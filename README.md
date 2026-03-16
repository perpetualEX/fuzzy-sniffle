# GenLayer Validator Best Practices Guide

## Introduction
This guide covers best practices for setting up, running, and maintaining a 
validator node on the GenLayer Asimov & Bradbury Testnets. Following these 
practices will improve your uptime, security, and overall validator performance.

---

## 1. Prerequisites
Before setting up your node, ensure you have:
- Docker 26+
- Node.js 18+
- npm installed
- At least 4GB RAM and 50GB SSD storage

---

## 2. Installation
Install the GenLayer CLI globally:
```bash
npm install -g genlayer
```
Initialize your environment with 5 validators:
```bash
genlayer init --numValidators 5
```
Use `--reset-db` for a clean slate during testing.

---

## 3. Linux Prerequisites (Often Missed!)
The CLI uses `keytar` for secure key storage, which requires `libsecret`:
```bash
# Ubuntu/Debian
sudo apt-get install libsecret-1-0

# Fedora
sudo dnf install libsecret
```

---

## 4. Pin Your Localnet Version
Always pin your version on testnets to avoid breaking changes:
```bash
genlayer init --localnet-version v0.10.2
```

---

## 5. Connect to the Right Testnet
Using the GenLayer JS SDK, point to the correct chain:
```javascript
import { testnetAsimov } from 'genlayer-js/chains';
const client = createClient({ chain: testnetAsimov, account });
```

---

## 6. Check Validator Status
```javascript
const isValidator = await client.isValidator("0xYourAddress");
const validators = await client.getActiveValidators();
```

---

## 7. Security Best Practices
- Disable password login; use SSH keys only
- Configure UFW firewall with strict port rules
- Store validator key backups encrypted and offsite
- Apply security patches promptly

---

## 8. Monitoring
- Set up Grafana + Prometheus dashboards
- Connect alerts to PagerDuty or Telegram
- Don't rely on manual checks — automate everything

---

## 9. Governance Participation
- Monitor GenLayer Discord and governance forums regularly
- Vote on every proposal — abstaining signals inactivity
- Engage in pre-vote discussions to represent your validator's position

---

## Conclusion
Following these best practices will ensure your GenLayer validator node is 
secure, reliable, and positively contributing to the network.
