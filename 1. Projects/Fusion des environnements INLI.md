---
tags:
- templates/project
---
## Areas
- [[INLI]]

## Notes
- Sowell (1 jour) => Créer environnement INLI IDF avec l'intégralité du patrimoine,  des affectations et des utilisateurs de INLI RS IDF et INLI Gardiens IDF 
	- NB : Mettre tous les emails en .test sur cet environnement
- Sowell (1/2 jour) => Dupliquer tous les signalements depuis INLI RS IDF et INLI Gardiens IDF vers le nouveau INLI IDF
	- Questions pour Billal:
		- Pourra-t-on conserver les issues existantes, avec les issues.code (ref easiware) actuels ? 
- Sowell (1/4 jour) => Dupliquer les jobs et déclencheurs pour INLI IDF :
	- Customers::Inli::GardiensIdf::CloseRemoteIssueJob
	- Customers::Inli::GardiensIdf::CreateRemoteIssueJob
	- Customers::Inli::GardiensIdf::CreateRemoteTalkJob
- Sowell (1/4 jour) => Communiquer à INLI les informations nécessaires :
	- Créer le compte utilisateur easiware :
		- mail : bot@easyware.test
		- first name : SRC
		- last name : Easiware
		- can close issues : true
		- mdp : TBD (un truc complexe sur 12 char)
- INLI (?) => 
Inli et SoWell : màj connecteur + rapatriement des signalements (1 semaine si implication ok pour Inli)  
  
Inli : test sur un échantillon utilisateur avec des adresses email en .test (1 semaine si implication ok pour Inli)  
  
SoWell pour MEP (1 semaine) : nouveau rapatriement des signalements et bascule des adresses email du nouvel environnement en .fr pour que tous les utilisateurs basculent automatiquement sur le nouvel environnement fusionné   
  
Deux options pour se connecter au nouvel environnement avec des adresses en .fr :   
- soit réinitialisation des MDP pour 123456  
- soit passage en connexion SSO en amont
## Meetings
```dataview
LIST
FROM "4. Archives/Meetings" and [[#]]
SORT file.name ASC
```
## Tasks 
- [ ]
