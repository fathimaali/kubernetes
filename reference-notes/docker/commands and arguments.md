
* CMD 
    - command to run when container is run 
    - input param replaces the hard coded param of the CMD in this case
    - eg. sleep 5
* ENTRYPOINT /
    - command to run when the container starts, expects input param
    - input param gets appended to the ENTRYPOINT for execution
* ENTRYPOINT + CMD /
    - used to overcome the issue of ENTRYPOINT missing the input param
    - if no input is specified, CMD value specified in the image is appended
    - if input param is passed during runtime, it will override the CMD
* ENTRYPOINT override /
    - can we override the ENTRYPOINT if needed, (because that's technically hardcoded)
    - yes!
    - docker run --entrypoint sleep2 ubuntu-sleeper 10
    - here sleep2 overrides the hardcoded sleep, and 10 overrides harcoded 5


ubuntu is a container image, with CMD [bash], it starts and it exits. 

```
    docker run ubuntu [CMD]
```

changing CMD at runtime 
example: making the ubuntu 

```
    docker run ubuntu sleep 5 
```

if we wanna make this change permanent we change the container image and create new image ubuntu-sleeper
FROM ubuntu
SLEEP 5

    CMD command param1 or CMD ["command","param1"]
    CMD sleep 5 or CMD ["sleep","5"]

if we wanna change the number of seconds this will sleep, 5 is hard-coded in the image
it looks like 

    docker run ubuntu-sleeper sleep 10

if we dont want the command to look like that, we can change the param and code the CMD alone inside the image

    docker run ubuntu-sleeper 10

 
