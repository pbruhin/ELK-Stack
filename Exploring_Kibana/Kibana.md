## Exploring Kibana from Day 3 of the activity

Instructions

	1. Add the sample web log data to Kibana.
	2. Answer the following questions:
	        ○ In the last 7 days, how many unique visitors were located in India? 254
		○ In the last 24 hours, of the visitors from China, how many were using Mac OSX? 13
		○ In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors? 6.6, 13.3
		○ In the last 7 days, what country produced the majority of the traffic on the website? China
		○ Of the traffic that's coming from that country, what time of day had the highest amount of activity? 12
		○ List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type). Gz - zip, css - Cascading Style Sheets, zip - zip, deb - software package format for the Debian Linux distribution, rpm - Red Hat Package Manager file
	3. Now that you have a feel for the data, Let's dive a bit deeper. Look at the chart that shows Unique Visitors Vs. Average Bytes.
		○ Locate the time frame in the last 7 days with the most amount of bytes (activity). 2021-11-21 21.00
		○ In your own words, is there anything that seems potentially strange about this activity? A spike in data is visible.
	4. Filter the data by this event.
		○ What is the timestamp for this event? 21:00
		○ What kind of file was downloaded? rpm - red hat package
		○ From what country did this activity originate? Nigeria
		○ What HTTP response codes were encountered by this visitor? 200
	5. Switch to the Kibana Discover page to see more details about this activity.
		○ What is the source IP address of this activity? 172.3.128.226
		○ What are the geo coordinates of this activity? "lat": 34.39944167, "lon": -86.27016111
		○ What OS was the source machine running? iOS
		○ What is the full URL that was accessed? https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-6.3.2-amd64.deb
		○ From what website did the visitor's traffic originate? http://www.facebook.com/success/winston-scott
	6. Finish your investigation with a short overview of your insights.
		○ What do you think the user was doing? Downloading a Linux package
		○ Was the file they downloaded malicious? If not, what is the file used for? No. It is to install software on a Linux machine. 
		○ Is there anything that seems suspicious about this activity? No
		○ Is any of the traffic you inspected potentially outside of compliance guidlines? Potential concern that referral is from Facebook

