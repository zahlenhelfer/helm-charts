# falco

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square)

This Chart deploys falco.

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://falcosecurity.github.io/charts | falco | 6.0.1 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| falco.customRules."CVE-2024-21626.yaml" | string | `"- rule: Suspicious Chdir Event Detected\n  desc: Detects a process changing a directory using a proc-based file descriptor.  \n  condition: >\n    evt.type=chdir and evt.dir=< and evt.rawres=0 and evt.arg.path startswith \"/proc/self/fd/\" \n  output: >\n    Suspicious Chdir event detected, executed by process %proc.name with cmdline %proc.cmdline under user %user.name (details=%evt.args proc.cmdline=%proc.cmdline evt.type=%evt.type evt.res=%evt.res fd=%evt.arg.fd nstype=%evt.arg.nstype proc.pid=%proc.pid proc.cwd=%proc.cwd proc.pname=%proc.pname proc.ppid=%proc.ppid proc.pcmdline=%proc.pcmdline proc.sid=%proc.sid proc.exepath=%proc.exepath user.name=%user.name user.loginuid=%user.loginuid user.uid=%user.uid user.loginname=%user.loginname group.gid=%group.gid group.name=%group.name container.id=%container.id container_name=%container.name image=%container.image.repository:%container.image.tag)\n  priority: ALERT\n  tags: [host, container]"` |  |
| falco.customRules.BASH-IN-CONTAINER | string | `"- rule: shell_in_container\n  desc: notice shell activity within a container\n  condition: >\n    spawned_process and \n    container and \n    proc.name = bash    \n  output: >\n    shell in a container\n    (user=%user.name container_id=%container.id container_name=%container.name \n    shell=%proc.name parent=%proc.pname cmdline=%proc.cmdline)    \n  priority: WARNING\n  tags: [container, shell, host]"` |  |
| falco.customRules.CVE-2024-23652 | string | `"- macro: create_symlink\n  condition: evt.type in (symlink, symlinkat) and evt.dir=<\n\n- list: sensitive_file_names\n  items: [/etc/shadow, /etc/sudoers, /etc/pam.conf, /etc/security/pwquality.conf]\n\n- list: sensitive_directory_names\n  items: [/, /etc, /etc/, /root, /root/]\n\n- rule: Create Symlink Over Sensitive Files\n  desc: Detect symlink created over sensitive files\n  condition: >\n    create_symlink and\n    (evt.arg.target in (sensitive_file_names) or evt.arg.target in (sensitive_directory_names) or evt.arg.target contains \"/var/spool/cron\" or evt.arg.target contains \"/var/cron\" or evt.arg.target contains \"/etc/cron\" or evt.arg.target contains \"/etc/security\" or evt.arg.target contains \"/usr/lib/cron\") \n  output: >\n    Symlinks created over sensitive files by process %proc.name with parent %proc.pname under user %user.name with cmdline %proc.cmdline executed on %container.name (user.name=%user.name user.loginuid=%user.loginuid proc.cmdline=%proc.cmdline target=%evt.arg.target linkpath=%evt.arg.linkpath evt.type=%evt.type evt.res=%evt.res proc.name=%proc.name proc.pname=%proc.pname proc.pid=%proc.pid proc.cwd=%proc.cwd proc.ppid=%proc.ppid proc.pcmdline=%proc.pcmdline user.uid=%user.uid user.loginname=%user.loginname container.id=%container.id container.name=%container.name image=%container.image.repository:%container.image.tag)\n  priority: ALERT\n  tags: [host,container]"` |  |
| falco.customRules.CVE-2024-23653 | string | `"- macro: container\n  condition: (container.id != host)\n\n- macro: container_started\n  condition: >\n    ((evt.type = container or\n    (spawned_process and proc.vpid=1)) and\n    container.image.repository != incomplete)\n\n- rule: Launch Privileged Container\n  desc: Detect the initial process started in a privileged container. Exceptions are made for known trusted images.\n  condition: >\n    container and ((evt.type = execve and proc.cwd startswith \"/proc/self/fd\") or (evt.type in (open, openat, openat2) and fd.name glob \"/proc/*/cwd/*\") or (evt.type in (symlink, symlinkat) and fs.path.target startswith \"/proc/self/fd/\")) and proc.name != \"runc:[1:CHILD]\"\n  output: CVE-2024-21626 exploited ( %container.info evt_type=%evt.type process=%proc.name command=%proc.cmdline )\n  priority: CRITICAL"` |  |
| falco.driver.ebpf.leastPrivileged | bool | `true` |  |
| falco.driver.enabled | bool | `true` |  |
| falco.driver.kind | string | `"ebpf"` |  |
| falco.driver.resources.limits.cpu | string | `"100m"` |  |
| falco.driver.resources.limits.memory | string | `"128Mi"` |  |
| falco.driver.resources.requests.cpu | string | `"10m"` |  |
| falco.driver.resources.requests.memory | string | `"64Mi"` |  |
| falco.falco.grpc.bind_address | string | `"unix:///run/falco/falco.sock"` |  |
| falco.falco.grpc.enabled | bool | `true` |  |
| falco.falco.grpc.threadiness | int | `8` |  |
| falco.falcoctl.artifact.follow.resources.limits.cpu | string | `"100m"` |  |
| falco.falcoctl.artifact.follow.resources.limits.memory | string | `"128Mi"` |  |
| falco.falcoctl.artifact.follow.resources.requests.cpu | string | `"10m"` |  |
| falco.falcoctl.artifact.follow.resources.requests.memory | string | `"64Mi"` |  |
| falco.falcoctl.artifact.install.resources.limits.cpu | string | `"100m"` |  |
| falco.falcoctl.artifact.install.resources.limits.memory | string | `"128Mi"` |  |
| falco.falcoctl.artifact.install.resources.requests.cpu | string | `"10m"` |  |
| falco.falcoctl.artifact.install.resources.requests.memory | string | `"64Mi"` |  |
| falco.falcosidekick.enabled | bool | `true` |  |
| falco.falcosidekick.resources.limits.cpu | string | `"50m"` |  |
| falco.falcosidekick.resources.limits.memory | string | `"128Mi"` |  |
| falco.falcosidekick.resources.requests.cpu | string | `"10m"` |  |
| falco.falcosidekick.resources.requests.memory | string | `"64Mi"` |  |
| falco.scc.create | bool | `false` |  |
| falco.serviceAccount.create | bool | `true` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
