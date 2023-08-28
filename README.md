# BSPD_FSAE
Formula Student ---> BSPD
![WhatsApp Image 2023-08-28 at 5 27 10 PM](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/d721680a-b1ab-4ed9-96c7-895bd1758d72)
Greetings! Step into the world of innovation as we delve into the creation of the BSPD for our remarkable 2024 Formula Student car, Genesis. Triumphantly claiming 7th place overall at the fiercely contested Formula Bharat 2023 in India, our journey showcases the fusion of cutting-edge technology and automotive prowess. Below we have mentioned on how about we went ahead with the design of our BSPD circuit.

Free Softwares to start your journey in PCB design and circuit simulations

https://www.kicad.org/download/

https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html
![bsdpflowchart](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/5dccebae-a13b-4e30-97e4-6490c4390e89)

"Brake System Plausibility Device" is a term used in Formula Student and Formula SAE (Society of Automotive Engineers) contests. It is a crucial safety element that monitors and ensures the car's brakes are functioning properly. The BSPD is designed to spot brake system abnormalities or faults, including erroneous pressure measurements, and take the appropriate preventative measures to avoid accidents or breakdowns in the future. It's essential to ensure the overall operation of the Formula Student vehicle safely and successfully, both in practice and during competition.

The vehicle's shutdown system includes the BSPD (Brake System Plausibility device), a non-programmable circuit that prevents the driver from braking and accelerating simultaneously to prevent issues that could result from doing so.



Conditions to trigger the BSPD : 

If both of the below conditions are active together for more than the 500ms :

Brake pressure exceeds the set threshold value (Threshold Value <= 30 bar)
Power delivered to motors >= 5kW or the throttle position is more than 25 % over idle position
After the BSPD is triggered the shutdown circuit must remain open until power cycling the LVMS or the BSPD may reset itself if the opening condition is no longer present for more than 10 s.

![BSPD PCB PHOTO](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/d3bfe385-b08d-4530-a627-4f0a204ab5d9)
![WhatsApp Image 2023-08-23 at 4 43 10 PM](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/3ce598da-d96b-4ad5-9aee-c57af4103944)

A heartfelt thank you goes out to JLCPCB for their generous sponsorship! All of our current boards were DIY etched by hand but with the increase in complexity and number of components of each circuit it became next to impossible to continue, the support of JLCPCB has played a significant role in our success and journey with the Genesis 2024 Formula Student car. Your contribution has helped us achieve our goals and showcase our innovation on the track. We deeply appreciate your partnership and look forward to continuing our collaboration in the future.

We recommend them because they are the best in the business. If you want to use the best PCBs available, click this link: https://jlcpcb.com/HAR

![BSPD1](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/a8548879-3682-41db-98b9-6706bedda12a)
![bspd3](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/b2ce25d4-b104-4520-9c85-ee128550a409)
![bspd2](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/dcf3b2e6-eb35-4d9e-9a76-cebf77cbe34c)

A LM339 comparator is used it compares two input voltages and outputs a binary signal indicating which is larger. If the non-inverting (+) input is greater than the inverting (-) input, the output goes high. If the inverting input is greater than the non-inverting, the output goes low.

To signal when the sensor input goes over a certain threshold, we can connect the - terminal to a voltage representing said threshold, and the sensor to the + terminal. This way, when the sensor signal overtakes our designated voltage value (the - terminal voltage), the comparator emits a “1” signal.

In case our sensor outputs a value which is out of range or the signal connection is lost we need to activate the latching circuit in accordance to the SCS rules.

Till this part we have now understood how to understand to read the sensor and verify if a certain condition is met or not.

Proceeding ahead the BSPD triggers when the 2 conditions are active at the same time so for this we need to use an AND logic gate for verifying if both the conditions are met. For checking if this signal is free from errors and is not resulted high from any external interference we need to add a 500ms plausibility check circuit which can simply be executed with a delay circuit.

We must keep in mind that the BSPD circuit is a nonprogrammable circuit which means we cannot use any microcontroller etc for the 500ms check.

The delay circuit consists of a RC network in which depending on resistors value the time required to charge the capacitor to almost 99% of the input voltage. This time delay helps to verify if the conditions are present for more than the threshold and are non erroneous signals.

After we verify that the signal is genuine we send it to the 555 timer circuit(Monostable mode) which will perform the job of opening the shutdown circuit for 10sec by actuating the relay.
![bspd top only pcb](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/5c8210b0-6b41-4e25-9391-0d102af74904)

![BSPD top view](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/c0023641-aec7-46ef-93fc-8b2283b08d8c)

After we designed our schematic we then designed out PCB layout followed by generating our gerber files.

After finalising all of our designs we sent them to JLC PCB for manufacturing.

We assembled the boards and the BSPD worked well every time we needed it. 

Thanks to our sponsor JLCPCB for giving us the opportunity, and remember, 

here is your link: https://jlcpcb.com/HAR 

How To Order : https://www.youtube.com/watch?v=ZZWdaWAr5A8

![jlclogo](https://github.com/crceformularacing/BSPD_FSAE/assets/143417641/59009b60-0709-4fbb-b74c-d1569875cbaa)




