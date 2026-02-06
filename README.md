# Playwright Trace Debugging Skill

An [Agent Skills](https://skills.sh) skill that teaches AI agents how to debug Playwright test failures by analyzing trace files using [pwtrace](https://www.npmjs.com/package/pwtrace).

## What is this?

This skill provides AI agents with procedural knowledge for systematically debugging failed Playwright tests using trace file analysis. Instead of just knowing Playwright's API, agents learn a proven debugging workflow for investigating failures.

## When to use this skill

- After Playwright tests fail and you have a `trace.zip` file
- When debugging flaky or intermittent test failures
- To understand what went wrong in CI/CD test runs
- When the Playwright Trace Viewer GUI isn't available
- To get LLM-friendly text output from trace files

## Installation

### For AI Agents

Install this skill in your AI agent using the skills CLI:

```bash
npx skills add playwright-trace-debugging
# Or from a GitHub repo:
# npx skills add nlong/playwright-trace-debugging
```

Once installed, you can ask your agent things like:

- "Debug this trace.zip file from my failed test"
- "Why did step 4 in this trace time out?"
- "Check the DOM state when the login button click failed"

### Prerequisites

The skill requires [pwtrace](https://www.npmjs.com/package/pwtrace) to be installed:

```bash
npm install -g pwtrace
```

Or use it without global installation:

```bash
npx pwtrace <command> trace.zip
```

## What this skill teaches

This skill teaches agents the **progressive disclosure debugging workflow**:

1. **Overview** (`pwtrace show`) - Identify which steps passed or failed
2. **Deep dive** (`pwtrace step`) - Get details about any step
3. **DOM inspection** (`pwtrace dom`) - See what was on the page
4. **Console logs** (`pwtrace console`) - Find JavaScript errors
5. **Screenshots** (`pwtrace screenshot`) - Visual confirmation
6. **Network analysis** (`pwtrace network`) - Check API failures

## How it complements existing skills

Other skills teach how to write playwright tests; this teaches how to **analyze playwright traces**.
These could be from test runs or traces of other environments.

## Example usage

```bash
# Your Playwright test fails in CI and generates trace.zip
# Ask your AI agent:
"Figure out why this trace of a checkout is failing"

# The agent will use the skill to:
# 1. Run: pwtrace show trace.zip (see that step 4 fails)
# 2. Run: pwtrace step trace.zip 4
# 3. Run: pwtrace dom trace.zip --step 4 --interactive
# 4. Run: pwtrace console trace.zip --step 4 --level error
# 5. Explain what went wrong and suggest fixes
```

## Learn more

- [pwtrace](https://www.npmjs.com/package/pwtrace) - The CLI tool this skill uses
- [skills.sh](https://skills.sh) - The Agent Skills ecosystem
- [Playwright Traces](https://playwright.dev/docs/trace-viewer) - Official Playwright trace docs

## License

MIT
