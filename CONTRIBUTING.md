# Contributing to Execution APIs

Thank you for your interest in contributing to the Sila Execution API
specification. This document provides a concise overview of the contribution
process. For detailed guidance on principles and the standardization process,
see the [Contributors Guide](docs-api/docs/contributors-guide.md). For test
generation and format, see the [Tests documentation](docs-api/docs/tests.md).

## Contribution Workflow

1. **Open an Issue or PR** — If opening an issue, describe in as much detail as
   possible what you want and why. If opening a PR, ensure spec changes are
   compatible with the repo structure and OpenRPC so that speccheck and CI can
   pass. Note: rpctestgen may not pass for new methods until go-sila
   implements them upstream; maintainers may merge such PRs with CI exceptions.

2. **Obtain Client Consensus** — The issue or PR needs review from execution
   client developers to achieve rough consensus. Bring proposals to one of: RPC
   Standards calls, the [json-rpc-api](https://discord.gg/tWQwJSaqEE) channel in
   Sil R&D Discord, or (recommended) the All Core Devs Testing (ACDT) calls.

3. **Implement in go-sila** — The spec must be implemented in go-sila
   so that rpctestgen can generate test fixtures (`.io` files). This enables
   all CI/CD pipelines to pass.

4. **Merge and Hive** — Once the spec is merged and tests pass,
   [hive](https://github.com/sila-chain/sila-hive)'s
   [rpc-compat](https://github.com/sila-chain/sila-hive/tree/main/simulators/sila/rpc-compat)
   simulator pulls the `main` branch and automatically tests execution clients.

5. **Hive Updates** — Occasionally, hive/rpc-compat may need to be updated to
   add CLI flags for new API namespaces or methods.

6. **Versioned Releases** — Versioned releases are planned so hive can target
   specific execution-apis versions instead of always using `main`.

## Quick Links

- [Contributors Guide](docs-api/docs/contributors-guide.md) — Guiding
  principles, standardization process, and acquiring client support
- [Tests](docs-api/docs/tests.md) — Test format, generation with rpctestgen,
  and chain making
- [Tools](tools/README.md) — specgen, speccheck, rpctestgen; how to pass CI
