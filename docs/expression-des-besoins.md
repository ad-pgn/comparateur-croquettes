# Expression des besoins — comparateur-croquettes

> Version 1.1 — validée le 24 septembre 2026.
> Les éléments marqués **(à valider)** restent à arrêter en conception.
> Les éléments marqués **(hypothèse)** ne sont pas démontrés et ne doivent pas être présentés comme des faits.

---

## 1. Contexte

### 1.1 Origine du projet

Ce projet personnel est réalisé dans le cadre de la préparation au titre professionnel Développeur Web et Web Mobile (DWWM).

Son porteur est propriétaire de chiens. Il part d'un constat simple : pour choisir des croquettes, un propriétaire doit confronter des informations dispersées et difficiles à comparer. Ces informations sont les suivantes :

- les étiquettes réglementaires (composition, constituants analytiques, additifs) ;
- des allégations marketing (« premium », « sans céréales », « naturel »…) ;
- des prix qui varient selon le format du sac et le revendeur.

### 1.2 Données de marché

- **Lieux d'achat** : selon le baromètre FACCO-Odoxa 2025, les grandes et moyennes surfaces restent le premier lieu d'achat de la nourriture pour chiens. 50 % des propriétaires y achètent, dont 44 % en lieu d'achat principal. L'animalerie concerne 32 % des chiens et les achats en ligne 28 %, un chiffre qui se stabilise.
  Source : FACCO, rapport annuel 2025 — https://www.facco.fr/wp-content/uploads/2025/05/2025-rapport-annuel-facco-BD.pdf
- **Poids du marché** : le marché français de l'alimentation pour animaux de compagnie représenterait 5,7 Md€ en 2024. La répartition annoncée est la suivante : grandes surfaces 48,6 %, e-commerce 24,6 %, animaleries et jardineries 22,4 %, vétérinaires et éleveurs 4,4 %.
  Source secondaire, **à vérifier avant citation** : https://www.intotheminds.com/blog/petfood/

Enseignement : Internet est le deuxième circuit en valeur. Un outil de comparaison en ligne répond donc à un usage réel. L'exclusion de la grande distribution est un **choix de périmètre** du projet, pas un reflet du marché.

### 1.3 L'existant

Plusieurs comparateurs existent en France (analyse réalisée en septembre 2026) :

| Site | Approche | Limites observées |
|---|---|---|
| Une gamelle au top | Grand tableau filtrable d'environ 6 500 références, sans notes ; valeurs brutes et sur matière sèche ; source et date par produit | Aucun prix ; dates de mise à jour anciennes dans l'échantillon consulté (2019-2020) ; sources parfois étrangères |
| macroquette.com | Questionnaire (âge, poids, stérilisation, activité, race…) et notation ; option qualité-prix | Page non modifiée depuis fin 2020 ; notation fondée sur une méthode propre |
| Le Bon Choix Croquettes | Comparaison de 8 marques sur 6 critères, prix au kilo relevé et daté, avis clients | Comparaison au niveau de la marque, pas du produit ; liens d'affiliation |
| Gangdesmoustaches.fr | Classements par score maison (23 critères) | Score subjectif |
| Mes-Croquettes.com | Analyse de valeurs saisies par l'utilisateur | Pas de catalogue comparatif |

**Combinaison non observée chez les concurrents :**

- la sélection libre de produits précis mis côte à côte ;
- des prix relevés **par format**, avec un prix au kilo au niveau du produit ;
- une traçabilité datée de chaque donnée ;
- des comptes utilisateurs avec favoris et comparaisons sauvegardées.

### 1.4 Positionnement

> Un comparateur **factuel**, centré sur le **marché français** (circuit spécialisé et vente en ligne), qui permet de mettre **côte à côte des produits précis** avec leur **coût réel** (prix au kilo par format, relevé et daté) et la **source de chaque donnée**.

---

## 2. Problématique

> Comment permettre à un propriétaire de chien de comparer, de façon **factuelle, sourcée et à jour**, des croquettes commercialisées en France, en tenant compte à la fois de leur **composition** et de leur **coût réel** ?

