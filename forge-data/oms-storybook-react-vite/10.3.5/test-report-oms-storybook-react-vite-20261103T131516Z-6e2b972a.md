---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261103T131516Z-6e2b972a'
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
testDate: '2026-11-03T13:15:16Z'
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

**Mode Rationale:** metadata.json records `skill_type: "single"`, so the deterministic lookup selects Naive Mode (API-surface coverage; coherence is structural only and carries no scoring category).

**Analysis Plan:**
- Coverage Check: Deep tier, local source at the pinned commit e486d38 (workspace drift ok): every documented export is checked for presence in SKILL.md and references, and its signature compared against the deciding source line (name, type, order, optionality of every parameter, and the return type), with type coverage of the public surface.
- Coherence Check: naive (structural) checks only: references resolve, SKILL.md and reference files agree on the documented surface, and the metadata coherence script runs; no coherence category is scored.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces
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
- **Documented:** 467 (100%)
- **Missing Documentation:** 0 (a floored residual: the numerator exceeds the denominator)
- **Signature Mismatches:** 4
- **Stale Documentation:** N/A: the scalar denominator (`stats.effective_denominator`) counts the exports without naming them
- **Numerator Surplus:** 187, uncapped coverage 166.79%
- **Scoped Out by the Brief:** `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx), `AngularMeta` (code/frameworks/angular/src/client/preview.ts), `AngularOptions` (code/frameworks/angular/src/types.ts), `AngularPreview` (code/frameworks/angular/src/client/preview.ts), `AngularRenderer` (code/frameworks/angular/src/client/types.ts), `AngularStory` (code/frameworks/angular/src/client/preview.ts), `BabelFileClass` (code/core/src/babel/index.ts), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts), `Bar` (code/core/src/components/components/Bar/Bar.tsx), `BaseLocationProvider` (code/core/src/router/router.tsx), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx), `BuildIndexOptions` (code/core/src/core-server/build-index.ts), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts), `CacheEntry` (code/core/src/telemetry/event-cache.ts), `Channel` (code/core/src/channels/main.ts), `ChannelHandler` (code/core/src/channels/types.ts), `ChannelTransport` (code/core/src/channels/types.ts), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts), `CsfFile` (code/core/src/csf-tools/CsfFile.ts), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts), `DL` (code/core/src/components/components/typography/elements/DL.tsx), `Dependency` (code/core/src/telemetry/types.ts), `Div` (code/core/src/components/components/typography/elements/Div.tsx), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts), `ErrorCollector` (code/core/src/telemetry/error-collector.ts), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx), `EventType` (code/core/src/telemetry/types.ts), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts), `H1` (code/core/src/components/components/typography/elements/H1.tsx), `H2` (code/core/src/components/components/typography/elements/H2.tsx), `H3` (code/core/src/components/components/typography/elements/H3.tsx), `H4` (code/core/src/components/components/typography/elements/H4.tsx), `H5` (code/core/src/components/components/typography/elements/H5.tsx), `H6` (code/core/src/components/components/typography/elements/H6.tsx), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts), `HR` (code/core/src/components/components/typography/elements/HR.tsx), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts), `IStory` (code/frameworks/angular/src/client/types.ts), `InitPayload` (code/core/src/telemetry/types.ts), `LI` (code/core/src/components/components/typography/elements/LI.tsx), `LinkProps` (code/core/src/router/types.ts), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx), `Location` (code/core/src/router/router.tsx), `LocationProvider` (code/core/src/router/router.tsx), `LogLevel` (code/core/src/node-logger/logger/logger.ts), `MemoryRouter` (code/core/src/router/router.tsx), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts), `NavigateFunction` (code/core/src/router/types.ts), `NavigateOptions` (code/core/src/router/types.ts), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts), `OL` (code/core/src/components/components/typography/elements/OL.tsx), `Other` (code/core/src/router/types.ts), `P` (code/core/src/components/components/typography/elements/P.tsx), `Payload` (code/core/src/telemetry/types.ts), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx), `Popover` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts), `PreactRenderer` (code/renderers/preact/src/types.ts), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx), `RenderData` (code/core/src/router/types.ts), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx), `Route` (code/core/src/router/router.tsx), `RouterData` (code/core/src/router/types.ts), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx), `Separator` (code/core/src/components/components/Bar/Separator.tsx), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx), `Span` (code/core/src/components/components/typography/elements/Span.tsx), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts), `StaticStory` (code/core/src/csf-tools/CsfFile.ts), `StoryData` (code/core/src/router/utils.ts), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts), `StoryTest` (code/core/src/csf-tools/CsfFile.ts), `StorybookAddon` (code/core/src/telemetry/types.ts), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx), `StorybookMetadata` (code/core/src/telemetry/types.ts), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts), `SvelteRenderer` (code/renderers/svelte/src/types.ts), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `TT` (code/core/src/components/components/typography/elements/TT.tsx), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx), `TabButton` (code/core/src/components/components/Tabs/Button.tsx), `TabList` (code/core/src/components/components/Tabs/TabList.tsx), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `TelemetryData` (code/core/src/telemetry/types.ts), `TelemetryEvent` (code/core/src/telemetry/types.ts), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts), `UL` (code/core/src/components/components/typography/elements/UL.tsx), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts), `WebComponentsStory` (code/renderers/web-components/src/preview.ts), `WebComponentsTypes` (code/renderers/web-components/src/types.ts), `WebsocketTransport` (code/core/src/channels/websocket/index.ts), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts), `babelParseExpression` (code/core/src/babel/babelParse.ts), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts), `babelPrint` (code/core/src/babel/babelParse.ts), `buildArgsParam` (code/core/src/router/utils.ts), `buildDevStandalone` (code/core/src/core-server/build-dev.ts), `buildIndexStandalone` (code/core/src/core-server/build-index.ts), `buildStaticStandalone` (code/core/src/core-server/build-static.ts), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts), `cleanPaths` (code/core/src/telemetry/sanitize.ts), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx), `colors` (code/core/src/node-logger/index.ts), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts), `components` (code/core/src/components/index.ts), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `createBrowserChannel` (code/core/src/channels/index.ts), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts), `experimental_loadStorybook` (code/core/src/core-server/load.ts), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts), `extractSource` (code/core/src/csf-tools/enrichCsf.ts), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts), `formatCsf` (code/core/src/csf-tools/CsfFile.ts), `framework` (code/core/src/core-server/presets/common-override-preset.ts), `generate` (code/core/src/babel/index.ts), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts), `getCustomElements` (code/renderers/web-components/src/framework-api.ts), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts), `getLastEvents` (code/core/src/telemetry/event-cache.ts), `getMatch` (code/core/src/router/utils.ts), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts), `getServerPort` (code/core/src/core-server/utils/server-address.ts), `getSessionId` (code/core/src/telemetry/session-id.ts), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts), `hrefTo` (code/addons/links/src/utils.ts), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts), `isExampleStoryId` (code/core/src/telemetry/index.ts), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts), `isValidComponent` (code/renderers/web-components/src/framework-api.ts), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts), `linkTo` (code/addons/links/src/utils.ts), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts), `loadCsf` (code/core/src/csf-tools/CsfFile.ts), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx), `navigate` (code/addons/links/src/utils.ts), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts), `parsePath` (code/core/src/router/utils.ts), `parserOptions` (code/core/src/babel/babelParse.ts), `printConfig` (code/core/src/csf-tools/ConfigFile.ts), `printCsf` (code/core/src/csf-tools/CsfFile.ts), `prompt` (code/core/src/node-logger/prompts/index.ts), `protectUrls` (code/core/src/node-logger/wrap-utils.ts), `queryFromLocation` (code/core/src/router/utils.ts), `readConfig` (code/core/src/csf-tools/ConfigFile.ts), `readCsf` (code/core/src/csf-tools/CsfFile.ts), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts), `resetComponents` (code/core/src/components/index.ts), `resolveExpression` (code/core/src/babel/expression-resolver.ts), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts), `sanitizeError` (code/core/src/telemetry/sanitize.ts), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts), `setCustomElements` (code/renderers/web-components/src/framework-api.ts), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts), `stories` (code/core/src/core-server/presets/common-override-preset.ts), `stringifyQuery` (code/core/src/router/utils.ts), `telemetry` (code/core/src/telemetry/index.ts), `traverse` (code/core/src/babel/index.ts), `typescript` (code/core/src/core-server/presets/common-override-preset.ts), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts), `useNavigate` (code/core/src/router/router.tsx), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `withLinks` (code/addons/links/src/utils.ts), `withReset` (code/core/src/components/components/typography/lib/common.tsx), `withTelemetry` (code/core/src/core-server/withTelemetry.ts), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts), `writeCsf` (code/core/src/csf-tools/CsfFile.ts)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 95.35% |
| Type Coverage | 81.67% |

**Notes (§2 to §4b):**

- **Deep tier, version check:** `gh api repos/storybookjs/storybook/git/ref/tags/v10.3.5` resolves to commit `e486d3826bcd40c52db1c766966d1c8ec16df6cb`, the pinned `source_commit`; the workspace HEAD matches it (init §5b) and `code/core/package.json` reads `"version": "10.3.5"`. Re-exports were traced for the paired names whose surface record is not the documented declaration: `@storybook/react-vite` re-exports `@storybook/react` (`code/frameworks/react-vite/src/index.ts:1`), whose `composeStories`, `composeStory` and `setProjectAnnotations` are defined in `code/renderers/react/src/portable-stories.tsx` (lines 148, 106, 46).
- **Extraction:** `status: ok`, 1274 files in scope, no fallback. `extraction.readByEye` names 5 files with an ast-grep syntax issue (`code/core/src/csf/csf-factories.ts`, `code/core/src/instrumenter/typings.d.ts`, `code/core/src/mocking-utils/esmWalker.ts`, `code/core/src/test/spy.ts`, `code/core/src/typings.d.ts`); §2 reads them by eye only on `status: incomplete`, so none was read. `code/core/src/test/spy.ts` is tier A and its seven function exports are on the surface.
- **Extraction gaps:** 7 names no recipe found (`BabelFile`, `GeneratorOptions`, `NodePath`, `analyzeMdx`, `babelParse`, `instance`, `transformSync`), all with no file or line and none in the `tier_a_include` set; the skill gives none of them a signature, so there was nothing to read.
- **Inventory (§1, §1a):** no subagent tool is available in this session, so the main thread read SKILL.md (its `## Full` sections are stubs) and all six reference files, in that order (references alphabetically), and built the §1 JSON itself: 473 entries, one per documented name and kind, a second entry only where the skill documents a second declaration of the same name (`composeStories`, `composeStory`, `Meta`, `ArgTypes`, `Preview`, `Canvas`). A first build missed `PropDescriptor` (core-api.md:114) and `StoryProps` (doc-blocks.md:31); both were added and §1a, the plan and the score were run again before anything was recorded (the plan did not change). §1a: valid, spot-check sampled `A`, `Stories`, `withoutVitePlugins`, none absent.
- **Split-body cross-check (§1b):** no mismatch recorded. Borderline, called no mismatch: SKILL.md:111 writes the call `withThemeByDataAttribute({ themes, defaultTheme })`, while references/addons.md:110-111 give the parameter as `config: DataAttributeStrategyConfiguration` with the optional `parentSelector?` and `attributeName?`. Both sides show one parameter; the SKILL.md form is an object literal in a call (shorthand properties, no types, no `?`), read as a usage example like SKILL.md:120's `<Canvas of={...} />`, not as a signature that omits an optional parameter.
- **Signature comparison batching (§2):** no subagent tool is available, so all 86 checks of the plan's 60 file entries were compared in the main thread, each against the full declaration at the plan's `file:line`, with the §2 rule as written (params: name, type, order, optionality; and the return type; a missing optional parameter is a mismatch). The 60 per-file results were saved as one JSON list, `signatures-1.txt`, with the Write tool. 4 mismatches: `composeStories`, `setProjectAnnotations`, `useParameter`, `viteFinal`.
- **How the rule was applied (recorded so a re-run judges alike):** a documented parameter given without a type (`ArgTypes`, `Controls`, `ColorItem`, `prepareMeta`, `prepareStory`, `decorateStory`, `sortStoriesV7`, `viteFinal`, `Source`'s `storyContext`) was compared on name, order and optionality only, a bare name without `?` being read as required (so `ColorItem`'s `{ title, subtitle, colors }` matches three required props, and `useParameter`'s bare `default` does not match the optional `defaultValue?`); a documented parameter name against a destructuring pattern in the source (`withThemeBy*`, `normalizeProjectAnnotations`, `sanitizeStoryContextUpdate`, `afterEach`) is no name mismatch; type-parameter headers (`<R>` for `<TRenderer extends Renderer>`, `fn<T>` for `fn<T extends Procedure = Procedure>`) are outside the compared list; an unannotated source return type was compared as the type TypeScript infers (`formatDate`, `parseDate`, `parse`, `format`, `toId`, `mockChannel`, `combineParameters`, `sortStoriesV7`, `hasVitePlugins`, `initializeThemeState`, `clearAllMocks`, `resetAllMocks`, `restoreAllMocks`, `defineMain`); overload order (`mocked`) and member order inside one props object are not compared.
- **Borderline signature calls (recorded, not overridden):** `useParameter` (mismatch: the bare-name optionality reading above, plus the names `key`/`default` against `parameterKey`/`defaultValue`); `useThemeParameters` (match: the documented return `ThemesParameters['themes']`, named against the `types.ts` interface, is the type the source's local alias `ThemesParameters = Parameters['themes']` denotes, and the skill spells out the resolved `{ disable?: boolean; themeOverride?: string } | undefined`); `ColorControl` (match: the source's `ComponentProps<typeof LazyColorControl>` resolves to the documented `ColorControlProps`, `Color.tsx:459` default-exporting `FC<ColorControlProps>`); `afterEach` (match: the documented `AfterEach<any>` is the declared type, and the documented `Promise<void>` is what the async arrow returns, while `AfterEach`'s own return type is `Awaitable<void>`); `spyOn` (match on the declaration `spyOn: typeof vitestSpyOn`; the three vitest overloads were checked against `@vitest/spy` 3.2.4 from knowledge, since the workspace has no `node_modules`).
- **Plan pairing:** the plan pairs each documented name with the first surface record of that name by file. `composeStories` and `setProjectAnnotations` were compared with core's `code/core/src/preview-api/modules/store/csf/portable-stories.ts` while their first inventory entries document the React wrappers of `code/renderers/react/src/portable-stories.tsx`; `viteFinal` with `@storybook/addon-docs`' preset (`code/addons/docs/src/preset.ts:159`) while the skill documents `@storybook/react-vite`'s preset (`code/frameworks/react-vite/src/preset.ts:10`); `defineMain` with `code/frameworks/angular/src/node/index.ts:3`, textually identical to react-vite's `node/index.ts:3`. `composeStory`'s first inventory entry is core's form (references/core-api.md:94, read before story-types.md), so it was compared with core's declaration and matches.
- **Numerator surplus:** the scalar branch counts 467 documented names against the stored 280, a surplus of 187, held at 100%. The brief's `scope.tier_a_include` globs match files (118 files define the 280 tier A names; 272 files match the globs) and `guards.deflation` does not fire (re-derived 985 vs 280), so this is not the deflated-denominator signature.
- **Numerator ground truth:** skipped (`stats.exports_documented` 228 ≠ `stats.effective_denominator` 280).
- **Type Coverage:** 98 of the 120 tier A types are documented; the 22 missing are listed in `signatures.json` `missingTypes` (`ColorProps`, `Component`, `DescriptionType`, `Easing`, `ExternalDocsProps`, `GlobalStateUpdate`, `HighlightTypes`, `Of`, `ReactTypes`, `Report`, `ReporterAPI`, `SelectionStore`, `SourceContextProps`, `SourceItem`, `StorySources`, `UserEvent`, `UserEventObject`, `View`, `Viewport`, `ViewportGlobals`, `ViewportMap`, `ViewportTypes`). `Of`, `ReactTypes` and `ViewportMap` appear in the skill only inside other signatures, never described.
- **Metadata coherence (§4b):** barrel cluster `stats.exports_public_api` 1335 vs `exports[].length` 88 (93% drift, Medium `metadata-drift`); barrel 1335 vs documented 228 (Info `multi-denominator`).
- **Provenance line check (§4c):** 27 stale entries, all `line-not-definition` with no definition line (Info `provenance-unverified`). The helper also reports 3 metadata exports with no map entry (`Args`, `DocsPage`, `Parameters`) and 143 orphaned map entries, which §4c does not report as gaps.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| — | — | — | No structural finding across §§2.1–2.7 | — |

**Structural Issues:** 0

- §2.1 required sections: `description` satisfied by `Overview` (line 20), `usage` by `Quick Start` (line 29), `api_surface` by `Key API Summary` (line 125); the frontmatter `description` is non-empty.
- §2.2 code fences: balanced (10 fences).
- §2.3 language tags: no bare opening fence.
- §2.4 usage scope: split body (the `## Full API Reference`, `## Full Type Definitions` and `## Full Integration Patterns` sections at lines 202, 206 and 210 are stubs pointing at `references/`, so `--body single` was not passed); every one of the 201 function and method exports of the inventory is referenced in a usage-family section or reference file (`zero_usage` empty).
- §2.5 async/sync: 9 function exports are called in fenced code (`fn`, `composeStories`, `setProjectAnnotations`, `withThemeByClassName`, `withThemeByDataAttribute`, `withThemeFromJSXProvider`, `storybookTest`, `definePreview`, `getByRole`); none is described as async or as sync. `getByRole`'s two awaited calls (`references/csf3-patterns.md:37`, `references/story-types.md:321`) await `userEvent.click(...)`, which wraps the query, and the skill makes no sync claim for `getByRole`. The async builder helpers (`hasVitePlugins`, `withoutVitePlugins`, `bail`, `start`, `build`) are called in no fenced example. No finding.
- §2.6 table syntax: no column drift.
- §2.7 Scripts & Assets: no `scripts/` or `assets/` folder.
- Observation outside §§2.1–2.7, not recorded as a gap (no naive check covers it): SKILL.md:171 says `A11yTestMode` and `Framework` "live in `references/story-types.md`", but story-types.md documents neither, and neither name is a type the in-scope source exports (the a11y test mode type is the module-local `A11yTest` at `code/addons/a11y/src/params.ts:18`).

**Naive coherence:** PASS (0 findings).

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| — | — | — | No mismatch | — | — |

**Exports Cross-Checked:** 473 inventory entries across SKILL.md and 6 reference files
**Mismatches Found:** 0 (one borderline call, `withThemeByDataAttribute` at SKILL.md:111 against references/addons.md:110-111, judged no mismatch: see the Coverage Analysis notes)

### Migration / Deprecation (§2b)

Section 4b verification skipped — evidence-report.md not found. (Case 4: `forge-data/oms-storybook-react-vite/10.3.5/evidence-report.md` exists but has no YAML frontmatter, so `t2_future_count` is absent; the detection contract treats that as Case 4 and skips silently. SKILL.md has no "Migration & Deprecation Warnings" section either.)

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

**Result:** **FAIL**, not scored: the hard gate blocked this run on 4 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 33
**Blocking (Critical + High):** 4
**Non-blocking (Medium + Low + Info):** 29

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 4 | Read the source code and write or correct the documentation |
| High | 0 | None |
| Medium | 1 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 28 | Optional improvements, no action required |
| **Total** | **33** | |

### GAP-001: Signature mismatch: viteFinal

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/preset.ts:159
**Export:** viteFinal

**Issue:** documented `viteFinal: PresetProperty<'viteFinal'> = async (config, options) => { ... }`, source `export const viteFinal = async (config: any, options: Options) => { ...; return { ...config, plugins: [...] } } (no declared type; return type inferred)`: declared type: the documented `PresetProperty<'viteFinal'>` is not the type of this declaration (unannotated, `config: any, options: Options`), and since StorybookConfigRaw has no `viteFinal` key it resolves to a function taking `config: never` and returning `never | Promise<never>`, so parameter and return types differ

**Remediation:** Update the documented signature of `viteFinal` from `viteFinal: PresetProperty<'viteFinal'> = async (config, options) => { ... }` to `export const viteFinal = async (config: any, options: Options) => { ...; return { ...config, plugins: [...] } } (no declared type; return type inferred)`, the signature the source defines at `code/addons/docs/src/preset.ts:159`.

### GAP-002: Signature mismatch: useParameter

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/addons/hooks.ts:590
**Export:** useParameter

**Issue:** documented `useParameter(key, default)`, source `useParameter<S>(parameterKey: string, defaultValue?: S): S | undefined`: parameter names differ ('key' vs 'parameterKey', 'default' vs 'defaultValue') and the second parameter is optional in the source ('defaultValue?') while the documented 'default' is shown without '?'

**Remediation:** Update the documented signature of `useParameter` from `useParameter(key, default)` to `useParameter<S>(parameterKey: string, defaultValue?: S): S | undefined`, the signature the source defines at `code/core/src/preview-api/modules/addons/hooks.ts:590`.

### GAP-003: Signature mismatch: setProjectAnnotations

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:73
**Export:** setProjectAnnotations

**Issue:** documented `setProjectAnnotations(projectAnnotations: NamedOrDefaultProjectAnnotations<any> | NamedOrDefaultProjectAnnotations<any>[]): NormalizedProjectAnnotations<ReactRenderer>`, source `setProjectAnnotations<TRenderer extends Renderer = Renderer>(projectAnnotations: NamedOrDefaultProjectAnnotations<TRenderer> | NamedOrDefaultProjectAnnotations<TRenderer>[]): NormalizedProjectAnnotations<TRenderer>`: type of 'projectAnnotations': NamedOrDefaultProjectAnnotations<TRenderer> (generic) vs <any>; return type NormalizedProjectAnnotations<TRenderer> vs NormalizedProjectAnnotations<ReactRenderer>

**Remediation:** Update the documented signature of `setProjectAnnotations` from `setProjectAnnotations(projectAnnotations: NamedOrDefaultProjectAnnotations<any> | NamedOrDefaultProjectAnnotations<any>[]): NormalizedProjectAnnotations<ReactRenderer>` to `setProjectAnnotations<TRenderer extends Renderer = Renderer>(projectAnnotations: NamedOrDefaultProjectAnnotations<TRenderer> | NamedOrDefaultProjectAnnotations<TRenderer>[]): NormalizedProjectAnnotations<TRenderer>`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:73`.

### GAP-004: Signature mismatch: composeStories

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:274
**Export:** composeStories

**Issue:** documented `composeStories<TModule extends Store_CSFExports<ReactRenderer, any>>(csfExports: TModule, projectAnnotations?: ProjectAnnotations<ReactRenderer>): Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>`, source `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory) (return type not annotated)`: first parameter named 'csfExports' vs 'storiesImport'; second parameter is the required 'globalConfig: ProjectAnnotations<Renderer>' in the source, documented as optional 'projectAnnotations?: ProjectAnnotations<ReactRenderer>'; missing optional parameter 'composeStoryFn'; documented return type Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports> vs not annotated

**Remediation:** Update the documented signature of `composeStories` from `composeStories<TModule extends Store_CSFExports<ReactRenderer, any>>(csfExports: TModule, projectAnnotations?: ProjectAnnotations<ReactRenderer>): Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>` to `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory) (return type not annotated)`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:274`.

