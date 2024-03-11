# <p align="center">Masked face generation</p>
<p align="center">
  <img src="docs/vinorsoft_logo.png" width="150">
  <br />
  <br />
  <a href="http://www.vinorsoft.com/"><img alt="Auth Vinorsoft" src="https://img.shields.io/badge/Auth-Vinorsoft-FFD500?style=flat&labelColor=005BBB" /></a>
  <a href="https://github.com/pytorch/fairseq/blob/main/LICENSE"><img alt="Team" src="https://img.shields.io/badge/Team-Camera AI-FFD500?style=flat&labelColor=005BBB" /></a>
  <a href="https://github.com/optimuskonboi"><img alt="Instructor DanPV" src="https://img.shields.io/badge/Instructor-DanPV-FFD500?style=flat&labelColor=005BBB" /></a>
  <a href="https://github.com/giangnv125"><img alt="Deployer GiangNV" src="https://img.shields.io/badge/Deployer-GiangNV-FFD500?style=flat&labelColor=005BBB" /></a>
</p>

## Overview
- This masked face generation based on [this repo](https://github.com/aqeelanwar/MaskTheFace) to convert face datasets to masked face datasets
- It uses a dlib based face landmarks detector to identify the face tilt and six key features of the face necessary for applying mask.

## Installation & Running
1. Clone the repository
- ```shell
  git clone https://github.com/giangnv125/MaskTheFace.git
  ```
2. Install pakages
- ```shell
  cd MaskTheFace
  pip3 install -r requirements.txt
  ```
- [This repository](https://github.com/z-mahmud22/Dlib_Windows_Python3.x) contains the compiled binary (.whl) files for the Dlib library to install on Python versions 3.7, 3.8, 3.9, 3.10, and 3.11 on a Windows x64 OS. Open a terminal and install Dlib such as below:
  ```shell
  pip3 install dlib-19.22.99-cp310-cp310-win_amd64.whl
  ```
3. Run
```shell
cd MaskTheFace
# Generic
python mask_the_face.py --path <path-to-file-or-dir> --mask_type <type-of-mask> --verbose --write_original_image

# Example
python mask_the_face.py --path 'datasets/test' --mask_type 'N95' --verbose --write_original_image
```
### Arguments
|    Argument    |                                                                                                       Explanation                                                                                                       |
|:--------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|      path      |                                                                            Path to the image file or a folder containing images to be masked                                                                            |
|    mask_type   | Select the mask to be applied. Available options are 'N95', 'surgical_blue', 'surgical_green', 'cloth', 'empty' and 'inpaint'. The details of these mask types can be seen in the image above. More masks will be added |
|     pattern    |                                 Selects the pattern to be applied to the mask-type selected above. The textures are available in the masks/textures folder. User can add more textures.                                 |
| pattern_weight |                                   Selects the intensity of the pattern to be applied on the mask. The value should be between 0 (no texture strength) to 1 (maximum texture strength)                                   |
|      color     |                                                         Selects the color to be applied to the mask-type selected above. The colors are provided as hex values.                                                         |
|  color_weight  |                                      Selects the intensity of the color to be applied on the mask. The value should be between 0 (no color strength) to 1 (maximum color strength)                                      |
|      code      |                                                              Can be used to create specific mask formats at random. More can be found in the section below.                                                             |
|     verbose    |                                                                          If set to True, will be used to display useful messages during masking                                                                         |
|write_original_image|                   If used, the original unmasked image will also be saved in the masked image folder along with processed masked image                                                                              |

