Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi **Dipartimenti** (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);

- ogni **Dipartimento** offre più **Corsi di Laurea** (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni **Corso di Laurea** prevede diversi **Corsi** (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni **Corso** può essere tenuto da diversi **Insegnanti**;
- ogni **Corso** prevede più appelli di **Esame**;
- ogni **Studente** è iscritto ad un solo Corso di Laurea;
- ogni **Studente** può iscriversi a più appelli di Esame;

per ogni appello d'**Esame** a cui lo **Studente** ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

# University DB

## Table name: `dipartimenti`

**columns**:

- id(BIGINT) - primary key - auto_increment - NOT NULL
- name: VARCHAR(255) - NOT NULL

## Table name: `corsi_di_laurea`

**columns**:

- id(BIGINT) - primary key - auto_increment - NOT NULL
- id_dipartimento (FK, BIGINT) - NOT NULL
- name: VARCHAR(255) - NOT NULL

## Table name: `corsi`

**columns**:

- id_corso di laurea (FK, BIGINT) - NOT NULL
- id(BIGINT) - primary key - auto_increment - NOT NULL
- name: VARCHAR(255) - NOT NULL

## Table name: `insegnanti`

**columns**:

- id (BIGINT) - primary key - auto_increment - NOT NULL
- name: VARCHAR(255) - NOT NULL
- lastname: VARCHAR(255) - NOT NULL
- email: VARCHAR(255) NOT NULL - UNIQUE

## Table name: `studenti`

**columns**:

- id (BIGINT) - primary key - auto_increment - NOT NULL
- name: VARCHAR(255) - NOT NULL
- lastname: VARCHAR(255) - NOT NULL
- email: VARCHAR(255) NOT NULL - UNIQUE
- id_dipartimento (FK, BIGINT) - NOT NULL
- id_corso_di_laurea (FK, BIGINT) - NOT NULL
- id_corso (FK, BIGINT) - NOT NULL

## Table name: `esame`

**columns**:

- id (BIGINT) - primary key - auto_increment - NOT NULL
- id_corso (FK, int)
- id_data: (FK, int)
- name: VARCHAR(255) - NOT NULL

# Tabelle ponte

## Table name: `iscrizioni_esame`

**columns**:

- id (BIGINT) - primary key - auto_increment - NOT NULL
- id_corso (FK, BIGINT) - NOT NULL
- id_data: (FK, BIGINT) - NOT NULL
- id_studente: (FK, BIGINT) - NOT NULL
- id_voto: (FK, tinyint) - NOT NULL

## Table name: `corsi_insegnanti`

**columns**:

- id (BIGINT) - primary key - auto_increment - NOT NULL
- id_corso - (FK, int)
- id_insegnante - (FK, int)
