# CIFAR-10 Soft-Classification
 This repository contains a Colab notebook that trains a [ResNet18](https://arxiv.org/abs/1512.03385) architecture on CIFAR-10 using a novel training approach based on soft labels. Soft labels are estimated directly from the network's own representational geometry over the course of training by computing a weighted average between the _true label_ (one-hot vector) and a _similarity label_.

The _similarity labels_ are derived mini-batch-wise and are computed so that each of their entries corresponds to how much a class-label describes the instance. More specifically, the _similarity label_ for a single training sample is derived by computing the average class-wise similarity of that observations to all the other observations present within the same mini-batch. 

To get a more concrete idea about how the soft labels are computed, it might be useful to consider a simplified example. Let's imagine that the network has to learn only four object classes (_cat_, _dog_, _elephant_ and _butterfly_) and that the image of a dog has the following _similarity label_:

$[0.5, 0.84, 0.21, 0.01]$

Here, $0.5$ would be the average similarity of our training image to all the other images of cats present within the same mini-batch, $0.84$ would be the average similarity to the images of dogs, and so on. Similarity is quantified as Pearson's correlation coefficient. 
