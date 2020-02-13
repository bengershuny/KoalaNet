# KoalaNet
KoalaNet's goal is to develop a pipeline for creating high quality photos in low light, improving on existing mechanisms for brightening underexposed images.

I am implementing a paper by Chen Chen, Qifeng Chen, Jia Xu, and Vladlen Koltun entitled “Learning to See in the Dark.” This paper takes a novel approach to processing underexposed images – creating a fully convolutional autencoder pipeline that takes in underexposed images and produces images with proper exposure, saturation, sharpness, and contrast without the noise and artifacts that existing processing pipelines produce. Instead of taking PNG or JPG images as inputs, it takes raw image sensor data from a camera, which preserves far more information and allows for better and more generalizable results.

<h2>Dataset</h2>
The dataset was acquired from the authors of the original paper, containing 2,000 underexposed images mapped to 250 light versions (107 GB). The images are raw sensor data from a Sony camera which uses a Bayer filter, common among modern cameras, allowing this model to be generalizable.

<h2>Model Architecture</h2>
The model architecture is a fully convolutional autoencoder with skip connections (Figure 1). More specifically, I use strided convolution instead of max pooling for downsampling, and single strided convolutional layers between each downsampling and upsampling layer. Raw inputs are demosaiced in preprocessing, fed through the model as four Bayer channels, and output as 12 color channels that are pixel-shuffled into a 3-channel RGB output (Figure 2).

<h2>Training</h2>
Trained the model using an Adam optimizer with a learning rate of 1e-4 for the first 2000 epochs, switching to 1e-5  for the next 2000 to improve convergence. The model trained for 48 hours on a Tesla P4 GPU with a batch size of 32.
