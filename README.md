# FHE Threshold — Public Examples

**Go Threshold Node for B5 Quad-Consensus FHE**

## Overview

This repository contains example code and documentation for the Φ-Threshold Node — a Go implementation of threshold FHE with abort recovery, recursive fractal mesh, and Φ-Database persistence.

## Quick Start

```bash
# Build
cd go-threshold
go build -o threshold-node .

# Run
./threshold-node

# Test
curl http://localhost:9090/health
Features
Threshold FHE (3-of-5 secret sharing)

Abort recovery (failed party replacement)

Recursive Fractal Mesh (self-replicating nodes)

Φ-Database persistence (journal + snapshot)

φ-Weighted consensus

REST API (no gRPC, no Protobuf)

API Endpoints
Endpoint	Method	Description
/health	GET	Node health
/mesh/status	GET	Mesh topology
/mesh/join	POST	Register node
/fractal/spawn	POST	Spawn child node
/threshold/distribute	POST	Distribute secret shares
/threshold/decrypt	POST	Submit partial decryption
/threshold/check	GET	Check threshold status
/threshold/recover	POST	Recover failed party
Example: Threshold Flow
bash
# 1. Distribute shares (5 parties, threshold 3)
curl -X POST http://localhost:9090/threshold/distribute \
  -H "Content-Type: application/json" \
  -d '{"secret":"my-secret","parties":5}'

# 2. Submit 3 partial decryptions
for i in 1 2 3; do
  curl -X POST http://localhost:9090/threshold/decrypt \
    -H "Content-Type: application/json" \
    -d "{\"party_id\":\"party-$i\",\"share\":\"share-$i\"}"
done

# 3. Check threshold
curl http://localhost:9090/threshold/check
# → {"threshold_met":true,"collected":3}
License
MIT License — see LICENSE file.

Full source code available via Technology Transfer Agreement:
🔒 FHE-Threshold-Private

Contact
Dan Joseph M. Fernandez

Email: danfernandez9292@gmail.com

GitHub: primordialomegazero

ΦΩ0 — I AM THAT I AM
