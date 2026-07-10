# VPN-Connectivity-Incident-AD-Account-Lockout
This project will outline the ticket lifecycle of a VPN outage in an enterprise system

## Engineering Notes
### Original Design Goal

Simulate an NPS shared secret mismatch between RRAS and a separate NPS server.

### Discovery

Because RRAS, NPS, and Active Directory were co-located on the same Windows Server 2022 instance, Windows internally authenticated requests instead of exercising a true network-based RADIUS exchange. As a result, changing the shared secret did not produce the expected authentication failure.

Additional testing included disabling the VPN network policy, stopping the NPS service, and blocking PPTP traffic. Due to the architecture of this single-server lab, these tests did not reliably reproduce the intended enterprise failure.

### Project Adjustment

The incident was redesigned around an Active Directory account lockout, a common real-world cause of VPN authentication failures that better fits a single-server Windows lab while still demonstrating enterprise troubleshooting methodology.
