# Running the robot

To run the robot, go to the directory with the python project.

```shell
cd /home/pi/Robot
```

Then run the application.

```shell
python3 app.py
```

The application has some arguments that can be used to specify how it should be run.

	-d, --debug           Run robot in debug mode.
	-s, --simulate        Run robot in simulation mode, which can be run on a none-rpi system.
	-t, --auto-terminate  Auto terminate application after 5 sec.

# Robot setup

## Pull Robot project from Github

Generate a new ssh key on the raspberry.

```shell
ssh-keygen
```

You can use the default on all the settings during the setup. Then add the generated ssh key from the raspberry to Github. Run the following command to get the key.

```shell
cat /home/pi/.ssh/id_rsa.pub
```
Copy the output to Github.

When the key is added you can pull the project from Github

```shell
git clone --recurse-submodules git@github.com:Projektkurs-HT21/Robot.git
```

## Install requirements
Install the following for numpy to work

```shell
sudo apt-get install libatlas-base-dev
```

Upgrade pip to the newest version.

```shell
python3 -m pip install --upgrade pip
```

Then install all python packages

```shell
cd Robot
pip3 install -r requirements.tex
```

# Adding functionality
To add a new python file that is supposed to run on the robot, do the following.

## Import the project as a submodule
Start by importing the project containing the code as a submodule for this project

```shell
git submodule add <SSH link>
```

## Make the project into a python module
Make the project into a package module that the application can import. Create the file _\_\_init\_\_.py_ in the top directory of the submodule.

```shell
touch <SUBMODULE PATH>/__init__.py
```

Do this for every sub folder in the submodule that has a python file that needs to be run.

## Reference all imports as relative from root
For the imports between files in your submodule to work when they are referenced from the python application, you need to make all imports relative to the _Robot_ directory. The syntax will be.

```python
import <SUBMODULE>.<FILENAME>
```

## Create a process in app.py
The application uses the [multiprocessing library](https://docs.python.org/3/library/multiprocessing.html) to be able to run different processes at the same time on different CPU cores. In app.py there is a dict called _processes_. Add a key for your process and a new process as a value for it.

```python
processes = {
	mp.Process(name="Controller", target=controller.run),
	mp.Process(name="<YOUR PROCESS NAME>", target=<YOUR FUNCTION>)
	}
```

For the new process to terminate successfully, you should pass the `stop_event` to it. This event will be set when a terminate signal is sent to the program, so make sure your process checks this event reguraly and terminates the process correctly if this is set. To get access to the commandline arguments passed into the project you can access the object `args`.