### GAP-005: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_public_api=1335, exports[].length=88 → 93% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json`; update-skill applies it as a metadata update.

### GAP-006: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=1335, documented=228

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-007: Provenance line not verified for A11yGlobals_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:16
**Export:** A11yGlobals_exact

**Issue:** the line-check rules found no definition line for `A11yGlobals_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 16 defines `A11yGlobals_exact`; if another line does, set the provenance `source_line` to it.

### GAP-008: Provenance line not verified for A11yReport_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:5
**Export:** A11yReport_exact

**Issue:** the line-check rules found no definition line for `A11yReport_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 5 defines `A11yReport_exact`; if another line does, set the provenance `source_line` to it.

### GAP-009: Provenance line not verified for ComponentEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** ComponentEntry

**Issue:** the line-check rules found no definition line for `ComponentEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 27 defines `ComponentEntry`; if another line does, set the provenance `source_line` to it.

### GAP-010: Provenance line not verified for DocsEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** DocsEntry

**Issue:** the line-check rules found no definition line for `DocsEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 34 defines `DocsEntry`; if another line does, set the provenance `source_line` to it.

### GAP-011: Provenance line not verified for GroupEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** GroupEntry

**Issue:** the line-check rules found no definition line for `GroupEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 21 defines `GroupEntry`; if another line does, set the provenance `source_line` to it.

### GAP-012: Provenance line not verified for HashEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** HashEntry

**Issue:** the line-check rules found no definition line for `HashEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 67 defines `HashEntry`; if another line does, set the provenance `source_line` to it.

