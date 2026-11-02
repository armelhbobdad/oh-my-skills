---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261102T220003Z-e01e5ee1'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'blocked'
testResult: 'fail'
score: ''
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: ''
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-02T22:00:03Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'report']
nextWorkflow: 'update-skill'
---

# Test Report: oms-storybook-react-vite

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once and that no placeholder comment is left: a stage that
skipped its section stops the run there. Do not reorder or delete the
headings or their placeholder comments.

Heading / owning step:
  Test Summary        → detect-mode §2
  Coverage Analysis   → coverage-check §5
  Coherence Analysis  → coherence-check §6
  External Validation → external-validators §5
  (hard gate)         → step-hard-gate reads the gap ledger; it writes the
                        Completeness Score section only when it blocks the run
  Completeness Score  → score §6, or step-hard-gate §3 on a blocked run
  Gap Report          → report §4c, rendered from the gap ledger (with the
                        Discovery Quality subsection)
-->

## Test Summary

**Skill:** oms-storybook-react-vite
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json records `skill_type: "single"` (one library, the Storybook 10.3.5 React + Vite authoring surface), so the skill is tested in naive mode: API-surface coverage, with structural coherence only and no coherence category in scoring.

**Analysis Plan:**
- Coverage Check: Deep tier — AST-backed (ast-grep) extraction of the public export surface from the pinned source (e486d38, workspace HEAD matches), compared against every export SKILL.md and references/ document, with signature and type checks.
- Coherence Check: structural only (naive mode) — references/ files resolve, internal links and section structure are consistent; no cross-skill integration validation.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces
**Denominator:** Stratified scope, denominator: effective_denominator (216 exports; 1274 files matched by scope.include, 985 exports scope.include union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: 216  ← chosen on the scalar branch
- `scope.tier_a_include` union: 280
- `scope.include` union: 985
- exports-map subpath union: 1281
- root barrel: 54                               (secondary candidate: root-barrel-vs-subpath-union audit)

**Files Analyzed:** 319

### Export Coverage

No per-export table: the scalar denominator (`stats.effective_denominator`) counts the exports without naming them. The summary below gives the counts.

### Coverage Summary

- **Exports Found:** 216
- **Documented:** 453 (100%)
- **Missing Documentation:** 0 (a floored residual: the numerator exceeds the denominator)
- **Signature Mismatches:** 14
- **Stale Documentation:** N/A: the scalar denominator (`stats.effective_denominator`) counts the exports without naming them
- **Numerator Surplus:** 237, uncapped coverage 209.72%
- **Scoped Out by the Brief:** `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx), `AngularMeta` (code/frameworks/angular/src/client/preview.ts), `AngularOptions` (code/frameworks/angular/src/types.ts), `AngularPreview` (code/frameworks/angular/src/client/preview.ts), `AngularRenderer` (code/frameworks/angular/src/client/types.ts), `AngularStory` (code/frameworks/angular/src/client/preview.ts), `BabelFileClass` (code/core/src/babel/index.ts), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts), `Bar` (code/core/src/components/components/Bar/Bar.tsx), `BaseLocationProvider` (code/core/src/router/router.tsx), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx), `BuildIndexOptions` (code/core/src/core-server/build-index.ts), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts), `CacheEntry` (code/core/src/telemetry/event-cache.ts), `Channel` (code/core/src/channels/main.ts), `ChannelHandler` (code/core/src/channels/types.ts), `ChannelTransport` (code/core/src/channels/types.ts), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts), `CsfFile` (code/core/src/csf-tools/CsfFile.ts), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts), `DL` (code/core/src/components/components/typography/elements/DL.tsx), `Dependency` (code/core/src/telemetry/types.ts), `Div` (code/core/src/components/components/typography/elements/Div.tsx), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts), `ErrorCollector` (code/core/src/telemetry/error-collector.ts), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx), `EventType` (code/core/src/telemetry/types.ts), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts), `H1` (code/core/src/components/components/typography/elements/H1.tsx), `H2` (code/core/src/components/components/typography/elements/H2.tsx), `H3` (code/core/src/components/components/typography/elements/H3.tsx), `H4` (code/core/src/components/components/typography/elements/H4.tsx), `H5` (code/core/src/components/components/typography/elements/H5.tsx), `H6` (code/core/src/components/components/typography/elements/H6.tsx), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts), `HR` (code/core/src/components/components/typography/elements/HR.tsx), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts), `IStory` (code/frameworks/angular/src/client/types.ts), `InitPayload` (code/core/src/telemetry/types.ts), `LI` (code/core/src/components/components/typography/elements/LI.tsx), `LinkProps` (code/core/src/router/types.ts), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx), `Location` (code/core/src/router/router.tsx), `LocationProvider` (code/core/src/router/router.tsx), `LogLevel` (code/core/src/node-logger/logger/logger.ts), `MemoryRouter` (code/core/src/router/router.tsx), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts), `NavigateFunction` (code/core/src/router/types.ts), `NavigateOptions` (code/core/src/router/types.ts), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts), `OL` (code/core/src/components/components/typography/elements/OL.tsx), `Other` (code/core/src/router/types.ts), `P` (code/core/src/components/components/typography/elements/P.tsx), `Payload` (code/core/src/telemetry/types.ts), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx), `Popover` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts), `PreactRenderer` (code/renderers/preact/src/types.ts), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx), `RenderData` (code/core/src/router/types.ts), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx), `Route` (code/core/src/router/router.tsx), `RouterData` (code/core/src/router/types.ts), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx), `Separator` (code/core/src/components/components/Bar/Separator.tsx), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx), `Span` (code/core/src/components/components/typography/elements/Span.tsx), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts), `StaticStory` (code/core/src/csf-tools/CsfFile.ts), `StoryData` (code/core/src/router/utils.ts), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts), `StoryTest` (code/core/src/csf-tools/CsfFile.ts), `StorybookAddon` (code/core/src/telemetry/types.ts), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx), `StorybookMetadata` (code/core/src/telemetry/types.ts), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts), `SvelteRenderer` (code/renderers/svelte/src/types.ts), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `TT` (code/core/src/components/components/typography/elements/TT.tsx), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx), `TabButton` (code/core/src/components/components/Tabs/Button.tsx), `TabList` (code/core/src/components/components/Tabs/TabList.tsx), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `TelemetryData` (code/core/src/telemetry/types.ts), `TelemetryEvent` (code/core/src/telemetry/types.ts), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts), `UL` (code/core/src/components/components/typography/elements/UL.tsx), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts), `WebComponentsStory` (code/renderers/web-components/src/preview.ts), `WebComponentsTypes` (code/renderers/web-components/src/types.ts), `WebsocketTransport` (code/core/src/channels/websocket/index.ts), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts), `babelParseExpression` (code/core/src/babel/babelParse.ts), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts), `babelPrint` (code/core/src/babel/babelParse.ts), `buildArgsParam` (code/core/src/router/utils.ts), `buildDevStandalone` (code/core/src/core-server/build-dev.ts), `buildIndexStandalone` (code/core/src/core-server/build-index.ts), `buildStaticStandalone` (code/core/src/core-server/build-static.ts), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts), `cleanPaths` (code/core/src/telemetry/sanitize.ts), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx), `colors` (code/core/src/node-logger/index.ts), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts), `components` (code/core/src/components/index.ts), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `createBrowserChannel` (code/core/src/channels/index.ts), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts), `experimental_loadStorybook` (code/core/src/core-server/load.ts), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts), `extractSource` (code/core/src/csf-tools/enrichCsf.ts), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts), `formatCsf` (code/core/src/csf-tools/CsfFile.ts), `framework` (code/core/src/core-server/presets/common-override-preset.ts), `generate` (code/core/src/babel/index.ts), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts), `getCustomElements` (code/renderers/web-components/src/framework-api.ts), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts), `getLastEvents` (code/core/src/telemetry/event-cache.ts), `getMatch` (code/core/src/router/utils.ts), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts), `getServerPort` (code/core/src/core-server/utils/server-address.ts), `getSessionId` (code/core/src/telemetry/session-id.ts), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts), `hrefTo` (code/addons/links/src/utils.ts), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts), `isExampleStoryId` (code/core/src/telemetry/index.ts), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts), `isValidComponent` (code/renderers/web-components/src/framework-api.ts), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts), `linkTo` (code/addons/links/src/utils.ts), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts), `loadCsf` (code/core/src/csf-tools/CsfFile.ts), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx), `navigate` (code/addons/links/src/utils.ts), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts), `parsePath` (code/core/src/router/utils.ts), `parserOptions` (code/core/src/babel/babelParse.ts), `printConfig` (code/core/src/csf-tools/ConfigFile.ts), `printCsf` (code/core/src/csf-tools/CsfFile.ts), `prompt` (code/core/src/node-logger/prompts/index.ts), `protectUrls` (code/core/src/node-logger/wrap-utils.ts), `queryFromLocation` (code/core/src/router/utils.ts), `readConfig` (code/core/src/csf-tools/ConfigFile.ts), `readCsf` (code/core/src/csf-tools/CsfFile.ts), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts), `resetComponents` (code/core/src/components/index.ts), `resolveExpression` (code/core/src/babel/expression-resolver.ts), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts), `sanitizeError` (code/core/src/telemetry/sanitize.ts), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts), `setCustomElements` (code/renderers/web-components/src/framework-api.ts), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts), `stories` (code/core/src/core-server/presets/common-override-preset.ts), `stringifyQuery` (code/core/src/router/utils.ts), `telemetry` (code/core/src/telemetry/index.ts), `traverse` (code/core/src/babel/index.ts), `typescript` (code/core/src/core-server/presets/common-override-preset.ts), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts), `useNavigate` (code/core/src/router/router.tsx), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `withLinks` (code/addons/links/src/utils.ts), `withReset` (code/core/src/components/components/typography/lib/common.tsx), `withTelemetry` (code/core/src/core-server/withTelemetry.ts), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts), `writeCsf` (code/core/src/csf-tools/CsfFile.ts)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 82.93% |
| Type Coverage | 74.17% |

**Notes:**
- Deep tier: `gh api repos/storybookjs/storybook/git/ref/tags/v10.3.5` resolves to `e486d3826bcd40c52db1c766966d1c8ec16df6cb`, the `metadata.source_commit`; the workspace HEAD matches it (init §5b).
- Extraction: `skf-extract-public-api.py --mode full` status `ok` over 1274 in-scope files (113 entry points, `entry_points.status` barrel). The runner reported 5 `syntax-errors` file issues (`code/core/src/csf/csf-factories.ts:75`, `code/core/src/instrumenter/typings.d.ts:8`, `code/core/src/mocking-utils/esmWalker.ts:37`, `code/core/src/test/spy.ts:15`, `code/core/src/typings.d.ts:28`), listed in `extraction.readByEye`; status is not `incomplete`, so no per-file read-by-eye pass ran.
- `extractionGaps[]`: 7 names no recipe found (`BabelFile`, `GeneratorOptions`, `NodePath`, `analyzeMdx`, `babelParse`, `instance`, `transformSync`), each with no file or line, so no signature could be read for them; none is in the `tier_a_include` set.
- Denominator: the stratified-scope clause takes `stats.effective_denominator` (216) at ladder step 1 because `guards.deflation.fires` is false (the brief's `scope.tier_a_include` globs count 280 public names, which suppresses the deflation guard); `tier_a_include` (280) is the `surfaceSet` the signature and type scores read. `guards.staleScope` did not fire (every `scope.include` and `scope.tier_a_include` glob matches a file); `guards.inflation` not applicable; umbrella ratio 0.93 over 12 root entries.
- Numerator ground truth (§2b): `stats.exports_documented` (216) equals `stats.effective_denominator` (216), so the check ran: declared 82, verified 82, absent 0 — not inflated.
- Split-body consistency (§1b): the inventory subagent found 2 SKILL.md vs `references/` mismatches (`StoryObj`, `composeStories`), recorded as High `split-body-mismatch` gaps.
- Signature comparison: 82 documented names compared across 56 source files by 5 subagents (grouped by file); 14 mismatches; the score uses `--surface-set tier_a_include`. 31 tier A types are undocumented (`missingTypes`).
- Metadata count coherence (§4b): 2 Medium `metadata-drift` findings (`stats.exports_public_api`=216 vs `exports[].length`=82; `stats.exports_documented`=216 vs provenance named-exports 222 / confidence_distribution sum 572) and 1 Info `multi-denominator` finding.
- Provenance line check (§4c): 222 entries checked; 79 `line-not-definition` items (Low `provenance-line` where the helper found a definition line, else Info `provenance-unverified`); the helper's 2 `file-missing`, 3 `missing` and 143 `orphaned` findings are outside this section.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| 1 | missing_section | High | naive-coherence: missing required section: api_surface. No heading matches the API-surface family (`tried`: API, API Surface, Exports, Key Exports, Public API, Interface, Reference, Key API Summary, Pattern Surface, Component Catalog), and no body section lists the library's exports: `Key Types (quick-start essentials)` (line 149) declares three types (`Meta`, `StoryObj`, `Preview`), `v10 Import Corrections` (line 125) lists three import-path rewrites, and `Full API Reference` (line 182) is a stub that points to `references/`. The Tier 1 `Key API Summary` table of the SKF section catalog (`skf-create-skill/assets/skill-sections.md`, row 4, "always inline, survives split-body") is absent. | — |

**Structural Issues:** 1

Checks with no finding: §2.1 `description` (matched `Overview`, line 20) and `usage` (matched `Quick Start`, line 29); §2.2 fences balanced (10 fences); §2.3 no bare opening fence; §2.4 every documented function export is referenced in a usage-family section or a reference file (`zero_usage` empty over 202 function exports; `## Full*` sections are stubs, so the split-body scope was used); §2.5 no export is described as async or sync against its examples (`composeStories`, `setProjectAnnotations`, `definePreview`, `expect`, `fn`, `getByRole`, `withThemeByClassName`, `withThemeByDataAttribute`, `withThemeFromJSXProvider` and `storybookTest` are called in examples; `expect` is awaited in 3 of 4 calls and `getByRole` in 2 of 4, but no description asserts either is sync); §2.6 no table drift; §2.7 no `scripts/` or `assets/` folder.

**Migration section (§2b):** Section 4b verification skipped: `forge-data/oms-storybook-react-vite/10.3.5/evidence-report.md` exists but has no YAML frontmatter, so `t2_future_count` cannot be read (Case 4).

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| 1 | references/story-types.md | `StoryObj` | SKILL.md shows `type StoryObj<TMeta>;` (one required generic); the reference shows `StoryObj<TMetaOrCmpOrArgs = Args>` (optional generic accepting a meta, a component or raw args), as `code/renderers/react/src/public-types.ts:47` defines it | 156 | 80 |
| 2 | references/story-types.md | `composeStories` | SKILL.md recommends `import { composeStories } from 'storybook/preview-api'` (or `@storybook/react`); the reference says prefer `@storybook/react-vite` and keep the `storybook/preview-api` re-export for non-renderer infrastructure code | 117 | 181 |

**Exports Cross-Checked:** 45 (inventory names that occur in both the SKILL.md body and a reference file)
**Mismatches Found:** 2 (recorded by coverage-check §1b)

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 100%
- **Tools used:** skill-check

## Completeness Score

**Result:** **FAIL**, not scored: the hard gate blocked this run on 17 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 99
**Blocking (Critical + High):** 17
**Non-blocking (Medium + Low + Info):** 82

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 14 | Read the source code and write or correct the documentation |
| High | 3 | Read the source code and write or correct the documentation |
| Medium | 2 | Add type definitions, interface docs or the missing section |
| Low | 34 | Add examples or metadata |
| Info | 46 | Optional improvements, no action required |
| **Total** | **99** | |

### GAP-001: Signature mismatch: Description

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Description.tsx:74
**Export:** Description

**Issue:** documented `{ of?, markdown? }`, source `Description = withMdxComponentOverride('Description', DescriptionImpl: FC<DescriptionProps>) where DescriptionProps = { of?: Of }`: The documented `markdown` prop does not exist; DescriptionProps declares only `of?: Of`.

**Remediation:** Update the documented signature of `Description` from `{ of?, markdown? }` to `Description = withMdxComponentOverride('Description', DescriptionImpl: FC<DescriptionProps>) where DescriptionProps = { of?: Of }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Description.tsx:74`.

### GAP-002: Signature mismatch: Primary

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Primary.tsx:16
**Export:** Primary

**Issue:** documented `{ of? }`, source `Primary = withMdxComponentOverride('Primary', PrimaryImpl: FC) (no props; renders usePrimaryStory())`: The documented `of` prop does not exist; PrimaryImpl is declared as a bare `FC` with no props and always uses the attached CSF file's primary story.

**Remediation:** Update the documented signature of `Primary` from `{ of? }` to `Primary = withMdxComponentOverride('Primary', PrimaryImpl: FC) (no props; renders usePrimaryStory())`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Primary.tsx:16`.

### GAP-003: Signature mismatch: Stories

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Stories.tsx:74
**Export:** Stories

**Issue:** documented `{ of?, includePrimary?, title? }`, source `Stories = withMdxComponentOverride('Stories', StoriesImpl: FC<StoriesProps>) where StoriesProps = { title?: ReactElement | string; includePrimary?: boolean }`: The documented `of` prop does not exist; StoriesProps declares only `title?` and `includePrimary?`, and the block always reads componentStories() from DocsContext.

**Remediation:** Update the documented signature of `Stories` from `{ of?, includePrimary?, title? }` to `Stories = withMdxComponentOverride('Stories', StoriesImpl: FC<StoriesProps>) where StoriesProps = { title?: ReactElement | string; includePrimary?: boolean }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Stories.tsx:74`.

### GAP-004: Signature mismatch: Story

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:134
**Export:** Story

**Issue:** documented `{ of, expanded, ... }`, source `Story = withMdxComponentOverride('Story', StoryImpl: FC<StoryProps>) where StoryProps = { of?: ModuleExport; meta?: ModuleExports } & { inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }`: The documented `expanded` prop does not exist on StoryProps (it belongs to DocsStory); Story accepts of?, meta?, inline?, height?, autoplay?, __forceInitialArgs?, __primary?.

**Remediation:** Update the documented signature of `Story` from `{ of, expanded, ... }` to `Story = withMdxComponentOverride('Story', StoryImpl: FC<StoryProps>) where StoryProps = { of?: ModuleExport; meta?: ModuleExports } & { inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Story.tsx:134`.

### GAP-005: Signature mismatch: ColorPalette

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/components/ColorPalette.tsx:202
**Export:** ColorPalette

**Issue:** documented `{ children: ColorItem[] }`, source `ColorPalette: FunctionComponent<ColorPaletteProps> = ({ children, ...props }) where ColorPaletteProps { children?: React.ReactNode }`: The skill documents children as a required ColorItem[] prop, but the declaration types it as optional React.ReactNode (children?: React.ReactNode).

**Remediation:** Update the documented signature of `ColorPalette` from `{ children: ColorItem[] }` to `ColorPalette: FunctionComponent<ColorPaletteProps> = ({ children, ...props }) where ColorPaletteProps { children?: React.ReactNode }`, the signature the source defines at `code/addons/docs/src/blocks/components/ColorPalette.tsx:202`.

### GAP-006: Signature mismatch: IconGallery

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/components/IconGallery.tsx:74
**Export:** IconGallery

**Issue:** documented `{ children: IconItem[] }`, source `IconGallery: FunctionComponent<IconGalleryProps> = ({ children, ...props }) where IconGalleryProps { children?: React.ReactNode }`: The skill documents children as a required IconItem[] prop, but the declaration types it as optional React.ReactNode (children?: React.ReactNode).

**Remediation:** Update the documented signature of `IconGallery` from `{ children: IconItem[] }` to `IconGallery: FunctionComponent<IconGalleryProps> = ({ children, ...props }) where IconGalleryProps { children?: React.ReactNode }`, the signature the source defines at `code/addons/docs/src/blocks/components/IconGallery.tsx:74`.

### GAP-007: Signature mismatch: start

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/builders/builder-vite/src/index.ts:41
**Export:** start

**Issue:** documented `start(options: BuilderOptions): Promise<{ bail, stats, totalTime }>`, source `start: ViteBuilder['start'] = async ({ startTime, options, router, server }: { options: Options; startTime; router: ServerApp; server: HttpServer; channel: ChannelLike }) => Promise<void | { stats?, totalTime, bail }>`: The builder takes a single args object { options: Options, startTime, router, server, channel }, not a positional options argument of type BuilderOptions ({ viteConfigPath?: string }).

**Remediation:** Update the documented signature of `start` from `start(options: BuilderOptions): Promise<{ bail, stats, totalTime }>` to `start: ViteBuilder['start'] = async ({ startTime, options, router, server }: { options: Options; startTime; router: ServerApp; server: HttpServer; channel: ChannelLike }) => Promise<void | { stats?, totalTime, bail }>`, the signature the source defines at `code/builders/builder-vite/src/index.ts:41`.

### GAP-008: Signature mismatch: build

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/builders/builder-vite/src/index.ts:63
**Export:** build

**Issue:** documented `build(options: BuilderOptions): Promise<any>`, source `build: ViteBuilder['build'] = async ({ options }: { options: Options; startTime: ReturnType<typeof process.hrtime> }) => Promise<void | ViteStats>`: The builder takes a single args object { options: Options, startTime } (destructuring options), not a positional options argument of type BuilderOptions ({ viteConfigPath?: string }).

**Remediation:** Update the documented signature of `build` from `build(options: BuilderOptions): Promise<any>` to `build: ViteBuilder['build'] = async ({ options }: { options: Options; startTime: ReturnType<typeof process.hrtime> }) => Promise<void | ViteStats>`, the signature the source defines at `code/builders/builder-vite/src/index.ts:63`.

### GAP-009: Signature mismatch: hasVitePlugins

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/builders/builder-vite/src/utils/has-vite-plugins.ts:13
**Export:** hasVitePlugins

**Issue:** documented `hasVitePlugins(config: InlineConfig): boolean`, source `async function hasVitePlugins(plugins: PluginOption[], names: string[]): Promise<boolean>`: Source takes two positional params (plugins: PluginOption[], names: string[]) and is async returning Promise<boolean>, whereas the skill documents a single InlineConfig param and a synchronous boolean return.

**Remediation:** Update the documented signature of `hasVitePlugins` from `hasVitePlugins(config: InlineConfig): boolean` to `async function hasVitePlugins(plugins: PluginOption[], names: string[]): Promise<boolean>`, the signature the source defines at `code/builders/builder-vite/src/utils/has-vite-plugins.ts:13`.

### GAP-010: Signature mismatch: withoutVitePlugins

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/builders/builder-vite/src/utils/without-vite-plugins.ts:2
**Export:** withoutVitePlugins

**Issue:** documented `withoutVitePlugins(config: InlineConfig): InlineConfig`, source `withoutVitePlugins = async <TPlugin>(plugins: TPlugin[] = [], namesToRemove: string[]): Promise<TPlugin[]>`: Source takes (plugins: TPlugin[] = [], namesToRemove: string[]) and resolves to the filtered plugin array Promise<TPlugin[]>, not a single InlineConfig param returning InlineConfig.

**Remediation:** Update the documented signature of `withoutVitePlugins` from `withoutVitePlugins(config: InlineConfig): InlineConfig` to `withoutVitePlugins = async <TPlugin>(plugins: TPlugin[] = [], namesToRemove: string[]): Promise<TPlugin[]>`, the signature the source defines at `code/builders/builder-vite/src/utils/without-vite-plugins.ts:2`.

### GAP-011: Signature mismatch: composeStory

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:90
**Export:** composeStory

**Issue:** documented `(story: StoryAnnotationsOrFn<ReactRenderer, TArgs>, componentAnnotations: Meta<TArgs | any>, projectAnnotations?: ProjectAnnotations<ReactRenderer>, exportsName?: string): ComposedStoryFn<ReactRenderer, Partial<TArgs>>`, source `composeStory<TRenderer extends Renderer = Renderer, TArgs extends Args = Args>(storyAnnotations: LegacyStoryAnnotationsOrFn<TRenderer>, componentAnnotations: ComponentAnnotations<TRenderer, TArgs>, projectAnnotations?: ProjectAnnotations<TRenderer>, defaultConfig?: ProjectAnnotations<TRenderer>, exportsName?: string): ComposedStoryFn<TRenderer, Partial<TArgs>>`: The core declaration has five positional params with defaultConfig at position 4 and exportsName at position 5, while the documented four-param form (the React wrapper at code/renderers/react/src/portable-stories.tsx:L106) puts exportsName at position 4, so passing it fourth to this export would bind it to defaultConfig.

**Remediation:** Update the documented signature of `composeStory` from `(story: StoryAnnotationsOrFn<ReactRenderer, TArgs>, componentAnnotations: Meta<TArgs | any>, projectAnnotations?: ProjectAnnotations<ReactRenderer>, exportsName?: string): ComposedStoryFn<ReactRenderer, Partial<TArgs>>` to `composeStory<TRenderer extends Renderer = Renderer, TArgs extends Args = Args>(storyAnnotations: LegacyStoryAnnotationsOrFn<TRenderer>, componentAnnotations: ComponentAnnotations<TRenderer, TArgs>, projectAnnotations?: ProjectAnnotations<TRenderer>, defaultConfig?: ProjectAnnotations<TRenderer>, exportsName?: string): ComposedStoryFn<TRenderer, Partial<TArgs>>`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:90`.

### GAP-012: Signature mismatch: composeStories

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:274
**Export:** composeStories

**Issue:** documented `(csfExports: TModule, projectAnnotations?: ProjectAnnotations<ReactRenderer>): Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>`, source `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory) — no annotated return (inferred {} from the reduce)`: This core declaration (the storybook/preview-api export) requires its second parameter globalConfig (documented as optional), takes a third optional composeStoryFn, and returns the un-cast reduce result rather than Omit<StoriesWithPartialProps<...>>; the documented form is the React renderer wrapper at code/renderers/react/src/portable-stories.tsx:L148, not this declaration.

**Remediation:** Update the documented signature of `composeStories` from `(csfExports: TModule, projectAnnotations?: ProjectAnnotations<ReactRenderer>): Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>` to `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory) — no annotated return (inferred {} from the reduce)`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:274`.

### GAP-013: Signature mismatch: mocked

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/test/spy.ts:119
**Export:** mocked

**Issue:** documented `(item: T, options?: { partial?: boolean; deep?: boolean }) => MaybeMocked<T>`, source `overloads: mocked<T>(item: T, deep?: false): MaybeMocked<T>; mocked<T>(item: T, deep: true): MaybeMockedDeep<T>; mocked<T>(item: T, options: { partial?: false; deep?: false }): MaybeMocked<T>; mocked<T>(item: T, options: { partial?: false; deep: true }): MaybeMockedDeep<T>; mocked<T>(item: T, options: { partial: true; deep?: false }): MaybePartiallyMocked<T>; mocked<T>(item: T, options: { partial: true; deep: true }): MaybePartiallyMockedDeep<T>; mocked<T>(item: T): MaybeMocked<T>`: The declaration at L119 takes a boolean-literal second parameter `deep?: false` (not an options object), and the overload set returns MaybeMockedDeep/MaybePartiallyMocked/MaybePartiallyMockedDeep when deep or partial is true, whereas the documented signature collapses this into one options-object form that always returns MaybeMocked<T>.

**Remediation:** Update the documented signature of `mocked` from `(item: T, options?: { partial?: boolean; deep?: boolean }) => MaybeMocked<T>` to `overloads: mocked<T>(item: T, deep?: false): MaybeMocked<T>; mocked<T>(item: T, deep: true): MaybeMockedDeep<T>; mocked<T>(item: T, options: { partial?: false; deep?: false }): MaybeMocked<T>; mocked<T>(item: T, options: { partial?: false; deep: true }): MaybeMockedDeep<T>; mocked<T>(item: T, options: { partial: true; deep?: false }): MaybePartiallyMocked<T>; mocked<T>(item: T, options: { partial: true; deep: true }): MaybePartiallyMockedDeep<T>; mocked<T>(item: T): MaybeMocked<T>`, the signature the source defines at `code/core/src/test/spy.ts:119`.

### GAP-014: Signature mismatch: create

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/theming/create.ts:29
**Export:** create

**Issue:** documented `create(vars: ThemeVarsPartial, rest?: Rest): ThemeVars`, source `create(vars: ThemeVarsPartial = { base: preferredColorScheme }, rest?: Rest): ThemeVars`: `vars` has a default value in the source and is therefore optional (create() is callable with no arguments), but the documented signature presents it as a required parameter.

**Remediation:** Update the documented signature of `create` from `create(vars: ThemeVarsPartial, rest?: Rest): ThemeVars` to `create(vars: ThemeVarsPartial = { base: preferredColorScheme }, rest?: Rest): ThemeVars`, the signature the source defines at `code/core/src/theming/create.ts:29`.

### GAP-097: Split-body mismatch: StoryObj

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/story-types.md:80
**Export:** StoryObj

**Issue:** SKILL.md:156 declares `type StoryObj<TMeta>;` (one required generic) while references/story-types.md:80 shows `StoryObj<TMetaOrCmpOrArgs = Args>` (an optional generic that also accepts a component or a raw args type); the source at code/renderers/react/src/public-types.ts:47 is `export type StoryObj<TMetaOrCmpOrArgs = Args>`.

**Remediation:** Make SKILL.md and references/story-types.md document one StoryObj shape: change the Quick Start type line in SKILL.md:156 from `type StoryObj<TMeta>;` to `type StoryObj<TMetaOrCmpOrArgs = Args>;`, the form references/story-types.md:80 already gives and code/renderers/react/src/public-types.ts:47 defines; leave references/story-types.md:80 unchanged.

### GAP-098: Split-body mismatch: composeStories

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/story-types.md:181
**Export:** composeStories

**Issue:** SKILL.md:117 tells authors to `import { composeStories } from 'storybook/preview-api'` (or '@storybook/react') for portable stories, while references/story-types.md:181 says to prefer `@storybook/react-vite` and keep the `storybook/preview-api` re-export for non-renderer infrastructure code only.

**Remediation:** Make SKILL.md:117 match references/story-types.md:181: change the portable-stories recipe import to `import { composeStories } from '@storybook/react-vite'` (React renderer definition at code/renderers/react/src/portable-stories.tsx:148, `(csfExports, projectAnnotations?)`), and drop `storybook/preview-api` as the recommended source, whose composeStories (code/core/src/preview-api/modules/store/csf/portable-stories.ts:274) requires a `globalConfig` argument.

### GAP-099: naive-coherence: missing required section: api_surface

**Severity:** High
**Category:** Structural (structural)
**Source:** SKILL.md

**Issue:** no heading of SKILL.md serves the api_surface family (synonyms tried: API, API Surface, Exports, Key Exports, Public API, Interface, Reference, Key API Summary, Pattern Surface, Component Catalog)

**Remediation:** Add a `## Key API Summary` section to SKILL.md that lists the library's exports with their purpose.

### GAP-015: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_public_api=216, exports[].length=82 → 62% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json`; update-skill applies it as a metadata update.

### GAP-016: metadata drift — documented-surface export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_documented=216, provenance named-exports=222, confidence_distribution sum=572 → 62% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json`; update-skill applies it as a metadata update.

### GAP-018: Provenance line is not the definition of A11yGlobals

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/a11y/src/index.ts:1
**Export:** A11yGlobals

**Issue:** the provenance map records `A11yGlobals` at `code/addons/a11y/src/index.ts:1`, which is not the line that defines it; the lines that define it are 8.

**Remediation:** Set the provenance `source_line` of `A11yGlobals` in `code/addons/a11y/src/index.ts` to its definition line (8) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-020: Provenance line is not the definition of A11yReport

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/a11y/src/index.ts:1
**Export:** A11yReport

**Issue:** the provenance map records `A11yReport` at `code/addons/a11y/src/index.ts:1`, which is not the line that defines it; the lines that define it are 8.

**Remediation:** Set the provenance `source_line` of `A11yReport` in `code/addons/a11y/src/index.ts` to its definition line (8) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-022: Provenance line is not the definition of ADDON_ID

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/vitest/src/constants.ts:1
**Export:** ADDON_ID

**Issue:** the provenance map records `ADDON_ID` at `code/addons/vitest/src/constants.ts:1`, which is not the line that defines it; the lines that define it are 11.

**Remediation:** Set the provenance `source_line` of `ADDON_ID` in `code/addons/vitest/src/constants.ts` to its definition line (11) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-028: Provenance line is not the definition of Decorator

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/public-types.ts:55
**Export:** Decorator

**Issue:** the provenance map records `Decorator` at `code/renderers/react/src/public-types.ts:55`, which is not the line that defines it; the lines that define it are 77.

**Remediation:** Set the provenance `source_line` of `Decorator` in `code/renderers/react/src/public-types.ts` to its definition line (77) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-033: Provenance line is not the definition of DocsRenderer

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/docs/src/index.ts:1
**Export:** DocsRenderer

**Issue:** the provenance map records `DocsRenderer` at `code/addons/docs/src/index.ts:1`, which is not the line that defines it; the lines that define it are 8.

**Remediation:** Set the provenance `source_line` of `DocsRenderer` in `code/addons/docs/src/index.ts` to its definition line (8) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-034: Provenance line is not the definition of FrameworkOptions

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/frameworks/react-vite/src/types.ts:1
**Export:** FrameworkOptions

**Issue:** the provenance map records `FrameworkOptions` at `code/frameworks/react-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 14.

**Remediation:** Set the provenance `source_line` of `FrameworkOptions` in `code/frameworks/react-vite/src/types.ts` to its definition line (14) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-040: Provenance line is not the definition of Loader

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/public-types.ts:60
**Export:** Loader

**Issue:** the provenance map records `Loader` at `code/renderers/react/src/public-types.ts:60`, which is not the line that defines it; the lines that define it are 78.

**Remediation:** Set the provenance `source_line` of `Loader` in `code/renderers/react/src/public-types.ts` to its definition line (78) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-042: Provenance line is not the definition of PARAM_KEY

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/a11y/src/index.ts:1
**Export:** PARAM_KEY

**Issue:** the provenance map records `PARAM_KEY` at `code/addons/a11y/src/index.ts:1`, which is not the line that defines it; the lines that define it are 6.

**Remediation:** Set the provenance `source_line` of `PARAM_KEY` in `code/addons/a11y/src/index.ts` to its definition line (6) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-044: Provenance line is not the definition of ReactMeta

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/preview.tsx:1
**Export:** ReactMeta

**Issue:** the provenance map records `ReactMeta` at `code/renderers/react/src/preview.tsx:1`, which is not the line that defines it; the lines that define it are 147.

**Remediation:** Set the provenance `source_line` of `ReactMeta` in `code/renderers/react/src/preview.tsx` to its definition line (147) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-045: Provenance line is not the definition of ReactPreview

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/preview.tsx:1
**Export:** ReactPreview

**Issue:** the provenance map records `ReactPreview` at `code/renderers/react/src/preview.tsx:1`, which is not the line that defines it; the lines that define it are 102.

**Remediation:** Set the provenance `source_line` of `ReactPreview` in `code/renderers/react/src/preview.tsx` to its definition line (102) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-046: Provenance line is not the definition of ReactRenderer

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/types.ts:1
**Export:** ReactRenderer

**Issue:** the provenance map records `ReactRenderer` at `code/renderers/react/src/types.ts:1`, which is not the line that defines it; the lines that define it are 8.

**Remediation:** Set the provenance `source_line` of `ReactRenderer` in `code/renderers/react/src/types.ts` to its definition line (8) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-047: Provenance line is not the definition of ReactStory

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/preview.tsx:1
**Export:** ReactStory

**Issue:** the provenance map records `ReactStory` at `code/renderers/react/src/preview.tsx:1`, which is not the line that defines it; the lines that define it are 249.

**Remediation:** Set the provenance `source_line` of `ReactStory` in `code/renderers/react/src/preview.tsx` to its definition line (249) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-052: Provenance line is not the definition of StoryContext

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/public-types.ts:65
**Export:** StoryContext

**Issue:** the provenance map records `StoryContext` at `code/renderers/react/src/public-types.ts:65`, which is not the line that defines it; the lines that define it are 79.

**Remediation:** Set the provenance `source_line` of `StoryContext` in `code/renderers/react/src/public-types.ts` to its definition line (79) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-054: Provenance line is not the definition of StoryFn

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/public-types.ts:35
**Export:** StoryFn

**Issue:** the provenance map records `StoryFn` at `code/renderers/react/src/public-types.ts:35`, which is not the line that defines it; the lines that define it are 38.

**Remediation:** Set the provenance `source_line` of `StoryFn` in `code/renderers/react/src/public-types.ts` to its definition line (38) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-055: Provenance line is not the definition of StorybookConfig

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/frameworks/react-vite/src/types.ts:1
**Export:** StorybookConfig

**Issue:** the provenance map records `StorybookConfig` at `code/frameworks/react-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 66.

**Remediation:** Set the provenance `source_line` of `StorybookConfig` in `code/frameworks/react-vite/src/types.ts` to its definition line (66) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-056: Provenance line is not the definition of StorybookConfigVite

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/types.ts:1
**Export:** StorybookConfigVite

**Issue:** the provenance map records `StorybookConfigVite` at `code/builders/builder-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 17.

**Remediation:** Set the provenance `source_line` of `StorybookConfigVite` in `code/builders/builder-vite/src/types.ts` to its definition line (17) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-058: Provenance line is not the definition of TEST_PROVIDER_ID

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/vitest/src/constants.ts:1
**Export:** TEST_PROVIDER_ID

**Issue:** the provenance map records `TEST_PROVIDER_ID` at `code/addons/vitest/src/constants.ts:1`, which is not the line that defines it; the lines that define it are 12.

**Remediation:** Set the provenance `source_line` of `TEST_PROVIDER_ID` in `code/addons/vitest/src/constants.ts` to its definition line (12) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-059: Provenance line is not the definition of ThemeProvider

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/theming/index.ts:10
**Export:** ThemeProvider

**Issue:** the provenance map records `ThemeProvider` at `code/core/src/theming/index.ts:10`, which is not the line that defines it; the lines that define it are 17.

**Remediation:** Set the provenance `source_line` of `ThemeProvider` in `code/core/src/theming/index.ts` to its definition line (17) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-060: Provenance line is not the definition of ThemesGlobals

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/themes/src/index.ts:1
**Export:** ThemesGlobals

**Issue:** the provenance map records `ThemesGlobals` at `code/addons/themes/src/index.ts:1`, which is not the line that defines it; the lines that define it are 6.

**Remediation:** Set the provenance `source_line` of `ThemesGlobals` in `code/addons/themes/src/index.ts` to its definition line (6) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-065: Provenance line is not the definition of ViteBuilder

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/types.ts:1
**Export:** ViteBuilder

**Issue:** the provenance map records `ViteBuilder` at `code/builders/builder-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 10.

**Remediation:** Set the provenance `source_line` of `ViteBuilder` in `code/builders/builder-vite/src/types.ts` to its definition line (10) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-066: Provenance line is not the definition of ViteFinal

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/types.ts:1
**Export:** ViteFinal

**Issue:** the provenance map records `ViteFinal` at `code/builders/builder-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 12.

**Remediation:** Set the provenance `source_line` of `ViteFinal` in `code/builders/builder-vite/src/types.ts` to its definition line (12) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-067: Provenance line is not the definition of __definePreview

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/preview.tsx:1
**Export:** __definePreview

**Issue:** the provenance map records `__definePreview` at `code/renderers/react/src/preview.tsx:1`, which is not the line that defines it; the lines that define it are 55.

**Remediation:** Set the provenance `source_line` of `__definePreview` in `code/renderers/react/src/preview.tsx` to its definition line (55) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-071: Provenance line is not the definition of action

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/actions/runtime/action.ts:1
**Export:** action

**Issue:** the provenance map records `action` at `code/core/src/actions/runtime/action.ts:1`, which is not the line that defines it; the lines that define it are 50.

**Remediation:** Set the provenance `source_line` of `action` in `code/core/src/actions/runtime/action.ts` to its definition line (50) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-072: Provenance line is not the definition of bail

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** bail

**Issue:** the provenance map records `bail` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 37.

**Remediation:** Set the provenance `source_line` of `bail` in `code/builders/builder-vite/src/index.ts` to its definition line (37) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-073: Provenance line is not the definition of build

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** build

**Issue:** the provenance map records `build` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 63.

**Remediation:** Set the provenance `source_line` of `build` in `code/builders/builder-vite/src/index.ts` to its definition line (63) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-074: Provenance line is not the definition of configureActions

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/actions/runtime/configureActions.ts:1
**Export:** configureActions

**Issue:** the provenance map records `configureActions` at `code/core/src/actions/runtime/configureActions.ts:1`, which is not the line that defines it; the lines that define it are 9.

**Remediation:** Set the provenance `source_line` of `configureActions` in `code/core/src/actions/runtime/configureActions.ts` to its definition line (9) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-075: Provenance line is not the definition of css

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/theming/index.ts:10
**Export:** css

**Issue:** the provenance map records `css` at `code/core/src/theming/index.ts:10`, which is not the line that defines it; the lines that define it are 13.

**Remediation:** Set the provenance `source_line` of `css` in `code/core/src/theming/index.ts` to its definition line (13) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-078: Provenance line is not the definition of hasVitePlugins

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** hasVitePlugins

**Issue:** the provenance map records `hasVitePlugins` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 15.

**Remediation:** Set the provenance `source_line` of `hasVitePlugins` in `code/builders/builder-vite/src/index.ts` to its definition line (15) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-079: Provenance line is not the definition of keyframes

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/theming/index.ts:10
**Export:** keyframes

**Issue:** the provenance map records `keyframes` at `code/core/src/theming/index.ts:10`, which is not the line that defines it; the lines that define it are 16.

**Remediation:** Set the provenance `source_line` of `keyframes` in `code/core/src/theming/index.ts` to its definition line (16) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-082: Provenance line is not the definition of spyOn

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/test/spy.ts:1
**Export:** spyOn

**Issue:** the provenance map records `spyOn` at `code/core/src/test/spy.ts:1`, which is not the line that defines it; the lines that define it are 41.

**Remediation:** Set the provenance `source_line` of `spyOn` in `code/core/src/test/spy.ts` to its definition line (41) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-083: Provenance line is not the definition of start

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** start

**Issue:** the provenance map records `start` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 41.

**Remediation:** Set the provenance `source_line` of `start` in `code/builders/builder-vite/src/index.ts` to its definition line (41) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-084: Provenance line is not the definition of storeOptions

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/vitest/src/constants.ts:1
**Export:** storeOptions

**Issue:** the provenance map records `storeOptions` at `code/addons/vitest/src/constants.ts:1`, which is not the line that defines it; the lines that define it are 21.

**Remediation:** Set the provenance `source_line` of `storeOptions` in `code/addons/vitest/src/constants.ts` to its definition line (21) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-086: Provenance line is not the definition of useTheme

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/theming/index.ts:10
**Export:** useTheme

**Issue:** the provenance map records `useTheme` at `code/core/src/theming/index.ts:10`, which is not the line that defines it; the lines that define it are 18.

**Remediation:** Set the provenance `source_line` of `useTheme` in `code/core/src/theming/index.ts` to its definition line (18) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-096: Provenance line is not the definition of withoutVitePlugins

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** withoutVitePlugins

**Issue:** the provenance map records `withoutVitePlugins` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 14.

**Remediation:** Set the provenance `source_line` of `withoutVitePlugins` in `code/builders/builder-vite/src/index.ts` to its definition line (14) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-017: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=216, documented=572

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-019: Provenance line not verified for A11yGlobals_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:16
**Export:** A11yGlobals_exact

**Issue:** the line-check rules found no definition line for `A11yGlobals_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 16 defines `A11yGlobals_exact`; if another line does, set the provenance `source_line` to it.

### GAP-021: Provenance line not verified for A11yReport_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:5
**Export:** A11yReport_exact

**Issue:** the line-check rules found no definition line for `A11yReport_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 5 defines `A11yReport_exact`; if another line does, set the provenance `source_line` to it.

### GAP-023: Provenance line not verified for ArgTypes

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ArgTypes

**Issue:** the line-check rules found no definition line for `ArgTypes` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ArgTypes`; if another line does, set the provenance `source_line` to it.

### GAP-024: Provenance line not verified for Canvas

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Canvas

**Issue:** the line-check rules found no definition line for `Canvas` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Canvas`; if another line does, set the provenance `source_line` to it.

### GAP-025: Provenance line not verified for ColorPalette

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ColorPalette

**Issue:** the line-check rules found no definition line for `ColorPalette` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ColorPalette`; if another line does, set the provenance `source_line` to it.

### GAP-026: Provenance line not verified for ComponentEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** ComponentEntry

**Issue:** the line-check rules found no definition line for `ComponentEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 27 defines `ComponentEntry`; if another line does, set the provenance `source_line` to it.

### GAP-027: Provenance line not verified for Controls

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Controls

**Issue:** the line-check rules found no definition line for `Controls` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Controls`; if another line does, set the provenance `source_line` to it.

### GAP-029: Provenance line not verified for Description

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Description

**Issue:** the line-check rules found no definition line for `Description` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Description`; if another line does, set the provenance `source_line` to it.

### GAP-030: Provenance line not verified for DocsContainer

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContainer

**Issue:** the line-check rules found no definition line for `DocsContainer` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContainer`; if another line does, set the provenance `source_line` to it.

### GAP-031: Provenance line not verified for DocsContext

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContext

**Issue:** the line-check rules found no definition line for `DocsContext` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContext`; if another line does, set the provenance `source_line` to it.

### GAP-032: Provenance line not verified for DocsEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** DocsEntry

**Issue:** the line-check rules found no definition line for `DocsEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 34 defines `DocsEntry`; if another line does, set the provenance `source_line` to it.

### GAP-035: Provenance line not verified for GroupEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** GroupEntry

**Issue:** the line-check rules found no definition line for `GroupEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 21 defines `GroupEntry`; if another line does, set the provenance `source_line` to it.

### GAP-036: Provenance line not verified for HashEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** HashEntry

**Issue:** the line-check rules found no definition line for `HashEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 67 defines `HashEntry`; if another line does, set the provenance `source_line` to it.

### GAP-037: Provenance line not verified for IconGallery

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** IconGallery

**Issue:** the line-check rules found no definition line for `IconGallery` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `IconGallery`; if another line does, set the provenance `source_line` to it.

### GAP-038: Provenance line not verified for IndexHash

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** IndexHash

**Issue:** the line-check rules found no definition line for `IndexHash` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 80 defines `IndexHash`; if another line does, set the provenance `source_line` to it.

### GAP-039: Provenance line not verified for LeafEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** LeafEntry

**Issue:** the line-check rules found no definition line for `LeafEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 66 defines `LeafEntry`; if another line does, set the provenance `source_line` to it.

### GAP-041: Provenance line not verified for Markdown

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Markdown

**Issue:** the line-check rules found no definition line for `Markdown` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Markdown`; if another line does, set the provenance `source_line` to it.

### GAP-043: Provenance line not verified for Primary

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Primary

**Issue:** the line-check rules found no definition line for `Primary` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Primary`; if another line does, set the provenance `source_line` to it.

### GAP-048: Provenance line not verified for RootEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** RootEntry

**Issue:** the line-check rules found no definition line for `RootEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 15 defines `RootEntry`; if another line does, set the provenance `source_line` to it.

### GAP-049: Provenance line not verified for Source

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Source

**Issue:** the line-check rules found no definition line for `Source` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Source`; if another line does, set the provenance `source_line` to it.

### GAP-050: Provenance line not verified for Stories

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Stories

**Issue:** the line-check rules found no definition line for `Stories` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Stories`; if another line does, set the provenance `source_line` to it.

### GAP-051: Provenance line not verified for Story

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Story

**Issue:** the line-check rules found no definition line for `Story` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Story`; if another line does, set the provenance `source_line` to it.

### GAP-053: Provenance line not verified for StoryEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** StoryEntry

**Issue:** the line-check rules found no definition line for `StoryEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 45 defines `StoryEntry`; if another line does, set the provenance `source_line` to it.

### GAP-057: Provenance line not verified for Subtitle

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Subtitle

**Issue:** the line-check rules found no definition line for `Subtitle` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Subtitle`; if another line does, set the provenance `source_line` to it.

### GAP-061: Provenance line not verified for ThemesGlobals_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/types.ts:20
**Export:** ThemesGlobals_def

**Issue:** the line-check rules found no definition line for `ThemesGlobals_def` in `code/addons/themes/src/types.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/types.ts` and confirm that line 20 defines `ThemesGlobals_def`; if another line does, set the provenance `source_line` to it.

### GAP-062: Provenance line not verified for Title

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Title

**Issue:** the line-check rules found no definition line for `Title` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Title`; if another line does, set the provenance `source_line` to it.

### GAP-063: Provenance line not verified for Typeset

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Typeset

**Issue:** the line-check rules found no definition line for `Typeset` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Typeset`; if another line does, set the provenance `source_line` to it.

### GAP-064: Provenance line not verified for Unstyled

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Unstyled

**Issue:** the line-check rules found no definition line for `Unstyled` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Unstyled`; if another line does, set the provenance `source_line` to it.

### GAP-068: Provenance line not verified for a11y_decorators

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:12
**Export:** a11y_decorators

**Issue:** the line-check rules found no definition line for `a11y_decorators` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 12 defines `a11y_decorators`; if another line does, set the provenance `source_line` to it.

### GAP-069: Provenance line not verified for a11y_initialGlobals

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:98
**Export:** a11y_initialGlobals

**Issue:** the line-check rules found no definition line for `a11y_initialGlobals` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 98 defines `a11y_initialGlobals`; if another line does, set the provenance `source_line` to it.

### GAP-070: Provenance line not verified for a11y_parameters

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:105
**Export:** a11y_parameters

**Issue:** the line-check rules found no definition line for `a11y_parameters` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 105 defines `a11y_parameters`; if another line does, set the provenance `source_line` to it.

### GAP-076: Provenance line not verified for definePreview

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/preview-api/index.ts:1
**Export:** definePreview

**Issue:** the line-check rules found no definition line for `definePreview` in `code/core/src/preview-api/index.ts`; check by hand

**Remediation:** Open `code/core/src/preview-api/index.ts` and confirm that line 1 defines `definePreview`; if another line does, set the provenance `source_line` to it.

### GAP-077: Provenance line not verified for fireEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:43
**Export:** fireEvent

**Issue:** the line-check rules found no definition line for `fireEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 43 defines `fireEvent`; if another line does, set the provenance `source_line` to it.

### GAP-080: Provenance line not verified for mockChannel_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:3
**Export:** mockChannel_def

**Issue:** the line-check rules found no definition line for `mockChannel_def` in `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts`; check by hand

**Remediation:** Open `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts` and confirm that line 3 defines `mockChannel_def`; if another line does, set the provenance `source_line` to it.

### GAP-081: Provenance line not verified for screen

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:107
**Export:** screen

**Issue:** the line-check rules found no definition line for `screen` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 107 defines `screen`; if another line does, set the provenance `source_line` to it.

### GAP-085: Provenance line not verified for useOf

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** useOf

**Issue:** the line-check rules found no definition line for `useOf` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `useOf`; if another line does, set the provenance `source_line` to it.

### GAP-087: Provenance line not verified for userEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:123
**Export:** userEvent

**Issue:** the line-check rules found no definition line for `userEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 123 defines `userEvent`; if another line does, set the provenance `source_line` to it.

### GAP-088: Provenance line not verified for waitFor

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:108
**Export:** waitFor

**Issue:** the line-check rules found no definition line for `waitFor` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 108 defines `waitFor`; if another line does, set the provenance `source_line` to it.

### GAP-089: Provenance line not verified for withThemeByClassName

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByClassName

**Issue:** the line-check rules found no definition line for `withThemeByClassName` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByClassName`; if another line does, set the provenance `source_line` to it.

### GAP-090: Provenance line not verified for withThemeByClassName_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/class-name.decorator.tsx:19
**Export:** withThemeByClassName_exact

**Issue:** the line-check rules found no definition line for `withThemeByClassName_exact` in `code/addons/themes/src/decorators/class-name.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/class-name.decorator.tsx` and confirm that line 19 defines `withThemeByClassName_exact`; if another line does, set the provenance `source_line` to it.

### GAP-091: Provenance line not verified for withThemeByDataAttribute

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByDataAttribute

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByDataAttribute`; if another line does, set the provenance `source_line` to it.

### GAP-092: Provenance line not verified for withThemeByDataAttribute_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/data-attribute.decorator.tsx:19
**Export:** withThemeByDataAttribute_exact

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute_exact` in `code/addons/themes/src/decorators/data-attribute.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/data-attribute.decorator.tsx` and confirm that line 19 defines `withThemeByDataAttribute_exact`; if another line does, set the provenance `source_line` to it.

### GAP-093: Provenance line not verified for withThemeFromJSXProvider

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeFromJSXProvider

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeFromJSXProvider`; if another line does, set the provenance `source_line` to it.

### GAP-094: Provenance line not verified for withThemeFromJSXProvider_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:23
**Export:** withThemeFromJSXProvider_exact

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider_exact` in `code/addons/themes/src/decorators/provider.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/provider.decorator.tsx` and confirm that line 23 defines `withThemeFromJSXProvider_exact`; if another line does, set the provenance `source_line` to it.

### GAP-095: Provenance line not verified for within

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:110
**Export:** within

**Issue:** the line-check rules found no definition line for `within` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 110 defines `within`; if another line does, set the provenance `source_line` to it.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
