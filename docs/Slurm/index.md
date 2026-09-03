# Slurm Partitions

BlueHive provides group-owned and university-shared partitions for different
types of workloads.

## Partition overview

| Partition | Type | Resources and limits | Recommended use |
| --- | --- | --- | --- |
| `atmos` | Group-owned | Each node has 64 cores and 512 GB of memory each | Computationally intensive model runs and high-performance MPI workloads |
| `atmos2` | Group-owned | Older slower group nodes with 36 cores and 128 GB of memory each. | Model development and non-time-critical runs |
| `interactive` | University-shared | Two nodes; one job per user; up to 24 cores and 128 GB per session; 12-hour limit | Interactive development work |
| `standard` | University-shared | Nodes in this partition are similar to atmos but shared by everyone | Generally not used by this group |
| `gpu` | University-shared | GPU resources | GPU workloads; contact Peter before use |
| `h100` | University-shared | GPU resources | GPU workloads; contact Peter before use |

## Interactive partition

The university's shared `interactive` partition provides users with interactive
sessions. It consists of two nodes and accepts only one interactive job per
user, making it suitable for development work.

For a general-purpose interactive session, request eight cores and 32 GB of
memory:

```bash
srun --partition=interactive --cpus-per-task=8 --mem=32G --time=12:00:00 --pty bash
```

The partition can provide up to 24 cores and 128 GB of memory per session:

```bash
srun --partition=interactive --cpus-per-task=24 --mem=128G --time=12:00:00 --pty bash
```

Interactive sessions are limited to 12 hours.

The `atmos` and `atmos2` partitions can also provide interactive jobs. Set
`--partition=atmos` or `--partition=atmos2` in the command above. Use these
partitions interactively only when the university's `interactive` partition is
full: `interactive` is much faster than `atmos2`, and `atmos` should remain
available for model runs whenever possible.
