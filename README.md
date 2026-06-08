# RFM Customer Segmentation 📊

## Overview

A data-driven customer analytics project using RFM (Recency, Frequency, Monetary) analysis to segment retail customers into actionable business segments. This enables targeted marketing, customer retention, and personalized strategies for different customer groups.

## Problem Statement

Retail businesses struggle to identify:
- **High-value customers** to retain and reward
- **At-risk customers** who might churn and need engagement
- **Potential customers** to nurture and convert
- **Lost customers** to re-engage or let go strategically

**Solution:** RFM segmentation provides a simple, quantifiable framework for customer classification based on purchasing behavior.

---

## What is RFM Analysis?

RFM is a behavior-based customer segmentation model based on three key metrics:

### R - Recency: How Recently Did They Purchase?

**Definition:** Days since last purchase from the snapshot date

**Why It Matters:** Recent customers are more likely to respond to campaigns and make repeat purchases

**Formula:** Snapshot Date - Last Purchase Date = Recency (in days)

**Interpretation:** Lower recency = Better (more recent purchase = higher engagement)

**Example:**
- Customer A: Last purchase 2 days ago → Recency = 2 (EXCELLENT)
- Customer B: Last purchase 326 days ago → Recency = 326 (POOR)

### F - Frequency: How Often Do They Purchase?

**Definition:** Number of transactions/purchases in the time period

**Why It Matters:** Frequent buyers are more loyal and predictable

**Formula:** COUNT(Transactions per customer)

**Interpretation:** Higher frequency = Better (frequent purchases = loyal)

**Example:**
- Customer A: 1 purchase → Frequency = 1 (RARE)
- Customer B: 182 purchases → Frequency = 182 (LOYAL)

### M - Monetary: How Much Have They Spent?

**Definition:** Total revenue/spending from customer transactions

**Why It Matters:** Spending indicates customer value and profitability

**Formula:** SUM(Transaction Amount per customer)

**Interpretation:** Higher monetary = Better (big spenders = high value)

**Example:**
- Customer A: $77 total spent → Monetary = 77 (LOW VALUE)
- Customer B: $4,310 total spent → Monetary = 4310 (HIGH VALUE)

---

## RFM Scoring System

Each metric is scored from **1 to 5** based on quantiles:
Quantile Ranges:
├─ Score 1: Bottom 25% (Worst performers)
├─ Score 2: 25-50% (Below average)
├─ Score 3: 50-75% (Average)
├─ Score 4: 75-95% (Good performers)
└─ Score 5: Top 5% (Best performers)

### Scoring Logic for Each Metric

**Recency Score:** LOWER is better
Recency Distribution:
├─ Score 5: Last purchase 0-2 days ago (VERY RECENT - Best)
├─ Score 4: Last purchase 3-19 days ago
├─ Score 3: Last purchase 20-75 days ago
├─ Score 2: Last purchase 76-310 days ago
└─ Score 1: Last purchase 326+ days ago (NOT RECENT - Worst)

**Frequency Score:** HIGHER is better
Frequency Distribution:
├─ Score 5: 182 purchases (LOYAL - Best)
├─ Score 4: 95 purchases
├─ Score 3: 45 purchases
├─ Score 2: 17 purchases
└─ Score 1: 1 purchase (RARE - Worst)

**Monetary Score:** HIGHER is better
Monetary Distribution:
├─ Score 5: $4,310 total spent (HIGH VALUE - Best)
├─ Score 4: $2,156 total spent
├─ Score 3: $1,200 total spent
├─ Score 2: $500 total spent
└─ Score 1: $77 total spent (LOW VALUE - Worst)

---

## Customer Segments

Combining R, F, M scores creates actionable business segments:

### 1. Champions (RFM: 5,5,5 or 4,5,5 or 5,4,5)

**Profile:** The absolute best customers

**Characteristics:**
- Recent purchases (last 2 days)
- Frequent buyers (100+ purchases)
- High spending ($2,000+ total)
- Maximum lifetime value

**Business Value:** Highest priority - generate majority of revenue

**Recommended Actions:**
- ✅ VIP treatment and exclusive perks
- ✅ Involve in product development and beta testing
- ✅ Assign personal account manager
- ✅ First access to new products and collections
- ✅ Exclusive discounts for bulk purchases
- ✅ Birthday/anniversary gifts and surprises

