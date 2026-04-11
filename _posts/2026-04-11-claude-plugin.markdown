---
layout: post
title:  "Claude Code Plugin: AI-Native Flink Pipeline Orchestration"
date:   2026-04-11 00:00:00 +0530
---

 I built an AI-native agentic workflow that automates end-to-end Apache Flink streaming pipeline creation on our internal data platform, replacing a tedious, multi-step manual process with an AI-managed conversational experience powered by Claude Code.

## The Problem

Creating a Flink pipeline required engineers to navigate a 6-8 step manual workflow, relying on a wiki doc to get through each step.

Engineers context-switched between the JupyterLab UI, terminal, wiki docs, access control portals, and metadata catalogs. Build failures, stale clusters, and access control misconfigurations routinely required oncall escalation. The median time to a working pipeline was measured in hours, not minutes.

## My Approach

I built a Claude Code plugin with 11 composable skills — each backed by a purpose-built CLI that talks directly to the platform's kernel sessions, Flink SQL gateway, access control services, and schema registry APIs.


<p align="center">
  <img src="{{ '/assets/images/workflow.png' | relative_url }}" alt="Flink Pipeline Automation: Before vs After" />
</p>

What makes this truly AI-native — and not just a CLI with a chat wrapper — is the **reasoning and recovery layer**. After every skill step, the agent evaluates the full log output and takes corrective action autonomously:

- **Build failure**: Parses the Gradle error, fixes the build config, re-runs the build.
- **Cluster recycled mid-session**: Detects the error, reprovisions automatically, resumes where it left off.
- **Job pod crash**: Fetches Kubernetes pod logs, diagnoses root cause (OOM, misconfiguration), suggests or applies fix.
- **Access control pending**: Identifies the request, provides the approval URL, advises retry after approval.
- **DDL placeholder mismatch**: Validates substitution against app config before execution, flags mismatches proactively.

I also built a session summary skill that reconstructs the entire session state from conversation logs — a structured audit trail of every operation, failure, and fix.

## Human-in-the-loop visibility

The agent before running each command, it surfaces the exact parameters and a 1–2 line explanation of what the command does and its expected execution time — giving engineers a moment to review.

Engineers can also check progress at any point via a summary command, which prints a structured view of what has completed and what remains. This surfaces the essential details that previously got buried in kernel logs.

## Impact

- **Hours to minutes**: The full workflow completes in a single conversational session.
- **Zero context switching**: Everything happens in one terminal — no more toggling between UI, wiki, portals, and catalogs.
- **Self-healing reduces escalations**: Failures that previously required oncall help are resolved by the agent inline.
- **Human-in-the-loop visibility**: Engineers stay informed at every step — no more digging through logs to understand what happened.
- **Composable by design**: Each skill runs independently — add a single source without re-running the full workflow.
- **No platform changes required**: The plugin integrates at the CLI layer with zero modifications to the underlying platform.