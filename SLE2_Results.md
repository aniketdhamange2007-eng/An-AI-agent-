# SLE-2: Profiling and Empirical Performance Analysis

## Student Details

**Name:** Aniket Dhamange
**PRN:** 25UAM002
**Course:** 02AML204 – Introduction to Artificial Intelligence
**Program:** SY B.Tech CSE (AI & ML)
**Division:** A
**SLE:** SLE-2
**GitHub Repository:** https://github.com/aniketdhamange2007-eng/An-AI-agent-

---

## 1. Objective

The objective of this SLE-2 activity is to measure and compare the actual performance of two versions of the response-selection part of the AI agent.

The two versions are:

1. **Version 1:** If/Elif based response selection
2. **Version 2:** Dictionary based response selection

The comparison is performed using actual execution time and memory measurements.

---

## 2. Algorithms / Versions Profiled

### Version 1 – If/Elif Based

The original AI agent uses a sequence of `if` and `elif` conditions to identify the user's command and generate an appropriate response.

Example commands include:

* hello
* help
* study
* python
* ai
* bye

The program checks the conditions one by one until a matching condition is found.

### Version 2 – Dictionary Based

The second version uses a Python dictionary to store commands and their corresponding responses.

The command is used as a key, and the corresponding response is retrieved using dictionary lookup.

This version was selected because dictionary mapping was identified as a possible improvement to the original rule-based response system.

---

## 3. Profiling Method

The following Python tools were used:

* **`timeit`** – to measure execution time.
* **`tracemalloc`** – to measure current and peak memory usage.

The same set of test commands was given to both versions so that the comparison remained consistent.

### Test Commands

```text
hello
help
study
python
ai
bye
unknown
```

Each version was tested for **10,000 iterations per run** and the test was repeated **3 times**.

The average execution time was calculated from the three runs.

---

## 4. Results

### Execution Time

| Run         | Version 1: If/Elif | Version 2: Dictionary |
| ----------- | -----------------: | --------------------: |
| Run 1       |     ______ seconds |        ______ seconds |
| Run 2       |     ______ seconds |        ______ seconds |
| Run 3       |     ______ seconds |        ______ seconds |
| **Average** | **______ seconds** |    **______ seconds** |

### Memory Usage

| Version               | Current Memory |  Peak Memory |
| --------------------- | -------------: | -----------: |
| Version 1: If/Elif    |   ______ bytes | ______ bytes |
| Version 2: Dictionary |   ______ bytes | ______ bytes |

### Relative Performance

**Version 1 / Version 2 ratio:** ______ ×

**Observed faster version:** ______________________

---

## 5. Observation

The profiling results show a measurable difference between the two implementations.

The If/Elif implementation checks conditions sequentially. As the number of possible commands increases, more conditions may need to be checked before finding the required response.

The dictionary implementation stores commands as keys and retrieves the response through dictionary lookup. Therefore, it provides a more structured way of handling a larger number of commands.

The actual execution-time difference should be interpreted using the measured results obtained from the local system.

---

## 6. Justification and Analysis

The comparison demonstrates how a change in implementation can affect the empirical performance of a program.

For the original implementation, the response-selection process depends on a sequence of conditional checks. The amount of checking can increase when more commands are added.

In the dictionary-based implementation, the commands are stored in a mapping structure. This makes the response system easier to extend because a new command can generally be added as another dictionary entry.

Based on the profiling results, the version with the lower average execution time performed faster for the selected test workload.

Memory usage was also measured using `tracemalloc`. The memory values provide an additional practical measurement for comparing the two implementations.

However, the measured results are specific to the computer, Python environment, workload, and number of iterations used during testing. Therefore, the results should be considered empirical measurements rather than universal performance values.

---

## 7. AI Contribution Note

AI tools were used during the development of the SLE-2 profiling activity to help structure the profiling code and suggest an improved dictionary-based implementation.

The generated code was reviewed and tested before
