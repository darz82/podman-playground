# Opengrok Service via Podman

Service runs as user 'opengrok' on port 3002.

Directories under /home/opengrok/Source are indexed and browsable under Opengrok.

The `opengrok.sh` script will deploy the pod and its container and then generate Systemd unit files for each.  These files are installed in `/home/opengrok/.config/systemd/user` and enabled via `systemctl --user enable ...`

## Example

```bash
[opengrok@birch opengrok]$ ./opengrok.sh 
Validating account opengrok...
opengrok:296608:65536
opengrok:296608:65536
Setting owner/group on /home/opengrok/Source...
Creating pod...
9f7e8be365eb1c9783292d4eb9268d51857af9de534e421516e65ed67f56efb9
Creating indexer container...
9fb6201233c198adb4627e996f0176c088f10e2c2c3540b23d0d38585cd59ee1
Creating /home/opengrok/.config/systemd/user...
Generating systemd unit files...
/home/opengrok/.config/systemd/user/pod-opengrok.service
/home/opengrok/.config/systemd/user/container-indexer.service
    Fixing target in container-indexer.service...
    Fixing target in pod-opengrok.service...
Reloading systemd...
Enabling systemd services...
    Enabling container-indexer.service...
Created symlink /home/opengrok/.config/systemd/user/default.target.wants/container-indexer.service → /home/opengrok/.config/systemd/user/container-indexer.service.
    Enabling pod-opengrok.service...
Created symlink /home/opengrok/.config/systemd/user/default.target.wants/pod-opengrok.service → /home/opengrok/.config/systemd/user/pod-opengrok.service.
/home/love/Development/podman-playground/opengrok
Opengrok service running on port 3002
```
