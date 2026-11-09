# Rackview ML fitter releases

Signed release tarballs for the Rackview ML fitter (`rackview-ml-fit`), the nightly baseline fit that runs beside the Rackview edge on an appliance, in learning mode. One GitHub release per version (tag `ml-vX.Y.Z`). This repository holds release assets only; the source is private.

Each release carries, per architecture (`linux_amd64`, `linux_arm64`):

- `rackview-ml_<version>_linux_<arch>.tar.gz` and its minisign signature `.minisig`: the fitter's wheels (pinned by sha256), its installer and its systemd units
- `SHA256SUMS` over the tarballs, and `SHA256SUMS.minisig`, whose trusted comment is `rackview-ml <version> SHA256SUMS`

Verify before installing:

```sh
minisign -Vm rackview-ml_<version>_linux_amd64.tar.gz -P RWSPexohIkU/joEhZUO/mBr1C8nF+XOL2JAeHHl24IBLKeHVtiepv3Ln
```

Public key (key id 8E3F4522211A7B8F, the same key as the edge's releases):

```
untrusted comment: minisign public key 8E3F4522211A7B8F
RWSPexohIkU/joEhZUO/mBr1C8nF+XOL2JAeHHl24IBLKeHVtiepv3Ln
```

An installed appliance verifies fitter updates (`rackview-edge update -component ml`) against `/etc/rackview-edge/release.pub` and refuses anything else.
