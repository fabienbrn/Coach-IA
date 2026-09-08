# Charge, coach de musculation

Application web de coaching sportif, installable sur Android et iOS, fonctionnant hors ligne.
Aucun serveur, aucune base de données, aucune clé d'API. Les données restent sur l'appareil.

## Contenu du dépôt

| Fichier | Rôle |
|---|---|
| `index.html` | L'application entière, HTML, CSS et JavaScript |
| `manifest.json` | Déclaration PWA, nom, icônes, couleurs, mode plein écran |
| `sw.js` | Service worker, mise en cache de la coquille pour le hors ligne |
| `icon-192.png`, `icon-512.png` | Icônes du raccourci |
| `icon-maskable-512.png` | Icône adaptative Android, zone de sécurité respectée |

## Déploiement

1. Déposer les six fichiers à la racine du dépôt GitHub, sans sous-dossier.
2. Settings, Pages, source `Deploy from a branch`, branche `main`, dossier `/ (root)`.
3. Ouvrir l'URL fournie, puis menu Chrome, `Ajouter à l'écran d'accueil`.
   Sur iPhone, Safari, Partager, `Sur l'écran d'accueil`.

L'installation exige HTTPS. GitHub Pages le fournit. Ouvert en `file://`, l'application
fonctionne mais n'est pas installable.

## Mise à jour

Après toute modification de `index.html`, incrémenter la constante `CACHE` dans `sw.js`
(`charge-v1` vers `charge-v2`). Sans cela, les appareils déjà installés continueront
d'afficher la version en cache.

## Sauvegarde des données

Tout est écrit dans le `localStorage` du navigateur, à chaque saisie. Vider les données du
site ou désinstaller efface l'historique. Utiliser Profils, Exporter pour produire un
fichier JSON avant tout changement d'appareil.

## Limites assumées

- Pas de synchronisation entre appareils, pas de compte utilisateur.
- Le mode édition du contenu est local, il ne constitue pas un back-office multi-utilisateur
  et n'offre aucune étanchéité de droits.
- Les contenus de réathlétisation sont éducatifs et ne remplacent pas un avis médical.
