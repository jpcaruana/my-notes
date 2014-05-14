#Votre première semaine avec AWS : Amazon EC2
    Sébastien Stormacq, AWS Senior Technical Trainer

## EC2
EC2 = Elastic Compute Cloud

permet le choix (non définitif) de l'OS, de la taille de l'instance. Le coût est à l'heure par instance.

déployer près des clients :
* 10 régions (dont 8 sont dispos pour tous)
* 26 zones de disponibilité (redondance des datacenters)
* 51 sites AWS Edge (partie CDN)

Plus de 30 types d'instances différents:
* généralistes: M3
* CPU : C3 (jusqu'à 32 vCPU Xeon 2,8 GHz)
* Mémoire : R3 (jusqu'à 244 Go de RAM et 32 vCPU)
* Stockage/IO : I2 (jusqu'à 8x800 Go SSD = 6,4 To) et HS1
* GPU : G2

Quelques exemples :
* DowJones économise 40 000 $/an en frais d'infrastruture.
* Expedia a réduit ses temps de latence en dessous des 50ms (au lieu de 250) et a augmenté l'efficacité de ses CPU de 230%

## Pourquoi EC2 ?
* élasticité : s'adapte à votre usage (variation journalières, mensuelles). pas besoin de sur-provisionner
* contrôle : root sur les instances, templates de machines (AMI)
* flexibilité
* fiabilité :
    * plein de briques de base à assembler
    * ELB (Elastic Load Balancer)
    * Auto Scaling (dans les 2 sens),
    * 99,95% de SLA par datacenter
* sécurité
* rentabilité
    * le capex devient de l'opex
    * économies d'échelle
    * tarifs négociables


## Texte d'origine
Cette session est recommandée pour toute personne qui débute sur Amazon EC2, ou qui cherche à connaitre les dernières innovations du service.

Amazon Elastic Compute Cloud (Amazon EC2) fournit de la capacité de calcul redimensionnable dans le cloud et est conçu pour faciliter l'accès aux ressources informatiques à l'échelle du Web pour les clients. Amazon EC2 propose une grande variété d’instances de calcul adaptées à tous types d’usage, du site internet statique au calcul de haute performance à la demande, disponible via des options de tarification flexibles. Amazon EC2 fonctionne avec Amazon Elastic Block Store (Amazon EBS) et l’Auto Scaling pour permettre d’obtenir facilement les performances et la disponibilité dont vous avez besoin pour vos applications. Cette session introduira les fonctionnalités clés et les différents types d’instances offerts par Amazon EC2, montrera comment vous pouvez débuter et vous permettra de bénéficier de conseils pour choisir les bonnes instances et les options d’achat.
