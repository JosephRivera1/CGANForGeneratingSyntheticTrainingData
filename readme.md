# Using cGANs for Generating Synthetic Training Data

This project demonstrates using a conditional gan for creating synthetic images to train a ResNet18 Classifier.

Download the Chest X-Ray Pneumonia Dataset from Kaggle: https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia

First, Use the ```TrainConditionalGenerativeAdversarialNetworkCGANExample.mlx``` script to generate the GAN model and new imagery. You simply need to point the image datastore to your training dataset in the following heirarchy ```dataset_top_level_name\className\class_image1.png```. You can include as many classes and as many images as you wish.

After running through the training code, you can generate new samples and include that in a new folder with the same heirarchy. Next we'll train the classifier.

Use the ```experimentManager``` function to create a new project. Next link the ```Experiment1_setup1.mlx``` as your setup function, and create your desired hyperparameters in the hyperparameter table.

I have included the following hyperparameters:

```params.GANData``` = [1 0] trains with and without GAN data, you must specify paths to these image directories in the setup script.

```params.augmentation``` = [0 1] you can run experiments with and without augmentations specified.

```params.transformFunction``` is not used in this experiment however, if you'd like to include non-standard augmentations to your data, this is the way to do it.

```params.network``` allows you to swap between different ResNet18 networks and has the ```custom``` case defined in case you would like to use your own model.

```params.inputNormalization``` you may also trade input normalization schemes.

as well as the following training options ```params.numEpochs```, ```params.miniBatchSize```, ```params.myInitialLearnRate```

a custom metric function can also be defined for evaluating testing data in addition to the validation data, just link ```testingAcc.mlx``` to the metrics list.
