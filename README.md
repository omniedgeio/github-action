# OmniEdge for Github Action

> CLI Version: 2.2.1

Bring Github Action into your private network. Access nodes/devices from CI workflows.

## Usage

### Edge Mode (VPN Client)

Connect your GitHub Action runner to your OmniEdge network:

```yaml
- name: OmniEdge
  uses: omniedgeio/github-action@v2
  with:
    mode: edge
    network_id: ${{ secrets.OMNIEDGE_NETWORK_ID }}
    security_key: ${{ secrets.OMNIEDGE_SECURITY_KEY }}
```

### Nucleus Mode (Signaling Server)

Run a signaling server in your workflow:

```yaml
- name: OmniEdge Nucleus
  uses: omniedgeio/github-action@v2
  with:
    mode: nucleus
    secret: ${{ secrets.OMNIEDGE_SECRET }}
```

### Dual Mode (VPN + Signaling)

Run both VPN client and signaling server:

```yaml
- name: OmniEdge Dual
  uses: omniedgeio/github-action@v2
  with:
    mode: dual
    network_id: ${{ secrets.OMNIEDGE_NETWORK_ID }}
    security_key: ${{ secrets.OMNIEDGE_SECURITY_KEY }}
    secret: ${{ secrets.OMNIEDGE_SECRET }}
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `mode` | OmniEdge mode: `edge`, `nucleus`, or `dual` | No | `edge` |
| `network_id` | Network ID (edge/dual) | Yes* | |
| `security_key` | Security key (edge/dual) | Yes* | |
| `secret` | Cluster secret (nucleus/dual, min 16 chars) | Yes* | |
| `port` | UDP port | No | `51820` |
| `as_exit_node` | Act as exit node | No | `false` |
| `exit_node` | Route traffic through exit node IP | No | |
| `verbose` | Enable debug logging | No | `false` |
| `version` | OmniEdge CLI version | No | `2.0.0` |

\* Required based on mode

## Exit Node

### As Exit Node

```yaml
- name: OmniEdge Exit Node
  uses: omniedgeio/github-action@v2
  with:
    mode: edge
    network_id: ${{ secrets.OMNIEDGE_NETWORK_ID }}
    security_key: ${{ secrets.OMNIEDGE_SECURITY_KEY }}
    as_exit_node: true
```

### Use Exit Node

```yaml
- name: OmniEdge
  uses: omniedgeio/github-action@v2
  with:
    mode: edge
    network_id: ${{ secrets.OMNIEDGE_NETWORK_ID }}
    security_key: ${{ secrets.OMNIEDGE_SECURITY_KEY }}
    exit_node: '10.0.0.1'
```

## Setup

1. [Sign up](https://omniedge.io) for an OmniEdge account
2. Create a network and get your Network ID from the dashboard
3. Generate a Security Key from the dashboard
4. Add secrets to your GitHub repository:
   - `OMNIEDGE_NETWORK_ID`
   - `OMNIEDGE_SECURITY_KEY`
   - `OMNIEDGE_SECRET` (for nucleus/dual mode)

## Links

- [OmniEdge](https://omniedge.io)
- [Documentation](https://omniedge.io/docs)
- [GitHub](https://github.com/omniedgeio/omniedge)
