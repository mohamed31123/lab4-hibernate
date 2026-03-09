# 🗄️ TP 4 – Hibernate avec JakartaEE

## 📝 Description
Ce projet est une application Java utilisant **Hibernate** pour gérer la persistance des entités.  
Il illustre la mise en place d’une architecture DAO/Service avec gestion des transactions, et l’utilisation de JUnit pour les tests unitaires.

## 📂 Étapes du TP
1. **Introduction**
2. **Configuration du fichier `pom.xml`**  
   → Dépendances Hibernate, JPA, JUnit.
3. **Création de l’interface DAO**  
   → Interface générique `IDao<T>` définissant les opérations CRUD.
4. **Création des entités JPA**  
   → Exemple : `Salle`, `Machine`.
5. **Configuration de Hibernate**  
   → Fichier `hibernate.cfg.xml` et mapping des entités.
6. **Classe utilitaire Hibernate**  
   → `HibernateUtil` pour gérer la `SessionFactory`.
7. **Création de la couche Service**  
   → Implémentations concrètes des opérations DAO pour chaque entité (`SalleService`, `MachineService`).
8. **Classe de test pour générer la base de données**  
   → Vérification de la création des tables et insertion initiale.
9. **Mise en place des tests unitaires avec JUnit**  
   → Validation des opérations CRUD et des requêtes spécifiques.

## ⚙️ Exemple de Service : `SalleService`
La classe `SalleService` implémente `IDao<Salle>` et fournit :
- `create(Salle o)` : insertion d’une salle
- `delete(Salle o)` : suppression
- `update(Salle o)` : mise à jour
- `findById(int id)` : recherche par identifiant
- `findAll()` : récupération de toutes les salles via HQL

Chaque méthode :
- Ouvre une session Hibernate
- Démarre une transaction
- Exécute l’opération
- Valide ou annule la transaction en cas d’exception
- Ferme la session

## ⚙️ Exemple de Service : `MachineService`
La classe `MachineService` suit la même logique que `SalleService` et ajoute :
- `findBetweenDate(Date d1, Date d2)` : récupération des machines dont la date d’achat est comprise entre deux dates, via une **NamedQuery** définie dans l’entité `Machine`.

## ▶️ Exécution
Pour lancer le projet :
```bash
mvn clean install
mvn test

```


## Video Demo



https://github.com/user-attachments/assets/474e8f19-2703-4acb-8620-f80da66e4899



## Conclusion

Ce TP montre comment intégrer Hibernate dans une application Java pour gérer la persistance des données.
Grâce à la séparation en couches (DAO, Service, Utilitaire), l’application est modulaire, maintenable et extensible.
Les tests unitaires garantissent la fiabilité et facilitent l’évolution du projet.

## Auteur : EDDINARI MED
