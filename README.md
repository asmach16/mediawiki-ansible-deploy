# mediawiki-ansible-deploy

Déploiement automatisé de MediaWiki avec Ansible

Description du projet
Ce projet automatise le déploiement complet de MediaWiki sur une infrastructure à deux serveurs Debian 12, en utilisant Ansible pour appliquer les principes d'Infrastructure as Code (IaC).

L'objectif est de créer un wiki interne pour l'entreprise fictive GreenOps, permettant de centraliser la documentation et les bonnes pratiques DevOps de manière collaborative et reproductible.

Architecture technique
Le déploiement est séparé en deux serveurs pour respecter les bonnes pratiques et préparer une montée en charge future :

Serveur Web (srv-web-wiki)
Système : Debian 12

Rôle : héberge Apache, PHP et les fichiers de MediaWiki

Accès : via l'URL http://srv-web-wiki/mediawiki

Serveur Base de données (srv-db-wiki)
Système : Debian 12

Rôle : héberge MariaDB et la base de données MediaWiki

Sécurité : isolation de la base de données du serveur web

Machine de contrôle Ansible
Système : Debian

Rôle : exécute Ansible pour configurer automatiquement les deux serveurs

Cette architecture modulaire permet d'ajouter facilement de nouveaux serveurs web en cas d'augmentation du trafic.

 Fonctionnalités
Le playbook Ansible automatise les étapes suivantes :

Sur le serveur de base de données (db)
Installation de MariaDB

Démarrage et activation du service MariaDB

Installation des modules Python pour la gestion de MySQL

Création de la base de données mediawiki

Création de l'utilisateur dédié wikiuser avec les privilèges appropriés

Sur le serveur web (web)
Installation d'Apache2 et de PHP (avec les extensions nécessaires)

Démarrage et activation du service Apache

Téléchargement de MediaWiki 1.41.1 depuis les sources officielles

Extraction et déploiement dans /var/www/mediawiki

Configuration du VirtualHost Apache pour l'accès au wiki

Activation du module `mod_rewr

