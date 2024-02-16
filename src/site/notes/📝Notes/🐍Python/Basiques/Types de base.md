---
{"dg-publish":true,"permalink":"/📝Notes/🐍Python/Basiques/Types de base/","tags":["Python"]}
---

# Types de base

## Les classiques
```python
entier = 50_000_000
flotant= 1.0
string = "hello"
string_multiligne = """Hello
					   World"""
bytes  = b"Hello\x20World"
liste  = [0,1,2]
tuple  = (0,1,2)
dico   = {'a':0, 'b':1}
ensemble = {0,1,2,2} # {0,1,2}
```

## Les non-considérés
```python
booléen    = True
fonction   = print
expression = lambda x:x
générateur = range(10)
format     = f"{1+1}" # '2'
tranche    = slice(-1, 1, 2)
```

## Les exotiques
```python
complexe = complex(2,4) # (2+4j)
fraction = fractions.Fraction(10,25) # Fraction(2,5)
décimal  = decimal.Decimal(1.1) # Decimal('1.100000000000000088817841970012523233890533447265625')

```

## Les variantes
```python
binaire = 0b010100000111100101110100011010000110111101101110
hex     = 0x507974686F6E
octal   = o120171164150157156
```
