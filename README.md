# presentations_render
This is a vagrant environment configured as a base for displaying presentations for CloudNative courses or OpenStack courses. It should automatically deploy all needed packages to run either the cn.sh or os.sh scripts to render the html for slides and exercise assets. If you do not already have the needed software, here are steps:

## macOS
_Gatekeeper will block virtualbox from installing. All you have to do is go into Security & Privacy of System Preferences and click Allow under the General tab and rerun installation._
##### Install all at once with the command below:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" && xcode-select --install &&brew install ansible ; brew install python ; brew cask install vagrant ; brew cask install VirtualBox ; brew cask install virtualbox-extension-pack ; vagrant plugin install vagrant-guest_ansible
```

##### Alternatively, you can install everything individually below.
- [Install the Latest Version of Vagrant](https://www.vagrantup.com/downloads.html) - (`brew cask install vagrant`)
    - Vagrant Plugin - `vagrant plugin install vagrant-guest_ansible`
- [Install the Latest Version of Virtualbox](https://www.virtualbox.org/wiki/Downloads) (`brew cask install VirtualBox`)
    - Virtual Box Extension Pack (`brew cask install virtualbox-extension-pack`)

##### Once the above software is installed. Do the following if you're running the environment on Mac:
1. Create a separate `~/bin` directory and `cd` to it.  (The directory doesn't have to be ~/bin, it can be anything you want.)
2. Clone the environment repo to it with `git clone https://github.com/OpenCloudJedi/CyberEnvironment.git`
3. Change to the `Environment` directory that is now in your `~/bin` directory.
4. Run `vagrant up` to deploy the environment It will take the longest to deploy the first time only, this is because the system will have to download the images from vagrant on the first time this is run

## Windows
- If using Windows:
- [Install the Latest Version of Vagrant](https://www.vagrantup.com/downloads.html)
- [Install the Latest Version of Virtualbox and Virtual Box Extension Pack](https://www.virtualbox.org/wiki/Downloads)
- Then install the following vagrant plugin via PowerShell as Administrator `vagrant plugin install vagrant-guest_ansible`


##### Once the above software is installed. Do the following if you're running the environment on Windows:
1. Create a separate `~/bin` directory and `cd` to it using the same PowerShell/Terminal as Administrator/Root.  (The directory doesn't have to be ~/bin, it can be anything you want.)
2. Use your browser of choice and navigate to https://github.com/OpenCloudJedi/Environment, press the green “Clone or download” button then the “Download ZIP” button. Or use Github Desktop (See below).
3. Once downloaded, unzip the file and move it to the directory you created earlier, `~/bin` in the above example.
4. Use PowerShell/Terminal as Administrator/Root again and cd to the `~/bin/CyberEnvironment-main` directory then run `vagrant up` to deploy the environment. (It will take the longest to deploy the first time only, this is because the Vagrant system downloads the base image only the first time.

## Notable commands to control the environment:
- `vagrant up` - Boots and provisions the environment
- `vagrant destroy -f` - Shuts down and destroys all of the vms
- `vagrant ssh ubuntu` - Uses console connection to ssh to the VM
- `vagrant up --provision` - Builds the servers that were destroyed and runs provisioning scripts again

This machine has the IP `192.168.2.100`. When rendering the slides you will use this IP in the browser followed by the port. 
Example:
- `192.168.2.100:8000` - This would connect to the site for slides on port 8000
