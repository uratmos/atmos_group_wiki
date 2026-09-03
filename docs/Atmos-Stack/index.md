# Atmospheric Software Stack

The atmospheric software stack (Atmos Stack) clears CIRC-related variables from
your environment and loads a fresh set of Atmos environment variables. This
provides an atmospheric-science-specific software stack.

## Why not use the CIRC environment?

The default CIRC environment supports all BlueHive users, resulting in many
different versions of installed software. Changes to that environment must be
made carefully because they affect everyone.

By managing its own environment, the group can provide a streamlined software
stack that is updated more frequently. Group members can still use the default
CIRC environment when needed.

## Set up the Atmos Stack

Add the following to your `~/.bashrc` file:

```bash
# Add Atmos Stack commands to the shell
source "/sfw/rhel9-x86_64/atmos/bin/atmos-functions.sh"
```

Restart your Bash session:

```bash
exec bash
```

Alternatively, open a new terminal. You can then set up the Atmos Stack by
running:

```bash
activate-atmos-stack
```

The <span style="color: #42a5f5;">[ATMOS]</span> prefix at the start of your command prompt indicates that the
Atmos Stack is active.
