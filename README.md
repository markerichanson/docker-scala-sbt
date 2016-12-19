# docker-scala-sbt
Scala sbt image built and tested for spark builds


* [`2.11.8-0.13.13`](https://hub.docker.com/r/markerichanson/docker-scala-sbt/)

## Pulling
```sh
docker pull markerichanson/docker-scala-sbt
```

## Building
```sh
docker build -f docker-scala-sbt/Dockerfile -t "markerichanson/docker-scala-sbt:2.11.8-0.13.13" --build-arg SBT_VERSION=0.13.13 .
```

# docker run parms
## /root/.ivy2
Ivy2 cache location in your local file system so you don't have to download dependencies on every build.
This is safe to share across different projects.
```sh
-v ~/.ivy2/:/root/.ivy2
```
## /root/project
The root directory of the project to build, i.e., the directory with the .sbt file in it.
```sh
-v $PWD:/root/project
```

# Suggested aliases
```sh
# for direct invocation of sbt on your command line
alias sbt='docker run -it  -v ~/.ivy2/:/root/.ivy2  -v $PWD:/root/project markerichanson/docker-scala-sbt:2.11.8-0.13.13 sbt'
# for a bash session in the sbt environment, though this isn't likely needed except for debuging the image
alias sbt_bash='docker run -it  -v ~/.ivy2/:/root/.ivy2  -v $PWD:/root/project markerichanson/docker-scala-sbt:2.11.8-0.13.13 bash --login'
```

