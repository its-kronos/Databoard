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
