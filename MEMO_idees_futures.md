# Mémo — idées futures et décisions en attente

*Dernière mise à jour : 27 août 2026*

---

## RÉALISÉ — sorti de ce mémo

**Mécanisme d'emprunt entre thématiques** (ex-« système d'étiquettes »). Conçu, codé et mis en production le 24/08/2026. Colonne « Aussi dans » dans les onglets thématiques ; le convertisseur propage le sujet vers les thématiques cibles sans duplication de contenu. Documenté dans les instructions du projet, section 6.

**Intégration du deuxième candidat.** Programme Gabriel Attal (six pages « chantiers capitaux » et « dettes à résorber ») transcrit intégralement les 26–27/08/2026, en six lots GA-01 à GA-06 : 59 verbatims, 11 sujets créés, 6 sources. La colonne « Candidat B » a été renommée « Gabriel Attal » dans les 36 onglets thématiques. La dernière donnée d'exemple du classeur a été supprimée à cette occasion.

**Sujets créés en réaction au programme Attal** : `ECO-harcelement`, `ECO-eleves-par-classe`, `NUM-reseaux-sociaux-mineurs`, `IND-investissements`, `TRA-droit-travail`, `MIL-industrie-defense`, `MIL-effectifs`, `INT-ukraine`, `IND-souverainete-industrielle`, `NUM-cybersecurite`, `AID-reformes`.

---

## A. Chantiers techniques à court terme

### A.1 Garde-fous du convertisseur

**Problème constaté** : déposer `data.js` (au lieu du `.xlsx`) dans le convertisseur produit un rapport absurde — 895 « sujets », 1435 faux doublons — au lieu d'un message d'erreur clair. Le fichier est lu comme un classeur, chaque ligne de JSON devient un sujet.

**Correctif à apporter** (une dizaine de lignes) :
- vérifier l'extension du fichier déposé et refuser tout ce qui n'est pas `.xlsx` ;
- vérifier que le classeur contient les onglets attendus (« Bibliographie », « Analyses & partis pris ») et alerter sinon ;
- éventuellement, alerter si le nombre de « thématiques » détectées est anormalement bas (1 ou 2).

**Priorité** : faible en usage solo, forte dès que d'autres personnes manipuleront l'outil. *Toujours non fait au 27/08/2026.*

### A.2 Alias d'emprunt disparus

Si un emprunt est retiré de l'Excel, les liens partageables `#s/ID/Thème` correspondants cessent de désigner la bonne thématique (le site retombe silencieusement sur la thématique d'origine — pas de page cassée, mais le lien ne fait plus ce qu'il promettait). Possibilité d'ajouter au convertisseur un avertissement listant les alias supprimés depuis la dernière conversion. **Non implémenté, cas rare.**

### A.3 Refonte de la page Bibliographie — NOUVEAU

**Problème constaté le 27/08/2026** : 20 entrées pour une seule analyse et deux programmes partiels. La page mélange deux objets de nature différente, et le plus nombreux des deux est celui qui n'a aucun rapport avec une bibliographie au sens habituel.

Sur les 20 entrées : 10 sont des **pages de programme** (4 Philippe, 6 Attal), 10 sont des **sources d'analyse**. Aucune entrée « programme » n'est citée par un appel de note : elles sont orphelines dans la logique propre de la bibliographie, alors qu'elles sont indispensables à la promesse de vérifiabilité de la méthodologie.

Les deux ensembles croissent selon des lois différentes : les sources de programme croissent en candidats × pages publiées (dix candidats à six pages feraient 60 lignes à elles seules), les sources d'analyse croissent avec le travail éditorial.

**Direction retenue** : séparer les deux registres, en cohérence avec la doctrine des trois registres du site. Voir le détail dans la conversation du 27/08/2026. Trois niveaux, du plus urgent au plus optionnel :
1. Colonne « Registre » (`programme` / `analyse`) dans l'onglet Bibliographie ; deux sections distinctes sur la page du site.
2. Navigation dans les sources d'analyse : regroupement par Type, index inverse « cité dans », champ de filtre. À faire quand le volume dépassera la trentaine d'entrées.
3. Question non tranchée, plus lourde : relier chaque verbatim à la page de programme dont il provient. Aujourd'hui rien ne relie une case à sa source précise, alors que la méthodologie promet cette vérifiabilité.

---

## B. Question de modélisation non tranchée

### Verbatim transversal (« cas B »)

Distinction posée le 24/08/2026, dont un seul versant est traité :

- **Cas A — sujet-frontière** : un même *objet* relève de deux thématiques (ex. « Prisons » → Justice + Sécurité). → **Résolu** par le mécanisme d'emprunt.
- **Cas B — verbatim transversal** : une *phrase* d'un candidat éclaire deux sujets distincts, qui restent deux objets séparés (d'autres candidats y répondront différemment). → **Non mécanisé.** On duplique le texte manuellement dans les deux cases.

