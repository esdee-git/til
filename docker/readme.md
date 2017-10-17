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
