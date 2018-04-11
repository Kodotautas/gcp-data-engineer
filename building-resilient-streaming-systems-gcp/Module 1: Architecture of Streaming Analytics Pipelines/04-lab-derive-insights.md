# Discuss some streaming scenarios
So let's go ahead and discuss some streaming scenarios. So we'll look at a scenario, we'll talk about what data is sent; what processing does this data need; what analytics or queries would you run on it and what dashboard or reporting would be most useful. So let's take - just to give you an idea of what this is, let's go ahead and take the lab exercise that we're going to be doing in the rest of this course. So the scenario is that the San Diego Department of Transport, they want to bring live updates on highway lanes to commuters on the highway. So they want to put up a sign on the highway that says this is what the average speed is, there is a blockage on the road three miles from here etc. So they want to basically provide live updates on the highway lanes to people traveling on the highway. So that's the scenario. So in order to do that, what data are we going to be sending? We're going to be sending traffic data and this is going to come from the sensors that are going to be located on the highway lanes. And the sensors are going to be sending new data every five minutes. So every five minutes the sensors are going to be sending data on the speed at that lane at the location of the sensor at that point in time. So what processing does that need? We want to be able to show the current traffic condition. The idea is that for rerouting purposes, for example, if somebody is running a fleet of busses and they need to say, oh well, that highway is blocked, so I'm going to send all my buses on this other route instead, they'll need to have a heads-up view of the average speed of every mile of every highway in the city. But at the same time, we might also need another processing. So besides the current traffic conditions, we might also want to compute the average speed to basically show things like that lane is blocked and then maybe send an emergency vehicle to go figure out what's wrong, unblock the lane or if there's a problem, send police officers to get rid off, to move the vehicles out of the lane whatever. So we need to figure out which lanes are slower. We need to do some analysis to figure out which lanes are slow, which lanes are moving normally. So what kind of analytics and queries do you need to run on this data? We need to get the minimum, the maximum, the average within the lane. That's to show for current conditions. But we also need to compare lanes on a highway to figure out if one lane is blocked, to detect an anomaly. So those are the two types of queries that we want to run on the data. But what kind of dashboards? What data do we keep showing all the time? Well, we need to show an update on lane slowdowns. So we may have a dashboard that says these are the lanes that are slower, these are the lanes on these highways that are slower than normal. We may want to have a map with markers, showing these areas are red, these areas are green, these areas are moving normally, these areas are congested, those kinds of things. So that's the scenario, the data, the processing that it needs, what kind of analytics you want to do, what kind of dashboard or reporting you want to do. So take a look at the next two. This looks easy but it isn't because you want to think about the whole scenario and you want to break it down into this streaming architecture that we talked about. The data being sent goes into pub/sub. The data processing, the continuous queries that you're running go into dataflow. The ad hoc analytics that you're running, those go into BigQuery and the dashboards go into dashboard tools. So we want to understand, given a scenario how to break it down into these four components. So take a few minutes, pause the video and try out the next two. Ready? For the PR example, so if the PR department of an airline wants to handle negative tweets. So what data is sent?There are tweets that mention the airline name, the hashtag of the airline, something like that. That's the data that's going to be sent. What processing does the data need? You need to do sentiment analysis. Are the people mentioning the airline in a happy way, in a sad way? Are they excited that they're traveling somewhere else or are they frustrated that they're not traveling anywhere, that they're stuck, that the plane is delayed? You also want to do NTT detection for topics, things like delays, weather, baggage, flight attendant. You may also want to figure out the location of the tweet. Which airport, which city are they or is this tweet from? So what kind of queries do you run? The queries might be things like grouping by location, grouping by topic, grouping by looking at different areas of the country to see if there are problems in some particular airspace or some particular airport etc. What kind of dashboard would you need? Well, the dashboard could be something like for example, the top 10 negative topics that are segregated in different ways. And you can imagine that this is a dashboard that you would look at and that you would prominently display in the airlines office so that people can jump on problems and resolve them very quickly.

Try the next one. Ready? So here we want to do a fraud detection. So we want to inform the users of suspicious transactions as they happen. So for this example, what data do we need to send? Well, the data would be the data transactions from every terminal, every purchase terminal in the world. What kind of processing do we need? We might need to segregate the credit card transactions by the user, by the credit card, by the country, by the store, who to notify. What kind of queries? Well, we might want to do something like are we seeing an increase in fraudulent activity in London. That's the kind of query that a business user might want to suddenly run. So we want to provide the ability in BigQuery for example, to be able to run that query. How about a dashboard? Well, today's query, this is the way I often think about it - today's query is tomorrow's dashboard. So if you find users often querying and saying, is there an increase in fraudulent activity in London, then you might build a dashboard that shows the locations in which there is an increase in fraudulent activity. So that's the way you would think about it. So now go ahead and try these. 