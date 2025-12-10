# WebOps Suite: Ansible Nginx + SSL + System Tuning

A curated collection of Ansible playbooks and roles focused on provisioning an Nginx web server with SSL and OS-level tuning on Linux hosts.

🚀 Overview  
These runbooks automate a complete web stack setup on Linux-based servers, providing reliable, reusable, and idempotent automation for:

🧱 Web server setup — Nginx installation, configuration, and reload handlers using Jinja2 templates  
🔐 SSL certificate management — deployment of `fullchain.pem` and `privatekey.pem`, with Nginx reload on certificate changes  
🧾 Application artifacts — shipping environment-specific configuration such as `web.cfg` to target nodes  
🛡 System hardening — OS tuning via `sysctl`, `limits.conf`, and systemd/user configuration files  
🔁 Infrastructure hygiene — role-based structure (`nginx`, `ssl`, `artifacts`, `system_config`) that is easy to extend, reuse, and maintain  

---

## 📂 Playbook & role structure

Main entry-point playbook:

```yaml
# site.yml
- name: Deploy and configure Nginx with SSL and artifacts
  hosts: begin-docker-test
  become: true
  roles:
    - nginx
    - ssl
    - artifacts
    - system_config
