---
{"dg-publish":true,"permalink":"/📝Notes/🐍Python/Basiques/Fonctions de base/","tags":["Python"]}
---

# [Fonctions builtins](https://docs.python.org/3/library/functions.html)
## Utilitaire
```python
sum     # somme de nombres
divmod  # retourne le quotient et le reste
enumerate(['a','b','c']) # (0,a), (1,b), (2,c)
complex # str -> complex
filter  # filtre avec la fonction donnée
map     # applique une fonction
```


## Types related
- ``bin`` : Binaire
- ``bool`` : Booléen
- ``bytearray`` : Liste de Bytes
- ``bytes`` : Bytes, 
- ``chr`` : Entier -> Caractère au code Unicode donné
- ``complex`` : Nombre complexe
- ``dict`` : Dictionnaire
- ``float`` : Nombre flottant
- ``frozenset`` : Ensemble immuable
- ``hex`` : Hexadécimal
- ``id`` : Valeur d'identité, unique à une valeur (selon le cycle de vie des variables contenant les valeurs), CPython donne l'adresse mémoire
- ``int`` : Entier
- ``iter`` : Itérateur, peut prendre une valeur sentinel d'arrêt
- ``list`` : List
- ``object`` : Object, père de tous les objets, enfant de l'infini, destructeur des mondes
- ``oct`` : Octal
- ``ord`` : String/Byte -> Entier représentant le code Unicode
- ``set`` : Ensemble
- ``slice`` : Tranche, plus communément utilisé à travers la notation `liste[debut:fin:pas]`
- ``str`` : String
- ``tuple`` : Tuple

D'autres un peu plus spéciaux (avis subjectif) sont :
```python
aiter, ascii, hash
```



## Autres notables
```python
all, any, breakpoint, callable, compile, delattr, dir, eval, exec, format, getattr, globals, hasattr, help, input, isinstance, issubclass, len, locals, max, memoryview, min, next, open, pow, print, range, repr, round, setattr, sorted, super, type, vars, __import__
```

Visitez [la doc officiel de Python sur le sujet](https://docs.python.org/3/library/functions.html) pour en apprendre plus