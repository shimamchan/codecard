# The Code Card
![](images/codecard.png)

Code Card is a Wi-Fi-enabled device with an e-paper display that can retrieve content from Oracle Cloud. Code Cards are available on a first-come basis to Oracle OpenWorld and Oracle Code One attendees who sign up for a cloud trial account. Stop by the Groundbreakers Hub to sign up and start configuring your Code Card.

There are loads of things that you can do with your Code Card - here's a list of documentation, work instructions, & code to get you up and running:

## Instructions
- **[Code Card Designer Mobile App](#code-card-mobile-app)**  
Personalise the contents of your Code Card's display using the Code Card Designer Mobile Application.
Create different template layouts, save them to the Oracle Cloud, and then apply them to your card with the press of a button. Ths is the quickest way to get up and running.

- **[Configuration Settings](/terminal/README.md)**  
Manage your Code Card configuration via serial connection over USB. Settings such as Wi-Fi SSID & Password can be managed via serial connection.
  - **[Code Card Serial Connection](/terminal/serial.md)**  
Manually configure Code Card using a serial connection over USB. Initiate the serial connection using your favourite terminal emulation package (Putty, etc).. (TBC)
  - **[Code Card Configurator](https://github.com/cameronsenese/codecard-configurator)**  
Python script to automatically configure Code Card settings using serial connection over USB. Useful for restting Code Card settings back to default, or to save and batch apply custom settings.. (TBC)

- **[Fn Functions (FaaS)](functions/README.md)**  
Fn Functions on Oracle Cloud Infrastructure.. (TBC)

- **[Helidon (Java) Microservices on Kubernetes](#helidon/README.md)**  
Helidon (Java) Microservices on Kubernetes.. (TBC)

- **[Programming the Code Card Firmware](/arduino/README.md)**  
Programming the Code Card Firmware.. (TBC)

## How did we build the Code Card?
We partnered with [Squarofumi](http://www.sqfmi.com/), creators of [Badgy](https://www.tindie.com/products/squarofumi/badgy-iot-badge/), an IoT badge, to create the Code Card.

![](images/badgy.jpg)

