Bonsai CLI & SDK

$ virtualenv bonsaienv 
$ source bonsaienv/bin/activate 
$ pip install git+https://github.com/BonsaiAI/bonsaitools 
$ git clone https://github.com/BonsaiAI/breakoutdemo.git 
 
$ cd breakoutdemo 
 
# Launch the game and play it 
$ python bricka.py 
 
# Edit the inkling to show how the system will learn to play 
$ subl breakout.ink 
 
# Edit bricka.py to show necessary changes 
$ subl bricka.py 
 
# verify breakout.ink 
$ brain --lint breakout.ink 
0 errors 
Ready to upload. 
 
# upload breakout.ink 
# the following command could lint pre-upload 
# the URL could be shortened given config info (for example brains.bons.ai and the user name) 
# Uploading a new inkling file generates a new id. Most old id's don't need to stick around right now (only the 
# deployed brain). 
$ brain --user=megan --password --create http://brains.bons.ai/megan/breakout-brain breakout.ink 
Password:  
Upload success. 
http://brains.bons.ai/megan/breakout-brain/1 
 
# Launch bricka.py for training, url updates to  
$ python --brainnpc=http://brains.bons.ai/megan/breakout-brain/1 bricka.py 
 
# train 
$ brain --train http://brains.bons.ai/megan/breakout-brain/1 
BRAIN breakout-brain found. 
Simulator breakoutsim found. 
Training… 
10000 epochs, 90% accuracy 
Train complete. 
 
# deploy.  
# Only one version is in the 'deployed' state, old versions are in a not deployed stated 
$ brain --deploy http://brains.bons.ai/megan/breakout-brain/1 
Deploy Success 
http://brains.bons.ai/megan/breakout-brain/1 
Host: 127.0.0.1 
Port: 5554 
 
# show the deployed net playing the game 
$ python --brainnpc=http://brains.bons.ai/megan/breakout-brain/deployed bricka.py  
