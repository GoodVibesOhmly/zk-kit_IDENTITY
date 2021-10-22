<p align="center">
    <h1 align="center">
        Semaphore protocols
    </h1>
    <p align="center">Client library for generating and verifying Semaphore & Rln ZK proofs.</p>
</p>

<p align="center">
    <a href="https://github.com/appliedzkp/libsemaphore/blob/master/LICENSE">
        <img alt="Github license" src="https://img.shields.io/github/license/appliedzkp/libsemaphore.svg?style=flat-square">
    </a>
    <a href="https://www.npmjs.com/package/@libsem/protocols">
        <img alt="NPM version" src="https://img.shields.io/npm/v/@libsem/protocols?style=flat-square" />
    </a>
    <a href="https://npmjs.org/package/@libsem/protocols">
        <img alt="Downloads" src="https://img.shields.io/npm/dm/@libsem/protocols.svg?style=flat-square" />
    </a>
    <a href="https://bundlephobia.com/package/@libsem/protocols">
        <img alt="npm bundle size (scoped)" src="https://img.shields.io/bundlephobia/minzip/@libsem/protocols" />
    </a>
    <a href="https://eslint.org/">
        <img alt="Linter eslint" src="https://img.shields.io/badge/linter-eslint-8080f2?style=flat-square&logo=eslint" />
    </a>
    <a href="https://prettier.io/">
        <img alt="Code style prettier" src="https://img.shields.io/badge/code%20style-prettier-f8bc45?style=flat-square&logo=prettier" />
    </a>
</p>

---

## 🛠 Install

### npm or yarn

Install the `@libsem/protocols` package with npm:

```bash
npm i @libsem/protocols
```

or yarn:

```bash
yarn add @libsem/protocols
```

## 📜 Usage

**Import**

```typescript
import { ZkIdentity, Identity } from "@libsem/identity"
import {
  Semaphore,
  MerkleProof,
  IProof,
  generateMerkleProof,
  genExternalNullifier,
  genSignalHash
} from "@libsem/protocols"
```

```javascript
const { ZkIdentity } = require("@libsem/identity")
const { Semaphore, Rln, NRln, generateMerkleProof, genExternalNullifier, genSignalHash } = require("@libsem/protocols")
```

**Merkle Proofs**
Generate merkle proof for your identity given the array of registered identity commitments

```typescript
const identityCommitments: Array<bigint> = [...];
const identity: ZkIdentity = new ZkIdentity();
const identityCommitment: bigint = identity.genIdentityCommitment();

const merkleProof: MerkleProof = generateMerkleProof(TREE_DEPTH, ZERO_VALUE, NUMBER_OF_LEAVES_PER_NODE, identityCommitments, identityCommitment);
```

**Semaphore**

In order to create semaphore proof, make sure to

```typescript
const witness = Semaphore.genWitness(identity, merkleProof, externalNullifier, signal)
const fullProof = await Semaphore.genProof(witness, wasmFilePath, finalZkeyPath)
```

## 📜 Final Note

For full examples of how to integrate with contracts check https://github.com/appliedzkp/semaphore repository.

For additional info check tests directory.
