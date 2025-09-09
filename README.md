# PySpark Experience Summary

## Overview
This document summarizes observed experience with PySpark based on interactions and troubleshooting.

## SparkSession
- Able to start a session with `spark.read.csv(..., header=True, inferSchema=True)`.
- Understands `SparkSession.builder.appName(...).getOrCreate()` as the entry point.

## DataFrame Operations
- Correctly uses `withColumn` to add or overwrite columns.
- Knows how to convert string columns into `date` and `timestamp` using `to_date` and `to_timestamp`.
- Combines separate `date` and `time` columns into a full `datetime` column.
- Dropping columns is understood, but confusion arises when chaining with `.show()`.

## Common Pitfalls
- Frequently overwrites DataFrame with `None` by assigning the result of actions like `.show()`, `.printSchema()`, `.describe()`.
- Confusion between **transformations** (return DataFrames) and **actions** (trigger execution, return side-effects or results).

## Random Data
- Initially attempted to use Python's `random`, later learned Spark requires SQL functions like `rand`, `floor` for distributed-safe randomness.

## Filtering
- Attempted equality with Python sets, corrected to `.isin()` for multi-value filtering.
- Learns filtering with time ranges by comparing `timestamp` columns.
- Understands Spark lacks a pure "time" type; dummy dates or combined fields are required.

## Errors Encountered
- `AttributeError: 'NoneType' object ...` caused by misassigning results of `.show()` and similar actions.
- `Py4JJavaError` caused by parsing mismatches when applying `to_timestamp` on time-only strings.

## Current Level
- Capable of loading, inspecting, manipulating, casting, and filtering data in Spark.
- Still consolidating understanding of Spark’s lazy evaluation model, transformation vs. action distinction, and distributed function usage.
- Position: **Beginner to Intermediate** — can express common operations but still prone to conceptual missteps.
