## Welcome to Cole Herman's Protfolio

![](https://github.com/Hermsmegerms/Portfolio/blob/gh-pages/photo4938553280880027961%20(1).jpg)

### Project Part 1

```markdown
Enviroserv.py

import grovepi

import math
import json
import time,sys
from grove_rgb_lcd import *
# Connect the Grove Temperature & Humidity Sensor Pro to digital port D4

# This example uses the blue colored sensor.

# SIG,NC,VCC,GND

sensor = 4  # The Sensor goes on digital port 4.



# temp_humidity_sensor_type

# Grove Base Kit comes with the blue sensor.

blue = 0    # The Blue colored sensor.

white = 1   # The White colored sensor.



while True:

    try:

        # This example uses the blue colored sensor. 

        # The first parameter is the port, the second parameter is the type of sensor.

        [temp,humidity] = grovepi.dht(sensor,blue)
	#convert C to F

	temp = ((temp/5)*9)+32

	#output to file
	outputData = {}
	outputData['weather'] = []
	outputData['weather'].append({
		'temperature': temp,
		'humidity' : humidity
		})
	with open ('EnviroDat.txt', 'w') as outfile :
		json.dump (outputData, outfile)
		outfile.write('\n')


        if math.isnan(temp) == False and math.isnan(humidity) == False:
		print("temp = %.02f F  humidity = %.02f%%"%(temp, humidity))
		setText("temp = %.02f F\nhumidity = %.02f%%"%(temp, humidity))



    except IOError:

        print ("Error")

```


### Project Part  2 You can access my Mongo DB scripts here. They were written in python
The data base and json files are to large to store on git hub but it can be accessed here:
[Link to data base files and Json](https://drive.google.com/drive/folders/1pjZoslM0Pyl7kXR36hkXia0RDeQBUZS9?usp=sharing)
```markdown  
import json
from bson import json_util
from pymongo import MongoClient

connection = MongoClient('localhost', 27017)
db = connection['myDB']
collection = db['myCollection']

def insert_document(document):
  try:
  result=collection.save(document)
  except ValidationError as ve:
  abort(400, str(ve))
  return result

def main():
  myDocument = { "keyName" : "test value data"}
  print insert_document(myDocument)

main()
```

### Project Part 3 Data Minning
I have a complete write up of my data mining projected here in a word document. This includes expansions ont he base project required for the Dat220 course.

[Document Download](https://github.com/Hermsmegerms/Portfolio/blob/gh-pages/Database%20analysis%20Dat220.docx) 


