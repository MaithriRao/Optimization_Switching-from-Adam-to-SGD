# SWATS-Optimizer
SWATS optimizer (switching from Adam to SGD)

# Overview
Adaptive optimization methods like RMSprop, Adagrad or Adam generalizes poorly despite their superior training performance when compared to Stochastic gradient descent (SGD). Adaptive optimization methods perform well in the initial training stage but lack in performance in later stages due to unstable and non-uniform learning rate at the end of training. Hence, SGD generalizes better when compared to adaptive methods.

Adam has fast initial progress and good performance with default hyper-parameters, and SGD has good generalization properties. SWATS from the paper [Improving Generalization Performance by Switching from Adam to SGD](https://arxiv.org/pdf/1712.07628.pdf) is a method proposed to automatically switch from Adam to SGD when a triggering condition is satisfied. The SGD learning rate and switchover point from adam to SGD are both learned as a part of training process. The projection of the Adam step on the gradient subspace are monitored and its exponential average as an estimate for the SGD learning rate after the switchover is used. The switchover is triggered when no chnage in this monitored quantity is detected.

# Experiment
To perform analysis we used ResNet-34 and DenseNet architectures on [CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html) dataset. Dataset has 60000 images, which is divided into train set (40000 images), validation set (10000 images) and test set(10000 images).
We then compared the results for three optimizers: Adam, SGD and SWATS, with learning rate 0.001 and threshold 1e-5.

# Setup
* batch_size = 128
* epochs = 150
* initial learning rate = 0.01
* threshold to switch or eposilon = 10^-5 (In the paper \epsilon = 10^-9)
* loss_function = Cross Entropy loss

# Results
| Model | Optimizer | Step | Learning_Rate | Test Accuracy |
| ----- | --------- | ---- | ------------- | ------------- |
|ResNet-34 | SGD |  |  |  |
|ResNet-34 | Adam | - |intial LR: 0.001  | 93% |
|ResNet-34 | SWATS |  |  |  |
|DenseNet-121| SGD |  |  |  |
|DenseNet-121| Adam |  |  |  |
|DenseNet-121| SWATS |  |  |  |


# Conclusion 



