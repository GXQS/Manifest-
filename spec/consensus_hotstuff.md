# HotStuff Consensus Specification (GXQS)

## Scope
This document defines the canonical state machine and message-flow invariants for GXQS HotStuff consensus.

## Phase Model
Every proposal progresses through the following ordered phases:
1. Prepare
2. PreCommit
3. Commit
4. Decide

A block can only reach a later phase if the previous phase has a valid quorum certificate (QC) over the same view and block hash.

## Quorum and Fault Threshold
- Validator set size is `N`
- Byzantine tolerance is `f = floor((N-1)/3)`
- Quorum threshold is `2f + 1`

All QCs and timeout certificates require at least `2f + 1` unique validator signatures from the active epoch set.

## Pacemaker and Views
- Views are monotonically increasing per epoch.
- The pacemaker starts timers per view.
- On timeout, validators broadcast timeout votes referencing their highest known QC.
- A timeout certificate (TC) advances the network to the next view.

## Proposer Selection
Proposer selection is deterministic:
`proposer_index = H(epoch || view || previous_qc_hash) mod validator_count`

## Epoch Transitions
Epoch transitions are activated only by finalized blocks containing validator-set updates.
All consensus votes for a view must validate against the epoch active at that view.

## Fork Choice and Finality
- Preferred branch is the highest-QC chain.
- A block is final only when the Decide phase is reached.
- Reorgs are allowed only for non-finalized branches.

## Slashing Conditions
Validators are slashable for:
- Double voting in the same phase/view.
- Voting conflicting descendants violating locked-QC safety.
- Equivocating timeout votes in the same view.

## Safety Invariant
No two conflicting blocks can both be finalized if at most `f` validators are Byzantine.
