# Ansible Role: Ghosts Server

An Ansible Role that installs [GHOSTS Server](https://github.com/cmu-sei/GHOSTS) on linux.

Based on the 8.2 version information

## Requirements

- Linux server
- Internet connection (docker images are 12GB)

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

- `LUDUS_GHOST_SERVER_UI_TAG`: Docker image tag for Ghosts Server UI (default: "0.0.7")
- `LUDUS_GHOST_GHOST_TAG`: Docker image tag for Ghosts core (default: "v8.3.1")
- `LUDUS_GHOST_SHADOWS_TAG`: Docker image tag for Shadows (default: "latest")
- `LUDUS_GHOST_PANDORA_TAG`: Docker image tag for Pandora (default: "2.0.0.0")
- `LUDUS_GHOST_OLLAMA_TAG`: Docker image tag for Ollama (default: "latest")
- `LUDUS_GHOST_POSTGRES_TAG`: Docker image tag for PostgreSQL (default: "13")
- `LUDUS_GHOST_GRAFANA_TAG`: Docker image tag for Grafana (default: "9.5.7")
- `LUDUS_GHOST_NGINX_TAG`: Docker image tag for Nginx (default: "1.25.3")


## Dependencies

Ansible :

- community.docker
- community.grafana
- geerlingguy.docker

## Ports

Ghosts UI (<https://cmu-sei.github.io/GHOSTS/core/ui/>):

- 8080

Ghosts API (<https://cmu-sei.github.io/GHOSTS/core/api/>)

- 5000
- 3000 grafana

shadows (<https://cmu-sei.github.io/GHOSTS/shadows/>):

- 5900 API
- 7860 UI

pandora (<https://cmu-sei.github.io/GHOSTS/content/>):

- 80

## Example Playbook

## Example Ludus Range Config

```yaml
ludus:
  - vm_name: "{{ range_id }}-Ghosts"
    hostname: "{{ range_id }}-Ghosts"
    template: ubuntu-24.04-x64-server-template
    vlan: 99
    ip_last_octet: 2
    ram_gb: 6
    cpus: 4
    linux: true
    roles:
      - frack113.ludus_ghosts_server
```

## License

[//]: # (If you change the License type, be sure to change the actual LICENSE file as well)
GPLv3

## Author Information

This role was created by [frack113](https://github.com/frack113), for [Ludus](https://ludus.cloud/).
