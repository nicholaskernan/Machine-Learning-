# Machine-Learning-

The "MultiCaptcha" file above shows a convolutional neural network created with PyTorch that was trained to recognize Captcha images.

Each Captcha image has four characters, so its label would be a tensor with four entries. The labels are numerical, so "A" is a 10, "B" is 11, etc. As such, a Captcha image with characters "RIJ0" would have the label [27, 18, 19, 0]. 

Each image has resolution 60 x 160 with 3 color channels. As such, each image is 3x60x160, and the overall tensor of all 500 training images is 500x3x60x160. 

The simplest classifier would have only two possible labels (e.g. 1-cat, 0-noncat). As such, it may have a few convolution layers to discover features, then a few fully connected layers where the last layer outputs a number between 0 and 1, the probability of the image being a cat. 

A bit more complex is a classifier that e.g. analyzes Captcha images of only one character. It would need 36 outputs, where output 0 is the probability the image is the character 0, 1 is 1...and its final output is the probability of Z. These values are normalized to sum to 1, and the max is taken as its prediction. 

Finally, the current multi-character classifier uses this idea, but with four sets of fully connected layers for the output, since it is classifying multiple characters simultaneously. It never needs to be hard coded that e.g. the first set of fully connected layers should only look at the first character, that is done automatically by repeatedly having a high cost whenever it doesn't successfully classify the first character. 
