# Security Audits

Smart contract security reviews by **Muhammad Usman Atique**, covering EVM,
Solana and Sui/Move protocols: staking, lending, launchpads, bonding curves,
DEXs and vaults.

| | |
|---|---|
| **Findings in public reports** | 196: 21 Critical, 17 High, 38 Medium, 66 Low, 52 Info, 2 Undetermined |
| **Ecosystems** | Solana (Rust/Anchor), EVM (Solidity), Sui (Move) |
| **Firms** | BlockApex, BlockGenesys, FailSafe Security |

## Public reports

| Protocol | Firm | Date | Chain | Role | C | H | M | L | I | Report |
|---|---|---|---|---|---|---|---|---|---|---|
| Pixpel NFT Gaming Launchpad | BlockApex | 2026-02 | EVM | Team | 4 | 5 | 12 | 24 | 9 | [PDF](https://drive.google.com/file/d/1Pe5zejT3_Qg-J_hDSghyGH-GQTd0V5Vm/view) |
| Nodo AI Vault & Integration | FailSafe | H2 2025 | Sui | Lead | 3 | 1 | 4 | 2 | - | [PDF](https://drive.google.com/file/d/1gk4eIAn7LyD1_Zgbly061Ght8q0J1upW/view) |
| Meta Pool Stable Verde | BlockApex | 2025-09 | EVM | Team | - | 3 | 2 | 5 | 2 | [PDF](https://github.com/BlockApex/Audit-Reports/blob/master/Meta%20Pool%20Stable%20Verde%20EVM.pdf) |
| Open Game Protocol | BlockApex | 2025-09 | Solana | Team | 5 | 3 | 7 | 12 | 21 | [PDF](https://github.com/BlockApex/Audit-Reports/blob/master/Open%20Game%20Protocol%20Comprehensive%20Report.pdf) |
| Open Game Staking | BlockApex | 2025-07 | EVM | Solo | 1 | - | - | 4 | 1 | [PDF](https://github.com/BlockApex/Audit-Reports/blob/master/Open%20Game%20Staking%20-%20Final%20Audit%20Report.pdf) |
| RandomDEX Token | BlockApex | 2025-03 | EVM | Solo | - | - | 1 | 2 | 1 | [PDF](https://github.com/BlockApex/Audit-Reports/blob/master/Random%20Dex%20Token%20-%20Final%20Audit%20Report.pdf) |
| Pumpkin.fun | BlockApex | 2025-03 | Solana | Team | - | - | - | 1 | 2 | [PDF](https://github.com/BlockApex/Audit-Reports/blob/master/Pumpkin.fun%20Final%20Audit%20Report%20%7C%20BlockApex.pdf) |
| TARS AI Agent Protocol | BlockGenesys | 2025-02 | Solana | Lead | 2 | 1 | 3 | 4 | 4 | [PDF](https://drive.google.com/file/d/1Ro46vtGMTgpXDZdy6lHXozYbQPEwl9Q4/view) |
| TARS V2 Staking | BlockGenesys | 2025-02 | Solana | Lead | 2 | 1 | 1 | 4 | 1 | [PDF](https://drive.google.com/file/d/1so2o_7HBmhw0oKcPTY-CqpXPNG0NUsbO/view) |
| Dark Machine | BlockApex | 2025-01 | EVM | Team | - | 1 | 1 | 3 | 5 | [PDF](https://github.com/BlockApex/Audit-Reports/blob/master/Dark%20Machine%20Final%20Audit%20Report.pdf) |
| DOJO Staking | BlockGenesys | 2024-11 | Solana | Lead | 1 | 1 | 3 | 4 | 2 | [PDF](https://drive.google.com/file/d/1xZlwPWzmIg3hV-16WYkBE_reGgKZ1-oK/view) |
| Stakera Lottery | BlockApex | 2024-09 | Solana | Team | 2 | - | 2 | 1 | 1 | [PDF](https://github.com/BlockApex/Audit-Reports/blob/master/Stakera%20Solana%20Final%20Audit%20Report.pdf) |
| Elektrik Staking | BlockApex | 2024-07 | EVM (LightLink) | Team | 1 | 1 | 2 | - | 3 | [PDF](https://github.com/BlockApex/Audit-Reports/blob/master/Elektrik%20Staking%20Final%20Audit%20Report.pdf) |

## Selected findings

| Severity | Protocol | Finding |
|---|---|---|
| Critical | Nodo AI Vault | Cross-type token substitution: a `CoinType` generic bypass allowed redeeming assets the caller never deposited |
| Critical | Open Game Protocol | Any signer could configure or reinitialize a bonding curve it did not create |
| Critical | Open Game Protocol | Token donation to the curve vault broke a strict balance equality check and halted all swaps |
| Critical | Open Game Staking | Inherited ERC-4626 `withdraw` and `redeem` stayed public, bypassing the one-week withdrawal timelock |
| Critical | Elektrik Staking | Reward claims validated only the last epoch in the list, so current-epoch rewards could be claimed early |
| Critical | Stakera Lottery | Reusing one randomness account for both lotteries overwrote the committed slot and blocked the large-lottery payout |
| High | Meta Pool Stable Verde | No liquidation incentive above 100% LTV, leaving underwater positions as unrecoverable bad debt |

## Private engagements

Reports not published.

| Protocol | Firm | Date | Chain | Scope |
|---|---|---|---|---|
| Memeswap | BlockApex | 2025-02 | EVM | AMM contracts |
| Token Metrics AI | BlockApex | 2025-01 | EVM | Launchpad contracts |
| Pluto | BlockApex | 2024-12 | Solana | Lending protocol |
| Alethea AI Launchpad | BlockApex | 2024-11 | Solana | Launchpad programs |

## Competitive audits

| Contest | Platform | Result | Link |
|---|---|---|---|
| Axion Protocol | Sherlock | Rewarded; valid Medium findings (`UsmanAtique`) | [Results](https://audits.sherlock.xyz/contests/552?filter=results) |
| Superposition | Code4rena | Rewarded; valid High and Medium findings (`usmanatique`) | [Report](https://www.code4rena.com/reports/2024-08-superposition) |

## Exploit research

Post-mortems of live incidents, each reproduced on a mainnet fork in
[`defi-exploit-reproductions`](https://github.com/Usman-CrYpToo2/defi-exploit-reproductions).

| Incident | Loss | Root cause | Analysis |
|---|---|---|---|
| Seneca Protocol | ~$6.4M | Arbitrary external call drains user approvals | [BlockApex](https://blockapex.io/seneca-protocol-hack-analysis/) |
| Shezmu | ~$4.9M | Borrowing against collateral anyone can mint | [BlockApex](https://blockapex.io/shezmu-hack-analysis/) |
| Super Sushi Samurai | ~$4.6M | Self-transfer doubles the balance | [BlockApex](https://blockapex.io/super-sushi-samurai-hack-analysis/) |

## Contact

[LinkedIn](https://www.linkedin.com/in/usman-atiquee/) · [usman.atiq159753@gmail.com](mailto:usman.atiq159753@gmail.com)
