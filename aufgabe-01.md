# Aufgabe 1: Verständnisfragen


1. Was ist Docker Compose, und wofür wird es verwendet?

Docker Compose ist ein Tool, das verwendet wird, um Docker-Anwendungen mit mehreren Containern zu definieren und auszuführen. Mit Docker Compose können Sie die Dienste Ihrer Anwendung über eine YAML-Datei konfigurieren und alle Dienste aus Ihrer Konfiguration mit einem einzigen Befehl erstellen und starten.

Docker Compose bietet folgende Hauptfunktionen:

Dienste: Dienste sind eine Liste von einzelnen Docker-Containern, die vom Compose-Tool ausgeführt werden. Hier werden die Ports und andere Konfigurationen angegeben, die zum Ausführen der Docker-Container erforderlich sind.

Netzwerke: Netzwerke bieten eine Möglichkeit, über die verschiedene Dienste miteinander interagieren können. Jeder Container kann sich an ein Netzwerk anschließen und alle Container innerhalb desselben Netzwerks können miteinander kommunizieren.

Volumes: Docker-Container enthalten standardmäßig keinen Persistenzspeicher. Wenn ein Docker-Container beendet wird, gehen alle Daten in seinem Speicher verloren. Um einige persistente Daten zu speichern, benötigen Sie also Volumes.

Docker Compose wird hauptsächlich in den folgenden Szenarien verwendet:

Zentrale Verwaltung von Microservices: Docker Compose erlaubt die zentrale Verwaltung von Deployments von vielen verschiedenen Docker-Containern, was es zu einem wichtigen Tool für jede Anwendung macht, die mehrere Microservices benötigt.

Schnelle Bereitstellung: Mit Docker Compose können neue Hardware bereitgestellt und zum Laufen gebracht werden, was normalerweise Tage dauert und mit einem enormen Aufwand verbunden ist, auf Sekunden reduziert werden.
Bereitstellung von Anwendungen mit mehreren Containern: Docker Compose kann verwendet werden, um das Containerimage zu erstellen, das Redis-Image herunterzuladen und die Anwendung zu starten.

Erstellen von optimierten Docker-Images: Docker Compose kann auch innerhalb eines Dockerfile-Projekts verwendet werden und kann so konfiguriert werden, dass es ein Image lokal erstellt und ausführt, anstatt es vom Docker Hub zu ziehen.

2. Was ermöglicht Docker Compose in Bezug auf Container?
Docker Compose ermöglicht die Verwaltung mehrerer Container auf verschiedene Weisen:

Definition von Anwendungsumgebungen: Mit Docker Compose können Sie die Umgebung Ihrer App mit einer Dockerfile definieren, sodass sie überall reproduziert werden kann. Sie können die Dienste, die Ihre App bilden, in einer compose.yaml-Datei definieren, sodass sie zusammen in einer isolierten Umgebung ausgeführt werden können.

Netzwerkeinstellungen: Docker Compose ermöglicht die Definition von Netzwerkeinstellungen für Container. Dies beinhaltet die Konfiguration der Netzwerkmodi und die Definition von benutzerdefinierten Netzwerken.

Bau von Anwendungen: Docker Compose ermöglicht das Bauen von Anwendungen direkt aus der compose.yaml-Datei heraus. Sie können den Pfad zum Build-Kontext, das Dockerfile und die Build-Argumente angeben.

Verwendung von Labels: Docker Compose unterstützt die Verwendung von Labels, um Metadaten zu Containern hinzuzufügen. Sie können entweder ein Array oder ein Wörterbuch verwenden.

Bereitstellungsspezifikationen: Docker Compose unterstützt die Verwendung von Bereitstellungsspezifikationen, um zusätzliche Metadaten zu Diensten zu deklarieren. Diese Spezifikationen enthalten Informationen wie den Modus, die Platzierung und die Ressourcenbeschränkungen.

3. Was sind die Vorteile der Verwendung von Docker Compose für die Orchestrierung von Containern?
Einfachheit: Docker Compose ermöglicht es Ihnen, komplexe Anwendungen mit mehreren Containern über eine einzige YAML-Datei zu definieren und auszuführen. Dies vereinfacht die Bereitstellung und Verwaltung dieser Anwendungen erheblich.

Automatisierte Testumgebungen: Docker Compose bietet eine praktische Möglichkeit, isolierte Testumgebungen für Ihre Testsuite zu erstellen und zu zerstören. Dies ist ein wichtiger Teil jedes Continuous Deployment oder Continuous Integration Prozesses.

