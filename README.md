# gretl-local
A non-jenkins agent image for GRETL

Das Image ist ohne sämtliches Jenkins-Agent-Zeugs und sollte aus diesem Grund leichtgewichtiger sein. Wichtiger ist jedoch, dass es multitplatform-fähig ist: Es gibt ein `linux/amd64`- und ein `linux/arm64`-Image. Damit läuft es auch auf Apple Silicon Rechnern. 

Das Image weist den gleichen Stand wie das "normale" GRETL-Image auf. Der Buildprozess zum jetzigen Zeitpunkt nicht gekoppelt. Die Datei `start-gretl.sh` ist aus dem `gretljobs`-Repo kopiert und dient zum lokalen Testen. Die Buildlogik ist aus dem `gretl`-Repo.

Sinnigerweise sollte dieser Buildprozess im Original-Repo integriert werden, damit die Dependencies nicht nachgeführt werden müssen und die Versionsnummer (des Images) gleich sind.

```
./start-gretl.sh --docker-image sogis/gretl-local:latest [--docker-network NETWORK] --job-directory $PWD/jobname [taskName...] [--option-name...]

```