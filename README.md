# Bonsai CLI & SDK
This is for training my own breakout BRAIN
The first step, not on the command line, is to make a new brain on the website. 
The instructions below assume it's named mybreakout

```

$ virtualenv bonsaienv
$ source bonsaienv/bin/activate 
$ git clone https://github.com/BonsaiAI/breakoutdemo.git
$ cd breakoutdemo
$ pip install -r requirements.txt
 
# Optional: Launch the game and play it 
$ python bricka.py 
 
# Optional: Edit the inkling to show how the system will learn to play 
$ subl breakout.ink 
 
# Optional: Edit bricka.py to show necessary changes 
$ subl bricka.py 

# this command will popup a web page that asks you to login once you login it has an access key (like phacility or heroku)
# the page will tell them to copy the key here
$ bonsai configure
You can get the access key at https://brains.bons.ai/accesskey
Access Key:
authenticated.

$ bonsai load mybreakout breakout.ink
loaded


$ python breakout.py --brainnpc=<http link to BRAIN server>

$ bonsai sims list
Simulator   Count    Status
---------   -----    --------
breakout    1        ready

$ bonsai brain train mybreakout
training started.
Training...
10000 trials, 90% accuracy 
Train complete.

# Breakout exits, the user could change inkling, load it again, and train again until they are
# satisfied.

#Once satisfied with the training accuracy, you can go ahead and deploy your brain

$ bonsai deploy mybreakout
deploy success.
Deploy Success 
For predictions connect your simulator to: https://brains.bons.ai/<link to trained BRAIN>
```
