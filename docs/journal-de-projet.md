# Journal de projet — comparateur-croquettes

> Mémoire du projet : décisions, choix, difficultés, solutions, tests, compétences mobilisées.
> Format des décisions : Décision → Raisons → Alternatives écartées → Conséquences.
> Ne contient que des éléments réellement décidés ou réalisés.

## Sommaire
1. Analyse des documents
2. Cadrage
3. Conception
4. Mise en place du projet
5. Développement
6. Tests
7. Difficultés rencontrées et solutions
8. Veille technologique et sécurité
9. Compétences du référentiel mobilisées
10. Évolutions futures

---

## 1. Analyse des documents

### Documents analysés
- Brief CEF « Préparation Examen TP DWWM ».
- REAC et RE du titre DWWM (TP-01280, millésime 2023).
- Dossier de projet d'exemple d'une promotion précédente.

### Constats (brief + REAC/RE)
- Compétences obligatoires dans le dossier : CP2, CP3, CP4 (front) ; CP5, CP6, CP7 (back).
  CP1 et CP8 évaluées en entretien technique ; CP1 et CP5 également au questionnaire professionnel (doc technique en anglais).
- Épreuve réelle : présentation 35 min, entretien technique 40 min, questionnaire 30 min, entretien final 15 min.
  Devoir CEF : présentation orale de 45 min.
