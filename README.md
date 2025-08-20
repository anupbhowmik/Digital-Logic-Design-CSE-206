# Digital Logic Design

A collection of digital counter circuits implemented in Logisim for the CSE-206 Digital Logic Design course.

## Requirements

To use these circuit files, you need:

- **Logisim version 2.7.1**
- The included `7400-lib.circ` library file (located in the `lib/` folder)

## Circuit Collection

### Advanced Counters

#### Johnson Counter ([advanced-counters/johnson-counter.circ](advanced-counters/johnson-counter.circ))

A 4-bit Johnson counter (also known as a twisted ring counter) that produces a sequence where only one bit changes at a time.

**Features:**

- Uses 4 D flip-flops (7474 ICs)
- Feedback from inverted output of last stage to input of first stage
- Produces 8 unique states in sequence
- Self-correcting for invalid states

**Truth Table:**
| Clock | Q3 | Q2 | Q1 | Q0 | Decimal |
|-------|----|----|----|----|---------|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 | 1 |
| 2 | 0 | 0 | 1 | 1 | 3 |
| 3 | 0 | 1 | 1 | 1 | 7 |
| 4 | 1 | 1 | 1 | 1 | 15 |
| 5 | 1 | 1 | 1 | 0 | 14 |
| 6 | 1 | 1 | 0 | 0 | 12 |
| 7 | 1 | 0 | 0 | 0 | 8 |

#### Ring Counter ([advanced-counters/ring-counter.circ](advanced-counters/ring-counter.circ))

A 4-bit ring counter where data circulates in a loop with only one bit set at a time.

**Features:**

- Uses 4 D flip-flops (7474 ICs)
- Direct feedback from output of last stage to input of first stage
- Produces 4 unique states
- One-hot encoding (only one output high at a time)

**Truth Table:**
| Clock | Q3 | Q2 | Q1 | Q0 | Active Output |
|-------|----|----|----|----|---------------|
| 0 | 0 | 0 | 0 | 1 | Q0 |
| 1 | 0 | 0 | 1 | 0 | Q1 |
| 2 | 0 | 1 | 0 | 0 | Q2 |
| 3 | 1 | 0 | 0 | 0 | Q3 |

### Asynchronous Counters (Ripple Counters)

#### 4-bit Ripple Up Counter ([asynchronous-counters/4-bit-ripple-up-counter.circ](asynchronous-counters/4-bit-ripple-up-counter.circ))

An asynchronous binary up counter using JK flip-flops.

**Features:**

- Uses 4 JK flip-flops (7476 ICs)
- Clock input only to first stage; subsequent stages triggered by previous stage output
- Counts from 0 to 15 (0000 to 1111)
- Ripple delay propagation

**Truth Table:**
| Clock | Q3 | Q2 | Q1 | Q0 | Decimal |
|-------|----|----|----|----|---------|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 | 1 |
| 2 | 0 | 0 | 1 | 0 | 2 |
| 3 | 0 | 0 | 1 | 1 | 3 |
| 4 | 0 | 1 | 0 | 0 | 4 |
| ... | ...| ...| ...| ...| ... |
| 15 | 1 | 1 | 1 | 1 | 15 |

#### 4-bit Ripple Down Counter ([asynchronous-counters/4-bit-ripple-down-counter.circ](asynchronous-counters/4-bit-ripple-down-counter.circ))

An asynchronous binary down counter using JK flip-flops.

**Features:**

- Uses 4 JK flip-flops (7476 ICs)
- Clock input to first stage; subsequent stages triggered by inverted outputs
- Counts from 15 to 0 (1111 to 0000)
- Ripple delay propagation

**Truth Table:**
| Clock | Q3 | Q2 | Q1 | Q0 | Decimal |
|-------|----|----|----|----|---------|
| 0 | 1 | 1 | 1 | 1 | 15 |
| 1 | 1 | 1 | 1 | 0 | 14 |
| 2 | 1 | 1 | 0 | 1 | 13 |
| 3 | 1 | 1 | 0 | 0 | 12 |
| 4 | 1 | 0 | 1 | 1 | 11 |
| ... | ...| ...| ...| ...| ... |
| 15 | 0 | 0 | 0 | 0 | 0 |

