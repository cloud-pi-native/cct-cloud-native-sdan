# Référentiel d'exigences applicables au CCT Cloud Pi Native

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

---

## Organisation et modèle d'opération

**EXI-ORG-1** · P · *Modèle d'opération*
Conformité au modèle de responsabilité Cloud Pi Native : l'équipe projet est responsable de la qualité de sa solution et de la prise en compte des vulnérabilités. CPiN remonte des indicateurs ; l'équipe projet les évalue, puis corrige ou accepte le risque de manière tracée.

**EXI-ORG-2** · I · *Modèle d'opération*
Les équipes contribuent à la remontée et à l'enrichissement de l'offre Cloud Native : elles signalent les défauts éventuels ou les besoins d'évolution et soumettent, le cas échéant, une rectification ou une évolution sur le dépôt de code après l'avoir testée.

**EXI-ORG-3** · P · *Modèle d'opération*
Conformité au modèle de responsabilité « you build it – you run it – you secure it – you support it » de l'offre Cloud Pi Native.
L'équipe projet est responsable d'organiser le bon fonctionnement de l'application en production et le soutien aux usagers.
Un modèle de collaboration, précisant les responsabilités de chaque acteur, est établi dans la convention d'utilisation de l'offre avec l'hébergeur. Cela peut inclure d'autres conventions avec d'autres services (supervision applicative, SOC ministériel). Les normes d'interface sont à demander lors de la contractualisation de l'hébergement.

**EXI-ORG-17** · I · *Compétence*
L'équipe est formée aux bonnes pratiques des technologies Cloud Native (Kubernetes), à la construction et au maintien en qualité d'une base de code, à l'agilité, au DevSecOps et à l'intégration continue (fournir les certifications en preuve).

**EXI-ORG-16** · I · *Compétence*
L'équipe s'appuie de préférence sur un ou plusieurs coachs et experts certifiés Cloud Pi Native pour l'initialisation du programme et une revue régulière des pratiques.

