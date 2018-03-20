# Expression des besoins 0 (1$ shop Customer)

La société Libanaise "1$ shop" vend de tout et n'importe quoi. Elle est implantée depuis plusieurs année au Liban, où ses principaux clients sont domiciliés. Récemment elle a eyu l'idée de passer en ligne et de créer un magazin en ligne Elle continue à exercer sa profession telle qu'elle le faisait à ses débuts, c'est-à-dire qu'elle répertorie ses clients sur des fiches de papier bristol, indexées par le nom de famille, reçoit les commandes par téléphone, fax et les payement par OMT (Transfert de cash). Une fois le montant encaissé, "1$ shop" envoie les produits via son réseau de livreures. Régulièrement "1$ shop" envoie son catalogue à ses clients. Elle trouve ses nouveaux clients au travers de publicités qu'elle envoie aussi par courrier ou démarchage direct (brochure distribué sur les routes libanaise…).
"1$ shop" veut informatiser la gestion de ses clients car ils sont de plus en plus nombreux. Elle voudrait saisir leurs coordonnées et pouvoir les modifier. Cette informatisation lui permettrait surtout de pouvoir retrouver les informations de ses clients plus rapidement. "1$ shop" possède des PC un peu obsolètes avec Windows comme système d'exploitation. Il faut donc que l'application ne consomme pas trop de ressources systèmes.
Cette tâche de gestion des clients sera menée par "l'utilisateur final Bob" qui assure la relation clientèle. L'application devra être uniquement déployée sur le serveur d'impression. La particularité de ce serveur est qu'il est constamment allumé et n'est jamais éteint. "1$ shop" ne possédant pas de base de données, les données peuvent être stockées en mémoire ou dans de simple fichiers. L'application devra être simple d'utilisation et l'interface utilisateur, ainsi que la documentation et le code, devront être rédigés en français. Ce système de gestion clientèle se nomme "1$ shop" Customer.

Nous souhaitons donc définit les cas d'utilisations de 1$C (1$ shop Customer) en travaillant avec Bob.

Après notre premier entretien informel avec Bob il nous fournit sa vision de l'interface texte de l'application comme il le souhaiterait.

```
 (0) Quit
 ----------
 (1) Créer un client
 (2) Trouver Client
 (3) Supprimer Client
 (4) Mettre a jour client
```

(1)On pourra ainsi accéder à l'action « créer d'un client » en tapant le chiffre 1. S'affiche ensuite un menu aidant l'utilisateur à saisir les bonnes données. La ligne Usage permet à Bob de connaître l'ordre des données à saisir et la ligne 'Exemple' lui fournit un exemple.

Voici une manière de faire un menu textuel en java [Menu text](Menu)

--- Créer client ---
> Usage : Id- prénom - nom - tel - adresse

> Exemple : bob001 - Bob - Ducnam - 03240246 - Beyrouth ...

Bob n'aura plus qu'à saisir les coordonnées d'un client en séparant chaque donnée par le caractère '-'. Le système alertera l'utilisateur du bon ou mauvais fonctionnement d'une action. Le système, dans sa version initiale, ne vérifiera pas la cohérence des données saisies telle que la validité du numéro de téléphone, des états ou des pays.
(2) Pour consulter les informations d'un client, Bob saisi un identifiant et le système affiche les données.

## A faire (ici une proposition)
### A - Trouvons et décrivons les cas d'utilisations

[Une première proposition](CasUtilisation) 

### B- Analyse conception
Nous utiliserons le patron de conception objet d'accès aux données (en anglais data access object ou DAO)  https://fr.wikipedia.org/wiki/Objet_d%27acc%C3%A8s_aux_donn%C3%A9es

#### B1 - Modèle statique

Les cas d'utilisation proposés nous donnent plusieurs informations sur la gestion des clients, ce qui nous permet d'extraire le diagramme de classes ci-dessous.

![Diagramme de classe](images/CD_Customer.png)

La classe Customer est un POJO qui modélise un client; tous ses attributs (identifiant, nom, prénom, adresse, ...) sont de type String. Elle ne possède qu'une méthode (checkData) qui permet de vérifier la validité de ses informations.

La classe CustomerDAO permet de stocker les clients (insert), de les modifier (update), de les supprimer (remove) ou de les rechercher (find) dans un container. Pour cela, elle utilise une hashMap dont les éléments associent l'identifiant d'un client (id) à l'instance de Customer correspondante.

Cette classe CustomerDAO 'implémentes' le design pattern 'Data Access Object', dispensant l'objet métier Customer d'avoir à connaître la couche d'accès aux données, le rendant ainsi plus réutilisable.
La convention de nommage des attributs utilisée s'inspire du C++. Les attributs d'une classe commencent tous par un underscore '_'. Cela permet de différencier rapidement une variable ou un paramètre d'un attribut. L'autre avantage est que l'on réduit le nombre de bug d'inattention des méthodes set et que l'on n'a pas à préfixer l'attribut par this:

##### La classe client (pattern builder)

Voir [Client (pattern builder)](Client)

#### B2 - Modèle dynamique

Repéter toujours { Afficher menu -> lire choix -> faire traitement }

Ou 

Acteur <Generateur d'evènement> : Repéter toujours { Afficher menu -> lire choix -> créer évènement -> diffuser evènement }

Acteurs<Consomateur dévènemt> : pour chaque ev*i* -> action*i* (traitement)

### Développer le logiciel et ses tests (dans netbeans et maven)

# Informations utile : voir [Source](http://aisl.cnam.fr/xwiki/wiki/aisl/view/GLG203/TP01)


# COMPLEMENT : Gestion des erreurs

Voir [Gestion erreurs](GestionErreurs)