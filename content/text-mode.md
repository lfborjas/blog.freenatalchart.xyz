+++
title = "Introducing: text mode"
date = 2020-12-23

[taxonomies]
tags = ["tech", "announcement"]
+++

As part of my work with [transits](https://github.com/lfborjas/freenatalchart.xyz/issues/1), I wanted an easy way to see a bunch of data, as processed by the server, without waiting until I put together the full markup. So, as a quick little hack, but also a learning experiment, I introduced the ability to request transit pages (and natal chart
pages!) in plain text.

<!-- more -->

On the backend, albeit a bit heterodoxically, we use the fantastic [Servant](https://www.servant.dev/) library to describe the endpoints we support. As part of the HTTP standard,
one can ask a server for a specific content type using the `Accept` header, and Servant
makes it really easy to declare, at the type level, which content types a given endpoint
supports. From that, it was a hop and a skip to implement a "text mode" for our endpoints, although they can only be obtained through applications (like postman
or the humble terminal) that allow you to set the `Accept` header of a request. 

Here's an example (only about half of the output is shown):

<pre>
curl -H "Accept: text/plain" "http://localhost:3000/transits?at=2020-12-22T02:14:58.450Z&location=Tegucigalpa%2C+Francisco+Morazán%2C+Honduras&month=1&day=6&year=1989&hour=12&minute=30&day-part=am&lat=14.0932&lng=-87.2013"

Freenatalchart.xyz
==================
Transits for:
2020-12-22 02:14:58 UTC
Tegucigalpa  (87w16, 14n5)

Natal Planet Positions
----------------------
Planet       |House|Longitude|Speed   |Latitude|Declination|Zodiac Longitude
Sun          |3    |285.9234 |1.0197  |-0.0001 |-22.4930   |♑️ 15° 55' 24"
Moon         |3    |266.1612 |13.6359 |-4.8030 |-28.1881   |♐️ 26° 9' 40"
Mercury      |4    |304.6572 |1.2569  |-1.3025 |-20.3661   |♒️ 4° 39' 26"
Venus        |2    |264.3876 |1.2513  |0.5999  |-22.7245   |♐️ 24° 23' 15"
Mars         |6    |22.9268  |0.5246  |0.6525  |9.5214     |♈️ 22° 55' 37"
Jupiter (r)  |8    |56.4284  |-0.0480 |-0.8774 |18.5050    |♉️ 26° 25' 42"
Saturn       |3    |276.2138 |0.1173  |0.7122  |-22.5856   |♑️ 6° 12' 50"
Uranus       |3    |272.0677 |0.0592  |-0.2201 |-23.6468   |♑️ 2° 4' 4"
Neptune      |3    |280.1213 |0.0378  |0.9024  |-22.1570   |♑️ 10° 7' 17"
Pluto        |1    |224.6882 |0.0238  |15.6315 |-1.2732    |♏️ 14° 41' 17"
Mean Node    |5    |337.5092 |-0.0529 |0.0000  |-8.7536    |♓️ 7° 30' 33"
Lilith       |12   |176.3080 |0.1109  |-1.6621 |-0.0575    |♍️ 26° 18' 29"
Chiron (r)   |9    |93.5200  |-0.0638 |-6.8491 |16.5492    |♋️ 3° 31' 12"

Transiting Planet Positions
---------------------------
Planet       |House|Longitude|Speed   |Latitude|Declination|Zodiac Longitude
Sun          |3    |270.6879 |1.0185  |-0.0002 |-23.4353   |♑️ 0° 41' 17"
Moon         |6    |1.8697   |12.0756 |-5.1709 |-4.0006    |♈️ 1° 52' 11"
Mercury      |3    |271.7927 |1.5879  |-1.6027 |-25.0273   |♑️ 1° 47' 34"
Venus        |2    |248.0143 |1.2505  |1.0473  |-20.6087   |♐️ 8° 0' 52"
Mars         |6    |23.3362  |0.3776  |0.6496  |9.6685     |♈️ 23° 20' 10"
Jupiter      |4    |300.5587 |0.2205  |-0.4806 |-20.4983   |♒️ 0° 33' 31"
Saturn       |4    |300.5218 |0.1085  |-0.3788 |-20.4069   |♒️ 0° 31' 19"
Uranus (r)   |7    |36.9528  |-0.0194 |-0.4553 |13.4034    |♉️ 6° 57' 10"
Neptune      |5    |348.3160 |0.0132  |-1.0856 |-5.6192    |♓️ 18° 18' 57"
Pluto        |3    |293.8720 |0.0311  |-1.1825 |-22.4930   |♑️ 23° 52' 19"
Mean Node    |8    |79.3827  |-0.0530 |0.0000  |23.0124    |♊️ 19° 22' 58"
Lilith       |7    |36.8806  |0.1113  |-3.4814 |10.5182    |♉️ 6° 52' 50"
Chiron       |6    |4.9583   |0.0056  |2.5787  |4.3370     |♈️ 4° 57' 30"

Planetary Transits
------------------

All Aspects to Natal Planets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Aspecting|Aspect      |Aspected |Angle   |Orb     
Sun      |Conjunction |Moon     |4.5267  |4.5267  
Sun      |Conjunction |Venus    |6.3003  |6.3003  
</pre>

Since this is a technologist-oriented feature, all dates are shown in universal time
(UTC,) and all angles are shown as double precision floating point numbers -- 
except for the longitude of planets, which is _also_ shown as a more traditional
zodiac longitude, for reference.
