# Contare quanti iscritti ci sono stati ogni anno
SELECT COUNT(*) AS `students_per_year`, YEAR(`enrolment_date`) AS `year`
FROM `students`
GROUP BY `year`;

# Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT COUNT(*) AS `teacher_per_building`, `office_address`
FROM `teachers`
GROUP BY `office_address`;

# Calcolare la media dei voti di ogni appello d'esame
SELECT AVG(`vote`) AS `average_vote` , `exam_id` 
FROM `exam_student`
GROUP BY `exam_id`;

# Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT COUNT(`degrees`.`name`) as `degrees`, `degrees`.`department_id`, `departments`.`name`
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
GROUP BY `department_id`
