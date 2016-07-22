# Jenkins SSH slave + docker

[`zfil/ssh-slave`](https://hub.docker.com/r/zfil/jenkins-slave/)

A [Jenkins](https://jenkins-ci.org) slave using SSH to establish connection.

See [Jenkins Distributed builds](https://wiki.jenkins-ci.org/display/JENKINS/Distributed+builds) for more info.

## Note

This image is inspired from [`jenkinsci/ssh-slave`](https://hub.docker.com/r/jenkinsci/ssh-slave/)

## Running

To run a Docker container

    docker run -v /var/run/docker.sock:/var/run/docker.sock zfil/ssh-slave "<public key>"

You'll then be able to connect this slave using ssh-slaves-plugin as "jenkins" with the matching private key.
