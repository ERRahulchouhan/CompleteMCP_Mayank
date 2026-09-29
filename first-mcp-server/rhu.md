# FastMCP with UV and Claude Desktop

This file shows the exact commands to run a FastMCP server with `uv` and register it with Claude Desktop on Windows.

## 1) Start the server directly with uv

From PowerShell:

```powershell
cd "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server"
& "C:\Users\rahul\.local\bin\uv.exe" run --with fastmcp fastmcp run "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server\recipebox_fastmcp.py"
```

This starts the MCP server in stdio mode. It will wait for a client like Claude Desktop to connect.

## 2) Use uv project mode

If you want to use the project directory explicitly:

```powershell
cd "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server"
& "C:\Users\rahul\.local\bin\uv.exe" run --project "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server" fastmcp run "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server\recipebox_fastmcp.py"
```

## 3) Register with Claude Desktop

Use this command to install the server into Claude Desktop:

```powershell
cd "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server"
& "C:\Users\rahul\.local\bin\uv.exe" run --project "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server" fastmcp install claude-desktop --config-path "C:\Users\rahul\AppData\Local\Packages\Claude_pzs8sxrjxfjjc\LocalCache\Roaming\Claude" "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server\mybox_fastmcp.py"
```

You should see output like:

```text
Successfully installed 'MyBox_Updated' in Claude Desktop
```

## 4) Use the recipe box server

To register the recipebox server instead:

```powershell
cd "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server"
& "C:\Users\rahul\.local\bin\uv.exe" run --project "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server" fastmcp install claude-desktop --config-path "C:\Users\rahul\AppData\Local\Packages\Claude_pzs8sxrjxfjjc\LocalCache\Roaming\Claude" "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server\recipebox_fastmcp.py"
```

## 5) Important notes

- Always use the Windows `uv.exe` path: `C:\Users\rahul\.local\bin\uv.exe`
- Always use full Windows file paths
- For Claude Desktop, keep `transport` as `stdio`
- If Claude does not show the server, close and reopen Claude after installation

## 6) Quick summary

```powershell
& "C:\Users\rahul\.local\bin\uv.exe" run --with fastmcp fastmcp run "E:\AgenticAI_Mayank_Aggarwal\Live-Class-2026\Complete MCP\first-mcp-server\recipebox_fastmcp.py"
```

This is the working pattern for this machine.
