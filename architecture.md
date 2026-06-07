# Architecture

TruthStamp is a Web2.5 hybrid — centralized UX, decentralized permanence.

## Stack

| Layer       | Technology         | Purpose                              |
|-------------|--------------------|--------------------------------------|
| Blockchain  | MegaETH (EVM)      | On-chain proof registry              |
| Storage     | Arweave            | Permanent content storage            |
| Archive     | Bitcoin OP_RETURN  | Optional highest-permanence anchor   |
| Backend     | Supabase           | Auth, DB, Edge Functions             |
| Frontend    | Vanilla HTML/JS    | GitHub Pages static site             |

## Flow

1. User submits content via frontend
2. Supabase Edge Function hashes content (SHA-256)
3. Platform wallet calls createStamp() on MegaETH
4. Content uploaded to Arweave (public stamps)
5. Proof ID returned and stored in DB
6. User receives shareable proof URL

## Trust Model

The platform wallet is an authorized stamper — it calls createStamp() 
on behalf of users. For wallet users, creatorIdentity is their own 
Ethereum address. For email users, it is a UUID assigned by the 
auth system. This is an intentional Web2.5 design — the chain 
records who stamped, the platform vouches for identity.
