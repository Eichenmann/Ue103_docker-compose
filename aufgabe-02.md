# Aufgabe 2: Praxis

In dieser Aufgabe werden wir die letzte Aufgabe (von Martin) weiterführen, und die erstellte Infrastruktur auf docker-compose umziehen.

- Clone dir als Vorbereitung das folgende Repository `https://github.com/0xfabio/docker-compose-task`

## Aufgabe 1

- Das Dockerfile um diese Anwendung zu bauen wurde bereits erstellt
- Erstelle eine neue `docker-compose` Datei (im root des repos) mit einem Service für unsere api

```yaml
version: '3'

services:
  api:
```

- Ändere die Datei so ab, dass automatisch das Image der lokalen Dockerfile Datei gebaut wird und verwendet wird

Lösung:
docker-compose.yaml
version: '3'

services:
  api:
    build: .
    ports:
      - 80:3000

Die build-Anweisung wurde hinzugefügt und auf . gesetzt. Dadurch wird Docker Compose angewiesen, das Image basierend auf der Dockerfile im aktuellen Verzeichnis zu bauen.
Die ports-Anweisung wurde hinzugefügt, um den Port-Mapping für den Container anzugeben. In diesem Fall wird der Port 80 auf dem Host auf den Port 3000 im Container gemappt.

- Für weitere Infos schaue hier nach [Doku](https://docs.docker.com/compose/compose-file/build/)

## Aufgabe 2

- Füge einen weiteren Datenbank Service zur docker-compose Config hinzu:
    - Name: `db`
    - Image: `mariadb:11.1.2`
- Stelle sicher, dass folgende Environment Variablen richtig definiert sind, sodass eine Kommunikation mit `app.js` funktioniert:
    - MYSQL_DATABASE=
    - MYSQL_USER=
    - MYSQL_PASSWORD=
- Erstelle ein Volume was die Daten über verschiedene restarts persistiert:
    - Nenne das Volume `db_data`
    - Erstelle ein Mapping von `db_data` zu `/var/lib/mysql`

Lösung:
docker-compose.yaml
version: '3'

services:
  api:
    build: .
    ports:
      - 80:3000
    environment:
      - MYSQL_DATABASE=your_database_name
      - MYSQL_USER=your_username
      - MYSQL_PASSWORD=your_password
  db:
    image: mariadb:11.1.2
    environment:
      - MYSQL_DATABASE=your_database_name
      - MYSQL_USER=your_username
      - MYSQL_PASSWORD=your_password
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:

Hier sind die Änderungen, die vorgenommen wurden:

Ein neuer Service mit dem Namen db wurde hinzugefügt, der das mariadb:11.1.2-Image verwendet.

Die Umgebungsvariablen MYSQL_DATABASE, MYSQL_USER und MYSQL_PASSWORD wurden sowohl für den api-Service als auch für den db-Service definiert. Sie müssen diese Variablen entsprechend Ihren Anforderungen anpassen.

Ein neues Volume mit dem Namen db_data wurde erstellt und dem db-Service zugeordnet. Dieses Volume wird verwendet, um die Daten über verschiedene Neustarts hinweg zu persistieren.

Durch das Hinzufügen des db-Services und die Konfiguration der Umgebungsvariablen wird eine Kommunikation zwischen app.js und der MariaDB-Datenbank ermöglicht.

## Aufgabe 3

- Erstelle ein Netzwerk, was von beiden Services genutzt wird:
    - Name: `app_net`

Lösung:
docker-compose.yaml
version: '3'

services:
  api:
    build: .
    ports:
      - 80:3000
    environment:
      - MYSQL_DATABASE=your_database_name
      - MYSQL_USER=your_username
      - MYSQL_PASSWORD=your_password
    networks:
      - app_net
  db:
    image: mariadb:11.1.2
    environment:
      - MYSQL_DATABASE=your_database_name
      - MYSQL_USER=your_username
      - MYSQL_PASSWORD=your_password
    volumes:
      - db_data:/var/lib/mysql
    networks:
      - app_net

volumes:
  db_data:

networks:
  app_net: