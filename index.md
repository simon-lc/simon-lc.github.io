---
permalink: /
title: "Bio"
seo_title: "Simon Le Cleac'h"
author_profile: true
---



I am a **Lead Research Scientist** at the [Robotics and AI Institute (RAI Institute)](https://rai-inst.com/). My research combines **reinforcement learning, imitation learning**, and large-scale simulation to enhance robot capabilities in **manipulation** and locomotion. My goal is to bridge theoretical foundations with practical algorithmic solutions that enable robots to achieve human-level whole-body manipulation in real-world environments.

During my **PhD at Stanford** and as intern at **Google Robotics**, I built a **differentiable physics engine** from scratch, enabling gradients to propagate through contact dynamics for optimization and learning. 
My research focused on developing fast optimization algorithms for simulation, planning, and control of robotic systems. I applied differentiable physics to trajectory optimization, planning, and reinforcement learning for locomotion and manipulation. I developed optimization algorithms that enable game-theoretic reasoning for autonomous vehicles.
{: style="text-align: justify;"}


# Portfolio
## Combining sampling and learning for dynamic whole-body manipulation
<figure class="align-center" style="max-width: 100%; margin: 0 auto;">
    <video 
        src="{{ site.url }}{{ site.baseurl }}/assets/release/spot_smpc/spot_upright_roll_stack_lq.mp4" 
        autoplay 
        loop 
        muted
        controls
        style="width: 100%; height: auto;"
    >
        Your browser does not support the video tag.
    </video>
    <figcaption>Dynamic whole-body manipulation deployed on Boston Dynamics Spot.</figcaption>
</figure>
We combined reinforcement learning with sampling-based optimization to enable legged robots to dynamically manipulate large, heavy objects with coordinated use of their arms, legs, and body. We adopted a hierarchical architecture in which a learned locomotion policy handles balance and movement at the low level, while a high-level controller reasons about the task in a reduced space of base velocities and end-effector positions. Sampling-based control discovers forceful, multi-contact strategies by simulating many futures in parallel, allowing the robot to perform dynamic loco-manipulation at human cadence.
{: style="text-align: justify;"}



## Learning from planner demonstrations
With Jacta, we combined reinforcement learning with sampling-based algorithms to solve contact-rich manipulation tasks. While sampling-based planners can quickly find successful trajectories for complex manipulation tasks, the solutions often lack robustness. We leveraged a reinforcement learning algorithm to enhance the robustness of a set of planner demonstrations, distilling them into a single policy.
<figure class="align-center" style="max-width: 100%; margin: 0 auto;">
    <video 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/jacta/stool_lift_lq.mp4" 
        autoplay 
        loop 
        muted
        controls
        style="width: 100%; height: auto;"
    >
        Your browser does not support the video tag.
    </video>
    <figcaption>Contact-rich manipulation policy deployed on two Boston Dynamics Spot robots.</figcaption>
</figure>

## Unified collision detection and contact dynamics
With Silico, we unified collision detection and contact dynamics into a single optimization problem. With this novel formulation, we can smoothly differentiate through contact dynamics for objects of arbitrary shapes. Previous differentiable physics formulations were limited to simple shape primitives.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<figure class="align-center">
    <video 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/silico/rrt_grasping_lq.mp4"
        autoplay loop muted playsinline
        style="width: 100%; height: auto;"
    >
        Your browser does not support the video tag.
    </video>
    <figcaption>Grasping behavior obtained with a sampling-based planner leveraging smoothly differentiable collision detection and contact simulation.</figcaption>
</figure> 


## Differentiable physics engine
With Dojo, we took a physics- and optimization-first approach to address some of the limitations of the current physics engines. In particular, we can provide informative gradients through contact dynamics. Contrary to simulators relying on soft-contact models, Dojo can simulate hard contact interactions. Additionally, it does not need to approximate the friction cone to simulate sliding behavior.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<!-- style="height: 530px; object-fit: cover; object-position: 0 100%;"  -->
<figure class="align-center">
    <video 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/dojo/springy_quadruped_lq.mp4"
        autoplay loop muted playsinline
        style="width: 100%; height: auto;"
    >
        Your browser does not support the video tag.
    </video>
    <figcaption>Differentiable simulation of a Unitree A1 quadruped in Dojo.</figcaption>
</figure> 


## Simulating neural objects contact interactions
We proposed a simple approach to neural object contact simulation. By augmenting a neural object with dynamics properties such as mass, inertia, coefficient of friction, we can simulate the object interaction with the environment, other objects or even oter neural objects.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<figure class="align-center">
    <video 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/dano/dano_lq.mp4"
        autoplay loop muted playsinline
        style="width: 100%; height: auto;"
    >
        Your browser does not support the video tag.
    </video>
    <figcaption>Sampling the neural object density field is the first step before simulating contact interactions.</figcaption>
</figure> 



## Optimizing through contact
We leveraged differentiable contact simulation for control through contact. We embedded a differentiable physics engine into an online optimization pipeline.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<figure class="align-center">
    <video 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/cimpc/robust_trotting_lq_lq.mp4"
        autoplay loop muted playsinline
        style="width: 100%; height: auto;"
    >
        Your browser does not support the video tag.
    </video>
    <figcaption>The quadruped trots while we introduce some disturbances.</figcaption>
</figure> 




## Learning Objective Functions
We coupled an online estimation technique and a fast dynamic game solver to allow an autonomous driving vehicle to optimize its trajectory while learning the objective functions of the cars in its surroundings. It allows the autonomous vehicle to quickly identify the desired speed, desired lane and aggresiveness level of the vehicles it is interacting with. This gained information further improves the trajectory prediction ability of the autonomous vehicle.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<figure class="align-center">
    <video 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/lucidgames/LUCIDGames_lq.mp4"
        autoplay loop muted playsinline
        style="width: 100%; height: auto;"
    >
        Your browser does not support the video tag.
    </video>
    <figcaption>Orange estimates if blue will accelerate of slow down to let it go first.</figcaption>
</figure> 



## Solving Dynamic Games
We developed fast solver for constrained dynamic games and applied it to complex autonomous driving scenarios. It generates complex driving behaviors where vehicles negotiate and share the responsibility for avoiding collisions.
{: style="text-align: justify;"}

<!-- <figure style="width: 600px" class="align-center"> -->
<figure class="align-center">
    <video 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/algames/algames_4p_lq.mp4"
        autoplay loop muted playsinline
        style="width: 100%; height: auto;"
    >
        Your browser does not support the video tag.
    </video>
    <figcaption>Vehicles negotiating right-of-way on a highway ramp.</figcaption>
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
    <video 
        src="{{ site.url }}{{ site.baseurl }}/assets/papers/l1_cost/l1_cost_lq.mp4"
        autoplay loop muted playsinline
        style="width: 100%; height: auto;"
    >
        Your browser does not support the video tag.
    </video>
    <figcaption>Fuel-optimal rendez-vous trajectory between two satellites.</figcaption>
</figure> 