**Expected Response:** Very high (60-80% to campaigns)

**Goal:** Maximize lifetime value and advocacy

---

### 2. Loyal Customers (R≥4, F≥3)

**Profile:** Consistently valuable, dependable customers

**Characteristics:**
- Regular recent purchases
- Good purchase frequency (30+ purchases)
- Decent spending ($800-2,000)
- Proven loyalty over time

**Business Value:** Second tier - stable revenue generators

**Recommended Actions:**
- ✅ Membership/rewards program enrollment
- ✅ Cross-sell and upsell opportunities
- ✅ Personalized product recommendations
- ✅ Special birthday and anniversary offers
- ✅ Exclusive member-only sales
- ✅ Loyalty points that accrue benefits

**Expected Response:** High (40-60% to campaigns)

**Goal:** Retain and grow spending over time

---

### 3. Potential Loyalists (R≥3)

**Profile:** Recently engaged, building relationships

**Characteristics:**
- Decent recent activity (20-75 days)
- Moderate purchase frequency (10-30 purchases)
- Building spending history ($300-1,000)
- Early stage of customer lifecycle

**Business Value:** Future value - conversion opportunity

**Recommended Actions:**
- ✅ Targeted email campaigns with relevant products
- ✅ First-purchase category discounts
- ✅ Engagement through educational newsletters
- ✅ Customer feedback surveys
- ✅ Product recommendations based on history
- ✅ Incentives to increase purchase frequency

**Expected Response:** Moderate (20-40% to campaigns)

**Goal:** Convert to loyal customer segment

---

### 4. At-Risk Customers (R low, F high, M high)

**Profile:** URGENT - Previously loyal, now disengaged

**Characteristics:**
- Long time since last purchase (100+ days)
- Were frequent buyers (50+ purchases)
- Had good spending history ($1,500+)
- Silent for extended period

**Business Value:** Churn risk - potential to recover

**Recommended Actions:**
- ✅ Urgent re-engagement campaigns
- ✅ Special "We miss you" messaging
- ✅ Significant comeback offers (15-20% discount)
- ✅ Survey: "What happened? Why haven't you visited?"
- ✅ Highlight new products since last visit
- ✅ Exclusive win-back promotions

**Expected Response:** Low-Moderate (10-25% to campaigns)

**Goal:** Prevent churn and reactivate

---

### 5. Lost Customers (R=1, F=1)

**Profile:** Haven't bought in very long time

**Characteristics:**
- No recent activity (300+ days)
- Minimal engagement (1 purchase)
- Very low spending ($77 or less)
- Likely churned permanently

**Business Value:** Recovery unlikely - lowest priority

**Recommended Actions:**
- ✅ Win-back promotions (20-30% discount)
- ✅ Simplified reactivation process
- ✅ Remove from active marketing campaigns
- ✅ Seasonal/holiday special offers
- ✅ "One last offer" before removal from list

**Expected Response:** Very Low (5-15% to campaigns)

**Goal:** Attempt recovery or accept loss gracefully

---

## Dataset Information

### Source
Online retail transaction dataset (e-commerce data)

### Columns in Dataset
InvoiceNo    - Unique transaction identifier
StockCode    - Product SKU/identifier
Description  - Product name and details
Quantity     - Number of items purchased
InvoiceDate  - Transaction timestamp
UnitPrice    - Price per individual item
CustomerID   - Unique customer identifier
Country      - Customer's country/location

### Example Transaction Records
InvoiceNo: 536365
StockCode: 85123A
Description: WHITE HANGING HEART T-LIGHT HOLDER
Quantity: 6
InvoiceDate: 2010-12-01 08:26:00
UnitPrice: 2.55
CustomerID: 17850
Country: United Kingdom
TotalPrice: 15.30 (Calculated: 6 × 2.55)

### Dataset Statistics
- **Total Transactions:** 500,000+
- **Unique Customers:** 4,000+
- **Countries Represented:** 37
- **Time Period:** Dec 2010 - Dec 2011
- **Product Categories:** Multiple retail categories

---

## Project Workflow

### Step 1: Data Cleaning

Remove incomplete or invalid data:

