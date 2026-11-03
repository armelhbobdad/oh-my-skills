---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261103T084026Z-c861c18d'
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
testDate: '2026-11-03T08:40:26Z'
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

**Mode Rationale:** metadata.json sets `skill_type: 'single'`, an individual skill, so the run takes Naive Mode (API-surface coverage; coherence is structural only and carries no scored category).

**Analysis Plan:**
- Coverage Check: Deep tier against the local source at the pinned commit e486d38: export coverage of the stratified tier A denominator, AST-backed signature accuracy (params: name, type, order, optionality; return type) and type coverage for the documented exports.
- Coherence Check: structural checks only (references resolve, SKILL.md sections and reference files agree), no coherence category in the score.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces (monorepo, 44 workspaces)
**Denominator:** Stratified scope, denominator: effective_denominator (118 files matched, 280 exports union)

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
- **Signature Mismatches:** 8
- **Stale Documentation:** N/A: the scalar denominator (`stats.effective_denominator`) counts the exports without naming them
- **Numerator Surplus:** 171, uncapped coverage 161.07%
- **Scoped Out by the Brief:** `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx), `AngularMeta` (code/frameworks/angular/src/client/preview.ts), `AngularOptions` (code/frameworks/angular/src/types.ts), `AngularPreview` (code/frameworks/angular/src/client/preview.ts), `AngularRenderer` (code/frameworks/angular/src/client/types.ts), `AngularStory` (code/frameworks/angular/src/client/preview.ts), `BabelFileClass` (code/core/src/babel/index.ts), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts), `Bar` (code/core/src/components/components/Bar/Bar.tsx), `BaseLocationProvider` (code/core/src/router/router.tsx), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx), `BuildIndexOptions` (code/core/src/core-server/build-index.ts), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts), `CacheEntry` (code/core/src/telemetry/event-cache.ts), `Channel` (code/core/src/channels/main.ts), `ChannelHandler` (code/core/src/channels/types.ts), `ChannelTransport` (code/core/src/channels/types.ts), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts), `CsfFile` (code/core/src/csf-tools/CsfFile.ts), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts), `DL` (code/core/src/components/components/typography/elements/DL.tsx), `Dependency` (code/core/src/telemetry/types.ts), `Div` (code/core/src/components/components/typography/elements/Div.tsx), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts), `ErrorCollector` (code/core/src/telemetry/error-collector.ts), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx), `EventType` (code/core/src/telemetry/types.ts), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts), `H1` (code/core/src/components/components/typography/elements/H1.tsx), `H2` (code/core/src/components/components/typography/elements/H2.tsx), `H3` (code/core/src/components/components/typography/elements/H3.tsx), `H4` (code/core/src/components/components/typography/elements/H4.tsx), `H5` (code/core/src/components/components/typography/elements/H5.tsx), `H6` (code/core/src/components/components/typography/elements/H6.tsx), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts), `HR` (code/core/src/components/components/typography/elements/HR.tsx), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts), `IStory` (code/frameworks/angular/src/client/types.ts), `InitPayload` (code/core/src/telemetry/types.ts), `LI` (code/core/src/components/components/typography/elements/LI.tsx), `LinkProps` (code/core/src/router/types.ts), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx), `Location` (code/core/src/router/router.tsx), `LocationProvider` (code/core/src/router/router.tsx), `LogLevel` (code/core/src/node-logger/logger/logger.ts), `MemoryRouter` (code/core/src/router/router.tsx), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts), `NavigateFunction` (code/core/src/router/types.ts), `NavigateOptions` (code/core/src/router/types.ts), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts), `OL` (code/core/src/components/components/typography/elements/OL.tsx), `Other` (code/core/src/router/types.ts), `P` (code/core/src/components/components/typography/elements/P.tsx), `Payload` (code/core/src/telemetry/types.ts), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx), `Popover` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts), `PreactRenderer` (code/renderers/preact/src/types.ts), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx), `RenderData` (code/core/src/router/types.ts), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx), `Route` (code/core/src/router/router.tsx), `RouterData` (code/core/src/router/types.ts), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx), `Separator` (code/core/src/components/components/Bar/Separator.tsx), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx), `Span` (code/core/src/components/components/typography/elements/Span.tsx), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts), `StaticStory` (code/core/src/csf-tools/CsfFile.ts), `StoryData` (code/core/src/router/utils.ts), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts), `StoryTest` (code/core/src/csf-tools/CsfFile.ts), `StorybookAddon` (code/core/src/telemetry/types.ts), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx), `StorybookMetadata` (code/core/src/telemetry/types.ts), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts), `SvelteRenderer` (code/renderers/svelte/src/types.ts), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `TT` (code/core/src/components/components/typography/elements/TT.tsx), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx), `TabButton` (code/core/src/components/components/Tabs/Button.tsx), `TabList` (code/core/src/components/components/Tabs/TabList.tsx), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `TelemetryData` (code/core/src/telemetry/types.ts), `TelemetryEvent` (code/core/src/telemetry/types.ts), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts), `UL` (code/core/src/components/components/typography/elements/UL.tsx), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts), `WebComponentsStory` (code/renderers/web-components/src/preview.ts), `WebComponentsTypes` (code/renderers/web-components/src/types.ts), `WebsocketTransport` (code/core/src/channels/websocket/index.ts), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts), `babelParseExpression` (code/core/src/babel/babelParse.ts), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts), `babelPrint` (code/core/src/babel/babelParse.ts), `buildArgsParam` (code/core/src/router/utils.ts), `buildDevStandalone` (code/core/src/core-server/build-dev.ts), `buildIndexStandalone` (code/core/src/core-server/build-index.ts), `buildStaticStandalone` (code/core/src/core-server/build-static.ts), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts), `cleanPaths` (code/core/src/telemetry/sanitize.ts), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx), `colors` (code/core/src/node-logger/index.ts), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts), `components` (code/core/src/components/index.ts), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `createBrowserChannel` (code/core/src/channels/index.ts), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts), `experimental_loadStorybook` (code/core/src/core-server/load.ts), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts), `extractSource` (code/core/src/csf-tools/enrichCsf.ts), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts), `formatCsf` (code/core/src/csf-tools/CsfFile.ts), `framework` (code/core/src/core-server/presets/common-override-preset.ts), `generate` (code/core/src/babel/index.ts), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts), `getCustomElements` (code/renderers/web-components/src/framework-api.ts), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts), `getLastEvents` (code/core/src/telemetry/event-cache.ts), `getMatch` (code/core/src/router/utils.ts), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts), `getServerPort` (code/core/src/core-server/utils/server-address.ts), `getSessionId` (code/core/src/telemetry/session-id.ts), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts), `hrefTo` (code/addons/links/src/utils.ts), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts), `isExampleStoryId` (code/core/src/telemetry/index.ts), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts), `isValidComponent` (code/renderers/web-components/src/framework-api.ts), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts), `linkTo` (code/addons/links/src/utils.ts), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts), `loadCsf` (code/core/src/csf-tools/CsfFile.ts), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx), `navigate` (code/addons/links/src/utils.ts), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts), `parsePath` (code/core/src/router/utils.ts), `parserOptions` (code/core/src/babel/babelParse.ts), `printConfig` (code/core/src/csf-tools/ConfigFile.ts), `printCsf` (code/core/src/csf-tools/CsfFile.ts), `prompt` (code/core/src/node-logger/prompts/index.ts), `protectUrls` (code/core/src/node-logger/wrap-utils.ts), `queryFromLocation` (code/core/src/router/utils.ts), `readConfig` (code/core/src/csf-tools/ConfigFile.ts), `readCsf` (code/core/src/csf-tools/CsfFile.ts), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts), `resetComponents` (code/core/src/components/index.ts), `resolveExpression` (code/core/src/babel/expression-resolver.ts), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts), `sanitizeError` (code/core/src/telemetry/sanitize.ts), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts), `setCustomElements` (code/renderers/web-components/src/framework-api.ts), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts), `stories` (code/core/src/core-server/presets/common-override-preset.ts), `stringifyQuery` (code/core/src/router/utils.ts), `telemetry` (code/core/src/telemetry/index.ts), `traverse` (code/core/src/babel/index.ts), `typescript` (code/core/src/core-server/presets/common-override-preset.ts), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts), `useNavigate` (code/core/src/router/router.tsx), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `withLinks` (code/addons/links/src/utils.ts), `withReset` (code/core/src/components/components/typography/lib/common.tsx), `withTelemetry` (code/core/src/core-server/withTelemetry.ts), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts), `writeCsf` (code/core/src/csf-tools/CsfFile.ts)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 90.48% |
| Type Coverage | 73.33% |

**Notes (§2 to §4b):**
- Denominator clause `stratified-scope`, branch `scalar`, surfaceSet `tier_a_include`, ladderStep 1 (`absentSet` null, no `rebuild`). Guards: deflation applicable, does not fire (re-derived 985 against 280, with tier A globs that count names); inflation not applicable; staleScope does not fire (no unmatched `scope.include` or `scope.tier_a_include` glob).
- Numerator surplus: the inventory documents 451 names against the 280 scalar, so Export Coverage is capped at 100 (uncapped 161.07%). The brief has `scope.tier_a_include` globs that match files and `guards.deflation` does not fire, so this is not the deflated-denominator signature.
- Deep tier: `gh api repos/storybookjs/storybook/commits/v10.3.5` resolves to e486d3826bcd40c52db1c766966d1c8ec16df6cb, the pinned `source_commit`, and `code/package.json` reads `"version": "10.3.5"`.
- Extraction: `status: ok`, 1274 files in scope, no fallback. The runner reports one syntax-error node in each of 5 files (`code/core/src/csf/csf-factories.ts`, `code/core/src/instrumenter/typings.d.ts`, `code/core/src/mocking-utils/esmWalker.ts`, `code/core/src/test/spy.ts`, `code/core/src/typings.d.ts`) and lists them as `readByEye`, but with a complete extraction §2 does not re-read them; all 7 `spy.ts` exports (`fn`, `spyOn`, `mocked`, `onMockCall`, `clearAllMocks`, `resetAllMocks`, `restoreAllMocks`) are on the surface. `extractionGaps` names 7 Babel re-exports with no file (`BabelFile`, `GeneratorOptions`, `NodePath`, `analyzeMdx`, `babelParse`, `instance`, `transformSync`); none is documented, so none is compared.
- Signature comparison: `plan` listed 58 files and 84 checks. They were judged by 7 subagents, batched by directory (files 1-10, 11-20, 21-29, 30-38, 39-47, 48-54, 55-58), each writing one `signatures-<n>.txt` per plan file. 76 of 84 match.
- Deep tier re-export trace: the surface records one defining file per name. For `composeStories`, `composeStory` and `setProjectAnnotations` it records the renderer-agnostic core declarations (`code/core/src/preview-api/modules/store/csf/portable-stories.ts:274`, `:90`, `:73`), while the skill documents the React renderer wrappers that `@storybook/react` re-exports through `code/renderers/react/src/index.ts:5` (`code/renderers/react/src/portable-stories.tsx:148`, `:106`, `:46`), whose signatures the skill reproduces exactly. For `definePreview` and `defineMain` it records the Angular framework files (`code/frameworks/angular/src/client/preview.ts:45`, `code/frameworks/angular/src/node/index.ts:3`), which the brief scopes out, while `@storybook/react-vite` exports them from `code/frameworks/react-vite/src/index.ts:2` (`__definePreview` at `code/renderers/react/src/preview.tsx:55`) and `code/frameworks/react-vite/src/node/index.ts:3`. Neither `definePreview` nor `defineMain` is counted in the `tier_a_include` set as a result.
- Borderline signature judgments, as the subagents recorded them: `IconItem` and `Typeset` were called mismatches because the names-only prop lists carry no `?` while sibling rows of the same table mark optional props; `Canvas` (names-only, all props optional) was called a match because its table is headed "Props (simplified)". `storybookTest` was called a mismatch on a documented form taken from a usage example. `useThemeParameters` was called a mismatch on the resolved meaning of `ThemesParameters` (module-local alias for the inner object at `code/addons/themes/src/decorators/helpers.ts:10`), not on its text. The three portable-stories names and `definePreview` were compared at the file the plan named. Called matches: `useParameter` (`(key, default)` against `(parameterKey: string, defaultValue?: S): S | undefined`), `build`/`start` (destructured params against the `Builder` type), `DocsContainer`, `Markdown`, `ColorControl`, `mocked` (overload order), `spyOn` (read from `@vitest/spy` 3.2.4), `filterArgTypes` (inferred return), and `defineMain` (compared at the Angular file, same shape as react-vite).
- §1b: the inventory reports no `cross_check_mismatches`, so no split-body gap.
- §2b numerator ground truth: skipped (`stats.exports_documented` 228 differs from `effective_denominator` 280, no inflation signature).
- §4b metadata coherence: Medium drift (`stats.exports_public_api` 1335 against `exports[].length` 88, 93%) and Info multi-denominator (barrel 1335 against documented 228).
- §4c provenance line check: 228 entries checked; 45 `line-not-definition` stale items (none with a `definition_lines` entry, so all are Info `provenance-unverified`), 1 `file-missing`, 3 missing, 143 orphaned (reported by the helper only).

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | §2.1 required sections: `description` (Overview, L20), `usage` (Quick Start, L29) and `api_surface` (Key API Summary, L125) all satisfied; §2.2 fences balanced (10 fences); §2.3 no bare opening fence; §2.4 all 207 function exports used in the usage-family scope (split body, `references/` read); §2.5 no async/sync contradiction (10 exports called in examples: `expect` described with `await expect(...)` and awaited in 3 of 4 calls; `getByRole`'s awaited calls are arguments of `await userEvent.click(...)`; `storybookTest` carries no async claim); §2.6 no table drift; §2.7 no `scripts/` or `assets/` folder | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| - | - | - | none: the §1 inventory subagent reported no `cross_check_mismatches` | - | - |

**Exports Cross-Checked:** 37 (inventory names written in code both in the SKILL.md body and in a reference file)
**Mismatches Found:** 0

### Migration & Deprecation (§2b)

Section 4b verification skipped — evidence-report.md not found. (`forge-data/oms-storybook-react-vite/10.3.5/evidence-report.md` exists but has no YAML frontmatter, so `t2_future_count` is absent: Case 4.)

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
- **External Validation Score:** 100.0%
- **Tools used:** skill-check

## Completeness Score

**Result:** **FAIL**, not scored: the hard gate blocked this run on 8 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 55
**Blocking (Critical + High):** 8
**Non-blocking (Medium + Low + Info):** 47

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 8 | Read the source code and write or correct the documentation |
| High | 0 | None |
| Medium | 1 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 46 | Optional improvements, no action required |
| **Total** | **55** | |

### GAP-001: Signature mismatch: IconItem

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/components/IconGallery.tsx:62
**Export:** IconItem

**Issue:** documented `{ name, children }`, source `IconItem: FunctionComponent<IconItemProps>, IconItemProps = { name: string; children?: React.ReactNode }`: optionality not conveyed: 'children' is optional in source (children?: React.ReactNode) but documented without '?', which under the same file's names-only convention (Story row: '{ of?, meta?, ... }') reads as required; types (name: string) also omitted

**Remediation:** Update the documented signature of `IconItem` from `{ name, children }` to `IconItem: FunctionComponent<IconItemProps>, IconItemProps = { name: string; children?: React.ReactNode }`, the signature the source defines at `code/addons/docs/src/blocks/components/IconGallery.tsx:62`.

### GAP-002: Signature mismatch: Typeset

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/components/Typeset.tsx:50
**Export:** Typeset

**Issue:** documented `{ fontSizes, fontWeight, sampleText, fontFamily }`, source `Typeset: FC<TypesetProps>, TypesetProps = { fontFamily?: string; fontSizes: (string | number)[]; fontWeight?: number; sampleText?: string }`: optionality not conveyed: fontFamily, fontWeight and sampleText are optional and only fontSizes is required, but all four are documented without '?', which under the same file's names-only convention (Story row: '{ of?, meta?, ... }') reads as all required; types (fontSizes: (string | number)[], fontWeight: number, etc.) also omitted

**Remediation:** Update the documented signature of `Typeset` from `{ fontSizes, fontWeight, sampleText, fontFamily }` to `Typeset: FC<TypesetProps>, TypesetProps = { fontFamily?: string; fontSizes: (string | number)[]; fontWeight?: number; sampleText?: string }`, the signature the source defines at `code/addons/docs/src/blocks/components/Typeset.tsx:50`.

### GAP-003: Signature mismatch: useThemeParameters

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/themes/src/decorators/helpers.ts:20
**Export:** useThemeParameters

**Issue:** documented `(context?: StoryContext) => ThemesParameters`, source `(context?: StoryContext) => ThemesParameters  [module-local alias: type ThemesParameters = Parameters['themes'], where Parameters is the exported ThemesParameters interface from ../types, i.e. { disable?: boolean; themeOverride?: string } | undefined]`: return type 'ThemesParameters' in source is a module-local alias for the exported ThemesParameters['themes'] (the inner { disable?, themeOverride? } object, possibly undefined), not the exported ThemesParameters interface { themes?: { disable?; themeOverride? } } that the skill documents under that name

**Remediation:** Update the documented signature of `useThemeParameters` from `(context?: StoryContext) => ThemesParameters` to `(context?: StoryContext) => ThemesParameters  [module-local alias: type ThemesParameters = Parameters['themes'], where Parameters is the exported ThemesParameters interface from ../types, i.e. { disable?: boolean; themeOverride?: string } | undefined]`, the signature the source defines at `code/addons/themes/src/decorators/helpers.ts:20`.

### GAP-004: Signature mismatch: storybookTest

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/vitest/src/vitest-plugin/index.ts:164
**Export:** storybookTest

**Issue:** documented `({ configDir })`, source `(options?: UserOptions) => Promise<Plugin[]>  [UserOptions = { configDir?: string; storybookScript?: string; storybookUrl?: string; tags?: { include?: string[]; exclude?: string[]; skip?: string[] }; disableAddonDocs?: boolean }]`: single parameter 'options' is optional and typed UserOptions (five optional properties), but is documented as a required destructured object exposing only configDir (storybookScript, storybookUrl, tags, disableAddonDocs and the parameter's optionality are missing)

**Remediation:** Update the documented signature of `storybookTest` from `({ configDir })` to `(options?: UserOptions) => Promise<Plugin[]>  [UserOptions = { configDir?: string; storybookScript?: string; storybookUrl?: string; tags?: { include?: string[]; exclude?: string[]; skip?: string[] }; disableAddonDocs?: boolean }]`, the signature the source defines at `code/addons/vitest/src/vitest-plugin/index.ts:164`.

### GAP-005: Signature mismatch: setProjectAnnotations

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:73
**Export:** setProjectAnnotations

**Issue:** documented `(projectAnnotations: NamedOrDefaultProjectAnnotations<any> | NamedOrDefaultProjectAnnotations<any>[]) => NormalizedProjectAnnotations<ReactRenderer>`, source `setProjectAnnotations<TRenderer extends Renderer = Renderer>(projectAnnotations: NamedOrDefaultProjectAnnotations<TRenderer> | NamedOrDefaultProjectAnnotations<TRenderer>[]): NormalizedProjectAnnotations<TRenderer>`: documented is the React renderer wrapper (code/renderers/react/src/portable-stories.tsx:46), not this core declaration: source is generic over 'TRenderer extends Renderer = Renderer', taking NamedOrDefaultProjectAnnotations<TRenderer> (not <any>) and returning NormalizedProjectAnnotations<TRenderer> (not fixed to ReactRenderer)

**Remediation:** Update the documented signature of `setProjectAnnotations` from `(projectAnnotations: NamedOrDefaultProjectAnnotations<any> | NamedOrDefaultProjectAnnotations<any>[]) => NormalizedProjectAnnotations<ReactRenderer>` to `setProjectAnnotations<TRenderer extends Renderer = Renderer>(projectAnnotations: NamedOrDefaultProjectAnnotations<TRenderer> | NamedOrDefaultProjectAnnotations<TRenderer>[]): NormalizedProjectAnnotations<TRenderer>`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:73`.