---

## 3. Objectifs

### 3.1 Objectifs pour l'utilisateur

1. Trouver rapidement des croquettes correspondant à son chien : stade de vie, gabarit, besoins spécifiques.
2. Exclure les produits contenant un ingrédient ou un additif qu'il souhaite éviter.
3. Comparer 2 à 4 produits côte à côte sur des critères homogènes.
4. Connaître le coût réel de chaque produit (prix au kilo par format), avec la date et la source du relevé.
5. Vérifier l'origine de chaque information affichée.
6. Retrouver ses produits favoris et ses comparaisons d'une visite à l'autre.

### 3.2 Objectifs du projet

1. Démontrer les compétences du titre DWWM, en particulier les six compétences obligatoires du dossier (CP2 à CP7).
2. Produire une application sécurisée, accessible, responsive, testée et documentée.
3. Concevoir un modèle de données capable d'évoluer : volume, autres espèces, autres types d'aliments.

### 3.3 Indicateurs de réussite

| Indicateur | Cible |
|---|---|
| Produits publiés et vérifiés | 30 à 45 |
| Marques couvertes | 10 à 12 |
| Produits comparables simultanément | 2 à 4 |
| Couverture des user stories MVP | 100 % des critères d'acceptation validés |
| Accessibilité | Aucune erreur bloquante à l'audit automatique ; vérification manuelle des critères RGAA principaux |
| Tests | Tests unitaires sur les composants métier et d'accès aux données ; tests de sécurité sur les points d'entrée |

---

## 4. Utilisateurs

### 4.1 Rôles

| Rôle | Description | Accès |
|---|---|---|
| **Visiteur** | Utilisateur non connecté | Recherche, filtres, fiches produits, comparateur (sélection non sauvegardée), pages légales |
| **Membre** | Utilisateur disposant d'un compte | Tout l'accès visiteur, plus favoris, comparaisons sauvegardées, gestion et suppression du compte |
| **Administrateur** | Gestionnaire du catalogue | Back-office : marques, gammes, produits, référentiels, relevés de prix, imports, publication |

Un administrateur n'est jamais créé par l'inscription publique (voir RG-15).

### 4.2 Personas

> Personas **fictifs**, construits à partir des hypothèses du projet. Ils ne reposent pas sur une étude utilisateurs.

**Camille, 34 ans — la propriétaire attentive au budget**

- Chien : labrador adulte, 30 kg.
- Habitudes : achète en ligne, en grands sacs.
- Besoin : savoir si un sac de 14 kg est vraiment plus avantageux qu'un sac de 3 kg, et comparer le prix au kilo de produits équivalents.
- Frustration : les prix affichés ne sont pas comparables d'un format à l'autre ni d'un site à l'autre.

**Julien, 45 ans — le propriétaire qui lit les étiquettes**

- Chien : bouledogue français à la digestion sensible.
- Besoin : exclure un ingrédient précis, puis comparer trois produits « digestion sensible » sur leurs taux de protéines, matières grasses et fibres.
- Frustration : les informations sont dispersées sur plusieurs sites et il ne sait pas si elles sont à jour.

**L'administrateur — le porteur du projet**

- Besoin : saisir ou importer des produits de façon fiable, tracer les sources, maintenir les prix à jour sans risque d'écraser une modification.

---

## 5. Périmètre

### 5.1 Périmètre des données

**Inclus :**

- croquettes pour chiens ;
- produits commercialisés en France (RG-01) ;
- marques présentes en circuit spécialisé ou en vente en ligne, y compris les marques propres des enseignes spécialisées.

**Exclus :**

- autres types d'aliments (pâtées, friandises) et autres espèces ;
- aliments diététiques et gammes distribuées exclusivement par les vétérinaires ;
- marques propres de la grande distribution ;
- marques sans relevé de prix possible dans les sources retenues (dont Pedigree et Friskies).

### 5.2 Périmètre fonctionnel

**MVP (indispensable)**

