# Full-Stack Yoga App Testing

Application full-stack Angular + Spring Boot autour de la gestion de cours de yoga, mise en valeur comme projet de tests automatisés.

## Objectif du projet

Ce projet montre la mise en place d'une stratégie de tests complète sur une application existante :

- tests unitaires et d'intégration Angular avec Jest ;
- tests end-to-end avec Cypress ;
- tests unitaires et d'intégration Spring Boot avec JUnit et Mockito ;
- rapports de couverture front-end et back-end ;
- API sécurisée avec authentification JWT.

## Fonctionnalités applicatives

L'application permet à des utilisateurs de consulter et rejoindre des sessions de yoga. Un administrateur peut gérer les sessions et les enseignants.

Fonctionnalités principales :

- inscription et connexion utilisateur ;
- authentification JWT ;
- consultation des sessions de yoga ;
- création, modification et suppression de sessions côté admin ;
- consultation du profil utilisateur ;
- participation / désinscription à une session.

## Stack technique

### Front-end

- Angular 14
- Angular Material
- RxJS
- Jest
- Cypress

### Back-end

- Java 8
- Spring Boot 2.6
- Spring Security
- JWT
- Spring Data JPA
- MySQL
- JUnit / Mockito
- Maven

### Infra locale

- Docker Compose pour MySQL
- Postman collection disponible dans `ressources/postman/`

## Structure du dépôt

```text
front/       Application Angular
back/        API Spring Boot sécurisée par JWT
db/          Docker Compose et image MySQL locale
ressources/  Collection Postman et ressources de test
```

## Lancer l'application en local

### 1. Préparer la base MySQL

Créer `db/.env` avec les variables attendues par `db/compose.yml` :

- `MYSQL_USERNAME`
- `MYSQL_ROOT_PASSWORD`
- `MYSQL_PASSWORD`

Démarrer MySQL :

```bash
cd db
docker compose up -d
```

La base expose MySQL sur le port `3307` côté machine.

### 2. Configurer le back-end

Créer `back/.env` avec les variables attendues par `back/src/main/resources/application.properties` :

- `MYSQL_URL`
- `MYSQL_USERNAME`
- `MYSQL_PASSWORD`
- `SECURITY_JWT_SECRET_KEY`
- `SECURITY_JWT_EXPIRATION_TIME`

Pour une installation locale classique, `MYSQL_URL` pointe vers la base MySQL du Docker Compose sur `localhost:3307`.

### 3. Lancer l'API Spring Boot

```bash
cd back
mvn spring-boot:run
```

API disponible par défaut sur :

```text
http://localhost:8080
```

### 4. Lancer le front Angular

```bash
cd front
npm ci
npm start
```

Application disponible sur :

```text
http://localhost:4200
```

Le compte administrateur de démonstration est créé par le script SQL dans `db/script.sql`.

## Tests et couverture

### Tests front-end Jest

```bash
cd front
npm test
```

Rapport de couverture :

```text
front/coverage/jest/lcov-report/index.html
```

### Tests end-to-end Cypress

```bash
cd front
npm run e2e:ci
```

Rapport de couverture E2E :

```bash
npm run e2e:coverage
```

Rapport HTML :

```text
front/coverage/lcov-report/index.html
```

### Tests back-end JUnit / Mockito

```bash
cd back
mvn test
```

Rapport JaCoCo :

```text
back/target/site/jacoco/index.html
```

## Ce que le projet met en valeur

- Mise en place d'une stratégie de tests complète sur une app full-stack.
- Couverture des composants Angular, services, guards et intercepteurs.
- Tests API Spring Boot avec services, contrôleurs, sécurité JWT et repositories.
- Parcours utilisateur validés avec Cypress.
- Configuration locale reproductible avec Docker Compose.

## Résumé portfolio

Projet full-stack Angular/Spring Boot centré sur la qualité logicielle : sécurisation JWT, base MySQL Dockerisée, tests front/back/e2e et rapports de couverture. Il démontre la capacité à fiabiliser une application existante avec une vraie stratégie de test automatisée.
