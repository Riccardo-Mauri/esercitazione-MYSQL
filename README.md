CREAZIONE DI UN DATABASE DI ESERCITAZIONE

per creare un database  ho utilizato MAMP - PHPMYADMIN

ho eseguito in primo luogo il codice SQL

- CREATE DATABASE universita ( questo mi ha creato un DB con il nome 'universita').

al suo interno ho eseguito poi il codice PER creare TRE tabelle

in primo luogo ho creato la tabella 'studenti' 

-CREATE TABLE studenti (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(50) NOT NULL,
    cognome VARCHAR(50) NOT NULL,
    data_di_nascita DATE,
    email VARCHAR(100) NOT NULL UNIQUE
    );
Questo codice mi eseguirà la creazione della tabella 'studenti' ALL'INTERNO del database 'universita'

poi ho creato la tabella 'corsi'

-CREATE TABLE corsi (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome_corso VARCHAR(50) NOT NULL,
    docente VARCHAR(50) NOT NULL,
    crediti INT NOT NULL
);
Questo codice mi eseguirà la creazione della tabella 'corsi' ALL'INTERNO del database 'universita'

Ed infine ho creato la tabella 'iscrizioni'

-CREATE TABLE iscrizioni (
    id INT AUTO_INCREMENT PRIMARY KEY,
    studente_id INT NOT NULL,
    corso_id INT NOT NULL,
    data_iscrizione TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (studente_id) REFERENCES studenti(id) ON DELETE CASCADE,
    FOREIGN KEY (corso_id) REFERENCES corsi(id) ON DELETE CASCADE
);
Questo codice creerà una tabella PIVOT cioè una tabella in relazione tra le due tabelle 'studenti' e 'corsi'
