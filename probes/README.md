Probes do health check either by TCP,HTTP,cmds

Liveness Probe - recovers the containers from application errors, networking errors by restarting.

Readiness Probe - Ensures application is ready to accept traffic. Attaches the pods to loadbalancers only after these are passed.

Startup - A probe for legacy application that take a lot of time to startup.