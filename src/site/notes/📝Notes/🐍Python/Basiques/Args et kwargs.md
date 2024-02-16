---
{"dg-publish":true,"permalink":"/📝Notes/🐍Python/Basiques/Args et kwargs/","tags":["Python"]}
---

# \*args et \*\*kwargs
## \*args
Transforme les arguments supplémentaires en un tuple ordonné
```python
def f(text, *l):
	print(text, l)

f("numbers :", 1,2,3,4) # numbers : (1,2,3,4)
```

## \*\*kwargs
Acronyme de Keyword arguments
Accepte les arguments *nommés* et les ajoutent à un dictionnaire
```python
def f(**shopping_list):
	print("Shopping list:")
	for product,quantity in shopping_list.items():
		print("\t-", product, quantity)

f(banana=5, apple=2, onion=1)

# Shopping list:
#     - banana 5
#     - apple 2
#     - onion 1
```

> Bien sûr il est possible d'utiliser en même temps \*args et \*\*kwargs
> C'est une fonctionnalité très utile et utilisé dans beaucoup de fonctions *builtins*.
> Certains [[📝Notes/🐍Python/Basiques/Paramètres cachés\|paramètres sont "cachés"]] et pourraient vous intéresser donc renseignez vous.