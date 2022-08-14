
<a name="Nueral Style Transfer"></a>


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/nikhilreddy2002/Envision-Real-Time-Style-Transfer">
    <img src="images/generated3000.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Nueral Style Transfer</h3>

  <p align="center">
    Nueral Style Transfer on the VGG19 model
    <br />
    <a href="https://github.com/nikhilreddy2002/Envision-Real-Time-Style-Transfer"><strong>Explore the docs »</strong></a>

  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project">About The Project</a></li>
    <li><a href="#the-vgg19-model">The VGG19 model</a></li>
    <li><a href="#implementation">Implementation</a></li>
    <li><a href="#results">Results</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

Style Transfer is the process in which one image is composed in the style of another image. We are going to use deep learning in order to make this possible. The process in itself is called neural style transfer and the technique comes from A Neural Algorithm of Artistic Style (<a href=https://arxiv.org/abs/1508.06576>by Gatys et al.</a>).

Neural style transfer is an optimization technique that takes two images - a content image and style reference image. The deep net blends these images together so that the output image looks like the content image, but it seems as though it were “painted” in the style of the reference image.

The implementation involves optimization of the output image to match the content statistics of the content image and the style statistics of the reference image. These statistics are extracted from the images using a convolutional network.

## The VGG19 model


<img src="images/vgg19.png">


VGG is a deep CNN used to classify images. The layers in VGG19 model are as follows:
* Conv3x3 (64)
* Conv3x3 (64)
* MaxPool
* Conv3x3 (128)
* Conv3x3 (128)
* MaxPool
* Conv3x3 (256)
* Conv3x3 (256)
* Conv3x3 (256)
* Conv3x3 (256)
* MaxPool
* Conv3x3 (512)
* Conv3x3 (512)
* Conv3x3 (512)
* Conv3x3 (512)
* MaxPool
* Conv3x3 (512)
* Conv3x3 (512)
* Conv3x3 (512)
* Conv3x3 (512)
* MaxPool
* Fully Connected (4096)
* Fully Connected (4096)
* Fully Connected (1000)
* SoftMax


## Implementation
a loss function which blends two images seamlessly to create visually appealing art, NST defines the following inputs:

* A content image (c) — the image we want to transfer a style to
* A style image (s) — the image we want to transfer the style from
* An input (generated) image (g) — the image that contains the final result (the only trainable variable) 

The architecture of the model as well as how the loss is computed is shown below.

<img src="images/nst_implementationjpeg.jpeg">

The Content loss is calculated by taking the norm of the generated image and the content image for the activations (a) of any layer (l).
## Jcontent <sup>\[l\]</sup> = || a <sup>\[l\] \(c\)</sup> - a <sup>\[l\] \(g\)</sup> || <sup>2</sup>
The Style loss is calculated by taking the norm of the Gram matrix(Gs) of the style image and the generated image (Gg) activations (a) of any layer (l).
## Jstyle <sup>\[l\]</sup> = || G <sup>\[l\] \(s\)</sup> - G <sup>\[l\] \(s\)</sup> || <sup>2</sup>
The Gram matrices Gs and Gg are calculated by multiplying the activation of the layer (l) with its transpose. 

The final loss function is a combination of both for different layers.
## J(G)  = 	$\alpha$ * Jcontent + $\beta$ * Jstyle
where alpha and beta are hyperparameters.

<br>

## <a href="https://github.com/nikhilreddy2002/Envision-Real-Time-Style-Transfer"><strong>Find the code here»</strong></a>

<br>

## Results

### Content Image
<img src="images/mona_lisa.jpg" alt="Content image" width="250" height="250">


### Style Image
<img src="images/great_wave.jpg" alt="Style image" width="250" height="250">

<br>

|0 epochs|1000 epochs|2000 epoch|
|---|---|---|
|<img src="images/generated0.png"  width="150" height="150">|<img src="images/generated1000.png" width="150" height="150">|<img src="images/generated2000.png" width="150" height="150">|

|3000 epochs|4000 epochs|5000 epoch|
|---|---|---|
|<img src="images/generated3000.png" width="150" height="150">|<img src="images/generated4000.png" width="150" height="150">|<img src="images/generated5000.png" width="150" height="150">|

<br>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [A Neural Algorithm of Artistic Style
Leon A. Gatys, Alexander S. Ecker, Matthias Bethge](https://arxiv.org/abs/1508.06576)
* [CNN by Andrew Ng](https://www.youtube.com/watch?v=ArPaAX_PhIs&list=PLkDaE6sCZn6Gl29AoE31iwdVwSG-KnDzF)


