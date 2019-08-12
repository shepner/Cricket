# Cricket
Updated electronic cricket idea

Back in the late 70s or possibly early 80s, I remember seeing an article in a magazine for a fun little electronics kit for an electronic cricket.  It ran off a 9v battery, had wire legs and probably had a 555 or the like for chirping every so often.  Now that embedded CPUs likely have more computing power then the actual cricket, I think it is time to have one with a bit more functionality.

Sensors:
* light sensors (eyes)
* stereo microphones (ears)
* speaker (legs)
* accelerometer (touch)
* thermocouple (touch)

Functions and such:
* Each cricket would have a unique ID (UUID?)
* Network with other crickets via sound (15kHz?)
* variable volume
* provide regular health/location status updates to other crickets
* alert each other to location of danger
* dynamically generate a network map based on IDs heard and their volume
* Cricket (annoyatron) mode
* USB serial interface
* data logger
* API
* they could work as a distributed sensor network
* This for networking:  https://en.wikipedia.org/wiki/Interplanetary_Internet  Would love to be able to have 2 of these working at IP gateways with N crickets between passing data
* instant messaging/email like functionality
* shape it like a cricket
* rechargable battery large enough for days of operation



cricket (annoyatron) mode:
* listen for danger and be quiet until it goes away
* make more noise in the dark
* if the danger is annoyed, all crickets chirp at once at max volume the moment it leaves
* with a network of crickets, lure danger away
 

[Chirp](https://chirp.io/) is closely related to this:
https://create.arduino.cc/projecthub/ChirpDevs/send-data-with-sound-bf7024
