FROM swisscomcloud/shield:8.0.15
WORKDIR /shield
ADD shield /shield
RUN /shield/src/daemon/shield-schema -d /shield/data/shield.db
CMD ["/shield/src/daemon/shieldd", "-c", "/shield/shieldd.conf", "-l", "debug"]
