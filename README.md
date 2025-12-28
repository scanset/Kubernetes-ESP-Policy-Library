# Kubernetes ESP Policy Library

This repository contains a curated set of Endpoint State Policy (ESP) definitions for Kubernetes environments.

The policies are designed to validate security-relevant system and cluster state across Kubernetes control plane components, nodes, and supporting services. They align with widely used security frameworks and include negative-test cases for validation and testing.

**Total policies:** 28

---

## Policy Categories

### CIS Benchmarks

Policies aligned with CIS Kubernetes and Linux hardening guidance.

- **cis-2.1-dangerous-ports** — Detects exposure of commonly dangerous or unnecessary network ports.
- **cis-5.3.4-sudo-logfile** — Ensures sudo activity is logged to a dedicated logfile.
- **cis-5.4.1.4-password-sha512** — Verifies password hashing uses SHA-512.
- **cis-6.1.1-passwd-perms** — Validates permissions on `/etc/passwd`.

### DISA STIG – Kubernetes

Policies aligned with DISA Kubernetes STIG requirements.

- **stig-v242378-apiserver-tls** — Ensures the Kubernetes API server is configured with TLS.
- **stig-v242379-etcd-tls** — Verifies etcd is configured to use TLS encryption.
- **stig-v242381-cm-service-account** — Ensures the controller manager uses a dedicated service account.
- **stig-v242382-rbac-auth** — Confirms RBAC authorization is enabled.
- **stig-v242383-default-ns-services** — Detects unauthorized services in the default namespace.
- **stig-v242384-scheduler-secure-bind** — Ensures the scheduler binds only to secure interfaces.
- **stig-v242385-cm-secure-bind** — Ensures the controller manager binds only to secure interfaces.
- **stig-v242386-etcd-client-auth** — Verifies etcd client authentication is enabled.
- **stig-v242386-etcd-peer-auth** — Verifies etcd peer authentication is enabled.
- **stig-v242388-no-insecure-bind** — Detects insecure bind addresses on Kubernetes components.
- **stig-v242436-admission-plugins** — Ensures required admission plugins are enabled.
- **stig-v245542-no-basic-auth** — Confirms basic authentication is disabled on the API server.
- **stig-v245543-no-token-auth** — Confirms token-based authentication is disabled where prohibited.
- **stig-v245544-kubelet-client-certs** — Ensures kubelet client certificates are in use.

### NIST 800-53

Policies aligned with NIST SP 800-53 audit controls.

- **nist-au9-audit-config-protection** — Ensures audit configurations are protected from modification.
- **nist-au12-audit-log-rotation** — Verifies audit logs are rotated to prevent exhaustion.

### MITRE ATT&CK (Defensive Mappings)

Policies mapped to ATT&CK techniques to detect or mitigate adversary behavior.

- **mitre-t1046-attack-surface** — Detects excessive or unnecessary network exposure.
- **mitre-t1133-ssh-hardening** — Validates SSH configuration to reduce external access risk.
- **mitre-t1562.001-audit-protection** — Detects attempts to disable or tamper with audit mechanisms.

### Negative / Validation Policies

Policies intentionally designed to fail under specific conditions to validate ESP behavior.

- **neg-nonexistent-pod** — Validates handling of missing Kubernetes resources.
- **neg-ssh-insecure** — Detects insecure SSH configuration.
- **neg-sudo-nopasswd** — Detects sudo configurations allowing passwordless escalation.

---

## Usage

These `.esp` files are intended to be consumed by the ESP compiler and orchestrator as part of a Kubernetes security or compliance workflow.

Policies are framework-agnostic at execution time and can be evaluated independently or as part of a larger control set.