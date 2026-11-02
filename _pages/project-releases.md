---
permalink: /project-release/
title: "Project Release"
layout: single
classes: wide
---

## Whole-Body Manipulation Outside the Lab
<figure class="align-center" style="max-width: 100%; margin: 0 auto;">
    <div style="position: relative; width: 100%; padding-bottom: 56.25%; height: 0;">
        <div id="spot-vision-yt" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></div>
    </div>
</figure>


Perceptive whole-body manipulation running entirely onboard: reinforcement learning skills that work from depth cameras, trained with Crossfade RL and sequenced by a learned gating network, let a legged robot manipulate a heavy tire in uninstrumented environments. More details in the [blog post](https://rai-inst.com/resources/blog/whole-body-manipulation-outside-the-lab/).

<a href="https://www.youtube.com/watch?v=nDIWulWjDz8" class="btn btn--youtube btn--small"><i class="fab fa-youtube" aria-hidden="true"></i> YouTube</a>
[blog post](https://rai-inst.com/resources/blog/whole-body-manipulation-outside-the-lab/){: .btn .btn--success .btn--small}

<br>

## Combining Sampling and Learning for Dynamic Whole-Body Manipulation
<figure class="align-center" style="max-width: 100%; margin: 0 auto;">
    <div style="position: relative; width: 100%; padding-bottom: 56.25%; height: 0;">
        <div id="spot-smpc-yt" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></div>
    </div>
</figure>


A framework that steers a learned whole-body policy with a sampling-based reactive controller, letting legged robots dynamically manipulate large, heavy objects at human cadence. More details in the [blog post](https://rai-inst.com/resources/blog/combining-sampling-and-learning-for-dynamic-whole-body-manipulation/).

<a href="https://www.youtube.com/watch?v=nM_ZHzp8nQA" class="btn btn--youtube btn--small"><i class="fab fa-youtube" aria-hidden="true"></i> YouTube</a>
[blog post](https://rai-inst.com/resources/blog/combining-sampling-and-learning-for-dynamic-whole-body-manipulation/){: .btn .btn--success .btn--small}

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