### GAP-006: Signature mismatch: composeStory

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:90
**Export:** composeStory

**Issue:** documented `(story: StoryAnnotationsOrFn<ReactRenderer, TArgs>, componentAnnotations: Meta<TArgs | any>, projectAnnotations?: ProjectAnnotations<ReactRenderer>, exportsName?: string) => ComposedStoryFn<ReactRenderer, Partial<TArgs>>`, source `composeStory<TRenderer extends Renderer = Renderer, TArgs extends Args = Args>(storyAnnotations: LegacyStoryAnnotationsOrFn<TRenderer>, componentAnnotations: ComponentAnnotations<TRenderer, TArgs>, projectAnnotations?: ProjectAnnotations<TRenderer>, defaultConfig?: ProjectAnnotations<TRenderer>, exportsName?: string): ComposedStoryFn<TRenderer, Partial<TArgs>>`: documented is the four-parameter React renderer wrapper (code/renderers/react/src/portable-stories.tsx:106), not this core declaration: missing optional fourth parameter 'defaultConfig?: ProjectAnnotations<TRenderer>', so 'exportsName' is the fifth parameter in source, not the fourth; first parameter is 'storyAnnotations: LegacyStoryAnnotationsOrFn<TRenderer>' (not 'story: StoryAnnotationsOrFn<ReactRenderer, TArgs>'); second is 'ComponentAnnotations<TRenderer, TArgs>' (not 'Meta<TArgs | any>'); source is generic over TRenderer (params and return ComposedStoryFn<TRenderer, Partial<TArgs>>), not fixed to ReactRenderer

