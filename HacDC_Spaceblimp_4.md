Spaceblimp-4 sucessfully launched and retrieved: April 10, 2011 ![500
px](_sb4_IMG_7739_small.JPG "500 px")

## Summary

We launched from Breezewood Elementary School??? at 1:30 pm, the balloon
popped at 2:41 pm at 103,764 ft, and touched back down at 3:09 pm.
Again, we were exceptionally lucky with the recovery and were able to
drive up to within 200 ft of the package.

The "package" contains two GPS units connected to radio modems that
transmit the balloon's location every 30s, various instruments, and
still and video cameras. It's all enclosed in super-space-age,
soft-sided insulated lunchboxes and secured to pegboard, cushioned for
landing with pink insulation foam.

![300 px](_sb4_path.png "300 px")
<img src="_sb4_the_package.jpg" title="_sb4_the_package.jpg" width="430"
alt="_sb4_the_package.jpg" />

## Video


This time, in addition to running a still camera, we also put up a HD
video camera running 720p at 60 frames/sec. The results are fantastic!

- [SB4 at apex on youtube](http://www.youtube.com/watch?v=6Cz4s8potWE)
  about 80 seconds before the balloon popped.

Notice how quickly it stabilized as the chute opened. Don't be deceived,
though, it got up to 136 mph within the first minute of fall -- there's
just not much chute drag in space.

- [SB4 launch on youtube](http://www.youtube.com/watch?v=pwT_LmqpgCc).
  Skipping hours of preparation and 20 minutes filling up the balloon,
  going straight to the good stuff...

Why no movies in-between? The clouds were very heavy on launch day, and
most of the footage is white-out. Something failed in the video camera a
few minutes after popping too, so there's no re-entry video.

Oh yeah, and for fun all of the raw video is posted up on projects in
/home/spaceblimp4, and here is the script I used to make the
youtube-compatible videos: [Media:
sb4_editingMovieForYoutube.txt](Media:_sb4_editingMovieForYoutube.txt "wikilink")

## Data

### On-board Logging

The on-board datalogger keeps records of interior/exterior temperature
and GPS data.

[Media: SB-4_flight_log.gz](Media:_SB-4_flight_log.gz "wikilink") (and
here's the code in R that generates the above images, and some PDFs to
boot: [Media:
spaceblimp4_analysis.gz](Media:_spaceblimp4_analysis.gz "wikilink"))

<img src="_sb4_altitude_time.png" title="_sb4_altitude_time.png"
width="300" alt="_sb4_altitude_time.png" />
<img src="_sb4_gpsHeading_time.png" title="_sb4_gpsHeading_time.png"
width="300" alt="_sb4_gpsHeading_time.png" />
<img src="_sb4_location.png" title="_sb4_location.png" width="300"
alt="_sb4_location.png" /> <img src="_sb4_riseSpeed_altitude.png"
title="_sb4_riseSpeed_altitude.png" width="300"
alt="_sb4_riseSpeed_altitude.png" />
<img src="_sb4_riseSpeed_histogram.png"
title="_sb4_riseSpeed_histogram.png" width="300"
alt="_sb4_riseSpeed_histogram.png" />
<img src="_sb4_riseSpeed_time.png" title="_sb4_riseSpeed_time.png"
width="300" alt="_sb4_riseSpeed_time.png" />
<img src="_sb4_temp_altitude.png" title="_sb4_temp_altitude.png"
width="300" alt="_sb4_temp_altitude.png" />
<img src="_sb4_temp_time.png" title="_sb4_temp_time.png" width="300"
alt="_sb4_temp_time.png" /> <img src="_sb4_windspeed_altitude.png"
title="_sb4_windspeed_altitude.png" width="300"
alt="_sb4_windspeed_altitude.png" />
<img src="_sb4_windspeed_time.png" title="_sb4_windspeed_time.png"
width="300" alt="_sb4_windspeed_time.png" />

### Accelerometer

The accelerometer package flown was the same as last time, with the
exception of having half the memory, so there are 50 observations per
second. The data are 0-255, with (roughly) 127 being no acceleration. If
you graph it, you can clearly see liftoff, popping, and landing. Until
we get some time for analysis, the rest is left up to you:

<figure>
<img src="_sb4_accelerometer.png" title="_sb4_accelerometer.png"
width="300" />
<figcaption>_sb4_accelerometer.png</figcaption>
</figure>

[Accelerometer CSV raw
data](http://www.postero.us/spaceblimp4_accelerometer.csv.gz) Here's
some python code to get you started with the accelerometer data: [Media:
analyseAccelerometer.py](Media:_analyseAccelerometer.py "wikilink").
(Requires SciPy for plotting.)

## Launch Plans (Historic)

<table>
<thead>
<tr class="header">
<th style="text-align: right;"><p>Planned launch date:</p></th>
<th><p>Sunday, April 10, 2011</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;"><p>Launch time:</p></td>
<td><p>10:00 AM, Launch should take less than an hour.</p></td>
</tr>
<tr class="even">
<td style="text-align: right;" data-valign="top"><p>Launch
Location:</p></td>
<td><dl>
<dt></dt>
<dd>
Where: Breezewood Elementary School???
</dd>
<dd>
Address: 133 North Main Street, Breezewood PA 15533-8142
</dd>
<dd>
Lat/Long: 39.9970,-78.2440
</dd>
</dl></td>
</tr>
<tr class="odd">
<td style="text-align: right;"><p>Coordination/Talk-in:</p></td>
<td><p>146.685 MHz simplex</p></td>
</tr>
<tr class="even">
<td style="text-align: right;"><p>Planned Altitude:</p></td>
<td><p>100,000 feet</p></td>
</tr>
<tr class="odd">
<td style="text-align: right;"><p>Planned Ascent Rate:</p></td>
<td><p>1,300 ft/min</p></td>
</tr>
<tr class="even">
<td style="text-align: right;"><p>Planned Descent Rate:</p></td>
<td><p>1,000 ft/min</p></td>
</tr>
<tr class="odd">
<td style="text-align: right;"><p>Primary Beacon:</p></td>
<td><p>Tiny Track 4 with 0.5 W transmitter on 144.390 MHz, call sign
W3HAC-11 (<a href="http://aprs.fi/?call=W3HAC-11">map</a>). $3 GPS
module</p></td>
</tr>
<tr class="even">
<td style="text-align: right;"><p>Secondary Beacon:</p></td>
<td><p>Son-of-WhereAVR with ublox GPS. Yaesu VX-1 handi-talkie with 1 W
Transmitter, call sign W3HAC-12 (<a
href="http://aprs.fi/?call=W3HAC-12">map</a>), Frequency 432.225
MHz</p></td>
</tr>
<tr class="odd">
<td style="text-align: right;"><p>Payload:</p></td>
<td><p>Still camera, HD video camera, Geiger counter to measure cosmic
rays, a nine degree of freedom Inertial Measurement Unit, accelerometer,
pressure, light and temperature sensors.</p></td>
</tr>
</tbody>
</table>

The balloon is a 2000g Kaymont/Totex with 291 cubic feet of helium. The
total weight of the capsule is about five pounds.