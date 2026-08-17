# Week 3 — Suricata IDS Integration with Wazuh

**Program:** Cyberster Blue Team Internship
**Phase:** Phase One — SOC Operations and SIEM Foundations
**Week:** Week 3 (Days 15–21)

## Summary
Installed and configured Suricata IDS on the Kali VM, wrote custom detection rules for three attack scenarios,
integrated the Suricata alert stream into Wazuh for correlation, and implemented GeoIP-based firewall blocking.

## Day-by-Day Breakdown

**Days 15–16 — Suricata Installation and Configuration**
Installed Suricata, configured af-packet to monitor the lab interface, enabled and verified the service, and
confirmed it was inspecting live lab traffic via `fast.log`.

**Day 17 — Suricata Rule Writing**
Wrote three custom rules in `local.rules`: Nmap SYN scan detection, HTTP directory traversal / exploit attempt
detection, and ICMP flood detection. Validated the config and reloaded rules live.

**Days 18–19 — Suricata and Wazuh Integration**
Connected Suricata's `eve.json` alert stream into the Wazuh agent config so network-level detections appear
alongside host-based alerts. Verified all three custom alerts plus default ET signatures in the Wazuh Threat
Hunting dashboard, and correlated Suricata alerts with Windows FIM activity on the same timeline.

**Days 20–21 — GeoIP Blocking and Firewall Rules**
Downloaded country-based IP blocklists (China, Russia, North Korea) from ipdeny.com and configured
iptables-based blocking using them, with additional DNS-level domain blocking via `/etc/hosts`.

## Evidence Screenshots

| # | Screenshot | Description |
|---|---|---|
| 1 | ![Suricata service active](./Screenshots/01-suricata-service-active.jpg) | Suricata service enabled and running |
| 2 | ![Custom rules](./Screenshots/02-local-rules-custom.jpg) | `local.rules` — Nmap, HTTP exploit, and ICMP flood custom rules |
| 3 | ![Config test and reload](./Screenshots/03-config-test-and-reload.jpg) | Suricata config test passing and rules reloaded live |
| 4 | ![Nmap alert](./Screenshots/04-nmap-scan-alert.png) | `fast.log` showing repeated Nmap SYN Scan alerts during a real scan |
| 5 | ![HTTP exploit alert](./Screenshots/05-http-exploit-alert.jpg) | Custom HTTP Exploit Attempt alert firing |
| 6 | ![ICMP flood alert](./Screenshots/06-icmp-flood-alert.jpg) | Custom ICMP Flood alert firing |
| 7 | ![Suricata-Wazuh integration](./Screenshots/07-ossec-conf-suricata-integration.jpg) | `ossec.conf` configured to ingest Suricata's `eve.json` alert stream |
| 8 | ![Suricata events table](./Screenshots/08-suricata-events-table.jpg) | Wazuh Events table listing individual Suricata alerts |
| 9 | ![Suricata ruleset on manager](./Screenshots/09-suricata-ruleset-on-manager.png) | Built-in Suricata rule file located on the Wazuh Manager |
| 10 | ![Correlated view](./Screenshots/10-correlated-suricata-fim-view.jpg) | Combined Threat Hunting view — Suricata alerts correlated with Windows FIM |
| 11 | ![GeoIP blocklists](./Screenshots/11-geoip-blocklists-downloaded.png) | Country blocklist files downloaded (cn/ru/kp.zone) |
| 12 | ![iptables rules verified](./Screenshots/12-iptables-drop-rules-verified.png) | iptables INPUT chain confirming GeoIP DROP rules in place |
| 13 | ![GeoIP block confirmed](./Screenshots/13-geoip-block-test-confirmed.jpg) | Verification that traffic from blocked countries is dropped |
| 14 | ![Domain blocking](./Screenshots/14-etc-hosts-domain-blocking.jpg) | Domain entries added to `/etc/hosts` for DNS-level blocking |