**Remediation:** Update the documented signature of `composeStory` from `(story: StoryAnnotationsOrFn<ReactRenderer, TArgs>, componentAnnotations: Meta<TArgs | any>, projectAnnotations?: ProjectAnnotations<ReactRenderer>, exportsName?: string) => ComposedStoryFn<ReactRenderer, Partial<TArgs>>` to `composeStory<TRenderer extends Renderer = Renderer, TArgs extends Args = Args>(storyAnnotations: LegacyStoryAnnotationsOrFn<TRenderer>, componentAnnotations: ComponentAnnotations<TRenderer, TArgs>, projectAnnotations?: ProjectAnnotations<TRenderer>, defaultConfig?: ProjectAnnotations<TRenderer>, exportsName?: string): ComposedStoryFn<TRenderer, Partial<TArgs>>`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:90`.

### GAP-007: Signature mismatch: composeStories

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:274
**Export:** composeStories

**Issue:** documented `(csfExports: TModule, projectAnnotations?: ProjectAnnotations<ReactRenderer>) => Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>`, source `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory) (return type not annotated; inferred from reduce(..., {}) as {})`: documented is the React renderer wrapper (code/renderers/react/src/portable-stories.tsx:148), not this core declaration: second parameter is the required 'globalConfig: ProjectAnnotations<Renderer>', documented as optional 'projectAnnotations?: ProjectAnnotations<ReactRenderer>'; optional third parameter 'composeStoryFn: ComposeStoryFn' is missing; first parameter is named 'storiesImport' (TModule extends Store_CSFExports, no ReactRenderer binding); source return type is unannotated (inferred {}), not Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>

**Remediation:** Update the documented signature of `composeStories` from `(csfExports: TModule, projectAnnotations?: ProjectAnnotations<ReactRenderer>) => Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>` to `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory) (return type not annotated; inferred from reduce(..., {}) as {})`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:274`.

