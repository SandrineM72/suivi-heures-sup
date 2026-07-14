# Suivi des heures

Application web **autonome** (un seul fichier `index.html`, aucune dépendance) pour pointer ses heures de travail depuis un smartphone, avec calcul automatique des heures supplémentaires et export Excel.

## Fonctionnalités

- **Saisie rapide** en chiffres avec aperçu en direct : `9` → 09:00, `930` → 09:30, `1730` → 17:30 (les `:` fonctionnent aussi).
- **Calcul automatique** de l'horaire total effectif et des **heures supplémentaires** (base théorique : 7h/jour, 09:00 → 17:00).
- **Récap hebdomadaire** par semaine ISO.
- **Export Excel (`.xlsx`)** — deux feuilles (suivi journalier + récap), **100 % hors-ligne** (générateur `.xlsx` maison, sans librairie externe).
- **Thème clair / sombre** avec bascule (mémorisé).
- **Stockage local** : les données restent dans le navigateur (`localStorage`), rien n'est envoyé à un serveur.

## Utilisation

Sur Android : ouvrir l'URL puis « Ajouter à l'écran d'accueil » pour un lancement type application.

> Les données étant stockées dans le navigateur, l'**export Excel** sert aussi de **sauvegarde** (à faire régulièrement).
> Les données exportées sont copiées-collées dans l'onglet **Saisies** du fichier Excel de suivi global.
> Une macro permet de récupérer les données dans un **tableau de bord**.

## Design

Style « Pop brutalist » : cadres noirs, ombres portées dures, couleurs vives, typographies Space Grotesk + DM Sans.

Accessibilité : contraste respecté en modes clair / sombre

## Technique

- HTML / CSS / JavaScript **vanilla**, zéro dépendance à l'exécution.
- Générateur `.xlsx` maison : un fichier `.xlsx` est une archive ZIP de fichiers XML (format OpenXML), fabriquée directement en JS (CRC32 + ZIP « stored »).
- Détection d'environnement pour le stockage : `window.storage` dans l'aperçu Artefact de Claude, `localStorage` en fichier autonome.

## Déploiement

Servi en statique derrière **Caddy** sur un VPS, protégé par `basic_auth`, sur le sous-domaine `suivi-heures-sup.culturecook.fr`.

## Licence

Projet personnel.
