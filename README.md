# FY-B10-or-YF-B10-flow-sensor-esp32-example
Calibration factor and calculation formula for YF-B10 or "FY-B10" Flow Sensor

If you bought a water flow sensor in aliexpress, 1 inch model YF-B10 or as it happened to me receive a "FY-B10" that is not retrieved in any google search, you probably felt a bit frustrated finding the calibration factor formula to use it with your ESP32 or Arduino in your IoT projects.

First, I thought that the model "FY-B10" could be a typo when the label was printed. So I started digging into YF-B10 datasheets, and I found 2 different possible formulae:
**F = 8 * Q - 4    (± 5%) where Q = L/Min**
(usually these sensors has only a factor element. This one has in its original formula a calibration factor (8) and something like a calibration correction (-4))

Another search and I found this one:
**F = 6 * Q - 8 (±3%) where Q = L/min**

Unfortunately, when comparing sensor readings with the Janz water meter of my water company the values were very different of those retrieved with any one of these formulae.
So I started measuring 2 different driplines water flow getting the frequency (pulses per second) with the ESP32 in arduino IDE, and getting the flowrate through the oficial water meter reading against 60 seconds counting.
Then I put those data in a two equations system to get X (calibration factor) and Y (that minus something).

Testing again all the readings were perfectly correct for both driplines and even with both simultaneously.

My resulting formula was **F = 6.5163 x Q - 2.7**

The .ino file for arduino IDE shared here is based on one of the most examples available all over the web.

Note: These values worked for me, with my flow sensor. I don't know if this is valid to all YF-B10 or only for "FY-B10", or just for my own FY-B10.
Anyway, my only intention is to help anyone with the same problem.
