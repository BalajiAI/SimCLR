# SimCLR - A Simple Framework for Contrastive Learning of Visual Representations

Transfer learning is a common practice among AI practitioners for solving Computer Vision problems such as Classification, Object Detection, etc. But, Pre-training requires a large labeled dataset. However, labeled datasets are very expensive. Self-Supervised Learning is an approach for learning reprsentations from unlabeled dataset (without human supervision). Self-Supervised Learning approaches have been widely adopted as a popular method for Pre-training NLP models. Recently, those methods have shown promising results for pre-training vision models.

SimCLR is a simple framework for learning visual reprsentations without human supervision via Contrastive Learning. SimCLR makes use of an idea that different views of the same image should be close together in the Latent space and different views of the different image should be far apart. So, we take two different views of all the images in a batch by applying data augmentation techniques like cropping, Gaussian noise, blurring, etc., then we pass those images to our network to obtain a 1-d feature vector. Then we train our network, So that feature vector of two different views of the same image should be similar, while all the other feature vectors of images in a batch should be as different as possible. By doing so, the model has to learn to recognize the content of the image that remains unchanged under the data augmentations, such as objects which we usually care about in supervised tasks.
Then, we can use that learned reprsentations of the network for out Fine-tuning tasks. 


<div align="center">
  <img width="60%" alt="SimCLR Illustration" src="https://1.bp.blogspot.com/--vH4PKpE9Yo/Xo4a2BYervI/AAAAAAAAFpM/vaFDwPXOyAokAC8Xh852DzOgEs22NhbXwCLcBGAsYHQ/s1600/image4.gif">
</div>
<div align="center">
  An Illustration of SimCLR
</div>


## Dataset
The Dataset that I've used was [STL-10 dataset](https://cs.stanford.edu/~acoates/stl10/).

## Results
The Network which has pre-trained using SimCLR learns very quickly than a randomly initialized network. And also, SimCLR based pre-trained network achieved high-accuracy on the Test dataset.
For more details, view the Ablation Study notebook.

## References
[1] Chen, T., Kornblith, S., Norouzi, M., and Hinton, G. (2020). A simple framework for contrastive learning of visual representations. ([link](https://arxiv.org/abs/2002.05709))

[2] Advancing Self-Supervised and Semi-Supervised Learning with SimCLR. ([link](https://ai.googleblog.com/2020/04/advancing-self-supervised-and-semi.html))

[3] Tutorial on SimCLR from UvA Deep Learning Course. ([link](https://uvadlc-notebooks.readthedocs.io/en/latest/tutorial_notebooks/tutorial17/SimCLR.html))

[4] Original GitHub Repository. ([link](https://github.com/google-research/simclr))
