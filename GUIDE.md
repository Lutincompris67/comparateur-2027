# Guide de mise en ligne — Comparateur 2027 sur GitHub Pages (avec GitHub Desktop)

Ce guide vous accompagne de zéro jusqu'au lien partageable, puis décrit votre routine de mise à jour avec **GitHub Desktop**. C'est l'approche la plus confortable pour des mises à jour régulières : vous travaillez dans un dossier normal sur votre ordinateur, et vous publiez vos changements d'un clic.

## Les fichiers du site

- **index.html** — le site lui-même (grille comparative, panneaux, méthodologie, bibliographie).
- **data.js** — les données affichées (générées depuis votre Excel). C'est le seul fichier que vous remplacerez au fil des mises à jour.
- **convertisseur.html** — votre outil de conversion : il transforme votre fichier Excel en data.js, dans le navigateur, sans rien installer.

## Comment fonctionne GitHub Desktop (le principe en deux mots)

GitHub Desktop relie un **dossier sur votre ordinateur** (appelé « dépôt local ») à un **dossier en ligne sur GitHub** (le « dépôt distant »). Vous modifiez les fichiers normalement sur votre ordinateur ; quand vous êtes prêt, vous enregistrez l'état (« commit ») et vous l'envoyez en ligne (« push »). GitHub Pages publie alors automatiquement.

Le vocabulaire à connaître, une fois pour toutes :
- **Commit** = enregistrer une photo de l'état actuel de vos fichiers, avec un petit message.
- **Push** (ou « Push origin ») = envoyer vos commits vers GitHub en ligne.
- **Repository / dépôt** = le dossier de votre projet, en local et en ligne.

## Étape 1 — Créer un compte GitHub (5 minutes, une seule fois)

1. Allez sur https://github.com et cliquez sur « Sign up ».
2. Choisissez un nom d'utilisateur (il apparaîtra dans l'adresse de votre site, ex. `votrepseudo.github.io/...`), une adresse e-mail et un mot de passe.
3. Validez l'e-mail de confirmation.

## Étape 2 — Installer et connecter GitHub Desktop

1. Téléchargez GitHub Desktop sur https://desktop.github.com et installez-le.
2. Ouvrez l'application. Au premier lancement, cliquez « Sign in to GitHub.com » et connectez-vous avec le compte créé à l'étape 1. Autorisez la connexion dans le navigateur quand il vous le demande.
3. Si l'application vous demande de configurer votre nom et votre e-mail (« Git config »), validez les valeurs proposées.

## Étape 3 — Créer le dépôt depuis GitHub Desktop

1. Dans GitHub Desktop : menu « File » → « New repository… ».
2. Renseignez :
   - **Name** : `comparateur-2027` (minuscules, sans espaces).
   - **Local path** : l'emplacement sur votre ordinateur où sera créé le dossier (ex. vos Documents). Notez-le, vous y reviendrez.
   - Laissez le reste par défaut, cliquez « Create repository ».
3. Le dépôt existe maintenant en local, mais pas encore en ligne. Cliquez le bouton bleu **« Publish repository »** (en haut).
   - **Décochez** « Keep this code private » — GitHub Pages gratuit exige un dépôt public.
   - Cliquez « Publish repository ».

Votre dépôt est maintenant en ligne et vide. Place aux fichiers.

## Étape 4 — Déposer les fichiers du site

