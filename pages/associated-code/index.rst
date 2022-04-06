.. title: Associated methods
.. slug: associated-code
.. date: 2022-03-24 22:35:15 UTC+01:00
.. tags: 
.. category: 
.. link: 
.. description: Code used to run, collect and analyse Ushichka. Also stuff that is potentially relevant.
.. type: text

Analysing and collecting `Ushichka` meant doing a whole bunch of things from scratch, and also creating the technical tools needed. This page hosts a selection of tools that may be of general interest. Check out the short description and the more detailed online repo/docs link too.  

fieldrecorder
-------------
Holger's initial MATLAB + Soundmexpro script initially worked well to run the audio-video rig. The code began to raise issues on my laptop over time however. SoundmexPro is an audio-interface plugin which needs a dongle to run. However, thanks to my laptop's USB ports (and perhaps one too many rough field nights) - the dongle never sat properly, and even checking audio files while the code was running would trigger an error. 

At some point I finally got bugged with the finickiness of having a dongle to run data collection. Why not get rid of the dongle completely? And thus began my foray into the Python :code:`sounddevice` package. :code:`fieldrecorder` is the result - a bit of janky code I patched together. It is far from beautiful, but gets the job done - and may perhaps be of interest for anyone looking to develop an ASIO based input-output reactive system! There are at least two version of the code - one which triggers recordings automatically once a threshold is crossed, and one which requires a user to press a keyboard button. 

Check out :code:`fieldrecorder` on `this link <https://github.com/thejasvibr/fieldrecorder>`_ .

beamshapes
----------
:code:`beamshapes` started out as an attempt to realistically model sound radiation in bat calls. There is `one` model used a lot - and that assumes front-back symmetry in sound radiation. A lot of studies also only study what happens in `front` of the animal. :code:`beamshapes` is an attempt to show the community that there are other sound radiation models out there that truly describe all-round sound radiation. The package implements multiple sound radiation models - which can be used for predicting acoustic detections or to estimate source model parameters. 

Check out :code:`beamshapes` `here <https://beamshapes.readthedocs.io/en/latest/>`_.

DMCP
----
`Ushichka` has thermal and LiDAR data which need to be aligned to a common coordinate system. Methods exist to align the two with specifically designed calibration objects. Moreover, the thermal scenes are typically high-contrast urban/office scenes with lots of features. The thermal scene inside the cave however is `very` uniform (only a few degrees variation across the scene), and self-similar (walls and rocks look alike). Julian Jandeleit developed the DMCP algorithm after seeing that the classical methods used for 'normal' feature detection failed. The DMCP algorithm is a semi-automated, requiring the user to define 12-18 correspondin points between a depth map and a single camera scene. The final output is a transformation matrix that can be used to convert 3D coordinates from camera tracking to the LiDAR coordinate system. 

While DMCP was built keepin thermal-LiDAR alignment in mind, in principle it could be used to align any datasets with meshes and cameras (color, IR, UV, etc). The DMCP algorithm was developed by Julian during his Bachelor's thesis with Bastian Goldluecke. Website with run-throughs and example use-cases coming soon!