**EXI-ORG-6** · I · *Modèle d'opération*
La chaîne primaire (dépôts de code applicatif et de code d'infrastructure, outillage du projet) est la source de vérité de l'équipe projet. L'équipe projet est responsable de son intégration technique à la chaîne DevSecOps de CPiN et de son maintien en condition de disponibilité et de sécurité. La chaîne secondaire reconstruit et déploie à partir de cette source.

**EXI-ORG-7** · P · *Modèle d'opération*
L'équipe projet est responsable du pipeline de la chaîne secondaire de construction applicative (pipeline GitLab). Elle s'appuie sur les outils et les exemples proposés par la documentation et met en œuvre les vérifications nécessaires : qualité du code, vérifications fonctionnelles automatiques, mesures de sécurité spécifiques issues de la démarche d'homologation.

**EXI-ORG-8** · P · *Modèle d'opération*
Seul le mode de déploiement GitOps est mis en œuvre. L'équipe projet versionne son code applicatif et son code d'infrastructure. Les déploiements par manifest « à la main » ne sont pas autorisés.

**EXI-ORG-9** · I · *Modèle d'opération*
L'équipe projet met en place un principe de livraison continue, de préférence par lots de taille réduite.

**EXI-ORG-11** · I · *Qualité de la solution* 
L'équipe projet est responsable de la qualité de son code, de la politique de test et de la non-régression.

**EXI-ORG-13** · P · *Modèle d'opération* 
L'équipe projet est responsable de la prise en compte des vulnérabilités de son application, y compris celles découvertes après le dernier déploiement stable. CPiN remonte les indicateurs (scans de vulnérabilités, qualité du code) ; l'équipe projet les évalue, puis corrige ou accepte le risque.

**EXI-ORG-15** · I · *Modèle d'opération*
Alerting : CPiN met en place l'outillage d'alerting. L'équipe projet l'implémente dans son contexte : règles d'alerte et destinataires.

**EXI-ORG-17 bis** · P · *Modèle d'opération*
L'orchestration de la sauvegarde est de la responsabilité de l'équipe projet.

**EXI-ORG-18** · I · *Modèle d'opération*
L'équipe projet teste régulièrement sa capacité à restaurer l'ensemble de l'architecture et des données de l'application, avec un scénario de test connu à l'avance.

---

## Architecture

**EXI-ARCH-1** · I · *Architecture*
L'application doit être cloud native et respecter les principes des 12 facteurs : https://12factor.net/

**EXI-ARCH-2** · P · *Architecture*
Afin de répondre aux exigences de disponibilité DIMA/PDMA, le projet peut mettre en place un PRA et déployer son application sur plusieurs régions. Les modalités de mise en place, d'activation et de test du PRA sont de la responsabilité du projet. Des opérateurs liés aux bases de données sont mis à disposition par CPiN pour permettre de faciliter la haute disponibilité de la persistance (par exemple CNPG). Le stockage S3 est accessible depuis les différentes régions. La mise en place de plusieurs réplicas permet de limité l'indisponibilité pendant les opérations de maintenance.

**EXI-ARCH-3** · I · *Architecture*
Il est conseillé d'avoir une approche modulaire à l'intérieur des projets CPIN afin d'éviter les charges de travail (pod) nécessitant des request (CPU/RAM) importants.

**EXI-ARCH-4** · I · *Architecture*
L'utilisation du stockage objet (S3) du ministère est conseillée pour le stockage des sauvegardes.

**EXI-ARCH-5** · P · *Code applicatif & image d'infrastructure applicative*
Il est conseillé de s'appuyer sur des images et des charts Helm issus de communautés actives, à cycle de MCO/MCS fréquent. Les images doivent être rootless. Vérifier systématiquement la date de dernière mise à jour, les vulnérabilités connues et l'accès au code source.
Le choix de l'image de base reste celui du projet ; il est recommandé, dans l'ordre :
1. des images sans outillage (distroless, minideb) ;
2. des images de communautés reconnues, régulièrement mises à jour et adaptées à un usage sécurisé sous OpenShift (rootless, système de fichiers en lecture seule, securityContext).


**EXI-ARCH-6** · I · *Déploiement*
La configuration de l'application (valeurs et secrets) est séparée du code et de l'image et fournie à l'exécution : ConfigMap, Secret ou variables d'environnement (par exemple via le mécanisme `values.yaml` des charts Helm).

**EXI-ARCH-6 bis** · I · *Code applicatif & image*
La construction d'images en plusieurs étapes (*multi-stage build*) est possible et encouragée : elle ne recopie dans l'image finale que les fichiers utiles.

**EXI-ARCH-7** · P · *Architecture*
Les certificats racines (et intermédiaires) de la PKI interne du ministère doivent être injectés aux images par configuration, afin que les services consommant des endpoints HTTPS puissent en valider les certificats. *Conseil : si le runtime permet de monter les CA depuis un fichier ou un répertoire, les monter depuis une ConfigMap ou un Secret ; si le service utilise le CA-bundle de l'OS, exécuter `update-ca-certificates` à la construction de l'image.*

**EXI-ARCH-8** · I · *Architecture*
Le déploiement est réalisé en GitOps (Argo CD). Le code d'infrastructure est versionné dans Git.

**EXI-ARCH-10** · P · *Services mutualisés*
L'équipe projet utilise les services socles de l'offre Cloud Pi Native : chaîne de service, IAM, Vault et gestion des secrets, observabilité (logs et télémétrie), dépôt d'images. Le projet doit se conformer aux contraintes d'usage de l'offre de service CPiN (pas de dérogation par projet) 

**EXI-ARCH-12** · I · *Code applicatif & image*
L'application est monitorable techniquement et fonctionnellement. L'usage des probes Kubernetes (*liveness*, *readiness*, *startup*) est fortement conseillé. L'application expose une API de santé auto-descriptive `/health` (JSON + problem) et des métriques `/metrics` (Prometheus), et s'intègre dans la ou les chaînes de supervision.

**EXI-ARCH-14a** · I · *Architecture*
L'application prend en compte dans sa conception la séparation des flux et des usages : flux usagers, flux de services, flux d'administration.

**EXI-ARCH-14b** · I · *Architecture*
L'usage du protocole HTTPS est obligatoire jusqu'à la CDS. Il est possible de faire du https de bout en bout sur l'ensemble des composant, à la charge du projet.

**EXI-ARCH-18a** · P · *Code applicatif & image*
Les images de conteneurs s'exécutent en « rootless », sur des ports réseau internes supérieurs à 1024, sans élévation de privilèges et sans se modifier elles-mêmes au lancement. L'écriture dans les pods n'est possible que sur un volume monté (par exemple un volume `emptyDir` sur `/tmp`, le système de fichiers étant en lecture seule). L'exécution du pod est bloquée si ces règles ne sont pas respectées.

**EXI-ARCH-26** · I · *Architecture*
Les déploiements Kubernetes n'imposent pas d'éléments de securityContext (runAsUser, runAsGroup, fsGroup, capabilities ajoutées, etc.). Il n'est pas autorisé de monter des ressources depuis le nœud (hostPath, par exemple).

**EXI-ARCH-18b** · I · *Code applicatif & image*
L'image est minimaliste, centrée sur une fonction primaire ou atomique, et conçue pour démarrer très rapidement avec le moins de dépendances possible, dans l'intérêt de la résilience et du bon fonctionnement de l'orchestrateur.

**EXI-ARCH-19** · P · *Code applicatif & image*
Les pods applicatifs stateless doivent pouvoir être redémarrés rapidement et à tout instant, sans affinité de session par l'orchestrateur. L'application est conçue pour minimiser les pertes de données et de transactions en cours en cas de bascule de nœud.

**EXI-ARCH-23** · I · *Architecture*
Les logs sont redirigés vers la sortie standard et sont suffisants pour permettre au projet d'exploiter son application. En cas d'interconnexion avec le C2MI, un format de log peut être imposé à la charge du projet.

**EXI-ARCH-24** · P · *Architecture*
L'équipe projet est responsable de l'exploitation de son application et de ses performances. Elle met en place la mesure des performances pour contrôler la qualité de service et soutenir les investigations en cas de dysfonctionnement.

**EXI-ARCH-27a** · P · *Architecture*
Si le paramètre `imagePullPolicy` est spécifié, il est positionné à `IfNotPresent`, ce qui permet de découpler le cluster de la registry.

**EXI-ARCH-27b** · P · *Architecture*
Le tag des images est une valeur explicite de version. La valeur `latest` est proscrite.

---

## Données

**EXI-DATA-2** · P · *Données*
Le projet est responsable de la protection des données personnelles qu'il traite. Pour la persistance de données soumises au RGPD, il intègre dès la conception l'identification des données personnelles, des règles et processus d'anonymisation, et une politique de gestion des droits des personnes.
