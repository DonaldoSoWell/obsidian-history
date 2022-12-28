---
tags:
- templates/project
---
## Notes
- Areas : [[Vivest]]
- Scénarios :
	- 1) Signalement créé depuis SoWell
		- SoWell pousse le signalement vers le CRM en créant une requête à l'api REST standard. Fonctionnellement, ces demandes devront être traitées par le responsablede secteur qui se trouve sur la fiche résidence.
		- Données fournies par SoWell dans la requête :
			- Qualification => code de la catégorie SoWell
			- Résidence => code de la place SoWell
			- Bien (optionnel) => code du spot SoWell
			- Autheur => Nom + prénom de l'autheur SoWell
			- Email autheur => Email de l'autheur SoWell
			- Date de création => Date au format ISO8601 (2012-04-23T18:25:43.511Z)
			- Niveau de priorité => 
				- low = fiable
				- normal = normal
				- high = haute
			- Description => Champ texte
			- Photos => Tableau JSON de photos au format base64
			- Lien SoWell => URL du signalement sur l'interface manager SoWell
		- Traitement des données de la requête par le CRM :
			- Ajout du statut "Transférée"
			- Ajout du canal "SoWell"
			- Ajout du "Gestionnaire concerné" et "Acteur en charge" calculé par rapport à la résidence et en fonction du Type de gestionnaire de la qualification
			- Intégration du champ "Autheur" fourni dans un champ texte en lecture seule
			- Intégration des champs "Date de création", "Niveau de priorité" et "Description" fourni dans le champ "Contexte de la demande"
			- Intégration des photos dans l'onglet "Fichiers"
		- Remarques :
			- Il n'y a pas de demandeur pour les signalements SoWell. Uniquement une résidence et éventuellement un bien.
			- Vivest paramètre le Workflow à utiliser sur chaque qualification
			- Si des accusés de réception doIvent être envoyés, Vivest sait les paramétrer avec le moteur de règles.
			- 

## Meetings
```dataview
LIST
FROM "4. Archives/Meetings" and [[#]]
SORT file.name ASC
```
## Tasks 
- [ ]
