

# Stock Movement Optimization Engine 🏦📈

## 📘 Overview
This project simulates the daily operations of a **broker facilitating stock movements** for multiple hedge funds, aiming to satisfy client trading requirements while minimizing **transaction costs** and **maximizing liquidity**. It is designed to intelligently route stock flows across accounts and pledge excess holdings into triparty accounts to raise capital efficiently.

The core objective is to design an algorithm that:
- Prioritizes client demand fulfillment
- Minimizes transaction costs by preferring intra-parent account transfers
- Maximizes cash generation by utilizing idle stock through triparty pledging

---

## 🧠 Problem Context
In a real-world broker-dealer scenario:
- Each stock is held in multiple accounts (owned by clients or triparty custodians)
- Each account belongs to a parent entity (e.g., hedge funds, clearing firms)
- **Client stock demands** must be fulfilled using available balances
- **Excess stocks** should be moved to **triparty accounts** to generate liquidity
- **Transaction costs** are lower for intra-parent transfers and higher across parents
- The system must choose paths (chains of transfers) that minimize total movement cost

---

## 🔍 Key Features
- 🔄 **Dynamic Routing of Stock Flows**: Uses Dijkstra’s algorithm to find the optimal low-cost path for each stock transfer.
- 🏦 **Parent-aware Cost Optimization**: Penalizes inter-parent transfers while prioritizing intra-group movements.
- 💰 **Triparty Liquidity Maximization**: Moves unused stock into triparty accounts when possible to unlock value.
- 📉 **Custom Transaction Cost Model**:
  - Base intra-parent cost: low
  - Base inter-parent cost: high
  - Cost increases with transaction volume

---

## ⚙️ Tech Stack
- **Python** – Core logic and simulation
- **Heapq** – Priority queue for efficient pathfinding
- **Defaultdict** – State and structure management for balances, graphs, and accounts

---

## 🧪 Algorithm Workflow

1. **Parse Input**: Load stock prices, account metadata, stock eligibility, and balances.
2. **Construct Graph**: Build a weighted, directed graph of valid stock transfer paths.
3. **Demand Matching**:
   - Match accounts with stock deficits (demands) to accounts with surpluses (sources).
   - Use **shortest-cost path** between them.
   - Prioritize paths within the same parent entity.
4. **Triparty Movement**:
   - After fulfilling demands, excess stock is transferred to triparty accounts via optimal routes.

---

## 📁 Project Structure


