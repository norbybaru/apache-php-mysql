## Decouple dependencies, run one process per container

Containers at the core are simply process encapsulation within a shared Linux kernel, 
to allow for many processes to run inside of their own spaces without interfering or interacting unless we explicitly tell them they can. 
Thus, it is a long-running best practice to run your primary service within a container as PID 1. 
This means that no other process should be running inside of your containers. 
It allows containers to maintain a native linux process lifecycle, respect linux process signals, 
allow for greater security, 
and will make your life easier when you schedule these containers on orchestrators such as Docker Swarm or Kubernetes in production.

#### Running Apache and PHP in separate containers

Commands:
- Start containers
```$xslt
docker-compose up -d
```
- View logs once containers are up
```$xslt
docker-compose log -f -t
```
- curl this url on terminal or open on browser and this shuld tell you if everything is setup correctly.
```$xslt
curl http://localhost:8080/
```
