---
permalink: /portfolio/
title: "Portfolio"
layout: single
# classes: wide
---


## Learning Objective Functions
We coupled an online estimation technique and a fast dynamic game solver to allow an autonomous driving vehicle to optimize its trajectory while learning the objective functions of the cars in its surroundings. It allows the autonomous vehicle to quickly identify the desired speed, desired lane and aggresiveness level of the vehicles it is interacting with. This gained information further improves the trajectory prediction ability of the autonomous vehicle.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<figure class="align-center">
    <img 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/lucidgames/LUCIDGames.gif" 
        alt="LUCIDGames.gif" 
    />
    <figcaption>Orange estimates if blue will accelerate of slow down to let it go first.</figcaption>
</figure> 



## Solving Dynamic Games
We developed fast solver for constrained dynamic games and applied it to complex autonomous driving scenarios. It generates complex driving behaviors where vehicles negotiate and share the responsibility for avoiding collisions.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<figure class="align-center">
    <img 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/algames/algames_4p.gif" 
        alt="algames_4p.gif" 
    />
    <figcaption>Vehicles negatiating right-of-way on a highway ramp.</figcaption>
</figure> 



## Computing Robustness Guarantees
We developed an algorithm relying on a novel sampling-based technique to efficiently compute regions of finite time invariance, commonly refered to as “invariant funnels”. We apply our algorithm to a spacecraft atmospheric entry problem where the goal is to identify the landing zone that the spacecraft is guaranteed to reach under uncertain atmospheric disturbances.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<figure class="align-center">
    <img 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/funnel/sampling_funnel.jpg" 
        alt="sampling_funnel.jpg" 
    />
    <figcaption>Trajectory funnel of a probe landing on Mars.</figcaption>
</figure> 




## Optimizing nonsmooth objective functions
We applied the Alternating Direction Method of Multipliers (ADMM) to solve optimal control problems with L1-norm cost. One application of this work is minimum-fuel trajectory optimization for satellites.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<figure class="align-center">
    <img 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/l1_cost/l1_cost.gif" 
        alt="l1_cost.gif" 
    />
    <figcaption>Fuel-optimal rendez-vous trajectory between two satellites.</figcaption>
</figure> 