- Dossier : 30 à 50 pages hors garde, sommaire et annexes ; annexes ≤ 30 pages ; dossier imprimé lu par le jury avant l'oral.
- Projet réalisé en formation → plan RE : compétences, expression des besoins, environnement technique, réalisations.
  Choix : enrichir la partie « réalisations » avec les éléments du plan « projet en entreprise » (critères d'évaluation identiques).
- Critères souvent oubliés : POO côté serveur (CP7), NoSQL (CP6), utilisateurs SQL et droits, sauvegarde/restauration (CP5),
  tests unitaires et de sécurité par composant, documentation en anglais, site publié et référencé (CP3), conteneurs (CP1).

### Constats (dossier d'exemple)
- Structure conforme au plan « entreprise » du RE ; environ 30 pages de corps + environ 15 pages d'annexes.
- À reprendre : format du jeu d'essai (entrée / attendu / obtenu / écarts, avec défaut corrigé), format de la veille sécurité.
- À dépasser : absence de base relationnelle (CP5), logique métier dans les contrôleurs (CP7 / POO),
  absence de documentation en anglais et de procédure de déploiement.

---

## 2. Cadrage

### Décision : un seul projet présenté dans le dossier
- Raisons : cohérence du dossier ; couverture des 6 compétences obligatoires par un projet complet.
- Alternative écartée : dossier multi-projets.
- Conséquences : le projet doit couvrir à lui seul l'ensemble des compétences obligatoires.

### Décision : périmètre limité aux croquettes pour chiens
- Raisons : maîtriser le volume de données et la complexité.
- Alternatives écartées (reportées en évolutions futures) : autres aliments, friandises, chats, autres animaux.
- Conséquences : exigence de conception → modèle de données extensible (espèce, type d'aliment).

### Décision : comptes utilisateurs (favoris, comparaisons sauvegardées)
- Raisons : besoin utilisateur ; démonstration de l'authentification, des rôles et du RGPD.
- Conséquences : gestion des données personnelles, suppression de compte, sécurisation de l'authentification.

### Décision : définition de « commercialisé en France »
- Règle : produit étiqueté en français, vendu dans au moins un point de vente physique en France
  ou sur un site marchand exploité par une entité établie en France (y compris le site français de la marque).
- Raisons : critère objectif et vérifiable, conforme à l'exclusion des produits vendus uniquement sur des sites étrangers.
- Conséquences : un produit vendu uniquement sur un site d'une entité étrangère (ex. zooplus.fr) ne serait pas éligible ; cas à trancher s'il se présente.

### Décision : stratégie de données
- Sources : étiquetage officiel (site de la marque) et Open Pet Food Facts (ODbL), utilisé au maximum.
- Raisons : aucune API publique documentée trouvée pour les marques ; scraping écarté (CGU, droit des bases de données, fragilité).
- Alternatives écartées : API des marques (inexistantes à notre connaissance), scraping.
- Conséquences :
  - vérification de chaque fiche contre l'étiquette officielle (statut vérifié / non vérifié) ;
  - traçabilité : source, URL, date de consultation ;
  - attribution Open Pet Food Facts visible dans l'interface ; partage à l'identique (ODbL) des données dérivées ;
  - pas de photos de produits dans le MVP (droits sur les packagings).

### Décision : prix gérés sous forme de relevés datés
- Modèle : format, prix, type (PPC marque / vente directe marque / prix revendeur), source, date ; prix au kilo calculé.
- Sources retenues : sites des marques, Zooplus (si le produit est vendu dans un autre circuit éligible), Maxi Zoo, Truffaut, Animalis.
- Raisons : le budget est un critère majeur ; PPC non systématiquement publiés ;
  choix de périmètre centré sur le circuit spécialisé et la vente en ligne (voir étude des circuits d'achat).
- Alternative écartée : sources de la grande distribution (reportées en évolution future).
- Conséquences : relevés manuels ; une marque sans relevé de prix possible dans les sources retenues est écartée de la sélection.

### Décision : volume cible de 30 à 45 produits
- Principe de sélection : couvrir des segments communs à plusieurs marques (stade de vie, gabarit, stérilisé/light, digestion sensible),
  puis popularité (indicateur : classements « meilleures ventes » des revendeurs, datés), puis disponibilité des données.
- Raisons : rendre les comparaisons pertinentes ; volume réaliste pour une saisie vérifiée.
- Conséquences : production d'une matrice marque × segment documentée.

### Décision : exclusion des aliments vétérinaires
- Règle : exclusion des aliments diététiques destinés à des pathologies et des gammes distribuées exclusivement par les vétérinaires.
- Raisons : usage sur prescription ; hors du besoin d'un propriétaire qui compare librement.
- Conséquences : exclusion par gamme (ex. Hill's Prescription Diet, Royal Canin Veterinary) ; cas de Virbac Veterinary HPM à vérifier.

### Décision : exclusion des marques propres de la grande distribution
- Règle : exclusion des marques appartenant aux enseignes de grande distribution ;
  les marques propres des enseignes spécialisées (animaleries, jardineries) sont retenues.
- Raisons : périmètre centré sur les circuits spécialisés et la vente en ligne ; limitation du volume de données.
- Conséquences : les marques propres vendues uniquement sur un site d'une entité étrangère (ex. Zooplus)
  restent hors périmètre selon la définition de « commercialisé en France ».

### Décision : repository GitHub public
- Raisons : consultation par le mentor et le jury ; transparence de l'historique ; valeur de portfolio.
- Alternative écartée : dépôt privé avec accès partagé.
- Conséquences :
  - aucun secret versionné (`.env` ignoré, `.env.example` fourni) ; tout secret exposé doit être révoqué ;
  - détection de secrets et alertes de dépendances activées ;
  - jeux d'essai sans données personnelles réelles ;
  - licences distinctes à définir pour le code et pour les données dérivées d'Open Pet Food Facts ;
  - historique de commits soigné, car il fait partie du livrable.

### Décision : déploiement documenté mais non réalisé pour le devoir
- Raisons : modifications attendues après la correction du mentor ; déploiement réel avant l'envoi du dossier final.
- Conséquences :
  - le dossier du devoir présente le déploiement comme documenté, non réalisé ;
  - application conçue pour être déployable (variables d'environnement, conteneurs, scripts) ;
  - critères CP3 « publié de manière sécurisée » et « visible sur les moteurs de recherche » couverts au déploiement final.

### Décision : périmètre fonctionnel (premier jet validé)
- Rôles : Visiteur, Membre, Administrateur.
- MVP : recherche et filtres multicritères ; fiche produit sourcée ; comparateur de 2 à 4 produits (prix au kilo, affichage sur matière sèche) ;
  comptes (inscription, connexion, suppression, favoris, comparaisons sauvegardées) ;
  back-office (marques, gammes, produits, référentiels, relevés de prix) ;
  import assisté depuis Open Pet Food Facts (à confirmer en conception) ; pages légales ; accessibilité RGAA ; responsive.
- Complémentaires : recherches sauvegardées, réinitialisation du mot de passe par e-mail, historique des prix, export d'une comparaison.

### Décision : pas de Vue.js
- Stack envisagée (non arrêtée, décision en phase 3) : React, Node/Express ou Symfony, MySQL, MongoDB, Docker en développement.

### Points ouverts
- Choix de stack définitif (phase 3).
- Rôle exact de MongoDB (import Open Pet Food Facts envisagé).
- Licence du code.
- Marques propres des animaleries.

### Décision : Zooplus retenu comme source de prix
- Règle : Zooplus sert de source de prix pour un produit vendu également dans au moins un autre circuit éligible.
- Raisons : site très utilisé par les propriétaires en France ; l'éligibilité du produit reste jugée indépendamment de la source de prix.

### Étude : circuits d'achat de l'alimentation pour chiens en France
- Baromètre FACCO-Odoxa 2025 (source primaire, enquête propriétaires) : la grande distribution reste le premier lieu d'achat
  (50 % des propriétaires de chiens, 44 % en lieu principal) ; animalerie : 32 % ; achats en ligne : 28 %, en stabilisation.
- Synthèse de marché (source secondaire, à vérifier) : marché de 5,7 Md€ en 2024 ; grande distribution 48,6 %,
  e-commerce 24,6 %, animaleries et jardineries 22,4 %, vétérinaires et éleveurs 4,4 %.
- Conclusion : l'hypothèse « achat majoritairement en circuit spécialisé » n'est pas confirmée à l'échelle du marché.
  L'exclusion de la grande distribution est un choix de périmètre, pas un reflet du marché.
- Utilité pour le dossier : contexte et problématique (poids du marché, place d'Internet comme deuxième circuit en valeur).

### Décision : retrait de Pedigree et Friskies
- Raisons : marques principalement distribuées en grande distribution, hors des sources de prix retenues ;
  cohérence du périmètre (éviter des produits sans prix dans le comparateur).
- Alternative écartée : ajout d'une source de prix de la grande distribution (plus de relevés, périmètre moins cohérent).
- Conséquences : disponibilité de Purina ONE et Ultima dans les sources retenues à vérifier lors de la sélection.

### Décision : aucune licence de code pour l'instant (tous droits réservés)
- Raisons : projet destiné à être déployé et potentiellement exploité ; choix réversible.
- Alternatives écartées : MIT (réutilisation libre, y compris commerciale, irréversible pour les versions publiées) ;
  GPL (obligation de publier les dérivés sous GPL).
- Conséquences : mention « Tous droits réservés » dans le README ; code consultable mais non réutilisable ;
  données dérivées d'Open Pet Food Facts soumises à l'ODbL indépendamment ; choix à réexaminer avant l'envoi du dossier final.

### Décision : plan du dossier de projet
- Plan retenu : plan « projet en formation » du RE (compétences, expression des besoins, environnement technique, réalisations),
  avec une partie « réalisations » détaillée selon les éléments du plan « projet en entreprise », puis un bilan.
- Raisons : conformité au RE pour un projet personnel ; couverture explicite des critères d'évaluation du jury.
- Conséquences : « présentation de l'entreprise » remplacée par le contexte personnel du projet ; plan révisable.

### Étude : analyse de l'existant (septembre 2026)
- Sites examinés : Une gamelle au top, macroquette.com, Le Bon Choix Croquettes, Gangdesmoustaches.fr,
  Mes-Croquettes.com (via extraits de recherche), Open Pet Food Facts.
- Constats principaux :
  - Une gamelle au top : environ 6 500 références (chiens/chats, croquettes/pâtées), sans notes, filtres nombreux,
    valeurs brutes et sur matière sèche, source et date par produit (dates 2019-2020 dans l'échantillon consulté), aucun prix.
  - macroquette.com : notation fondée sur les publications FEDIAF, questionnaire (âge, poids, stérilisation, activité, race,
    morphologie, gabarit) renvoyant 3 à 10 résultats, option qualité-prix ; page non modifiée depuis fin 2020.
  - Le Bon Choix Croquettes : comparaison de 8 marques sur 6 critères, prix au kilo relevé et daté, classement par avis clients,
    liens d'affiliation.
  - Gangdesmoustaches.fr : classements par score maison (23 critères).
  - Mes-Croquettes.com : outil d'analyse de valeurs saisies par l'utilisateur.
- Conclusions :
  - la comparaison sur matière sèche n'est pas un élément différenciant (fonction conservée) ;
  - le questionnaire de présélection existe déjà ailleurs (évolution future conservée) ;
  - combinaison non observée chez les concurrents : sélection côte à côte de produits, prix par format et prix au kilo
    au niveau produit, traçabilité datée de chaque donnée, comptes utilisateurs ;
  - la fraîcheur des données est un problème du secteur ; le coût de maintenance des données est un risque pour une exploitation réelle.

### Décision : aucune note ni classement subjectif
- Règle : l'application n'attribue aucune note, aucun score et aucun classement de qualité ; seules des données factuelles
  sourcées ou des valeurs calculées selon une formule documentée sont affichées.
- Raisons : neutralité ; les scores des concurrents reposent sur des méthodes propres et discutables ; limitation des risques juridiques.
- Alternative écartée : score de qualité maison.

### Décision : positionnement du projet
- Positionnement : comparateur factuel, centré sur le marché français (circuit spécialisé et vente en ligne),
  permettant de mettre côte à côte des produits précis avec leur coût réel (prix au kilo par format, relevé et daté)
  et la source de chaque donnée.
- Raisons : combinaison non observée chez les concurrents analysés (sélection de produits côte à côte,
  prix au niveau produit, traçabilité datée, comptes utilisateurs).
- Alternatives écartées : catalogue exhaustif, score de qualité, questionnaire comme fonction principale.

### Livrable : expression des besoins v1.0
- Fichier : `docs/expression-des-besoins.md`.
- Contenu : contexte, problématique, objectifs, rôles et personas fictifs, périmètre, 20 règles métier,
  5 parcours, 22 user stories MVP avec critères d'acceptation, 5 user stories complémentaires,
  9 exigences non fonctionnelles, contraintes, hypothèses et points ouverts.
- Statut : validé le 24/09/2026 (v1.1) — seuil d'ancienneté des prix fixé à 90 jours ; au moins un relevé de prix
  obligatoire pour publier un produit ; états Brouillon / Publié / Archivé ; personas et indicateurs de réussite validés.

---

## 3. Conception

### Issue #3 — Choix de la stack technique (25/09/2026)

#### Décision : Next.js + API Express + MySQL + MongoDB
- Raisons :
  - rendu côté serveur des pages publiques : référencement exigé par la CP3 et indispensable à l'exploitation réelle d'un comparateur ;
  - React conservé (technologie maîtrisée) ; Next.js déjà abordé en formation ;
  - API Express séparée : back-end identifiable, testable, organisé en couches et en classes (CP5 à CP7) ;
  - technologie très demandée en entreprise (portfolio).
- Alternatives écartées :
  - React en SPA + Express : pages construites en JavaScript dans le navigateur, référencement faible ;
  - Symfony (rendu Twig) : technologie la moins maîtrisée, abandon de React au profit de JavaScript sans framework ;
  - Symfony en API + React en SPA : solution la plus lourde, même faiblesse de référencement ;
  - Laravel : hors du programme de formation.
- Conséquences :
  - POO et sécurité à construire volontairement dans l'API (contrôleurs, services, accès aux données en classes) ;
  - Next.js limité à l'affichage : aucune logique métier côté Next.js ;
  - deux applications Node.js et deux bases de données à orchestrer ;
  - Next.js à approfondir (composants serveur et client, mise en cache).

#### Décision : choix secondaires
- Langage : JavaScript, documenté avec JSDoc en anglais. 
- Base relationnelle : MySQL (déjà pratiqué ; script SQL généré depuis le MLD de Looping).
- Accès à MySQL : Sequelize, branché sur un schéma créé par un script SQL issu du MLD.
  La synchronisation automatique du schéma par Sequelize est écartée : le script SQL reste la source de vérité et la preuve de la CP5.
- Accès à MongoDB : décidé dans l'issue #7 (rôle du NoSQL et flux d'import).
- Tests : Vitest (front-end et back-end) et Supertest (API) ; un seul outil de test à maîtriser.
- Qualité : ESLint et Prettier ; intégration continue avec GitHub Actions (linter et tests).
- Docker (développement) : MySQL, MongoDB et un outil d'administration en conteneurs ;
  Next.js et Express exécutés sur la machine hôte. Prérequis : WSL 2 pour Docker Desktop sous Windows.
- Styles : Sass avec CSS Modules, sans framework CSS.
  - Raisons : meilleure démonstration de la CP3 ; fidélité à une charte sobre ; CSS limité au nécessaire (éco-conception) ;
    pas de conflit de classes entre composants.
  - Alternative écartée : Bootstrap (moins de CSS personnel, dépendance React-Bootstrap, rendu générique, poids du CSS).
  - Conséquences : création en premier d'une base commune (variables CSS issues de la charte, composants réutilisables :
    bouton, champ de formulaire, carte, tableau, boîte de dialogue) ; recours aux éléments HTML natifs accessibles
    (`<dialog>`, `<details>`).
- Authentification (sessions ou jetons) : décidée dans l'issue #4 (architecture).

### Issue #4 — Architecture logicielle (29/09/2026)

#### Décision : domaine unique pour Next.js et l'API
- Règle : pages servies sur `/...` par Next.js, données servies sur `/api/...` par Express ; aiguillage par un reverse proxy
  en production et par les `rewrites` de Next.js en développement ; appels internes directs de Next.js vers l'API pour le rendu serveur.
- Raisons : cookies de session sans configuration inter-domaines ; aucune configuration CORS (source d'erreurs de sécurité en moins).
- Alternative écartée : API sur un domaine ou un port distinct, appelée directement par le navigateur.

#### Décision : stratégie de rendu
- Rendu serveur : accueil, résultats, fiche produit, pages légales (référencement).
- Rendu client : filtres, tri, sélection, comparateur ; espace membre et back-office exclus de l'indexation.
- Filtres et sélection de comparaison inscrits dans l'URL : partage par lien, bouton « Retour » fonctionnel, rendu serveur des bons résultats.

#### Décision : sessions côté serveur stockées dans MySQL
- Mesures : cookie `httpOnly`, `Secure` (production), `SameSite=Lax` ; vérification de l'en-tête `Origin` sur les requêtes
  de modification ; nouvel identifiant de session à la connexion ; session supprimée à la déconnexion et à la suppression du compte ;
  hachage Argon2id ; limitation des tentatives de connexion ; message d'erreur générique.
- Raisons : révocation immédiate ; identifiant illisible par JavaScript ; complexité faible ; pas de service supplémentaire.
- Alternative écartée : JWT (révocation difficile, exposition en `localStorage`, adapté à plusieurs services ou applications mobiles).
- Principe : la sécurité est vérifiée par l'API, jamais seulement par l'interface.

#### Décision : API en couches, en programmation orientée objet
- Couches : routes, middlewares, contrôleurs, services (règles métier et transactions), calculateurs (calculs purs),
  repositories (accès aux données).
- Injection des dépendances par constructeur (tests unitaires sans base de données) ; validation des entrées avec Zod ;
  erreurs typées gérées par un middleware central (aucun détail technique renvoyé au client) ; en-têtes de sécurité avec Helmet.
- Raisons : séparation des responsabilités, testabilité, démonstration de la POO (CP7).

#### Décision : structure du dépôt
- Dossiers `api/`, `web/`, `database/`, `docs/`, `.github/` et `docker-compose.yml` à la racine ; un `package.json` par application,
  sans outil de monorepo.
- Raison : preuves de la CP5 regroupées dans `database/` ; complexité limitée.

- Livrable : `docs/architecture.md` (en anglais, schémas Mermaid).

### Issue #5 — Modèle conceptuel de données (30/09/2026)

#### Contenu
- 17 entités : catalogue (BRAND, PRODUCT_LINE, PRODUCT, PACKAGING, SPECIES, FOOD_TYPE, LIFE_STAGE, BODY_SIZE, SPECIFIC_NEED),
  composition (INGREDIENT, ADDITIVE, CONSTITUENT), prix et traçabilité (PRICE_RECORD, SELLER, DATA_SOURCE),
  utilisateurs (USER_ACCOUNT, COMPARISON).
- 19 associations : 11 « un à plusieurs », 8 « plusieurs à plusieurs » (dont 5 avec attributs portés).
- Livrables : `docs/data-model/mcd.loo`, `docs/data-model/mcd.png`, `docs/data-model/data-dictionary.md` (en anglais).

#### Décision : constituants analytiques en entité (CONSTITUENT + association PRODUCT_CONSTITUENT)
- Raisons : ajout d'un constituant sans modifier la structure de la base (ex. taurine pour les chats) ; affichage générique
  dans le comparateur.
- Alternative écartée : une colonne par constituant dans PRODUCT (structure rigide, nombreuses colonnes vides).
- Conséquences : filtres par sous-requêtes ; validation des valeurs dans l'API plutôt que par CHECK ; attribut `is_mandatory`
  pour les quatre constituants obligatoires sur l'étiquette (protéines, matières grasses, fibres, cendres).

#### Décision : « sans céréales » = déclaration du fabricant
- Raison : donnée factuelle, cohérente avec la règle de neutralité (RG-12).
- Alternative écartée : déduction à partir des ingrédients (frontière floue : quinoa, sarrasin…).

#### Décision : pas d'entité fabricant (groupe industriel)
- Raison : aucune fonctionnalité ne l'utilise ; ajout ultérieur possible sans refonte.

#### Décision : noms en anglais, identifiants `<entité>_id`
- Raisons : cohérence avec le code ; génération directe du script SQL ; clés étrangères aux noms explicites.
- Mots réservés ou ambigus de MySQL évités (`range`, `rank`, `user`, `source`, `value`, `type`, `format`).
- Entités en majuscules dans le MCD (convention Merise) ; tables en minuscules dans le script SQL.

#### Choix de conception
- Produit relié à la marque par sa gamme uniquement (pas de redondance, troisième forme normale).
- Code EAN porté par le format (un code-barres par taille de sac).
- Prix au kilo non stocké (calculé, RG-05).
- Composition conservée sous deux formes : texte de l'étiquette (fidélité) et liste normalisée (filtres).
- Types : DECIMAL pour les prix et les valeurs nutritionnelles (valeurs exactes), poids en grammes entiers, EAN en texte.
- Règles non exprimables dans le MCD, vérifiées par l'API : 2 à 4 produits par comparaison (RG-13), conditions de publication
  (RG-10), cohérence des stades de vie et gabarits avec l'espèce du produit.

#### Erreurs initiales et corrections
- Contrainte UNIQUE cochée sur des attributs non uniques (ex. `role`, `category`, `net_weight_g`) :
  une seule valeur aurait été autorisée par table. Corrigé après relecture du dictionnaire des données.
- `amount` initialement en DECIMAL(6,3) (999,999 au maximum, insuffisant pour les valeurs en mg/kg) : passé en DECIMAL(10,3).
- Unicité par marque (gamme) ou par espèce (stade de vie, gabarit) : non exprimable par une case UNIQUE, reportée au MLD (issue #6).

### Issue #6 — Modèle logique de données (01/10/2026)

#### Contenu
- MLD généré par Looping : 25 tables (17 entités, 8 tables de liaison).
- Règles de passage : chaque entité devient une table ; association « un à plusieurs » → clé étrangère du côté (1,1) ;
  association « plusieurs à plusieurs » → table de liaison à clé primaire composée, avec ses attributs portés.
- Colonne technique `product.version` ajoutée (verrou optimiste, RG-18) ; MCD réexporté.
- Livrables : `docs/data-model/mld.png` ; section « Logical data model » du dictionnaire des données
  (schéma relationnel, unicités, CHECK, clés étrangères, index).
  - Fichier Looping renommé en `mcd.loo` (commité par erreur sous le nom `Looping1.loo` lors de l'issue #5).

#### Décisions
- Unicités composées : gamme par marque, stade de vie et gabarit par espèce, rang d'un ingrédient par produit.
- Listes de valeurs en VARCHAR + CHECK plutôt qu'en ENUM (tri par ordre de déclaration, type propre à MySQL).
  Table de référence écartée (excessive pour trois valeurs).
- `comparison_product.display_order` limité de 1 à 4 : maximum de la RG-13 garanti par la base.
- Suppression : RESTRICT pour les référentiels et les éléments en usage, CASCADE pour les données dépendantes
  (formats, prix, sources, liens) et pour les données d'un compte supprimé (RG-17).
- Un produit présent dans des favoris ou des comparaisons ne peut pas être supprimé, seulement archivé (cohérence avec la RG-11).
- Trois index ajoutés pour des requêtes identifiées ; index des clés étrangères créés automatiquement par InnoDB.

#### Constat
- Script SQL de Looping non exécutable tel quel sous MySQL : types génériques (COUNTER, LOGICAL), noms en majuscules,
  aucune règle de suppression, aucun CHECK ni unicité composée.
- Script physique à écrire et tester dans le milestone M2, une fois MySQL disponible dans Docker. Le script de Looping
  n'est pas versionné.

  ### Issue #7 — Rôle du NoSQL et flux d'import (05/10/2026)

#### Décision : MongoDB stocke les réponses brutes de l'API Open Pet Food Facts
- Raisons : documents volumineux, imbriqués et à structure évolutive (nouvelle structure des valeurs nutritionnelles en API v3.5) ;
  traçabilité de ce que disait la source à une date donnée (RG-08, RG-19) ; transformation rejouable sans nouvel appel
  (limites de débit) ; séparation entre données externes non vérifiées et données de référence vérifiées.
- Alternatives écartées : colonne JSON dans MySQL (possible et plus simple, mais sans séparation des données ni démonstration
  de la partie NoSQL de la CP6) ; journal des modifications des administrateurs (sans lien avec la problématique des données).
- Accès : pilote officiel MongoDB, encapsulé dans une classe `ImportRepository`. Mongoose écarté (impose un schéma aux documents ;
  validation déjà assurée par Zod). Validation `$jsonSchema` des métadonnées dans MongoDB.

#### Décision : flux d'import
- Vérification du code-barres (format, clé de contrôle, absence de doublon) avant tout appel externe.
- Appel de l'API v3 avec sous-version fixée, User-Agent identifié, délai maximal et gestion des erreurs (inconnu, indisponible,
  limite de débit, produit non destiné aux animaux).
- Réponse brute stockée dans MongoDB, puis formulaire pré-rempli ; création du produit en brouillon non vérifié, dans une
  transaction MySQL, après que l'administrateur a complété la gamme, l'espèce et le type d'aliment.
- Photos non importées. Tests automatisés sur des réponses enregistrées, sans appel à l'API.
- US-20 (issue #32) mise à jour : produit pré-rempli puis créé après validation (les clés étrangères obligatoires de `product`
  empêchent une création automatique).

#### Constats sur les données
- Règles de l'API : v2 dépréciée, v3 recommandée ; 15 lectures par minute et par IP ; User-Agent obligatoire ;
  aucune garantie d'exactitude ; licences ODbL (base), DbCL (contenus), CC BY-SA (images).
- Réponse réelle analysée (Royal Canin, code-barres 3182550846127) : complétude de 35 %, ni ingrédients ni valeurs nutritionnelles,
  nom uniquement en français, dernière modification en octobre 2022.
- Sur les pages web, les pourcentages affichés à côté des constituants sont souvent des moyennes de catégorie, et non les valeurs du produit.
- Conséquence : Open Pet Food Facts fournit surtout l'identification des produits ; la saisie manuelle à partir des étiquettes
  officielles reste la source principale des données.

#### Erreur initiale et correction
- Une humidité de 40,81 % avait d'abord été lue comme une valeur du produit ; il s'agissait de la moyenne de la catégorie
  « nourriture pour chiens » (pâtées comprises). Corrigé après comparaison de plusieurs fiches et analyse de la réponse de l'API.

- Livrable : `docs/data-import.md` (en anglais).

### Issue #8 — Contrat de l'API REST (05/10/2026)

#### Décisions
- Pas de version dans l'URL : un seul client, déployé avec l'API.
- Erreurs au format standard RFC 9457 (Problem Details), avec un code lisible par le programme et la liste des champs invalides ;
  aucun détail technique renvoyé.
- Codes HTTP : 400 pour une donnée invalide, 422 pour une règle métier non respectée (ex. RG-10), 409 pour un conflit
  (unicité, élément en usage, modification concurrente `VERSION_CONFLICT`).
- Pagination par numéro de page (20 par défaut, 50 au maximum) ; tri `?sort=` avec `-` pour l'ordre décroissant.
- Champs JSON en camelCase, colonnes en snake_case ; slugs pour les pages indexées, identifiants numériques ailleurs.
- Filtres combinés (ET) ; plages de constituants `range=<code>:<min>:<max>` ; exclusions d'ingrédients, d'additifs et de groupes
  fonctionnels.
- Suppression de compte par `POST /api/me/deletion` (le corps d'une requête DELETE n'a pas de sens défini en HTTP).
- Calculs (prix au kilo, matière sèche, relevé ancien) effectués par l'API, jamais par l'application Next.js.
- Spécification OpenAPI à rédiger pendant le développement, en parallèle du code.

#### Évolution du modèle de données
- Ajout de `constituent.code` (VARCHAR(30), obligatoire, unique) : identifiant technique stable nécessaire à la RG-07
  (humidité), au tri (US-04) et aux filtres par plage. Le nom affiché ne peut pas servir d'identifiant (fragile en cas de correction).
- MCD, MLD et dictionnaire des données mis à jour.

- Livrable : `docs/api-contract.md` (en anglais).

### Issue #9 — Charte graphique (08/10/2026)

#### Décision : palette « sauge et ardoise » (direction A)
- Une seule couleur de marque (vert sauge), gris neutres, fonds clairs.
- Raisons : sobriété demandée ; le vert sauge est une couleur de marque, pas d'évaluation.
- Alternative écartée : palette « encre et ambre » (plus contrastée, mais l'ambre attire fortement l'œil).
- Règle de neutralité (RG-12) : aucun code vert/rouge sur les valeurs des produits ; écarts signalés par le gras et un repère
  neutre ; rouge réservé aux erreurs de formulaire.
- Contrastes calculés pour chaque combinaison (formule WCAG) : texte ≥ 4,5:1, éléments d'interface ≥ 3:1.
- Thème clair uniquement dans le MVP.

#### Décision : police Source Sans 3
- Raisons : humaniste et chaleureuse tout en restant sérieuse ; très lisible en tableau ; chiffres de largeur fixe pour aligner
  les valeurs du comparateur ; hébergée avec le site via `next/font` (aucun appel des visiteurs vers Google, RGPD).
- Alternatives étudiées : Atkinson Hyperlegible Next, Inter, Nunito Sans, DM Sans, Lexend, Figtree, Public Sans.
- Deux graisses (400 et 600), tailles en rem (respect du réglage de taille du navigateur).

#### Erreur initiale et correction
- Bordure des champs proposée en #8A948F : 3,13:1 sur blanc, mais 2,99:1 sur le fond de page (sous le seuil de 3:1).
  Remplacée par #7F8984 (au moins 3,24:1 sur les trois fonds). Enseignement : vérifier un contraste sur tous les fonds
  où la couleur apparaît.

  #### Réalisation dans Figma
- Variables : 16 couleurs (collection « Colors »), 8 espacements (« Spacing »), 2 rayons (« Radius ») ; 7 styles de texte.
  Les éléments du guide de style sont liés aux variables, et non saisis en valeurs fixes.
- Organisation du fichier imposée par le forfait gratuit (3 pages maximum) : « Charte et composants », « Wireframes »,
  « Maquettes », avec des sections Mobile et Desktop à l'intérieur des pages.

#### Décision : pas de maquettes tablette
- Raisons : le référentiel demande des maquettes web et mobile ; dessiner un troisième format alourdirait le travail
  sans apport pour l'évaluation.
- Conséquence : maquettes mobile (375 px) et desktop (1 440 px) ; le comportement intermédiaire (points de rupture à 600,
  900 et 1 200 px) sera démontré sur le site réel.
- Rôles de couleur distincts à valeur identique (`primary-hover` et `primary-strong`) : nommage par rôle, pour pouvoir
  les faire évoluer séparément.

- Livrables : `docs/visual-identity.md` (en anglais, variables CSS incluses), guide de style Figma exporté
  (`docs/design/style-guide.png`).

## 4. Mise en place du projet

### Étape 4.1 — Création du dépôt (24/09/2026)
- Dépôt public créé avec GitHub CLI : https://github.com/ad-pgn/comparateur-croquettes (branche par défaut : `main`).
- Premier commit : `.gitignore`, `README.md`, `docs/` (expression des besoins v1.1, journal de projet).
- `.gitignore` créé avant le premier `git add` : secrets (`.env`), dépendances, builds, sauvegardes de base (`backups/`),
  fichiers système et éditeur.
- Confidentialité : adresse e-mail GitHub privée (noreply) utilisée pour les commits ;
  blocage des push exposant l'adresse personnelle activé.
- README : aucune fonctionnalité présentée comme réalisée ; résumé en anglais.

### Étape 4.2 — Conventions de travail (24/09/2026)

#### Décision : GitHub Flow
- Règle : `main` toujours stable, sans commit direct ; une branche courte par issue ; fusion par pull request.
- Raisons : modèle simple adapté à un développeur seul ; traçabilité de chaque évolution par une pull request ;
  vérifications automatiques possibles avant fusion.
- Alternatives écartées : Git Flow (complexité inutile sans versions planifiées) ; commits directs sur `main` (aucune trace de revue).

#### Décision : Conventional Commits et « Squash and merge »
- Règle : messages `type(portée): description` en anglais ; un commit par pull request sur `main`.
- Raisons : historique de `main` lisible comme un journal des fonctionnalités ; détail conservé dans chaque pull request.
- Conséquences : options du dépôt limitées au « Squash and merge » ; suppression automatique des branches fusionnées.

#### Décision : répartition des langues
- Règle : code, commits, branches, pull requests et documentation technique en anglais ;
  documentation fonctionnelle en français.
- Raisons : pratique professionnelle courante ; démonstration de la compétence « anglais » ; documents d'examen en français.
- Livrables : `CONTRIBUTING.md`, `.github/pull_request_template.md`.

### Étape 4.3 — Sécurisation du dépôt (24/09/2026)
- Ruleset « Protect main » (branche par défaut) : suppression interdite, force push interdit,
  modifications uniquement par pull request (0 approbation requise : un auteur ne peut pas approuver sa propre pull request).
- Détection de secrets et protection des push contre les secrets : activées.
- Dependabot : alertes de vulnérabilités et correctifs de sécurité automatiques activés.
- Fusion : titre de la pull request imposé comme titre du commit « squash » ; liste des commits conservée dans la description.
- Wiki désactivé : documentation centralisée et versionnée dans le dépôt.
- Test : push direct d'un commit vide sur `main` refusé (erreur GH013, « Changes must be made through a pull request ») ;
  commit de test annulé en local. Capture d'écran conservée comme preuve.
- Évolution prévue : exiger la réussite de l'intégration continue avant fusion, une fois celle-ci en place.

### Étape 4.4 — Labels et milestones (24/09/2026)

#### Décision : quatre familles de labels
- Familles : `type:` (nature du travail), `area:` (partie du projet), `priority:` (MVP ou complémentaire),
  `cp1:` à `cp8:` (compétence du référentiel).
- Raisons : filtrage des issues par compétence pour construire la matrice compétence → réalisation → preuve ;
  repérage rapide du travail de sécurité et d'accessibilité.
- Conséquences : labels par défaut de GitHub supprimés ; 24 labels créés.

#### Décision : neuf milestones dans l'ordre de développement
- Milestones : M1 Design, M2 Technical foundation, M3 Authentication, M4 Catalog administration,
  M5 Search and product pages, M6 Comparison, M7 Member area, M8 Quality and delivery, M9 Exam deliverables.
- Raisons : l'authentification conditionne l'accès au back-office ; le back-office permet de saisir les données réelles
  avant de développer la consultation.
- Conséquences : aucune date d'échéance (pas de date de rendu imposée) ; ordre révisable après la conception.

### Étape 4.5 — Issues et tableau de suivi (25/09/2026)

#### Décision : issues rédigées en français
- Raisons : issues issues directement de l'expression des besoins (user stories et critères d'acceptation repris à l'identique) ;
  lisibilité pour le mentor et le jury.
- Alternative écartée : issues en anglais (cohérence avec les commits et pull requests).
- Conséquences : `CONTRIBUTING.md` mis à jour ; labels et milestones conservés en anglais.

#### Réalisation
- 40 issues créées par un script PowerShell (liste JSON + un fichier Markdown par issue), conservé hors du dépôt :
  10 tâches de conception (M1), 22 user stories MVP, 5 user stories complémentaires, 3 livrables d'examen (M9).
- Script sans effet de doublon : il ignore les issues dont le titre existe déjà ; exécution à blanc avant création.
- Chaque issue porte ses labels (type, partie, priorité, compétence) et son milestone ;
  critères d'acceptation sous forme de cases à cocher.
- Tâches du socle technique (M2) et de qualité (M8) : créées après la conception (dépendantes de la stack).
- Modèles d'issues en français (user story, tâche, bug) ; création d'issues vierges désactivée.
- GitHub Project public « comparateur-croquettes » lié au dépôt : vue Kanban (Todo / In Progress / Done) ;
  passage automatique en Done à la fermeture d'une issue ou à la fusion d'une pull request ;
  ajout automatique des nouvelles issues et pull requests.

## 5. Développement

## 6. Tests

## 7. Difficultés rencontrées et solutions

### Difficulté : guillemets imbriqués dans une commande `gh` sous PowerShell (24/09/2026)
- Problème : `gh api ... --jq ".[] | \"\(.number) - \(.title)\""` échoue avec
  « Le terme .number n'est pas reconnu comme nom d'applet de commande ».
- Cause : PowerShell n'utilise pas la barre oblique inverse comme caractère d'échappement (c'est la syntaxe de Bash) ;
  la chaîne se termine trop tôt et la suite est interprétée comme une commande.
- Solution : expression jq sans guillemets imbriqués (`--jq ".[].title"`).
- Enseignement : vérifier la compatibilité d'une commande avec le shell utilisé (PowerShell sous Windows, Bash sous Linux).

## 8. Veille technologique et sécurité

## 9. Compétences du référentiel mobilisées

## 10. Évolutions futures
- Extension aux autres aliments, friandises, chats et autres animaux.
- Questionnaire de présélection (race, poids, allergies, stérilisation, activité) proposant 2-3 produits selon différents budgets.
  Point de vigilance : rester un filtrage factuel, pas une recommandation médicale.
- Coût journalier (ration × prix au kilo).
- Alertes de prix.
- Extension à la grande distribution (sources de prix et marques associées).