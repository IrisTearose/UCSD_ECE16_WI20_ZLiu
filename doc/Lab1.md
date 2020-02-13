## Tutorial:

 **thought out and backed by your reasoning**, **the same way as you answer math questions**. 

 **show your work**

Sample answers 

> 1. **Not Good (no credit)**: Screenshot the output on the Serial Monitor with no explanation
> 2. **Acceptable (partial credit)**: Screenshot the output on the Serial Monitor. Simple description like, the Serial Monitor's output slows down when the strings being printed out get's larger. 
> 3. **Excellent (full credit)**: Screenshot the output on the Serial Monitor. **Descriptive observation** like, in the initial test at 9600 Baud Rate, the Serial Monitor had printouts every X ms. When the message was changed to double the length, each line was printed out at Y ms. **This makes sense because** the Baud Rate is equal to SOMETHING SOMETHING. As such, when we print out a message of z length, the time it takes to print equal u. 

When answering a Question, please include both the question and the answer, as such:

> Q. The question verbatim from the lab document

> A. Your excellent answer with whatever images and stuff.
>
> and if you need to skip a line, just keep adding > and you will have the same block. 

### Q1 

> Q. What is the **frequency of the blink rate** in this example? Note that frequency is the inverse of the time it takes for a cycle. **A cycle is the time it takes to go HIGH to LOW to HIGH again**. Record a video of your FireBeetle blinking.  Make a note of the answer for now, in the next GIT tutorial, you will get a copy of a sample lab report. 

>  Video of the FireBeetle blinking:
>
>  ![Lab0_BlinkingVideo](fig/Lab0_BlinkingVideo.gif)
>
> I think because of the time it takes from High to Low and go back to low again is 1500 milliseconds, which mean 1.5 seconds, its cycle period is 1.5 secs.. So the frequency is the inverse, 0.67Hz.

### Q2

> Q. When you open the conflicted readme, what did you get? How did you fix it?

#### 

> #### The confliction I made. 
>
> ![image-20200109115216877](fig/Lab1_1.png)![image-20200109115323891](fig/Lab1_2.png)
>
> #### The error I got 
>
> ![image-20200109115757423](fig/Lab1_3.png)![image-20200109115812085](fig/Lab1_4.png)
>
> #### The way I solved it: 
>
> This is the webpage I refered to in order to solve the prob:https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/resolving-a-merge-conflict-using-the-command-line
>
> ![image-20200109141045177](fig/Lab1_5.png)
>
> ![image-20200109140757696](fig/Lab1_6.png)
>
> Here, after the <<<<<<<<<<<HEAD, is my modification on PC, and after that, is my modification on Github. The vertical lines are actually >>>>>>>>>>>, which looks this way in my markdown editor Typora. After that is the branch name.

> **Keep both editing in the file**
>
> ![image-20200109141246138](fig/Lab1_7.png)![image-20200109141618256](fig/Lab1_8.png)
>
> ![image-20200109142142104](fig/Lab1_9.png)
>
> On the Github: 
>
> ![image-20200109142256305](fig/Lab1_10.png)
>
> If I want to keep the version on github while erasing the local version or do the opposite thing, I'll just edit it that way in my local file, which shows the conflict of the two version, and then commit & pull it to the Github. 

### Q3_DigitalRead

> Q. Why do we need a  pull-up resistor? Describe the behavior without it. 

> **The phenomenon observed**
>
> When the button was not presses, the light would be dark;
>
> When the button was pressed, the light would be turned on.
>
> As shown in the following gif. 
>
> ![DigitalRead](fig/DigitalRead.gif)
>
> **The reason that we cannot connect the Vcc directly to the IO25 without using a pull-up resistor**
>
> When the switch is open, a large pull-up resistor could make sure that a small amount of current is flowing between VCC and the input pin (not to ground), thus the input pin reads close to VCC.
>
> When the switch is closed, a large pull-up resistor could make sure that the Vcc would not be shorted to the ground, which could create a large current and may damage the circuit. 
>
> **The reson why we need the Vcc and the pull-up resistor**
>
> If we don't use the Vcc & the R1,  when the switch was disconnected, the IO25 is connected to nothing, which would make the input IO25 in the state of floating. In other words, the input to IO25 would be uncertain, which we don't want. 
>
> **The behavior without it:**
>
> ![image-20200111125047002](fig/Lab1_11.png)
>
> **If we connect  Vcc directly to the IO25**
>
> Without the pull-up resistor R1, when the switch is closed, there will be a direct short circuit between the Vcc supply and ground, resulting in excessive current flow either blowing a fuse or damaging the circuit. 
>
> **If we do not use the Vcc & Pull-up resistor R1 at all**
>
> The builtin LED is always lighted up. 
>
> ![image-20200114100137592](fig/Lab1_12.png)

##### 

### Q4-Q6_RedLED

> Q4. Which GPIO pin did you have to use according to the above setup?

> According the the setting of the board, the GPIO pin I used was the IO26. 

> Q5. What is the expected current draw? 

> According to the following calculation, the expected current draw is 5mA. ![image-20200114100749284](fig/Lab1_13.png)
>
> 
>
> ![image-20200114113742589](fig/Lab1_14.png)
>
> ![image-20200114113756872](fig/Lab1_15.png)

