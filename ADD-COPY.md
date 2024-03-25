COPY and ADD are both Dockerfile instructions that serve similar purposes. They let you copy files 
from a specific location into a Docker image.

COPY
The COPY instruction copies files or directories into the Docker image.
It takes a src and destination as arguments.
Source can be absolute or relative from current WORKDIR or wild cards.
Destination path can be absolute or relative to current WORKDIR.

For Example:
COPY ./requirements.txt /app/requirements.txt
COPY package.json package-lock.json /app
COPY package*.json /app
COPY . /app

ADD
The ADD instruction copies files, directories, remote file or tar archive into the Docker 
image.
It takes a src and destination as arguments.
Source can be files and directories.
Source can be a URL. The ADD instruction will download the file from the URL and save it to 
the destination. We don’t need to use curl or wget to download a file.
Source can be a local tar/zip archive. The ADD instruction will automatically extract it to the 
destination. We don’t need to run unarchive commands manually.
Use ADD when you want download a file from a URL or extract local archive file.


For Example: 
ADD ./example.tar.gz /tmp/
ADD https://bootstrap.pypa.io/get-pip.py /get-pip.py /get-pip.py
ADD example.txt /tmp/
ADD https://mirrors.estointernet.in/apache/tomcat/tomcat-8/v8.5.58/bin/apache-tomcat- 
8.5.58.tar.gz /tmp/

ADD command just copied and extracted where COPY only do copy the files.
If you want to extract the tar file need to add one more extra command in Dockerfile.

Instead of using add to download form remote url use curl or wget and use && multiple commands 
to execute.

Note - difference between ADD and COPY is that COPY has the --
from=<name|index> flag that lets you copy files from a previous build stage in a multi-stage build. 
ADD does not have this option.
This is another reason to use COPY as your preferred option.