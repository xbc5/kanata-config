#!/usr/bin/env bash
set -euo pipefail

dir=$(dirname "$0")

# Source files
if [[ $(file -b "$dir/kanata") != ELF* ]]; then
  echo "kanata is not a binary" >&2
  exit 1
fi
if [[ $(file -b --mime-type "$dir/kanata.kbd") != text/* ]]; then
  echo "kanata.kbd is not text" >&2
  exit 1
fi

# Binary and config
sudo install -m 0755 "$dir/kanata" /usr/local/bin/kanata
sudo mkdir -p /etc/kanata
sudo install -m 0644 "$dir/kanata.kbd" /etc/kanata/kanata.kbd

# Uinput module
echo uinput | sudo tee /etc/modules-load.d/uinput.conf >/dev/null
sudo modprobe uinput

# Systemd service
sudo tee /etc/systemd/system/kanata.service >/dev/null <<'EOF'
[Unit]
Description=Kanata keyboard remapper

[Service]
ExecStart=/usr/local/bin/kanata --cfg /etc/kanata/kanata.kbd --no-wait
Restart=on-failure
RestartSec=3

[Install]
WantedBy=multi-user.target
EOF
sudo systemctl daemon-reload
sudo systemctl enable --now kanata.service
