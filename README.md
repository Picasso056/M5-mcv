# Scene Understanding for Autonomous Vehicles with deep neural networks
Master in Computer Vision - M5 Visual recognition

## Project description
The goal of this project is to study the use of deep learning to semantically segment images and extract some knowledge of the scene. To do it we will use different types of neural networks.

Download the [Overleaf document](https://www.overleaf.com/read/zbhrkkjvwkjv)

## Code Changes

- Modified Optimizer_factory from Tools folder, added learning rate parameter to the Adam and SGD optimizers in order to be useful.
- Added new CNN models for classification: Resnet50 and InceptionV3. Using the Keras implementation are available in the configuration file in the parameter "model_name".
- Support for Weight decay integrated for this Models: VGG16, VGG19, Resnet50 and InceptionV3. The Weight Decay use L2 normalization and is activated when the value of the parameter "weight_decay" of the configuration file is higher than 0.

## Configuration Hints

- Resize dataset: remember that Resnet50 and inceptionV3 need a resize for the dataset in order to process the input image properly and work. Minimum input size [139,139] for InceptionV3 and [199,199] for Resnet50. When the dataset is smaller than this size like TT100K, use the reasize parameter close to the minimum in order to penalize minimally the computation time for epoch only in the models with this requeriments.
- TensorFlow try to allocate memory on the GPU even if don't fit firstly, if you use batch sizes inapropiate or resize the image to higher dimensions you can experiment a drastical increment in the epoch calculation time, so it's improtant to take into account.
- Use weight decay with lower values (exponent -4 or -5), high values penalyze the weight and allows less variations needing more time to train and higher loss values, still the CNN will learn, but not appropriately.

## Test Realized

Tested the Weight normalization behaviour in the models trying a weight decay value of 0.1, 0.01 and 0.001 in VGG16.
- 0.1: High starting loss, around 150, each epoch reduce this loss constantly but the training step is really slow per epoch, reducing the loss in the validation data but poor changes in the accuracy score. Too slow and higher penalization for weight is not useful.
- 0.01: Similar to the previous case, but the lost start at 20 and drops slowly, being better but still too slow to be really useful.
- 0.001 and above: train fast, similar loss speed like without weight decay but with a better control of the train step and normalizing the weights.  

## Project slides
- Google slides for [Week 1](https://docs.google.com/presentation/d/1jiS8scHFZGNVeYUV8wJpG2AjLw9J-iSCpzYKUXmoAWQ/edit?usp=sharing)
- Google slides for [Week 2](https://docs.google.com/presentation/d/10zmaSSAL-29dpJZ-WZNhcl8yIUSg30iNnNcKlxDesTc/edit?usp=sharing)
- Google slides for Week 3 (T.B.A.)
- Google slides for Week 4 (T.B.A.)
- Google slides for Week 5 (T.B.A.)
- Google slides for Week 6 (T.B.A.)
- Google slides for Week 7 (T.B.A.)

## Groups
 - [Group 6:](https://github.com/LLebronC/mcv-m5)
  - Jose Luis Gómez (joseluis-master@hotmail.com)
  - Luís Lebron(luis.lebron@e-campus.uab.cat)
  - Axel Barroso
  - Hassan Ahmed
  
## Reference
Simonyan, K., & Zisserman, A. (2014). Very deep convolutional networks for large-scale image recognition. arXiv preprint arXiv:1409.1556. [Summary](Summaries/VGG.md)

He, K., Zhang, X., Ren, S., & Sun, J. (2016). Deep residual learning for image recognition. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (pp. 770-778). 

Szegedy, C., Vanhoucke, V., Ioffe, S., Shlens, J., & Wojna, Z. (2016). Rethinking the inception architecture for computer vision. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (pp. 2818-2826). [Summary](Summaries/InceptionV3.md)