### GAP-008: Signature mismatch: definePreview

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/frameworks/angular/src/client/preview.ts:45
**Export:** definePreview

**Issue:** documented `(input: PreviewInput) => ReactPreview<Addons>`, source `__definePreview<Addons extends PreviewAddon<never>[]>(input: { addons: Addons } & ProjectAnnotations<AngularRenderer & InferTypes<Addons>>): AngularPreview<AngularRenderer & InferTypes<Addons>>`: return type mismatch: source returns AngularPreview<AngularRenderer & InferTypes<Addons>>, documented ReactPreview<Addons>; documented param type PreviewInput does not exist in source (actual: { addons: Addons } & ProjectAnnotations<AngularRenderer & InferTypes<Addons>>)

**Remediation:** Update the documented signature of `definePreview` from `(input: PreviewInput) => ReactPreview<Addons>` to `__definePreview<Addons extends PreviewAddon<never>[]>(input: { addons: Addons } & ProjectAnnotations<AngularRenderer & InferTypes<Addons>>): AngularPreview<AngularRenderer & InferTypes<Addons>>`, the signature the source defines at `code/frameworks/angular/src/client/preview.ts:45`.

### GAP-009: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_public_api=1335, exports[].length=88 → 93% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json`; update-skill applies it as a metadata update.

