## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/Hermsmegerms/Portfolio/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Hermsmegerms/Portfolio/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

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


        if math.isnan(temp) == False and math.isnan(humidity) == False:
		print("temp = %.02f F  humidity = %.02f%%"%(temp, humidity))
		setText("temp = %.02f F\nhumidity = %.02f%%"%(temp, humidity))



    except IOError:

        print ("Error")

```
