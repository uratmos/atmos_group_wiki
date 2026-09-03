# Getting Started

This documentation explains how to use BlueHive for atmospheric chemistry and
climate research. It summarizes key concepts; for more detailed information,
consult the [CIRC BlueHive documentation](https://www.circ.rochester.edu/info-circ).

## Login nodes

BlueHive currently has two login nodes:

- Legacy: `<username>@bluehive.circ.rochester.edu`
- BlueHive 3: `<username>@bluehive3.circ.rochester.edu`

All Atmos group nodes are on BlueHive 3, so group members should use the
BlueHive 3 login node.

## Move to a compute node

When you log in, your command prompt ends with `<username>@bluehive3` (or
`<username>@bluehive` on the legacy system). This indicates that you are on a
login node.

Think of a login node as a shared lobby: everyone arrives there, so any work
performed on it can affect other users. Limit activity on login nodes to
lightweight tasks, such as navigating directories. Run scripts and other
substantial work on a compute node. Slurm reserves compute resources for this
work, as described in the [Slurm guide](Slurm/index.md).

To start a general-purpose interactive session, run:

```bash
srun --partition=interactive --cpus-per-task=8 --mem=32G --time=12:00:00 --pty bash
```

This provides an interactive session with approximately the same computing
power as a desktop computer. When the command prompt changes from
`@bluehive3` to a hostname such as `@bhdrb8x0158`, you are on a compute node.

## Storage

BlueHive provides three main storage locations:

| Location | Purpose | Notes |
| --- | --- | --- |
| `/home/<username>` | Configuration files | Backed up, but limited to a few tens of gigabytes |
| `/scratch/<username>` | Personal working data | Provides hundreds of gigabytes but is not backed up |
| `/scratch/ltmurray_lab` | Shared input data, including emissions inventories and meteorological fields | Write to this directory only when asked by Lee or Peter |

Because scratch storage is not backed up, its contents could be lost if a
catastrophic data-center failure occurs.

Your home and scratch usage appears when you log in. You can also check it by
running:

```bash
quota
```

## Use group-managed software

The instructions above cover the basic BlueHive workflow with CIRC software.
To use the group's atmospheric-science software environment, first
[activate the Atmos Stack](Atmos-Stack/index.md).
