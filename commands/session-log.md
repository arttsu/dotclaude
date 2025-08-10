**ROLE**: You are a diligent assistant maintaining the session log for our current project.

**TASK**: Append a new session entry to the `session-log.org` file.

**INPUTS**:
- **Current Datetime**: !`date`
- **Additional notes**: Optional notes from the user for the current session: $ARGUMENTS

**FILE HANDLING**:
1.  **If `session-log.org` does not exist**: Create it with the following content. This ensures the main heading is always present.
    ```org
    * Session Log
    ```
2.  **If `session-log.org` exists**:
    - Locate the `* Session Log` heading.
    - **Append** the new session entry as a sub-heading under `* Session Log`.
    - Do not modify or overwrite any other content. If the `* Session Log` heading is missing, add it to the end of the file before appending the new entry.

**ENTRY STRUCTURE**:
You must create a new entry with the following org-mode structure.

1.  **Level 2 Heading `**`**:
    - Start with an org-mode active timestamp, formatted as `<YYYY-MM-DD Day HH:MM>` from the provided date string.
    - Follow it with a space and a short title.
    - Example: `** <2023-10-27 Fri 16:02> Refactored the data validation logic`

2.  **Level 3 Headings `***`**:
    - Under the level 2 heading, generate content for the following sections by analyzing our conversation in this session.
    - Be concise and focus on non-obvious insights suitable for a workshop.
    - `*** Summary`: A brief overview of the goal and outcome.
    - `*** What Worked Well`: Specific techniques, prompts, or approaches that were effective.
    - `*** Challenges & What Didn't Work`: Any misunderstandings, dead ends, or inefficient approaches.
    - `*** Key Learnings & Tips`: Actionable takeaways, reusable patterns, or "aha!" moments. Avoid generic advice.

**EXAMPLE ENTRY**:
```org
** <2023-10-27 Fri 16:02> Refactored data validation using Pydantic
*** Summary
The session focused on replacing custom dictionary-based validation with Pydantic models to improve type safety and clarity. The final code is more robust and self-documenting.
*** What Worked Well
- Providing a complete `pydantic/main.py` file as initial context was highly effective.
- Iteratively refining the model by asking to "add a validator for emails" worked better than describing all requirements at once.
- Using the `/diff` command to apply changes directly was fast and reliable.
*** Challenges & What Didn't Work
- The AI initially used Pydantic V1 syntax (`@validator`). I had to explicitly correct this by providing a V2 (`@field_validator`) example.
- A broad request to "fix the code" was less effective than a specific "run the linter and apply its suggestions."
*** Key Learnings & Tips
- **Pattern**: For library-specific tasks, always provide a small, correct code sample demonstrating the exact version/syntax you want. This grounds the AI effectively.
- **Tip**: When a test fails, paste the full `pytest` error output. The AI is excellent at parsing tracebacks to find the root cause.

**Please make sure that implementation notes are up-to date as well**
