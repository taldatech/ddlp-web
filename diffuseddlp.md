---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: "page"
title: DiffuseDDLP
subtitle: Unconditional object-centric video generation with DDPMs
icon: fa-bolt
order: 5
---
<p style="text-align:center;">
<img src="{{ 'assets/images/balls_150.gif' }}" style="height:150px">
<img src="{{ 'assets/images/obj3d_g2.gif' }}" style="height:150px">
<img src="{{ 'assets/images/traffic_g9.gif' }}" style="height:150px">
</p>

*DiffuseDDLP* employs a <a href="https://arxiv.org/abs/2006.11239">DDPM</a> over the latent space of a pre-trained DDLP as follows: 
* Given a sequence of $$\tau$$ input frames $$x_0, ..., x_{\tau -1}$$, encode a sequence of latent particles $$z_{\tau}=\{z_K^t\}_{t=0}^{\tau} \in \mathbb{R}^{\tau \times K \times F}$$ with DDLP's frozen encoder, where $$K$$ is the number of particles, including a background particle, and $$F$$ is the total dimension of the concatenated attributes (position, scale, depth, transparency and visual features). 
* Train a <a href="https://arxiv.org/abs/2006.11239">DDPM</a> model to approximate the distribution of the latent particles sequence of length $$\tau$$. 
* Equipped with a trained <a href="https://arxiv.org/abs/2006.11239">DDPM</a>, sample sequences of $$\tau$$ particles and use them as input to the pre-trained DDLP dynamics module, PINT, to unroll the sequence to horizon $$T$$, where $$T >> \tau$$ ($$\tau=4$$ for all datasets). Generation results of the first $$\tau=4$$ frames represented as latent particles by the DDPM of DiffuseDDLP (decoded to pixel-space with DDLP's image decoder for visualization purposes):
<p style="text-align:center;"><img src="{{ 'assets/images/diffuse_ddlp_tau.png' }}" style="height:300px"></p>
* Finally, generate a video by decoding the sequence of generated particles back to pixel-space with DDLP's pre-trained image decoder.

<p style="text-align:center;"><img src="{{ 'assets/images/diffuseddlp_arch.png' }}" style="height:300px"></p>

**PINT denoiser**: due to the unique structure of DDLP's latent space, a denoiser architecture that considers the evolution of a set of particles over time is required. To that end, in DiffuseDDLP we repurpose PINT to perform denoising instead of predicting the next state of the particles (in our initial experiments, both the 1D and 2D UNet introduced unsatisfying visual artifacts).

<p style="text-align:center;">
<img src="{{ 'assets/images/balls_135.gif' }}" style="height:150px">
<img src="{{ 'assets/images/obj3d_g1.gif' }}" style="height:150px">
<img src="{{ 'assets/images/traffic_g3.gif' }}" style="height:150px">
</p>

**Fast video genereration with DLPs**: as DDLP's latent space is compact, training a <a href="https://arxiv.org/abs/2006.11239">DDPM</a> is fast and takes less than a day on a single RTX A4000 GPU. For example, for *OBJ3D*, each frame is represented as 12 foreground particles and 1 background particle, i.e. $$K=13$$, and each particle has a total of $$F=14$$, resulting in $$\tau \times K \times F= 4 \times 13 \times 14 = 728$$, which is much smaller than a single CIFAR10 image, $$C\times H \times W = 3\times32\times32=3072$$.

<p style="text-align:center;">
<img src="{{ 'assets/images/balls_170.gif' }}" style="height:150px">
<img src="{{ 'assets/images/obj3d_g6.gif' }}" style="height:150px">
<img src="{{ 'assets/images/traffic_g13.gif' }}" style="height:150px">
</p>

