## V41 — grille épurée

Les cases vides ne montrent plus de point central ; les noms des couleurs ne sont plus affichés dans les cases. Les indices et toutes les règles restent inchangés.

# Cogit

**Cogit** (anciennement ColorDigitLogic) est une application web indépendante permettant de recopier, compléter et vérifier des grilles de logique mêlant **nombres et couleurs**. Elle fonctionne sur ordinateur, tablette et téléphone, directement dans le navigateur.

**Version actuelle : V40** — application web installable (PWA), utilisable hors ligne après un premier chargement, avec solveur et contrôle immédiat des erreurs par rapport à la solution unique lorsqu’elle existe.

**Jouer :** https://pixou2000.github.io/ColorDigitLogic/

## V40 — nouveau nom et nouveau logo

- L’application s’appelle désormais **Cogit** (anciennement **ColorDigitLogic**).
- Nouveau logo sur l’accueil et nouvelles icônes PWA (`icon-192.png` et `icon-512.png`) : chiffres dans les cases, indices violet et rouge sans chiffre, indice numérique 5 conservé.
- Le titre du navigateur, le nom d’installation et le manifeste PWA sont mis à jour.
- L’URL GitHub Pages reste **https://pixou2000.github.io/ColorDigitLogic/** : aucun changement de dépôt n’est nécessaire.
- Les **clés localStorage** (`colordigitlogic_*`), les types JSON (`ColorDigitLogicResults`, `ColorDigitLogicRecords`) et le schéma des bibliothèques (`ColorDigitLogic-library-v1`) restent **inchangés** pour préserver l’historique, les records, les sauvegardes et la compatibilité des imports.
- Les exports nouvellement téléchargés portent le préfixe `Cogit` ; les anciens fichiers JSON restent importables.
- Les sept bibliothèques de grilles sont conservées sans modification.
- Lors d'une mise à jour d'une PWA déjà installée, l'ancienne icône peut rester visible temporairement à cause du cache du système ; si nécessaire, supprimer puis réinstaller le raccourci **après avoir exporté les résultats par précaution**.

## Correction V39 — records propres à chaque grille

- Le message « Record de la grille 2x3-0003 ! » n'apparaît que si la nouvelle victoire améliore le **nombre d'erreurs**, ou à erreurs égales le **temps** de la meilleure victoire antérieure sur cette grille.
- Le numéro de tentative n'intervient pas dans les records propres à une grille.
- Les records par format restent classés par **tentative**, puis **erreurs**, puis **temps** ; leur annonce reste prioritaire.
- Une première victoire sur une grille, sans nouveau record de format, affiche simplement « GAGNÉ ! ».

## Nouveautés V38 — records de grille et accueil

- Une victoire améliorant le classement général affiche **« Nouveau record format 2x3 ! »** (format adapté).
- Sinon, une victoire plus rapide qu'une victoire précédente sur le même numéro affiche **« Record de la grille 2x3-0004 ! »** (identifiant adapté).
- Une première victoire sur une grille, sans record de format, affiche uniquement **« GAGNÉ ! »**.
- Le record de format conserve les priorités **tentative minimale, erreurs minimales, temps minimal** ; le record de grille compare les temps des victoires sur le même identifiant.
- L'accueil présente le logo du jeu à côté du titre et une phrase décrivant son objectif.

## Correction V37 — annonce des records

- Le message « Nouveau record ! » est affiché **uniquement** si la victoire améliore réellement le record du format, selon les mêmes critères que le tableau : tentative minimale, erreurs minimales, puis temps minimal.
- Une première victoire sur un numéro de grille après plusieurs tentatives ne déclenche plus à tort « Nouveau record ! » si un meilleur record existe déjà sur le format.
- L’historique, les tentatives et les bibliothèques restent inchangés.

## Nouveautés V36 — tentative visible et correction immédiate des erreurs

- Le numéro de tentative d’une grille de bibliothèque apparaît dans la barre de jeu, à côté de son identifiant, et pas seulement dans un élément masqué de l’ancienne interface.
- Lorsqu’une saisie de chiffre ou de couleur est incorrecte, elle est **annulée immédiatement** : la valeur précédente de ce champ est conservée, l’autre champ de la case n’est pas modifié.
- Un **cadre rouge** reste sur la case fautive jusqu’à une saisie correcte sur cette case ; le message « ERREUR 1/3 » ou « ERREUR 2/3 » apparaît brièvement sur la grille.
- Une erreur n’est comptée qu’une fois et ne peut plus être recomptée lors d’une saisie correcte ailleurs.
- À la troisième erreur, la partie est perdue et enregistrée dans l’historique, comme en V34/V35.
- Les sept bibliothèques, le classement des records et l’historique sont conservés.

