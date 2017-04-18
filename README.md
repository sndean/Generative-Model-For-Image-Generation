# Generative Models For Image Generation
This project uses machine learning techniques for generating real looking artificial images. These images are generated by neural network and we train our neural network to produce meaningful images.

Abstract
---
This repository contains code for artificial image generation using generative models, namely, Variational Autoencoders (VAE) and Generative Adversarial Networks (GAN). VAEs are appealing because they are built on top of standard function approximators (neural networks), and can be trained with stochastic gradient descent. In GAN, we train two models: a generative model G that captures the data distribution, and a discriminative model D that estimates the probability that a sample came from the training data rather than G.

About library and code
---
I have used Keras library for this project. As mentioned on their webpage, it is a high-level neural networks library, written in Python and capable of running on top of either TensorFlow or Theano. It is easy to use and I would highly recommend it.

Code in this repository is heavily influenced from these articles and repositories:
- [Variational Autoencoder using Keras](https://github.com/fchollet/keras/blob/master/examples/variational_autoencoder.py)
- [Keras blog on autoencoders](https://blog.keras.io/building-autoencoders-in-keras.html)
- [DCGAN using Keras](https://github.com/jacobgil/keras-dcgan)
- [OpenAI Generative Models blog](https://openai.com/blog/generative-models/)

Experiments
---
For this project I used my laptop with i5 processor for training. This restricted the traning set size and iterations I could run to get results in acceptable amount of time. The most interesting datasets were [Celebrity Face Dataset (CFD)](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html) and [New York Skyline Dataset (NYSD)](https://www.youtube.com/watch?v=DDo73Njxdqc). CFD provides a large set of images for training, but I used only 9000 images. NYSD was created using frames of a video, partitioned into 1200 training images and 125 test images. These images were later resized (32x32 or 64x64) to feed to the network.

Note: VAE code in this repository takes 64X64 colored images as input, while DCGAN takes 32X32 colored images.

Results
---
Artificial face images generated by VAE (very fast):
![Output with training from 9000 celebrity face](/results/final_face.png)

Skyline images generated by VAE (first row are real images, second row contains generated images):
![Output with training from 1200 skyline images](/results/final_skyline.png)

Artificial face images generated by GAN (took 18 hours):

![Output with training from 9000 celebrity faces](/results/GAN1.png)

Analysis and Conclusion
---
Some benefits and drawbacks of both the techniques are as follows:

- Pros:
    1. VAE - We can compare generated images directly to the originals, which is not possible when using a GAN
    2. VAE - Gives decent results in less training time
    3. GAN - Can generate the sharpest images
- Cons:
    1. VAE - Network tends to produce more blurry images
    2. GAN - No way of determining which initial noise values would produce a particular picture

Execution Steps
---
To run GAN code you will need tensorflow backend with "image_dim_ordering" set to "th" in ~/.keras/keras.json file. Also you need to set path for dataset in dcgan.py file. Use following command to run:
```
python dcgan_face.py --mode train --batch_size 128
```

To run VAE code you will need tensorflow backend with "image_dim_ordering" set to "tf" in ~/.keras/keras.json file. Also you need to set path for dataset in vae_landscape_64.py file. Use following command to run:
```
python vae_landscape_64.py
```

References
---
