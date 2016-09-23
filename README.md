# What is this?

Production SciDB 15.12 Python 3.5 Client System (for standalone or cluster) by Cerbo.IO

It includes SciDB specifics:
* perl 5
* python 3.5
* ipython 3.5
* python3-grib
* python3-netcdf4
* python3-pandas
* scidb-py
* jupyter
* iquery

Also:
* openssh
* wget
* screen
* git
* vim
* emacs

# Help/Questions/Comments:
For help or more info, feel free to contact us: support@cerbo.io (http://cerbo.io)

# How to run it:
```
docker run -it --rm=true cerbo/scidb-python-client
```
This will get you a bash shell, where you can run iquery, python, etc.

# How to run it as a service (with access via ssh):
```
CID=$(docker run --name=scidb-python-client -d cerbo/scidb-python-client /start-ssh)
```
```
IP=$(docker inspect --format '{{ .NetworkSettings.IPAddress }}' ${CID})
```

```
ssh root@$IP
pass: scidb
```

# How to run it IF you are using Cerbo's Grid/Mesh
```
docker run --name=scidb-python-client -d --net=XYZ --ip=A.B.C.D cerbo/scidb-python-client /start-ssh

* replacece "XYZ" with your overlay or macvlan docker network
* replace "A.B.C.D" with a valid and free IP from your "XYZ" network
```

# How to run it IF you are using Weave or Cerbo's Grid/Mesh
```
export DOCKER_HOST='unix:///var/run/weave/weave.sock'
```
and then:
```
docker run --name=scidb-python-client -d -e WEAVE_CIDR='$GRID_IP/$CIDR' cerbo/scidb-python-client /start-ssh
```
Similar to the standard service with ssh access, find out the IP address you received from your default docker bridge and ssh to that. From there, you will have access to the grid via the $GRID_IP