## Nouveautés V35 — numéro de tentative et priorité des records

- Lors du lancement d’une grille de bibliothèque, affichage de « Grille 2x3-0003 — Tentative 2 » sur l’écran de jeu, y compris en mode « Non encore résolue ».
- Les records des parties gagnées sont désormais classés par **tentative minimale**, puis **erreurs minimales**, puis **temps minimal**.
- La table des records affiche le numéro de tentative lorsqu’il est connu.
- Les historiques importés sont fusionnés et les numéros de tentative recalculés dans l’ordre chronologique des parties connues.
- Pour les anciens records sans numéro de tentative vérifiable, celui-ci reste « inconnu » ; il n’est pas inventé.
- Les défaites restent enregistrées et ne sont jamais admissibles comme records.

## Nouveautés V34 — défaites et tentatives

- Une partie perdue à la troisième erreur est enregistrée dans l’historique avec le résultat **PERDU** et son temps d’arrêt.
- L’historique affiche **Résultat** et **Tentative**. Les tentatives sont numérotées chronologiquement pour chaque identifiant de grille de la bibliothèque (1, 2, 3, etc.).
- Une grille perdue reste proposée par le mode « Non encore résolue » ; seule une victoire la retire de cette sélection.
- Les défaites ne comptent pas pour les records. Les anciennes parties sans résultat explicite sont considérées comme gagnées.
- Les exports et imports de résultats conservent les défaites et les tentatives, calculées à partir des parties enregistrées.

## Nouveautés V33 — messages sur la grille et limite d’erreurs

- **Victoire** : affichage « GAGNÉ ! » en superposition au centre de la grille, avec le temps, le nombre d’erreurs et l’éventuel nouveau record.
- **Erreur** : message temporaire « ERREUR 1/3 » ou « ERREUR 2/3 » directement sur la grille (environ 1,1 seconde).
- **Troisième erreur** : affichage permanent « PERDU » et « 3 erreurs sur 3 » ; arrêt du chronomètre et verrouillage de la partie. Une partie perdue n’est pas enregistrée comme une victoire et ne marque pas la grille de bibliothèque comme résolue.
- Le compteur d’erreurs affiche désormais `Erreurs : 0/3` à `3/3`.
- Les grilles, bibliothèques, résultats précédents et modes de jeu V32 sont conservés.
- La limite s’applique aux erreurs détectées immédiatement lors de la saisie (solution unique connue ou indice voisin contredit). Si le solveur ne peut pas certifier une solution unique, le contrôle reste limité aux indices vérifiables.

## Nouveautés V32 — bibliothèque fixe

- 710 grilles numérotées : 110 en 2×3 et 100 dans chacun des six autres formats.
- Sur l'accueil, sélectionner un format puis choisir une grille au hasard, par numéro, ou la première non encore résolue **sur cet appareil**.
- Les résultats enregistrent le numéro de grille de bibliothèque ; il figure dans l'historique et les exports JSON.
- Les sept fichiers `grilles/*.json` doivent être publiés sur GitHub Pages avec `index.html`.
- Les grilles de la bibliothèque sont des puzzles prêts à jouer, tandis que le générateur aléatoire et le mode préparation restent disponibles.
- Les historiques restent locaux à chaque navigateur : le statut « non encore résolue » ne se synchronise pas automatiquement entre appareils.
- La difficulté de la bibliothèque reste provisoire. Les grilles sont issues du générateur V1 et ne contiennent pas d'indices négatifs.

## Fonctionnalités

- Grilles de plusieurs formats : **2×3, 3×3, 3×4, 4×4, 4×5, 5×5 et 5×6**.
- Démarrage sur une grille vide **2×3**.
- **Mode préparation** : saisie des indices situés entre les cases (sommes numériques ou mélanges de couleurs), y compris les indices négatifs. Les emplacements laissés vides ne comportent pas d'indice.
- **Mode jeu** : saisie des nombres et couleurs dans les cases.
- Palettes adaptées à la taille de la grille, avec les couleurs dans l'ordre **bleu, rouge, jaune, blanc, noir**, suivies des mélanges disponibles.
- Annulation, effacement de la sélection et vérification de la grille.
- Chronomètre avec pause, reprise et remise à zéro ; mémorisation de records par format de grille sur l'appareil.
- Sauvegarde locale et **import/export JSON** pour conserver une grille et son temps écoulé.
- Interface adaptée aux écrans tactiles ; fond gris autour du plateau pour distinguer les cases blanches.

