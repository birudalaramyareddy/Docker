the difference between CMD, RUN and ENTRYPOINT 

 RUN executes command(s) in a new layer and creates a new image. E.g., it is often used 
for installing software packages.

 CMD sets default command and/or parameters, which can be overwritten from 
command line when docker container runs.

 ENTRYPOINT configures a container that will run as an executable


What is the difference between CMD and ENTRYPOINT? 
You cannot override the ENTRYPOINT instruction by adding command-line parameters to the docker run command


RUN
RUN instruction allows you to install your application and packages required for it. It executes 
any commands on top of the current image and creates a new layer by committing the results. 
Often you will find multiple RUN instructions in a Dockerfile.

CMD
CMD instruction allows you to set a default command, which will be executed only when you 
run container without specifying a command. If Docker container runs with a command, the 
default command will be ignored. If Dockerfile has more than one CMD instruction, all but last 
CMD instructions are ignored.


CMD has three forms:
CMD ["executable","param1","param2"] (exec form, preferred)
CMD ["param1","param2"] (sets additional default parameters for ENTRYPOINT in exec form)
CMD command param1 param2 (shell form)

ENTRYPOINT
ENTRYPOINT instruction allows you to configure a container that will run as an executable. It 
looks similar to CMD, because it also allows you to specify a command with parameters. The 
difference is ENTRYPOINT command and parameters are not ignored when Docker container 
runs with command line parameters. (There is a way to ignore ENTTRYPOINT, but it is unlikely 
that you will do it.)

ENTRYPOINT has two forms:
ENTRYPOINT ["executable", "param1", "param2"] (exec form, preferred)
ENTRYPOINT command param1 param2 (shell form)
Be very careful when choosing ENTRYPOINT form, because forms behaviour differs significantly.


The bottom line:

Use RUN instructions to build your image by adding layers on top of initial image.
Prefer ENTRYPOINT to CMD when building executable Docker image and you need a command 
always to be executed. Additionally use CMD if you need to provide extra default arguments 
that could be overwritten from command line when docker container runs.
Choose CMD if you need to provide a default command and/or arguments that can be 
overwritten from command line when docker container runs.