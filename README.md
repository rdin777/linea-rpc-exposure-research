# linea-rpc-exposure-research

*If this research helped you, please consider giving it a ⭐ Star.*


## 🚀 Stay Updated
Found this research useful?
* **Star ⭐** this repo to keep track of it.
* **Follow me** on GitHub for more DeFi security research.
* **Fork** it if you want to run your own experiments.

### ☕ Support the Research
If you appreciate the work and want to support further security research:

<img src="456.PNG" alt="Donate QR" width="200"/>

**Wallet Address (ETH/EVM):** 0xBDDD7973D0DE27B715A4A5cbdb87d0DF78757b3A 


Research and PoC for unauthenticated JSON-RPC endpoint exposure on Linea Mainnet infrastructure.
# Infrastructure Security: Unauthenticated JSON-RPC on Linea Mainnet

## 🛡️ Executive Summary
This research documents a security misconfiguration identified within the **Linea (Consensys)** infrastructure. An unauthenticated JSON-RPC endpoint was found exposed, potentially leading to Information Disclosure and Denial of Service (DoS) via resource exhaustion.

## 🔍 Vulnerability Details
- **Target:** Linea Mainnet Nodes / RPC Infrastructure
- **Vulnerability Type:** Improper Access Control / Missing Authentication
- **Impact:** Unauthorized access to node administrative methods, potential exposure of internal network topology, and susceptibility to RPC-based DoS attacks.
- **Report ID:** HackerOne #3514518

## 🛠️ Technical Analysis
The endpoint allowed execution of sensitive JSON-RPC methods without proper Bearer token validation or IP whitelisting. This is a critical oversight in production blockchain environments where RPC nodes should be hardened against public scanning.

### Example Request (PoC)
```bash
curl -X POST -H "Content-Type: application/json" \
--data '{"jsonrpc":"2.0","method":"net_peerCount","params":[],"id":1}' \
https://{REDACTED_ENDPOINT}