### GAP-013: Provenance line not verified for IndexHash

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** IndexHash

**Issue:** the line-check rules found no definition line for `IndexHash` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 80 defines `IndexHash`; if another line does, set the provenance `source_line` to it.

### GAP-014: Provenance line not verified for LeafEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** LeafEntry

**Issue:** the line-check rules found no definition line for `LeafEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 66 defines `LeafEntry`; if another line does, set the provenance `source_line` to it.

### GAP-015: Provenance line not verified for PureArgsTable

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320
**Export:** PureArgsTable

**Issue:** the line-check rules found no definition line for `PureArgsTable` in `code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx` and confirm that line 320 defines `PureArgsTable`; if another line does, set the provenance `source_line` to it.

### GAP-016: Provenance line not verified for RootEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** RootEntry

**Issue:** the line-check rules found no definition line for `RootEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 15 defines `RootEntry`; if another line does, set the provenance `source_line` to it.

### GAP-017: Provenance line not verified for StoryEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** StoryEntry

**Issue:** the line-check rules found no definition line for `StoryEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 45 defines `StoryEntry`; if another line does, set the provenance `source_line` to it.

### GAP-018: Provenance line not verified for ThemesGlobals_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/types.ts:20
**Export:** ThemesGlobals_def

**Issue:** the line-check rules found no definition line for `ThemesGlobals_def` in `code/addons/themes/src/types.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/types.ts` and confirm that line 20 defines `ThemesGlobals_def`; if another line does, set the provenance `source_line` to it.

### GAP-019: Provenance line not verified for a11y_decorators

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:12
**Export:** a11y_decorators

**Issue:** the line-check rules found no definition line for `a11y_decorators` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 12 defines `a11y_decorators`; if another line does, set the provenance `source_line` to it.

### GAP-020: Provenance line not verified for a11y_initialGlobals

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:98
**Export:** a11y_initialGlobals

**Issue:** the line-check rules found no definition line for `a11y_initialGlobals` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 98 defines `a11y_initialGlobals`; if another line does, set the provenance `source_line` to it.

### GAP-021: Provenance line not verified for a11y_parameters

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:105
**Export:** a11y_parameters

**Issue:** the line-check rules found no definition line for `a11y_parameters` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 105 defines `a11y_parameters`; if another line does, set the provenance `source_line` to it.

### GAP-022: Provenance line not verified for fireEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:43
**Export:** fireEvent

**Issue:** the line-check rules found no definition line for `fireEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 43 defines `fireEvent`; if another line does, set the provenance `source_line` to it.

