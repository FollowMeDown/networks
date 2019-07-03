# OpenChat networks
This repo collects the genesis and configuration files for the various OpenChat testnets/mainnet.

## Join the testnet
### Setup an OpenChat full node
First, initialize the node and create the necessary config files:
```bash
chatd init <your_custom_moniker> --home=<chatd_home> 
```
Note that `--home` flag is optional. If not specified, `$HOME/.chatd` will be used by default.

Monikers can contain only ASCII characters. Using Unicode characters will render your node unreachable.
You can edit this moniker later, in the `<chatd_home>/config/config.toml` file:

```toml
# A custom human readable name for this node
moniker = "<your_custom_moniker>"
```
Now your full node has been initialized! 

### Download the Genesis File
You should fetch the correct testnet's `genesis.json` file into `chatd`'s config directory before connecting to public testnet.

```
curl https://raw.githubusercontent.com/openchatproject/networks/master/chat-test-0003/genesis.json > <chatd_home>/config/genesis.json
```

We use the `chat-test-0003` directory in the [networks repo](https://github.com/openchatproject/networks) which contains details for the current testnet. If you prepare connecting to a different one, ensure you get the right files.

You can verify the correctness of genesis file.
```bash
chatd validate-genesis --home=<chatd_home>
```

### Add Seed Nodes

Your node needs to know how to find peers. You'll need to add healthy seed nodes to `<chatd_home>/config/config.toml`. The [networks repo](https://github.com/openchatproject/networks) contains template config file including the seed nodes for each testnet. You can download the config file or manually update the local one.
To check the seeds in [networks repo](https://github.com/openchatproject/networks) of `chat-test-0003`.

```bash
curl https://raw.githubusercontent.com/openchatproject/networks/master/chat-test-0003/config.toml | grep 'seeds = '
```

You can update the `seeds` value to the local config file.

### Run a Full Node 
Now, you are ready to join the testnet with you own full node.
Start the full node with:

```bash
chatd start --home=<chatd_home>
```
Check that everything is running smoothly via chatcli:
```bash
chatcli status
```
You can view the status of the testnet with the [explorer](http://testnet.openchat.co). 

