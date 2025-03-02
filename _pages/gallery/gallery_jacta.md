---
permalink: /gallery/jacta-gallery/
title: "Jacta gallery"
layout: single
classes: wide
gallery_jacta_video:
  - video_path: /assets/papers/jacta/stool_lift.mp4
    alt: "stool_lift.mp4"
  - video_path: /assets/papers/jacta/ball_turn.mp4
    alt: "ball_turn.mp4"
  - video_path: /assets/papers/jacta/box_grasp.mp4
    alt: "box_grasp.mp4"
gallery_jacta:
  - url: /assets/papers/jacta/allegro_hand.gif
    image_path: /assets/papers/jacta/allegro_hand.gif
    alt: "allegro_hand.gif"
    title: "allegro_hand.gif"
  - url: /assets/papers/jacta/floating_hand.gif
    image_path: /assets/papers/jacta/floating_hand.gif
    alt: "floating_hand.gif"
    title: "floating_hand.gif"
  - url: /assets/papers/jacta/planar_hand.gif
    image_path: /assets/papers/jacta/planar_hand.gif
    alt: "planar_hand.gif"
    title: "planar_hand.gif"
---


<!-- Video Gallery -->
<div class="video-gallery" style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; justify-items: center; margin-bottom: 40px;">
  {% for video in page.gallery_jacta_video %}
    <figure class="align-center" style="max-width: 100%; margin: 0;">
      <video 
          src="{{ site.url }}{{ video.video_path }}" 
          autoplay 
          loop 
          muted
          controls
          style="width: 100%; height: auto; cursor: pointer;" 
          onclick="openModal('{{ site.url }}{{ video.video_path }}')"
      >
          Your browser does not support the video tag.
      </video>
      <figcaption>{{ video.title }}</figcaption>
    </figure>
  {% endfor %}
</div>

<!-- Include the Gallery for GIFs (Keep this as is) -->
{% include gallery id="gallery_jacta" %}

[back to main gallery]({{ site.url }}{{ site.baseurl }}/gallery){: .btn .btn--primary .btn--small}