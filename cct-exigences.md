# Référentiel d'exigences applicables au CCT Cloud Pi Native

> **Brouillon de révision du 22/10/2026**, issu de l'application de `TODO.txt` à la version bêta du 27/05/2024.
> Les passages marqués ⚠️ sont à arbitrer : voir `cct-exigences-notes-de-revision.md`.
> La numérotation est provisoire (les doublons d'ID de la bêta sont signalés « bis ») ; elle sera refaite une fois le contenu stabilisé.

**Note** : le terme « équipe projet » désigne l'individu ou l'organisation pluridisciplinaire chargée de produire et maintenir la base de code, le corpus de tests, les fichiers de description d'infrastructure ainsi que la documentation technique et usager. Elle est responsable de l'adéquation et de la qualité de la solution au besoin des usagers, en collaborant de manière étendue avec les autres acteurs impliqués.

**Principe directeur** : CPiN met à disposition l'outillage et remonte des indicateurs (qualité, vulnérabilités, supervision). Il revient à l'équipe projet de les évaluer, de les prendre en compte (corriger) ou d'accepter le risque de façon tracée.

**Niveaux d'exigence**
- **P** : primordiale, le non-respect entraîne un rejet administratif de l'offre lors d'un appel d'offres et un plan de remédiation obligatoire lors de l'exécution du marché.
- **I** : importante, permet de maximiser la qualité de la solution.

---

## Généralités

**EXI-G-1** · I · *Hiérarchie des normes*
Dans le cadre d'un appel d'offres, en cas d'incohérence entre les documents et hors mentions explicites, le CCT et la liste des exigences associées sont de niveau supérieur.

**EXI-G-2** · I · *Applicabilité*
Le respect des exigences du CCT est limité à la durée du marché pour un opérateur économique, mais permanent pour la direction d'application métier.

**EXI-G-3** · I · *Cadre de normes*
Respect des standards et des normes applicables (industrielles, européennes et étatiques) pour la conception de solutions numériques hébergées dans le cloud native (Kubernetes) : Design Système de l'État, RGAA, RGS, RGI, doctrine Cloud au centre. Cf. le paragraphe du volet de CCT « Les normes industrielles, institutionnelles applicables ».

**EXI-G-4** · I · *Qualité de la solution*
Respect du guide d'éco-conception : conception frugale vis-à-vis des ressources d'infrastructure consommées et de l'impact sur le terminal de l'usager.

**EXI-G-5** · P · *Infrastructure*
Choix d'un hébergement adapté à la nature des données manipulées (usuel / DR) et au cadre légal applicable : Cloud Pi (on-prem), cloud public, infrastructure dédiée ou mixte.

**EXI-G-6** · P · *Infrastructure* ⚠️ à arbitrer (maintien, avis du conseil, ou suppression)
Si l'application est exposée sur internet, un service de CDN / anti-DDoS externalisé est mis en place.

---

## Organisation et modèle d'opération

**EXI-ORG-1** · P · *Modèle d'opération* ⚠️ reformulé
Conformité au modèle de responsabilité Cloud Pi Native : l'équipe projet est responsable de la qualité de sa solution et de la prise en compte des vulnérabilités. CPiN remonte des indicateurs ; l'équipe projet les évalue, puis corrige ou accepte le risque de manière tracée.

**EXI-ORG-2** · I · *Modèle d'opération*
Les équipes contribuent à la remontée et à l'enrichissement de l'offre Cloud Native : elles signalent les défauts éventuels ou les besoins d'évolution et soumettent, le cas échéant, une rectification ou une évolution sur le dépôt de code après l'avoir testée.

**EXI-ORG-3** · P · *Modèle d'opération* ⚠️ à rapprocher des cas BnB et Camping
Conformité au modèle de responsabilité « you build it – you run it – you secure it – you support it » de l'offre Cloud Pi Native.
L'équipe projet est responsable d'organiser le bon fonctionnement de l'application en production et le soutien aux usagers.
Un modèle de collaboration, précisant les responsabilités de chaque acteur, est établi dans la convention d'utilisation de l'offre avec l'hébergeur. Cela peut inclure d'autres conventions avec d'autres services (supervision applicative, SOC ministériel). Les normes d'interface sont à demander lors de la contractualisation de l'hébergement.

**EXI-ORG-17** · I · *Compétence*
L'équipe est formée aux bonnes pratiques des technologies Cloud Native (Kubernetes), à la construction et au maintien en qualité d'une base de code, à l'agilité, au DevSecOps et à l'intégration continue (fournir les certifications en preuve).

**EXI-ORG-16** · I · *Compétence*
L'équipe s'appuie de préférence sur un ou plusieurs coachs et experts certifiés Cloud Pi Native pour l'initialisation du programme et une revue régulière des pratiques.

**EXI-ORG-6** · I · *Modèle d'opération* ⚠️ reformulé
La chaîne primaire (dépôts de code applicatif et de code d'infrastructure, outillage du projet) est la source de vérité de l'équipe projet. L'équipe projet est responsable de son intégration technique à la chaîne DevSecOps de CPiN et de son maintien en condition de disponibilité et de sécurité. La chaîne secondaire reconstruit et déploie à partir de cette source.

**EXI-ORG-7** · P · *Modèle d'opération*
L'équipe projet est responsable du pipeline de la chaîne secondaire de construction applicative (pipeline GitLab). Elle s'appuie sur les outils et les exemples proposés par la documentation et met en œuvre les vérifications nécessaires : qualité du code, vérifications fonctionnelles automatiques, mesures de sécurité spécifiques issues de la démarche d'homologation.

**EXI-ORG-8** · P · *Modèle d'opération*
Seul le mode de déploiement GitOps est mis en œuvre. L'équipe projet versionne son code applicatif et son code d'infrastructure. Les déploiements par manifest « à la main » ne sont pas autorisés.

**EXI-ORG-9** · I · *Modèle d'opération* ⚠️ à valider (Brice)
L'équipe projet met en place un principe de livraison continue, par lots de taille réduite.

**EXI-ORG-10** · I · *Code applicatif & image* ⚠️ à valider (Brice)
Couverture et capitalisation des tests, respect des métiers (non-régression) : la couverture des tests unitaires du back-end visée est de 100 % du code. La mise en place d'une approche test-driven development est fortement recommandée.

**EXI-ORG-11** · I · *Qualité de la solution* ⚠️ reformulé
L'équipe projet est responsable de la qualité de son code et de la non-régression. La couverture fonctionnelle des tests du front end permet de s'assurer de l'absence de régression majeure en vérifiant les séquences d'usage principales (login, actes métiers fréquents, etc.).

**EXI-ORG-12** · I · *Qualité de la solution* ⚠️ reformulé
Un bug détecté donne lieu à l'écriture d'un test automatique avant celle du correctif, afin d'enrichir la base de cas de tests et de renforcer les tests de non-régression.

**EXI-ORG-13** · P · *Modèle d'opération* ⚠️ reformulé
L'équipe projet est responsable de la prise en compte des vulnérabilités de son application, y compris celles découvertes après le dernier déploiement stable. CPiN remonte les indicateurs (scans de vulnérabilités, qualité du code) ; l'équipe projet les évalue, puis corrige ou accepte le risque, selon les modalités du dossier d'homologation et son plan d'actions.
La chaîne de construction applicative peut bloquer un déploiement lorsque des vulnérabilités critiques sont détectées ou que la qualité d'ensemble du code décroît.
Une application présentant des vulnérabilités critiques ni corrigées ni faisant l'objet d'une acceptation de risque, malgré les injonctions de correction, est susceptible d'être suspendue jusqu'à remédiation, pour garantir l'intégrité et la protection de ses données.
Pour améliorer le « signal sur bruit » des CVE, se référer à l'exigence sur le choix des images de base (EXI-ARCH-6).

**EXI-ORG-14** · P · *Qualité de la solution* ⚠️ reformulé
L'équipe projet met en œuvre une activité continue de refactoring et maîtrise la qualité de son code (revue par les pairs, processus de maîtrise des changements, par exemple lors des pull requests). La qualité mesurée ne peut pas être décroissante dans le temps.
L'équipe fournit les preuves que des tests de sécurité, de qualité et de robustesse ont été mis en œuvre et qu'ils n'ont pas remonté de vulnérabilité ou d'erreur majeure. Ces preuves sont annexées au dossier d'homologation et les actions sont suivies dans le plan d'actions.
*(La réserve de capacité d'environ 20 % pour le refactoring de la bêta est retirée du texte : à confirmer, voir notes.)*

**EXI-ORG-15** · I · *Modèle d'opération* ⚠️ nouvelle règle (remplace ORG-15 et ORG-16 bis de la bêta)
Alerting : CPiN met en place l'outillage d'alerting et de remontée « shift-left » (notifications de pipeline, supervision). L'équipe projet l'implémente dans son contexte : règles d'alerte, destinataires, canaux (intégrations possibles avec Mattermost et Tchap, ou WebHook pour s'intégrer aux flux de travail). *[À vérifier : outillage actuellement proposé par CPiN ; la bêta citait « kibaba » (sic).]*

**EXI-ORG-17 bis** · P · *Modèle d'opération*
L'orchestration de la sauvegarde est de la responsabilité de l'équipe projet.

**EXI-ORG-18** · I · *Modèle d'opération*
L'équipe projet teste régulièrement sa capacité à restaurer l'ensemble de l'architecture et des données de l'application, avec un scénario de test connu à l'avance.

---

## Architecture

*Supprimées par rapport à la bêta : EXI-ARCH-1, 9, 11, 13 (fusionnée dans ARCH-10), 15, 16, 17, 20, 21.*

**EXI-ARCH-2** · P · *Architecture* ⚠️ reformulé
Résilience : l'architecture interne et l'organisation sont conçues pour atteindre la durée maximale d'interruption acceptable (DMIA) fixée par le métier, en combinant un déploiement sur 2 datacenters (résilience assurée au niveau applicatif, en actif/passif ou actif/actif selon le besoin), une architecture modulaire avec dégradation gracieuse (*graceful degradation*) et des mesures organisationnelles.
Au sein d'un datacenter, des règles d'anti-affinité sont posées dans les manifests / charts pour répartir les composants sur des AZ différentes (lorsque le cluster le permet) ; cette répartition est vérifiée à chaque déploiement.
L'équipe confirme par des exercices réguliers que ses processus et ses mesures atteignent l'objectif visé.
*Notes (offre actuelle, à vérifier) : par défaut, 2 environnements de production, 1 environnement hors production et 2 buckets S3 sont proposés à la contractualisation ; des operators tels que CloudNativePG facilitent la haute disponibilité de la persistance ; le S3 permet une disponibilité inter-datacenter ; la dégradation gracieuse permet à un module dont une dépendance est indisponible de fournir une expérience dégradée mais acceptable.*

**EXI-ARCH-3** · I · *Architecture* ⚠️ reformulé
L'architecture de la solution est modulaire, avec un couplage lâche, organisationnel et technique, entre composants via des interfaces normées et documentées (ex. API). CPiN permet de modulariser les déploiements : les composants peuvent être déployés indépendamment les uns des autres, sans coordination entre équipes.

**EXI-ARCH-4** · I · *Architecture* ⚠️ reformulé (était P)
L'utilisation du stockage objet (S3) du ministère est conseillée comme point de présence et de vérité des sauvegardes, de façon indépendante et résiliente vis-à-vis de l'architecture de production.

**EXI-ARCH-5** · P · *Code applicatif & image d'infrastructure applicative* ⚠️ reformulé
Pour les composants d'infrastructure logicielle open source (ex. nginx, Keycloak, Airflow, Quarkus), s'appuyer sur des images et des charts Helm issus de communautés actives, à cycle de MCO/MCS fréquent. Les images sont construites rootless, de préférence multi-architectures. Vérifier systématiquement la date de dernière mise à jour, les vulnérabilités connues et l'accès au code source.

**EXI-ARCH-5 bis** · I · *Déploiement* ⚠️ nouvelle règle (recoupe ARCH-22)
La configuration de l'application (valeurs et secrets) est séparée du code et de l'image et fournie à l'exécution : ConfigMap, Secret ou variables d'environnement (par exemple via le mécanisme `values.yaml` des charts Helm).

**EXI-ARCH-6** · I · *Services mutualisés* ⚠️ reformulé (était P)
Le choix de l'image de base est structurant. Plus l'image est fine, meilleur est le « signal sur bruit » de la détection de vulnérabilités propres au code du projet. Le choix reste celui du projet ; il est recommandé, dans l'ordre :
1. des images sans outillage (distroless, minideb) ;
2. des images de communautés reconnues, régulièrement mises à jour et adaptées à un usage sécurisé sous OpenShift (rootless, système de fichiers en lecture seule, securityContext).
Une version « debug » (curl, tail, vi, shell avancé) peut être maintenue en parallèle (`version` et `version-debug`).

**EXI-ARCH-6 bis** · I · *Code applicatif & image* ⚠️ nouvelle règle
La construction d'images en plusieurs étapes (*multi-stage build*) est possible et encouragée : elle ne recopie dans l'image finale que les fichiers utiles.

**EXI-ARCH-7** · P · *Architecture* ⚠️ reformulé
Les certificats racines (et intermédiaires) de la PKI interne du ministère sont intégrés aux images, afin que les services consommant des endpoints HTTPS puissent en valider les certificats. Le certificat d'un endpoint ne doit pas être intégré, car il est amené à être renouvelé.
*Conseil : si le runtime permet de monter les CA depuis un fichier ou un répertoire, les monter depuis une ConfigMap ou un Secret ; si le service utilise le CA-bundle de l'OS, exécuter `update-ca-certificates` à la construction de l'image.*

**EXI-ARCH-8** · I · *Architecture* ⚠️ reformulé
Le déploiement est réalisé en GitOps (Argo CD). Le code d'infrastructure est versionné dans Git ; chaque changement passe par un push ou une pull request. L'application est découpée en une application d'ensemble référençant des sous-applications, afin de déployer les modules indépendamment.

**EXI-ARCH-10** · P · *Services mutualisés* ⚠️ reformulé (fusion ARCH-10 + ARCH-13)
L'équipe projet utilise les services socles de l'offre Cloud Pi Native : chaîne de service, IAM, Vault et gestion des secrets, observabilité (logs et télémétrie), registry d'images. Lorsque plusieurs services sont utilisables, privilégier ceux dont l'enrôlement est automatisé.

**EXI-ARCH-12** · I · *Code applicatif & image* ⚠️ reformulé (était P)
L'application est monitorable techniquement et fonctionnellement. L'usage des probes Kubernetes (*liveness*, *readiness*, *startup*) est fortement conseillé. L'application expose une API de santé auto-descriptive `/health` (JSON + problem) et des métriques `/metrics` (Prometheus), et s'intègre dans la ou les chaînes de supervision.

**EXI-ARCH-14a** · I · *Architecture* ⚠️ découpé
L'application prend en compte dans sa conception la séparation des flux et des usages : flux usagers, flux de services, flux d'administration.

**EXI-ARCH-14b** · I · *Architecture* ⚠️ découpé
L'usage du protocole HTTPS est privilégié, avec authentification mutuelle des composants.

**EXI-ARCH-14c** · I · *Architecture* ⚠️ découpé (3ᵉ volet non précisé dans la TODO)
Pour minimiser les SPOF et la surcharge de trafic inutile des équipements de protection, l'interconnexion entre applications mutuellement connues au sein d'un même niveau de sensibilité ne requiert pas le transit des flux par une passerelle ou un composant d'API management (ex. chaîne de service).

**EXI-ARCH-18a** · P · *Code applicatif & image* ⚠️ découpé
Les images de conteneurs s'exécutent en « rootless », sur des ports réseau internes supérieurs à 1024, sans élévation de privilèges et sans se modifier elles-mêmes au lancement. L'écriture dans les pods n'est possible que sur un volume monté (par exemple un volume `emptyDir` sur `/tmp`, le système de fichiers étant en lecture seule). L'exécution du pod est bloquée si ces règles ne sont pas respectées.

**EXI-ARCH-18b** · I · *Code applicatif & image* ⚠️ découpé
L'image est minimaliste, centrée sur une fonction primaire ou atomique, et conçue pour démarrer très rapidement avec le moins de dépendances possible, dans l'intérêt de la résilience et du bon fonctionnement de l'orchestrateur.

**EXI-ARCH-18c** · I · *Code applicatif & image* ⚠️ découpé
L'image n'embarque pas de service réseau non essentiel à son fonctionnement (par exemple SSHD).

**EXI-ARCH-19** · P · *Code applicatif & image*
Les pods applicatifs stateless doivent pouvoir être redémarrés rapidement et à tout instant, sans affinité de session par l'orchestrateur. L'application est conçue pour minimiser les pertes de données et de transactions en cours en cas de bascule de nœud.

**EXI-ARCH-22** · P · *Déploiement*
La configuration de l'application n'est jamais codée en dur. Elle provient de l'environnement (principe « Config » des 12 facteurs : https://12factor.net/config). Note : l'utilisation de charts Helm avec un fichier `values.yaml` couvre l'exigence.

**EXI-ARCH-23** · I · *Architecture* ⚠️ reformulé
Les logs sont redirigés vers la sortie standard et sont suffisants pour permettre au projet d'exploiter son application. *[Format de log du C2MI à vérifier.]*

**EXI-ARCH-24** · P · *Architecture* ⚠️ reformulé
L'équipe projet est responsable de l'exploitation de son application et de ses performances. Elle met en place la mesure des performances des transactions pour contrôler la qualité de service et soutenir les investigations en cas de dysfonctionnement.

**EXI-ARCH-25** · I · *Architecture*
L'application respecte dans sa conception les 12 facteurs d'une application Cloud Native : https://12factor.net/fr

**EXI-ARCH-26** · I · *Architecture* ⚠️ réduit (recoupe ARCH-18a)
Les déploiements Kubernetes n'imposent pas d'éléments de securityContext (runAsUser, runAsGroup, fsGroup, capabilities ajoutées, etc.). Il n'est pas autorisé de monter des ressources depuis le nœud (hostPath, par exemple).

**EXI-ARCH-27a** · P · *Architecture* ⚠️ séparé
Si le paramètre `imagePullPolicy` est spécifié, il est positionné à `IfNotPresent`, ce qui permet de découpler le cluster de la registry.

**EXI-ARCH-27b** · P · *Architecture* ⚠️ séparé
Le tag des images est une valeur explicite de version. La valeur `latest` est proscrite.

---

## Données

*Supprimées par rapport à la bêta : EXI-DATA-1, 3, 4.*

**EXI-DATA-2** · P · *Données* ⚠️ reformulé
Le projet est responsable de la protection des données personnelles qu'il traite. Pour la persistance de données soumises au RGPD, il intègre dès la conception l'identification des données personnelles, des règles et processus d'anonymisation, et une politique de gestion des droits des personnes.
