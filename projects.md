---
layout: page
title: Projects
permalink: /projects/
---
# IS-Count

<figure>
  <img src="https://raw.githubusercontent.com/jesscel/jesscel.github.io/master/assets/projects/is_count/pipeline.png" alt="IS-Count pipeline">
  <figcaption style="text-align: center; color: #808080;"><em>Compared to the exhaustive approach, IS-Count largely reduces the number of satellite images and human annotations while achieving a high accuracy.</em></figcaption>
</figure>

<figure>
  <img src="https://raw.githubusercontent.com/jesscel/jesscel.github.io/master/assets/projects/is_count/visualization.jpg" alt="Visualization">
  <figcaption style="text-align: center; color: #808080;"><em>Visualization of distributions in Africa. The proposal distribution learned from the population density raster (Subfig. (c)) represents the ground truth building distribution (Subfig. (d)) quite well. In the most ideal case, we want the proposal distribution to be proportional to the ground truth.</em></figcaption>
</figure>

* [🧩 Project homepage](https://is-count.github.io/)
* [📃 Paper](https://arxiv.org/pdf/2112.09126.pdf)

<!-- IS-Count: Large-scale Object Counting from Satellite Images with Covariate-based Importance Sampling. 
Chenlin Meng*, **Enci Liu\***, Willie Neiswanger, Jiaming Song, Marshall Burke, David B. Lobell, Stefano Ermon. 
In Proc. 36th AAAI Conference on Artificial Intelligence, (AAAI 2022). -->

# Metadata Shaping

Metadata Shaping is a simple and effective approach to enhance LMs with knowledge. The method involves inserting readily available entity metadata into examples based on mutual information, and training on the shaped data. 

<figure>
  <img src="https://raw.githubusercontent.com/jesscel/jesscel.github.io/master/assets/projects/metadata_shaping/shaping_main.png" alt="Metadata Shaping">
  <figcaption style="text-align: center; color: #808080;"><em>Metadata Shaping shifts the weights of the pretrained model usefully to the metadata token.</em></figcaption>
</figure>


* [🧩 Project homepage](https://github.com/simran-arora/metadatashaping)
* [📃 Paper](https://aclanthology.org/2022.findings-acl.137.pdf)

<!-- Metadata Shaping: Natural Language Annotations for the Tail
Simran Arora, Sen Wu, **Enci Liu\***, and Christopher Ré. 
In Findings of ACL 2022. -->