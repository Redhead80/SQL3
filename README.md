## Новая схема БД SQL 

![](https://github.com/Redhead80/SQL3/blob/main/database_diagram2.png)

## Задание 2. Команды SQL которые были использованы для создания БД по заданию 2.

```sql
CREATE TABLE IF NOT EXISTS Исполнители (
	id_artist SERIAL PRIMARY key,
	Имя VARCHAR(50) NOT NULL unique,
	id_genre INTEGER NOT NULL unique
);
CREATE TABLE IF NOT EXISTS Альбомы (
	id_album SERIAL PRIMARY key,
	Название_альбома VARCHAR(100)  NOT NULL, 
	Год_выпуска INTEGER NOT NULL,
	id_artist INTEGER REFERENCES Исполнители(id_artist) NOT NULL
);
CREATE TABLE IF NOT EXISTS Треки (
	id_track SERIAL PRIMARY key,
	Название_трека VARCHAR(100)  NOT NULL,
	Длительность INTEGER NOT NULL,
	id_album INTEGER REFERENCES Альбомы(id_album) NOT NULL
);
CREATE TABLE IF NOT EXISTS Жанры (
	id_genre SERIAL PRIMARY key,
	Название_жанра VARCHAR(100)  NOT NULL UNIQUE
);
ALTER TABLE Исполнители ADD CONSTRAINT id_genre FOREIGN KEY (id_genre) REFERENCES Жанры(id_genre);
```
## Задание 3. Команды SQL для изменения БД.

```sql
"Задание 3. Изменение БД"

ALTER TABLE Исполнители DROP COLUMN id_genre;

CREATE TABLE IF NOT EXISTS Жанры_Исполнители (
	id_genre INTEGER REFERENCES Жанры(id_genre) NOT NULL,
	id_artist INTEGER REFERENCES Исполнители(id_artist) NOT NULL
);	
CREATE TABLE IF NOT EXISTS Альбомы_Исполнители (
	id_album INTEGER REFERENCES Альбомы(id_album) NOT NULL,
	id_artist INTEGER REFERENCES Исполнители(id_artist) NOT NULL
);	
CREATE TABLE IF NOT EXISTS Сборники (
	id_collection SERIAL PRIMARY key,
	Название_сборника VARCHAR(100)  NOT NULL, 
	Год_выпуска INTEGER NOT NULL,
	id_track INTEGER REFERENCES Треки(id_track) NOT NULL,
	id_album INTEGER REFERENCES Альбомы(id_album) NOT NULL
);
```
