# SimCLR - A Simple Framework for Contrastive Learning of Visual Representations

Transfer Learning has become a standard method for using Deep learning models especially in the low data regime. Transfer Learning consists of 2 steps, Pre-training and Fine-tuning. Pre-training phase requires a large labelled dataset (supervised learning). How can we learn representations from unlabeled dataset? Self-supervised learning (SSL) addresses this question. SSL is successful in NLP (Ex: BERT, GPT) but not fruitful in CV. However, there has been a recent trend in applying SSL to CV, among those techniques Contrastive learning and Non-Contrastive learning are popular. In Contrastive learning, the model is trained to produce similar embeddings for different views of the same image (positive pair) but dissimilar embeddings for different images (negative pair). Whereas in Non-contrastive learning, model is trained to produce similar embeddings only for the positive pair, without requiring negative pair. But Non-contrastive learning method suffers from a model collapse, when the model outputs constant vectors for the positive pair; a lot of methods have been proposed to address this issue (Ex: BYOL, W-MSE, VicReg).

SimCLR falls under the Contrastive learning category. Compared to other contrastive learning methods, SimCLR doesn’t require specialized network architectures or a memory bank. It makes use of multiple data augmentation such as random cropping, color distortion, rotation and gaussian blurring to produce different views of an image batch. The network architecture has 2 parts, Encoder (ResNet) and non-linear projection head (Fully connected layer with ReLU activation) which is applied to Encoder’s output. The contrastive loss (InfoNCE) is applied to the projection head’s latent space. During training, a single batch of images is fed to the data augmentation pipeline to produce two batches of different views of the same input batch, and then it is passed to the network to produce embeddings. Embeddings for both the batches are inputted to scalar-valued loss function to calculate the loss and the network is updated to minimize this loss. In doing so, the network will learn meaningful representations and can be applied to various downstream tasks. Though the proposed technique is simple, it performs better than the previous SOTA results in contrastive learning and matches the performance of the supervised baseline. But the main drawback of the method is, it requires a large batch size and large network to perform well which is computationally expensive.



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
