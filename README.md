# MySQL Installation

Installiere die MySQL Community Edition: https://dev.mysql.com/downloads/mysql/. 
Notiere das Passwort für den während der Installation erzeugten Root-Account.

Stelle sicher, dass `mysql` und `mysqladmin` auf der Command Line verfügbar sind:
- https://dev.mysql.com/doc/refman/5.7/en/installing.html 

## Root-Zugang konfigurieren 

Bei Bedarf kannst Du das Passwort des Root-Users ändern. 
Melde Dich dazu an DB mit dem notierten ROOT-Zugang an:

    $ mysql -u root -p 
    Enter password: 
    Welcome to the MySQL monitor.  Commands end with ; or \g.
    Your MySQL connection id is 156
    Server version: 5.7.21
    
    Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.
    
    Oracle is a registered trademark of Oracle Corporation and/or its
    affiliates. Other names may be trademarks of their respective
    owners.
    
    Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
    
    mysql>
    
Nun kannst Du das Passwort ändern: 
 
    mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass';

## Development-User erstellen

Füge einen neuen User mit dem Namen Deines Betriebssystem-Logins hinzu:

    mysql> GRANT ALL PRIVILEGES ON *.* TO 'seb'@'localhost' IDENTIFIED BY 'password';

Stelle sicher, dass Du Dich anmelden kannst

    mysql> quit;
    $  mysql -p 
    Enter password:
    ...
    mysql>

## Datenbank und Tabellen erzeugen und mit Daten füllen

Erzeuge eine neue Datenbank `first` und darin die Tabelle `book`. 
Füge gleich ein paar Daten in die Tabelle ein.

    mysql> 
    
    CREATE DATABASE first;
    USE first;

    CREATE TABLE book (
        id BIGINT NOT NULL,
        author varchar(255),
        title varchar(255),
        primary key (id)
    );

    INSERT INTO book VALUES (1, "Joshua Bloch", "Effective Java (3rd)");
    INSERT INTO book VALUES (2, "Robert C. Martin", "Clean Code");
    
    SELECT * FROM book;