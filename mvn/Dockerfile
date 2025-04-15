# Étape 1 : Construire l'application avec Maven
FROM maven:3.9.6-eclipse-temurin-17 as builder
WORKDIR /app
# Copier le fichier pom.xml et les sources
COPY pom.xml .
COPY src ./src
RUN mvn clean package

# 2: Créer une image minimale avec le JAR généré
FROM eclipse-temurin:17-jre-jammy
WORKDIR /app
# Copier le JAR depuis l'étape de build
COPY --from=builder /app/target/mon-projet-1.0-SNAPSHOT.jar app.jar
# Lancer l'application
ENTRYPOINT ["java", "-jar", "app.jar"]
