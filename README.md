# x4-memory

**Local-first persistent multi-layer agent memory**

Working • Episodic • Semantic • Knowledge Graph • Provenance • Privacy controls

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-v0.1-orange)](CHANGELOG.md)

Part of **[ARIEX4Ops / X4](https://github.com/dhe-cruzer69)**.

---

## Principle

Memory must never be a mysterious black box. Every stored item carries provenance, namespace, and export/deletion support.

## Related

- [x4-agents](https://github.com/dhe-cruzer69/x4-agents)
- [x4-core](https://github.com/dhe-cruzer69/x4-core)

## License

Apache-2.0

## Support

**[GitHub Sponsors](https://github.com/sponsors/dhe-cruzer69)**

## APEX Architecture Map

> Status: architecture documentation; implementation and deployment claims require independent verification.

```mermaid
flowchart TB
  Writer[Memory write request] --> Validate[Validate schema and tenant/session scope]
  Validate --> Classify[Classify sensitivity and retention class]
  Classify --> Decision{Persistence allowed?}
  Decision -->|no| Reject[Reject or keep ephemeral]
  Decision -->|yes| TTL[Calculate expiry]
  TTL --> Adapter[Storage adapter contract]
  Adapter --> SQLite[(SQLite backend)]
  Adapter --> Volatile[(In-memory backend)]
  Reader[Memory read request] --> Scope[Authorize scope]
  Scope --> Adapter
  Adapter --> Filter[Filter expired records]
  Filter --> Return[Return minimal matching records]
  Return --> Audit[Audit metadata only]
  Reject --> Audit
  TTL --> Sweeper[Retention cleanup job]
  Sweeper --> Adapter
```
**Evidence note:** Retention enforcement, encryption, access scope, and cleanup scheduling are not implied by this diagram; verify them in implementation and tests.

