# Walk-Through: PrimedRPA Primer Design Setup and Execution

This guide walks you through setting up and running the repo [PrimedRPA](https://github.com/Szor54/RPA-Primer-Program-2.0.git) based on [PrimedRPA orginal](https://github.com/MatthewHiggins2017/bioconda-PrimedRPA) primer design tool in a reproducible Docker environment using Visual Studio Code (VSCode) with full container support.

---

## Prerequisites

Before beginning, ensure the following are installed:

- **[Docker](https://docs.docker.com/get-docker/)** – Required to run the environment in a container.
- **[Visual Studio Code](https://code.visualstudio.com/Download)** – Your main IDE.
- **[Git](https://git-scm.com/downloads)** - To clone the repo
- **Remote - Containers Extension for VSCode**
  - Install this from the Extensions panel or run `Ctrl+Shift+P` → “Extensions: Install Extensions” → Search: `Remote - Containers`.

---

## Development Environment with Docker and VSCode

Create the following folder structure inside your project, should be made after git clone and the steps above:

```
/RPA-Primer-Program-2.0
│
├── .devcontainer/
│   ├── devcontainer.json
│   └── Dockerfile
│
├── RPA-Primer-Program-2.0-main/
│   ├── LICENSE
│   ├── meta.yaml
│   ├── PrimedRPA_Parameters.txt
│   ├── PrimedRPA.py
│   ├── PrimedRPA.yml
│   └── (other files...)
│
├── .gitignore
├── README.md
└── setup.md

```

---

## Launch the Dev Container in VSCode

1. Open the project in VSCode.
2. Press `Ctrl+Shift+P` and run:

   ```
   Remote-Containers: Reopen in Container
   ```

VSCode will now build the container and open a terminal inside it.

---

## Running the Primer Design Script

After ensuring the parameters are corrrect
cd into the `RPA-Primer-Program-2.0-main` directory and run the program using:

```bash
cd RPA-Primer-Program-2.0-main
python3 PrimedRPA.py PrimedRPA_Parameters.txt
```

Make sure you use `python3`, **not just `python`**, to ensure the correct interpreter is used (if in the container, if on windows use `python`).

---

## Output

The program will output the following files:

* `[RunID]_Alignment_Summary.csv`
* `[RunID]_PrimedRPA_Oligo_Binding_Sites.csv`
* `[RunID]_Output_Sets.csv`

These files contain your alignment summary, valid primer/probe candidates, and final primer-probe set combinations.

---

## Summary

This setup guided you through:

1. Installing **Docker** and **VSCode**.
2. Using **Remote Containers** to build an isolated development environment.
3. Cloning and configuring the **PrimedRPA** genome and parameter inputs.
4. Running the `PrimedRPA.py` script inside the container using `python3`.

You now have a fully functional and reproducible setup to design RPA primers.


By Scott Rose

