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


-----------------------------------------------------------------------------------------------------------------------------------

Dopo fatto ciò ho popolato le tabelle con dei dati fittizi abbastanza realistici per poi fare delle prove con delle query

per la tabelle ho utilizzato il comando INSERT INTO nome della tabella (colonna in cui inserire i dati, nome della seconda colonna in cui inserire i dati, ecc)
                                        VALUES perché ho inserito valori multipli 
                                        ('valore da inserire nella PRIMA colonna', ?valore da inserire nella SECONDA colonna', ecc ecc N:B: i numeri senza apici!);

                                        
Valori che ho inserito nella tabella studenti:
![Immagine 2025-02-20 154410](https://github.com/user-attachments/assets/6641e8b1-dea5-449b-8401-d63aa81bf645)


Valori che ho inserito nella tabella corsi:

![Immagine 2025-02-20 154637](https://github.com/user-attachments/assets/a95cb6cf-1ea1-4325-ba31-59e2949fad7f)


Valori che ho inserito nella tabella iscrizioni:

![Immagine 2025-02-20 154703](https://github.com/user-attachments/assets/a9667fe7-6da9-475d-8e0a-caadc3ca0b86)

-----------------------------------------------------------------------------------------------------------------------------------
Dopo un controllo fatto dal dipartimento si nota che il cognome del docente di Matematica è sbagliato e va corretto quindi si esegue la query di UPDATE per AGGIORNARE la tabella corsi dove è presente l'errore.
UPDATE corsi
SET docente = 'Nuovo Nome' -> in questo caso 'Asia Altalenati'
WHERE id = 2;
Questo andrà ad aggiornare il cognome del docente dell ID 2 che è in questo caso quello di Matematica ma si potrebbe pure aggiornare selezionando direttamente la voce 'Matematica' SE non conosciamo l'ID del docente.

![Immagine 2025-02-21 180403](https://github.com/user-attachments/assets/510072a6-0482-4465-a267-b1501d99644b)

                                    
