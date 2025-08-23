# fix-pipewire-in-VM
 install & fix pipewire vmware workstation


1º
*need install* pipewire wireplumber pipewire-pulse


2º
sudo mkdir -p ~/.config/wireplumber/wireplumber.conf.d/


3º
sudo nano ~/.config/wireplumber/wireplumber.conf.d/50-alsa-config.conf



4º paste

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



5º
systemctl --user restart wireplumber pipewire pipewire-pulse


*need install*  
in arch: pacman -S
in fedora: dnf install
in debian: apt
or your choice 
