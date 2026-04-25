---
workflowType: 'test-skill'
skillName: ''
skillDir: ''
runId: ''
testMode: ''
forgeTier: ''
testResult: ''
score: ''
threshold: ''
analysisConfidence: ''
toolingStatus: ''
workspaceDrift: ''
health_check_dispatched: false
testDate: ''
stepsCompleted: []
nextWorkflow: ''
---

# Test Report: {{skillName}}

<!--
Section order is LOAD-BEARING: step-05 §5 enforces it, step-06 §5 verifies
stepsCompleted against the canonical chain. Do not reorder or delete anchors.

Anchor / Step mapping:
  Test Summary       → step-02-detect-mode
  Coverage Analysis  → step-03-coverage-check
  Coherence Analysis → step-04-coherence-check
  External Validation→ step-04b-external-validators
  Completeness Score → step-05-score
  Gap Report         → step-06-report (includes Discovery Quality subsection)
-->

## Test Summary

<!-- Populated by step-02-detect-mode §3 -->

## Coverage Analysis

<!-- Populated by step-03-coverage-check §5 -->

## Coherence Analysis

<!-- Populated by step-04-coherence-check §6 (naive or contextual variant) -->

## External Validation

<!-- Populated by step-04b-external-validators §5 -->

## Completeness Score

<!-- Populated by step-05-score §6 -->

## Gap Report

<!-- Populated by step-06-report §3-§4b (includes Discovery Quality subsection) -->

