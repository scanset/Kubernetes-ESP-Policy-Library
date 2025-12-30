# Kubernetes ESP Policy Library

This repository contains a curated set of Endpoint State Policy (ESP) definitions for Kubernetes environments.

The policies are designed to validate security-relevant system and cluster state across Kubernetes control plane components, nodes, and supporting services. They align with widely used security frameworks and include negative-test cases for validation and testing.

**Total policies:** 27

---

## Policy Categories

### CIS Benchmarks

Policies aligned with CIS Kubernetes and Linux hardening guidance.

- **cis-2.1-dangerous-ports** — Ensures legacy services (Telnet, FTP, RPC portmapper) are not enabled.
- **cis-5.3.4-sudo-logfile** — Ensures sudo log file exists via `Defaults logfile` configuration.
- **cis-5.4.1.4-password-sha512** — Ensures password hashing algorithm is SHA-512.
- **cis-6.1.1-passwd-perms** — Ensures permissions on `/etc/passwd` are configured correctly (0644, root:root).

### DISA STIG — Kubernetes

Policies aligned with DISA Kubernetes STIG requirements.

- **stig-v242378-apiserver-tls** — API Server must have TLS certificates configured.
- **stig-v242379-etcd-tls** — etcd must have TLS configured.
- **stig-v242381-cm-service-account** — Controller Manager must use service account credentials.
- **stig-v242382-rbac-auth** — Kubernetes API Server must have RBAC authorization enabled.
- **stig-v242383-default-ns-services** — Default namespace must only have kubernetes service.
- **stig-v242384-scheduler-secure-bind** — Scheduler must be bound to localhost.
- **stig-v242385-cm-secure-bind** — Controller Manager must be bound to localhost.
- **stig-v242386-etcd-client-auth** — etcd must have client certificate authentication enabled.
- **stig-v242386-etcd-peer-auth** — etcd must have peer client certificate authentication enabled.
- **stig-v242388-no-insecure-bind** — API Server must not have insecure bind address.
- **stig-v242436-admission-plugins** — API Server must have admission plugins enabled.
- **stig-v245542-no-basic-auth** — API Server must not use basic authentication.
- **stig-v245543-no-token-auth** — API Server must not use static token authentication.
- **stig-v245544-kubelet-client-certs** — API Server must have kubelet client certificate configured.

### NIST 800-53

Policies aligned with NIST SP 800-53 audit controls.

- **nist-au9-audit-config-protection** — Protection of Audit Information - ensures auditd.conf has restrictive permissions.
- **nist-au12-audit-log-rotation** — Audit Generation - ensures log rotation is configured.

### MITRE ATT&CK (Defensive Mappings)

Policies mapped to ATT&CK techniques to detect or mitigate adversary behavior.

- **mitre-t1046-attack-surface** — Network Service Discovery - reduces attack surface by detecting unnecessary services (SMTP, MySQL, PostgreSQL).
- **mitre-t1133-ssh-hardening** — External Remote Services - validates SSH hardening (no root login, no password auth, no empty passwords).
- **mitre-t1562.001-audit-protection** — Impair Defenses Prevention - ensures audit config is protected from tampering.

### Negative / Validation Policies

Policies intentionally designed to fail under specific conditions to validate ESP behavior.

- **neg-nonexistent-pod** — Validates handling of missing Kubernetes resources (looks for non-existent pod).
- **neg-ssh-insecure** — Detects insecure SSH configuration that permits root login.
- **neg-sudo-nopasswd** — Detects sudo configurations allowing passwordless escalation via NOPASSWD.

---

## Usage

These `.esp` files are intended to be consumed by the ESP compiler and orchestrator as part of a Kubernetes security or compliance workflow.

Policies are framework-agnostic at execution time and can be evaluated independently or as part of a larger control set.