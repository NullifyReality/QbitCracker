# QbitCracker

My guide to solving **Bitcoin Puzzle 71** with no prior experience (I have yet to solve it).

---

### Puzzle Link
[Bitcoin Puzzle 71](https://privatekeys.pw/puzzles/bitcoin-puzzle-tx)

---

## About

I’m new to this — I don’t know much about how private keys work or how quantum searches work either. But I had an idea to use **Shor's algorithm** to crack the puzzle, breaking it down into smaller parts.

This is a big task, so the first thing I did was educate myself. Below are some of my resources and notes.

---

## Basic Number Theory and Cryptography Concepts

- **Prime factorization:** Understanding how to factor a number into primes.
- **Modular arithmetic:** Concepts like modular exponentiation, modular inverse, and congruences.
- **Order finding:** The core quantum subroutine in Shor’s algorithm is finding the order of a number modulo *N*.
- **Why factoring matters:** Bitcoin Puzzle 71 is based on factoring a large number, which is hard classically but can be sped up by Shor’s algorithm.

**Resource:**  
I created a free account on Khan Academy and searched for modular arithmetic:  
[Modular Arithmetic on Khan Academy](https://www.khanacademy.org/search?referer=%2Fcomputing%2Fcomputer-science%2Fcryptography%2Fmodarithmetic&page_search_query=modular+arithmetic)

---

## Quantum Computing Fundamentals

- **Qubits and quantum states:** What is a qubit, superposition, and measurement.
- **Quantum gates:** Basic gates like Hadamard (H), Pauli-X, controlled gates (CNOT), phase gates.
- **Quantum circuits:** How quantum gates combine to form circuits.
- **Quantum measurement:** How quantum states collapse to classical bits.
- **Quantum algorithms overview:** What makes quantum algorithms different and powerful.

**Resources:**  
- [Qiskit Textbook: Quantum Circuits](https://qiskit.org/textbook/ch-states/quantum-circuits.html)  
- IBM Quantum Experience tutorials and YouTube videos

---

## Shor’s Algorithm Theory

- **Problem Shor’s algorithm solves:** Efficient integer factorization.
- **High-level steps:**
  1. Pick a random number *a* coprime to *N*.
  2. Use quantum order-finding to find the order *r* of *a* modulo *N*.
  3. Use *r* to compute factors of *N*.
- **Quantum order-finding subroutine:** The quantum part that finds the period of a function.
- **Classical post-processing:** How to use the order *r* to get factors.

**Resources:**  
- [Qiskit Textbook: Shor’s Algorithm](https://github.com/Qiskit/textbook/tree/main/notebooks/ch-algorithms#shors-algorithm)  
- Video lectures on Shor’s algorithm (e.g., MIT OpenCourseWare)

---

## Qiskit and Quantum Programming

- **Qiskit basics:** How to create quantum circuits, add gates, run simulations.
- **Using Qiskit’s built-in Shor’s algorithm:** How to call and customize it.
- **Running on simulators vs real hardware:** Differences and limitations.
- **Circuit optimization and transpilation:** Making circuits efficient for hardware.
- **Error mitigation basics:** Handling noise on real devices.

**Resources:**  
- [Qiskit Documentation](https://qiskit.org/documentation/)  
- [Qiskit Tutorials](https://qiskit.org/documentation/tutorials.html)  
- IBM Quantum Lab for hands-on practice

---

## Modular Approach to Large Factoring Problems

- **Why modularize:** Current quantum hardware can’t handle large numbers directly.
- **Breaking down the problem:** Splitting the factoring into smaller subproblems.
- **Hybrid quantum-classical algorithms:** Using classical computation to assist quantum parts.
- **Iterative refinement:** Running parts of the algorithm multiple times and combining results.

---

## Suggested Learning Path


| Step | Topic                      | Time Estimate | Suggested Resource                          |
|-------|----------------------------|---------------|--------------------------------------------|
| 1     | Number theory basics        | 1-2 days      | Khan Academy modular arithmetic            |
| 2     | Quantum computing fundamentals | 3-5 days      | Qiskit textbook chapters 1-3                |
| 3     | Shor’s algorithm theory    | 2-3 days      | Qiskit textbook chapter on Shor’s algorithm |
| 4     | Qiskit programming basics  | 3-5 days      | Qiskit tutorials and IBM Quantum Lab       |
| 5     | Modular problem decomposition | Ongoing       | Research papers, Qiskit community forums    |

---

## Summary: What You’ll Be Able to Do After Learning This

- Understand the math behind factoring and why it’s hard classically.
- Understand how Shor’s algorithm uses quantum mechanics to factor efficiently.
- Write and run quantum circuits in Qiskit.
- Use Qiskit’s Shor’s algorithm implementation to factor small numbers.
- Design a modular approach to factor larger numbers by breaking the problem into smaller quantum circuits.
- Run your code on simulators and real IBM quantum hardware.

---

*Feel free to contribute or reach out if you want to collaborate on this journey!*
