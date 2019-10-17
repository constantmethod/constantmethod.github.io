[<Home](README.md)

# Collecting and visualising network traffic

The idea with this tutorial is to give an introduction to how you can do some basic analysis of the data that is exchanged between a computer and online servers when using particular platforms or services (e.g. social media, learning management systems, etc). It discusses some simple approaches to creating visualisations that could be used to enrich ethnographic inquiries into the ways people use digital systems rather than providing a introduction to network traffic analysis for computer science purposes.

To follow this tutorial, you will need have [Wireshark](https://www.wireshark.org) and [Gephi](https://gephi.org) installed.

## Collecting meta data about network traffic - 'packet sniffing'

All traffic on data networks like the internet consists of packets that are small chunks of data. These packets come in many different forms (or protocols) and each have source and destination addresses. We can use these pieces of meta data to get a sense of the flows of data without looking at the content of the packets themselves.

The first step is collect the metadata on the traffic we want to analyse. While we can filter the metadata we collect later, it is a good idea to minimize the amount of unwanted noise that is collected. For that reason, close all applications other than the one you want to collect traffic from (for this tutorial we will capture traffic from a web browser).

- Launch Wireshark and look at the section on the screen under the heading 'Capture'

![Wireshark network interfaces](https://github.com/constantmethod/constantmethod.github.io/blob/master/wireshark_interfaces.png?raw=true)

The network interfaces you are using on your computer are listed here and you need to select one
  - Start your web browser and watch the little heartbeat graphs beside each network interface. Double click the one that shows the most activity as you use your web browser (in my case it is 'Belkin USB-C LAN: en7)
- You should now see a screen full of scrolling information about the packets being exchanged when you use your web browser. This information is automatically recorded by Wireshark

![Wireshark capture](https://github.com/constantmethod/constantmethod.github.io/blob/master/Wireshark_capture.png?raw=true)

- Use the platform or service that you are interested in and when you are finished, go back to Wireshark and click on the red stop button on the toolbar
- Save your capture to file in the default 'pcapng' format

## Mapping the servers you've been in contact with

Part of the pcapng file is the Internet Protocol (IP) addresses for the source and destination of each packet of data that was exchanged. Using databases that link those IP addresses to geographic locations, we can map the infrastructure that is involved while a platform or service is in use.

- Download the [MaxMind GeoLite2 Country database](https://dev.maxmind.com/geoip/geoip2/geolite2) in the binary 'MaxMind DB' format
  - You can also download a database that resolves to the level of cities, but for this tutorial we will stick to countries
- In Wireshark, go to 'Edit→Preferences→Name Resolution'
  - Click 'Edit' next to 'Max Mind database directories'
  - Choose the folder that you put the downloaded Geolite2 database in

![Wireshark MaxMind](https://github.com/constantmethod/constantmethod.github.io/blob/master/wireshark_maxmind.png?raw=true)

- Go to 'Statistics→Endpoints'
  - On the top of the new window, make sure IPv4 is selected (you can try IPv6 as well, but the newer IP standard usually has less traceable addresses)
  - At the bottom of the window, click 'Map→Open in browser'

![Wireshark map](https://github.com/constantmethod/constantmethod.github.io/blob/master/wireshark_map.png?raw=true)


