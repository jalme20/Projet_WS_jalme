# Projet_WS_jalme

# Projet d'Exploration des Données Météorologiques
### Aperçu
Ce projet fournit une infrastructure robuste pour l'acquisition, le stockage et l'interrogation de données météorologiques pour les villes françaises via l'API OpenWeather. Nous mettons à profit la puissance de Cassandra pour le stockage de données et Flask pour la récupération de données via une API personnalisée. L'orchestration du service est réalisée grâce à Docker et Docker Compose, assurant une mise en service fluide et une maintenance aisée.

### Composants Clés
Cassandra Database: La colonne vertébrale de notre système de stockage, une base de données NoSQL hautement performante.
Service de Crawling Python: Le moteur de collecte qui alimente notre base de données avec des données météorologiques fraîches et précises.
Flask API Service: Notre interface utilisateur pour interroger et récupérer des données météorologiques en fonction des besoins spécifiques.
Docker Compose: L'outil qui fait le lien entre nos services, permettant à notre base de données et à notre service de Crawling de communiquer sans accroc.
Dockerfiles: Les recettes pour construire nos conteneurs, garantissant une uniformité et une portabilité à travers les environnements de déploiement.

### Prérequis
Avant de plonger dans ce projet, assurez-vous d'avoir installé les outils suivants :

Docker: Pour conteneuriser et gérer les environnements d'application.
Docker Compose: Pour orchestrer et gérer les conteneurs Docker.

### Configuration de la Base de Données
Notre base de données utilise l'image Docker officielle de Cassandra, prête à l'emploi sur le port 9042 et joignable au sein de notre réseau Docker sous le nom d'hôte 'cassandra'. Une procédure de vérification de santé intégrée s'assure que la base est prête à recevoir les données avant le démarrage du Crawling.

### Initialisation de Cassandra
Grâce au script init_db.py, notre base de données se voit configurée avec un espace de clés weather_db et une table weather_table, conçue pour accueillir les détails météorologiques comme la température et l'humidité.

### Service de Crawling
Le service de Crawling exploite crawler.py pour collecter les informations météorologiques via l'API OpenWeather, tout en s'assurant de leur insertion efficace dans notre base de données Cassandra. Seules les villes françaises sont ciblées, et les 100 premières reçoivent une attention particulière pour leur stockage.

### Service Flask-API
Notre API Flask constitue le point d'entrée pour les requêtes de données météorologiques. Conteneurisé pour maintenir la cohérence avec le reste de l'infrastructure, ce service sert d'intermédiaire pour transmettre les données météorologiques collectées de la base de données à l'utilisateur final.

### Mise en Route
Pour démarrer le projet, dirigez-vous vers le répertoire principal et lancez docker-compose up. Ceci initialisera et liera tous les services nécessaires, mettant en place notre pipeline d'exploration de données météorologiques.

