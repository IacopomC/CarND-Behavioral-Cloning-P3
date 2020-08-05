# **Behavioral Cloning Project**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

This repository contains my implementation of the homonymous open source [project](https://github.com/udacity/CarND-Behavioral-Cloning-P3) part of the [Udacity - Self-Driving Car NanoDegree](http://www.udacity.com/drive).

For a step by step walkthrough of the project see [here](https://iacopomc.github.io/projects/2020-08-03-behavioral-cloning-project/)

Dependencies
---
This project requires:

* [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit)

The lab enviroment can be created with CarND Term1 Starter Kit. Click [here](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) for the details.

The project includes the following files:
* `model.py` containing the script to create and train the model
* `drive.py` for driving the car in autonomous mode
* `model.h5` containing a trained convolution neural network

The simulator can be downloaded [here](https://github.com/udacity/self-driving-car-sim)

Installation
---
Clone the Github Repository and run each cell contained in the Jupiter Notebook `behavioral_cloning.ipynb`

```python
git clone https://github.com/IacopomC/CarND-Behavioral-Cloning-P3
cd CarND-Behavioral-Cloning-P3
jupyter notebook behavioral_cloning.ipynb
```

Functional Code
---

Usage of `drive.py` requires you have saved the trained model as an h5 file, i.e. `model.h5`. To do so, run the jupyter notebook `behavioral_cloning.ipynb`.

Once the model has been saved, it can be used with drive.py using this command:

```sh
python drive.py model.h5
```

and then run the simulator.

The above command will load the trained model and use the model to make predictions on individual images in real-time and send the predicted angle back to the server via a websocket connection.

Note: There is known local system's setting issue with replacing "," with "." when using drive.py. When this happens it can make predicted steering values clipped to max/min values. If this occurs, a known fix for this is to add "export LANG=en_US.utf8" to the bashrc file.

Saving a video of the autonomous agent
---

```sh
python drive.py model.h5 run1
```

The fourth argument, `run1`, is the directory in which to save the images seen by the agent. If the directory already exists, it'll be overwritten.

```sh
ls run1

[2017-01-09 16:10:23 EST]  12KiB 2017_01_09_21_10_23_424.jpg
[2017-01-09 16:10:23 EST]  12KiB 2017_01_09_21_10_23_451.jpg
[2017-01-09 16:10:23 EST]  12KiB 2017_01_09_21_10_23_477.jpg
[2017-01-09 16:10:23 EST]  12KiB 2017_01_09_21_10_23_528.jpg
...
```

The image file name is a timestamp of when the image was seen. This information is used by `video.py` to create a chronological video of the agent driving. Executing the command:

```sh
python video.py run1
```

creates a video based on images found in the `run1` directory. The name of the video will be the name of the directory followed by `'.mp4'`, so, in this case the video will be `run1.mp4`.

Optionally, one can specify the FPS (frames per second) of the video:

```sh
python video.py run1 --fps 48
```

Will run the video at 48 FPS. The default FPS is 60.
