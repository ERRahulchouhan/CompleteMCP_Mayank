# How to run this MCP server with Claude Desktop

This project is a FastMCP server. It must be started by Claude Desktop through the MCP config, not by running the file from a normal terminal alone.

## 1) Confirm the server works

From PowerShell in the project folder:

```powershell
cd "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server"
& "C:\Users\rahul\.local\bin\uv.exe" run --with fastmcp fastmcp run "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server\recipebox_fastmcp.py"
```

If it starts successfully, you will see output similar to:

```text
Starting MCP server 'RecipeBox_Updated' with transport 'stdio'
```

This is the expected behavior for a stdio MCP server: it waits for a client like Claude to connect.

## 2) Check the Claude config

The file [claude_desktop_config.json](../claude_desktop_config.json) must contain the Windows paths, not old macOS paths.

Example entry:

```json
{
  "mcpServers": {
    "RecipeBox_Updated": {
      "command": "C:\\Users\\rahul\\.local\\bin\\uv.exe",
      "args": [
        "run",
        "--with",
        "fastmcp",
        "fastmcp",
        "run",
        "E:\\AgenticAI_Mayank_Aggarwal\\Live-Class-2026\\Complete MCP\\first-mcp-server\\recipebox_fastmcp.py"
      ],
      "transport": "stdio"
    }
  }
}
```

Important notes:

- Use `C:\Users\rahul\.local\bin\uv.exe`
- Use the full Windows path to the Python file
- Use `transport: "stdio"`
- Avoid old `/Users/...` or `/opt/homebrew/...` paths

## 3) Restart Claude Desktop

After updating the config:

1. Close Claude Desktop completely
2. Reopen Claude Desktop
3. Go to the MCP / tools section
4. Reload or reconnect the server

## 4) If Claude still does not detect it

Sometimes Claude uses a different config file location than the workspace copy. In that case, open the real Claude Desktop config file on Windows and copy the same values there.

The workspace file is:

```text
E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\claude_desktop_config.json
```

## 5) Server names

This project contains multiple examples:

- `recipebox_fastmcp.py` -> server name: `RecipeBox_Updated`
- `mybox_fastmcp.py` -> server name: `MyBox_Updated`

If you want to use `mybox_fastmcp.py`, make the Claude config entry match the same name and file path.

Example:

```json
"MyBox_Updated": {
  "command": "C:\\Users\\rahul\\.local\\bin\\uv.exe",
  "args": [
    "run",
    "--with",
    "fastmcp",
    "fastmcp",
    "run",
    "E:\\AgenticAI_Mayank_Aggarwal\\Live-Class-2026\\Complete MCP\\first-mcp-server\\mybox_fastmcp.py"
  ],
  "transport": "stdio"
}
```

## 6) Summary

The key idea is simple:

- MCP server runs as a stdio process
- Claude starts it by command + args
- On Windows, the command path must be the local `uv.exe`
- The file path must be a valid Windows path

This is the setup that works on this machine.
