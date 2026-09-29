# comparateur-croquettes

Comparateur factuel de croquettes pour chiens commercialisées en France.

> Projet en cours — phase de conception. Aucune fonctionnalité n'est encore développée.

## Présentation

Application web permettant de mettre côte à côte des produits précis avec leur coût réel
(prix au kilo par format, relevé et daté) et la source de chaque donnée.
Projet réalisé dans le cadre du titre professionnel Développeur Web et Web Mobile (DWWM).

## About (English)

Fact-based web app to compare dog kibble sold in France: compare specific products side by side,
with their real cost (price per kg by bag size, dated) and the source of every data point.
Final project for the French "Développeur Web et Web Mobile" professional certification.
Status: design phase — no feature implemented yet.

## Documentation

- [Expression des besoins](docs/expression-des-besoins.md)
- [Journal de projet](docs/journal-de-projet.md)
- [Architecture (EN)](docs/architecture.md)

## Stack technique

Choix validés en phase de conception. Mise en place à venir.

| Couche | Technologies |
|---|---|
| Front-end | Next.js (React), Sass avec CSS Modules |
| Back-end | API REST Node.js / Express |
| Base relationnelle | MySQL, Sequelize |
| Base NoSQL | MongoDB (rôle précisé en conception) |
| Tests | Vitest, Supertest |
| Qualité | ESLint, Prettier, GitHub Actions |
| Environnement de développement | Docker (bases de données) |

## Données

Il est prévu d'utiliser l'étiquetage officiel des fabricants et Open Pet Food Facts (licence ODbL).
Les sources et l'attribution seront détaillées lors de l'intégration des données.

## Licence

Tous droits réservés © 2026 Adrian Pogneau.
Le code est consultable publiquement mais ne peut pas être réutilisé sans autorisation.