[![Build Status](https://drone.element-networks.nl/api/badges/Ansible/role-ipa_ssl/status.svg)](https://drone.element-networks.nl/Ansible/role-ipa_ssl)

## SSL certificates powered by IPA
This role will provide SSL certificates for hosts that are enrolled in a IPA domain

# Requirements
Ansible collection requirements:
* community.general
* community.crypto
* freeipa.ansible_freeipa

The succesful execution of this role requires the following on the target hosts:

* Administrative access (we need to be able to run ```kinit -k```)
* Administrative credentials for FreeIPA
  Only required when you want to use certificate altnames, as these require Kerberos
  Principal Aliases to be defined in the IPA server.

# Usage
After fulfilling the requirements above this role can be used as follows:

* Install the role (either from Galaxy or directly from GitHub)
* Copy the defaults file to your inventory (or wherever you store them) and
  fill in the blanks
* Add the role to your master playbook
* Run Ansible
* ???
* Profit!

Keep in mind: This role does *NOT* reconfigure software to actually use those certs! It will create a group on your system 'ssl-cert' with access permissions to the certificate files.

# Limitations
This role will attempt to create Kerberos principals to allow for the certificates to be generated on the host. However, should that action fail (mostly because one or more of the principal aliases already exists) you need to address that manually for now.
