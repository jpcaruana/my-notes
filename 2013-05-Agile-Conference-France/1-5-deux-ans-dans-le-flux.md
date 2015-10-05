<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Deux ans dans le flux](#deux-ans-dans-le-flux)
- [Retour d'expérience](#retour-dexp%C3%A9rience)
  - [](#)
  - [----](#----)
  - [Texte de présentation](#texte-de-pr%C3%A9sentation)
    - [Compléments](#compl%C3%A9ments)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Deux ans dans le flux
    Olivier Azeau @oaz
    agilitateur.azeau.com
    références : méthode de Monte Carlo

# Retour d'expérience
Équipe = 4 dev + 1 chef d'équipe + 1 support + 1 chef de produit (qui fait office de PO)

Commencé Scrumm en 2007. Sprints de 3 semaines.

En 2012 : arrivée d'une nouvelle ligne de produits et d'une nouvelle techno. Une "tendance à trop être sur l'achèvement à une date donnée quitte à couper les coins" se dégageait et avait un impact négatif sur la qualité à long terme.

Mise en place (découverte itérative) d'un scrum-ban (sans le dire):
* livraisons toutes les 3 semaines -> en continu (en interne). Plus de couperêt de la release en fin de sprint : l'équipe est plus sereine
* kanban
* branche unique de développement avec des features en cours de développement non activées. cela a conduit à une *conception modulaire* et à un code *testable*
* abandon de la vélocité, mais mesure du lead time et de la probabilité de terminer une story dans la journée, dans la semaine, dans le mois. (calcul statistique à partir des lead times observés avec la méthode de Monte Carlo)
* les démos et les rétros en mode "juste à temps", pas en fin de sprintt. La rétro peut avoir lieu pendant le daily meeting si le besoin s'en fait sentir. (voir la notion de handon dans le lean)
* spécification éxécutables
* client explorateur : ne fournit pas de spécifications très détaillées, mais itère sur les réalisations (livrées, démontrées) pour changer le produit
* (processus) de conception documenté par l'inclusion d'une vérification du processus dans le build (en rendant toutes les règles de processus éxécutables) et génération automatique de la documentation -- *je n'ai pas compris cette partie*

----
----
## Texte de présentation
http://www.conference-agile.fr/sessions/deux-ans-dans-le-flux.html

C'est l'histoire de développeurs qui viennent de passer deux ans dans le flux... (c'est aussi celle d'un Scrum qui a mal tourné)

Vous aimez les voyages ? Laissez-vous emporter par celui d'une petite équipe de développeurs qui est entrée dans l'agilité il y a sept ans avec Scrum et qui a fait évoluer pas à pas sa façon de fonctionner.

Pas de grandes leçons au bout du chemin mais une découverte essentielle : la méthode agile qui convient à une équipe, c’est celle qui se construit, jour après jour, choix après choix.

La session porte principalement sur les deux dernières années et une sélection de pratiques fortement liées à un fonctionnement en flux :
* les livraisons en continu qui ont remplacé les itérations
* la branche unique dans la gestion du code source
* le planning basé sur des calculs de probabilités
* la totalité des activités organisées en "juste à temps"
* les spécifications exécutables
* le client dans un rôle d'explorateur

### Compléments

La session a été présentée à l'automne 2012 à Agile Tour Toulouse et Agile Tour Montpellier. A ces occasions, les retours ont montré qu'une une réelle pratique de l'agilité permet de mieux apprécier le contenu de la session car on n'y parle pas d'une transition vers l'agilité mais d'une possibilité (parmi d'autres) d'un "après Scrum".
