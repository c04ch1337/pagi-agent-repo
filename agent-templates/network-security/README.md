# Network Security Agent

A specialized agent for network scanning, security analysis, and threat detection.

## 🎯 Purpose

The Network Security Agent is designed to handle security-focused tasks related to:
- Internal network scanning and discovery
- Security vulnerability assessment
- Threat intelligence queries
- Network health monitoring
- Security event analysis

## 🛠️ Capabilities

### Available Tools

- **`run_command`**: Execute network diagnostic commands (nmap, netstat, etc.)
- **`memory_query`**: Query threat intelligence and security knowledge bases
- **`read_file`**: Read network configuration files and security logs

### Permissions

- `run_command` - Execute network commands
- `memory_query` - Query threat intelligence
- `read_file` - Read network configs and logs

## 🔒 Security Constraints

**CRITICAL**: This agent operates under strict security constraints:

- **Internal Networks Only**: Network scanning is restricted to internal subnets:
  - `192.168.x.x` (Private Class C)
  - `10.x.x.x` (Private Class A)
  - `172.16-31.x.x` (Private Class B)
- **No External Scanning**: Never scan external/public IPs without explicit authorization
- **Policy Compliance**: Always respect corporate security policies
- **Threat Intelligence**: Query threat databases before taking actions

## 📋 Use Cases

### 1. Internal Network Discovery

**Scenario**: Discover devices and services on internal network

**Example Task**:
```
Scan the internal network (192.168.1.0/24) and identify all devices with ports 8281-8284 open
```

**Agent Actions**:
1. Verify target is internal subnet
2. Use `run_command` to execute network scan
3. Parse scan results
4. Identify AGI core nodes (ports 8281-8284)
5. Generate network map report

### 2. Security Vulnerability Assessment

**Scenario**: Assess network security posture

**Example Task**:
```
Assess the security posture of our internal network and identify any exposed services
```

**Agent Actions**:
1. Query threat intelligence → `memory_query namespace=threat_intel`
2. Scan internal network for open ports
3. Identify potentially vulnerable services
4. Cross-reference with threat intelligence
5. Generate security assessment report

### 3. Threat Intelligence Research

**Scenario**: Research known threats and vulnerabilities

**Example Task**:
```
Research known threats related to the services we're running
```

**Agent Actions**:
1. Use `read_file` to identify running services
2. Use `memory_query` to query threat intelligence
3. Correlate services with known vulnerabilities
4. Provide threat assessment

### 4. Network Health Monitoring

**Scenario**: Monitor network connectivity and health

**Example Task**:
```
Check network connectivity to all critical services
```

**Agent Actions**:
1. Use `run_command` to test connectivity
2. Identify connectivity issues
3. Analyze network paths
4. Generate health report

### 5. Security Event Analysis

**Scenario**: Analyze security-related events

**Example Task**:
```
Analyze firewall logs for suspicious activity
```

**Agent Actions**:
1. Use `read_file` to access firewall logs
2. Parse and analyze log entries
3. Query threat intelligence for context
4. Identify suspicious patterns
5. Generate security analysis report

## 🔄 Operating Principles

1. **Security First**: Prioritize system and network security
2. **Compliance**: Follow all security policies and guardrails
3. **Threat Awareness**: Query threat intelligence before actions
4. **Documentation**: Log all security-related findings
5. **Minimal Impact**: Use non-intrusive scanning methods

## 📊 Output Format

The agent returns structured JSON:

```json
{
  "status": "ok" | "blocked" | "error",
  "report": "Security analysis and findings",
  "evidence": [
    "Network scan results",
    "Threat intelligence data",
    "Security log excerpts",
    "Vulnerability assessments"
  ],
  "next_steps": [
    "Security recommendations",
    "Remediation steps",
    "Follow-up monitoring tasks"
  ]
}
```

## 🚀 Spawning the Agent

### Via Orchestrator API

```json
{
  "action_type": "ActionSpawnAgent",
  "details": {
    "name": "Network Security Agent",
    "mission": "Scan internal network and assess security",
    "permissions": [
      "run_command",
      "memory_query",
      "read_file"
    ]
  }
}
```

### Example Missions

- "Scan internal network and identify all AGI core nodes"
- "Assess security posture of internal services"
- "Research threats related to our current infrastructure"
- "Monitor network connectivity to critical services"
- "Analyze firewall logs for suspicious activity"

## 🛡️ Security Best Practices

### Network Scanning
- Always verify target is internal subnet
- Use appropriate scan intensity
- Respect rate limits
- Document all scans

### Threat Intelligence
- Query before taking actions
- Correlate findings with known threats
- Update threat intelligence with new findings
- Share discoveries with security team

### Log Analysis
- Review security logs regularly
- Identify patterns and anomalies
- Correlate with threat intelligence
- Document findings

## 📚 Related Templates

- **Security Watch**: For continuous security monitoring
- **System Administrator**: For security-related system tasks
- **Research Analyst**: For deeper security log analysis

## 🔍 Example Interaction Flow

1. **Task Received**: "Scan internal network for devices with port 8281 open"
2. **Validation**:
   - Verify target is internal subnet
   - Check scan authorization
3. **Execution**:
   - Execute network scan → `run_command cmd="nmap -p 8281 192.168.1.0/24"`
   - Query threat intelligence → `memory_query query="port 8281 security"`
4. **Analysis**:
   - Parse scan results
   - Identify devices
   - Assess security implications
5. **Report**: Security findings with recommendations

## ⚠️ Important Security Notes

- **Never scan external IPs** without explicit authorization
- **Respect rate limits** to avoid network disruption
- **Document all scans** for audit purposes
- **Query threat intelligence** before taking actions
- **Report suspicious activity** immediately

## 🔐 Compliance

This agent is designed to comply with:
- Corporate security policies
- Network scanning restrictions
- Threat intelligence sharing protocols
- Security audit requirements

---

**Template Location**: `agent-templates/network-security/`  
**Manifest**: `manifest.yaml`  
**System Prompt**: `base_prompt.txt`
