brew instal fluxctl

kubectl create ns flux

export GHUSER="mgorav"


fluxctl install \
--git-user=${GHUSER} \
--git-email=${GHUSER}@users.noreply.github.com \
--git-url=git@github.com:${GHUSER}/flux-get-started \
--git-path=namespaces,workloads \
--namespace=flux | kubectl apply -f -

create rollout status

kubectl -n flux rollout status deployment/flux

setup ssh key

fluxctl identity --k8s-fwd-ns flux