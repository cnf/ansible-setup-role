# Basic setup ansible role.

## Functionality

### Set system proxy

```
http_proxy: http://192.168.1.2:3128/
https_proxy: http://user:pass@192.168.1.2:3128/
ftp_proxy: http://1.2.3.4/
no_proxy: 192.168.0.1
yum_proxy:  http://1.2.3.4/
yum_proxy_username: some
yum_proxy_password: password
```

### Install EPEL on redhat

### Hostname
if `cfg_hostname` is set, the hostname will be made to match.

### Timezone
Set the timezone to `host_timezone`, or to `'UTC'` as a default.

### sysctl
Configure sysctl value.
```
sysctl_settings:
  - name: net.ipv4.tcp_fin_timeout
    value: 10
```
values will be read from: `sysctl_settings`, `sysctl_group_settings`, and `sysctl_host_settings`

### Basic packages
The following packages get installed:

  - vim
  - tree
  - htop
  - rsync
  - pip

### Install and configure NTP

```
ntpd_service: "{{ __ntpd_service }}"
ntpd_conf: "{{ __ntpd_conf }}"
ntpd_db_dir: "{{ __ntpd_db_dir }}"
ntpd_script_dir: "{{ __ntpd_script_dir }}"
ntpd_package: "{{ __ntpd_package }}"
ntpd_leap_seconds_url: "https://www.ietf.org/timezones/data/leap-seconds.list"

ntpd_upstreams: []
ntpd_pools: [ '0.pool.ntp.org', '1.pool.ntp.org', '2.pool.ntp.org', '3.pool.ntp.org' ]
```

### VMWare tools
VMWare tools get installed if the target is a VMWare guest.

## TODO: DNS, Users, ssh keys, groups