# Get configuration files

{% hint style="danger" %}
**WARNING**

In this course we use the **CARDANO TESTNET,** so let's get the configuration files for it. 

**DO NOT USE MAINNET DURING THIS COURSE.** _****_
{% endhint %}



Starting the node and connecting it to the testnet requires 4 configuration files:

* topology.json
* BYRON genesis.json
* SHELLEY genesis.json
* config.json

In your home directory, create a new directory for the configuration files:

```text
cd
mkdir relay
cd relay
```

Now download the latest testnet configuration files:

```text
wget https://hydra.iohk.io/job/Cardano/cardano-node/cardano-deployment/latest-finished/download/1/testnet-config.json
wget https://hydra.iohk.io/job/Cardano/cardano-node/cardano-deployment/latest-finished/download/1/testnet-shelley-genesis.json
wget https://hydra.iohk.io/job/Cardano/cardano-node/cardano-deployment/latest-finished/download/1/testnet-byron-genesis.json
wget https://hydra.iohk.io/job/Cardano/cardano-node/cardano-deployment/latest-finished/download/1/testnet-topology.json
```



{% hint style="info" %}
QUESTIONS AND FEEDBACK

  
If you have any questions and suggestions while taking the lessons please feel free to ask in the [forum](https://forum.cardano.org/c/english/operators-talk/119) and we will respond as soon as possible.
{% endhint %}

