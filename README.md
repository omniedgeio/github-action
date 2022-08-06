# OmniEdge for Github Action

Bring Github Action into intranet, access nodes/devices from CI workflows.

## Usage

```bash
- name: OmniEdge for Github Action
  uses: omniedgeio/github-action@v1
  with:
    securitykey: ${{ secrets.OMNIEDGE_SECURITY_KEY }}
    virtualnetworkid: ${{ secrets.OMNIEDGE_VIRTUALNETWORK_ID }}
```
      
1. [Sign up](https://omniedge.io/register) your account
2. Generate Security-key, and get the Virtual Network ID from [Dashboard](https://omniedge.io/dashboard)
3. Put your own Security-key and Virtual Network ID into your action


