# Testing Agent Library Sync

This document describes how to test the `ActionSyncAgentLibrary` functionality.

## Prerequisites

1. SSH key configured: `~/.ssh/id_rsa` should have access to `git@github.com:c04ch1337/pagi-agent-repo.git`
2. Orchestrator running with the updated code
3. Repository structure matches expected format

## Test Steps

### 1. Test via Orchestrator API

Send a POST request to the orchestrator chat endpoint:

```json
{
  "message": "Sync agent library from GitHub",
  "twin_id": "test-twin",
  "namespace": "default"
}
```

Or use the direct action:

```json
{
  "action_type": "ActionSyncAgentLibrary",
  "details": {}
}
```

### 2. Expected Behavior

1. **First Run (Clone)**:
   - Clones repository to `config/agents/pagi-agent-repo/`
   - Scans `agent-templates/` directory
   - Copies each category to `config/agents/{category}/`
   - Lists available templates

2. **Subsequent Runs (Pull)**:
   - Pulls latest changes from `origin/main`
   - Updates local category directories
   - Lists available templates

### 3. Expected Output

The response should include:
- Success message: "Agent library synced successfully to config/agents"
- List of available templates:
  ```
  Available agent templates:
  - System Administrator Agent (sys-admin)
  - Research Analyst Agent (research)
  - Network Security Agent (network-security)
  ```

### 4. Verify Local Structure

After sync, check that these directories exist:
```
config/agents/
├── pagi-agent-repo/          # Cloned repository
├── sys-admin/
│   ├── manifest.yaml
│   └── base_prompt.txt
├── research/
│   ├── manifest.yaml
│   └── base_prompt.txt
└── network-security/
    ├── manifest.yaml
    └── base_prompt.txt
```

### 5. Test Template Parsing

Verify that templates can be parsed:
- Each `manifest.yaml` should be valid YAML
- `system_prompt_path` should point to `base_prompt.txt`
- `base_prompt.txt` should exist and be readable

## Troubleshooting

### SSH Authentication Issues
- Ensure `~/.ssh/id_rsa` exists
- Test SSH: `ssh -T git@github.com`
- Verify key is added to GitHub account

### Git Clone/Pull Failures
- Check network connectivity
- Verify repository is accessible
- Check git is installed: `git --version`

### Template Not Found
- Verify `agent-templates/` directory exists in repo
- Check category folders contain `manifest.yaml`
- Verify `system_prompt_path` points to correct file

### Parse Errors
- Validate YAML syntax in `manifest.yaml`
- Check required fields: `agent_name`, `category`
- Verify `base_prompt.txt` exists if `system_prompt_path` is set
