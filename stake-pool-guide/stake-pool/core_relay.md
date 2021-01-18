# Configure topology files for block-producing and relay nodes.

Before we register our stake pool, let's configure our **block-producing** and **relay** nodes:

**NOTE:** Here you can find peers to connect to, and submit your own relay's data:[  
](https://explorer.cardano-testnet.iohkdev.io/relays/topology.json)[https://explorer.cardano-testnet.iohkdev.io/relays/topology.json](https://explorer.cardano-testnet.iohkdev.io/relays/topology.json)

## Configure the block-producing node

Get the configuration files for your core node if you don't have them already, for example

```text
mkdir pool
cd pool

wget https://hydra.iohk.io/job/Cardano/cardano-node/cardano-deployment/latest-finished/download/1/testnet-config.json
wget https://hydra.iohk.io/job/Cardano/cardano-node/cardano-deployment/latest-finished/download/1/testnet-shelley-genesis.json
wget https://hydra.iohk.io/job/Cardano/cardano-node/cardano-deployment/latest-finished/download/1/testnet-topology.json

```

Make the core node "talk" only to **YOUR** relay node.

```text
nano testnet-topology.json

  {
    "Producers": [
      {
        "addr": "<YOUR RELAY NODE IP ADDRESS>",
        "port": <PORT>,
        "valency": 1
      }
    ]
  }
```

## Configure the relay node:

Make your **relay node** `talk` to your **block-producing** node and **other relays** in the network by editing the `testnet-topology.json` file:

```text
nano testnet-topology.json

{
  "Producers": [
    {
      "addr": "<YOUR BLOCK-PRODUCING NODE IP ADDRESS>",
      "port": <PORT>,
      "valency": 1
    },
    {
      "addr": "<OTHER RELAY NODE IP ADDRESS>",
      "port": <PORT>,
      "valency": 1
    },
    {
      "addr": "<OTHER RELAY NODE IP ADDRESS>",
      "port": <PORT>,
      "valency": 1
    }
  ]
}
```

{% hint style="info" %}
QUESTIONS AND FEEDBACK

If you have any questions and suggestions while taking the lessons please feel free to ask in the [forum](https://forum.cardano.org/c/english/operators-talk/119) and we will respond as soon as possible.
{% endhint %}

