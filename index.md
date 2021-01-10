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

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.


```markdown
TEST
Skip to content
Search or jump to…

Pull requests
Issues
Marketplace
Explore
 
@Hermsmegerms 
Learn Git and GitHub without any code!
Using the Hello World guide, you’ll start a branch, write comments, and open a pull request.


Hermsmegerms
/
Portfolio
1
00
Code
Issues
Pull requests
Actions
Projects
Wiki
Security
Insights
Settings
Portfolio/Enviroserv.py /
@Hermsmegerms
Hermsmegerms Rename Enviroserv to Enviroserv.py
Latest commit 56ea5e5 3 minutes ago
 History
 1 contributor
121 lines (65 sloc)  2.77 KB
  
#!/usr/bin/env python

#

# GrovePi Example for using the Grove Temperature & Humidity Sensor Pro 

# (http://www.seeedstudio.com/wiki/Grove_-_Temperature_and_Humidity_Sensor_Pro)

#

# The GrovePi connects the Raspberry Pi and Grove sensors.  

# You can learn more about GrovePi here:  http://www.dexterindustries.com/GrovePi

#

# Have a question about this example?  Ask on the forums here:  http://forum.dexterindustries.com/c/grovepi

#

'''
## License
The MIT License (MIT)
GrovePi for the Raspberry Pi: an open source platform for connecting Grove Sensors to the Raspberry Pi.
Copyright (C) 2017  Dexter Industries
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
'''

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
© 2021 GitHub, Inc.
Terms
Privacy
Security
Status
Help
Contact GitHub
Pricing
API
Training
Blog
About


```
