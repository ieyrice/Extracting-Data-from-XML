# Extracting-Data-from-XML

Coursera Using Python to Access Web Data Program Week 5 Assignment

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

In this assignment you will write a Python program somewhat similar to http://www.py4e.com/code3/geoxml.py. The program will prompt for a URL, read the XML data from that URL using urllib and then parse and extract the comment counts from the XML data, compute the sum of the numbers in the file.

We provide two files for this assignment. One is a sample file where we give you the sum for your testing and the other is the actual data you need to process for the assignment.

Sample data: http://py4e-data.dr-chuck.net/comments_42.xml (Sum=2553)
Actual data: http://py4e-data.dr-chuck.net/comments_469370.xml (Sum ends with 51)

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

import urllib
import urllib.request
import xml.etree.ElementTree as ET

url = input("Enter location: ")
if len(url) < 1:
    url = "http://python-data.dr-chuck.net/comments_200531.xml"
print("Retrieving " + ' http://py4e-data.dr-chuck.net/comments_469370.xml')

xml = urllib.urlopen(url).read()
print("Retrieved: " + str(len(xml)) + " characters")

tree = ET.fromstring(xml)

counts =  tree.findall('.//count')
print("Count: " + str(len(counts)))

accumulator = 0

for count in counts:
    accumulator += int(count.text)

print("Sum:" + str(accumulator))

