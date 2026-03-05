# Minimal Anchor Contract Implementation

## Blockchain Spine – Immutable Commitment Layer

### Overview
This repository implements a minimal anchor-only layer for blockchain-based hash commitment. The blockchain serves as the **spine** (not brain, not memory, not execution) providing immutable structural continuity.

---

## Day 1 ✅ COMPLETE

### Deliverables

#### 1. anchor_contract.sol
Minimal Solidity contract implementing append-only anchor storage.

**Features**:
- Stores 6 required fields: anchorId, artifactType, artifactHash, parentHash, timestampUtc, schemaVersion
- Deterministic anchorId generation
- Immutable storage (no update/delete functions)
- Event emission for off-chain indexing
- Read-only query function

**Interface**:
```solidity
function createAnchor(
    string memory _artifactType,
    bytes32 _artifactHash,
    bytes32 _parentHash,
    uint8 _schemaVersion
) external returns (bytes32)

function getAnchor(bytes32 _anchorId) external view returns (...)
```

#### 2. anchor-structure-spec.md
Canonical specification of anchor structure.

**Defines**:
- Field types and requirements
- Validation rules
- Immutability constraints
- Design principles
- Non-goals (no governance, no logic, no interpretation)

#### 3. example-anchors.json
Example anchor entries demonstrating:
- Root anchors (no parent)
- Linked anchors (with parent)
- Multiple artifact types
- Chain visualization
- Hash verification example

#### 4. transaction-log.md
Transaction log documentation showing:
- 4 example anchor creation transactions
- Input parameters
- Generated anchorIds
- Event emissions
- Chain state summary
- Hash verification walkthrough
- Gas cost analysis

---

## Core Principles

### What This IS
✅ Immutable hash commitment mechanism  
✅ Append-only storage  
✅ Parent-child structural linking  
✅ Event-based anchoring  
✅ Chain-agnostic design  

### What This IS NOT
❌ Governance logic  
❌ Registry storage  
❌ Policy validation  
❌ Authority checks  
❌ Execution logic  
❌ Token mechanics  
❌ Business logic  

---

## Anchor Structure

```solidity
struct Anchor {
    bytes32 anchorId;        // Deterministic ID
    string artifactType;     // Type classification
    bytes32 artifactHash;    // Hash commitment
    bytes32 parentHash;      // Optional parent link
    uint256 timestampUtc;    // Creation timestamp
    uint8 schemaVersion;     // Schema version
}
```

---

## Usage Flow

```
Off-Chain System
    |
    v
Generate Artifact Hash
    |
    v
Call createAnchor()
    |
    v
Blockchain Storage (Immutable)
    |
    v
Emit AnchorCreated Event
    |
    v
Off-Chain Indexing
```

---

## Day 2 (Pending)
- Non-mutation guarantee proof
- Parent-child linkability proof

## Day 3 (Pending)
- Replaceability constraint documentation
- Final verification
- Interface boundary definition

---

## Repository Structure

```
Minimal-Anchor-Contract-Implementation/
├── README.md                          # This file
├── anchor_contract.sol                # Minimal anchor contract
├── anchor-structure-spec.md           # Structure specification
├── example-anchors.json               # Example anchor entries
└── transaction-log.md                 # Transaction log documentation
```

---

## Verification Checklist (Day 1)

- [x] Anchor structure defined with 6 required fields
- [x] artifactHash is required
- [x] artifactType is required
- [x] timestampUtc is required (auto-generated)
- [x] parentHash is optional
- [x] schemaVersion is required
- [x] anchorId is deterministic
- [x] No additional metadata fields
- [x] No expansion beyond minimal structure
- [x] Contract interface documented
- [x] Example anchors provided
- [x] Transaction log created
- [x] No semantic logic present
- [x] No governance coupling
- [x] No authority checks

---

## Next Steps

**Day 2**: Implement non-mutation guarantees and parent linking proofs  
**Day 3**: Document replaceability constraints and finalize interface

---

## License
MIT