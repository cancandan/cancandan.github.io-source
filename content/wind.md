Title: Porting Andy Farnell's PureData Wind patch to Max/MSP
Category: Sound Design
Tags: max, puredata, sound design
Slug: pd_wind_to_max
Authors: Can Candan
Summary: An exercise in porting a complex patch from pure data to max/msp

The pure data patch I'm trying to reproduce in max is from the excellent book "Designing Sound" by Andy Farnell, which can be found [here](https://mitpress.mit.edu/books/designing-sound).

Download the Code Examples, open the wind4.pd, you will see this:

![wind4]({filename}/images/wind4.png)

Below is my initial attempt in max, circled objects are subpatches or abstractions or stuff not found in max:

![puremax]({filename}/images/puremax.png)

I've used the following max objects corresponding to pd ones, but I'm not sure they are correct:


| pd | max |
|------ | ------ |
|hip~| cross~|
|delwrite~/vd~|tapin~/tapout~|
|catch~/throw~|receive~/send~|
|lop~|lores~|
|bp~|reson~|


Shown below are the subpatches in pure data and max side by side

"pd windspeed":
![windspeed]({filename}/images/windspeed.png) ![windspeed_max]({filename}/images/windspeed_max.png)

containing sub patches "pd gust" 

![gust]({filename}/images/gust.png) ![gust_max]({filename}/images/gust_max.png)

and "pd squall"

![squall]({filename}/images/squall.png) ![squall_max]({filename}/images/squall_max.png)

There's also the abstraction "fcpan"

![fcpan]({filename}/images/fcpan.png) ![fcpan_max]({filename}/images/fcpan_max.png)

And rzero~ which is not found in max, below is a max port I've found in forums

![rzero]({filename}/images/rzero.png)

At this point the resulting sounds from pure data and max are completely different

Max output:

<audio controls="controls">
  <source type="audio/mpeg" src="audio/initial_max_audio.mp3"></source>  
</audio>

Pd output:

<audio controls="controls">
  <source type="audio/mpeg" src="audio/pd_audio.mp3"></source>  
</audio>


This exercise reveals that the two environments are quite different and patches are not easily portable between the two. 

Max code is located [here](https://github.com/cancandan/puredata-wind-to-max). Please let me know if you can spot the problem.

I'll try using the abstractions I've found in this [repository](https://github.com/tkzic/max-pd-abstractions) for emulating the Pd patch. 
