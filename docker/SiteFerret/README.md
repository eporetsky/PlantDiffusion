## SiteFerret (**not working**)

A Docker image for SiteFerret used for detecting protein binding pockets.

Build the Docker container:
```
docker build --rm -f Dockerfile -t ubuntu:siteferret .
```

Run the docker container with a shared PDB mount:
```
docker run --name=siteferret -v ${PWD}/mount/pdb:/mount --rm -it ubuntu:siteferret
# To use sudo, the password is `password`
```

This is Docker image is based on the template image found here: https://github.com/maliksahil/docker-ubuntu-sahil