### GAP-010: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=1335, documented=228

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-011: Provenance line not verified for A11yGlobals_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:16
**Export:** A11yGlobals_exact

**Issue:** the line-check rules found no definition line for `A11yGlobals_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 16 defines `A11yGlobals_exact`; if another line does, set the provenance `source_line` to it.

### GAP-012: Provenance line not verified for A11yReport_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:5
**Export:** A11yReport_exact

**Issue:** the line-check rules found no definition line for `A11yReport_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 5 defines `A11yReport_exact`; if another line does, set the provenance `source_line` to it.

### GAP-013: Provenance line not verified for ArgTypes

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ArgTypes

**Issue:** the line-check rules found no definition line for `ArgTypes` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ArgTypes`; if another line does, set the provenance `source_line` to it.

### GAP-014: Provenance line not verified for Canvas

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Canvas

**Issue:** the line-check rules found no definition line for `Canvas` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Canvas`; if another line does, set the provenance `source_line` to it.

### GAP-015: Provenance line not verified for ColorPalette

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ColorPalette

**Issue:** the line-check rules found no definition line for `ColorPalette` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ColorPalette`; if another line does, set the provenance `source_line` to it.

### GAP-016: Provenance line not verified for ComponentEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** ComponentEntry

**Issue:** the line-check rules found no definition line for `ComponentEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 27 defines `ComponentEntry`; if another line does, set the provenance `source_line` to it.

