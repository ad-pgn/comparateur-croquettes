# Sélection des produits

> Issue #12. Document de travail : il est complété au fil des vérifications, puis figé avant la saisie du catalogue.
> Version 0.4 — 25 novembre 2026 (Purina Pro Plan vérifiée, marque et gamme). Version 0.3 du 23 novembre 2026 (Royal Canin, règle du prix relevé, collecte large puis filtrage). Version 0.1 du 14 novembre 2026.

## 1. Objectif

Choisir **30 à 45 produits** de **10 à 12 marques** (expression des besoins, section 4), de façon documentée et reproductible,
pour que le comparateur propose des comparaisons pertinentes dès sa mise en ligne.

## 2. Méthode

La sélection applique quatre filtres successifs.

| Étape | Filtre | Règle |
|---|---|---|
| 1 | Éligibilité de la marque | RG-01 (commercialisé en France), RG-02 (pas de gamme vétérinaire exclusive, pas de marque propre de la grande distribution), marque propre d'un revendeur étranger exclue |
| 2 | Prix disponible | Au moins un relevé possible dans une source de la RG-04 (site de la marque, Maxi Zoo, Truffaut, Animalis ; Zooplus seulement si le produit est vendu dans un autre circuit éligible), selon la règle du prix relevé (section 7) |
| 3 | Données disponibles | Le site officiel de la marque publie la composition et les constituants analytiques obligatoires (protéines, matières grasses, cellulose, cendres). Seuls les constituants déclarés pour le marché français comptent : une analyse destinée à un autre pays (par exemple le bloc « RSA » des fiches Royal Canin) n'est pas reprise |
| 4 | Couverture des segments | Chaque segment retenu doit compter **au moins 4 marques**, pour permettre une comparaison complète de 4 produits |

