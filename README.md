# Ansible Playbook for Let's Encrypt SSL Certificate Requests

This Ansible playbook automates the request and management of SSL certificates from Let's Encrypt using the ACME protocol. It helps you set up your environment, create private keys and CSRs, handle DNS challenges for certificate validation, and manage the certificate retrieval process.

## Requirements

Before running the playbook, ensure you have the following:

- **Ansible** installed on your local machine.
- A server with **root** access (for certificate management).

## Structure

The playbook is divided into multiple roles, each focusing on a specific task:

1. **pre_requisites**: Installs dependencies and prepares necessary directories.
2. **certificate_creation**: Handles the creation of private keys and Certificate Signing Requests (CSRs).
3. **acme_challenge**: Manages ACME challenges and retrieves certificates from Let's Encrypt.
4. **dns_update**: Manages DNS records to publish and remove challenge validation.

## Setup

### 1. In the `variables.yaml` file, set the variables based on your need.

### 2. In the inventory.ini file, set the target server IP address and user.

### 3. This playbook interacts with AWS for DNS updates. Set your AWS credentials as environment variables before running the playbook.

### 4. Run ansible-playbook -i inventory.ini site.yml

## Notes

The playbook uses AWS API for DNS updates, so ensure that your AWS credentials are correctly set. If you're using a different DNS provider, you'll need to modify the dns_update role to support it.

## Usage

To use this playbook, follow these steps:

1. Ensure you have met all the prerequisites mentioned above.

2. Clone this repository to your local machine:

`git clone https://github.com/audreyper/letsencrypt-certificates.git`

Navigate to the directory containing the playbook:

`cd <playbook-directory>`

Run the playbook:

`ansible-playbook playbook.yaml -i inventory.ini`