- **Consultation** : recherche textuelle, filtres multicritères, tri, fiche produit sourcée.
- **Comparaison** : sélection de 2 à 4 produits, tableau comparatif, affichage brut ou sur matière sèche, prix au kilo.
- **Compte** : inscription, connexion, déconnexion, favoris, comparaisons sauvegardées, suppression du compte.
- **Administration** : marques, gammes, produits, référentiels, relevés de prix, publication, gestion des conflits d'édition.
- **Import** : import assisté depuis Open Pet Food Facts par code-barres (le rôle exact de la base NoSQL sera confirmé en conception).
- **Transverse** : mentions légales, politique de confidentialité, attribution Open Pet Food Facts, avertissement vétérinaire, accessibilité, responsive.

**Complémentaire (si le temps le permet)**

- Recherches sauvegardées.
- Réinitialisation du mot de passe par e-mail.
- Historique des prix d'un produit (graphique).
- Export d'une comparaison.
- Export des données personnelles du membre (droit à la portabilité).

**Évolutions futures**

- Extension aux autres aliments, aux friandises, aux chats et aux autres animaux.
- Extension à la grande distribution (sources de prix et marques).
- Questionnaire de présélection (filtrage factuel, pas de recommandation médicale).
- Coût journalier (ration × prix au kilo).
- Alertes de prix.

### 5.3 Hors périmètre

- Vente en ligne ou panier d'achat.
- Conseil vétérinaire ou nutritionnel personnalisé.
- Notes, scores, classements de qualité et avis d'utilisateurs.
- Application mobile native (le mobile est couvert par le responsive web).
- Interface multilingue.

---

## 6. Règles métier

| ID | Règle | Détail |
|---|---|---|
| RG-01 | Éligibilité « commercialisé en France » | Le produit est étiqueté en français et vendu dans au moins un point de vente physique en France, ou sur un site marchand exploité par une entité établie en France (y compris le site français de la marque). |
| RG-02 | Exclusions | Sont exclus : les aliments diététiques et gammes distribuées exclusivement par les vétérinaires, et les marques propres de la grande distribution. |
| RG-03 | Relevé de prix | Un relevé comprend : format (poids net), prix TTC en euros, type (PPC marque / vente directe marque / prix revendeur), source (enseigne ou site), URL et date du relevé. |
| RG-04 | Sources de prix autorisées | Sites des marques, Zooplus, Maxi Zoo, Truffaut, Animalis. Zooplus n'est une source valable que si le produit est aussi vendu dans un autre circuit éligible. |
| RG-05 | Prix au kilo | Prix au kilo = prix TTC ÷ poids net du format en kg, arrondi au centime. Il est calculé par l'application et n'est jamais saisi. |
| RG-06 | Ancienneté d'un prix | Un relevé de plus de 90 jours est signalé comme « à actualiser ». |
| RG-07 | Matière sèche | Valeur sur matière sèche = valeur brute × 100 ÷ (100 − humidité). Elle n'est calculée et affichée que si le taux d'humidité est renseigné. |
| RG-08 | Traçabilité | Chaque fiche produit indique au moins une source (URL et date de consultation) et un statut de vérification (vérifié / non vérifié). Les données issues d'Open Pet Food Facts conservent leur identifiant d'origine. |
| RG-09 | Publication | Un produit a un statut : Brouillon, Publié ou Archivé. Seuls les produits publiés sont visibles publiquement. |
| RG-10 | Conditions de publication | Un produit ne peut passer au statut Publié que s'il a : une marque, une gamme, une dénomination, une composition, les constituants analytiques obligatoires, au moins une source, le statut « vérifié » et au moins un relevé de prix. |
| RG-11 | Produit archivé | Un produit archivé n'apparaît plus dans la recherche. S'il figure dans une comparaison sauvegardée, il reste affiché avec la mention « produit retiré ». |
| RG-12 | Neutralité | L'application n'attribue aucune note, aucun score et aucun classement de qualité. Les écarts sont mis en évidence sans jugement de valeur. |
| RG-13 | Comparateur | Une comparaison contient de 2 à 4 produits. Un visiteur peut comparer, mais seul un membre peut sauvegarder une comparaison. |
| RG-14 | Exclusion d'ingrédients | Le filtre repose sur la liste normalisée des ingrédients de la composition. Un avertissement précise qu'il ne tient pas compte des traces ni des contaminations croisées, et qu'il ne remplace pas un avis vétérinaire. |
| RG-15 | Comptes | L'adresse e-mail est unique. Le mot de passe fait au moins 12 caractères, conformément aux recommandations de la CNIL (règle exacte à préciser en conception). Les comptes administrateurs sont créés hors de l'inscription publique. |
| RG-16 | Favoris | Un produit ne peut figurer qu'une fois dans les favoris d'un membre. |
| RG-17 | Suppression de compte | La suppression exige une confirmation. Elle supprime les données personnelles du membre, ses favoris et ses comparaisons sauvegardées. |
| RG-18 | Modifications concurrentes | Si un produit a été modifié par un autre administrateur depuis l'ouverture du formulaire, l'enregistrement est refusé et l'administrateur est invité à recharger la fiche. |
| RG-19 | Import Open Pet Food Facts | Un produit importé est créé en Brouillon, avec le statut « non vérifié », et l'attribution à Open Pet Food Facts est conservée. |
| RG-20 | Avertissement | Toute page de résultat, de fiche ou de comparaison rappelle que les informations sont indicatives et ne remplacent pas l'avis d'un vétérinaire. |

