---
tags:
- templates/meeting
---
<nav aria-label="Breadcrumb" class="custom-breadcrumb">
    <ul>
        <li><a href="obsidian://advanced-uri?vault=Donaldo&filepath=MOC"> MOC</a></li>
    </ul>
</nav>

- **Date:**  [[2022-09-21]]
- Project: [[Connexion SSO Sequens]]
- Area: [[Sequens]]
- **Attendees:** 
	- PHILIPPE Benoit
	- HUSSON Natham

## Meeting Objective
Echanger avec Nathan sur comment mettre en place le SSO sur une interface web

## Agenda
- Mise en service en Janvier
- Début des tests avec SSO ASAP

## Decisions
- On mets d'abord le SSO sur le site manager puis on enchaine avec l'app reporter

## Notes
- Dans leur mise en oeuvre, ils ont utilisé SAML via une libraiarie PHP
- C'est Savio FOURIER qui gère le service SSO, Nathan lui a juste implémenté le service dans une app
- L'appel que le SSO fait à notre URL peut contenir différentes infos, dont le mail, le nom et le prénom de l'utilisateur
- Process : 
	- L'utilisateur précise qu'il veut se connecter via SSO
	- Il choisi son entreprise
	- On l'envoi vers la mire de connexion
	- Il se connecte sur le serveur SSO
	- Il est redirigé chez nous
	- On vérifie qu'il est bien authentifié
	- On vérifie qu'on le connait
	- On lui donne un JWT

## Action Items
- Envoyer un mail à SavIo, CC Nathan et Benoit avec les infos dont j'ai besoin et y indiquer notre URL de retour
