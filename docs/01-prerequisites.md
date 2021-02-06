# Prerequisites

## Microsoft Azure

This tutorial leverages the [Azure](https://azure.microsoft.com) Cloud to streamline provisioning of the compute infrastructure required to bootstrap a Kubernetes cluster from the ground up.

### Sign up for Azure

To begin, [Sign up](https://azure.microsoft.com/free/) for for a free account and $200 in credits.

> In Azure Free Trial there is a limit of 4 Cores available, therefore tutorial instructions must be changed to create 4 nodes instead of 6 (2 controllers and 2 workers).

> The [Estimated cost](https://azure.microsoft.com/pricing/calculator/) to run this tutorial: $0.4 per hour ($10 per day).

> The compute resources required for this tutorial will not exceed the Microsoft Azure free tier.

## Microsoft Azure Cloud Platform SDK

We will use the [Azure Command Line Interface](https://docs.microsoft.com/en-us/cli/azure/get-started-with-azure-cli) throughout this tutorial and the examples will be written in `bash` shell.

### Install the Azure CLI 2.0

Follow the Azure CLI 2.0 [documentation](https://github.com/azure/azure-cli#installation) to install and configure the `az` command line utility.

Verify the Azure CLI 2.0 version is 2.1.0 or higher:

```shell
az --version
```

This tutorial was verified to work on Ubuntu via [WSL2](https://docs.microsoft.com/en-us/windows/wsl/install-win10), and Visual Studio Code on Windows using the following versions:

- `az cli: 2.14.0`
- `bash: 4.4.20`
- `Ubuntu: 18.04 (bionic)`

If you are starting from scratch, here is a good article on how to install and configure all these components: [Running Ubuntu on Windows 10 with WSL2](https://maurogiusti.medium.com/running-ubuntu-on-windows-10-with-wsl2-c4f06b3c353)

### Login to Azure

From your bash prompt run:

```shell
az login
```

and follow the instructions to log in.

### Select a Subscription to work with

If you have more than one Azure Subscription (a free account can only have one), select the one you want to use. To see the list of your Azure Subscriptions run:

```shell
az account list -o table
```

To select the Subscription to use run:

```shell
az account set --subscription "<Your subscription Name or Id>"
```

### Create a default Resource Group in a location

To create a resource group named 'kubernetes' to host the resources needed for the tutorial in the `eastus2` location, run:

```shell
az group create -n kubernetes -l eastus2
```

> You can use the `az account list-locations` command to view additional locations.

## Running Commands in Parallel with tmux

[tmux](https://github.com/tmux/tmux/wiki) can be used to run commands on multiple compute instances at the same time. Labs in this tutorial may require running the same commands across multiple compute instances, in those cases consider using tmux and splitting a window into multiple panes with `synchronize-panes` enabled to speed up the provisioning process.

> The use of tmux is optional and not required to complete this tutorial.

![tmux screenshot](images/tmux-screenshot.png)

> Enable `synchronize-panes`: `ctrl+b` then `shift :`. Then type `set synchronize-panes on` at the prompt. To disable synchronization: `set synchronize-panes off`.

Next: [Installing the Client Tools](02-client-tools.md)
