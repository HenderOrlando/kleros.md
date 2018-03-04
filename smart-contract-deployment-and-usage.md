# Smart Contract Deployment and Usage

The Kleros implementation requires three smart contracts to be deployed on the same network and configured to interact with each other; A Kleros arbitrator contract \(KlerosPOC at the moment\), a random number generator contract \(RNG at the moment\), and a Pinakion Token contract \(PinakionPOC at the moment\).

---

### Step 1: Deploy a RNG Contract

If you have an existing RNG contract deployed, you can skip this step and use that same contract. Otherwise, Deploy an instance of a [standardized RNG](https://github.com/kleros/kleros-interaction/blob/master/contracts/standard/rng/RNG.sol).

E.g. [BlockhashRNGFallback](https://github.com/kleros/kleros-interaction/blob/master/contracts/standard/rng/BlockhashRNGFallback.sol).

### Step 2: Deploy a PNK Contract

Deploy an instance of [PinakionPOC](https://github.com/kleros/kleros/blob/master/contracts/PinakionPOC.sol). You can't reuse this one with multiple arbitrator contracts like with the RNG contract.

### Step 3: Deploy an Arbitrator Contract

Deploy an instance of [KlerosPOC](https://github.com/kleros/kleros/blob/master/contracts/KlerosPOC.sol) with the RNG you created as well as an `int[5]` specifying the time for each Kleros period in seconds.

```js
KlerosPOC.new(PNKAddress, RNGAddress, [300,300,300,300,300])
```

This would create a new KlerosPOC contract instance where each period lasts 5 minutes.

### Step 4: Configure the Contracts

We must configure the PinakionPOC contract instance for use by the KlerosPOC contract instance.

* Set the KlerosPOC contract instance address on the PinakionPOC contract instance.

```js
PinakionPOCInstance.setKleros(KlerosPOCAddress)
```

* Set the owner of the PinakionPOC contract instance to the KlerosPOC contract instance address.

```js
PinakionPOCInstance.transferOwnership(KlerosPOCAddress)
```



