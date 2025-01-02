# MICCAI 2023/CROWN_CHALLENGE/DCS_CUSAT_TASK1
This repository contains all the necessary files and configurations required to set up and run the model submitted to crown challenge, enabling users to easily deploy and validate the network in their own environment. 
Due to memory limitations of the GitHub repository, the ready-to-use Docker container (crownchallenge/dcs_cusat_task1) and sample input can be accessed via the following link: https://shorturl.at/K58N3
# Usage
You can load the dcs_cusat_task1 docker image directly from the dcs_cusat_task1.tar using the following command:
```bash
docker load < dcs_cusat_task1.tar
```

 Then, you can run the ready-to-use crownchallenge/dcs_cusat_task1 container with the following command:
```bash
docker run -dit --network none -v [full_path_to_input_dataset]:/input:ro -v /output crownchallenge/dcs_cusat_task1
```

The -v options map the input directory into the container at /input, read-only. The last -v creates an output directory.
This command outputs the Container ID,  which you can also look up with the following command:
```bash
docker ps
```
Next, you can execute the model's validation script using the following command:

```bash
docker exec [CONTAINER-ID] python /crown_dcs/run.py
```

Then, you can copy the output from the container to your local machine with the following command: 

```bash
docker cp [CONTAINER-ID]:/output [full_path_to_output_location]
```

Finally, you can shut down the running container. This also removes the created /output folder and any other changes made to the container:

```bash
docker rm -v [CONTAINER-ID]
```



