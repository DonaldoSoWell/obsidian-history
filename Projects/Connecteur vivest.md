---
template: project
---
[[Home]] / [[Projects]]

> [!summary]
>***Area***: [[Vivest]]

## Notes
### 
### 1. Scénarios validés :
#### Signalement créé depuis SoWell
SoWell pousse le signalement vers le CRM en créant une requête à l'api REST standard. Fonctionnellement, ces demandes devront être traitées par le responsable de secteur qui se trouve sur la fiche résidence.

>[!question]
>SoWell doit envoyer (au choix)
>- tous les signalements
>- uniquement les signalement de certaine catégories
>- les signalements pour lesquels l'auteur à précisé qu'ils devaient être envoyés
>- les signalements pour lesquels un manager à précisé via l'UI manager qu'ils devaient être envoyés

##### Données fournies par SoWell dans la requête 
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
##### 
##### Traitement des données de la requête par le CRM 
  - Ajout du statut "Transférée"
  - Ajout du canal "SoWell"
  - Ajout du "Gestionnaire concerné" et "Acteur en charge" calculé par rapport à la résidence et en fonction du Type de gestionnaire de la qualification
  - Intégration du champ "Autheur" fourni dans un champ texte en lecture seule
  - Intégration des champs "Date de création", "Niveau de priorité" et "Description" fourni dans le champ "Contexte de la demande"
  - Intégration des photos dans l'onglet "Fichiers"
  
>[!info]
>Il n'y a pas de demandeur pour les signalements SoWell. Uniquement une résidence et éventuellement un bien.
>Vivest paramètre le Workflow à utiliser sur chaque qualification
>Si des accusés de réception doIvent être envoyés, Vivest sait les paramétrer avec le moteur de règles.

##### Réponse attendue par SoWell 
  - HTTP Status Code => Pour indiquer le résultat de la requête 
	  - 2xx => Ok
	  - 4xx => Ko client
	  - 5xx => Ko server
  - CRM UID => Identifiant unique du signalement créé dans le CRM et servant de référence commune pour le suivi de ce signalement

#### Changement de statut d'un signalement SoWell depuis Vivest
Lorsque le statut d'un signalement évolue dans le CRM, si le canal est SoWell, le CRM met à jour le signalement dans SoWell en créant une requête à l'api SoWell

##### Données fournies par le CRM dans la requête :
- CRM UID
- nouveau status (cf. correspondance des status[^1])

##### Réponse fournie par SoWell
HTTP Status Code => Pour indiquer le résultat de la requête 
	- 2xx => Ok
	- 4xx => Ko client
	- 5xx => Ko server

> [!question]
>Doit on interdire le changement de statut d'un signalement depuis SoWell ?

### 2. Scénarios à discuter :
1. Signalement créé depuis le CRM => Le transférer vers SoWell ? Sous quels critères
2. Nouveau message sur un signalement depuis SoWell => Le transférer vers le CRM ?
3. Nouvelle photo sur un signalement depuis SoWell => La transférer vers le CRM ?
4. Nouveau message sur un signalement depuis le CRM => Le transférer vers SoWell ?
5. Nouveau document sur un signalement depuis le CRM => Le transférer vers SoWell ?
6. Changement de status d'un signalement depuis SoWell => Mettre à jour dans le CRM ?



[^1]: | CRM                      | SoWell                 |
|:------------------------ | ---------------------- |
| Ouverte                  | En attente             |
| CRC en cours             | En cours de traitement |
| CRC en attente retour    | En attente             |
| Transférée               | En attente             |
| Vivest en cours          | En cours de traitement |
| Vivest en attente retour | En attente             |
| Clôturée[^2]             | Traité ou Rejeté       |

[^2]: Pour distinguer le statut clôturé (Traité ou Rejeté), un champ spécifique est ajouté dans les champs des qualifications. Le champ Résultat devra être paramétré en "obligatoire" dans la (ou les) transition(s) de workflow vers le statut clôturé.

## Meetings
```dataview
LIST
FROM "4. Archives/Meetings" and [[#]]
SORT file.name ASC
```
## Tasks 
- [ ]
