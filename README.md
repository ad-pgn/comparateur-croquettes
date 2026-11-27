# comparateur-croquettes

Comparateur factuel de croquettes pour chiens commercialisées en France.

> Projet en cours — phase de développement (socle technique). Aucune fonctionnalité n'est encore disponible.

## Présentation

Application web permettant de mettre côte à côte des produits précis avec leur coût réel
(prix au kilo par format, relevé et daté) et la source de chaque donnée.
Projet réalisé dans le cadre du titre professionnel Développeur Web et Web Mobile (DWWM).

## About (English)

Fact-based web app to compare dog kibble sold in France: compare specific products side by side,
with their real cost (price per kg by bag size, dated) and the source of every data point.
Final project for the French "Développeur Web et Web Mobile" professional certification.
Status: development phase (technical foundation) — no feature available yet.

## Documentation

- [Expression des besoins](docs/expression-des-besoins.md)
- [Journal de projet](docs/journal-de-projet.md)
- [Architecture (EN)](docs/architecture.md)
- [Data dictionary (EN)](docs/data-model/data-dictionary.md)
- [Data import (EN)](docs/data-import.md)
- [API contract (EN)](docs/api-contract.md)
- [Visual identity (EN)](docs/visual-identity.md)
- [Annotations des wireframes (FR)](docs/design/annotations-wireframes.md)
- [Schéma d'enchaînement des écrans (FR)](docs/design/navigation-flow.md)
- Maquettes : [`docs/design/mockups/`](docs/design/mockups/)

## Stack technique

Choix validés en phase de conception. Mise en place en cours (milestone M2).

| Couche | Technologies |
|---|---|
| Front-end | Next.js (React), Sass avec CSS Modules |
| Back-end | API REST Node.js / Express |
| Base relationnelle | MySQL, Sequelize |
| Base NoSQL | MongoDB (rôle précisé en conception) |
| Tests | Vitest, Supertest |
| Qualité | ESLint, Prettier, GitHub Actions |
| Environnement de développement | Docker (bases de données) |

## Installation

> Section complétée au fil du milestone M2.

### Prérequis

- [Node.js](https://nodejs.org/) 26 (version fixée dans `.nvmrc`)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (bases de données en conteneurs)
- [Git](https://git-scm.com/)

### Structure du dépôt

| Dossier | Contenu |
|---|---|
| `api/` | API REST Express |
| `web/` | Application Next.js |
| `database/` | Scripts SQL et d'initialisation MongoDB |
| `docs/` | Documentation |

## Données

Il est prévu d'utiliser l'étiquetage officiel des fabricants et Open Pet Food Facts (licence ODbL).
Les sources et l'attribution seront détaillées lors de l'intégration des données.

## Licence

Tous droits réservés © 2026 Adrian Pogneau.
Le code est consultable publiquement mais ne peut pas être réutilisé sans autorisation.