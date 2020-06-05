---
layout: page
title: MineSkins - an exploration of generative art and dimensional reduction
#tagline: Easy websites with GitHub Pages
description:
---

### Menu
| Methodology | Data | Visuals | Results | Future | References |
|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
|[Methodology](pages/methodology.html)|[Data](pages/data.html)|[Visuals](pages/visuals.html)|[Results](pages/results.html)|[Looking Forward](pages/looking_forward.html)|[References](pages/references.html)|

<br><br>

### Overview
Minecraft, a creative sandbox-like computer game, allows players to explore their personalized randomly generated world in which they can harvest resources, build structures, and craft new items. Each player model is wrapped using a flattened "skin" which can either be downloaded from the internet or custom build using one of the many online editors. <br>

Online Skin Editor | Minecraft Player (in-game)
:---:|:---:
![](./assets/skin-editor.png) | ![](./assets/skin-in-game-01.jpg)

In this project I attempt the following objectives:
1. Visualize the sample of skins as clusters using associated tags
2. Use the sample of skins and a DCGAN to generate new samples of Minecraft skins <br>

A sample of roughly 2800 skins were downloaded from https://www.minecraftskins.com/ and stored locally as PNG files. Using PyTorch's example DCGAN implementation, I trained the Generator and Discriminator networks using the sample of skins until the resulting outputs seemed reasonable. This process took roughly 180 epochs although the DCGAN was able to produce cohesive results within the first 50 epochs. <br>

<div align="center">
    <p>DCGAN Training Progress</p>
    <img src="./assets/training.gif" width="400" height="400"/>
</div>
<br>

Using the generated skins, I mapped each one on top of a Minecraft player model in order to visualize the results. Here are a few of the samples produced:

New Skin 1 | New Skin 2 | New Skin 3 | New Skin 4 
:---:|:---:|:---:|:---:
![](./assets/fake_3_scaled.png) | ![](./assets/fake_4_scaled.png) | ![](./assets/fake_6_scaled.png) | ![](./assets/fake_9_scaled.png)

For the second portion of my objective, each skin was converted into a feature vector and reduced into 2 dimensions so that a comprehensible plot could be produced. My objective was to observe whether these skins, when reduced from thousand of dimensions into 2, preserved any sort of clusterable structure. The image feature extraction process utilized the VGG16 convolution neural network, a pre-trained network that was trained using roughly 1.2 million images. <br>

Before running the entire dataset through the dimensionality reduction algorithm I first wanted to test this idea using a smaller subset of skins - preferably those of similar structure. Thus, I gathered 348 skins using the search term "Spiderman".

<div>
    <img src="../assets/skin-unwrapped-spiderman-01.png" width="500" height="800"/>
    <img src="../assets/skin-unwrapped-spiderman-02.png" width="500" height="800"/>
</div>

The below plot was created using the entire dataset of skins. This includes skins that did not have tags and skins that had a label other than one of the most popular ones.
<div align="center">
    <p>Dimensionality Reduction on All Skins</p>
    <img src="./assets/full-data-umap.png" width="500" height="500" class="center" /> <br>
</div>

<br>

The below plot was created using only skins that had at least 1 tag and a most popular tag that was part of the subset of top N tags (where N can be changed depending on preference). For example, if out of the top 20 most popular tags the first tag was "girl", then I would not include skins which had their most popular skin recorded with a tag of "girl".  
<div align="center">
    <p>Dimensionality Reduction on Skins With Popular Tag as Label</p>
    <img src="./assets/data-with-tags.png" width="500" height="500" class="center" /> <br>
</div>



