# pytorch_cpp
 
This is the repo for playground and other pytorch cpp projects.

### Install Pytorch CPP on Windows
To use pytorch cpp lib, the [official method](https://pytorch.org/cppdocs/installing.html) only supports limited versions of pytorch. If your project satifies those versions, that would be fine. 
#### Another easy way to link lib is to
- use the easy python installation of pytorch first, like pip or conda, and select your [target projet version](https://pytorch.org/get-started/previous-versions/) of CUDA and cuDNN which can be downloaded from Nvidia developer website.
- After you have installed pytroch python on your computer, find the absolute path of the python library e.g. **/your_path/conda/conda/envs/Py3/Lib/site-packages/torch**
- Add the path to your cmake file 
```
list(APPEND CMAKE_PREFIX_PATH "your_path/conda/conda/envs/Py3/Lib/site-packages/torch")
```
- Use cmake to build and generate your project, I test mine using Visual Studio 2017.
