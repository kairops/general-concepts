# Environment d'exécution

## Definition

Ensemble complet d'éléments que permettant l'exécution d'une application.

En tant qu'element nous pouvons localiser un service, comme le service Web fourni par Apache ou Nginx, un moteur de base de données  mysql, un certificat HTTPS, un nom de domaine, où sont stockés les fichiers téléchargés par l'utilisateur. .. cela pourrait pratiquement être tout ce qui aide notre application à fonctionner.

## Catégories 

Nous pouvons avoir plusieurs environnements d'exécution, chacun destiné à un objectif différent. En ce qui concerne les éléments d'un environnement, ils doivent être équivalents. La puissance d'un environnement local est différente de celle d'un environnement de production, même si les services proposés et déployés doivent être du même type (pas nécessairement dans le même nombre).

Exemple: repartiteur de charge et service WEB. L'environnement de développement aura un repartiteur et deux éléments fournissant un service WEB (par exemple, deux Nginx), et dans l'environnement de production, nous aurons un "repartiteur en tant que service" (ELB ou F5) et un service WEB formé par plusieurs instances NGINX.


Quelques catégories d'environnements typiques:

- **Environnement local**. Destiné à fonctionner sur le PC d'un développeur.
- **Environnement d'intégration**. Partagé par tous les membres de l'équipe, destiné aux tests d'intégration.
- **Environnement de validation / qualité / test**. Celui dans lequel nous exécutons le test d'acceptation (BDD), le chargement, la sécurité, etc.
- **Environnement de préproduction**. Le plus proche de l'environnement de production, en termes de diversité et de nombre d'éléments des services. 
- **Environnement de production**. Il n'est pas nécessaire d'ajouter beaucoup plus: allez vivre!


## Et les microservices

... et les architectures hexagonales, les kubernetes, les environnements éphémères provisionnés par la branche technique. En attente de quelque chosse d'intéressant à dire :) 
