# ASOS Inventory & Supply Chain Analysis: Optimizing Phantom Revenue Loss

An end-to-end data analysis and supply chain risk intelligence project that extracts insights from scraped ASOS e-commerce data. This project identifies operational inefficiencies, quantifies financial leakages due to out-of-stock items ("Phantom Revenue Loss"), and provides strategic recommendations for inventory restocking.

---

## 🚀 Project Overview

In retail, e-commerce stockouts do not just represent missing products; they represent uncaptured market demand and straight financial leakage. This project analyzes a dataset of over 30,000 ASOS products to isolate supply chain bottlenecks by brand, item category, and specific sizing tiers.

### Key Business Metrics Derived:
*   **Stockout Rate**: The proportion of missing sizes relative to the total sizes offered for a unique product.
*   **Lost Revenue (Phantom Revenue)**: `Product Base Price` $\times$ `Total Count of Out-of-Stock Sizes`. This quantifies the gross financial value of demand that went completely unfulfilled.

---

## 🛠️ Tech Stack & Environment

*   **Platform**: Google Colab
*   **Language**: Python 3
*   **Core Libraries**: 
    *   `pandas` (Data manipulation, string parsing, and aggregation)
    *   `numpy` (Numerical operations)
    *   `matplotlib` & `seaborn` (Advanced data visualization)
    *   `adjustText` (Iterative label alignment algorithms)
    *   `re` (Regular expression parsing for sizing string features)

---

## 📈 Executive Insights & Visualizations

### 1. Brand Strategy Analysis (Price vs. Restock Risk)
*   **The Problem**: A standard scatterplot grouped by brand created an unreadable categorical smudge due to the massive volume of unique manufacturers. 
*   **The Solution**: Data points were aggregated into macro-level brand strategies plotting **Average Price vs. Average Stockout Count**, scaled dynamically by **Total Lost Revenue**. `adjustText` was used to programmatically align and highlight major risk drivers.
*   **Insight**: **ASOS (In-House Brand)** represents a massive outlier, sitting squarely in the high-price, high-stockout danger quadrant, indicating substantial unfulfilled demand for proprietary lines.
![Brand Strategy Analysis](images/brand_analysis.png)


### 2. Category Failure Modes
*   **Insight**: Grouping text descriptions into strict item families revealed that **Dresses** dwarf all other apparel categories combined in terms of total uncaptured revenue. Inventory optimization should start here.
![Total Lost Revenue by Category](images/category_loss.png)


### 3. Size-Level Supply Bottlenecks
*   **Insight**: Standardizing size availability data revealed a near-perfect bell curve centered over **UK 8, UK 10, and UK 12**. The supply chain is systematically under-ordering the most popular, mainstream consumer sizes while over-indexing on fringe sizes.
![Size Stockouts](images/size_bottlenecks.png)


### 4. Pricing Resilience Tiers
*   **Insight**: A distributional boxplot across stockout severity levels indicates that low-to-mid tier budget items (£20 - £45) experience the highest frequency of extreme size depletion, fueled by faster retail turnover rates.
![Price Distribution Boxplot](images/price_distribution.png)


---

## 💻 Code Structure & Workflow

1.  **Ingestion & Data Type Correction**: Loading Kaggle e-commerce data and strictly coercing prices into floating-point numerical types using `pd.to_numeric()`.
2.  **Feature Extraction**: Applying customized string-splitting algorithms and regex architectures to clean messy string objects into countable inventory features.
3.  **Algorithmic Restructuring**: Leveraging `.explode()` arrays to flatten nested size string records into clean statistical frequency tables.
4.  **Reporting**: Exporting cleanly segmented DataFrames pointing out exactly which brands demand immediate warehouse replenishment.

---

## 📊 Data Source
The dataset used in this analysis was sourced from **Kaggle** (ASOS Scraped Product Dataset).

---

## 🔧 How to Run
1. Open a blank notebook in **Google Colab**.
2. Clone this repository or upload the notebook file.
3. Download the `products_asos.csv` file from Kaggle and place it in your local runtime working directory.
4. Install the required text optimization library:
   ```bash
   !pip install adjustText