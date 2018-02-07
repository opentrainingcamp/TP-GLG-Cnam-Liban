# Pour démarrer

A- Télécharger puis installer

Optimum : Ubuntu ou iOS, Java JDK >8, Netbeans, Maven (avant de venir en cours avec vos portable ... )

Ou

pour ceux qui sont sous windows : Installer github for windows viens avec un Linux bash puis Java JDK >8, Netbeans, Maven (les version windows)

B- utilisation git et github

Ce premier TP vous permet de prendre en main le système basé sur git et github pour la procedure de soumission de vos futurs TP. On vous demande d'écrire la classe Client.java  et les tests unitaires.


La classe Client représente un client; elle possède les attributs suivants, tous de type String : 
```
    private String _id;
    private String _prenom;
    private String _nom;
    private String _telephone;
    private String _rue;
    private String _ville;
    private String _etat;
    private String _code;
    private String _pays;
    private String _mail;
```

nous utilisons et créons aussi, 
 1. Le pattern Builder pour la création d'un nouveaux client
 2. dans cette première version, des méthodes statiques (find, insert, remove) gérant (par exemple dans une HashMap associant l'id d'un Client et son instance) l'ensemble de ses instances .