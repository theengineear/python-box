## Yay boxes

### Step 1
Create the directory you want to have your virtual machine in. Mines here:

`~/vms/python-tests`

### Step 2
Change a line in the `Vagrantfile` in your local copy of this repo:

`config.vm.synced_folder "/Users/ee/PyCharmProjects/python-api", "/home/python-api"`

So that this `"/Users/ee/PyCharmProjects/python-api"` is pointing to your python-api directory for the `plotly/python-api` repo on your local (host) machine. This is going to get shared with the guest (vagrant) machine.

### Step 3
cd *into* the directory you created in "Step 1" and run:

`vagrant up`

### Step 4
ssh into the new VM you just created when that finishes

`vagrant ssh`

### Step 5
*source* the setup script provided (don't just chmod/run!)

`source /vagrant/setup`

### Step 6
wait... this might take a little bit, it needs to install a bunch of stuff
when this finishes, you'll have a nice pyenv setup ready and waiting for you. to see what versions of python exist run:

`pyenv versions`

you switch between versions by exporting changes to the PYENV_VERSION variable like so:

`export PYENV_VERSION=3.4.1`

### Step 7
you're done! note that plotly's not installed yet, you'll need to either pip install yourself, or, if you want to make sure everything worked... (a good idea) source the test script!

`source /vagrant/test` 

### Step 8 (contingent on Step 7)
run:

`cat test_log.txt`

make sure that there aren't any errors!
