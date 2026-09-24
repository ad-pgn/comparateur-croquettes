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

## 4. Mise en place du projet

## 5. Développement

## 6. Tests

## 7. Difficultés rencontrées et solutions

## 8. Veille technologique et sécurité

## 9. Compétences du référentiel mobilisées

## 10. Évolutions futures
- Extension aux autres aliments, friandises, chats et autres animaux.
- Questionnaire de présélection (race, poids, allergies, stérilisation, activité) proposant 2-3 produits selon différents budgets.
  Point de vigilance : rester un filtrage factuel, pas une recommandation médicale.
- Coût journalier (ration × prix au kilo).
- Alertes de prix.
- Extension à la grande distribution (sources de prix et marques associées).