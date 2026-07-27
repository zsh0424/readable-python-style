---
name: readable-python-style
description: Write, modify, translate, refactor, or review Python code in a simple and readable personal style with clear Chinese comments. Use for Python scripts, notebooks, data-processing code, automation, and translations from MATLAB or other languages when the user wants familiar packages, explicit logic, minimal engineering overhead, no unnecessary classes or type annotations, preservation of existing behavior, or consistency with an existing codebase.
---

# Readable Python Style

## Apply priorities

1. Follow the user's explicit requirements.
2. Preserve existing project conventions when modifying code.
3. Apply this style where the first two do not decide the form.

Do not change business logic merely to make code look cleaner. Ask about uncertain requirements, field meanings, units, formulas, or interfaces instead of guessing.

## Keep the solution simple

- Prefer direct, familiar Python over clever or compressed syntax.
- Use standard-library modules and common packages already present in the project.
- Do not add unfamiliar dependencies for small conveniences.
- Default to one Python file for a simple task.
- Do not create configuration files, common utility modules, logging frameworks, command-line interfaces, caches, abstractions, or fallback systems unless the task requires them.
- Do not use `from __future__ import ...` unless the existing project requires it.

## Organize code by function

- Separate substantial responsibilities into clearly named functions.
- Let each function perform one coherent task.
- Avoid both oversized functions containing unrelated work and many tiny one-use helpers.
- Use one `if __name__ == '__main__':` block in a standalone script.
- Arrange a typical script in a natural order: imports, parameters, functions, main workflow, output.
- Use visible Chinese section comments when they materially improve navigation.

## Prefer readable syntax

- Use meaningful English `snake_case` names for variables and functions.
- Use `UPPER_SNAKE_CASE` for genuine constants.
- Avoid unexplained abbreviations and names such as `a`, `tmp`, `res1`, or `df2` when clearer names are practical.
- Default to ordinary functions rather than classes. Use a class only when persistent object state or an existing architecture makes it natural.
- Default to no type annotations or return arrows. Retain them when the existing codebase consistently uses them or the user requests them.
- Use short list comprehensions only when immediately clear. Use an explicit loop for multi-step conditions or transformations.
- Limit `lambda` to short, obvious expressions.
- Break complex transformations into named intermediate steps.
- Avoid long chains written only to reduce line count.
- Put long argument lists, field lists, and mappings on separate lines.

## Write useful Chinese comments

- Explain the purpose and business reason of each important section.
- Comment important filters, formulas, units, date handling, merge keys, and format conversions.
- For multi-step logic, use short numbered comments when helpful.
- Do not translate every Python statement into a comment.
- Do not add lengthy engineering documentation inside the script.
- Keep identifiers in clear English unless the data's required output columns are Chinese.

## Handle data explicitly

When using pandas or similar tabular tools:

- Prefer familiar operations such as `merge`, `groupby`, `sort_values`, `drop_duplicates`, `rename`, and `reset_index`.
- State merge keys and join type explicitly.
- Preserve identifiers such as security codes as text.
- Preserve correct date and numeric types.
- Use intermediate DataFrames with descriptive names.
- Keep field selection, filtering, calculation, and output ordering visible and auditable.

## Handle errors without overengineering

- Do not add large validation frameworks or many broad `try/except` blocks.
- Never use an empty `except` for an important operation.
- Raise a short, specific error only when execution genuinely cannot continue.
- Do not silently substitute an approximate method, alternate field, alternate package, or fallback data source.
- Ask the user when an unresolved choice would change the result materially.

## Modify existing code carefully

- Read the relevant file completely before changing it.
- Make the smallest coherent change that satisfies the request.
- Preserve naming, imports, function structure, comments, and data-processing patterns where practical.
- Do not rewrite an entire file merely to impose this style.
- Do not modify unrelated files or unrelated logic.
- Preserve user changes and existing outputs unless the request explicitly replaces them.

## Verify in proportion to the task

- At minimum, check syntax after creating or changing Python code.
- Run focused tests when allowed and useful.
- If the user says not to run the code, do not execute its main workflow, access databases, call external services, or generate production outputs. A non-executing syntax parse is allowed.
- State clearly whether the code was run, syntax-checked only, or left unverified because required data or services were unavailable.

## Report concisely

At handoff, state:

- which file was created or modified;
- the main behavior implemented;
- what verification was performed;
- any specific information or data still required.

Do not turn the handoff into a long engineering report unless requested.