## Utilisation

### 1. Préparer une grille

1. Choisir le format souhaité dans le menu **Format**.
2. Cliquer sur **Nouvelle grille vide** si nécessaire.
3. En mode préparation, sélectionner un emplacement entre deux cases, puis choisir son indice numérique ou coloré.
4. Utiliser l'option d'indice négatif pour indiquer qu'une somme ou un mélange est **interdit**.
5. Laisser vides les emplacements sans indice. Un second clic sur la même valeur permet d'effacer un indice saisi par erreur.

### 2. Résoudre la grille

1. Cliquer sur **Passer en mode jeu**.
2. Sélectionner une case et lui attribuer un nombre et une couleur.
3. Utiliser **Annuler** ou **Effacer la sélection** si nécessaire.
4. Cliquer sur **Vérifier** pour contrôler les contraintes de la grille.

Le chronomètre démarre au passage en mode jeu et peut être mis en pause ou repris.

### 3. Sauvegarder ou transférer une partie

- **Sauvegarder sur cet appareil** : conserve la grille dans le stockage local du navigateur.
- **Recharger la sauvegarde** : récupère cette sauvegarde locale.
- **Exporter en fichier JSON** : télécharge une copie de la grille, incluant le temps écoulé.
- **Importer une grille JSON** : recharge un fichier précédemment exporté, y compris sur un autre appareil.

Les sauvegardes locales et les records **ne se synchronisent pas automatiquement** entre appareils. Pour transférer une partie, utiliser le fichier JSON.

## Installer Cogit sur iPhone ou iPad

1. Ouvrir https://pixou2000.github.io/ColorDigitLogic/ dans **Safari**.
2. Toucher le bouton **Partager**.
3. Choisir **Sur l'écran d'accueil**, puis **Ajouter**.
4. Lancer Cogit depuis l'icône ajoutée.

L'application est conçue pour fonctionner **hors ligne après un premier chargement en ligne**. Pour vérifier : ouvrir l'application une première fois, fermer l'application, activer le mode Avion et la relancer depuis son icône.

## Installation sur GitHub Pages

Le projet comprend cinq fichiers à placer à la racine du dépôt :

| Fichier | Rôle |
| --- | --- |
| `index.html` | Interface, styles et logique du jeu |
| `manifest.webmanifest` | Informations nécessaires à l'installation de la PWA |
| `sw.js` | Mise en cache pour l'utilisation hors ligne |
| `icon-192.png` | Icône de l'application (192 px) |
| `icon-512.png` | Icône de l'application (512 px) |

Pour publier une nouvelle version, remplacer les fichiers modifiés dans le dépôt GitHub, puis attendre la mise à jour de GitHub Pages. Le cache de la PWA peut nécessiter un rechargement ou une mise à jour pour afficher la dernière version.

## Structure du code

Le fichier `index.html` regroupe trois technologies :

- **HTML** : éléments de l'interface (plateau, boutons et palettes).
- **CSS**, dans la balise `<style>` : apparence et adaptation aux tailles d'écran.
- **JavaScript**, dans la balise `<script>` : construction de la grille, interactions, vérifications, chronomètre et sauvegardes.

Le code peut être consulté et modifié avec **Visual Studio Code**. Pour mettre le fichier en forme : **Shift + Option + F** sur Mac. Pour prévisualiser ce README : **Cmd + Shift + V**.

## Évolutions possibles

- Ajouter un solveur automatique.
- Expliquer les déductions étape par étape.
- Améliorer la validation des grilles et la détection de solutions uniques.

---

*Projet personnel indépendant, non affilié au jeu ColorDigitLogic d'origine.*

## Indépendance du projet

ColorDigitLogic est un projet personnel indépendant, non affilié aux créateurs du jeu Acrylogic. Les grilles d’origine ne sont pas distribuées avec cette application.


## Version 16 — Contrôle des erreurs

En mode jeu, la saisie d'un chiffre ou d'une couleur est comparée aux indices voisins dès que les deux valeurs nécessaires sont renseignées. Toute nouvelle contradiction incrémente le compteur d'erreurs. Le compteur est inclus dans les exports JSON et les sauvegardes locales. Annuler une action ne retire pas les erreurs déjà commises.


