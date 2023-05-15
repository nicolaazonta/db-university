# Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT `students`.`name` as `stud_name`, `students`.`surname` as `stud_surname` from `students` join `degrees` on `students`.`degree_id` = `degrees`.`id` where `degrees`.`name`= 'Corso di Laurea in Economia';

# Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze





