---
title: Scientific Machine Learning
---

# <i class="fas scientific-machine-learning"></i>Scientific Machine Learning


As a computational lab, we do a lot of machine learning simulations in rheology. But there is more to it.

<p style="text-align: center;">
  <a href="https://rheoinformatic.com/publications/?search=%22tag:Machine%20Learning%22">Browse All Machine Learning Publications</a>
</p>

{% include section.html %}

# Physics-inspired surrogate models


Imagine you have a structured material in hand, interested in understanding its properties such as viscosity and elastic modulus. Typically, obtaining the entire material properties requires rheometry, a process that is resource- and time-consuming. However, machine learning techniques can serve as surrogate models, potentially replacing or complementing rheometry by representing material properties. By embedding a physical law governing the structured material, it's possible to use just a fraction of rheometric data to recover the entire parametric space of the properties. The challenge lies in the imposition of the governing equation. When this equation is fully understood and given, rheometric measurements can be entirely replaced. However, if the equation is missing, we face a more traditional machine learning task. The reality often falls somewhere in between, with some data and some physics available. This scenario particularly benefits from physics-inspired surrogate models, which leverage both available data and physical laws to represent material properties efficiently.

{%
  include feature.html
  image="images/research_topics/ml-long.png"
%}

{% include section.html %}

# Constitutive model construction using machine learning

A vast number of complex fluids lack a proper governing equation, prohibiting rheologists from predicting and/or controlling the behavior of the fluid. Unfortunately, defining governing equations is not always feasible since data is often scarce and even noisy. On the other hand, physical equations only have a few terms, making them sparce in high-dimensional space. Leveraging the automaic differentiation feature of deep neural networks and encoding governing equations in PINNs alongside spacity of equations, offers promising results on discovery of governing equations.

{% include section.html %}

# Neural operators and transformers 

Let's circle back to the structured material example with the same objective: to find its properties. Surrogate models such as physics-informed neural networks (PINNs) do a great job in recovering those properties. However, in these scenarios, the learned model might struggle to generalize to unseen cases, as the learning is specific to the provided geometry and ICs/BCs. To overcome these limitations of standard neural networks (NNs), neural operators have been proposed to remedy the mesh-dependent nature of finite-dimensional operator methods by producing a single set of network parameters that may be used with different discretizations. In a rheometric configuration, therefore, the operator mapping the input signal (the imposed shear rate, for instance) to the output signal (the desired material property) is learned in one shot.

Transformers, on the other hand, offer a robust solution by leveraging their self-attention mechanism to efficiently capture the complex, long-range dependencies typical in rheological data. Unlike traditional models, they aren't limited by specific geometries or conditions, allowing for a more accurate and generalized prediction of material properties across different scenarios. This makes transformers particularly suited for understanding and predicting the dynamic behavior of structured materials in rheology.