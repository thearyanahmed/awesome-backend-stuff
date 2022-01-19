# dockerfile 

Commands 

```bash
// source image
FROM baseImage:version

//entrypoint
ENTRYPOINT ["executable", "param1", "param2"]
ENTRYPOINT command param1 param2

//This will use shell processing to substitute shell variables, and will ignore any CMD or docker run command line arguments.


// commands 
EXPOSE port1 port2 
CMD ["executable","param1","param2"]

// variables 
ENV APP_HOME /myapp
RUN mkdir $APP_HOME

ARG APP_HOME=""
RUN mkdir $APP_HOME

// mount 
ADD /local/machine/directory /inside/container/directory
```

## multi stage builds
Helpful because docker will cache these layers, untill anything changes in intermediate layer ( until RUN #some expensive operation), it will be cached and used on future builds. 
```bash
FROM ubuntu as intermediate
RUN mkdir -p /data
RUN mkdir -p /result
ADD data.tar /data/data.tar
RUN #some expensive operation
# finally, /result ends up with the final data

FROM ubuntu
COPY --from=intermediate /result /result
# simply use the result
```