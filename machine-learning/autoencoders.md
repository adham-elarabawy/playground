# Autoencoders

### What is an autoencoder?

An autoencoder is a type of neural network that attempts to learn an approximation of the input function in a lower-dimensional space -- usually called the **latent space**. 

![](../.gitbook/assets/image%20%2812%29.png)

Once the model is trained, it can be split up into the `encoder` and the `decoder` sections, which allow us to compress an input into a lower-dimensional latent space. 

They're extremely useful in being able to compress high-dimensional data into lower \(more fundamental\) dimensions, which is a notion that lends itself very nicely to image segmentation and data compression.

Intuitively, an autoencoder can act like an unsupervised version of [PCA \(principal component analysis\)](../engineering/principal-component-analysis.md).

### Denoising Autoencoder Example

A denoising autoencoder works by applying a noise mask on the input data, then training it with a loss computed with reference to the original \(un-noised\) image, which forces the encoder to capture the true features \(and avoid noise\). The result is a model that can take in a noisy image and spew out a lower-dimensional representation \(latent space representation\) of the true image, which can then be reconstructed using the `decoder` to result in a close-to-original _denoised_ output.

Here is an example of the results from a denoising autoencoder, implemented [here](https://github.com/adham-elarabawy/playground/blob/master/machine-learning/autoencoder/autoencoder.py). 

![](../.gitbook/assets/image%20%283%29.png)





