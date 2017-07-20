# Deploying MobilERP

## Preparing the Raspberry Pie.

### Pre-requesites

* 1 [Raspberry Pi][3] (with an output of 5V and >1A)
* 1 MicroSD card class 10 or better, with at least 2GB space.
* [Raspbian Lite image][1]

### Instructions

1. Download the Raspbian image from the [offical raspberry pi site][1]
1. Prepare the MicroSD card [to boot up][2]
1. Login into your rpi and update it (```apt-get update && apt-get -y upgrade)
1. Install ```git``` and ```sudo apt-get install -y git```
1. install pyenv ```curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash``` 
1. Install the required dependencies to install python 3.6.2 
	```bash
	apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
	libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
	xz-utils tk-dev
	```
1. Add a new user to run MobilERP ```useradd -m mobilerp && passwd mobilerp```
1. Login as ```mobilerp``` and download the current version of the software ```git clone https://github.com/eligiobz/mobilerp-server.git```
	1. (**Optional**) SSH on startup: run the following command ```sudo raspi-config``` and the going to “Advanced Options” -> Select the “SSH” option -> Set the option to “Yes” -< Select “OK” -> Select “Finish”
1. Download Python version 3.6.2 with pyenv ```pyenv install 3.6.2```
1. Create the virtual enviroment for the application and activate it
	```bash
	cd mobilerp/
	pyenv virtualenv 3.6.2 env
	pyenv activate env
	```
1. Install the requiremients for the server
	```bash
	pip install -r requeriments.txt
	```
1. Launch mobilerp server with ```python app.py```

[1]: https://www.raspberrypi.org/downloads/raspbian/
[2]: https://www.raspberrypi.org/documentation/installation/installing-images/README.md
[3]: https://www.raspberrypi.org