### GAP-017: Provenance line not verified for Controls

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Controls

**Issue:** the line-check rules found no definition line for `Controls` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Controls`; if another line does, set the provenance `source_line` to it.

### GAP-018: Provenance line not verified for Description

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Description

**Issue:** the line-check rules found no definition line for `Description` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Description`; if another line does, set the provenance `source_line` to it.

### GAP-019: Provenance line not verified for DocsContainer

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContainer

**Issue:** the line-check rules found no definition line for `DocsContainer` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContainer`; if another line does, set the provenance `source_line` to it.

### GAP-020: Provenance line not verified for DocsContext

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContext

**Issue:** the line-check rules found no definition line for `DocsContext` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContext`; if another line does, set the provenance `source_line` to it.

### GAP-021: Provenance line not verified for DocsEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** DocsEntry

**Issue:** the line-check rules found no definition line for `DocsEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 34 defines `DocsEntry`; if another line does, set the provenance `source_line` to it.

### GAP-022: Provenance line not verified for GroupEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** GroupEntry

**Issue:** the line-check rules found no definition line for `GroupEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 21 defines `GroupEntry`; if another line does, set the provenance `source_line` to it.

### GAP-023: Provenance line not verified for HashEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** HashEntry

**Issue:** the line-check rules found no definition line for `HashEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 67 defines `HashEntry`; if another line does, set the provenance `source_line` to it.

### GAP-024: Provenance line not verified for IconGallery

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** IconGallery

**Issue:** the line-check rules found no definition line for `IconGallery` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `IconGallery`; if another line does, set the provenance `source_line` to it.

### GAP-025: Provenance line not verified for IndexHash

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** IndexHash

**Issue:** the line-check rules found no definition line for `IndexHash` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 80 defines `IndexHash`; if another line does, set the provenance `source_line` to it.

### GAP-026: Provenance line not verified for LeafEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** LeafEntry

**Issue:** the line-check rules found no definition line for `LeafEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 66 defines `LeafEntry`; if another line does, set the provenance `source_line` to it.

