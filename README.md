# template
Boiler plate code for Production Grade ML apps

This repo use the Builder pattern to create machine learning code that is manageable and trackable. Each submodule explains in detail its purpose. In general, the `train.py` should contain minimal code to train the model. Additional files should be created for prediction code and such things. This repo assumes that the development happens on Ubuntu 16.04 and that the user is using `conda` with CUDA.

docker-compose support is still pending although much of the setup has already been written owing to unsupported `--gpus` flag(as of compose file version "3.7").