### Synchronous Counters

#### 4-bit Synchronous Up Counter ([synchronousc-counters/4-bit-syn-up-counter.circ](synchronousc-counters/4-bit-syn-up-counter.circ))

A synchronous binary up counter with parallel clocking (Modulo-12 implementation).

**Features:**

- Uses JK flip-flops (7476 ICs) and AND gates (7408 ICs)
- All flip-flops clocked simultaneously
- Reset logic for modulo-12 operation (counts 0-11)
- No ripple delay - faster operation

**Truth Table (Modulo-12):**
| Clock | Q3 | Q2 | Q1 | Q0 | Decimal |
|-------|----|----|----|----|---------|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 | 1 |
| 2 | 0 | 0 | 1 | 0 | 2 |
| ... | ...| ...| ...| ...| ... |
| 11 | 1 | 0 | 1 | 1 | 11 |
| 12 | 0 | 0 | 0 | 0 | 0 (Reset)|

#### 4-bit Synchronous Down Counter ([synchronousc-counters/4-bit-down-counter.circ](synchronousc-counters/4-bit-down-counter.circ))

A synchronous binary down counter with parallel clocking.

**Features:**

- Uses JK flip-flops (7476 ICs) and AND gates (7408 ICs)
- All flip-flops clocked simultaneously
- Counts from 15 to 0
- Faster than ripple counters

**Truth Table:**
| Clock | Q3 | Q2 | Q1 | Q0 | Decimal |
|-------|----|----|----|----|---------|
| 0 | 1 | 1 | 1 | 1 | 15 |
| 1 | 1 | 1 | 1 | 0 | 14 |
| 2 | 1 | 1 | 0 | 1 | 13 |
| ... | ...| ...| ...| ...| ... |
| 15 | 0 | 0 | 0 | 0 | 0 |

#### Modulo-8 Counter ([synchronousc-counters/modulo-8-counter.circ](synchronousc-counters/modulo-8-counter.circ))

A 3-bit synchronous counter that counts from 0 to 7.

**Features:**

- Uses 3 JK flip-flops (7476 ICs) and AND gates (7408 ICs)
- Automatic reset after count of 7
- Output Z indicates full cycle completion

**Truth Table:**
| Clock | Q2 | Q1 | Q0 | Decimal | Z |
|-------|----|----|----|---------|----|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 1 | 1 | 0 |
| 2 | 0 | 1 | 0 | 2 | 0 |
| 3 | 0 | 1 | 1 | 3 | 0 |
| 4 | 1 | 0 | 0 | 4 | 0 |
| 5 | 1 | 0 | 1 | 5 | 0 |
| 6 | 1 | 1 | 0 | 6 | 0 |
| 7 | 1 | 1 | 1 | 7 | 1 |

## IC Components Used

- **7474**: Dual D-type flip-flop
- **7476**: Dual JK flip-flop
- **7408**: Quad 2-input AND gate
- **7404**: Hex inverter

## Usage Instructions

1. Install Logisim version 2.7.1
2. Load the `7400-lib.circ` library file from the `lib/` folder
3. Open any circuit file (.circ) in Logisim
4. Use the simulation controls to:
   - Apply clock pulses
   - Initialize counters using INIT/Initialize buttons
   - Observe output states on the pins
   - Monitor timing relationships

## Key Concepts Demonstrated

- **Asynchronous vs Synchronous Design**: Compare ripple delay in asynchronous counters vs simultaneous clocking in synchronous designs
- **State Machine Design**: Understanding counter sequences and state transitions
- **Feedback Systems**: Ring and Johnson counters demonstrate different feedback mechanisms
- **Modular Arithmetic**: Modulo counters show how to create custom count sequences
- **Digital IC Integration**: Practical use of common 7400-series logic ICs