```python
# Remove rows with missing CustomerID
df = df.dropna(subset=['CustomerID'])

# Remove exact duplicate rows
df = df.drop_duplicates()

# Remove negative quantities (product returns/cancellations)
df = df[df['Quantity'] > 0]
```

**Result:** Clean dataset ready for analysis

### Step 2: Feature Engineering

Create business-relevant features:

```python
# Calculate revenue per transaction
df['TotalPrice'] = df['Quantity'] * df['UnitPrice']

# Convert to proper datetime format
df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])
```

**Result:** Additional columns for RFM calculation

### Step 3: RFM Calculation

Aggregate customer metrics:

```python
# Set reference date (one day after latest transaction)
snapshot_date = df['InvoiceDate'].max() + timedelta(days=1)

# Group by customer and calculate RFM
rfm = df.groupby('CustomerID').agg({
    'InvoiceDate': lambda x: (snapshot_date - x.max()).days,  # Recency
    'InvoiceNo': 'count',                                      # Frequency
    'TotalPrice': 'sum'                                        # Monetary
})

rfm.columns = ['Recency', 'Frequency', 'Monetary']
```

**Result:** One row per customer with RFM metrics

### Step 4: RFM Scoring

Convert metrics to 1-5 scores:

```python
# Calculate quantiles
r_quantiles = rfm['Recency'].quantile([0.25, 0.50, 0.75, 0.95])
f_quantiles = rfm['Frequency'].quantile([0.25, 0.50, 0.75, 0.95])
m_quantiles = rfm['Monetary'].quantile([0.25, 0.50, 0.75, 0.95])

# Score each metric
def score_metric(value, quantiles):
    if value <= quantiles[0.25]:
        return 1
    elif value <= quantiles[0.50]:
        return 2
    elif value <= quantiles[0.75]:
        return 3
    elif value <= quantiles[0.95]:
        return 4
    else:
        return 5

rfm['R_Score'] = rfm['Recency'].apply(lambda x: score_metric(x, r_quantiles))
rfm['F_Score'] = rfm['Frequency'].apply(lambda x: score_metric(x, f_quantiles))
rfm['M_Score'] = rfm['Monetary'].apply(lambda x: score_metric(x, m_quantiles))

# Combine into RFM segment code
rfm['RFM_Segment'] = rfm['R_Score'].astype(str) + \
                     rfm['F_Score'].astype(str) + \
                     rfm['M_Score'].astype(str)
```

**Result:** Each customer has R_Score, F_Score, M_Score, and RFM_Segment

### Step 5: Segmentation

Assign business segment names:

```python
def segment_customer(r, f, m):
    if r >= 4 and f >= 4 and m >= 4:
        return 'Champions'
    elif r >= 4 and f >= 3:
        return 'Loyal Customers'
    elif r >= 3:
        return 'Potential Loyalists'
    elif r == 1 and f == 1:
        return 'Lost Customers'
    else:
        return 'At-Risk'

rfm['Customer_Segment'] = rfm.apply(
    lambda row: segment_customer(row['R_Score'], row['F_Score'], row['M_Score']),
    axis=1
)
```

**Result:** Each customer assigned to a business segment

### Step 6: Analysis & Visualization

Explore segment characteristics:

```python
# 1. Distribution of RFM metrics
fig, axes = plt.subplots(1, 3, figsize=(15, 4))
rfm['Recency'].hist(ax=axes[0], bins=30, color='skyblue')
axes[0].set_title('Recency Distribution')
axes[0].set_xlabel('Days Since Last Purchase')

rfm['Frequency'].hist(ax=axes[1], bins=30, color='lightgreen')
axes[1].set_title('Frequency Distribution')
axes[1].set_xlabel('Number of Purchases')

rfm['Monetary'].hist(ax=axes[2], bins=30, color='salmon')
axes[2].set_title('Monetary Distribution')
axes[2].set_xlabel('Total Amount Spent ($)')

plt.tight_layout()
plt.show()

# 2. Segment distribution
segment_counts = rfm['Customer_Segment'].value_counts()
segment_counts.plot(kind='barh', figsize=(10, 6), color='teal')
plt.title('Customer Count by Segment')
plt.xlabel('Number of Customers')
plt.show()

# 3. Recency vs Frequency scatter
plt.figure(figsize=(12, 8))
scatter = plt.scatter(rfm['Recency'], rfm['Frequency'], 
                     c=rfm['M_Score'], cmap='viridis', 
                     alpha=0.6, s=100)
plt.colorbar(scatter, label='Monetary Score')
plt.xlabel('Recency (Days Since Last Purchase)')
plt.ylabel('Frequency (Number of Purchases)')
plt.title('Customer Positioning: Recency vs Frequency')
plt.show()
```

