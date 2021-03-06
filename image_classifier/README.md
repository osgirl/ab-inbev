# ab-inbev

## Image Classifier

### Install Tensorflow
```
// Mac OS X, CPU only, Python 3.4 or 3.5:
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-0.11.0rc1-py3-none-any.whl
$ pip3 install --upgrade $TF_BINARY_URL

// For the Raspberry PI
$ wget https://github.com/samjabrahams/tensorflow-on-raspberry-pi/releases/download/v0.11.0/tensorflow-0.11.0-cp27-none-linux_armv7l.whl
$ sudo pip install tensorflow-0.11.0-cp27-none-linux_armv7l.whl

```

### Training

* Save the images in jpg format.
* Drop them into the *image_classifier/tf_files/caps* folder. Create a subfolder for each brand. The name of the subfolder will be used by the script as the label for the images.  
* From the *image_classifier* folder, run:

```
$ sudo python3 retrain.py \
--bottleneck_dir=tf_files/bottlenecks \
--how_many_training_steps 500 \
--model_dir=tf_files/inception \
--output_graph=tf_files/retrained_graph.pb \
--output_labels=tf_files/retrained_labels.txt \
--image_dir tf_files/caps
```

**NOTE**: remove *the --how_many_training_steps* parameter to use the default (4000) and get better results.

### Guessing

The *classifier_usage.py* file shows how to import the module and request an image guess.  
The example usage loads:

* the image classifier module from *classifier.py*.
* a test image from *image_classifier/text_images*.