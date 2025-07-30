# Walk-Through: PrimedRPA Primer Design Setup and Execution

This guide walks you through setting up and running the repo [PrimedRPA](https://github.com/Szor54/RPA-Primer-Program-2.0.git) based on [PrimedRPA orginal](https://github.com/MatthewHiggins2017/bioconda-PrimedRPA) primer design tool in a reproducible Docker environment using Visual Studio Code (VSCode) with full container support.

---

## Prerequisites

Before beginning, ensure the following are installed:

- **[Docker](https://docs.docker.com/get-docker/)** – Required to run the environment in a container.
- **[Visual Studio Code](https://code.visualstudio.com/Download)** – Your main IDE.
- **Remote - Containers Extension for VSCode**
  - Install this from the Extensions panel or run `Ctrl+Shift+P` → “Extensions: Install Extensions” → Search: `Remote - Containers`.

---

## Development Environment with Docker and VSCode

Create the following folder structure inside your project, should be made after git clone and the steps above:

```
/[RPA Project Name]
│
├── .devcontainer/
│   ├── devcontainer.json
│   └── Dockerfile
├── GCF_000896435.1_ViralProj76727_genomic.fna
├── PrimedRPA_Parameters.txt
└── (your script files will go here)
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
cd into the `RPA-Primer-Program-2.0-main` directory using:

```bash
cd RPA-Primer-Program-2.0-main
```

Run the program:

```bash
python3 PrimedRPA.py PrimedRPA_Parameters.txt
```

Make sure you use `python3`, **not just `python`**, to ensure the correct interpreter is used.

---

## Output

The program will output the following files:

* `[RunID]_Alignment_Summary.csv`
* `[RunID]_PrimedRPA_Oligo_Binding_Sites.csv`
* `[RunID]_Output_Sets.csv`

These files contain your alignment summary, valid primer/probe candidates, and final primer-probe set combinations.

---

## Summary

This README guided you through:

1. Installing **Docker** and **VSCode**.
2. Using **Remote Containers** to build an isolated development environment.
3. Cloning and configuring the **PrimedRPA** genome and parameter inputs.
4. Running the `PrimedRPA.py` script inside the container using `python3`.

You now have a fully functional and reproducible setup to design RPA primers.

