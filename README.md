# hyperchamber-gan
A GAN(generative adversarial network) that you can run from the command line.  Integrates with hyperchamber to find the best GAN for your dataset.

## Screenshots

<img src='https://raw.githubusercontent.com/255BITS/HyperGAN/master/samples/decent-1.png'/>
<img src='https://raw.githubusercontent.com/255BITS/HyperGAN/master/samples/decent-2.png'/>
<img src='https://raw.githubusercontent.com/255BITS/HyperGAN/master/samples/decent-3.png'/>
<img src='https://raw.githubusercontent.com/255BITS/HyperGAN/master/samples/creepy.png'/>
<img src='https://raw.githubusercontent.com/255BITS/HyperGAN/master/samples/decent-4.png'/>
<img src='https://raw.githubusercontent.com/255BITS/HyperGAN/master/samples/decent-5.png'/>
<img src='https://raw.githubusercontent.com/255BITS/HyperGAN/master/samples/decent-6.png'/>
<img src='https://raw.githubusercontent.com/255BITS/HyperGAN/master/samples/decent-7.png'/>


## Goals

* Fast
* Flexible - any data size
* Multi-format (image/audio)
* Extensible
* No preprocessing if possible
* Easy to deploy

## Architecture

HyperGAN is a flexible GAN framework.  With swap out the discriminator, use a different training technique, switch data types, use a different loss function, and more.
```
```

## Discriminators

The discriminators job is to tell if something is real or fake.  In hypergan, a discriminator can also be a classifier.

If the discriminator is a classifier, we treat this part of the network as a softmax classifier.

To put this as an example, if we were to classify the difference between apples and oranges, most classifiers would classify a pear as an apple, having never seen a pear before.
A classifier trained with a GAN will include additional information - a discriminator which could identify the pear as a fake image(in the context of worlds consisting of only apples and oranges).

### Discriminators

Implemented discriminators: TODO


### Trainers

## Server mode

```
  hypergan server=True
```
TODO 

## Formats

* jpg
* png
* wav(experimental)
* mp3(experimental)

## Features

* Efficient GAN implementation
* Semi-supervised or unsupervised learning(works with and without labels)
* Variational methods
* InfoGAN-inspired categories
* Minibatch normalization
* Adversarial inference

## Arguments

* --directory, required, specifies which parent directory to use.  Each subdirectory is a different classification.  For example if you have 'data/a' and 'data/b', files in 'data/a' will be represented internally as the one-hot vector [1,0].
* --channels, optional(default 3), the number of channels in your images.  Black and white images typically only have 1.
* --width, optional(default 64), the width of each image.  If smaller than this width, the image will be centered and cropped.
* --height, optional(default 64), the height of each image.  If smaller than this height, the image will be centered and cropped.
* --format, optional(default png), file format of the images.  Only supports jpg and png for now.
* --epoch, optional(default 10), number of epochs to run before exiting
* --load_config, optional(default None), the config uuid from hyperchamber to run
* --save_every, optional(default 0), after this many epochs, the network weights/checkpoint are saved into the 'saves' directory.

## Running

First, choose a dataset.  If you use one of the standard datasets, you can find a config that will work with hyperchamber.  If using a new/different dataset, start with a 'Search', detailed below.

For example, the following command will run a configuration with id [https://hyperchamber.255bits.com/ba3051e944601e2d98b601f3347df0b1/40k_overfit_3:1.2/samples/25e15455541d84bb76dcc4c8f8dce5a1](7543d9f4cc6746b68b3247e7c258a50e)

Note: Requires a (free) account at hyperchamber to run.

```
  python3 directory-gan.py --directory test/ --channels 3 --width 64 --height 80 --format jpg --epoch 10000 --load_config 6d09d839d3b74a208a168dc3189c3f59 --save_every 10
```


## Searching

````
  python3 directory-gan.py --directory test/ --channels 3 --width 64 --height 80 --format jpg --epoch 1
```

You can review the results on hyperchamber.

## How to use
To use on any data:

* Run config sweep with hyperchamber
* Run your favorite config for longer


## Papers

* GAN
* DCGAN
* InfoGAN
* Improved GAN
* Adversarial Inference

## Sources

* DCGAN
* InfoGAN
* Ian's GAN


<img src='https://raw.githubusercontent.com/255BITS/HyperGAN/master/samples/magic-1.png'/>

# Citation

If you wish to cite this project, do so like this:

```
  TOD
```
