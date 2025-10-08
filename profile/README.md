# 0-ART

**0-ART** is a novel solution by [FreedomTool.org](https://freedomtool.org/) for building privacy-first, scalable, decentalization-friendly and verifiable applications such as messengers, private collaborative workspaces and many others. Extending the classic approaches for group management such as [ART](https://eprint.iacr.org/2017/666.pdf) and [MLS](https://datatracker.ietf.org/doc/rfc9420/) it gives a crucial component
beforementioned solutions lack - *verifiability*: each group operation is supplied with a proof of a correct execution which lowers a level of trust assumptions on *Service Provider* and makes systems built with **0-ART** scalable, efficient and even more privacy-preserving. Moreover, **0-ART** supports concurrent updates of a group through a merging mechanism 
and gives a practical solution for role management based on *anonymous verifiable credentials*.

Here we present our implementation of **0-ART** written in Rust along with a demo Flutter app for private collaboration - [Veil](https://github.com/zero-art-rs/veil-app).

## Repositories

- [book](https://github.com/zero-art-rs/book) - engineering description of our **0-ART** protocol implementation
- [core](https://github.com/zero-art-rs/core) - core crates implementing **0-ART** protocol:
  - [cortado](https://github.com/zero-art-rs/core/tree/main/cortado) - carefully crafted elliptic curve which is "native" for the [bulletproofs](https://github.com/zero-art-rs/bulletproofs) implementation(built upon [Ristretto](https://ristretto.group/) group).
  - [zk](https://github.com/zero-art-rs/core/tree/main/zk) - zero-knowledge proofs for tree operations built with great [bulletproofs](https://github.com/zkcrypto/bulletproofs) protocol.
  - [art](https://github.com/zero-art-rs/core/tree/main/art) - implementation of ART and auxiliary tree routines.
  - [crypto](https://github.com/zero-art-rs/core/tree/main/art) - implementation of additional cryptography routines([X3DH](https://signal.org/docs/specifications/x3dh/) protocol, Schnorr signatures).
- [client-sdk](https://github.com/zero-art-rs/client-sdk) - client SDK library for developers which want to integrate **0-ART** protocol into their applications based on our own [application layer protocol](https://zero-art-rs.github.io/book/protocol/0_protocol.html).
- [veil-app](https://github.com/zero-art-rs/veil-app) - the first practical application of **0-ART**: demo of the private collaborative workspace.
- [infrastructure](https://github.com/zero-art-rs/infrastructure) - all backend services supplied in *docker-compose*
  - [node](https://github.com/zero-art-rs/node) - delivery backend service that also verifies all group operations.
  - [message-relay](https://github.com/zero-art-rs/message-relay) - service implementing *outbox* pattern for supplying messages into message-broker
  - [transistor](https://github.com/zero-art-rs/message-relay) - auxiliary service for untrusted encrypted data sharing
