# Annotations des wireframes

> Issue #10. Annotations reportées sur les cadres Figma, sous forme de pastilles numérotées avec une note.
> Elles décrivent le comportement et l'accessibilité, que le dessin seul ne montre pas.
> Les écrans mobiles portent toutes les annotations ; les écrans desktop ne portent que celles qui leur sont propres,
> avec la mention « Comportements communs : voir les annotations de la version mobile ».

## Éléments communs (tous les écrans publics)

1. **Logo** : lien vers l'accueil ; texte alternatif « comparateur-croquettes — accueil ».
2. **Icône de compte** : nom accessible « Connexion » (visiteur) ou « Mon compte » (membre) ; zone cliquable de 44 px minimum ; libellé visible en desktop.
3. **« Comparer (n) »** : nombre de produits sélectionnés ; sans sélection, mène à une page expliquant comment ajouter des produits.
4. **Pied de page** : l'avertissement vétérinaire est présent sur toutes les pages (RG-20).
5. **Fil d'Ariane** : zone de navigation nommée « Fil d'Ariane » ; la page actuelle est signalée comme page courante et n'est pas un lien.

## E1 — Accueil

1. La recherche mène aux résultats (E2) avec le texte saisi.
2. Chaque étiquette d'accès rapide mène aux résultats déjà filtrés (E2) ; les valeurs proviennent des référentiels gérés dans le back-office.
3. Étiquettes d'au moins 44 px de haut.

## E2 — Résultats (mobile et desktop)

