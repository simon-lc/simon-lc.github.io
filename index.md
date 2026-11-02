---
permalink: /
title: "Bio"
seo_title: "Simon Le Cleac'h"
author_profile: true
---



I currently lead the **whole-body manipulation team** at [Robotics and AI Institute (RAI Institute)](https://rai-inst.com/). Our research combines **reinforcement learning, imitation learning**, and large-scale simulation to enhance robot capabilities in **manipulation** and locomotion. Our goal is to bridge theoretical foundations with practical algorithmic solutions that enable robots to achieve human-level whole-body manipulation in real-world environments.

During my **PhD at Stanford** and as intern at **Google Robotics**, I built a **differentiable physics engine** from scratch, enabling gradients to propagate through contact dynamics for optimization and learning. 
My research focused on developing fast optimization algorithms for simulation, planning, and control of robotic systems. I applied differentiable physics to trajectory optimization, planning, and reinforcement learning for locomotion and manipulation. I developed optimization algorithms that enable game-theoretic reasoning for autonomous vehicles.
{: style="text-align: justify;"}


# Highlight of the team


## Perceptive dynamic manipulation
<figure class="align-center" style="max-width: 100%; margin: 0 auto;">
    <div style="position: relative; width: 100%; padding-bottom: 56.25%; height: 0;">
        <div id="spot-vision-yt" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></div>
    </div>
    <figcaption>Percetive dynamic manipulation deployed on Boston Dynamics Spot.</figcaption>
</figure>

<script src="https://www.youtube.com/iframe_api"></script>
<script>
(function () {
  var START = 39, END = 125;
  function createPlayer() {
    new YT.Player('spot-vision-yt', {
      videoId: 'nDIWulWjDz8',
      playerVars: {
        autoplay: 1,
        mute: 1,
        controls: 1,
        start: START,
        end: END,
        rel: 0,
        modestbranding: 1,
        playsinline: 1
      },
      events: {
        onReady: function (e) {
          e.target.mute();
          e.target.setVolume(0);
          e.target.seekTo(START);
          e.target.playVideo();
        },
        onStateChange: function (e) {
          if (e.data === YT.PlayerState.ENDED) {
            e.target.seekTo(START);
            e.target.playVideo();
          }
        }
      }
    });
  }
  if (window.YT && window.YT.Player) {
    createPlayer();
  } else {
    var prev = window.onYouTubeIframeAPIReady;
    window.onYouTubeIframeAPIReady = function () {
      if (prev) prev();
      createPlayer();
    };
  }
})();
</script>
In our latest project, we took whole-body manipulation out of the lab by making a legged robot run entirely on its own sensors and computer. Spot now finds and handles a 15 kg car tire using only its built-in depth cameras, with no motion capture or external workstation. Every skill (uprighting, rolling, dragging) is a reinforcement learning policy trained in simulation. We converted each policy from using exact tire poses to relying only on noisy depth images with a method we call Crossfade RL. The method keeps reinforcement learning running while new vision encoders are distilled in. A learned gating network picks which skill to run, so the robot can carry out long tasks on its own and recover when something goes wrong. All of this runs on an onboard Mac Mini, and we tested it in uninstrumented settings such as a skatepark, a basketball court and a garage. More details in the [blog post](https://rai-inst.com/resources/blog/whole-body-manipulation-outside-the-lab/).
{: style="text-align: justify;"}



## Combining sampling and learning for dynamic whole-body manipulation
<figure class="align-center" style="max-width: 100%; margin: 0 auto;">
    <div style="position: relative; width: 100%; padding-bottom: 56.25%; height: 0;">
        <div id="spot-smpc-yt" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></div>
    </div>
    <figcaption>Dynamic whole-body manipulation deployed on Boston Dynamics Spot.</figcaption>
</figure>

<script src="https://www.youtube.com/iframe_api"></script>
<script>
(function () {
  var players = [
    { id: 'spot-vision-yt', videoId: 'nDIWulWjDz8', start: 39, end: 125 },
    { id: 'spot-smpc-yt', videoId: 'nM_ZHzp8nQA', start: 30, end: 67 }
  ];
  function createPlayer(p) {
    new YT.Player(p.id, {
      videoId: p.videoId,
      playerVars: {
        autoplay: 1,
        mute: 1,
        controls: 1,
        start: p.start,
        end: p.end,
        rel: 0,
        modestbranding: 1,
        playsinline: 1
      },
      events: {
        onReady: function (e) {
          e.target.mute();
          e.target.setVolume(0);
          e.target.seekTo(p.start);
          e.target.playVideo();
        },
        onStateChange: function (e) {
          if (e.data === YT.PlayerState.ENDED) {
            e.target.seekTo(p.start);
            e.target.playVideo();
          }
        }
      }
    });
  }
  function createAll() { players.forEach(createPlayer); }
  if (window.YT && window.YT.Player) {
    createAll();
  } else {
    var prev = window.onYouTubeIframeAPIReady;
    window.onYouTubeIframeAPIReady = function () {
      if (prev) prev();
      createAll();
    };
  }
})();
</script>

We combined reinforcement learning with sampling-based optimization to enable legged robots to dynamically manipulate large, heavy objects with coordinated use of their arms, legs, and body. We adopted a hierarchical architecture in which a learned locomotion policy handles balance and movement at the low level, while a high-level controller reasons about the task in a reduced space of base velocities and end-effector positions. Sampling-based control discovers forceful, multi-contact strategies by simulating many futures in parallel, allowing the robot to perform dynamic loco-manipulation at human cadence. More details in the [blog post](https://rai-inst.com/resources/blog/combining-sampling-and-learning-for-dynamic-whole-body-manipulation/).
{: style="text-align: justify;"}





## Learning from planner demonstrations
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
With Jacta, we combined reinforcement learning with sampling-based algorithms to solve contact-rich manipulation tasks. While sampling-based planners can quickly find successful trajectories for complex manipulation tasks, the solutions often lack robustness. We leveraged a reinforcement learning algorithm to enhance the robustness of a set of planner demonstrations, distilling them into a single policy.

<div style="text-align: center; margin-top: 30px;">
  <a href="{{ site.url }}{{ site.baseurl }}/portfolio/" class="btn btn--primary btn--large">Past projects</a>
</div>
