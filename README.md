# CMPSC487W - SWEng - Fall 2023
Name: Love Patel 

Date: November 17, 2023

## Introduction

Mutation testing is a powerful technique used to evaluate the effectiveness of a test suite by introducing small, artificial faults (mutations) into the source code and observing how well the tests can detect these mutations. This report analyzes the results of the mutation testing process conducted using MutPy on the Polynomial class in the src module, with the test suite in the test module.

## Code to run mutpy
```bash
mut.py --target src --unit-test test --runner pytest
```
## Defined Mutation Operators

The following mutation operators were defined and applied to the Polynomial class:

1. **AOD (Arithmetic Operator Replacement)**: Replaces arithmetic operators with alternative ones.
2. **AOR (Arithmetic Operator Replacement)**: Alters the arithmetic operators to introduce variations.
3. **ASR (Assignment Operator Replacement)**: Replaces assignment operators with alternative ones.
4. **BCR (Boolean Condition Replacement)**: Replaces boolean conditions with alternatives.
5. **COI (Conditional Operator Insertion)**: Inserts conditional operators into boolean expressions.
6. **ROR (Relational Operator Replacement)**: Replaces relational operators with alternatives.
7. **SIR (Statement Insertion and Removal)**: Inserts or removes statements in the code.

## Applied Mutations and Their Impact

1. **AOD Mutations**: One mutant was applied and killed by `test_mutated_str`, indicating the mutation affected the `__str__` method. This is a serious mutation.
   
2. **AOR Mutations**: Several mutants were applied. Some were killed by specific tests (`test_str`, `test_add`, `test_mutated_add`), while others survived or were classified as incompetent. These mutations are serious, affecting arithmetic operations and potentially leading to incorrect results.

3. **ASR Mutations**: No mutants were applied. 

4. **BCR Mutations**: One mutant was applied and killed by `test_str`, indicating the mutation affected boolean conditions. This is a serious mutation.

5. **COI Mutations**: Several mutants were applied. Some were killed by specific tests (`test_str`, `test_first_degree_polynomial`), while others survived or were classified as incompetent. These mutations can impact conditional logic and should be considered serious.

6. **ROR Mutations**: Several mutants were applied. Some were killed by specific tests (`test_str`, `test_first_degree_polynomial`), while others survived or were classified as incompetent. These mutations are serious as they affect relational operations.

7. **SIR Mutations**: One mutant was applied and survived. This mutation is serious as it involves inserting or removing statements in the code.

## Summary of Mutant Survival and Killing
```
[*] Mutation score [11.37569 s]: 81.0%
   - all: 80
   - killed: 47 (58.8%)
   - survived: 11 (13.8%)
   - incompetent: 22 (27.5%)
   - timeout: 0 (0.0%)
```

## Analysis of Test Suite Effectiveness

The test suite demonstrates effectiveness in identifying and killing mutants. However, there are still surviving mutants and a significant number classified as incompetent. This indicates potential areas for improvement in test coverage and test quality.

The test suite demonstrates effectiveness in detecting mutations related to:
- **Arithmetic Operations (AOR):** Mutations were successfully identified in arithmetic operations, improving the reliability of the test suite.
- **Conditional Operator Insertion (COI):** The test suite effectively detected mutations related to conditional operators, contributing to its robustness.

However, the suite exhibited limitations in detecting mutations related to:
- **Arithmetic Operator Replacement (AOD):** Surviving mutants indicate a need for additional test cases or enhanced test scenarios to cover AOD mutations comprehensively.
- **Boolean Condition Replacement (BCR):** The BCR mutation was not effectively detected, highlighting a gap in the test suite's coverage.
- **Statement Insertion/Removal (SIR):** The SIR mutation was not detected, indicating a potential blind spot in the test suite.

## Recommendations for Improving the Test Suite

1. **Enhance Test Coverage**: Identify areas of the code that are not covered by the current test suite and create additional test cases to improve coverage.

2. **Refine Test Cases**: Review and refine existing test cases to ensure they are robust and cover various scenarios, especially those revealed by the mutation testing process.

3. **Consider Edge Cases**: Introduce test cases that specifically target edge cases, boundary conditions, and corner cases to ensure the test suite is comprehensive.

4. **Address Timeout Issues**: Investigate and address any timeout issues during the mutation testing process to ensure that all mutants are properly evaluated.

## Conclusion

The test suite demonstrates commendable strengths in detecting mutations related to arithmetic operations, conditional operator insertions, and relational operator replacements. However, identified gaps in detecting arithmetic operator replacements, boolean condition replacements, and statement insertions/removals underline areas for improvement. Implementing the recommended enhancements will not only address these shortcomings but also contribute to a more robust and reliable testing process for the `Polynomial` class, ensuring its resilience against potential mutations.
