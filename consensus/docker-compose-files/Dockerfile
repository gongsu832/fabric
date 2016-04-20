from s390xlinux/hyperledger-go1.6-rocksdb4.6:latest

# Copy GOPATH src and install Peer
RUN mkdir -p /var/hyperledger/db
RUN mkdir -p /var/hyperledger/production
WORKDIR $GOPATH/src/github.com/hyperledger/fabric
COPY . .
WORKDIR $GOPATH/src/github.com/hyperledger/fabric/peer
RUN CGO_CFLAGS="-I/opt/rocksdb/include" CGO_LDFLAGS="-L/opt/rocksdb -lrocksdb -lstdc++ -lm -lz -lbz2 -lsnappy" go install && cp $GOPATH/src/github.com/hyperledger/fabric/peer/core.yaml $GOPATH/bin
RUN cp $GOPATH/src/github.com/hyperledger/fabric/consensus/obcpbft/config.yaml $GOPATH/bin
# RUN CGO_CFLAGS=" " CGO_LDFLAGS="-lrocksdb -lstdc++ -lm -lz -lbz2 -lsnappy" go install
# RUN cd membersrvc && go install
