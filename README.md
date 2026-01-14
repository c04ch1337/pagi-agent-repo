# PAGI Agent Repository

A distributed, self-learning network of AI agents for the Multi Digital Twin Platform. This repository serves as the global intelligence pool where agents share templates, playbooks, and knowledge.

## 🏛️ Repository Structure

```
pagi-agent-repo/
├── agent-templates/     # Agent manifest templates and system prompts
├── playbooks/            # AI-generated operational playbooks
├── core-values/          # Organizational values and principles
└── manifest.yaml         # Root repository manifest
```

## 🚀 Purpose

This repository enables:

1. **Agent Template Sharing**: Standardized agent configurations that can be discovered and deployed across nodes
2. **Knowledge Evolution**: Playbooks distilled from successful agent task completions
3. **Distributed Learning**: Each node contributes learned wisdom back to the global pool
4. **Community Collaboration**: Agents defined by the community for specialized tasks

## 📋 How It Works

### Agent Templates

The `agent-templates/` directory contains pre-configured agent definitions:
- **Manifest Files**: Define agent capabilities, tools, and permissions
- **System Prompts**: Specialized instructions for each agent type
- **Categories**: Organized by function (sys-admin, research, security, etc.)

### Playbooks

The `playbooks/` directory contains:
- **AI-Generated Guides**: Step-by-step procedures distilled from successful task completions
- **Best Practices**: Patterns extracted from agent execution logs
- **Lessons Learned**: Common pitfalls and how to avoid them

### Core Values

The `core-values/` directory contains:
- **Organizational Principles**: Values that guide agent behavior
- **Ethical Guidelines**: Standards for agent decision-making

## 🔄 Integration with Orchestrator

The orchestrator can:

1. **Sync Templates**: Use `ActionSyncAgentLibrary` to pull latest agent templates
2. **Discover Agents**: Automatically find and list available agent categories
3. **Spawn Agents**: Create new agents from templates with proper configuration
4. **Contribute Playbooks**: Automatically push learned playbooks back to this repository

## 📖 Getting Started

1. **Clone the Repository**:
   ```bash
   git clone git@github.com:c04ch1337/pagi-agent-repo.git
   ```

2. **Sync with Orchestrator**:
   - Use the orchestrator's `ActionSyncAgentLibrary` action
   - Templates will be organized into `config/agents/{category}/`

3. **Create Agents**:
   - Use discovered templates to spawn specialized agents
   - Each agent inherits its template's configuration and system prompt

## 🔐 Security & Privacy

- **Privacy Filtering**: All playbooks are automatically filtered to remove sensitive information
- **SSH Authentication**: Repository access requires configured SSH keys
- **Safety Checks**: Only files in `playbooks/` and `agent-templates/` can be pushed

## 🤝 Contributing

To contribute new agent templates:

1. Create a new directory in `agent-templates/{category}/`
2. Add `manifest.yaml` with agent configuration
3. Add `base_prompt.txt` with specialized system prompt
4. Submit a pull request or push directly (if authorized)

## 📚 Documentation

- See `TEST_SYNC.md` for testing the sync functionality
- See individual category READMEs for specific agent documentation
- See `playbooks/README.md` for playbook generation details

## 🌐 The Learning Loop

This repository is part of "The Blue Flame" distributed intelligence system:

1. **Local Execution**: Agents execute tasks on local nodes
2. **Memory Logging**: Successful completions are logged to Qdrant
3. **Consolidation**: Memory consolidator distills logs into playbooks
4. **Sharing**: Playbooks are pushed to this repository
5. **Discovery**: Other nodes sync and learn from shared knowledge

---

**Repository**: https://github.com/c04ch1337/pagi-agent-repo  
**Maintained by**: The Blue Flame Orchestrator Network
