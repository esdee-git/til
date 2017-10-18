docker-compose build:
...
Step 7/11 : RUN wget -O /tmp/blazegraph.jar https://github.com/blazegraph/database/releases/download/BLAZEGRAPH_RELEASE_${BLAZEGRAPH_VERSION}/blazegraph.jar
 ---> Running in eb616a255855
wget: bad address 'github.com'

wget cannot resolve the webserver name

to resolve need to add
nameserver a.b.c.d.
nameserver z.y.x.w

to /etc/resolv.conf on the host machine
for all dns servers


java.io.IOException: failed to obtain lock
for me no matter how i tried to fix this problem, playing with docker volume settings, user id 1000 and on and on, it turned out that the real problem was another exception, a little earlier in the stacktrace:
 Caused by: java.io.IOException: Mount point not found

once i realised this, finding the solution was easier:
change docker's storage from overlay2 to aufs - problem solved

on mac(change in Preferences/advanced)
on Linux add file in /etc/docker/daemon.json
both should contain:
{
  "storage-driver" : "aufs"
}

