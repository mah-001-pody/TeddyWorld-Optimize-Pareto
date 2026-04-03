# 🧸 TeddyWorld Optimize Analyst

A data analysis project applying the **Pareto Principle (80/20 Rule)** to optimize product portfolio and marketing channel allocation for **TeddyWorld** — a teddy bear e-commerce store.

---

## 📌 Project Overview

This project addresses two key business questions raised by TeddyWorld's management:

1. **Product Optimization** — Which products are actually generating profit and which are just cluttering the warehouse?
2. **Marketing Channel Optimization** — Which advertising channels (Google, Facebook, etc.) are driving the most revenue and deserve continued investment?

By applying the Pareto Principle, this analysis aims to identify the **20% of products and channels that generate 80% of the business value**, enabling smarter resource allocation decisions.

---

## 🗂️ Dataset

The analysis uses six relational tables from TeddyWorld's transactional database:

| Table | Description |
|---|---|
| `orders.csv` | General order information (order ID, price, COGS, session ID) |
| `order_items.csv` | Line-item details per order (product, price, COGS) |
| `order_item_refunds.csv` | Refund transactions linked to order items |
| `products.csv` | Product catalog (ID, name, launch date) |
| `website_sessions.csv` | Web session data including UTM source/campaign and device type |
| `website_pageviews.csv` | Individual page views per session |

> See [`Data_Dictionary.pdf`](Data_Dictionary.pdf) for full field descriptions.

**Date range:** March 2012 – (multi-year transactional data)

---

## 🔍 Problem Statements

### Problem 1: Product Portfolio Optimization

> *"Get rid of the cluttering, non-profit items and only keep the real money-making ones!"*

**Goal:** Identify which products contribute the most to net profit (after refunds), and which underperform enough to consider discontinuing.

**Approach:**
- Merge `order_items` with `order_item_refunds` to calculate **net revenue per product**
- Compute **cumulative revenue percentages** to build a Pareto table
- Visualize with a combined bar + line chart (Pareto chart)
- Analyze **refund rates** per product to surface hidden cost risks

**Key Findings:**
- 🥇 **The Original Mr. Fuzzy** alone contributes **59.87%** of total net profit — the undisputed top performer
- 🥈 **The Forever Love Bear** brings the combined share to **78.41%**, closely aligning with the 80/20 rule
- ⚠️ The Original Mr. Fuzzy also carries the **highest refund cost** ($61,837.63, refund rate ~5.11%), warranting product quality investigation
- ⚠️ **The Birthday Sugar Panda** has the **highest refund rate (6.04%)** despite mid-tier revenue — a risk to monitor

---

### Problem 2: Marketing Channel Optimization

> *"We are investing heavily in multiple advertising channels, but which ones actually bring in high-quality customers?"*

**Goal:** Identify the top 20% of traffic sources (UTM sources) that generate 80% of total net revenue, so the marketing team can reallocate budget effectively.

**Approach:**
- Join `website_sessions` → `orders` → `order_items` → `order_item_refunds` to compute **net revenue per UTM source**
- Handle missing `utm_source` values by categorizing them as `"Organic"` (natural traffic)
- Build and visualize a **Pareto table for UTM sources**

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| **Python 3** | Core programming language |
| **pandas** | Data loading, merging, and aggregation |
| **matplotlib** | Custom chart rendering |
| **seaborn** | Statistical visualizations |
| **Jupyter Notebook** | Interactive analysis environment |

---

## 📁 Project Structure

```
TeddyWorld-Optimize-Analyst/
│
├── data/
│   ├── orders.csv
│   ├── order_items.csv
│   ├── order_item_refunds.csv
│   ├── products.csv
│   ├── website_sessions.csv
│   └── website_pageviews.csv
│
├── TeddyWorld_Optimize_Pareto.ipynb   # Main analysis notebook
├── Data_Dictionary.pdf                # Field descriptions for all tables
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas matplotlib seaborn jupyter
```

### Run the Notebook

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/teddyworld-optimize-analyst.git
   cd teddyworld-optimize-analyst
   ```

2. Place the CSV data files inside a `data/` folder (or update the file paths in the notebook).

3. Launch Jupyter:
   ```bash
   jupyter notebook TeddyWorld_Optimize_Pareto.ipynb
   ```

4. Run all cells from top to bottom.

---

## 📊 Sample Outputs

- **Pareto Chart — Net Revenue by Product**: Bar chart of net revenue per product overlaid with a cumulative percentage line
- **Refund Rate Analysis Table**: Side-by-side comparison of net revenue vs. refund cost and refund rate per product
- **Pareto Chart — Net Revenue by UTM Source**: Same methodology applied to marketing channels

---

## 💡 Business Recommendations

- **Retain and invest further** in *The Original Mr. Fuzzy* and *The Forever Love Bear* — they are the core profit drivers
- **Investigate quality issues** for *The Original Mr. Fuzzy* to reduce its refund rate and protect net margins
- **Evaluate strategically** *The Birthday Sugar Panda* and *The Hudson River Mini Bear* — their high refund rates relative to revenue make them candidates for product improvement or discontinuation
- **Focus marketing budget** on the top-performing UTM sources identified in Problem 2, and reallocate spend away from underperforming channels

---

## 👤 Author

**[Your Name]**
- GitHub: [@your-username](https://github.com/your-username)
- LinkedIn: [your-linkedin](https://linkedin.com/in/your-linkedin)

---

## 📄 License

This project is for educational and portfolio purposes. Data is fictional/simulated for analysis practice.
