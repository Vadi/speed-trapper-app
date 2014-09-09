# Speed Trapper Application

<img src="images/T1000.jpg" />

Have you ever facinated to become [Terminator 2: Judgment Day](http://en.wikipedia.org/wiki/Terminator_2:_Judgment_Day) movie fame [T-1000](http://en.wikipedia.org/wiki/T-1000)?. 

*Continue reading ..*

You're a cop from [SkyNet](http://en.wikipedia.org/wiki/Skynet_(Terminator)) (pretend yourself as T-1000 for a moment and don't ask why T-1000 has to be in cop form) and you're tasked to trap speed of cars that are speeding above X kilometer speed.

Oh! you're also a programmer, what would you do? Yes, you would first write a prototype to see how you can trap speed of cars.

To keep things simple, Mr. T-1000, we would develop two web applications -

* an app to track speed of cars and bust them when they overspeed.
* an app to simulate a car so that we can run more cars that would send speed details to speed tracking app. 

Before we go too much into details, let's quickly see what tech stuffs you need in order to build this app. If you know following keywords, ignore bullets below, jump onto next paragraph. Otherwise, take a break and quickly read links provided below -

1. [SignalR](http://signalr.net/) - a C# based framework that can send quick signals to various browser sessions.
2. [jQuery](https://jquery.org/) - a JS framework, made JavaScript reachable to poor people.
3. [ASP.NET MVC 5](http://en.wikipedia.org/wiki/ASP.NET_MVC_Framework) - a web application framework makes web apps development breeze.

## Speed Trapper

![image](./images/speed-trap-app-sc.png)

Above design shows how you observe speeds of cars while you sip cup of coffee sitting in Skynet office. Each number represents current speed of cars speeding in some roads. We don't care about which road a car is currently being driven. Each car has some name we will come to that part little later.

The text box in the top row tells you the speed that you define as "Overspeed". Any number less than 200km should be allowed in the text box.

Let's call this app as "Speed Trapper" app since it traps speed of cars and tells you based on your Overspeed setting. Assume this app lives in URL - http://localhost:8080/speed-trapper/

## Speeding Cars

Now Speed Trapper needs to receive speeds of cars. We will have a separate web application, let's call as "Car" app, lives in URL - http://localhost:8081/car.

![image](./images/car-app-sc.png)

Above screenshot shows how Car app would look like, it just displays a random number between 10 - 200 that is assumed to be the speed of the car. The car is nothing but your browser session. So if you open more browsers, you have more cars generating random numbers. This numbers, using SignalR, would be sent to Speed Trapper application. We will leave the details to you on how you would make the communication work.

The screenshot shows names for each car. We have kept ```car-names.txt``` file in ```resources``` folder for your reading pleasure, it has readable names that you would need to randomnly pick and assign to new browser sessions a.k.a new cars. However, do not worry about duplicate car names appearing in browser sessions.

## Making Speed Trapper and Car app talk

Once the Car app starts sending the data to Speed Trapper app. Speed Trapper now would receive the speed values (the random numbers). Speed Trapper now would check numbers to see if it is more than Overspeed thresold. In case, the number is greater than Overspeed thresold, Speed Trapper sends a SignalR message "You're busted". Car app now shows the message and stops sending random numbers, pretending, the car has been busted.

# Submissions

## How to submit

1. Fork this repository.
2. Implement two web apps exactly mentioned above. You will find two folders ```car-app``` to keep Car app source code and ```speed-trapper-app```.
3. Send us a pull request and let us know by writing to hello@exzeo.com. You will receive a call back from us.
4. Though we love completed solutions, if you're stuck on something or unable to complete, feel free to send us a pull request.

## Things to note (aka secrets to get selected)

0. If you have any questions regarding use cases on above requirements, try to avoid asking us, we would love if you would assume something to save time and back your assumption with convincing arguments when asked during review process about your decisions. This approach probably show offs your creativity.
1. Don't send code as a zip file. We love pull requests and it saves time.
2. We love those who goes extra miles, so feel free to surprise us with your own creativity.
3. We like to go details so bother to explain any details with additional markdown files in case you want code reviewer to specifically look from your code.
4. Strictly assume you're writing __production quality code__ so write anything with reasons and must address all neccessary [cross cutting concerns] (http://en.wikipedia.org/wiki/Cross-cutting_concern)
5. We love __unit tests__ and you will get our full attention if you include [NCover reports](http://ncover.sourceforge.net/sample-output/NCover-report.html)

# Thanks
1. James Cameroon for wonderful Terminator series.
2. T-1000 image taken from Fast company.
3. .NET and Javascript eco system.
