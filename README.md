# fix-pipewire-in-VM
fix pipewire vmware workstation

1º
sudo mkdir -p ~/.config/wireplumber/wireplumber.conf.d/
2º
sudo nano ~/.config/wireplumber/wireplumber.conf.d/50-alsa-config.conf

3º paste

monitor.alsa.rules = [
  {
    matches = [
      { node.name = "~alsa_output.*" },
      { node.name = "~alsa_input.*" }
    ]
    actions = {
      update-props = {
        api.alsa.period-size = 1024
        api.alsa.headroom    = 8192
      }
    }
  }
]

4º
systemctl --user restart wireplumber pipewire pipewire-pulse
