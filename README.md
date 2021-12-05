# gelatto
Who doesn't love gelato

HI! the code will be available soon. Meanwhile, enjoy our [paper](https://arxiv.org/pdf/2111.00231.pdf)!

# Two Heads are Better than One: Geometric-Latent Attention for Point Cloud Classification and Segmentation 

![Intro figure](img/gelatto_banner.png)

[comment]: <> (<p align="center">)

[comment]: <> (  <img width="460" height="300" src="https://gitlab.com/cuevhv/gelatto/-/blob/main/img/gelatto_logo.png">)

[comment]: <> (</p>)

## Performance
### S3DIS area 5
|Method | OA    |       mIoU    |       mAcc    | ceiling       | floor         | wall          | beam          | column        | window        | door          | table         | chair         | sofa          | bookcase      | board         | clutter        |
|:---   | :---: |    :---:      |       :---:   | :---:         | :---:         | :---:         | :---:         | :---:         | :---:         |  :---:           | :---:         | :---:         | :---:         | :---:         | :---:         | :---:          |
|PointNet    | 41.1 | 49.0   | 88.8    | 97.3  | 69.8 | **0.1**  | 3.9    | 46.3   | 10.8 | 59.0    | 52.6  | 5.9  | 40.3     | 26.4  | 33.2     |
|SegCloud   | 48.9 | 57.4 | 90.1    | 96.1  | 69.9 | 0.0    | 18.4   | 38.4   | 23.1 | 70.4  | 75.9  | 40.9 | 58.4     | 13.0    | 41.6     |
|FPConv       | 62.7 | 68.9 | **94.6**    | 98.5  | 80.9 | 0.0    | 19.1   | 60.1   | 48.9 | 80.6  | 88.0    | 53.2 | 68.4     | 68.2  | 54.9     |
|MinkowskiNet  | 65.3 | 71.7 | 91.8    | 98.7  | **86.2** | 0.0    | **34.1**   | 48.9   | 62.4 | 81.6  | 89.8  | 47.2 | 74.9     | 74.4  | 58.6     |
|KPConv       | 67.1 | 72.8 | 92.8    | 97.3  | 82.4 | 0.0    | 23.9   | 58.0     | **69.0**   | 81.5  | 91.0    | 75.4 | **75.3**     | 66.7  | 58.9     |
|PCT  | 61.3 | 67.6 | 92.5   | 98.4  | 80.6 | 0.0    | 19.4  | 61.6     | 48.0   | 76.6  | 85.2    | 46.2 | 67.7     | 67.9  | 52.3    |
|Bilateral  | 65.4 | 73.1 | 92.9 | 97.9 | 82.3 | 0.0 | 23.1  | **65.5** | 64.9 | 78.5 | 87.5 | 61.4 | 70.7 | 68.7 | 57.2 |
|**Ge-Latto (ours)** |**69.2** | **75.9** | 94.5 | **99.2** | 84.0 | 0.0 | 24.5 | 56.3 | 68.9 | **84.2** | **92.4** | **82.8** | 70.9 | **76.9** | **64.6**          |


### S3DIS 6-fold cross-validation
|Method | OA    |       mIoU    |       mAcc    | ceiling       | floor         | wall          | beam          | column        | window        | door          | table         | chair         | sofa          | bookcase      | board         | clutter        |
|:---   | :---: |    :---:      |       :---:   | :---:         | :---:         | :---:         | :---:         | :---:         | :---:         |  :---:           | :---:         | :---:         | :---:         | :---:         | :---:         | :---:          |
|PointNet      | 78.5          | 47.6          | 66.2          | 88.0          | 88.7          | 69.3          | 42.4          | 23.1          | 47.5          | 51.6          | 54.1          | 42.0          | 9.6           | 38.2          | 29.4          | 35.2          |
|PointCNN      | 88.1          | 65.4          | **88.1**      | 94.8          | **97.3** | 75.8          | 63.3          | 51.7          | 58.4          | 57.2          | 71.6          | 69.1          | 39.1          | 61.2          | 52.2          | 58.6           |
|SPGraph       | -             | 62.1          | 73.0          | 89.9          | 95.1          | 76.4          | 62.8          | 47.1          | 55.3          | 68.4          | 73.5          | 69.2          | 63.2          | 45.9          | 8.7           | 52.9           |
|RandLA-Net    | 88.0          | 70.0          | 82.0          | 93.1          | 96.1          | 80.6          | 62.4          | 48.0          | 64.4          | 69.4          | 69.4          | 76.4          | 60.0          | 64.2          | 65.9          | 60.1           |
|KPConv        | -             | 70.6          | 79.1          | 93.6          | 92.4          | **83.1** | 63.9          | **54.3** | **66.1** | **76.6** | 64.0          | 57.8          | **74.9** | **69.3** | 61.3          | 60.3           |
|Bilateral     | 88.9          | **72.2**      | 83.1          | 93.3          | 96.8          | 81.6          | 61.9          | 49.5          | 65.4          | 73.3          | 72.0          | **83.7** | 67.5          | 64.3          | 67.0          | **62.4**  |
|**Ge-Latto (ours)**     | **89.7**      | 71.4          | 81.3          | **95.3**      | 95.1          | 82.3          | **69.2** | 51.9          | 64.8          | 73.3          | **77.3** | 59.6          | 71.1          | 63.0          | **67.4** | 57.9           |


### ShapeNet Parts
|Method        |   Cat. MIoU    |    Inst. MIoU    |
|:---          |     :---:      |     :---:        |
|PointNet      |     80.4       |      83.7        |
|PointNet++    |     81.9       |      85.1        |
|SO-Net        |     81.0       |      84.9        |
|KPConv        |     **85.1**   |    **86.4**      |
|PCT           |        -       |    **86.4**      |
|**Ge-Latto (ours)** | **93.2** |      84.5        |

### Modelnet40
|Method        |   OA    |
|:---          |   :---: |
|PointNet      |   89.2  |
|PointNet++    |   91.9  |
|SO-Net        |   90.9  |
|KPConv        |   92.7  |
|PCT           |**93.2** |
|**Ge-Latto (ours)** | **93.2**|


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





