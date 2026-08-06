# AI Mux Apt Repository

Public Debian apt repository for AI Mux.

## Install

```sh
sudo install -d -m 0755 /etc/apt/keyrings
curl -fsSL https://raw.githubusercontent.com/Schmidt-Embedded-Systems-GmbH/ai-mux-apt/main/ai-mux.asc \
  | sudo tee /etc/apt/keyrings/ai-mux.asc >/dev/null

sudo tee /etc/apt/sources.list.d/ai-mux.sources >/dev/null <<'EOF'
Types: deb
URIs: https://raw.githubusercontent.com/Schmidt-Embedded-Systems-GmbH/ai-mux-apt/main
Suites: stable
Components: main
Architectures: amd64
Signed-By: /etc/apt/keyrings/ai-mux.asc
EOF

sudo apt update
sudo apt install ai-mux
```

If an existing installation still uses the former GitHub Pages URL, update its
source before the next upgrade:

```sh
sudo sed -i \
  's#https://schmidt-embedded-systems-gmbh.github.io/ai-mux-apt/#https://raw.githubusercontent.com/Schmidt-Embedded-Systems-GmbH/ai-mux-apt/main#' \
  /etc/apt/sources.list.d/ai-mux.sources
sudo apt update
```

## Nightly Builds

A nightly build of the latest `main` is published to this repository as the
separate package `ai-mux-nightly`. It uses the same sources entry as the
stable package — after completing the install steps above, run:

```sh
sudo apt install ai-mux-nightly
```

Notes:

- `ai-mux-nightly` installs alongside `ai-mux`; you can keep both. It ships its
  own binary (`ai-mux-nightly`) and desktop entry, and stores its settings
  separately (`~/.config/ai-mux-nightly`).
- Nightly versions look like `0.0.14+nightly.<timestamp>.<commit>` and update
  via regular `sudo apt upgrade` whenever `main` has new commits.
- Nightlies are built straight from `main` without the manual release checks a
  stable release gets — expect occasional rough edges.

## Signing Key

```text
F862 D3D0 8B98 4F8F 992B 2533 2390 2D63 2AAB 14C6
```
