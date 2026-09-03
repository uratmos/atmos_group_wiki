# Running GEOS-Chem on BlueHive

This guide explains the BlueHive-specific steps for using GEOS-Chem. For general
instructions, consult the
[GEOS-Chem documentation](https://geos-chem.readthedocs.io/en/stable/getting-started/quick-start.html).

## 1. Start an interactive job

Before setting up GEOS-Chem, request an interactive compute session:

```bash
srun --partition=interactive --cpus-per-task=8 --mem=32G --time=12:00:00 --pty bash
```

## 2. Set up the GEOS-Chem environment

After [activating the Atmos Stack](../Atmos-Stack/index.md), activate the
GEOS-Chem Classic Spack environment:

```bash
spack env activate GCClassic
```

This loads the environment variables and software needed to run GEOS-Chem.

## 3. Follow the GEOS-Chem Quickstart Guide

### Create a working directory

Create a GEOS-Chem directory in your personal scratch space and move into it:

```bash
mkdir /scratch/<username>/GEOS-Chem
cd /scratch/<username>/GEOS-Chem
```

Replace `<username>` with your BlueHive username. See the
[CIRC BlueHive scratch documentation](https://www.circ.rochester.edu/info-circ)
for more information about using scratch storage.

### Apply the BlueHive-specific adjustments

Follow the
[GEOS-Chem Quickstart Guide](https://geos-chem.readthedocs.io/en/stable/getting-started/quick-start.html#clone-geos-chem-classic)
with these adjustments:

1. In Step 2, creating a run directory prompts you for several settings. When
   asked to `Enter path for ExtData`, provide:

```text
/gpfs/fs2/scratch/ltmurray_lab/data/input/gc/ExtData
```

   The first run creates `~/.geoschem/config` and stores the ExtData path there.
   You do not need to enter it again unless the ExtData directory moves.

2. Skip Step 3, **Load your environment**. The `GCClassic` Spack environment
   activated above already provides the required software and environment
   variables.

3. Skip Step 7, **Download input data**. The required input data has already
   been downloaded for the group.
