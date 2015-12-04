# Openshift
Scripts for stepping through OSE demo examples, showcasing various applications and scenarios.
Based on the most excellent working demos done by Veer -> https://github.com/VeerMuchandi

These are for Openshift Enterprise version 3.1.0 and aren't guaranteed to work on other versions.

### Setup

git clone this repo: 
```
cd /home/demo
git clone https://github.com/ffirg/openshift.git
cd openshift/bin
```

Using demobuilder all-in-one image as your base (https://github.com/RedHatEMEA/demobuilder), open up the console and fire up the Firefox browser and a Terminal.

### What They Demo

#### MLB Parks 
Creates the visually appealing MLBParks example. Overlays baseball venues on to Google Maps.
MongoDB is used for the back-end database, JBoss EAP for the front-end, so this demonstrates a multi-tiered application, wired together in stages.

```
$ ./create-ose3-mlbparks-app.sh
```


#### Code Promotion Between Environments *** NOT CURRENTLY WORKING !!! ***
Demonstrates how an application can be 'promoted' from one environment (namespace) to another. The example uses Development & Test/QA, to show how an application can be released in a manual and controlled manner.  See https://www.youtube.com/watch?v=Rzsa6VJRGDw for a demo. 

```
$ ./create-ose3-app-promo-envs.sh
```


#### Blue Green Deployment 
Demonstrates how you can deploy 2 versions of the same application, and quickly change the exposed route between them to allow one service or the other to be used. This example could be used in environments where there is still fairly rigid change control, who like a more 'big bang' release approach still. Could also be used for DR testing for the application on a regular basis! See https://www.youtube.com/watch?v=Rzsa6VJRGDw for a demo. 

```
$ ./create-ose3-app-bluegreen-deployment.sh
```

##### Demo steps
1. Please fork the project https://github.com/VeerMuchandi/bluegreen.  
2. vi the create-ose3-app-bluegreen-deployment.sh script to reference the new forked project (SRC= line near the top)
3. ./create-ose3-app-bluegreen-deployment.sh  Once you build the "blue" service, you need to pop over to your forked repo and do a code change to image.php (comment out blue and uncomment green).  Run through the rest of the script. 

#### AB Deployment 
Demonstrates how to do rolling A-B or Canary style deployment. Bring application version 1 into service. Then change the code to make version 2 and deploy that into the service but in incremental stages. Turn off version 1, once everyones happy with version 2. Enables a lower risk application deployment strategy, with rollback capabilities.

##### Demo steps
1. Please fork the project https://github.com/VeerMuchandi/ab-deploy.git
2. vi create-ose3-app-ab-deployment.sh script to reference the new forked project (SRC= line near the top)
3. ./create-ose3-app-ab-deployment.sh (Once it builds "app-a", you need to pop over to your forked repo and do a code change to index.php - the script will tell you this). Run through the rest of the script. 


### Running
In the Terminal (as the demo user):
```
$ cd /home/demo
$ git clone https://github.com/ffirg/openshift.git
$ cd openshift/bin
$ ./create-ose3-app-ab-deployment.sh
```
Follow the prompts! Some scripts need to be as run (for system:admin privileges) but the scripts check and advise :)
