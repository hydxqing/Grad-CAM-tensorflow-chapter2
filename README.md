# Grad-CAM-tensorflow-chapter2

The chapter2 of the segmentation network summary:
### Look at the problem through the essence．
External links: Grad-CAM: Visual Explanations from Deep Networks via Gradient-based Localization [paper](https://arxiv.org/abs/1610.02391).

 This paper is an interesting paper. In the paper, a interpretation method of convolutional neural network is introduced. Through the construction of a heatmap-like format, the features learned by the convolutional neural network are presented intuitively. I noticed this because the winner of the image algorithm group of the 2018 AI FEATURE challenge used the method of this paper.

***References***

This code borrows from [insikk](https://github.com/insikk)'s [work](https://github.com/insikk/Grad-CAM-tensorflow) and is modified to use on my own dataset.

## Notes

1. As mentioned in the paper: Grad-CAM use the gradient information flowing into the last convolutional layer of CNN to understand the importance of each neuron for a decision of interest. 
##### First, Grad-CAM guided backpropagtion calculates the gradient value of the final convolution layer for a certain class with the trained model. Then, take the global average of the gradient maps (C H W) obtained to generate the weight (C) of each feature map. Finally, a weighted sum operation are performed between the weight and the corresponding feature map.
In addition, the paper also mentioned that they added a ReLU to the final weighted sum, because we are only interested in the features that have a positive influence on the class of interest.

2. Grad-cam can be used with any other CNN models. Just modify convolution layer in code. At the same time, it can be used for localization in weak supervised segmentation, such as [SEC](https://arxiv.org/abs/1603.06098).
