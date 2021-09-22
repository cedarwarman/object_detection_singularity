# Tensorflow Object Detection in Singularity
This repo contains a Singularity Definition File for making a container that runs the [Tensorflow Object Detection API](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2.md). It also contains a Python script that runs a modified version of the API's [Eager Few Shot Detector demo](https://github.com/tensorflow/models/blob/master/research/object_detection/colab_tutorials/eager_few_shot_od_training_tf2_colab.ipynb).

## Building the Singularity container
To build the Singularity container with [Remote Builder](https://cloud.sylabs.io/builder), first add your credentials:
    
    singularity remote login

Then run:
    
    singularity -v build --remote ./singularity/tf_od.sif ./singularity/Singularity

## Running the demo
To run the demo with X11 forwarding and error message suppression:

    singularity exec --nv -B ~/.Xauthority ./singularity/tf_od.sif python3 ./python/eager_few_shot_od_training_tf2_singularity.py &>/dev/null &

I use this in an HPC environment, so putting it in the background and suppressing messages allows me to monitor the progress with `nvtop` or `nvidia-smi` in the same window. Adjust to suit your needs.
