# Stop All Docker Containers That Match A Filter

Pipe the output of `docker ps` using `-f` for filtering and `--format` to format the output to `xargs` which reads the items from standard input and executes the `docker stop` command on the items.

```bash
docker ps -f "name={name-filter}" --format "{format}" | xargs docker stop
```

## docker ps
https://docs.docker.com/engine/reference/commandline/ps/
```bash
docker ps [OPTIONS]
```

## docker ps filtering
https://docs.docker.com/engine/reference/commandline/ps/#filtering
> The filtering flag (`-f` or `--filter`) format is a `key=value `pair. If there is more than one filter, then pass multiple flags (e.g. `--filter "foo=bar" --filter "bif=baz"`)

This example displays containers whose name contains `bitwarden`
```bash
docker ps -f "name=*bitwarden*"
```

## docker ps formatting
https://docs.docker.com/engine/reference/commandline/ps/#formatting
> The formatting option (`--format`) pretty-prints container output using a Go template.

This example outputs the `ID` of the container
```bash
docker ps --format "{{.ID}}"
```

## docker stop
https://docs.docker.com/engine/reference/commandline/stop/
```bash
docker stop [OPTIONS] CONTAINER [CONTAINER...]
```

## xargs
https://man7.org/linux/man-pages/man1/xargs.1.html
```bash
xargs [options] [command [initial-arguments]]
```