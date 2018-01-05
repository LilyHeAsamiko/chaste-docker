Chaster
=======

*Dockerfiles for Chaste*

Quickstart
----------

1. Install [Docker](https://www.docker.com) and configure it to have at least 4GB of RAM and as many cores as you have. For [Windows](https://docs.docker.com/docker-for-windows/install/#download-docker-for-windows) you may be prompted to install Hyper-V, in which case do so. Also select which local drives to be available to containers (e.g. the C: drive in Windows).

2. `docker build -t chaste:dependencies https://github.com/bdevans/chaste-docker.git`

3. Navigate to the folder where you would like to clone and build Chaste e.g. C:\Users\$USERNAME\chaste (Windows) or ~/chaste (Linux/MacOS).
    a) Windows
    i) If using the command prompt: `docker run -it -v %cd%:/home/chaste chaste:dependencies`
    ii) Alternatively if you are using PowerShell§ then type: `docker run -it -v ${PWD}:/home/chaste chaste:dependencies`.
    b) Linux / MacOS: `docker run -it -v $(pwd):/home/chaste chaste:dependencies`

4. You should now have a running container. To build Chaste, within the container type:
```
build_chaste.sh
```

5. Optionally run the continuous test pack: `ctest -j$(nproc) -L Continuous`


<div class="alert alert-success">
N.B. Docker containers are ephemeral by design and no changes will be saved after exiting except to files in the home directory which is where the host's present working directory is mounted.
</div>

§ If you are using PowerShell, you can enable tab completion by installing pos-docker: https://docs.docker.com/docker-for-windows/#set-up-tab-completion-in-powershell
