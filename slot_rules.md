# ODYSSEY: VOYAGE OF FORTUNE — Official Slot Game Rules & Paytable Spec — v2

**Platform:** Engine (`stake-engine.com` — `lines` Template)  
**Grid Format:** 5 Reels × 3 Rows | 20 Fixed Paylines (Left-to-Right)  
**Theoretical RTP:** 96.20% (Base Game) | 96.25%–96.40% (Feature Modes, see Section 4). Every mode must stay within Engine's required **96.0%–96.7%** band.  
**Volatility:** High (5/5)  
**Maximum Win:** 10,000× Base Play / Bet in every mode  

> **v2 notes:** The Super Bonus is renamed **The Shores of Hades** (was "The Gates of Hades"). The Engine general disclaimer is added (Section 8). A Social Mode wording map is added (Section 9). Per-mode max win is stated (Section 4). See Section 10 for the change log and open items.

---

## 1. Game Overview
**Odyssey: Voyage of Fortune** is a 5-reel, 3-row video slot featuring **20 fixed paylines**, **Expanding Full-Reel Bow Wilds (`1:3`)** with multipliers up to **100×**, and two tiered Free Spins bonus rounds set across the mythical set pieces of Homer’s epic:
* **Act I (Base Game — The Walls of Troy):** Land Expanding Bow Wilds to pierce the reels with instant multipliers.
* **Act II (Free Spins — The Cyclops’s Cave):** Triggered by 3 or 4 Trojan Horse Bonus Scatters. All Expanded Bow Wilds become **Sticky (Locked in Place)** for the rest of the bonus round.
* **Act III (Super Bonus — The Shores of Hades):** Triggered by 5 Trojan Horse Bonus Scatters. Awards Sticky Expanded Bow Wilds with a **guaranteed Expanded Wild on Spin 1** and a minimum Wild Multiplier of **5×**!

---

## 2. Special Symbols & Core Mechanics

### 🏹 Odysseus’s Arrow — Expanding Full-Reel Wild (`WILD`)
* **Trigger:** The **Bow of Odysseus (`1×1 WILD`)** can land on any of the 5 reels (`Reels 1, 2, 3, 4, and 5`).
* **Full-Reel Expansion (`1:3`):** Whenever a Bow Wild lands and an expansion would form part of at least one winning payline combination, it fires a cyan lightning arrow upward and expands vertically to cover **all 3 positions on that reel (`1×3`)**.
* **Dynamic Wild Multipliers:** Upon expanding into a full-reel banner, the Wild reveals a random multiplier crest from the following possible values:
  > **`2×` | `3×` | `4×` | `5×` | `10×` | `15×` | `20×` | `25×` | `50×` | `100×`**
* **Additive Multipliers:** The Wild multiplier applies to any payline win that passes through the Expanded Wild. If **more than one Expanded Wild** is part of the same winning payline, their multiplier values are **added together** first before multiplying the line win (e.g., a `10×` Wild + a `25×` Wild on the same payline = **`35×`** total line multiplier!).
* **Substitution Rule:** Wild symbols substitute for all regular High (`H1–H4`) and Low (`L1–L4`) paying symbols. Wilds do not substitute for the **Trojan Horse (`BONUS`)** Scatter symbol. Only one Bow Wild can land per reel.

---

### 🐴 The Trojan Horse — Bonus Scatter (`SCATTER`)
* The **Trojan Horse (`BONUS`)** symbol can appear on all 5 reels during the Base Game and during both Free Spins rounds. It cannot land on a reel already covered by a Sticky Expanded Wild.
* Landing **3, 4, or 5** Trojan Horse Scatters anywhere on the reels in a single spin triggers the Free Spins Bonus feature:
  * **3 `BONUS` Scatters** $\rightarrow$ Triggers **10 Free Spins** in **The Cyclops’s Cave**.
  * **4 `BONUS` Scatters** $\rightarrow$ Triggers **12 Free Spins** in **The Cyclops’s Cave**.
  * **5 `BONUS` Scatters** $\rightarrow$ Triggers **12 Super Free Spins** at **The Shores of Hades**.

---

## 3. Bonus Game Modes