### GAP-027: Provenance line not verified for Markdown

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Markdown

**Issue:** the line-check rules found no definition line for `Markdown` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Markdown`; if another line does, set the provenance `source_line` to it.

### GAP-028: Provenance line not verified for Primary

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Primary

**Issue:** the line-check rules found no definition line for `Primary` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Primary`; if another line does, set the provenance `source_line` to it.

### GAP-029: Provenance line not verified for PureArgsTable

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320
**Export:** PureArgsTable

**Issue:** the line-check rules found no definition line for `PureArgsTable` in `code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx` and confirm that line 320 defines `PureArgsTable`; if another line does, set the provenance `source_line` to it.

### GAP-030: Provenance line not verified for RootEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** RootEntry

**Issue:** the line-check rules found no definition line for `RootEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 15 defines `RootEntry`; if another line does, set the provenance `source_line` to it.

### GAP-031: Provenance line not verified for Source

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Source

**Issue:** the line-check rules found no definition line for `Source` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Source`; if another line does, set the provenance `source_line` to it.

### GAP-032: Provenance line not verified for Stories

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Stories

**Issue:** the line-check rules found no definition line for `Stories` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Stories`; if another line does, set the provenance `source_line` to it.

### GAP-033: Provenance line not verified for Story

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Story

**Issue:** the line-check rules found no definition line for `Story` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Story`; if another line does, set the provenance `source_line` to it.

### GAP-034: Provenance line not verified for StoryEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** StoryEntry

**Issue:** the line-check rules found no definition line for `StoryEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 45 defines `StoryEntry`; if another line does, set the provenance `source_line` to it.

### GAP-035: Provenance line not verified for Subtitle

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Subtitle

**Issue:** the line-check rules found no definition line for `Subtitle` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Subtitle`; if another line does, set the provenance `source_line` to it.

### GAP-036: Provenance line not verified for ThemesGlobals_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/types.ts:20
**Export:** ThemesGlobals_def

**Issue:** the line-check rules found no definition line for `ThemesGlobals_def` in `code/addons/themes/src/types.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/types.ts` and confirm that line 20 defines `ThemesGlobals_def`; if another line does, set the provenance `source_line` to it.

### GAP-037: Provenance line not verified for Title

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Title

**Issue:** the line-check rules found no definition line for `Title` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Title`; if another line does, set the provenance `source_line` to it.

### GAP-038: Provenance line not verified for Typeset

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Typeset

**Issue:** the line-check rules found no definition line for `Typeset` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Typeset`; if another line does, set the provenance `source_line` to it.

