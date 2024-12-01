---
{"dg-publish":true,"permalink":"/👩‍🏫Writeups/NBCTF 2024 - Game Hacking/","tags":["Writeup","NBCTF","Misc"]}
---

# NoBrackets CTF 2024 - Game Hacking Final

## Desktop Friend
> Agent !
> Je pars en mission !
> 
> Pourriez-vous prendre soin de mon compagnon de bureau ?
> Pas besoin de le nourrir, il suffit juste de le caresser.
> 
> Si vous le caressez assez, il vous donnera peut-être même un flag, mais au bout de 5 000 000 de caresses au moins !
> 
> Format du flag : `NBCTF{...}` ou sa version chiffrée

Vous pouvez télécharger le jeu [ici](https://antoine.rocks/WU_files/desktop_friend.zip) (quand mon serveur est up, soit 1 semaine sur 2 😓)

**CheatEngine**:
- **Unknown initial values** avec des valeurs de type **All**
- On enlève les valeurs très hautes avec **smaller than** d'une valeur que l'on souhaite comme 100 par exemple
- On regarde et filtre les valeurs restantes avec **increased value** ou **unchanged value**

Bien sûr lorsque l'on filtre avec **increased value**, il est nécessaire de caresser notre amis entre chaque scan sinon l'adresse que nous cherchons sera filtré.

Dès que nous avons trouvé l'adresse il nous suffit de double cliquer dessus pour l'ajouter à notre liste d'addresses pour pouvoir la modifier.