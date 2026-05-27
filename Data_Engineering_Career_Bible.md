# 🏗️ DATA ENGINEERING CAREER BIBLE
### From Zero to FAANG-Level Data Engineer — Complete Master Roadmap

> **Author's Note:** This is a living career document. Revisit it monthly. What feels hard today will feel obvious in 6 months. Trust the process.

---

## 📋 TABLE OF CONTENTS

1. [Foundation Phase](#1-foundation-phase)
2. [Python for Data Engineering](#2-python-for-data-engineering)
3. [SQL Roadmap](#3-sql-roadmap)
4. [Linux + Git Roadmap](#4-linux--git-roadmap)
5. [Data Warehousing](#5-data-warehousing)
6. [PySpark Roadmap](#6-pyspark-roadmap)
7. [Databricks Roadmap](#7-databricks-roadmap)
8. [Azure Roadmap](#8-azure-roadmap)
9. [Airflow Roadmap](#9-airflow-roadmap)
10. [Kafka Roadmap](#10-kafka-roadmap)
11. [Snowflake Roadmap](#11-snowflake-roadmap)
12. [DBT Roadmap](#12-dbt-roadmap)
13. [Power BI Roadmap](#13-power-bi-roadmap)
14. [Unique Projects Section](#14-unique-projects-section)
15. [Mega End-to-End Project](#15-mega-end-to-end-project)
16. [System Design for Data Engineers](#16-system-design-for-data-engineers)
17. [Interview Preparation](#17-interview-preparation)
18. [GitHub + Portfolio Roadmap](#18-github--portfolio-roadmap)
19. [Certification Roadmap](#19-certification-roadmap)
20. [Daily/Weekly Schedule](#20-dailyweekly-schedule)
21. [AI-Proof Strategy](#21-ai-proof-strategy)
22. [Career Roadmap](#22-career-roadmap)
23. [Learning Strategy](#23-learning-strategy)
24. [Final Section — The Edge](#24-final-section--the-edge)

---

# 1. FOUNDATION PHASE

## 🧱 What to Learn First (Before Everything Else)

Before touching PySpark or Databricks, your foundation must be bulletproof. The biggest failure pattern for freshers is jumping to advanced tools without understanding why they exist.

### The Mental Model First
Data Engineering is fundamentally about **moving, transforming, and storing data reliably at scale**. Every tool you learn (Kafka, Spark, Airflow) exists to solve one of these three problems.

Ask yourself before every new tool: *What problem does this solve? Why did engineers need to build this?*

### Core Foundation Topics (Week 1–4)

**1. Understand the Data Ecosystem**
- What is structured, semi-structured, and unstructured data?
- What is a data pipeline?
- What is ETL (Extract, Transform, Load) vs ELT?
- What is batch processing vs stream processing?
- What is a data warehouse vs data lake vs data lakehouse?
- What is OLTP vs OLAP?
- Understand: Databases → Data Warehouses → Data Lakes → Lakehouses (evolution)

**2. Computer Science Fundamentals (Don't Skip)**
- How computers store data (bytes, files, memory)
- What is a process vs thread?
- What is a distributed system?
- What is latency vs throughput?
- What is serialization? (JSON, CSV, Parquet, Avro, ORC)
- What is compression? Why does it matter in data engineering?
- What is fault tolerance and why pipelines need it?

**3. File Formats — Deeply Understand These**

| Format | Type | Best For | Compression | Columnar? |
|--------|------|----------|-------------|-----------|
| CSV | Text | Small datasets, portability | No | No |
| JSON | Text | APIs, semi-structured | No | No |
| Parquet | Binary | Analytics, Spark, cloud | Yes | Yes |
| Avro | Binary | Streaming, Kafka | Yes | No |
| ORC | Binary | Hive, Hadoop | Yes | Yes |
| Delta | Binary | Lakehouse (Databricks) | Yes | Yes |

> **Rule:** Always use Parquet or Delta for analytical workloads. CSV is for data exchange only.

**4. Networking Basics**
- What is an API? REST vs GraphQL
- What are HTTP status codes (200, 400, 401, 500)?
- What is pagination in APIs?
- What is rate limiting?
- What is authentication (API keys, OAuth, Bearer tokens)?

---

## ⚠️ Common Mistakes Beginners Make

1. **Tutorial Hell** — Watching 50 YouTube videos without building anything. Stop after 20% of theory; build immediately.
2. **Tool Obsession** — Learning every tool without understanding the underlying problem. Tools change; concepts don't.
3. **Skipping SQL** — Most Data Engineering interviews are 40% SQL. Freshers who skip deep SQL always lose.
4. **Ignoring fundamentals** — Not knowing why Parquet is better than CSV, or what lazy evaluation means.
5. **No GitHub presence** — Studying for months without public code is invisible to recruiters.
6. **Learning in isolation** — Not reading engineering blogs (Uber, Netflix, Airbnb) about real production systems.
7. **Skipping Linux** — Shell scripting is used daily in production pipelines.
8. **Skipping logging and monitoring** — Production pipelines without observability are disaster waiting to happen.

---

## 🏗️ How to Build Strong Fundamentals

**The 3-Layer Understanding Method:**
- **Layer 1 — Concept:** What is it and why does it exist?
- **Layer 2 — Hands-on:** Build it yourself, break it, fix it.
- **Layer 3 — Production:** How is this used at scale in real companies?

**Resources for Foundation:**
- "Fundamentals of Data Engineering" by Joe Reis & Matt Housley (read chapters 1–3 first)
- "Designing Data-Intensive Applications" by Martin Kleppmann (the Data Engineering bible)
- Google's "Site Reliability Engineering" (free online) — for production thinking
- Read engineering blogs: Netflix Tech Blog, Uber Engineering, Airbnb Engineering

---

# 2. PYTHON FOR DATA ENGINEERING

## 🐍 Core Python Topics (Must Master First)

### Data Types and Structures
```python
# Know these deeply — interviews test edge cases
lists = [1, 2, 3]           # mutable, ordered
tuples = (1, 2, 3)          # immutable, ordered — use for fixed data
sets = {1, 2, 3}            # unordered, unique — fast lookup
dicts = {"key": "value"}    # key-value — backbone of JSON/API data

# List comprehensions — used constantly in DE
squared = [x**2 for x in range(10) if x % 2 == 0]

# Dict comprehensions
inverted = {v: k for k, v in my_dict.items()}

# Generator expressions — memory efficient for large data
gen = (x**2 for x in range(1_000_000))  # doesn't load all into memory
```

### Functions — Go Beyond Basics
```python
# *args and **kwargs — used in dynamic pipeline configs
def run_pipeline(*args, **kwargs):
    for step in args:
        step(**kwargs)

# Decorators — used for logging, retries, timing
import functools

def retry(max_attempts=3):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            for attempt in range(max_attempts):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    if attempt == max_attempts - 1:
                        raise
                    print(f"Attempt {attempt+1} failed: {e}")
        return wrapper
    return decorator

@retry(max_attempts=3)
def fetch_data_from_api(url):
    # Your API call here
    pass

# Lambda functions
transform = lambda x: x.strip().lower()

# Map, Filter, Reduce
cleaned = list(map(transform, raw_strings))
filtered = list(filter(lambda x: x != "", cleaned))
```

### Object-Oriented Python for DE
```python
# Design pipeline components as classes
from abc import ABC, abstractmethod
from dataclasses import dataclass
from typing import Optional, List, Dict, Any

@dataclass
class PipelineConfig:
    source: str
    destination: str
    batch_size: int = 1000
    retry_count: int = 3
    tags: Optional[List[str]] = None

class DataConnector(ABC):
    """Base class for all data connectors"""
    
    def __init__(self, config: PipelineConfig):
        self.config = config
        self.logger = self._setup_logger()
    
    @abstractmethod
    def extract(self) -> Any:
        pass
    
    @abstractmethod
    def validate(self, data: Any) -> bool:
        pass
    
    def _setup_logger(self):
        import logging
        return logging.getLogger(self.__class__.__name__)

class S3Connector(DataConnector):
    def extract(self):
        # S3-specific implementation
        pass
    
    def validate(self, data):
        return data is not None and len(data) > 0
```

---

## 🚀 Advanced Python Topics for Production

### Exception Handling — Production Grade
```python
import logging
from typing import Optional

# Custom exceptions for your pipeline
class PipelineException(Exception):
    """Base exception for all pipeline errors"""
    pass

class DataValidationError(PipelineException):
    """Raised when data fails validation checks"""
    def __init__(self, message: str, record_count: int = 0):
        super().__init__(message)
        self.record_count = record_count

class SourceConnectionError(PipelineException):
    """Raised when unable to connect to data source"""
    pass

class SchemaEvolutionError(PipelineException):
    """Raised when source schema doesn't match expected"""
    pass

# Production exception handling pattern
def extract_with_context(source_config: dict) -> Optional[list]:
    logger = logging.getLogger(__name__)
    
    try:
        data = connect_and_fetch(source_config)
        if not data:
            raise DataValidationError("Empty dataset returned", record_count=0)
        return data
    
    except ConnectionRefusedError as e:
        logger.error(f"Cannot connect to source: {source_config['host']}", exc_info=True)
        raise SourceConnectionError(f"Connection failed: {e}") from e
    
    except KeyError as e:
        logger.error(f"Schema mismatch — missing field: {e}")
        raise SchemaEvolutionError(f"Missing expected field: {e}") from e
    
    except Exception as e:
        logger.critical(f"Unexpected error in extraction", exc_info=True)
        raise PipelineException(f"Extraction failed: {e}") from e
    
    finally:
        # Always clean up connections
        logger.info("Extraction attempt completed (success or failure)")
```

### Logging — The Right Way
```python
import logging
import json
from datetime import datetime

# Structured logging — searchable in production log systems
class JSONFormatter(logging.Formatter):
    def format(self, record):
        log_entry = {
            "timestamp": datetime.utcnow().isoformat(),
            "level": record.levelname,
            "logger": record.name,
            "message": record.getMessage(),
            "pipeline": getattr(record, 'pipeline', 'unknown'),
            "run_id": getattr(record, 'run_id', 'unknown')
        }
        if record.exc_info:
            log_entry["exception"] = self.formatException(record.exc_info)
        return json.dumps(log_entry)

def setup_pipeline_logger(name: str, log_level: str = "INFO") -> logging.Logger:
    logger = logging.getLogger(name)
    logger.setLevel(getattr(logging, log_level))
    
    # Console handler
    console_handler = logging.StreamHandler()
    console_handler.setFormatter(JSONFormatter())
    
    # File handler
    file_handler = logging.FileHandler(f"logs/{name}.log")
    file_handler.setFormatter(JSONFormatter())
    
    logger.addHandler(console_handler)
    logger.addHandler(file_handler)
    
    return logger
```

### File Handling for Large Data
```python
import csv
import json
import gzip
from pathlib import Path
from typing import Generator, Iterator

# Never load large files entirely into memory
def read_large_csv_in_chunks(filepath: str, chunk_size: int = 10_000) -> Generator:
    """Memory-efficient CSV reading using generators"""
    with open(filepath, 'r', encoding='utf-8') as f:
        reader = csv.DictReader(f)
        chunk = []
        for row in reader:
            chunk.append(row)
            if len(chunk) >= chunk_size:
                yield chunk
                chunk = []
        if chunk:  # yield remaining records
            yield chunk

# Reading compressed files (common in DE)
def read_gzipped_json(filepath: str) -> Iterator[dict]:
    """Read gzipped JSON lines file (JSONL format)"""
    with gzip.open(filepath, 'rt', encoding='utf-8') as f:
        for line in f:
            yield json.loads(line.strip())

# Context managers for resource cleanup
class DataFileManager:
    def __init__(self, filepath: str, mode: str = 'r'):
        self.filepath = Path(filepath)
        self.mode = mode
        self.file = None
    
    def __enter__(self):
        self.file = open(self.filepath, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()
        return False  # Don't suppress exceptions

# Usage
for chunk in read_large_csv_in_chunks("huge_file.csv", chunk_size=5000):
    process_chunk(chunk)  # Process 5000 rows at a time
```

### Multithreading and Multiprocessing
```python
import concurrent.futures
import threading
from typing import List, Callable

# I/O-bound tasks (API calls, file reads) → Threading
def fetch_from_multiple_apis(urls: List[str], max_workers: int = 10) -> List[dict]:
    """Fetch data from multiple APIs concurrently"""
    results = []
    lock = threading.Lock()
    
    def fetch_single(url: str) -> dict:
        import requests
        response = requests.get(url, timeout=30)
        response.raise_for_status()
        return response.json()
    
    with concurrent.futures.ThreadPoolExecutor(max_workers=max_workers) as executor:
        future_to_url = {executor.submit(fetch_single, url): url for url in urls}
        
        for future in concurrent.futures.as_completed(future_to_url):
            url = future_to_url[future]
            try:
                data = future.result()
                with lock:
                    results.append(data)
            except Exception as e:
                print(f"Failed to fetch {url}: {e}")
    
    return results

# CPU-bound tasks (data transformation) → Multiprocessing
from multiprocessing import Pool, cpu_count

def transform_batch(batch: List[dict]) -> List[dict]:
    """CPU-intensive transformation on a batch"""
    return [transform_record(record) for record in batch]

def parallel_transform(data: List[dict], n_processes: int = None) -> List[dict]:
    """Use all CPU cores for transformation"""
    if n_processes is None:
        n_processes = cpu_count()
    
    batch_size = len(data) // n_processes
    batches = [data[i:i+batch_size] for i in range(0, len(data), batch_size)]
    
    with Pool(processes=n_processes) as pool:
        results = pool.map(transform_batch, batches)
    
    return [item for sublist in results for item in sublist]  # flatten
```

### APIs for Data Engineers
```python
import requests
import time
from typing import Generator, Optional

class APIClient:
    """Production-grade API client with rate limiting and pagination"""
    
    def __init__(self, base_url: str, api_key: str, rate_limit_per_minute: int = 60):
        self.base_url = base_url
        self.session = requests.Session()
        self.session.headers.update({
            "Authorization": f"Bearer {api_key}",
            "Content-Type": "application/json",
            "Accept": "application/json"
        })
        self.rate_limit_per_minute = rate_limit_per_minute
        self._request_times = []
    
    def _rate_limit(self):
        """Enforce rate limiting"""
        now = time.time()
        # Remove requests older than 1 minute
        self._request_times = [t for t in self._request_times if now - t < 60]
        
        if len(self._request_times) >= self.rate_limit_per_minute:
            sleep_time = 60 - (now - self._request_times[0])
            if sleep_time > 0:
                time.sleep(sleep_time)
        
        self._request_times.append(time.time())
    
    def get(self, endpoint: str, params: dict = None) -> dict:
        self._rate_limit()
        url = f"{self.base_url}/{endpoint}"
        response = self.session.get(url, params=params, timeout=30)
        response.raise_for_status()
        return response.json()
    
    def paginate(self, endpoint: str, page_param: str = "page", 
                 limit_param: str = "limit", limit: int = 100) -> Generator:
        """Auto-paginate through all results"""
        page = 1
        while True:
            params = {page_param: page, limit_param: limit}
            data = self.get(endpoint, params=params)
            
            results = data.get("results", data.get("data", []))
            if not results:
                break
            
            yield from results
            
            # Handle different pagination patterns
            if "next" in data and data["next"] is None:
                break
            if len(results) < limit:
                break
            
            page += 1
```

---

## 📦 Essential Python Libraries for Data Engineering

| Library | Use Case | Priority |
|---------|----------|----------|
| `pandas` | Data manipulation, EDA | Critical |
| `polars` | Fast dataframes (Rust-based, 10x faster) | High |
| `requests` / `httpx` | HTTP APIs | Critical |
| `pydantic` | Data validation, schemas | High |
| `great_expectations` | Data quality testing | High |
| `boto3` | AWS SDK | High |
| `azure-storage-blob` | Azure Blob storage | High |
| `google-cloud-storage` | GCS | Medium |
| `sqlalchemy` | Database ORM | High |
| `psycopg2` | PostgreSQL | High |
| `pyarrow` | Parquet read/write | Critical |
| `fsspec` | Filesystem abstraction | High |
| `tenacity` | Retry logic | High |
| `pyyaml` | Config files | High |
| `python-dotenv` | Environment variables | Critical |
| `typer` / `click` | CLI tools | Medium |
| `pytest` | Testing | Critical |
| `black` / `ruff` | Code formatting | High |

---

## 🏆 Best Python Projects for Data Engineers

1. **API Data Pipeline** — Fetch data from a public API (OpenWeather, CoinGecko), transform it, store in PostgreSQL
2. **File Processing Engine** — Process 10GB CSV files in chunks, apply transformations, output Parquet
3. **Data Quality Framework** — Build a reusable validation library using Pydantic + Great Expectations
4. **Multi-threaded Web Scraper** — Scrape job listings, store structured data, handle pagination
5. **Config-driven ETL Framework** — YAML-configurable pipeline that any non-engineer can use

---

# 3. SQL ROADMAP

## 🎯 The SQL Learning Pyramid

```
                    [Expert]
              Window Functions + CTEs
           Query Optimization + Indexing
        Partitioning + Stored Procedures
     Advanced JOINs + Subqueries + Set Ops
  Aggregations + GROUP BY + HAVING + CASE
Basic SELECT, WHERE, ORDER BY, INSERT, UPDATE
```

## Beginner SQL (Week 1–2)

```sql
-- 1. Basic SELECT and filtering
SELECT 
    customer_id,
    first_name,
    last_name,
    email,
    UPPER(city) as city_upper,
    DATEDIFF(NOW(), created_at) as days_since_signup
FROM customers
WHERE 
    is_active = TRUE 
    AND country = 'India'
    AND created_at >= '2024-01-01'
ORDER BY created_at DESC
LIMIT 100;

-- 2. Aggregations
SELECT 
    DATE_TRUNC('month', order_date) as month,
    COUNT(*) as total_orders,
    COUNT(DISTINCT customer_id) as unique_customers,
    SUM(order_value) as total_revenue,
    AVG(order_value) as avg_order_value,
    MAX(order_value) as max_order,
    MIN(order_value) as min_order
FROM orders
GROUP BY 1
HAVING SUM(order_value) > 10000  -- HAVING filters AFTER aggregation
ORDER BY 1;

-- 3. JOINs — understand the difference deeply
-- INNER JOIN: only matching rows from both tables
SELECT c.customer_id, c.name, o.order_id, o.amount
FROM customers c
INNER JOIN orders o ON c.customer_id = o.customer_id;

-- LEFT JOIN: all rows from left, matched rows from right
SELECT c.customer_id, c.name, COUNT(o.order_id) as order_count
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.name;

-- Find customers with NO orders
SELECT c.customer_id, c.name
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;  -- Key pattern for "no match"
```

## Intermediate SQL (Week 3–4)

```sql
-- 4. Subqueries
-- Scalar subquery in SELECT
SELECT 
    product_id,
    product_name,
    price,
    (SELECT AVG(price) FROM products) as avg_price,
    price - (SELECT AVG(price) FROM products) as price_vs_avg
FROM products;

-- Subquery in WHERE (semi-join pattern)
SELECT customer_id, name
FROM customers
WHERE customer_id IN (
    SELECT DISTINCT customer_id 
    FROM orders 
    WHERE order_date >= '2024-01-01'
);

-- Correlated subquery (slow but important to know)
SELECT 
    o.order_id,
    o.customer_id,
    o.order_value,
    (SELECT AVG(o2.order_value) 
     FROM orders o2 
     WHERE o2.customer_id = o.customer_id) as customer_avg
FROM orders o;

-- 5. CTEs (Common Table Expressions) — cleaner than subqueries
WITH 
monthly_revenue AS (
    SELECT 
        DATE_TRUNC('month', order_date) as month,
        SUM(order_value) as revenue
    FROM orders
    GROUP BY 1
),
revenue_with_growth AS (
    SELECT 
        month,
        revenue,
        LAG(revenue) OVER (ORDER BY month) as prev_revenue,
        ROUND(
            (revenue - LAG(revenue) OVER (ORDER BY month)) / 
            NULLIF(LAG(revenue) OVER (ORDER BY month), 0) * 100, 2
        ) as growth_pct
    FROM monthly_revenue
)
SELECT * FROM revenue_with_growth
WHERE month >= '2024-01-01';

-- Recursive CTE — for hierarchical data (org charts, categories)
WITH RECURSIVE employee_hierarchy AS (
    -- Base case: CEO (no manager)
    SELECT employee_id, name, manager_id, 0 as level, name as path
    FROM employees
    WHERE manager_id IS NULL
    
    UNION ALL
    
    -- Recursive case: find each employee's reports
    SELECT e.employee_id, e.name, e.manager_id, h.level + 1, 
           h.path || ' > ' || e.name
    FROM employees e
    INNER JOIN employee_hierarchy h ON e.manager_id = h.employee_id
)
SELECT * FROM employee_hierarchy
ORDER BY path;
```

## Advanced SQL — Window Functions (Most Important for Interviews)

```sql
-- Window functions: ROW_NUMBER, RANK, DENSE_RANK, NTILE
SELECT 
    customer_id,
    order_date,
    order_value,
    
    -- Ranking within each customer's orders
    ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY order_value DESC) as order_rank,
    RANK() OVER (PARTITION BY customer_id ORDER BY order_value DESC) as rank_with_gaps,
    DENSE_RANK() OVER (PARTITION BY customer_id ORDER BY order_value DESC) as dense_rank,
    
    -- Percentile bucketing
    NTILE(4) OVER (ORDER BY order_value) as quartile
FROM orders;

-- Running totals and moving averages
SELECT 
    order_date,
    daily_revenue,
    SUM(daily_revenue) OVER (ORDER BY order_date) as running_total,
    AVG(daily_revenue) OVER (
        ORDER BY order_date 
        ROWS BETWEEN 6 PRECEDING AND CURRENT ROW
    ) as rolling_7day_avg,
    
    -- Lead/Lag for time-series comparisons
    LAG(daily_revenue, 1) OVER (ORDER BY order_date) as yesterday_revenue,
    LEAD(daily_revenue, 1) OVER (ORDER BY order_date) as tomorrow_revenue
FROM daily_sales;

-- Top-N per group (extremely common interview question)
-- "Get the top 3 products by revenue for each category"
WITH ranked_products AS (
    SELECT 
        category,
        product_name,
        revenue,
        ROW_NUMBER() OVER (PARTITION BY category ORDER BY revenue DESC) as rn
    FROM product_sales
)
SELECT category, product_name, revenue
FROM ranked_products
WHERE rn <= 3;

-- Gap and Island analysis (advanced — shows SQL mastery)
-- Find consecutive date ranges
WITH numbered AS (
    SELECT 
        user_id,
        login_date,
        ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY login_date) as rn,
        login_date - INTERVAL (ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY login_date) - 1) DAY as grp
    FROM user_logins
)
SELECT 
    user_id,
    MIN(login_date) as streak_start,
    MAX(login_date) as streak_end,
    COUNT(*) as streak_length
FROM numbered
GROUP BY user_id, grp
ORDER BY user_id, streak_start;
```

## Query Optimization

```sql
-- 1. Use EXPLAIN/EXPLAIN ANALYZE to understand query plans
EXPLAIN ANALYZE
SELECT * FROM orders WHERE customer_id = 12345;

-- 2. Avoid SELECT *
-- Bad: SELECT * FROM orders
-- Good: SELECT order_id, customer_id, order_value, created_at FROM orders

-- 3. Index properly
-- Single column index
CREATE INDEX idx_orders_customer_id ON orders(customer_id);

-- Composite index (order matters — most selective column first)
CREATE INDEX idx_orders_customer_date ON orders(customer_id, order_date);

-- Covering index (includes all columns in query — no table lookup needed)
CREATE INDEX idx_orders_covering ON orders(customer_id, order_date) 
INCLUDE (order_value, status);

-- 4. Partitioning for large tables
CREATE TABLE orders_2024 PARTITION OF orders
FOR VALUES FROM ('2024-01-01') TO ('2025-01-01');

-- 5. Avoid functions on indexed columns (prevents index use)
-- Bad:
WHERE YEAR(order_date) = 2024
-- Good:
WHERE order_date >= '2024-01-01' AND order_date < '2025-01-01'
```

## 📅 Daily SQL Practice Plan

| Day | Focus | Source |
|-----|-------|--------|
| Mon | 2 Easy LeetCode SQL problems | leetcode.com/study-plan/sql-50 |
| Tue | 1 Medium + window function practice | |
| Wed | 1 Business scenario query (write from scratch) | |
| Thu | Query optimization practice (EXPLAIN on your queries) | |
| Fri | 1 Hard problem or system design SQL question | |
| Sat | Mock interview: 3 SQL questions in 45 minutes | |
| Sun | Review week's mistakes, rewrite all failed queries | |

## 📊 200+ SQL Problem Progression Strategy

**Level 1 (Problems 1–50): Fundamentals**
- All basic SELECT, WHERE, GROUP BY, HAVING
- All JOIN types with real-world scenarios
- Basic aggregation and filtering
- Platform: LeetCode Easy SQL, HackerRank SQL Basic

**Level 2 (Problems 51–120): Intermediate**
- Subqueries (scalar, correlated, IN/EXISTS)
- CTEs and recursive CTEs
- All window functions (ROW_NUMBER, RANK, LEAD/LAG)
- Date/time manipulation
- String functions
- Platform: LeetCode Medium SQL, Mode Analytics

**Level 3 (Problems 121–180): Advanced**
- Complex window function combinations
- Gap and Island problems
- Pivot/Unpivot patterns
- Performance optimization problems
- Platform: LeetCode Hard SQL, DataLemur

**Level 4 (Problems 181–200+): Expert**
- System design SQL (partitioning strategies)
- Large dataset handling
- Custom business logic (retention, cohort analysis)
- Write stored procedures
- Platform: Real company SQL rounds (Glassdoor), StrataScratch

## Top SQL Interview Patterns

```sql
-- Pattern 1: Nth highest/lowest value
SELECT MAX(salary) as third_highest
FROM employees
WHERE salary < (
    SELECT MAX(salary) FROM employees WHERE salary < (
        SELECT MAX(salary) FROM employees
    )
);
-- Better with window functions:
SELECT salary FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) as rk 
    FROM employees
) WHERE rk = 3;

-- Pattern 2: Duplicate detection
SELECT email, COUNT(*) as count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;

-- Pattern 3: Self-join for comparisons
SELECT a.employee_id, a.name, a.salary
FROM employees a
JOIN employees b ON a.manager_id = b.employee_id
WHERE a.salary > b.salary;

-- Pattern 4: Rolling/cohort retention
WITH cohorts AS (
    SELECT user_id, DATE_TRUNC('month', first_purchase) as cohort_month
    FROM (
        SELECT user_id, MIN(purchase_date) as first_purchase 
        FROM purchases GROUP BY user_id
    ) x
)
SELECT 
    c.cohort_month,
    DATEDIFF('month', c.cohort_month, DATE_TRUNC('month', p.purchase_date)) as month_number,
    COUNT(DISTINCT p.user_id) as retained_users
FROM cohorts c
JOIN purchases p ON c.user_id = p.user_id
GROUP BY 1, 2
ORDER BY 1, 2;
```

---

# 4. LINUX + GIT ROADMAP

## 🐧 Linux Commands — From Essential to Mastery

### File System Commands
```bash
# Navigation
pwd                         # Print working directory
ls -la                      # List all files with permissions
cd /path/to/dir             # Change directory
cd ..                       # Go up one level
cd ~                        # Go home directory

# File operations
cp -r source/ destination/  # Copy recursively
mv file.csv /new/path/      # Move/rename
rm -rf folder/              # Remove recursively (careful!)
find / -name "*.parquet" 2>/dev/null  # Find files

# Viewing files
cat file.csv                # Print entire file
head -n 100 large_file.csv  # First 100 lines
tail -f pipeline.log        # Follow log in real-time (essential!)
less large_file.csv         # Page through file
wc -l file.csv              # Count lines
```

### Text Processing (Critical for DE)
```bash
# grep — search patterns
grep "ERROR" pipeline.log           # Find errors
grep -i "warning" pipeline.log      # Case insensitive
grep -n "exception" pipeline.log    # Show line numbers
grep -r "def transform" src/        # Recursive search

# awk — field processing
awk -F',' '{print $1, $3}' data.csv        # Print columns 1 and 3
awk -F',' 'NR > 1 {sum += $4} END {print sum}' data.csv  # Sum column 4

# sed — stream editor
sed 's/old_value/new_value/g' file.txt     # Replace all occurrences
sed '/^#/d' config.txt                      # Delete comment lines
sed -n '100,200p' large_file.csv            # Print lines 100-200

# sort, uniq
sort -t',' -k3 -n data.csv          # Sort by 3rd column numerically
sort data.csv | uniq -c | sort -rn  # Count unique values

# cut, paste
cut -d',' -f1,3,5 data.csv          # Extract specific columns

# Pipeline composition (the Unix philosophy)
cat access.log | grep "POST" | awk '{print $7}' | sort | uniq -c | sort -rn | head -20
```

### System Monitoring (Production Essential)
```bash
top                         # Process monitor (press 'q' to quit)
htop                        # Better process monitor
ps aux | grep python        # Find Python processes
df -h                       # Disk space usage
du -sh /path/to/dir         # Size of directory
free -h                     # Memory usage
vmstat 1                    # CPU/memory stats every second
iostat                      # I/O statistics
netstat -tulpn              # Network connections
lsof -i :8080               # What's on port 8080?
```

### Process Management
```bash
# Run in background
python pipeline.py &
nohup python pipeline.py > pipeline.log 2>&1 &  # Persists after logout

# Job control
jobs                        # List background jobs
fg %1                       # Bring job 1 to foreground
kill -9 PID                 # Force kill process

# Screen/tmux (essential for long-running pipelines)
screen -S pipeline_run      # Start named screen session
# Ctrl+A, D to detach
screen -r pipeline_run      # Reattach
```

### Shell Scripting for Data Engineers
```bash
#!/bin/bash
# Production-grade pipeline orchestration script
set -euo pipefail  # Exit on error, undefined vars, pipe failures

# Configuration
PIPELINE_NAME="daily_sales_etl"
LOG_DIR="/var/log/pipelines"
DATE=$(date +%Y-%m-%d)
LOG_FILE="${LOG_DIR}/${PIPELINE_NAME}_${DATE}.log"

# Logging function
log() {
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" | tee -a "$LOG_FILE"
}

# Error handling
error_exit() {
    log "ERROR: $1"
    # Send alert (email, Slack, PagerDuty)
    curl -X POST "$SLACK_WEBHOOK" -d "{\"text\": \"Pipeline FAILED: $PIPELINE_NAME\"}"
    exit 1
}

# Health check function
check_disk_space() {
    local required_gb=$1
    local available_gb=$(df -BG /data | tail -1 | awk '{print $4}' | sed 's/G//')
    if [ "$available_gb" -lt "$required_gb" ]; then
        error_exit "Insufficient disk space: ${available_gb}GB available, ${required_gb}GB required"
    fi
}

# Main pipeline
main() {
    log "Starting ${PIPELINE_NAME} for ${DATE}"
    
    check_disk_space 50  # Need at least 50GB
    
    log "Step 1: Extracting data..."
    python extract.py --date "$DATE" || error_exit "Extraction failed"
    
    log "Step 2: Transforming data..."
    python transform.py --date "$DATE" || error_exit "Transformation failed"
    
    log "Step 3: Loading to warehouse..."
    python load.py --date "$DATE" || error_exit "Loading failed"
    
    log "Pipeline completed successfully"
}

main "$@"
```

### Cron Jobs for Scheduling
```bash
# Crontab syntax: MIN HOUR DOM MON DOW COMMAND
# Edit crontab
crontab -e

# Examples:
# Run daily at 2 AM
0 2 * * * /home/user/pipelines/daily_etl.sh >> /var/log/cron_etl.log 2>&1

# Run every 15 minutes
*/15 * * * * /home/user/pipelines/check_kafka_lag.sh

# Run every weekday at 6 AM
0 6 * * 1-5 /home/user/pipelines/business_report.sh

# Run first day of every month
0 0 1 * * /home/user/pipelines/monthly_rollup.sh

# List current crontabs
crontab -l
```

---

## 🌿 Git Workflow — Professional Standard

### Daily Git Commands
```bash
# Setup (once)
git config --global user.name "Your Name"
git config --global user.email "you@email.com"
git config --global core.editor vim

# Branching strategy (Git Flow)
git checkout -b feature/add-kafka-consumer    # Create feature branch
git add -p                                    # Stage changes interactively
git commit -m "feat: add kafka consumer for orders topic"  # Conventional commits
git push origin feature/add-kafka-consumer

# Conventional commit message format:
# feat: new feature
# fix: bug fix
# docs: documentation
# refactor: code restructure
# test: add tests
# chore: maintenance

# Rebase (keep linear history)
git fetch origin
git rebase origin/main

# Squash commits before PR
git rebase -i HEAD~3  # Squash last 3 commits

# Stash work in progress
git stash push -m "WIP: kafka consumer"
git stash list
git stash pop
```

### `.gitignore` Template for DE Projects
```
# Python
__pycache__/
*.py[cod]
*.egg-info/
.venv/
env/
venv/
.env
.env.*

# Data files — never commit large data
*.csv
*.parquet
*.json
data/raw/
data/processed/

# Logs
logs/
*.log

# Credentials — CRITICAL
*.pem
*.key
credentials.json
config/secrets/

# IDE
.idea/
.vscode/
*.swp

# OS
.DS_Store
Thumbs.db

# Notebooks (checkpoint files)
.ipynb_checkpoints/

# Terraform
*.tfstate
*.tfstate.backup
.terraform/
```

### GitHub Best Practices
- **Branch protection:** Require PR reviews before merging to main
- **PR templates:** Create `.github/pull_request_template.md`
- **Issue templates:** Create bug report and feature request templates
- **GitHub Actions:** Automate testing, linting, and deployment
- **Releases:** Tag releases with semantic versioning (v1.2.3)

### Basic CI/CD with GitHub Actions
```yaml
# .github/workflows/pipeline_tests.yml
name: Data Pipeline CI

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.11'
    
    - name: Install dependencies
      run: |
        pip install -r requirements.txt
        pip install pytest pytest-cov black ruff
    
    - name: Lint with ruff
      run: ruff check src/
    
    - name: Format check with black
      run: black --check src/
    
    - name: Run tests
      run: pytest tests/ -v --cov=src --cov-report=xml
    
    - name: Data quality checks
      run: python scripts/validate_schemas.py
```

---

# 5. DATA WAREHOUSING

## 🏛️ Core Concepts — Know These Cold

### OLTP vs OLAP

| Aspect | OLTP | OLAP |
|--------|------|------|
| Purpose | Transaction processing | Analytics |
| Operations | INSERT, UPDATE, DELETE | SELECT (heavy reads) |
| Schema | Normalized (3NF) | Denormalized (star/snowflake) |
| Data volume | GB | TB–PB |
| Query type | Simple, fast | Complex, aggregations |
| Examples | MySQL, PostgreSQL | Snowflake, BigQuery, Redshift |
| Users | Applications | Analysts, BI tools |

### Dimensional Modeling — The Core of Data Warehousing

**Fact Tables:** Store measurable events (sales, clicks, transactions)
- Contain foreign keys to dimension tables
- Contain numeric measures (amount, quantity, duration)
- Grow continuously (additive over time)

**Dimension Tables:** Store descriptive attributes (who, what, where, when)
- Products, Customers, Dates, Geography
- Change slowly or not at all
- Denormalized (flat) for query performance

### Star Schema
```
                    [Date Dimension]
                          |
[Customer Dimension] — [FACT: Sales] — [Product Dimension]
                          |
                    [Store Dimension]
```

```sql
-- Fact table design
CREATE TABLE fact_sales (
    sale_id         BIGINT PRIMARY KEY,
    date_key        INT REFERENCES dim_date(date_key),
    customer_key    INT REFERENCES dim_customer(customer_key),
    product_key     INT REFERENCES dim_product(product_key),
    store_key       INT REFERENCES dim_store(store_key),
    
    -- Measures
    quantity        INT NOT NULL,
    unit_price      DECIMAL(10,2) NOT NULL,
    discount_amount DECIMAL(10,2) DEFAULT 0,
    total_amount    DECIMAL(10,2) NOT NULL,
    cost_amount     DECIMAL(10,2) NOT NULL,
    profit_amount   DECIMAL(10,2) NOT NULL
);

-- Date dimension — pre-populate for years in advance
CREATE TABLE dim_date (
    date_key        INT PRIMARY KEY,  -- YYYYMMDD format
    full_date       DATE NOT NULL,
    year            INT,
    quarter         INT,
    month           INT,
    month_name      VARCHAR(10),
    week            INT,
    day_of_week     INT,
    day_name        VARCHAR(10),
    is_weekend      BOOLEAN,
    is_holiday      BOOLEAN,
    fiscal_year     INT,
    fiscal_quarter  INT
);
```

### Slowly Changing Dimensions (SCD)

**SCD Type 0:** Never changes (birth date)
**SCD Type 1:** Overwrite old value (no history kept)
**SCD Type 2:** Add new row with validity dates (full history) — Most Common!
**SCD Type 3:** Add new column for previous value (limited history)
**SCD Type 4:** Separate history table
**SCD Type 6:** Combination of 1+2+3

```sql
-- SCD Type 2 Customer Dimension
CREATE TABLE dim_customer (
    customer_key        BIGINT PRIMARY KEY AUTO_INCREMENT,
    customer_id         INT NOT NULL,  -- Natural/business key
    first_name          VARCHAR(100),
    last_name           VARCHAR(100),
    email               VARCHAR(200),
    city                VARCHAR(100),
    country             VARCHAR(100),
    customer_segment    VARCHAR(50),
    
    -- SCD Type 2 columns
    effective_date      DATE NOT NULL,
    expiry_date         DATE,           -- NULL means current record
    is_current          BOOLEAN DEFAULT TRUE,
    version             INT DEFAULT 1
);

-- When customer moves to new city:
-- 1. UPDATE old record: expiry_date = TODAY, is_current = FALSE
-- 2. INSERT new record with new city, effective_date = TODAY, is_current = TRUE
```

### ETL vs ELT

| Aspect | ETL | ELT |
|--------|-----|-----|
| Transform | Before loading | After loading |
| Where | External ETL tool | Inside the warehouse |
| Cost | Compute is separate | Warehouse compute |
| Flexibility | Schema-on-write | Schema-on-read |
| Best for | Legacy systems, sensitive data | Cloud warehouses (Snowflake, BigQuery) |
| Modern choice? | Less common | Preferred (DBT-based ELT) |

### Incremental Loading Strategies

```python
# Strategy 1: Timestamp-based incremental load
def get_incremental_data(conn, table: str, last_watermark: datetime) -> pd.DataFrame:
    query = f"""
    SELECT * FROM {table}
    WHERE updated_at > '{last_watermark.isoformat()}'
    ORDER BY updated_at
    """
    return pd.read_sql(query, conn)

# Strategy 2: CDC (Change Data Capture)
# Reads database transaction logs (binlog in MySQL, WAL in PostgreSQL)
# Tools: Debezium, AWS DMS, Airbyte

# Strategy 3: Hash-based change detection
def detect_changed_rows(source_df, target_df, key_cols, compare_cols):
    # Create hash of all compare columns
    source_df['row_hash'] = source_df[compare_cols].apply(
        lambda row: hashlib.md5(str(row.values).encode()).hexdigest(), axis=1
    )
    # Compare with existing hashes in target
    # Only load rows where hash changed
    pass

# Watermark management
def update_watermark(table: str, new_watermark: datetime, meta_db):
    meta_db.execute("""
        INSERT INTO pipeline_watermarks (table_name, last_run, watermark_value)
        VALUES (%s, NOW(), %s)
        ON CONFLICT (table_name) DO UPDATE
        SET last_run = NOW(), watermark_value = %s
    """, (table, new_watermark, new_watermark))
```

---

# 6. PYSPARK ROADMAP

## ⚡ Spark Architecture — Understand Deeply

```
[Driver Program (SparkContext)]
         |
    [Cluster Manager]  (YARN, Kubernetes, Standalone)
     /      |     \
[Executor] [Executor] [Executor]  (Workers)
  |    |     |    |     |    |
[Cache] [Task] [Cache] [Task] [Cache] [Task]
```

**Key concepts:**
- **Driver:** Orchestrates the job, creates DAG, schedules tasks
- **Executor:** Runs actual computation, stores data in memory/disk
- **Task:** Smallest unit of work, processes one partition
- **Stage:** Set of tasks with no shuffle between them
- **Job:** Complete Spark action (triggered by `.collect()`, `.write()`, etc.)

## RDD vs DataFrame vs Dataset

```python
from pyspark.sql import SparkSession
from pyspark.sql import functions as F
from pyspark.sql.types import *

spark = SparkSession.builder \
    .appName("DataEngineering") \
    .config("spark.sql.adaptive.enabled", "true") \
    .config("spark.sql.adaptive.coalescePartitions.enabled", "true") \
    .getOrCreate()

# RDD — low level, avoid in modern Spark
rdd = spark.sparkContext.parallelize([1, 2, 3, 4, 5])
result = rdd.filter(lambda x: x > 2).map(lambda x: x * 2).collect()

# DataFrame — use this (SQL-like, optimized by Catalyst)
df = spark.read.parquet("s3://bucket/data/")
```

## PySpark Transformations and Actions

```python
# ========= TRANSFORMATIONS (Lazy — don't execute until action) =========

# Select and rename
df = df.select(
    F.col("customer_id"),
    F.col("order_date"),
    F.col("order_value").alias("revenue"),
    F.upper(F.col("country")).alias("country_upper"),
    F.year(F.col("order_date")).alias("year"),
    F.month(F.col("order_date")).alias("month")
)

# Filter
df = df.filter(
    (F.col("revenue") > 100) & 
    (F.col("country").isin(["India", "US", "UK"])) &
    (F.col("order_date") >= "2024-01-01")
)

# GroupBy and aggregations
df_agg = df.groupBy("country", "year", "month").agg(
    F.count("*").alias("order_count"),
    F.countDistinct("customer_id").alias("unique_customers"),
    F.sum("revenue").alias("total_revenue"),
    F.avg("revenue").alias("avg_order_value"),
    F.percentile_approx("revenue", 0.5).alias("median_revenue"),
    F.stddev("revenue").alias("revenue_stddev")
)

# JOINs
df_enriched = df.join(
    dim_customer.select("customer_id", "segment", "country"),
    on="customer_id",
    how="left"
)

# Window functions
from pyspark.sql.window import Window

window_spec = Window.partitionBy("customer_id").orderBy("order_date")
rolling_window = Window.partitionBy("customer_id").orderBy("order_date").rowsBetween(-6, 0)

df = df.withColumn("order_rank", F.row_number().over(window_spec)) \
       .withColumn("prev_order_value", F.lag("revenue", 1).over(window_spec)) \
       .withColumn("rolling_7day_revenue", F.sum("revenue").over(rolling_window)) \
       .withColumn("running_total", F.sum("revenue").over(
           Window.partitionBy("customer_id").orderBy("order_date")
           .rowsBetween(Window.unboundedPreceding, Window.currentRow)
       ))

# UDFs (User-Defined Functions) — use sparingly, prefer built-ins
from pyspark.sql.types import StringType

@F.udf(returnType=StringType())
def classify_order_value(amount):
    if amount is None:
        return "unknown"
    elif amount < 100:
        return "low"
    elif amount < 1000:
        return "medium"
    else:
        return "high"

df = df.withColumn("order_tier", classify_order_value(F.col("revenue")))

# ========= ACTIONS (Trigger execution) =========
df.count()                          # Count rows
df.collect()                        # Collect to driver (careful with large data!)
df.take(10)                         # Take first N rows
df.show(20, truncate=False)         # Display in console
df.write.parquet("output/")         # Write to storage
```

## PySpark Optimization — This Separates Junior from Senior

```python
# 1. Broadcast joins (for small tables)
from pyspark.sql.functions import broadcast

# If dim_country is small (<10MB), broadcast it
df_joined = df_large.join(
    broadcast(df_small_lookup),  # Avoids shuffle entirely
    on="country_code"
)

# 2. Repartitioning — critical for performance
# Check current partitions
print(f"Partitions: {df.rdd.getNumPartitions()}")

# Repartition by a column (used before joins/groupbys)
df = df.repartition(200, "customer_id")

# Coalesce (reduce partitions without full shuffle)
df.coalesce(10).write.parquet("output/")  # Before writing small datasets

# 3. Caching and Persistence
df_reused = df.filter(F.col("country") == "India") \
              .join(df_products, "product_id")

df_reused.cache()  # Cache in memory (use when reusing multiple times)
df_reused.persist(StorageLevel.MEMORY_AND_DISK)  # Spill to disk if needed

df_reused.count()  # Triggers caching
# ... use df_reused multiple times ...
df_reused.unpersist()  # Free memory when done

# 4. Avoid data skew
# Check partition sizes
df.groupBy(F.spark_partition_id()).count().orderBy("count", ascending=False).show()

# Handle skew with salting
import random
salt_range = 10
df_skewed = df_skewed.withColumn("salt", (F.rand() * salt_range).cast("int"))
df_skewed = df_skewed.withColumn("salted_key", 
    F.concat(F.col("skewed_column"), F.lit("_"), F.col("salt")))

# 5. Adaptive Query Execution (Spark 3.x+)
spark.conf.set("spark.sql.adaptive.enabled", "true")
spark.conf.set("spark.sql.adaptive.skewJoin.enabled", "true")
spark.conf.set("spark.sql.adaptive.coalescePartitions.enabled", "true")

# 6. Predicate pushdown — filter before loading
spark.conf.set("spark.sql.parquet.filterPushdown", "true")
df = spark.read.parquet("s3://bucket/orders/") \
    .filter(F.col("year") == 2024)  # Pushes filter to Parquet reader
```

## Spark SQL
```python
# Register DataFrame as temp view
df.createOrReplaceTempView("orders")
dim_customer.createOrReplaceTempView("customers")

# Write SQL queries directly
result = spark.sql("""
    WITH monthly_summary AS (
        SELECT 
            c.segment,
            DATE_TRUNC('month', o.order_date) as month,
            SUM(o.revenue) as total_revenue,
            COUNT(DISTINCT o.customer_id) as unique_buyers
        FROM orders o
        JOIN customers c ON o.customer_id = c.customer_id
        WHERE o.order_date >= '2024-01-01'
        GROUP BY 1, 2
    )
    SELECT 
        segment,
        month,
        total_revenue,
        unique_buyers,
        SUM(total_revenue) OVER (PARTITION BY segment ORDER BY month) as cumulative_revenue,
        total_revenue / SUM(total_revenue) OVER (PARTITION BY month) as month_revenue_share
    FROM monthly_summary
    ORDER BY segment, month
""")
```

---

# 7. DATABRICKS ROADMAP

## 🧱 Databricks Architecture

Databricks is a unified analytics platform built on Apache Spark, with Delta Lake at its core.

**Key Components:**
- **Workspace:** Web UI for notebooks, jobs, clusters, data
- **Clusters:** Compute environments (All-Purpose vs Job clusters)
- **Notebooks:** Interactive development environment
- **Delta Lake:** ACID-compliant storage format
- **DBFS:** Databricks File System (abstraction over blob storage)
- **Unity Catalog:** Data governance and access control (modern)
- **Workflows:** Job orchestration within Databricks

## Delta Lake — The Core Innovation

```python
# Why Delta Lake?
# 1. ACID transactions on data lakes
# 2. Schema enforcement and evolution
# 3. Time travel (versioning)
# 4. UPSERT operations (MERGE)
# 5. Unified batch + streaming

# Writing Delta tables
df.write.format("delta") \
    .mode("overwrite") \
    .partitionBy("year", "month") \
    .option("mergeSchema", "true") \  # Allow schema evolution
    .save("/mnt/datalake/sales/silver/orders")

# Reading Delta tables
df = spark.read.format("delta").load("/mnt/datalake/sales/silver/orders")
# Or using SQL
spark.sql("CREATE TABLE orders USING DELTA LOCATION '/mnt/datalake/sales/silver/orders'")

# MERGE (UPSERT) — most powerful Delta feature
from delta.tables import DeltaTable

target_table = DeltaTable.forPath(spark, "/mnt/datalake/customers")

target_table.alias("target").merge(
    new_data.alias("source"),
    "target.customer_id = source.customer_id"
).whenMatchedUpdate(set={
    "email": "source.email",
    "city": "source.city",
    "updated_at": "source.updated_at"
}).whenNotMatchedInsert(values={
    "customer_id": "source.customer_id",
    "email": "source.email",
    "city": "source.city",
    "created_at": "source.created_at",
    "updated_at": "source.updated_at"
}).execute()

# Time Travel
# Read previous version
df_yesterday = spark.read.format("delta") \
    .option("versionAsOf", 5) \
    .load("/mnt/datalake/sales/orders")

# Read at specific timestamp
df_last_week = spark.read.format("delta") \
    .option("timestampAsOf", "2024-11-01") \
    .load("/mnt/datalake/sales/orders")

# View history
spark.sql("DESCRIBE HISTORY delta.`/mnt/datalake/sales/orders`").show()

# Restore to previous version
spark.sql("""
    RESTORE TABLE orders TO VERSION AS OF 10
""")

# Optimize and Z-Order (clustering)
spark.sql("""
    OPTIMIZE delta.`/mnt/datalake/sales/orders`
    ZORDER BY (customer_id, order_date)
""")

# Vacuum (remove old files)
spark.sql("""
    VACUUM delta.`/mnt/datalake/sales/orders` 
    RETAIN 168 HOURS  -- 7 days minimum
""")
```

## Medallion Architecture (Bronze → Silver → Gold)

```
[Source Systems: APIs, DBs, Files, Kafka]
          |
     [BRONZE Layer]
     - Raw data, no changes
     - Preserves original format
     - Append-only
     - Partition by ingestion_date
          |
     [SILVER Layer]
     - Cleaned and validated
     - Schema enforced
     - Duplicates removed
     - Business rules applied
     - Delta MERGE for SCD logic
          |
     [GOLD Layer]
     - Business-level aggregates
     - Fact and dimension tables
     - Ready for BI/ML consumption
     - Optimized for query performance
```

```python
# Bronze ingestion (raw)
def ingest_to_bronze(source_path: str, table_name: str, partition_cols: list):
    df = spark.read.json(source_path)
    df = df.withColumn("_ingestion_timestamp", F.current_timestamp()) \
           .withColumn("_source_file", F.input_file_name()) \
           .withColumn("_ingestion_date", F.current_date())
    
    df.write.format("delta") \
        .mode("append") \
        .partitionBy("_ingestion_date") \
        .saveAsTable(f"bronze.{table_name}")

# Silver transformation (cleaned)
def process_to_silver(bronze_table: str, silver_table: str, last_watermark: str):
    df_raw = spark.sql(f"""
        SELECT * FROM bronze.{bronze_table}
        WHERE _ingestion_date > '{last_watermark}'
    """)
    
    # Clean and validate
    df_clean = df_raw \
        .dropDuplicates(["order_id"]) \
        .filter(F.col("order_value").isNotNull()) \
        .filter(F.col("order_value") > 0) \
        .withColumn("order_value", F.col("order_value").cast(DoubleType())) \
        .withColumn("order_date", F.to_date(F.col("order_date"), "yyyy-MM-dd"))
    
    # MERGE into silver
    target = DeltaTable.forName(spark, f"silver.{silver_table}")
    target.alias("t").merge(
        df_clean.alias("s"),
        "t.order_id = s.order_id"
    ).whenMatchedUpdateAll() \
     .whenNotMatchedInsertAll() \
     .execute()
```

## Delta Live Tables (DLT)

```python
import dlt

@dlt.table(
    comment="Raw orders from source API",
    table_properties={"quality": "bronze"}
)
def orders_bronze():
    return (
        spark.readStream.format("cloudFiles")
        .option("cloudFiles.format", "json")
        .load("abfss://raw@storage.dfs.core.windows.net/orders/")
    )

@dlt.table(
    comment="Cleaned and validated orders",
    table_properties={"quality": "silver"}
)
@dlt.expect_or_drop("valid_order_value", "order_value > 0")
@dlt.expect_or_drop("non_null_customer", "customer_id IS NOT NULL")
def orders_silver():
    return (
        dlt.read_stream("orders_bronze")
        .withColumn("order_date", F.to_date("order_date"))
        .dropDuplicates(["order_id"])
    )

@dlt.table(
    comment="Daily revenue aggregation for BI",
    table_properties={"quality": "gold"}
)
def daily_revenue_gold():
    return (
        dlt.read("orders_silver")
        .groupBy("order_date", "country")
        .agg(
            F.sum("order_value").alias("total_revenue"),
            F.count("order_id").alias("order_count"),
            F.countDistinct("customer_id").alias("unique_buyers")
        )
    )
```

---

# 8. AZURE ROADMAP

## ☁️ Azure for Data Engineers

### Azure Core Services Map

```
[Data Sources]
     |
[Azure Data Factory]  ← Orchestration + ELT
     |
[Azure Data Lake Storage Gen2]  ← Raw Storage
     |
[Azure Databricks]  ← Big Data Processing
     |
[Azure Synapse Analytics]  ← SQL + Analytics
     |
[Power BI / Azure Analysis Services]  ← Visualization
```

### Azure Data Lake Storage Gen2 (ADLS)
```python
from azure.storage.blob import BlobServiceClient
from azure.identity import DefaultAzureCredential

# Authentication (use Managed Identity in production — no credentials in code!)
credential = DefaultAzureCredential()
service_client = BlobServiceClient(
    account_url="https://{account}.blob.core.windows.net",
    credential=credential
)

# Upload file
def upload_to_adls(local_path: str, container: str, blob_path: str):
    blob_client = service_client.get_blob_client(container, blob_path)
    with open(local_path, "rb") as data:
        blob_client.upload_blob(data, overwrite=True)

# List files
def list_files(container: str, prefix: str) -> list:
    container_client = service_client.get_container_client(container)
    return [blob.name for blob in container_client.list_blobs(name_starts_with=prefix)]

# Mounting in Databricks
configs = {
    "fs.azure.account.auth.type": "OAuth",
    "fs.azure.account.oauth.provider.type": "org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider",
    "fs.azure.account.oauth2.client.id": dbutils.secrets.get("scope", "client-id"),
    "fs.azure.account.oauth2.client.secret": dbutils.secrets.get("scope", "client-secret"),
    "fs.azure.account.oauth2.client.endpoint": f"https://login.microsoftonline.com/{tenant_id}/oauth2/token"
}

dbutils.fs.mount(
    source="abfss://bronze@{account}.dfs.core.windows.net/",
    mount_point="/mnt/bronze",
    extra_configs=configs
)
```

### Azure Data Factory (ADF)
Key concepts to master:
- **Pipelines:** Collection of activities
- **Activities:** Copy, Databricks Notebook, Stored Procedure, Web, etc.
- **Datasets:** Definition of data structure in a linked service
- **Linked Services:** Connection strings to external systems
- **Triggers:** Schedule, Event, Tumbling Window
- **Parameters:** Dynamic pipelines that accept runtime values
- **Data Flows:** Visual ETL transformations (avoid for complex logic — use Databricks)

**ADF vs Databricks Workflows:**
- ADF: Cross-system orchestration, ingestion, simple transformations
- Databricks Workflows: Spark-based transformations, ML jobs, DLT

### Azure Synapse Analytics
```sql
-- External tables over ADLS
CREATE EXTERNAL TABLE orders_external (
    order_id BIGINT,
    customer_id INT,
    order_date DATE,
    order_value DECIMAL(10,2)
)
WITH (
    LOCATION = '/sales/silver/orders/',
    DATA_SOURCE = MyDataLakeSource,
    FILE_FORMAT = MyParquetFormat
);

-- COPY INTO (efficient bulk loading)
COPY INTO orders_dwh
FROM 'https://account.blob.core.windows.net/silver/orders/'
WITH (
    FILE_TYPE = 'PARQUET',
    CREDENTIAL = (IDENTITY = 'Managed Identity')
)
OPTION (MAXERRORS = 10);

-- Distribution strategies (critical for Synapse performance)
CREATE TABLE fact_sales (
    sale_id BIGINT NOT NULL,
    customer_id INT NOT NULL,
    product_id INT NOT NULL,
    sale_date DATE NOT NULL,
    amount DECIMAL(10,2) NOT NULL
)
WITH (
    DISTRIBUTION = HASH(customer_id),  -- Distribute by join column
    CLUSTERED COLUMNSTORE INDEX         -- Best for analytics
);
```

### Azure IAM and Security Best Practices
- **Managed Identity:** Services authenticate using Azure AD (no credentials in code)
- **Service Principal:** Application identity (use for CI/CD pipelines)
- **Key Vault:** Store all secrets, connection strings, API keys
- **RBAC:** Assign roles at resource group level (least privilege principle)
- **Private Endpoints:** Keep traffic within Azure network
- **Encryption:** Always enable encryption at rest (default) and in transit

---

# 9. AIRFLOW ROADMAP

## 🌬️ Apache Airflow — Pipeline Orchestration

### DAG Fundamentals
```python
from airflow import DAG
from airflow.operators.python import PythonOperator
from airflow.operators.bash import BashOperator
from airflow.providers.databricks.operators.databricks import DatabricksRunNowOperator
from airflow.providers.apache.kafka.operators.produce import ProduceToTopicOperator
from datetime import datetime, timedelta

# DAG definition
default_args = {
    "owner": "data-engineering-team",
    "depends_on_past": False,
    "start_date": datetime(2024, 1, 1),
    "email": ["data-alerts@company.com"],
    "email_on_failure": True,
    "email_on_retry": False,
    "retries": 3,
    "retry_delay": timedelta(minutes=5),
    "execution_timeout": timedelta(hours=2),
}

with DAG(
    dag_id="daily_sales_pipeline",
    default_args=default_args,
    description="Daily sales ETL pipeline",
    schedule_interval="0 2 * * *",  # 2 AM daily
    catchup=False,
    max_active_runs=1,
    tags=["sales", "daily", "production"],
) as dag:
    
    # Python operators
    def extract_from_api(**context):
        """Extract data from source API"""
        execution_date = context["execution_date"]
        # Use execution_date for idempotent extractions
        data = fetch_api_data(date=execution_date.date())
        
        # Push data to XCom for next task
        context["ti"].xcom_push(key="record_count", value=len(data))
        return len(data)
    
    def validate_data(**context):
        """Validate extracted data"""
        record_count = context["ti"].xcom_pull(
            task_ids="extract_task", key="record_count"
        )
        if record_count < 100:
            raise ValueError(f"Low record count: {record_count}. Expected > 100")
    
    extract_task = PythonOperator(
        task_id="extract_task",
        python_callable=extract_from_api,
    )
    
    validate_task = PythonOperator(
        task_id="validate_task",
        python_callable=validate_data,
    )
    
    # Databricks job
    databricks_transform = DatabricksRunNowOperator(
        task_id="databricks_transform",
        databricks_conn_id="databricks_default",
        job_id=12345,
        notebook_params={"execution_date": "{{ ds }}"},
    )
    
    # Bash operator
    notify_success = BashOperator(
        task_id="notify_success",
        bash_command="""
            curl -X POST $SLACK_WEBHOOK \
            -d '{"text": "Sales pipeline completed for {{ ds }}"}'
        """,
    )
    
    # Task dependencies (DAG structure)
    extract_task >> validate_task >> databricks_transform >> notify_success
```

### Dynamic DAGs (Advanced)
```python
# Generate DAGs dynamically for multiple clients
import yaml
from airflow.models import DAG
from airflow.operators.python import PythonOperator

def create_client_dag(client_config: dict) -> DAG:
    client_id = client_config["client_id"]
    
    with DAG(
        dag_id=f"client_{client_id}_pipeline",
        schedule_interval=client_config["schedule"],
        default_args=default_args,
        catchup=False,
    ) as dag:
        
        extract = PythonOperator(
            task_id="extract",
            python_callable=extract_client_data,
            op_kwargs={"client_config": client_config}
        )
        
        transform = PythonOperator(
            task_id="transform",
            python_callable=transform_client_data,
            op_kwargs={"client_id": client_id}
        )
        
        extract >> transform
    
    return dag

# Load client configs from YAML
with open("configs/clients.yaml") as f:
    clients = yaml.safe_load(f)

# Create a DAG for each client
for client in clients["clients"]:
    globals()[f"dag_{client['client_id']}"] = create_client_dag(client)
```

### Airflow Production Best Practices
1. **Use task groups** for logical organization
2. **Never put credentials in DAGs** — use Airflow Connections
3. **Use SLAs** to detect slow tasks
4. **Use sensors sparingly** — they consume worker slots
5. **Set concurrency limits** to prevent resource exhaustion
6. **Use Celery or Kubernetes executor** for production (not Local)
7. **Enable RBAC** for multi-team environments
8. **Implement alerting** (PagerDuty/Slack on failure)
9. **Use task IDs consistently** — renaming breaks task history
10. **Always set `catchup=False`** for new DAGs unless you need backfill

---

# 10. KAFKA ROADMAP

## 📨 Apache Kafka — Real-Time Data Streaming

### Core Concepts

```
[Producers]  →  [Kafka Cluster]  →  [Consumers]
                    |
               [Topics/Partitions]
               [ZooKeeper/KRaft]
               [Brokers]
               [Consumer Groups]
```

**Key Terms:**
- **Topic:** Named stream of messages (like a table)
- **Partition:** Parallelism unit within a topic (more partitions = more throughput)
- **Offset:** Position of a message within a partition
- **Consumer Group:** Multiple consumers reading from the same topic in parallel
- **Broker:** Kafka server that stores and serves messages
- **Replication Factor:** Number of copies of each partition (fault tolerance)
- **Retention:** How long messages are kept (time or size-based)

### Producer in Python
```python
from confluent_kafka import Producer
import json
import uuid
from datetime import datetime

class OrderEventProducer:
    def __init__(self, bootstrap_servers: str, topic: str):
        self.topic = topic
        self.producer = Producer({
            "bootstrap.servers": bootstrap_servers,
            "client.id": f"order-producer-{uuid.uuid4()}",
            
            # Performance tuning
            "batch.size": 65536,        # 64KB batches
            "linger.ms": 5,             # Wait 5ms for batch to fill
            "compression.type": "lz4",  # Compress messages
            "acks": "all",              # Wait for all replicas (reliability)
            "max.in.flight.requests.per.connection": 5,
            "enable.idempotence": True, # Exactly-once delivery
            
            # Retries
            "retries": 3,
            "retry.backoff.ms": 100,
        })
    
    def delivery_callback(self, err, msg):
        if err:
            print(f"Message delivery failed: {err}")
        else:
            print(f"Delivered to {msg.topic()} [{msg.partition()}] at offset {msg.offset()}")
    
    def produce_order_event(self, order: dict):
        event = {
            "event_id": str(uuid.uuid4()),
            "event_type": "ORDER_CREATED",
            "timestamp": datetime.utcnow().isoformat(),
            "payload": order
        }
        
        self.producer.produce(
            topic=self.topic,
            key=str(order["customer_id"]).encode("utf-8"),  # Key ensures ordering per customer
            value=json.dumps(event).encode("utf-8"),
            callback=self.delivery_callback,
            headers={"source": b"order-service", "version": b"1.0"}
        )
        
        self.producer.poll(0)  # Trigger delivery callbacks
    
    def flush(self):
        pending = self.producer.flush(timeout=30)
        if pending > 0:
            print(f"Warning: {pending} messages not delivered")

# Usage
producer = OrderEventProducer("kafka-broker:9092", "orders")
producer.produce_order_event({
    "order_id": "ORD-001",
    "customer_id": 12345,
    "amount": 299.99,
    "products": ["PROD-A", "PROD-B"]
})
producer.flush()
```

### Consumer in Python
```python
from confluent_kafka import Consumer, KafkaError
import json

class OrderEventConsumer:
    def __init__(self, bootstrap_servers: str, topic: str, group_id: str):
        self.consumer = Consumer({
            "bootstrap.servers": bootstrap_servers,
            "group.id": group_id,
            "auto.offset.reset": "earliest",    # Start from beginning for new groups
            "enable.auto.commit": False,         # Manual commit for reliability
            "max.poll.interval.ms": 300000,      # 5 minute processing limit
            "session.timeout.ms": 45000,
        })
        self.consumer.subscribe([topic])
    
    def consume_with_manual_commit(self, batch_size: int = 100):
        messages_batch = []
        
        try:
            while True:
                msg = self.consumer.poll(timeout=1.0)
                
                if msg is None:
                    # No message, process existing batch
                    if messages_batch:
                        self._process_batch(messages_batch)
                        self.consumer.commit()
                        messages_batch = []
                    continue
                
                if msg.error():
                    if msg.error().code() == KafkaError._PARTITION_EOF:
                        continue
                    raise KafkaError(msg.error())
                
                event = json.loads(msg.value().decode("utf-8"))
                messages_batch.append(event)
                
                if len(messages_batch) >= batch_size:
                    self._process_batch(messages_batch)
                    self.consumer.commit()  # Commit after successful processing
                    messages_batch = []
        
        except KeyboardInterrupt:
            pass
        finally:
            self.consumer.close()
    
    def _process_batch(self, events: list):
        """Process a batch of events (write to database, trigger downstream, etc.)"""
        print(f"Processing batch of {len(events)} events")
        # Write to database, call downstream API, etc.
```

### Kafka + Spark Streaming Integration
```python
from pyspark.sql import SparkSession
from pyspark.sql import functions as F
from pyspark.sql.types import StructType, StructField, StringType, DoubleType, TimestampType

spark = SparkSession.builder \
    .appName("OrderStreamProcessor") \
    .config("spark.jars.packages", "org.apache.spark:spark-sql-kafka-0-10_2.12:3.5.0") \
    .getOrCreate()

# Define schema for order events
order_schema = StructType([
    StructField("event_id", StringType()),
    StructField("event_type", StringType()),
    StructField("timestamp", TimestampType()),
    StructField("payload", StructType([
        StructField("order_id", StringType()),
        StructField("customer_id", StringType()),
        StructField("amount", DoubleType()),
    ]))
])

# Read from Kafka
df_stream = spark.readStream \
    .format("kafka") \
    .option("kafka.bootstrap.servers", "kafka-broker:9092") \
    .option("subscribe", "orders") \
    .option("startingOffsets", "latest") \
    .option("maxOffsetsPerTrigger", 10000) \
    .load()

# Parse JSON events
df_parsed = df_stream \
    .select(
        F.col("key").cast("string").alias("partition_key"),
        F.from_json(F.col("value").cast("string"), order_schema).alias("event"),
        F.col("timestamp").alias("kafka_timestamp"),
        F.col("partition"),
        F.col("offset")
    ) \
    .select(
        "partition_key",
        "kafka_timestamp",
        "event.event_id",
        "event.event_type",
        "event.timestamp",
        "event.payload.*"
    )

# Real-time aggregation with watermarking
df_windowed = df_parsed \
    .withWatermark("timestamp", "10 minutes") \
    .groupBy(
        F.window("timestamp", "5 minutes"),
        "event_type"
    ) \
    .agg(
        F.count("*").alias("event_count"),
        F.sum("amount").alias("total_amount"),
        F.avg("amount").alias("avg_amount")
    )

# Write to Delta Lake (streaming)
query = df_windowed.writeStream \
    .format("delta") \
    .outputMode("append") \
    .option("checkpointLocation", "/mnt/checkpoints/order_stream") \
    .trigger(processingTime="1 minute") \
    .start("/mnt/silver/order_metrics")

query.awaitTermination()
```

---

# 11. SNOWFLAKE ROADMAP

## ❄️ Snowflake — Cloud Data Warehouse

### Core Architecture
```
[Snowflake Architecture]
    ├── Cloud Services Layer (Query compilation, optimization, metadata)
    ├── Compute Layer (Virtual Warehouses — CPU/Memory)
    └── Storage Layer (S3/Azure/GCS — structured columnar data)
```

**Key differentiators:**
- **Separate compute and storage:** Scale independently, pay only for what you use
- **Multi-cluster warehouses:** Auto-scale for concurrent workloads
- **Zero-copy cloning:** Instant copies without duplicating storage
- **Time Travel:** Query historical data up to 90 days
- **Data Sharing:** Share live data across organizations without copying

### Essential Snowflake SQL
```sql
-- Virtual warehouse management
CREATE WAREHOUSE transform_wh
    WAREHOUSE_SIZE = 'MEDIUM'
    AUTO_SUSPEND = 120         -- Auto-suspend after 2 minutes idle
    AUTO_RESUME = TRUE
    COMMENT = 'ETL transformation warehouse';

-- Context setup
USE WAREHOUSE transform_wh;
USE DATABASE analytics_db;
USE SCHEMA gold;

-- Stages (external storage)
CREATE STAGE s3_stage
    URL = 's3://my-bucket/data/'
    CREDENTIALS = (
        AWS_KEY_ID = '...'
        AWS_SECRET_KEY = '...'
    )
    FILE_FORMAT = (TYPE = 'PARQUET');

-- COPY INTO (bulk loading)
COPY INTO orders
FROM @s3_stage/orders/
FILE_FORMAT = (TYPE = 'PARQUET')
ON_ERROR = 'SKIP_FILE'
PURGE = FALSE;

-- Streams (Change Data Capture)
CREATE STREAM orders_stream ON TABLE orders;

-- After DML operations on orders, stream captures changes
SELECT * FROM orders_stream;
-- Columns: all original columns + METADATA$ACTION, METADATA$ISUPDATE, METADATA$ROW_ID

-- Tasks (scheduled SQL)
CREATE TASK process_new_orders
    WAREHOUSE = transform_wh
    SCHEDULE = '5 MINUTE'  -- Run every 5 minutes
    WHEN SYSTEM$STREAM_HAS_DATA('orders_stream')
AS
    INSERT INTO orders_processed
    SELECT order_id, customer_id, amount, 'processed' as status, CURRENT_TIMESTAMP()
    FROM orders_stream
    WHERE METADATA$ACTION = 'INSERT';

ALTER TASK process_new_orders RESUME;

-- Zero-copy cloning
CREATE DATABASE analytics_dev CLONE analytics_prod;  -- Instant, no storage cost
CREATE TABLE orders_backup CLONE orders;
```

### Snowflake Performance Optimization
```sql
-- 1. Clustering keys (for large tables, reduces micro-partition scans)
ALTER TABLE fact_sales CLUSTER BY (sale_date, country_code);

-- 2. Search optimization (for selective point lookups)
ALTER TABLE customers ADD SEARCH OPTIMIZATION ON order_id;

-- 3. Materialized views (pre-compute expensive aggregations)
CREATE MATERIALIZED VIEW daily_sales_summary AS
SELECT 
    DATE_TRUNC('day', sale_date) as day,
    country,
    SUM(amount) as total_sales,
    COUNT(*) as order_count
FROM fact_sales
GROUP BY 1, 2;

-- 4. Result caching (Snowflake caches query results for 24h)
-- Ensure deterministic queries to benefit from cache

-- 5. Query profiling
SELECT * FROM TABLE(RESULT_SCAN(LAST_QUERY_ID()));
-- Check INFORMATION_SCHEMA.QUERY_HISTORY for slow queries

-- Data sharing
CREATE SHARE product_analytics_share;
GRANT USAGE ON DATABASE analytics_db TO SHARE product_analytics_share;
GRANT USAGE ON SCHEMA analytics_db.gold TO SHARE product_analytics_share;
GRANT SELECT ON TABLE analytics_db.gold.sales_dashboard TO SHARE product_analytics_share;
ALTER SHARE product_analytics_share ADD ACCOUNTS = partner_account;
```

---

# 12. DBT ROADMAP

## 🔧 dbt (Data Build Tool) — Analytics Engineering

### Why dbt? (The Key Mental Model)
dbt brings **software engineering practices** to SQL transformations:
- Version control for SQL
- Testing data quality automatically
- Auto-generated documentation
- Lineage graphs
- Modular, reusable SQL

### dbt Project Structure
```
my_dbt_project/
├── dbt_project.yml          # Project configuration
├── profiles.yml             # Connection profiles (in ~/.dbt/)
├── packages.yml             # External packages
├── models/
│   ├── staging/             # 1:1 with source tables (light cleaning)
│   │   ├── stg_orders.sql
│   │   ├── stg_customers.sql
│   │   └── schema.yml       # Tests and documentation
│   ├── intermediate/        # Business logic
│   │   └── int_orders_enriched.sql
│   └── marts/               # Final models for BI
│       ├── finance/
│       │   └── fct_orders.sql
│       └── marketing/
│           └── dim_customers.sql
├── tests/                   # Custom data tests
│   └── assert_positive_revenue.sql
├── macros/                  # Reusable SQL functions
│   └── generate_surrogate_key.sql
├── seeds/                   # Static CSV files
│   └── country_codes.csv
└── analyses/                # Ad-hoc analyses (not materialized)
```

### Models
```sql
-- models/staging/stg_orders.sql
-- Staging: light transformations, source fidelity
{{ config(
    materialized='incremental',
    unique_key='order_id',
    on_schema_change='sync_all_columns'
) }}

WITH source AS (
    SELECT * FROM {{ source('raw', 'orders') }}
    {% if is_incremental() %}
        WHERE created_at > (SELECT MAX(created_at) FROM {{ this }})
    {% endif %}
),

renamed AS (
    SELECT
        order_id::VARCHAR         AS order_id,
        customer_id::INTEGER      AS customer_id,
        order_date::DATE          AS order_date,
        UPPER(status)             AS status,
        amount::DECIMAL(10,2)     AS order_amount,
        created_at::TIMESTAMP     AS created_at,
        _etl_loaded_at            AS loaded_at
    FROM source
),

cleaned AS (
    SELECT * FROM renamed
    WHERE order_id IS NOT NULL
      AND order_amount > 0
)

SELECT * FROM cleaned
```

```sql
-- models/marts/finance/fct_orders.sql
-- Gold layer model — final business logic
{{ config(
    materialized='table',
    cluster_by=['order_date', 'country_code']
) }}

WITH orders AS (
    SELECT * FROM {{ ref('stg_orders') }}
),

customers AS (
    SELECT * FROM {{ ref('dim_customers') }}
),

date_spine AS (
    SELECT * FROM {{ ref('dim_date') }}
),

final AS (
    SELECT
        {{ dbt_utils.generate_surrogate_key(['o.order_id']) }} AS order_key,
        o.order_id,
        o.customer_id,
        c.customer_segment,
        c.country_code,
        o.order_date,
        d.fiscal_quarter,
        d.fiscal_year,
        o.order_amount,
        o.order_amount * COALESCE(fx.usd_rate, 1) AS order_amount_usd,
        o.status,
        CASE 
            WHEN o.order_amount < 100 THEN 'low'
            WHEN o.order_amount < 1000 THEN 'medium'
            ELSE 'high'
        END AS order_tier
    FROM orders o
    LEFT JOIN customers c ON o.customer_id = c.customer_id
    LEFT JOIN date_spine d ON o.order_date = d.full_date
    LEFT JOIN {{ ref('fx_rates') }} fx ON o.order_date = fx.date AND c.country_code = fx.country_code
)

SELECT * FROM final
```

### dbt Tests and Documentation
```yaml
# models/staging/schema.yml
version: 2

sources:
  - name: raw
    database: raw_db
    schema: public
    tables:
      - name: orders
        freshness:
          warn_after: {count: 1, period: hour}
          error_after: {count: 6, period: hour}
        loaded_at_field: _etl_loaded_at

models:
  - name: stg_orders
    description: "Staged orders from source system. One row per order."
    columns:
      - name: order_id
        description: "Unique order identifier"
        tests:
          - unique
          - not_null
      - name: customer_id
        tests:
          - not_null
          - relationships:
              to: ref('stg_customers')
              field: customer_id
      - name: order_amount
        tests:
          - not_null
          - dbt_utils.expression_is_true:
              expression: ">= 0"
      - name: status
        tests:
          - accepted_values:
              values: ['PENDING', 'COMPLETED', 'CANCELLED', 'REFUNDED']
```

### dbt Macros
```sql
-- macros/generate_surrogate_key.sql
{% macro generate_surrogate_key(field_list) %}
    {{ dbt_utils.surrogate_key(field_list) }}
{% endmacro %}

-- macros/cents_to_dollars.sql
{% macro cents_to_dollars(column_name, precision=2) %}
    ROUND({{ column_name }} / 100.0, {{ precision }})
{% endmacro %}

-- macros/date_spine.sql — generate a complete date table
{% macro create_date_spine(start_date, end_date) %}
    {{ dbt_utils.date_spine(
        datepart="day",
        start_date="cast('" ~ start_date ~ "' as date)",
        end_date="cast('" ~ end_date ~ "' as date)"
    ) }}
{% endmacro %}
```

### dbt Commands
```bash
dbt debug                           # Test connection
dbt run                             # Run all models
dbt run --models staging.*          # Run only staging models
dbt run --models +fct_orders        # Run fct_orders and all its dependencies
dbt test                            # Run all tests
dbt test --models stg_orders        # Test specific model
dbt docs generate                   # Generate documentation
dbt docs serve                      # Serve docs locally (port 8080)
dbt snapshot                        # Run SCD Type 2 snapshots
dbt seed                            # Load seed CSV files
dbt source freshness                # Check source data freshness
dbt compile                         # Compile SQL without running
```

---

# 13. POWER BI ROADMAP

## 📊 Power BI for Data Engineers

### The Data Engineer's Role in Power BI
Your job: Build **optimal, fast data models** that analysts can use. Not designing dashboards — that's the analyst's job. Focus on:
- Designing the semantic model
- Writing efficient DAX
- Optimizing query performance
- Implementing Row-Level Security (RLS)
- Building reusable measures

### DAX — Data Analysis Expressions
```dax
-- Basic measures
Total Revenue = SUM(fact_sales[order_amount])

Unique Customers = DISTINCTCOUNT(fact_sales[customer_id])

Avg Order Value = DIVIDE([Total Revenue], COUNTROWS(fact_sales))

-- Time intelligence
Revenue YTD = 
CALCULATE(
    [Total Revenue],
    DATESYTD(dim_date[date])
)

Revenue LY = 
CALCULATE(
    [Total Revenue],
    SAMEPERIODLASTYEAR(dim_date[date])
)

YoY Growth % = 
DIVIDE(
    [Total Revenue] - [Revenue LY],
    [Revenue LY]
)

-- CALCULATE with complex filters
Revenue Premium Customers = 
CALCULATE(
    [Total Revenue],
    dim_customers[segment] = "Premium",
    fact_sales[status] = "COMPLETED"
)

-- Running total
Running Total Revenue = 
CALCULATE(
    [Total Revenue],
    FILTER(
        ALL(dim_date[date]),
        dim_date[date] <= MAX(dim_date[date])
    )
)

-- Ranking
Product Revenue Rank = 
RANKX(
    ALL(dim_products[product_name]),
    [Total Revenue],
    ,
    DESC,
    Dense
)

-- Dynamic top N
Top N Revenue = 
IF(
    [Product Revenue Rank] <= SELECTEDVALUE(top_n_parameter[Value], 10),
    [Total Revenue]
)

-- % of total with ALLSELECTED
Revenue % of Total = 
DIVIDE(
    [Total Revenue],
    CALCULATE([Total Revenue], ALLSELECTED(dim_date[date]))
)
```

### Row-Level Security (RLS)
```dax
-- In Power BI Desktop: Manage Roles
-- Create role "Regional Manager"
-- Add DAX filter to dim_geography table:
[region_code] = USERPRINCIPALNAME()  -- Match user's email to region

-- Or use a security table:
-- Create role "User Access Control"
[region_code] IN 
    VALUES(
        FILTER(
            user_regions,
            user_regions[user_email] = USERPRINCIPALNAME()
        )[region_code]
    )
```

### Power Query (M Language) for Data Transformation
```m
// Power Query — used for data shaping before loading to model
let
    // Load from Azure SQL
    Source = Sql.Database("server.database.windows.net", "analytics_db"),
    Schema = Source{[Schema="gold",Item="fact_sales"]}[Data],
    
    // Filter only last 3 years
    #"Filtered Rows" = Table.SelectRows(Schema, each 
        [order_date] >= Date.AddYears(DateTime.LocalNow(), -3)
    ),
    
    // Remove unnecessary columns
    #"Removed Columns" = Table.RemoveColumns(#"Filtered Rows", {"internal_id", "_etl_loaded_at"}),
    
    // Add custom column
    #"Added Revenue Tier" = Table.AddColumn(#"Removed Columns", "Revenue Tier", each 
        if [order_amount] < 100 then "Low"
        else if [order_amount] < 1000 then "Medium"
        else "High"
    ),
    
    // Change types
    #"Changed Types" = Table.TransformColumnTypes(#"Added Revenue Tier", {
        {"order_date", type date},
        {"order_amount", type number},
        {"customer_id", Int64.Type}
    })
    
in
    #"Changed Types"
```

### Power BI Optimization Best Practices
1. **Import mode > DirectQuery** for performance (unless real-time required)
2. **Star schema only** — never load joined flat tables
3. **Disable auto date/time** — use your own dim_date
4. **Reduce model size:** Remove unused columns before loading
5. **Use integer keys** for relationships, not strings
6. **Avoid row-level calculations** in DAX (pre-compute in SQL/dbt)
7. **Use aggregation tables** for large fact tables
8. **Avoid bidirectional relationships** — causes ambiguity
9. **Measure, not calculated column** — measures are evaluated at query time
10. **Performance Analyzer** — use to find slow visuals

---

# 14. UNIQUE PROJECTS SECTION

## 🏗️ Beginner Projects (Month 1–2)

### Project 1: Multi-Source Financial Data Pipeline
**Objective:** Build an automated pipeline that collects financial data from multiple free APIs and stores it in a structured format.

**Architecture:**
```
[Alpha Vantage API] ──┐
[Yahoo Finance API]  ──┤→ [Python Collector] → [PostgreSQL] → [Power BI Dashboard]
[CoinGecko API]     ──┘         |
                            [Error Logs]
                            [SQLite Metadata]
```

**Technologies:** Python, requests, pandas, SQLAlchemy, PostgreSQL, Power BI, schedule library

**Dataset/APIs:**
- Alpha Vantage (free tier): Stock prices, forex rates
- CoinGecko: Cryptocurrency prices (free, no key)
- FRED API: Macroeconomic data (free)

**Workflow:**
1. Pull daily OHLCV data for 20 stocks/cryptos
2. Validate: check for nulls, price spikes, missing dates
3. Normalize to schema and load to PostgreSQL
4. Log pipeline metadata (run time, records loaded, errors)
5. Build Power BI dashboard with sparklines, returns, volatility

**GitHub Structure:**
```
financial-data-pipeline/
├── src/
│   ├── collectors/
│   │   ├── alpha_vantage.py
│   │   ├── coingecko.py
│   │   └── fred.py
│   ├── transformers/
│   │   └── normalize.py
│   ├── loaders/
│   │   └── postgres_loader.py
│   └── validators/
│       └── data_quality.py
├── tests/
├── configs/
│   └── pipeline.yaml
├── dashboards/
│   └── financial_dashboard.pbix
├── docker-compose.yml
├── requirements.txt
└── README.md
```

**Business Use Case:** Portfolio monitoring, risk analysis, automated alerts

**Deployment:** Docker Compose + cron job on a free cloud VM (Oracle Cloud Free Tier)

**Interview Questions Based on Project:**
- How did you handle API rate limits?
- What happens if one API fails? Does the whole pipeline fail?
- How do you handle missing data (market holidays)?
- How would you scale this to 500 stocks?
- How do you detect data quality issues automatically?

**Scaling Ideas:** Add Airflow for orchestration, replace PostgreSQL with Snowflake, add ML-based anomaly detection

---

### Project 2: E-Commerce Data Warehouse
**Objective:** Build a complete analytical data warehouse from a generated e-commerce dataset.

**Architecture:**
```
[Python Data Generator] → [Raw CSV Files] → [PostgreSQL OLTP] → [ETL Scripts] → [Star Schema DWH] → [Power BI]
```

**Technologies:** Python (Faker), pandas, SQLAlchemy, PostgreSQL, Power BI

**What to Build:**
1. Generate realistic data: 1M orders, 100K customers, 10K products
2. Design and implement star schema (fact_orders, dim_customer, dim_product, dim_date, dim_geography)
3. Implement SCD Type 2 for customer address changes
4. Build Power BI dashboard with sales KPIs, cohort analysis, product performance

---

## 🔥 Intermediate Projects (Month 3–5)

### Project 3: Real-Time Twitter/Reddit Sentiment Pipeline
**Objective:** Stream social media posts, analyze sentiment in real-time, aggregate and visualize.

**Architecture:**
```
[Twitter/Reddit API] → [Kafka Producer] → [Kafka Topic: posts] 
                                              |
                    [Spark Structured Streaming Consumer]
                              |                |
                    [Sentiment Analysis]  [Raw Storage Delta]
                              |
                    [Aggregated Metrics Delta]
                              |
                    [Power BI Streaming Dataset]
```

**Technologies:** Python, Kafka (Confluent Cloud free tier), PySpark, Databricks Community Edition, Delta Lake, Power BI

**Unique Twist:** Use Hugging Face's free sentiment model — pipeline runs entirely on free tiers

---

### Project 4: Automated Data Quality Monitoring Framework
**Objective:** Build a reusable data quality engine that monitors any pipeline and alerts on anomalies.

**Architecture:**
```
[Any Pipeline] → [DQ Engine] → [Metrics Store] → [Anomaly Detector] → [Slack Alert]
                     |
              [Rules Engine]
              (null %, schema drift, 
               row count variance,
               value distribution shift)
```

**Technologies:** Python, Great Expectations, pandas, PostgreSQL, Slack API, APScheduler

**Why This Stands Out:** Companies lose millions from bad data. A candidate who thinks about data quality proactively is gold.

**DQ Checks to Implement:**
```python
# Custom DQ framework
class DataQualityEngine:
    def check_null_percentage(self, df, column, threshold=0.05):
        null_pct = df[column].isnull().mean()
        return {"check": "null_percentage", "column": column, 
                "value": null_pct, "passed": null_pct <= threshold}
    
    def check_row_count_variance(self, current_count, historical_avg, threshold=0.2):
        variance = abs(current_count - historical_avg) / historical_avg
        return {"check": "row_count_variance", "value": variance,
                "passed": variance <= threshold}
    
    def check_schema_drift(self, current_schema, expected_schema):
        missing_cols = set(expected_schema) - set(current_schema)
        extra_cols = set(current_schema) - set(expected_schema)
        return {"check": "schema_drift", "missing": list(missing_cols),
                "extra": list(extra_cols), "passed": len(missing_cols) == 0}
```

---

## 🚀 Advanced Projects (Month 5–8)

### Project 5: Lakehouse Pipeline on Azure + Databricks
**Objective:** End-to-end data lakehouse using Medallion Architecture.

**Architecture:**
```
[Public APIs / Kaggle Dataset]
      |
[Azure Data Factory] (Ingestion orchestration)
      |
[ADLS Gen2 - Bronze Layer] (Raw Parquet)
      |
[Azure Databricks - PySpark] (Silver Layer transforms)
      |
[ADLS Gen2 - Silver Layer] (Delta format, cleaned)
      |
[Azure Databricks - PySpark] (Gold Layer aggregations)
      |
[ADLS Gen2 - Gold Layer] (Delta, BI-ready)
      |
[Azure Synapse Analytics] (SQL analytics on Gold)
      |
[Power BI] (Executive dashboards)
```

**What Makes This Resume-Level:**
- Uses production Azure services (free credits available)
- Implements Delta Lake with MERGE and Time Travel
- Uses Databricks Secrets for credential management
- Includes monitoring with job alerts
- Has CI/CD via GitHub Actions

---

### Project 6: Real-Time Fraud Detection System
**Objective:** Detect fraudulent transactions in real-time using streaming pipeline.

**Architecture:**
```
[Transaction Generator (Python)] 
    → [Kafka: transactions topic]
        → [Spark Structured Streaming]
            ├── [Rule-based fraud detection]
            ├── [Aggregate features: 1hr spending velocity]
            └── [Flag suspicious transactions]
                → [Kafka: fraud-alerts topic]
                    → [Alert Consumer → Slack/Email]
                → [Delta Lake: all transactions + fraud labels]
                    → [Power BI: fraud monitoring dashboard]
```

**Fraud Rules to Implement:**
- Transaction amount > 3x customer's 30-day average
- 5+ transactions within 10 minutes
- Transactions from 2 different countries within 1 hour
- Unusually high value for customer segment

---

## 🏆 Production-Grade + Unique Projects (Month 8–12)

### Project 7: Self-Healing Data Pipeline with Observability
**Objective:** Build a pipeline that automatically detects failures, heals itself, and maintains full observability.

**Unique Features:**
- Automatic retry with exponential backoff
- Dead letter queue for failed records
- Full metrics dashboard (throughput, latency, error rate, data quality score)
- Self-healing: automatic schema migration, partition repair
- PagerDuty-style alerting for SLA breaches

### Project 8: Multi-Tenant Data Platform
**Objective:** Build a data platform that serves multiple teams/clients with proper isolation.

**Unique Features:**
- Tenant-specific schemas and access controls
- Cost allocation by tenant (compute usage tracking)
- Tenant-specific data retention policies
- Self-service data catalog

---

# 15. MEGA END-TO-END PROJECT

## 🌟 Project: "DataNova" — Real-Time E-Commerce Intelligence Platform

### Overview
A production-grade, end-to-end data platform for a global e-commerce company processing 10M+ events/day.

### Complete Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                         DATA SOURCES                                │
│  [E-commerce App]  [CRM System]  [ERP System]  [Marketing APIs]     │
└──────┬────────────────┬──────────────┬──────────────┬──────────────┘
       │                │              │              │
       ▼                ▼              ▼              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      INGESTION LAYER                                │
│  [Kafka: Orders Topic]  [ADF: Batch Ingestion]  [Debezium CDC]      │
│  Producers → Brokers (3 nodes, RF=3) → Consumer Groups              │
└──────┬────────────────┬──────────────────────────────────────────────┘
       │                │
       ▼                ▼
┌──────────────┐  ┌─────────────────────────────────────────────────┐
│  STREAMING   │  │              BATCH PROCESSING                    │
│              │  │                                                  │
│ Spark        │  │  Azure Data Lake Storage Gen2                    │
│ Structured   │  │  ├── /bronze  (raw, JSON/CSV)                    │
│ Streaming    │  │  ├── /silver  (Delta, cleaned)                   │
│ (5-min       │  │  └── /gold    (Delta, aggregated)                │
│  micro-batch)│  │                                                  │
└──────┬───────┘  └────────────────┬────────────────────────────────┘
       │                           │
       ▼                           ▼
┌─────────────────────────────────────────────────────────────────────┐
│                    PROCESSING LAYER (DATABRICKS)                     │
│                                                                      │
│  Bronze Jobs:    Raw ingestion, schema enforcement, append-only      │
│  Silver Jobs:    Dedup, validate, enrich, SCD Type 2                 │
│  Gold Jobs:      Aggregations, fact tables, BI-ready models          │
│                                                                      │
│  Delta Live Tables:  Automated pipeline with quality constraints     │
│  Unity Catalog:      Data governance, lineage, access control        │
└──────┬──────────────────────────────────────────────────────────────┘
       │
       ▼
┌─────────────────────────────────────────────────────────────────────┐
│                    TRANSFORMATION LAYER (DBT)                        │
│                                                                      │
│  Staging models → Intermediate models → Mart models                  │
│  Tests: unique, not_null, referential integrity, custom              │
│  Documentation: auto-generated lineage graph                         │
│  Snowflake: Final analytical tables                                  │
└──────┬──────────────────────────────────────────────────────────────┘
       │
       ▼
┌─────────────────────────────────────────────────────────────────────┐
│                   ORCHESTRATION (AIRFLOW)                            │
│                                                                      │
│  DAGs:                                                               │
│  ├── hourly_bronze_ingestion (ADF trigger + validation)              │
│  ├── daily_silver_transform (Databricks jobs)                        │
│  ├── daily_gold_aggregation (Databricks + dbt run)                   │
│  ├── dbt_test_suite (data quality gate before Gold promotion)        │
│  └── snowflake_sync (Gold → Snowflake via COPY INTO)                 │
│                                                                      │
│  Features: Retries, SLAs, Slack alerts, dynamic DAGs                 │
└──────┬──────────────────────────────────────────────────────────────┘
       │
       ▼
┌─────────────────────────────────────────────────────────────────────┐
│                  SERVING LAYER                                       │
│                                                                      │
│  Snowflake:       SQL analytics, ad-hoc queries, data science        │
│  Power BI:        Executive dashboards, operational reports           │
│  REST API:        Internal teams query Gold Delta tables              │
└─────────────────────────────────────────────────────────────────────┘
```

### Data Flow Detail

**1. Order Placement Event (Real-time path)**
```
Customer Places Order 
  → Order Service publishes to Kafka (orders topic, keyed by customer_id)
  → Spark Streaming reads from Kafka (5-min micro-batch)
  → Applies business rules: validate schema, enrich with customer segment
  → Fraud detection: check 1-hour spending velocity via stateful streaming
  → Writes to Delta (silver/orders_stream) 
  → Triggers streaming aggregation: revenue_by_minute to Delta
  → Power BI reads streaming dataset for real-time dashboard
```

**2. Daily Batch Path (Historical accuracy)**
```
Airflow @ 2AM triggers:
  → ADF ingests full day's orders from OLTP → ADLS Bronze
  → Databricks Silver job: dedup, validate, apply SCD Type 2 for customers
  → Databricks Gold job: compute daily KPIs, cohort assignments
  → dbt runs: staging → intermediate → marts (with all tests)
  → If dbt tests pass: COPY INTO Snowflake
  → Power BI dataset refreshes
  → Slack success notification
```

### Storage Layers Design

**Bronze Schema (raw, schema-on-read):**
```json
{
  "order_id": "ORD-12345",
  "customer_id": 67890,
  "items": [{"product_id": "P001", "qty": 2, "price": 49.99}],
  "created_at": "2024-11-15T10:30:00Z",
  "_source": "order-service",
  "_ingestion_ts": "2024-11-15T10:31:05Z",
  "_batch_id": "batch-2024-11-15-10"
}
```

**Silver Schema (typed, cleaned, Delta format):**
```sql
order_id STRING NOT NULL,
customer_id BIGINT NOT NULL,
order_date DATE NOT NULL,
total_amount DECIMAL(12,2) NOT NULL,
item_count INT,
customer_segment STRING,    -- enriched from dim_customer
country_code STRING,         -- enriched from dim_customer
fraud_score FLOAT,           -- from fraud model
is_fraudulent BOOLEAN,
created_at TIMESTAMP,
_silver_processed_at TIMESTAMP,
_version INT                  -- for SCD tracking
```

**Gold Schema (aggregated, Snowflake-ready):**
```sql
-- mart_daily_sales
date_key INT,
country_code STRING,
customer_segment STRING,
total_orders BIGINT,
total_revenue DECIMAL(18,2),
avg_order_value DECIMAL(10,2),
new_customers INT,
returning_customers INT,
fraud_rate FLOAT,
_dbt_updated_at TIMESTAMP
```

### Monitoring and Observability

```python
# Pipeline metrics tracked in metadata database
pipeline_metrics = {
    "pipeline_id": "daily_gold_2024-11-15",
    "stage": "silver_transform",
    "records_in": 1_234_567,
    "records_out": 1_234_102,
    "records_failed": 465,
    "failure_rate": 0.000377,
    "processing_time_seconds": 342,
    "avg_record_latency_ms": 0.277,
    "data_quality_score": 0.9996,
    "sla_met": True,
    "sla_threshold_minutes": 30,
    "actual_duration_minutes": 5.7,
    "timestamp": "2024-11-15T02:05:42Z"
}

# Alerts configured:
# - failure_rate > 1% → PagerDuty (P2 incident)
# - sla_met = False → Slack #data-alerts (P3)
# - records_in < 100K → Slack warning (possible source issue)
# - data_quality_score < 0.99 → Slack warning + block Gold promotion
```

### CI/CD Pipeline

```yaml
# .github/workflows/data_platform_cicd.yml
name: Data Platform CI/CD

on:
  push:
    branches: [main]
  pull_request:

jobs:
  unit-tests:
    runs-on: ubuntu-latest
    steps:
      - name: Run Python unit tests
        run: pytest tests/unit/ -v --cov=src
  
  dbt-tests:
    runs-on: ubuntu-latest
    steps:
      - name: Run dbt compile
        run: dbt compile --target ci
      - name: Run dbt tests on staging
        run: dbt test --target ci --models staging.*
  
  integration-tests:
    runs-on: ubuntu-latest
    services:
      postgres:
        image: postgres:15
    steps:
      - name: Run integration tests
        run: pytest tests/integration/ -v
  
  deploy-to-staging:
    needs: [unit-tests, dbt-tests, integration-tests]
    if: github.ref == 'refs/heads/main'
    steps:
      - name: Deploy Databricks notebooks
        run: databricks workspace import-dir notebooks/ /Production/
      - name: Deploy Airflow DAGs
        run: aws s3 sync dags/ s3://airflow-bucket/dags/
      - name: Run dbt on staging
        run: dbt run --target staging
```

### Security Architecture
- All credentials in Azure Key Vault (accessed via Managed Identity)
- ADLS: RBAC + ACLs (readers/writers per team)
- Databricks Unity Catalog: Column-level security for PII
- Snowflake: RBAC + network policy (IP allowlist)
- Kafka: SSL + SASL authentication
- Power BI: Row-Level Security based on Azure AD groups
- All data encrypted at rest (AES-256) and in transit (TLS 1.3)

---

# 16. SYSTEM DESIGN FOR DATA ENGINEERS

## 🏛️ Scalable Pipeline Design

### The Data Engineering Design Framework

When designing any system, answer these questions:
1. **Volume:** How much data? (GB/day → TB/day → PB/day changes everything)
2. **Velocity:** Batch daily? Hourly? Real-time seconds?
3. **Variety:** Structured, semi-structured, unstructured?
4. **Veracity:** How clean is the data? Where can it be wrong?
5. **Value:** What decisions does this data enable?

### Batch vs Streaming Decision Matrix

| Requirement | Choose Batch | Choose Streaming |
|-------------|-------------|-----------------|
| Latency tolerance | Hours/days acceptable | Seconds/minutes required |
| Data volume | Any | High throughput |
| Correctness | Exact (reprocessable) | Approximate (acceptable) |
| Complexity | Higher transform logic OK | Simpler transforms preferred |
| Cost | Lower (compute only when running) | Higher (always-on infrastructure) |
| Use cases | Reporting, DWH, ML training | Fraud detection, monitoring, alerts |

### Lambda vs Kappa Architecture

**Lambda Architecture (Batch + Speed layers):**
```
[Data Source] → [Message Queue] → [Speed Layer (Streaming)] → [Serving] ← [Query]
                      |                                           ↑
                      └──────────[Batch Layer] ────────────────────
```
Problem: Two codebases for batch and streaming logic (high maintenance)

**Kappa Architecture (Streaming only):**
```
[Data Source] → [Kafka] → [Streaming Processor (Spark/Flink)] → [Serving Layer]
                  |
                  └── (Replay from beginning to reprocess)
```
Modern preference: Kappa is simpler. Only go Lambda if streaming can't handle your complexity.

**Lakehouse Architecture (Modern synthesis):**
```
[All Sources] → [Message Queue/Files] → [Delta Lake/Iceberg]
                                              |
                              [Streaming queries + Batch queries]
                                              |
                              [Single source of truth for all use cases]
```

### Partitioning Strategies

```python
# Partition by date (most common)
df.write.partitionBy("year", "month", "day").parquet("s3://bucket/data/")
# Result: data/year=2024/month=11/day=15/part-0000.parquet

# When to partition:
# - Column is frequently used in WHERE clause
# - Column has low-to-medium cardinality (not user_id with 10M values)
# - Data access is often for a slice of time/geography

# File size optimization — target 128MB–1GB per file
# Too small: many file open operations (S3 has overhead per file)
# Too large: parallelism suffers (one task per file)

df.coalesce(optimal_partitions).write.parquet(output_path)

# Optimal partition formula:
total_data_size_bytes = 500 * 1024**3  # 500 GB
target_partition_size = 256 * 1024**2   # 256 MB
optimal_partitions = total_data_size_bytes // target_partition_size  # ~2000
```

### Fault Tolerance Design
```python
# Idempotent pipeline design (can run multiple times safely)
class IdempotentLoader:
    def load(self, df, target_table: str, partition_key: str, partition_value: str):
        """
        DELETE partition then INSERT = idempotent.
        Running twice gives same result.
        """
        spark.sql(f"""
            DELETE FROM {target_table}
            WHERE {partition_key} = '{partition_value}'
        """)
        
        df.write.format("delta").mode("append").saveAsTable(target_table)

# Checkpointing for streaming
query = df_stream.writeStream \
    .option("checkpointLocation", "/checkpoints/stream_name") \
    .start()
# If stream crashes and restarts, it continues from last checkpoint

# Dead letter queues for failed records
def process_with_dlq(records: list, dlq_path: str):
    successful = []
    failed = []
    
    for record in records:
        try:
            result = transform(record)
            successful.append(result)
        except Exception as e:
            failed.append({"record": record, "error": str(e), "timestamp": datetime.utcnow().isoformat()})
    
    if failed:
        write_to_dlq(failed, dlq_path)  # For investigation and reprocessing
    
    return successful
```

### High Availability and Scalability

**Horizontal Scaling (add more machines):**
- Kafka: Add brokers, increase partitions
- Spark: Add executor nodes
- Snowflake: Scale warehouse up/down automatically

**Data Skew Handling:**
```python
# Detect skew
df.groupBy(F.spark_partition_id()).count().show()

# Solutions:
# 1. Salting (add random prefix to skewed key)
# 2. Broadcast join (for small dimension tables)
# 3. AQE (Spark 3.x handles automatically)
# 4. Repartition before join
```

**CAP Theorem for Data Engineers:**
- **Consistency:** Every read gets the most recent write
- **Availability:** Every request gets a response
- **Partition Tolerance:** System works despite network failures

Data systems choose 2 of 3:
- **CA (no partition tolerance):** Traditional RDBMS — inconsistent choice for distributed systems
- **CP (consistency + partition tolerance):** HBase, Zookeeper — consistent but may be unavailable during partition
- **AP (availability + partition tolerance):** Cassandra, CouchDB — always available but eventually consistent

For analytics pipelines: **AP** is usually acceptable (eventual consistency is fine for dashboards)

---

# 17. INTERVIEW PREPARATION

## 🎯 SQL Interview — 30-Day Sprint

**Week 1:** Review all JOIN types, practice 20 LeetCode Easy SQL
**Week 2:** Window functions daily — 3 problems per day
**Week 3:** CTEs, subqueries, 5 complex business scenario queries
**Week 4:** Mock interviews — 3 timed SQL sessions

**Top SQL Interview Questions at Product Companies:**
1. Find users who logged in every day for the past 7 days
2. Calculate 7-day rolling revenue by region
3. Find the second highest salary per department
4. Identify churned customers (no purchase in 90 days)
5. Compute month-over-month growth rate
6. Find duplicate records and keep only the latest
7. Build a simple cohort retention analysis
8. Find sessions from clickstream data (gaps > 30 min = new session)

## 💡 PySpark Interview Questions

**Architecture:**
- Explain Spark's DAG execution model
- What is lazy evaluation and why is it important?
- Explain the difference between a transformation and an action
- What causes a shuffle? How do you minimize shuffles?
- Explain Catalyst optimizer and Tungsten execution engine

**Performance:**
- How do you handle data skew in Spark?
- When would you use `repartition` vs `coalesce`?
- When should you use `broadcast` join?
- How does partition pruning work?
- Explain AQE (Adaptive Query Execution)

**Code questions:**
- Write PySpark to compute rolling 7-day average
- Implement a SCD Type 2 MERGE in Delta Lake
- Read from Kafka, filter, and write to Delta with checkpointing

## 🌐 System Design Interview — Data Engineering Style

**Common questions:**
1. Design a real-time fraud detection system
2. Design Twitter's data pipeline (10B tweets/day)
3. Design a data warehouse for an e-commerce company
4. Design a CDC pipeline from MySQL to a data lake
5. Design a platform that serves 1000 data scientists

**Framework for answering:**
```
1. Clarify requirements (functional + non-functional)
   "How much data? What latency? What consistency requirements?"

2. Back-of-envelope calculations
   "10M events/day = ~115 events/second = low Kafka traffic"

3. High-level architecture (draw boxes)

4. Deep dive on key components

5. Identify bottlenecks and solutions

6. Handle edge cases (failures, schema changes, backfills)

7. Discuss trade-offs of your choices
```

## 🔥 Kafka Interview Questions

1. What is a consumer group and why does it matter?
2. What happens when a consumer goes down mid-processing?
3. Explain exactly-once semantics in Kafka
4. What is log compaction and when would you use it?
5. How do you handle message ordering in Kafka?
6. What is the difference between at-least-once and exactly-once delivery?
7. How do you monitor consumer lag? What does high lag indicate?
8. How do you choose the number of partitions for a topic?

## 🌬️ Airflow Interview Questions

1. What is the difference between `execution_date` and `start_date`?
2. How do you pass data between tasks?
3. What is the difference between catchup and backfill?
4. How would you implement a dynamic DAG?
5. What is a sensor and when would you use one?
6. How do you handle cross-DAG dependencies?
7. Explain the difference between LocalExecutor, CeleryExecutor, and KubernetesExecutor

## 🏢 HR + Behavioral Interview Prep

**STAR Method for behavioral questions:**
- **S**ituation: Set the context
- **T**ask: What was your responsibility?
- **A**ction: What did you do specifically?
- **R**esult: What was the measurable outcome?

**Common behavioral questions for DE roles:**
1. Tell me about a time you dealt with bad data in production
2. Describe a technical decision you disagreed with. How did you handle it?
3. How do you prioritize when multiple pipelines are failing?
4. Tell me about a pipeline optimization you made. What was the impact?
5. How do you communicate technical issues to non-technical stakeholders?

**Prepare these answers before every interview:**
- 3 stories about handling failures/incidents
- 2 stories about cross-team collaboration
- 2 stories about optimization (performance or process)
- 1 story about learning from a mistake

---

# 18. GITHUB + PORTFOLIO ROADMAP

## 📁 Repository Structure Template

```
project-name/
├── README.md                    # Project overview (most important!)
├── architecture/
│   ├── architecture_diagram.png  # Draw with draw.io or Excalidraw
│   └── data_flow.md
├── src/
│   ├── __init__.py
│   ├── extractors/
│   ├── transformers/
│   └── loaders/
├── tests/
│   ├── unit/
│   └── integration/
├── configs/
│   ├── config.yaml
│   └── config.example.yaml      # Template without secrets
├── notebooks/
│   └── exploration.ipynb
├── docs/
│   └── technical_design.md
├── .github/
│   └── workflows/
│       └── ci.yml
├── docker-compose.yml
├── Dockerfile
├── requirements.txt
├── Makefile                     # Easy commands: make run, make test
└── .gitignore
```

## 📝 README Template (What Gets You Hired)

```markdown
# Project Title — One Sentence Description

![Architecture Diagram](architecture/architecture_diagram.png)

## 🎯 Business Problem
Describe the real business problem this solves. 
(What decision does this data enable? Who benefits?)

## 🏗️ Architecture
Walk through the diagram. Explain each component's role.

## 🛠️ Tech Stack
| Component | Technology | Why |
|-----------|-----------|-----|
| Ingestion | Kafka | Real-time, high throughput |
| Processing | PySpark on Databricks | Distributed, scalable |
| Storage | Delta Lake on ADLS | ACID + time travel |
| Orchestration | Apache Airflow | Complex dependency management |
| BI | Power BI | Business-friendly dashboards |

## 📊 Key Metrics
- Processes X events per second
- Pipeline latency: < Y minutes
- Data quality score: >99.9%

## 🚀 Quick Start
```bash
git clone https://github.com/you/project
cd project
cp configs/config.example.yaml configs/config.yaml
# Fill in your credentials
docker-compose up -d
make run
```

## 📖 Documentation
- [Technical Design](docs/technical_design.md)
- [Data Dictionary](docs/data_dictionary.md)
- [API Reference](docs/api_reference.md)

## 🧪 Running Tests
```bash
make test
```

## 📈 Results / Demo
Screenshots of dashboards. Link to live demo if available.
```

## LinkedIn Optimization Strategy

**Profile must-haves for DE roles:**
1. **Headline:** "Data Engineer | Python · PySpark · Azure · Databricks · SQL" (keywords!)
2. **About section:** Your specialization + what problems you solve + call to action
3. **Featured:** Your best GitHub project, any blog posts, certifications
4. **Experience:** Quantify everything — "Reduced pipeline runtime by 60%" not "improved pipeline"
5. **Skills:** Add all 15 core DE skills (recruiters filter by skills)
6. **Certifications:** Display DP-203, Databricks certs prominently
7. **Activity:** Post weekly about what you're learning/building

**Content to post (builds authority fast):**
- "I built X today. Here's what I learned about Y" (project posts)
- Share your blog posts explaining DE concepts simply
- Comment thoughtfully on posts by data engineering influencers
- Share insights from engineering blogs (Netflix, Airbnb)

---

# 19. CERTIFICATION ROADMAP

## 📜 Certifications That Actually Matter

### Tier 1 — High Value (Get These First)
| Certification | Provider | Value | Cost | Time |
|--------------|----------|-------|------|------|
| DP-203: Azure Data Engineer Associate | Microsoft | Very High | $165 | 2–3 months |
| Databricks Certified Data Engineer Associate | Databricks | Very High | $200 | 1–2 months |
| dbt Analytics Engineering | dbt Labs | High | Free | 2 weeks |
| Databricks Certified Associate Developer for Apache Spark | Databricks | High | $200 | 1–2 months |

### Tier 2 — Good Supporting Certs
| Certification | Provider | Value | Notes |
|--------------|----------|-------|-------|
| Snowflake SnowPro Core | Snowflake | High | Great if targeting Snowflake shops |
| Google Professional Data Engineer | Google | High | Better for GCP-heavy roles |
| AWS Data Analytics Specialty | AWS | High | Better for AWS-heavy roles |
| Confluent Certified Developer (Kafka) | Confluent | Medium | For streaming-focused roles |
| AZ-900: Azure Fundamentals | Microsoft | Low-Medium | Free prep, quick win |

### Certifications to Skip
- Generic "Big Data" certifications from Udemy (no employer recognition)
- Hadoop/Hive certifications (becoming obsolete)
- Old Spark certifications (not maintained)
- Certifications from platforms no one has heard of

### Recommended Order
```
Month 1-2: AZ-900 (builds Azure foundation, cheap)
Month 3-4: DP-203 (main Azure DE cert, highest ROI)
Month 5-6: Databricks Associate Data Engineer
Month 7:   Databricks Spark Developer Associate
Month 8+:  Snowflake SnowPro Core OR GCP Professional DE
```

## 🆓 Best Free Learning Resources

| Resource | What You Get | Best For |
|----------|-------------|----------|
| Databricks Academy | Free DE courses + Spark courses | Databricks, Spark |
| Microsoft Learn | Full DP-203 learning path | Azure |
| dbt Learn | Official dbt courses | dbt |
| Confluent Fundamentals | Kafka courses | Kafka |
| Snowflake University | Snowflake hands-on | Snowflake |
| Apache Airflow Docs | Tutorials and examples | Airflow |
| LeetCode (free tier) | 50-plan SQL problems | SQL |
| Mode Analytics | SQL exercises on real data | SQL |
| Google Colab | Free GPU/CPU notebooks | PySpark experiments |
| Databricks Community Edition | Free Spark + Delta Lake | PySpark, Delta |

---

# 20. DAILY/WEEKLY SCHEDULE

## 📅 Daily Learning Plan (3–4 hours/day)

```
⏰ Morning Block (1.5 hours — before day starts)
├── 30 min: SQL practice (1-2 problems on LeetCode/DataLemur)
├── 30 min: Read one engineering blog or documentation
└── 30 min: Work on current project

🌙 Evening Block (1.5 hours — after work/college)
├── 45 min: Study current phase topic
├── 30 min: Code implementation / project work
└── 15 min: Write 3 things learned today in a notebook
```

## 📊 Weekly Roadmap

| Day | Focus Area | Deliverable |
|-----|-----------|-------------|
| Monday | Primary skill (current phase) | 1 new concept implemented |
| Tuesday | SQL practice (2 problems) | GitHub commit |
| Wednesday | Project work | Feature added to project |
| Thursday | Primary skill (advanced topic) | Code + documentation |
| Friday | Interview prep (1 mock question) | Written answer |
| Saturday | Project + architecture thinking | Architecture diagram updated |
| Sunday | Review week, plan next week | Weekly learning log entry |

## 🗓️ Monthly Milestones

**Month 1:** Python mastery + SQL fundamentals + First mini-project
**Month 2:** Advanced SQL + Linux/Git + Beginner project on GitHub
**Month 3:** Data Warehousing concepts + PySpark basics + AZ-900 exam
**Month 4:** PySpark advanced + Databricks + Intermediate project
**Month 5:** Azure + Airflow + DP-203 exam prep
**Month 6:** Kafka streaming + Integration project + DP-203 exam

**Month 7:** Snowflake + dbt + Power BI + Apply for internships/junior roles
**Month 8:** Advanced projects + Databricks certification
**Month 9:** Mega project start + System design prep
**Month 10:** Mega project complete + Portfolio finalized
**Month 11:** Active job applications + Interview rounds
**Month 12:** Hired or close to offer stage

## 🚀 6-Month Milestone Targets

| Milestone | Target Date | Status |
|-----------|-------------|--------|
| Python + SQL solid fundamentals | Month 1 | |
| First project on GitHub | Month 2 | |
| AZ-900 certified | Month 3 | |
| PySpark + Databricks proficient | Month 4 | |
| DP-203 certified | Month 5 | |
| 3 projects on GitHub | Month 5 | |
| Kafka + Snowflake + dbt working | Month 6 | |
| First internship applications sent | Month 6 | |

---

# 21. AI-PROOF STRATEGY

## 🤖 What AI CAN Automate (Your Risk Area)

- Writing boilerplate ETL code
- Basic SQL queries and transformations
- Simple data cleaning scripts
- Generating test data
- Writing documentation from code
- Basic dashboard creation
- Finding bugs in simple pipelines

## 🛡️ What AI CANNOT Replace (Your Safe Harbor)

**1. Systems Thinking and Architecture Design**
AI can write code but cannot design a system that handles 10TB/day with sub-5-minute latency, handles schema evolution, maintains exactly-once semantics, and stays within a $50K/month cloud budget.

**2. Business Context Translation**
Converting "the finance team needs revenue by region but excluding returns before 30 days, except for premium customers" into the correct data model requires human judgment.

**3. Production Incident Response**
When a pipeline fails at 2 AM and 3 downstream dashboards are broken, a human with deep knowledge needs to diagnose, fix, and communicate.

**4. Data Governance and Privacy**
Understanding GDPR implications, implementing PII masking, designing retention policies — requires legal understanding + technical implementation.

**5. Cross-Team Collaboration**
Negotiating schema standards, evangelizing data practices, building data literacy in non-technical teams.

**6. Novel Problem Solving**
Building the first ML feature pipeline, designing a new CDC approach for a legacy system no one has documented.

## 🔮 How to Evolve (10-Year Strategy)

**Year 1–2:** Master the core stack (this roadmap)
**Year 3–4:** Specialize in one area (ML infrastructure, Real-time systems, or Data Platform)
**Year 5–6:** Lead architecture decisions, mentor others, build platforms
**Year 7–10:** Staff Engineer / Architect / Director level

**Emerging areas to learn:**
- **AI/ML Infrastructure:** Feature stores (Feast), ML pipelines (MLflow, Kubeflow), LLM pipelines
- **Data Mesh:** Federated ownership, domain-oriented data products
- **DataOps:** Automated testing, CI/CD for data, observability platforms
- **Lakehouse Optimization:** Apache Iceberg, Apache Hudi (alternatives to Delta)
- **Open Source Contributions:** Building reputation in the community

**The AI-Proof Mindset:**
> Use AI as a force multiplier. A Data Engineer who uses AI tools effectively is 10x more productive than one who doesn't. Become the person who knows what to build, why, and how to validate it — then use AI to build it faster.

---

# 22. CAREER ROADMAP

## 📈 Realistic Growth Path

### Intern (0–6 months)
**Skills:** Python, SQL, basic ETL, one cloud platform
**Responsibilities:** Small feature additions, bug fixes, data analysis support
**Salary (India):** ₹10K–30K/month stipend
**Salary (Remote/International):** $2K–5K/month
**Mindset:** Learn aggressively, ask good questions, ship small things

### Junior Data Engineer (6 months – 2 years)
**Skills:** Python, PySpark, one cloud stack, basic Airflow, SQL (intermediate)
**Responsibilities:** Build and maintain pipelines, implement features from specs, fix production issues
**Salary (India):** ₹6–18 LPA
**Salary (US Remote):** $70K–$110K
**Mindset:** Understand the "why" behind every system you touch

### Mid-Level Data Engineer (2–5 years)
**Skills:** Full stack DE (this entire roadmap), system design, mentoring
**Responsibilities:** Design pipeline architecture, lead feature delivery, own reliability
**Salary (India):** ₹18–40 LPA
**Salary (US Remote):** $110K–$160K
**Mindset:** Optimize for impact; ask "what problem does this solve?"

### Senior Data Engineer (5–8 years)
**Skills:** Platform design, cost optimization, data strategy, cross-org influence
**Responsibilities:** Define technical direction, set standards, unblock teams, drive critical projects
**Salary (India):** ₹40–80 LPA
**Salary (US/Remote):** $150K–$220K
**Mindset:** Think in systems, not features. Build for the next engineer.

### Staff Engineer / Architect (8–12 years)
**Skills:** Org-level technical strategy, vendor evaluation, build vs buy decisions
**Responsibilities:** Define multi-year technical roadmap, partner with VP-level stakeholders
**Salary (India):** ₹80–150 LPA
**Salary (US):** $200K–$350K + equity
**Mindset:** The code you write matters less than the decisions you make.

### Director of Data Engineering (12+ years)
**Responsibilities:** Hire and grow teams, own data engineering organization, set culture
**Salary (US):** $250K–$450K+ + equity
**Mindset:** People are the product. Technical leadership is organizational leadership.

---

# 23. LEARNING STRATEGY

## 🧠 How to Learn Faster

### The Feynman Technique (Accelerated Understanding)
1. Learn a concept
2. Explain it in simple words as if teaching a 12-year-old
3. Find gaps in your explanation
4. Return to source, fill gaps
5. Simplify further

Apply this to every major concept (lazy evaluation, shuffle, SCD Type 2).

### The 70-20-10 Rule
- **70%** of learning happens through **doing** (projects, implementation)
- **20%** through **feedback** (code reviews, mentor questions, interviews)
- **10%** through **formal learning** (courses, books, documentation)

If you're spending more than 30% on courses, you're in tutorial hell.

### Escaping Tutorial Hell

**Signs you're in tutorial hell:**
- Finished 5 courses, can't build anything independently
- You can answer questions but only if they match the tutorial structure
- You copy-paste code without understanding it

**The cure:**
```
Rule: For every hour of watching/reading, spend 2 hours building.
Protocol: 
  1. Watch 20 min of content
  2. Close the tutorial
  3. Try to build what you saw from scratch
  4. Get stuck — THAT'S the learning
  5. Only look up specific errors, not re-watch the tutorial
  6. Commit your code to GitHub
```

### How to Think Like a Real Engineer

1. **Start with requirements:** What problem are we solving? Who uses this? What are the SLAs?
2. **Design before coding:** Draw the architecture, identify bottlenecks
3. **Write tests first (TDD mindset):** What should this function return for edge cases?
4. **Monitor everything:** A pipeline without metrics is flying blind
5. **Document as you go:** "Future you" will thank you
6. **Challenge assumptions:** "Why are we storing data this way?" might save a company millions

### Professional Debugging

```python
# Debugging framework for Data Engineers
# 1. Reproduce the issue in isolation
# 2. Understand what the expected behavior should be
# 3. Form a hypothesis
# 4. Test the hypothesis (one change at a time)
# 5. Document the root cause and fix

# Common DE debugging patterns:
# Issue: Pipeline produces wrong numbers
# → Check: Source data (is input correct?)
# → Check: Transformation logic (print intermediate results)
# → Check: Join logic (are you losing or duplicating rows?)
# → Check: Aggregation (GROUP BY correct columns?)
# → Check: Time zones (are dates consistent?)

# Use Spark's explain() to debug query plans
df.explain(True)  # Shows logical plan, optimized plan, physical plan

# Sample and inspect data at each stage
df_bronze.sample(0.01).toPandas().to_csv("debug_bronze.csv")
df_silver.filter(F.col("order_id") == "ORD-12345").show(vertical=True)
```

### How to Become Top 1% in Data Engineering

The top 1% aren't the ones who know the most tools. They are:

1. **Reliability obsessed:** Their pipelines rarely break. When they do, they fix fast.
2. **Business aware:** They understand why the data matters to the company.
3. **Communication experts:** Can explain complex systems to any audience.
4. **Systems thinkers:** See how changes cascade through the entire data ecosystem.
5. **Continuous learners:** Read engineering blogs, contribute to open source, share knowledge.
6. **Mentors:** Make everyone around them better.

---

# 24. FINAL SECTION — THE EDGE

## ⚠️ Biggest Mistakes Beginners Make

1. **Over-planning, under-building** — 50 YouTube videos, zero commits
2. **Pursuing perfection** — The first project doesn't need to be perfect; it needs to exist
3. **Ignoring fundamentals** — Not knowing why a shuffle is slow. Knowing commands without understanding concepts.
4. **Studying tools instead of problems** — "I'm learning Kafka" vs "I'm building a real-time order tracking system using Kafka"
5. **Networking avoidance** — Most jobs come through referrals. The tech matters less than the human network.
6. **Resume over-claiming** — Claiming "expert in PySpark" when you've done one tutorial. Interviewers will find out.
7. **Giving up at hard problems** — The debugging session you almost quit is the one that teaches you the most.

## 💎 Most Underrated Skills

1. **Data modeling intuition** — Designing schemas that last years without major refactoring
2. **Cost optimization** — Reducing cloud spend by 40% makes you extremely valuable
3. **Documentation writing** — The engineer whose systems everyone can maintain is invaluable
4. **Observability design** — Building pipelines with great logging, metrics, and alerting from day 1
5. **Cross-functional communication** — Translating "the pipeline is slow" into "customers see stale data for 4 hours, costing $X"
6. **Saying no strategically** — Knowing which work to take on and what to push back on
7. **Reading production logs** — Most juniors don't know how to find signal in log noise

## 🏆 Most Valuable Habits

| Habit | Frequency | Impact |
|-------|-----------|--------|
| SQL problem solving | Daily | Interview readiness, analytical sharpness |
| Engineering blog reading | 3x/week | Stay current, industry awareness |
| GitHub commit | Daily | Portfolio, consistency signal |
| Learning log | Daily | Retention, reflection |
| Code review practice | Weekly | Learn from others' patterns |
| System design thinking | Weekly | Architecture muscle |
| Networking (LinkedIn/Twitter) | Weekly | Opportunities, referrals |
| Teach something you learned | Weekly | Deepens understanding |

## 🌍 How to Become Internationally Employable

**Target markets:** US (highest pay), UK/Europe (work-life balance), Canada (immigration-friendly), Remote-first companies (best of both worlds)

**What international companies look for in Indian freshers:**
1. **Communication:** Clear written English is non-negotiable for remote roles
2. **GitHub with real projects:** Not toy projects — problem-solving projects
3. **Certifications:** Azure DP-203 + Databricks signals industry-standard knowledge
4. **Time zone flexibility:** Willingness to overlap with US/EU hours
5. **System design thinking:** Ability to discuss trade-offs, not just implementation

**Remote job boards to target:**
- LinkedIn (filter: Remote + Data Engineer + Entry Level)
- Remote.co
- We Work Remotely
- Toptal (high bar, high pay)
- Gun.io
- Arc.dev (specifically for remote developers)
- Turing.com

**Application strategy:**
1. Apply to 5 well-researched companies/week (better than 50 mass applications)
2. Customize each application with the specific tech stack from job description
3. Write a cover letter that mentions their specific engineering blog post or architecture
4. Get referrals — connect with Indian engineers at target companies on LinkedIn
5. Contribute to open-source tools the company uses (easiest way to get noticed)

## 🔗 Networking Strategy

**In the next 30 days:**
1. Follow 10 Data Engineering thought leaders on LinkedIn (Zach Wilson, Joe Reis, Tristan Handy)
2. Comment meaningfully on 3 posts per week (not just "great post!")
3. Connect with 2 Data Engineers who graduated from your college/background
4. Join: dbt Community Slack, Locally Optimistic Slack, Data Engineering Discord
5. Post one "what I learned building X" post on LinkedIn

**Long-term:**
- Contribute to open source projects (Airflow, dbt, Delta Lake all welcome PRs)
- Write a technical blog (Medium, Substack, personal site)
- Speak at a local meetup about a project you built
- Build a reputation for being genuinely helpful in communities

## 💼 Internship/Job Application Strategy

**Resume tips:**
- Lead with projects (not education) if you're a fresher
- Every bullet: Action → Technology → Quantified Impact
  - ❌ "Built data pipeline"
  - ✅ "Designed PySpark pipeline on Databricks that processed 50GB/day of transaction data, reducing report generation time from 4 hours to 15 minutes"
- Keep to 1 page (2 pages max after 3 years)
- Include GitHub link prominently

**Interview preparation timeline:**
- 4 weeks before application: Finalize GitHub portfolio
- 3 weeks before: Mock interview (SQL + system design)
- 2 weeks before: Research each target company's tech stack
- 1 week before: Practice behavioral answers (STAR format)
- Day before: Review your own projects — expect deep questions

**The secret weapon:** Build something using the company's own tech stack. If a company uses Databricks + Snowflake + dbt, your portfolio should have exactly those. Recruiters pattern-match.

---

## 🗺️ Your First 30 Days — START HERE

If this roadmap feels overwhelming, start with just this:

**Day 1:** Install VS Code, Python, Git. Create GitHub account.
**Day 2–7:** Python basics + write 1 small script daily
**Day 8–14:** SQL basics on LeetCode (the SQL 50 plan) — 2 problems/day
**Day 15–21:** Build the financial API pipeline project
**Day 22–30:** Document it on GitHub with a proper README

You'll have your first project live in 30 days. That's how careers start.

---

## 📚 Essential Reading List

**Books (read in this order):**
1. "Fundamentals of Data Engineering" — Joe Reis & Matt Housley
2. "Designing Data-Intensive Applications" — Martin Kleppmann
3. "The Data Warehouse Toolkit" — Ralph Kimball (dimensional modeling bible)
4. "Learning Spark, 2nd Edition" — O'Reilly (free with Safari)
5. "Kafka: The Definitive Guide" — O'Reilly (free on Confluent website)

**Blogs to follow:**
- databricks.com/blog
- airbyte.com/blog
- dbt Labs blog
- Locally Optimistic
- Netflix Tech Blog
- Uber Engineering
- Airbnb Engineering
- AWS Big Data Blog

---

*This roadmap was designed for maximum career velocity. The path is clear. The tools are listed. The projects are defined.*

*The only variable is you.*

*Start today.*

---
**Version 1.0 | Built for the next generation of Data Engineers**
*Review quarterly — technology evolves, but principles endure.*