### GAP-039: Provenance line not verified for Unstyled

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Unstyled

**Issue:** the line-check rules found no definition line for `Unstyled` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Unstyled`; if another line does, set the provenance `source_line` to it.

### GAP-040: Provenance line not verified for a11y_decorators

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:12
**Export:** a11y_decorators

**Issue:** the line-check rules found no definition line for `a11y_decorators` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 12 defines `a11y_decorators`; if another line does, set the provenance `source_line` to it.

### GAP-041: Provenance line not verified for a11y_initialGlobals

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:98
**Export:** a11y_initialGlobals

**Issue:** the line-check rules found no definition line for `a11y_initialGlobals` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 98 defines `a11y_initialGlobals`; if another line does, set the provenance `source_line` to it.

### GAP-042: Provenance line not verified for a11y_parameters

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:105
**Export:** a11y_parameters

**Issue:** the line-check rules found no definition line for `a11y_parameters` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 105 defines `a11y_parameters`; if another line does, set the provenance `source_line` to it.

### GAP-043: Provenance line not verified for fireEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:43
**Export:** fireEvent

**Issue:** the line-check rules found no definition line for `fireEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 43 defines `fireEvent`; if another line does, set the provenance `source_line` to it.

### GAP-044: Provenance line not verified for mockChannel_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:3
**Export:** mockChannel_def

**Issue:** the line-check rules found no definition line for `mockChannel_def` in `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts`; check by hand

**Remediation:** Open `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts` and confirm that line 3 defines `mockChannel_def`; if another line does, set the provenance `source_line` to it.

### GAP-045: Provenance line not verified for screen

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:107
**Export:** screen

**Issue:** the line-check rules found no definition line for `screen` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 107 defines `screen`; if another line does, set the provenance `source_line` to it.

### GAP-046: Provenance line not verified for useOf

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** useOf

**Issue:** the line-check rules found no definition line for `useOf` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `useOf`; if another line does, set the provenance `source_line` to it.

### GAP-047: Provenance line not verified for userEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:123
**Export:** userEvent

**Issue:** the line-check rules found no definition line for `userEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 123 defines `userEvent`; if another line does, set the provenance `source_line` to it.

### GAP-048: Provenance line not verified for waitFor

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:108
**Export:** waitFor

**Issue:** the line-check rules found no definition line for `waitFor` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 108 defines `waitFor`; if another line does, set the provenance `source_line` to it.

### GAP-049: Provenance line not verified for withThemeByClassName

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByClassName

**Issue:** the line-check rules found no definition line for `withThemeByClassName` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByClassName`; if another line does, set the provenance `source_line` to it.

### GAP-050: Provenance line not verified for withThemeByClassName_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/class-name.decorator.tsx:19
**Export:** withThemeByClassName_exact

**Issue:** the line-check rules found no definition line for `withThemeByClassName_exact` in `code/addons/themes/src/decorators/class-name.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/class-name.decorator.tsx` and confirm that line 19 defines `withThemeByClassName_exact`; if another line does, set the provenance `source_line` to it.

### GAP-051: Provenance line not verified for withThemeByDataAttribute

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByDataAttribute

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByDataAttribute`; if another line does, set the provenance `source_line` to it.

### GAP-052: Provenance line not verified for withThemeByDataAttribute_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/data-attribute.decorator.tsx:19
**Export:** withThemeByDataAttribute_exact

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute_exact` in `code/addons/themes/src/decorators/data-attribute.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/data-attribute.decorator.tsx` and confirm that line 19 defines `withThemeByDataAttribute_exact`; if another line does, set the provenance `source_line` to it.

### GAP-053: Provenance line not verified for withThemeFromJSXProvider

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeFromJSXProvider

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeFromJSXProvider`; if another line does, set the provenance `source_line` to it.

### GAP-054: Provenance line not verified for withThemeFromJSXProvider_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:23
**Export:** withThemeFromJSXProvider_exact

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider_exact` in `code/addons/themes/src/decorators/provider.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/provider.decorator.tsx` and confirm that line 23 defines `withThemeFromJSXProvider_exact`; if another line does, set the provenance `source_line` to it.

### GAP-055: Provenance line not verified for within

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:110
**Export:** within

**Issue:** the line-check rules found no definition line for `within` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 110 defines `within`; if another line does, set the provenance `source_line` to it.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
