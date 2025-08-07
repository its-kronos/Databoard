# 8/1/25

- Started by creating some ideas of what I generally wanted this project to be, and thanks to a few people, I came up with a basic idea.

<img width="501" height="320" alt="image" src="https://github.com/user-attachments/assets/2cd28aea-4f35-4b02-99f5-82221e487b40" />

- After coming up with the basic idea, I started to look at documentation for the STM32 chip I was going to be using, and started creating the schematic, which was pretty easy, but just a bit challenging since I've only been used to the Raspberry Pi documentation for their chips, which were very detailed and easy to follo whwne compared to STM

<img width="905" height="239" alt="image" src="https://github.com/user-attachments/assets/f738028e-5fe6-4a84-8d74-f553ccc9a002" />

<img width="716" height="730" alt="image" src="https://github.com/user-attachments/assets/4313b58c-d859-424a-94c5-10d958e0cacd" />

<img width="622" height="367" alt="image" src="https://github.com/user-attachments/assets/2336656c-9cb2-432e-b2fb-2d6123a9d126" />

- Towards the end, I knew that a crystal that works with this chip would be hard to find. I looked at the only basic JLCPCB part (which would avoid a 3 dollar fee for assembly) that resonates at 16 MHZ, and it took about an hour of calculating to determine that it was probably fine. The only thing I wasn't able to calculate was how good the crystal would be over periods of time since I would need to measure how current flows through the crystal, which would be impossible without specific tools (oscilloscope) and the crystal itself.

- <img width="622" height="367" alt="image" src="https://github.com/user-attachments/assets/07491753-3eb2-4623-beec-46b05315ecec" />

- Also, I decided that I would be "starting over" and creating the PCB in easyEDA instead of Kicad since the Twist You Ship We Ship of Hackclub has two possible routes of funding for the PCB. One of them is to use any EDA but track your time, which doesn't include looking at documentation for 5 dollars an hour, or using easyEDA and receiving a grant from JLCPCB instead, with any amount of time
- Using easyEDA would mean that I wouldn't have to worry about the PCB budget, especially since most of it isn't even tracked due to how documentation heavy hardware design can be

**time: 3 hours**

# 8/3/25

- Ported over everything to easyEDA (without importing, just remade everything)
- After, I added a 32.768 KHZ crystal for the RTC of the chip to be more accurate, especially since time tracking is something that can be fundamental for a board based on collecting data.
- Finally, I started implementing USBC and esd protection with the USBLC6, but then I learned about how I could use TVS diodes for protection, which would be cheaper, and something I implement during the next session.

<img width="1168" height="613" alt="image" src="https://github.com/user-attachments/assets/4fa9709f-0945-48c2-af2d-40767253c966" />

- Also, towards the end, I learned about how the specific MCU I'm using requires 1.5k Ohm pull up resistor on USB DP, and after doing some research I decided that the next session I would include an P channel mosfet to control it

<img width="794" height="43" alt="image" src="https://github.com/user-attachments/assets/6874f43a-fec2-4279-862b-ebbc6c66e618" />


**time: 2.5 hours**

- Finished circuits for USB + ESD protection

<img width="641" height="591" alt="image" src="https://github.com/user-attachments/assets/1c028988-3568-4dba-91fa-f7d43c803431" />


- Did a lot of research on what type of converter I should use, since I would like for it to be compatable with different types of batteries, but this wasn't the easiest due to trying to make the board as cheap as possible. I was able to find a convertor that would allow for a stable conversion from 4.5 volts to 16 volts, which would be pretty good for things like 9V battery

<img width="563" height="361" alt="image" src="https://github.com/user-attachments/assets/03c7181d-74b1-40cb-b3e2-841c3fd6907e" />

**time: 1 hour**

# 8/4/25

- Started laying out everything and sourced other parts, such as the WIFI module and microSD reader, and then learned about how LDOs (the dropout voltage regulator I chose) would be inefficient, so now I'm trying to find a buck regulator instead

<img width="445" height="630" alt="image" src="https://github.com/user-attachments/assets/66c0a3ba-30be-41d3-a048-5f4bfb0a5c00" />

<img width="846" height="522" alt="image" src="https://github.com/user-attachments/assets/28fda6e9-2035-4dd8-b806-98aeefc7287e" />



**time: 2 hours**

- Did some research about a buck regulator, but turns out they would require way too many extended components, so although it would be less efficient, it would drive up the costs

