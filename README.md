# Data Product – Change Events (Dev Environment)

This repository contains the **end-to-end flow** for building a **Data Product (Change Events)** in the otis environment for sanity testing.  
The flow covers **data migration, semantic modeling, deployment, manifest creation, scanning, and quality/SLO validation**.  

---

## 📌 Steps

### 1. Data Migration (MetisDB → Icebase)
- Extract source data from **MetisDB**.  
- Load the data into **Icebase** as the target storage.  
- Validate:
  - Row counts between source and target.  
  - Schema compatibility.  
  - Data consistency checks.  

---

### 2. Semantic Model Creation
- Define a **semantic model** on top of Icebase.  
- Logical tables, measures, and dimensions are added as required for analytics.  
- Store semantic model definition files in `/semantic-model`.  

---

### 3. Bundle Deployment
- Package the semantic model and resources into a **bundle**.  
- Deploy the bundle into the otis environment:  

---

### 4. Data Product Manifest Deployment
- Create a Data Product manifest file (dp-manifest.yaml) describing the data product specification.
- Deploy the manifest to register the Data Product.
- Run a scanner job to sync metadata and lineage for the deployed Data Product.

---

### 5. SLO Job – Profiling & Quality Checks

- Execute an **SLO job** on the Data Product to validate data profiling and quality.  
- The SLO job evaluates two main aspects:

**Profiling checks**
- Row counts across tables  
- Schema structure and statistics  
- Data distribution metrics  

**Quality checks**
- Null value validations  
- Constraint validations (e.g., primary keys, uniqueness, foreign keys)  
- Threshold-based rules (e.g., % of nulls, numeric ranges, data freshness)  

- Once the SLO job completes, review the results in logs or via the **DPH UI** to ensure compliance.

