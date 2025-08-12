# QbitCracker

A beginner-friendly guide and project to solve **Bitcoin Puzzle 71** using quantum computing and Shor's algorithm — still a work in progress!

---

## Why This Project Matters

Bitcoin Puzzle 71 is a cryptographic challenge based on factoring a large number that underpins Bitcoin’s security. Classical computers find this extremely hard, but quantum algorithms like Shor's algorithm offer a potential shortcut. Successfully cracking this puzzle would demonstrate the power of quantum computing and deepen our understanding of cryptography’s future.

---

## Puzzle Link

[Bitcoin Puzzle 71](https://privatekeys.pw/puzzles/bitcoin-puzzle-tx)

---

## About Me

I'm new to cryptography and quantum computing, but I’m excited to learn and apply **Shor's algorithm** to break down this puzzle into smaller, manageable parts. im a hacker at heart so i figured why not give this a shot.

---

## Current Status & Roadmap

- **Learning fundamentals:** Number theory, quantum computing basics, and Shor’s algorithm.  
- **Building a mock cracker:** Starting with a simplified version solving 15-20 bit factoring puzzles.  
- **Scaling up:** Aiming to tackle the full Bitcoin Puzzle 71 after validating smaller cases.

---

## Basic Number Theory and Cryptography Concepts

- Prime factorization and its difficulty  
- Modular arithmetic: modular exponentiation, inverse, congruences  
- Order finding: central to Shor’s algorithm  
- Why factoring matters for Bitcoin security

**Resource:**  
[Khan Academy: Modular Arithmetic](https://www.khanacademy.org/search?referer=%2Fcomputing%2Fcomputer-science%2Fcryptography%2Fmodarithmetic&page_search_query=modular+arithmetic)

---

## Quantum Computing Fundamentals

- Qubits, superposition, and measurement  
- Quantum gates (Hadamard, Pauli-X, CNOT, phase gates)  
- Quantum circuits and how gates combine  
- Quantum measurement collapse  
- Overview of quantum algorithms

**Resources:**  
- [Qiskit Textbook: Quantum Circuits](https://qiskit.org/textbook/ch-states/quantum-circuits.html)  
- IBM Quantum Experience tutorials and YouTube videos

---

## Shor’s Algorithm Theory

- The problem it solves: efficient integer factorization  
- High-level steps:  
  1. Choose a random coprime *a*  
  2. Quantum order-finding to find order *r* of *a* mod *N*  
  3. Compute factors from *r*  
- Quantum order-finding subroutine explained  
- Classical post-processing details

**Resources:**  
- [Qiskit Textbook: Shor’s Algorithm](https://github.com/Qiskit/textbook/tree/main/notebooks/ch-algorithms#shors-algorithm)  
- MIT OpenCourseWare video lectures

---

## Qiskit and Quantum Programming

- Creating quantum circuits and gates  
- Using Qiskit’s built-in Shor’s algorithm  
- Simulators vs real quantum hardware  
- Circuit optimization and transpilation  
- Basics of error mitigation

**Resources:**  
- [Qiskit Documentation](https://qiskit.org/documentation/)  
- [Qiskit Tutorials](https://qiskit.org/documentation/tutorials.html)  
- IBM Quantum Lab for hands-on coding

---

## Modular Approach to Large Factoring Problems

- Why modularize large factoring problems (hardware limits)  
- Splitting the problem into smaller subproblems  
- Hybrid quantum-classical strategies  
- Iterative refinement and combining results

---

## Suggested Learning Path

| Step | Topic                       | Time Estimate | Suggested Resource                          |
|-------|-----------------------------|---------------|--------------------------------------------|
| 1     | Number theory basics         | 1-2 days      | Khan Academy modular arithmetic            |
| 2     | Quantum computing fundamentals | 3-5 days      | Qiskit textbook chapters 1-3                |
| 3     | Shor’s algorithm theory     | 2-3 days      | Qiskit textbook chapter on Shor’s algorithm |
| 4     | Qiskit programming basics   | 3-5 days      | Qiskit tutorials and IBM Quantum Lab       |
| 5     | Modular problem decomposition | Ongoing       | Research papers, Qiskit community forums    |

---

## What You’ll Be Able to Do After This

- Understand classical factoring difficulty  
- Grasp how Shor’s algorithm uses quantum mechanics  
- Write and run quantum circuits with Qiskit  
- Use Shor’s algorithm implementation to factor small numbers  
- Design modular approaches for larger factoring problems  
- Run code on simulators and IBM quantum hardware

---

## FAQ / Common Challenges

- **Q:** Can current quantum hardware solve Bitcoin Puzzle 71 directly?  
  **A:** Not yet — hardware limitations require breaking down the problem into smaller pieces.  
- **Q:** Is this legal?  
  **A:** This project is for educational purposes only. Attempting to crack private keys without permission is illegal.  
- **Q:** Where can I contribute?  
  **A:** See the [Contributing](#contributing) section below.

---

## Contributing

I welcome collaborators and contributions! Feel free to open issues, submit pull requests, or reach out via GitHub.

---

## Contact

- GitHub: [QbitCracker](https://github.com/NullifyReality/QbitCracker)  
- Email: DTDT@toke.com
---

*Happy quantum hacking!*

# My Current Plan

## Modular Factoring Plan for Bitcoin Puzzle 71

Bitcoin Puzzle 71 involves factoring a **256-bit composite number \(N = p \times q\)**, which is currently beyond the reach of direct quantum factoring on today’s devices. To tackle this, we use a **modular factoring approach** that breaks the problem into smaller subproblems manageable by ~100-qubit quantum hardware.

---

### Overview

- Directly factoring \(N\) requires thousands of qubits — not feasible now.  
- We split \(N\) into smaller chunks by guessing parts of the factors \(p\) or \(q\).  
- Run Shor’s algorithm on smaller subproblems (~30-50 bits) on quantum devices.  
- Combine partial results classically and iterate until the full factors are found.

---

### How It Works

1. **Classical Preprocessing:**  
   Use classical algorithms to remove small factors and narrow down candidate bit ranges.

2. **Partial Bit Guessing:**  
   Guess some known bits of \(p\) (e.g., high or low bits).  
   Represent \(p\) as:  
   \[
   p = p_{\text{known}} \times 2^{k} + p_{\text{unknown}}
   \]  
   where \(p_{\text{unknown}}\) is a smaller unknown integer to factor.

3. **Build Quantum Subproblem:**  
   Construct a smaller integer to factor that depends on \(p_{\text{unknown}}\) and \(N\).  
   This smaller integer is within the size limits of current quantum hardware.

4. **Run Shor’s Algorithm:**  
   Factor the smaller integer on a quantum computer or simulator.

5. **Verify and Iterate:**  
   Combine results to reconstruct \(p\) and \(q\).  
   Check if \(p \times q = N\).  
   If not, repeat with new guesses.

---

### Pseudo-code Example

```python
def modular_factor(N, bit_window_size=40):
    # Step 1: classical factor removal
    N_reduced = classical_preprocessing(N)

    # Step 2: generate guesses for known bits of p
    for p_known_guess in generate_bit_guesses(N, bit_window_size):
        # Step 3: build subproblem number for unknown bits
        subproblem_number = build_subproblem(N_reduced, p_known_guess, bit_window_size)

        # Step 4: quantum factoring on subproblem
        factors = quantum_shor(subproblem_number)

        if factors_found(factors):
            p_unknown = reconstruct_unknown_bits(factors)
            p_candidate = combine_bits(p_known_guess, p_unknown, bit_window_size)
            q_candidate = N // p_candidate

            if p_candidate * q_candidate == N:
                return p_candidate, q_candidate

    return None, None  # Factors not found yet
```
Notes

    The efficiency depends heavily on how well the partial bit guesses are chosen.

    Quantum subproblems should fit within ~30-50 bits factoring range for ~100 qubits usage.

    This is an active research area; developing heuristics and hybrid algorithms is key.

    Parallelizing quantum runs over different guesses can speed up the process.
