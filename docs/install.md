# Install and use

## Blender addon

Blender 4.2 or later installs the addon as an extension from a zip of `addons/blender_mcp_addon`.

macOS and Linux:

```bash
git clone https://github.com/V-Sekai-fire/transport-blender-mcp
cd transport-blender-mcp/addons
zip -r ../blender_mcp_addon.zip blender_mcp_addon -x '*/__pycache__/*' '*.pyc'
```

Windows (PowerShell):

```powershell
git clone https://github.com/V-Sekai-fire/transport-blender-mcp
cd transport-blender-mcp\addons
Compress-Archive -Path blender_mcp_addon -DestinationPath ..\blender_mcp_addon.zip
```

Drag `blender_mcp_addon.zip` onto a Blender window and confirm, or pick it from **Edit > Preferences > Get Extensions > Install from Disk**. Enable **Blender MCP**. Settings are under **Edit > Preferences > Add-ons > Blender MCP** and in the 3D Viewport sidebar (`N`) on the **BlenderMCP** tab. The server starts with Blender unless **Auto-connect on Blender launch** is unchecked.

To update, rebuild the zip from a fresh checkout and install it again; preferences survive.

## MCP client

Install this package into a Python 3.10+ environment, which puts the `blender-mcp` console script on its path, and register that command with the MCP client:

```json
{
    "mcpServers": {
        "blender": {
            "command": "blender-mcp"
        }
    }
}
```

On Windows, some clients need the command wrapped as `cmd /c blender-mcp`. The client launches the server; do not start it by hand.

Run one MCP server at a time. Two clients each launching one fight over the Blender socket.

`BLENDER_HOST` (default `localhost`) and `BLENDER_PORT` (default `9876`) set where the server connects.

## Use

![BlenderMCP in the sidebar](../addons/blender_mcp_addon/assets/addon-instructions.png)

With the addon enabled and the client started, the tools appear in the client. The **Connect to MCP server** and **Disconnect from MCP server** button in the BlenderMCP panel starts and stops the socket by hand.

`execute_blender_code` runs arbitrary Python inside Blender with the user's permissions. Save work before letting an agent use it.

## Troubleshooting

- **No connection.** The panel reads "Disconnect from MCP server" when the socket is up. If it reads "Connect", autostart is off or the last start failed; click it.
- **Timeouts.** Break the request into smaller steps.
- **Persistent failures.** Restart Blender and the MCP client.
