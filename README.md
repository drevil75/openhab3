# openhab3
## Openhab3-Installation mit Docker und Persistence (Maria-DB)

Mit dem docker-compose.yml-File werden Docker-Container mit Openhab3 und Maria-DB erstellt.

## Vor dem Start bitte folgende Dinge anpassen:

### docker-compose.yml
    openhab3:
    ports:
      - "38080:8080/tcp" # hier den gewünschten Port angeben.
    
    oh3persistence-db:
    ports:
      - "33306:3306" # hier den gewünschten Port angeben.
    environment:
      - MYSQL_ROOT_PASSWORD=MeinOHrootPW # Datenbank Root-Passwort wählen. Nur für Adminzwecke notwendig.
      - MYSQL_PASSWORD=MeinOHPW # Datenbank User-Passwort wählen, wird bei der Persistence-Konfig abgefragt.
      - MYSQL_DATABASE=openhab3 # Datenbankname anpassen oder so lassen, wird bei der Persistence-Konfig abgefragt.
      - MYSQL_USER=openhab3     # Datenbank User wählen, wird bei der Persistence-Konfig abgefragt.
     
      
### openhab3 -Persistence-Konfig:
    Database URL: jdbc:mariadb://192.168.0.50:33306/openhab3
    Database User: openhab3         # Hier den Usernamen aus dem docker-compose.yml eintragen
    Database Password: MeinOHPW     # Hier das Passwort aus dem docker-compose.yml eintragen

