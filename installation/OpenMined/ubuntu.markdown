# Linux - Setting up your Dev Environment

In this document, we're going to condense how you should setup your machine in preparation for the rest of the tutorials contained in this document. Running OpenMined means having several different applications and repositories correctly installed and ready to work together, which can have unique challenges for each system. To that end, let's get your Mac up and running!!!

**Follow this guide in its [YouTube Video Tutorial](https://youtu.be/P3DPmVlWye0)**

- [Step 1: Install Unity](#Step-1-Install-Unity)
- [Step 2: Install Jupyter Notebook](#)
- [Step 3: Fork, Clone & Build Relevant Repositories](#)
- [Step 4: Start Jupyter Notebook](#)
- [Step 5: Start OpenMined Unity Application](#)

# Step 1: Install Unity

Unity is a cross-platform game engine to develop applications (usually games) for computers, consoles, and mobile devices.
Since we want utilize the GPU power from video games (such as PS4 and Xbox One) to training the Deep Learning models, Unity helps us to develop OpenMined application that can run like a game on those consoles.

1. So, to get Unity just proceed to [this page](https://beta.unity3d.com/download/7807bc63c3ab/public_download.html)

2. Click on the `Linux Download Assistant` link to download the installer.

3. After the download is complete, make it executable with `chmod +x UnitySetup-2017.3.0b1`.

4. Then, execute it with `./UnitySetup-2017.3.0b1`.

5. This will open the installer. Follow the instructions to complete the Unity installation.

It's the longest part of the process, but you can continue with the other steps in this tutorial while you wait for the download.

A few quick tips:

- You only need the *Free* version in order to use OpenMined.
- Unity will start with your internet turned *off*, but if you have your internet turned *on* but are simply attached to a bad connection, sometimes Unity will hang. Just turn off your Wi-Fi and restart Unity if you have this issue.

# Step 2: Install Jupyter Notebook

We use Jupyter Notebook to register code and its explanations, because it allows not only write executable documents which can be run to perform data analysis, but also human-readable documents containing the analysis description and the results (figures, tables, etc..)

The best way to install Jupyter Notebook is thru Anaconda (the most popular Python Data Science platform), because use *pip* (a Python package manager) is unreliable for installing Jupyter Notebook. Sometimes it works, sometimes it totally screws up your system

#### Part 1: Install Anaconda

First, navigate to the [Linux Anaconda Download Page](https://www.anaconda.com/download/#linux) and click "Download" for the *Python 3.6* version. And once you download the install script, type this commands on terminal:

1. Make it executable: `chmod +x Anaconda3-5.0.1-Linux-x86_64.sh`

2. And then run it: `./Anaconda3-5.0.1-Linux-x86_64.sh`

   - Follow the instructions in the installer.
   - When asked if the installer should add the install location to your PATH, say **yes**.

3. Once the installer finishes. Re-source your bashrc: `source ~/.bashrc`.

#### Part 2: Change to Python 3.6

At the time of writing, PySyft is built against Python 3.6 version, so we'll want to change the default version over to *3.6*.
Fortunately, Anaconda includes a [tutorial on how to do this](https://conda.io/docs/user-guide/tasks/manage-python.html).

First, restart your terminal (if its open since before Anaconda instalation) and see if you're already on version 3.6 by enter `$ python --version`. If it says 3.6, you can skip to *Part 3*! If it don't, just run this 2 commands:

1. Create the new environment for Python 3.6: `$ conda create -n py36 python=3.6 anaconda`

2. Activate the new environment: `$ source activate py36`

Now, check the version again, and it should tell you "3.6".

#### Part 3: Install Jupyter Notebook

If you installed Anaconda, you have already installed Jupyter Notebook!
But if you didnt, you'll need to use [these instructions](http://jupyter.readthedocs.io/en/latest/install.html) as a backup.

# Step 3: Fork, Clone & Build Relevant Repositories

To download the project files to your computer you could directly clone our main repository, but by doing that you aren't be able to send Pull Request. So in order to do that, you need to make a fork.

#### Part 1: Your OpenMined directory

For organizational reasons, is important to have a dedicaded directory on you computer to hold all your OpenMined related projects.

1. To do that, just create a OpenMined folder: `$ mkdir OpenMined`

2. Go to that folder: `$ cd OpenMined`

3. And do one more check if that Python 3.6 is activated: `$ python --version`
   
   - If don't activate the 3.6 environment: `$ source activate py36`

#### Part 2: Fork PySyft an OpenMined Repositories

Now let's download the files of the OpenMined (The OpenMined Unity Application) and PySyft (Private Deep Learning Client) projetcs. To do that, follow this steps:

1. Fork the Repository of both projects by clicking on the top right corner button.

   - [OpenMined Repository](https://github.com/OpenMined/OpenMined)
   - [PySyft Repository](https://github.com/OpenMined/PySyft)
   
   This will copy our repositories to **your** GitHub account.
   
2. Once in your own GitHub repository, click in the green button "Clone or download", and then copy the shown link.

3. Now back to the terminal and clone the repositories by typing this command:

   - `$ git clone <and paste the link>`
   
   The link should be like: `https://github.com/<your github username>/<name of the repository>.git`
   
   If you're having some issues to clone, you can try [clone with SSH](https://youtu.be/Vi-WqFKYpnw).
   
Here's an image showing the "Fork" button:

![Fork Button](../resources/images/fork.png)

#### Part 3: Install and Build

Let's install PySyft!

1. Go to the PySyft folder: `$ cd PySyft`

2. Install the requeriments: `$ pip3 install -r requirements.txt`

3. Install the application itself: `$ python setup.py install`

  Notice that if you don't activate the environment *3.6* with Anaconda, you need to type `python3` instead of just `python`.

4. Go back to OpenMined folder: `$ cd ..`

If you have any trouble with the installation of PySyft, debug using the [README](https://github.com/OpenMined/PySyft).

# Step 4: Start Jupyter Notebook

From your general directory (containing both your OpenMined and PySyft folders), run the following command:

- Start the Jupyter Notebook Server: `$ jupyter notebook`

It should automatically open your browser to the main Jupyter Notebook folder.

# Step 5: Start OpenMined Unity Application

Last step! We're so close. Now we gonna open the OpenMined Unity Project in Unity3D.

#### Part 1: Start Unity Application

Find where Unity installed, start the application and login with your account.

#### Part 2: Select OpenMined/UnityProject

Click in the "Open" button and select the folder `UnityProject` within the OpenMined folder.

![](../resources/images/OpenUnityProject.png)

#### Part 3: Double-click Assets/OpenMinedMain

To design games, Unity uses a concept called 'scene', witch is a collection of code objects that interacts each other. In OpenMined case, we're build an Deep Learning library, so our scene it's a little bit different.

To open it, go to the project pane, and in the "Assets" folder, double click on `OpenMinedMain` Unity Scene (little file with the Unity logo next to it).

![](../resources/images/SelectUnityScene.png)

#### Part 4: Make sure SyftServer is properly attached to the FloatTensorShaders file.

In the `Hierarchy` pane, click the `Main Camera`.

![](../resources/images/HierarchyMainCamera.png)

Then, in the `Inspector` pane (towards the bottom), you should see a `Syft Server (script)` inside of which is a textarea labeled `Shader`. The contents of this text area should say `FloatTensorShaders` like pictured below.

![](../resources/images/CameraInspector.png)

If you don't see `Syft Server Script` in the inspector pane, drag the file `Assets/OpenMined/Network/Servers/SyftServer` and drop it into the inspector as pictured below.

![](../resources/images/DragSyftServer.png)

If you DO see the `Syft Server Script` but `FloatTensorShaders` is NOT in the `Shader` area (if area will is grayed out and say `None (ComputeShader)`. Drag the file `Assets/OpenMined/Syft/Tensor/Ops/Shaders/FloatTensorShaders` into that text area like seen below.

![](../resources/images/DragShader.png)

#### Part 5: Press Play

At the top of the Unity application there's a Play button. Press it! This will start the OpenMined Server.

![](../resources/images/UnityPlayButton.png)

# Next Step

Now you're a ready to start doing some [tutorials](https://github.com/OpenMined/tutorials)!

If jupyter notebook is not running, start it with `jupyter notebook`.  If you still have it running, open the tree view by going to `localhost:8888/tree` in your browser.  There are lots of notebooks in the openmined repo that you can test. Navigate to `openmined/notebooks` and then click `Syft Tensor Example Notebook`.

Inside the notebook, run the first two cells. If they execute properly, you are all set!

# Getting help

If you have any trouble at any point. Drop into our [slack](https://openmined.slack.com/join/shared_invite/enQtMjU5MzE5ODk4MTc3LWI2ZGE1ODc1YjdkZDJiNjdmYTdkZmE4ZTY5N2NkNDgxZjUyNjgxMTVhMmJkOTZhZjEyZDA3MTM2MThkZWVhMjg) group and ask for help! There are lots of people always online who are glad to help!
