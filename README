# FTEC5660 Individual Project: Reproducibility Study & Optimization

- **Course:** FTEC5660 Agentic AI for Business and FinTech (CUHK MSc FinTech)
- **Author:** Cheng Ho Long
- **Student ID:** 1155273628
- **Benchmark Paper:** *TradingAgents: Multi-Agents LLM Financial Trading Framework* (arXiv:2412.20138, Tauric Research)
- **Target Asset & Date:** AAPL (Apple Inc.), March 25, 2024 (Table 1 Capital Preservation Verification)

---

## 1. Quickstart: Reproduction & Run Steps

### Step 1: Environment Setup
Clone this repository and create the Conda environment running Python 3.13:
```bash
# Clone this fork
git clone https://github.com/LeonHLCheng/TradingAgents.git
cd TradingAgents

# Create and activate Conda environment
conda create -n tradingagents-py312 python=3.13 -y
conda activate tradingagents-py312

# Install dependencies and editable package
pip install -e .
```

### Step 2: Configuration (`.env`)
Create a `.env` file in the repository root with the following configuration:
```bash
TRADINGAGENTS_LLM_PROVIDER=deepseek
TRADINGAGENTS_LLM_BACKEND_URL=https://www.moyu.cn/v1
TRADINGAGENTS_DEEP_THINK_LLM=DeepSeek-V4.1-flash
TRADINGAGENTS_QUICK_THINK_LLM=DeepSeek-V4.1-flash
DEEPSEEK_API_KEY=your_api_key_here
```

### Step 3: Single-Command Reproduction Execution
Run the trading simulation on the exact target evaluation date:
```bash
tradingagents --ticker AAPL --date 2024-03-25
```

---

## 2. Summary of Author Contributions & Commits

All code modifications are cleanly isolated in the git commit history (no monolithic dumps):

* **Primary Optimization Commit:** [`a87f2d0b7`](https://github.com/LeonHLCheng/TradingAgents/commit/a87f2d0b7507519b42fbc0b94b472b896709b773)
  * **Modified Files:**
    - `tradingagents/agents/risk_mgmt/aggressive_debator.py`
    - `tradingagents/agents/risk_mgmt/conservative_debator.py`
    - `tradingagents/agents/risk_mgmt/neutral_debator.py`
  * **Turn-Level Prompt Density Bounding:** Enforced 500 to 800 word density limits, stripping conversational filler and textbook definitions.
  * **Turn 1 Anti-Hallucination Guardrail:** Prevented the Aggressive Analyst from inventing hypothetical peer counter-arguments before other debaters speak.
  * **Risk Debate Round Truncation:** Demonstrated that 3 risk debate rounds achieve full mathematical consensus, cutting redundant turns.

---

## 3. Comparative Evaluation Matrix

| Metric | Baseline Avg ($\mu$) | Baseline Peak | Optimization Round 1 | Optimization Round 2 | Optimization Round 3 | Optimization Round 4 | Best Achieved vs Baseline |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Modification Scope** | Unconstrained Baseline | Unconstrained Peak | Conversational Filler Pruning | Symmetrical Word Caps (Research + Risk) | Targeted Risk Constraints (5 Rounds) | Targeted Risk Constraints (3 Rounds) | **Targeted Prompt + Round Reduction** |
| **Debate Rounds (Res / Risk)** | 5 / 5 | 5 / 5 | 5 / 5 | 5 / 5 | 5 / 5 | 5 / 3 | **5 Research / 3 Risk** |
| **Tokens Consumed** | 876,773 tokens | 985,595 tokens | 764,580 tokens | 665,623 tokens | 735,616 tokens | **553,153 tokens** | **-36.9% mean / -43.9% peak** |
| **Execution Latency** | 27.3 min | 28.0 min | 23.0 min | 14.0 min | 19.0 min | **17.0 min** | **-37.7% latency (10.3 min saved)** |
| **Trader Proposal** | Sell (66.7%) / Hold | Hold | Sell | Buy (Starter) | Sell (trim 20–25%) | **Sell (trim 40–50%)** | Restored Defensive Stance |
| **Portfolio Rating** | **Underweight** | **Hold** | **Underweight** | **Overweight (FAILED)** | **Underweight (SUCCESS)** | **Underweight (SUCCESS)** | **100% Capital Preservation** |
| **Risk Team Consensus** | Reached | Reached | Reached | Symmetrically Distorted | Reached | **Reached (Unanimous Derisk)** | **Full Quantitative Synthesis** |

---

## 4. Key Reproducibility Findings

1. **Table 1 Capital Preservation Replicated:** Across all baseline trials on March 25, 2024, TradingAgents accurately identified Apple's 50/200 SMA Death Cross and heavy institutional distribution, issuing defensive Underweight and Hold ratings that protected capital from Apple's subsequent April drop to $163.22.
2. **The Asymmetry of Financial Proof:** Constraining debaters symmetrically (Optimization Round 2) starved the Bear Analyst of the narrative bandwidth required to refute backward-looking record earnings, causing an erroneous Buy recommendation. Asymmetric budgeting (unconstrained Research, constrained Risk) fully restored defensive accuracy.
3. **Redundant Risk Debate Turns Eliminated:** Truncating Risk Management debate rounds from 5 to 3 rounds eliminated 6 redundant turns with zero loss in mathematical consensus depth, delivering the highest efficiency gains of the project.
