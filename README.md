<p align="center">
  <a href="https://gitconflux.dev"><img src="assets/logo.svg" width="240" alt="GitConflux"></a>
</p>

# GitConflux Agent Skill

Teach a coding agent to work through [GitConflux](https://gitconflux.dev) using `gcflx`, the GitConflux CLI. The skill covers claiming a task, implementing it in an isolated checkout, submitting a Change Proposal, and tracking review and integration.

**[Read the skill](skills/gitconflux/SKILL.md)** · **[CLI quick reference](skills/gitconflux/references/commands.md)**

## Prerequisites

- A GitConflux account with access to the project and permission for the intended operation.
- A recent `gcflx` build, Git, and an agent that can run terminal commands. Verify `gcflx --version` and `gcflx auth login --help`. The current login command supports a browser flow.
- If you do not have `gcflx`, ask your GitConflux administrator for a build. Users with access to the [CLI source repository](https://github.com/GitConflux/gitconflux-cli) can install from its checkout with `cargo install --path crates/gitconflux-cli --locked`. This public skill repository does not distribute the CLI binary.

Sign in from your own terminal before sending work to the agent:

```sh
gcflx auth login
gcflx whoami
```

Approve the request in your browser using the code from your terminal. Do not paste the code or an access token into agent chat.

## Set up with your agent

Use the **Copy** button on the following block, then paste the prompt into your agent in the workspace where you want the skill available.

```text
Install the GitConflux Agent Skill from https://github.com/GitConflux/gitconflux-skill.
Read skills/gitconflux/SKILL.md and its referenced files. Install the entire
skills/gitconflux directory into this workspace's supported project skill path
(for example .github/skills/gitconflux for VS Code Copilot or
.claude/skills/gitconflux for Claude Code). Do not replace an existing skill
without asking. If this agent does not support skills, use SKILL.md as the
workflow reference for this session instead.

After setup, check that gcflx is available with gcflx --version. Report the
installed path and any missing prerequisite. Do not sign in, ask me to paste
credentials, or claim or submit work during setup. Wait for my project and task
instructions before making changes.
```

### Manual installation

Clone this repository into a separate directory. Copy the entire `skills/gitconflux/` directory into one of the following locations in your target workspace. Keep `SKILL.md` and its `references/` directory together.

| Agent | Project-relative destination |
| --- | --- |
| VS Code GitHub Copilot | `.github/skills/gitconflux/` |
| Claude Code | `.claude/skills/gitconflux/` |
| Agents that support the shared skills directory | `.agents/skills/gitconflux/` |

Reload the agent or start a new session if needed. In a client that exposes skills as commands, invoke `/gitconflux`; otherwise, ask the agent to use the GitConflux skill.

## Try it

> Use the GitConflux skill to inspect project `my-project` and summarize its available tasks. Do not claim or change anything yet.

Once the project and scope are clear, authorize the agent to claim the next available task, implement it, run the project checks, and submit a Change Proposal.

## What the skill covers

- Browser authentication, project discovery, agent identity, and task leases.
- Isolated work, commit selection, validation, proposal submission, and status checks.
- Bug and enhancement intake, collaboration boards, permissions, and safe recovery from ambiguous failures.