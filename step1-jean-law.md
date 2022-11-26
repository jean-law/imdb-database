# Jia Jean LAW INF553 Project Step 1
## Loading the data

CREATE DATABASE "imdb-tables"

\connect imbd-tables
SET CLIENT_ENCODING TO 'utf8';



CREATE TABLE person (
  id VARCHAR(10),
  name VARCHAR(200),
  gender CHAR(1)
);

\copy person FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\person.csv' CSV header;


CREATE TABLE aka_name (
  id VARCHAR(10),
  person_id VARCHAR(200),
  name VARCHAR(500)
);

\copy aka_name FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\aka_name.csv' CSV header;



CREATE TABLE movie (
  id VARCHAR(10),
  title VARCHAR(500),
  kind_id VARCHAR(1),
  production_year VARCHAR(4),
  episode_of_id VARCHAR(10),
  season_nr VARCHAR(5),
  episode_nr VARCHAR(10),
  series_years VARCHAR(20)
);

\copy movie FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\movie.csv' CSV header;



CREATE TABLE aka_title (
  id VARCHAR(10),
  movie_id VARCHAR(10),
  title VARCHAR(1000),
  kind_id VARCHAR(1),
  production_year VARCHAR(4),
  episode_of_id VARCHAR(10),
  season_nr VARCHAR(5),
  episode_nr VARCHAR(10),
  note VARCHAR(100)
);

\copy aka_title FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\aka_title.csv' CSV header;


CREATE TABLE cast_info (
  id VARCHAR(10),
  person_id VARCHAR(10),
  movie_id VARCHAR(10),
  person_role_id VARCHAR(10),
  note VARCHAR(1000),
  role_id VARCHAR(10)
);

\copy cast_info FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\cast_info.csv' CSV header;


CREATE TABLE char_name (
  id VARCHAR(10),
  name VARCHAR(500)
);

\copy char_name FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\char_name.csv' CSV header;

CREATE TABLE comp_cast_type (
  id CHAR(1),
  kind VARCHAR(20)
);

\copy comp_cast_type FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\comp_cast_type.csv' CSV header;

CREATE TABLE company (
  id VARCHAR(10),
  name VARCHAR(300),
  country_code VARCHAR(10)
);

\copy company FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\company.csv' CSV header;


CREATE TABLE company_type(
	id CHAR(1),
	kind VARCHAR(100)
	);

\copy company_type FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\company_type.csv' CSV header;

CREATE TABLE complete_cast(
	id VARCHAR(10),
	movie_id VARCHAR(10),
	subject_id VARCHAR(10),
	status_id VARCHAR(10)
	);
	
\copy complete_cast FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\complete_cast.csv' CSV header;


CREATE TABLE info_type(
	id VARCHAR(10),
	info VARCHAR(500)
	);
	
\copy info_type FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\info_type.csv' CSV header;

CREATE TABLE keyword(
	id VARCHAR(10),
	keyword VARCHAR(500)
	);
	
\copy keyword FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\keyword.csv' CSV header;

CREATE TABLE link_type(
	id VARCHAR(10),
	link VARCHAR(500)
	);
	
\copy link_type FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\link_type.csv' CSV header;

CREATE TABLE movie_company(
	id VARCHAR(10),
	movie_id VARCHAR(10),
	company_id VARCHAR(10),
	company_type_id VARCHAR(10),
	note VARCHAR(500)
	);
	
\copy movie_company FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\movie_company.csv' CSV header;

CREATE TABLE movie_info(
	id VARCHAR(10),
	movie_id VARCHAR(10),
	info_type_id VARCHAR(10),
	info VARCHAR(100000),
	note VARCHAR(10000)
	);
	
\copy movie_info FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\movie_info.csv' CSV header;

CREATE TABLE movie_keyword(
	id VARCHAR(10),
	movie_id VARCHAR(10),
	keyword_id VARCHAR(10)
	);
	
