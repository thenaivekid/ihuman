[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1tbj4By3B1bUpWdQ-WPbynd733d13bjR8?usp=sharing)
# iHuman: Instant Animatable Digital Humans From Monocular Videos [ECCV 2024]


This is official implementation of the paper: "iHuman: Instant Animatable Digital Humans From Monocular Videos".

Learn more on our project page: [iHuman](https://pramishp.github.io/iHuman/index.html) 

## Prerequisites

* Cuda 11.8/12.1
* Conda
* A C++14 capable compiler
  * __Linux:__ GCC/G++ 8 or higher

## Setup
First make sure all the Prerequisites are installed in your operating system. Then, invoke

```bash
conda env create -f environment-cuda12_1.yaml # or environment-cuda11_8.sh
conda activate ihuman
cd submodules
bash ./install-cuda12_1.sh # or install-cuda11_8.sh
```


## Running the Code in Google Colab

For an easier setup, we provide a [Google Colab notebook](https://colab.research.google.com/drive/1tbj4By3B1bUpWdQ-WPbynd733d13bjR8?usp=sharing) to run the project in the cloud. This allows you to run the code without worrying about local setup.

### Steps to use Colab:
1. **Select a Runtime with GPU**: In Colab, go to `Runtime` -> `Change runtime type` and select GPU (e.g., T4).
2. **Add Directories as Shortcuts**: Follow the instructions in the notebook to add the following directories as shortcuts to your Google Drive:
   - **Prebuilt wheels**: [Get the prebuilt wheels](https://drive.google.com/drive/folders/1tNCO1sfMlKS5X2aWEEtAniF-eYSn_66h?usp=sharing)
   - **Dataset, models, and other assets**: [Get the dataset and models](https://drive.google.com/drive/folders/1Ux98nBmlGbtvjyiu_k_aZYASXCH4Qy5P?usp=drive_link)

   You can refer to the screenshots in the notebook for step-by-step guidance on adding these directories.

3. **Run the Notebook**: Follow the instructions in the Colab notebook to train the model and animate the rendered human model.


## Running the code locally
### Step 1: Download Dataset
a. download dataset from this link https://drive.google.com/file/d/1qwM1jdabiJFmEGywuYowKD0-nC2-rWVe/view?usp=share_link
<br>
b. place it in {root}/data/peoplesnapshot/

### Step 2: Download Models
a. Download the SMPL v1.1 `SMPL_python_v.1.1.0.zip` model from the [SMPL official website](https://smpl.is.tue.mpg.de/download.php) and move and rename `SMPL_python_v.1.1.0/smpl/models/*.pkl` to `PROJECT_ROOT/data/smpl/models`.

After this the project folder should look like this:
```
PROJECT_ROOT/data/smpl/models
    ├── SMPL_FEMALE.pkl
    ├── SMPL_MALE.pkl
    ├── SMPL_NEUTRAL.pkl

```

b. Download the files from this drive link (https://drive.google.com/file/d/17OdyNkfdFKFqBnmFMZtmT9B-6AXKAZeG/view?usp=share_link) and place them in `PROJECT_ROOT/data/smpl/small/`.


After this the project folder should look like this:
```
PROJECT_ROOT/data/smpl/small/
    ├── J regressor.txt
    ├── joint locations.txt
    ├── kintree table.txt
    ├── mesh2smpl_idx.txt
    ├── triangles.txt
    ├── uv_coords.txt
    ├── uv_map2face.txt
    ├── vertices.txt
    ├── weights.txt

```

<br>


### Step 3:
4. python train.py

You can modify the training parameters in the `conf/mmpeoplesnapshot_fine.yaml` file.

### Step 4: Animate the rendered model
a. Download the files from this drive link (https://drive.google.com/drive/folders/1XUpygOfdTSx4pKflAzbu7CY7fLTSNAe8?usp=sharing) and place them in `PROJECT_ROOT/data/animation`.

After this the project folder should look like this:
```
PROJECT_ROOT/data/animation
    ├── motion
    ├── camera.pkl

```

b. python animate.py

## Acknowledgement

Our code is based on several interesting and helpful projects:

- InstantAvatar: <https://github.com/tijiang13/InstantAvatar>
- GaussianSplatting: <https://github.com/graphdeco-inria/gaussian-splatting>
- Diff-gaussian-rasterization: <https://github.com/ashawkey/diff-gaussian-rasterization>
- SuGaR: <https://github.com/Anttwo/SuGaR>
- Animatable 3D Gaussian:<https://github.com/jimmyYliu/Animatable-3D-Gaussian>
- GART: https://github.com/JiahuiLei/GART
- Anim-NeRF: https://github.com/JanaldoChen/Anim-NeRF

We are grateful to the developers and contributors of these repositories for their hard work and dedication to the open-source community. Without their contributions, our project would not have been possible.
