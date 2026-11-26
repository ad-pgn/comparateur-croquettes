# Sélection des produits

> Issue #12. Sélection figée le 26 novembre 2026 : elle sert de référence pour la saisie du catalogue.
> Version 1.0 — 26 novembre 2026 (filtrage final : 61 produits, 11 marques). Versions de travail 0.1 à 0.15 du 14 au 26 novembre 2026. Version 0.3 du 23 novembre 2026 (Royal Canin, règle du prix relevé, collecte large puis filtrage). Version 0.1 du 14 novembre 2026.

## 1. Objectif

Choisir les produits du catalogue initial de façon documentée et reproductible, pour que le comparateur propose des comparaisons
pertinentes dès sa mise en ligne. Cible initiale : 30 à 45 produits de 10 à 12 marques ; cible révisée lors du filtrage final :
**61 produits de 11 marques** (section 7).

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
| 2 | Hill's (Science Plan) | ✓ | ✓ Truffaut, Zooplus (si vendu aussi chez Truffaut) ; pas de vente directe ; Maxi Zoo non trouvé | ✓ (humidité déclarée, énergie déclarée) | Retenue |
| 3 | Ultima | ✓ | ✓ Maxi Zoo, Zooplus (si même produit) ; pas de vente directe | ✓ constituants affichés (contrôle visuel), humidité et énergie non déclarées | Retenue |
| 4 | Purina (ONE) | ✓ | ✗ aucune source éligible pour les croquettes chien du site officiel | ✓ site officiel | Écartée (étape 2) |
| 5 | Advance | ✓ | ✗ aucune source éligible (Maxi Zoo : Veterinary Diets uniquement ; Truffaut : vendeur partenaire ; absente d'Animalis) | — | Écartée (étape 2) |
| 6 | Real Nature (Wilderness) | ✓ marque propre de Maxi Zoo | ✓ Maxi Zoo (source unique, marque exclusive) | ✓ fiches Maxi Zoo (humidité et énergie non déclarées) | Retenue |
| 7 | Josera (gamme principale) | ✓ | ✓ vente directe josera.fr, Zooplus | ✓ (énergie déclarée, humidité non déclarée) | Retenue |
| 8 | Acana | ✓ | ✓ Animalis (source unique : offres Zooplus de vendeurs partenaires, fiche Truffaut indisponible) | ✓ (humidité 12 % et énergie déclarées) | Retenue |
| 9 | Eukanuba (Life Care) | ✓ | ✓ Animalis, Truffaut ; pas de vente directe ; Zooplus non retenu (ancienne gamme) | ✓ (humidité et énergie non déclarées) | Retenue |
| 10 | Select Gold (Complete, Light, Sensitive) | ✓ marque propre de Maxi Zoo ; gamme Medica exclue (RG-02) | ✓ Maxi Zoo (source unique, marque exclusive) | ✓ fiches Maxi Zoo (humidité et énergie non déclarées) | Retenue |
| 11 | Edgard & Cooper | ✓ | ✓ vente directe, Zooplus, Truffaut (adulte) | ✓ contrôle visuel (énergie déclarée, humidité non déclarée) | Retenue |
| 12 | Nature's Variety (No Grain) | ✓ | ✓ Maxi Zoo, Animalis, Zooplus ; fiches Truffaut non retenues | ✓ contrôle visuel (humidité et énergie non déclarées) | Retenue |
| 13 | Lily's Kitchen | ✓ | ✓ Truffaut, Zooplus, Animalis | ✗ pas de site officiel français | Écartée (étape 3) |
| 14 | Marque propre Truffaut (nom à identifier) | — | — | — | Écartée (décision du 26/11/2026) |
| 15 | True Origins (Pure, Wild), probable marque propre d'Animalis | — | — | — | Écartée (décision du 26/11/2026) |
| 16 | Virbac Veterinary HPM | ✗ gamme vétérinaire (RG-02) | ✗ Zooplus : vendeurs partenaires ; Truffaut : fiches sans référence | — | Écartée (étape 1) |
| 17 | Réserve (repérées chez Animalis le 26/11/2026) : Ownat, Natura Diet, Pro-Nutrition Flatazor, Orijen, Wellness, Carnilove, Taste of the Wild | ? | ? | ? | À étudier si un segment manque de marques |

## 5. Matrice marque × segment

Chaque case contient le nom exact du produit retenu, ou « — » si la marque n'a pas de produit retenu dans ce segment.
Un produit « toutes tailles » ou « moyen et grand » qui apparaît en S2 et S3 n'est compté qu'une fois. La colonne « Hors segment » garde les produits utiles à la couverture
de la section 3 bis sans entrer dans un segment (par exemple un chiot de petit gabarit, S4 visant les gabarits moyen et grand).

| Marque (gamme) | S1 | S2 | S3 | S4 | S5 | S6 | S7 | Hors segment | Total |
|---|---|---|---|---|---|---|---|---|---|
| Royal Canin (Size Health Nutrition) | Mini Adult | Medium Adult | Maxi Adult | Medium Puppy | Medium Ageing 10+ | X-Small Sterilised | Maxi Digestive Care | — | 7 |
| Purina (Pro Plan) | Small & Mini Adult Everyday Nutrition | Medium Adult Everyday Nutrition | Large Athletic Adult Everyday Nutrition | Medium Puppy Healthy Start | Medium & Large Adult 7+ Age Defence | All Sizes Adult Light / Sterilised poisson blanc | Medium & Large Adult Sensitive Digestion Grain Free dinde | Small & Mini Puppy Healthy Start (chiot petit gabarit) | 8 |
| Hill's (Science Plan) | Small & Mini Adult poulet | Adult Medium poulet | Adult Large Breed agneau + riz | Puppy Medium poulet | Senior Vitality Mature 7+ Small & Mini poulet + riz | Perfect Weight Adult Large Breed poulet | Perfect Digestion Adult Medium poulet + riz complet | — | 7 |
| Ultima | Petit Adulte avec du Poulet | Medium-Maxi Adulte avec du Poulet | Medium-Maxi Adulte avec du Poulet (même produit qu'en S2 : gabarits moyen et grand) | — | Medium-Maxi Senior avec du Poulet | Petit Stérilisé avec du Poulet | — | — | 4 |
| Real Nature (Wilderness) | Mini Adult Green Coast (canard, saumon, crevettes) | Adult True Country (poulet, poisson) | Adult grande taille Wide Savannah (sanglier, agneau, canard) | Maxi Junior Pur Canard | Senior True Country (poulet, poisson) | — | — | — | 5 |
| Josera (gamme principale) | Mini Chicken & Rice | Medi/Maxi Chicken & Rice | Medi/Maxi Chicken & Rice (même produit qu'en S2 : moyennes et grandes races) | Kids | Balance (senior) | — | SensiPlus | — | 5 |
| Acana | Adult Small Breed Recipe | Adult Dog Recipe | Adult Large Breed Recipe | Puppy Large Breed Recipe | Senior Recipe | Light & Fit Recipe | — | Puppy Small Breed Recipe (chiot petit gabarit) | 7 |
| Eukanuba (Life Care) | Adulte petites races poulet frais | Adulte moyennes races poulet frais | Adulte grandes races poulet frais | Chiot grandes races agneau et riz | Senior moyennes races poulet frais | — | — | — | 5 |
| Select Gold (Complete, Light, Sensitive) | Complete Mini Adulte Poulet | Complete Medium Adulte Poulet | Complete Maxi Adulte Bœuf | Complete Maxi Junior Poulet | Complete Medium Senior Poulet | Light Medium Adulte Poulet | Sensitive Medium Adulte Cheval au tapioca | — | 7 |
| Edgard & Cooper | — | Adulte Poulet Frais (toutes tailles) | — | Chiot Canard et Poulet frais (toutes tailles) | Senior Poulet & Saumon Frais | — | — | — | 3 |
| Nature's Variety (No Grain) | No Grain Mini Adulte Poulet | No Grain Adulte Medium/Maxi Poulet | No Grain Adulte Medium/Maxi Poulet (même produit qu'en S2 : plus de 10 kg) | No Grain Puppy Medium/Maxi Saumon | — | — | — | — | 3 |
| **Marques par segment** | 10 | 11 | 10 | 10 | 10 | 6 | 5 | 2 | **61** |

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
| 25/11/2026 | Hill's (Science Plan) | Éligibilité (RG-01, RG-02) | Fiches Truffaut ci-dessous | ✓ Vendue par Truffaut ; gamme Prescription Diet exclue (RG-02) ; aucune offre trouvée chez Maxi Zoo |
| 25/11/2026 | Hill's (Science Plan) | Vente directe | Fiches officielles ci-dessous | ✗ Pas de prix sur le site de la marque (renvoi vers les revendeurs) |
| 25/11/2026 | Small & Mini Adult agneau + riz (S1) | Données officielles | https://www.hillspet.fr/dog-food/science-plan-adult-small-miniature-lamb-rice-dry | ✓ Composition, constituants obligatoires, humidité (8 %), énergie (3 685 kcal/kg) |
| 25/11/2026 | Small & Mini Adult agneau + riz (S1) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/hills_science_plan_croquettes_chien/hills_science_plan_adulte_croquettes_chien/790980 | ✗ Zooplus seul (6 kg) : non retenu tant que le produit n'est pas trouvé dans un autre circuit éligible (RG-04) |
| 25/11/2026 | Adult Medium poulet (S2) | Données officielles | https://www.hillspet.fr/dog-food/science-plan-adult-medium-chicken-dry | ✓ Composition, constituants obligatoires, humidité (8 %), énergie (3 724 kcal/kg) |
| 25/11/2026 | Adult Medium poulet (S2) | Prix | https://www.truffaut.com/croquettes-chien-medium-advanced-fitness-poulet-12-kg-525471.html | ✓ Format 12 kg, vendu par Truffaut ; fiche à l'ancien nom « Advanced Fitness » (contrôler le sac à la saisie) |
| 25/11/2026 | Adult Large Breed agneau + riz (S3) | Données officielles | https://www.hillspet.fr/dog-food/science-plan-adult-large-breed-lamb-rice-dry | ✓ Composition, constituants obligatoires, humidité (8 %), énergie (3 701 kcal/kg) |
| 25/11/2026 | Adult Large Breed agneau + riz (S3) | Prix | https://www.truffaut.com/croquettes-chien-large-breed-advanced-fitness-agneau-riz-12-kg-368869.html | ✓ Format 12 kg, vendu par Truffaut, mais indisponible en ligne ; ancien nom « Advanced Fitness » |
| 25/11/2026 | Puppy Medium agneau + riz (S4) | Données officielles | https://www.hillspet.fr/dog-food/science-plan-puppy-lamb-rice-dry | ✓ Composition, constituants obligatoires, humidité (8 %), énergie (3 829 kcal/kg) |
| 25/11/2026 | Puppy Medium agneau + riz (S4) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/hills_science_plan_croquettes_chien/lots_economiques_croquettes_chien_hills/283618 | ✗ Sac unique de 18 kg, mais Zooplus seul : non retenu tant que le produit n'est pas trouvé dans un autre circuit éligible (RG-04) |
| 25/11/2026 | Senior Vitality Mature 7+ Small & Mini (S5) | Données officielles | https://www.hillspet.fr/dog-food/science-plan-adult-7-senior-vitality-mini-chicken-dry | ✓ Composition, constituants obligatoires, énergie (3 604 kcal/kg) ; humidité (8 %) donnée dans le tableau des valeurs nutritionnelles |
| 25/11/2026 | Senior Vitality Mature 7+ Small & Mini (S5) | Prix | https://www.truffaut.com/croquettes-petit-chien-age-au-poulet-science-plan-adult-7-1-5kg-824339.html | ✓ Format 1,5 kg, vendu par Truffaut |
| 25/11/2026 | Perfect Weight Adult Large Breed (S6) | Données officielles | https://www.hillspet.fr/dog-food/science-plan-adult-perfect-weight-large-breed-chicken-dry | ✓ Composition, constituants obligatoires, humidité (8 %), énergie (3 166 kcal/kg) ; chiens de 25 kg et plus, gestion du poids |
| 25/11/2026 | Perfect Weight Adult Large Breed (S6) | Prix | https://www.truffaut.com/croquettes-chien-grande-race-perfect-weight-poulet-12kg-537797.html | ✓ Format 12 kg, vendu par Truffaut. Le lien Zooplus proposé au départ (278044) est un lot 2 × 12 kg : non relevé |
| 25/11/2026 | Perfect Digestion Adult Medium (S7) | Données officielles | https://www.hillspet.fr/dog-food/science-plan-adult-perfect-digestion-medium-dry | ✓ Composition, constituants obligatoires, humidité (8 %), énergie (3 524 kcal/kg) |
| 25/11/2026 | Perfect Digestion Adult Medium (S7) | Prix | https://www.truffaut.com/croquettes-chien-race-moyenne-perfect-digestion-poulet-12kg-955026.html | ✓ Format 12 kg, vendu par Truffaut |
| 25/11/2026 | Perfect Digestion Adult Medium (S7) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/hills_science_plan_croquettes_chien/hills_science_plan_soin_special_croquettes_chien/1099037 | ✓ Sac unique de 14 kg (lot 2 × 14 kg non relevé) ; source valable car le produit est aussi vendu chez Truffaut |
| 25/11/2026 | Small & Mini Adult poulet (S1, remplace la version agneau) | Données officielles | https://www.hillspet.fr/dog-food/science-plan-adult-small-mini-chicken-dry | ✓ Composition, constituants obligatoires, énergie (3 721 kcal/kg) ; humidité (8 %) dans le tableau des valeurs nutritionnelles |
| 25/11/2026 | Small & Mini Adult poulet (S1) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/hills_science_plan_croquettes_chien/hills_science_plan_adulte_croquettes_chien/583173 | ✓ Sacs uniques de 3 et 6 kg (lot 2 × 6 kg non relevé). La fiche 9980010466 proposée au départ n'a pas pu être ouverte ; son numéro en 9980 correspond aux offres de vendeurs partenaires : non retenue |
| 25/11/2026 | Small & Mini Adult poulet (S1) | Prix | https://www.truffaut.com/croquettes-chien-petite-tres-petite-race-poulet-dinde-3kg-522555.html | ✓ Format 3 kg, vendu par Truffaut ; description de la fiche incohérente (mentionne aussi les seniors) : contrôler le sac à la saisie |
| 25/11/2026 | Puppy Medium poulet (S4, remplace la version agneau) | Données officielles | https://www.hillspet.fr/dog-food/science-plan-puppy-medium-chicken-dry | ✓ Composition, constituants obligatoires, humidité (8 %), énergie (3 749 kcal/kg) |
| 25/11/2026 | Puppy Medium poulet (S4) | Prix | https://www.truffaut.com/croquettes-chiot-medium-healthy-development-au-poulet-12-kg-368800.html | ✓ Format 12 kg, vendu par Truffaut ; ancien nom « Healthy Development » |
| 25/11/2026 | Puppy Medium poulet (S4) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/hills_science_plan_croquettes_chien/lots_economiques_croquettes_chien_hills/283618 | ✓ Variante « Puppy <1 Medium poulet », sac unique de 18 kg ; valable car le produit est aussi vendu chez Truffaut |
| 25/11/2026 | Ultima | Éligibilité et prix | https://www.maxizoo.fr/c/marques/ultima/ | ✓ 9 croquettes chien vendues par Maxi Zoo ; absente de Truffaut d'après les recherches ; pas de vente directe |
| 25/11/2026 | Ultima | Données officielles | https://www.ultima-affinity.com/fr/fr/chien/nourriture-chien/seche-medium-maxi-adult-poulet-1000297.html | ✓ Constituants analytiques affichés (25 % / 14 % / 3,2 % / 7 %, capture du 25/11/2026) : la section est chargée par un script, invisible pour l'outil de lecture automatique ; humidité et énergie non déclarées |
| 25/11/2026 | Petit Adulte avec du Poulet (S1) | Données officielles | https://www.ultima-affinity.com/fr/fr/chien/nourriture-chien/seche-petit-adulte-poulet-1000312.html | ✓ Formats 1,35, 2,75 et 7 kg ; matières grasses 16 % (contrôle visuel) ; humidité et énergie non déclarées |
| 25/11/2026 | Petit Adulte avec du Poulet (S1) | Prix | https://www.maxizoo.fr/p/ultima-croquettes-petit-chien-adulte-poulet-135-kg-1384050/ | ✓ Formats 1,35 et 7 kg (27 % / 16 % / 2,5 % / 7 %) |
| 25/11/2026 | Petit Adulte avec du Poulet (S1) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/ultima_croquettes_chien/croquettes/438808 | ✗ Matières grasses 17 % contre 16 % sur le site officiel : produit différent, non retenu |
| 25/11/2026 | Medium-Maxi Adulte avec du Poulet (S2, S3) | Prix | https://www.maxizoo.fr/p/ultima-medium-maxi-adulte-avec-du-poulet-75-kg-1164912/ | ✓ Format 7,5 kg (24 % / 12 % / 3 % / 6,5 %) |
| 25/11/2026 | Medium-Maxi Adulte avec du Poulet (S2, S3) | Données officielles | https://www.ultima-affinity.com/fr/fr/chien/nourriture-chien/seche-medium-maxi-adult-poulet-repas-1000295.html | ✓ Référence 1000295 : constituants identiques au sac Maxi Zoo (contrôle visuel). Les références 1000294 et 1000297 ne sont pas retenues |
| 25/11/2026 | Medium-Maxi Adulte avec du Poulet (S2, S3) | Prix | Zooplus | ✗ Seul un sac de 18 kg « poulet, riz » est proposé, format absent du site officiel : produit différent, non retenu |
| 25/11/2026 | Medium-Maxi Senior avec du Poulet (S5) | Données officielles | https://www.ultima-affinity.com/fr/fr/chien/nourriture-chien/seche-medium-maxi-senior-poulet-repas-1000301.html | ? Formats 2 et 7,5 kg ; constituants à relever visuellement |
| 25/11/2026 | Medium-Maxi Senior avec du Poulet (S5) | Prix | https://www.maxizoo.fr/p/ultima-medium-maxi-senior-avec-du-poulet-75-kg-1164914/ | ✓ Format 7,5 kg. Zooplus (3 et 12 kg, formats absents du site officiel) non retenu |
| 25/11/2026 | Petit Stérilisé avec du Poulet (S6) | Prix | https://www.maxizoo.fr/p/ultima-petit-strilis-avec-du-poulet-135-kg-1384104/ | ✓ Format 1,35 kg (29 % / 13 % / 5 % / 7,4 %) |
| 25/11/2026 | Petit Stérilisé avec du Poulet (S6) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/ultima_croquettes_chien/2301653 | ✓ Sac unique de 1,35 kg, constituants identiques à Maxi Zoo (lot 2 × 1,35 kg non relevé) |
| 25/11/2026 | Petit Stérilisé avec du Poulet (S6) | Données officielles | https://www.ultima-affinity.com/fr/fr/chien/nourriture-chien/seche-petit-sterilise-poulet-1000322.html | ✓ Format 1,35 kg ; composition et constituants analytiques publiés ; chiens stérilisés de 1 à 10 kg |
| 25/11/2026 | Medium-Maxi Light in Fat avec du Poulet (S6, candidat) | Données officielles | https://www.ultima-affinity.com/fr/fr/chien/nourriture-chien/seche-medium-maxi-light-in-fat-poulet-1000306.html | ? Formats 2 et 7,5 kg ; constituants à relever visuellement |
| 25/11/2026 | Medium-Maxi Light in Fat avec du Poulet (S6, candidat) | Prix | https://www.maxizoo.fr/p/ultima-medium-maxi-light-formule--fat--au-poulet-75-kg-1164913/ | ✓ Format 7,5 kg |
| 25/11/2026 | Ultima (S4, S7) | Couverture | https://www.zooplus.fr/shop/chiens/croquettes_chien/ultima_croquettes_chien | ✗ Medium-Maxi Junior et Sensitive saumon seulement sur Zooplus, dans des formats absents du site officiel : aucun produit retenu |
| 25/11/2026 | Petit Junior avec du Poulet (hors segment) | Données officielles | https://www.ultima-affinity.com/fr/fr/chien/nourriture-chien/seche-petit-junior-poulet-1000316.html | ✓ Chiot de petit gabarit ; formats 1,35 et 2,75 kg ; composition publiée, constituants à contrôler visuellement à la saisie |
| 25/11/2026 | Petit Junior avec du Poulet (hors segment) | Prix | https://www.maxizoo.fr/p/ultima-petit-junior-avec-du-poulet-135-kg-1384101/ | ✓ Format 1,35 kg (31 % / 18,5 % / 2 % / 6,5 %). Pas de fiche Zooplus France trouvée |
| 25/11/2026 | Ultima (S7) | Couverture | Site officiel, Maxi Zoo | ✗ Aucune croquette digestion sensible trouvée (recherche faite aussi par Adrian) |
| 25/11/2026 | Purina (ONE) | Données officielles | https://www.purina.fr/chien/alimentation/purina-one/chien | ✓ 9 croquettes chien : Mini/Small (bœuf, active, sans céréales, contrôle du poids), Medium/Maxi (poulet, bœuf, agneau, active, contrôle du poids) ; ni chiot, ni senior, ni digestion |
| 25/11/2026 | Purina (ONE) | Prix | https://www.maxizoo.fr/c/marques/purina-one/ | ✗ Une seule croquette chien : Mini Adult Saumon 3 × 800 g, recette absente du site officiel français |
| 25/11/2026 | Purina (ONE) | Prix | Truffaut | ✗ Purina ONE vendu pour chats uniquement d'après les recherches |
| 25/11/2026 | Purina (ONE) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/purina_one_croquettes_chien | ✗ Gamme disponible, mais Zooplus ne compte pas sans autre circuit éligible (RG-04) |
| 25/11/2026 | Advance | Prix | https://www.maxizoo.fr/c/marques/affinity/ | ✗ Seule la gamme Veterinary Diets (exclue par RG-02) est vendue en croquettes chien ; le reste est des friandises |
| 25/11/2026 | Advance | Prix | https://www.truffaut.com/croquettes-chien-adult-medium-advance-1.html | ✗ Adult Medium 14 kg vendu par Nutricroc (vendeur partenaire, contrôle d'Adrian), indisponible |
| 25/11/2026 | Advance | Prix | Animalis | ✗ Absente (contrôle d'Adrian) |
| 25/11/2026 | Advance | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/affinity_advance | ✗ Gamme disponible, mais Zooplus ne compte pas sans autre circuit éligible (RG-04) |
| 25/11/2026 | Real Nature (Wilderness) | Éligibilité et données | https://www.maxizoo.fr/c/marques/real-nature-wilderness/ | ✓ Marque propre de Maxi Zoo (RG-02 n'exclut que les marques propres de la grande distribution) ; la fiche Maxi Zoo tient lieu de site officiel ; gamme sans céréales |
| 25/11/2026 | Mini Adult Green Coast (S1) | Données et prix | https://www.maxizoo.fr/p/real-nature-wilderness-mini-adult-green-coast-canard-au-saumon-et-aux-crevettes-1-kg-1083996008/ | ✓ Petite race (1 à 10 kg), dès 11 mois ; 1 kg ; constituants publiés (« fibres brutes » = cellulose brute) ; humidité et énergie non déclarées |
| 25/11/2026 | Adult True Country (S2) | Données et prix | https://www.maxizoo.fr/p/real-nature-wilderness-croquettes-chien-adulte-true-country-poulet-avec-poisson-12-kg-1083998001/ | ✓ Adulte toutes tailles (5 à 80 kg) ; 12 kg en promotion (prix barré 78,99 € à relever) ; lot 2 × 12 kg non relevé ; « matière inorganique » = cendres brutes |
| 25/11/2026 | Adult grande taille Wide Savannah (S3) | Données et prix | https://www.maxizoo.fr/p/real-nature-wilderness-croquettes-pour-chien-adulte-de-grande-taille-wide-savannah-sanglier-avec-agneau-et-canard-12-kg-1083998010/ | ✓ Adulte de 25 kg et plus ; 12 kg ; lot 2 × 12 kg non relevé |
| 25/11/2026 | Maxi Junior Pur Canard (S4) | Données et prix | https://www.maxizoo.fr/p/real-nature-wilderness-maxi-junior-pur-canard-4-kg-1297082/ | ✓ Chiot de grande race (poids adulte > 25 kg) ; 4 et 12 kg ; monoprotéine (canard) |
| 25/11/2026 | Senior True Country (S5) | Données et prix | https://www.maxizoo.fr/p/real-nature-wilderness-senior-true-country-poulet-au-poisson-4-kg-1083997007/ | ✓ Senior toutes tailles, dès 6 à 8 ans ; 1, 4 et 12 kg |
| 25/11/2026 | Real Nature (S6, S7) | Couverture | Maxi Zoo | ✗ Aucune croquette light, stérilisé ou digestion sensible (contrôle d'Adrian) |
| 25/11/2026 | Josera | Éligibilité et vente directe | https://www.josera.fr/nourriture-chien.html | ✓ Boutique officielle française (vente directe) ; Zooplus valable en seconde source ; absente de Truffaut et de Maxi Zoo d'après les recherches ; gammes JosiDog et Josera Help non retenues |
| 25/11/2026 | Mini Chicken & Rice (S1) | Données et prix | https://www.josera.fr/josera-miniwell.html | ✓ Adulte petite taille ; 900 g, 3 et 10 kg ; constituants et énergie (3 872 kcal/kg) ; humidité non déclarée |
| 25/11/2026 | Mini Chicken & Rice (S1) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/josera_croquettes_chien/chien_adulte/2406319 | ✓ « Josera Mini Adult poulet et riz », sacs de 900 g et 10 kg |
| 25/11/2026 | Medi/Maxi Chicken & Rice (S2, S3) | Données et prix | https://www.josera.fr/josera-large-breed.html | ✓ Adulte moyenne et grande race ; 3 et 12,5 kg ; constituants et énergie (3 663 kcal/kg) |
| 25/11/2026 | Medi/Maxi Chicken & Rice (S2, S3) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/josera_croquettes_chien/chien_adulte/2414646 | ✓ Sacs de 3 et 12,5 kg (lot 2 × 12,5 kg non relevé) |
| 25/11/2026 | Kids (S4) | Données et prix | https://www.josera.fr/josera-kids.html | ✓ Chiot moyenne et grande race, dès 6 semaines ; 900 g, 3 et 12,5 kg ; énergie (3 675 kcal/kg) |
| 25/11/2026 | Kids (S4) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/josera_croquettes_chien/chien_junior_chiot/2413774 | ✓ Sacs de 900 g, 3 et 12,5 kg ; constituants identiques |
| 25/11/2026 | Balance (S5) | Données et prix | https://www.josera.fr/josera-balance.html | ✓ Senior toutes races, besoins énergétiques réduits ; 900 g, 3 et 12,5 kg ; énergie (3 477 kcal/kg). Préféré à Senior Salmon & Rice, absent de Zooplus |
| 25/11/2026 | Balance (S5) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/josera_croquettes_chien/chien_age_senior/2397023 | ✓ Sacs de 900 g, 3 et 12,5 kg ; constituants identiques |
| 25/11/2026 | SensiPlus (S7) | Données et prix | https://www.josera.fr/josera-sensiplus.html | ✓ Adulte à digestion sensible, toutes tailles ; 900 g, 3 et 12,5 kg ; énergie (3 678 kcal/kg) ; sans gluten (contient du maïs) |
| 25/11/2026 | SensiPlus (S7) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/josera_croquettes_chien/chien_adulte/2397069 | ✓ Sacs de 900 g et 12,5 kg |
| 25/11/2026 | Light & Vital (S6) | Éligibilité | https://www.josera.fr/josera-light-vital.html | ✗ Présenté comme « aliment diététique complet pour réduire le surpoids » : exclu par RG-02 |
| 25/11/2026 | Josera | Prix | josera.fr | Prix « PVC » barrés d'environ 10 % sur plusieurs fiches, bandeau « Black Week » sur le site : prix PVC à relever |
| 25/11/2026 | Acana | Éligibilité et prix | https://www.animalis.com/marques/acana/ | ✓ 19 croquettes chien vendues par Animalis (contrôle d'Adrian puis vérification) ; pas de vente directe |
| 25/11/2026 | Acana | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/acana/9980002796 | ✗ Toutes les offres Zooplus proviennent de vendeurs partenaires |
| 25/11/2026 | Acana | Prix | https://www.truffaut.com/acana-pacifica-sans-cereales-croquettes-pour-chien-11-4kg.html | ✗ Seule fiche Truffaut, indisponible en ligne et en magasin |
| 25/11/2026 | Acana | Données officielles | https://emea.acana.com/fr-FR/pour-chiens/eu-aca-adult.html | ✓ Composition, additifs, constituants (humidité 12 %) et énergie (3 510 kcal/kg) affichés : contrôle visuel d'Adrian sur 4 à 5 fiches (composition et énergie chargées par un script) |
| 25/11/2026 | Adult Small Breed Recipe (S1) | Données et prix | https://emea.acana.com/fr-FR/pour-chiens/eu-aca-adult-small.html | ✓ Petites races ; 2 et 6 kg ; humidité 12 % ; Animalis : https://www.animalis.com/acana-croquettes-heritage-adult-small-breed-pour-chien-PM600001_M.html |
| 25/11/2026 | Adult Dog Recipe (S2) | Données et prix | https://emea.acana.com/fr-FR/pour-chiens/eu-aca-adult.html | ✓ Toutes races ; 2, 6, 11,4 et 17 kg ; humidité 12 % ; Animalis : https://www.animalis.com/acana-croquettes-adult-dog-recipe-au-poulet-pour-chiens-PM221907_M.html |
| 25/11/2026 | Adult Large Breed Recipe (S3) | Données et prix | https://emea.acana.com/fr-FR/pour-chiens/eu-aca-adult-large.html | ✓ Grandes races ; 11,4 et 17 kg ; humidité 12 % ; Animalis : https://www.animalis.com/acana-croquettes-adult-large-breed-au-poulet-pour-chien-PM600000_M.html |
| 25/11/2026 | Puppy Large Breed Recipe (S4) | Données et prix | https://emea.acana.com/fr-FR/pour-chiens/eu-aca-puppy-large.html | ✓ Chiot grande race ; 11,4 et 17 kg ; humidité 12 % ; Animalis : https://www.animalis.com/acana-croquettes-heritage-puppy-large-breed-pour-chiot-PM600010_M.html |
| 25/11/2026 | Senior Recipe (S5) | Données et prix | https://emea.acana.com/fr-FR/pour-chiens/eu-aca-senior.html | ✓ Senior toutes races ; 2, 6 et 11,4 kg ; humidité 12 % ; Animalis : https://www.animalis.com/acana-croquettes-heritage-senior-pour-chien-PM221906_M.html |
| 25/11/2026 | Light & Fit Recipe (S6) | Données et prix | https://emea.acana.com/fr-FR/pour-chiens/eu-aca-light-fit.html | ✓ Adulte toutes races, maintien d'un poids sain ; non présenté comme aliment diététique ; 2, 6 et 11,4 kg ; humidité 12 % ; Animalis : https://www.animalis.com/acana-croquettes-heritage-light-fit-pour-chien-PM600006_M.html |
| 25/11/2026 | Puppy Small Breed Recipe (hors segment) | Données et prix | https://emea.acana.com/fr-FR/pour-chiens/eu-aca-puppy-small.html | ✓ Chiot petit gabarit ; Animalis : https://www.animalis.com/acana-croquettes-heritage-puppy-small-breed-pour-chiot-PM221902_M.html |
| 25/11/2026 | Acana (S7) | Couverture | Site officiel, Animalis | ✗ Aucune croquette digestion sensible |
| 25/11/2026 | Eukanuba | Éligibilité et données | https://www.eukanuba.eu/fr-fr/chien/croquettes/adulte-petites-races-poulet-frais | ✓ Nouvelle gamme Life Care ; composition et constituants publiés ; humidité et énergie non déclarées ; Zooplus vend surtout l'ancienne gamme « Premium Nutrition » : non retenu |
| 25/11/2026 | Adulte petites races poulet frais (S1) | Données et prix | https://www.eukanuba.eu/fr-fr/chien/croquettes/adulte-petites-races-poulet-frais | ✓ 1 à 8 ans, 2 à 10 kg ; 3, 7,5 et 15 kg ; Animalis (3 et 15 kg) : https://www.animalis.com/eukanuba-croquettes-riche-en-poulet-frais-pour-chien-adulte-s-PM800705_M.html |
| 25/11/2026 | Adulte moyennes races poulet frais (S2) | Données et prix | https://www.eukanuba.eu/fr-fr/chien/croquettes/adulte-moyennes-races-poulet-frais | ✓ 1 à 7 ans ; 3 et 15 kg ; Animalis (3 et 15 kg) : https://www.animalis.com/eukanuba-croquettes-riche-en-poulet-frais-pour-chien-adulte-m-PM800706_M.html ; Truffaut 15 kg (vendu par Truffaut, indisponible en ligne) : https://www.truffaut.com/croquettes-au-poulet-pour-chien-adulte-taille-moyenne-15kg-1111874.html |
| 25/11/2026 | Adulte grandes races poulet frais (S3) | Données et prix | https://www.eukanuba.eu/fr-fr/chien/croquettes/adulte-grandes-races-poulet-frais | ✓ 25 à 90 kg ; 3 et 15 kg ; Animalis (3 et 15 kg) : https://www.animalis.com/eukanuba-croquettes-riche-en-poulet-frais-pour-chien-adulte-l/xl-PM800707_M.html |
| 25/11/2026 | Chiot grandes races agneau et riz (S4) | Données et prix | https://www.eukanuba.eu/fr-fr/chien/croquettes/chiot-grandes-races-agneau-et-riz | ✓ 1 à 18 mois (géantes : 24 mois) ; 3 et 12 kg ; Truffaut 12 kg (vendu par Truffaut, en stock) : https://www.truffaut.com/croquettes-agneau-au-riz-pour-chiot-grande-taille-12kg-1111876.html ; Animalis : https://www.animalis.com/eukanuba-croquettes-riche-en-agneau-pour-chiot-l/xl-PM800704_M.html |
| 25/11/2026 | Senior moyennes races poulet frais (S5) | Données et prix | https://www.eukanuba.eu/fr-fr/chien/croquettes/senior-moyennes-races-poulet-frais | ✓ 10 ans et plus ; 3 et 15 kg ; Animalis (3 et 15 kg) : https://www.animalis.com/eukanuba-croquettes-riche-en-poulet-frais-pour-chien-senior-m-PM800711_M.html |
| 25/11/2026 | Special Care Weight Control (S6) | Prix | https://www.maxizoo.fr/p/eukanuba-weight-control-medium-breed-15-kg-1013178/ | ✗ Format 15 kg absent du site officiel (2,3 et 12 kg) et constituants différents (cellulose 2,5 % contre 2,7 %, cendres 7 % contre 6 %) : ancienne recette, non retenue |
| 25/11/2026 | Special Care Sensitive Digestion (S7) | Prix | https://www.maxizoo.fr/p/eukanuba-daily-care-digestion-sensible-2x12-kg-1297527/ | ✗ Lot 2 × 12 kg uniquement, indisponible ; absent d'Animalis (contrôle d'Adrian) |
| 26/11/2026 | Select Gold | Éligibilité et données | https://www.maxizoo.fr/c/chien/nourriture-pour-chien/nourriture-seche/?q=::brand:SELE | ✓ Marque propre de Maxi Zoo, 47 références de croquettes ; la fiche Maxi Zoo tient lieu de site officiel ; gamme Medica (19 références d'aliments diététiques) exclue par RG-02 |
| 26/11/2026 | Complete Mini Adulte Poulet (S1) | Données et prix | https://www.maxizoo.fr/p/select-gold-complete-croquettes-chien-adulte-mini-poulet-4-kg-1001478003/ | ✓ 5 à 10 kg, dès 8 mois ; 1, 4 et 10 kg ; composition et constituants publiés ; humidité et énergie non déclarées |
| 26/11/2026 | Complete Medium Adulte Poulet (S2) | Données et prix | https://www.maxizoo.fr/p/select-gold-complete-croquettes-chien-adulte-medium-poulet-4-kg-1001478007/ | ✓ 11 à 25 kg, dès 12 mois ; 4 et 12 kg (12 kg marqué « PROMO friends » : prix non-membre à relever) |
| 26/11/2026 | Complete Maxi Adulte Bœuf (S3) | Données et prix | https://www.maxizoo.fr/p/select-gold-complete-croquettes-chien-adulte-maxi-buf-4-kg-1001478013/ | ✓ Plus de 25 kg, dès 15 mois ; 4 et 12 kg ; 4 kg en promotion (prix barré 27,99 € à relever) |
| 26/11/2026 | Complete Maxi Junior Poulet (S4) | Données et prix | https://www.maxizoo.fr/p/select-gold-complete-maxi-junior-poulet-12-kg-1001492001/ | ✓ Grandes races (25 kg et plus), jusqu'à environ 15 mois ; 12 kg (« PROMO friends » : prix non-membre à relever) |
| 26/11/2026 | Complete Medium Senior Poulet (S5) | Données et prix | https://www.maxizoo.fr/p/select-gold-croquettes-pour-chien-complete-medium-senior-au-poulet-4-kg-1001478010/ | ✓ 11 à 25 kg, dès 8 ans ; 4 et 12 kg (12 kg « PROMO friends ») |
| 26/11/2026 | Light Medium Adulte Poulet (S6) | Données et prix | https://www.maxizoo.fr/p/select-gold-croquettes-chien-light-medium-adulte-poulet-4-kg-1001478009/ | ✓ 11 à 25 kg, tendance au surpoids ; aliment complet (pas « diététique ») ; 4 et 12 kg |
| 26/11/2026 | Sensitive Medium Adulte Cheval au tapioca (S7) | Données et prix | https://www.maxizoo.fr/p/select-gold-sensitive--croquettes-pour-chiens-adultes-de-taille-moyenne-cheval-au-tapioca-1-kg-1001743015/ | ✓ 11 à 25 kg, dès 12 mois ; « soulage le système digestif », « idéal en cas d'intolérances » ; 1, 4 et 12 kg (lot 2 × 12 kg non relevé) |
| 26/11/2026 | Edgard & Cooper | Données officielles | https://www.edgardcooper.com/fr/collections/dogs/ | ✓ Site chargé par un script, illisible par l'outil : relevé visuel d'Adrian. Vente directe en euros ; recettes sans distinction de gabarit ; aucune recette light ou digestion sensible |
| 26/11/2026 | Adulte Poulet Frais (S2) | Données officielles | https://www.edgardcooper.com/fr/collections/dogs/ | ✓ Toutes tailles ; 0,7, 1, 2,5, 3, 7 et 12 kg ; constituants publiés ; énergie 371,1 kcal/100 g ; humidité non déclarée |
| 26/11/2026 | Adulte Poulet Frais (S2) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/edgard_cooper | ✓ Vendu par Zooplus sous « Medium Adult Dog Poulet » (2,5 et 7 kg) et « Large Adult Dog Poulet » (12 kg) : formats officiels, même produit ; valable car vendu en direct par la marque |
| 26/11/2026 | Adulte Poulet Frais (S2) | Prix | https://www.truffaut.com/croquettes-canard-poulet-7kg-749235.html | ✓ « Croquettes chien adultes sans céréales au poulet frais, toutes tailles », 7 kg, vendu par Truffaut (livraison indisponible lors de la vérification) |
| 26/11/2026 | Chiot Canard et Poulet frais (S4) | Données officielles | https://www.edgardcooper.com/fr/collections/dogs/ | ✓ Toutes tailles ; 1, 2,5, 3, 7 et 12 kg ; énergie 383,2 kcal/100 g ; humidité non déclarée |
| 26/11/2026 | Chiot Canard et Poulet frais (S4) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/edgard_cooper/chiot/1613832 | ✓ Vendu par Zooplus (« Medium Puppy » 2,5 et 7 kg, « Large Puppy » 12 kg) |
| 26/11/2026 | Senior Poulet & Saumon Frais (S5) | Données officielles | https://www.edgardcooper.com/fr/collections/dogs/ | ✓ 2,5, 7 et 12 kg ; énergie 348,6 kcal/100 g ; humidité non déclarée |
| 26/11/2026 | Senior Poulet & Saumon Frais (S5) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/edgard_cooper/senior/1599918 | ✓ Vendu par Zooplus (« Medium Senior » 2,5 et 7 kg, « Large Senior » 12 kg) |
| 26/11/2026 | Edgard & Cooper | Prix | Animalis | ? Fiches présentes, mais inaccessibles à l'outil (accès refusé par le site) : non comptées |
| 26/11/2026 | Nature's Variety | Prix | https://www.truffaut.com/croquette-chien-original-medium-max-poulet-nature-s-variety.html | ✗ Fiches Truffaut sans numéro de référence, indisponibles, avec vendeurs partenaires et prix incohérents : non retenues |
| 26/11/2026 | Nature's Variety | Éligibilité et prix | https://www.maxizoo.fr/c/marques/natures-variety/ | ✓ 14 croquettes chien vendues par Maxi Zoo (toutes à -20 % : prix barrés à relever) ; présente chez Animalis (21 références) ; Zooplus valable en seconde source |
| 26/11/2026 | Nature's Variety | Données officielles | https://www.naturesvariety.com/fr/chien/croquettes-chien/selected-no-grain-medium-maxi-poulet-plein-air-1000199.html | ✓ Site inaccessible à l'outil : contrôle visuel d'Adrian (composition, additifs et constituants affichés ; humidité et énergie non déclarées) |
| 26/11/2026 | No Grain Mini Adulte Poulet (S1) | Prix | https://www.maxizoo.fr/p/natures-variety-no-grain-mini-adulte-poulet-15-kg-1356577/ | ✓ Adulte 1 à 10 kg ; 1,5 kg |
| 26/11/2026 | No Grain Adulte Medium/Maxi Poulet (S2, S3) | Prix | https://www.maxizoo.fr/p/natures-variety-no-grain-adulte-medmax-poulet-3-kg-2035040/ | ✓ Adulte de plus de 10 kg ; 3 et 10 kg |
| 26/11/2026 | No Grain Adulte Medium/Maxi Poulet (S2, S3) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/natures_variety/selected/1077709 | ✓ Vendu par Zooplus |
| 26/11/2026 | No Grain Puppy Medium/Maxi Saumon (S4) | Prix | https://www.maxizoo.fr/p/natures-variety-no-grain-puppy-medmax-saumon-10-kg-2035045/ | ✓ Chiot medium/maxi, 2 à 12 mois ; 10 kg |
| 26/11/2026 | No Grain Puppy Medium/Maxi Saumon (S4) | Prix | https://www.zooplus.fr/shop/chiens/croquettes_chien/natures_variety/original_no_grain/1077716 | ✓ Vendu par Zooplus |
| 26/11/2026 | No Grain Chiot Mini Saumon (hors segment) | Prix | https://www.maxizoo.fr/p/natures-variety-no-grain-chiot-mini-saumon-15kg-2035046/ | ✓ Chiot mini, 2 à 12 mois ; 1,5 kg |
| 26/11/2026 | Lily's Kitchen | Données officielles | Recherche web | ✗ Pas de site officiel français trouvé (site britannique, recettes possiblement différentes) ; gamme française limitée aux adultes toutes tailles |
| 26/11/2026 | Animalis | Marques | https://www.animalis.com/chiens/alimentation/croquettes/?start=0&page=1 | 48 marques de croquettes chien ; Purina ONE et Advance absentes (confirmé) |
| 26/11/2026 | Virbac Veterinary HPM | Éligibilité (RG-02) | https://pro-fr.virbac.com/files/live/sites/virbac-b2b-fr/files/Gammes/Nutrition/revamping/sous-main-gamme-nutritionnelle-hpm.pdf | ✗ Gamme présentée comme vétérinaire (nom « Veterinary », diffusion auprès des vétérinaires) ; Zooplus : offres de vendeurs partenaires (9980) ; Truffaut : fiches sans numéro de référence |

## 7. Décisions

- **Prix relevé (23/11/2026)** : on relève toujours le prix public standard, en achat unique, sans abonnement, sans code promo,
  sans remise de fidélité ni de première commande, et hors frais de port. Les lots (par exemple 2 × 12 kg) et les sacs
  promotionnels (« + X kg offerts ») ne sont pas relevés. Raison : comparer des prix obtenus dans les mêmes conditions.
- **Prix barré (25/11/2026)** : quand une promotion est affichée, on relève le prix barré (prix habituel de l'enseigne), pas le prix
  promotionnel. Raisons : la réglementation impose que le prix barré soit le prix le plus bas pratiqué dans les 30 jours précédant
  la réduction ; une promotion se termine souvent avant la mise à jour suivante des relevés.
- **Prix conseillé (25/11/2026)** : un « prix conseillé » barré affiché à titre de comparaison (cas de Zooplus) n'est pas une
  promotion : on relève le prix de vente affiché. La règle du prix barré ne s'applique qu'à une promotion temporaire
  (mention « promo », pourcentage de réduction ou date de fin).
- **Liens (25/11/2026)** : on enregistre l'adresse d'une fiche sans ses paramètres de suivi (tout ce qui suit le « ? »).
- **Plusieurs sources par produit (23/11/2026)** : un produit peut avoir plusieurs relevés (vente directe marque et revendeurs).
  Le comparateur affiche le prix au kilo le plus bas avec sa source et sa date ; la fiche produit montre tous les relevés.
- **Vendeur (23/11/2026)** : un prix n'est relevé que s'il est vendu par l'enseigne elle-même. Les offres de vendeurs partenaires
  (marketplace, par exemple « Vendu par … » sur Truffaut, ou « Vendu et expédié par notre partenaire » sur Zooplus, dont les
  fiches ont un numéro commençant par 9980) ne sont pas des sources de la RG-04.
- **Collecte large puis filtrage (23/11/2026)** : tous les produits éligibles d'une marque sont collectés, même plusieurs par segment ;
  le filtrage final ramène le catalogue à 30 à 45 produits en respectant la section 3 bis. La règle « un produit par marque et par
  segment » est abandonnée au profit de cette couverture.
- **S4 Royal Canin (23/11/2026)** : Medium Puppy prioritaire, Maxi Puppy conservé comme candidat. Critère de popularité :
  Medium Puppy apparaît juste avant Maxi Puppy dans la liste Truffaut (tri à préciser).
- **Marque et gamme (25/11/2026)** : conformément au modèle de données (`brand` → `product_line` → `product`), la marque est le
  fabricant affiché (Purina) et la gamme la ligne commerciale (Pro Plan, ONE). Les sous-lignes (Everyday Nutrition, Healthy Start,
  Age Defence, Sensitive Digestion…) restent dans le nom du produit. Le décompte « 10 à 12 marques » porte sur les marques.
- **S4 Purina Pro Plan (25/11/2026)** : Medium Puppy Healthy Start prioritaire (même gabarit que le Medium Puppy Royal Canin),
  Large Athletic Puppy Sensitive Digestion candidat ; Small & Mini Puppy Healthy Start classé hors segment (S4 vise les gabarits
  moyen et grand), conservé pour la couverture des chiots de petit gabarit.
- **Ultima retenue (25/11/2026)** : écartée dans un premier temps (constituants non trouvés par l'outil de lecture automatique),
  puis réintégrée après contrôle visuel : les constituants sont affichés par un script. Conséquence : une absence de donnée constatée
  automatiquement est toujours confirmée visuellement avant d'écarter un produit.
- **Purina ONE écartée (25/11/2026)** : aucune croquette chien du site officiel n'est vendue par Truffaut ou Maxi Zoo (étape 2) ;
  la gamme est surtout distribuée en grande distribution et sur Zooplus. Absence chez Animalis confirmée par Adrian.
- **Advance écartée (25/11/2026)** : aucune croquette chien hors gamme vétérinaire n'est vendue par Truffaut, Maxi Zoo ou Animalis
  (étape 2) ; la seule offre Truffaut provient d'un vendeur partenaire.
- **Aliments diététiques (25/11/2026)** : RG-02 est appliquée à la lettre : un produit présenté par la marque comme « aliment
  diététique » est exclu, même vendu hors réseau vétérinaire (cas de Josera Light & Vital).
- **Josera, promotion « Black Week » (25/11/2026)** : dans le doute, on relève le prix PVC barré.
- **Animalis (25/11/2026)** : le site animalis.com est mal indexé par l'outil de recherche ; la présence d'une marque chez Animalis
  est vérifiée à la main avant d'écarter la marque (cas d'Acana, d'abord jugée sans source de prix).
- **Lily's Kitchen écartée (26/11/2026)** : aucun site officiel français ne publie les données des produits vendus en France (étape 3) ;
  la marque n'aurait de toute façon couvert que S2, déjà largement fourni.
- **Fiches Truffaut sans numéro de référence (26/11/2026)** : les fiches dont l'adresse ne se termine pas par un numéro de
  référence Truffaut se sont toutes révélées indisponibles ou partagées avec des vendeurs partenaires ; elles ne sont pas retenues.
- **Marques propres de Truffaut et d'Animalis écartées (26/11/2026)** : le nombre de marques (11) et de produits (environ 62) est
  suffisant ; leur identification et leur vérification auraient demandé un effort disproportionné.
- **Virbac Veterinary HPM écartée (26/11/2026)** : gamme vétérinaire par son nom et sa diffusion (RG-02) ; aucune source de prix
  éligible fiable.
- **Fin de la collecte (26/11/2026)** : toutes les candidates ont été étudiées.
- **Filtrage final (26/11/2026)** : option A retenue. Les 59 produits des segments sont conservés, ainsi que 2 chiots de petit
  gabarit hors segment (Pro Plan Small & Mini Puppy Healthy Start, deux sources de prix ; Acana Puppy Small Breed, humidité déclarée),
  soit **61 produits de 11 marques**. Candidats non retenus : Royal Canin Maxi Puppy, Pro Plan Large Athletic Puppy Sensitive
  Digestion, Ultima Medium-Maxi Light in Fat, Ultima Petit Junior, Nature's Variety No Grain Chiot Mini Saumon.
  Raisons : la couverture de la section 3 bis est complète, et la variété (protéines, gammes, sources de prix) sert la démonstration.
  Conséquences : la cible « 30 à 45 produits » de l'expression des besoins est révisée ; le catalogue est saisi principalement par
  un fichier de données et un script d'import, le back-office servant à la démonstration sur quelques produits.
- **Produits sans gabarit (26/11/2026)** : une recette adulte destinée à toutes les tailles est rangée en S2 dans la matrice ;
  dans l'application, son gabarit est « tous » et elle répond à tous les filtres de taille (cas d'Acana Adult Dog, Real Nature
  True Country, Edgard & Cooper).
- **Prix fidélité Maxi Zoo (26/11/2026)** : un prix marqué « PROMO friends » est réservé aux membres du programme de fidélité ;
  on relève le prix non-membre. Si la fiche n'affiche que le prix membre, le format n'est pas relevé.
- **Ajout de marques (25/11/2026)** : si, une fois la liste des candidates épuisée, un segment ou la section 3 bis n'est pas couvert,
  on ajoute d'autres marques candidates, en appliquant la même méthode.
- **Même produit chez deux revendeurs (25/11/2026)** : une seconde source de prix n'est retenue que si le produit est le même :
  même nom, format présent dans la liste officielle, constituants identiques. Une marque peut vendre sous le même nom des recettes
  différentes selon les pays ou les circuits.
- **Deux sources de prix (25/11/2026)** : quand la marque ne vend pas en direct, on cherche deux sources de prix par produit
  lorsque c'est possible.
- (à compléter : marques écartées et raison, arbitrages entre produits)
