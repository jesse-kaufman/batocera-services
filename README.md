# Common Batocera Services

This repository holds various common Batocera services I use across multiple Batocera installs.

It includes:
1. aaa_mounts (mounts network filesystems)
2. mqtt (sends events to MQTT; _being deprecated soon_)
3. docker (Docker)

## Network Mounts (aaa_mounts)

This script mounts NFS shares from other machines inside Batocera (primarily for use in Docker containers).

### Config

Adjust MOUNTS variable as needed to add/remove mounts. Format is `[REMOTE_IP]:[REMOTE_MOUNT]\t[LOCAL MOUNT]`.

```bash
MOUNTS=(
    "192.168.22.11:/home/storage/media   /home/storage/media"
    "192.168.22.11:/home/storage/4tbhdd  /home/storage/4tbhdd"
    "192.168.22.10:/home/storage/2tbsdd/music  /home/storage/music"
)
```

## Docker (docker)

Starts Docker by mounting cgroup v1 mounts and starting dockerd.

### Config

1. Expects docker to be installed in `/userdata/system/docker` (so the docker binary is at `/userdata/system/docker/bin/docker`)
2. Expects bind mounts/compose files to be in `/userdata/system/docker/containers`
3. Expects docker data dir to be `/userdata/docker-data`
4. Logs are in `/userdata/system/docker`

## MQTT (mqtt)
