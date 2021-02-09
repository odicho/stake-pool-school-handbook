# Generate your stake pool keys

{% hint style="danger" %}
### WARNING: 

### Basic core node firewall configuration:

* Make sure you can only login with SSH Keys, not password.
* Make sure you cannot login as root
* Make sure to setup SSH connections in a port different than the default 22
* Make sure to configure the firewall to only allow connections from your relay nodes by setting up their ip addresses.

### Basic relay node firewall configuration:

* Make sure you can only login with SSH Keys, not password.
* Make sure you cannot login as root
* Make sure to setup SSH connections in a port different than the default 22.
* Make sure you only have the strictly necessary ports opened.

[See Firewall ](../../additional-material/firewall.md)Additional Material 
{% endhint %}

## Creating stake pool keys

{% hint style="danger" %}
**WARNING:** For Mainnet, you may want to use your **local machine** for this process. Make sure you are not online until you have put your **cold keys** in a secure storage and deleted the files from your local machine.
{% endhint %}

The **core node** needs:

* **Cold** Key pair,
* **VRF** Key pair,
* **KES** Key pair,
* **Operational Certificate**

Create a directory to store your keys:

```text
mkdir pool-keys
cd pool-keys
```

### Generate **Cold** Keys and a **Cold\_counter**:

```text
cardano-cli node key-gen \
--cold-verification-key-file cold.vkey \
--cold-signing-key-file cold.skey \
--operational-certificate-issue-counter-file cold.counter
```

### Generate VRF Key pair

```text
cardano-cli node key-gen-VRF \
--verification-key-file vrf.vkey \
--signing-key-file vrf.skey
```

### Generate the KES Key pair

```text
cardano-cli node key-gen-KES \
--verification-key-file kes.vkey \
--signing-key-file kes.skey
```

### Generate the Operational Certificate

We need to know the slots per KES period, we get it from the genesis file:

```text
cat testnet-shelley-genesis.json | grep KESPeriod
> "slotsPerKESPeriod": 3600,
```

So one period lasts 3600 slots.

Then we need the current tip of the blockchain:

We can use your relay node to query the tip:

```text
cardano-cli query tip --testnet-magic 1097911063

{
    "blockNo": 27470,
    "headerHash": "bd954e753c1131a6cb7ab3a737ca7f78e2477bea93db54511cedefe8899ebed0",
    "slotNo": 656260
}
```

Look for Tip `unSlotNo` value. In this example we are on slot 656260. So we have KES period is 182:

```text
expr 656260 / 3600
> 182
```

{% hint style="warning" %}
**NOTE:** `slotNo` and `Kes-period` will be different when you run this commands. So make sure to calculate them yourself.
{% endhint %}

To generate the certificate:

```text
cardano-cli node issue-op-cert \
--kes-verification-key-file kes.vkey \
--cold-signing-key-file cold.skey \
--operational-certificate-issue-counter cold.counter \
--kes-period 182 \
--out-file node.cert
```

## Move the cold keys to secure storage

The best place for your cold keys is a **SECURE USB** or other **SECURE EXTERNAL DEVICE**, not a computer with internet access.

### Copy the cold keys from your server to your local machine and from there to COLD storage.

For example:

```text
scp -i " file.pem" remote_username@10.10.0.2:~/poolkeys/cold* /local/directory

> Transferred: sent 3220, received 6012 bytes, in 1.2 seconds
Bytes per second: sent 2606.6, received 4866.8
debug1: Exit status 0
```

Later on we will learn how to register our pool in the blockchain.

{% hint style="info" %}
QUESTIONS AND FEEDBACK

If you have any questions and suggestions while taking the lessons please feel free to ask in the [forum](https://forum.cardano.org/c/english/operators-talk/119) and we will respond as soon as possible.
{% endhint %}

