---
{"dg-publish":true,"permalink":"/📝Notes/🐍Python/Basiques/T par compréhension/","tags":["Python"]}
---

# \<T\> par compréhension

```python
[<élément ajouté> for <var(s)> in <iter>]
[<élément ajouté> for <var(s)> in <iter> if <cond>]
```

Possibilités:
- listes par compréhension
- tuples par compréhension
- ensembles par compréhension
- dictionnaires par compréhension

```python
[i for i in range(10)]
(i for i in range(10) if i%2==0)
{l for l in 'abcdef'}
{k:v for v,k in enumerate('abcde’)}
```

> [!NOTE]
> Les fonctions prenant en paramètre un itérateur peuvent se passer des parenthèses
> ```python
> sum(i for i in range(10))
> ```

Plus d'informations disponible sur la PEP dédiée, [PEP 202](https://peps.python.org/pep-0202/)