---

## 7. Parcours utilisateurs

**P1 — Trouver un produit (visiteur)**

1. Accueil.
2. Recherche ou accès direct aux filtres.
3. Application des filtres (stade de vie, gabarit, besoins, exclusions, prix au kilo maximum).
4. Liste des résultats triée.
5. Fiche produit.

**P2 — Comparer des produits (visiteur ou membre)**

1. Depuis la liste ou une fiche, ajout d'un produit à la sélection.
2. Ajout d'un deuxième produit, puis jusqu'à 4.
3. Ouverture du comparateur.
4. Lecture des écarts ; bascule entre valeurs brutes et matière sèche.
5. Pour un membre : sauvegarde de la comparaison.

**P3 — Retrouver ses produits (membre)**

1. Connexion.
2. Espace personnel.
3. Consultation des favoris et des comparaisons sauvegardées.
4. Réouverture d'une comparaison.

**P4 — Ajouter un produit (administrateur)**

1. Connexion au back-office.
2. Création ou import d'un produit.
3. Saisie ou vérification : composition, constituants, additifs, formats.
4. Saisie d'au moins un relevé de prix.
5. Ajout des sources.
6. Passage au statut « vérifié ».
7. Publication.

**P5 — Actualiser un prix (administrateur)**

1. Accès à la liste des relevés à actualiser.
2. Saisie d'un nouveau relevé daté.
3. Le prix au kilo et l'affichage public sont mis à jour.

---

## 8. User stories et critères d'acceptation

Priorité : **MVP** ou **C** (complémentaire).
Les critères suivent le format « Étant donné / Quand / Alors ».

### Épopée A — Consultation

**US-01 — Rechercher un produit** (MVP)
En tant que visiteur, je veux rechercher un produit par son nom ou sa marque afin de le trouver rapidement.
- Étant donné des produits publiés, quand je saisis au moins 2 caractères, alors les produits dont le nom ou la marque correspond s'affichent.
- Quand aucun produit ne correspond, alors un message l'indique clairement, avec une suggestion de modifier la recherche.
- Les produits en brouillon ou archivés n'apparaissent jamais.

**US-02 — Filtrer les produits** (MVP)
En tant que visiteur, je veux filtrer les produits selon plusieurs critères afin de ne voir que ceux adaptés à mon chien.
- Critères disponibles : marque, gamme, stade de vie, gabarit, besoins spécifiques, sans céréales, fourchettes de taux (protéines, matières grasses, fibres, cendres), prix au kilo maximum.
- Quand je combine plusieurs filtres, alors seuls les produits respectant **tous** les filtres s'affichent.
- Le nombre de résultats est annoncé, y compris aux technologies d'assistance.
- Les filtres actifs sont visibles et peuvent être retirés un par un ou tous ensemble.

