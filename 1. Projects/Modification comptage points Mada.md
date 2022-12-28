
---
tags:
- templates/project
---
## Notes
- Areas : [[Admin]]
- #people/jeni voici donc les problèmes qu'on a relevé concernant les comptages de points:
	- Focus sur l'objectif perso (Vrai pbl pour les lead dev)
	- Course au ticket les mieux estimer sans souci de sa valeur metier
	- les gens préfère travailler seul pour ne pas partager les points 
	- par peur que les autres prennent trop dans le pots commun certains sous-estime les tickets
	- Focus sur les gains des autres en pensant que ça pourrait leurs revenir
	- Chacun travail et évolue mais gagne quand meme la meme somme car il se partage la meme somme(ex: tout le monde fais 10% de plus que le mois dernier mais aucun changement sur le gain)
	- Personne ne veut prendre un bug car ça peut prendre du temps de le traiter mais peu de points
- Pistes de réflexions
	- Interdire la prise en charge de tickets avant leur estimation
	- Aucune distribution de point pour la correction de bug :
		- Soit on sait qui en est l'auteur et on lui confie la résolution
		- Soit on ne sait pas qui en est l'auteur et on tire au sort ou on fait à tour de role pour savoir à qui le confier
		- NB : 
			- La personne en charge de la résolution ne peut plus traiter d'autre ticket tant que le bug n'est pas reglé
			- Si la correctIon du bug nécessite un refactoring du code (validé par le Lead dev), on passe en mode normal (estimatIon + comptage des points)
	- L'estimation des tickets "features" integre :
		- La difficultée estimée par les dev + lead dev
		- La valeur ajoutée estimée par le market et Rantsa
		- Todo : Définir une règle de calcul
	- En cas de collaboration sur un ticket, les dev se mettent d'accord sur la répartition des points, si pas d'accord, c'est le lead dev qui tranche
	- Quand c'est un Lead dev qui fait le dev, il ne gagne pas de poInts :
		- Pour une tache associée à une feature, les points sont répartit 

## Meetings
```dataview
LIST
FROM "4. Archives/Meetings" and [[#]]
SORT file.name ASC
```
## Tasks 
- [ ]
