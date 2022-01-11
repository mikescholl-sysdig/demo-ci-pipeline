## Testing Workflows in .github/workflows

Localized testing of workflows can be done with [act](https://github.com/nektos/act)

Ensure you have your `GITHUB_TOKEN` configured in your environment variables for `act` to pull from Github.

Example Run: 

```
❯ act create --eventpath tests/workflow/tag_create.json --secret SECURE_API_TOKEN --workflows .github/workflows/sysdig-scanning-main.yml --job Build-Docker-Artifact --secret GITHUB_TOKEN
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact] 🚀  Start image=ghcr.io/catthehacker/ubuntu:act-latest
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   🐳  docker pull image=ghcr.io/catthehacker/ubuntu:act-latest platform= username= forcePull=false
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   🐳  docker create image=ghcr.io/catthehacker/ubuntu:act-latest platform= entrypoint=["/usr/bin/tail" "-f" "/dev/null"] cmd=[]
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   🐳  docker run image=ghcr.io/catthehacker/ubuntu:act-latest platform= entrypoint=["/usr/bin/tail" "-f" "/dev/null"] cmd=[]
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   🐳  docker exec cmd=[mkdir -m 0777 -p /var/run/act] user=root workdir=
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact] ⭐  Run Define branch output
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   🐳  docker exec cmd=[bash --noprofile --norc -e -o pipefail /Users/michael.scholl/work/demo-ci-pipeline/workflow/branch] user= workdir=
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ⚙  ::set-output:: branch=v1.0.0
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ✅  Success - Define branch output
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact] ⭐  Run Docker metadata tag set
INFO[0000]   ☁  git clone 'https://github.com/docker/metadata-action' # ref=v3 
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   🐳  docker cp src=/Users/michael.scholl/.cache/act/docker-metadata-action@v3/ dst=/var/run/act/actions/docker-metadata-action@v3/
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   🐳  docker exec cmd=[mkdir -p /var/run/act/actions/docker-metadata-action@v3/] user= workdir=
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   🐳  docker exec cmd=[node /var/run/act/actions/docker-metadata-action@v3/dist/index.js] user= workdir=
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::group::Context info
| eventName: create
| sha: 599bd6a871c1053b7f3505214b724e374a72dfd7
| ref: refs/tags/v1.0.0
| workflow: Build and Scan Image with Sysdig Secure Inline Scanner v1
| action: meta
| actor: nektos/act
| runNumber: 1
| runId: 1
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::endgroup::
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::group::Processing tags input
| type=semver,pattern={{ version }},priority=900,value=,enable=true
| type=semver,pattern={{major}}.{{minor}},priority=900,value=,enable=true
| type=sha,prefix={{ branch }}-,priority=400,enable=false,format=short
| type=ref,event=branch,priority=100,enable=false
| type=raw,priority=100,enable=false,value=pr-v1.0.0-{{sha}}
| type=ref,enable=true,event=tag,priority=100
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::endgroup::
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::group::Processing flavor input
| latest=auto
| prefix=
| prefixLatest=false
| suffix=
| suffixLatest=false
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::endgroup::
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::group::Docker image version
| 1.0.0
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::endgroup::
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ⚙  ::set-output:: version=1.0.0
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::group::Docker tags
| hello-world:1.0.0
| hello-world:1.0
| hello-world:v1.0.0
| hello-world:latest
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::endgroup::
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ⚙  ::set-output:: tags=hello-world:1.0.0
hello-world:1.0
hello-world:v1.0.0
hello-world:latest
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::group::Docker labels
| org.opencontainers.image.title=demo-ci-pipeline
| org.opencontainers.image.description=A demo Github action pipeline doing a Sysdig Scan
| org.opencontainers.image.url=https://github.com/mikescholl-sysdig/demo-ci-pipeline
| org.opencontainers.image.source=https://github.com/mikescholl-sysdig/demo-ci-pipeline
| org.opencontainers.image.version=1.0.0
| org.opencontainers.image.created=2022-01-11T20:30:25.532Z
| org.opencontainers.image.revision=599bd6a871c1053b7f3505214b724e374a72dfd7
| org.opencontainers.image.licenses=Apache-2.0
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::endgroup::
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ⚙  ::set-output:: labels=org.opencontainers.image.title=demo-ci-pipeline
org.opencontainers.image.description=A demo Github action pipeline doing a Sysdig Scan
org.opencontainers.image.url=https://github.com/mikescholl-sysdig/demo-ci-pipeline
org.opencontainers.image.source=https://github.com/mikescholl-sysdig/demo-ci-pipeline
org.opencontainers.image.version=1.0.0
org.opencontainers.image.created=2022-01-11T20:30:25.532Z
org.opencontainers.image.revision=599bd6a871c1053b7f3505214b724e374a72dfd7
org.opencontainers.image.licenses=Apache-2.0
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::group::JSON output
| {
|   "tags": [
|     "hello-world:1.0.0",
|     "hello-world:1.0",
|     "hello-world:v1.0.0",
|     "hello-world:latest"
|   ],
|   "labels": {
|     "org.opencontainers.image.title": "demo-ci-pipeline",
|     "org.opencontainers.image.description": "A demo Github action pipeline doing a Sysdig Scan",
|     "org.opencontainers.image.url": "https://github.com/mikescholl-sysdig/demo-ci-pipeline",
|     "org.opencontainers.image.source": "https://github.com/mikescholl-sysdig/demo-ci-pipeline",
|     "org.opencontainers.image.version": "1.0.0",
|     "org.opencontainers.image.created": "2022-01-11T20:30:25.532Z",
|     "org.opencontainers.image.revision": "599bd6a871c1053b7f3505214b724e374a72dfd7",
|     "org.opencontainers.image.licenses": "Apache-2.0"
|   }
| }
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::endgroup::
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ⚙  ::set-output:: json={"tags":["hello-world:1.0.0","hello-world:1.0","hello-world:v1.0.0","hello-world:latest"],"labels":{"org.opencontainers.image.title":"demo-ci-pipeline","org.opencontainers.image.description":"A demo Github action pipeline doing a Sysdig Scan","org.opencontainers.image.url":"https://github.com/mikescholl-sysdig/demo-ci-pipeline","org.opencontainers.image.source":"https://github.com/mikescholl-sysdig/demo-ci-pipeline","org.opencontainers.image.version":"1.0.0","org.opencontainers.image.created":"2022-01-11T20:30:25.532Z","org.opencontainers.image.revision":"599bd6a871c1053b7f3505214b724e374a72dfd7","org.opencontainers.image.licenses":"Apache-2.0"}}
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::group::Bake definition file
| {
|   "target": {
|     "docker-metadata-action": {
|       "tags": [
|         "hello-world:1.0.0",
|         "hello-world:1.0",
|         "hello-world:v1.0.0",
|         "hello-world:latest"
|       ],
|       "labels": {
|         "org.opencontainers.image.title": "demo-ci-pipeline",
|         "org.opencontainers.image.description": "A demo Github action pipeline doing a Sysdig Scan",
|         "org.opencontainers.image.url": "https://github.com/mikescholl-sysdig/demo-ci-pipeline",
|         "org.opencontainers.image.source": "https://github.com/mikescholl-sysdig/demo-ci-pipeline",
|         "org.opencontainers.image.version": "1.0.0",
|         "org.opencontainers.image.created": "2022-01-11T20:30:25.532Z",
|         "org.opencontainers.image.revision": "599bd6a871c1053b7f3505214b724e374a72dfd7",
|         "org.opencontainers.image.licenses": "Apache-2.0"
|       },
|       "args": {
|         "DOCKER_META_IMAGES": "hello-world",
|         "DOCKER_META_VERSION": "1.0.0"
|       }
|     }
|   }
| }
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ❓  ::endgroup::
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ⚙  ::set-output:: bake-file=/tmp/docker-metadata-action-PHKAmr/docker-metadata-action-bake.json
[Build and Scan Image with Sysdig Secure Inline Scanner v1/Build-Docker-Artifact]   ✅  Success - Docker metadata tag set
```