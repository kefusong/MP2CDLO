# MP2CDLO:Self-supervised Learning of Reconstructing Deformable Linear Objects under Single-Frame Occluded View<br>
<!-- [[`arXiv`](https://arxiv.org/abs/2307.14726)]
[[`BibTex`](#citation)]
[[`Poster`](./assets/ICCV_Poster.pdf)]

![Framework image](./assets/pipeline.png) -->
## <center> Framwork
![alt text](assets/framework.png)
##### <center> <span style="color: rgb(41, 34, 33); font-weight:bold"> A. Self-supervised DLO Point cloud completion, B. Ordered key points generation.</span>

## Introduction
[**MP2CDLO:Self-supervised Learning of Reconstructing Deformable Linear Objects under Single-Frame Occluded View**]<br>
Song Wang,Guanghui Shen,Shiru WU and Dan Wu

**[abstract]** <span style="color: rgb(3, 168,158); font-weight:bold">Deformable linear objects (DLOs)</span>,such as ropes, cables, and rods, are common in various scenarios, and <span style="color: rgb(3, 168,158); font-weight:bold">accurate occlusion reconstruction</span>of them are <span style="color: rgb(3, 168,158); font-weight:bold">crucial for effective robotic manipulation. </span>Previous studies for DLO reconstruction eitherrely on supervised learning, which is limited by the availability of labeled real-world data, orgeometric approaches, which fail to capture global features and often struggle with occlusions and complex shapes. This paper presents<span style="color: rgb(102, 8, 116); font-weight:bold">a novel DLO occlusion reconstruction framework</span> that integrates self-supervised point cloud completion with traditional techniques like clustering, sorting, and fitting to enerate ordered key points. <span style="color: rgb(102, 8, 116); font-weight:bold">A memory module</span> is proposed to enhance the self-supervised training process by consolidating prototype information, while <span style="color: rgb(102, 8, 116); font-weight:bold">DLO shape constraints </span>are utilized</span> to improve reconstruction accuracy. Experimental results on both synthetic and real-world datasets demonstrate that our method <span style="color: rgb(40,61, 126); font-weight:bold">outperforms state-of-the-art algorithms</span>, particularly in scenarios involving <span style="color: rgb(40,61, 126); font-weight:bold">complex occlusions and intricate self-intersections.</span>



## Installation
#### Requirements
- Python >= 3.7
- CUDA 11.7
- Pytorch >= 1.12
- open3d>=0.14.1
- transforms3d
- pytorch3d
- pyyaml
- opencv-python
- tensorboard
- tqdm
- timm==0.4.5
- scipy
- torch_kmeans
- geomdl
- bezier
- scikit-learn

#### Or you can setup the environment using `conda`:
- Create conda environments and active it.
```
conda create -n MP2CDLO python=3.9
conda activate MP2CDLO
```
- Install Pytorch
```
pip install torch==1.13.0+cu117 torchvision==0.14.0+cu117 torchaudio==0.13.0 --extra-index-url https://download.pytorch.org/whl/cu117
```
- Download the package of pytorch3d and install
```
https://anaconda.org/pytorch3d/pytorch3d/files
conda install https://anaconda.org/pytorch3d/pytorch3d/0.7.5/download/linux-64/pytorch3d-0.7.5-py39_cu117_pyt1130.tar.bz2
```
- Install the other packages using requirements
```
pip install -r requirements.txt
```
#### Some packages are needed to train and evaluate the model.
- Pytorch Chamfer Distance
- pointops_cuda

To build this, run the command below:
```
python setup.py install --user
```
**Remenber to delete the last build files by other cofig environment!!! 
Complie from scratch on your own environment.**

## Preparing the Data


1. 3D-EPN dataset [[`Google Drive`](https://drive.google.com/file/d/1pq0lp8D54lBF9npg-YmXRExbDKM_DUDo/view?usp=sharing)] 

2. Please download the dataset to `./data/EPN3D_rope/`

**The layout should look like this**
```
├── cfgs
├── data [This is your dataroot]
│   ├── rope_dict.json
│   ├── EPN3D_rope
│   │   ├── EPN3D.json
│   │   ├── rope
│   │   │   ├── complete
│   │   │   │   ├── label_0000.npy
│   │   │   │   ├── ......
│   │   │   ├── partial
│   │   │   │   ├── pointcloud_0000.npy
│   │   │   │   ├── ......
```

## Training
To train a self-supervised DLO Point cloud completion model from scratch, run:

```
python train.py --config ./cfgs/EPN3D_models/MP2CDLO.yaml --exp_name your_exp_name
```

## Demo 

We provide pre-trained model weights on the real-world data.You can directly with the following code.
```
python ./demo/src/demo.py
```
 

<!-- ## <a name="citation"></a>Citing P2C

If you find our work useful to your research, please consider citing:

```BibTeX
@misc{cui2023p2c,
      title={P2C: Self-Supervised Point Cloud Completion from Single Partial Clouds},
      author={Ruikai Cui and Shi Qiu and Saeed Anwar and Jiawei Liu and Chaoyue Xing and Jing Zhang and Nick Barnes},
      year={2023},
      eprint={2307.14726},
      archivePrefix={arXiv},
}
``` -->

## Acknowledgement
This code is standing on the shoulders of giants. We want to thank the following contributors that our code is based on:[Partial2Complete](https://github.com/CuiRuikai/Partial2Complete), [Dloftbs](https://github.com/PPI-PUT/cable_observer/tree/master) and [PoinTr](https://github.com/yuxumin/PoinTr). 

Thanks for the useful advice given by the following contributors: [Kangchen Lv](https://github.com/Kangchen-Lv/DLO-perception) and [Zhaole Sun](https://github.com/TheGoblinTechies/DLO-perception-pipeline).
