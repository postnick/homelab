---
tags:
  - ssh
  - ssh-keygen
  - ed25519
  - linux
  - FirstSteps
---
Generate a new SSH Key with ed25519 encryption
```shell
ssh-keygen -t ed25519 
```

Copy that SSH-ID to your remote devices to allow for passwordless entry.
```shell
ssh-copy-id user@device
```