### 🔥 Bonus Feature 1: The Cyclops’s Cave (3 or 4 Scatters)
* **Setting:** The reels descend into the torch-lit treasure cavern of Polyphemus (`bg_freegame.png`).
* **Sticky Expanded Wilds:** During the Cyclops’s Cave Free Spins, any **Bow Wild** that lands on a reel **always expands to cover the full reel (`1×3`)** and becomes **Sticky (locked in place with golden chains)** for all remaining Free Spins!
* **Multiplier Roll:** When a Bow Wild expands, it locks in its revealed multiplier (`2×` to `100×`) for the duration of the Free Spins.
* **Re-trigger:** Landing Trojan Horse Scatters during the Cyclops’s Cave awards extra spins: **3 Scatters = +5 Free Spins**, **4 Scatters = +8 Free Spins**, **5 Scatters = +10 Free Spins**. Re-triggers can repeat, up to a maximum of **40 Free Spins** in total per round. Locked Sticky Wilds and their multipliers carry over.
* **Full Fleet (Max Win):** If Sticky Expanded Wilds lock on **all 5 reels**, every payline becomes a full Wild line. The round ends immediately and awards the **10,000× Maximum Win**.

### 💀 Bonus Feature 2: The Shores of Hades — Super Bonus (5 Scatters)
* **Setting:** The volcanic black-sand shores of the Underworld (`bg_superbonus.png`).
* **Guaranteed Sticky Wild on Spin 1:** Before the first spin begins, **1 full-reel Sticky Expanded Wild (`1×3`)** is guaranteed to drop onto a random reel.
* **Boosted Minimum Multipliers:** Low multipliers (`2×`, `3×`, `4×`) are removed from the pool! Every Expanded Wild that lands during the Shores of Hades is guaranteed to carry a multiplier between **`5×` and `100×`**:
  > **`5×` | `10×` | `15×` | `20×` | `25×` | `50×` | `100×`**
* **Re-trigger:** **3 Scatters = +3 Super Free Spins**, **4 Scatters = +5**, **5 Scatters = +8**. Re-triggers can repeat, up to a maximum of **40 Super Free Spins** in total per round.
* **Full Fleet (Max Win):** If Sticky Expanded Wilds lock on **all 5 reels**, the round ends immediately and awards the **10,000× Maximum Win**.

---

## 4. Feature Spin & Bonus Modes (Optional Play Modes)
Players can activate special modes directly from the left-side **Feature Panel** *(Note: Any mode costing more than `2×` the base play displays a mandatory confirmation prompt before activation)*:

| Feature Mode Name | Cost Multiplier | RTP | Max Win | What It Does |
| :--- | :--- | :--- | :--- | :--- |
| **Base Game** | **`1.0×`** | `96.20%` | `10,000×` | Standard play. This is the cheapest mode and must stay at exactly `1.0×`. |
| **Double Chance (Boost Mode)** | **`1.5×`** per spin | `96.25%` | `10,000×` | Doubles the statistical probability of landing 3+ Trojan Horse `BONUS` Scatters on each spin. Stays active until toggled off. |
| **Odysseus’s Volley (Feature Spin)** | **`25×`** per spin | `96.30%` | `10,000×` | Guarantees that at least **2 Expanding Bow Wilds (`1:3`)** land on a single Base Game spin. |
| **Trojan Bonus (Cave Free Spins)** | **`100×`** one-time | `96.35%` | `10,000×` | Immediately lands 3 or 4 Trojan Horse `BONUS` Scatters and enters **The Cyclops’s Cave** (10–12 Free Spins with Sticky Expanding Wilds). |
| **Wrath of Hades (Super Bonus)** | **`250×`** one-time | `96.40%` | `10,000×` | Immediately lands 5 Trojan Horse `BONUS` Scatters and enters **The Shores of Hades** (12 Super Free Spins with 1 Guaranteed Sticky Wild + `5×–100×` minimum multipliers). |

---

## 5. Symbol Payout Table
All payouts below are shown as **multipliers of the Base Play / Bet amount**. Wins are awarded for matching **3, 4, or 5 identical symbols** along any of the 20 active paylines, consecutively from the leftmost reel to the right (`Reel 1` $\rightarrow$ `Reel 5`).

