---
datePublished: '2016-11-26T03:44:01.281Z'
sourcePath: _posts/2016-09-04-designing-with-high-power-led-modules.md
inFeed: true
authors: []
hasPage: true
keywords:
  - capacitor
  - circuits
  - heatsink
  - led
  - voltage
  - wire
  - rectifier
  - cob
  - switch
  - packages
related: []
author:
  - name: ''
    url: ''
via: {}
dateModified: '2016-11-26T03:44:00.663Z'
title: Making HP-LED Light Systems
app_links: []
publisher: {}
description: Here’s the latest version of the circuit. Many new changes are made.
inLanguage: en
starred: false
url: making-hp-led-light-systems/index.html
_context: 'http://schema.org'
_type: MediaObject

---
# Making HP-LED Light Systems
![Designing, building and testing LED lighting systems. Comparing systems performance Anecdotally. ](https://the-grid-user-content.s3-us-west-2.amazonaws.com/1f7251c5-8b60-4dee-b882-5eb4afc27654.png)

### Update: November 25, 2016

[Here's the latest version of the circuit.][0] Many new changes are made.

<iframe src="https://the-grid.github.io/ed-userhtml/?g=eJx1jbsSgjAQRXu_Ymd7SZCH4CRphM7aHsJCUmRw1qjj3yti59jdW5xzVAeOadToYrwchKA78dN6tjcfEzsH8d2ikHlZyX2aZ-lOVnWJ5tQ20LB_A3CWSQ1baBf4uAJKdEb1bDbKj9wFgocfotNYlBLBkZ9c1Jgt58r2f55CT8NvHD7OfuaBWKNEo8SaMS8wHUGM" height="800" style=""></iframe>

### Update: September 05, 2016

I added a few more elements to the circuit, [this schematic][1] is much closer to the circuits I am currently testing.

<iframe src="https://the-grid.github.io/ed-userhtml/?g=eJx1jjEPgjAUhHd_xUt3aK1IgbRdlI3ZHcqDdkDMs2r89wZhM253uct3p1vwhINhPsZbxTk-kd4ukHuEmLp54pvmWZkVpSxUrpTcZ0oy29RnaMLoY7iOcFprkCRwEalMBSRQL6wt0Ly1uiO702GgdkJ4hT56w465YOBxwRh2WMyd3P83OHXY_36BL7ObqUcyTDCr-TpjPzPRRkg" height="800" style=""></iframe>

### **<NOTICE \>**

**Don't mess with electricity if you haven't been adequately trained to do so. The circuit discussed below is a high voltage circuit and is potentially dangerous. Mishandling the circuit could lead to electrocution causing serious bodily harm or death. Please do not attempt to recreate or assemble this circuit unless you are an experienced professional. Additionally, the circuit discussed is only a prototype. It has not undergone safety testing by any third party, and its design has not been reviewed by anyone other than myself. If you attempt to construct or reproduce this circuit, you do so at your own risk and against my advice. I am offering the following information as an evolving documentation of the state of this project and nothing more.**

### **</NOTICE\>**

---

A little less than two years ago I began studying how to power high power LED modules for home lighting solutions, and since then I designed and tested a number of prototypes. I found a design I preferred, and I have been honing this design for the last nine months or so. It's beginning to shape up a bit, but there is still work to be done. The upside is, the lights aren't very expensive to make, and they are working fairly well at this point.

This post is an attempt to document the process of prototyping and testing these lights, and the design decisions made throughout.

_\*I appologize that this is not yet adequately annotated. I hope to fill in more details over time, please accept my sincere appologies in the mean time._

### Background

For a while now I have been designing my own LED lighting ballasts. A few years ago on a whim I ordered some LED COB packages off of Ali-Express.com; they were really cheap, but appeared to be quite powerful. When I got my hands on them I was blown away by how powerful they were. I knew it must be possible to make bright and effective LED lights for much less than they were retailing for at the time, so I started researching and building circuits and ballasts to test my theory out. I've been through a few different prototypes now, and I'm finally satisfied with the results I'm getting.

I ultimately made and tested two circuit types over the course of this project, one with the LED's arranged in paralell, and another with them arranged in series. For a number of reasons, I preferred running the LED's in series, and that's the type of circuit discussed here.

### **Overview**

If we omit a few safety features, the simple circuit has only three components:

* A Bridge Rectifier used to rectify AC coming from the wall to DC.
* A capacitor smooths the DC output. (Not strictly necessary, but you get flashing at 120hz without it).
* A series of LED COB modules to produce the light.

​The simple circuit:
![](https://the-grid-user-content.s3-us-west-2.amazonaws.com/2054a708-23fa-434e-a191-4854e441b315.png)

### **Additional Safety Measures**

_**Note:**This list of safety measures is not exhaustive; do not assume the circuits shown above are safe simply because these measures have been implemented._

1. Low Voltage Controls - I add an isolated five volt power source to the circuit, and I connect the power switch through the low voltage side of the relays, and they pass the AC voltage through to the lights power circuit.
2. Inrush Current Limiting - For smaller systems this isn't always necessary, but for larger systems current needs to be limited during power up. I use NTC thermistors in my circuit.
3. Bleeder Resistor - This resistor is used to slowly bleed the capacitors of charge after the circuit is powered off. Without one, the capacitors can hold their charge for days or even weeks, and this is a major safety concern\*. The desired value for this resistor is the highest value that will still allow the capacitor bank to discharge in a safe amount of time.
4. Over Current Protection - Some form of fusible link should run in series with the light. I use re-settable fuses rated at 133% of the circuit's max current.
5. Over Temperature Protection - LED's forward resistance declines as temperature increases. The hotter an LED gets the more current it conducts, and the more current an LED conducts the hotter it gets. I designed my ballast with heat sinks that are much larger than necessary, I do not deny the potential for a thermal runaway situation to occur. On each ballast I attache a normally closed temperature controlled switch in series with the lights. When the temperature rises over 70 degrees Celsius, the switch opens and powers down the ballast.

\*It is a safety hazard because people are not conditioned to be cautious when handling unplugged electronic devices. Most people assume an unplugged device is a safe device, which could be a deadly mistake in this case.

**Materials**
![](https://s3-us-west-2.amazonaws.com/the-grid-img/p/d97ab3e71761cb1f2785c3e1d3dd29417657f289.jpg)

_Primary Components -_

* A few additional circuit elements improve safety and/or convenience. I include a temperature controlled switch and an on-off switch in the prototypes right now. The temperature controlled switch helps prevent overheating the LEDs; when the temperature rises above 70 degrees celcius, the point where the LED's are at risk of damage, the switch opens and the lights turn off.Bridge Rectifier: For 120V AC input, any bridge rectifier with a max voltage greater than 170V and a max current greater than the forward current of the LED package will suffice. I am most recently using this [part][2].
* Capacitor: For 120V AC input, the capacitors must have a max voltage greater than 170VDC, and they must also be able to withstand the current draw of the led modules. Determining the correct capacitance value of the capacitor is tricky business. Rather than trying to optimise the circuit mathematically by hand, I modelled the circuit in LTSpice and did transient analysis with different values for the smoothing capacitor. In general, a larger capacitor will produce a smoother voltage. The voltage doesn't need to be perfectly smooth, but the capacitor needs to provide enough energy to maintain a relatively stable light output. I found that 470uF was sufficient to smooth LED's with around a 1 amp draw, but results continue to improve as the capacitor grows in size. My latest circuits use [this capacitor][3].
* LED Modules: I use LED COB modules, COB stands for Chip OnBoard. As I understand it, the LED COB module is an array of LED's that has been printed onto a single silicon wafer which uses an onboard processor to ensure each paralell leg of LED's recieves the same current. There are many different packages available, each with different voltage and amperage characteristics. I tried out two different packages, a 50W package which draws 1.4A at 36V DC, and a 10W package which draws .8A at 12V DC. I ultimately settled on the later, but both worked equally well. I ordered mine from [this vendor][4] at AliExpress.com, but there are many options available. I've heard a lot of good things about the [Cree Packages][5].
* Temperature Dependent Switch: I found [this][6] Temperature Dependent Switch at Amazon.com. They seem to work fairly well.
* Heat Sink - Heat sink is needed because the lights put out a lot of heat. It can be a complicated component to size accurately, but the risks of overheating the LED's outweigh any other considerations here. It is better to end up with too much heatsink than too little. This website is useful for calculating the heatsink needs. In the project shown below, I used a [three and a half inch heatsink][7] from [Heatsink USA][8].

_Other Ingredients -_

* Thermal Adhesive - Serves a dual purpose: it secures the LED's to the heatsink, and it ensures heat can flow from the component to the heatsink easily. For this project I used [Arctic Alumina][9].
* Wires - One three wire cable with [NEMA 5-15 plug][10] to connect the wall to the ballast, and 18 guage wire to connect the components.
* Conformal Coating - (Optional) I like to paint over the electrical connections with Conformal Coating to reduce the likelihood of accidental shorts occuring.

### **Process**
![](https://s3-us-west-2.amazonaws.com/the-grid-img/p/37021a9526e05f5deef0a9bac3f4d4833521ec9e.jpg)

1. Attach the LED's and the Temperature Controlled Switches to the heat sink with thermal adhesive.
2. Build the power supply circuitry on a prototype board/bread board. Besides making sure to solder everything together correctly, the system is more convenient to use if it includes a well thought out and easy to use system for connecting and disconnecting the lights and power supply to the circuitry.
3. Build the isolated 5 Volt relay and switch circuitry on the controller board.
4. Hook everything together, plug in, and Viola! There is Light.
![](https://the-grid-user-content.s3-us-west-2.amazonaws.com/12e64bac-28b6-4ec1-8683-f800ada86b5e.jpg)

<iframe src="https://the-grid.github.io/ed-userhtml/?g=eJxFkcFPwyAUxu_7K3oDDKPWwzR2Ndmi8TYvemp6QPrGWFqoQG2Wdf-70E69AO97P768D9ZOWNX5p0WS4H2vhVdGY0UdNVRSSzltyVmV6NUY2cBG8-bklXBvn0cQHlWFzVVpqyIu4_h3n5yjXRTZVzFv41hWhHW9O2BuZd-C9o5c6NRsiuxGw5A8cw-Y5LxwTFgIxUsDEcSG0GDYBl2Cv4pue3rncsdbCO3ytso54-6kRZGFk7OikHnLOm4DujM1MKUdWL-FvbGAY6zgeCF4ULo2A62NmGaiaH4PRNHB-849pukwDExO8Zf8Nz8Tpk3_q6MLvOSI5IvgKjlG8_yIJuhjs1zdZw9ZdrdaZlHgvTeRnEEHuo5qxyV8Kxgmj3V6_ZUfFKSJPA" height="244" style=""></iframe>

## _Notes:_

### **Paralel Circuit Design**

The Paralell circuit used a BJT circuit mirror arrangement to control current. I used the information from [this article][11] to get started designing a circuit to fit my LED package. The light produced from this design was good, and overall the design behaved reasonably well, but I wasn't fully satisfied with it. It was more expensive to produce, and it was less efficient than I had hoped it would be. I decided to test a series circuit.

### **Series Circuit Design**

The series circuit rectified AC from the wall to run a string of LED's. It is current limited by a MOSFET-BJT configuration, (The FET runs in series with the LED's; it's gate is tied to the collector of the BJT. The BJT emitter run goes to ground, and it's base is connected in series with and after the LED's, with a single resistor between it and ground. The voltage across this resistor will always be proportional to the current going through it, (V=IR), so the voltage at the base will increase as the current through the LED's increases. If the voltage gets too high, the BJT will turn on and it will allow electricity to flow from the FET's gate pin to ground. This lowers the voltage at thschematicschematice gate, and the FET begins to turn off. As the FET closes, the current through the resister goes down, the voltage at the BJT base goes down, the BJT turns back off, and finally the FET returns to its initial state. The initial design was based on information in [this article][12].

[0]: http://everycircuit.com/circuit/5046807143120896 "Latest Circuit"
[1]: http://everycircuit.com/circuit/4948928767721472 "Online simulation of second generation circuit concept"
[2]: http://www.mouser.com/Search/ProductDetail.aspx?R=BR32virtualkey58300000virtualkey583-BR32
[3]: http://www.mouser.com/Search/ProductDetail.aspx?R=LGG2E471MELA30virtualkey64700000virtualkey647-LGG2E471MELA30
[4]: http://www.aliexpress.com/item/100pcs-lot-10W-High-Power-LED-Chip-Bulb-IC-SMD-Floodlight-lamp-bead-Color-White-warm/1654967446.html
[5]: http://www.cree.com/LED-Components-and-Modules/Landing-pages/CXA
[6]: http://www.amazon.com/Bimetal-Temperature-Control-Thermostat-KSD9700/dp/B00978QHK8?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o06_s01
[7]: http://www.heatsinkusa.com/3-500-wide-extruded-aluminum-heatsink/
[8]: http://heatsinkusa.com/
[9]: http://www.arcticsilver.com/arctic_alumina_thermal_adhesive.htm
[10]: http://www.cablewholesale.com/products/power-products/power-cords/product-10w1-10106.php?utm_source=GoogleShopping&utm_medium=cpc&utm_term=10W1-10106&utm_campaign=NEMA%205-15P%20to%20Standard%20ROJ%20Power%20Cord%2C%20Black%2C%2018%2F3%20(18AWG%203%20Conductor)%20SVT%2C%2010%20Amp%20%2F%20125%20Volt%2C%206%20foot&gclid=CjwKEAjwxoG5BRCC7ezlzNmR8HUSJAAre36jo0XMXtpPa_m5wux6VjFe0f-h_TxZ2lhypkkWk4ul8xoCcq3w_wcB
[11]: http://www.ledsmagazine.com/articles/print/volume-6/issue-2/features/led-design-forum-avoiding-thermal-runaway-when-driving-multiple-led-strings-magazine.html
[12]: http://www.instructables.com/id/Circuits-for-using-High-Power-LED-s/?ALLSTEPS