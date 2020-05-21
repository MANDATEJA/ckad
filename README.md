# ckad

## Docker security:
A container running on a host runs all its processes on the host itself but within a different namespace. So, a process running inside a container with PID 1 can appear as process running on the host with a differenct PID like 65883.

By default docker runs the processes inside the conatienr as root user. This can be changes using USER commad in Dockerfile. The root user running inside the container will have less privilages as compared to root user running on host. This is implemented as part of docker security to prevent container root user from making changes to host that would affect host performance and more.

Additional privilages can be added or existing privilages can be removed from the container using below commands

To add a privilage:
docker run --cap-add MAC_ADMIN ubuntu

To remove a privilage:
docker run --cap-drop MAC_ADMIN ubuntu

To give full privilage:
docker run --privilaged ubuntu
