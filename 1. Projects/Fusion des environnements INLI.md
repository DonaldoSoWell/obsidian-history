---
tags:
- templates/project
---
## Areas
- [[INLI]]

## Notes
- Lancement en beta test
	- Sowell (1 jour) => Créer environnement INLI IDF avec l'intégralité du patrimoine,  des affectations et des utilisateurs de INLI RS IDF et INLI Gardiens IDF 
		- NB : Mettre tous les emails en .test sur cet environnement
	- Sowell (1/2 jour) => Dupliquer tous les signalements depuis INLI RS IDF et INLI Gardiens IDF vers le nouveau INLI IDF
		- Questions pour Billal:
			- Pourra-t-on conserver les issues existantes, avec les issues.code (data.recordId dans Easiware ) actuels ? 
	- INLI (?) => Communiquer les informations nécessaires :
		- Valeur attendue pour easyware_channel
		- Valeur attendue pour easyware_escalation
	- Sowell (1/4 jour) => Dupliquer les jobs et déclencheurs pour INLI IDF :
		- Customers::Inli::GardiensIdf::CloseRemoteIssueJob
		- Customers::Inli::GardiensIdf::CreateRemoteIssueJob
		- Customers::Inli::GardiensIdf::CreateRemoteTalkJob
	- Sowell (1/4 jour) => Communiquer à INLI les informations nécessaires :
		- Créer le compte utilisateur easiware et transmettre les informations de connexion :
			- mail : bot@easyware.test
			- first name : SRC
			- last name : Easiware
			- can close issues : true
			- mdp : TBD (un truc complexe sur 12 char)
			- role : manager sur le scope "INLI FULL" avec tout le patrimoine
	- INLI (?) => Créer les connecteurs pour la syncro :
		- Renvoi d'un statut 200 + la référence easiware (data.recordId) à la création de signalement depuis Sowell vers Easiware
		- Création de signalement depuis Easiware vers Sowell
		- Création de messages chats depuis Easiware vers Sowell
		- Renvoi d'un statut 200 à la création d'un message chat depuis Sowell vers Easiware
		- Renvoi d'un statut 200 à la cloture d'un signalement depuis Sowell vers Easiware
		- Changement de statut d'un signalement depuis Easiware vers Sowell
	- INLI + Sowell (?) => Recette des connecteurs de syncro 
	- INLI => Lancement sur un panel réduit d'utilisateurs (5 reporter RS IDF + 5 reporter Gardien IDF + 2 manager RS IDF + 2 manager Gardien IDF)
- Lancement en production
	- INLI => Faire une communication auprés des utilisateurs avec  une des deux options suivantes (TBD) pour se connecter au nouvel environement :
		- soit réinitialisation des MDP pour 123456  
		- soit passage en connexion SSO en amont
	- Sowell (1/4 jour) => Mettre tous les emails en .old sur les environnements INLI RS IDF et INLI Gardiens IDF
	- Sowell (1/4 jour) => Supprimer tous les signalements depuis INLI IDF
	- Sowell (1 jour) => Déplacer tous les signalements depuis INLI RS IDF et INLI Gardiens IDF vers INLI IDF
	- Sowell (1/4 jour) => Mettre tous les emails en .fr sur l'environement INLI IDF
	- INLI => Informer et suivre les utilisateurs pendants quelques jours
  
## Meetings
```dataview
LIST
FROM "4. Archives/Meetings" and [[#]]
SORT file.name ASC
```
## Tasks 
- [ ]