**Cas B rencontrés à ce jour.** Chez Philippe : le pacte fiscal (IMP-impots-production + ECN-aides-publiques), le livret capital France (NUM-souverainete-ia + ECN-epargne), la mesure IA sur l'enseignement (triplée : NUM-ia-emploi + ECO-intelligence-artificielle + TRA-chomage). Chez Attal : le livret garde d'enfant (ECO-creches + ECN-epargne), la phrase sur l'emploi des jeunes (éclatée en trois : TRA-jeunes-actifs + RES-reformes + ECO-enseignement-professionnel), « reprendre l'offensive » (EUR-industrie + EUR-numerique), et la formation universelle à l'IA (triplée sur exactement les trois mêmes cases que Philippe).

**Pronostic confirmé.** Le mémo prévoyait que le cas B deviendrait fréquent « quand les programmes afflueront ». Il l'est devenu dès le deuxième candidat : quatre cas nouveaux sur six lots. Le triplé IA est particulièrement net — deux candidats produisent indépendamment un verbatim transversal sur les mêmes trois sujets.

**Réponse structurelle possible** (à concevoir le jour venu) : référencer un même *bloc de texte* depuis plusieurs cases, plutôt que de le recopier — mécanisme plus fin que l'emprunt, qui opère au niveau de la position et non du sujet. Le coût de maintenance de la duplication manuelle est désormais réel : six cas, dont deux triplés.

---

## C. Dette structurelle de la base 2022

La base héritée de 2022 sous-couvre des domaines devenus centraux. Onze sujets ont dû être créés en réaction au seul programme Attal, un par un, exactement le mode de fonctionnement que ce mémo voulait éviter.

**Position du porteur au 27/08/2026** : l'intérêt d'un audit d'anticipation en une passe n'est pas démontré à ses yeux. La création réactive, sujet par sujet, reste le mode de travail retenu. La présente section est donc conservée comme inventaire des manques repérés, non comme plan d'action.

**Manques repérés au fil des lots Attal, non comblés** :
- attractivité de la recherche (« attirer les meilleurs chercheurs » logé faute de mieux dans `RES-effectifs-personnels`) ;
- adoption de l'IA par les entreprises (logée dans `NUM-reformes`) ;
- taille des classes au-delà du primaire (`ECO-eleves-par-classe` créé, mais son périmètre reste à préciser).

**Domaines à auditer** (inventaire du 24/08, inchangé) :
- IA et numérique : souveraineté du cloud, data centers et consommation électrique, IA et services publics, IA et création.
- Adaptation climatique : retrait-gonflement des argiles, littoral et trait de côte, forêts et incendies, santé et chaleur.
- Autres angles probables : logement et transition, économie de la mer, vieillissement.

**Sujets à supprimer ou fusionner** : certains sujets hérités sont fourre-tout ou redondants (`ENV-echelle-europeenne`, les multiples `-reformes` et `-plans`). Décision reportée sciemment.

**État de la fenêtre de renommage au 27/08/2026** : un seul ID est gelé, `ATT-capture-carbone`, parce qu'il est cité par l'unique analyse existante. Tous les autres restent renommables ou déplaçables sans risque. La fenêtre se refermera aux premiers contenus éditoriaux supplémentaires.

### C.1 Piste d'un onglet « Dette publique » — NOUVEAU

`ECN-dette-deficit` a reçu quatre mesures d'Attal dans une seule cellule — cible chiffrée, méthode de redressement, arbitrage entre postes, règle de campagne — ce qui en fait probablement la case la plus longue du site. Une cellule trop longue signale presque toujours un sujet trop large.

**Piste** : un onglet « Dette publique » découpant l'objet en trajectoire et cible, répartition de l'effort, gouvernance budgétaire, charge de la dette, dette et générations futures. Le mécanisme d'emprunt permettrait de garder le sujet visible depuis Economie sans duplication.

