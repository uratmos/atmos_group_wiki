# Using the Atmos Stack

## Keep `.bashrc` minimal

Keep your `.bashrc` file as empty as practical. Although you can configure it to
run `activate_atmos_stack` automatically, the command makes many changes to your
environment. It is generally better to activate the Atmos Stack manually when
starting a session.

## Activate the Atmos Stack in scripts

When running a script, such as a model `sbatch` script, ensure that the Atmos
environment is active. It is safe to call `activate_atmos_stack` when the stack
is already active because it will not attempt to reload the environment.

Within scripts, source the activation script directly:

```bash
source /sfw/rhel9-x86_64/atmos/bin/_activate-Atmos-Stack
```

This does not depend on the activation function already being sourced and works
for anyone using BlueHive.

## Load Spack environments

The `spacktivate` command is an alias for `spack env activate`. Aliases work in
interactive console sessions but are not available within Bash or `sbatch`
scripts.

For an interactive session, use:

```bash
spacktivate <model-environment>
```

Inside a script, use:

```bash
spack env activate <model-environment>
```

Replace `<model-environment>` with the name of the environment you want to use.