\copy movie_keyword FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\movie_keyword.csv' CSV header;

CREATE TABLE movie_rating(
	id VARCHAR(10),
	movie_id VARCHAR(10),
	info_type_id VARCHAR(10),
	info VARCHAR(10)
	);
	
\copy  movie_rating FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\movie_rating.csv' CSV header;

CREATE TABLE movie_link(
	id VARCHAR(10),
	movie_id VARCHAR(10),
	linked_movie_id VARCHAR(10),
	link_type_id VARCHAR(10)
	);
	
\copy movie_link FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\movie_link.csv' CSV header;


CREATE TABLE movie_type(
	id VARCHAR(10),
	kind VARCHAR(500)
	);
	
\copy movie_type FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\movie_type.csv' CSV header;

CREATE TABLE person_info(
	id VARCHAR(10),
	person_id VARCHAR(10),
	info_type_id VARCHAR(10),
	info VARCHAR(10000),
	note VARCHAR(500)
	);
	
\copy person_info FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\person_info.csv' CSV header;

CREATE TABLE role_type(
	id VARCHAR(10),
	role VARCHAR(500)
	);
	
\copy role_type FROM 'C:\Users\lawji\Documents\data\INF553\imdb-tables\role_type.csv' CSV header;


## Adding constraints

ALTER TABLE role_type
    ADD CONSTRAINT role_type_id PRIMARY KEY (id);

ALTER TABLE person_info
    ADD CONSTRAINT person_info_id PRIMARY KEY (id);

ALTER TABLE movie_type
    ADD CONSTRAINT movie_type_id PRIMARY KEY (id);

ALTER TABLE movie_rating
    ADD CONSTRAINT movie_rating_id PRIMARY KEY (id);

ALTER TABLE movie_link
    ADD CONSTRAINT movie_link_id PRIMARY KEY (id);

ALTER TABLE movie_keyword
    ADD CONSTRAINT movie_keyword_id PRIMARY KEY (id);

ALTER TABLE movie_info
    ADD CONSTRAINT movie_info_id PRIMARY KEY (id);

ALTER TABLE movie_company
    ADD CONSTRAINT movie_company_id PRIMARY KEY (id);

ALTER TABLE link_type
    ADD CONSTRAINT link_type_id PRIMARY KEY (id);

ALTER TABLE keyword
    ADD CONSTRAINT keyword_id PRIMARY KEY (id);

ALTER TABLE info_type
    ADD CONSTRAINT info_type_id PRIMARY KEY (id);

ALTER TABLE complete_cast
    ADD CONSTRAINT complete_cast_id PRIMARY KEY (id);

ALTER TABLE company_type
    ADD CONSTRAINT company_type_id PRIMARY KEY (id);

ALTER TABLE company
    ADD CONSTRAINT company_id PRIMARY KEY (id);

ALTER TABLE comp_cast_type
    ADD CONSTRAINT comp_cast_type_id PRIMARY KEY (id);

ALTER TABLE char_name
    ADD CONSTRAINT char_name_id PRIMARY KEY (id);

ALTER TABLE cast_info
    ADD CONSTRAINT cast_info_id PRIMARY KEY (id);

ALTER TABLE aka_title
    ADD CONSTRAINT aka_title_id PRIMARY KEY (id);

ALTER TABLE movie
    ADD CONSTRAINT movie_id PRIMARY KEY (id);

ALTER TABLE aka_name
    ADD CONSTRAINT aka_name_id PRIMARY KEY (id);

ALTER TABLE person
    ADD CONSTRAINT person_id PRIMARY KEY (id);

ALTER TABLE movie
ALTER COLUMN title SET NOT NULL,
ALTER COLUMN production_year SET NOT NULL;

*//Comment: Error message obtained "ERROR:  column "production_year" contains null values" -> real-world error*

ALTER TABLE aka_name
    ADD CONSTRAINT person_id FOREIGN KEY (person_id) REFERENCES person (id);

