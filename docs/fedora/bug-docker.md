2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t nat -D PREROUTING -m addrtype --dst-type LOCAL -j DOCKER' failed: iptables v1.8.0 (legacy): Couldn't load target `DOCKER':No such file or directory
Try `iptables -h' or 'iptables --help' for more information.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t nat -D OUTPUT -m addrtype --dst-type LOCAL ! --dst 127.0.0.0/8 -j DOCKER' failed: iptables v1.8.0 (legacy): Couldn't load target `DOCKER':No such file or directory
Try `iptables -h' or 'iptables --help' for more information.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t nat -D OUTPUT -m addrtype --dst-type LOCAL -j DOCKER' failed: iptables v1.8.0 (legacy): Couldn't load target `DOCKER':No such file or directory
Try `iptables -h' or 'iptables --help' for more information.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t nat -D PREROUTING' failed: iptables: Bad rule (does a matching rule exist in that chain?).
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t nat -D OUTPUT' failed: iptables: Bad rule (does a matching rule exist in that chain?).
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t nat -F DOCKER' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t nat -X DOCKER' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t filter -F DOCKER' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t filter -X DOCKER' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t filter -F DOCKER-ISOLATION-STAGE-1' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t filter -X DOCKER-ISOLATION-STAGE-1' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t filter -F DOCKER-ISOLATION-STAGE-2' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t filter -X DOCKER-ISOLATION-STAGE-2' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t filter -F DOCKER-ISOLATION' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -t filter -X DOCKER-ISOLATION' failed: iptables: No chain/target/match by that name.
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -D FORWARD -i docker0 -o docker0 -j DROP' failed: iptables: Bad rule (does a matching rule exist in that chain?).
2019-04-04 11:31:03 WARNING: COMMAND_FAILED: '/usr/sbin/iptables -w10 -D FORWARD -i docker0 -o docker0 -j DROP' failed: iptables: Bad rule (does a matching rule exist in that chain?).
