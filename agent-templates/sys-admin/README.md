# System Administrator Agent

A specialized agent for system administration tasks, service management, and infrastructure monitoring.

## 🎯 Purpose

The System Administrator Agent is designed to handle operational tasks related to:
- System health monitoring
- Service lifecycle management
- Configuration file operations
- Log analysis and diagnostics
- Infrastructure troubleshooting

## 🛠️ Capabilities

### Available Tools

- **`run_command`**: Execute diagnostic and administrative commands
- **`read_file`**: Inspect configuration files and logs
- **`write_file`**: Modify configuration files (with caution)
- **`manage_service`**: Start, stop, restart, enable, disable services
- **`get_logs`**: Retrieve service logs for analysis
- **`inspect_system`**: Get real-time system metrics (CPU, RAM, processes)

### Permissions

- `read_file` - Read system files
- `write_file` - Modify configuration files
- `manage_service` - Control services
- `get_logs` - Access service logs
- `run_command` - Execute commands
- `inspect_system` - View system metrics

## 📋 Use Cases

### 1. Service Health Monitoring

**Scenario**: Monitor critical services and alert on failures

**Example Task**:
```
Check the status of all telemetry services and report any that are not running
```

**Agent Actions**:
1. Use `inspect_system` to get current system state
2. Use `manage_service` to check service status
3. Use `get_logs` to review recent errors
4. Generate report with findings and recommendations

### 2. Configuration Management

**Scenario**: Update system configuration files safely

**Example Task**:
```
Update the telemetry service configuration to increase log retention to 7 days
```

**Agent Actions**:
1. Use `read_file` to read current configuration
2. Analyze configuration structure
3. Use `write_file` to update with new settings
4. Use `manage_service` to restart service if needed
5. Verify changes with `get_logs`

### 3. System Diagnostics

**Scenario**: Troubleshoot performance issues

**Example Task**:
```
Investigate why the system is experiencing high CPU usage
```

**Agent Actions**:
1. Use `inspect_system` to identify high-CPU processes
2. Use `run_command` to get detailed process information
3. Use `get_logs` to check for related errors
4. Analyze patterns and provide recommendations

### 4. Service Recovery

**Scenario**: Automatically recover failed services

**Example Task**:
```
The orchestrator service has stopped. Diagnose and restart it
```

**Agent Actions**:
1. Use `manage_service` to check service status
2. Use `get_logs` to identify failure cause
3. Use `run_command` for additional diagnostics
4. Use `manage_service` to restart service
5. Verify recovery with `inspect_system`

### 5. Log Analysis

**Scenario**: Analyze logs for patterns and issues

**Example Task**:
```
Review the last 100 log entries for the memory service and identify any errors
```

**Agent Actions**:
1. Use `get_logs` to retrieve recent logs
2. Parse and analyze log entries
3. Identify error patterns
4. Query memory for historical context
5. Generate analysis report

## 🔄 Operating Principles

1. **Safety First**: Always verify before making changes
2. **Documentation**: Log all actions and findings
3. **Minimal Impact**: Use least disruptive methods
4. **Clear Reporting**: Provide structured, actionable reports
5. **Recovery Planning**: Consider rollback strategies

## 📊 Output Format

The agent returns structured JSON:

```json
{
  "status": "ok" | "blocked" | "error",
  "report": "Detailed findings and actions taken",
  "evidence": ["Supporting data", "Log excerpts", "Command outputs"],
  "next_steps": ["Recommended actions", "Follow-up tasks"]
}
```

## 🚀 Spawning the Agent

### Via Orchestrator API

```json
{
  "action_type": "ActionSpawnAgent",
  "details": {
    "name": "System Administrator Agent",
    "mission": "Monitor and maintain system services",
    "permissions": [
      "read_file",
      "write_file",
      "manage_service",
      "get_logs",
      "run_command",
      "inspect_system"
    ]
  }
}
```

### Example Missions

- "Monitor all services and report any failures"
- "Update telemetry configuration and restart service"
- "Investigate high CPU usage and provide recommendations"
- "Review logs for the last 24 hours and identify issues"
- "Ensure all critical services are running and healthy"

## 🔒 Security Considerations

- **Read-Only by Default**: Prefer read operations unless modification is necessary
- **Backup Before Changes**: Consider backing up configs before modification
- **Service Impact**: Be aware of service restart impacts
- **Permission Scope**: Only request necessary permissions

## 📚 Related Templates

- **Research Analyst**: For deeper log analysis and pattern recognition
- **Network Security**: For network-related diagnostics
- **Security Watch**: For security-focused monitoring

## 🔍 Example Interaction Flow

1. **Task Received**: "Check why the telemetry service keeps restarting"
2. **Investigation**:
   - Check service status → `manage_service status telemetry`
   - Review logs → `get_logs service=telemetry`
   - Check system resources → `inspect_system`
3. **Analysis**: Identify root cause from logs and metrics
4. **Action**: Restart service or apply fix
5. **Verification**: Confirm service is stable
6. **Report**: Provide structured findings and recommendations

---

**Template Location**: `agent-templates/sys-admin/`  
**Manifest**: `manifest.yaml`  
**System Prompt**: `base_prompt.txt`
