---
{"dg-publish":true,"permalink":"/📝Notes/🐍Python/Basiques/Expressions anonymes/","tags":["Python"]}
---

# Lambdas
## Notation
```python
lambda [paramètres]: <code, résultat sera retourné>
```

## Exemples
```python
lambda x: x+1
lambda a,b: a+b
calcSum = lambda *l: sum(l)  
calcSum(1,2,3) # 6
```