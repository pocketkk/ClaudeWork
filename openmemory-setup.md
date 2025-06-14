# OpenMemory Setup Instructions

## Services Running

OpenMemory is now successfully running with the following services:

- **MCP Server**: `http://localhost:8765`
- **Dashboard**: `http://localhost:3000` 
- **Vector Database**: `http://localhost:6333`

## Configure Claude Desktop

To connect Claude Desktop to OpenMemory, you need to add the MCP server configuration:

### 1. Open Claude Desktop Settings

In Claude Desktop, go to Settings > Developer > Edit Config

### 2. Add OpenMemory MCP Server

Add the following configuration to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "openmemory": {
      "url": "http://localhost:8765/mcp/claude/sse/sylvia",
      "description": "Local memory server for persistent context"
    }
  }
}
```

Note: Replace `sylvia` in the URL with your desired username if different.

### 3. Restart Claude Desktop

After saving the configuration, restart Claude Desktop for the changes to take effect.

## Using OpenMemory

### Memory Operations

Once connected, you can use these memory operations in Claude:

1. **Add Memory**
   - Store important information, preferences, or context
   - Example: "Remember that I prefer using snap apps for Wave Terminal"

2. **Search Memory**
   - Retrieve relevant stored information
   - Example: "What do you know about my Wave Terminal setup?"

3. **List Memories**
   - View all stored memories
   - Useful for reviewing what's been saved

4. **Delete Memories**
   - Remove specific memories or clear all
   - Use when information is outdated

### Dashboard Access

Visit `http://localhost:3000` in your browser to:
- View all stored memories
- See memory usage statistics
- Monitor which tools are accessing memories
- Track memory history

## Docker Management

### Check Status
```bash
docker ps  # See running containers
```

### Stop OpenMemory
```bash
cd /home/sylvia/ClaudeWork/mem0/openmemory
make down
```

### Restart OpenMemory
```bash
cd /home/sylvia/ClaudeWork/mem0/openmemory
make up
```

### View Logs
```bash
docker logs openmemory-openmemory-mcp-1
```

## Important Notes

1. **Data Persistence**: All memory data is stored locally in Docker volumes
2. **Privacy**: No data leaves your machine - everything runs locally
3. **Backup**: The volume `openmemory_mem0_storage` contains your memory data

## Troubleshooting

### If services don't start:
1. Check Docker is running: `systemctl status docker`
2. Check port availability: `ss -tulpn | grep -E '3000|8765|6333'`
3. View logs: `docker compose logs`

### If Claude Desktop can't connect:
1. Verify services are running: `curl http://localhost:8765/health`
2. Check the MCP URL format is correct
3. Ensure Claude Desktop was restarted after config changes

## Memory Examples for Your Environment

Store these useful memories:
- "Wave Terminal snap config is at /snap/waveterm/114/.config/waveterm/widgets/widgets.json"
- "GitHub CLI is at /usr/bin/gh (not the shell alias)"
- "I use ClaudeWork directory for documentation and analysis"
- "Wave Terminal widgets should only show YouTube widget"