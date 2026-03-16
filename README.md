# Tenth Man

A GitHub Copilot CLI plugin that adds a verification agent inspired by the **Tenth Man Rule**.

> *If nine people agree, the tenth must assume they are all wrong.*

## What it does

The **Tenth Man** agent stress-tests its own answers before showing them to you. Instead of giving you the first plausible response, it:

1. Drafts an initial answer
2. Generates verification questions designed to expose flaws in that answer
3. Answers each question independently
4. Revises the final answer based on what verification revealed

This catches wrong assumptions, missing edge cases, and unverified claims — before they reach you.

## Install

```bash
copilot plugin install <owner>/10thman
```

## Use

Start a Copilot CLI session and select the agent:

```
/agent
```

Pick **Tenth Man** from the list. Or just ask Copilot to use it:

```
Use the tenth-man agent to review this function
```

## Uninstall

```bash
copilot plugin uninstall tenth-man
```

## Inspiration

- [The Tenth Man Rule](https://themindcollection.com/the-tenth-man-rule-devils-advocacy)
- *World War Z* — the Mossad doctrine of mandatory dissent
