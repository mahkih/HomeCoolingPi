HomeCoolingPi
=============

Whole house fan controller and temperature monitoring powered by the Raspberry Pi

Description
-----------
HomeCoolingPi provides real-time temperature data from a variety of sensors inside and outside the home. This data is streamed to the online time-series database TempoDB and periodically queried and plotted to the online charting service Plotly. The data can then be analyzed to make better decisions on how to heat and cool the home. The chart can show the thermal interaction between the floors, the attic, and the outside temperature. This helps to determine the best time to open or close windows, run the heater or AC, or run the whole house fan.

The Raspberry Pi is the gateway that runs a multi-threaded Python script that gets periodic sensor measurements and streams the data to TempoDB. One additional thread will query the most recent measurements in the database and plot a chart in Plotly.

In future enhancements, the sensor data will also be used to control a whole house fan. It will determine the best time of day to cool down the home by pushing out hot air from the attic and pulling in fresh air into the home.

Block Diagram
-------------
![Alt text](/block_diagram.png)

Sample Chart
------------

Image below; [interactive graph](https://plot.ly/~flann321/9/) also available. 
![Alt text](/chart.png)

Citations
---------
Streaming Data with Plotly
(http://makezine.com/2014/01/21/streaming-data-with-plotly/)
Big Data Under The Surface At Mobile World Congress
(http://www.forbes.com/sites/tjmccue/2014/02/24/big-data-under-the-surface-at-mobile-world-congress/)
