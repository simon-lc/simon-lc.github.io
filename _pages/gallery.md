---
permalink: /gallery/
title: "Gallery"
layout: single
classes: wide
gallery_jacta_video:
  - video_path: /assets/papers/jacta/stool_lift.mp4
    alt: "stool_lift.mp4"
  - video_path: /assets/papers/jacta/ball_turn.mp4
    alt: "ball_turn.mp4"
  - video_path: /assets/papers/jacta/box_grasp.mp4
    alt: "box_grasp.mp4"
gallery_silico:
  - url: /assets/papers/silico/collision_split_fast.gif
    image_path: /assets/papers/silico/collision_split_fast.gif
    alt: "collision_split_fast.gif"
    title: "collision_split_fast.gif"
  - url: /assets/papers/silico/rrt_grasping.gif
    image_path: /assets/papers/silico/rrt_grasping.gif
    alt: "rrt_grasping.gif"
    title: "rrt_grasping.gif"
  - url: /assets/papers/silico/nonconvex_bundle_slippery.gif
    image_path: /assets/papers/silico/nonconvex_bundle_slippery.gif
    alt: "nonconvex_bundle_slippery.gif"
    title: "nonconvex_bundle_slippery.gif"
gallery_dojo:  
  - url: /assets/papers/dojo/springy_quadruped.gif
    image_path: /assets/papers/dojo/springy_quadruped.gif
    alt: "springy_quadruped.gif"
    title: "springy_quadruped.gif"
  - url: /assets/papers/dojo/atlas_6_steps_square.gif
    image_path: /assets/papers/dojo/atlas_6_steps_square.gif
    alt: "atlas_6_steps_square.gif"
    title: "atlas_6_steps_square.gif"
  - url: /assets/papers/dojo/quadruped_joint_limits.gif
    image_path: /assets/papers/dojo/quadruped_joint_limits.gif
    alt: "quadruped_joint_limits.gif"
    title: "quadruped_joint_limits.gif"
gallery_cimpc:
  - url: /assets/papers/cimpc/robust_trotting_lq.gif
    image_path: /assets/papers/cimpc/robust_trotting_lq.gif
    alt: "robust_trotting_lq.gif"
    title: "robust_trotting_lq.gif"
  - url: /assets/papers/cimpc/wall_stand.gif
    image_path: /assets/papers/cimpc/wall_stand.gif
    alt: "wall_stand.gif"
    title: "wall_stand.gif"
  - url: /assets/papers/cimpc/quadruped_monte_carlo_lq.gif
    image_path: /assets/papers/cimpc/quadruped_monte_carlo_lq.gif
    alt: "quadruped_monte_carlo_lq.gif"
    title: "quadruped_monte_carlo_lq.gif"
gallery_dano:
  - url: /assets/papers/dano/dano.gif
    image_path: /assets/papers/dano/dano.gif
    alt: "dano.gif"
    title: "dano.gif"
  - url: /assets/papers/dano/nerf_trajopt_push_slow.gif
    image_path: /assets/papers/dano/nerf_trajopt_push_slow.gif
    alt: "nerf_trajopt_push_slow.gif"
    title: "nerf_trajopt_push_slow.gif"
  - url: /assets/papers/dano/triumvirate_simulation_corl.gif
    image_path: /assets/papers/dano/triumvirate_simulation_corl.gif
    alt: "triumvirate_simulation_corl.gif"
    title: "triumvirate_simulation_corl.gif"
gallery_algames:
  - url: /assets/papers/algames/algames_4p.gif
    image_path: /assets/papers/algames/algames_4p.gif
    alt: "algames_4p.gif"
    title: "algames_4p.gif"
  - url: /assets/papers/algames/GNE_continuum.gif
    image_path: /assets/papers/algames/GNE_continuum.gif
    alt: "GNE_continuum.gif"
    title: "GNE_continuum.gif"
  - url: /assets/papers/algames/4_drones_door.gif
    image_path: /assets/papers/algames/4_drones_door.gif
    alt: "4_drones_door.gif"
    title: "4_drones_door.gif"
---

This is a quick selection of some of the animations I created so far.

# Jacta [extended gallery]({{ site.url }}{{ site.baseurl }}/gallery/jacta-gallery){: .btn .btn--primary .btn--small}
<!-- Video Gallery -->
<div class="video-gallery" style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; justify-items: center;">
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

***

# Silico [extended gallery]({{ site.url }}{{ site.baseurl }}/gallery/silico-gallery){: .btn .btn--primary .btn--small}
{% include gallery id="gallery_silico" %}

***

# Dojo [extended gallery]({{ site.url }}{{ site.baseurl }}/gallery/dojo-gallery){: .btn .btn--primary .btn--small}
{% include gallery id="gallery_dojo" %}

***

# Contact Implicit MPC [extended gallery]({{ site.url }}{{ site.baseurl }}/gallery/cimpc-gallery){: .btn .btn--primary .btn--small}
{% include gallery id="gallery_cimpc" %}

***

# Dynamics Augmented Neural Objects [extended gallery]({{ site.url }}{{ site.baseurl }}/gallery/dano-gallery){: .btn .btn--primary .btn--small}
{% include gallery id="gallery_dano" %}

***

# Algames [extended gallery]({{ site.url }}{{ site.baseurl }}/gallery/algames-gallery){: .btn .btn--primary .btn--small}
{% include gallery id="gallery_algames" %}

