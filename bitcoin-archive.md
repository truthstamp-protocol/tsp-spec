# Bitcoin Archiving

Public stamps can optionally be anchored to Bitcoin via OP_RETURN.

## What is stored
An OP_RETURN transaction containing a TSA-1 manifest:

TS1:<proofId>:<contentHash>:<arweaveTxId>
## How to verify
1. Find the Bitcoin transaction on any block explorer
2. Decode the OP_RETURN output
3. Match the contentHash against your content
4. The Bitcoin block timestamp is your independent timestamp proof

## Why Bitcoin
Bitcoin has the strongest timestamp guarantee of any blockchain —
the most decentralized, longest-running, most widely trusted ledger.