ALTER TABLE movie
    ADD CONSTRAINT kind_id FOREIGN KEY (kind_id) REFERENCES movie_type (id),
    ADD CONSTRAINT episode_of_id FOREIGN KEY (episode_of_id) REFERENCES movie (id);

ALTER TABLE person_info
    ADD CONSTRAINT person_id FOREIGN KEY (person_id) REFERENCES person (id),
    ADD CONSTRAINT info_type_id FOREIGN KEY (info_type_id) REFERENCES info_type (id);

ALTER TABLE movie_company
    ADD CONSTRAINT movie_id FOREIGN KEY (movie_id) REFERENCES movie (id),
    ADD CONSTRAINT company_type_id FOREIGN KEY (company_type_id) REFERENCES company_type (id),
    ADD CONSTRAINT company_id FOREIGN KEY (company_id) REFERENCES company (id);

ALTER TABLE aka_title
    ADD CONSTRAINT episode_of_id FOREIGN KEY (episode_of_id) REFERENCES movie (id),
    ADD CONSTRAINT kind_id FOREIGN KEY (kind_id) REFERENCES movie_type (id);

ALTER TABLE cast_info
    ADD CONSTRAINT person_id FOREIGN KEY (person_id) REFERENCES person (id),
    ADD CONSTRAINT person_role_id FOREIGN KEY (person_role_id) REFERENCES char_name (id),
    ADD CONSTRAINT role_id FOREIGN KEY (role_id) REFERENCES role_type (id),
    ADD CONSTRAINT movie_id FOREIGN KEY (movie_id) REFERENCES movie (id);

ALTER TABLE complete_cast
    ADD CONSTRAINT movie_id FOREIGN KEY (movie_id) REFERENCES movie (id),
    ADD CONSTRAINT status_id FOREIGN KEY (status_id) REFERENCES comp_cast_type (id),
    ADD CONSTRAINT subject_id FOREIGN KEY (subject_id) REFERENCES comp_cast_type (id);

ALTER TABLE movie_rating
    ADD CONSTRAINT movie_id FOREIGN KEY (movie_id) REFERENCES movie (id),
    ADD CONSTRAINT info_type_id FOREIGN KEY (info_type_id) REFERENCES info_type (id);

*//Comment: these two foreign keys were not mentioned explicitly in the instructions but i included them because it seemed logical; did not get any errors</span>*


ALTER TABLE movie_info
    ADD CONSTRAINT movie_id FOREIGN KEY (movie_id) REFERENCES movie (id),
    ADD CONSTRAINT info_type_id FOREIGN KEY (info_type_id) REFERENCES info_type (id);

ALTER TABLE movie_keyword
    ADD CONSTRAINT movie_id FOREIGN KEY (movie_id) REFERENCES movie (id),
    ADD CONSTRAINT keyword_id FOREIGN KEY (keyword_id) REFERENCES keyword (id);

ALTER TABLE movie_link
    ADD CONSTRAINT movie_id FOREIGN KEY (movie_id) REFERENCES movie (id),
    ADD CONSTRAINT link_type_id FOREIGN KEY (link_type_id) REFERENCES link_type (id),
    ADD CONSTRAINT linked_movie_id FOREIGN KEY (linked_movie_id) REFERENCES movie (id);


## SQL
### 1. Find the pairs of (movie title, actor name) such that the actor played in the movie.

SELECT DISTINCT movie.title,person.name FROM movie JOIN cast_info ON movie.id = cast_info.movie_id 

JOIN role_type ON role_type.id = cast_info.role_id 

JOIN person ON person.id = cast_info.person_id

WHERE role_type.role = 'actor'

OR role_type.role = 'actress';

### 2. Find the person names and movie titles such that the person has played in the movie a character called Amber.

SELECT DISTINCT movie.title,person.name FROM movie JOIN cast_info ON movie.id = cast_info.movie_id 

