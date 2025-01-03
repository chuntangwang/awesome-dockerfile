FROM --platform=${BUILDPLATFORM} alpine:3.20.2
# Reference: https://github.com/dtzar/helm-kubectl

# K8s version:
#   QAT: v1.20.11
#   UAT: v1.19.13
#   PRD: v1.19.8
#   kubectl version should be 1.19.x ~ 1.20.x to support all env.
ENV KUBE_VERSION=1.20.15
ENV HELM_VERSION=3.15.4
ENV YQ_VERSION=4.44.3
ENV TARGETOS=linux
ENV TARGETARCH=amd64

# Google Cloud Storage: https://console.cloud.google.com/storage/browser/kubernetes-release/release
RUN apk -U upgrade && \
    apk add --no-cache ca-certificates bash git openssh curl gettext jq && \
    wget -q https://storage.googleapis.com/kubernetes-release/release/v${KUBE_VERSION}/bin/${TARGETOS}/${TARGETARCH}/kubectl -O /usr/local/bin/kubectl && \
    wget -q https://get.helm.sh/helm-v${HELM_VERSION}-${TARGETOS}-${TARGETARCH}.tar.gz -O - | tar -xzO ${TARGETOS}-${TARGETARCH}/helm > /usr/local/bin/helm && \
    wget -q https://github.com/mikefarah/yq/releases/download/v${YQ_VERSION}/yq_${TARGETOS}_${TARGETARCH} -O /usr/local/bin/yq && \
    chmod +x /usr/local/bin/helm /usr/local/bin/kubectl /usr/local/bin/yq && \
    mkdir /config && \
    chmod g+rwx /config /root && \
    helm repo add "stable" "https://charts.helm.sh/stable" --force-update && \
    kubectl version --client && \
    helm version && \
    helm plugin install --version master https://github.com/sonatype-nexus-community/helm-nexus-push.git && \
    helm nexus-push --help

WORKDIR /config

CMD ["bash"]
