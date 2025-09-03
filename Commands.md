# Create a json/yaml-encoded Secret somehow:
# (note use of `--dry-run` - this is just a local file!)
echo -n bar | kubectl create secret generic mysecret --dry-run=client --from-file=foo=/dev/stdin -o json >mysecret.yaml

# This is the important bit:
kubeseal -f mysecret.yaml -w mysealedsecret.yaml


project: konfi
source:
repoURL: 'git@github.com:DeNic0la/konfi-infra.git'
path: stages/dev
targetRevision: dev
destination:
server: 'https://kubernetes.default.svc'
namespace: konfi-dev
