# entrega_1sergiolopez_mysql_coderhouse
entrega 1 sergio lopez rico 

nombre del proyecto 	juegos olimpicos tokio 
	
descripcion del proyecto; 	se toma este proyecto desde cero identificando 5 tablas atletas, entrenadores, medalla, inscripciones y equipos la idea de este proyecto es validar los juegos olimpicos de tokio haciedo el analisis de este evento idetificando la catidad de participates de diferentes las disciplinas y cantidad de medallas ganas por nacion 
}
objetivo; 	la idea de este proyecto es tomar cualquier base de datos en el trasbajo que este y poder analizarlos e implementar todos los conocimientos del curso y asi poder entregar un buen analisis del mismo según indicaciones 
![image](https://user-images.githubusercontent.com/96400527/146702428-f4a0a082-539c-4191-ad9a-91b9ea99257d.png)


					
medallas	clave	tipo	características		observaciones
					
Rank		int	nota null	auto increment	en esta tabla se identifica la cantidad de medallas ganadas por los equipos y nacionalidad donde se encontrará el Racing total de medallas ganadas, en esta se tomada como llave principal el campo Team/Nac
Team/Nac	PK	varchar (50)	not null		
Gold		int	not null		
Silver		int	not null		
Bronze		int	not null		
Total		int	not null		
Rank by Total		int	not null		
					
					
					
					
entrenador	clave	tipo	características		observaciones
					
Ñame		varchar (50)	not null		en esta tabla encontraremos el detalle del entrenador y la nacionalidad que esta participado asimismo la diciplina
NOC	mul	varchar (50)	not null		
Discipline	pk	varchar (30)	not null		
Event		varchar (20)	not null		
					
					
					
					
atletas	clave	tipo 	características		observaciones
					
Name		varchar (50)	not null		se encontrar los participantes de acuerdo a su nacionalidad y disciplina
NOC	mul	varchar (50)	not null		
Discipline	pk	varchar (50)	not null		
					
					
					
					
equipos	clave	tipo 	características		observaciones
					
Name		varchar (50)	not null		esta tabla se encontrará los nombres del equipo nacionalidad y disciplina donde se relaciona de acuerdo a las tablas entrenadores y atletas
Discipline	pk	varchar (50)	not null		
NOC	mul	varchar (50)	not null		
Event		varchar (50)	not null		
					
					
					
					
inscripciones	clave	tipo	características		observaciones
					
Discipline	pk	varchar (50)	no null		a cada diciplina se relaciona una cantidad de participantes establecida por los juegos olímpicos donde se relaciona la cantidad de atletas que estarán en cada evento
Female		int	no null		
Male		int	no null		
Total		int	no null		
![image](https://user-images.githubusercontent.com/96400527/146702472-7fc2a70e-4c9c-48bd-a524-64a5c3b49d6a.png)


								
								
								
			atletas				entrenador	
								
			Name				Ñame	
			NOC				NOC	
		pk	Discipline				Discipline	pk
							Event	
								
								
					inscripciones			
								
					Discipline	pk		
					Female			
					Male			
					Total			
								
								
								
			equipos				medallas	
								
			Name				Rank	
		pk	Discipline				Team/Nac	pk
			NOC				Gold	
			Event				Silver	
							Bronze	
							Total	
							Rank by Total	
![image](https://user-images.githubusercontent.com/96400527/146702503-24799f5a-375a-4e59-8275-2c9658ad160e.png)




codigo creacion base de datos en mysql
CREATE DATABASE POYECTO_FINAL_2;


CREATE TABLE `ATLETAS` (
  `ATLETA_id` smallint unsigned NOT NULL AUTO_INCREMENT,
  `NAME` varchar(50) NOT NULL,
  `NOC` varchar(50) NOT NULL,
  `DISCIPLINE` varchar(50) NOT NULL,
  `ID_ENTRENADOR` varchar(100) NOT NULL,
  `ID_EQUIPOS` varchar(100) NOT NULL,
  PRIMARY KEY (`ATLETA_id`),
  KEY `idx_DICIPLINA_NOC` (`DISCIPLINE`)
) ENGINE=InnoDB AUTO_INCREMENT=201 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

DESCRIBE atletas;


CREATE TABLE `ENTRENADORES` (
  `ID_ENTRENADOR` smallint unsigned NOT NULL AUTO_INCREMENT,
  `NAME_ENTRENADOR` varchar(50) NOT NULL,
  `NOC` varchar(50) NOT NULL,
  `DISCIPLINE` varchar(50) NOT NULL,
  `EVENTO` varchar(25) NOT NULL,
    PRIMARY KEY (`ID_ENTRENADOR`),
    KEY `idx_DICIPLINA_ENTRENADOR` (`DISCIPLINE`)
) ENGINE=InnoDB AUTO_INCREMENT=201 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;


CREATE TABLE `EQUIPOS` (
  `ID_EQUIPOS` smallint unsigned NOT NULL AUTO_INCREMENT,
  `NAME` varchar(50) NOT NULL,
  `NOC` varchar(50) NOT NULL,
  `DISCIPLINE` varchar(50) NOT NULL,
   `EVENTO` varchar(50) NOT NULL,
  PRIMARY KEY (`ID_EQUIPOS`),
  KEY `idx_DICIPLINA_EQUIPOS` (`DISCIPLINE`)
) ENGINE=InnoDB AUTO_INCREMENT=201 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;




CREATE TABLE `INSCRIPCIONES` (
  `ID_INSCRIPCIONES` smallint unsigned NOT NULL AUTO_INCREMENT,
	`DISCIPLINE` varchar(45) NOT NULL,
    `FEMALE` int NOT NULL,
    `MALE` INT NOT NULL,
	`TOTAL` INT NOT NULL,
  PRIMARY KEY (`ID_INSCRIPCIONES`),
  KEY `idx_DICIPLINA_INSCIPCIONES` (`DISCIPLINE`)
) ENGINE=InnoDB AUTO_INCREMENT=201 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;



CREATE TABLE `MEDALLAS` (
  `MEDALLAS_id` smallint unsigned NOT NULL AUTO_INCREMENT,
  `RANK` varchar(45) NOT NULL,
  `TEAM/NAC` varchar(45) NOT NULL,
  `GOLD` varchar(45) NOT NULL,
  `SILVER` varchar(45) NOT NULL,
  `BRONCE` varchar(45) NOT NULL,
  `TOTAL` varchar(45) NOT NULL,
  `RANK BY TOTAL` varchar(45) NOT NULL,  
  PRIMARY KEY (`MEDALLAS_id`),
  KEY `idx_DICIPLINA_MEDALLAS` (`TEAM/NAC`)
) ENGINE=InnoDB AUTO_INCREMENT=201 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;



