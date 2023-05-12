### 1-Selezionare tutti gli studenti nati nel 1990 (160) ###
- show databases;
- use uni_boolean;
- show tables;
- describe students;
- SELECT name, date_of_birth FROM students WHERE date_of_birth LIKE '1990%';

### Selezionare tutti i corsi che valgono più di 10 crediti (479) ###
- show databases;
- use uni_boolean;
- show tables;
- describe students;
- SELECT name,cfu FROM courses WHERE cfu > 10;