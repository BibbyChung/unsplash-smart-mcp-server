## Quickly use the docker image

```bash
# set up by docker image
docker run -d \
  --restart always \
  --name unsplash-mcp \
  -e UNSPLASH_ACCESS_KEY=<your-unsplash-key> \
  bibbynet/unsplash-smart-mcp-server:latest
```

### Configure the MCP settings

```json
{
  "servers": {
    "unsplash-mcp": {
        "command": "docker",
        "args": ["exec", "-i", "unsplash-mcp", "tsx", "src/server.ts"],
        "env": {}
    }
  }
}
```

### Build the image

```bash
DOCKER_BUILDKIT=1 docker buildx build \
    --platform linux/amd64 \
    --tag bibbynet/unsplash-smart-mcp-server:<git-hash> \
    --tag bibbynet/unsplash-smart-mcp-server:latest \
    --push \
    -f ./Dockerfile \
    .
```

---