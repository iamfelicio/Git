# Git Service Under Various Protocols
_using Docker technology_

This project demonstrates containerization practices on a subject of version control. Each of inspected Dockerfiles focuses on configuration of a runtime environment for bare repositories' distribution via specified data transfer protocol.

__Currently supported solutions are:__
- [x] Git protocol
- [x] SSH protocol
- [ ] HTTP protocol

When built and run user is left with a container (an application) that serves user's provided Git repositories either to read-only public access or read-write access for contributors.

![Alt text](Resources/git.png)

## Build, Run
### Docker Engine
#### Git Protocol

To simply share your work with others on trusted network run the following command.
```bash
docker build -t IMAGE PATH/git
docker run -dP -v PATH:/srv/git/public --name CONTAINER IMAGE
```

#### SSH Protocol

To let others contribute to your work add their public keys to a single file you'll later mount to the container.
```bash
docker build -t IMAGE -f PATH/ssh
docker run -d -p P:22 -v /PATH:/home/git/.ssh/authorized_keys -v /PATH:/srv/git/private felicio/ssh
```
#### Clean up
```bash
docker stop CONTAINER
docker rm -v CONTAINER
docker rmi IMAGE
```

### Docker Compose
#### Git Protocol
#### SSH Protocol
#### Clean up


## Clone
_from a running container_

#### Git Protocol

```bash
git clone git://HOST:PORT/PATH
```
#### SSH Protocol

```bash
git clone ssh://git@HOST:PORT/PATH
```
