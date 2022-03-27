.. title: Associated code
.. slug: associated-code
.. date: 2022-03-24 22:35:15 UTC+01:00
.. tags: 
.. category: 
.. link: 
.. description: Code used to run, collect and analyse Ushichka. Also stuff that is potentially relevant.
.. type: text

fieldrecorder
-------------
Holger's initial MATLAB + Soundmexpro script initially worked well to run the audio-video rig. The code began to raise issues on my laptop over time however. SoundmexPro is an audio-interface plugin which needs a dongle to run. However, thanks to my laptop's USB ports (and perhaps one too many rough field nights) - the dongle never sat properly, and even checking audio files while the code was running would trigger an error. 

At some point I finally got bugged with the finickiness of having a dongle to run data collection. Why not get rid of the dongle completely? And thus began my foray into the Python :code:`sounddevice` package. :code:`fieldrecorder` is the result - a bit of janky code I patched together. It is far from beautiful, but gets the job done - and may perhaps be of interest for anyone looking to develop an ASIO based input-output reactive system! There are at least two version of the code - one which triggers recordings automatically once a threshold is crossed, and one which requires a user to press a keyboard button. 

Check out :code:`fieldrecorder` on `this link <https://github.com/thejasvibr/fieldrecorder>`_ .


beamshapes
----------
:code:`beamshapes` started out as an attempt to realistically model sound radiation in bat calls. There is `one` model used a lot - and that assumes front-back symmetry in sound radiation. A lot of studies also only study what happens in `front` of the animal. :code:`beamshapes` is an attempt to show the community that there are other sound radiation models out there that truly describe all-round sound radiation. The package implements multiple sound radiation models - which can be used for predicting acoustic detections or to estimate source model parameters. 

Check out :code:`beamshapes` `here <https://beamshapes.readthedocs.io/en/latest/>`_.