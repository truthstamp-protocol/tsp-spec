# Stamp Types

## Public
Content + hash stored on MegaETH. Content uploaded to Arweave permanently.
Anyone can verify. storageUri is set at creation.

## Sealed
Hash locked on-chain at creation. Content hidden until reveal date.
After reveal date, platform calls revealSealed() which attaches the 
Arweave URI on-chain. Content was never exposed before reveal.

Sealed file stamps: encrypted at rest in Supabase Storage,
decrypted and uploaded to Arweave only after on-chain reveal.

## Hash-Only
Only the hash is stored. Content stays entirely private.
Proves you had the content at that time without revealing what it is.
