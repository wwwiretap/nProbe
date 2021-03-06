#Changelog

#### nprobe 7.4 (June 22nd, 2016)

## Main New Features

* Lua scriptability and support for plugins: DHCP, DNS, IMAP, RADIUS, SIP, SMTP, GTPv1, POP, FTP, HTTP
* Ability to drop HTTP flows via Lua
* Ability to push flow information into Lua (e.g., flow.protocol, flow.l7_proto)
* ZMQ *data encryption* to safely exchange information with ntopng
* ZMQ *data compression* to reduce the bandwith consumed when interacting with ntopng
* ZMQ *probe mode* to seamlessly work behind firewalls / NATs
* HTTP full requests/responses content dump
* Ability to specify traffic capture direction (tx, rx, both)
* Flows dump to syslog in JSON format
* Flows export to Apache Kafka via the export plugin
* Implemented SSDP and NETBIOS plugins
* Implemented CAPWAP protocol support
* MIPSEL builds

## New Options
* `--add-engineid-to-logfile` to append the NetFlow engineId to dump files
* `--bind-export-interface` to bind export socket to the specified interface
* `--capture-direction` to specify packet capture direction
* `--cli-http-port` command line
* `--disable-startup-checks` to prevent nProbe public ip detection
* `--host` to capture packets from pcap interfaces rather than from a mirror/tap
* `--json-to-syslog` to export flows to syslog in JSON format
* `--notify-plugin` to notify users of a pluging activity immediately and not when the flow has matched
* `--online-license-check` to check nProbe license online
* `--with-minimal-nprobe` to build nProbe with a minimum set of dependencies
* `--zmq-encrypt-pwd` to encrypt ZMQ data
* `--zmq-probe-mode` to implement ZMQ *probe mode*
* `--http-dump-dir` to dump HTTP logs
* `--http-content-dump-dir` to dump full HTTP requests content
* `--http-content-dump-response` to dump both HTTP requests and responses content with `--http-content-dump-dir`
* `--http-content-dump-dir-layout` to specify layout to be used with `--http-content-dump-dir`
* `--http-exec-cmd` to execute a command whenever an HTTP dump directory has been written
* `--minute-expire` to force active flows to expire when a minute is past

## Plugin Extensions
* Extended the export template with %BITTORENT_HASH, %PACKET_HASH, %SSL_SERVER_NAM, %UPSTREAM_SESSION_ID, %DOWNSTREAM_SESSION_ID, %SRC_AS_MAP and %DST_AS_MAP
* Extended the export template to include longitude and latitude (%SRC_IP_LONG, %SRC_IP_LAT, %DST_IP_LONG and %DST_IP_LAT)
* Implemented SIP RTP support, handling of early export and support of OPTIONS messages
* Extended GTPV1 plugin support to field GTPV1_RAT_TYPE
* Extended GTPV2 plugin support to fields GTPV2_C2S_S5_S8_GTPC_IP and GTPV2_S2C_S5_S8_GTPC_IP, GTPV2_PDN_IP, GTPV2_END_USER_IMEI, GTPV2_C2S_S5_S8_GTPU_TEID, GTPV2_C2S_S5_S8_GTPU_IP, GTPV2_S2C_S5_S8_GTPU_TEID, GTPV2_S2C_S5_S8_GTPU_IP, GTPV2_C2S_S5_S8_SGW_GTPU_TEID, GTPV2_S2C_S5_S8_SGW_GTPU_TEID, GTPV2_C2S_S5_S8_SGW_GTPU_IP and GTPV2_S2C_S5_S8_SGW_GTPU_IP
* GTPV2 plugin check to the export bucket when response isn't the right type for a request and when a response has been done from the same peer as the request
* Implemented GTPV2 0x4A message type management
* Implemented Diameter support of fields DIAMETER_CLR_CANCEL_TYPE and DIAMETER_CLR_FLAGS and 3GPP type messages (317, 319, 320, 321, 322 and 323)
* Extended the Diameter plugin in order to export ""Diameter Hop-by-Hop Identifier" information
* Added DOT1Q_SRC_VLAN/DOT1Q_DST_VLAN for supporting Q-in-Q VLANs
* HTTP plugin export of HTTP_X_FORWARDED_FOR and HTTP_VIA fields
* Extended DNS plugin with multicast DNS


## ZMQ
* ZMQ event handling to send interface statistics to ntopng
* ZMQ statistics in flow collector mode
* Ability to use ZMQ zlib compression
* Enhanced ZMQ statistics with bps/pps rates

## Miscellaneous
* Added black list support for netflow data when nprobe is in proxy mode (ipv4 - V5,V9,IPFIX)
* Twitter heuristics to guess user activities
* Implemented support for TCP fast retransmissions

