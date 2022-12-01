# Monocular Depth Estimation with Thermal Images

## Preliminary

This project is in collaboration with Carnegie Mellon University and National Robotics Engineering Center [TODO: Link] for off-road autonomous navigation in low-light environments. 

For any questions, please contact Vanshaj Chowdhary (vanshajc@andrew.cmu.edu) or Christoph Mertz (cmertz@andrew.cmu.edu)


## Overview

This repository builds off monodepth2 [TODO: citation] and extends it to support thermal-based depth estimation. Firstly, we leverage the self-supervised approach in monodepth2 where we predict depth and pose from multiple input thermal images, then apply a reprojection loss across all input views. In the case of thermal, we notice this is insufficient supervision and doesn't lead to good results due to the lack of features / low-resolution nature of thermal images. Therefore, we provide additional supervision in the form of pseudo-ground truth signal from a near infrared stereo pair.


## Requirements

Basic requirements:

1. Ubuntu 18
2. CUDA 11+
3. Python 3.6+
4. PyTorch 1.7+


Simply run:
```shell
pip install requirements.txt
```
We ran our experiments with PyTorch 1.7.0, CUDA 11.2, Python 3.6.10 and Ubuntu 18.04.
We have also successfully trained models with PyTorch 1.0, and our code is compatible with Python 2.7. You may have issues installing OpenCV version 3.3.1 if you use Python 3.7, we recommend to create a virtual environment with Python 3.6.6 `conda create -n monodepth2 python=3.6.6 anaconda `.



## Dataset

This project by default accepts datasets with the following file structure:

```
<database root path>
-- <sequence1 dir>
    -- rectified
        -- file1
        -- file2
        -- ...
-- <sequence2 dir>
    -- ...
...
```

Each file is of the form: `p<pod_id>m<module_id>l<lens_id>_<frame_num>_<timestamp>.png`.


## Inference

Inference can be run on pretrained models or your own trained models with the `inference.py` script.

Example command: `python3 inference.py -i sample/thermal1.npy -w weights/pretrained_thermal_model.pt --num_channels 1 -o debug/`


### Pre-Trained Models



## Training

