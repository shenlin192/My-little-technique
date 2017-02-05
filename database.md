
## 1,2,3NF, BCNF
 
1. 1NF的定义为：符合1NF的关系中的每个属性都不可再分
2. 2NF在1NF的基础之上，消除了`非主属性`对于`码`的`部分函数依赖`
3. 3NF在2NF的基础之上，消除了`非主属性`对于`码`的`传递函数依赖`
4. BCNF在3NF的基础上消除`主属性`对于`码`的`部分与传递函数依赖`

[link](https://www.zhihu.com/question/24696366)

5. [第四范式的定义很简单：已经是BC范式，并且不包含多值依赖关系](http://www.cnblogs.com/studyzy/p/5823224.html)

## SQL vs NoSQL

[dataType, Schema, Normalization, Join, transaction, Integrite, volume  ...]
https://www.sitepoint.com/sql-vs-nosql-differences/
http://blog.bigstep.com/sql-versus-nosql-differences-choose/
https://www.quora.com/What-is-the-difference-between-SQL-and-NoSQL-databases

- SQL databases are structured into tables, while NoSQL databases are based on documents, graphs, wide-column stores, or key-value pairs.

- In SQL, databases are structured on predefined schema based on structured data, while in NoSQL, schema is dynamic in order to manage unstructured data. 

- SQL 1,2,3,4,5NF BCNF; NoSQL no normalisation

- SQL queries offer a powerful JOIN clause. We can obtain related data in multiple tables using a single SQL statement. 
NoSQL has no equivalent of JOIN

- Most SQL databases allow you to enforce data integrity rules using foreign key constraints. The schema enforces these rules for the database to follow. It’s impossible for developers or users to add, edit or remove records, which could result in invalid data or orphan records.

The same data integrity options are not available in NoSQL databases; you can store what you want regardless of any other documents. Ideally, a single document will be the sole source of all information about an item.

NoSQL databases sacrifice ACID compliancy for flexibility and processing speed.

- In SQL databases, two or more updates can be executed in a transaction — an all-or-nothing wrapper that guarantees success or failure. Placing the same updates within a transaction ensures either both succeed or both fail.

In a NoSQL database, modification of a single document is atomic. In other words, if you’re updating three values within a document, either all three are updated successfully or it remains unchanged. However, there’s no transaction equivalent for updates to multiple documents. 

-  
NoSQL Storing large volumes of data that often have little to no structure. Making the most of cloud computing and storage.

## Volume
1. Neo4j: Il manque la capacité pour traiter un grande volume de données.
2. Cassandra: a été développé dans le but de gérer des quantités importantes de
données réparties sur plusieurs serveurs
3. MySQL: manquerait de robustesse avec de fortes volumétries.
4. MongoDB: permet le stockage de volume important de données
5. Redis: La taille des bases de données est assez limitée et les données doivent être
distribuées sur plusieurs serveurs si elles sont importantes
6. BaseX: Il se spécialise dans la gestion de documents XML de grande taille

## Transactions et Cohérence des Données
1. MongoDB permet de faire des requêtes transactionnelles sur un document. Par
défaut ces requêtes suivent ACI (Atomicité, Cohérence et Isolation). la Durabilité peut
être activée mais est désactivée par défaut.
Cependant, mongoDB ne permet pas de faire des requêtes transactionnelles sur
plusieurs documents.
2. Pour ses transactions, Neo4j sécurise les données avec les propriétés ACID.
3. Cassandra n'utilise pas de transactions ACID permettant le retour en arrière ou
de verrous de lecture ou d'écriture. Cependant on a tout même des transactions
atomiques, isolées et durables. La consistance quant à elle peut être modifiée pour
chaque transaction par l'utilisateur.
4. Afin que les données soient cohérentes dans la base, il est possible de les faire
vérifier automatiquement lors de leur saisie dans la base notamment avec un système
de contraintes. Cependant MySQL ne supporte pas par défaut cette fonctionnalité et
nécessite que cette étape soit réalisée par l’application utilisant MySQL.
5. Redis possède des transactions et des notions de cohérence des données. De
base, toutes les requêtes de base sont atomiques et par conséquent l’état du système
est par construction toujours cohérent de façon interne.
6. BaseX présente une architecture client-serveur qui offre les propriétés de ACID
avec plusieurs lectures et écritures.

## Schema
1. Les données avec MongoDB ont un schéma flexible, c’est-à-dire que la structure de ce qui
est stocké peut varier à tous moment sans changement à effectuer sur la base.

2. Cassandra est une base de données de type clé-valeur qui utilise un modèle de données
dynamique afin d’obtenir une flexibilité accrue et une bonne performance. 

3. Redis est un moteur non-relationnel de stockage de données opérant principalement en
mémoire cache. Il manipule exclusivement des paires clés valeurs sous 5 types différents :
les chaînes, les listes, les ensembles, les ensembles triés, et les tables de hachage.

4. MySQL est une base de données de type clé-valeur distribuée. Les
structures de données ne sont pas contraintes par un schéma.

5. Neo4j est un SGBD basé sur les graphes, permettant de représenter les données via des
nœuds reliés entre eux par un ensemble de relations. 

6. De nombreux formats de fichiers sont aussi pris en compte
par BaseX tel que JSON, HTML, CSV ou encore Text.

## application
1. Neo4j 
systèmes de recommandation
● analyse réseau
● réseaux sociaux
● biologies (interactions entre les molécules, etc.)
● logistique (calcul du meilleur itinéraire)

2. Redis
1) Des web applications qui ont besoins de faire le I/O rapide
2) Les platforms qui ont besoins de calculer les données en temps réel
3) L’opération qui ont besoin de lire des données fréquent et assez grand, comme la
visualisation de données
4) Les applications qui lie des données référencé aux clé, comme les applications
sociales.

3. Cassandra
Ce système est adapté aux traitements de volumes importants de données
éventuellement dynamiques, aux applications en lignes exigeant rapidité de réponse et
haute disponibilité comme nous avons pu le citer avec Netflix ou GitHub.

4. MySQL est très utilisé pour réaliser des sites web en l’associant à PHP. 

5. De part sa structure, BaseX est très orienté vers le stockage, le requêtage mais
aussi la visualisation de vastes collections de documents XML.

6. MongoDB 
La base possède la spécificité d'avoir été conçue par une entreprise de cloud computing,
pour être répartie sur un nombre quelconque d'ordinateurs, permettant ainsi de gérer très
facilement la montée en charge, d'appliquer des opérations Map-Reduce, et d'assurer les
données avec un système de réplication natif. Il est pour cela très facile de déployer des
bases de données dans le cloud ; de nombreux services existent en ce sens (mLab,
scalegrid, MongoDB Atlas, …).

En effet, dans le domaine des serveurs web, la raison souvent énoncée pour justifier un
environnement NodeJS et MongoDB est que cela permet d'utiliser un seul et unique
langage, à la fois pour le développement client, serveur, et la base de données.
Cette pratique s'illustre par exemple par le populaire stack MEAN (fondée sur l'utilisation des
technologies MongoDB, Express.js, AngularJS, NodeJS), et ses variantes. Ce stack est
particulièrement utilisé par les startups, ne comportant que des technologies gratuites,
rapides à déployer (utilisation de services dans le cloud) et permettant de facilement faire
évoluer des prototypes