> Q. What is the limit for the GPIO? You can find this on the ESP32_WROOM datasheet: https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32_datasheet_en.pdf . Look under IOH.

> According to the datasheet, the High-level source current should be 20mA. and that's the limit. 

##### 

### Q7-Q8_SerialWrite

>  Q7. In your report, run the above code at Baud Rate of 9600. How many seconds are between each Hello World? What did you expect the time between each print statement to be and what did you actually get? 

>  Q8. How does this change when you change the baud rate to 2400, 4800, and 115200. (When you change the baud rate, you’ll also need to change the Serial Monitor’s Baud Rate. The answer to this question should be **quantitative** and not just qualitative.  Remember that baud rate refers to how many bytes per second is sent. Remember that an ASCII character is 8 bits. 

> **Settings**
>
> Setting the Baud Rate of the serial monitor. 
>
> ![image-20200112142806290](fig/image-20200112142806290.png)
>
> **Output**
>
> **Baud Rate: 9600**: Average Time Interval: about 30 ms. 
>
> (I used the millis() function to count the time. )
>
> ![image-20200114112646561](fig/image-20200114112646561.png)
>
> According to the calculation in the picture attached below, for each of the baud rate among 2400, 4800, 9600 and 115200, the expected spent time and actually time interval are not very close, and I suppose the source of error is: the small error in counting time and the time my computer spent to execute the program. 
>
> I explain the gap between expectation and actual interval of other baud rates in the same way. 
>
> **Deduction**
>
> ![image-20200114120342695](fig/image-20200114120342695.png)
>
> **Baud Rate: 2400**: Average Time Interval: about 120 ms. 
>
> ![image-20200114113506217](fig/image-20200114113506217.png)
>
> **Baud Rate: 4800**: Average Time Interval: about 60 ms. ![image-20200114115912777](fig/image-20200114115912777.png)
>
> **Baud Rate: 115200**:Average Time Interval: about 3 ms.  
>
> ![image-20200114120117741](fig/image-20200114120117741.png)

### Q9_Tabs 

> Q. Note the tabs shown in the figure (for Button, LED, Message, and Timer), please make these four tabs.

> The view in Arduino. 
>
> ![image-20200112150313772](fig/image-20200112150313772.png)
>
> The way they are organized in my folder: 
>
> ![image-20200112150405428](fig/image-20200112150405428.png)



## Challenges: 

Including **Screenshots, photos, and videos of my outputs and setup** 

For the most part, we only expect you to include **screenshots and photos to augment your report.** 

### Challenge 0: Creating my own repository and accept the assignment 

It's about creating our own repository, and cloning it to our local machine.

> Q. Creat our own repository 

> 
>
> I followed the steps in the tutorial to do this. 
>
> ![image-20200109143500233](fig/image-20200109143500233.png)
>
> ![image-20200109143616775](fig/image-20200109143616775.png)

> Q. Creating the assignment repository 

> ![image-20200109143320623](fig/image-20200109143320623.png)



### Challenge 1: LED blink frequency 

Blink the LED lights of different colors and the different frequencies. 

![IMG_4777(1)](fig/IMG_4777(1).gif)

![IMG_4778(1)](fig/IMG_4778(1).gif)

![IMG-4779](fig/IMG-4779.gif)

<video src="fig/IMG_4775.MOV"></video>

<video src="fig/IMG_4773.MOV"></video>

<video src="fig/IMG_4774.MOV"></video>

> Q1. What are the resistor values you chose for each of the LEDs?

> A. I chose 22ohm resistors for both yellow LED and blue LED. 
>
> According to the Amazon page of the LED lights, the expected voltage drop for the yellow & blue led lights is 3.6 V.
>
> So, according to the following calculation, the voltage drop could be 2.8-3.6V. Here I choose 3.0V for calculation, and in this way, the current draw of LED 13.6mA is enough for lighting the LED and at the same time is lower than the I _OH_ 20mA. 
>
> ![IMG_3126](fig/IMG_3126.JPG)





### Challenge 2: Timer part1 

Constructing a timer to calculate the time in seconds, and measure its accuracy using mill() function. 

>Q.  What is the average time elapsed for each second increment? Use [millis()](https://www.arduino.cc/reference/en/language/functions/time/millis/) to help you with this task. Describe how you measured this.  

>A. According to the video, the average time for one second's increasing is 1000 ms, which means 1s. I used the output of millis() to measure this. To measure the actual interval before and after 1 second is added to the timer_seconds, I minused the output of millis(), and got averagely 1000ms, which means that the timer is accurate. 

<video src="fig/IMG_4785.MOV"></video>

### Challenge 3: Timer part2

Adding in the going down of the timer when the button is released. 



> Q. Describe in plain english the logic of your program. 

> In my program, firstly, I setup the GPIO26 as the input pin, and then read if its voltage is low or high, representing it as 0 or 1 respectively. If the voltage of GPIO26 is low (which means that the button is pressed), I add one to the time variable, and wait for 100ms, in this way I'm counting the number of 100ms past. If the GPIO26 is high, I would minus 1 from time variable every 1 second past, and until it goes to 0, GPIO becoming low would not make any difference it. Every time my time variable is changed, I would print it in the serial monitor. 

<video src="fig/IMG_4788.MOV"></video>