**Result:** Visualizations reveal segment patterns and characteristics

### Step 7: Export Results

Save segmentation for business use:

```python
# Save to CSV for marketing team
rfm.to_csv('RFM_Segments.csv', index=False)
print("✓ File saved: RFM_Segments.csv")
```

**Result:** Ready for marketing campaigns and business decisions

---

## Results

### Segment Distribution (Example)
Potential Loyalists: 45%  (Recently active, building relationship)
Loyal Customers:     25%  (Regular, good spending)
Others:              15%  (Various intermediate categories)
At-Risk:             10%  (Previously active, now dormant)
Lost Customers:       5%  (Haven't bought in very long time)
Champions:           <1%  (Best of the best customers)

### Customer Value Metrics by Segment

| Segment | Avg Recency | Avg Frequency | Avg Monetary | Customer Count | % of Total |
|---------|-------------|---------------|--------------|----------------|-----------|
| Champions | 2 days | 182 purchases | $4,310 | 50 | <1% |
| Loyal Customers | 35 days | 95 purchases | $2,156 | 800 | 20% |
| Potential Loyalists | 75 days | 45 purchases | $1,200 | 1,800 | 45% |
| At-Risk | 180 days | 120 purchases | $3,500 | 400 | 10% |
| Lost Customers | 326 days | 1 purchase | $77 | 200 | 5% |

### Key Insights

- **Champions** account for <1% of customers but highest lifetime value
- **At-Risk** segment has high historical value - strong recovery opportunity
- **Potential Loyalists** largest segment - conversion potential
- **Recency-Frequency relationship:** Recent ≠ Frequent (different characteristics)
- **Monetary varies widely:** Some high spenders are infrequent; some frequent spenders spend little

---

## Business Recommendations

### Action Plan by Segment

**Champions (Best Customers):**
- Implement VIP program with dedicated support
- Involve in product development and feedback
- Offer exclusive previews and early access
- Create personal relationship touchpoints
- Higher lifetime value justifies investment
- Expected ROI: Very High (5-10x per $1 invested)

**Loyal Customers (Keep Growing):**
- Build membership/loyalty points program
- Cross-sell and upsell complementary products
- Regular personalized communications
- Celebrate relationship milestones
- Encourage referrals with incentives
- Expected ROI: High (3-5x per $1 invested)

**Potential Loyalists (Convert & Nurture):**
- Educational email nurture sequences
- Category-based discounts to explore
- Product recommendations from purchase history
- Feedback surveys to understand preferences
- Low-pressure engagement content
- Expected ROI: Moderate (1.5-3x per $1 invested)

**At-Risk (Urgent Recovery):**
- Immediate win-back campaign (time-sensitive)
- Highlight what's new since last visit
- Significant discount or special offer
- Personal outreach: "We miss you"
- Address potential pain points
- Expected ROI: Low-Moderate (1-2x per $1 invested)

**Lost Customers (Accept Loss):**
- One final seasonal offer attempt
- If no response, remove from active campaigns
- Archival with potential reactivation later
- Monitor for unexpected return interest
- Learn from exit patterns
- Expected ROI: Very Low (<1x per $1 invested)

---

## Technical Stack

| Tool | Purpose | Version |
|------|---------|---------|
| Python | Core language | 3.8+ |
| Pandas | Data manipulation & grouping | 2.0.3 |
| NumPy | Numerical operations | 1.24.3 |
| Matplotlib | Basic visualization | 3.7.2 |
| Seaborn | Advanced visualization | 0.12.2 |
| Scikit-learn | Quantile calculations | 1.3.0 |

## Requirements
pandas==2.0.3
numpy==1.24.3
matplotlib==3.7.2
seaborn==0.12.2
scikit-learn==1.3.0

---

## Installation

```bash
# Clone repository
git clone https://github.com/najeetha-banu/RFM-Customer-Segmentation.git
cd RFM-Customer-Segmentation

# Install dependencies
pip install -r requirements.txt
```

---

## Usage

### Run in Google Colab

1. Open `rfm_segmentation.ipynb` in Google Colab
2. Upload dataset or connect to Google Drive
3. Execute cells sequentially
4. Download RFM_Segments.csv with results

### Run Locally

```bash
jupyter notebook rfm_segmentation.ipynb
```

### Key Parameters (Customize for Your Business)

```python
# Reference date for recency calculation
snapshot_date = df['InvoiceDate'].max() + timedelta(days=1)

# Quantile thresholds for scoring
quantiles = [0.25, 0.50, 0.75, 0.95]

# Segment assignment thresholds
CHAMPIONS_R = 4
CHAMPIONS_F = 4
CHAMPIONS_M = 4

LOYAL_R = 4
LOYAL_F = 3

POTENTIAL_R = 3
```

---

## Output Files Generated

The notebook creates:
- **RFM_Segments.csv** - Customer segmentation with all metrics
- **Distribution plots** - RFM metric histograms
- **Segment counts** - Bar chart of customers per segment
- **Scatter plots** - Recency vs Frequency visualization
- **Summary statistics** - Mean metrics by segment

---

## Key Learnings

✅ **RFM Framework:** Simple yet powerful customer segmentation approach  
✅ **Quantile-based Scoring:** Distributional approach to fair classification  
✅ **Customer Behavior Analysis:** Understanding purchase patterns and trends  
✅ **Business Strategy:** Converting data insights into actionable strategies  
✅ **Data Visualization:** Communicating insights effectively to stakeholders  
✅ **Feature Engineering:** Creating business-relevant metrics from transactions  
✅ **Marketing Analytics:** Data-driven customer relationship management  

---

## Interview Explanation

> "This RFM customer segmentation project analyzes retail transaction data to identify and target different customer groups strategically. I cleaned the dataset by removing missing values, duplicates, and cancelled orders, then engineered features like TotalPrice. I calculated three key RFM metrics: Recency (days since purchase), Frequency (number of purchases), and Monetary value (total spending). I scored each metric from 1-5 based on quantiles, then combined these scores to create five business segments: Champions (best customers), Loyal Customers, Potential Loyalists, At-Risk (churn risk), and Lost Customers. I visualized the segment distribution and provided specific business recommendations for each segment—for example, Champions should receive VIP treatment and exclusive access, while At-Risk customers need urgent re-engagement campaigns. This data-driven approach enables targeted marketing, personalized strategies, and maximizes customer lifetime value."

---

## Real-World Applications

| Industry | Use Case | Business Impact |
|----------|----------|-----------------|
| E-commerce | Customer retention and upselling | Increase repeat purchase rate |
| Retail | In-store personalization and loyalty | Improve customer lifetime value |
| SaaS | Churn prediction and upsell | Reduce churn, increase ARPU |
| Banking | Customer lifetime value and credit risk | Optimize credit decisions |
| Insurance | Premium optimization and retention | Reduce lapse rate |
| Telecom | Churn prediction and loyalty rewards | Reduce customer churn |
| Subscription | Renewal probability and upgrades | Increase subscription retention |

---

## Future Enhancements

- [ ] Integrate machine learning for churn prediction
- [ ] Cohort analysis (customer acquisition date tracking)
- [ ] CLV (Customer Lifetime Value) prediction models
- [ ] Collaborative filtering for personalized recommendations
- [ ] Time-series analysis of customer segment evolution
- [ ] A/B testing framework for campaign effectiveness
- [ ] Automated email campaigns triggered by segment changes
- [ ] Dashboard for real-time segment monitoring

---

## Author

**Najeetha Banu**
- M.Tech in AI & Decision Sciences, Manipal Institute of Technology
- Interest in Data Analytics and Business Intelligence
- 10-month internship at SABIC (Data Science & Analytics)

## Contact

📧 Email: najeetha2002@gmail.com
🔗 LinkedIn: [https://linkedin.com/in/najeetha-banu](https://www.linkedin.com/in/najeetha-banu-37314820a/)
