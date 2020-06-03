---
layout: page
title: Generating Minecraft Player Skins with a DCGAN
#tagline: Easy websites with GitHub Pages
description:
---

### Menu
- [Methodology](pages/methodology.html)
- [Data](pages/data.html)
- [Visuals](pages/visuals.html)
- [Results](pages/results.html)
- [Looking Forward](pages/looking_forward.html)
- [References](pages/references.html)

### Overview
Minecraft, a creative sandbox-like computer game, allows players to explore their personalized randomly generated world in which they can harvest resources, build structures, and craft new items. Each player model is wrapped using a flattened "skin" which can either be downloaded from the internet or custom build using one of the many online editors. <br>

<img src="./assets/skin-editor.png" width="600" height="600"/> <br>

In this project I attempt the following objectives:
1. Visualize the sample of skins as clusters using associated tags
2. Use the sample of skins and a DCGAN to generate new samples of Minecraft skins <br>

A sample of roughly 2800 skins were downloaded from https://www.minecraftskins.com/ and stored locally as PNG files. Using PyTorch's example DCGAN implementation, I trained the Generator and Discriminator networks using the sample of skins until the resulting outputs seemed reasonable. This process took roughly 180 epochs although the DCGAN was able to produce cohesive results within the first 50 epochs. <br>

<img src="./assets/training.gif" width="400" height="400"/> <br>

For the second portion of my objective, each skin converted into a feature vector and reduced into 2 dimensions that that a comprehensible plot could be produced. This image feature extraction process utilized the VGG16 convolution neural network, a pre-trained network that was fed 1.2 million images. The resulting array of feature vectors was then reduced using UMAP (Uniform Manifold Approximation and Projection), a state of the art function for reducing high dimensional data down to only 2 dimensions for visualizations. <br>

<img src="./assets/full-dataset-top-class-labels.png" width="1000" height="800"/> <br>

