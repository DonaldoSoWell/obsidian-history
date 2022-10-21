---
tags:
- templates/project
---
<nav aria-label="Breadcrumb" class="custom-breadcrumb">
    <ul>
        <li><a href="obsidian://advanced-uri?vault=Donaldo&filepath=MOC"> MOC</a></li>
        <li><a href="obsidian://advanced-uri?vault=Donaldo&filepath=PARA/1. Projects/1. Projects"> Projects</a></li>
    </ul>
</nav>

## Tasks 
- [x] Reprendre note de réunion et les mettre au propre 
- [x] Envoyer mail à SavIo, CC Nathan et Benoit avec les infos dont j'ai besoin @due 📅 2022-09-23 [completion:: 2022-10-07]
	- cf [[2022-09-21 Call technique SSO Sequens#Action Items]]
	- [x] Préciser qu'on est sur une Single Page APP [completion:: 2022-10-07]
	- [x] Lui communiquer notre URL de retour [completion:: 2022-10-07]
	- [x] Lui demander de nous fournir toute info utile : [completion:: 2022-10-07]
		- [x] tenant ID [completion:: 2022-10-07]
		- [x] client ID [completion:: 2022-10-07]
		- [x] URL complete du serveur si pas la version cloud [completion:: 2022-10-07]
- [x] Voir s'il existe des librairies SAML microsoft pour VueJS [completion:: 2022-10-07]
	- [x] https://devblogs.microsoft.com/azure-sdk/vue-js-user-authentication/
	- [x] https://stackoverflow.com/questions/44437634/how-do-you-authenticate-a-vuejs-app-with-azure-ad
	- [x] https://medium.com/adidoescode/azure-ad-for-user-authentication-with-vue-and-nestjs-4dab3e96d240
	- [x] https://bestofvue.com/repo/mvertopoulos-vue-msal-vuejs-authentication-authorization
	- [x] https://github.com/survirtual/vue-adal
	- [x] https://www.web-dev-qa-db-fra.com/fr/node.js/comment-authentifier-une-application-vuejs-avec-azure-ad/832164266/
	- [x] https://thewebdev.info/2022/03/12/how-to-authenticate-a-vue-js-app-with-azure-ad/
- [x] Planifier la réalisation du SSO dans Obsidian conformément au dates annoncées [ici](message://<E3ADF990-B915-47A7-AE04-E2C3B01DC179@sowellapp.com>) @due 📅 2022-10-08 ✅ 2022-10-11
- [ ] Respecter la planification annocée  [cf mail](message://<E3ADF990-B915-47A7-AE04-E2C3B01DC179@sowellapp.com>)
	- [ ] Pour l’application Web [manager.sowellapp.com](http://manager.sowellapp.com/) :
		1. Etude de faisabilité :
			- [x] Création de "l'intégration SoWell" dans la marketplace Microsoft
			- [x] Ajout de "l’intégration SoWell" dans une organisation Microsoft Azur existante pour validation
			- [x] Réalisation d’une application Web en mode "Proof Of Concept” pour se connecter via SSO avec un compte utilisateur d'une organisation Microsoft Azur  
		2. Implémentation du workflow de connexion via SSO :
			- [x] Ajout du bouton “Se connecter avec Microsoft” et implémentation des librairies JS correspondantes dans l’application. @due 📅 2022-10-16 [completion:: 2022-10-15]
			- [x] Gestion du workflow de connexion SSO dans notre API @due 📅 2022-10-16 [completion:: 2022-10-15]
			- [x] Livrer en productIon et prévenir le client @due 📅 2022-10-16 
		3. Ajout de "l’intégration SoWell" dans l'organisation Microsoft Azur Seqens 
			- [x] Todo Seqens semaine 42 (je vous donnerai la démarche à suivre le moment venu)
		4. Test de connexion via SSO 
			- [x] Todo SoWell/Seqens semaine 42
	- [ ] Pour l'application Mobile SoWell :
		1. Etude de faisabilité :
			- [ ] Réalisation d’une application mobile en mode "Proof Of Concept” pour se connecter via SSO avec un compte utilisateur d'une organisation Microsoft Azur => Todo SoWell semaine 43
		2. Implémentation du workflow de connexion via SSO :
			- [ ] Ajout du bouton “Se connecter avec Microsoft” et implémentation des librairies natives correspondantes dans l’application. => Todo SoWell semaine 44
			- [ ] Gestion du workflow de connexion SSO dans notre API => Todo SoWell semaine 44
		3. Test de connexion via SSO
			- [ ] Todo SoWell/Seqens semaine 45