# Core

This folder contains the meat of the code. Each file and its purpose is listed below:

1. `builders.py` - Since this repo follows the builder pattern, this file is the one responsible for housing all the different types of builders. Each builder is responsible for creating a `Trainer` object which can be called by `train.py` to train the appropriate model with the appropriate parameters.
2. `common.py` - This houses code which is common to all models defined in `models.py`.
3. `config.py` - Contains config in EasyDict format
4. `loaders.py` - Contains all the dataset loaders 
5. `models.py` - Contains all the models
6. `utils.py` - Unlike `common.py` this file contains helper functions like file I/O operations which might be needed by the `Trainer` object
