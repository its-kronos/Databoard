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

