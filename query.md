### 1-Selezionare tutti gli studenti nati nel 1990 (160) ###
- SELECT name, date_of_birth FROM students WHERE date_of_birth LIKE '1990%';

### 2-Selezionare tutti i corsi che valgono più di 10 crediti (479) ###
- SELECT name,cfu FROM courses WHERE cfu > 10;

### 3-Selezionare tutti gli studenti che hanno più di 30 anni ###
- SELECT * FROM students
WHERE (year(curdate()) - year(date_of_birth)) >= 30
AND (month(curdate()) - month(date_of_birth)) > 0
AND (day(curdate()) - day(date_of_birth)) > 0  
### soluzione fab ###
- select * from students where timestampdiff (year, `date_of_birth`, curdate()) > 30;

### 4-Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286) ###
- SELECT * FROM courses WHERE period = 'I semestre' AND year = 1;

### 5-Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21) 
- SELECT * FROM exams WHERE date = '2020-06-20' AND hour > '14:00:00';

### 6-Selezionare tutti i corsi di laurea magistrale (38) ###
- SELECT * FROM degrees WHERE level = 'magistrale';

### 7-Da quanti dipartimenti è composta l'università? (12) ###
- SELECT * FROM departments;
### oppure ###
select count(*) as 'total_departments'

### 8-Quanti sono gli insegnanti che non hanno un numero di telefono? (50) ###
- SELECT * FROM teachers WHERE phone IS null;
### oppure ###
- select count(*) teachers WHERE phone IS null;


