
- [RLUS-BINARY-SEARCH](https://github.com/armandiag/RLUS-BINARY-SEARCH): A Python implementation of the RLUS-BINARY-SEARCH algorithm.
- [RLUS-BRUTEFORCE](https://github.com/armandiag/RLUS-BRUTEFORCE): A Python implementation of the RLUS-BRUTEFORCE algorithm.
- [RLUS-HEURISTIC](https://github.com/armandiag/RLUS-HEURISTIC): A Python implementation of the RLUS-HEURISTIC algorithm.


**Prerequisites**

Docker installed on your system.

**Setup and Execution**

Follow these steps to set up and execute the project within a Dockerized environment.

**Step 1**: Clone the Repository

Open your terminal or command prompt.

Clone the repository to your local machine and navigate into the project directory.


git clone <repository-url>
cd <repository-directory>


**Step 2**: Build the Docker Image


docker build -t <project_name> .

**Step 3**: Make sure your project directory contains the following structure:

.
├── Dockerfile
├── requirements.txt
├── data
│   └── [data files, e.g., 9_20_2017.csv, 9_21_2017.csv, ...]
├── logs
│   └── [log files will be generated here]
├── results
│   └── [result files will be generated here]
├── scripts
│   ├── master_script.sh
│   ├── measure_time.sh
│   ├── run_20.sh
│   ├── run_21.sh
│   └── ...
├── C_bootstrap.py
├── C_command_line_main.py
└── C_RLUS.py

**Step 4**: Run the Docker Container

docker run --rm -v /absolute/path/to/project:/app <project_name> 

This command will execute the measure_time.sh script inside the container, which runs master_script.sh to process all data files in parallel.

**Step 5**: Review the Logs: when the container finishes running, check the logs/ directory for execution logs. This directory will contain detailed logs of each task's execution time and any error messages. Also, check the results/ directory to see the rho values.

- docker logs <container-id>

You can find the <container-id> by running docker ps -a if the container is still listed.

- Python Dependencies: All necessary Python dependencies are listed in requirements.txt. These will be installed automatically in the Docker container during the build process. The dependencies include:

numpy
pandas
argparse

- Additional Notes

  - The project is designed to handle multiple data files with different epsilon values for each script.
  - You may modify the epsilon ranges directly in the individual run_xx.sh scripts located in the scripts/ directory.
