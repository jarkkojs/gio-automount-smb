Install the systemd units:

```
mkdir -p ~/.config/systemd/user
cp -v gio-automount-smb.{timer,service} ~/.config/systemd/user
```

Create an automount script `~/.local/bin/gio-automount-smb`:

```
#!/usr/bin/env bash

gio mount smb://haaparousku/home || true
gio mount smb://haaparousku/music || true
```

Enable the service:

```
systemctl --user enable gio-automount-smb.service
systemctl --user enable gio-automount-smb.timer
systemctl --user start gio-automount-smb.timer
```

