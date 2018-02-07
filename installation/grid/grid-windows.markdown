# Grid Windows Tutorial

All commands are called from the basic windows command prompt.

## Step 1: Install go

Download the installer from [here](https://dl.google.com/go/go1.9.3.windows-amd64.msi).

Launch the installer, follow the instructions and complete the installation.

## Step 2: Install IPFS

First we're going to install a tool that can install IPFS and update it.

Run the following command:

```
go get -v -u github.com/ipfs/ipfs-update
```

Once that's completed you can run that tool to install IPFS:

```
ipfs-update install latest
```

Note: If `ipfs-update` cannot be found make sure your `GOPATH` is added to your `PATH` environment variable. If `GOPATH` isn't set then its mostly in your users home directory `C:\Users\{user-name}\Go\bin`. So this can be added to your `PATH` with the following command:

```
set PATH=%PATH%;C:\Users\{user-name}\Go\bin
```

where `{user-name}` is your user name.

## Step 3: Setup IPFS

Now, you need to initialize IPFS:

```
ipfs init
```

And start the daemon, this is what is used to connect to the wider IPFS network:

```
ipfs daemon --enable-pubsub-experiment
```

## Step 4: Install PyTorch

Currently Windows isn't officially supported by PyTorch (hopefully soon!) but a member of the community has created a conda package for it. Make sure you have anaconda or miniconda installed for this part! The installer can be found [here](https://www.anaconda.com/download/#windows).

This can be installed with the following command:

```
conda install -c peterjc123 pytorch
```

More information can be found [here](https://github.com/pytorch/pytorch/issues/494#issuecomment-322096506). There are other ways of installing in that thread so GPU/CUDA is supported.

## Step 5: Setup the Grid

The Grid currently only supports Python 3.6 so make sure that is installed/enabled.

First you need to get the grid code:

```
git clone git@github.com:OpenMined/Grid.git
```

Call the setup script:

```
python setup.py install
```

This script installs the rest of the dependencies and installs it.

## Step 6: Run Grid Worker and Train a Model

To run the worker run the following python file:

```
python ipfs_grid_worker_daemon.py
```

Next open the jupyter notebook in the notebooks folder:

```
notebooks/pubsub/Keras Grid Client and Worker.ipynb
```

and run all of the cells. These cells should complete with no errors and you should see the model being trained!

## Known issues

In the future the Grid will need to rely on ethereum and the python ethereum package pythereum will not build on windows. See issue: https://github.com/OpenMined/Grid/issues/33
