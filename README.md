# KittiClass

KittiClass performance road type classification using Kitti Data. The model is able to distinguish between different road types. The data was generated by combining GPS information with Open Street Map information. Check out the paper of [Wei-Chiu .et al](https://arxiv.org/abs/1606.07415) for a desciption on how the data is generated. Out [MultiNet](https://github.com/MarvinTeichmann/MultiNet) comes with a detailed desciption of this model. 

<img src="data/examples/um_000032_out.png" width="288"> <img src="data/examples/umm_000059_out.png" width="288"> <img src="data/examples/007241_out.png" width="288"> 

<img src="data/examples/007109_out.png" width="288"> <img src="data/examples/007034_out.png" width="288"> <img src="data/examples/007028_out.png" width="288">

This project is very similar to the [KittiSeg](https://github.com/MarvinTeichmann/KittiSeg#kittiseg) and [KittiBox](https://github.com/MarvinTeichmann/KittiBox#kittibox) project. Unfortunately the training data for KittiClass is not public. You can still use `demo.py` to view results or use `train.py` to train on your own data. Latter will however not work out of the box. If you are new to tensorflow, I recommend to use [KittiSeg](https://github.com/MarvinTeichmann/KittiSeg#kittiseg) as starting point. The code is build to be compatible with the [TensorVision](http://tensorvision.readthedocs.io/en/master/user/tutorial.html#workflow) backend which allows to organize experiments in a very clean way.

## Requirements

The code requires [Tensorflow 1.0](https://www.tensorflow.org/api_docs/) as well as the following python libraries: 

* matplotlib
* numpy
* Pillow
* scipy

Those modules can be installed using: `pip install numpy scipy pillow matplotlib` or `pip install -r requirements.txt`.


## Setup

1. Clone this repository: `https://github.com/MarvinTeichmann/KittiClass`
2. Initialize all submodules: `git submodule update --init --recursive`


## Tutorial

### Getting started

Run: `python demo.py --input_image data/demo/demo.png` to obtain a prediction using [demo.png](data//demo/demo.png) as input.

Run: `python train.py --hypes hypes/KittiClass.json` train a KittiClass model.

### Manage Data Storage

KittiSeg allows to separate data storage from code. This is very useful in many server environments. By default, the data is stored in the folder `KittiClass/DATA` and the output of runs in `KittiClass/RUNS`. This behaviour can be changed by setting the bash environment variables: `$TV_DIR_DATA` and `$TV_DIR_RUNS`.

Include  `export TV_DIR_DATA="/MY/LARGE/HDD/DATA"` in your `.profile` and the all data will be downloaded to `/MY/LARGE/HDD/DATA/data_road`. Include `export TV_DIR_RUNS="/MY/LARGE/HDD/RUNS"` in your `.profile` and all runs will be saved to `/MY/LARGE/HDD/RUNS/KittiClass`

### Modifying Model & Train on your own data

The model is controlled by the file `hypes/KittiClass.json`. Modifying this file should be enough to train the model on your own data and adjust the architecture according to your needs. A small sample of the [train](data/train.txt) and [val](data/val.txt) is provided.

Once again, I would like to point you to [KittiSeg](https://github.com/MarvinTeichmann/KittiSeg#kittiseg) documentation. It contains more explanation on how to utilize your own data.

# Citation

If you benefit from this code, please consider citing our paper:

```
@article{teichmann2016multinet,
  title={MultiNet: Real-time Joint Semantic Reasoning for Autonomous Driving},
  author={Teichmann, Marvin and Weber, Michael and Zoellner, Marius and Cipolla, Roberto and Urtasun, Raquel},
  journal={arXiv preprint arXiv:1612.07695},
  year={2016}
}
```

If you use the Classification Data please cite: 

```
@article{ma2016find,
  title={Find your Way by Observing the Sun and Other Semantic Cues},
  author={Ma, Wei-Chiu and Wang, Shenlong and Brubaker, Marcus A and Fidler, Sanja and Urtasun, Raquel},
  journal={arXiv preprint arXiv:1606.07415},
  year={2016}
}
```

