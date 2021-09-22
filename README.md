# Tensorflow Object Detection in Singularity
This repo contains a Singularity Definition File for making a container that runs the Tensorflow Object Detection API. In addition, it contains a Python script that runs the API's eager few shot detector demo.

## Building the Singularity container
To build the Singularity container with [Remote Builder](https://cloud.sylabs.io/builder), first add your credentials:
    
    singularity remote login

Then run:
    
    singularity -v build --remote tf_od.sif ./singularity/Singularity

## Running the demo
To run the demo with X11 forwarding and error message suppression:

    singularity exec --nv -B ~/.Xauthority /groups/rpalaniv/backed_up/cedar/singularity/singularity_image_files/tf_od.sif python /home/u16/cedar/git/object_detection_singularity/python/eager_few_shot_od_training_tf2_singularity.py &>/dev/null &

I run this in an HPC environment, so putting it in the background and suppressing messages allows me to also monitor the progress with nvtop or nvidia-smi in the same window. Adjust to suit your needs.
