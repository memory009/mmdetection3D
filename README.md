## enviroment requirement
* Python 3.6+
* PyTorch 1.3+
* CUDA 9.2+ (If you build PyTorch from source, CUDA 9.0 is also compatible)
* GCC 5+
* MMCV
### step 0. Create a conda virtual environment
```
conda create --n openmmlab python=3.8 -y
conda activate openmmlab
```

### step 1.Install Pytorch following official instruction
#### On GPU platforms(recommend):
```
conda install pytorch torchvision -c pytorch
```

#### On CPU platforms:
```
conda install pytorch torchvision cpuonly -c pytorch
```

## Installation

### step 0. Install MMCV using MM.
```
pip install openmim
mim install mmcv-full
```

### step 1. Install MMsegmentation:
```
pip install mmsegmentation
```

### step 2.Install build requirements and then install MMDetection3D:
```
pip install -v -e .  # or "python setup.py develop"
```

## Verification
### Verify with point cloud demo 
```
python demo/pcd_demo.py ${PCD_FILE} ${CONFIG_FILE} ${CHECKPOINT_FILE} [--device ${GPU_ID}] [--score-thr ${SCORE_THR}] [--out-dir ${OUT_DIR}]
```

for example:
```
cd ~/mmdetection3d/demo
python pcd_demo.py ./data/kitti/kitti_000008.bin ../configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py ../checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth --show
# use the parameter '--show' can get a visualized detection output
```

### Pointcloud format Convert
CARLA outputs .ply by default as a point cloud result, so we should convert the output from '.ply' to '.bin' using ```format_convert.py``` 
![demo](/home/daniel/mmdetection3d/figrue/detect_000008.png)