Einzel-Host-Bereitstellungen: Docker Compose ist traditionell auf Entwicklung und Test-Workflows ausgerichtet, macht aber mit jeder Veröffentlichung Fortschritte bei produktionsorientierten Funktionen.

Skalierbarkeit: Mit Docker Compose können Sie schnell und einfach neue Container erstellen, um die Skalierbarkeit Ihrer Anwendung zu erhöhen. Dies ist besonders nützlich für Anwendungen, die unter hoher Last stehen oder schnell wachsen.

Portabilität: Docker Compose erhöht die Portabilität Ihrer Anwendungen, da Sie sie auf jedem System, das Docker ausführen kann, bereitstellen können. Dies stellt sicher, dass Ihre Anwendung konsistent auf jedem Host ausgeführt wird.

Produktivitätssteigerung: Docker Compose kann die Produktivität steigern, indem es die Zeit reduziert, die zum Ausführen von Aufgaben benötigt wird, und gleichzeitig die Sicherheit erhöht, da alle Container voneinander isoliert sind.

Versionskontrolle: Die YAML-Dateien, die Docker Compose verwendet, können in ein Versionskontrollsystem eingecheckt werden. Dies ermöglicht es Teams, Änderungen an der Anwendungskonfiguration im Laufe der Zeit zu verfolgen und bei Bedarf zu früheren Konfigurationen zurückzukehren.

4. Wie wird die Konfiguration in einer `docker-compose.yml`-Datei festgelegt?

Die Konfiguration in einer docker-compose.yml-Datei wird durch eine Reihe von Schlüsselwörtern und Strukturen bestimmt, die bestimmte Aspekte der Docker-Container und ihrer Interaktionen definieren:

version: Dieser Schlüssel definiert die Version von Docker Compose, die zur Interpretation der Datei verwendet wird

services: Unter diesem Schlüssel werden die einzelnen Container definiert, die in Ihrer Anwendung ausgeführt werden. Jeder Dienst hat eine Reihe von Konfigurationsoptionen, darunter image (das zu verwendende Docker-Image), build (Anweisungen zum Erstellen des Docker-Images), ports (Port-Mappings für den Container), volumes (definiert die Volumes für den Container) und viele andere

networks: Dieser Schlüssel definiert die Netzwerke, die von den Containern in Ihrer Anwendung verwendet werden. Sie können benutzerdefinierte Netzwerke erstellen und sie dann Ihren Diensten zuweisen.

volumes: Unter diesem Schlüssel werden die Volumes definiert, die von den Containern in Ihrer Anwendung verwendet werden. Sie können benutzerdefinierte Volumes erstellen und sie dann Ihren Diensten zuweisen.

5. Welches Dateiformat wird für Docker Compose-Konfigurationen verwendet?
Das YAML-Format (Yet Another Markup Lanuguage)

6. Wenn ich einen Fehler in meiner Yaml Datei habe, was sollte zuerst überprüft werden?
    a. Einrückung (Interrogation)
    b. Formatierung
    c. Anführungszeichen
    d. Version
    e. Syntax
    f. Docker Compose spezifische Schlüsselwörter

7. Was sind die grundlegenden Datentypen, die in YAML-Konfigurationen verwendet werden können?
In YAML-Konfigurationen können verschiedene grundlegende Datentypen verwendet werden:

Skalare: Dies sind einfache Datentypen wie Zahlen, Booleans und Strings. Sie sind die grundlegendsten Datentypen in YAML.

Sequenzen: Sequenzen sind Listen von Elementen. In YAML werden sie durch einen Bindestrich "-" und ein Leerzeichen vor jedem Element gekennzeichnet.

Abbildungen: Abbildungen (oder Dictionaries) sind Sammlungen von Schlüssel-Wert-Paaren. Sie ähneln Skalaren, können aber verschachtelte Daten einschließlich anderer Datentypen enthalten.
Komplexe Strukturen: YAML unterstützt die Erstellung komplexer Datenstrukturen durch Verweise auf andere Datenobjekte. Dies ermöglicht es Ihnen, rekursive Daten in der YAML-Datei zu schreiben und komplexere Datenstrukturen zu erstellen.

Darüber hinaus können Sie in YAML explizite Datentypen mit Tags angeben.

8. Welche top-level Elemente können in einer `docker-compose.yml`-Datei definiert werden?
    a. version
    b. services
    c. networks
    d. volumes
    e. secrects

