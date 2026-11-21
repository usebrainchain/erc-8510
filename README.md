# Inference Receipts (draft ERC)

Signed receipts for paid model calls, listed per UTC day under a Merkle root that the endpoint publishes on chain once
the day closes. A payer holding a receipt can show the endpoint counted the call that day, and a signed receipt the
published root does not cover is evidence the endpoint left a call out.

**Status: draft, submitted as [ethereum/ERCs#2194](https://github.com/ethereum/ERCs/pull/2194).** The text is in
[`ERCS/erc-draft_inference_receipts.md`](ERCS/erc-draft_inference_receipts.md); this repository takes the ERC's number
once the editors assign one. Discussion:
[Ethereum Magicians](https://ethereum-magicians.org/t/draft-erc-inference-receipts/30464).

## Why

Agents buy model calls from endpoints they do not run and pay per call, often over x402. The payment settles on chain;
what it bought does not. Each endpoint reports usage in its own format, if at all, and nothing ties a charge to the
request it answered. A signed receipt per call ties them together, a day list under a Merkle root lets a payer check the
endpoint's account of a day without publishing anyone's calls, and one record per day on chain fixes that account at
the cost of one transaction a day.

## What is here

| Path | What |
| --- | --- |
| `ERCS/erc-draft_inference_receipts.md` | The ERC text, in the ethereum/ERCs template |
| `assets/eip-draft_inference_receipts/receipts.mjs` | Canonical form, receipt hash, signature check, day lists, day roots, inclusion proofs, day records |
| `assets/eip-draft_inference_receipts/cli.mjs` | Runs them on files |
| `assets/eip-draft_inference_receipts/vectors.json` | Test vectors from a test key, and one real receipt whose hash matches the root published for its day |
| `assets/eip-draft_inference_receipts/test.mjs` | Offline tests over the vectors |

Node.js 18 or later, no dependencies.

```sh
cd assets/eip-draft_inference_receipts
node --test test.mjs
```

## Changes

This repository follows the text in the pull request. Comments on the standard belong in the Magicians thread; issues
and pull requests here are welcome for the reference code.

## License

Copyright and related rights waived via [CC0](LICENSE.md).
