For Educational Purposes
=========================
SpringBoot web example with JDBCTemplate functionality. Will need MySQL server (Download both MySQL Community and MySQL WorkBench to operate)

Not all pages are functional, with the intention being that the learner would use the working Teachers page to complete the Courses and Students Pages.

N.B. There is a supposed error in the updating of records when a new teacher is inserted. This is a challenge to find the cause of this ;-) 

Main intention is to show the scale and relationship between the various aspects, such as POM file, DAO, Controller and View files. 

Also shows how ThymeLeaf makes it possible to allow for interaction between Java and HTML.  

To show page, run program in IDE and type http://localhost:8080/teachers into your browser.

Script to set up MySQL DB
=========================


Create DATABASE classroster;

DROP TABLE IF EXISTS `teacher`;

CREATE TABLE `teacher` (
  `id` int NOT NULL AUTO_INCREMENT,
  `firstName` varchar(30) NOT NULL,
  `lastName` varchar(50) NOT NULL,
  `specialty` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`id`)
)
/* Populating table with some values */
INSERT INTO `teacher` VALUES (1,'Shane','Keefe','Maths'),(2,'Mary','Lyons','History'),(3,'Eddie','Donovan','Geography'),(4,'Brian','Eno','Music'),(5,'Mr.','Miyagi','Wax on, Wax off'),(6,'Eugene','Regan','Cowbell'),(7,'John','Wick','Hitman'),(8,'lo','li','il'),(9,'Lautaro','Martinez','Footie');

CREATE TABLE `course` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(50) NOT NULL,
  `description` varchar(255) DEFAULT NULL,
  `teacherId` int NOT NULL,
  PRIMARY KEY (`id`),
  KEY `teacherId` (`teacherId`),
  CONSTRAINT `course_ibfk_1` FOREIGN KEY (`teacherId`) REFERENCES `teacher` (`id`)
) 

INSERT INTO `course` VALUES (1,'Quadratics','Intro',1),(2,'Flight of the Earls','Intro',2);