### GAP-023: Provenance line not verified for mockChannel_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:3
**Export:** mockChannel_def

**Issue:** the line-check rules found no definition line for `mockChannel_def` in `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts`; check by hand

**Remediation:** Open `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts` and confirm that line 3 defines `mockChannel_def`; if another line does, set the provenance `source_line` to it.

### GAP-024: Provenance line not verified for screen

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:107
**Export:** screen

**Issue:** the line-check rules found no definition line for `screen` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 107 defines `screen`; if another line does, set the provenance `source_line` to it.

### GAP-025: Provenance line not verified for userEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:123
**Export:** userEvent

**Issue:** the line-check rules found no definition line for `userEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 123 defines `userEvent`; if another line does, set the provenance `source_line` to it.

### GAP-026: Provenance line not verified for waitFor

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:108
**Export:** waitFor

**Issue:** the line-check rules found no definition line for `waitFor` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 108 defines `waitFor`; if another line does, set the provenance `source_line` to it.

### GAP-027: Provenance line not verified for withThemeByClassName

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByClassName

**Issue:** the line-check rules found no definition line for `withThemeByClassName` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByClassName`; if another line does, set the provenance `source_line` to it.

### GAP-028: Provenance line not verified for withThemeByClassName_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/class-name.decorator.tsx:19
**Export:** withThemeByClassName_exact