<img width="921" height="286" alt="image" src="https://github.com/user-attachments/assets/56fc2ead-86e8-41fd-9c4a-3d525a7a428c" />


- Changed up the layout a bit to make it neater as well as finished it, and added headers for debugging (SWDIO), and then started some of the start of routing, especially for important traces like USB and some of the power traces

<img width="180" height="502" alt="image" src="https://github.com/user-attachments/assets/b2484456-0914-46ec-b0c0-58911c0b1199" />

**time: 2 hours**

# 8/5/25

- Did a lot of the routing for the traces, and GPIO pins, especially the ones at the top of the STM32.

<img width="326" height="433" alt="image" src="https://github.com/user-attachments/assets/19615aab-a05c-4299-a745-89155c418e0a" />


- However, after doing this I noticed that most of the ADC pins (convert Analog signals to binary) would be used for communication with the SD card and the wifi chip, which would be a waste, so I started to restart and better plan this layout, trying to make sure that I would keep in mind which signals are more important than others (like communication between components > GPIO)

<img width="326" height="662" alt="image" src="https://github.com/user-attachments/assets/0fa39cfb-5403-490e-8788-c4250a344fbf" />

**time: 2h 30m**

- I then spent quite a bit of time on routing, trying to make sure that it was neat, and when I got to the part where I had to route a second UART to communicate with the ESP32, I realized that Instead of using two GPIOs, I could use one and have a switch that switches between the REPL UART pins to the UART pins one would use for communicating with custom code. 

<img width="568" height="499" alt="image" src="https://github.com/user-attachments/assets/cd30645c-8677-4909-900d-b5455fa0647e" />

- During this time, I was able to successfully route 50% of the GPIO headers (and there were a few moment where I pretty much boxed myself in really badly)

  <img width="255" height="656" alt="image" src="https://github.com/user-attachments/assets/5f43eaa3-bb17-4074-b666-f9dae985444d" />

  <img width="214" height="665" alt="image" src="https://github.com/user-attachments/assets/c9198a32-19f4-4d62-9333-e904fb6f9425" />


- This is quite tightly spaced:

<img width="601" height="630" alt="image" src="https://github.com/user-attachments/assets/dd533679-cde9-45c0-9efb-53ef8e2cca73" />

**time: 2h45m**

# 8/6/25

- This was a really big session especially due to today being the final day for the YSWS.

- To start, I completely finished routing the board, which was really easy due to it pretty much being only straight lines.
- After, I proceeded to check over everything in the schematic and the documentation, to make sure that everything would work


- Unfortunately, the crystal that I was using for the RTC wouldn't work due to having too much of a load capacitance. This means that I must go with an extended component (which adds 3 dollars to the cost) and also reroute a small amount of the board.

<img width="903" height="128" alt="image" src="https://github.com/user-attachments/assets/1d3a28b0-1fbb-46bf-afe6-81ebaa02dd9f" />

- I also had to end up swapping RX and PB6 here, and the reason for that was that I thought RX (receive) would be sending the signals (I wasn't really thinking about it)

<img width="309" height="349" alt="image" src="https://github.com/user-attachments/assets/c0b8c363-73bc-4961-9c89-45a815a21b01" />

- Now, the only thing left is the art, and I was able to completely finish the top side, which in my opinion, looks really good, but took me a lot of time due to me being pretty bad at art.

<img width="627" height="822" alt="image (8)" src="https://github.com/user-attachments/assets/1c26c4e5-2693-495d-9984-62a9c3ff739f" />

**time: ~5h**

- I started to add images to the back of the board, and one thing that was a challenge was how imported images always were bottom-most compared to patterns made natively in easyeda which was a pain to fix and move the shapes/reshape them.

<img width="311" height="363" alt="image" src="https://github.com/user-attachments/assets/17a307cd-c8a9-4f6a-baf7-7cbc9d85ca09" />

- Eventually I was able to get it looking pretty good after quite a bit of time

<img width="905" height="823" alt="image" src="https://github.com/user-attachments/assets/358bb33f-bee4-44a8-9230-3eae65b1def0" />

- Also turns out that multicolor silkscreen requires a white board, and at 0.8mm board thickness it requires a special surcharge of 32 dollars, so I changed it to 1.6 and redid the USB traces, as board thickness impacts impedence.

<img width="413" height="296" alt="image" src="https://github.com/user-attachments/assets/84b750bc-ac0f-4a2d-8c74-c3296dbfb94b" />

**time: ~2h**

