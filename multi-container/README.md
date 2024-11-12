*Learnings*

A pod can have multiple containers. Having said that it is recommended that it should be a main app and others be side car conatiners which support the main app like logging etc.

when such pod is created the inti containers are created first. Unless they start the main app wont start.

first we created a pod with a main app container and 2 init containers which interally do a nslooup in the service. 
this nslookup will fail initailly due the service not being created. which causes the init conatiner to go to pending state untill service is up.
once the servoce is created the pod starts running.

