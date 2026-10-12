# clone-lin-opgeth-fjord

LIN clone of op-geth `NewL1CostFuncFjord` / `estimatedDASizeScaled` (tag `v1.101702.3`, LGPL-3.0).

This repository holds **only the LIN kernel**. Auditable proofs live in [kbelludoo/lin-open](https://github.com/kbelludoo/lin-open):

- kernel (also mirrored): `src/lin_opgeth_fjord.lin`
- harness: `test/prove_opgeth_fjord_external.py`
- evidence: `examples/opgeth_fjord/`
- event: `docs/events/EVENT_OPGETH_FJORD_CLONE_LIN.rulel`

Class: **EXPERIMENTAL** (real Fjord linear-regression + min-size clamp, i64-scale + 128-bit product). Not an op-geth node. Not uint256 / Base mainnet parity. `FlzCompressLen` is **not** ported; FastLZ size is an explicit integer.

Commercial hook (honest): a wallet that still prices Base/OP txs with Ecotone (`calldataGas * inner / 16e6`) after Fjord undercharges the official emptyTx by **2242100 wei** (3203000 vs 960900) because Fjord replaces that estimate with `max(100 bytes, intercept + 0.8365*FastLZ)`. Dropping the min-size clamp on FastLZ 31 yields a negative size.

Upstream: [ethereum-optimism/op-geth](https://github.com/ethereum-optimism/op-geth) commit `7da4560d1fb3045286b70a8dc23360d2626543f2`
`core/types/rollup_cost.go` blob `3266ae13faaabf599feb4417d60893a11b908fb3` sha256 `35a4e1976fca49cb5f328c6bf3f1513458eda450c9e7425c24a78a8750c51dec`
