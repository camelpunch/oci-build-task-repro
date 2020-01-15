# Concourse oci-build-task repro for bad diff id

[jboss/keycloak:8.0.1](https://hub.docker.com/layers/jboss/keycloak/8.0.1/images/sha256-9a91f646de4becefbae9bd3e5e0cd8de21bf17a22055ccabff324798c2be68a0)
triggers the following error with this `run` script (script assumes you
have a `fly` target called `ci`).

I'm using Concourse 5.7.2

```
#4 unpacking docker.io/jboss/keycloak:8.0.1@sha256:9a91f646de4becefbae9bd3e5e0cd8de21bf17a22055ccabff324798c2be68a0
#4 unpacking docker.io/jboss/keycloak:8.0.1@sha256:9a91f646de4becefbae9bd3e5e0cd8de21bf17a22055ccabff324798c2be68a0 1.6s done
#4 ERROR: wrong diff id calculated on extraction "sha256:b9b09662851111407b73e7338db6a00216d21a6569b0a34162ade268f8363d81"
------
 > [1/1] FROM docker.io/jboss/keycloak:8.0.1@sha256:9a91f646de4becefbae9bd3e5e0cd8de21bf17a22055ccabff324798c2be68a0:
------
error: failed to solve: rpc error: code = Unknown desc = failed to solve with frontend dockerfile.v0: failed to build LLB: wrong diff id calculated on extraction "sha256:b9b09662851111407b73e7338db6a00216d21a6569b0a34162ade268f8363d81"
FATA[0007] failed to build: build: exit status 1
FATA[0007] failed to run task: exit status 1
failed
```
