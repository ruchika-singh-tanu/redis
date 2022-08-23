#  Redis Stream With Spring Boot 

![](../../../Desktop/1.PNG)!

* Our publisher will publish some evens to related to purchases into Redis. Lets call them purchase-events stream.
* A consumer group is interested in listening to those events. This could be for calculating the revenue or processing payment or sending out an email!
* When you need to do all of these – for ex: payment processing and sending out an email then you need a separate consumer group for each.
* The consumers will be consuming events & they can do anything with it. In our case we just find the price user paid and calculate the revenue by category.
* This can be logged in a separate DB. But to keep things simple, I will be logging this info as a SortedSet in Redis.

##### Redis Stream – Set up:
Lets bring up the redis and redis-commander instances first.

> docker-compose up redis redis-commander

You can access the redis instance at port 8081 as shown here.

![](../../../Desktop/2.png)

I have created a stream :
> XADD purchase-events * dummy-key dummy-value

I have created a consumer-group :
> XGROUP CREATE purchase-events purchase-events $

And finally run the application using docker-compose file

> docker-compose up