# StyLit-3D-Style-Transfer

## Project Overview

This project implements parts of the research presented in the paper **"StyLit: Illumination-Guided Example-Based Stylization of 3D Renderings"**. The project focuses on creating a stylized image based on 3D renderings using a two-stage process that incorporates both illumination effects and example-based stylization.

## Table of Contents

- [Motivation](#motivation)
- [Methodology](#methodology)
- [Previous Work](#previous-work)
- [Implementation](#implementation)
- [Results](#results)
- [Future Work](#future-work)

## Motivation

The primary motivation for this project is to explore how example-based stylization can be enhanced by incorporating illumination information, allowing for more visually rich and realistic stylized images of 3D renderings.

## Methodology

The project is divided into two main components:

1. **Light Propagation Calculation**: 
   The 3D scene is rendered using a global illumination algorithm to capture effects such as soft shadows, color bleeding, and glossy reflections. This illumination information is then used as the basis for the stylization process.

2. **Example-Based Stylization**:
   An example-based algorithm is used to apply the style of the provided exemplars to the 3D renderings. This is guided by the light propagation data from the previous step, ensuring that the shading and highlights are preserved in the stylized image.

## Previous Work

The project builds upon several previous methods:
- **Normals-based stylization**: The lit sphere model is used to guide rendering based on normals but often fails to reproduce texture details consistently.
- **Color-based methods**: Algorithms like Image Analogies are used to transfer visual styles between images but often fail in retrieving correct patches, especially for highlights.
- **LPE (Light Path Expression)**: Various methods use LPE channels to guide synthesis but often suffer from "wash-out" effects or lack of consistency.

## Implementation

For this project, we use pre-existing models (spheres and rabbits) provided by OpenCV. The core implementation is based on the Image Analogies method, utilizing light path expressions (LPE) to guide the style transfer process.

The input includes:
- An exemplar scene rendered with LPE channels.
- A stylized exemplar aligned to the exemplar scene.
- A target scene rendered with LPE channels.

The output is a new synthesized image that transfers the style from the exemplar to the target scene based on the similarity between them.

## Results

The final result uses nearest-neighbor field (NNF) and runs on a GPU, leveraging five different LPE channels (global illumination, direct diffuse, direct specular, diffuse bounces, and interreflections). The stylization algorithm runs on six pyramid levels with eight light path tracings, producing an image of size 860x650, with results generated in approximately 3 minutes.

## Future Work

Future research will focus on improving the efficiency of the nearest-neighbor field calculation by exploring the **PatchMatch** algorithm. This algorithm could enhance the performance and accuracy of the stylization process, particularly for larger and more complex 3D scenes.

