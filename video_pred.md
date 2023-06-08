---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: "page"
title: Video Prediction
subtitle: Unsupervised object-centric video prediction with DDLP
icon: fa-video
order: 3
---
* We compare DDLP to two SOTA object-centric models: [G-SWM](https://sites.google.com/view/gswm) (patch-based model) and [SlotFormer](https://slotformer.github.io/) (slot-based model, <a href="{{ 'comparison.html' }}">"Comaprison"</a> section).

<p style="text-align:center;"><img src="{{ 'assets/images/obj3d3.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/phyre4.gif' }}"></p>

* Input frames $$ \{x\}_0^{T-1} $$. 
* For each $$ 0\leq t \leq T-1 $$, a particle encoder produces the latent particle representation $$ z_t $$ given $$ x_t $$ and $$ z_{t-1} $$ -- tracking the particles to induce consistency between frames. 
* Each individual latent $$ z_{t} $$ is fed through the particle decoder to produce the reconstruction of frame $$ \hat{x}_{t} $$. 
* A Transformer-based dynamics module (PINT - Particle Interaction Transformer) models the prior distribution parameters $$ \{ \hat{z}\}_1^{T-1} $$ given $$ \{ z\}_0^{T-2} $$.
* A pixel-wise reconstruction term minimizes the distance between the original frame $$ x_t $$ and decoded frame $$ \hat{x}_{t} $$, and A KL loss term minimizes the distance between the prior $$\{ \hat{z}\}_1^{T-1}$$ and posterior $$\{ z\}_1^{T-1}$$.

<p style="text-align:center;"><img src="{{ 'assets/images/arch_fig_pp.png' }}" style="height:400px"></p>




# OBJ3D
---

More videos are available under the <a href="{{ 'what_if.html' }}">"What If...?"</a> section.

<p style="text-align:center;"><img src="{{ 'assets/images/obj3d1.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/obj3d2.gif' }}"></p>


# Traffic
---

<p style="text-align:center;"><img src="{{ 'assets/images/traffic1.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/traffic2.gif' }}"></p>
<p style="text-align:center;"><img src="{{ 'assets/images/traffic3.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/traffic4.gif' }}"></p>


# PHYRE
---

<p style="text-align:center;"><img src="{{ 'assets/images/phyre5.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/phyre2.gif' }}"></p>
<p style="text-align:center;"><img src="{{ 'assets/images/phyre3.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/phyre1.gif' }}"></p>


# CLEVRER
---

<p style="text-align:center;"><img src="{{ 'assets/images/clevrer1.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/clevrer2.gif' }}"></p>
<p style="text-align:center;"><img src="{{ 'assets/images/clevrer3.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/clevrer4.gif' }}"></p>


# Balls-Interaction
---

<p style="text-align:center;"><img src="{{ 'assets/images/balls1.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/balls2.gif' }}"></p>
<p style="text-align:center;"><img src="{{ 'assets/images/balls3.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/balls4.gif' }}"></p>

# Failure Cases
---
* *DDLP errs when new objects appear during the context window* (CLEVRER)
* *DDLP may deform objects in scenes with objects of varying scales* (PHYRE)

<p style="text-align:center;"><img src="{{ 'assets/images/failure_clevrer1.gif' }}">&ensp;&ensp;&ensp;&ensp;<img src="{{ 'assets/images/failure_phyre1.gif' }}"></p>
