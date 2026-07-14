# Back-end Spring Boot

API Spring Boot du projet Yoga App.

## Commandes utiles

Lancer les tests JUnit/Mockito :

```bash
mvn test
```

Lancer l'API en local après configuration de `back/.env` :

```bash
mvn spring-boot:run
```

Le rapport JaCoCo est généré dans :

```text
target/site/jacoco/index.html
```

Voir le README racine pour la configuration MySQL, JWT et le lancement complet de l'application.
