pgadmin3 from Ubuntu Xenial (16.04 LTS)

## Usage

Example: `docker run --rm -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix:0 zfil/pgadmin3`

You can as well keep the container around (to keep the configuration settings between run inside the container).

Add this is your `.bashrc`

```
pgadmin3() {
    local state=$(docker inspect --format "{{.State.Running}}" pgadmin3 2>/dev/null)

    if [[ "$state" == "false" ]]; then
        docker start pgadmin3
    elif [[ "$state" != "true" ]]; then
        docker run --name pgadmin3 -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix:0 zfil/pgadmin3
    fi
}
```
