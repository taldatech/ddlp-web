---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: "page"
title: "What If...?"
subtitle: Video manipulation and consequence prediction with DDLP
icon: fa-question
order: 4
---

<p style="text-align:center;"><img src="{{ 'assets/images/obj3d_ball_to_cube.gif' }}"></p>

* DDLP provides an interpretable latent representation allowing to directly modify scenes in the latent space by changing objects' learned attributes -- position, scale, depth or shape. 
* Equipped with a pre-trained DDLP on *OBJ3D*, we take an initial sequence of frames, encode them to latent particles and manually locate and modify specific particles corresponding to objects-of-interest according to a specific scenario, e.g., ``what if the green ball moved to the left?''.
<p style="text-align:center;"><img src="{{ 'assets/images/what_if_4_short.png' }}" style="height:250px"></p>
<p style="text-align:center;"><img src="{{ 'assets/images/obj3d_green_ball_left.gif' }}"></p>
* Then, we unroll the latent sequence with the dynamics module and decode to produce a video of the consequences of our interventions.

<p style="text-align:center;"><img src="{{ 'assets/images/obj3d_pink_left.gif' }}">&ensp;<img src="{{ 'assets/images/obj3d_yellow_bigger.gif' }}"></p>
<p style="text-align:center;"><img src="{{ 'assets/images/obj3d_ball_to_cylinder.gif' }}">&ensp;<img src="{{ 'assets/images/obj3d_red_little_left.gif' }}"></p>




