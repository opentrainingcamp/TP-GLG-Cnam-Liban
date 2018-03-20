# Cas d'utilisations

![Cas Utilsation](images/UC_Gestion_de_clients.png)

----

# Nom : Créer client
## Résumé
> Permet à Bob de saisir les coordonnées des clients.
## Acteurs
> Bob.
## Pré-conditions 
> Le client ne doit pas exister dans le système.
## Description	
> 1$Shop saisir les coordonnées de ses clients. Elle désire avoir les données figurant sur ses fiches actuelle. Les coordonnées des clients sont les suivantes :
> * **Customer Id** : identifiant unique du client ((1)). Cet identifiant est construit manuellement par Bill à partir du nom de famille suivi d'un numéro. (1)
> * **First Name** : prénom 
> * **Last Name** : nom de famille
> * **Telephone** : numéro de téléphone où l'on peut joindre le client 
> * **Street 1 et Street 2** : ces deux zones permettent de saisir l'adresse du client.
> * **City** : ville de résidence
> * **State** : état de résidence ou région de résidence
> * **Zipcode** : code postal
> * **Country** : pays de résidence

Uniquement les champs Customer Id, First Name et Last Name sont obligatoires ((2))
## Exceptions 
((GLOBAL)) : Si une erreur système se produit, une exception doit être levée.
> 1. Si l'identifiant saisi existe déjà dans le système, une exception doit être levée.
> 2. Si l'un des champs est manquant, une exception doit être levée.
## Post-conditions
Un client est créé.

----
----

# Supprimer un client.

## Résumé	
    Permet à Bob de supprimer un client du système.

## Acteurs	
    Bob.

## Pré-conditions	
    Le client doit exister dans le système ((1)).

## Description	
    A partir d'un numéro de client (Customer Id) le système affiche ses coordonnées et propose à Bob de le supprimer. Si Bill accepte alors le client est supprimé du système.

## Exceptions	
    1. Si l'identifiant n'existe pas dans le système, une exception doit être levée.

    ((GLOBAL)) Si une erreur système se produit, une exception doit être levée.
## Post-conditions	
    Le client est supprimé.

# Mettre à jour les informations d'un client.

## Résumé	
    Permet à Bill de modifier les coordonnées d'un client.

## Acteurs	
    Bill.
## Pré-conditions	
    Le client doit exister dans le système ((1)).

## Description	
    A partir d'un numéro de client (Customer Id) le système affiche ses coordonnées et propose à Bill de les modifier. Toutes les données sont modifiables sauf l'identifiant. Lors d'une mise à jour, le prénom (First Name) et le nom (Last Name) doivent rester obligatoires ((2)).

## Exceptions	
    1. Si l'identifiant n'existe pas dans le système, une exception doit être levée.
    2. Si l'un des champs est manquant, une exception doit être levée.

    ((GLOBAL)) Si une erreur système se produit, une exception doit être levée.
## Post-conditions	
    Les coordonnées du client sont mises à jour.

-----
-----

# Rechercher un client par son identifiant.

## Résumé	
    Permet à Bill de rechercher les coordonnées d'un client.

## Acteurs	
    Bill.
## Pré-conditions	
    Le client doit exister dans le système ((1)).
## Description	
    A partir d'un numéro de client (Customer Id) le système affiche ses coordonnées.
## Exceptions	
    1. Si l'identifiant n'existe pas dans le système, une exception doit être levée.

    ((GLOBAL)) Si une erreur système se produit, une exception doit être levée.
## Post-conditions
Les coordonnées du client affichées.
