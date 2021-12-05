# gelatto
Who doesn't love gelato

HI! the code will be available soon. Meanwhile, enjoy our [paper](https://arxiv.org/pdf/2111.00231.pdf)!

# Two Heads are Better than One: Geometric-Latent Attention for Point Cloud Classification and Segmentation 

![Intro figure](img/gelatto_banner.png)

[comment]: <> (<p align="center">)

[comment]: <> (  <img width="460" height="300" src="https://gitlab.com/cuevhv/gelatto/-/blob/main/img/gelatto_logo.png">)

[comment]: <> (</p>)
## Dependencies
- pytorch >=1.6
- pandas
- seaborn
- scikit-learn

To visualize the points or do some sandbox experiments with points
- open3d 0.8.0 or 0.7.0
- torch gemetric (https://pytorch-geometric.readthedocs.io/en/latest/notes/installation.html)

## Datasets
- shapenet: 
  - Download: https://shapenet.cs.stanford.edu/ericyi/shapenetcore_partanno_segmentation_benchmark_v0.zip
- modelNet40:
  - Download: https://shapenet.cs.stanford.edu/media/modelnet40_normal_resampled.zip
- S3DIS:
  - Download: https://shapenet.cs.stanford.edu/media/indoor3d_sem_seg_hdf5_data.zip
  - Preprocessing files:
  
## Folder management
You have to create the following folders and subfolders:
```bash
├── dataset
│   ├── shapenet
│   ├── s3dis
│   ├── modelnet40
├── weights
└── results
```

All the datasets have to be inside the folder `dataset`:
- shapenet
  - dataset/shapenetcore_partanno_segmentation_benchmark_v0
- modelnet40
  - dataset/modelnet40
- s3dis
  - download the dataset from [link](https://drive.google.com/file/d/1-co_MyDk-qsc5cvlhNkG1z7Mlr4F1zUA/view?usp=sharing) and place it in the order given bellow:
  - dataset/s3dis/ply_version
  - dataset/s3dis/train_{files.txt, bins2500.csv, start_pos.txt} 
  - dataset/s3dis/test_{files.txt, bins.csv, start_pos.txt}
- gelatto/pointnet2
  
  We need FPS sampling and KNN to group the points. Therefore, we have to install [pointnet2](https://github.com/sshaoshuai/Pointnet2.PyTorch) library running the following command:
  ```bash
    cd gelatto/pointnet2
    python setup.py install
    cd ../
  ```  
## Experiments
**Note: Only run the experiments using modelnet40!!!**

the folder `scripts` has an example for the different experiments you can launch.

You need to modify the `data_folder` variable with the absolute path of folder that contains the dataset.

To test the network, you have to change the variable `train` to `0` and provide the path to the `weights`. This path can be a relative path.


- shapenet: There are 2 type of networks:
  - `singe_net.sh` 1 Network per object which segments the parts for the specific object.
  - `mult_head.sh` Multi-head output network which receives as input any object and segments the parts for the given object.
- modelnet40
  - `net.sh`
- s3dis
  - `net.sh`

  
## Docker
go do docker and execute `sudo docker build .`

execute the following command:
`docker run  -it --rm --gpus all -v $(path_to_the_repo)/transform_registration:/workspace/ -u $(id -u):$(id -g) $DOCKER_ID bash scripts/$dataset/$script.sh`

