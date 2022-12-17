# lafayette-gan

This repository holds my project my Independent Study on Machine Learning with a focus on GANs

For this project I found the weights of a DCGAN trained on the CIFAR-10 dataset. The goal was to use transfer learning to learn to create images from a database of images from around Lafayette College. 

The model that I found was a DCGAN, where the Generator and Discriminator have a specific structure that has been found to be highly effective. The Discriminator having 4 downscaling stages each consisting of a convolution, batch normalization, and leaky RELU activation layer. The Generator mirrors this structure but upscales, stages each with a Convolutional Transpose layer, batch normalization, and a RELU activation layer. 

The goal of transfer learning is that the early convolutional stages will likely encode basic image features that the datasets may share, and the last layers encode the highly specific information to the dataset it was trained on. Thus by freezing the early layers, we can save time and computational power by having a better starting point for learning and reduce the need to compute gradients. 

I attempted to use train just the last convolutional layer in both the generator and the discriminator by freezing everything before them. I experimented with a variety of batch sizes, dataset contents, learning rate. It seemed it was not able to find the features of this dataset effectively in the amount of training time it had. In the examples directory I have an example of the grid pattern. This was the result of training overnight where the previous model's classes were still evident in the output. I did attempt a few training sessions with more parameters unfrozen but found that they would crash due to memory allocation maxing out for my hardware. The other example I got many times where the output seemed all white. It seemed that the parameters input could not capture and propogate features from the dataset and training was stuck. 

If I were to continue this project I might try a few things. 
- Selecting images for the dataset with more specific features. The dataset I used was mostly influenced by convinience as I could only download a few at a time and the process took a lot of time. Selecting better images, especially ones with a better target feature set would help the model converge better.
- better hardware obviously would help. There were many models I attempted to load in that would crash due to memory limits very quickly. By limiting batch size I could effectively train this model, but the dataset it was trained on was not perfectly ideal for the output. If I could, a larger model trained for ImageNet would be a better choice. 
- More time for training is not always possible when I am constantly tweaking things and rerunning. Once I have found a good set of hyperparameters, allowing it ample time to train would likely show much better results. 