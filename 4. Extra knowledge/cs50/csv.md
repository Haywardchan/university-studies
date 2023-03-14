it is a flat database.
portable between mac, pc, linux.
reading in csv
```python
import csv
with open("favourites.csv", "r") as file:
	reader=csv.reader(file)
	next(reader)
	for row in reader:
		print(row[1])
```
usage of DictReader
```python
import csv
with open("favourites.csv", "r") as file:
	reader=csv.DictReader(file)
	for row in reader:
		print(row["title"])
```
remove duplicates:
```python
import csv
titles=[]
with open("favourites.csv", "r") as file:
	reader=csv.DictReader(file)
	for row in reader:
		if not row["title"] in titles:
			titles.append(row["titles"])
for title in titles:
	print(titles)
```
remove space and capitalization:
```python
import csv
titles=[]
with open("favourites.csv", "r") as file:
	reader=csv.DictReader(file)
	for row in reader:
		title = row["title"].strip().upper()
		if not row["title"] in titles:
			titles.append(row["titles"])
for title in titles:
	print(titles)
```
set can be used as no duplicate can exist in sets:
```python
import csv
titles=set()
with open("favourites.csv", "r") as file:
	reader=csv.DictReader(file)
	for row in reader:
		title = row["title"].strip().upper() #removing unwanted materials
		titles.add(title)
for title in sorted(titles): #sort the data
	print(titles)
```
dictionaries can be used to count number of data:
```python
import csv
titles={}
with open("favourites.csv", "r") as file:
	reader=csv.DictReader(file)
	for row in reader:
		title = row["title"].strip().upper() 
		\\\
		if title in titles:
			titles[title]+=1
		else:
			titles[title]=1 #initialization
		\\\or we can write it like this\\\
		if not title in titles:
			titles[title]=0
		titles[title]+=1 #initialization
		\\\
def function get_return(title):
	return titles[title]
for title in sorted(titles): '''sorted by key''' \\\or 
we def function get_return '''to get the number od counts'''
for title in sorted(titles, key=get_value, reverse=True):
\\\or we use lambda 
for title in sorted(titles, key=lambda title:titles[title], reverse=True):
	print(titles, titles[title])
```
to only search the count of one specific key:
```python
import csv
counter=0
with open("favourites.csv", "r") as file:
	reader=csv.DictReader(file)
	for row in reader:
		title = row["title"].strip().upper() 
		if title=="THE OFFICE": \\\to be more general
		if "OFFICE" in title: 
 			counter+=1
print(f"Number of people who like the office:{counter}")
```

##### [[wildcard characters]]
. any character
.* 0 or more character
.+ 1 or more character
? optional
^ start of input
$ end of input

[[regular expression library]] can be used:
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
