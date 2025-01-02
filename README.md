# CROWN_DCS_CUSAT
# ICADnet: Prior Knowledge-based Framework for Intracranial Aneurysm Detection on TOF-MRA using Coupled CNN
ICADnet is  a prior knowledge-based framework for aneurysm detection from TOF-MRA volume.  It embeds task-specific domain knowledge as a function or operator into the deep learning model to develop a framework for aneurysm detection with limited training samples and, thereby, improve the generalization and  efficiency of the CAD systems. 

This repository contains all the necessary files and configurations required to set up and run ICADnet, enabling users to easily deploy and validate the network in their own environment. The Sample_Dataset folder contains some test samples of 3D TOF-MRA for ICADnet framework.
# Usage
You can load the ICADnet docker image directly from the icadnet_docker.tar using the following command:
```bash
docker load < icadnet_docker.tar
```

 Then, you can run the ready-to-use icadnet_docker container with the following command:
```bash
docker run -dit --network none -v [full_path_to_input_dataset]:/input:ro -v /output icadnet_docker
```

The -v options map the input directory into the container at /input, read-only. The last -v creates an output directory.
This command outputs the Container ID,  which you can also look up with the following command:
```bash
docker ps
```
Next, you can execute the ICADnet validation script using the following command:

```bash
docker exec [CONTAINER-ID] python /ICADnet_dockerfolder/run.py
```
Finally, you can shut down the running container. This also removes the created /output folder and any other changes made to the container:

```bash
docker rm -v [CONTAINER-ID]
```

Due to memory limitations of the GitHub repository, the ready-to-use Docker container can be accessed via the following link: https://shorturl.at/I5Q7z


