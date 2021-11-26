---
title: 'H bridge'
date: 2021-04-06 13:32:20 +0300
description: H-bridge. # Add post description (optional)
img:  ./software.jpg# Add image post (optional)
---

## So whats an H-Bridge

an H-bridge is a rather simple circuit, containing four switching element, with the load at the center, in an H-like configuration.



 diagram goes here

The most pervasive usage of  H-bridges are  brushed DC or bipolar stepper motor (steppers need two H-bridges per motor)



## Operation modes H-bridge

### Valid and invalid switch states


**You should never ever open both Q1 and Q2 (or Q3 and Q4) at the same time.**
This creates  low-resistance path between power and GND



Because of this restriction from the four possible states the side-A switches could be in only three make sense:

Q1 |	Q2
----------
open |	open
close |	open
open |	close
Similarly for side-B:

Q3 |	Q4
----------
open |	open
close |	open
open |	close
Altogether this allows for 9 different states for the full bridge to be in:

Q1 |	Q2 |	Q3 |	Q4
--------------------------
close | 	open |	open |	open
close | 	open |	open |	close
close |	open  |	close |	open
open  |	close |	open |	open
open  |	close |	open |	close
open  |	close |	close |	open
open  |	open |	open |	open
open  |	open |	open  |	close
open  |	open |	close |	open


## Resources
[h-bridge secrets](https://www.modularcircuits.com/blog/articles/h-bridge-secrets/h-bridges-the-basics/)
(robotherapyy.blogspot.com)