1. Ouvrez le dossier local du dépôt (celui choisi à l'étape 3). Astuce : dans GitHub Desktop, menu « Repository » → « Show in Explorer » (Windows) ou « Show in Finder » (Mac) l'ouvre directement.
2. Copiez-y les trois fichiers : `index.html`, `data.js`, `convertisseur.html`. Ils doivent être **à la racine** du dossier, pas dans un sous-dossier.
3. Revenez dans GitHub Desktop : les trois fichiers apparaissent à gauche dans « Changes ».
4. En bas à gauche, dans le champ « Summary », écrivez un court message, par exemple `Ajout du site`. Cliquez **« Commit to main »**.
5. En haut, cliquez **« Push origin »** pour envoyer en ligne.

## Étape 5 — Activer GitHub Pages

Cette étape se fait sur le site GitHub (une seule fois) :

1. Dans GitHub Desktop, menu « Repository » → « View on GitHub » : votre dépôt s'ouvre dans le navigateur.
2. Ouvrez l'onglet **« Settings »** (en haut à droite), puis **« Pages »** dans le menu de gauche.
3. Sous « Build and deployment » → « Source », choisissez **« Deploy from a branch »**.
4. Sous « Branch », sélectionnez **`main`** et le dossier **`/ (root)`**, puis « Save ».
5. Patientez une à deux minutes (parfois jusqu'à dix la première fois), rechargez : l'adresse de votre site s'affiche en haut, du type :
   **https://votrepseudo.github.io/comparateur-2027/**

C'est ce lien que vous partagez. Il fonctionne sur mobile comme sur ordinateur.

Astuce : chaque thématique et chaque sujet ont leur propre lien partageable. Ouvrez un sujet sur le site et copiez l'adresse de la barre du navigateur : ce lien ramène directement à ce sujet.

## Votre routine de mise à jour (2 minutes à chaque fois)

1. Modifiez votre fichier **Comparateur_2027_source.xlsx** (positions, analyses, partis pris, bibliographie) — au besoin avec l'aide de Claude dans Excel.
2. Ouvrez **convertisseur.html** (double-clic sur le fichier, ou via le lien `…/convertisseur.html` de votre site).
3. Glissez-y votre fichier Excel. Lisez le rapport de cohérence : il signale les ID orphelins, doublons ou sources manquantes. Corrigez dans Excel si besoin et recommencez.
4. Cliquez « Télécharger data.js ».
5. Remplacez l'ancien `data.js` du dossier local par celui que vous venez de télécharger (déplacez-le depuis vos téléchargements vers le dossier du dépôt, en acceptant d'écraser l'ancien).
6. Dans GitHub Desktop : un message de commit (ex. `Mise à jour des données`), « Commit to main », puis « Push origin ».
7. Une à deux minutes plus tard, le site est à jour.

## Ce qu'il faut savoir

- **Le contenu vit dans Excel, jamais dans le code.** Ajouter un candidat = renommer/ajouter une colonne dans les onglets thématiques. Ajouter un sujet = une ligne avec un nouvel ID_sujet. Ajouter une analyse, un parti pris ou une source = une ligne dans l'onglet correspondant. Puis reconversion + commit + push du data.js.
- **Ne modifiez jamais un ID_sujet existant** : il relie le sujet à ses analyses.
- **Les données d'exemple** (marquées [EXEMPLE à remplacer], surlignées en jaune dans Excel) montrent le fonctionnement : remplacez-les ou supprimez les lignes quand vous saisirez du contenu réel, puis reconvertissez.
- **Gardez votre fichier Excel hors du dépôt** (ou dans un sous-dossier que vous n'envoyez pas), à moins de vouloir le publier : seuls index.html, data.js et convertisseur.html sont nécessaires au site.
- **Modifications structurelles du site** (nouvelle fonctionnalité, changement de mise en page, passage à l'option B collaborative) : revenez vers Claude avec le fichier index.html, qui est écrit pour être facilement modifiable.
- **Nom de domaine personnalisé** (optionnel) : Settings → Pages → Custom domain, pour associer un domaine acheté (ex. comparateur-2027.fr).

## En cas de problème

- **Le bouton « Publish repository » a disparu / je ne sais plus si c'est en ligne** : menu « Repository » → « View on GitHub ». Si la page s'ouvre, le dépôt est bien en ligne.
- **Le site affiche « data.js introuvable »** : vérifiez que data.js est bien à la racine du dossier local (au même niveau que index.html), que son nom est exactement `data.js`, et que vous avez bien fait « Commit » puis « Push ».
- **Mes changements n'apparaissent pas en ligne** : avez-vous cliqué « Push origin » après le commit ? Un commit seul reste sur votre ordinateur. Vérifiez aussi qu'il ne reste rien dans « Changes ».
- **La page reste l'ancienne version après mise à jour** : cache du navigateur. Rechargez avec Ctrl+F5 (Windows) ou Cmd+Maj+R (Mac). Comptez aussi jusqu'à 10 minutes de délai de publication GitHub.
- **Le convertisseur signale des « points à vérifier »** : ce sont des incohérences dans l'Excel (ID orphelin, source citée absente de la bibliographie). Le data.js est tout de même généré, mais corrigez-les pour un site propre.
