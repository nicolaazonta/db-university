# Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT `students`.`name` AS `stud_name`, `students`.`surname` AS `stud_surname`, `degrees`.`name` AS `degree_name`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

# Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT `degrees`.`name` AS `deg_name`, `degrees`.`level` as `deg_type`, `departments`.`name`AS `department_name`
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = 'magistrale'
AND `departments`.`name` = 'Dipartimento di Neuroscienze';

# Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT `courses`.`name` AS `course_name`, `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teachers_surname`
FROM `course_teacher`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
WHERE `teachers`.`id` = 44;

# Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT `students`.`surname` AS `stud_surname`,`students`.`name` AS `stud_name`,  `degrees`.`name` AS `deg_name` , `degrees`.`level` AS `deg_level`, `departments`.`name` AS `department`, `departments`.`website` AS `website`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `stud_surname`, `stud_name`;

# Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti # dopo correzione fab
SELECT `degrees`.`name` AS `degrees_name`, `courses`.`name` AS `courses_name`, `teachers`.`name` AS `teach_name`, `teachers`.`surname` AS `teach_surname`
FROM `degrees`
JOIN `courses` ON `degrees`.`id` = `courses`.`id`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`;

# Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54) # dopo correzione fab
SELECT DISTINCT `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname` , `teachers`.`email` AS `email`, `departments`.`name` AS `department` FROM `teachers` JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id` JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id` JOIN `departments` on `degrees`.`department_id` = `departments`.`id` WHERE `departments`.`name` = 'Dipartimento di Matematica';

# BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami # dopo correzione fab
SELECT `students`.`id`, `exam_student`.`exam_id` AS `exam_id`, `students`.`surname` AS `student_surname`, `courses`.`id` AS `course_id`, 
COUNT(`exam_student`.`vote`) AS `attempts_number`,
MAX(`exam_student`.`vote`) AS `hightest_vote`
FROM `students`
JOIN `exam_student` ON `students`.`id` = `exam_student`.`student_id`
JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id`
JOIN `courses` on `exams`.`course_id` = `courses`.`id`
GROUP BY `students`.`id`, `courses`.`id`
HAVING `hightest_vote` >= 18;







