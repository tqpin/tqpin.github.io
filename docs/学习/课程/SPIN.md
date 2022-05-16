## SMPL
smplify: 
opt_cam_t

## SPIN structure
smpl parameter (smpl_para): pose, beta
vertices and joints from smpl model (smpl_2d)
gt_keypoints_2d: get from OpenPose


Each step:
1. Get data from the batch (smpl_para, gt_keypoints_2d, gt_joints_3d)
2. Get GT smpl_2d from SMPL model using pip-smplx(smpl_para)
3. Get current best fits from the dictionary --> (opt_smpl_para, opt_smpl_2d)
4. Estimate camera translation for opt & gt

Compute reprojection loss value of  `opt_*` and `gt_keypoints_2d_orig` --> `opt_joint_loss`

Feed images in the HMR network to predict camera and SMPL parameters --> `pred_*`

run_smplify
* Step 1: Optimize camera translation and body orientation
* Step 2: Optimize body joints
* Get final loss value
* Will update the dictionary for the examples where the new loss is less than the current one  `new_opt_*`-->`opt_*`

Replace the optimized parameters with the ground truth parameters, if available?


## Visualize for 3D mesh

[EasyMoCap](https://github.com/zju3dv/EasyMocap/blob/master/doc/realtime_visualization.md)

BVH file format
* Blender 2.8, down with python extension
* see Blender Visualization tools, like save/load function in [DeepMotionEditing](https://github.com/DeepMotionEditing/deep-motion-editing)

## set the env for SPIN

* chumpy：only need for [this](https://github.com/vchoutas/smplx/tree/master/tools)
* anaconda：numpy scikit-image scipy=1.0.0 tensorboard tqdm
* anaconda：conda install -c conda-forge opencv
* torch=1.1.0 torchvision [官网](https://pytorch.org/get-started/locally/)  conda install pytorch=1.1.0 torchvision=0.3.0 cudatoolkit=10.0 -c pytorch
* pyopengl [官网](http://pyopengl.sourceforge.net/documentation/installation.html)  pip install PyOpenGL PyOpenGL_accelerate
* pyrender [官网](https://pyrender.readthedocs.io/en/latest/install/index.html)  pip install pyrender （在 zshrc 里写 export MUJOCO_GL=osmesa    export PYOPENGL_PLATFORM=osmesa）
* sudo apt install nvidia-cuda-toolkit
* pip install smplx neural-renderer-pytorch future（pip）
* sudo apt install libosmesa6 libosmesa6-dev（为了运行 osmesa）
* torchgeometry pip install torchgeometry （忘记哪里看来的了，但是操作就对了，官网要求更高版本 pytorch，但可以根据 [osmesa](https://pyrender.readthedocs.io/en/latest/install/index.html#installing-osmesa) 的指导 git clone https://github.com/mmatl/pyopengl.git ；pip install ./pyopengl）
* trimesh（pyrender 一起安装了）
* spacepy（记得看 spin 指示的几个链接一定要 build from source）used by h36m

在集群安装：
* fail in neural-renderer-pytorch
* sudo apt install libosmesa6 libosmesa6-dev
* spacepy（记得看spin指示的几个链接 一定要build from source）used by h36m
* torchgeometry（官网要求更高版本pytorch，但可以根据[osmesa](https://pyrender.readthedocs.io/en/latest/install/index.html#installing-osmesa)的指导 git clone https://github.com/mmatl/pyopengl.git ；pip install ./pyopengl）
* trimesh（pyrender一起安装了）


smpl from [this](https://smpl.is.tue.mpg.de/), we have not use anything from [this](https://smplify.is.tue.mpg.de/). see readme in data/smpl/webuser

然后
* bash fetch_data.sh
* 创建 data/smpl 把三个模型复制进去
* change smpl.py from smplx.body_models import SMPLOutput

然后就可以测试 python demo.py --checkpoint=data/model_checkpoint.pt --img=examples/im1010.jpg --openpose=examples/im1010_openpose.json
2022-04-25：但是 train 所需要的数据集还很麻烦，比如 h36m 需要视频原数据集，现在下载不了
所以对于毕设来说，现在就把
