# Air-Quality-Index
i used tkinter, Python when combined with Tkinter provides a fast and easy way to create GUI applications. Tkinter provides a powerful object-oriented interface to the Tk GUI toolkit. Import the Tkinter module.
import modules 
from tkinter import *
import requests 
from bs4 import BeautifulSoup 

def getdata(url): 
	r = requests.get(url) 
	return r.text 


def airinfo(): 
	htmldata = getdata( 
		" 
	soup = BeautifulSoup(htmldata, 'html.parser') 
	
	# Traverse the air quality 
	for item in (soup.find_all("div", 
							class_="styles_aqiGraphNumber_2R6Y9")): 
		res_data = item.get_text() 

		# traverse the content 
	data = '' 
	for item in (soup.find_all("div", 
							class_="styles_primaryPollutantGraphNumber_2WgP9")): 
		data += item.get_text() 
		data += " "
	
	air_data = data.split(" ") 
	
	ar.set(res_data) 
	o3.set(air_data[0]) 
	no2.set(air_data[1]) 
	so2.set(air_data[2]) 
	pm.set(air_data[3]) 
	pml.set(air_data[4]) 
	co.set(air_data[5]) 
	res = int(res_data) 
	if res <= 50: 
		remark = "Good"
		impact = "Minimal impact"
	elif res <= 100 and res > 51: 
		remark = "Satisfactory"
		impact = "Minor breathing discomfort to sensitive people"
	elif res <= 200 and res >= 101: 
		remark = "Moderate"
		impact = "Breathing discomfort to the people with lungs, asthma and heart diseases"
	elif res <= 400 and res >= 201: 
		remark = "Very Poor"
		impact = "Breathing discomfort to most people on prolonged exposure"
	elif res <= 500 and res >= 401: 
		remark = "Severe"
		impact = "Affects healthy people and seriously impacts those with existing diseases"
	res_remark.set(remark) 
	res_imp.set(impact) 

# object of tkinter 
# and background set to grey 
master = Tk() 
master.configure(
