-> Similar to deployments

### Why stateful sets:
* In case of multi-pod database dpeloyments, if we want the pods to be intitialized in a certain order(master, slave1, slave2 etc.,), we cannot do it with Deployment objects, stateful sets can bye used instead.
* We can designate pods as master and slave with stateful sets indexes

=> you must specify a headless service name in stateful set definition file
