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
Fits files are time series of a star's brightness as recorded by the satellite.These files were generated in NASA's Kepler mission.

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

Light curves are graphs that show the brightness of an object over a period of time.We first get the plots for each of the stars using LightKurve library.By measuring the time between successive transit ‘dips’ we can deduce the orbit period of the planet. From the orbit period and the mass of the star we also obtain the distance between the star and the planet by using Kepler's 3rd Law.

The method used to identify transiting exoplanets is the Box Least Squares (BLS) periodogram analysis.The Box-fitting Least Squares (BLS) algorithm fits the input time series to periodic "box"-shaped functions.Periodic box-shaped functions represent the behavior of a light curve during a transit better than sines and cosines; they are flat except for a repeated periodic dip in brightness that lasts.BLS works by modeling a transit using an upside-down top hat with four parameters: period, duration, depth, and reference time.These parameters are shown in the following sketch.

![BoxLeastSquares](https://docs.astropy.org/en/stable/timeseries/bls-1.svg)

The output from BLS method has several useful columns, but the most useful ones are probably period and power. Using these, we can plot the periodogram
The highest power spike shows the most likely period, while the lower power spikes are fractional harmonics of the period, for example, 1/2, 1/3, 1/4, etc
To confirm that this period and transit time (epoch) correspond to a transit signal, we can phase-fold the light curve using these values and plot it.

### References

https://exoplanetarchive.ipac.caltech.edu/docs/pgram/pgram_algo.html#:~:text=The%20BLS%20periodogram%20is%20optimized,exoplanets%20or%20detached%20eclipsing%20binaries.

http://docs.lightkurve.org/tutorials/3-science-examples/exoplanets-identifying-transiting-planet-signals.html
