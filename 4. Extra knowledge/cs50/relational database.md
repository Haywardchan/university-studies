##### SQL
CREATE, INSERT
SELECT 
UPDATE
DELETE, DROP

create table
CREATE TABLE table (column type, ...);

run sqlite3 in terminal by command:
```command
sqlite3 file.db
.mode csv 
import file.csv table_name
```

.schema
show the design of the table

SELECT
```SQL
SELECT columns//columnA,columnB FROM table;
```


we can include [[aggregate functions]] into a SQL query
eg AVG COUNT DISTINCT LOWER MAX MIN UPPER

Ie 
```SQL
SELECT DISTINCT(UPPER(column)) FROM table;
	SELECT COUNT(columns) FROM table;

Filter operations can be made:
WHERE LIKE ORDER BY LIMIT GROUP BY
```

Ie 
```SQL
SELECT columns//columnA,columnB FROM table LIMIT 10;
SELECT columns//columnA,columnB FROM table WHERE title LIKE "%OFFICE%";
```

//%wording% can be used to approximate wanted vlaues

DELETE
```SQL
DELETE FROM favorites WHERE title LIKE "%friends%";
```
UPDATE
```SQL
UPDATE table SET title="The office" WHERE title="Thevoffice";
```
selecting things separated by comma:
```SQL
SELECT genre FROM favourites WHERE titles LIKE "%comedy%";
```
alternative: 
```python
open("name.db","w").close()
db=cs50.SQL("sqlite:///name.db")

db.execute("CREATE TABLE shows (id INTEGER, title TEXT NOT NULL, PRIMARY KEY)")
db.execute("CREATE TABLE genres (show_id INTEGER, genre TEXT NOT NULL, FOREIGN KEY(show_id) REFERENCES shows(id)")

with open("name.csv","r") as file:
	reader=csv.DictReader(file)
	for row in reader:
		title=row["title"].strip().upper()
		show_id=db.execute("INSERT INTO shows (title) VALUES(?)", title)
		for genre in row["genres"].split(", ")
			db.execute("INSERT INTO genres (show_id, genre) VALUES(?, ?)")
```

```SQL
SELECT DISTINCT(title) FROM shows WHERE id IN (SELECT show_id FROM genres WHERE genres="comedy") ORDER BY title;
```
INSERT
```SQL
INSERT INTO genres (show_id, genre) VALUES(159, "comedy");
UPDATE shows SET title = "SEINFELD" WHERE title = "SEINFELD";
```
SQL in python
```python
import csv
from cs50 import SQL

db=SQL("sqlite:///favourites.db")

title=input("Title: ").strip()
rows=db.execute("SELECT COUNT(*) AS counter FROM favourites WHERE title LIKE ?",title)

row=row[0]

print(row["counter"])
```

5 data types in SQL
BLOB
INTEGER
NUMERIC
REAL
TEXT
```command
.timer on 
```
to check the run time of the query

creating an index can make it better than linear search:
```sql
CREATE INDEX "title_index" ON "shows" ("title");
CREATE INDEX name ON table (column, ...);
```
B-tree is slow for computation time.
JOIN
```SQL
SELECT title FROM people JOIN stars ON people.id=stars.person.id JOIN shows ON stars.show_id=shows.id WHERE name="STEVE CARELL"

SELECT title FROM people, stars, shows
WHERE people.id=stars.person_id
AND stars.show_id=shows.id
AND name="Steve Carell" 
```
creating indexes occupies space
comment of SQL 
```SQL
--i am a comment
```
SQL injection attacks
dont use quote in a database:
may cause injection attacks by using commenting andone more dash
Ie
```python
rows=db.execute(f"SELECT * FROM users WHERE username='{username}'--'' AND password='{password}'")
```
Race condition
both people may access the db at the same time and may cause alternating problems of running the code independently, thus, the following code have to be implemented
```python
db.execute("BEGIN TRANSACTION")
rows=db.execute("SELECT likes FROM posts WHERE id = "?", id);
likes =rows[0]["likes"]
db.execute("UPDATE posts SET likes = ? WHERE id = ?", likes +1, id);
db.execute("COMMIT")
```
