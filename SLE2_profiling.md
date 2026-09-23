"""
SLE-2: Profiling and Empirical Performance Analysis

Course: 02AML204 - Introduction to Artificial Intelligence
Student: Aniket Dhamange
PRN: 25UAM002

Comparison:
Version 1 -> If/Elif based response selection
Version 2 -> Dictionary based response selection

Profiling tools:
- timeit     : execution time
- tracemalloc: peak memory usage
"""

import timeit
import tracemalloc


# ============================================================
# VERSION 1: ORIGINAL IF/ELIF IMPLEMENTATION
# ============================================================

def get_response_v1(command):
    """Original rule-based response selection using if/elif."""

    command = command.lower().strip()

    if command in ["hello", "hi", "hey"]:
        return "Hello! How can I help you?"

    elif command == "your name":
        return "I am your AI assistant."

    elif command == "help":
        return "You can ask me about AI, Python, or study."

    elif command == "study":
        return "Study regularly and practice what you learn."

    elif command == "python":
        return "Python is a popular programming language."

    elif command == "ai":
        return "AI means Artificial Intelligence."

    elif command == "bye" or command == "exit" or command == "quit":
        return "Goodbye!"

    else:
        return "Sorry, I don't understand that command."


# ============================================================
# VERSION 2: DICTIONARY-BASED IMPLEMENTATION
# ============================================================

RESPONSES = {
    "hello": "Hello! How can I help you?",
    "hi": "Hello! How can I help you?",
    "hey": "Hello! How can I help you?",
    "your name": "I am your AI assistant.",
    "help": "You can ask me about AI, Python, or study.",
    "study": "Study regularly and practice what you learn.",
    "python": "Python is a popular programming language.",
    "ai": "AI means Artificial Intelligence.",
    "bye": "Goodbye!",
    "exit": "Goodbye!",
    "quit": "Goodbye!"
}


def get_response_v2(command):
    """Improved response selection using dictionary lookup."""

    command = command.lower().strip()

    return RESPONSES.get(
        command,
        "Sorry, I don't understand that command."
    )


# ============================================================
# TEST DATA
# ============================================================

TEST_COMMANDS = [
    "hello",
    "help",
    "study",
    "python",
    "ai",
    "bye",
    "unknown"
]


# ============================================================
# TIME PROFILING
# ============================================================

def benchmark(function, number=10000):
    """
    Measure execution time of a function.

    The same test commands are executed repeatedly
    so that the difference between the two versions
    can be measured more clearly.
    """

    def test_function():
        for command in TEST_COMMANDS:
            function(command)

    execution_time = timeit.timeit(
        test_function,
        number=number
    )

    return execution_time


# ============================================================
# MEMORY PROFILING
# ============================================================

def measure_memory(function):
    """
    Measure peak memory used while executing the function.
    """

    tracemalloc.start()

    for command in TEST_COMMANDS:
        function(command)

    current, peak = tracemalloc.get_traced_memory()

    tracemalloc.stop()

    return current, peak


# ============================================================
# MAIN PROFILING PROGRAM
# ============================================================

def main():

    print("=" * 60)
    print("SLE-2: EMPIRICAL PERFORMANCE ANALYSIS")
    print("=" * 60)

    print("\nStudent : Aniket Dhamange")
    print("PRN     : 25UAM002")
    print("Course  : 02AML204 - Introduction to Artificial Intelligence")

    print("\nAlgorithms / Versions Compared:")
    print("Version 1 : If/Elif based response selection")
    print("Version 2 : Dictionary based response selection")

    print("\nTest Commands:")
    print(TEST_COMMANDS)

    # --------------------------------------------------------
    # TIME MEASUREMENT
    # --------------------------------------------------------

    print("\n" + "-" * 60)
    print("EXECUTION TIME PROFILING")
    print("-" * 60)

    number_of_iterations = 10000
    number_of_runs = 3

    print(f"\nIterations per run : {number_of_iterations}")
    print(f"Number of runs     : {number_of_runs}")

    v1_times = []
    v2_times = []

    for run in range(1, number_of_runs + 1):

        v1_time = benchmark(
            get_response_v1,
            number_of_iterations
        )

        v2_time = benchmark(
            get_response_v2,
            number_of_iterations
        )

        v1_times.append(v1_time)
        v2_times.append(v2_time)

        print(f"\nRun {run}:")
        print(f"Version 1 (If/Elif) : {v1_time:.6f} seconds")
        print(f"Version 2 (Dict)    : {v2_time:.6f} seconds")

    # --------------------------------------------------------
    # AVERAGE TIME
    # --------------------------------------------------------

    v1_average = sum(v1_times) / len(v1_times)
    v2_average = sum(v2_times) / len(v2_times)

    print("\n" + "-" * 60)
    print("AVERAGE EXECUTION TIME")
    print("-" * 60)

    print(f"Version 1 Average : {v1_average:.6f} seconds")
    print(f"Version 2 Average : {v2_average:.6f} seconds")

    # --------------------------------------------------------
    # TIME COMPARISON
    # --------------------------------------------------------

    print("\n" + "-" * 60)
    print("TIME COMPARISON")
    print("-" * 60)

    if v2_average > 0:
        ratio = v1_average / v2_average

        print(f"Version 1 / Version 2 : {ratio:.2f}x")

    if v2_average < v1_average:
        improvement = (
            (v1_average - v2_average)
            / v1_average
        ) * 100

        print(
            f"Dictionary version is approximately "
            f"{improvement:.2f}% faster."
        )

    elif v1_average < v2_average:

        difference = (
            (v2_average - v1_average)
            / v2_average
        ) * 100

        print(
            f"If/Elif version is approximately "
            f"{difference:.2f}% faster."
        )

    else:
        print("Both versions have approximately the same execution time.")

    # --------------------------------------------------------
    # MEMORY MEASUREMENT
    # --------------------------------------------------------

    print("\n" + "-" * 60)
    print("MEMORY PROFILING")
    print("-" * 60)

    v1_current, v1_peak = measure_memory(
        get_response_v1
    )

    v2_current, v2_peak = measure_memory(
        get_response_v2
    )

    print("\nVersion 1 (If/Elif):")
    print(f"Current memory : {v1_current:,} bytes")
    print(f"Peak memory    : {v1_peak:,} bytes")

    print("\nVersion 2 (Dictionary):")
    print(f"Current memory : {v2_current:,} bytes")
    print(f"Peak memory    : {v2_peak:,} bytes")

    # --------------------------------------------------------
    # FINAL SUMMARY
    # --------------------------------------------------------

    print("\n" + "=" * 60)
    print("FINAL PROFILING SUMMARY")
    print("=" * 60)

    print("\nVersion 1 - If/Elif")
    print(f"Average Time : {v1_average:.6f} seconds")
    print(f"Peak Memory  : {v1_peak:,} bytes")

    print("\nVersion 2 - Dictionary")
    print(f"Average Time : {v2_average:.6f} seconds")
    print(f"Peak Memory  : {v2_peak:,} bytes")

    print("\n" + "=" * 60)
    print("Profiling completed successfully.")
    print("=" * 60)


# ============================================================
# PROGRAM START
# ============================================================

if __name__ == "__main__":
    main()
