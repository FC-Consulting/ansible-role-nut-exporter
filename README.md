# Ansible Role: Network UPS Tools exporter

[![CI](https://github.com/FC-Consulting/ansible-role-nut-exporter/actions/workflows/ci.yml/badge.svg)](https://github.com/FC-Consulting/ansible-role-nut-exporter/actions/workflows/ci.yml)
[![Release](https://github.com/FC-Consulting/ansible-role-nut-exporter/actions/workflows/release.yml/badge.svg)](https://github.com/FC-Consulting/ansible-role-nut-exporter/actions/workflows/release.yml)

This role installs Prometheus' [NUT exporter](https://github.com/DRuggeri/nut_exporter) on Linux hosts, and configures a systemd unit file so the service can run and be controlled by systemd.

## Requirements

N/A

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    nut_exporter_version: '3.1.1'

The version of NUT exporter to install. Available releases can be found on the [tags](https://github.com/DRuggeri/nut_exporter/tags) listing in the NUT exporter repository. Drop the `v` off the tag.

If you change the version, the `nut_exporter` binary will be replaced with the updated version, and the service will be restarted.

    nut_exporter_arch: 'amd64'
    nut_exporter_download_url: https://github.com/DRuggeri/nut_exporter/releases/download/v{{ nut_exporter_version }}/nut_exporter-v{{ nut_exporter_version }}-linux-{{ nut_exporter_arch }}

The architecture and download URL for NUT exporter. If you're on a Raspberry Pi running Raspbian, you may need to override the `arch` value with `armv7`.

    nut_exporter_bin_path: /usr/local/bin/nut_exporter

The path where the `nut_exporter` binary will be installed.

    nut_exporter_host: 'localhost'
    nut_exporter_port: 9199

Host and port on which nut exporter will listen.

    nut_exporter_options: ''

Any additional options to pass to `nut_exporter` when it starts.

    nut_exporter_state: started
    nut_exporter_enabled: true

Controls for the `nut_exporter` service.

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - role: fc_consulting.nut_exporter

## License

MIT
