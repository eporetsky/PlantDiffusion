This Docker container runs [DynamicBind](https://github.com/luwei0917/DynamicBind/).

Note: I didn't have the chace to test if DynamicBind itself runs properly in this environment but I the installation itself seems to complete succesfully. 

Build the Docker container:
```
docker build --rm -f Dockerfile -t ubuntu:DynamicBind .
```

Run the docker container with a shared PDB mount:
```
docker run --shm-size 8G --gpus all -it -v ${PWD}:/dynamicbind ubuntu:DynamicBind /bin/bash
# ${PWD} on windows/$PWD for linux 
```

Once you start running the Docker container, your commandline should be redirected to the Docker terminal. From there you can run the different packages mentioned below. The current directory is mounted to the /DynamicBind directory in the container image for persistant access with the Docker environment.

```
cd DynamicBind
conda activate dynamicbind
python run_single_protein_inference.py ...
```