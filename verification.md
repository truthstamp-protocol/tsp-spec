# Verify a Stamp Without TruthStamp

TruthStamp proofs are independently verifiable using any Ethereum RPC.

## By Content Hash (ethers.js)

```javascript
import { ethers } from 'ethers';

const RPC  = 'https://mainnet.megaeth.com/rpc';
const CA   = '0xD8beDEa4DdaCBF681CCca5DBFa90b04bB654d0B7';
const ABI  = ['function verifyByHash(bytes32) view returns (uint256, uint256, string)'];

const provider = new ethers.JsonRpcProvider(RPC);
const contract = new ethers.Contract(CA, ABI, provider);

// Hash your content
const content = 'Your content here';
const hash    = ethers.sha256(ethers.toUtf8Bytes(content));

const [proofId, timestamp, identity] = await contract.verifyByHash(hash);
if (proofId > 0) {
  console.log('First stamped:', new Date(Number(timestamp) * 1000));
  console.log('By:', identity);
}
```

## By Proof ID

```javascript
const ABI2   = ['function getStamp(uint256) view returns (tuple(bytes32,address,uint64,uint8,uint8,uint8,bool,uint64,string,string,string))'];
const stamp  = await contract.getStamp(proofId);
// stamp[2] = createdAt timestamp
// stamp[9] = storageUri (Arweave)
```

## Verify via Events

Filter `StampCreated` events on any block explorer or RPC:
```
Event: StampCreated(contentHash=0xYOUR_HASH)
Contract: 0xD8beDEa4DdaCBF681CCca5DBFa90b04bB654d0B7
```