**Précaution** : ne pas instruire ce découpage sans regarder en même temps `EUR-dette`, `CON-regle-or-budgetaire` (où Philippe propose une règle d'or constitutionnelle) et `FPU-reformes`, qui gravitent autour du même objet et resteraient orphelins.

---

## D. Module « quiz à l'aveugle » / « je fabrique mon programme »

**Statut** : validé sur le principe, à construire plus tard. Le seuil se rapproche : avec deux candidats transcrits, plusieurs sujets portent désormais deux propositions écrites — mais deux candidats restent insuffisants pour un module de similitude.

**Deux variantes d'un même moteur** :
- *Quiz à l'aveugle* : sur des sujets tirés aléatoirement, les propositions sont présentées MÉLANGÉES et ANONYMISÉES. Le lecteur choisit celles qui lui parlent ; on lui révèle ensuite vers quels candidats penchent ses choix.
- *Je fabrique mon programme* : version exhaustive. Le visiteur parcourt les sujets et choisit pour chacun la proposition qui lui plaît, se constituant SON programme idéal. Analyse finale en POURCENTAGES DE SIMILITUDE avec chaque candidat.

**Pourquoi c'est cohérent** : masquer l'auteur force à juger l'idée et non son étiquette — antidote au réflexe partisan. Singularité par rapport aux boussoles électorales existantes (Smartvote, ex-Boussole présidentielle) : s'appuie sur les MOTS EXACTS des programmes écrits, pas sur des questions reformulées par un tiers.

**Décision d'architecture déjà prise** : NE PAS transformer le comparateur en outil anonyme. Le masquage d'auteur est réservé à ces modules ludiques, espaces de jeu clairement identifiés. Le comparateur reste le comparateur.

**Points à trancher au développement** :
- Nombre de sujets par session, présentation du résultat (classement ? graphique ? pourcentages ?).
- Ne tirer que des sujets où PLUSIEURS candidats ont une proposition écrite (exclure les « À venir »).
- Honnêteté méthodologique : assumer que c'est un jeu de découverte, PAS un conseil de vote.
- Anonymisation parfois illusoire : le style peut trahir l'auteur.
- Les verbatims sont souvent des fragments avec `[...]` et amorce reprise, peu lisibles hors du contexte de la grille. Le module devra soit sélectionner les verbatims autonomes, soit afficher la mesure entière.
- **Difficulté aggravée par le corpus Attal** : ses fragments dépendent d'amorces longues (« Nous devons devenir la première puissance d'Europe sur l'intelligence artificielle. Pour cela, nous allons [...] »). Un module de comparaison rapide sera difficile à alimenter avec ce type de matière.

---

## E. Filtrage des candidats

**Idée** : n'afficher que certains candidats dans les pages thématiques (masquer des colonnes), avec un choix posé DÈS LA PAGE D'ACCUEIL s'appliquant à toutes les thématiques (préférence globale persistante).

**DÉCISION ÉDITORIALE PRISE** : le filtrage est LIBRE, y compris l'affichage d'UN SEUL candidat. Assouplissement assumé du principe fondateur « ne jamais lire un candidat isolément » — le filtrage est temporaire et choisi, pas imposé.

**DÉCISION CONNEXE du 27/08/2026** : les colonnes « Candidat C » et « Candidat D », vides, sont CONSERVÉES, pour matérialiser la place des candidats à venir. Conséquence à surveiller : sur mobile, chaque colonne candidat occupe la largeur de l'écran, donc deux écrans de « À venir » à faire défiler après les deux candidats renseignés. C'est le premier argument concret en faveur du filtrage.

**À clarifier au développement** : filtre global (posé à l'accueil) vs filtre local (par thématique) — les deux peuvent coexister, mais définir la logique principale.

---

## F. Mode lecture anonymisé

**Idée** : un bouton de bascule « masquer / révéler les noms » affichant les colonnes sans les noms de candidats (Candidat A, B, C…), pour juger les propositions sans préjugé. C'est un MODE DE LECTURE du comparateur, distinct du filtrage et distinct du module quiz.

**Combinaison possible** : une barre d'outils en haut de chaque thématique réunissant le choix des candidats à afficher (filtrage) et le bouton « masquer les noms » (mode anonyme).

---

## G. Points d'attention design

**Page d'accueil** : le nid d'abeille compte 35 hexagones (36 thématiques moins Constitution, qui a sa bannière propre), sur 8 colonnes en grand écran. Les libellés « Climat — atténuation » et « Climat — adaptation » sont les plus longs de la série, avec une taille de police fixée en dur à 13 px. À surveiller lors des prochains ajouts de thématiques : au-delà d'un certain nombre, la grille devra passer à 9 colonnes ou réduire la taille des hexagones. *Aucune thématique ajoutée par les lots Attal — situation inchangée.*

**Plafonnement des cases longues — NOUVEAU.** Les cases de la grille sont plafonnées à 8 lignes (10 sur mobile), avec mention « Lire la suite ». Le corpus Attal produit des cellules à plusieurs mesures qui dépassent régulièrement ce seuil, `ECN-dette-deficit` en tête. Deux réponses possibles, à ne pas confondre : ajuster le plafonnement (cosmétique) ou scinder le sujet (structurel — voir C.1). La seconde est presque toujours la bonne.

---

## H. Conventions de transcription — précision à consigner au « Lisez-moi »

**Règle dégagée le 27/08/2026, non encore écrite dans le « Lisez-moi ».**

Lorsqu'un verbatim est un fragment emprunté à une énumération et qu'il atterrit dans une thématique éloignée de son contexte d'origine, l'amorce reprise doit **porter le sujet**, et pas seulement être grammaticalement correcte. La coupe la plus courte n'est pas la bonne si elle laisse le lecteur ignorer de quoi on parle.

Exemple : « [...] une véritable stratégie globale, qui va [...] à la préférence européenne dans les marchés publics [...] », placé dans l'onglet Europe, ne dit pas qu'il s'agit d'intelligence artificielle. L'amorce correcte est « [...] nous devons maîtriser toute la chaîne de l'IA. Cela exige de nous une véritable stratégie globale, qui va [...] ».

**Corollaire** : quand aucune amorce disponible ne rend le fragment lisible, trois issues seulement — changer la sélection du verbatim, le domicilier dans une thématique où le contexte est donné, ou ne pas le transcrire. Jamais ajouter un mot d'explication.

**Application faite** : deux fragments du chantier IA (volet énergie, volet approvisionnements) ont été écartés sur ce motif, étant par ailleurs du diagnostic sans mesure.
