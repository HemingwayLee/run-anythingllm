# run-anythingllm
## run by docker
* pull the image
```
docker pull mintplexlabs/anythingllm
```

* run with my local docker-compose file
```
docker-compose up
```

## How to use mcp server
* setup local mcp server with json and put it into container using docker-compose.yml
```
{
  "mcpServers": {
    "my-local-hello-mcp": {
      "command": "python3",
      "args": ["/app/hello_local_mcp_server.py"],
      "env": {
        "ANY_REQUIRED_KEY": "your_value"
      }
    }
  }
}
```

* my the mcp server I have is based on python
```
docker exec -u root -it ${CONTAINER_ID} bash
apt-get update
apt-get install -y python3-pip
pip3 install mcp --break-system-packages
```

* it shows
```
anythingllm  | [backend] info: [MCPHypervisor] Initializing MCP Hypervisor - subsequent calls will boot faster
anythingllm  | [backend] info: [MCPHypervisor] MCP Config File: /app/server/storage/plugins/anythingllm_mcp_servers.json
anythingllm  | [backend] info: [MCPHypervisor] Attempting to start MCP server: my-local-hello-mcp
anythingllm  | [backend] info: Shell environment path patched successfully.
anythingllm  | [backend] info: [MCPHypervisor] my-local-hello-mcp - Transport message: {"jsonrpc":"2.0","id":0,"result":{"protocolVersion":"2025-11-25","capabilities":{"experimental":{},"tools":{"listChanged":false}},"serverInfo":{"name":"hello-server","version":"1.26.0"}}}
anythingllm  | [backend] info: [MCPHypervisor] Successfully started 1 MCP servers: ["my-local-hello-mcp"]
```

