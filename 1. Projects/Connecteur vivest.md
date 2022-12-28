---
tags:
- templates/project
---
## Notes
- Areas : [[Vivest]]
- Scénarios :
	- Signalement créé depuis SoWell
		- SoWell pousse le signalement dans le CRM en créant une demande via l'api REST standard. Fonctionnellement, ces demandes devront être traitées par le responsablede secteur qui se trouve sur la fiche résidence.
		- Données fournies par SoWell :
			- Qualification => code de la catégorie SoWell
			- Résidence => code de la place SoWell
			- Bien (logement) => code du spot SoWell
			- Autheur => Nom + prénom de l'autheur SoWell
			- Email autheur => Email de l'autheur SoWell
			- Date de création => Date de création du signalement au format ISO 8601

## Meetings
```dataview
LIST
FROM "4. Archives/Meetings" and [[#]]
SORT file.name ASC
```
## Tasks 
- [ ]
