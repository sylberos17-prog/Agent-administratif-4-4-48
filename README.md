# Admin 4/4/48

Agent administratif de La Saintes 4/4/48. Application installable sur téléphone,
qui suit les quatorze démarches réglementaires et rédige les courriers.

## Mettre en ligne sur GitHub Pages

1. Créer un dépôt public, par exemple `admin-448`.
2. Y déposer les cinq fichiers de ce dossier, à la racine :
   `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`.
3. Dans le dépôt : **Settings → Pages → Source : Deploy from a branch**,
   branche `main`, dossier `/ (root)`. Enregistrer.
4. Au bout d'une minute, l'app est en ligne sur
   `https://<ton-compte>.github.io/admin-448/`.

## Installer sur le téléphone

- **iPhone** : ouvrir l'adresse dans Safari, bouton Partager, *Sur l'écran d'accueil*.
- **Android** : ouvrir dans Chrome, menu, *Installer l'application*.

L'icône apparaît comme une app normale, elle s'ouvre en plein écran.

## Clé API

L'agent a besoin d'une clé API Anthropic pour rédiger. À créer sur
console.anthropic.com, puis à coller dans l'onglet **Réglages**.

La clé est enregistrée uniquement dans le navigateur du téléphone et n'est
envoyée qu'à l'API d'Anthropic. Elle n'apparaît nulle part dans le code déposé
sur GitHub. Ne jamais l'écrire en dur dans `index.html` : le dépôt est public.

Compter quelques centimes par courrier généré.

## Hors connexion

L'interface, la liste des démarches et les statuts fonctionnent sans réseau.
Seules la rédaction et les conseils demandent une connexion.

## Mettre à jour le contenu

Tout est dans `index.html` :

- le tableau `D` contient les démarches — pour en ajouter une, copier un bloc
  existant et changer `j` (le nombre de jours avant l'événement) ;
- la constante `EVENT` fixe la date de départ, les échéances se recalculent seules ;
- `FICHE` porte le contexte de l'événement injecté dans chaque génération ;
- `SYS` définit la façon d'écrire de l'agent.

Après modification, incrémenter `CACHE = "admin448-v2"` dans `sw.js` pour que
les téléphones récupèrent la nouvelle version.
