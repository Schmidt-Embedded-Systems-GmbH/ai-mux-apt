# AI Mux Apt Repository

Public Debian apt repository for AI Mux.

## Install

```sh
sudo install -d -m 0755 /etc/apt/keyrings
curl -fsSL https://schmidt-embedded-systems-gmbh.github.io/ai-mux-apt/ai-mux.asc \
  | sudo tee /etc/apt/keyrings/ai-mux.asc >/dev/null

sudo tee /etc/apt/sources.list.d/ai-mux.sources >/dev/null <<'EOF'
Types: deb
URIs: https://schmidt-embedded-systems-gmbh.github.io/ai-mux-apt/
Suites: stable
Components: main
Architectures: amd64
Signed-By: /etc/apt/keyrings/ai-mux.asc
EOF

sudo apt update
sudo apt install ai-mux
```

## Signing Key

```text
F862 D3D0 8B98 4F8F 992B 2533 2390 2D63 2AAB 14C6
```
