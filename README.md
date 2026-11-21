# ERC-8510: Inference Receipts (draft)

Signed receipts for paid model calls, listed per UTC day under a Merkle root that the endpoint publishes on chain once
the day closes. A payer holding a receipt can show the endpoint counted the call that day, and a signed receipt the
published root does not cover is evidence the endpoint left a call out.

**Status: draft, submitted as [ethereum/ERCs#2194](https://github.com/ethereum/ERCs/pull/2194).** The text is in
[`ERCS/erc-8510.md`](ERCS/erc-8510.md). The editors assigned it ERC-8510 on 2026-11-21. Discussion:
[Ethereum Magicians](https://ethereum-magicians.org/t/erc-8510-inference-receipts/30464).

## Why

Agents buy model calls from endpoints they do not run and pay per call, often over x402. The payment settles on chain;
what it bought does not. Each endpoint reports usage in its own format, if at all, and nothing ties a charge to the
request it answered. A signed receipt per call ties them together, a day list under a Merkle root lets a payer check the
endpoint's account of a day without publishing anyone's calls, and one record per day on chain fixes that account at
the cost of one transaction a day.

## What is here

| Path | What |
| --- | --- |
| `ERCS/erc-8510.md` | The ERC text, in the ethereum/ERCs template |
| `assets/erc-8510/receipts.mjs` | Canonical form, receipt hash, signature check, day lists, day roots, inclusion proofs, day records |
| `assets/erc-8510/cli.mjs` | Runs them on files |
| `assets/erc-8510/vectors.json` | Test vectors from a test key, and one real receipt whose hash matches the root published for its day |
| `assets/erc-8510/test.mjs` | Offline tests over the vectors |

Node.js 18 or later, no dependencies.

```sh
cd assets/erc-8510
node --test test.mjs
```

## Changes

This repository follows the text in the pull request. Comments on the standard belong in the Magicians thread; issues
and pull requests here are welcome for the reference code.

## License

Copyright and related rights waived via [CC0](LICENSE.md).
