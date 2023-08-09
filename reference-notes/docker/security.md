# security on docker

process isolation  ;
    acheived through namespaces

user isolation : 
    acheived with linux capabilities
    /user/include/linux/capability.h
    by default, the root user inside the container does not have the same capability as the root user on the host
    if we wanna edit that and edit this container root user, we can change that by adding linux capability
    - docker run --cap-add SYS_TIME ubuntu
    - docker run --cap-drop SYS_TIME ubuntu
    - docker run --privileged ubuntu -> grant all priviliges

by default docker runs commands with root user
    can be changed 
        imperatively
            - docker run --user=1000 ubuntu-sleeper 3000
        declaratively
            dockerfile:
                FROM ubuntu
                USER 1000
            - docker run ubuntu-sleeper 3000


    

