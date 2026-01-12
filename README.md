# 🐘 Mini-Projet Big Data : Infrastructure Hadoop, Spark & Sécurité Kerberos

**Master 2 BI&A - Université Lumière Lyon 2** *Matière : Traitement et Analyse de Données Massives (TCSD)*

![Docker](https://img.shields.io/badge/Docker-Enabled-blue?logo=docker) ![Hadoop](https://img.shields.io/badge/Hadoop-3.2.1-yellow?logo=apache-hadoop) ![Spark](https://img.shields.io/badge/Spark-PySpark-orange?logo=apache-spark) ![Security](https://img.shields.io/badge/Security-Kerberos-red)

Ce dépôt contient l'infrastructure et le code nécessaires au déploiement d'un cluster Big Data complet utilisant **Docker**. Le projet implémente une chaîne de traitement allant du stockage distribué (HDFS) à l'analyse de données (Spark), en passant par une sécurisation des accès via le protocole **Kerberos**.

---

## 🎯 Contexte et Objectifs

L'objectif de ce projet est de simuler un environnement de production Big Data sur une machine locale (Windows/Linux) en surmontant les contraintes de ressources matérielles.

**Points clés du projet :**
* **Virtualisation légère :** Utilisation de conteneurs Docker au lieu de machines virtuelles lourdes pour simuler le cluster.
* **HDFS (Hadoop Distributed File System) :** Déploiement d'un système de fichiers distribué avec un Namenode et plusieurs Datanodes.
* **Spark & PySpark :** Ingestion, nettoyage et analyse d'un jeu de données ("Films" et "Bons écologiques").
* **Sécurité Kerberos :** Implémentation d'un serveur KDC pour gérer l'authentification et les tickets d'accès.

---

## 🏗 Architecture Technique

Le projet est orchestré via `docker-compose`. Voici les services déployés :

| Service | Image Docker | Rôle | Port(s) |
| :--- | :--- | :--- | :--- |
| **Namenode** | `bde2020/hadoop-namenode` | Maître du cluster HDFS (Orchestrateur) | `9870` (Web UI), `9000` (RPC) |
| **Datanode 1 & 2** | `bde2020/hadoop-datanode` | Stockage des blocs de données (Workers) | - |
| **Spark Client** | `jupyter/pyspark-notebook` | Environnement d'analyse (Jupyter Lab + PySpark) | `8888` (Jupyter), `4040` (Spark UI) |
| **Kerberos** | `gcavalcante8808/krb5-server` | Serveur d'authentification (KDC) | `88` (Ticket), `749` (Admin) |

---

## ⚙ Prérequis

Avant de lancer le projet, assurez-vous d'avoir :

* **Docker Desktop** (version récente) installé.
* **4 GB de RAM** minimum alloués à Docker (Recommandé : 6 GB pour la stabilité de Spark).
* **Git** pour cloner le projet.

> **⚠️ Note pour Windows :** Il est fortement recommandé d'utiliser le backend **WSL 2** dans Docker Desktop pour éviter les problèmes de performance et de permissions sur les volumes montés.

--
