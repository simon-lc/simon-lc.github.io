---
permalink: /
title: "Bio"
seo_title: "Simon Le Cleac'h"
author_profile: true
---



I lead the **whole-body manipulation team** at [Robotics and AI Institute (RAI Institute)](https://rai-inst.com/). My research combines **reinforcement learning, imitation learning**, and large-scale simulation to enhance robot capabilities in **manipulation** and locomotion. My goal is to bridge theoretical foundations with practical algorithmic solutions that enable robots to achieve human-level whole-body manipulation in real-world environments.

During my **PhD at Stanford** and as intern at **Google Robotics**, I built a **differentiable physics engine** from scratch, enabling gradients to propagate through contact dynamics for optimization and learning. 
My research focused on developing fast optimization algorithms for simulation, planning, and control of robotic systems. I applied differentiable physics to trajectory optimization, planning, and reinforcement learning for locomotion and manipulation. I developed optimization algorithms that enable game-theoretic reasoning for autonomous vehicles.
{: style="text-align: justify;"}


# Portfolio
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
  var START = 30, END = 67;
  function createPlayer() {
    new YT.Player('spot-smpc-yt', {
      videoId: 'nM_ZHzp8nQA',
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
Highlight of the team, we combined reinforcement learning with sampling-based optimization to enable legged robots to dynamically manipulate large, heavy objects with coordinated use of their arms, legs, and body. We adopted a hierarchical architecture in which a learned locomotion policy handles balance and movement at the low level, while a high-level controller reasons about the task in a reduced space of base velocities and end-effector positions. Sampling-based control discovers forceful, multi-contact strategies by simulating many futures in parallel, allowing the robot to perform dynamic loco-manipulation at human cadence.
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

<div style="text-align: center; margin-top: 30px;">
  <a href="{{ site.url }}{{ site.baseurl }}/portfolio/" class="btn btn--primary btn--large">Past projects</a>
</div>
