# 🛡️ Aegis-Solana-PQC-Bridge

[![Solana](https://img.shields.io/badge/Solana-Mainnet--Beta-00FFA3)](https://solana.com/)
[![PQC-Standard](https://img.shields.io/badge/PQC-ML--DSA--65-blueviolet)](https://csrc.nist.gov/projects/post-quantum-cryptography)

## 📌 Project Overview
The **Aegis-Solana Bridge** is a quantum-resistant escrow and payment protocol. It implements a secondary cryptographic layer on top of Solana’s native Ed25519, requiring a **Lattice-based Signature (ML-DSA)** for the release of high-value funds.

## ⚙️ Key Features
* **Quantum-Resistant Escrow:** Funds are locked in a PDA (Program Derived Address) that only accepts ML-DSA-verified instructions.
* **Hybrid Verification:** Combines Solana's speed with NIST-standardized quantum security.
* **Sanctum Agent Integration:** Fully compatible with Sanctum Private Agents for automated, secure treasury management.

## 🚀 Implementation (Rust)
The program utilizes the `pqcrypto-falcon` and `pqcrypto-ml-dsa` crates to perform on-chain verification of quantum-resistant signatures before executing `invoke_signed` instructions.

```rust
// Snippet: Verification of PQC Signature before Fund Release
pub fn release_escrow(ctx: Context<ReleaseEscrow>, signature: [u8; 2420]) -> Result<()> {
    let pubkey = &ctx.accounts.quantum_pki.data;
    pqc_verify_mldsa(&signature, &ctx.accounts.message, pubkey)?;
    // Transfer logic follows...
}
```
## 📜 Research & Whitepaper
This project serves as a live implementation of the Quantum-Resistant P2P Payment model, bridging traditional DevOps automation with PQC security standards.
