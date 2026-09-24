# Build & Breach - Session Log

## 2026-09-24 - M1: Host readiness check
- **Did:** Checked host specs (16 GB RAM, i7-1260P, virtualization enabled). Found high idle memory; traced it to Chrome and Splunk.
- **Why it worked / failed:** Chrome runs a separate process per tab and extension, so closing tabs freed memory directly. Splunk and MySQL were set to Automatic startup, so they ran at every boot even when unused. Switching them to Manual stops that.
- **Still don't understand:** If dual-boot pc of my home network should be added to this project or not.