## Version 17 — Solveur (étape 1)

Le bouton **Résoudre** cherche une affectation des paires chiffre-couleur respectant tous les indices, les cases déjà saisies et l'unicité de chaque paire. Il recherche jusqu'à deux solutions pour distinguer une solution unique de plusieurs solutions, avec une limite de 7 secondes. Une solution trouvée peut être affichée après confirmation. Le calcul s'effectue localement dans le navigateur.

## Version 18 — Vérification par solution unique

Au passage en **mode jeu**, l'application calcule une solution de référence à partir des **indices seuls**, en ignorant volontairement toutes les valeurs déjà saisies dans les cases. Si une seule solution est trouvée et que la recherche se termine sans dépasser le délai, chaque chiffre et couleur nouvellement saisi est immédiatement comparé à cette solution.

- Une saisie incorrecte augmente le compteur d'erreurs **une seule fois**, même si elle contredit également un indice.
- Cliquer une deuxième fois sur une valeur déjà présente ne compte pas comme une nouvelle saisie.
- Les erreurs sont comptabilisées même si les cases voisines sont encore vides.
- Si plusieurs solutions existent, si aucune solution n'existe ou si le calcul dépasse 7 secondes, seul le contrôle des indices voisins est appliqué.
- Modifier les indices invalide la solution de référence. Elle est recalculée lors du prochain passage en mode jeu.
- Le bouton **Résoudre** continue de tenir compte des valeurs actuellement présentes dans les cases, contrairement au calcul de la solution de référence.
- Les sauvegardes JSON et les records restent compatibles avec les versions précédentes.

**Limite connue :** la recherche s'exécute dans le navigateur ; sur une grille difficile, l'interface peut être momentanément occupée pendant le calcul.


## Version 19 — Générateur de grilles

Le bouton **Générer une grille** crée une répartition aléatoire de toutes les paires chiffre-couleur, calcule un indice par frontière (somme ou mélange), puis utilise le solveur pour rechercher une grille à solution unique. Une fois cette unicité établie, il retire des indices tant que l'unicité reste démontrée.

- Les cases sont **vides** dans la grille créée : il faut passer en mode jeu pour la résoudre.
- Les grilles ne sont annoncées comme **uniques** que lorsque le solveur a terminé la vérification sans dépasser son délai.
- Si la recherche échoue, la grille en cours est conservée.
- Le générateur travaille localement dans le navigateur, sans serveur.
- Le résultat est exportable en JSON comme les autres grilles.
- **Limites :** la génération peut prendre plusieurs secondes, notamment en 5×6 ; la difficulté n'est pas encore calibrée, et la suppression des indices est une heuristique, pas une minimisation garantie.


## V20 — Fin de partie automatique et records

Lorsque la grille est entièrement remplie et que **chaque chiffre et chaque couleur** correspond à la solution unique calculée à partir des indices, la partie est automatiquement terminée :

- Le chronomètre s'arrête immédiatement après la dernière saisie correcte.
- Un message « Grille résolue ! » affiche le temps et le nombre d'erreurs.
- Le record du format de grille est mis à jour si le temps est meilleur, et son affichage est actualisé sans recharger la page.
- Le bouton « Vérifier » reste disponible pour les grilles incomplètes ou les situations sans solution unique confirmée.
- Une solution **affichée par le bouton Résoudre** ne donne pas droit à un record.

**Limite :** la fin automatique suppose qu'une solution unique ait été calculée. Si la recherche est indéterminée ou si la grille a plusieurs solutions, le contrôle des indices reste disponible.


## V21 — Records partageables entre appareils

Un **tableau des records** affiche le meilleur temps pour chaque format, avec le nombre d'erreurs et la date. Deux nouvelles commandes permettent d'**exporter** les records dans `ColorDigitLogic_records.json` et de les **importer** sur un autre appareil (Mac, iPad ou iPhone), par exemple via iCloud Drive.

- L'importation **fusionne** les records : seul le meilleur temps de chaque format est conservé. En cas d'égalité, le record local est conservé.
- Les anciens records enregistrés dans `localStorage` par les versions précédentes sont repris automatiquement. Leur **date et nombre d'erreurs sont inconnus** et sont affichés par « — ».
- Les nouveaux records comprennent le temps en millisecondes, le nombre d'erreurs et la date ISO.
- Le fichier exporté est distinct des fichiers JSON des grilles. Les records restent disponibles localement après l'export.
- La synchronisation **n'est pas automatique** : il faut exporter et importer le fichier lorsqu'on souhaite transférer les meilleurs temps entre appareils.
- Le stockage local peut être effacé par le navigateur ; conserver une copie du JSON dans iCloud Drive est recommandé.