**US-03 — Exclure des ingrédients ou des additifs** (MVP)
En tant que propriétaire, je veux exclure les produits contenant un ingrédient ou un additif donné afin d'éviter ce que mon chien ne doit pas consommer.
- Quand j'exclus un ingrédient, alors aucun produit dont la composition normalisée le contient n'est affiché.
- L'avertissement de la RG-14 est affiché.

**US-04 — Trier les résultats** (MVP)
En tant que visiteur, je veux trier les résultats afin de les parcourir selon ma priorité.
- Tris disponibles : prix au kilo (croissant ou décroissant), taux de protéines, nom.
- Un produit sans prix au kilo est placé en fin de liste lors d'un tri par prix.

**US-05 — Consulter une fiche produit** (MVP)
En tant que visiteur, je veux consulter la fiche détaillée d'un produit afin de connaître toutes ses caractéristiques.
- La fiche affiche : marque, gamme, dénomination, stade de vie, gabarit, besoins, composition, constituants analytiques, additifs, formats avec relevés de prix et prix au kilo.
- Chaque relevé affiche sa source et sa date ; un relevé ancien est signalé (RG-06).
- Les sources de la fiche, son statut de vérification et, le cas échéant, l'attribution Open Pet Food Facts sont affichés.
- La fiche a une URL lisible et des balises adaptées au référencement.

### Épopée B — Comparaison

**US-06 — Constituer une sélection** (MVP)
En tant que visiteur, je veux ajouter ou retirer des produits d'une sélection afin de préparer une comparaison.
- Je peux ajouter un produit depuis la liste ou depuis sa fiche.
- Quand la sélection contient déjà 4 produits, alors l'ajout est refusé avec un message explicite.
- La sélection est conservée pendant la navigation.

**US-07 — Comparer des produits** (MVP)
En tant que visiteur, je veux afficher 2 à 4 produits côte à côte afin d'identifier leurs différences.
- Avec moins de 2 produits, le comparateur invite à en ajouter.
- Les critères sont alignés ligne par ligne ; les valeurs extrêmes sont mises en évidence sans jugement de valeur (RG-12).
- Le prix au kilo le plus bas relevé pour chaque produit est affiché, avec sa source et sa date.
- Le tableau reste lisible sur mobile.

**US-08 — Afficher les valeurs sur matière sèche** (MVP)
En tant que visiteur, je veux basculer entre valeurs brutes et valeurs sur matière sèche afin de comparer des produits d'humidités différentes.
- Les valeurs sont calculées selon la RG-07.
- Un produit sans humidité renseignée affiche « non calculable » plutôt qu'une valeur.

### Épopée C — Compte membre

**US-09 — Créer un compte** (MVP)
En tant que visiteur, je veux créer un compte afin de sauvegarder mes favoris et mes comparaisons.
- L'e-mail doit être valide et unique ; le mot de passe respecte la RG-15.
- Les erreurs sont affichées à côté des champs concernés, sans effacer la saisie valide.
- Le mot de passe n'est jamais stocké en clair.
- L'inscription nécessite d'avoir pris connaissance de la politique de confidentialité.

**US-10 — Se connecter et se déconnecter** (MVP)
En tant que membre, je veux me connecter et me déconnecter afin d'accéder à mon espace de façon sécurisée.
- En cas d'identifiants incorrects, le message reste générique : il ne révèle pas si l'e-mail existe.
- Les tentatives répétées sont limitées.
- Après déconnexion, les pages de l'espace membre ne sont plus accessibles.

**US-11 — Gérer mes favoris** (MVP)
En tant que membre, je veux ajouter et retirer des produits de mes favoris afin de les retrouver facilement.
- Un produit ne peut être ajouté qu'une fois (RG-16).
- La liste des favoris est accessible depuis l'espace membre.

