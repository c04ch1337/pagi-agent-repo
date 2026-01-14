# Agent Templates

This directory contains pre-configured agent templates that can be discovered and deployed by the orchestrator. Each template defines a specialized agent with specific capabilities, tools, and system prompts.

## 📁 Structure

Each agent template consists of:

- **`manifest.yaml`**: Agent configuration file defining:
  - Agent name and description
  - Category classification
  - Required tools and permissions
  - System prompt path
  - Privacy filter settings

- **`base_prompt.txt`**: Specialized system prompt that defines:
  - Agent mission and purpose
  - Available tools and capabilities
  - Operating principles
  - Output format requirements

## 🎯 Available Agent Categories

### System Administration (`sys-admin/`)
Specialized for system administration, service management, and infrastructure monitoring.

**Use Cases**:
- Service health monitoring
- Configuration file management
- System diagnostics
- Log analysis and troubleshooting

### Research Analyst (`research/`)
Focused on log analysis, data research, and pattern recognition.

**Use Cases**:
- Log file analysis
- Data pattern identification
- Historical research queries
- Trend analysis

### Network Security (`network-security/`)
Dedicated to network scanning, security analysis, and threat detection.

**Use Cases**:
- Internal network scanning
- Security vulnerability assessment
- Threat intelligence queries
- Network health monitoring

### Data Analyst (`data-analyst/`)
Specialized in data analysis, statistical processing, and insights generation.

**Use Cases**:
- Data processing and transformation
- Statistical analysis
- Report generation
- Data visualization insights

### Security Watch (`security-watch/`)
Focused on continuous security monitoring and threat detection.

**Use Cases**:
- Real-time security monitoring
- Threat detection
- Security event analysis
- Incident response support

## 🔄 How Templates Are Used

### 1. Discovery
The orchestrator syncs templates from this repository:
```json
{
  "action_type": "ActionSyncAgentLibrary",
  "details": {}
}
```

### 2. Organization
Templates are organized into `config/agents/{category}/` on the local node.

### 3. Spawning
Agents can be spawned from templates:
```json
{
  "action_type": "ActionSpawnAgent",
  "details": {
    "name": "System Administrator Agent",
    "mission": "Monitor service health",
    "permissions": ["read_file", "manage_service", "get_logs"]
  }
}
```

### 4. Execution
Spawned agents inherit:
- System prompt from `base_prompt.txt`
- Tool permissions from `manifest.yaml`
- Operating principles from the template

## 📝 Creating New Templates

To create a new agent template:

1. **Create Category Directory**:
   ```bash
   mkdir -p agent-templates/{category-name}/
   ```

2. **Create Manifest** (`manifest.yaml`):
   ```yaml
   agent_name: Your Agent Name
   description: What this agent does
   category: category-name
   required_tools:
     - tool1
     - tool2
   system_prompt_path: base_prompt.txt
   permissions:
     - permission1
     - permission2
   privacy_filter: true
   ```

3. **Create System Prompt** (`base_prompt.txt`):
   - Define agent mission
   - List available tools
   - Specify operating principles
   - Define output format

4. **Test Locally**:
   - Sync the library
   - Verify template appears in list
   - Test spawning an agent

5. **Push to Repository**:
   ```bash
   git add agent-templates/{category-name}/
   git commit -m "Add {category-name} agent template"
   git push origin main
   ```

## 🛠️ Available Tools

Agents can use these tools (defined in permissions):

- **`run_command`**: Execute shell commands
- **`read_file`**: Read files from filesystem
- **`write_file`**: Write files to filesystem
- **`manage_service`**: Control system services
- **`get_logs`**: Retrieve service logs
- **`inspect_system`**: Get system metrics
- **`memory_query`**: Query knowledge bases
- **`memory_commit`**: Write to knowledge bases

## 🔒 Security Considerations

- **Privacy Filtering**: Set `privacy_filter: true` to automatically redact sensitive data
- **Permission Scoping**: Only grant necessary permissions
- **Tool Restrictions**: Limit tools to what's required for the agent's mission

## 📚 Template Best Practices

1. **Clear Mission**: Define a specific, focused purpose
2. **Minimal Permissions**: Grant only necessary permissions
3. **Comprehensive Prompts**: Include all relevant context in system prompt
4. **Documentation**: Add README.md explaining use cases
5. **Testing**: Test templates before pushing

## 🔍 Finding Templates

After syncing, list available templates:
```json
{
  "action_type": "ActionSyncAgentLibrary",
  "details": {}
}
```

The response will include a list of all discovered templates with their categories.

---

For specific agent documentation, see the README.md in each category directory.
