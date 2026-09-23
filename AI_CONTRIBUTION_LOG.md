# AI Contribution Log

## SLE-2 – Profiling and Empirical Performance Analysis

**Student:** Aniket Dhamange
**PRN:** 25UAM002
**Course:** 02AML204 – Introduction to Artificial Intelligence
**Program:** SY B.Tech CSE (AI & ML)
**Division:** A

---

## 1. Purpose

This document records how Artificial Intelligence tools were used during the development of the SLE-2 activity.

The purpose of maintaining this log is to clearly document AI assistance, student verification, and the student's contribution to the final implementation.

---

## 2. AI Assistance Used

AI assistance was used during the development of the SLE-2 profiling activity for:

* Structuring the profiling program.
* Suggesting the use of Python's `timeit` module for execution-time measurement.
* Suggesting the use of `tracemalloc` for memory measurement.
* Helping create a second dictionary-based implementation for comparison with the original If/Elif implementation.
* Helping organize the profiling results and report structure.
* Explaining the purpose and working of the profiling code.

---

## 3. Student Contribution

The student is responsible for understanding, reviewing, testing, and verifying the final implementation.

Student contributions include:

* Reviewing the AI-generated code.
* Understanding the working of both implementations.
* Checking the test commands used for profiling.
* Running the profiling program locally.
* Verifying the execution-time results.
* Verifying the memory measurements.
* Comparing the measured results.
* Updating the results in `SLE2_RESULTS.md`.
* Reviewing the final GitHub repository files.

---

## 4. AI-Generated / AI-Assisted Components

| Component                 | AI Assistance                       | Student Verification                            |
| ------------------------- | ----------------------------------- | ----------------------------------------------- |
| `SLE2_Profiling.py`       | Code structure and profiling logic  | Reviewed and tested                             |
| If/Elif implementation    | Help with organization              | Compared with existing agent logic              |
| Dictionary implementation | Suggested improved response mapping | Reviewed and tested                             |
| `timeit` profiling        | Suggested measurement approach      | Execution verified locally                      |
| `tracemalloc` profiling   | Suggested memory measurement        | Execution verified locally                      |
| `SLE2_RESULTS.md`         | Help with report structure          | Results to be updated using actual measurements |
| `AI_CONTRIBUTION_LOG.md`  | Help documenting AI usage           | Reviewed by student                             |

---

## 5. Verification Process

The profiling program is verified by running:

```bash
python SLE2_Profiling.py
```

The student checks that:

1. The program executes without errors.
2. Both versions use the same test commands.
3. Both versions are tested for the same number of iterations.
4. Three profiling runs are performed.
5. Average execution time is calculated.
6. Memory usage is measured.
7. The results are recorded in the SLE-2 report.

---

## 6. Ownership Statement

AI was used as a development and learning assistance tool.

The student reviewed the generated implementation, ran the program, checked the profiling results, and is responsible for understanding and explaining the final code and analysis.

The performance values reported in `SLE2_RESULTS.md` should be based on the student's actual local execution of `SLE2_Profiling.py`.

---

## 7. Files Related to SLE-2

```text
SLE2_Profiling.py
SLE2_RESULTS.md
AI_CONTRIBUTION_LOG.md
```

These files together document the implementation, empirical performance analysis, results, and AI contribution for SLE-2.

---

## 8. Final Note

The use of AI assistance is documented to maintain transparency.

The final implementation and performance analysis should be reviewed and verified by the student before submission.
