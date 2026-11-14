# Schéma d'enchaînement des écrans

> Issue #11. Enchaînement des écrans des wireframes et des maquettes (`docs/design/`).
> Chaque flèche porte l'action qui provoque le passage d'un écran à l'autre.

## Navigation commune aux écrans publics

L'en-tête, présent sur tous les écrans publics, donne accès à trois destinations :

- le logo mène à l'accueil (E1) ;
- « Comparer (n) » mène au comparateur (E4) ;
- le lien du compte mène à la connexion (E5a) pour un visiteur, ou à l'espace membre (E6) pour un membre.

Le pied de page mène aux pages légales et à la page des sources des données.

## Schéma

```mermaid
flowchart TB
    subgraph PUB["Parcours public"]
        E1["E1 Accueil"]
        E2["E2 Résultats"]
        E2b["E2b Filtres (mobile)"]
        E3["E3 Fiche produit"]
        E4["E4 Comparateur"]
    end

    subgraph AUTH["Authentification"]
        E5a["E5a Connexion"]
        E5b["E5b Inscription"]
        E5c["E5c Mot de passe oublié"]
        E5d["E5d Nouveau mot de passe"]
    end

    subgraph MEMBER["Espace membre"]
        E6["E6 Mon compte"]
        E6b["E6b Confirmation de suppression"]
        E6c["E6c Mes informations"]
    end

    subgraph ADMIN["Back-office (administrateur)"]
        E7["E7 Liste des produits"]
        E8["E8 Formulaire produit"]
        E9["E9 Import par code-barres"]
    end

    E1 -->|"Recherche ou accès rapide"| E2
    E2 -->|"Filtres (n)"| E2b
    E2b -->|"Afficher n résultats ou Fermer"| E2
    E2 -->|"Nom du produit"| E3
    E2 -->|"Barre de comparaison : Comparer"| E4
    E3 -->|"Comparer"| E4
    E4 -->|"Nom du produit"| E3
    E4 -->|"Ajouter un produit"| E2

    E2 -->|"Favori (visiteur)"| E5a
    E3 -->|"Favori (visiteur)"| E5a
    E4 -->|"Connectez-vous pour enregistrer"| E5a

    E5a -->|"Créer un compte"| E5b
    E5b -->|"Se connecter"| E5a
    E5a -->|"Mot de passe oublié ?"| E5c
    E5c -->|"Lien reçu par e-mail"| E5d
    E5d -->|"Mot de passe enregistré"| E5a
    E5a -->|"Connexion réussie"| E6
    E5b -->|"Compte créé"| E6

    E6 -->|"Modifier l'adresse e-mail ou le mot de passe"| E6c
    E6c -->|"Fil d'Ariane : Mon compte"| E6
    E6 -->|"Supprimer mon compte"| E6b
    E6b -->|"Annuler"| E6
    E6b -->|"Suppression confirmée"| E1
    E6 -->|"Ouvrir une comparaison"| E4
    E6 -->|"Nom d'un favori"| E3
    E6 -->|"Se déconnecter"| E1
    E6 -->|"Accéder au back-office (administrateur)"| E7

    E7 -->|"Nouveau produit ou Modifier"| E8
    E7 -->|"Importer par code-barres"| E9
    E9 -->|"Créer le produit à partir de ces données"| E8
    E8 -->|"Enregistrer ou Annuler"| E7
    E7 -->|"Retour au site"| E1
```

## Précisions

- **Connexion réussie** : le membre revient sur la page où il se trouvait avant de se connecter, par exemple la fiche produit s'il voulait l'ajouter à ses favoris. Le schéma montre l'espace membre (E6) comme destination par défaut, quand aucune page d'origine n'existe.
- **E2b** n'existe qu'en mobile : en desktop, les filtres sont une colonne permanente de E2.
- **E6b** est une fenêtre de confirmation affichée par-dessus E6, et non une page distincte.
- **Les autres listes du back-office** (marques et gammes, référentiels, enseignes, relevés de prix, imports) reprennent le gabarit de E7 : elles sont accessibles depuis la barre latérale, et ne figurent pas dans le schéma pour le garder lisible.
- **Les routes d'accès protégé** : un visiteur qui tente d'ouvrir E6 ou E6c est redirigé vers E5a ; un membre qui tente d'ouvrir le back-office reçoit un refus (US-15).
