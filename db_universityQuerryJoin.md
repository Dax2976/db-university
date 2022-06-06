# QUERY JOINS:

## 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT COUNT(*) FROM `students` INNER JOIN `degrees` ON `degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';


## 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT * FROM `departments` INNER JOIN `degrees` ON `departments` . `id` = `degrees` . `department_id` WHERE `departments` . `name` = "Dipartimento di Neuroscienze" AND `level` = "magistrale";

## 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT * 
FROM `course_teacher` 
INNER JOIN `courses` 
ON `course_teacher` . `course_id` =  `courses` . `id`
INNER JOIN `teachers` ON `course_teacher` . `teacher_id` = `teachers` . `id`
WHERE `teachers` . `id` = 44;

## 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT * 
FROM `students` 
INNER JOIN `degrees` 
ON `students` . `degree_id`= `degrees` . `id`
INNER JOIN `departments` ON `degrees` . `department_id` = `departments` . `id`
ORDER BY `students` . `surname`, `students` . `name`;



## 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT COUNT(*)
FROM `degrees` 
INNER JOIN `courses` 
ON  `courses` . `degree_id` = `degrees` . `id`
INNER JOIN `course_teacher` ON `course_teacher` . `course_id` = `courses` . `id`
INNER JOIN `teachers` ON `course_teacher` . `teacher_id` = `teachers` . `id`
ORDER BY `degrees`.`id`;




## 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

--forse sbagliata--


SELECT `teachers` . * 
FROM `teachers` 
INNER JOIN `course_teacher`
ON `course_teacher` . `teacher_id` = `teachers` . `id`
INNER JOIN `courses`
ON `course_teacher` . `course_id` = `courses` . `id`
INNER JOIN `degrees`
ON `courses` . `degree_id` = `degrees` . `id`
INNER JOIN `departments`
ON `degrees` . `department_id`= `departments` . `id`
WHERE `departments` . `name` = "Dipartimento di Matematica";
