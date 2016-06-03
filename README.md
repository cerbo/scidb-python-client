# What is this?

Production SciDB 15.12 Python 3.5 Client System (for standalone or cluster) by Cerbo.IO

It includes SciDB specifics:
* python 3.5
* python3-grib
* python3-netcdf4
* scidb-py
* iquery

Also:
* openssh
* wget
* screen
* vim

# Help/Questions/Comments:
For help or more info, feel free to contact us: support@cerbo.io (http://cerbo.io)

# How to run it:
```
docker run -it --rm=true cerbo/scidb-python-client
```

# How to run it as a service (access via ssh):
```
CID=$(docker run --name=scidb-python-client -d cerbo/scidb-python-client /start-ssh)
docker inspect --format '{{ .NetworkSettings.IPAddress }}' ${CID}

ssh root@{IP-from-above}
pass: scidb
```

# How to run it IF you are using Weave:
```
export DOCKER_HOST='unix:///var/run/weave/weave.sock'
```
and then:
```
docker run --name=scidb-python-client -d --net=none -e WEAVE_CIDR='$SUBNET/$CIDR' cerbo/scidb-python-client /start-ssh
```
