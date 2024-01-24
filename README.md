# spark-serverless-project
work in progress

### Account creation
To set up a Google Cloud account, we have two options, we can set up a full account with all the functionality offered or we can use a test account in which we receive 300\$ to use within 90 days. We opted for the test account. The disadvantage was that, although we only wanted to use the test version, we had to plug in our card. Google argues that this is a self-test, but at the same time guarantees that no funds will be collected until we upgrade to a full account. Nevertheless, distaste remains because not everyone likes to give out such important data if it is not necessary, and it would be nice to be able to use, for example, student email verification (in the case of students). As a matter of interest, the amount of US$ 300 was converted into the currency of our country at the time the account was opened.

We also checked the installation process of the gcloud client locally. We assess that it is user-friendly, quick, and does not require many steps, and it is possible to use the installer or a few commands in the console. Interestingly, in the case of authorization, a browser is launched in which we only need to log in to our Google account, which is a pleasant solution. 

### Problems
In our project, we encountered some resource scalability issues. Despite several attempts on different types of jobs, we could not force the system to allocate more working executors, despite the much higher demand. Graphs from the analysis of specific jobs on the Google platform also confirmed this. This aroused our interest and concern. We therefore manually started to increase the number of initial executors, within the relevant auto-scaling parameters. Quite quickly it became apparent that we had some resource limitations within the test account on Google Cloud, in this case, we found that we could use a maximum of 24 CPUs cors at any one time.

This was in line with our observations because after some simple maths, our phs server on which Spark UI was running on an instance with 4 cores, while our job in Spark serverless with standard spark properties settings allocated 4 cores to the driver and 4 cores to each subsequent executor, which allowed us to have a maximum of 4 executors, or 5 if the spark ui server was switched off. We have checked whether it is possible to increase this limit manually, but the Google Cloud trial account does not allow this. 

To do this, it is necessary to switch to the full version, but even in this case, it is not possible to do this immediately, because you need to send a request to the administrator together with the justification of your needs, which may take some time. If you would like to change the settings or check other restrictions in detail, this can be done under Administration=>Limits and System Restrictions. Please note that once you have switched to a full account, future charges may be taken from the linked credit card.