**Format JSON** : `{ "type": "ColorDigitLogicRecords", "version": 1, "exportedAt": "...", "records": { "2x3": { "timeMs": 154000, "errors": 1, "date": "..." } } }`.


## V22 — Historique complet des parties

Chaque **partie terminée normalement** est enregistrée dans le stockage local du navigateur avec un identifiant unique, la date, le format de grille, le temps et le nombre d'erreurs. Les parties simplement commencées, abandonnées ou révélées par le solveur ne sont pas enregistrées comme réussites.

- Un tableau affiche les 100 dernières parties, avec les statistiques globales (nombre de parties, temps moyen, erreurs moyennes).
- Les records par format sont conservés.
- **Exporter les résultats (JSON)** crée `ColorDigitLogic_resultats.json`, qui contient toutes les parties enregistrées, même celles au-delà des 100 dernières affichées, ainsi que les anciens records.
- **Importer des résultats JSON** fusionne les parties de plusieurs appareils par identifiant unique et évite de compter deux fois une partie déjà importée.
- L'importation des anciens fichiers `ColorDigitLogic_records.json` (V21) reste possible, mais ils ne contiennent pas l'historique des parties.
- L'export/import est **manuel** : placer le fichier dans iCloud Drive facilite le transfert, mais ne crée pas de synchronisation automatique.
- Les parties effectuées avant la V22 ne peuvent pas être reconstituées à partir des seuls records.

**Important :** les statistiques sont basées sur les parties terminées, et non sur toutes les tentatives commencées. Le classement par niveau de difficulté sera ajouté ultérieurement, lorsque l'évaluateur de difficulté sera disponible.


## V23 — Interface par écran

- Accueil : format, grille vide, génération, chargement local ou import JSON, historique et records.
- Préparation : grille et palette d’indices immédiatement dessous, bouton Jouer ; commandes secondaires dans Options sur téléphone ou à droite sur écran large.
- Jeu : grille et palette chiffres/couleurs sous la grille, chronomètre et erreurs en bandeau compact ; commandes secondaires dans Options.
- Historique : écran dédié avec statistiques, records et import/export des résultats.
- Taille des cases calculée selon l’espace disponible et le format de grille.
- Le moteur de jeu, le solveur, les sauvegardes et l’historique restent inchangés.

**Attention :** le retour à l’accueil ne supprime pas la grille en cours ; elle reste en mémoire tant que la page n’est pas rechargée. Utiliser « Sauvegarder sur cet appareil » pour la conserver après fermeture.


## V24 — Génération suivie et lancement direct

- Un écran de progression reste visible pendant la génération, avec tentative en cours, temps écoulé et nombre d'indices examinés. La barre représente le temps consommé dans le budget de génération, **pas** un pourcentage garanti d'achèvement.
- Le résultat final est affiché, y compris en cas d'échec (bouton Continuer pour revenir à l'accueil).
- Lorsqu'une grille est générée, l'application ouvre directement le **mode jeu** et démarre le chronomètre. Le résultat de génération reste visible dans le message de statut.
- Les boutons **Pause/Reprendre** et **Exporter** sont accessibles directement dans la barre du mode jeu, sur mobile et ordinateur.
- Les commandes secondaires restent dans Options sur mobile.


## V25 — Nombre d’indices dans les résultats

- Affichage permanent du nombre d’indices effectivement présents dans la grille, en préparation et en jeu (indices positifs et négatifs comptés chacun pour un).
- Ajout de la colonne **Indices** dans l’historique des parties.
- Chaque nouvelle partie terminée enregistre `clueCount` avec le format, la durée, les erreurs et la date.
- Les sauvegardes et exports de grille contiennent `clueCount` à titre informatif ; au chargement, le nombre est recalculé depuis `clues`, source de vérité.
- Export des résultats au format version 3, avec import compatible avec les fichiers des versions 2 et 3.
- Les anciennes parties n’ayant pas enregistré le nombre d’indices affichent « — » : cette donnée ne peut pas être reconstituée depuis les seuls résultats historiques.


## V26 — Classement des records par erreurs, puis temps

