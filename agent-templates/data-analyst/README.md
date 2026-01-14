# Data Analyst Agent

A specialized agent for data analysis, statistical processing, and insights generation.

## 🎯 Purpose

The Data Analyst Agent is designed to handle analytical tasks related to:
- Data processing and transformation
- Statistical analysis and reporting
- Trend identification and forecasting
- Data quality assessment
- Insights generation from structured data

## 🛠️ Capabilities

### Available Tools

- **`read_file`**: Access data files, logs, and structured data sources
- **`memory_query`**: Query knowledge bases for historical data and context
- **`run_command`**: Execute data processing commands and scripts

### Permissions

- `read_file` - Read data files and logs
- `memory_query` - Query data repositories
- `run_command` - Execute analysis commands

## 📋 Use Cases

### 1. Performance Metrics Analysis

**Scenario**: Analyze system performance metrics over time

**Example Task**:
```
Analyze CPU and memory usage trends over the past month and identify patterns
```

**Agent Actions**:
1. Use `read_file` to access performance logs
2. Extract and process metrics data
3. Calculate statistics (averages, peaks, trends)
4. Identify patterns and anomalies
5. Generate analysis report with insights

### 2. Service Usage Statistics

**Scenario**: Generate usage statistics for services

**Example Task**:
```
Generate usage statistics for all services showing request counts, error rates, and response times
```

**Agent Actions**:
1. Use `read_file` to access service logs
2. Parse and aggregate data
3. Calculate statistics (counts, rates, averages)
4. Identify outliers and patterns
5. Generate statistical report

### 3. Data Quality Assessment

**Scenario**: Assess data quality and completeness

**Example Task**:
```
Assess the quality of telemetry data collected over the last week
```

**Agent Actions**:
1. Use `read_file` to access data files
2. Analyze data completeness
3. Identify missing or corrupted entries
4. Calculate quality metrics
5. Generate quality assessment report

### 4. Comparative Analysis

**Scenario**: Compare data across different time periods or sources

**Example Task**:
```
Compare system performance metrics from this week with last week
```

**Agent Actions**:
1. Use `read_file` to access both datasets
2. Extract comparable metrics
3. Calculate differences and ratios
4. Identify significant changes
5. Generate comparative analysis

### 5. Predictive Insights

**Scenario**: Generate insights for future planning

**Example Task**:
```
Analyze resource usage trends and predict when we'll need to scale
```

**Agent Actions**:
1. Use `read_file` to access historical data
2. Identify trends and growth patterns
3. Calculate projections
4. Query memory for similar historical patterns
5. Generate predictive insights report

## 🔄 Operating Principles

1. **Data-Driven**: Base conclusions on actual data
2. **Statistical Rigor**: Use appropriate statistical methods
3. **Context Awareness**: Consider historical and contextual factors
4. **Clear Visualization**: Present data in understandable formats
5. **Actionable Insights**: Provide recommendations based on analysis

## 📊 Output Format

The agent returns structured JSON:

```json
{
  "status": "ok" | "blocked" | "error",
  "report": "Data analysis findings and insights",
  "evidence": [
    "Statistical summaries",
    "Data samples",
    "Trend visualizations (text-based)",
    "Comparative metrics"
  ],
  "next_steps": [
    "Recommended actions based on insights",
    "Additional analysis suggestions"
  ]
}
```

## 🚀 Spawning the Agent

### Via Orchestrator API

```json
{
  "action_type": "ActionSpawnAgent",
  "details": {
    "name": "Data Analyst Agent",
    "mission": "Analyze performance metrics and generate insights",
    "permissions": [
      "read_file",
      "memory_query",
      "run_command"
    ]
  }
}
```

### Example Missions

- "Analyze CPU usage trends and identify optimization opportunities"
- "Generate weekly performance statistics report"
- "Assess data quality for telemetry collection"
- "Compare current metrics with historical baselines"
- "Predict resource needs based on usage trends"

## 📈 Analysis Techniques

### Statistical Methods
- Descriptive statistics (mean, median, mode)
- Trend analysis
- Comparative analysis
- Anomaly detection
- Forecasting

### Data Sources
- Performance logs
- Service metrics
- System telemetry
- Historical knowledge bases
- Configuration data

### Output Formats
- Statistical summaries
- Trend reports
- Comparative tables
- Quality assessments
- Predictive insights

## 📚 Related Templates

- **Research Analyst**: For deeper pattern recognition and research
- **System Administrator**: For operational tasks based on data insights
- **Security Watch**: For security metrics analysis

## 🔍 Example Interaction Flow

1. **Task Received**: "Analyze memory usage patterns and identify optimization opportunities"
2. **Data Collection**:
   - Read performance logs → `read_file path=/var/log/performance.log`
   - Query historical data → `memory_query query="memory usage patterns"`
3. **Analysis**:
   - Calculate statistics
   - Identify trends
   - Detect anomalies
4. **Insights**:
   - Optimization opportunities
   - Trend predictions
   - Recommendations
5. **Report**: Structured analysis with actionable insights

## 💡 Analysis Best Practices

1. **Multiple Data Points**: Use sufficient data for reliable analysis
2. **Context Consideration**: Account for external factors
3. **Statistical Validity**: Use appropriate methods
4. **Clear Communication**: Present findings clearly
5. **Actionable Recommendations**: Provide specific next steps

---

**Template Location**: `agent-templates/data-analyst/`  
**Manifest**: `manifest.yaml`  
**System Prompt**: `base_prompt.txt`