**Issue:** the line-check rules found no definition line for `withThemeByClassName_exact` in `code/addons/themes/src/decorators/class-name.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/class-name.decorator.tsx` and confirm that line 19 defines `withThemeByClassName_exact`; if another line does, set the provenance `source_line` to it.

### GAP-029: Provenance line not verified for withThemeByDataAttribute

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByDataAttribute

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByDataAttribute`; if another line does, set the provenance `source_line` to it.

### GAP-030: Provenance line not verified for withThemeByDataAttribute_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/data-attribute.decorator.tsx:19
**Export:** withThemeByDataAttribute_exact

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute_exact` in `code/addons/themes/src/decorators/data-attribute.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/data-attribute.decorator.tsx` and confirm that line 19 defines `withThemeByDataAttribute_exact`; if another line does, set the provenance `source_line` to it.

### GAP-031: Provenance line not verified for withThemeFromJSXProvider

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeFromJSXProvider

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeFromJSXProvider`; if another line does, set the provenance `source_line` to it.

### GAP-032: Provenance line not verified for withThemeFromJSXProvider_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:23
**Export:** withThemeFromJSXProvider_exact

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider_exact` in `code/addons/themes/src/decorators/provider.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/provider.decorator.tsx` and confirm that line 23 defines `withThemeFromJSXProvider_exact`; if another line does, set the provenance `source_line` to it.

### GAP-033: Provenance line not verified for within

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:110
**Export:** within

**Issue:** the line-check rules found no definition line for `within` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 110 defines `within`; if another line does, set the provenance `source_line` to it.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