Le record d’un format est désormais la partie avec **le moins d’erreurs**, puis, à égalité d’erreurs, **le temps le plus court**. Cette règle s’applique aux nouvelles parties, à l’importation et à la fusion des historiques.

Les records anciens dont le nombre d’erreurs est inconnu ne sont plus assimilés à zéro erreur. Ils restent visibles jusqu’à l’obtention d’un résultat comparable avec un nombre d’erreurs connu. L’historique des parties n’est pas modifié.


## V28 — Règles à l’accueil et évaluation automatique

- La page d’accueil présente le but et les règles : unicité des paires chiffre-couleur, sommes, mélanges et indices négatifs.
- Lors du passage en **mode jeu**, qu’il soit manuel ou consécutif à une génération, la difficulté est évaluée automatiquement et affichée dans le bandeau de jeu (1 à 5). Le détail est disponible dans la zone de messages.
- L’évaluation est calculée à partir des indices de la grille, indépendamment des réponses déjà saisies.
- Le niveau est enregistré avec chaque partie terminée et apparaît dans l’historique. Les anciennes parties sans niveau affichent « — » ; l’importation de leurs fichiers reste possible.
- **Attention :** l’évaluateur V27/V28 est encore une estimation provisoire fondée sur des propagations de contraintes. Il ne distingue pas encore rigoureusement les cinq techniques progressives prévues ; le niveau 5 peut signifier simplement que ces techniques sont insuffisantes.


## V29 — Exemple visuel sur la page d’accueil

Entre « But du jeu » et « Règles », ajout d’un exemple statique 2×3 montrant côte à côte la grille à compléter et sa solution. Les indices sont identiques dans les deux grilles. Les six combinaisons chiffre-couleur sont utilisées exactement une fois. Cet exemple est purement illustratif et ne modifie ni la partie ni le stockage.


## V30 — Exemples visuels des mélanges

- L’exemple 2×3 sur l’accueil présente maintenant un indice **violet** entre deux cases de couleurs bleue et rouge. Tous les indices de l’exemple correspondent à la solution affichée.
- Les règles comportent un tableau visuel des mélanges : deux cases colorées, puis leur indice sous forme de cercle. Les 15 exemples couvrent les mélanges de couleurs primaires, le blanc neutre, le noir dominant et les paires de couleurs identiques.
- Aucun changement de logique de jeu ni de format de sauvegarde.


## V31 — Clarification de l’exemple sur l’accueil

- Déplacement de la règle d’unicité des combinaisons chiffre + couleur immédiatement après le but du jeu, avant la grille 2×3.
- Légende visuelle des trois indices (numérique, couleur, négatif) sous la grille d’exemple.
- Le dernier indice numérique de l’exemple est désormais un **indice négatif 4** (la somme réelle de la dernière ligne est 5), avec un contour rouge, dans les deux vues de la même grille.
- Les autres règles et les exemples de mélanges sont conservés.


## V42 — Compteurs dans les palettes de jeu

Les palettes des chiffres et des couleurs (sous la grille en mode jeu) affichent des points gris foncé représentant les placements encore disponibles. Pour un format 2×3, chaque chiffre a initialement 2 points et chaque couleur 3 points. Les points sont actualisés après chaque saisie correcte, effacement, annulation ou chargement. Les couleurs de la palette sont désormais carrées. Les indices et la grille ne changent pas.


## V43 — Palettes épuisées
Quand un chiffre ou une couleur n’a plus de placements disponibles, son bouton de palette devient entièrement gris et son contenu est masqué. Il reste possible de le sélectionner pour modifier une case déjà renseignée.

## V44 — Rejouer et double chronométrage
- Après trois erreurs, bouton Rejouer ? : mêmes indices et identifiant, grille vide, erreurs et chronos remis à zéro.
- Temps effectif suspendu hors écran de jeu, onglet masqué ou fenêtre sans focus ; reprise automatique. Temps écoulé depuis le départ, interruptions comprises.
- Compteur d’interruptions, bilan et historique enrichis ; records fondés sur le temps effectif comme auparavant.
- Sauvegardes JSON et locales : reprise des chronos et du compteur. Anciennes sauvegardes : temps effectif conservé, temps écoulé et interruptions inconnus.
- Aucun mode Campagne dans cette version.

## V45 — Plusieurs sauvegardes locales

Liste des parties sauvegardées, compteur dynamique, date de dernière sauvegarde, reprise et suppression individuelle. Migration de la sauvegarde unique V44. Une partie terminée est retirée de la liste.