9. Was sind Dienste (Services) in Docker Compose?
Definiert die Dienste (d.h. Container), die in Ihrer Anwendung ausgeführt werden sollen. Jeder Dienst hat seine eigene Konfiguration, einschließlich des Docker-Images, das verwendet werden soll, der Ports, die freigegeben werden sollen, und der Volumes, die gemountet werden sollen.

10. Wie können Volumes in einer Docker Compose-Konfiguration definiert werden?
Definiert benutzerdefinierte Volumes, die von Ihren Diensten verwendet werden können. Sie können auch die Standardvolumeneinstellungen für alle Dienste in der Datei definieren.

11. Warum sind Volumes wichtig, und wofür werden sie verwendet?

Volumes sind in Docker wichtig, da sie dazu dienen, persistente Daten in Containern zu verwalten. Sie ermöglichen es, Daten auch nach dem Entfernen oder Aktualisieren eines Containers beizubehalten, sodass wichtige Anwendungsdaten während routinemäßiger Vorgänge nicht verloren gehen.

Hier sind einige Gründe, warum Volumes wichtig sind und wofür sie verwendet werden:

Persistenz: Volumes ermöglichen es, Daten auch dann zu speichern, wenn Container beendet oder gelöscht werden. Dadurch können wichtige Daten, wie z.B. Konfigurationsdateien oder Datenbanken, dauerhaft gespeichert werden.
Portabilität: Volumes sind von der Dateisystemstruktur des Containers entkoppelt. Dadurch können sie einfach zwischen verschiedenen Containern oder Hosts verschoben werden. Dies ermöglicht eine flexible und effiziente Datenverwaltung in containerbasierten Anwendungen.

Datenaustausch: Volumes können zwischen mehreren Containern gemeinsam genutzt werden. Dadurch können Daten leicht zwischen verschiedenen Teilen einer Anwendung ausgetauscht werden.

Backup und Wiederherstellung: Mit Volumes können Daten einfach gesichert und wiederhergestellt werden. Durch das Trennen der Daten vom Container wird sichergestellt, dass sie bei der Wiederherstellung eines Containers oder bei der Migration auf einen anderen Host nicht verloren gehen.

Skalierbarkeit: Volumes ermöglichen es, Daten unabhängig von der Anzahl der Container zu verwalten. Beim Skalieren einer Anwendung können Volumes dazu beitragen, dass alle Container auf die gleichen Daten zugreifen und konsistente Ergebnisse liefern.

In Docker Compose können Volumes in der docker-compose.yml-Datei definiert werden, entweder als benannte Volumes oder als anonyme Volumes:

Benannte Volumes: Benannte Volumes werden mit einem eindeutigen Namen definiert und können von mehreren Containern gemeinsam genutzt werden. Sie werden in der volumes-Sektion der docker-compose.yml-Datei definiert.
Anonyme Volumes: Anonyme Volumes werden automatisch für einen Container erstellt und sind nur für diesen Container zugänglich. Sie werden in der volumes-Sektion der docker-compose.yml-Datei ohne einen Namen definiert.

12. Wie können benutzerdefinierte Netzwerke in Docker Compose erstellt werden?
Um benutzerdefinierte Netzwerke in Docker Compose zu erstellen, können Sie diese in Ihrer docker-compose.yml-Datei mithilfe des networks-Abschnitts definieren. 
Hier ist ein Beispiel, wie benutzerdefinierte Netzwerke in Docker Compose erstellt werden können:

version: '3'

services:
  backend:
    # Konfiguration des Dienstes hier angeben

networks:
  backnet:
  frontnet:
In diesem Beispiel definieren wir zwei benutzerdefinierte Netzwerke: backnet und frontnet. Sie können Ihren Netzwerken beliebige Namen geben. Diese Netzwerke werden erstellt, wenn Sie docker-compose up ausführen.

Man kann dann angeben, mit welchem Netzwerk(s) ein Dienst verbunden werden soll, indem dem Dienst die networks-Eigenschaft hinzugefügt wird. Hier ist ein Beispiel:

services:
  backend:
    # Konfiguration des Dienstes hier angeben
    networks:
      - backnet
      - frontnet
In diesem Beispiel ist der Dienst backend mit den Netzwerken backnet und frontnet verbunden.

13. Welche Befehle werden verwendet, um eine Docker Compose-Anwendung zu starten und zu stoppen?
Starten: docker-compose up
Befehl im Hintergrund ausführen: docker-compose up -d
Stoppen: docker-compose down
Container stoppen, ohne sie zu entfernen: docker-compose down --volumes

