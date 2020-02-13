# KoalaNet
KoalaNet's goal is to develop a pipeline for creating high quality photos in low light, improving on existing mechanisms for brightening underexposed images.

I am implementing a paper by Chen Chen, Qifeng Chen, Jia Xu, and Vladlen Koltun entitled “Learning to See in the Dark.” This paper takes a novel approach to processing underexposed images – creating a fully convolutional autencoder pipeline that takes in underexposed images and produces images with proper exposure, saturation, sharpness, and contrast without the noise and artifacts that existing processing pipelines produce. Instead of taking PNG or JPG images as inputs, it takes raw image sensor data from a camera, which preserves far more information and allows for better and more generalizable results.
