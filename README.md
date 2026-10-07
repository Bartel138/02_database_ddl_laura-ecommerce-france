# 02_database_ddl_laura-ecommerce-france
Conception d'une architecture e-commerce multinationale de 13 tables relationnelles. Définition des entités (clients, produits, commandes, paiements, stocks), des clés primaires/étrangères et des règles de normalisation.

# 🛒 Projet 1 : Architecture et Modélisation - Laura E-Commerce France

## 📋 Description du Projet
Ce projet présente l'architecture d'une base de données relationnelle hautement scalable, conçue pour supporter une plateforme e-commerce multinationale (**Laura E-Commerce France**). Le système gère un écosystème complexe de **13 tables** interconnectées, garantissant l'intégrité des données, la traçabilité des transactions (OLTP) et le support multi-devises/multi-pays.

---

## 🌍 Architecture Multinationale
La modélisation a été pensée dès l'origine pour répondre à des exigences internationales :
* **Multi-pays & Multi-devises** : Gestion centralisée des marchés géographiques et des taux de change.
* **Logistique & Stocks** : Suivi multi-entrepôts et gestion des flux de livraison.
* **Séparation des responsabilités** : Cloisonnement strict entre les référentiels (clients, produits, pays) et les tables transactionnelles (commandes, paiements, expéditions).

---

## 🗄️ Les 13 Tables de l'Écosystème
Le modèle relationnel s'articule autour des tables suivantes :

1. **`country`** : Référentiel international (pays et codes ISO).
2. **`currency`** : Gestion des devises et des taux de change par rapport à l'Euro.
3. **`customer`** : Fichier central des comptes clients.
4. **`address`** : Adresses de facturation et de livraison liées aux clients.
5. **`category`** : Classification hiérarchique du catalogue produits.
6. **`product`** : Catalogue des articles en vente (prix de base, catégories).
7. **`warehouse`** : Implantation des entrepôts logistiques par région.
8. **`inventory`** : Suivi des niveaux de stock par produit et par entrepôt.
9. **`orders`** : Table transactionnelle des commandes clients.
10. **`order_item`** : Table d'association des articles commandés (quantités et prix figés).
11. **`payment`** : Suivi des transactions financières et des modes de paiement.
12. **`shipping`** : Gestion logistique, transporteurs et numéros de suivi.
13. **`review`** : Gestion des avis et de la notation des produits par les clients.

---

## 🔒 Règles de Gestion & Intégrité
* **Intégrité Référentielle** : Utilisation stricte de clés primaires (`PRIMARY KEY`) et de clés étrangères (`FOREIGN KEY`) pour lier les entités logiquement.
* **Contraintes d'Unicité** : Application de contraintes `UNIQUE` (notamment sur les e-mails clients et les codes pays) pour éviter les doublons.
* **Typage Financier Rigoureux** : Utilisation du type `DECIMAL(10,2)` pour tous les montants monétaires afin d'éliminer les erreurs d'arrondi liées aux nombres à virgule flottante.
