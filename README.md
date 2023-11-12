# tsdf-fusion-torch
This is pytorch extention for Volumetric TSDF Fusion algorithm.


## TODO
[ ] Implement color integration  
[ ] Make demo  
[ ] Make cuda kernel follow torch style

## Install
Make sure to set up CUDA environment and install pytorch before installation.


You can install the extension by running the command below.  

```
git clone https://github.com/lshwan/tsdf-fusion-torch.git

cd tsdf-fusion-torch

python setup.py install
```


## Use
You can fuse depth and rgb images into TSDF values via following code.

Currently, color integration is not implemented. I will update it soon.

```
import tsdf_torch as tsdf

tsdf_values, color_values = tsdf.fusion(depth_images,   # depth images: N frames X H X W
                                        rgb_images,     #  RGB images: N X H X W X C
                                        camera_poses,   # camera pose matrices: N X 4 X 4
                                        camera_intrinsic,   # camera intrinsic matric: 4 X 4
                                        world_size,     # world boundary to build voxel grid: [[X
                                        _min, Y_min, Z_min], [X_max, Y_max, Z_max]]
                                        voxel_size,     # width of grid cell
                                        truncation,     # truncation value
                                        obs_weight      # updating weight value)
```

## References
Original Paper: [A Volumetric Method for Building Complex Models from Range Images (SIGGRAPH 1996)](https://graphics.stanford.edu/papers/volrange/volrange.pdf).

This code is based on the TSDF algorithm in python: https://github.com/andyzeng/tsdf-fusion-python.