**US-12 — Sauvegarder une comparaison** (MVP)
En tant que membre, je veux sauvegarder une comparaison sous un nom afin de la retrouver plus tard.
- La sauvegarde exige un nom et 2 à 4 produits.
- Si je ne suis pas connecté, je suis invité à me connecter ; ma sélection est conservée.

**US-13 — Gérer mes comparaisons** (MVP)
En tant que membre, je veux consulter, rouvrir et supprimer mes comparaisons sauvegardées.
- Un produit archivé depuis la sauvegarde apparaît avec la mention « produit retiré » (RG-11).
- La suppression demande une confirmation.

**US-14 — Supprimer mon compte** (MVP)
En tant que membre, je veux supprimer mon compte afin que mes données personnelles soient effacées.
- La suppression exige une confirmation (RG-17).
- Après suppression, mes données, favoris et comparaisons n'existent plus et je suis déconnecté.

### Épopée D — Administration

**US-15 — Accéder au back-office** (MVP)
En tant qu'administrateur, je veux accéder à un espace réservé afin de gérer le catalogue.
- Un utilisateur non administrateur qui tente d'accéder au back-office, par l'interface ou par l'API, est refusé.

**US-16 — Gérer marques et gammes** (MVP)
En tant qu'administrateur, je veux créer, modifier et supprimer des marques et des gammes.
- Une marque ou une gamme utilisée par un produit ne peut pas être supprimée ; un message l'explique.
- Les noms sont uniques dans leur périmètre : une marque est unique, une gamme est unique au sein de sa marque.

**US-17 — Créer ou modifier un produit** (MVP)
En tant qu'administrateur, je veux saisir un produit complet (informations, composition, constituants, additifs, formats) en une seule opération.
- L'enregistrement est **entièrement réussi ou entièrement annulé** : aucune donnée partielle n'est conservée en cas d'erreur.
- Toutes les données sont validées côté serveur (types, bornes, champs obligatoires).
- Une modification concurrente est détectée (RG-18).

**US-18 — Gérer les référentiels** (MVP)
En tant qu'administrateur, je veux gérer les listes d'ingrédients, d'additifs, de besoins spécifiques, de stades de vie et de gabarits.
- Un élément utilisé par au moins un produit ne peut pas être supprimé.

**US-19 — Enregistrer un relevé de prix** (MVP)
En tant qu'administrateur, je veux enregistrer un relevé de prix daté pour un format.
- Le relevé respecte les RG-03 et RG-04 ; le prix au kilo est calculé automatiquement (RG-05).
- Les relevés précédents sont conservés.
- Une liste des relevés à actualiser est disponible (RG-06).

**US-20 — Importer depuis Open Pet Food Facts** (MVP, à confirmer en conception)
En tant qu'administrateur, je veux importer un produit à partir de son code-barres afin de réduire la saisie manuelle.
- Si le code-barres est trouvé, les champs disponibles sont pré-remplis et le produit est créé selon la RG-19.
- Si le code-barres est inconnu ou si le service ne répond pas, un message explicite s'affiche et rien n'est créé.

**US-21 — Publier, dépublier, archiver** (MVP)
En tant qu'administrateur, je veux changer le statut d'un produit.
- La publication est refusée si les conditions de la RG-10 ne sont pas remplies ; les éléments manquants sont listés.

### Épopée E — Transverse

**US-22 — Informations légales** (MVP)
En tant que visiteur, je veux accéder aux mentions légales, à la politique de confidentialité et aux sources de données.
- Ces pages sont accessibles depuis toutes les pages.
- L'attribution Open Pet Food Facts et sa licence (ODbL) sont mentionnées.

### User stories complémentaires (sans critères détaillés à ce stade)

- US-C1 — Sauvegarder une recherche (filtres).
- US-C2 — Réinitialiser son mot de passe par e-mail.
- US-C3 — Consulter l'historique des prix d'un produit.
- US-C4 — Exporter une comparaison.
- US-C5 — Exporter ses données personnelles.

---

## 9. Exigences non fonctionnelles

| ID | Exigence | Détail |
|---|---|---|
| ENF-01 | Sécurité | Référentiel OWASP Top 10 ; validation de toutes les entrées côté serveur ; mots de passe hachés ; requêtes paramétrées ; contrôle d'accès par rôle ; limitation des tentatives de connexion ; HTTPS en production ; comptes de base de données au moindre privilège ; aucun secret versionné. |
| ENF-02 | RGPD | Minimisation des données collectées ; information des utilisateurs ; suppression du compte ; aucun traceur soumis à consentement **(à valider en conception)**. |
| ENF-03 | Accessibilité | Respect des critères du RGAA : structure sémantique, navigation au clavier, contrastes, libellés de formulaires, annonces des mises à jour dynamiques. |
| ENF-04 | Responsive | Conception mobile first ; utilisable de 320 px à grand écran. |
| ENF-05 | Performance et éco-conception | Pagination des résultats ; pas d'images lourdes ; limitation des requêtes et des dépendances. |
| ENF-06 | Référencement | Fiches produits indexables ; URLs lisibles ; balises title et meta ; plan du site. |
| ENF-07 | Maintenabilité | Architecture en couches ; programmation orientée objet côté serveur ; tests unitaires ; linter ; documentation technique, en partie en anglais. |
| ENF-08 | Compatibilité | Dernières versions de Chrome, Firefox, Edge et Safari. |
| ENF-09 | Déployabilité | Configuration par variables d'environnement ; environnement de développement conteneurisé ; procédure de déploiement documentée. |

---

## 10. Contraintes

- **Organisation** : projet réalisé seul, sans échéance imposée pour le devoir ; déploiement réel prévu après la correction du mentor.
- **Outils imposés** : VS Code, Figma, Looping, Git/GitHub.
- **Données** : aucune donnée produit inventée ; toute donnée est sourcée et datée ; licence ODbL pour les données dérivées d'Open Pet Food Facts ; pas de photos de produits (droits sur les packagings).
- **Juridique** : aucune recommandation vétérinaire ; respect des conditions d'utilisation des sites consultés (pas de collecte automatisée) ; code publié sans licence (tous droits réservés).
- **Examen** : couverture des critères d'évaluation du référentiel DWWM.

---

## 11. Livrables

1. Dépôt GitHub public, organisé et documenté.
2. Dossier de projet (30 à 50 pages hors annexes).
3. Diaporama de présentation.
4. Maquettes Figma (web et mobile), MCD/MLD (Looping), documentation technique et procédure de déploiement.

---

## 12. Hypothèses et points ouverts

| ID | Élément | Statut |
|---|---|---|
| H-01 | La cible du site achète majoritairement en circuit spécialisé ou en ligne | Hypothèse non démontrée à l'échelle du marché |
| H-02 | 30 à 45 produits suffisent à démontrer l'intérêt du comparateur | Hypothèse |
| PO-01 | Chiffres de la source secondaire de marché | À vérifier avant citation |
| PO-02 | Rôle exact de la base NoSQL et de l'import Open Pet Food Facts | Conception |
| PO-03 | Stack technique | Conception |

---

## Annexe — Correspondance user stories → compétences

| User stories | Compétences principalement mobilisées |
|---|---|
| US-01 à US-08 | CP2, CP3, CP4 (interfaces, filtres dynamiques, comparateur) ; CP6 (requêtes de recherche et de filtrage) ; CP7 (règles de calcul RG-05, RG-07) |
| US-09 à US-14 | CP4 (formulaires) ; CP7 (authentification, autorisations) ; CP6 (accès aux données) ; ENF-01 et ENF-02 |
| US-15 à US-21 | CP5 (modèle, contraintes d'intégrité) ; CP6 (transactions, conflits d'accès, NoSQL) ; CP7 (composants métier, appel d'un web service) |
| US-22 | CP3 (RGPD, mentions légales) |
| Transverse | CP1 (environnement, conteneurs) ; CP8 (procédure de déploiement) |