En cas de choix entre plusieurs produits pour une même case : **popularité** (présence dans les meilleures ventes d'une source, relevée et datée),
puis **richesse des données** (humidité et énergie déclarées, utiles au calcul sur matière sèche).

La sélection se fait en deux temps : **collecte large** (tous les produits éligibles de chaque marque, plusieurs par segment si besoin),
puis **filtrage final** pour revenir à 30 à 45 produits en conservant la couverture décrite en section 3 bis.

## 3. Segments

| Code | Segment | Stade de vie | Gabarit | Besoin |
|---|---|---|---|---|
| S1 | Adulte petit gabarit | Adulte | Mini, petit | — |
| S2 | Adulte moyen gabarit | Adulte | Moyen | — |
| S3 | Adulte grand gabarit | Adulte | Grand, géant | — |
| S4 | Chiot | Chiot | Moyen, grand | — |
| S5 | Senior | Senior | Tous | — |
| S6 | Stérilisé ou light | Adulte | Tous | Stérilisé / contrôle du poids |
| S7 | Digestion sensible | Adulte | Tous | Digestion sensible |

Avec 7 segments et 5 à 6 marques par segment, on obtient 35 à 42 produits.

## 3 bis. Couverture à garantir lors du filtrage final

Le catalogue final doit permettre de tester chaque filtre et chaque calcul de l'application :

- chaque **stade de vie** (chiot, adulte, senior), chaque **gabarit** (mini à géant) et chaque **besoin** proposé dans les filtres
  renvoie au moins un produit ;
- au moins 4 marques par segment, pour une comparaison complète ;
- des produits **avec et sans humidité déclarée**, pour tester le calcul sur matière sèche et son absence (RG-07) ;
- des produits **avec et sans céréales** et avec des sources de protéines variées, pour tester l'exclusion d'ingrédients (RG-14) ;
- des produits avec **plusieurs formats** et **plusieurs sources de prix**, pour tester le prix au kilo le plus bas (RG-05) ;
- plusieurs **gammes** pour une même marque.

## 4. Marques candidates

Légende : ✓ vérifié · ✗ éliminatoire · ? à vérifier. Chaque vérification est datée et sourcée dans la section 6.

| Priorité | Marque (gamme) | Éligibilité | Prix (source) | Données officielles | Décision |
|---|---|---|---|---|---|
| — | Royal Canin (Size Health Nutrition) | ✓ | ✓ vente directe marque, Truffaut, Maxi Zoo | ✓ (humidité non déclarée) | Retenue |
| 1 | Purina (Pro Plan) | ✓ | ✓ Truffaut, Maxi Zoo (Animalis à confirmer) ; pas de vente directe | ✓ (humidité non déclarée, énergie déclarée) | Retenue |
| 2 | Hill's (Science Plan) | ? | ? | ? | |
| 3 | Ultima | ? | ? | ? | |
| 4 | Purina (ONE) | ? | ? | ? | |
| 5 | Advance | ? | ? | ? | |
| 6 | Real Nature (Maxi Zoo) | ? | ? | ? | |
| 7 | Josera | ? | ? | ? | |
| 8 | Acana | ? | ? | ? | |
| 9 | Eukanuba | ? | ? | ? | |
| 10 | Select Gold (Maxi Zoo) | ? | ? | ? | |
| 11 | Edgard & Cooper | ? | ? | ? | |
| 12 | Nature's Variety | ? | ? | ? | |
| 13 | Lily's Kitchen | ? | ? | ? | |
| 14 | Marque propre Truffaut (nom à identifier) | ? | ? | ? | |
| 15 | Marque propre Animalis (nom à identifier) | ? | ? | ? | |
| 16 | Virbac Veterinary HPM | ? | ? | ? | Éligibilité douteuse (RG-02) |

## 5. Matrice marque × segment

Chaque case contient le nom exact du produit prioritaire, les autres produits collectés entre parenthèses (« candidat »),
ou « — » si la marque n'a pas de produit dans ce segment. La colonne « Hors segment » garde les produits utiles à la couverture
de la section 3 bis sans entrer dans un segment (par exemple un chiot de petit gabarit, S4 visant les gabarits moyen et grand).

| Marque (gamme) | S1 | S2 | S3 | S4 | S5 | S6 | S7 | Hors segment | Total |
|---|---|---|---|---|---|---|---|---|---|
| Royal Canin (Size Health Nutrition) | Mini Adult | Medium Adult | Maxi Adult | Medium Puppy (candidat : Maxi Puppy) | Medium Ageing 10+ | X-Small Sterilised | Maxi Digestive Care | — | 7 (+1 candidat) |
| Purina (Pro Plan) | Small & Mini Adult Everyday Nutrition | Medium Adult Everyday Nutrition | Large Athletic Adult Everyday Nutrition | Medium Puppy Healthy Start, proposé (candidat : Large Athletic Puppy Sensitive Digestion) | Medium & Large Adult 7+ Age Defence | All Sizes Adult Light / Sterilised poisson blanc | Medium & Large Adult Sensitive Digestion Grain Free dinde | Small & Mini Puppy Healthy Start (chiot petit gabarit) | 7 (+2 candidats) |
| **Marques par segment** | 2 | 2 | 2 | 2 | 2 | 2 | 2 | | |

## 6. Journal des vérifications

Les prix sont seulement constatés à ce stade ; les relevés officiels (RG-03) sont saisis avec le catalogue.

| Date | Marque ou produit | Vérification | Source (URL) | Résultat |
|---|---|---|---|---|
| 23/11/2026 | Royal Canin | Éligibilité (RG-01, RG-02) | Truffaut, Maxi Zoo (fiches ci-dessous) | ✓ Gamme Size Health Nutrition vendue en jardinerie et animalerie, hors réseau vétérinaire |
| 23/11/2026 | Royal Canin | Vente directe | Fiches officielles ci-dessous | ✓ Boutique en ligne sur le site de la marque, achat unique ou abonnement : source « vente directe marque » |
| 23/11/2026 | Mini Adult (S1) | Données officielles | https://www.royalcanin.com/fr/dogs/products/retail-products/mini-adult-3001?ean=1-3182551055719 | ✓ Composition, constituants obligatoires, énergie (3 916 kcal/kg) ; humidité non déclarée |
| 23/11/2026 | Mini Adult (S1) | Prix | https://www.truffaut.com/croquettes-pour-chien-mini-adult-8kg-1083333.html | ✓ Format 8 kg |
| 23/11/2026 | Medium Adult (S2) | Données officielles | https://www.royalcanin.com/fr/dogs/products/retail-products/medium-adult-3004?ean=1-3182551055849 | ✓ Composition, constituants obligatoires ; humidité et énergie non déclarées |
| 23/11/2026 | Medium Adult (S2) | Prix | https://www.truffaut.com/croquettes-pour-chien-medium-adulte-12kg-1105081.html | ✓ Format 12 kg |
| 23/11/2026 | Maxi Adult (S3) | Données officielles | https://www.royalcanin.com/fr/dogs/products/retail-products/maxi-adult-3007 | ✓ Composition, constituants obligatoires, énergie (3 937 kcal/kg) ; humidité non déclarée |
| 23/11/2026 | Maxi Adult (S3) | Prix | https://www.truffaut.com/croquettes-pour-chien-maxi-adult-15kg-1083335.html | ✓ Format 15 kg |
| 23/11/2026 | Maxi Puppy (S4) | Données officielles | https://www.royalcanin.com/fr/dogs/products/retail-products/puppy---maxi-3006?ean=1-3182550778305 | ✓ Composition, constituants obligatoires, énergie (3 791 kcal/kg) ; humidité non déclarée |
| 23/11/2026 | Maxi Puppy (S4) | Prix | https://www.truffaut.com/croquettes-pour-chiot-maxi-12kg-1105083.html | ✓ Format 12 kg |
| 23/11/2026 | Medium Puppy (S4) | Données officielles | https://www.royalcanin.com/fr/dogs/products/retail-products/puppy---medium-3003?ean=1-3182550778077 | ✓ Composition, constituants obligatoires, énergie (4 125 kcal/kg) ; humidité non déclarée |
| 23/11/2026 | Medium Puppy (S4) | Prix | https://www.truffaut.com/croquettes-pour-chiot-medium-mois-12kg-1105029.html | ✓ Format 12 kg |
| 23/11/2026 | Medium Ageing 10+ (S5) | Données officielles | https://www.royalcanin.com/fr/dogs/products/retail-products/medium-ageing-10%2b-2448?ean=1-3182550802758 | ✓ Composition, constituants obligatoires ; humidité et énergie non déclarées |
| 23/11/2026 | Medium Ageing 10+ (S5) | Prix | https://www.truffaut.com/croquette-chien-mature-medium-ageing-10-15kg-447950.html | ✓ Format 15 kg |
| 23/11/2026 | X-Small Sterilised (S6) | Données officielles | https://www.royalcanin.com/fr/dogs/products/retail-products/x-small-sterilised-1019?ean=1-3182550832540 | ✓ Composition, constituants obligatoires ; humidité et énergie non déclarées ; chiens de 4 kg au plus |
| 23/11/2026 | X-Small Sterilised (S6) | Prix | https://www.maxizoo.fr/p/royal-canin-x-small-sterilised-15kg-1083903/ | ✓ Format 1,5 kg (seul format) |
| 23/11/2026 | Maxi Digestive Care (S7) | Données officielles | https://www.royalcanin.com/fr/dogs/products/retail-products/maxi-digestive-care-3055?ean=1-3182550928687 | ✓ Composition, constituants obligatoires ; humidité : à confirmer (absente des constituants analytiques lors de la vérification) |
| 23/11/2026 | Maxi Digestive Care (S7) | Prix | https://www.maxizoo.fr/p/royal-canin-digestive-care-maxi-12-kg-1376252/ | ✓ Formats 3 kg et 12 kg (lot 2 × 12 kg non relevé) |
| 25/11/2026 | Purina (Pro Plan) | Éligibilité (RG-01, RG-02) | Truffaut, Maxi Zoo (fiches ci-dessous) | ✓ Vendue par Truffaut et Maxi Zoo ; gamme Pro Plan Veterinary Diets exclue (RG-02) |
| 25/11/2026 | Purina (Pro Plan) | Vente directe | https://www.purina.fr/marques/proplan/chien | ✗ Pas d'achat ni de prix sur le site de la marque |
| 25/11/2026 | Small & Mini Adult Everyday Nutrition (S1) | Données officielles | https://www.purina.fr/chien/alimentation/proplan-croquettes-adulte-mini-poulet | ✓ Composition, constituants obligatoires, énergie (395 kcal/100 g) ; humidité non déclarée |
| 25/11/2026 | Small & Mini Adult Everyday Nutrition (S1) | Prix | https://www.maxizoo.fr/p/pro-plan-small--mini-adult-everyday-nutrition-14-kg-1209739/ | ✓ Format 14 kg (7 kg : fiche 1208633) |
| 25/11/2026 | Medium Adult Everyday Nutrition (S2) | Données officielles | https://www.purina.fr/chien/alimentation/proplan-croquettes-adulte-medium-poulet | ✓ Composition, constituants obligatoires, énergie (389 kcal/100 g) ; humidité non déclarée |
| 25/11/2026 | Medium Adult Everyday Nutrition (S2) | Prix | https://www.truffaut.com/croquettes-pour-chien-adulte-moyen-14-kg-569176.html | ✓ Format 14 kg, vendu par Truffaut ; recette non nommée sur la fiche (à contrôler sur la photo du sac) |
| 25/11/2026 | Large Athletic Adult Everyday Nutrition (S3) | Données officielles | https://www.purina.fr/chien/alimentation/proplan-adulte-large-athletic | ✓ Composition, constituants obligatoires, énergie (400 kcal/100 g) ; humidité non déclarée |
| 25/11/2026 | Large Athletic Adult Everyday Nutrition (S3) | Prix | https://www.truffaut.com/croquettes-pour-chien-adulte-athletique-14-kg-569194.html | ✓ Format 14 kg, vendu par Truffaut ; recette non nommée sur la fiche (à contrôler sur la photo du sac) |
| 25/11/2026 | Medium Puppy Healthy Start (S4) | Données officielles | https://www.purina.fr/chien/alimentation/proplan-croquettes-chiot-medium | ✓ Composition, constituants obligatoires, énergie (405 kcal/100 g) ; humidité non déclarée |
| 25/11/2026 | Medium Puppy Healthy Start (S4) | Prix | https://www.maxizoo.fr/p/pro-plan-puppy-medium-healthy-start-poulet-3-kg-1206411/ | ✓ Formats 3 kg et 12 kg |
| 25/11/2026 | Large Athletic Puppy Sensitive Digestion (S4) | Données officielles | https://www.purina.fr/chien/alimentation/proplan-chiot-large-athletic-digestion | ✓ Composition, constituants obligatoires, énergie (397 kcal/100 g) ; humidité non déclarée |
| 25/11/2026 | Large Athletic Puppy Sensitive Digestion (S4) | Prix | https://www.truffaut.com/pro-plan-large-athletic-sensitive-digestion-agneau-12-kg-877398.html | ✓ Format 12 kg, vendu par Truffaut (fiche Animalis à confirmer) |
| 25/11/2026 | Small & Mini Puppy Healthy Start (hors segment) | Données officielles | https://www.purina.fr/chien/alimentation/proplan-croquettes-chiot-mini-poulet | ✓ Composition, constituants obligatoires, énergie (413 kcal/100 g) ; humidité non déclarée |
| 25/11/2026 | Small & Mini Puppy Healthy Start (hors segment) | Prix | https://www.maxizoo.fr/p/pro-plan-chien-small--mini-puppy-riche-en-poulet-3-kg-1206419/ | ✓ Format 3 kg ; prix promotionnel affiché (-20 %, prix barré) |
| 25/11/2026 | Medium & Large Adult 7+ Age Defence (S5) | Données officielles | https://www.purina.fr/chien/alimentation/proplan-croquettes-senior-medium-large | ✓ Composition, constituants obligatoires, énergie (386 kcal/100 g) ; humidité non déclarée |
| 25/11/2026 | Medium & Large Adult 7+ Age Defence (S5) | Prix | https://www.maxizoo.fr/p/pro-plan-adult-7-medium--large-age-defence-poulet-14-kg-1206432/ | ✓ Format 14 kg (lot 2 × 14 kg non relevé) ; fiche Animalis à confirmer |
| 25/11/2026 | All Sizes Adult Light / Sterilised poisson blanc (S6) | Données officielles | https://www.purina.fr/chien/alimentation/proplan-croquette-adulte-sterilise-poisson | ✓ Composition, constituants obligatoires, énergie (345 kcal/100 g) ; humidité non déclarée |
| 25/11/2026 | All Sizes Adult Light / Sterilised poisson blanc (S6) | Prix | https://www.truffaut.com/croquettes-all-sizes-light-sterilised-au-poisson-blanc-pour-chien-14kg-1079063.html | ✓ Format 14 kg, vendu par Truffaut. La fiche 569189 proposée au départ ne précise pas la recette : non retenue |
| 25/11/2026 | Medium & Large Adult Sensitive Digestion Grain Free dinde (S7) | Données officielles | https://www.purina.fr/chien/alimentation/proplan-adulte-medium-digestion-dinde | ✓ Sans céréales ; composition, constituants obligatoires, énergie (381 kcal/100 g) ; humidité non déclarée |
| 25/11/2026 | Medium & Large Adult Sensitive Digestion Grain Free dinde (S7) | Prix | https://www.truffaut.com/croquettes-chien-pro-plan-m-adulte-digestion-dinde-12kg-786639.html | ✓ Format 12 kg, vendu par Truffaut |

## 7. Décisions

- **Prix relevé (23/11/2026)** : on relève toujours le prix public standard, en achat unique, sans abonnement, sans code promo,
  sans remise de fidélité ni de première commande, et hors frais de port. Les lots (par exemple 2 × 12 kg) et les sacs
  promotionnels (« + X kg offerts ») ne sont pas relevés. Raison : comparer des prix obtenus dans les mêmes conditions.
- **Plusieurs sources par produit (23/11/2026)** : un produit peut avoir plusieurs relevés (vente directe marque et revendeurs).
  Le comparateur affiche le prix au kilo le plus bas avec sa source et sa date ; la fiche produit montre tous les relevés.
- **Vendeur (23/11/2026)** : un prix n'est relevé que s'il est vendu par l'enseigne elle-même. Les offres de vendeurs partenaires
  (marketplace, par exemple « Vendu par … » sur Truffaut) ne sont pas des sources de la RG-04.
- **Collecte large puis filtrage (23/11/2026)** : tous les produits éligibles d'une marque sont collectés, même plusieurs par segment ;
  le filtrage final ramène le catalogue à 30 à 45 produits en respectant la section 3 bis. La règle « un produit par marque et par
  segment » est abandonnée au profit de cette couverture.
- **S4 Royal Canin (23/11/2026)** : Medium Puppy prioritaire, Maxi Puppy conservé comme candidat. Critère de popularité :
  Medium Puppy apparaît juste avant Maxi Puppy dans la liste Truffaut (tri à préciser).
- **Marque et gamme (25/11/2026)** : conformément au modèle de données (`brand` → `product_line` → `product`), la marque est le
  fabricant affiché (Purina) et la gamme la ligne commerciale (Pro Plan, ONE). Les sous-lignes (Everyday Nutrition, Healthy Start,
  Age Defence, Sensitive Digestion…) restent dans le nom du produit. Le décompte « 10 à 12 marques » porte sur les marques.
- (à compléter : marques écartées et raison, arbitrages entre produits)
