## Pipeline for deploying Prometheus to PCF

This pipeline sets up a Prometheus monitoring environment for 

It can target an ops manager BOSH director or a standalone bosh director to monitor/deploy to.

## Jobs

- **Upload Release**

  Uploads the Prometheus BOSH releases to the target director.

- **Create UAA Creds**

  Creates UAA Credentials both in Cloud Foundry and BOSH (requires Ops Manager for now)

- **Deploy**

  Performs the deployment

## Parameters:

  - `github_token`: A github token
  - `pcf_sys_domain`: PCF System Domain
  - `prometheus_bosh_client`: prometheus BOSH UAA client name
  - `prometheus_bosh_secret`: Secret for the prometheus BOSH UAA client
  - `prometheus_firehose_client`: Prometheus CF UAA client name
  - `prometheus_firehose_secret`: Secret for the prometheus CF UAA client
  - `prometheus_cf_client`: Username for the prometheus CF
  - `prometheus_cf_secret`: Password for the prometheus CF user
  - `deploy_azs`: Deployment AZs (Array)
  - `deploy_network`: Deployment Network
  - `deploy_vm_password`: SHA of the VM Password
  - `deploy_nginx_ip`: IP for front end server
  - `bosh_creds_source`: Source of BOSH credentials (`opsman` or `manual`)

Define what foundation to monitor and where to deploy prometheus 
  - `pcf_bosh_creds_source`: Use either `opsman` or `manual` to define where the monitored foundation exists
  - `deploy_bosh_creds_source`: Use either `opsman` or `manual` to define where prometheus will be deployed

Ops Man:
  - `pcf_opsman_admin_username`: Ops Manager admin username
  - `pcf_opsman_admin_password`: Ops Manager admin password
  - `opsman_url`: Ops Manager URL
  - `pcf_ert_domain`: Main CF Domain

Manual:
 - `bosh_username`: BOSH Director username
 - `bosh_password`: BOSH Director password
 - `director_ip`: BOSH Director IP
 - `bosh_ca`: BOSH CA certificate (if any)
 - `nats_machines`: NATS Machines
 - `nats_username`: NATS Username
 - `nats_password`: NATS Password