14. Was bewirkt der Befehl `docker-compose up -d`?
Befehl im Hintergrund ausführen

15. Wie können Sie die Logs einer Docker Compose-Anwendung anzeigen?
Befehl: docker-compose logs [OPTIONS] [SERVICE...]
-f oder --follow: Zeigt die Logs in Echtzeit an und folgt neuen Logs, während sie generiert werden.
--tail <number>: Zeigt nur eine bestimmte Anzahl von Zeilen der Logs an, wobei <number> die Anzahl der Zeilen ist, die angezeigt werden sollen.
--since <time>: Zeigt nur die Logs an, die nach einem bestimmten Zeitpunkt generiert wurden. <time> kann eine relative Zeitangabe wie "5m" für 5 Minuten oder ein Zeitstempel im Format YYYY-MM-DDTHH:MM:SS sein.
--until <time>: Zeigt nur die Logs an, die vor einem bestimmten Zeitpunkt generiert wurden. <time> kann eine relative Zeitangabe oder ein Zeitstempel sein.

16. Welcher Befehl wird verwendet, um alle Images in einer Docker Compose-Konfiguration zu erstellen / bauen?
    docker compose build [SERVICE...]
    Beispiel: docker compose build frontend backend
17. Wie kann in einer Docker Compose-Konfiguration festgelegt werden, ob ein Image lokal erstellt oder aus der Registry gepulled werden soll?

Beispiel für das Erstellen eines Images aus dem Build-Context:

services:
  backend:
    build:
      context: ./backend

Beispiel für das Pullen eines Images aus der Registry:

services:
  frontend:
    image: nginx:latest

Beispiel für das Pullen eines Images aus der Registry:

services:
  frontend:
    image: nginx:latest
    pull: always

18. Welche grundlegenden Aufgaben erfüllen Netzwerke in Docker Compose?

Netzwerke in Docker Compose erfüllen verschiedene grundlegende Aufgaben, um die Kommunikation zwischen den Diensten in Ihrer Anwendung zu ermöglichen. Hier sind einige der wichtigsten Aufgaben, die Netzwerke in Docker Compose erfüllen:

a. Isolation: Netzwerke in Docker Compose bieten eine isolierte Umgebung für die Dienste in Ihrer Anwendung. Jeder Dienst wird standardmäßig in einem eigenen Netzwerksegment ausgeführt, was eine klare Trennung und Isolation ermöglicht. Dadurch können Sie sicherstellen, dass die Dienste nicht unerwünscht aufeinander zugreifen können und dass potenzielle Konflikte vermieden werden.

b. Kommunikation: Netzwerke ermöglichen die Kommunikation zwischen den Diensten in Ihrer Docker Compose-Anwendung. Wenn Dienste in derselben Netzwerkumgebung ausgeführt werden, können sie miteinander kommunizieren, Ressourcen teilen und Daten austauschen. Dies ist besonders wichtig, wenn Ihre Anwendung aus mehreren Diensten besteht, die zusammenarbeiten müssen.

c. Namensauflösung: Netzwerke in Docker Compose bieten eine Namensauflösungsfunktion, die es den Diensten ermöglicht, sich gegenseitig über ihre Dienstenamen zu erreichen. Anstatt IP-Adressen zu verwenden, können Sie in Ihrer Anwendung die Dienstenamen verwenden, um auf andere Dienste zu verweisen. Docker Compose verwendet standardmäßig einen internen DNS-Server, um die Namensauflösung zwischen den Diensten zu ermöglichen.

d. Skalierbarkeit: Netzwerke spielen auch eine wichtige Rolle bei der Skalierung von Diensten in Docker Compose. Wenn Sie einen Dienst skalieren, indem Sie mehrere Instanzen desselben Dienstes starten, werden diese Instanzen automatisch in das gleiche Netzwerk eingebunden. Dadurch können die replizierten Dienste miteinander kommunizieren und die Last auf mehrere Instanzen verteilen.

e. Externe Konnektivität: Netzwerke in Docker Compose können auch verwendet werden, um Dienste mit externen Ressourcen zu verbinden. Sie können beispielsweise ein benutzerdefiniertes Netzwerk erstellen und dann einen Dienst in diesem Netzwerk ausführen, um auf eine externe Datenbank oder einen anderen Dienst zuzugreifen, der außerhalb der Docker Compose-Umgebung läuft.