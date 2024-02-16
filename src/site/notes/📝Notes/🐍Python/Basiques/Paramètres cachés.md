---
{"dg-publish":true,"permalink":"/📝Notes/🐍Python/Basiques/Paramètres cachés/","tags":["Python"]}
---

# Paramètres cachés
Certaines fonctions possèdent des paramètres effectifs très utiles ! Il est vivement conseillé de lire la doc de chacune de ces fonctions ou d'utilisé un bon IDE qui peut afficher dynamiquement les différentes possibilités.

```python
print("hello", end=' World\n')
sorted(a, key=lambda a,b: a['value']<b['value'])
max(0,1,2,3,4,5)
max([0,1,2,3,4,5])
open("file", "r", encoding="latin-1")
```

> Ces paramètres souvent des [[📝Notes/🐍Python/Basiques/Args et kwargs\|*args et **kwargs]]