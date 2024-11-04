**1. Download nuScenes V1.0 full dataset data [HERE](https://www.nuscenes.org/download). Folder structure:**
```
AdaptiveOcc
├── data/
│   ├── nuscenes/
│   │   ├── maps/
│   │   ├── samples/
│   │   ├── sweeps/
│   │   ├── v1.0-test/
│   │   ├── v1.0-trainval/
```


**2. Download the generated [train](https://cloud.tsinghua.edu.cn/f/ebbed36c37b248149192/?dl=1)/[val](https://cloud.tsinghua.edu.cn/f/b3f169f4db034764bb87/?dl=1) pickle files and put them in data.**

**3. Download the generated dense occupancy labels from [SurroundOcc](https://github.com/weiyithu/SurroundOcc) (resolution 200x200x16 with voxel size 0.5m) and put and unzip it in data.**
| resolution | Subset | Link | Size |
| :---: | :---: | :---: | :---: |
| 200x200x16 | train | [link](https://cloud.tsinghua.edu.cn/f/ef8357724574491d9ddb/?dl=1) | 3.2G |
| 200x200x16 | val | [link](https://cloud.tsinghua.edu.cn/f/290276f4a4024896b733/?dl=1) | 627M |

Please note that: <br/>
1. the shape of each npy file is (n,4), where n is the number of non-empty occupancies. Four dimensions represent xyz and semantic label respectively. <br/>
2. In the [dataloader](https://github.com/weiyithu/SurroundOcc/blob/d346e8ce476817dfd8492226e7b92660955bf89c/projects/mmdet3d_plugin/datasets/pipelines/loading.py#L32), it convert empty occupancies as label 0 and ignore class as label 255. <br/>
3. The occupancy labels are the voxel indexes under LiDAR coordinate system, not the ego coordinate system. You can use the [code](https://github.com/weiyithu/SurroundOcc/blob/d346e8ce476817dfd8492226e7b92660955bf89c/projects/mmdet3d_plugin/datasets/evaluation_metrics.py#L19) to convert voxel indexes to the LiDAR points. <br/>


**Folder structure:**
```
SurroundOcc
├── data/
│   ├── nuscenes/
│   ├── nuscenes_occ/
│   ├── nuscenes_infos_train.pkl
│   ├── nuscenes_infos_val.pkl

```