### High-Paying Symbols (`H1` – `H4` & `WILD`)
| Symbol ID | Symbol Name | 3 of a Kind | 4 of a Kind | 5 of a Kind |
| :--- | :--- | :---: | :---: | :---: |
| **`WILD`** | **5× Expanded Bow Wilds** *(Full Line)* | — | — | **`25.00×`** *(+ Wild Multipliers)* |
| **`H1`** | **Odysseus (Golden Shield Medallion)** | `2.50×` | `8.00×` | **`25.00×`** |
| **`H2`** | **The Trireme Warship (Navy & Gold)** | `1.50×` | `5.00×` | **`15.00×`** |
| **`H3`** | **The Cyclops (Obsidian & Chain Emblem)** | `1.20×` | `3.00×` | **`10.00×`** |
| **`H4`** | **Island Map & Astrolabe (Glowing Cyan)** | `1.00×` | `2.00×` | **`6.00×`** |

### Low-Paying Symbols (`L1` – `L4`)
| Symbol ID | Symbol Name | 3 of a Kind | 4 of a Kind | 5 of a Kind |
| :--- | :--- | :---: | :---: | :---: |
| **`L1`** | **Greek Amphora Vase (Ruby Red)** | `0.40×` | `1.00×` | **`3.00×`** |
| **`L2`** | **Ancient Drachma Coin (Sapphire Blue)** | `0.30×` | `0.80×` | **`2.50×`** |
| **`L3`** | **Penelope’s Loom Shuttle (Emerald Green)** | `0.20×` | `0.60×` | **`2.00×`** |
| **`L4`** | **Kylix Wine Goblet (Amethyst Purple)** | `0.20×` | `0.50×` | **`1.50×`** |

---

## 6. 20 Fixed Paylines Map (5×3 Grid)
Only the highest win per payline is paid. Wins on different paylines are added together.  
*(Row `0` = Top Row, Row `1` = Middle Row, Row `2` = Bottom Row across Reels 1–5)*:

```text
Line 01: [1][1][1][1][1] (Middle Straight)   Line 11: [1][0][1][2][1] (Wave Down)
Line 02: [0][0][0][0][0] (Top Straight)      Line 12: [1][2][1][0][1] (Wave Up)
Line 03: [2][2][2][2][2] (Bottom Straight)   Line 13: [0][1][1][1][0] (Shallow U-Top)
Line 04: [0][1][2][1][0] (V-Shape)           Line 14: [2][1][1][1][2] (Shallow Arch)
Line 05: [2][1][0][1][2] (Inverted V)        Line 15: [0][1][0][1][0] (Top Zig-Zag)
Line 06: [0][0][1][2][2] (Step Down)         Line 16: [2][1][2][1][2] (Bottom Zig-Zag)
Line 07: [2][2][1][0][0] (Step Up)           Line 17: [1][0][0][0][1] (High Plateau)
Line 08: [1][2][2][2][1] (Low Trough)        Line 18: [0][2][0][2][0] (Deep W-Shape)
Line 09: [0][0][1][0][0] (Top Dip)           Line 19: [2][0][2][0][2] (Deep M-Shape)
Line 10: [2][2][1][2][2] (Bottom Peak)       Line 20: [0][2][2][2][0] (Deep Basin)
```

---

## 7. Win Celebration Tiers
When a spin or bonus round concludes with a high total multiplier, the game triggers an animated celebration popup (`hero_bigwin_popup.png`):
* **BIG WIN:** `15×` to `49.99×` Base Play
* **MEGA WIN:** `50×` to `199.99×` Base Play
* **EPIC ODYSSEY WIN:** `200×` to `9,999.99×` Base Play
* **OLYMPIAN MAX WIN (10,000×):** Reaches the `10,000×` Maximum Win cap!

---

