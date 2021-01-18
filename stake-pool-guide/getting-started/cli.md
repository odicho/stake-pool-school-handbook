# Command Line Interface

This command line interface provides a collection of tools for key generation, transaction construction, certificate creation and other important tasks.

It is organized in a hierarchy of subcommands, and each level comes with its own built-in documentation of command syntax and options.

We can get the top level help by simply typing the command without arguments:

```text
cardano-cli
```

We will be told that one available subcommand is `node`, and typing

```text
cardano-cli node
```

will display available sub-subcommands, one of which is `key-gen`. Typing

```text
cardano-cli node key-gen
```

will inform us about the parameters this command takes, so we can for example generate a key-pair of offline keys and a file for the issue counter by typing

```text
cardano-cli node key-gen \
--cold-verification-key-file cold.vkey \
--cold-signing-key-file cold.skey \
--operational-certificate-issue-counter-file cold.counter
```

![](../../.gitbook/assets/cli.png)



{% hint style="info" %}
QUESTIONS AND FEEDBACK

  
If you have any questions and suggestions while taking the lessons please feel free to ask in the [forum](https://forum.cardano.org/c/english/operators-talk/119) and we will respond as soon as possible.
{% endhint %}

