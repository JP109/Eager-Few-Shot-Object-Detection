# Eager-Few-Shot-Object-Detection
The goal of this notebook is to detect zombies, using only five training images to train the classifier.

We will retrain only the classification layer of the RetinaNet(we need to retrain them as they were trained on the coco dataset, which does not have a zombie class), whose architecture(configuration) and weights(coco checkpoints, except for classification layer) will be downloaded separately as config and tar files respectively. The model will be loaded and built from the config file using model_builder.build() utility of Object Detection API. and the weights would be loaded using .restore()

Our model(classification layer) will be Few Shot retrained, on just five novel zombie images, which were not present in the coco dataset on which the RetinaNet was originally trained on.

We will annotate the five training images manually first using colab_utils.annotate() utility of Object Detection API.

Training will be a custom loop, which will run in Graph mode, as we only need to train selected layers.
