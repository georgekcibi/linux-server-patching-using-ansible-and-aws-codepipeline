##### Automating Patching on Linux servers using Ansible and AWS codepipeline

### Advantage of this method is that we do not need to manage an Ansible server. The server will be deployed during pipeline execution. The playbook, Ansible inventory and  Ansible configuration can be managed via github repro.


### The buildspec.yml file consists of the commands that can be used to install ansible on the server being deployed and it can be used to deploy pipeline.

