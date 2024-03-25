The EXPOSE instruction exposes the specified port and makes it available only for inter-container 
communication. Let’s understand this with the help of an example.
Let’s say we have two containers, a nodejs application and a redis server. Our node app needs to 
communicate with the redis server for several reasons.
For the node app to be able to talk to the redis server, the redis container needs to expose the port. 
Have a look at the Dockerfile of official redis image and you will see a line saying EXPOSE 6379. This 
is what helps the two containers to communicate with each other.
So when your nodejs app container tries to connect to the 6379 port of the redis container, the 
EXPOSE instruction is what makes this possible.

Note: For the node app server to be able to communicate with the redis container, it’s important 
that both the containers are running in the same docker network.