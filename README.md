# x4-memory

**Local-first persistent multi-layer agent memory**

Working • Episodic • Semantic • Knowledge Graph • Provenance • Privacy controls

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-v0.1-orange)](CHANGELOG.md)

Part of **[ARIEX4Ops / X4](https://github.com/dhe-cruzer69)**.

---

## Principle

Memory must never be a mysterious black box. Every stored item carries provenance, namespace, and export/deletion support.

<!-- X4-APEX-DIAGRAM-START:x4-memory -->

```mermaid
flowchart TB
    WRITE[Memory Write] --> META[Namespace and Provenance Metadata]
    META --> CLASSIFY{Memory Layer}
    CLASSIFY --> WORK[Working Memory]
    CLASSIFY --> EPISODIC[Episodic Memory]
    CLASSIFY --> SEMANTIC[Semantic Memory]
    CLASSIFY --> GRAPH[Knowledge Graph]
    WORK --> POLICY[Privacy and Retention Controls]
    EPISODIC --> POLICY
    SEMANTIC --> POLICY
    GRAPH --> POLICY
    POLICY --> STORE[(Persistent Memory)]
    READ[Memory Read] --> STORE
    STORE --> RESULT[Memory Result with Provenance]
    EXPORT[Export or Deletion Request] --> STORE
    AGENT[x4-agents] --> READ
    AGENT --> WRITE
```

<!-- X4-APEX-DIAGRAM-END:x4-memory -->

## Related

- [x4-agents](https://github.com/dhe-cruzer69/x4-agents)
- [x4-core](https://github.com/dhe-cruzer69/x4-core)

## License

Apache-2.0

## Support

**[GitHub Sponsors](https://github.com/sponsors/dhe-cruzer69)**

## APEX Architecture Map

> Status: architecture documentation; implementation and deployment claims require independent verification.

**Evidence note:** Retention enforcement, encryption, access scope, and cleanup scheduling are not implied by this diagram; verify them in implementation and tests.

