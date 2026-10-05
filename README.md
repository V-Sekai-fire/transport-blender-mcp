# transport-blender-mcp

A Blender addon and Model Context Protocol server that let an agent build and edit 3D scenes over a local socket.

## What it is for

An agent connected through MCP creates, edits and inspects objects and materials in a running Blender session, runs Python there and captures the viewport. The addon listens on a local socket and makes no outbound request. It derives from Siddharth Ahuja's MIT-licensed MCP addon, whose notice is kept in `LICENSE`.

## Build and run

Zip `addons/blender_mcp_addon`, install the zip in Blender as an extension, and enable it. The server is this package's `blender-mcp` command, registered with your MCP client; `docs/install.md` has the steps.

Run one MCP server at a time, because two clients fight over the Blender socket. The `execute_blender_code` tool runs arbitrary Python inside Blender.

## Licence

MIT; see `LICENSE`.