1. Extrait : la page affiche 20 produits (taille de page du contrat d'API) ; 24 résultats, soit 2 pages.
2. « Trier » est une liste déroulante native.
3. La croix de chaque filtre actif a un nom accessible : « Retirer le filtre Adulte ».
4. Le nombre de résultats est annoncé aux lecteurs d'écran à chaque changement de filtre (US-02).
5. Le nom du produit est un lien vers sa fiche (E3).
6. Un produit sélectionné affiche « Retirer de la comparaison » ; au-delà de 4 produits, l'ajout est refusé avec un message explicite (US-06).
7. Sans résultat : « Aucun produit ne correspond à votre recherche. Essayez de retirer un filtre. » (US-01).
8. Barre de comparaison fixée en bas de l'écran, affichée seulement si au moins un produit est sélectionné.
9. La page courante de la pagination est signalée aux lecteurs d'écran.
10. « Favori » pour un visiteur : mène à la connexion, puis ramène à la page avec le produit ajouté aux favoris.
11. Desktop : chaque filtre s'applique dès qu'il est coché ; la liste se met à jour sans bouton de validation.
12. Relevé de plus de 90 jours signalé « à actualiser » (RG-06).

## E2b — Panneau des filtres (mobile)

1. La section « Gamme » n'apparaît qu'une fois au moins une marque cochée, et ne liste que les gammes des marques sélectionnées.
2. Stade de vie, gabarit et besoins sont ouverts par défaut ; les autres sections sont repliées ; chaque titre affiche le nombre de choix actifs.
3. Chaque ligne de case à cocher est cliquable sur toute sa hauteur (44 px minimum).
4. La croix a pour nom accessible « Fermer les filtres » ; la touche Échap ferme aussi le panneau ; le focus revient sur le bouton « Filtres (n) ».
5. « Afficher n résultats » se met à jour à chaque filtre coché.
6. L'avertissement sous les exclusions est celui de la RG-14.

## E3 — Fiche produit (mobile et desktop)

1. Exemple : composition, constituants et additifs relevés sur royalcanin.com le 17/10/2026 ; prix relevés sur zooplus.fr ; le relevé du 17/03/2026 est fabriqué pour illustrer un prix à actualiser.
2. La bascule « Valeurs brutes / Matière sèche » signale le bouton actif aux lecteurs d'écran.
3. Humidité non déclarée : les valeurs sur matière sèche affichent « non calculable » (RG-07).
4. Relevé de plus de 90 jours signalé « à actualiser » (RG-06).
5. Le prix au kilo est calculé par l'API (RG-05).
6. Desktop : la colonne des constituants précède celle de la composition dans le code ; l'ordre de lecture reste celui du mobile.

## E4 — Comparateur (mobile et desktop)

1. Mobile : la colonne des critères reste fixe ; les produits défilent horizontalement.
2. Desktop : la ligne des noms de produits reste fixée en haut de l'écran pendant le défilement vertical.
3. Vrai tableau HTML, avec cellules d'en-tête de ligne et de colonne ; la zone défilante est accessible au clavier.
4. Chaque bouton « Retirer » a un nom complet : « Retirer Produit B de la comparaison ».
5. Repères ▲ ▼ en gras, sans couleur, expliqués par la légende (RG-12).
6. Les valeurs, y compris sur matière sèche, et les repères sont calculés par l'API.
7. Les produits comparés sont inscrits dans l'URL (`/comparer?produits=12,15,21`).
8. Visiteur : « Connectez-vous pour enregistrer cette comparaison » remplace le bouton d'enregistrement.
9. Membre : l'enregistrement ouvre une fenêtre demandant un nom (US-12).
10. Moins de 2 produits : « Ajoutez au moins deux produits pour les comparer » et un bouton « Parcourir les croquettes » (US-07).
11. « Ajouter un produit » n'apparaît que s'il y a moins de 4 produits.
12. Valeurs fictives.

## E5a — Connexion

1. Message d'erreur générique : il ne révèle pas si l'adresse existe (US-10).
2. Les tentatives répétées sont limitées.
3. « Afficher » a pour nom accessible « Afficher le mot de passe ».
4. Le lien « Mot de passe oublié ? » mène à la demande de réinitialisation (E5c, US-25).

## E5b — Inscription

1. L'aide « 12 caractères minimum » est liée au champ et lue par les lecteurs d'écran.
2. Le lien vers la politique de confidentialité s'ouvre dans un nouvel onglet, ce qui est indiqué dans son libellé.
3. Les erreurs s'affichent sous le champ concerné, sans effacer la saisie valide (US-09).

## E5c — Mot de passe oublié (demande)

1. Après l'envoi, le message est toujours le même, que l'adresse corresponde à un compte ou non : le formulaire ne permet pas de deviner quelles adresses sont inscrites (RG-22).
2. Si un compte existe, un e-mail contenant un lien de réinitialisation est envoyé ; le lien est à usage unique et valable 1 heure (RG-22).
3. Une nouvelle demande rend les liens précédents inutilisables.
4. Les demandes répétées sont limitées.
5. En développement, les e-mails sont capturés par un serveur d'envoi de test local : aucun e-mail réel n'est envoyé.

## E5d — Nouveau mot de passe

1. Page accessible uniquement par le lien reçu par e-mail ; le jeton figure dans l'adresse de la page.
2. Lien expiré, déjà utilisé ou invalide : « Ce lien n'est plus valable. » et un lien « Faire une nouvelle demande » vers E5c.
3. Le nouveau mot de passe respecte la RG-15 et doit être saisi deux fois de façon identique.
4. Après la réinitialisation : le jeton est marqué comme utilisé, toutes les sessions du membre sont fermées, puis redirection vers la connexion (E5a) avec le message « Votre mot de passe a été modifié. Vous pouvez vous connecter. ».
5. La page ne transmet pas son adresse complète aux sites externes (en-tête `Referrer-Policy`), pour ne pas divulguer le jeton.

## E6 — Espace membre

1. Un administrateur voit en plus un lien « Accéder au back-office ».
2. « Retirer des favoris » s'applique sans confirmation (action facile à annuler).
3. « Supprimer » une comparaison demande une confirmation, dans une fenêtre identique à E6b sans mot de passe (US-13).
4. Listes vides : « Aucun favori pour l'instant. » et « Aucune comparaison enregistrée. »
5. « 1 produit retiré » : produit archivé depuis l'enregistrement de la comparaison (RG-11).

## E6b — Confirmation de suppression du compte

1. Fenêtre modale affichée par-dessus E6, page assombrie.
2. Élément `<dialog>` natif : focus sur le champ « Mot de passe » à l'ouverture ; Échap équivaut à « Annuler » ; le focus ne peut pas sortir de la fenêtre ; il revient sur « Supprimer mon compte » à la fermeture.
3. « Annuler » est volontairement mis en avant : l'action est irréversible.
4. Après suppression : déconnexion, redirection vers l'accueil et message « Votre compte a été supprimé. » (US-14).

## E6c — Mes informations

1. Toute modification exige le mot de passe actuel (RG-21).
2. Après un changement de mot de passe, les autres sessions sont fermées et la session en cours reçoit un nouvel identifiant (US-24).
3. Un seul message de confirmation s'affiche à la fois ; les deux sont dessinés pour montrer leur emplacement.
4. Les tentatives répétées sont limitées.

## E7 — Back-office : produits

1. Extrait : la page affiche 20 produits ; 43 produits, soit 3 pages.
2. Gabarit commun à toutes les listes du back-office (marques et gammes, référentiels, enseignes, relevés de prix, imports).
3. Les actions dépendent de l'état du produit ; « Publier » n'apparaît que si les conditions de la RG-10 sont remplies.
4. La suppression est refusée pour un produit utilisé par des membres : il faut l'archiver.
5. La section active de la barre latérale est signalée comme page courante.

## E8 — Back-office : formulaire produit

1. « Publier » n'apparaît que si les conditions de la RG-10 sont remplies.
2. L'encadré « Conditions de publication manquantes » liste ce qui empêche la publication (US-21).
3. L'astérisque signale les champs obligatoires pour enregistrer ; un brouillon peut être incomplet (RG-19).
4. La liste des gammes ne propose que celles de la marque choisie.
5. Le slug est proposé à partir du nom, et reste modifiable.
6. Le formulaire envoie la version du produit dans un champ invisible, pour détecter les modifications concurrentes (RG-18).
7. L'enregistrement est entièrement réussi ou entièrement annulé, grâce à une transaction (US-17).
8. Le prix au kilo n'est pas saisi : il est calculé par l'API (RG-05).
9. Exemple : constituants et additifs relevés sur royalcanin.com le 17/10/2026 ; relevé de prix zooplus.fr, avec une date fabriquée pour illustrer un prix à actualiser.

## E9 — Back-office : import par code-barres

1. Le code-barres est contrôlé avant tout appel externe : format, clé de contrôle, absence de doublon.
2. Erreurs possibles : « Code-barres invalide », « Ce code-barres est déjà utilisé par le format d'un produit », « Code-barres inconnu sur Open Pet Food Facts », « Ce produit n'est pas un aliment pour animaux », « Service indisponible, réessayez plus tard ».
3. La réponse brute de l'API est conservée dans MongoDB, avec le statut « en attente ».
4. La marque est rapprochée d'une marque existante, jamais créée automatiquement.
5. « Créer le produit à partir de ces données » ouvre E8 prérempli, en brouillon non vérifié.
6. « Rejeter cet import » marque l'import comme rejeté.
7. Exemple : réponse réelle de l'API, appel d'octobre 2026 (code-barres 3182550846127).