## 8. Engine Compliance & General Rules
*(Mandatory disclosures for the in-game Info Modal. The info modal must also state the RTP and max win of every mode, list all obtainable multiplier values, explain how each feature is triggered, and include a short guide to the UI buttons.)*
1. **Stateless Outcome Independence:** Every play round is completely independent of previous or future outcomes. All outcomes are predetermined at the moment of the request by the certified Remote Gaming Server (RGS).
2. **Maximum Win Cap (10,000×):** The maximum potential win in any single game round (Base Game or Bonus Feature) is capped at **10,000× the Base Play/Bet**. If the total accumulated win during a round reaches or exceeds `10,000×`, the round ends immediately, any remaining Free Spins are forfeited, and the player is awarded exactly `10,000×`.
3. **Interrupted Rounds & Malfunctions:** Malfunction voids all pays and plays. Any unfinished game round terminated due to connection loss can be resumed upon reloading the game, or will be automatically resolved by the server after the timeout period, with any winnings credited to the player's balance.
4. **Controls & Shortcuts:** Pressing the `Spacebar` on desktop triggers a Spin (or skips win count-up animations where permitted).
5. **General Disclaimer (required verbatim or equivalent):**
   > Malfunction voids all wins and plays. A consistent internet connection is required. In the event of a disconnection, reload the game to finish any uncompleted rounds. The expected return is calculated over many plays. The game display is not representative of any physical device and is for illustrative purposes only. Winnings are settled according to the amount received from the Remote Game Server and not from events within the web browser. TM and © 2026 Engine.
6. **Confirmation Prompt:** Any mode costing more than `2×` the base play (Odysseus’s Volley, Trojan Bonus, Wrath of Hades) must ask the player to confirm before activation.

---

## 9. Social Mode (Stake.us) Wording Map
When the game loads with `social=true`, **all** player-facing text (UI, rules, info modal, popups, errors, mode names, replay) must use the replacement phrases below. English is the only supported language, and the social currencies are `XSC` (SC) and `XGC` (GC), never prefixed with `$`. The base text in this document stays as written for non-social play; the game ships a second string set (suggested prefix `sweeps_en`) built from this map.

| Spec wording (non-social) | Social-mode wording |
| :--- | :--- |
| Bet / Base Play / Base Bet | Play / Play Amount |
| Place your bet / Total Bet | Come and play / Total Play |
| Payout Table / Paytable | Win Table / Symbol Wins |
| Payout / Pays / Paid | Win / Wins / Won |
| Cost Multiplier / cost | Play Multiplier / can be played for |
| Winnings credited to the player's balance | Wins added to the player's balance |
| Cash / Money / Currency | Coins / Coins / Token |
| Mode names | Keep as listed in Section 4. They contain no restricted terms, and they must read identically in the game, the replay, and the math files. |

> Never use `Buy`, `Bonus Buy`, `Purchase`, `Win Feature`, or `Wager` anywhere. `Trojan Bonus` and `Wrath of Hades` are one-time instantly triggered features, and should be described that way.

---

## 10. Change Log vs v1 *(2026-11-03)*

**Changes made**
* Super Bonus renamed **The Gates of Hades → The Shores of Hades** everywhere. Reason: Engine bans titles starting "Gates of…", and the rename keeps the wording clear of that restriction.
* Added the **general disclaimer** (Section 8, item 5), the **confirmation prompt** rule (item 6), and the extra **info-modal contents** Engine requires.
* Added **Base Game 1.0×** as an explicit row in Section 4, and a **Max Win** column (10,000× per mode).
* Added Section 9, the **Social Mode wording map**.
* Platform name updated to "Engine". Fixed two typos (a missing space after "Scatter symbol." and "will either can be resumed").

* **Re-triggers defined:** Cave 3/4/5 Scatters = +5/+8/+10 spins; Shores of Hades 3/4/5 = +3/+5/+8 spins; 40-spin cap per round. Scatters now appear in Free Spins but cannot land on sticky reels, so re-trigger odds fall naturally as the board fills.
* **"Full Screen Upgrade (+2 Spins)" replaced by "Full Fleet (Max Win)".** Reason: with all 5 reels wild, one spin pays 20 lines × 25× × the summed multipliers. That is at least 5,000× in the Cave (minimum 2× per reel) and at least 12,500× at the Shores of Hades (minimum 5× per reel). The +2 spins were therefore meaningless; the board reached the cap anyway. Awarding the max win directly is clearer, and it gives the game a named, signature max-win moment.

**Open items**
* **Math simulation:** the re-trigger table, spin cap, and Full Fleet rule must be built into the Math SDK and simulated. The tail-probability limits make P(≥ 10,000×) ≤ 1% per mode the ceiling; the Wrath of Hades mode is the one most likely to approach it.
* **Mode RTP spread:** every mode currently sits in the allowed 96.0–96.7% band. Confirm against the simulated math, since the critical tests also require base-mode std dev ≥ 0.6.
