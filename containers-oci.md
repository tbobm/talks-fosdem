# OCI containers

_author_: Spyros Trigazis

_url_: [How to build and run OCI containers][1]


> A shallow dive on the OCI container configuration and an overview of the available tools

## Intro

Linux containers = process controlled by linux cgroups and namespaces

OCI container: defined by OCI spec
- runtime-spec: defines config.json from which runtime know to run container
- image-spec: defines OCI image: 
      + Manifest, (image index)
      + set of FS layers, and config
- FS-bundle: config.json and container root FS

## Why do we need them?

Containers need supervisor(S) eg: docker daemon, kubelet, systemd...

Kubernetes implemented its own CRI specifications.

cri-containerd:cri implementation based on containerd
cri-o: implementation on runc

what if you need a service running that docker depends on?

## CERN container service

### use cases

- batch processing
- end user analysis
- ML / TensorFlow...
- Infrastructure management (Data Movement, web servers, PaaS)
- CI/CD
- OpenStack
- Others

### Magnum deployment

Cluster templates
hared/pub templates for most common setups (customizable)

### Node layout

### Building OCI container

#### System container

- dockerfile
- systemd template
- tmpfiles (if needed)
- manifest.json for default values (if needed)
- config.json
[projectatomic][2]

```bash
git clone $REPO_URL .
sudo docker build -t $IMAGE_NAME .
sudo docker push -t $IMAGE_NAME
sudo atomic install --system --name $NAME $IMAGE_NAME
sudo systemctl start $NAME
```

#### Populatic config.json

```bash
man 7 namespaces
```

- namespaces (mount, cgroup, ipc, network, pid, users, uts) (uts?)
- capabilities bouding
- mounts

```json
{
    "type": "bind",
    "source": "src",
    "destination": "dest",
    "options": []
}
```



[1]: https://fosdem.org/2018/schedule/event/containers_build_oci/
[2]: https://github.com/projectatomic/atomic-system-containers
