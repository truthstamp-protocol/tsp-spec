# Smart Contract Reference

**TruthStamp v3**  
Address: `0xD8beDEa4DdaCBF681CCca5DBFa90b04bB654d0B7`  
Network: MegaETH Mainnet (Chain ID: 4326)  
RPC: `https://mainnet.megaeth.com/rpc`

## Key Functions

### createStamp(StampParams p)
Creates a permanent on-chain stamp. Only callable by authorized stampers.

| Field           | Type    | Description                              |
|-----------------|---------|------------------------------------------|
| contentHash     | bytes32 | SHA-256 hash of content                  |
| hashAlgo        | string  | e.g. "SHA-256"                           |
| contentType     | uint8   | 0=Text, 1=File, 2=URL                    |
| visibility      | uint8   | 0=Public, 1=Sealed, 2=HashOnly           |
| sealedUntil     | uint64  | Unix timestamp for reveal (0 if not sealed)|
| storageUri      | string  | Arweave URI e.g. ar://txId               |
| creatorIdentity | string  | User UUID or wallet address              |
| shortText       | string  | Raw text ≤280 chars (public text only)   |

### revealSealed(uint256 proofId, string storageUri)
Attaches Arweave URI to a sealed stamp after its reveal date.
Only callable by the original creator wallet.

### verifyByHash(bytes32 contentHash)
Returns (proofId, timestamp, creatorIdentity) for any content hash.
Works on any RPC — no TruthStamp required.

### getStamp(uint256 proofId)
Returns full stamp struct by proof ID.

## Events

**StampCreated** — emitted on every stamp. Contains all stamp fields.  
**StampRevealed** — emitted when a sealed stamp is revealed.
