---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261103T073923Z-970f8905'
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
testDate: '2026-11-03T07:39:23Z'
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

**Mode Rationale:** metadata.json sets `skill_type: 'single'`, an individual skill, so naive mode applies: API-surface coverage, with a structural-only coherence check and no coherence category in scoring.

**Analysis Plan:**
- Coverage Check: the documented exports of SKILL.md and references/ against the public API surface the pinned source (e486d38) exports, under the stratified scope the extraction rules declare, with Deep-tier AST signature verification and type coverage.
- Coherence Check: structural only (naive mode): references named in SKILL.md resolve, and the metadata agrees with the package.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces
**Denominator:** Stratified scope, denominator: effective_denominator (280 exports; 1274 files matched by scope.include, 985 exports scope.include union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: 280  ← chosen on the scalar branch
- `scope.tier_a_include` union: 280
- `scope.include` union: 985
- exports-map subpath union: 1281
- root barrel: 54                               (secondary candidate: root-barrel-vs-subpath-union audit)

**Files Analyzed:** 319

### Export Coverage

No per-export table: the scalar denominator (`stats.effective_denominator`) counts the exports without naming them. The summary below gives the counts.

### Coverage Summary

- **Exports Found:** 280
- **Documented:** 451 (100%)
- **Missing Documentation:** 0 (a floored residual: the numerator exceeds the denominator)
- **Signature Mismatches:** 24
- **Stale Documentation:** N/A: the scalar denominator (`stats.effective_denominator`) counts the exports without naming them
- **Numerator Surplus:** 171, uncapped coverage 161.07%
- **Scoped Out by the Brief:** `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx), `AngularMeta` (code/frameworks/angular/src/client/preview.ts), `AngularOptions` (code/frameworks/angular/src/types.ts), `AngularPreview` (code/frameworks/angular/src/client/preview.ts), `AngularRenderer` (code/frameworks/angular/src/client/types.ts), `AngularStory` (code/frameworks/angular/src/client/preview.ts), `BabelFileClass` (code/core/src/babel/index.ts), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts), `Bar` (code/core/src/components/components/Bar/Bar.tsx), `BaseLocationProvider` (code/core/src/router/router.tsx), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx), `BuildIndexOptions` (code/core/src/core-server/build-index.ts), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts), `CacheEntry` (code/core/src/telemetry/event-cache.ts), `Channel` (code/core/src/channels/main.ts), `ChannelHandler` (code/core/src/channels/types.ts), `ChannelTransport` (code/core/src/channels/types.ts), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts), `CsfFile` (code/core/src/csf-tools/CsfFile.ts), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts), `DL` (code/core/src/components/components/typography/elements/DL.tsx), `Dependency` (code/core/src/telemetry/types.ts), `Div` (code/core/src/components/components/typography/elements/Div.tsx), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts), `ErrorCollector` (code/core/src/telemetry/error-collector.ts), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx), `EventType` (code/core/src/telemetry/types.ts), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts), `H1` (code/core/src/components/components/typography/elements/H1.tsx), `H2` (code/core/src/components/components/typography/elements/H2.tsx), `H3` (code/core/src/components/components/typography/elements/H3.tsx), `H4` (code/core/src/components/components/typography/elements/H4.tsx), `H5` (code/core/src/components/components/typography/elements/H5.tsx), `H6` (code/core/src/components/components/typography/elements/H6.tsx), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts), `HR` (code/core/src/components/components/typography/elements/HR.tsx), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts), `IStory` (code/frameworks/angular/src/client/types.ts), `InitPayload` (code/core/src/telemetry/types.ts), `LI` (code/core/src/components/components/typography/elements/LI.tsx), `LinkProps` (code/core/src/router/types.ts), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx), `Location` (code/core/src/router/router.tsx), `LocationProvider` (code/core/src/router/router.tsx), `LogLevel` (code/core/src/node-logger/logger/logger.ts), `MemoryRouter` (code/core/src/router/router.tsx), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts), `NavigateFunction` (code/core/src/router/types.ts), `NavigateOptions` (code/core/src/router/types.ts), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts), `OL` (code/core/src/components/components/typography/elements/OL.tsx), `Other` (code/core/src/router/types.ts), `P` (code/core/src/components/components/typography/elements/P.tsx), `Payload` (code/core/src/telemetry/types.ts), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx), `Popover` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts), `PreactRenderer` (code/renderers/preact/src/types.ts), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx), `RenderData` (code/core/src/router/types.ts), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx), `Route` (code/core/src/router/router.tsx), `RouterData` (code/core/src/router/types.ts), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx), `Separator` (code/core/src/components/components/Bar/Separator.tsx), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx), `Span` (code/core/src/components/components/typography/elements/Span.tsx), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts), `StaticStory` (code/core/src/csf-tools/CsfFile.ts), `StoryData` (code/core/src/router/utils.ts), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts), `StoryTest` (code/core/src/csf-tools/CsfFile.ts), `StorybookAddon` (code/core/src/telemetry/types.ts), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx), `StorybookMetadata` (code/core/src/telemetry/types.ts), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts), `SvelteRenderer` (code/renderers/svelte/src/types.ts), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `TT` (code/core/src/components/components/typography/elements/TT.tsx), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx), `TabButton` (code/core/src/components/components/Tabs/Button.tsx), `TabList` (code/core/src/components/components/Tabs/TabList.tsx), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `TelemetryData` (code/core/src/telemetry/types.ts), `TelemetryEvent` (code/core/src/telemetry/types.ts), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts), `UL` (code/core/src/components/components/typography/elements/UL.tsx), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts), `WebComponentsStory` (code/renderers/web-components/src/preview.ts), `WebComponentsTypes` (code/renderers/web-components/src/types.ts), `WebsocketTransport` (code/core/src/channels/websocket/index.ts), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts), `babelParseExpression` (code/core/src/babel/babelParse.ts), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts), `babelPrint` (code/core/src/babel/babelParse.ts), `buildArgsParam` (code/core/src/router/utils.ts), `buildDevStandalone` (code/core/src/core-server/build-dev.ts), `buildIndexStandalone` (code/core/src/core-server/build-index.ts), `buildStaticStandalone` (code/core/src/core-server/build-static.ts), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts), `cleanPaths` (code/core/src/telemetry/sanitize.ts), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx), `colors` (code/core/src/node-logger/index.ts), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts), `components` (code/core/src/components/index.ts), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `createBrowserChannel` (code/core/src/channels/index.ts), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts), `experimental_loadStorybook` (code/core/src/core-server/load.ts), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts), `extractSource` (code/core/src/csf-tools/enrichCsf.ts), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts), `formatCsf` (code/core/src/csf-tools/CsfFile.ts), `framework` (code/core/src/core-server/presets/common-override-preset.ts), `generate` (code/core/src/babel/index.ts), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts), `getCustomElements` (code/renderers/web-components/src/framework-api.ts), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts), `getLastEvents` (code/core/src/telemetry/event-cache.ts), `getMatch` (code/core/src/router/utils.ts), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts), `getServerPort` (code/core/src/core-server/utils/server-address.ts), `getSessionId` (code/core/src/telemetry/session-id.ts), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts), `hrefTo` (code/addons/links/src/utils.ts), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts), `isExampleStoryId` (code/core/src/telemetry/index.ts), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts), `isValidComponent` (code/renderers/web-components/src/framework-api.ts), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts), `linkTo` (code/addons/links/src/utils.ts), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts), `loadCsf` (code/core/src/csf-tools/CsfFile.ts), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx), `navigate` (code/addons/links/src/utils.ts), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts), `parsePath` (code/core/src/router/utils.ts), `parserOptions` (code/core/src/babel/babelParse.ts), `printConfig` (code/core/src/csf-tools/ConfigFile.ts), `printCsf` (code/core/src/csf-tools/CsfFile.ts), `prompt` (code/core/src/node-logger/prompts/index.ts), `protectUrls` (code/core/src/node-logger/wrap-utils.ts), `queryFromLocation` (code/core/src/router/utils.ts), `readConfig` (code/core/src/csf-tools/ConfigFile.ts), `readCsf` (code/core/src/csf-tools/CsfFile.ts), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts), `resetComponents` (code/core/src/components/index.ts), `resolveExpression` (code/core/src/babel/expression-resolver.ts), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts), `sanitizeError` (code/core/src/telemetry/sanitize.ts), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts), `setCustomElements` (code/renderers/web-components/src/framework-api.ts), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts), `stories` (code/core/src/core-server/presets/common-override-preset.ts), `stringifyQuery` (code/core/src/router/utils.ts), `telemetry` (code/core/src/telemetry/index.ts), `traverse` (code/core/src/babel/index.ts), `typescript` (code/core/src/core-server/presets/common-override-preset.ts), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts), `useNavigate` (code/core/src/router/router.tsx), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `withLinks` (code/addons/links/src/utils.ts), `withReset` (code/core/src/components/components/typography/lib/common.tsx), `withTelemetry` (code/core/src/core-server/withTelemetry.ts), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts), `writeCsf` (code/core/src/csf-tools/CsfFile.ts)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 72.41% |
| Type Coverage | 73.33% |

### Coverage Notes

- Deep tier: `gh api repos/storybookjs/storybook/git/ref/tags/v10.3.5` resolves to commit `e486d3826bcd40c52db1c766966d1c8ec16df6cb`, the `metadata.source_commit`; the workspace HEAD is that commit (init §5b, `workspace_drift_check: ok (e486d38)`), and `code/package.json` declares version 10.3.5.
- Inventory (§1): SKILL.md's `## Full*` headings are stubs, so every `references/*.md` file was read. The size of the six reference files forced a split into four parallel subagents: (1) SKILL.md, with the split-body cross-check against all six reference files; (2) `references/core-api.md`; (3) `references/framework-config.md` + `references/csf3-patterns.md`; (4) `references/story-types.md` + `references/doc-blocks.md` + `references/addons.md`. Each wrote its JSON to `inventory-part-<n>.json`; the four objects were merged unchanged (exports concatenated in part order, `references` unioned, `cross_check_mismatches` concatenated) into `inventory-response.txt`: 569 entries, 451 distinct names, 469 name+kind items. `validate-inventory.py`: valid; spot-check sampled `A`, `StoryFn`, `withoutVitePlugins`, none absent.
- Split-body cross-check (§1b): 2 mismatches, each a High `split-body-mismatch` gap at the reference line: `fn` (SKILL.md:135 `fn<T>(implementation?: T): Mock<T>` vs `references/core-api.md:53` `fn<T>(impl?: T): Mock<T>`, a parameter name) and `withThemeByDataAttribute` (SKILL.md:111 presents it "for CSS-in-JS providers"; `references/addons.md:110` says it toggles a `data-*` attribute, and gives the CSS-in-JS provider role to `withThemeFromJSXProvider` at line 112).
- Extraction (§2): `skf-extract-public-api.py --mode full --head-cap 0` status `ok`, 1274 files in scope, not truncated, no fallback, entry points `barrel`, `curatedSubset` true. `extraction.readByEye` lists 5 files with an ast-grep syntax error (`code/core/src/csf/csf-factories.ts`, `code/core/src/instrumenter/typings.d.ts`, `code/core/src/mocking-utils/esmWalker.ts`, `code/core/src/test/spy.ts`, `code/core/src/typings.d.ts`); the status is `ok`, not `incomplete`, so none was read by eye. `extractionGaps[]` names 7 exports with no file or line (`BabelFile`, `GeneratorOptions`, `NodePath`, `analyzeMdx`, `babelParse`, `instance`, `transformSync`), none in the `tier_a_include` set.
- Denominator (§2b): `surface.json` `denominator` = clause `stratified-scope`, branch `scalar`, `surfaceSet` `tier_a_include`, `ladderStep` 1, `absentSet` null, `rebuild` null, entry points `barrel`. The stored `stats.effective_denominator` (280) is taken at ladder step 1 because `guards.deflation.fires` is false (re-derived 985 vs 280, but the brief's `scope.tier_a_include` globs count public names); the extractor's own count agrees (280, basis `tier_a_include`). The scalar branch counts the 451 documented names against it (surplus 171, uncapped 161.07%, capped at 100%) and names no export, so no `missing-export` gap is recorded. Intersected with the inventory, the named `tier_a_include` set (280 names) holds 204 documented names and 76 undocumented ones: `AddContext`, `AnchorMdx`, `AnchorProps`, `CLEAR_ID`, `CYCLIC_KEY`, `CodeOrSourceMdx`, `ColorProps`, `Component`, `DEFAULT_VIEWPORT`, `DecoratorFunction`, `DescriptionType`, `DocsContainerProps`, `DocsProps`, `DocsStoryProps`, `EVENT_ID`, `Easing`, `ExternalDocs`, `ExternalDocsContainer`, `ExternalDocsProps`, `GlobalStateUpdate`, `HeaderMdx`, `HeadersMdx`, `HeadingProps`, `HighlightTypes`, `INITIAL_VIEWPORTS`, `MINIMAL_VIEWPORTS`, `Of`, `PANEL_ID`, `PRIMARY_STORY`, `PropDescriptor`, `ReactTypes`, `Report`, `ReporterAPI`, `SelectionStore`, `SourceContainer`, `SourceContext`, `SourceContextProps`, `SourceItem`, `SourceParameters`, `SourceProps`, `StoryProps`, `StorySources`, `TOOL_ID`, `UNKNOWN_ARGS_HASH`, `UserEvent`, `UserEventObject`, `View`, `Viewport`, `ViewportGlobals`, `ViewportMap`, `ViewportTypes`, `Wrapper`, `actions`, `anchorBlockIdFromId`, `argsHash`, `assertIsFn`, `background`, `color`, `config`, `createPlaywrightTest`, `emitTransformCode`, `ensure`, `extractTitle`, `getCsfFactoryAnnotations`, `getStoryId`, `getStoryProps`, `pauseAnimations`, `responsiveViewport`, `simulateDOMContentLoaded`, `simulatePageLoad`, `slugs`, `tokens`, `typography`, `uninstrumentedUserEvent`, `useSourceProps`, `waitForAnimations` (72.86% had the barrel branch counted it). The intersection is in `tier-a-intersection.json`.
- Guards (§4): `guards.deflation` applicable, does not fire; `guards.inflation` not applicable; `guards.staleScope` applicable, does not fire (no unmatched `scope.include` or `tier_a_include` glob, nothing restored). Umbrella: 12 root entries, 54 names. No guard gap.
- Signatures (§2, §2b): `score-signatures.py plan` listed 87 comparisons over 61 source files. One subagent per file (61) was batched into four subagents by plan order, balanced by check count: files 1-21 (22 checks), 22-36 (24), 37-51 (22), 52-61 (19); each wrote one response per source file (`signatures-1.txt` … `signatures-61.txt`, all parse). `score --surface-set tier_a_include`: 63 of 87 match, 24 mismatches, each a Critical `signature-mismatch` gap: 13 doc-block components whose documented prop summary leaves out optional props (`Anchor`, `Canvas`, `DocsContainer`, `DocsStory`, `Heading`, `Markdown`, `Meta`, `Source`, `Subheading`, `Subtitle`, `Title`, `Unstyled`, `PureArgsTable`), 8 controls documented as returning `JSX.Element` where the source declares `FC<…>`, whose call signature returns `ReactNode` (`BooleanControl`, `DateControl`, `FilesControl`, `NumberControl`, `ObjectControl`, `RangeControl`, `TextControl`, `OptionsControl`), `composeStories` (compared with core's `code/core/src/preview-api/modules/store/csf/portable-stories.ts:274`), `filterArgTypes` (return type) and `spyOn` (the getter/setter overloads' `accessType`, parameter name `methodName`). The plan compares each multiply-defined name with its first surface record by path: `composeStories`, `composeStory` and `setProjectAnnotations` were planned against core's declarations, `definePreview` and `defineMain` against `code/frameworks/angular/src/...`.
- Type Coverage: 88 of the 120 `tier_a_include` types documented; 32 undocumented (`missingTypes`); the scalar branch records no `missing-type` gap for them.
- Stale names (§2c): not applicable on the scalar branch (`staleApplicable` false), so `classify-stale` did not run and no `fabricated-signature`, `observation` or `stale-documentation` gap is recorded.
- Numerator ground truth (§2b): `skipped` (`stats.exports_documented` 223 differs from `stats.effective_denominator` 280, so the inflation signature is absent).
- Metadata count coherence (§4b): 1 Medium `metadata-drift` finding (`stats.exports_public_api`=1335 vs `exports[].length`=83, 94% drift) and 1 Info `multi-denominator` finding (barrel 1335 vs documented 223).
- Provenance line check (§4c): 45 stale map entries; 44 are `line-not-definition` with no definition line, each an Info `provenance-unverified` gap. The 1 `file-missing` item (`setProjectAnnotations`, entry 13, cites `code/renderers/react/src/portable-stories.ts:1`; the file is `.tsx`), the 3 `missing` (`Args`, `DocsPage`, `Parameters`) and the 143 `orphaned` findings are outside this section.
- `surface.json` warnings: 39 public entry points outside `scope.include` (addon-links, `storybook/internal/{babel,channels,components,core-server,csf-tools,node-logger,router,telemetry}`, the angular, preact, svelte and web-components packages), which `effective_denominator` leaves out by design (brief note 3 and the GAP-005 exclusions).
- Environment: midway through §2 the `/tmp` tmpfs ran out of inodes (another session's files), so the shell could not start its output capture; the remaining helper commands ran unchanged through a monitor with `TMPDIR` set to the run folder's `tmp/`. No helper input or output changed.


## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| — | — | — | No structural finding across §§2.1–2.7 | — |

**Structural Issues:** 0

Checks with no finding: §2.1 `description` (matched `Overview`, line 20), `usage` (matched `Quick Start`, line 29) and `api_surface` (matched `Key API Summary`, line 125); §2.2 fences balanced (10 fences); §2.3 no bare opening fence; §2.4 every function or method export of the inventory is referenced in a usage-family section or a reference file (`zero_usage` empty over 210 exports; split-body scope, because the `## Full*` sections are pointers to `references/`); §2.5 no export is described as async or sync against its examples (`fn`, `expect`, `composeStories`, `setProjectAnnotations`, `withThemeByClassName`, `withThemeByDataAttribute`, `withThemeFromJSXProvider`, `definePreview`, `getByRole` and `storybookTest` are called in examples; the `async` near `fn` and `getByRole` describes the `play` function, `expect` is awaited in 3 of its 4 calls and no description calls it sync, and `getByRole`'s two awaited calls sit inside an awaited `userEvent.click(...)`); §2.6 no table drift; §2.7 no `scripts/` or `assets/` folder.

**Migration/Deprecation (§2b):** Section 4b verification skipped: `evidence-report.md` exists but has no YAML frontmatter, so it pins no `t2_future_count` (Case 4 of `migration-section-rules.md`). SKILL.md has no "Migration & Deprecation Warnings" heading.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| 1 | `references/core-api.md` | `fn` | Parameter name differs: SKILL.md shows fn<T>(implementation?: T): Mock<T>, the reference fn<T>(impl?: T): Mock<T>. Type, order, optionality and return type agree; the source (code/core/src/test/spy.ts:L48) names it implementation, so the reference is the one that drifted. | 135 | 53 |
| 2 | `references/addons.md` | `withThemeByDataAttribute` | SKILL.md presents withThemeByDataAttribute (with withThemeFromJSXProvider) as the decorator 'for CSS-in-JS providers'; the reference says it toggles a data-* attribute (default data-theme) on the parent element, and gives the CSS-in-JS provider role (emotion / styled-components / MUI ThemeProvider) to withThemeFromJSXProvider alone (line 112). | 111 | 110 |

**Exports Cross-Checked:** 28 (the SKILL.md inventory names that a reference file also documents)
**Mismatches Found:** 2 (recorded by coverage-check §1b as High `split-body-mismatch` gaps)

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

**Result:** **FAIL**, not scored: the hard gate blocked this run on 26 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 72
**Blocking (Critical + High):** 26
**Non-blocking (Medium + Low + Info):** 46

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 24 | Read the source code and write or correct the documentation |
| High | 2 | Read the source code and write or correct the documentation |
| Medium | 1 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 45 | Optional improvements, no action required |
| **Total** | **72** | |

### GAP-001: Signature mismatch: Anchor

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Anchor.tsx:10
**Export:** Anchor

**Issue:** documented `{ storyId }`, source `({ storyId, children }: PropsWithChildren<AnchorProps>) where AnchorProps = { storyId: string }`: missing optional parameter 'children' (PropsWithChildren adds children?: ReactNode, and the declaration destructures it)

**Remediation:** Update the documented signature of `Anchor` from `{ storyId }` to `({ storyId, children }: PropsWithChildren<AnchorProps>) where AnchorProps = { storyId: string }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Anchor.tsx:10`.

### GAP-002: Signature mismatch: Canvas

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Canvas.tsx:100
**Export:** Canvas

**Issue:** documented `{ of }`, source `(props: CanvasProps) where CanvasProps = Pick<PreviewProps, 'withToolbar' | 'additionalActions' | 'className'> & { of?: ModuleExport; meta?: ModuleExports; sourceState?: 'hidden' | 'shown' | 'none'; layout?: Layout; source?: Omit<SourceProps, 'dark'>; story?: Pick<StoryProps, 'inline' | 'height' | 'autoplay' | '__forceInitialArgs' | '__primary'> } (withToolbar?: boolean, additionalActions?: ActionItem[], className?: string)`: missing optional parameters 'meta', 'sourceState', 'layout', 'source', 'story', 'withToolbar', 'additionalActions', 'className'; 'of' is optional (of?: ModuleExport) in the source

**Remediation:** Update the documented signature of `Canvas` from `{ of }` to `(props: CanvasProps) where CanvasProps = Pick<PreviewProps, 'withToolbar' | 'additionalActions' | 'className'> & { of?: ModuleExport; meta?: ModuleExports; sourceState?: 'hidden' | 'shown' | 'none'; layout?: Layout; source?: Omit<SourceProps, 'dark'>; story?: Pick<StoryProps, 'inline' | 'height' | 'autoplay' | '__forceInitialArgs' | '__primary'> } (withToolbar?: boolean, additionalActions?: ActionItem[], className?: string)`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Canvas.tsx:100`.

### GAP-003: Signature mismatch: DocsContainer

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/DocsContainer.tsx:23
**Export:** DocsContainer

**Issue:** documented `{ context, children }`, source `({ context, theme, children }: PropsWithChildren<DocsContainerProps>) where DocsContainerProps = { context: DocsContextProps<TFramework>; theme?: ThemeVars }`: missing optional parameter 'theme' (theme?: ThemeVars); 'children' is optional (PropsWithChildren) in the source

**Remediation:** Update the documented signature of `DocsContainer` from `{ context, children }` to `({ context, theme, children }: PropsWithChildren<DocsContainerProps>) where DocsContainerProps = { context: DocsContextProps<TFramework>; theme?: ThemeVars }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/DocsContainer.tsx:23`.

### GAP-004: Signature mismatch: DocsStory

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/DocsStory.tsx:42
**Export:** DocsStory

**Issue:** documented `{ of, expanded?, withToolbar? }`, source `({ of, expanded = true, withToolbar = false, __forceInitialArgs = false, __primary = false }: DocsStoryProps) where DocsStoryProps = { of: ModuleExport; expanded?: boolean; withToolbar?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }`: missing optional parameters '__forceInitialArgs' and '__primary' (internal props that DocsStoryImpl destructures)

**Remediation:** Update the documented signature of `DocsStory` from `{ of, expanded?, withToolbar? }` to `({ of, expanded = true, withToolbar = false, __forceInitialArgs = false, __primary = false }: DocsStoryProps) where DocsStoryProps = { of: ModuleExport; expanded?: boolean; withToolbar?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/DocsStory.tsx:42`.

### GAP-005: Signature mismatch: Heading

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Heading.tsx:33
**Export:** Heading

**Issue:** documented `{ children }`, source `({ children, disableAnchor, ...props }: PropsWithChildren<HeadingProps>) where HeadingProps = { disableAnchor?: boolean }`: missing optional parameter 'disableAnchor' (disableAnchor?: boolean); 'children' is optional (PropsWithChildren) in the source

**Remediation:** Update the documented signature of `Heading` from `{ children }` to `({ children, disableAnchor, ...props }: PropsWithChildren<HeadingProps>) where HeadingProps = { disableAnchor?: boolean }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Heading.tsx:33`.

### GAP-006: Signature mismatch: Markdown

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Markdown.tsx:55
**Export:** Markdown

**Issue:** documented `{ children }`, source `(props: MarkdownProps) where MarkdownProps = the props of markdown-to-jsx's default export (children plus options?, which MarkdownImpl reads as props.options and merges into the overrides, and is spread onto PureMarkdown)`: missing optional parameter 'options' (MarkdownToJSX options, read by the block via props.options), and the other mirrored markdown-to-jsx props

**Remediation:** Update the documented signature of `Markdown` from `{ children }` to `(props: MarkdownProps) where MarkdownProps = the props of markdown-to-jsx's default export (children plus options?, which MarkdownImpl reads as props.options and merges into the overrides, and is spread onto PureMarkdown)`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Markdown.tsx:55`.

### GAP-007: Signature mismatch: Meta

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Meta.tsx:15
**Export:** Meta

**Issue:** documented `{ of }`, source `({ of }: MetaProps) where MetaProps = BaseAnnotations & { of?: ModuleExports; title?: string }`: missing optional parameter 'title' (title?: string) and the BaseAnnotations props MetaProps includes; 'of' is optional (of?: ModuleExports) in the source

**Remediation:** Update the documented signature of `Meta` from `{ of }` to `({ of }: MetaProps) where MetaProps = BaseAnnotations & { of?: ModuleExports; title?: string }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Meta.tsx:15`.

### GAP-008: Signature mismatch: Source

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:181
**Export:** Source

**Issue:** documented `{ of?, code?, language?, dark?, format? }`, source `(props: SourceProps) where SourceProps = SourceParameters & { of?: ModuleExport; __forceInitialArgs?: boolean }, SourceParameters = SourceCodeProps & { type?: SourceType; transform?: (code: string, storyContext) => string | Promise<string>; originalSource?: string }, SourceCodeProps = { language?: SupportedLanguage; code?: string; format?; dark?: boolean; copyable?: boolean }`: missing optional parameters 'type', 'transform', 'copyable', 'originalSource' and '__forceInitialArgs'

**Remediation:** Update the documented signature of `Source` from `{ of?, code?, language?, dark?, format? }` to `(props: SourceProps) where SourceProps = SourceParameters & { of?: ModuleExport; __forceInitialArgs?: boolean }, SourceParameters = SourceCodeProps & { type?: SourceType; transform?: (code: string, storyContext) => string | Promise<string>; originalSource?: string }, SourceCodeProps = { language?: SupportedLanguage; code?: string; format?; dark?: boolean; copyable?: boolean }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Source.tsx:181`.

### GAP-009: Signature mismatch: Subheading

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Subheading.tsx:23
**Export:** Subheading

**Issue:** documented `{ children }`, source `({ children, disableAnchor }: PropsWithChildren<HeadingProps>) where HeadingProps = { disableAnchor?: boolean }`: missing optional parameter 'disableAnchor' (disableAnchor?: boolean); 'children' is optional (PropsWithChildren) in the source

**Remediation:** Update the documented signature of `Subheading` from `{ children }` to `({ children, disableAnchor }: PropsWithChildren<HeadingProps>) where HeadingProps = { disableAnchor?: boolean }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Subheading.tsx:23`.

### GAP-010: Signature mismatch: Subtitle

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Subtitle.tsx:55
**Export:** Subtitle

**Issue:** documented `{ children? }`, source `(props: SubtitleProps) where SubtitleProps = { children?: ReactNode; of?: Of }`: missing optional parameter 'of' (of?: Of)

**Remediation:** Update the documented signature of `Subtitle` from `{ children? }` to `(props: SubtitleProps) where SubtitleProps = { children?: ReactNode; of?: Of }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Subtitle.tsx:55`.

### GAP-011: Signature mismatch: Title

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Title.tsx:55
**Export:** Title

**Issue:** documented `{ children? }`, source `(props: TitleProps) where TitleProps = { of?: Of; children?: ReactNode }`: missing optional parameter 'of' (of?: Of)

**Remediation:** Update the documented signature of `Title` from `{ children? }` to `(props: TitleProps) where TitleProps = { of?: Of; children?: ReactNode }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Title.tsx:55`.

### GAP-012: Signature mismatch: Unstyled

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Unstyled.tsx:9
**Export:** Unstyled

**Issue:** documented `{ children }`, source `(props: React.DetailedHTMLProps<React.HTMLAttributes<HTMLDivElement>, HTMLDivElement>)`: missing the optional HTML div attribute props (id, style, ref, event handlers, etc.) that the props type accepts and the block spreads onto its <div>; 'children' is optional in the source

**Remediation:** Update the documented signature of `Unstyled` from `{ children }` to `(props: React.DetailedHTMLProps<React.HTMLAttributes<HTMLDivElement>, HTMLDivElement>)`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Unstyled.tsx:9`.

### GAP-013: Signature mismatch: PureArgsTable

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320
**Export:** PureArgsTable

**Issue:** documented `rows (accepted directly)`, source `(props: ArgsTableProps) where ArgsTableProps = ArgsTableOptionProps & (ArgsTableDataProps | ArgsTableErrorProps | ArgsTableLoadingProps); ArgsTableOptionProps = { children?; updateArgs?: (args: Args) => void; resetArgs?: (argNames?: string[]) => void; compact?; inAddonPanel?; inTabPanel?; initialExpandedArgs?; isLoading?; sort?: SortType }; ArgsTableDataProps = { rows: ArgTypes; args?: Args; globals?: Globals }; ArgsTableErrorProps = { error: ArgsTableError }; ArgsTableLoadingProps = { isLoading: boolean }`: missing optional parameters 'args', 'globals', 'updateArgs', 'resetArgs', 'sort', 'compact', 'inAddonPanel', 'inTabPanel', 'initialExpandedArgs', 'isLoading', 'children'; omits the union alternatives where 'rows' is absent ({ error } and { isLoading: true })

**Remediation:** Update the documented signature of `PureArgsTable` from `rows (accepted directly)` to `(props: ArgsTableProps) where ArgsTableProps = ArgsTableOptionProps & (ArgsTableDataProps | ArgsTableErrorProps | ArgsTableLoadingProps); ArgsTableOptionProps = { children?; updateArgs?: (args: Args) => void; resetArgs?: (argNames?: string[]) => void; compact?; inAddonPanel?; inTabPanel?; initialExpandedArgs?; isLoading?; sort?: SortType }; ArgsTableDataProps = { rows: ArgTypes; args?: Args; globals?: Globals }; ArgsTableErrorProps = { error: ArgsTableError }; ArgsTableLoadingProps = { isLoading: boolean }`, the signature the source defines at `code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320`.

### GAP-014: Signature mismatch: BooleanControl

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/controls/Boolean.tsx:117
**Export:** BooleanControl

**Issue:** documented `(props: BooleanProps) => JSX.Element`, source `FC<BooleanProps> i.e. (props: BooleanProps) => ReactNode`: return type differs: declared as FC<BooleanProps>, whose call signature returns ReactNode (@types/react 18.3.27, TS 5.9), not JSX.Element

**Remediation:** Update the documented signature of `BooleanControl` from `(props: BooleanProps) => JSX.Element` to `FC<BooleanProps> i.e. (props: BooleanProps) => ReactNode`, the signature the source defines at `code/addons/docs/src/blocks/controls/Boolean.tsx:117`.

### GAP-015: Signature mismatch: DateControl

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/controls/Date.tsx:69
**Export:** DateControl

**Issue:** documented `(props: DateProps) => JSX.Element`, source `FC<DateProps> i.e. (props: DateProps) => ReactNode`: return type differs: declared as FC<DateProps>, whose call signature returns ReactNode (@types/react 18.3.27, TS 5.9), not JSX.Element

**Remediation:** Update the documented signature of `DateControl` from `(props: DateProps) => JSX.Element` to `FC<DateProps> i.e. (props: DateProps) => ReactNode`, the signature the source defines at `code/addons/docs/src/blocks/controls/Date.tsx:69`.

### GAP-016: Signature mismatch: FilesControl

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/controls/Files.tsx:40
**Export:** FilesControl

**Issue:** documented `(props: FilesControlProps) => JSX.Element`, source `FC<FilesControlProps> i.e. (props: FilesControlProps) => ReactNode`: return type differs: declared as FC<FilesControlProps>, whose call signature returns ReactNode (@types/react 18.3.27, TS 5.9), not JSX.Element

**Remediation:** Update the documented signature of `FilesControl` from `(props: FilesControlProps) => JSX.Element` to `FC<FilesControlProps> i.e. (props: FilesControlProps) => ReactNode`, the signature the source defines at `code/addons/docs/src/blocks/controls/Files.tsx:40`.

### GAP-017: Signature mismatch: NumberControl

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/controls/Number.tsx:28
**Export:** NumberControl

**Issue:** documented `(props: NumberProps) => JSX.Element`, source `FC<NumberProps> i.e. (props: NumberProps) => ReactNode`: return type differs: declared as FC<NumberProps>, whose call signature returns ReactNode (@types/react 18.3.27, TS 5.9), not JSX.Element

**Remediation:** Update the documented signature of `NumberControl` from `(props: NumberProps) => JSX.Element` to `FC<NumberProps> i.e. (props: NumberProps) => ReactNode`, the signature the source defines at `code/addons/docs/src/blocks/controls/Number.tsx:28`.

### GAP-018: Signature mismatch: ObjectControl

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/controls/Object.tsx:166
**Export:** ObjectControl

**Issue:** documented `(props: ObjectProps) => JSX.Element`, source `FC<ObjectProps> i.e. (props: ObjectProps) => ReactNode`: return type differs: declared as FC<ObjectProps>, whose call signature returns ReactNode (@types/react 18.3.27, TS 5.9), not JSX.Element

**Remediation:** Update the documented signature of `ObjectControl` from `(props: ObjectProps) => JSX.Element` to `FC<ObjectProps> i.e. (props: ObjectProps) => ReactNode`, the signature the source defines at `code/addons/docs/src/blocks/controls/Object.tsx:166`.

### GAP-019: Signature mismatch: RangeControl

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/controls/Range.tsx:178
**Export:** RangeControl

**Issue:** documented `(props: RangeProps) => JSX.Element`, source `FC<RangeProps> i.e. (props: RangeProps) => ReactNode`: return type differs: declared as FC<RangeProps>, whose call signature returns ReactNode (@types/react 18.3.27, TS 5.9), not JSX.Element

**Remediation:** Update the documented signature of `RangeControl` from `(props: RangeProps) => JSX.Element` to `FC<RangeProps> i.e. (props: RangeProps) => ReactNode`, the signature the source defines at `code/addons/docs/src/blocks/controls/Range.tsx:178`.

### GAP-020: Signature mismatch: TextControl

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/controls/Text.tsx:23
**Export:** TextControl

**Issue:** documented `(props: TextProps) => JSX.Element`, source `FC<TextProps> i.e. (props: TextProps) => ReactNode`: return type differs: declared as FC<TextProps>, whose call signature returns ReactNode (@types/react 18.3.27, TS 5.9), not JSX.Element

**Remediation:** Update the documented signature of `TextControl` from `(props: TextProps) => JSX.Element` to `FC<TextProps> i.e. (props: TextProps) => ReactNode`, the signature the source defines at `code/addons/docs/src/blocks/controls/Text.tsx:23`.

### GAP-021: Signature mismatch: OptionsControl

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/controls/options/Options.tsx:41
**Export:** OptionsControl

**Issue:** documented `(props: OptionsProps) => JSX.Element`, source `FC<OptionsProps> i.e. (props: OptionsProps) => ReactNode`: return type differs: declared as FC<OptionsProps>, whose call signature returns ReactNode (@types/react 18.3.27, TS 5.9), not JSX.Element

**Remediation:** Update the documented signature of `OptionsControl` from `(props: OptionsProps) => JSX.Element` to `FC<OptionsProps> i.e. (props: OptionsProps) => ReactNode`, the signature the source defines at `code/addons/docs/src/blocks/controls/options/Options.tsx:41`.

### GAP-022: Signature mismatch: composeStories

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:274
**Export:** composeStories

**Issue:** documented `csfExports, projectAnnotations?`, source `<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory)`: second parameter is required in source (globalConfig: ProjectAnnotations<Renderer>) but documented as optional projectAnnotations?; missing optional third parameter composeStoryFn; parameter names differ (storiesImport vs csfExports, globalConfig vs projectAnnotations)

**Remediation:** Update the documented signature of `composeStories` from `csfExports, projectAnnotations?` to `<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory)`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:274`.

### GAP-023: Signature mismatch: filterArgTypes

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/filterArgTypes.ts:10
**Export:** filterArgTypes

**Issue:** documented `(argTypes: StrictArgTypes, include?: PropDescriptor, exclude?: PropDescriptor) => StrictArgTypes`, source `(argTypes: StrictArgTypes, include?: PropDescriptor, exclude?: PropDescriptor) => StrictArgTypes | Partial<StrictArgTypes>`: return type is not annotated in source; the filtering branch returns es-toolkit pickBy(argTypes, ...), which is typed Partial<T>, so the inferred return is StrictArgTypes | Partial<StrictArgTypes> (values may be undefined), not StrictArgTypes

**Remediation:** Update the documented signature of `filterArgTypes` from `(argTypes: StrictArgTypes, include?: PropDescriptor, exclude?: PropDescriptor) => StrictArgTypes` to `(argTypes: StrictArgTypes, include?: PropDescriptor, exclude?: PropDescriptor) => StrictArgTypes | Partial<StrictArgTypes>`, the signature the source defines at `code/core/src/preview-api/modules/store/filterArgTypes.ts:10`.

### GAP-024: Signature mismatch: spyOn

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/test/spy.ts:41
**Export:** spyOn

**Issue:** documented `(obj, method)`, source `typeof vitestSpyOn (@vitest/spy 3.2.4): (obj: T, methodName: S, accessType: 'get') | (obj: T, methodName: G, accessType: 'set') | (obj: T, methodName: M)`: missing the 'accessType' parameter ('get' | 'set') of the getter/setter overloads; second parameter is named 'methodName' in source, not 'method'

**Remediation:** Update the documented signature of `spyOn` from `(obj, method)` to `typeof vitestSpyOn (@vitest/spy 3.2.4): (obj: T, methodName: S, accessType: 'get') | (obj: T, methodName: G, accessType: 'set') | (obj: T, methodName: M)`, the signature the source defines at `code/core/src/test/spy.ts:41`.

### GAP-071: Split-body mismatch: fn

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/core-api.md:53
**Export:** fn

**Issue:** SKILL.md:135 documents fn<T>(implementation?: T): Mock<T>; references/core-api.md:53 documents fn<T>(impl?: T): Mock<T>. The parameter name differs (type, order, optionality and return type agree); the source code/core/src/test/spy.ts:48 names it implementation.

**Remediation:** In references/core-api.md line 53, change the signature from `fn<T>(impl?: T): Mock<T>` to `fn<T>(implementation?: T): Mock<T>` so it matches the SKILL.md body (line 135) and the source at code/core/src/test/spy.ts:48.

### GAP-072: Split-body mismatch: withThemeByDataAttribute

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/addons.md:110
**Export:** withThemeByDataAttribute

**Issue:** SKILL.md:111 presents withThemeByDataAttribute (with withThemeFromJSXProvider) as the decorator for CSS-in-JS providers; references/addons.md:110 says it toggles a data-* attribute (default data-theme) on the parent element and gives the CSS-in-JS provider role to withThemeFromJSXProvider alone (line 112).

**Remediation:** Make the SKILL.md body and references/addons.md:110 agree on the role of `withThemeByDataAttribute`: per code/addons/themes/src/decorators/data-attribute.decorator.tsx:19 it sets a `data-*` attribute (default `data-theme`) on the parent element, while `withThemeFromJSXProvider` (code/addons/themes/src/decorators/provider.decorator.tsx:23) wraps the story in a CSS-in-JS provider. SKILL.md is authoritative for update-skill, so correct SKILL.md line 111 to say `withThemeByDataAttribute` for data-attribute theming and `withThemeFromJSXProvider` for CSS-in-JS providers, and keep references/addons.md:110 consistent with it.

### GAP-025: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_public_api=1335, exports[].length=83 → 94% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json`; update-skill applies it as a metadata update.

### GAP-026: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=1335, documented=223

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-027: Provenance line not verified for A11yGlobals_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:16
**Export:** A11yGlobals_exact

**Issue:** the line-check rules found no definition line for `A11yGlobals_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 16 defines `A11yGlobals_exact`; if another line does, set the provenance `source_line` to it.

### GAP-028: Provenance line not verified for A11yReport_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:5
**Export:** A11yReport_exact

**Issue:** the line-check rules found no definition line for `A11yReport_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 5 defines `A11yReport_exact`; if another line does, set the provenance `source_line` to it.

### GAP-029: Provenance line not verified for ArgTypes

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ArgTypes

**Issue:** the line-check rules found no definition line for `ArgTypes` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ArgTypes`; if another line does, set the provenance `source_line` to it.

### GAP-030: Provenance line not verified for Canvas

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Canvas

**Issue:** the line-check rules found no definition line for `Canvas` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Canvas`; if another line does, set the provenance `source_line` to it.

### GAP-031: Provenance line not verified for ColorPalette

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ColorPalette

**Issue:** the line-check rules found no definition line for `ColorPalette` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ColorPalette`; if another line does, set the provenance `source_line` to it.

### GAP-032: Provenance line not verified for ComponentEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** ComponentEntry

**Issue:** the line-check rules found no definition line for `ComponentEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 27 defines `ComponentEntry`; if another line does, set the provenance `source_line` to it.

### GAP-033: Provenance line not verified for Controls

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Controls

**Issue:** the line-check rules found no definition line for `Controls` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Controls`; if another line does, set the provenance `source_line` to it.

### GAP-034: Provenance line not verified for Description

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Description

**Issue:** the line-check rules found no definition line for `Description` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Description`; if another line does, set the provenance `source_line` to it.

### GAP-035: Provenance line not verified for DocsContainer

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContainer

**Issue:** the line-check rules found no definition line for `DocsContainer` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContainer`; if another line does, set the provenance `source_line` to it.

### GAP-036: Provenance line not verified for DocsContext

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContext

**Issue:** the line-check rules found no definition line for `DocsContext` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContext`; if another line does, set the provenance `source_line` to it.

### GAP-037: Provenance line not verified for DocsEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** DocsEntry

**Issue:** the line-check rules found no definition line for `DocsEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 34 defines `DocsEntry`; if another line does, set the provenance `source_line` to it.

### GAP-038: Provenance line not verified for GroupEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** GroupEntry

**Issue:** the line-check rules found no definition line for `GroupEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 21 defines `GroupEntry`; if another line does, set the provenance `source_line` to it.

### GAP-039: Provenance line not verified for HashEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** HashEntry

**Issue:** the line-check rules found no definition line for `HashEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 67 defines `HashEntry`; if another line does, set the provenance `source_line` to it.

### GAP-040: Provenance line not verified for IconGallery

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** IconGallery

**Issue:** the line-check rules found no definition line for `IconGallery` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `IconGallery`; if another line does, set the provenance `source_line` to it.

### GAP-041: Provenance line not verified for IndexHash

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** IndexHash

**Issue:** the line-check rules found no definition line for `IndexHash` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 80 defines `IndexHash`; if another line does, set the provenance `source_line` to it.

### GAP-042: Provenance line not verified for LeafEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** LeafEntry

**Issue:** the line-check rules found no definition line for `LeafEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 66 defines `LeafEntry`; if another line does, set the provenance `source_line` to it.

### GAP-043: Provenance line not verified for Markdown

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Markdown

**Issue:** the line-check rules found no definition line for `Markdown` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Markdown`; if another line does, set the provenance `source_line` to it.

### GAP-044: Provenance line not verified for Primary

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Primary

**Issue:** the line-check rules found no definition line for `Primary` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Primary`; if another line does, set the provenance `source_line` to it.

### GAP-045: Provenance line not verified for RootEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** RootEntry

**Issue:** the line-check rules found no definition line for `RootEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 15 defines `RootEntry`; if another line does, set the provenance `source_line` to it.

### GAP-046: Provenance line not verified for Source

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Source

**Issue:** the line-check rules found no definition line for `Source` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Source`; if another line does, set the provenance `source_line` to it.

### GAP-047: Provenance line not verified for Stories

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Stories

**Issue:** the line-check rules found no definition line for `Stories` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Stories`; if another line does, set the provenance `source_line` to it.

### GAP-048: Provenance line not verified for Story

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Story

**Issue:** the line-check rules found no definition line for `Story` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Story`; if another line does, set the provenance `source_line` to it.

### GAP-049: Provenance line not verified for StoryEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** StoryEntry

**Issue:** the line-check rules found no definition line for `StoryEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 45 defines `StoryEntry`; if another line does, set the provenance `source_line` to it.

### GAP-050: Provenance line not verified for Subtitle

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Subtitle

**Issue:** the line-check rules found no definition line for `Subtitle` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Subtitle`; if another line does, set the provenance `source_line` to it.

### GAP-051: Provenance line not verified for ThemesGlobals_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/types.ts:20
**Export:** ThemesGlobals_def

**Issue:** the line-check rules found no definition line for `ThemesGlobals_def` in `code/addons/themes/src/types.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/types.ts` and confirm that line 20 defines `ThemesGlobals_def`; if another line does, set the provenance `source_line` to it.

### GAP-052: Provenance line not verified for Title

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Title

**Issue:** the line-check rules found no definition line for `Title` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Title`; if another line does, set the provenance `source_line` to it.

### GAP-053: Provenance line not verified for Typeset

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Typeset

**Issue:** the line-check rules found no definition line for `Typeset` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Typeset`; if another line does, set the provenance `source_line` to it.

### GAP-054: Provenance line not verified for Unstyled

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Unstyled

**Issue:** the line-check rules found no definition line for `Unstyled` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Unstyled`; if another line does, set the provenance `source_line` to it.

### GAP-055: Provenance line not verified for a11y_decorators

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:12
**Export:** a11y_decorators

**Issue:** the line-check rules found no definition line for `a11y_decorators` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 12 defines `a11y_decorators`; if another line does, set the provenance `source_line` to it.

### GAP-056: Provenance line not verified for a11y_initialGlobals

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:98
**Export:** a11y_initialGlobals

**Issue:** the line-check rules found no definition line for `a11y_initialGlobals` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 98 defines `a11y_initialGlobals`; if another line does, set the provenance `source_line` to it.

### GAP-057: Provenance line not verified for a11y_parameters

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:105
**Export:** a11y_parameters

**Issue:** the line-check rules found no definition line for `a11y_parameters` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 105 defines `a11y_parameters`; if another line does, set the provenance `source_line` to it.

### GAP-058: Provenance line not verified for fireEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:43
**Export:** fireEvent

**Issue:** the line-check rules found no definition line for `fireEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 43 defines `fireEvent`; if another line does, set the provenance `source_line` to it.

### GAP-059: Provenance line not verified for mockChannel_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:3
**Export:** mockChannel_def

**Issue:** the line-check rules found no definition line for `mockChannel_def` in `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts`; check by hand

**Remediation:** Open `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts` and confirm that line 3 defines `mockChannel_def`; if another line does, set the provenance `source_line` to it.

### GAP-060: Provenance line not verified for screen

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:107
**Export:** screen

**Issue:** the line-check rules found no definition line for `screen` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 107 defines `screen`; if another line does, set the provenance `source_line` to it.

### GAP-061: Provenance line not verified for useOf

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** useOf

**Issue:** the line-check rules found no definition line for `useOf` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `useOf`; if another line does, set the provenance `source_line` to it.

### GAP-062: Provenance line not verified for userEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:123
**Export:** userEvent

**Issue:** the line-check rules found no definition line for `userEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 123 defines `userEvent`; if another line does, set the provenance `source_line` to it.

### GAP-063: Provenance line not verified for waitFor

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:108
**Export:** waitFor

**Issue:** the line-check rules found no definition line for `waitFor` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 108 defines `waitFor`; if another line does, set the provenance `source_line` to it.

### GAP-064: Provenance line not verified for withThemeByClassName

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByClassName

**Issue:** the line-check rules found no definition line for `withThemeByClassName` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByClassName`; if another line does, set the provenance `source_line` to it.

### GAP-065: Provenance line not verified for withThemeByClassName_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/class-name.decorator.tsx:19
**Export:** withThemeByClassName_exact

**Issue:** the line-check rules found no definition line for `withThemeByClassName_exact` in `code/addons/themes/src/decorators/class-name.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/class-name.decorator.tsx` and confirm that line 19 defines `withThemeByClassName_exact`; if another line does, set the provenance `source_line` to it.

### GAP-066: Provenance line not verified for withThemeByDataAttribute

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByDataAttribute

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByDataAttribute`; if another line does, set the provenance `source_line` to it.

### GAP-067: Provenance line not verified for withThemeByDataAttribute_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/data-attribute.decorator.tsx:19
**Export:** withThemeByDataAttribute_exact

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute_exact` in `code/addons/themes/src/decorators/data-attribute.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/data-attribute.decorator.tsx` and confirm that line 19 defines `withThemeByDataAttribute_exact`; if another line does, set the provenance `source_line` to it.

### GAP-068: Provenance line not verified for withThemeFromJSXProvider

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeFromJSXProvider

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeFromJSXProvider`; if another line does, set the provenance `source_line` to it.

### GAP-069: Provenance line not verified for withThemeFromJSXProvider_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:23
**Export:** withThemeFromJSXProvider_exact

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider_exact` in `code/addons/themes/src/decorators/provider.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/provider.decorator.tsx` and confirm that line 23 defines `withThemeFromJSXProvider_exact`; if another line does, set the provenance `source_line` to it.

### GAP-070: Provenance line not verified for within

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:110
**Export:** within

**Issue:** the line-check rules found no definition line for `within` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 110 defines `within`; if another line does, set the provenance `source_line` to it.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
