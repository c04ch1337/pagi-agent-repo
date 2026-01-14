# Research Analyst Agent

A specialized agent for log analysis, data research, and pattern recognition tasks.

## 🎯 Purpose

The Research Analyst Agent is designed to handle analytical tasks related to:
- Log file analysis and pattern recognition
- Historical data research
- Knowledge base queries
- Trend identification
- Data correlation analysis

## 🛠️ Capabilities

### Available Tools

- **`read_file`**: Read log files, data files, and configuration files
- **`memory_query`**: Search knowledge bases for historical context
- **`run_command`**: Execute research queries and data extraction commands

### Permissions

- `read_file` - Read log and data files
- `memory_query` - Query knowledge bases
- `run_command` - Execute research commands

## 📋 Use Cases

### 1. Log Pattern Analysis

**Scenario**: Identify recurring patterns in application logs

**Example Task**:
```
Analyze the orchestrator logs from the last week and identify any recurring error patterns
```

**Agent Actions**:
1. Use `read_file` to access log files
2. Parse and analyze log entries
3. Identify patterns (error frequencies, time patterns, etc.)
4. Use `memory_query` to check for similar historical issues
5. Generate pattern analysis report

### 2. Historical Research

**Scenario**: Research past incidents or configurations

**Example Task**:
```
Research how we handled similar network issues in the past
```

**Agent Actions**:
1. Use `memory_query` to search knowledge bases
2. Retrieve relevant historical context
3. Correlate with current situation
4. Extract lessons learned
5. Provide research summary

### 3. Data Correlation

**Scenario**: Find correlations between different data sources

**Example Task**:
```
Correlate system performance metrics with service restart events
```

**Agent Actions**:
1. Use `read_file` to access performance logs
2. Use `read_file` to access service logs
3. Use `run_command` to extract and process data
4. Identify correlations and patterns
5. Generate correlation analysis

### 4. Trend Analysis

**Scenario**: Identify trends over time

**Example Task**:
```
Analyze memory usage trends over the past month
```

**Agent Actions**:
1. Use `read_file` to access historical data
2. Use `run_command` to process and aggregate data
3. Identify trends and anomalies
4. Query memory for context
5. Generate trend report with visualizations (text-based)

### 5. Root Cause Research

**Scenario**: Investigate root causes of issues

**Example Task**:
```
Research the root cause of the authentication failures we're seeing
```

**Agent Actions**:
1. Use `read_file` to access relevant logs
2. Use `memory_query` to find related incidents
3. Analyze patterns and correlations
4. Identify potential root causes
5. Provide research findings with evidence

## 🔄 Operating Principles

1. **Thorough Analysis**: Examine data comprehensively
2. **Pattern Recognition**: Identify trends and anomalies
3. **Context Awareness**: Use memory queries for historical context
4. **Clear Documentation**: Present findings in structured format
5. **Evidence-Based**: Support conclusions with data

## 📊 Output Format

The agent returns structured JSON:

```json
{
  "status": "ok" | "blocked" | "error",
  "report": "Research findings and analysis",
  "evidence": [
    "Supporting data",
    "Pattern examples",
    "Historical references",
    "Statistical summaries"
  ],
  "next_steps": [
    "Recommended follow-up research",
    "Additional data sources to investigate"
  ]
}
```

## 🚀 Spawning the Agent

### Via Orchestrator API

```json
{
  "action_type": "ActionSpawnAgent",
  "details": {
    "name": "Research Analyst Agent",
    "mission": "Analyze logs and identify patterns",
    "permissions": [
      "read_file",
      "memory_query",
      "run_command"
    ]
  }
}
```

### Example Missions

- "Analyze error logs from the last 7 days and identify patterns"
- "Research historical incidents similar to the current issue"
- "Correlate system metrics with service events"
- "Identify trends in authentication failures"
- "Research best practices for the current problem"

## 🔍 Research Techniques

### Pattern Recognition
- Frequency analysis
- Time-series analysis
- Anomaly detection
- Correlation identification

### Data Sources
- Application logs
- System logs
- Performance metrics
- Historical knowledge bases
- Configuration files

### Analysis Methods
- Statistical analysis
- Pattern matching
- Trend identification
- Root cause analysis
- Comparative analysis

## 📚 Related Templates

- **System Administrator**: For operational tasks based on research findings
- **Network Security**: For security-focused research
- **Data Analyst**: For deeper statistical analysis

## 🔍 Example Interaction Flow

1. **Task Received**: "Research why authentication failures increased last week"
2. **Data Collection**:
   - Read authentication logs → `read_file path=/var/log/auth.log`
   - Query historical incidents → `memory_query query="authentication failures"`
3. **Analysis**:
   - Identify failure patterns
   - Correlate with system events
   - Compare with historical data
4. **Findings**:
   - Root cause identification
   - Pattern recognition
   - Trend analysis
5. **Report**: Structured research findings with evidence

## 💡 Research Best Practices

1. **Multiple Sources**: Consult multiple data sources
2. **Historical Context**: Always check historical knowledge
3. **Pattern Validation**: Verify patterns with multiple data points
4. **Clear Conclusions**: Support findings with evidence
5. **Actionable Insights**: Provide recommendations based on research

---

**Template Location**: `agent-templates/research/`  
**Manifest**: `manifest.yaml`  
**System Prompt**: `base_prompt.txt`
