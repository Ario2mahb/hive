ARG branch=optimism
FROM us-docker.pkg.dev/oplabs-tools-artifacts/images/op-geth:$branch

RUN apk add curl jq bash tar zstd
RUN apk add --no-cache ca-certificates
RUN geth console --exec 'console.log(admin.nodeInfo.name)' --maxpeers=0 --nodiscover --dev 2>/dev/null | head -1 > /version.txt

ADD entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

ENTRYPOINT ["/bin/bash", "/entrypoint.sh"]
