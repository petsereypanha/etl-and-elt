# ETL and ELT Data Engineering Project

A comprehensive collection of data engineering notebooks covering ETL (Extract, Transform, Load) pipelines, advanced techniques, and production deployment strategies.

## 📚 Project Overview

This project contains hands-on exercises and implementations for building robust data pipelines using Python, pandas, and various data engineering best practices. The notebooks progress from basic ETL concepts to advanced techniques and production deployment.

## 🗂️ Project Structure

```
ETL-and-ELT/
├── data/                          # Data files used in exercises
│   ├── clean_data.csv
│   ├── raw_data.csv
│   ├── raw_tax_data.csv
│   ├── transformed_data.csv
│   ├── testing_scores.json
│   ├── nested_school_scores.json
│   └── school.json
├── src/                           # Jupyter notebooks
│   ├── ETL-pipelines.ipynb
│   ├── data-pipelines.ipynb
│   ├── advanced-ETL-techniques.ipynb
│   └── deploying-and-maintaining-a-data-pipeline.ipynb
└── README.md
```

## 📓 Notebooks

### 1. ETL-pipelines.ipynb
**Core ETL Concepts**
- Extracting data from CSV files
- Transforming data with pandas
- Loading data to CSV and PostgreSQL databases
- Building modular ETL functions
- SQL-based transformations

**Key Topics:**
- Basic Extract, Transform, Load workflow
- Data filtering and column selection
- Database connections with SQLAlchemy
- CSV file operations

### 2. data-pipelines.ipynb
**Building Production-Ready Pipelines**
- Extracting from SQL databases and parquet files
- Advanced data transformations
- Data validation techniques
- Loading to various destinations
- Exception handling and logging

**Key Topics:**
- PostgreSQL integration with SQLAlchemy
- Parquet file handling
- Data type conversions (datetime)
- Custom CSV formatting (delimiters, headers)
- Pipeline monitoring and alerting
- Try-except error handling
- Logging best practices

### 3. advanced-ETL-techniques.ipynb
**Working with Complex Data Formats**
- JSON data extraction and parsing
- Nested dictionary manipulation
- Non-tabular data transformation
- Missing value imputation
- Data grouping and aggregation
- PostgreSQL database loading

**Key Topics:**
- `pd.read_json()` with different orientations
- Python's `json` library
- Dictionary iteration (keys, values, items)
- Nested data structure parsing
- `fillna()` for missing values
- DataFrame grouping with `apply()`
- Database validation queries

### 4. deploying-and-maintaining-a-data-pipeline.ipynb
**Testing and Production Deployment**
- Manual pipeline testing strategies
- Checkpoint validation
- Unit testing with pytest
- Fixtures and test organization
- Production architecture patterns
- End-to-end pipeline execution

**Key Topics:**
- Shape and equality validation
- `assert` statements
- `pytest` framework
- Test fixtures
- Idempotent pipeline design
- Production monitoring
- Logging configuration

## 🛠️ Technologies Used

- **Python 3.x**
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical operations
- **SQLAlchemy** - Database toolkit
- **PostgreSQL** - Relational database
- **pytest** - Testing framework
- **fastparquet** - Parquet file support
- **json** - JSON data handling
- **logging** - Pipeline monitoring

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy sqlalchemy psycopg2-binary fastparquet pytest
```

### Running the Notebooks

1. Clone this repository
2. Navigate to the `src/` directory
3. Launch Jupyter Notebook or JupyterLab
4. Open any notebook to explore the exercises

```bash
cd src/
jupyter notebook
```

## 💡 Key Concepts Covered

### ETL Best Practices
- **Modularity**: Breaking pipelines into reusable functions
- **Error Handling**: Try-except blocks for robust pipelines
- **Logging**: Tracking pipeline execution and debugging
- **Validation**: Ensuring data quality at each stage
- **Testing**: Unit tests and fixtures for reliability

### Data Pipeline Patterns
```python
# Standard ETL Pattern
def extract(source):
    """Extract data from source"""
    return raw_data

def transform(raw_data):
    """Transform and clean data"""
    return clean_data

def load(clean_data, destination):
    """Load data to destination"""
    # Store data
```

### Common Operations

**Reading from PostgreSQL:**
```python
import sqlalchemy
engine = sqlalchemy.create_engine("postgresql+psycopg2://user:pass@host:port/db")
df = pd.read_sql("SELECT * FROM table", con=engine)
```

**Writing to PostgreSQL:**
```python
df.to_sql(name="table", con=engine, if_exists="replace", index=False)
```

**JSON Handling:**
```python
# Simple JSON
df = pd.read_json("file.json", orient="records")

# Nested JSON
import json
with open("file.json", "r") as f:
    data = json.load(f)
```

## 📊 Example Use Cases

### Sales Data Pipeline
- Extract sales data from parquet files
- Transform: calculate totals, filter by price
- Load to CSV or database

### School Testing Scores
- Extract nested JSON school data
- Transform: normalize structure, fill missing values
- Load to PostgreSQL for analysis

### Tax Data Processing
- Extract from CSV
- Transform: calculate averages, filter outliers
- Validate and load to parquet

## 🧪 Testing

The project includes comprehensive testing examples:

```python
import pytest

@pytest.fixture()
def raw_data():
    return extract("data.csv")

def test_transform(raw_data):
    clean = transform(raw_data)
    assert isinstance(clean, pd.DataFrame)
    assert len(clean.columns) > 0
```

## 📈 Monitoring and Logging

```python
import logging

logging.basicConfig(level=logging.DEBUG)

try:
    raw = extract(source)
    clean = transform(raw)
    load(clean, destination)
    logging.info("Pipeline completed successfully")
except Exception as e:
    logging.error(f"Pipeline failed: {e}")
```

## 🎯 Learning Outcomes

After completing these notebooks, you will understand:

1. How to build end-to-end ETL pipelines
2. Working with various data formats (CSV, JSON, Parquet, SQL)
3. Data transformation and cleaning techniques
4. Production-ready error handling and logging
5. Testing data pipelines with pytest
6. Database integration patterns
7. Pipeline monitoring and validation strategies

## 📝 Notes

- Sample data is included in the `data/` directory
- PostgreSQL connection strings use placeholder credentials
- Notebooks are designed for educational purposes
- Each notebook builds upon concepts from previous ones

## 🤝 Contributing

This is a learning project. Feel free to:
- Add more examples
- Improve documentation
- Share alternative approaches
- Report issues

## 📄 License

This project is for educational purposes.

## 👤 Author

**Serey Panha**
- GitHub: [@petsereypanha](https://github.com/petsereypanha)
- Repository: [etl-and-elt](https://github.com/petsereypanha/etl-and-elt)

---

*Last Updated: November 3, 2025*
