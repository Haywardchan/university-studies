```python
import csv
import re
counter=0
///we can ask for input:
title = input("Title: ").strip().upper()
with open("favourites.csv", "r") as file:
	reader=csv.DictReader(file)
	for row in reader:
		if row["title"].strip().upper()==title: 
			counter += 1
print(counter)
```