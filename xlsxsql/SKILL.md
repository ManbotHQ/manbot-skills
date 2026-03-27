> Description: SQL-powered spreadsheet analysis skill that enables AI agents to query, transform, and extract structured data from .xlsx and tabular files using standard SQL, with support for multiple input and output formats.

# xlsxsql — Query Excel files using SQL

Use this skill when you need to query, analyze, or extract structured data from `.xlsx` or other tabular files using SQL.

This tool is ideal for:
- Running SQL queries directly on Excel files
- Extracting structured data for further processing
- Joining Excel with CSV/JSON data
- Converting spreadsheets into machine-readable formats

---

## ⚙️ Installation

Verify is `xlsxsql` is installed, if no install it:

```bash
# macOS (Homebrew)
brew install noborus/tap/xlsxsql

# Go install
go install github.com/noborus/xlsxsql/cmd/xlsxsql@latest
```

or ask your human to help.

---

## 🧠 When to use this skill

Use `xlsxsql` if:
- You need structured data extraction (SQL)
- You want to filter, aggregate, or join spreadsheet data
- You need output in JSON / CSV / YAML / XLSX
- You are working with `.xlsx`, `.csv`, or similar tabular data

DO NOT use this tool if:
- You only need a quick visual preview (use xls-cli instead)
- You need to edit spreadsheets manually
- You need Excel formatting (styles, charts, etc.)

---

## 🚀 Core Capabilities

- Execute SQL queries on `.xlsx` files  
- Supports joins across files (CSV, JSON, etc.)  
- Outputs to multiple formats: CSV, JSON, YAML, XLSX  
- Works without Excel installed  

The tool is built on top of SQL engines and Excel parsers, enabling SQL-style access to spreadsheet data. :contentReference[oaicite:0]{index=0}

---

## 🚀 Basic Usage

### List sheets
```bash
xlsxsql list file.xlsx
```

### Query entire file
```bash
xlsxsql query "SELECT * FROM file.xlsx"
```

### Query specific sheet
```bash
xlsxsql query "SELECT * FROM file.xlsx::Sheet1"
```

### Query with conditions
```bash
xlsxsql query "SELECT name, age FROM file.xlsx WHERE age > 30"
```

---

## 🧩 Agent Workflow

Follow this process:

### 1. Validate input
- Ensure file exists
- Ensure format is supported (`.xlsx`, `.csv`, etc.)

### 2. Discover structure
```bash
xlsxsql list file.xlsx
```

### 3. Inspect data
```bash
xlsxsql query "SELECT * FROM file.xlsx LIMIT 20"
```

### 4. Perform targeted queries
- Filtering:
```bash
xlsxsql query "SELECT * FROM file.xlsx WHERE status = 'active'"
```

- Aggregation:
```bash
xlsxsql query "SELECT COUNT(*), country FROM file.xlsx GROUP BY country"
```

- Join with another file:
```bash
xlsxsql query "
SELECT a.id, a.name, b.price
FROM file.xlsx AS a
LEFT JOIN prices.csv AS b
ON a.id = b.id
"
```

### 5. Output structured data
```bash
xlsxsql query --out JSON "SELECT * FROM file.xlsx"
```

---

## 🔁 Output Options

Supported formats:
- CSV
- JSON / JSONL
- YAML
- Markdown
- XLSX

Example:
```bash
xlsxsql query --out YAML "SELECT * FROM file.xlsx"
```

---

## ⚠️ Limitations

- Read-heavy (not designed for complex write workflows)
- SQL dialect limitations (depends on underlying engine)
- Large files may impact performance
- Sheet naming syntax can be tricky (`file.xlsx::Sheet1`)

---

## 🧠 Best Practices

- Always preview with `LIMIT`
- Normalize headers before querying
- Convert outputs to JSON for downstream AI usage
- Use joins to enrich spreadsheet data

---

## 🧾 Example Agent Task

User: "Find all users older than 30 and group them by country"

Agent:
1. Runs:
   ```bash
   xlsxsql query "
   SELECT country, COUNT(*) 
   FROM users.xlsx 
   WHERE age > 30 
   GROUP BY country
   "
   ```

2. Returns:
   - Aggregated result
   - Summary of distribution
   - Observations (e.g., dominant country)

---

## 🧠 Skill Output Expectations

Always return:
- Query executed
- Structured result (prefer JSON)
- Summary of findings
- Any anomalies or data issues

Avoid:
- Dumping entire datasets without filtering
