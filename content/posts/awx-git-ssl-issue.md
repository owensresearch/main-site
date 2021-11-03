---
author: "Justin Owens"
date: 2021-11-02
title: "Ansible AWX SSL Issue w/ GitLab Playbooks"
---

## Primer
I have setup an internal GitLab server and hosted my Ansible playbooks.  AWX is running in a few docker containers on the Ansible server.  I created a new project and selected Git as the Source Control type.  On the first attempt to sync the content the below error appears:

```
PLAY [Update source tree if necessary] *****************************************
TASK [update project using git] ************************************************
fatal: [localhost]: FAILED! => {"changed": false, "cmd": ["/usr/bin/git", "fetch", "--tags", "origin"], "msg": "Failed to download remote objects and refs:  fatal: unable to access 'https://git.local.lab.domain/some-repo/ansible-scripts.git/': SSL certificate problem: unable to get local issuer certificate\n"}
PLAY RECAP *********************************************************************
localhost                  : ok=0    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0
```

## Fix
I tried everything from installing the GitLab HTTPS web certificate authority on the local Ansible server to playing with the global Git settings like below:

````
git config --global http.sslVerify false
````
Eventually I realized the certificate would need to be installed from within the *awx_task* docker container.

So let's run ``docker stats`` and identify the CONTAINER_ID of the *awx_task* container.

Then we will copy the certificate to the container.
````
docker cp ca_cert.pem 6fe4sadfasdf:/ca_cert.pem
````
Now let's enter the *awx_task* container shell.
````
docker exec -it 6fe4sadfasdf /bin/bash
````
At this point we can install the certificate.
````
mv ca_cert.pem /etc/pki/ca-trust/source/anchors/
````
````
update-ca-trust extract
````
Done!