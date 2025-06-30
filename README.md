# Workflow manager hello world tests

This repo consists of code and dataused to complete the [Snakemake General Use](https://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html) tutorial

## Directory structure

```
.
├── README.md
├── config
├── resources
├── results
├── snakemake-environment.yml
└── workflow
    ├── Snakefile
    ├── envs
    ├── notebooks
    ├── report
    ├── rules
    └── scripts
```

## Snakemake tutorial

Environment setup

Install pixi.
The shell may require restarting after pixi and miniconda installation.

```
curl -fsSL https://pixi.sh/install.sh | bash
```

Ensure that miniconda is installed

```
curl -L https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh -o Miniforge3-Linux-x86_64.sh

bash Miniforge3-Linux-x86_64.sh
```

If minifconda has not been previously installed, answer "yes" to `Do you wish the installer to prepend the install location to PATH ...? [yes|no]`.

Enter the snakemake tutorial directory
```
cd snakemake-tutorial
```

Download example data

```
curl -L https://api.github.com/repos/snakemake/snakemake-tutorial-data/tarball -o snakemake-tutorial-data.tar.gz
```

Extract example data
```
tar --wildcards -xf snakemake-tutorial-data.tar.gz --strip 1 "*/data" "*/environment.yaml"

```

Initialize conda environment with pixi

```
pixi init --import environment.yaml
```

Activation of conda environment

```
pixi shell
```

Test that environment is activated my invoking the snakemake help message:
```
snakemake --help
```

Create DAG of all jobs
```
snakemake --dag | dot -Tsvg > alljobs_dag.svg
```

Run all jobs in Snakefile
```
snakemake -p --cores 1
```
