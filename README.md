# fix-pipewire-in-VM
fix pipewire vmware workstation, 
- tested on Workstation 17.6.4: Windows 11 Host and Fedora 42 Guest

* ```mkdir -p ~/.config/wireplumber/wireplumber.conf.d/```

* ```vim ~/.config/wireplumber/wireplumber.conf.d/50-alsa-config.conf```

```
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
```

* ```systemctl --user restart wireplumber pipewire pipewire-pulse```
