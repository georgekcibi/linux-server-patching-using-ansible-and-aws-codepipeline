#### Automating Patching on Linux servers using Ansible and AWS codepipeline

### Advantage of this method is that we do not need to manage an Ansible server. The server will be deployed during pipeline execution. The playbook, Ansible inventory and  Ansible configuration can be managed via github repro.


### The buildspec.yml file consists of the commands that can be used to install ansible on the server being deployed and it can be used to deploy pipeline.

![Alt text](https://github.com/georgekcibi/linux-server-patching-using-ansible-and-aws-codepipeline/blob/main/codepipeline-patching.PNG.png)

### Ansible Playbook execution output

```
[Container] 2024/02/18 16:58:09.334363 Running command sudo ansible-playbook -i /root/ansible/hosts /root/ansible/playbook.yaml

PLAY [all] *********************************************************************

TASK [Gathering Facts] *********************************************************
ok: [server2]
ok: [server1]

TASK [Update facts about system type] ******************************************
ok: [server1]
ok: [server2]

TASK [Update RedHat systems] ***************************************************
skipping: [server1]
skipping: [server2]

TASK [Update Ubuntu systems] ***************************************************
skipping: [server1]
skipping: [server2]

TASK [Update SUSE systems] *****************************************************
skipping: [server1]
skipping: [server2]

TASK [check to see if we need a reboot] ****************************************
changed: [server1]
changed: [server2]

TASK [display result] **********************************************************
ok: [server1] => {
    "result.rc": "0"
}
ok: [server2] => {
    "result.rc": "0"
}

TASK [Reboot Server if Necessary] **********************************************
skipping: [server1]
skipping: [server2]

PLAY RECAP *********************************************************************
server1                    : ok=4    changed=1    unreachable=0    failed=0    skipped=4    rescued=0    ignored=0   
server2                    : ok=4    changed=1    unreachable=0    failed=0    skipped=4    rescued=0    ignored=0   


[Container] 2024/02/18 16:58:17.266186 Phase complete: BUILD State: SUCCEEDED
[Container] 2024/02/18 16:58:17.266205 Phase context status code:  Message: 
[Container] 2024/02/18 16:58:17.306440 Entering phase POST_BUILD
[Container] 2024/02/18 16:58:17.308034 Phase complete: POST_BUILD State: SUCCEEDED
[Container] 2024/02/18 16:58:17.308049 Phase context status code:  Message:
```

