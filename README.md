### Problem Statement

The earth is dying. Escape from this planet is the only solution. The Universal space
agency has spotted a wormhole near Saturn. By sending probes through it, you have
discovered that the wormhole opens up possibilities for reaching 5 unknown star systems. Due to limited resources visiting every star system is not possible. You are an Astrophysicist in the team of researchers which has been given the responsibility
to find an exoplanet that can support human life. You have access to the probe data which
contains light curves of all the 5 stars.Tasks are:
1. To find which star systems support exoplanets. 
2. Find the time period of those exoplanets (because humans don’t want longer
years). 
3. Find the distance of those exoplanets from their host stars.

----
>Code.ipynb file contains my solution for the given problem.

### Dataset
Fits files are time series of a star's brightness as recorded by the satellite.

### Install required packages using
```
!pip install lightkurve
```
### Instructions for use:
Download the .fits files from my repository which contains data for the 5 stars.
You need to make a small change in the above script before running it.
```
light_curve=lk.read(f'/content/drive/MyDrive/{name}.fits')
flat_lc=lk.read(f'/content/drive/MyDrive/{name}.fits').flatten(window_length=501)
```

In the above line of code , you need to change the path from this path to path where you have downloaded fits files.

----
To know more about exoplanet and it's transit visit this [link](https://docs.google.com/document/d/1yuy11cfP6FC4a8llFTEoOpWIL79jCH24e_oZ80vzVcU/edit?usp=sharing).Here I have discussed the concepts used to solve this problem and the significance of detecting exoplanets.

This [site](https://viewspace.org/interactives/unveiling_invisible_universe/detecting_other_worlds/transiting_exoplanet) beautifully illustrates the  exoplanet transit concept used to solve this problem.

### Approach Used

By measuring the time between successive transit ‘dips’ you can deduce the orbit period of the planet. From the orbit period and the mass of the star you also obtain the distance between the star and the planet

