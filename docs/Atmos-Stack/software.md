# Atmos Stack Software

The Atmos Stack provides software through default installations, Spack
environments, modules, and Conda environments.

## Default software

A selection of useful, up-to-date software is maintained and added directly to
your `PATH`. This software can be used without first loading a module. For
example, running `vim` provides an up-to-date, feature-rich version of Vim.

Unlike in the default CIRC environment, Slurm is provided through `PATH` rather
than through a module. Commands such as `sinfo` and `squeue` therefore work
without loading a module.

To see the complete list of default software, run:

```bash
DefaultSoftwareList
```

## Spack

Most software is installed and maintained using the Spack package manager.
Spack is activated by default in the Atmos environment, giving users access to
Spack environments with:

```bash
spack env activate <model-environment>
```

Replace `<model-environment>` with the name of the environment you want to use.
In interactive sessions, you can use the shorter command:

```bash
spacktivate <model-environment>
```

The `spacktivate` alias does not work in Bash or `sbatch` scripts. Run the
following command to see all available model environments:

```bash
spack env list
```

## Modules

Modules play a smaller role in the Atmos Stack than on most clusters because
they are not used to set up model runs. However, selected software is available
through modules for analysis and development.

The most important module is `miniforge3`, which is used to load and unload
Conda.

## Conda

Activate Conda by loading the `miniforge3` module:

```bash
module load miniforge3
```

This installation provides a cleaner version of Conda that can be activated and
deactivated as needed. Conda is not enabled by default because it can easily
clutter environments.

You can use Conda to access your own environments or group-managed environments.
When you run `conda env list`, paths under the `/sfw` group software directory
identify group-managed environments.

To make a Conda environment available to the whole group, contact the Atmos
Stack maintainer about copying it into the group software directory.

### Configure Conda storage

> **Important:** Configure Conda to use scratch storage before creating an
> environment or installing packages. Conda environments can quickly fill your
> smaller home directory.

If you have already used Conda, inspect your existing configuration and update
it manually rather than overwriting it:

```bash
cat ~/.condarc
```

For a new `~/.condarc` file, run:

```bash
cat > ~/.condarc <<'EOF'
envs_dirs:
  - /scratch/${USER}/.conda/envs
pkgs_dirs:
  - /scratch/${USER}/.conda/pkgs
EOF
```

These settings ensure that your environments and packages are stored in scratch
rather than in your smaller home directory.
