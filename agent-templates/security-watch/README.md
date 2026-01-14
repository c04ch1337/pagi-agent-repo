# Security Watch Agent

A specialized agent for continuous security monitoring and threat detection.

## 🎯 Purpose

The Security Watch Agent is designed to handle continuous security monitoring tasks:
- Real-time security event monitoring
- Threat detection and alerting
- Security log analysis
- Incident response support
- Security posture assessment

## 🛠️ Capabilities

### Available Tools

- **`read_file`**: Access security logs, firewall logs, and audit logs
- **`memory_query`**: Query threat intelligence and security knowledge bases
- **`run_command`**: Execute security monitoring commands

### Permissions

- `read_file` - Read security logs and configs
- `memory_query` - Query threat intelligence
- `run_command` - Execute security commands

## 📋 Use Cases

### 1. Continuous Security Monitoring

**Scenario**: Monitor security events in real-time

**Example Task**:
```
Monitor security logs for the last hour and identify any suspicious activity
```

**Agent Actions**:
1. Use `read_file` to access recent security logs
2. Parse and analyze log entries
3. Query threat intelligence for context
4. Identify suspicious patterns
5. Generate security alert report

### 2. Threat Detection

**Scenario**: Detect potential security threats

**Example Task**:
```
Analyze firewall logs and detect any potential intrusion attempts
```

**Agent Actions**:
1. Use `read_file` to access firewall logs
2. Parse connection attempts and blocks
3. Query threat intelligence for known attack patterns
4. Identify suspicious activity
5. Generate threat detection report

### 3. Security Event Correlation

**Scenario**: Correlate security events across multiple sources

**Example Task**:
```
Correlate authentication failures with network access attempts
```

**Agent Actions**:
1. Use `read_file` to access multiple log sources
2. Parse and correlate events by time and source
3. Identify patterns and relationships
4. Query memory for historical context
5. Generate correlation analysis

### 4. Incident Response Support

**Scenario**: Support incident response activities

**Example Task**:
```
Investigate the security incident reported at 14:30 and provide analysis
```

**Agent Actions**:
1. Use `read_file` to access relevant logs
2. Query threat intelligence for related threats
3. Analyze timeline of events
4. Identify root cause
5. Generate incident analysis report

### 5. Security Posture Assessment

**Scenario**: Assess overall security posture

**Example Task**:
```
Assess our security posture based on recent security events and threat intelligence
```

**Agent Actions**:
1. Use `read_file` to access security logs
2. Query threat intelligence for current threats
3. Analyze security event patterns
4. Assess risk levels
5. Generate security posture report

## 🔄 Operating Principles

1. **Continuous Monitoring**: Maintain constant security awareness
2. **Threat Intelligence**: Always consult threat databases
3. **Rapid Response**: Quickly identify and report threats
4. **Comprehensive Analysis**: Consider multiple data sources
5. **Clear Alerting**: Provide actionable security alerts

## 📊 Output Format

The agent returns structured JSON:

```json
{
  "status": "ok" | "blocked" | "error" | "alert",
  "report": "Security monitoring findings and alerts",
  "evidence": [
    "Security log excerpts",
    "Threat intelligence data",
    "Suspicious activity patterns",
    "Risk assessments"
  ],
  "next_steps": [
    "Immediate security actions",
    "Investigation recommendations",
    "Mitigation steps"
  ]
}
```

## 🚀 Spawning the Agent

### Via Orchestrator API

```json
{
  "action_type": "ActionSpawnAgent",
  "details": {
    "name": "Security Watch Agent",
    "mission": "Monitor security events and detect threats",
    "permissions": [
      "read_file",
      "memory_query",
      "run_command"
    ]
  }
}
```

### Example Missions

- "Monitor security logs for suspicious activity"
- "Detect potential intrusion attempts"
- "Correlate security events across systems"
- "Investigate reported security incident"
- "Assess current security posture"

## 🛡️ Security Monitoring Focus Areas

### Event Types
- Authentication failures
- Unauthorized access attempts
- Unusual network activity
- System configuration changes
- Privilege escalations

### Threat Indicators
- Known attack patterns
- Suspicious IP addresses
- Anomalous behavior
- Policy violations
- Security misconfigurations

### Response Actions
- Immediate alerting
- Threat intelligence queries
- Log analysis
- Incident documentation
- Mitigation recommendations

## 📚 Related Templates

- **Network Security**: For network-focused security tasks
- **Research Analyst**: For deeper security log analysis
- **System Administrator**: For security-related system tasks

## 🔍 Example Interaction Flow

1. **Task Received**: "Monitor security logs for the last 2 hours"
2. **Data Collection**:
   - Read security logs → `read_file path=/var/log/security.log`
   - Query threat intelligence → `memory_query namespace=threat_intel`
3. **Analysis**:
   - Parse log entries
   - Identify suspicious patterns
   - Correlate with threat intelligence
4. **Detection**:
   - Identify threats
   - Assess risk levels
   - Generate alerts
5. **Report**: Security monitoring report with alerts and recommendations

## ⚠️ Security Alert Criteria

The agent should alert on:
- Multiple failed authentication attempts
- Unusual access patterns
- Known attack signatures
- Policy violations
- Anomalous network activity
- Security configuration changes

## 🔐 Compliance & Reporting

- **Audit Trail**: Document all security monitoring activities
- **Threat Intelligence**: Share findings with security team
- **Incident Documentation**: Maintain detailed incident records
- **Compliance**: Follow security policies and procedures

---

**Template Location**: `agent-templates/security-watch/`  
**Manifest**: `manifest.yaml`  
**System Prompt**: `base_prompt.txt`