JOIN role_type ON role_type.id = cast_info.role_id 

JOIN person ON person.id = cast_info.person_id

JOIN char_name ON cast_info.person_role_id = char_name.id
WHERE role_type.role = 'actor'

AND char_name.name LIKE '%Amber%';


### 3. Find the title and the year of production of each movie in which Nicolas Cage played. The lines for which the production year is unavailable should not be displayed. Order the results by year in descending order, then by title in ascending order.

SELECT DISTINCT movie.title, movie.production_year FROM movie JOIN cast_info ON movie.id = cast_info.movie_id 

JOIN person ON person.id = cast_info.person_id

WHERE person.name = 'Cage, Nicolas'

AND movie.production_year IS NOT NULL
 
ORDER BY movie.production_year DESC,

movie.title ASC;


### 4. Find the name of all the people that have played in a movie they directed, and order them by their names (increasing alphabetical order).

SELECT DISTINCT person.name FROM person JOIN cast_info AS cast_info_1 ON person.id = cast_info_1.person_id 

JOIN cast_info AS cast_info_2 ON person.id = cast_info_2.person_id 

JOIN role_type AS role_type_1 ON role_type_1.id = cast_info_1.role_id 

JOIN role_type AS role_type_2 ON role_type_2.id = cast_info_2.role_id 

WHERE role_type_1.role = 'actor'

AND role_type_2.role = 'director'

AND cast_info_1.person_id = cast_info_2.person_id 

ORDER BY person.name ASC;

### 5. Find the titles of the movies that have only 1, 9 and 10 as rating.

SELECT DISTINCT movie.title FROM movie_rating 

JOIN movie ON movie_rating.movie_id = movie.id

WHERE info_type_id='99' AND info LIKE '_.......__';

### 6. Find the titles of the twenty movies having the largest number of directors and their number of directors,
ordered by their number of directors in decreasing order.

SELECT DISTINCT movie.title, COUNT(cast_info.id) FROM movie JOIN cast_info ON movie.id = cast_info.movie_id

JOIN role_type ON role_type.id = cast_info.role_id

WHERE role_type.role = 'director'

GROUP BY movie.title

ORDER BY COUNT(cast_info.id) DESC

LIMIT 20;


### 7. Find the average number of episode Layla Covino played in, in her active years. A year is active if she plays in at least one movie produced that year.


SELECT AVG(count) FROM 

(SELECT COUNT(movie.id), movie.production_year FROM movie JOIN cast_info ON movie.id = cast_info.movie_id 

JOIN person ON person.id = cast_info.person_id 

WHERE person.name = 'Covino, Layla'

GROUP BY movie.production_year) AS count; 


## Updates
### Creating relation

CREATE TABLE vote_distribution (
  id VARCHAR(10),
  one CHAR(1),
  two CHAR(1),
  three CHAR(1),
  four CHAR(1),
  five CHAR(1),
  six CHAR(1),
  seven CHAR(1),
  eight CHAR(1),
  nine CHAR(1),
  ten CHAR(1)
);

### Inserting IDs of tuples which correspond to vote distributions
INSERT INTO vote_distribution (id)  

SELECT id

 FROM movie_rating
 
 WHERE movie_rating.info_type_id='99';

### Update command

UPDATE vote_distribution 

SET one = substring(movie_rating.info from 1 for 1),

two = substring(movie_rating.info from 2 for 1),

three = substring(movie_rating.info from 3 for 1),

four = substring(movie_rating.info from 4 for 1),

five = substring(movie_rating.info from 5 for 1),

six = substring(movie_rating.info from 6 for 1),

seven = substring(movie_rating.info from 7 for 1),

eight = substring(movie_rating.info from 8 for 1),

nine = substring(movie_rating.info from 9 for 1),

ten = substring(movie_rating.info from 10 for 1)

FROM movie_rating 

WHERE movie_rating.id = vote_distribution.id;