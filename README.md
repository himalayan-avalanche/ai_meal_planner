# Retail AI: Personalized Meal Recommendation Engine

A production-grade recommendation and scoring engine built to bridge the gap between unstructured culinary inspiration and structured retail SKU inventory. This system processes raw recipes, extracts nutritional and allergen data, and maps ingredients to real-time inventory for hyper-personalized household recommendations.

## Core Architecture

The system operates on three primary intelligence layers:

### 1. The Retail Bridge (Ingredient-to-SKU Matching)
Generic LLMs understand "chicken"; this engine understands "Meijer 1lb Organic Chicken Breast."
* **Scale:** Extracted 5,000+ unique ingredients from 20,000+ distinct meals and mapped them to 60,000+ active retail SKUs.
* **Fidelity:** Handles complex substitutions, unit conversions, and brand hierarchies, achieving a 100% match rate for top-ranked recommendations.
* **Inventory Awareness:** Checks real-time stock availability and ranks the next-best alternatives if a primary SKU is out of stock.

### 2. Household Intelligence & Behavioral Clustering
Generates persistent dietary profiles by analyzing 2 years of past purchase data across 1.5 million households.
* **Dietary Classification:** Automatically segments households (e.g., Vegan, Pescatarian). 
* **Micro-Targeting:** Behavioral clustering isolates highly specific dietary vectors—for instance, identifying households that consistently exclude dairy (butter/cheese/cream) while over-indexing on high-spice regional cuisines like Mexican or Indian—and maps these vectors to the catalog.
* **Spend Profiling:** Identifies brand preferences and matches the total "Auto-Cart" cost to the household's historical spend tier.

### 3. The Convergence Scoring Engine
Meals are ranked and surfaced using a proprietary, multi-weighted algorithm:
* **Coverage %:** Hard filter for SKU availability.
* **Recency (2x Weight):** Heavily weights recent purchases to capture current staple patterns.
* **Collaborative Filtering:** Identifies "spending twins" using high-dimensional behavioral embeddings (FAISS).
* **Nutritional Profiling:** Cross-references 20+ extracted nutrients and allergens against user constraints.

## Tech Stack
* **Data Processing:** PySpark, Databricks, Delta Lake
* **Machine Learning:** Collaborative Filtering, Azure OpenAI (Embeddings), FAISS (Vector Retrieval)
* **Application Layer:** Python (FastAPI backend), Next.js / Tailwind CSS (UI), Vercel (Deployment)
