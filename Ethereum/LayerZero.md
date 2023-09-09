#bridge #l0
[[Ethereum]]

LayerZero is a messaging protocol allowing arbitrary contract invocation across chains with an included payload.

Well, there are four real components here: **Relayer**, **Oracle**, **Validation/Proof Library**, **Block Confirmations**

The application can have complete control over each of these components. I’ll walk through what those controls look like below:

**Relayer** — Relayers are completely open and permissionless. The application may select any existing Relayer, including the ability to operate their own and select themselves. Relayers can be a network of relayers or as simple as a single signer.
**Oracles** — Oracles are completely open and permissionless. The application may select any existing Oracle, including the ability to operate its own and select itself. Oracles can be a network of oracles or as simple as a single signer.
**Validation/Proof library** — Libraries are published in an append-only registry, new libraries can be published but existing libraries can never be modified and are completely and irrevocably immutable. The application may select any existing library (which all have public audits) to perform its validation.
**Block Confirmations** — Block confirmations are the number of blocks that must be completed on the current source chain before a message can be passed to the destination chain.

If an application configures these parameters it will look like this:
![[Pasted image 20230313115119.png]]
If an application does not setup its configuration then it uses the ‘Default’ settings which basically is just a pointer to some pointer:
![](https://miro.medium.com/v2/resize:fit:700/0*XtdFAkI21WBWvez7)


So, let’s discuss what the current state of the world is and what can and can’t be done.

Most generic messaging systems today work something like this:
![](https://miro.medium.com/v2/resize:fit:700/0*1SQtnJ2ca3kpbM6A)

Messaging systems such as Wormhole, Nomad, etc. all work in a similar manner. All of the control sits in the system and can be upgraded by whoever controls the admin keys for those systems (In Wormhole’s case this is the 13/19 multisig of validators). This has previously been extremely problematic resulting in multiple issues for [Wormhole](https://github.com/immunefi-team/wormhole-uninitialized) and [Nomad](https://halborn.com/explained-the-nomad-hack-august-2022/) and is generally seen as unsafe practice for applications. Using LayerZero’s defaults is exactly equivalent to these systems.

The difference is with each of those systems an application does not have any control and cannot ever prevent the system from forcing these upgrades on them and changing the underlying messaging behavior or the trust assumptions for the protocols.

LayerZero gives each application a way to explicitly choose a concrete set of security parameters that can **never** be modified or changed on them. We believe critical infrastructure should be immutable, open source, and **_always owned_** by user applications.