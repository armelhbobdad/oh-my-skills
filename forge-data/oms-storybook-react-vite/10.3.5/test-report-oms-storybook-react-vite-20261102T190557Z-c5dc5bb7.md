---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261102T190557Z-c5dc5bb7'
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
testDate: '2026-11-02T19:05:57Z'
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

**Mode Rationale:** metadata.json declares `skill_type: "single"`, so the skill is tested in naive mode: API-surface coverage, with a structural-only coherence check and no coherence category in the score.

**Analysis Plan:**
- Coverage Check: every public export in the provenance map / source surface at the pinned commit (e486d38, v10.3.5) checked for a documented entry in SKILL.md or references/, with AST-backed signature and type verification (Deep tier: ast-grep, gh, QMD, ccc available).
- Coherence Check: structural only (naive mode): internal reference links in SKILL.md resolve to existing references/ files and anchors; no cross-skill integration scoring.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces
**Denominator:** Stratified scope, denominator: scope.include union (1274 files matched, 985 exports union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: 216
- `scope.tier_a_include` union: absent
- `scope.include` union: 985    ← chosen (the barrel branch's set: `guards.deflation` fires, so the stored 216 is not used)
- exports-map subpath union: 1281
- root barrel: 54                               (secondary candidate: root-barrel-vs-subpath-union audit)

**Files Analyzed:** 319

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `A` | - | yes | - | code/core/src/components/components/typography/elements/A.tsx:7 | WARN |
| `A11Y_ADDON_ID` | const | yes | - | code/addons/a11y/src/constants.ts:1 | PASS |
| `A11Y_PANEL_ID` | const | yes | - | code/addons/a11y/src/constants.ts:2 | PASS |
| `A11yGlobals` | interface | yes | - | code/addons/a11y/src/types.ts:16 | PASS |
| `A11yParameters` | interface | yes | - | code/addons/a11y/src/params.ts:20 | PASS |
| `A11yReport` | type | yes | - | code/addons/a11y/src/types.ts:5 | PASS |
| `A11yTypes` | interface | yes | - | code/addons/a11y/src/types.ts:55 | PASS |
| `ADDON_ID` | const | yes | - | code/addons/vitest/src/constants.ts:11 | PASS |
| `ANGULAR_JSON_PATH` | const | no | - | code/core/src/cli/angular/helpers.ts:7 | WARN |
| `API` | type | no | - | code/core/src/manager-api/root.tsx:96 | WARN |
| `API_ActiveTabsType` | type | no | - | code/core/src/types/modules/api.ts:111 | WARN |
| `API_BaseEntry` | interface | no | - | code/core/src/types/modules/api-stories.ts:6 | WARN |
| `API_ComponentEntry` | interface | no | - | code/core/src/types/modules/api-stories.ts:27 | WARN |
| `API_ComposedRef` | interface | no | - | code/core/src/types/modules/api.ts:163 | WARN |
| `API_ComposedRefUpdate` | type | no | - | code/core/src/types/modules/api.ts:177 | WARN |
| `API_DocsEntry` | interface | no | - | code/core/src/types/modules/api-stories.ts:34 | WARN |
| `API_EventMap` | interface | yes | - | code/core/src/manager-api/root.tsx:318 | PASS |
| `API_FilterFunction` | type | no | - | code/core/src/types/modules/api-stories.ts:128 | WARN |
| `API_GroupEntry` | interface | no | - | code/core/src/types/modules/api-stories.ts:21 | WARN |
| `API_HashEntry` | type | no | - | code/core/src/types/modules/api-stories.ts:67 | WARN |
| `API_IframeRenderer` | type | no | - | code/core/src/types/modules/api.ts:57 | WARN |
| `API_IndexHash` | interface | no | - | code/core/src/types/modules/api-stories.ts:80 | WARN |
| `API_KeyCollection` | type | yes | - | code/core/src/manager-api/modules/shortcuts.ts:99 | PASS |
| `API_Layout` | interface | no | - | code/core/src/types/modules/api.ts:79 | WARN |
| `API_LayoutCustomisations` | interface | no | - | code/core/src/types/modules/api.ts:98 | WARN |
| `API_LeafEntry` | type | no | - | code/core/src/types/modules/api-stories.ts:66 | WARN |
| `API_LoadedRefData` | interface | no | - | code/core/src/types/modules/api.ts:156 | WARN |
| `API_MatchOptions` | interface | no | - | code/core/src/types/modules/api.ts:30 | WARN |
| `API_Notification` | interface | no | - | code/core/src/types/modules/api.ts:132 | WARN |
| `API_OptionsData` | type | no | - | code/core/src/types/modules/api-stories.ts:96 | WARN |
| `API_PanelPositions` | type | no | - | code/core/src/types/modules/api.ts:110 | WARN |
| `API_PreparedIndexEntry` | type | no | - | code/core/src/types/modules/api-stories.ts:85 | WARN |
| `API_PreparedStoryIndex` | interface | no | - | code/core/src/types/modules/api-stories.ts:91 | WARN |
| `API_Provider` | interface | no | - | code/core/src/types/modules/api.ts:44 | WARN |
| `API_ProviderData` | interface | no | - | code/core/src/types/modules/api.ts:39 | WARN |
| `API_RefId` | type | no | - | code/core/src/types/modules/api.ts:196 | WARN |
| `API_RefUrl` | type | no | - | code/core/src/types/modules/api.ts:197 | WARN |
| `API_Refs` | type | no | - | code/core/src/types/modules/api.ts:195 | WARN |
| `API_ReleaseNotes` | interface | no | - | code/core/src/types/modules/api-stories.ts:100 | WARN |
| `API_RenderOptions` | type | no | - | code/core/src/types/modules/api.ts:22 | WARN |
| `API_RootEntry` | interface | no | - | code/core/src/types/modules/api-stories.ts:15 | WARN |
| `API_RouteOptions` | interface | no | - | code/core/src/types/modules/api.ts:24 | WARN |
| `API_SetRefData` | type | no | - | code/core/src/types/modules/api.ts:147 | WARN |
| `API_Settings` | interface | no | - | code/core/src/types/modules/api-stories.ts:106 | WARN |
| `API_SidebarOptions` | interface | no | - | code/core/src/types/modules/api.ts:113 | WARN |
| `API_StateMerger` | type | no | - | code/core/src/types/modules/api.ts:37 | WARN |
| `API_StoryEntry` | interface | no | - | code/core/src/types/modules/api-stories.ts:45 | WARN |
| `API_StoryMapper` | type | no | - | code/core/src/types/modules/api.ts:154 | WARN |
| `API_TestEntry` | interface | no | - | code/core/src/types/modules/api-stories.ts:62 | WARN |
| `API_UI` | interface | no | - | code/core/src/types/modules/api.ts:104 | WARN |
| `API_UIOptions` | interface | no | - | code/core/src/types/modules/api.ts:66 | WARN |
| `API_UnknownEntries` | interface | no | - | code/core/src/types/modules/api-stories.ts:116 | WARN |
| `API_Version` | interface | no | - | code/core/src/types/modules/api-stories.ts:110 | WARN |
| `API_Versions` | interface | no | - | code/core/src/types/modules/api-stories.ts:122 | WARN |
| `API_ViewMode` | type | no | - | code/core/src/types/modules/api.ts:20 | WARN |
| `ActionBar` | - | yes | - | - | WARN |
| `ActionDisplay` | interface | yes | - | code/core/src/actions/models/ActionDisplay.ts:3 | PASS |
| `ActionList` | - | yes | - | - | WARN |
| `ActionOptions` | type | yes | - | code/core/src/actions/models/ActionOptions.ts:11 | PASS |
| `ActionsFunction` | interface | yes | - | code/core/src/actions/models/ActionsFunction.ts:4 | PASS |
| `ActionsMap` | type | yes | - | code/core/src/actions/models/ActionsMap.ts:3 | PASS |
| `ActionsTypes` | interface | no | - | code/core/src/actions/types.ts:51 | WARN |
| `ActiveTabs` | const | no | - | code/core/src/manager-api/root.tsx:78 | WARN |
| `Actor` | type | no | - | code/core/src/shared/universal-store/types.ts:11 | WARN |
| `AddContext` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:27 | WARN |
| `AddonPanel` | - | yes | - | code/core/src/components/components/addon-panel/addon-panel.tsx:36 | WARN |
| `AddonStore` | class | no | - | code/core/src/manager-api/lib/addons.ts:31 | WARN |
| `AddonTypes` | interface | no | - | code/core/src/csf/story.ts:187 | WARN |
| `AddonVitestCompatibilityOptions` | interface | no | - | code/core/src/cli/AddonVitestService.ts:23 | WARN |
| `AddonVitestPostinstallConfigUpdateError` | class | no | - | code/core/src/server-errors.ts:501 | WARN |
| `AddonVitestPostinstallError` | class | no | - | code/core/src/server-errors.ts:517 | WARN |
| `AddonVitestPostinstallFailedAddonA11yError` | class | no | - | code/core/src/server-errors.ts:473 | WARN |
| `AddonVitestPostinstallPrerequisiteCheckError` | class | no | - | code/core/src/server-errors.ts:460 | WARN |
| `AddonVitestPostinstallWorkspaceUpdateError` | class | no | - | code/core/src/server-errors.ts:485 | WARN |
| `AddonVitestService` | class | no | - | code/core/src/cli/AddonVitestService.ts:39 | WARN |
| `Addon_AddStoryArgs` | interface | no | - | code/core/src/types/modules/addons.ts:123 | WARN |
| `Addon_Annotations` | interface | no | - | code/core/src/types/modules/addons.ts:216 | WARN |
| `Addon_ArgType` | interface | no | - | code/core/src/types/modules/addons.ts:31 | WARN |
| `Addon_ArgsStoryFn` | type | no | - | code/core/src/types/modules/addons.ts:96 | WARN |
| `Addon_BaseAnnotations` | interface | no | - | code/core/src/types/modules/addons.ts:170 | WARN |
| `Addon_BaseDecorators` | type | no | - | code/core/src/types/modules/addons.ts:166 | WARN |
| `Addon_BaseMeta` | interface | no | - | code/core/src/types/modules/addons.ts:251 | WARN |
| `Addon_BaseStoryFn` | type | no | - | code/core/src/types/modules/addons.ts:312 | WARN |
| `Addon_BaseStoryObject` | type | no | - | code/core/src/types/modules/addons.ts:307 | WARN |
| `Addon_BaseType` | interface | no | - | code/core/src/types/modules/addons.ts:329 | WARN |
| `Addon_ClientApiAddon` | type | no | - | code/core/src/types/modules/addons.ts:131 | WARN |
| `Addon_ClientApiAddons` | interface | no | - | code/core/src/types/modules/addons.ts:135 | WARN |
| `Addon_ClientApiReturnFn` | type | no | - | code/core/src/types/modules/addons.ts:139 | WARN |
| `Addon_ClientStoryApi` | interface | no | - | code/core/src/types/modules/addons.ts:158 | WARN |
| `Addon_Collection` | interface | no | - | code/core/src/types/modules/addons.ts:470 | WARN |
| `Addon_Comparator` | type | no | - | code/core/src/types/modules/addons.ts:42 | WARN |
| `Addon_Config` | interface | no | - | code/core/src/types/modules/addons.ts:479 | WARN |
| `Addon_DecoratorFunction` | type | no | - | code/core/src/types/modules/addons.ts:103 | WARN |
| `Addon_Elements` | interface | no | - | code/core/src/types/modules/addons.ts:473 | WARN |
| `Addon_LegacyStoryFn` | type | no | - | code/core/src/types/modules/addons.ts:93 | WARN |
| `Addon_LoadFn` | type | no | - | code/core/src/types/modules/addons.ts:160 | WARN |
| `Addon_Loadable` | type | no | - | code/core/src/types/modules/addons.ts:162 | WARN |
| `Addon_Loader` | type | no | - | code/core/src/types/modules/addons.ts:465 | WARN |
| `Addon_LoaderFunction` | type | no | - | code/core/src/types/modules/addons.ts:106 | WARN |
| `Addon_Loaders` | interface | no | - | code/core/src/types/modules/addons.ts:467 | WARN |
| `Addon_MakeDecoratorResult` | type | no | - | code/core/src/types/modules/addons.ts:121 | WARN |
| `Addon_OptionsParameter` | interface | no | - | code/core/src/types/modules/addons.ts:63 | WARN |
| `Addon_OptionsParameterV7` | interface | no | - | code/core/src/types/modules/addons.ts:72 | WARN |
| `Addon_PageType` | interface | no | - | code/core/src/types/modules/addons.ts:393 | WARN |
| `Addon_PartialStoryFn` | type | no | - | code/core/src/types/modules/addons.ts:90 | WARN |
| `Addon_RenderOptions` | interface | no | - | code/core/src/types/modules/addons.ts:320 | WARN |
| `Addon_RequireContext` | type | no | - | code/core/src/types/modules/addons.ts:161 | WARN |
| `Addon_StoryApi` | interface | no | - | code/core/src/types/modules/addons.ts:143 | WARN |
| `Addon_StoryContext` | type | no | - | code/core/src/types/modules/addons.ts:81 | WARN |
| `Addon_StoryContextUpdate` | type | no | - | code/core/src/types/modules/addons.ts:83 | WARN |
| `Addon_StoryFn` | type | no | - | code/core/src/types/modules/addons.ts:99 | WARN |
| `Addon_StorySortComparator` | type | no | - | code/core/src/types/modules/addons.ts:54 | WARN |
| `Addon_StorySortComparatorV7` | type | no | - | code/core/src/types/modules/addons.ts:56 | WARN |
| `Addon_StorySortMethod` | type | no | - | code/core/src/types/modules/addons.ts:43 | WARN |
| `Addon_StorySortObjectParameter` | interface | no | - | code/core/src/types/modules/addons.ts:44 | WARN |
| `Addon_StorySortParameter` | type | no | - | code/core/src/types/modules/addons.ts:55 | WARN |
| `Addon_StorySortParameterV7` | type | no | - | code/core/src/types/modules/addons.ts:57 | WARN |
| `Addon_StoryWrapper` | type | no | - | code/core/src/types/modules/addons.ts:115 | WARN |
| `Addon_TestProviderType` | interface | no | - | code/core/src/types/modules/addons.ts:444 | WARN |
| `Addon_ToolbarConfig` | interface | no | - | code/core/src/types/modules/addons.ts:476 | WARN |
| `Addon_Type` | type | no | - | code/core/src/types/modules/addons.ts:324 | WARN |
| `Addon_Types` | type | no | - | code/core/src/types/modules/addons.ts:26 | WARN |
| `Addon_TypesEnum` | enum | no | - | code/core/src/types/modules/addons.ts:493 | WARN |
| `Addon_TypesMapping` | interface | no | - | code/core/src/types/modules/addons.ts:459 | WARN |
| `Addon_WrapperSettings` | interface | no | - | code/core/src/types/modules/addons.ts:108 | WARN |
| `Addon_WrapperType` | interface | no | - | code/core/src/types/modules/addons.ts:425 | WARN |
| `Addons_ArgTypes` | type | no | - | code/core/src/types/modules/addons.ts:35 | WARN |
| `AfterEach` | type | no | - | code/core/src/csf/story.ts:262 | WARN |
| `Anchor` | function | yes | yes | code/addons/docs/src/blocks/blocks/Anchor.tsx:10 | PASS |
| `AnchorMdx` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:98 | WARN |
| `AnchorProps` | interface | no | - | code/addons/docs/src/blocks/blocks/Anchor.tsx:6 | WARN |
| `AngularJSON` | class | no | - | code/core/src/cli/angular/helpers.ts:9 | WARN |
| `AngularLegacyBuildOptionsError` | class | no | - | code/core/src/server-errors.ts:241 | WARN |
| `Animation` | type | yes | - | code/core/src/theming/types.ts:60 | PASS |
| `AnnotatedStoryFn` | type | no | - | code/core/src/csf/story.ts:575 | WARN |
| `AnyFramework` | type | no | - | code/core/src/csf/story.ts:217 | WARN |
| `ArgTypes` | const | yes | yes | code/addons/docs/src/blocks/blocks/ArgTypes.tsx:108 | PASS |
| `ArgTypesEnhancer` | type | no | - | code/core/src/csf/story.ts:233 | WARN |
| `ArgTypesExtractor` | type | no | - | code/core/src/docs-tools/argTypes/docgen/types.ts:8 | WARN |
| `ArgTypesRequestPayload` | interface | no | - | code/core/src/core-events/data/argtypes-info.ts:3 | WARN |
| `ArgTypesResponsePayload` | interface | no | - | code/core/src/core-events/data/argtypes-info.ts:7 | WARN |
| `Args` | interface | yes | - | code/core/src/csf/story.ts:153 | PASS |
| `ArgsEnhancer` | type | no | - | code/core/src/csf/story.ts:230 | WARN |
| `ArgsFromMeta` | type | no | - | code/core/src/csf/story.ts:585 | WARN |
| `ArgsStoryFn` | type | no | - | code/core/src/csf/story.ts:321 | WARN |
| `AutomigrateError` | class | no | - | code/core/src/server-errors.ts:656 | WARN |
| `BabelFile` | - | yes | - | - | WARN |
| `Background` | type | yes | - | code/core/src/theming/types.ts:58 | PASS |
| `BackgroundTypes` | interface | no | - | code/core/src/backgrounds/types.ts:56 | WARN |
| `BackgroundsGlobals` | interface | no | - | code/core/src/backgrounds/types.ts:47 | WARN |
| `Badge` | - | yes | - | code/core/src/components/components/Badge/Badge.tsx:88 | WARN |
| `Bar` | - | yes | - | - | WARN |
| `BaseAnnotations` | interface | no | - | code/core/src/csf/story.ts:347 | WARN |
| `BaseIndexEntry` | interface | no | - | code/core/src/types/modules/indexer.ts:67 | WARN |
| `BaseIndexInput` | type | no | - | code/core/src/types/modules/indexer.ts:105 | WARN |
| `BaseProjectAnnotations` | - | yes | - | - | WARN |
| `BaseStory` | type | no | - | code/core/src/types/modules/addons.ts:316 | WARN |
| `BeforeAll` | type | no | - | code/core/src/csf/story.ts:256 | WARN |
| `BeforeEach` | type | no | - | code/core/src/csf/story.ts:258 | WARN |
| `Blockquote` | - | yes | - | - | WARN |
| `BooleanConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:14 | PASS |
| `BooleanControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Boolean.tsx:117 | PASS |
| `BooleanProps` | type | yes | - | code/addons/docs/src/blocks/controls/Boolean.tsx:104 | PASS |
| `BooleanValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:13 | PASS |
| `BoundStory` | type | no | - | code/core/src/types/modules/story.ts:124 | WARN |
| `Brand` | interface | yes | - | code/core/src/theming/types.ts:64 | PASS |
| `Builder` | interface | no | - | code/core/src/types/modules/core-common.ts:259 | WARN |
| `BuilderName` | type | no | - | code/core/src/types/modules/core-common.ts:20 | WARN |
| `BuilderOptions` | type | yes | - | code/builders/builder-vite/src/types.ts:21 | PASS |
| `BuilderResult` | interface | no | - | code/core/src/types/modules/core-common.ts:156 | WARN |
| `BuilderStats` | interface | no | - | code/core/src/types/modules/builder.ts:1 | WARN |
| `Builder_EnvsRaw` | type | no | - | code/core/src/types/modules/builder.ts:12 | WARN |
| `Builder_Unpromise` | type | no | - | code/core/src/types/modules/builder.ts:10 | WARN |
| `Builder_WithRequiredProperty` | type | no | - | code/core/src/types/modules/builder.ts:6 | WARN |
| `Button` | - | yes | - | code/core/src/components/components/Button/Button.tsx:53 | WARN |
| `CHANNEL_CREATED` | - | yes | - | - | WARN |
| `CLEAR_ID` | const | no | - | code/core/src/actions/constants.ts:5 | WARN |
| `CLIBaseOptions` | interface | no | - | code/core/src/types/modules/core-common.ts:175 | WARN |
| `CLIOptions` | interface | no | - | code/core/src/types/modules/core-common.ts:184 | WARN |
| `COMPONENT_TESTING_PANEL_ID` | const | yes | - | code/core/src/component-testing/constants.ts:2 | PASS |
| `COVERAGE_DIRECTORY` | const | no | - | code/addons/vitest/src/constants.ts:19 | WARN |
| `CSFFile` | type | yes | - | code/core/src/types/modules/story.ts:92 | PASS |
| `CSSObject` | - | yes | - | - | WARN |
| `CYCLIC_KEY` | const | no | - | code/core/src/actions/constants.ts:6 | WARN |
| `CacheProvider` | - | yes | - | - | WARN |
| `Call` | interface | no | - | code/core/src/instrumenter/types.ts:7 | WARN |
| `CallRef` | interface | no | - | code/core/src/instrumenter/types.ts:37 | WARN |
| `CallStates` | enum | no | - | code/core/src/instrumenter/types.ts:30 | WARN |
| `CalledExtractOnStoreError` | class | yes | - | code/core/src/preview-errors.ts:77 | PASS |
| `CalledPreviewMethodBeforeInitializationError` | class | yes | - | code/core/src/preview-errors.ts:107 | PASS |
| `Canvas` | const | yes | yes | code/addons/docs/src/blocks/blocks/Canvas.tsx:100 | PASS |
| `Card` | - | yes | - | code/core/src/components/components/Card/Card.tsx:98 | WARN |
| `Category` | enum | yes | - | code/core/src/manager-errors.ts:12 | PASS |
| `Channel` | - | yes | - | - | WARN |
| `CheckboxControl` | - | yes | - | - | WARN |
| `ClassNameStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/class-name.decorator.tsx:8 | PASS |
| `ClassNames` | - | yes | - | - | WARN |
| `CleanupCallback` | type | no | - | code/core/src/csf/story.ts:254 | WARN |
| `ClickEventDetails` | interface | yes | - | code/core/src/highlight/types.ts:60 | PASS |
| `Code` | - | yes | - | code/core/src/components/components/typography/elements/Code.tsx:42 | WARN |
| `CodeOrSourceMdx` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:39 | WARN |
| `Collapsible` | - | yes | - | - | WARN |
| `Color` | type | yes | - | code/core/src/theming/types.ts:57 | PASS |
| `ColorConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:18 | PASS |
| `ColorControl` | function | yes | yes | code/addons/docs/src/blocks/controls/index.tsx:14 | PASS |
| `ColorControlProps` | - | yes | - | - | WARN |
| `ColorItem` | function | yes | yes | code/addons/docs/src/blocks/components/ColorPalette.tsx:182 | PASS |
| `ColorPalette` | function | yes | yes | code/addons/docs/src/blocks/components/ColorPalette.tsx:202 | PASS |
| `ColorProps` | type | no | - | code/addons/docs/src/blocks/controls/index.tsx:10 | WARN |
| `ColorValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:16 | PASS |
| `Combo` | interface | yes | - | code/core/src/manager-api/root.tsx:116 | PASS |
| `CommonJsConfigNotSupportedError` | class | no | - | code/core/src/server-errors.ts:639 | WARN |
| `CompatibleString` | type | no | - | code/core/src/types/modules/core-common.ts:739 | WARN |
| `CompileOptions` | interface | no | - | code/addons/docs/src/mdx-loader.ts:7 | WARN |
| `Component` | type | no | - | code/addons/docs/src/blocks/blocks/types.ts:7 | WARN |
| `ComponentAnnotations` | interface | yes | - | code/core/src/csf/story.ts:452 | PASS |
| `ComponentEntry` | - | yes | - | - | WARN |
| `ComponentId` | type | no | - | code/core/src/csf/story.ts:9 | WARN |
| `ComponentManifest` | interface | no | - | code/core/src/types/modules/core-common.ts:357 | WARN |
| `ComponentTitle` | type | no | - | code/core/src/csf/story.ts:10 | WARN |
| `ComponentsManifest` | interface | no | - | code/core/src/types/modules/core-common.ts:375 | WARN |
| `ComposeStoryFn` | interface | no | - | code/core/src/types/modules/composedStory.ts:76 | WARN |
| `ComposedStoryFn` | type | no | - | code/core/src/types/modules/composedStory.ts:40 | WARN |
| `Conditional` | type | no | - | code/core/src/csf/story.ts:58 | WARN |
| `ConfigFile` | - | yes | - | - | WARN |
| `ConflictingStaticDirConfigError` | class | no | - | code/core/src/server-errors.ts:120 | WARN |
| `Consumer` | function | no | - | code/core/src/manager-api/root.tsx:316 | WARN |
| `ContextObjectWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:6 | PASS |
| `ContextSpecWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:16 | PASS |
| `Control` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:82 | PASS |
| `ControlProps` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:3 | PASS |
| `ControlStates` | interface | no | - | code/core/src/instrumenter/types.ts:51 | WARN |
| `ControlType` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:71 | PASS |
| `Controls` | const | yes | yes | code/addons/docs/src/blocks/blocks/Controls.tsx:109 | PASS |
| `ControlsTypes` | interface | no | - | code/core/src/controls/types.ts:55 | WARN |
| `CoreCommon_AddonEntry` | type | no | - | code/core/src/types/modules/core-common.ts:706 | WARN |
| `CoreCommon_AddonInfo` | type | no | - | code/core/src/types/modules/core-common.ts:707 | WARN |
| `CoreCommon_OptionsEntry` | type | no | - | code/core/src/types/modules/core-common.ts:705 | WARN |
| `CoreCommon_ResolvedAddonPreset` | interface | no | - | code/core/src/types/modules/core-common.ts:690 | WARN |
| `CoreCommon_ResolvedAddonVirtual` | interface | no | - | code/core/src/types/modules/core-common.ts:697 | WARN |
| `CoreCommon_StorybookInfo` | interface | no | - | code/core/src/types/modules/core-common.ts:709 | WARN |
| `CoreConfig` | interface | no | - | code/core/src/types/modules/core-common.ts:23 | WARN |
| `CoreTypes` | type | no | - | code/core/src/csf/core-annotations.ts:23 | WARN |
| `CoreWebpackCompiler` | enum | no | - | code/core/src/types/modules/webpack.ts:1 | WARN |
| `CouldNotEvaluateFrameworkError` | class | no | - | code/core/src/server-errors.ts:103 | WARN |
| `CreateNewStoryErrorPayload` | type | no | - | code/core/src/core-events/data/create-new-story.ts:21 | WARN |
| `CreateNewStoryRequestPayload` | interface | no | - | code/core/src/core-events/data/create-new-story.ts:1 | WARN |
| `CreateNewStoryResponsePayload` | interface | no | - | code/core/src/core-events/data/create-new-story.ts:12 | WARN |
| `CriticalPresetLoadError` | class | no | - | code/core/src/server-errors.ts:260 | WARN |
| `CsfEnricher` | type | no | - | code/core/src/types/modules/core-common.ts:388 | WARN |
| `CsfFile` | - | yes | - | - | WARN |
| `DEFAULT_FILES_PATTERN` | const | no | - | code/core/src/common/utils/normalize-stories.ts:15 | WARN |
| `DEFAULT_VIEWPORT` | const | no | - | code/core/src/viewport/defaults.ts:232 | WARN |
| `DL` | - | yes | - | - | WARN |
| `DOCUMENTATION_FATAL_ERROR_LINK` | const | no | - | code/addons/vitest/src/constants.ts:17 | WARN |
| `DOCUMENTATION_LINK` | const | no | - | code/addons/vitest/src/constants.ts:16 | WARN |
| `DataAttributeStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/data-attribute.decorator.tsx:8 | PASS |
| `DateConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:29 | PASS |
| `DateControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:69 | PASS |
| `DateProps` | type | yes | - | code/addons/docs/src/blocks/controls/Date.tsx:68 | PASS |
| `DateValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:28 | PASS |
| `Decorator` | - | yes | - | code/frameworks/angular/src/client/public-types.ts:50 | WARN |
| `DecoratorApplicator` | type | no | - | code/core/src/csf/story.ts:336 | WARN |
| `DecoratorFunction` | type | yes | - | code/core/src/actions/models/DecoratorFunction.ts:1 | PASS |
| `DecoratorHelpers` | - | yes | - | - | WARN |
| `Description` | const | yes | no | code/addons/docs/src/blocks/blocks/Description.tsx:74 | FAIL |
| `DescriptionType` | enum | no | - | code/addons/docs/src/blocks/blocks/Description.tsx:9 | WARN |
| `Div` | - | yes | - | - | WARN |
| `DocgenFlowType` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/types.ts:23 | WARN |
| `DocgenInfo` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/types.ts:42 | WARN |
| `DocgenPropDefaultValue` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/types.ts:36 | WARN |
| `DocgenPropType` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/types.ts:17 | WARN |
| `DocgenType` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/types.ts:10 | WARN |
| `DocgenTypeScriptType` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/types.ts:30 | WARN |
| `Docs` | function | yes | no | code/addons/docs/src/blocks/blocks/Docs.tsx:17 | FAIL |
| `DocsContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:23 | PASS |
| `DocsContainerProps` | interface | no | - | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18 | WARN |
| `DocsContext` | class | yes | - | code/core/src/preview-api/modules/preview-web/docs-context/DocsContext.ts:20 | PASS |
| `DocsEntry` | - | yes | - | - | WARN |
| `DocsIndexEntry` | type | no | - | code/core/src/types/modules/indexer.ts:83 | WARN |
| `DocsIndexInput` | type | no | - | code/core/src/types/modules/indexer.ts:145 | WARN |
| `DocsOptions` | type | no | - | code/core/src/types/modules/core-common.ts:313 | WARN |
| `DocsPage` | function | yes | - | code/addons/docs/src/blocks/blocks/DocsPage.tsx:12 | PASS |
| `DocsPreparedPayload` | interface | no | - | code/core/src/types/modules/channelApi.ts:75 | WARN |
| `DocsProps` | type | no | - | code/addons/docs/src/blocks/blocks/Docs.tsx:12 | WARN |
| `DocsRenderFunction` | type | no | - | code/core/src/types/modules/docs.ts:109 | WARN |
| `DocsRenderer` | class | yes | - | code/addons/docs/src/DocsRenderer.tsx:48 | PASS |
| `DocsStory` | const | yes | yes | code/addons/docs/src/blocks/blocks/DocsStory.tsx:42 | PASS |
| `DocsStoryProps` | type | no | - | code/addons/docs/src/blocks/blocks/types.ts:9 | WARN |
| `DocsTypes` | interface | yes | - | code/addons/docs/src/types.ts:254 | PASS |
| `EVENTS` | const | no | - | code/core/src/instrumenter/EVENTS.ts:1 | WARN |
| `EVENT_ID` | const | no | - | code/core/src/actions/constants.ts:4 | WARN |
| `Easing` | type | no | - | code/core/src/theming/types.ts:61 | WARN |
| `ElementA11yParameterError` | class | no | - | code/core/src/preview-errors.ts:385 | WARN |
| `ElementRef` | interface | no | - | code/core/src/instrumenter/types.ts:41 | WARN |
| `EmptyIndexError` | class | yes | - | code/core/src/preview-errors.ts:161 | PASS |
| `Entry` | type | no | - | code/core/src/types/modules/core-common.ts:306 | WARN |
| `ErrorFormatter` | - | yes | - | - | WARN |
| `Event` | type | no | - | code/core/src/shared/universal-store/types.ts:58 | WARN |
| `EventInfo` | type | no | - | code/core/src/shared/universal-store/types.ts:16 | WARN |
| `ExecuteCommandOptions` | type | no | - | code/core/src/common/utils/command.ts:19 | WARN |
| `ExternalDocs` | function | no | - | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26 | WARN |
| `ExternalDocsContainer` | function | no | - | code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12 | WARN |
| `ExternalDocsProps` | type | no | - | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11 | WARN |
| `ExtractProps` | type | no | - | code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:17 | WARN |
| `ExtractedJsDoc` | interface | no | - | code/core/src/docs-tools/argTypes/jsdocParser.ts:23 | WARN |
| `ExtractedJsDocParam` | interface | no | - | code/core/src/docs-tools/argTypes/jsdocParser.ts:12 | WARN |
| `ExtractedJsDocReturns` | interface | no | - | code/core/src/docs-tools/argTypes/jsdocParser.ts:18 | WARN |
| `ExtractedProp` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:10 | WARN |
| `FULL_RUN_TRIGGERS` | const | yes | - | code/addons/vitest/src/constants.ts:61 | PASS |
| `Feature` | enum | no | - | code/core/src/types/modules/features.ts:1 | WARN |
| `FileComponentSearchRequestPayload` | interface | no | - | code/core/src/core-events/data/file-component-search.ts:1 | WARN |
| `FileComponentSearchResponsePayload` | interface | no | - | code/core/src/core-events/data/file-component-search.ts:3 | WARN |
| `FileOptions` | type | no | - | code/core/src/common/utils/cli.ts:24 | WARN |
| `FileSystemCache` | class | no | - | code/core/src/common/utils/file-cache.ts:29 | WARN |
| `FilesControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Files.tsx:40 | PASS |
| `FilesControlProps` | interface | yes | - | code/addons/docs/src/blocks/controls/Files.tsx:11 | PASS |
| `FilterFunction` | type | no | - | code/core/src/types/modules/api.ts:77 | WARN |
| `FindPackageVersionsError` | class | no | - | code/core/src/server-errors.ts:580 | WARN |
| `FlexBar` | - | yes | - | - | WARN |
| `Form` | - | yes | - | code/core/src/components/components/Form/Form.tsx:11 | WARN |
| `FrameworkOptions` | - | yes | - | code/frameworks/angular/src/types.ts:16 | WARN |
| `FunctionInterpolation` | type | yes | - | code/core/src/theming/index.ts:26 | PASS |
| `GLOBALS_UPDATED` | - | yes | - | - | WARN |
| `GenerateNewProjectOnInitError` | class | no | - | code/core/src/server-errors.ts:441 | WARN |
| `Global` | - | yes | - | - | WARN |
| `GlobalState` | type | yes | - | code/core/src/viewport/types.ts:16 | PASS |
| `GlobalStateUpdate` | type | no | - | code/core/src/viewport/types.ts:31 | WARN |
| `GlobalTypes` | interface | no | - | code/core/src/csf/story.ts:168 | WARN |
| `Globals` | interface | yes | - | code/core/src/csf/story.ts:165 | PASS |
| `GlobalsUpdatedPayload` | interface | no | - | code/core/src/types/modules/channelApi.ts:60 | WARN |
| `GoogleFontsDownloadError` | class | no | - | code/core/src/server-errors.ts:305 | WARN |
| `GoogleFontsLoadingError` | class | no | - | code/core/src/server-errors.ts:319 | WARN |
| `GroupEntry` | - | yes | - | - | WARN |
| `H1` | - | yes | - | - | WARN |
| `H6` | - | yes | - | - | WARN |
| `HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:3 | PASS |
| `HR` | - | yes | - | - | WARN |
| `HandledError` | class | no | - | code/core/src/common/utils/HandledError.ts:1 | WARN |
| `HandlerFunction` | type | yes | - | code/core/src/actions/models/HandlerFunction.ts:1 | PASS |
| `HashEntry` | - | yes | - | - | WARN |
| `HeaderMdx` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:215 | WARN |
| `HeadersMdx` | const | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:232 | WARN |
| `Heading` | const | yes | yes | code/addons/docs/src/blocks/blocks/Heading.tsx:33 | PASS |
| `HeadingProps` | interface | no | - | code/addons/docs/src/blocks/blocks/Heading.tsx:11 | WARN |
| `HighlightMenuItem` | interface | yes | - | code/core/src/highlight/types.ts:24 | PASS |
| `HighlightOptions` | interface | yes | - | code/core/src/highlight/types.ts:41 | PASS |
| `HighlightTypes` | interface | no | - | code/core/src/highlight/types.ts:3 | WARN |
| `HooksContext` | class | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:36 | PASS |
| `INITIAL_VIEWPORTS` | const | no | - | code/core/src/viewport/defaults.ts:3 | WARN |
| `INTERNAL_DEFAULT_PROJECT_ANNOTATIONS` | const | yes | - | code/renderers/react/src/portable-stories.tsx:58 | PASS |
| `IconButton` | - | yes | - | code/core/src/components/components/Button/Button.tsx:327 | WARN |
| `IconGallery` | function | yes | yes | code/addons/docs/src/blocks/components/IconGallery.tsx:74 | PASS |
| `IconItem` | function | yes | yes | code/addons/docs/src/blocks/components/IconGallery.tsx:62 | PASS |
| `ImplicitActionsDuringRendering` | class | yes | - | code/core/src/preview-errors.ts:56 | PASS |
| `IncludeExcludeOptions` | interface | yes | - | code/core/src/csf/index.ts:38 | PASS |
| `IncompatiblePostCssConfigError` | class | no | - | code/core/src/server-errors.ts:595 | WARN |
| `IndexEntry` | type | no | - | code/core/src/types/modules/indexer.ts:88 | WARN |
| `IndexEntryLegacy` | type | no | - | code/core/src/types/modules/addons.ts:53 | WARN |
| `IndexHash` | - | yes | - | - | WARN |
| `IndexInput` | type | no | - | code/core/src/types/modules/indexer.ts:151 | WARN |
| `IndexInputStats` | interface | no | - | code/core/src/types/modules/indexer.ts:90 | WARN |
| `IndexedCSFFile` | interface | no | - | code/core/src/types/modules/indexer.ts:38 | WARN |
| `IndexedStory` | interface | no | - | code/core/src/types/modules/indexer.ts:32 | WARN |
| `Indexer` | type | no | - | code/core/src/types/modules/indexer.ts:56 | WARN |
| `IndexerOptions` | interface | no | - | code/core/src/types/modules/indexer.ts:28 | WARN |
| `InferTypes` | type | no | - | code/core/src/csf/csf-factories.ts:41 | WARN |
| `InitialViewportKeys` | type | yes | - | code/core/src/viewport/defaults.ts:230 | PASS |
| `InputType` | interface | no | - | code/core/src/csf/story.ts:111 | WARN |
| `InstallationMetadata` | type | no | - | code/core/src/common/js-package-manager/types.ts:2 | WARN |
| `InterPresetOptions` | type | no | - | code/core/src/common/presets.ts:24 | WARN |
| `Interpolation` | type | yes | - | code/core/src/theming/index.ts:27 | PASS |
| `InvalidFrameworkNameError` | class | yes | - | code/core/src/server-errors.ts:86 | PASS |
| `InvalidStoriesEntryError` | class | no | - | code/core/src/server-errors.ts:138 | WARN |
| `JsDocParam` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/PropDef.ts:3 | WARN |
| `JsDocParsingOptions` | interface | no | - | code/core/src/docs-tools/argTypes/jsdocParser.ts:30 | WARN |
| `JsDocParsingResult` | interface | no | - | code/core/src/docs-tools/argTypes/jsdocParser.ts:34 | WARN |
| `JsDocReturns` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/PropDef.ts:8 | WARN |
| `JsDocTags` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/PropDef.ts:12 | WARN |
| `JsPackageManager` | class | no | - | code/core/src/common/js-package-manager/JsPackageManager.ts:70 | WARN |
| `JsPackageManagerFactory` | class | no | - | code/core/src/common/js-package-manager/JsPackageManagerFactory.ts:29 | WARN |
| `KeyboardEventLike` | type | no | - | code/core/src/manager-api/lib/shortcut.ts:14 | WARN |
| `Keyframes` | - | yes | - | - | WARN |
| `LI` | - | yes | - | - | WARN |
| `LeafEntry` | - | yes | - | - | WARN |
| `LegacyAnnotatedStoryFn` | type | no | - | code/core/src/csf/story.ts:565 | WARN |
| `LegacyStoryAnnotationsOrFn` | type | no | - | code/core/src/csf/story.ts:571 | WARN |
| `LegacyStoryFn` | type | no | - | code/core/src/csf/story.ts:316 | WARN |
| `LoadOptions` | interface | no | - | code/core/src/types/modules/core-common.ts:165 | WARN |
| `LoadedPreset` | interface | no | - | code/core/src/types/modules/core-common.ts:122 | WARN |
| `Loader` | - | yes | - | code/core/src/components/components/Loader/Loader.tsx:109 | WARN |
| `LoaderFunction` | type | yes | - | code/core/src/csf/story.ts:249 | PASS |
| `LogItem` | interface | no | - | code/core/src/instrumenter/types.ts:60 | WARN |
| `MAX_DEFAULT_VALUE_SUMMARY_LENGTH` | const | no | - | code/core/src/docs-tools/argTypes/utils.ts:4 | WARN |
| `MAX_TYPE_SUMMARY_LENGTH` | const | no | - | code/core/src/docs-tools/argTypes/utils.ts:3 | WARN |
| `MINIMAL_VIEWPORTS` | const | no | - | code/core/src/viewport/defaults.ts:234 | WARN |
| `MainFileEvaluationError` | class | no | - | code/core/src/server-errors.ts:402 | WARN |
| `MainFileMissingError` | class | no | - | code/core/src/server-errors.ts:372 | WARN |
| `ManagerContext` | const | yes | - | code/core/src/manager-api/root.tsx:80 | PASS |
| `ManagerProviderProps` | type | yes | - | code/core/src/manager-api/root.tsx:121 | PASS |
| `Manifests` | type | no | - | code/core/src/types/modules/core-common.ts:386 | WARN |
| `Markdown` | const | yes | yes | code/addons/docs/src/blocks/blocks/Markdown.tsx:55 | PASS |
| `MaybeMocked` | - | yes | - | - | WARN |
| `MdxCompileOptions` | type | no | - | code/addons/docs/src/mdx-loader.ts:5 | WARN |
| `MdxFileWithNoCsfReferencesError` | class | yes | - | code/core/src/preview-errors.ts:145 | PASS |
| `MeasureTypes` | interface | no | - | code/core/src/measure/types.ts:18 | WARN |
| `Meta` | function | yes | yes | code/addons/docs/src/blocks/blocks/Meta.tsx:15 | PASS |
| `Middleware` | type | no | - | code/core/src/types/modules/core-common.ts:236 | WARN |
| `MissingAngularJsonError` | class | no | - | code/core/src/server-errors.ts:223 | WARN |
| `MissingBuilderError` | class | no | - | code/core/src/server-errors.ts:284 | WARN |
| `MissingFrameworkFieldError` | class | yes | - | code/core/src/server-errors.ts:70 | PASS |
| `MissingRenderToCanvasError` | class | yes | - | code/core/src/preview-errors.ts:91 | PASS |
| `MissingStoryAfterHmrError` | class | yes | - | code/core/src/preview-errors.ts:39 | PASS |
| `MissingStoryFromCsfFileError` | class | yes | - | code/core/src/preview-errors.ts:192 | PASS |
| `Mock` | - | yes | - | - | WARN |
| `MockCall` | type | no | - | code/core/src/mocking-utils/extract.ts:21 | WARN |
| `MockInstance` | - | yes | - | - | WARN |
| `MockUniversalStore` | class | yes | - | code/core/src/shared/universal-store/mock.ts:40 | PASS |
| `Modal` | - | yes | - | code/core/src/components/components/Modal/Modal.tsx:242 | WARN |
| `ModuleExport` | type | no | - | code/core/src/types/modules/story.ts:32 | WARN |
| `ModuleExports` | type | no | - | code/core/src/types/modules/story.ts:33 | WARN |
| `ModuleImportFn` | type | no | - | code/core/src/types/modules/story.ts:34 | WARN |
| `ModuleMockerInterceptor` | class | no | - | code/core/src/mocking-utils/mocker-runtime.js:5 | WARN |
| `MountMustBeDestructuredError` | class | yes | - | code/core/src/preview-errors.ts:226 | PASS |
| `NamedOrDefaultProjectAnnotations` | type | no | - | code/core/src/types/modules/story.ts:52 | WARN |
| `NextJsSharpError` | class | no | - | code/core/src/preview-errors.ts:315 | WARN |
| `NextjsRouterMocksNotAvailable` | class | no | - | code/core/src/preview-errors.ts:332 | WARN |
| `NoMatchingExportError` | class | no | - | code/core/src/server-errors.ts:350 | WARN |
| `NoRenderFunctionError` | class | yes | - | code/core/src/preview-errors.ts:256 | PASS |
| `NoStatsForViteDevError` | class | no | - | code/core/src/server-errors.ts:566 | WARN |
| `NoStoryMatchError` | class | yes | - | code/core/src/preview-errors.ts:176 | PASS |
| `NoStoryMountedError` | class | yes | - | code/core/src/preview-errors.ts:269 | PASS |
| `Node` | type | no | - | code/core/src/mocking-utils/esmWalker.ts:44 | WARN |
| `NodePath` | - | yes | - | - | WARN |
| `NormalizedComponentAnnotations` | type | yes | - | code/core/src/types/modules/story.ts:66 | PASS |
| `NormalizedOptionsConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:62 | PASS |
| `NormalizedProjectAnnotations` | type | yes | - | code/core/src/types/modules/story.ts:55 | PASS |
| `NormalizedStoriesSpecifier` | type | no | - | code/core/src/types/modules/indexer.ts:20 | WARN |
| `NormalizedStoryAnnotations` | type | yes | - | code/core/src/types/modules/story.ts:78 | PASS |
| `NpmOptions` | type | no | - | code/core/src/cli/NpmOptions.ts:3 | WARN |
| `NumberConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:32 | PASS |
| `NumberControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:28 | PASS |
| `NumberValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:31 | PASS |
| `NxProjectDetectedError` | class | yes | - | code/core/src/server-errors.ts:56 | PASS |
| `OL` | - | yes | - | - | WARN |
| `ObjectConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:41 | PASS |
| `ObjectControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Object.tsx:166 | PASS |
| `ObjectProps` | type | yes | - | code/addons/docs/src/blocks/controls/Object.tsx:164 | PASS |
| `ObjectValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:40 | PASS |
| `Of` | type | no | - | code/addons/docs/src/blocks/blocks/useOf.ts:11 | WARN |
| `OpenInEditorRequestPayload` | type | no | - | code/core/src/core-events/data/open-in-editor.ts:1 | WARN |
| `OpenInEditorResponsePayload` | type | no | - | code/core/src/core-events/data/open-in-editor.ts:3 | WARN |
| `Options` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:48 | PASS |
| `OptionsArray` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:46 | PASS |
| `OptionsConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:57 | PASS |
| `OptionsControl` | function | yes | yes | code/addons/docs/src/blocks/controls/options/Options.tsx:41 | PASS |
| `OptionsControlType` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:49 | PASS |
| `OptionsMultiSelection` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:44 | PASS |
| `OptionsObject` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:47 | PASS |
| `OptionsProps` | type | yes | - | code/addons/docs/src/blocks/controls/options/Options.tsx:40 | PASS |
| `OptionsSelection` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:45 | PASS |
| `OptionsSingleSelection` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:43 | PASS |
| `OutlineTypes` | interface | no | - | code/core/src/outline/types.ts:18 | WARN |
| `P` | - | yes | - | - | WARN |
| `PANEL_ID` | const | no | - | code/core/src/actions/constants.ts:3 | WARN |
| `PARAM_KEY` | const | yes | - | code/addons/a11y/src/constants.ts:3 | PASS |
| `PREVIEW_INITIALIZED` | - | yes | - | - | WARN |
| `PRIMARY_STORY` | const | no | - | code/addons/docs/src/blocks/blocks/types.ts:3 | WARN |
| `PackageJsonInfo` | type | no | - | code/core/src/common/js-package-manager/JsPackageManager.ts:64 | WARN |
| `PackageJsonWithDepsAndDevDeps` | type | no | - | code/core/src/common/js-package-manager/PackageJson.ts:3 | WARN |
| `PackageJsonWithMaybeDeps` | type | no | - | code/core/src/common/js-package-manager/PackageJson.ts:6 | WARN |
| `PackageManagerName` | enum | no | - | code/core/src/common/js-package-manager/JsPackageManager.ts:23 | WARN |
| `PackageMetadata` | type | no | - | code/core/src/common/js-package-manager/types.ts:1 | WARN |
| `Parameters` | interface | yes | - | code/core/src/csf/story.ts:32 | PASS |
| `ParseJsDoc` | type | no | - | code/core/src/docs-tools/argTypes/jsdocParser.ts:41 | WARN |
| `PartialArgsStoryFn` | type | no | - | code/core/src/types/modules/composedStory.ts:30 | WARN |
| `PartialStoryFn` | type | no | - | code/core/src/csf/story.ts:311 | WARN |
| `Path` | type | no | - | code/core/src/types/modules/csf.ts:94 | WARN |
| `Placeholder` | - | yes | - | - | WARN |
| `PlayFunction` | type | yes | - | code/core/src/csf/story.ts:302 | PASS |
| `PlayFunctionContext` | interface | no | - | code/core/src/csf/story.ts:290 | WARN |
| `Popover` | - | yes | - | - | WARN |
| `PopoverProvider` | - | yes | - | - | WARN |
| `Positioned` | type | no | - | code/core/src/mocking-utils/esmWalker.ts:39 | WARN |
| `PostMessageTransport` | - | yes | - | - | WARN |
| `Pre` | - | yes | - | code/core/src/components/components/typography/elements/Pre.tsx:6 | WARN |
| `PreparedMeta` | type | no | - | code/core/src/types/modules/story.ts:117 | WARN |
| `PreparedStory` | type | yes | - | code/core/src/types/modules/story.ts:99 | PASS |
| `Preset` | type | no | - | code/core/src/types/modules/core-common.ts:298 | WARN |
| `PresetColor` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:17 | PASS |
| `PresetConfig` | type | no | - | code/core/src/types/modules/core-common.ts:128 | WARN |
| `PresetProperty` | type | no | - | code/core/src/types/modules/core-common.ts:679 | WARN |
| `PresetPropertyFn` | type | no | - | code/core/src/types/modules/core-common.ts:683 | WARN |
| `PresetValue` | type | no | - | code/core/src/types/modules/core-common.ts:677 | WARN |
| `Presets` | interface | no | - | code/core/src/types/modules/core-common.ts:72 | WARN |
| `Preview` | class | yes | - | code/core/src/preview-api/modules/preview-web/Preview.tsx:60 | PASS |
| `PreviewAddon` | interface | no | - | code/core/src/csf/csf-factories.ts:74 | WARN |
| `PreviewAnnotation` | type | no | - | code/core/src/types/modules/core-common.ts:695 | WARN |
| `PreviewWeb` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWeb.tsx:11 | PASS |
| `PreviewWithSelection` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWithSelection.tsx:77 | PASS |
| `Primary` | const | yes | no | code/addons/docs/src/blocks/blocks/Primary.tsx:16 | FAIL |
| `ProjectAnnotations` | interface | yes | - | code/core/src/csf/story.ts:421 | PASS |
| `ProjectType` | enum | no | - | code/core/src/cli/projectTypes.ts:1 | WARN |
| `PropDef` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/PropDef.ts:25 | WARN |
| `PropDefaultValue` | type | no | - | code/core/src/docs-tools/argTypes/docgen/PropDef.ts:23 | WARN |
| `PropDescriptor` | type | no | - | code/core/src/preview-api/modules/store/filterArgTypes.ts:5 | WARN |
| `PropSummaryValue` | interface | no | - | code/core/src/docs-tools/argTypes/docgen/PropDef.ts:17 | WARN |
| `PropType` | type | no | - | code/core/src/docs-tools/argTypes/docgen/PropDef.ts:22 | WARN |
| `PropsExtractor` | type | no | - | code/core/src/docs-tools/argTypes/docgen/types.ts:6 | WARN |
| `Provider` | class | no | - | code/core/src/manager-api/root.tsx:316 | WARN |
| `ProviderDoesNotExtendBaseProviderError` | class | no | - | code/core/src/manager-errors.ts:23 | WARN |
| `ProviderStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/provider.decorator.tsx:13 | PASS |
| `PureArgsTable` | function | yes | - | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320 | PASS |
| `REMOVE_HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:4 | PASS |
| `RESET_HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:5 | PASS |
| `RadioControl` | - | yes | - | - | WARN |
| `RangeConfig` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:38 | PASS |
| `RangeControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Range.tsx:178 | PASS |
| `ReactMeta` | interface | yes | - | code/renderers/react/src/preview.tsx:147 | PASS |
| `ReactPreview` | interface | yes | - | code/renderers/react/src/preview.tsx:102 | PASS |
| `ReactRenderer` | interface | yes | - | code/renderers/react/src/types.ts:8 | PASS |
| `ReactStory` | interface | yes | - | code/renderers/react/src/preview.tsx:249 | PASS |
| `ReactTypes` | interface | no | - | code/renderers/react/src/types.ts:33 | WARN |
| `Ref` | interface | no | - | code/core/src/types/modules/core-common.ts:135 | WARN |
| `Refs` | - | yes | - | - | WARN |
| `RemoveAddonOptions` | type | no | - | code/core/src/common/utils/remove.ts:9 | WARN |
| `RenderContext` | type | yes | - | code/core/src/types/modules/story.ts:129 | PASS |
| `RenderContextCallbacks` | type | no | - | code/core/src/types/modules/docs.ts:14 | WARN |
| `RenderPhase` | type | no | - | code/core/src/preview-api/modules/preview-web/render/StoryRender.ts:36 | WARN |
| `RenderToCanvas` | type | yes | - | code/core/src/types/modules/story.ts:38 | PASS |
| `Renderer` | interface | no | - | code/core/src/csf/story.ts:193 | WARN |
| `RendererName` | type | no | - | code/core/src/types/modules/core-common.ts:21 | WARN |
| `Report` | interface | no | - | code/core/src/preview-api/modules/store/reporter-api.ts:1 | WARN |
| `ReporterAPI` | class | no | - | code/core/src/preview-api/modules/store/reporter-api.ts:8 | WARN |
| `RequestData` | type | no | - | code/core/src/core-events/data/request-response.ts:1 | WARN |
| `RequestResponseError` | class | no | - | code/core/src/manager-api/lib/request-response.ts:4 | WARN |
| `ResolvedModuleExport` | type | no | - | code/core/src/types/modules/docs.ts:47 | WARN |
| `ResolvedModuleExportFromType` | type | no | - | code/core/src/types/modules/docs.ts:34 | WARN |
| `ResolvedModuleExportType` | type | no | - | code/core/src/types/modules/docs.ts:24 | WARN |
| `ResponseData` | type | no | - | code/core/src/core-events/data/request-response.ts:6 | WARN |
| `RootEntry` | - | yes | - | - | WARN |
| `SBArrayType` | type | no | - | code/core/src/csf/SBType.ts:10 | WARN |
| `SBEnumType` | type | no | - | code/core/src/csf/SBType.ts:23 | WARN |
| `SBIntersectionType` | type | no | - | code/core/src/csf/SBType.ts:27 | WARN |
| `SBLiteralType` | type | no | - | code/core/src/csf/SBType.ts:35 | WARN |
| `SBNodeType` | type | no | - | code/core/src/csf/SBType.ts:14 | WARN |
| `SBObjectType` | type | no | - | code/core/src/csf/SBType.ts:19 | WARN |
| `SBOtherType` | type | no | - | code/core/src/csf/SBType.ts:43 | WARN |
| `SBScalarType` | type | no | - | code/core/src/csf/SBType.ts:6 | WARN |
| `SBTupleType` | type | no | - | code/core/src/csf/SBType.ts:39 | WARN |
| `SBType` | type | no | - | code/core/src/csf/SBType.ts:48 | WARN |
| `SBUnionType` | type | no | - | code/core/src/csf/SBType.ts:31 | WARN |
| `SCROLL_INTO_VIEW` | const | yes | - | code/core/src/highlight/constants.ts:6 | PASS |
| `SELECT_STORY` | - | yes | - | - | WARN |
| `SNIPPET_RENDERED` | const | no | - | code/core/src/docs-tools/shared.ts:5 | WARN |
| `STATUS_STORE_CHANNEL_EVENT_NAME` | const | no | - | code/addons/vitest/src/constants.ts:64 | WARN |
| `STATUS_TYPE_ID_A11Y` | const | no | - | code/addons/vitest/src/constants.ts:68 | WARN |
| `STATUS_TYPE_ID_COMPONENT_TEST` | const | no | - | code/addons/vitest/src/constants.ts:67 | WARN |
| `STORE_CHANNEL_EVENT_NAME` | const | no | - | code/addons/vitest/src/constants.ts:63 | WARN |
| `STORYBOOK_ADDON_TEST_CHANNEL` | const | yes | - | code/addons/vitest/src/constants.ts:13 | PASS |
| `STORY_PREPARED` | - | yes | - | - | WARN |
| `STORY_RENDERED` | - | yes | - | - | WARN |
| `STORY_SPECIFIED` | - | yes | - | - | WARN |
| `SUPPORTED_ESLINT_EXTENSIONS` | const | no | - | code/core/src/cli/eslintPlugin.ts:15 | WARN |
| `SaveStoryRequestPayload` | interface | no | - | code/core/src/core-events/data/save-story.ts:1 | WARN |
| `SaveStoryResponsePayload` | interface | no | - | code/core/src/core-events/data/save-story.ts:8 | WARN |
| `SavingGlobalSettingsFileError` | class | no | - | code/core/src/server-errors.ts:626 | WARN |
| `ScrollArea` | - | yes | - | - | WARN |
| `Select` | - | yes | - | code/core/src/components/components/Select/Select.tsx:201 | WARN |
| `SelectControl` | - | yes | - | - | WARN |
| `SelectionStore` | interface | no | - | code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17 | WARN |
| `SelectorWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:3 | PASS |
| `SeparatorOptions` | interface | yes | - | code/core/src/csf/index.ts:63 | PASS |
| `ServerApp` | interface | no | - | code/core/src/types/modules/core-common.ts:242 | WARN |
| `SetGlobalsPayload` | interface | no | - | code/core/src/types/modules/channelApi.ts:54 | WARN |
| `SetStoriesPayload` | type | no | - | code/core/src/types/modules/channelApi.ts:38 | WARN |
| `SetStoriesStory` | interface | no | - | code/core/src/types/modules/channelApi.ts:14 | WARN |
| `SetStoriesStoryData` | interface | no | - | code/core/src/types/modules/channelApi.ts:34 | WARN |
| `Settings` | class | no | - | code/core/src/cli/globalSettings.ts:91 | WARN |
| `SetupAddonInConfigOptions` | interface | no | - | code/core/src/common/utils/setup-addon-in-config.ts:11 | WARN |
| `SortType` | type | yes | - | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:186 | PASS |
| `Source` | const | yes | yes | code/addons/docs/src/blocks/blocks/Source.tsx:181 | PASS |
| `SourceContainer` | function | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38 | WARN |
| `SourceContext` | const | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27 | WARN |
| `SourceContextProps` | interface | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22 | WARN |
| `SourceItem` | interface | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15 | WARN |
| `SourceParameters` | type | no | - | code/addons/docs/src/blocks/blocks/Source.tsx:16 | WARN |
| `SourceProps` | type | no | - | code/addons/docs/src/blocks/blocks/Source.tsx:28 | WARN |
| `SourceType` | enum | no | - | code/core/src/docs-tools/shared.ts:7 | WARN |
| `Spaced` | - | yes | - | - | WARN |
| `Span` | - | yes | - | - | WARN |
| `State` | interface | yes | - | code/core/src/instrumenter/types.ts:72 | PASS |
| `Stats` | interface | no | - | code/core/src/types/modules/core-common.ts:152 | WARN |
| `Status` | interface | no | - | code/core/src/shared/status-store/index.ts:20 | WARN |
| `StatusByTypeId` | type | no | - | code/core/src/shared/status-store/index.ts:17 | WARN |
| `StatusStore` | type | no | - | code/core/src/shared/status-store/index.ts:45 | WARN |
| `StatusStoreByTypeId` | type | no | - | code/core/src/shared/status-store/index.ts:61 | WARN |
| `StatusTypeId` | type | no | - | code/core/src/shared/status-store/index.ts:16 | WARN |
| `StatusTypeIdMismatchError` | class | yes | - | code/core/src/manager-errors.ts:50 | PASS |
| `StatusValue` | type | no | - | code/core/src/shared/status-store/index.ts:9 | WARN |
| `StatusesByStoryIdAndTypeId` | type | no | - | code/core/src/shared/status-store/index.ts:18 | WARN |
| `StepFunction` | type | no | - | code/core/src/csf/story.ts:297 | WARN |
| `StepLabel` | type | no | - | code/core/src/csf/story.ts:295 | WARN |
| `StepRunner` | type | no | - | code/core/src/csf/story.ts:341 | WARN |
| `StoreOptions` | interface | yes | - | code/core/src/manager-api/store.ts:45 | PASS |
| `Store_CSFExports` | type | no | - | code/core/src/types/modules/composedStory.ts:23 | WARN |
| `Stories` | const | yes | no | code/addons/docs/src/blocks/blocks/Stories.tsx:74 | FAIL |
| `StoriesEntry` | type | no | - | code/core/src/types/modules/indexer.ts:18 | WARN |
| `StoriesHash` | - | yes | - | - | WARN |
| `StoriesSpecifier` | interface | no | - | code/core/src/types/modules/indexer.ts:6 | WARN |
| `StoriesWithPartialProps` | type | no | - | code/core/src/types/modules/composedStory.ts:60 | WARN |
| `Story` | const | yes | no | code/addons/docs/src/blocks/blocks/Story.tsx:134 | FAIL |
| `StoryAnnotations` | type | yes | - | code/core/src/csf/story.ts:543 | PASS |
| `StoryAnnotationsOrFn` | type | no | - | code/core/src/csf/story.ts:581 | WARN |
| `StoryContext` | interface | yes | - | code/core/src/csf/story.ts:268 | PASS |
| `StoryContextForEnhancers` | interface | no | - | code/core/src/csf/story.ts:219 | WARN |
| `StoryContextForLoaders` | interface | no | - | code/core/src/csf/story.ts:284 | WARN |
| `StoryContextUpdate` | interface | no | - | code/core/src/csf/story.ts:239 | WARN |
| `StoryEntry` | - | yes | - | - | WARN |
| `StoryFinishedPayload` | interface | no | - | code/core/src/core-events/data/phases.ts:3 | WARN |
| `StoryFn` | type | yes | - | code/core/src/csf/story.ts:327 | PASS |
| `StoryId` | type | no | - | code/core/src/csf/story.ts:8 | WARN |
| `StoryIdentifier` | interface | no | - | code/core/src/csf/story.ts:18 | WARN |
| `StoryIndex` | interface | no | - | code/core/src/types/modules/indexer.ts:174 | WARN |
| `StoryIndexEntry` | type | no | - | code/core/src/types/modules/indexer.ts:74 | WARN |
| `StoryIndexFetchError` | class | yes | - | code/core/src/preview-errors.ts:125 | PASS |
| `StoryIndexGenerator` | - | yes | - | - | WARN |
| `StoryIndexInput` | type | no | - | code/core/src/types/modules/indexer.ts:137 | WARN |
| `StoryIndexV2` | interface | no | - | code/core/src/types/modules/indexer.ts:159 | WARN |
| `StoryIndexV3` | interface | no | - | code/core/src/types/modules/indexer.ts:169 | WARN |
| `StoryKind` | type | no | - | code/core/src/csf/story.ts:14 | WARN |
| `StoryName` | type | no | - | code/core/src/csf/story.ts:11 | WARN |
| `StoryObj` | - | yes | - | code/frameworks/angular/src/client/public-types.ts:45 | WARN |
| `StoryPreparedPayload` | interface | no | - | code/core/src/types/modules/channelApi.ts:67 | WARN |
| `StoryProps` | type | no | - | code/addons/docs/src/blocks/blocks/Story.tsx:60 | WARN |
| `StoryRenderOptions` | type | no | - | code/core/src/types/modules/docs.ts:19 | WARN |
| `StorySources` | type | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20 | WARN |
| `StoryStore` | class | yes | - | code/core/src/preview-api/modules/store/StoryStore.ts:51 | PASS |
| `StoryStoreAccessedBeforeInitializationError` | class | yes | - | code/core/src/preview-errors.ts:211 | PASS |
| `StorybookConfig` | - | yes | - | code/frameworks/angular/src/types.ts:40 | WARN |
| `StorybookConfigOptions` | interface | no | - | code/core/src/types/modules/core-common.ts:224 | WARN |
| `StorybookConfigRaw` | interface | no | - | code/core/src/types/modules/core-common.ts:390 | WARN |
| `StorybookConfigVite` | type | yes | - | code/builders/builder-vite/src/types.ts:17 | PASS |
| `StorybookCoverageReporterOptions` | type | no | - | code/addons/vitest/src/node/coverage-reporter.ts:9 | WARN |
| `StorybookError` | class | yes | - | code/core/src/storybook-error.ts:25 | PASS |
| `StorybookIcon` | - | yes | - | - | WARN |
| `StorybookInternalParameters` | interface | no | - | code/core/src/types/modules/csf.ts:89 | WARN |
| `StorybookLogo` | - | yes | - | - | WARN |
| `StorybookParameters` | interface | yes | - | code/core/src/types/modules/csf.ts:75 | PASS |
| `StorybookTheme` | interface | yes | - | code/core/src/theming/types.ts:71 | PASS |
| `StorybookTypes` | interface | no | - | code/core/src/types/modules/csf.ts:85 | WARN |
| `StrictArgTypes` | type | no | - | code/core/src/csf/story.ts:163 | WARN |
| `StrictArgs` | interface | yes | - | code/core/src/csf/story.ts:157 | PASS |
| `StrictInputType` | interface | no | - | code/core/src/csf/story.ts:148 | WARN |
| `StrictParameters` | interface | no | - | code/core/src/csf/story.ts:36 | WARN |
| `StyledComponent` | - | yes | - | - | WARN |
| `Subheading` | const | yes | yes | code/addons/docs/src/blocks/blocks/Subheading.tsx:23 | PASS |
| `Subtitle` | const | yes | yes | code/addons/docs/src/blocks/blocks/Subtitle.tsx:55 | PASS |
| `SupportedBuilder` | enum | no | - | code/core/src/types/modules/builders.ts:1 | WARN |
| `SupportedFramework` | enum | no | - | code/core/src/types/modules/frameworks.ts:2 | WARN |
| `SupportedRenderer` | enum | no | - | code/core/src/types/modules/renderers.ts:1 | WARN |
| `SvelteViteWithSvelteKitError` | class | no | - | code/core/src/server-errors.ts:335 | WARN |
| `SyncPayload` | interface | no | - | code/core/src/instrumenter/types.ts:66 | WARN |
| `SyntaxHighlighter` | - | yes | - | - | WARN |
| `TEST_PROVIDER_ID` | const | yes | - | code/addons/vitest/src/constants.ts:12 | PASS |
| `TEST_PROVIDER_STORE_CHANNEL_EVENT_NAME` | const | no | - | code/addons/vitest/src/constants.ts:65 | WARN |
| `TOOL_ID` | const | no | - | code/core/src/viewport/constants.ts:4 | WARN |
| `TRIGGER_TEST_RUN_REQUEST` | const | no | - | code/addons/vitest/src/constants.ts:71 | WARN |
| `TRIGGER_TEST_RUN_RESPONSE` | const | no | - | code/addons/vitest/src/constants.ts:72 | WARN |
| `TUTORIAL_VIDEO_LINK` | const | no | - | code/addons/vitest/src/constants.ts:15 | WARN |
| `TabBar` | - | yes | - | - | WARN |
| `TabButton` | - | yes | - | - | WARN |
| `TabList` | - | yes | - | - | WARN |
| `TabPanel` | - | yes | - | - | WARN |
| `TabWrapper` | - | yes | - | - | WARN |
| `Table` | - | yes | - | code/core/src/components/components/typography/elements/Table.tsx:6 | WARN |
| `TableOfContents` | function | yes | - | code/addons/docs/src/blocks/components/TableOfContents.tsx:158 | PASS |
| `Tabs` | - | yes | - | code/core/src/components/components/Tabs/Tabs.tsx:188 | WARN |
| `TabsView` | - | yes | - | - | WARN |
| `Tag` | const | yes | - | code/core/src/shared/constants/tags.ts:4 | PASS |
| `TagOptions` | interface | no | - | code/core/src/types/modules/core-common.ts:348 | WARN |
| `TagsOptions` | type | no | - | code/core/src/types/modules/core-common.ts:355 | WARN |
| `Task` | type | no | - | code/addons/vitest/src/vitest-plugin/setup-file.ts:15 | WARN |
| `TeardownRenderToCanvas` | type | no | - | code/core/src/types/modules/story.ts:37 | WARN |
| `TestBuildConfig` | interface | no | - | code/core/src/types/modules/core-common.ts:342 | WARN |
| `TestBuildFlags` | interface | no | - | code/core/src/types/modules/core-common.ts:320 | WARN |
| `TestFunction` | type | no | - | code/core/src/csf/story.ts:306 | WARN |
| `TestProviderId` | type | no | - | code/core/src/shared/test-provider-store/index.ts:16 | WARN |
| `TestProviderState` | type | no | - | code/core/src/shared/test-provider-store/index.ts:11 | WARN |
| `TestProviderStateByProviderId` | type | no | - | code/core/src/shared/test-provider-store/index.ts:17 | WARN |
| `TestProviderStoreById` | type | no | - | code/core/src/shared/test-provider-store/index.ts:199 | WARN |
| `TestRunResult` | type | yes | - | code/addons/vitest/src/constants.ts:81 | PASS |
| `TestTypes` | interface | no | - | code/core/src/test/preview.ts:165 | WARN |
| `TextConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:67 | PASS |
| `TextControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Text.tsx:23 | PASS |
| `TextProps` | type | yes | - | code/addons/docs/src/blocks/controls/Text.tsx:11 | PASS |
| `TextSize` | type | yes | - | code/core/src/theming/types.ts:63 | PASS |
| `TextValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:66 | PASS |
| `Theme` | - | yes | - | - | WARN |
| `ThemeAddonState` | - | yes | - | - | WARN |
| `ThemeProvider` | - | yes | - | - | WARN |
| `ThemeVars` | interface | yes | - | code/core/src/theming/types.ts:4 | PASS |
| `ThemeVarsColors` | interface | yes | - | code/core/src/theming/types.ts:12 | PASS |
| `ThemeVarsPartial` | interface | yes | - | code/core/src/theming/types.ts:6 | PASS |
| `ThemesGlobals` | interface | yes | - | code/addons/themes/src/types.ts:20 | PASS |
| `ThemesParameters` | - | yes | - | - | WARN |
| `ThemesTypes` | interface | yes | - | code/addons/themes/src/types.ts:25 | PASS |
| `Title` | const | yes | yes | code/addons/docs/src/blocks/blocks/Title.tsx:55 | PASS |
| `ToggleButton` | - | yes | - | - | WARN |
| `Toolbar` | - | yes | - | code/core/src/components/components/Toolbar/Toolbar.tsx:36 | WARN |
| `Tooltip` | - | yes | - | code/core/src/components/components/tooltip/Tooltip.tsx:7 | WARN |
| `TooltipLinkList` | - | yes | - | - | WARN |
| `TooltipNote` | - | yes | - | - | WARN |
| `TriggerTestRunRequestPayload` | type | yes | - | code/addons/vitest/src/constants.ts:74 | PASS |
| `TriggerTestRunResponsePayload` | type | yes | - | code/addons/vitest/src/constants.ts:83 | PASS |
| `TypeSystem` | enum | no | - | code/core/src/docs-tools/argTypes/docgen/types.ts:51 | WARN |
| `TypescriptOptions` | interface | no | - | code/core/src/types/modules/core-common.ts:282 | WARN |
| `Typeset` | function | yes | yes | code/addons/docs/src/blocks/components/Typeset.tsx:50 | PASS |
| `Typography` | type | yes | - | code/core/src/theming/types.ts:59 | PASS |
| `UL` | - | yes | - | - | WARN |
| `UNKNOWN_ARGS_HASH` | const | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36 | WARN |
| `UPDATE_STORY_ARGS` | - | yes | - | - | WARN |
| `UncaughtManagerError` | class | no | - | code/core/src/manager-errors.ts:34 | WARN |
| `UniversalStore` | class | no | - | code/core/src/shared/universal-store/index.ts:82 | WARN |
| `UnknownArgTypesError` | class | no | - | code/core/src/preview-errors.ts:345 | WARN |
| `Unstyled` | const | yes | yes | code/addons/docs/src/blocks/blocks/Unstyled.tsx:9 | PASS |
| `UnsupportedViewportDimensionError` | class | no | - | code/core/src/preview-errors.ts:365 | WARN |
| `UpgradeStorybookToLowerVersionError` | class | no | - | code/core/src/server-errors.ts:530 | WARN |
| `UpgradeStorybookUnknownCurrentVersionError` | class | no | - | code/core/src/server-errors.ts:551 | WARN |
| `UrlStore` | class | yes | - | code/core/src/preview-api/modules/preview-web/UrlStore.ts:94 | PASS |
| `UseStatusStore` | type | no | - | code/core/src/shared/status-store/index.ts:67 | WARN |
| `UseTestProviderStore` | type | no | - | code/core/src/shared/test-provider-store/index.ts:330 | WARN |
| `UserEvent` | interface | no | - | code/core/src/test/testing-library.ts:119 | WARN |
| `UserEventObject` | type | no | - | code/core/src/test/index.ts:15 | WARN |
| `V3CompatIndexEntry` | interface | no | - | code/core/src/types/modules/indexer.ts:153 | WARN |
| `VersionCheck` | interface | no | - | code/core/src/types/modules/core-common.ts:144 | WARN |
| `View` | interface | no | - | code/core/src/preview-api/modules/preview-web/View.ts:3 | WARN |
| `ViewMode` | type | yes | - | code/core/src/csf/story.ts:247 | PASS |
| `Viewport` | interface | no | - | code/core/src/viewport/types.ts:1 | WARN |
| `ViewportGlobals` | interface | no | - | code/core/src/viewport/types.ts:56 | WARN |
| `ViewportMap` | type | no | - | code/core/src/viewport/types.ts:14 | WARN |
| `ViewportParameters` | interface | yes | - | code/core/src/viewport/types.ts:33 | PASS |
| `ViewportStyles` | interface | yes | - | code/core/src/viewport/types.ts:9 | PASS |
| `ViewportType` | type | yes | - | code/core/src/viewport/types.ts:7 | PASS |
| `ViewportTypes` | interface | no | - | code/core/src/viewport/types.ts:65 | WARN |
| `ViteBuilder` | type | yes | - | code/builders/builder-vite/src/types.ts:10 | PASS |
| `ViteFinal` | type | yes | - | code/builders/builder-vite/src/types.ts:12 | PASS |
| `WebRenderer` | interface | yes | - | code/core/src/types/modules/story.ts:28 | PASS |
| `WebView` | class | yes | - | code/core/src/preview-api/modules/preview-web/WebView.ts:42 | PASS |
| `WebpackCompilationError` | class | no | - | code/core/src/server-errors.ts:191 | WARN |
| `WebpackInvocationError` | class | no | - | code/core/src/server-errors.ts:172 | WARN |
| `WebpackMissingStatsError` | class | no | - | code/core/src/server-errors.ts:155 | WARN |
| `WebsocketTransport` | - | yes | - | - | WARN |
| `WhatsNewCache` | interface | no | - | code/core/src/core-events/data/whats-new.ts:1 | WARN |
| `WhatsNewData` | type | no | - | code/core/src/core-events/data/whats-new.ts:6 | WARN |
| `WithTooltip` | - | yes | - | - | WARN |
| `Wrapper` | const | no | - | code/addons/docs/src/blocks/blocks/Wrapper.tsx:10 | WARN |
| `Zoom` | - | yes | - | code/core/src/components/components/Zoom/Zoom.tsx:4 | WARN |
| `__definePreview` | - | yes | - | - | WARN |
| `action` | function | yes | no | code/core/src/actions/runtime/action.ts:50 | FAIL |
| `actions` | function | no | - | code/core/src/actions/runtime/actions.ts:5 | WARN |
| `addExtensionsToRelativeImports` | function | no | - | code/core/src/bin/loader.ts:64 | WARN |
| `addToDevDependenciesIfNotPresent` | function | no | - | code/core/src/cli/helpers.ts:106 | WARN |
| `addToGlobalContext` | - | yes | - | - | WARN |
| `addons` | const | yes | - | code/addons/docs/src/preset.ts:155 | PASS |
| `adjustTemplate` | function | no | - | code/core/src/cli/helpers.ts:230 | WARN |
| `afterEach` | function | yes | - | code/addons/a11y/src/preview.tsx:14 | PASS |
| `anchorBlockIdFromId` | function | no | - | code/addons/docs/src/blocks/blocks/Anchor.tsx:4 | WARN |
| `applyHooks` | function | yes | yes | code/core/src/preview-api/modules/addons/hooks.ts:184 | PASS |
| `argsHash` | function | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11 | WARN |
| `assertIsFn` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:19 | WARN |
| `automock` | - | yes | - | - | WARN |
| `automockModule` | function | no | - | code/core/src/mocking-utils/automock.ts:47 | WARN |
| `babelParse` | - | yes | - | - | WARN |
| `babelParser` | function | no | - | code/core/src/mocking-utils/extract.ts:44 | WARN |
| `background` | const | no | - | code/core/src/theming/base.ts:44 | WARN |
| `bail` | function | yes | yes | code/builders/builder-vite/src/index.ts:37 | PASS |
| `beforeAll` | function | no | - | code/renderers/react/src/entry-preview.tsx:49 | WARN |
| `build` | function | yes | no | code/builders/builder-vite/src/index.ts:63 | FAIL |
| `builderPackages` | const | no | - | code/core/src/common/utils/get-storybook-info.ts:64 | WARN |
| `cache` | const | no | - | code/core/src/common/utils/cache.ts:4 | WARN |
| `checkAddonOrder` | function | no | - | code/core/src/common/utils/check-addon-order.ts:39 | WARN |
| `checkRef` | function | no | - | code/core/src/common/utils/get-storybook-refs.ts:61 | WARN |
| `clearAllMocks` | function | yes | yes | code/core/src/test/spy.ts:77 | PASS |
| `cliStoriesTargetPath` | function | no | - | code/core/src/cli/helpers.ts:161 | WARN |
| `coerceSemver` | function | no | - | code/core/src/cli/helpers.ts:242 | WARN |
| `color` | const | no | - | code/core/src/theming/base.ts:1 | WARN |
| `colors` | - | yes | - | - | WARN |
| `combineArgs` | function | yes | yes | code/core/src/preview-api/modules/store/args.ts:84 | PASS |
| `combineParameters` | function | yes | yes | code/core/src/preview-api/modules/store/parameters.ts:11 | PASS |
| `combineTags` | function | yes | - | code/core/src/csf/index.ts:81 | PASS |
| `commonGlobOptions` | function | no | - | code/core/src/common/utils/common-glob-options.ts:4 | WARN |
| `compilerPackages` | const | no | - | code/core/src/common/utils/get-storybook-info.ts:71 | WARN |
| `componentTransform` | - | yes | - | - | WARN |
| `composeConfigs` | function | yes | yes | code/core/src/preview-api/modules/store/csf/composeConfigs.ts:43 | PASS |
| `composeStepRunners` | function | yes | yes | code/core/src/preview-api/modules/store/csf/stepRunners.ts:27 | PASS |
| `composeStories` | function | yes | no | code/core/src/preview-api/modules/store/csf/portable-stories.ts:274 | FAIL |
| `composeStory` | function | yes | no | code/core/src/preview-api/modules/store/csf/portable-stories.ts:90 | FAIL |
| `config` | const | no | - | code/core/src/actions/runtime/configureActions.ts:3 | WARN |
| `configureActions` | function | yes | - | code/core/src/actions/runtime/configureActions.ts:9 | PASS |
| `configureEslintPlugin` | function | no | - | code/core/src/cli/eslintPlugin.ts:265 | WARN |
| `configureFlatConfig` | function | no | - | code/core/src/cli/eslintPlugin.ts:55 | WARN |
| `controlOrMetaKey` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:7 | WARN |
| `controlOrMetaSymbol` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:6 | WARN |
| `convert` | function | no | - | code/core/src/docs-tools/argTypes/convert/index.ts:8 | WARN |
| `convertToFilePath` | function | no | - | code/addons/vitest/src/vitest-plugin/test-utils.ts:25 | WARN |
| `copyTemplate` | function | no | - | code/core/src/cli/helpers.ts:122 | WARN |
| `copyTemplateFiles` | function | no | - | code/core/src/cli/helpers.ts:168 | WARN |
| `core` | - | yes | - | - | WARN |
| `corePresets` | const | yes | - | code/builders/builder-vite/src/index.ts:67 | PASS |
| `create` | function | yes | yes | code/core/src/theming/create.ts:29 | PASS |
| `createBrowserChannel` | - | yes | - | - | WARN |
| `createCache` | - | yes | - | - | WARN |
| `createFileSystemCache` | function | no | - | code/core/src/common/utils/file-cache.ts:160 | WARN |
| `createGlobal` | const | yes | - | code/core/src/theming/global.ts:101 | PASS |
| `createLogStream` | function | no | - | code/core/src/common/utils/cli.ts:114 | WARN |
| `createPlaywrightTest` | function | no | - | code/core/src/preview-api/modules/store/csf/portable-stories.ts:319 | WARN |
| `createReset` | const | yes | - | code/core/src/theming/global.ts:25 | PASS |
| `createSummaryValue` | function | no | - | code/core/src/docs-tools/argTypes/utils.ts:14 | WARN |
| `createTest` | - | yes | - | - | WARN |
| `css` | - | yes | - | - | WARN |
| `darken` | const | yes | - | code/core/src/theming/utils.ts:62 | PASS |
| `decorateStory` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:10 | PASS |
| `decorators` | const | yes | - | code/addons/a11y/src/preview.tsx:12 | PASS |
| `default` | function | no | - | code/addons/a11y/src/postinstall.ts:5 | WARN |
| `defaultDecorateStory` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:49 | PASS |
| `defineMain` | - | yes | yes | code/frameworks/angular/src/node/index.ts:3 | WARN |
| `definePreview` | - | yes | - | code/frameworks/angular/src/client/preview.ts:45 | WARN |
| `definePreviewAddon` | function | no | - | code/core/src/csf/csf-factories.ts:78 | WARN |
| `deprecate` | const | yes | - | code/core/src/client-logger/index.ts:75 | PASS |
| `detectPnp` | function | no | - | code/core/src/cli/detect.ts:4 | WARN |
| `docs` | const | no | - | code/addons/docs/src/preset.ts:224 | WARN |
| `doesVariableOrFunctionDeclarationExist` | function | no | - | code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:17 | WARN |
| `emitTransformCode` | function | no | - | code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15 | WARN |
| `enhanceArgTypes` | function | no | - | code/core/src/docs-tools/argTypes/enhanceArgTypes.ts:5 | WARN |
| `enrichCsf` | - | yes | - | code/core/src/csf-tools/enrichCsf.ts:144 | WARN |
| `ensure` | function | no | - | code/core/src/theming/ensure.ts:10 | WARN |
| `esmWalker` | function | yes | - | code/core/src/mocking-utils/esmWalker.ts:71 | PASS |
| `eventMatchesShortcut` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:124 | WARN |
| `eventToShortcut` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:21 | WARN |
| `executeCommand` | function | no | - | code/core/src/common/utils/command.ts:49 | WARN |
| `executeCommandSync` | function | no | - | code/core/src/common/utils/command.ts:63 | WARN |
| `executeNodeCommand` | function | no | - | code/core/src/common/utils/command.ts:79 | WARN |
| `expect` | - | yes | - | - | WARN |
| `experimental_MockUniversalStore` | class | no | - | code/core/src/shared/universal-store/mock.ts:40 | WARN |
| `experimental_UniversalStore` | class | yes | - | code/core/src/shared/universal-store/index.ts:82 | PASS |
| `experimental_enrichCsf` | function | no | - | code/renderers/react/src/enrichCsf.ts:10 | WARN |
| `experimental_getStatusStore` | - | yes | - | code/core/src/core-server/stores/status.ts | WARN |
| `experimental_getTestProviderStore` | - | yes | - | code/core/src/core-server/stores/test-provider.ts | WARN |
| `experimental_loadStorybook` | - | yes | - | - | WARN |
| `experimental_manifests` | function | no | - | code/addons/docs/src/manifest.ts:135 | WARN |
| `experimental_requestResponse` | function | no | - | code/core/src/manager-api/lib/request-response.ts:13 | WARN |
| `experimental_serverChannel` | function | no | - | code/addons/vitest/src/preset.ts:59 | WARN |
| `experimental_useStatusStore` | - | no | - | code/core/src/manager-api/stores/status.ts | WARN |
| `experimental_useTestProviderStore` | - | no | - | code/core/src/manager-api/stores/test-provider.ts | WARN |
| `experimental_useUniversalStore` | function | no | - | code/core/src/shared/universal-store/use-universal-store-manager.ts:16 | WARN |
| `extract` | - | yes | - | - | WARN |
| `extractComponentDescription` | function | no | - | code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:106 | WARN |
| `extractComponentProps` | function | no | - | code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:70 | WARN |
| `extractComponentSectionArray` | function | no | - | code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:35 | WARN |
| `extractComponentSectionObject` | function | no | - | code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:54 | WARN |
| `extractEslintInfo` | function | no | - | code/core/src/cli/eslintPlugin.ts:217 | WARN |
| `extractFrameworkPackageName` | function | no | - | code/core/src/common/utils/get-framework-name.ts:34 | WARN |
| `extractMockCalls` | function | no | - | code/core/src/mocking-utils/extract.ts:85 | WARN |
| `extractRenderer` | function | no | - | code/core/src/common/utils/get-renderer-name.ts:37 | WARN |
| `extractTitle` | function | no | - | code/addons/docs/src/blocks/blocks/Title.tsx:24 | WARN |
| `filterArgTypes` | function | yes | yes | code/core/src/preview-api/modules/store/filterArgTypes.ts:10 | PASS |
| `filterPresetsConfig` | function | no | - | code/core/src/common/presets.ts:35 | WARN |
| `findByRole` | - | yes | - | - | WARN |
| `findConfigFile` | function | no | - | code/core/src/common/utils/get-storybook-info.ts:105 | WARN |
| `findEslintFile` | function | no | - | code/core/src/cli/eslintPlugin.ts:18 | WARN |
| `findFilesUp` | function | no | - | code/core/src/common/utils/paths.ts:64 | WARN |
| `fireEvent` | - | yes | - | - | WARN |
| `fn` | function | yes | yes | code/core/src/test/spy.ts:48 | PASS |
| `format` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:22 | PASS |
| `formatDate` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:26 | PASS |
| `formatFileContent` | function | no | - | code/core/src/common/utils/formatter.ts:51 | WARN |
| `formatTime` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:34 | PASS |
| `frameworkPackages` | const | no | - | code/core/src/common/utils/get-storybook-info.ts:39 | WARN |
| `frameworkToBuilder` | const | no | - | code/core/src/common/utils/framework.ts:41 | WARN |
| `frameworkToRenderer` | const | no | - | code/core/src/common/utils/framework.ts:3 | WARN |
| `generate` | - | yes | - | - | WARN |
| `generateStoryFile` | - | yes | - | - | WARN |
| `getAbsolutePathWrapperAsCallExpression` | function | no | - | code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:141 | WARN |
| `getAbsolutePathWrapperName` | function | no | - | code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:57 | WARN |
| `getAddonNames` | function | no | - | code/core/src/common/utils/get-addon-names.ts:5 | WARN |
| `getArbitraryModuleIdentifier` | function | no | - | code/core/src/mocking-utils/esmWalker.ts:341 | WARN |
| `getAutoRefs` | function | no | - | code/core/src/common/utils/get-storybook-refs.ts:12 | WARN |
| `getAutomockCode` | function | no | - | code/core/src/mocking-utils/automock.ts:17 | WARN |
| `getBabelDependencies` | function | no | - | code/core/src/cli/helpers.ts:73 | WARN |
| `getByRole` | - | yes | - | - | WARN |
| `getConfigInfo` | function | no | - | code/core/src/common/utils/get-storybook-info.ts:111 | WARN |
| `getCoreAnnotations` | function | no | - | code/core/src/csf/core-annotations.ts:33 | WARN |
| `getCsfFactoryAnnotations` | function | no | - | code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10 | WARN |
| `getDirectoryFromWorkingDir` | function | no | - | code/core/src/common/utils/normalize-stories.ts:25 | WARN |
| `getDocgenDescription` | function | no | - | code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:18 | WARN |
| `getDocgenSection` | function | no | - | code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:14 | WARN |
| `getEnvConfig` | function | no | - | code/core/src/common/utils/cli.ts:69 | WARN |
| `getFieldsForGetAbsolutePathWrapper` | function | no | - | code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:114 | WARN |
| `getFrameworkName` | function | no | - | code/core/src/common/utils/get-framework-name.ts:9 | WARN |
| `getInterpretedFile` | function | no | - | code/core/src/common/utils/interpret-files.ts:19 | WARN |
| `getIsExternal` | function | no | - | code/core/src/mocking-utils/resolve.ts:58 | WARN |
| `getMockerRuntime` | function | no | - | code/core/src/mocking-utils/runtime.ts:8 | WARN |
| `getPackageDetails` | function | no | - | code/core/src/common/js-package-manager/JsPackageManager.ts:45 | WARN |
| `getPreferredColorScheme` | function | yes | - | code/core/src/theming/utils.ts:66 | PASS |
| `getPresets` | function | no | - | code/core/src/common/presets.ts:318 | WARN |
| `getPrettier` | function | no | - | code/core/src/common/utils/formatter.ts:25 | WARN |
| `getPreviewBodyTemplate` | - | yes | - | - | WARN |
| `getPreviewHeadTemplate` | - | yes | - | - | WARN |
| `getProjectRoot` | function | no | - | code/core/src/common/utils/paths.ts:11 | WARN |
| `getRealPath` | function | no | - | code/core/src/mocking-utils/resolve.ts:124 | WARN |
| `getRefs` | function | no | - | code/core/src/common/utils/get-storybook-refs.ts:95 | WARN |
| `getRendererDir` | function | no | - | code/core/src/cli/dirs.ts:53 | WARN |
| `getRendererName` | function | no | - | code/core/src/common/utils/get-renderer-name.ts:11 | WARN |
| `getSessionId` | - | yes | - | - | WARN |
| `getStoryChildren` | function | no | - | code/core/src/csf/csf-factories.ts:278 | WARN |
| `getStoryHref` | - | yes | - | code/core/src/components/components/utils/getStoryHref.ts:15 | WARN |
| `getStoryId` | function | no | - | code/addons/docs/src/blocks/blocks/Story.tsx:62 | WARN |
| `getStoryProps` | function | no | - | code/addons/docs/src/blocks/blocks/Story.tsx:75 | WARN |
| `getStorySortParameter` | - | yes | - | - | WARN |
| `getStoryTitle` | function | no | - | code/core/src/common/utils/get-story-id.ts:49 | WARN |
| `getStorybookConfiguration` | function | no | - | code/core/src/common/utils/get-storybook-configuration.ts:7 | WARN |
| `getStorybookInfo` | function | yes | - | code/core/src/common/utils/get-storybook-info.ts:139 | PASS |
| `getStorybookMetadata` | - | yes | - | - | WARN |
| `getVersionSafe` | function | no | - | code/core/src/cli/helpers.ts:145 | WARN |
| `globToRegexp` | function | no | - | code/core/src/common/utils/glob-to-regexp.ts:3 | WARN |
| `globalPackages` | const | no | - | code/core/src/manager/globals/globals.ts:24 | WARN |
| `globalSettings` | function | no | - | code/core/src/cli/globalSettings.ts:61 | WARN |
| `globalsNameReferenceMap` | const | no | - | code/core/src/manager/globals/globals.ts:2 | WARN |
| `groupBy` | function | no | - | code/core/src/common/utils/utils.ts:2 | WARN |
| `hasDocgen` | function | no | - | code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:4 | WARN |
| `hasStorybookDependencies` | function | no | - | code/core/src/cli/helpers.ts:248 | WARN |
| `hasVitePlugins` | function | yes | no | code/builders/builder-vite/src/utils/has-vite-plugins.ts:13 | FAIL |
| `ignoreSsrWarning` | const | yes | - | code/core/src/theming/index.ts:43 | PASS |
| `importMetaResolve` | function | no | - | code/core/src/shared/utils/module.ts:15 | WARN |
| `importModule` | function | no | - | code/core/src/shared/utils/module.ts:65 | WARN |
| `includeConditionalArg` | function | no | - | code/core/src/csf/includeConditionalArg.ts:31 | WARN |
| `inferControls` | function | yes | - | code/core/src/preview-api/modules/store/inferControls.ts:66 | PASS |
| `initialGlobals` | const | yes | - | code/addons/a11y/src/preview.tsx:98 | PASS |
| `initializeThemeState` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:34 | PASS |
| `instrument` | function | yes | - | code/core/src/instrumenter/instrumenter.ts:749 | PASS |
| `internal_checklistStore` | const | no | - | code/core/src/manager-api/stores/checklist.ts:14 | WARN |
| `internal_getArgTypesData` | function | no | - | code/renderers/react/src/preset.ts:87 | WARN |
| `internal_universalChecklistStore` | const | no | - | code/core/src/manager-api/stores/checklist.ts:9 | WARN |
| `interpolate` | function | no | - | code/core/src/common/utils/interpolate.ts:10 | WARN |
| `invalidateProjectRootCache` | function | no | - | code/core/src/common/utils/paths.ts:59 | WARN |
| `invariant` | function | no | - | code/core/src/common/utils/utils.ts:18 | WARN |
| `isAddonA11yEnabled` | const | no | - | code/addons/a11y/src/preset.ts:3 | WARN |
| `isCI` | function | no | - | code/core/src/common/utils/envs.ts:80 | WARN |
| `isConfigAlreadySetup` | function | no | - | code/addons/vitest/src/postinstall.ts:410 | WARN |
| `isCorePackage` | function | no | - | code/core/src/common/utils/cli.ts:141 | WARN |
| `isDefaultValueBlacklisted` | function | no | - | code/core/src/docs-tools/argTypes/docgen/utils/defaultValue.ts:3 | WARN |
| `isExportStory` | function | yes | - | code/core/src/csf/index.ts:51 | PASS |
| `isExternal` | function | no | - | code/core/src/mocking-utils/resolve.ts:112 | WARN |
| `isFunctionNode` | function | no | - | code/core/src/mocking-utils/esmWalker.ts:320 | WARN |
| `isGetAbsolutePathWrapperNecessary` | function | no | - | code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:76 | WARN |
| `isInDestructuringAssignment` | function | no | - | code/core/src/mocking-utils/esmWalker.ts:333 | WARN |
| `isMacLike` | function | no | - | code/core/src/manager-api/lib/platform.ts:5 | WARN |
| `isMeta` | function | no | - | code/core/src/csf/csf-factories.ts:115 | WARN |
| `isMockFunction` | - | yes | - | - | WARN |
| `isModuleDirectory` | function | no | - | code/core/src/mocking-utils/extract.ts:16 | WARN |
| `isNodeInPattern` | function | no | - | code/core/src/mocking-utils/esmWalker.ts:66 | WARN |
| `isPreservingSymlinks` | function | no | - | code/core/src/common/utils/symlinks.ts:1 | WARN |
| `isPreview` | function | no | - | code/core/src/csf/csf-factories.ts:84 | WARN |
| `isPropValid` | - | yes | - | - | WARN |
| `isSatelliteAddon` | function | no | - | code/core/src/common/utils/cli.ts:143 | WARN |
| `isShortcutTaken` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:10 | WARN |
| `isStaticProperty` | function | no | - | code/core/src/mocking-utils/esmWalker.ts:311 | WARN |
| `isStaticPropertyKey` | function | no | - | code/core/src/mocking-utils/esmWalker.ts:315 | WARN |
| `isStory` | function | no | - | code/core/src/csf/csf-factories.ts:173 | WARN |
| `isTooLongForDefaultValueSummary` | function | no | - | code/core/src/docs-tools/argTypes/utils.ts:10 | WARN |
| `isTooLongForTypeSummary` | function | no | - | code/core/src/docs-tools/argTypes/utils.ts:6 | WARN |
| `isValidDocgenSection` | function | no | - | code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:10 | WARN |
| `jsx` | - | yes | - | - | WARN |
| `keyToSymbol` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:137 | WARN |
| `keyframes` | - | yes | - | - | WARN |
| `lighten` | const | yes | - | code/core/src/theming/utils.ts:61 | PASS |
| `load` | function | no | - | code/core/src/bin/loader.ts:90 | WARN |
| `loadAllPresets` | function | no | - | code/core/src/common/presets.ts:330 | WARN |
| `loadEnvs` | function | no | - | code/core/src/common/utils/envs.ts:9 | WARN |
| `loadMainConfig` | function | yes | - | code/core/src/common/utils/load-main-config.ts:14 | PASS |
| `loadManagerOrAddonsFile` | function | no | - | code/core/src/common/utils/load-manager-or-addons-file.ts:9 | WARN |
| `loadPreset` | function | no | - | code/core/src/common/presets.ts:156 | WARN |
| `loadPreviewOrConfigFile` | function | no | - | code/core/src/common/utils/load-preview-or-config-file.ts:7 | WARN |
| `logConfig` | function | no | - | code/core/src/common/utils/log-config.ts:3 | WARN |
| `logTracker` | - | yes | - | - | WARN |
| `logger` | const | yes | - | code/core/src/client-logger/index.ts:23 | PASS |
| `makeDecorator` | function | yes | - | code/core/src/preview-api/modules/addons/make-decorator.ts:44 | PASS |
| `merge` | - | no | - | code/core/src/manager-api/lib/merge.ts | WARN |
| `mockChannel` | function | yes | yes | code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:3 | PASS |
| `mocked` | function | yes | yes | code/core/src/test/spy.ts:119 | PASS |
| `mocks` | - | yes | - | - | WARN |
| `modifyErrorMessage` | function | no | - | code/addons/vitest/src/vitest-plugin/setup-file.ts:22 | WARN |
| `module.exports` | class | no | - | code/addons/vitest/src/node/coverage-reporter.ts:56 | WARN |
| `mount` | function | no | - | code/renderers/react/src/mount.ts:5 | WARN |
| `nodePathsToArray` | function | no | - | code/core/src/common/utils/paths.ts:73 | WARN |
| `normalizeArrays` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeArrays.ts:1 | PASS |
| `normalizeExtends` | function | no | - | code/core/src/cli/eslintPlugin.ts:250 | WARN |
| `normalizeNewlines` | function | no | - | code/core/src/docs-tools/argTypes/utils.ts:21 | WARN |
| `normalizeProjectAnnotations` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:17 | PASS |
| `normalizeStories` | function | yes | - | code/core/src/common/utils/normalize-stories.ts:108 | PASS |
| `normalizeStoriesEntry` | function | no | - | code/core/src/common/utils/normalize-stories.ts:38 | WARN |
| `normalizeStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeStory.ts:25 | PASS |
| `normalizeStoryPath` | function | no | - | code/core/src/common/utils/paths.ts:82 | WARN |
| `onMockCall` | function | yes | yes | code/core/src/test/spy.ts:35 | PASS |
| `once` | function | yes | - | code/core/src/client-logger/index.ts:57 | PASS |
| `optimizeViteDeps` | const | no | - | code/addons/docs/src/preset.ts:224 | WARN |
| `optionOrAltSymbol` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:8 | WARN |
| `optionalEnvToBoolean` | function | no | - | code/core/src/common/utils/envs.ts:61 | WARN |
| `parameters` | const | yes | - | code/addons/a11y/src/preview.tsx:105 | PASS |
| `parse` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:17 | PASS |
| `parseDate` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:11 | PASS |
| `parseJsDoc` | function | no | - | code/core/src/docs-tools/argTypes/jsdocParser.ts:75 | WARN |
| `parseKind` | function | yes | - | code/core/src/csf/index.ts:69 | PASS |
| `parseList` | function | no | - | code/core/src/common/utils/cli.ts:62 | WARN |
| `parseTime` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:18 | PASS |
| `parser` | - | yes | - | - | WARN |
| `pauseAnimations` | function | no | - | code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18 | WARN |
| `pluckThemeFromContext` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:16 | PASS |
| `posix` | function | no | - | code/core/src/common/utils/posix.ts:4 | WARN |
| `prepareMeta` | function | yes | yes | code/core/src/preview-api/modules/store/csf/prepareStory.ts:171 | PASS |
| `prepareStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/prepareStory.ts:37 | PASS |
| `pretty` | function | yes | - | code/core/src/client-logger/index.ts:77 | PASS |
| `prompt` | - | yes | - | - | WARN |
| `queryByRole` | - | yes | - | - | WARN |
| `readFileAsJson` | function | no | - | code/core/src/cli/helpers.ts:25 | WARN |
| `readTemplate` | function | no | - | code/core/src/common/utils/readTemplate.ts:3 | WARN |
| `recast` | - | yes | - | - | WARN |
| `redirect` | - | yes | - | - | WARN |
| `removeAddon` | function | no | - | code/core/src/common/utils/remove.ts:24 | WARN |
| `rendererPackages` | const | no | - | code/core/src/common/utils/get-storybook-info.ts:22 | WARN |
| `resetAllMocks` | function | yes | yes | code/core/src/test/spy.ts:89 | PASS |
| `resolve` | - | yes | - | - | WARN |
| `resolveAddonName` | function | no | - | code/core/src/common/presets.ts:68 | WARN |
| `resolveExternalModule` | function | no | - | code/core/src/mocking-utils/resolve.ts:34 | WARN |
| `resolveImport` | function | no | - | code/core/src/common/utils/interpret-files.ts:25 | WARN |
| `resolveMock` | function | no | - | code/core/src/mocking-utils/resolve.ts:74 | WARN |
| `resolvePackageDir` | function | no | - | code/core/src/shared/utils/module.ts:28 | WARN |
| `resolvePathInStorybookCache` | function | no | - | code/core/src/common/utils/resolve-path-in-sb-cache.ts:20 | WARN |
| `resolveWithExtension` | function | no | - | code/core/src/bin/loader.ts:34 | WARN |
| `resolveWithExtensions` | function | no | - | code/core/src/mocking-utils/resolve.ts:140 | WARN |
| `resolvedReact` | function | no | - | code/addons/docs/src/preset.ts:208 | WARN |
| `responsiveViewport` | const | no | - | code/core/src/viewport/responsiveViewport.tsx:4 | WARN |
| `restoreAllMocks` | function | yes | yes | code/core/src/test/spy.ts:98 | PASS |
| `rewriteSbMockImportCalls` | function | no | - | code/core/src/mocking-utils/extract.ts:54 | WARN |
| `runtime` | - | yes | - | - | WARN |
| `safeResolveModule` | function | no | - | code/core/src/shared/utils/module.ts:126 | WARN |
| `sanitize` | function | yes | - | code/core/src/csf/index.ts:8 | PASS |
| `sanitizeStoryContextUpdate` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:30 | PASS |
| `satisfies` | function | no | - | code/core/src/common/utils/satisfies.ts:2 | WARN |
| `sb` | const | yes | - | code/core/src/test/index.ts:54 | PASS |
| `scanAndTransformFiles` | function | no | - | code/core/src/common/utils/scan-and-transform-files.ts:13 | WARN |
| `screen` | - | yes | - | - | WARN |
| `serverRequire` | function | no | - | code/core/src/common/utils/interpret-require.ts:17 | WARN |
| `setCompodocJson` | function | no | - | code/addons/docs/src/angular/index.ts:1 | WARN |
| `setDefaultProjectAnnotations` | function | yes | - | code/core/src/preview-api/modules/store/csf/portable-stories.ts:49 | PASS |
| `setIsNodeInPattern` | function | no | - | code/core/src/mocking-utils/esmWalker.ts:63 | WARN |
| `setJSONDoc` | function | no | - | code/addons/docs/src/ember/index.ts:1 | WARN |
| `setProjectAnnotations` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:73 | PASS |
| `setup` | function | no | - | code/addons/vitest/src/vitest-plugin/global-setup.ts:71 | WARN |
| `setupAddonInConfig` | function | no | - | code/core/src/common/utils/setup-addon-in-config.ts:24 | WARN |
| `shortcutMatchesShortcut` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:102 | WARN |
| `shortcutToAriaKeyshortcuts` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:180 | WARN |
| `shortcutToHumanString` | function | no | - | code/core/src/manager-api/lib/shortcut.ts:175 | WARN |
| `simulateDOMContentLoaded` | function | no | - | code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31 | WARN |
| `simulatePageLoad` | function | no | - | code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83 | WARN |
| `slugs` | const | no | - | code/addons/docs/src/blocks/blocks/Heading.tsx:15 | WARN |
| `sortStoriesV7` | function | yes | yes | code/core/src/preview-api/modules/store/sortStories.ts:37 | PASS |
| `spyOn` | function | yes | yes | code/core/src/test/spy.ts:41 | PASS |
| `srOnlyStyles` | const | yes | - | code/core/src/theming/global.ts:12 | PASS |
| `start` | function | yes | no | code/builders/builder-vite/src/index.ts:41 | FAIL |
| `staticDirs` | function | no | - | code/addons/vitest/src/preset.ts:308 | WARN |
| `storeOptions` | const | yes | - | code/addons/vitest/src/constants.ts:21 | PASS |
| `storyNameFromExport` | function | yes | - | code/core/src/csf/index.ts:35 | PASS |
| `storybookTest` | function | yes | - | code/addons/vitest/src/vitest-plugin/index.ts:164 | PASS |
| `str` | function | no | - | code/core/src/docs-tools/argTypes/docgen/utils/string.ts:1 | WARN |
| `stringifyEnvs` | function | no | - | code/core/src/common/utils/envs.ts:47 | WARN |
| `stringifyProcessEnvs` | function | no | - | code/core/src/common/utils/envs.ts:53 | WARN |
| `styled` | - | yes | - | - | WARN |
| `suggestESLintPlugin` | function | no | - | code/core/src/cli/eslintPlugin.ts:331 | WARN |
| `supportedExtensions` | const | no | - | code/core/src/bin/loader.ts:19 | WARN |
| `syncPreviewAddonsWithMainConfig` | function | no | - | code/core/src/common/utils/sync-main-preview-addons.ts:31 | WARN |
| `syncStorybookAddons` | function | no | - | code/core/src/common/utils/sync-main-preview-addons.ts:16 | WARN |
| `teardown` | function | no | - | code/addons/vitest/src/vitest-plugin/global-setup.ts:77 | WARN |
| `telemetry` | - | yes | - | - | WARN |
| `temporaryDirectory` | function | no | - | code/core/src/common/utils/cli.ts:18 | WARN |
| `temporaryFile` | function | no | - | code/core/src/common/utils/cli.ts:47 | WARN |
| `testStory` | function | no | - | code/addons/vitest/src/vitest-plugin/test-utils.ts:34 | WARN |
| `themes` | const | yes | - | code/core/src/theming/create.ts:20 | PASS |
| `toId` | function | yes | yes | code/core/src/csf/index.ts:27 | PASS |
| `toTestId` | function | yes | - | code/core/src/csf/index.ts:31 | PASS |
| `tokens` | const | no | - | code/core/src/theming/base.ts:104 | WARN |
| `transformImportFiles` | function | no | - | code/core/src/common/utils/transform-imports.ts:19 | WARN |
| `transformSync` | - | yes | - | - | WARN |
| `traverse` | - | yes | - | - | WARN |
| `types` | - | yes | - | - | WARN |
| `typography` | const | no | - | code/core/src/theming/base.ts:59 | WARN |
| `uninstrumentedUserEvent` | const | no | - | code/core/src/test/testing-library.ts:121 | WARN |
| `useAddonState` | function | no | - | code/core/src/manager-api/root.tsx:458 | WARN |
| `useArgTypes` | function | no | - | code/core/src/manager-api/root.tsx:501 | WARN |
| `useArgs` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:614 | PASS |
| `useCallback` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:344 | PASS |
| `useChannel` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:530 | PASS |
| `useEffect` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:498 | PASS |
| `useGlobalTypes` | function | no | - | code/core/src/manager-api/root.tsx:491 | WARN |
| `useGlobals` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:649 | PASS |
| `useMemo` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:322 | PASS |
| `useOf` | function | yes | - | code/addons/docs/src/blocks/blocks/useOf.ts:18 | PASS |
| `useParameter` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:590 | PASS |
| `useReducer` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:457 | PASS |
| `useRef` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:367 | PASS |
| `useSharedState` | function | no | - | code/core/src/manager-api/root.tsx:371 | WARN |
| `useSourceProps` | function | no | - | code/addons/docs/src/blocks/blocks/Source.tsx:101 | WARN |
| `useState` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:418 | PASS |
| `useStatusStore` | - | yes | - | - | WARN |
| `useStoryContext` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:560 | PASS |
| `useStoryPrepared` | function | no | - | code/core/src/manager-api/root.tsx:341 | WARN |
| `useStorybookApi` | function | no | - | code/core/src/manager-api/root.tsx:297 | WARN |
| `useStorybookState` | function | no | - | code/core/src/manager-api/root.tsx:293 | WARN |
| `useTabsState` | - | yes | - | - | WARN |
| `useTestProviderStore` | - | yes | - | - | WARN |
| `useTheme` | - | yes | - | - | WARN |
| `useThemeParameters` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:20 | PASS |
| `useUniversalStore` | - | yes | - | - | WARN |
| `userEvent` | - | yes | - | - | WARN |
| `userOrAutoTitle` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:86 | PASS |
| `userOrAutoTitleFromSpecifier` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:49 | PASS |
| `validateConfigurationFiles` | function | no | - | code/core/src/common/utils/validate-configuration-files.ts:14 | WARN |
| `validateFrameworkName` | function | no | - | code/core/src/common/utils/validate-config.ts:16 | WARN |
| `versions` | - | no | - | code/core/src/common/versions.ts | WARN |
| `viteCorePlugins` | function | no | - | code/builders/builder-vite/src/preset.ts:19 | WARN |
| `viteFinal` | function | yes | - | code/addons/docs/src/preset.ts:159 | PASS |
| `vitestTransform` | - | yes | - | - | WARN |
| `waitFor` | - | yes | - | - | WARN |
| `waitForAnimations` | function | no | - | code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54 | WARN |
| `webpack` | const | no | - | code/addons/docs/src/preset.ts:224 | WARN |
| `withActions` | const | yes | - | code/core/src/actions/decorator.ts:59 | PASS |
| `withTheme` | - | yes | - | - | WARN |
| `withThemeByClassName` | function | yes | yes | code/addons/themes/src/decorators/class-name.decorator.tsx:19 | PASS |
| `withThemeByDataAttribute` | function | yes | yes | code/addons/themes/src/decorators/data-attribute.decorator.tsx:19 | PASS |
| `withThemeFromJSXProvider` | function | yes | yes | code/addons/themes/src/decorators/provider.decorator.tsx:23 | PASS |
| `within` | - | yes | - | - | WARN |
| `withoutVitePlugins` | function | yes | no | code/builders/builder-vite/src/utils/without-vite-plugins.ts:2 | FAIL |
| `wrapValueWithGetAbsolutePathWrapper` | function | no | - | code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:191 | WARN |
| `writeFileAsJson` | function | no | - | code/core/src/cli/helpers.ts:42 | WARN |

### Coverage Summary

- **Exports Found:** 985
- **Documented:** 292 (29.64%)
- **Missing Documentation:** 693
- **Signature Mismatches:** 12
- **Stale Documentation:** 160, documented extras included
- **Scoped Out by the Brief:** `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx), `AngularMeta` (code/frameworks/angular/src/client/preview.ts), `AngularOptions` (code/frameworks/angular/src/types.ts), `AngularPreview` (code/frameworks/angular/src/client/preview.ts), `AngularRenderer` (code/frameworks/angular/src/client/types.ts), `AngularStory` (code/frameworks/angular/src/client/preview.ts), `BabelFileClass` (code/core/src/babel/index.ts), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts), `Bar` (code/core/src/components/components/Bar/Bar.tsx), `BaseLocationProvider` (code/core/src/router/router.tsx), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx), `BuildIndexOptions` (code/core/src/core-server/build-index.ts), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts), `CacheEntry` (code/core/src/telemetry/event-cache.ts), `Channel` (code/core/src/channels/main.ts), `ChannelHandler` (code/core/src/channels/types.ts), `ChannelTransport` (code/core/src/channels/types.ts), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts), `CsfFile` (code/core/src/csf-tools/CsfFile.ts), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts), `DL` (code/core/src/components/components/typography/elements/DL.tsx), `Dependency` (code/core/src/telemetry/types.ts), `Div` (code/core/src/components/components/typography/elements/Div.tsx), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts), `ErrorCollector` (code/core/src/telemetry/error-collector.ts), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx), `EventType` (code/core/src/telemetry/types.ts), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts), `H1` (code/core/src/components/components/typography/elements/H1.tsx), `H2` (code/core/src/components/components/typography/elements/H2.tsx), `H3` (code/core/src/components/components/typography/elements/H3.tsx), `H4` (code/core/src/components/components/typography/elements/H4.tsx), `H5` (code/core/src/components/components/typography/elements/H5.tsx), `H6` (code/core/src/components/components/typography/elements/H6.tsx), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts), `HR` (code/core/src/components/components/typography/elements/HR.tsx), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts), `IStory` (code/frameworks/angular/src/client/types.ts), `InitPayload` (code/core/src/telemetry/types.ts), `LI` (code/core/src/components/components/typography/elements/LI.tsx), `LinkProps` (code/core/src/router/types.ts), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx), `Location` (code/core/src/router/router.tsx), `LocationProvider` (code/core/src/router/router.tsx), `LogLevel` (code/core/src/node-logger/logger/logger.ts), `MemoryRouter` (code/core/src/router/router.tsx), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts), `NavigateFunction` (code/core/src/router/types.ts), `NavigateOptions` (code/core/src/router/types.ts), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts), `OL` (code/core/src/components/components/typography/elements/OL.tsx), `Other` (code/core/src/router/types.ts), `P` (code/core/src/components/components/typography/elements/P.tsx), `Payload` (code/core/src/telemetry/types.ts), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx), `Popover` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts), `PreactRenderer` (code/renderers/preact/src/types.ts), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx), `RenderData` (code/core/src/router/types.ts), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx), `Route` (code/core/src/router/router.tsx), `RouterData` (code/core/src/router/types.ts), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx), `Separator` (code/core/src/components/components/Bar/Separator.tsx), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx), `Span` (code/core/src/components/components/typography/elements/Span.tsx), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts), `StaticStory` (code/core/src/csf-tools/CsfFile.ts), `StoryData` (code/core/src/router/utils.ts), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts), `StoryTest` (code/core/src/csf-tools/CsfFile.ts), `StorybookAddon` (code/core/src/telemetry/types.ts), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx), `StorybookMetadata` (code/core/src/telemetry/types.ts), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts), `SvelteRenderer` (code/renderers/svelte/src/types.ts), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `TT` (code/core/src/components/components/typography/elements/TT.tsx), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx), `TabButton` (code/core/src/components/components/Tabs/Button.tsx), `TabList` (code/core/src/components/components/Tabs/TabList.tsx), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `TelemetryData` (code/core/src/telemetry/types.ts), `TelemetryEvent` (code/core/src/telemetry/types.ts), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts), `UL` (code/core/src/components/components/typography/elements/UL.tsx), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts), `WebComponentsStory` (code/renderers/web-components/src/preview.ts), `WebComponentsTypes` (code/renderers/web-components/src/types.ts), `WebsocketTransport` (code/core/src/channels/websocket/index.ts), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts), `babelParseExpression` (code/core/src/babel/babelParse.ts), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts), `babelPrint` (code/core/src/babel/babelParse.ts), `buildArgsParam` (code/core/src/router/utils.ts), `buildDevStandalone` (code/core/src/core-server/build-dev.ts), `buildIndexStandalone` (code/core/src/core-server/build-index.ts), `buildStaticStandalone` (code/core/src/core-server/build-static.ts), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts), `cleanPaths` (code/core/src/telemetry/sanitize.ts), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx), `colors` (code/core/src/node-logger/index.ts), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts), `components` (code/core/src/components/index.ts), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `createBrowserChannel` (code/core/src/channels/index.ts), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts), `experimental_loadStorybook` (code/core/src/core-server/load.ts), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts), `extractSource` (code/core/src/csf-tools/enrichCsf.ts), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts), `formatCsf` (code/core/src/csf-tools/CsfFile.ts), `framework` (code/core/src/core-server/presets/common-override-preset.ts), `generate` (code/core/src/babel/index.ts), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts), `getCustomElements` (code/renderers/web-components/src/framework-api.ts), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts), `getLastEvents` (code/core/src/telemetry/event-cache.ts), `getMatch` (code/core/src/router/utils.ts), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts), `getServerPort` (code/core/src/core-server/utils/server-address.ts), `getSessionId` (code/core/src/telemetry/session-id.ts), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts), `hrefTo` (code/addons/links/src/utils.ts), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts), `isExampleStoryId` (code/core/src/telemetry/index.ts), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts), `isValidComponent` (code/renderers/web-components/src/framework-api.ts), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts), `linkTo` (code/addons/links/src/utils.ts), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts), `loadCsf` (code/core/src/csf-tools/CsfFile.ts), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx), `navigate` (code/addons/links/src/utils.ts), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts), `parsePath` (code/core/src/router/utils.ts), `parserOptions` (code/core/src/babel/babelParse.ts), `printConfig` (code/core/src/csf-tools/ConfigFile.ts), `printCsf` (code/core/src/csf-tools/CsfFile.ts), `prompt` (code/core/src/node-logger/prompts/index.ts), `protectUrls` (code/core/src/node-logger/wrap-utils.ts), `queryFromLocation` (code/core/src/router/utils.ts), `readConfig` (code/core/src/csf-tools/ConfigFile.ts), `readCsf` (code/core/src/csf-tools/CsfFile.ts), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts), `resetComponents` (code/core/src/components/index.ts), `resolveExpression` (code/core/src/babel/expression-resolver.ts), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts), `sanitizeError` (code/core/src/telemetry/sanitize.ts), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts), `setCustomElements` (code/renderers/web-components/src/framework-api.ts), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts), `stories` (code/core/src/core-server/presets/common-override-preset.ts), `stringifyQuery` (code/core/src/router/utils.ts), `telemetry` (code/core/src/telemetry/index.ts), `traverse` (code/core/src/babel/index.ts), `typescript` (code/core/src/core-server/presets/common-override-preset.ts), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts), `useNavigate` (code/core/src/router/router.tsx), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `withLinks` (code/addons/links/src/utils.ts), `withReset` (code/core/src/components/components/typography/lib/common.tsx), `withTelemetry` (code/core/src/core-server/withTelemetry.ts), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts), `writeCsf` (code/core/src/csf-tools/CsfFile.ts)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 29.64% |
| Signature Accuracy | 85% |
| Type Coverage | 25.13% |

**Notes (coverage-check §2 to §4b):**

- **Deep-tier version check:** `gh api repos/storybookjs/storybook/commits/v10.3.5` resolves to `e486d3826bcd40c52db1c766966d1c8ec16df6cb`, the `metadata.source_commit` the workspace HEAD matched at init.
- **Extraction:** status `ok` (1274 files in scope, no truncation). ast-grep reported a syntax error in 5 files (`code/core/src/csf/csf-factories.ts:75`, `code/core/src/instrumenter/typings.d.ts:8`, `code/core/src/mocking-utils/esmWalker.ts:37`, `code/core/src/test/spy.ts:15`, `code/core/src/typings.d.ts:28`); 7 names no recipe found (`BabelFile`, `GeneratorOptions`, `NodePath`, `analyzeMdx`, `babelParse`, `instance`, `transformSync`), all in the scoped-out `code/core/src/babel/**`, with no file to read.
- **Guards:** `guards.deflation` fires (`stats.effective_denominator` 216 against 985 re-derived, 356%) and `guards.inflation` fires (scope.include union 985 against 222 provenance entries, 344%); `guards.umbrella.umbrella` is true (50 of 54 root names are re-exports), so the protocol recommends `stats.effective_denominator` over `scope.tier_a_include`. The brief's `code/core/**` glob still sweeps in `code/core/src/cli`, `common`, `core-events`, `docs-tools`, `manager-api` types, `shared` and similar infrastructure, which is most of the 693 missing names. `guards.staleScope` does not fire.
- **Signature comparison:** 80 documented signatures compared, 12 mismatches (Primary, Stories, Story, Description and Docs props; `action`; builder-vite `start`, `build`, `hasVitePlugins`, `withoutVitePlugins`; the storybook/preview-api `composeStories` and `composeStory`). `composeStories`, `composeStory` and `setProjectAnnotations` resolve on the surface to `code/core/src/preview-api/modules/store/csf/portable-stories.ts`; the @storybook/react wrappers at `code/renderers/react/src/portable-stories.tsx:46,100,121` match `references/story-types.md`, the preview-api declarations do not match `references/core-api.md:94-95`.
- **Numerator ground truth:** not inflated (declared 82, verified 82).
- **Stale names (160):** `classify-stale` marks 14 names fabricated, 73 with a live declaration (documented extras) and 73 other. Checked by hand, 13 of the 14 fabricated flags are tool artifacts, not fabrication: `fireEvent`, `screen`, `waitFor`, `within` are destructured exports (`export const { ..., fireEvent, ..., screen, waitFor, ..., within, ... } = testingLibrary`, `code/core/src/test/testing-library.ts:39-112`), `userEvent` is `export const { userEvent } = instrument(...)` (`testing-library.ts:123`), and `ComponentEntry`, `DocsEntry`, `GroupEntry`, `HashEntry`, `IndexHash`, `LeafEntry`, `RootEntry`, `StoryEntry` are `export type { API_X as X }` aliases (`code/core/src/manager-api/root.tsx:302-316`) of the `API_*` declarations the skill cites. Only `definePreview` is a genuine wrong citation: `code/core/src/preview-api/index.ts` does not export it; it comes from `@storybook/react-vite` (`code/frameworks/react-vite/src/index.ts:2`, `export { __definePreview as definePreview }`) and `storybook/internal/csf` (`code/core/src/csf/csf-factories.ts:45`). Among the "other" stale names, `expect` (`export const { expect } = instrument(...)`, `code/core/src/test/index.ts:24`) and `Mock`, `MockInstance`, `MaybeMocked` (`export type * from '@vitest/spy'`, `code/core/src/test/spy.ts:15`) are also real exports the recipe runner cannot see. The gaps are recorded as the scripts classify them.
- **Metadata coherence (§4b):** `stats.exports_public_api` 216 against `exports[]` length 82 (62% drift) and `stats.exports_documented` 216 against 222 provenance entries and a 572 confidence-distribution sum (62% drift): two Medium `metadata-drift` findings and one Info `multi-denominator`.
- **Provenance line check (§4c):** 222 map entries checked; 79 `line-not-definition` (most cite line 1 of a barrel or index file rather than the declaration) and 2 `file-missing`, recorded as Low `provenance-line` or Info `provenance-unverified` gaps.
- **Split-body cross-check (§1b):** 1 mismatch, `composeStories` (SKILL.md:117 against `references/story-types.md:181`).

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| 1 | missing_section | High | naive-coherence: missing required section: api_surface. No heading matches the API-surface family (`tried`: API, API Surface, Exports, Key Exports, Public API, Interface, Reference, Key API Summary, Pattern Surface, Component Catalog), and no body section lists the library's exports: `Key Types (quick-start essentials)` (line 149) names three types, `v10 Import Corrections` (line 125) lists three import-path rewrites, and `Full API Reference` (line 182) is a stub that points to `references/`. The Tier 1 `Key API Summary` table of the SKF section catalog is absent. | — |

**Structural Issues:** 1

Checks with no finding: §2.1 `description` (matched `Overview`, line 20) and `usage` (matched `Quick Start`, line 29); §2.2 fences balanced (10 fences); §2.3 no bare opening fence; §2.4 every documented function export is referenced in Quick Start, Common Workflows or a reference file (`zero_usage` empty, 196 exports counted); §2.5 no export is described as async or sync against its examples (`composeStories`, `definePreview`, `fn`, `getByRole`, `setProjectAnnotations` and `storybookTest` are called in examples, none with an async or sync claim); §2.6 no table drift; §2.7 no `scripts/` or `assets/` folder.

**Migration section (§2b):** Section 4b verification skipped: `forge-data/oms-storybook-react-vite/10.3.5/evidence-report.md` has no YAML frontmatter, so `t2_future_count` cannot be read (Case 4).

**Notes outside the scored checks:** SKILL.md:151 says `A11yTestMode` and `Framework` live in `references/story-types.md`, which documents neither. SKILL.md:184 states "~430 extracted exports across core (`storybook` 28 subpaths ≈ 350 exports)" while SKILL.md:22 and :25 say 40 subpaths and metadata.json records 216 documented exports.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| 1 | references/story-types.md | `composeStories` | SKILL.md recommends `import { composeStories } from 'storybook/preview-api'` (or `@storybook/react`); the reference says prefer `@storybook/react-vite` and keep the `storybook/preview-api` re-export for non-renderer infrastructure code | 117 | 181 |

**Exports Cross-Checked:** 18 (`Meta` type, `StoryObj`, `Preview`, `fn`, `expect`, `useArgs`, `useState`, `useParameter`, `composeStories`, `setProjectAnnotations`, `withThemeByClassName`, `withThemeByDataAttribute`, `withThemeFromJSXProvider`, and the `Meta`, `Canvas`, `Controls`, `Primary`, `Stories` doc blocks)
**Mismatches Found:** 1 (recorded by coverage-check §1b)

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

**Result:** **FAIL**, not scored: the hard gate blocked this run on 28 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 951
**Blocking (Critical + High):** 28
**Non-blocking (Medium + Low + Info):** 923

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 26 | Read the source code and write or correct the documentation |
| High | 2 | Read the source code and write or correct the documentation |
| Medium | 814 | Add type definitions, interface docs or the missing section |
| Low | 34 | Add examples or metadata |
| Info | 75 | Optional improvements, no action required |
| **Total** | **951** | |

### GAP-001: Signature mismatch: Description

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Description.tsx:74
**Export:** Description

**Issue:** documented `{ of?, markdown? }`, source `FC<DescriptionProps> where DescriptionProps = { of?: Of }`: documented prop `markdown` does not exist on DescriptionProps

**Remediation:** Update the documented signature of `Description` from `{ of?, markdown? }` to `FC<DescriptionProps> where DescriptionProps = { of?: Of }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Description.tsx:74`.

### GAP-002: Signature mismatch: Docs

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Docs.tsx:17
**Export:** Docs

**Issue:** documented `{ context }`, source `Docs<TRenderer>({ context, docsParameter }: DocsProps<TRenderer>) where DocsProps = { docsParameter: Parameters; context: DocsContextProps<TRenderer> }`: required prop `docsParameter: Parameters` is missing from the documented props

**Remediation:** Update the documented signature of `Docs` from `{ context }` to `Docs<TRenderer>({ context, docsParameter }: DocsProps<TRenderer>) where DocsProps = { docsParameter: Parameters; context: DocsContextProps<TRenderer> }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Docs.tsx:17`.

### GAP-003: Signature mismatch: Primary

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Primary.tsx:16
**Export:** Primary

**Issue:** documented `{ of? }`, source `FC = () => (PrimaryImpl takes no props; Primary = withMdxComponentOverride('Primary', PrimaryImpl))`: documented prop `of` does not exist: the v10 Primary block takes no props and always renders the attached meta's primary story

**Remediation:** Update the documented signature of `Primary` from `{ of? }` to `FC = () => (PrimaryImpl takes no props; Primary = withMdxComponentOverride('Primary', PrimaryImpl))`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Primary.tsx:16`.

### GAP-004: Signature mismatch: Stories

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Stories.tsx:74
**Export:** Stories

**Issue:** documented `{ of?, includePrimary?, title? }`, source `FC<StoriesProps> where StoriesProps = { title?: ReactElement | string; includePrimary?: boolean }`: documented prop `of` does not exist on StoriesProps

**Remediation:** Update the documented signature of `Stories` from `{ of?, includePrimary?, title? }` to `FC<StoriesProps> where StoriesProps = { title?: ReactElement | string; includePrimary?: boolean }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Stories.tsx:74`.

### GAP-005: Signature mismatch: Story

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:134
**Export:** Story

**Issue:** documented `{ of, expanded, ... }`, source `FC<StoryProps> where StoryProps = { of?: ModuleExport; meta?: ModuleExports } & { inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?; __primary? }`: documented prop `expanded` does not exist on StoryProps (it belongs to DocsStoryProps)

**Remediation:** Update the documented signature of `Story` from `{ of, expanded, ... }` to `FC<StoryProps> where StoryProps = { of?: ModuleExport; meta?: ModuleExports } & { inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?; __primary? }`, the signature the source defines at `code/addons/docs/src/blocks/blocks/Story.tsx:134`.

### GAP-006: Signature mismatch: start

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/builders/builder-vite/src/index.ts:41
**Export:** start

**Issue:** documented `start(options: BuilderOptions): Promise<{ bail, stats, totalTime }>`, source `start: ViteBuilder['start'] = async ({ startTime, options, router, server }) => ... i.e. (args: { options: Options; startTime; router: ServerApp; server: HttpServer; channel: ChannelLike }) => Promise<void | { stats?, totalTime, bail }>`: the single parameter is an args object carrying options: Options plus startTime, router, server and channel, not `options: BuilderOptions` ({ viteConfigPath? }); the return type is Promise<void | {...}>

**Remediation:** Update the documented signature of `start` from `start(options: BuilderOptions): Promise<{ bail, stats, totalTime }>` to `start: ViteBuilder['start'] = async ({ startTime, options, router, server }) => ... i.e. (args: { options: Options; startTime; router: ServerApp; server: HttpServer; channel: ChannelLike }) => Promise<void | { stats?, totalTime, bail }>`, the signature the source defines at `code/builders/builder-vite/src/index.ts:41`.

### GAP-007: Signature mismatch: build

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/builders/builder-vite/src/index.ts:63
**Export:** build

**Issue:** documented `build(options: BuilderOptions): Promise<any>`, source `build: ViteBuilder['build'] = async ({ options }) => ... i.e. (arg: { options: Options; startTime }) => Promise<void | ViteStats>`: the single parameter is an args object { options: Options; startTime }, not `options: BuilderOptions`

**Remediation:** Update the documented signature of `build` from `build(options: BuilderOptions): Promise<any>` to `build: ViteBuilder['build'] = async ({ options }) => ... i.e. (arg: { options: Options; startTime }) => Promise<void | ViteStats>`, the signature the source defines at `code/builders/builder-vite/src/index.ts:63`.

### GAP-008: Signature mismatch: hasVitePlugins

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/builders/builder-vite/src/utils/has-vite-plugins.ts:13
**Export:** hasVitePlugins

**Issue:** documented `hasVitePlugins(config: InlineConfig): boolean`, source `async function hasVitePlugins(plugins: PluginOption[], names: string[]): Promise<boolean>`: takes (plugins: PluginOption[], names: string[]), not a Vite InlineConfig, and is async (returns Promise<boolean>)

**Remediation:** Update the documented signature of `hasVitePlugins` from `hasVitePlugins(config: InlineConfig): boolean` to `async function hasVitePlugins(plugins: PluginOption[], names: string[]): Promise<boolean>`, the signature the source defines at `code/builders/builder-vite/src/utils/has-vite-plugins.ts:13`.

### GAP-009: Signature mismatch: withoutVitePlugins

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/builders/builder-vite/src/utils/without-vite-plugins.ts:2
**Export:** withoutVitePlugins

**Issue:** documented `withoutVitePlugins(config: InlineConfig): InlineConfig`, source `withoutVitePlugins = async <TPlugin>(plugins: TPlugin[] = [], namesToRemove: string[]): Promise<TPlugin[]>`: takes (plugins: TPlugin[], namesToRemove: string[]) and returns Promise<TPlugin[]>, not (config: InlineConfig) => InlineConfig

**Remediation:** Update the documented signature of `withoutVitePlugins` from `withoutVitePlugins(config: InlineConfig): InlineConfig` to `withoutVitePlugins = async <TPlugin>(plugins: TPlugin[] = [], namesToRemove: string[]): Promise<TPlugin[]>`, the signature the source defines at `code/builders/builder-vite/src/utils/without-vite-plugins.ts:2`.

### GAP-010: Signature mismatch: action

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/actions/runtime/action.ts:50
**Export:** action

**Issue:** documented `action(name: string)`, source `action(name: string, options: ActionOptions = {}): HandlerFunction`: missing optional parameter 'options: ActionOptions' and the HandlerFunction return type

**Remediation:** Update the documented signature of `action` from `action(name: string)` to `action(name: string, options: ActionOptions = {}): HandlerFunction`, the signature the source defines at `code/core/src/actions/runtime/action.ts:50`.

### GAP-011: Signature mismatch: composeStory

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:90
**Export:** composeStory

**Issue:** documented `composeStory(story, componentAnnotations, projectAnnotations?, exportsName?)`, source `composeStory<TRenderer, TArgs>(storyAnnotations: LegacyStoryAnnotationsOrFn<TRenderer>, componentAnnotations: ComponentAnnotations<TRenderer, TArgs>, projectAnnotations?: ProjectAnnotations<TRenderer>, defaultConfig?: ProjectAnnotations<TRenderer>, exportsName?: string): ComposedStoryFn<TRenderer, Partial<TArgs>>`: the storybook/preview-api export (documented at core-api.md:94) has a `defaultConfig?` parameter before `exportsName`, so the documented 4th argument lands in defaultConfig; only the @storybook/react wrapper has the documented 4-parameter order

**Remediation:** Update the documented signature of `composeStory` from `composeStory(story, componentAnnotations, projectAnnotations?, exportsName?)` to `composeStory<TRenderer, TArgs>(storyAnnotations: LegacyStoryAnnotationsOrFn<TRenderer>, componentAnnotations: ComponentAnnotations<TRenderer, TArgs>, projectAnnotations?: ProjectAnnotations<TRenderer>, defaultConfig?: ProjectAnnotations<TRenderer>, exportsName?: string): ComposedStoryFn<TRenderer, Partial<TArgs>>`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:90`.

### GAP-012: Signature mismatch: composeStories

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:274
**Export:** composeStories

**Issue:** documented `composeStories(csfExports: TModule, projectAnnotations?: ProjectAnnotations<ReactRenderer>)`, source `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory)`: the storybook/preview-api export (documented at core-api.md:95 and recommended by SKILL.md:117) requires `globalConfig` and takes a third `composeStoryFn` parameter; the documented one-optional-argument form is only the @storybook/react renderer wrapper's signature

**Remediation:** Update the documented signature of `composeStories` from `composeStories(csfExports: TModule, projectAnnotations?: ProjectAnnotations<ReactRenderer>)` to `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory)`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:274`.

### GAP-726: Fabricated signature: ComponentEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** ComponentEntry

**Issue:** SKILL.md documents `ComponentEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `ComponentEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:27`).

### GAP-733: Fabricated signature: DocsEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** DocsEntry

**Issue:** SKILL.md documents `DocsEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `DocsEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:34`).

### GAP-740: Fabricated signature: GroupEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** GroupEntry

**Issue:** SKILL.md documents `GroupEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `GroupEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:21`).

### GAP-744: Fabricated signature: HashEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** HashEntry

**Issue:** SKILL.md documents `HashEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `HashEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:67`).

### GAP-746: Fabricated signature: IndexHash

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** IndexHash

**Issue:** SKILL.md documents `IndexHash`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `IndexHash` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:80`).

### GAP-749: Fabricated signature: LeafEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** LeafEntry

**Issue:** SKILL.md documents `LeafEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `LeafEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:66`).

### GAP-766: Fabricated signature: RootEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** RootEntry

**Issue:** SKILL.md documents `RootEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `RootEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:15`).

### GAP-777: Fabricated signature: StoryEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** StoryEntry

**Issue:** SKILL.md documents `StoryEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `StoryEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:45`).

### GAP-819: Fabricated signature: definePreview

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/preview-api/index.ts:1
**Export:** definePreview

**Issue:** SKILL.md documents `definePreview`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `definePreview` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/preview-api/index.ts:1`).

### GAP-827: Fabricated signature: fireEvent

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:43
**Export:** fireEvent

**Issue:** SKILL.md documents `fireEvent`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `fireEvent` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:43`).

### GAP-850: Fabricated signature: screen

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:107
**Export:** screen

**Issue:** SKILL.md documents `screen`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `screen` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:107`).

### GAP-861: Fabricated signature: userEvent

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:123
**Export:** userEvent

**Issue:** SKILL.md documents `userEvent`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `userEvent` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:123`).

### GAP-863: Fabricated signature: waitFor

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:108
**Export:** waitFor

**Issue:** SKILL.md documents `waitFor`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `waitFor` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:108`).

### GAP-865: Fabricated signature: within

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:110
**Export:** within

**Issue:** SKILL.md documents `within`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `within` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:110`).

### GAP-950: Split-body mismatch: composeStories

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/story-types.md:181
**Export:** composeStories

**Issue:** SKILL.md:117 (authoritative body) tells the reader to `import { composeStories } from 'storybook/preview-api'` (or '@storybook/react') and call `composeStories(stories)`; references/story-types.md:181 says to prefer '@storybook/react-vite' and that the storybook/preview-api re-export is not framework-specific and should only be used by non-renderer infrastructure code (references/core-api.md:17 also names @storybook/react-vite as canonical).

**Remediation:** Make references/story-types.md:181 and SKILL.md:117 agree on one import path for composeStories. The source supports the reference: the storybook/preview-api composeStories (code/core/src/preview-api/modules/store/csf/portable-stories.ts:274) requires a globalConfig argument and a composeStoryFn, while the one-argument React form is the @storybook/react / @storybook/react-vite wrapper (code/renderers/react/src/portable-stories.tsx:121); so change SKILL.md:117 to `import { composeStories } from '@storybook/react-vite'` and keep the reference as written.

### GAP-951: naive-coherence: missing required section: api_surface

**Severity:** High
**Category:** Structural (structural)
**Source:** SKILL.md

**Issue:** no heading of SKILL.md serves the api_surface family (synonyms tried: API, API Surface, Exports, Key Exports, Public API, Interface, Reference, Key API Summary, Pattern Surface, Component Catalog)

**Remediation:** Add a `## Key API Summary` section to SKILL.md that lists the library's exports with their purpose.

### GAP-013: Missing export: ANGULAR_JSON_PATH

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/angular/helpers.ts:7
**Export:** ANGULAR_JSON_PATH

**Issue:** `ANGULAR_JSON_PATH` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ANGULAR_JSON_PATH` in SKILL.md: read its definition at `code/core/src/cli/angular/helpers.ts:7` and add its signature, its purpose and a usage example.

### GAP-014: Missing type: API

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/manager-api/root.tsx:96
**Export:** API

**Issue:** the type `API` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:96` and list its fields or members.

### GAP-015: Missing type: API_ActiveTabsType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:111
**Export:** API_ActiveTabsType

**Issue:** the type `API_ActiveTabsType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_ActiveTabsType` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:111` and list its fields or members.

### GAP-016: Missing type: API_BaseEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:6
**Export:** API_BaseEntry

**Issue:** the type `API_BaseEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_BaseEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:6` and list its fields or members.

### GAP-017: Missing type: API_ComponentEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** API_ComponentEntry

**Issue:** the type `API_ComponentEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_ComponentEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:27` and list its fields or members.

### GAP-018: Missing type: API_ComposedRef

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:163
**Export:** API_ComposedRef

**Issue:** the type `API_ComposedRef` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_ComposedRef` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:163` and list its fields or members.

### GAP-019: Missing type: API_ComposedRefUpdate

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:177
**Export:** API_ComposedRefUpdate

**Issue:** the type `API_ComposedRefUpdate` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_ComposedRefUpdate` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:177` and list its fields or members.

### GAP-020: Missing type: API_DocsEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** API_DocsEntry

**Issue:** the type `API_DocsEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_DocsEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:34` and list its fields or members.

### GAP-021: Missing type: API_FilterFunction

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:128
**Export:** API_FilterFunction

**Issue:** the type `API_FilterFunction` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_FilterFunction` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:128` and list its fields or members.

### GAP-022: Missing type: API_GroupEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** API_GroupEntry

**Issue:** the type `API_GroupEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_GroupEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:21` and list its fields or members.

### GAP-023: Missing type: API_HashEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** API_HashEntry

**Issue:** the type `API_HashEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_HashEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:67` and list its fields or members.

### GAP-024: Missing type: API_IframeRenderer

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:57
**Export:** API_IframeRenderer

**Issue:** the type `API_IframeRenderer` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_IframeRenderer` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:57` and list its fields or members.

### GAP-025: Missing type: API_IndexHash

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** API_IndexHash

**Issue:** the type `API_IndexHash` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_IndexHash` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:80` and list its fields or members.

### GAP-026: Missing type: API_Layout

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:79
**Export:** API_Layout

**Issue:** the type `API_Layout` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_Layout` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:79` and list its fields or members.

### GAP-027: Missing type: API_LayoutCustomisations

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:98
**Export:** API_LayoutCustomisations

**Issue:** the type `API_LayoutCustomisations` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_LayoutCustomisations` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:98` and list its fields or members.

### GAP-028: Missing type: API_LeafEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** API_LeafEntry

**Issue:** the type `API_LeafEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_LeafEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:66` and list its fields or members.

### GAP-029: Missing type: API_LoadedRefData

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:156
**Export:** API_LoadedRefData

**Issue:** the type `API_LoadedRefData` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_LoadedRefData` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:156` and list its fields or members.

### GAP-030: Missing type: API_MatchOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:30
**Export:** API_MatchOptions

**Issue:** the type `API_MatchOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_MatchOptions` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:30` and list its fields or members.

### GAP-031: Missing type: API_Notification

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:132
**Export:** API_Notification

**Issue:** the type `API_Notification` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_Notification` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:132` and list its fields or members.

### GAP-032: Missing type: API_OptionsData

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:96
**Export:** API_OptionsData

**Issue:** the type `API_OptionsData` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_OptionsData` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:96` and list its fields or members.

### GAP-033: Missing type: API_PanelPositions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:110
**Export:** API_PanelPositions

**Issue:** the type `API_PanelPositions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_PanelPositions` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:110` and list its fields or members.

### GAP-034: Missing type: API_PreparedIndexEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:85
**Export:** API_PreparedIndexEntry

**Issue:** the type `API_PreparedIndexEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_PreparedIndexEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:85` and list its fields or members.

### GAP-035: Missing type: API_PreparedStoryIndex

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:91
**Export:** API_PreparedStoryIndex

**Issue:** the type `API_PreparedStoryIndex` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_PreparedStoryIndex` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:91` and list its fields or members.

### GAP-036: Missing type: API_Provider

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:44
**Export:** API_Provider

**Issue:** the type `API_Provider` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_Provider` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:44` and list its fields or members.

### GAP-037: Missing type: API_ProviderData

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:39
**Export:** API_ProviderData

**Issue:** the type `API_ProviderData` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_ProviderData` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:39` and list its fields or members.

### GAP-038: Missing type: API_RefId

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:196
**Export:** API_RefId

**Issue:** the type `API_RefId` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_RefId` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:196` and list its fields or members.

### GAP-039: Missing type: API_RefUrl

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:197
**Export:** API_RefUrl

**Issue:** the type `API_RefUrl` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_RefUrl` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:197` and list its fields or members.

### GAP-040: Missing type: API_Refs

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:195
**Export:** API_Refs

**Issue:** the type `API_Refs` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_Refs` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:195` and list its fields or members.

### GAP-041: Missing type: API_ReleaseNotes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:100
**Export:** API_ReleaseNotes

**Issue:** the type `API_ReleaseNotes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_ReleaseNotes` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:100` and list its fields or members.

### GAP-042: Missing type: API_RenderOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:22
**Export:** API_RenderOptions

**Issue:** the type `API_RenderOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_RenderOptions` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:22` and list its fields or members.

### GAP-043: Missing type: API_RootEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** API_RootEntry

**Issue:** the type `API_RootEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_RootEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:15` and list its fields or members.

### GAP-044: Missing type: API_RouteOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:24
**Export:** API_RouteOptions

**Issue:** the type `API_RouteOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_RouteOptions` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:24` and list its fields or members.

### GAP-045: Missing type: API_SetRefData

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:147
**Export:** API_SetRefData

**Issue:** the type `API_SetRefData` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_SetRefData` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:147` and list its fields or members.

### GAP-046: Missing type: API_Settings

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:106
**Export:** API_Settings

**Issue:** the type `API_Settings` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_Settings` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:106` and list its fields or members.

### GAP-047: Missing type: API_SidebarOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:113
**Export:** API_SidebarOptions

**Issue:** the type `API_SidebarOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_SidebarOptions` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:113` and list its fields or members.

### GAP-048: Missing type: API_StateMerger

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:37
**Export:** API_StateMerger

**Issue:** the type `API_StateMerger` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_StateMerger` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:37` and list its fields or members.

### GAP-049: Missing type: API_StoryEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** API_StoryEntry

**Issue:** the type `API_StoryEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_StoryEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:45` and list its fields or members.

### GAP-050: Missing type: API_StoryMapper

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:154
**Export:** API_StoryMapper

**Issue:** the type `API_StoryMapper` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_StoryMapper` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:154` and list its fields or members.

### GAP-051: Missing type: API_TestEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:62
**Export:** API_TestEntry

**Issue:** the type `API_TestEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_TestEntry` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:62` and list its fields or members.

### GAP-052: Missing type: API_UI

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:104
**Export:** API_UI

**Issue:** the type `API_UI` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_UI` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:104` and list its fields or members.

### GAP-053: Missing type: API_UIOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:66
**Export:** API_UIOptions

**Issue:** the type `API_UIOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_UIOptions` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:66` and list its fields or members.

### GAP-054: Missing type: API_UnknownEntries

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:116
**Export:** API_UnknownEntries

**Issue:** the type `API_UnknownEntries` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_UnknownEntries` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:116` and list its fields or members.

### GAP-055: Missing type: API_Version

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:110
**Export:** API_Version

**Issue:** the type `API_Version` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_Version` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:110` and list its fields or members.

### GAP-056: Missing type: API_Versions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api-stories.ts:122
**Export:** API_Versions

**Issue:** the type `API_Versions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_Versions` in SKILL.md: read its definition at `code/core/src/types/modules/api-stories.ts:122` and list its fields or members.

### GAP-057: Missing type: API_ViewMode

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:20
**Export:** API_ViewMode

**Issue:** the type `API_ViewMode` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `API_ViewMode` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:20` and list its fields or members.

### GAP-058: Missing type: ActionsTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/actions/types.ts:51
**Export:** ActionsTypes

**Issue:** the type `ActionsTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ActionsTypes` in SKILL.md: read its definition at `code/core/src/actions/types.ts:51` and list its fields or members.

### GAP-059: Missing export: ActiveTabs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/root.tsx:78
**Export:** ActiveTabs

**Issue:** `ActiveTabs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ActiveTabs` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:78` and add its signature, its purpose and a usage example.

### GAP-060: Missing type: Actor

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/universal-store/types.ts:11
**Export:** Actor

**Issue:** the type `Actor` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Actor` in SKILL.md: read its definition at `code/core/src/shared/universal-store/types.ts:11` and list its fields or members.

### GAP-061: Missing export: AddContext

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:27
**Export:** AddContext

**Issue:** `AddContext` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AddContext` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:27` and add its signature, its purpose and a usage example.

### GAP-062: Missing type: AddonStore

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/manager-api/lib/addons.ts:31
**Export:** AddonStore

**Issue:** the type `AddonStore` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddonStore` in SKILL.md: read its definition at `code/core/src/manager-api/lib/addons.ts:31` and list its fields or members.

### GAP-063: Missing type: AddonTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:187
**Export:** AddonTypes

**Issue:** the type `AddonTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddonTypes` in SKILL.md: read its definition at `code/core/src/csf/story.ts:187` and list its fields or members.

### GAP-064: Missing type: AddonVitestCompatibilityOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/cli/AddonVitestService.ts:23
**Export:** AddonVitestCompatibilityOptions

**Issue:** the type `AddonVitestCompatibilityOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddonVitestCompatibilityOptions` in SKILL.md: read its definition at `code/core/src/cli/AddonVitestService.ts:23` and list its fields or members.

### GAP-065: Missing type: AddonVitestPostinstallConfigUpdateError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:501
**Export:** AddonVitestPostinstallConfigUpdateError

**Issue:** the type `AddonVitestPostinstallConfigUpdateError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddonVitestPostinstallConfigUpdateError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:501` and list its fields or members.

### GAP-066: Missing type: AddonVitestPostinstallError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:517
**Export:** AddonVitestPostinstallError

**Issue:** the type `AddonVitestPostinstallError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddonVitestPostinstallError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:517` and list its fields or members.

### GAP-067: Missing type: AddonVitestPostinstallFailedAddonA11yError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:473
**Export:** AddonVitestPostinstallFailedAddonA11yError

**Issue:** the type `AddonVitestPostinstallFailedAddonA11yError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddonVitestPostinstallFailedAddonA11yError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:473` and list its fields or members.

### GAP-068: Missing type: AddonVitestPostinstallPrerequisiteCheckError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:460
**Export:** AddonVitestPostinstallPrerequisiteCheckError

**Issue:** the type `AddonVitestPostinstallPrerequisiteCheckError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddonVitestPostinstallPrerequisiteCheckError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:460` and list its fields or members.

### GAP-069: Missing type: AddonVitestPostinstallWorkspaceUpdateError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:485
**Export:** AddonVitestPostinstallWorkspaceUpdateError

**Issue:** the type `AddonVitestPostinstallWorkspaceUpdateError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddonVitestPostinstallWorkspaceUpdateError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:485` and list its fields or members.

### GAP-070: Missing type: AddonVitestService

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/cli/AddonVitestService.ts:39
**Export:** AddonVitestService

**Issue:** the type `AddonVitestService` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddonVitestService` in SKILL.md: read its definition at `code/core/src/cli/AddonVitestService.ts:39` and list its fields or members.

### GAP-071: Missing type: Addon_AddStoryArgs

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:123
**Export:** Addon_AddStoryArgs

**Issue:** the type `Addon_AddStoryArgs` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_AddStoryArgs` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:123` and list its fields or members.

### GAP-072: Missing type: Addon_Annotations

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:216
**Export:** Addon_Annotations

**Issue:** the type `Addon_Annotations` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Annotations` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:216` and list its fields or members.

### GAP-073: Missing type: Addon_ArgType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:31
**Export:** Addon_ArgType

**Issue:** the type `Addon_ArgType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_ArgType` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:31` and list its fields or members.

### GAP-074: Missing type: Addon_ArgsStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:96
**Export:** Addon_ArgsStoryFn

**Issue:** the type `Addon_ArgsStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_ArgsStoryFn` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:96` and list its fields or members.

### GAP-075: Missing type: Addon_BaseAnnotations

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:170
**Export:** Addon_BaseAnnotations

**Issue:** the type `Addon_BaseAnnotations` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_BaseAnnotations` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:170` and list its fields or members.

### GAP-076: Missing type: Addon_BaseDecorators

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:166
**Export:** Addon_BaseDecorators

**Issue:** the type `Addon_BaseDecorators` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_BaseDecorators` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:166` and list its fields or members.

### GAP-077: Missing type: Addon_BaseMeta

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:251
**Export:** Addon_BaseMeta

**Issue:** the type `Addon_BaseMeta` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_BaseMeta` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:251` and list its fields or members.

### GAP-078: Missing type: Addon_BaseStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:312
**Export:** Addon_BaseStoryFn

**Issue:** the type `Addon_BaseStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_BaseStoryFn` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:312` and list its fields or members.

### GAP-079: Missing type: Addon_BaseStoryObject

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:307
**Export:** Addon_BaseStoryObject

**Issue:** the type `Addon_BaseStoryObject` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_BaseStoryObject` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:307` and list its fields or members.

### GAP-080: Missing type: Addon_BaseType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:329
**Export:** Addon_BaseType

**Issue:** the type `Addon_BaseType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_BaseType` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:329` and list its fields or members.

### GAP-081: Missing type: Addon_ClientApiAddon

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:131
**Export:** Addon_ClientApiAddon

**Issue:** the type `Addon_ClientApiAddon` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_ClientApiAddon` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:131` and list its fields or members.

### GAP-082: Missing type: Addon_ClientApiAddons

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:135
**Export:** Addon_ClientApiAddons

**Issue:** the type `Addon_ClientApiAddons` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_ClientApiAddons` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:135` and list its fields or members.

### GAP-083: Missing type: Addon_ClientApiReturnFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:139
**Export:** Addon_ClientApiReturnFn

**Issue:** the type `Addon_ClientApiReturnFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_ClientApiReturnFn` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:139` and list its fields or members.

### GAP-084: Missing type: Addon_ClientStoryApi

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:158
**Export:** Addon_ClientStoryApi

**Issue:** the type `Addon_ClientStoryApi` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_ClientStoryApi` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:158` and list its fields or members.

### GAP-085: Missing type: Addon_Collection

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:470
**Export:** Addon_Collection

**Issue:** the type `Addon_Collection` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Collection` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:470` and list its fields or members.

### GAP-086: Missing type: Addon_Comparator

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:42
**Export:** Addon_Comparator

**Issue:** the type `Addon_Comparator` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Comparator` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:42` and list its fields or members.

### GAP-087: Missing type: Addon_Config

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:479
**Export:** Addon_Config

**Issue:** the type `Addon_Config` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Config` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:479` and list its fields or members.

### GAP-088: Missing type: Addon_DecoratorFunction

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:103
**Export:** Addon_DecoratorFunction

**Issue:** the type `Addon_DecoratorFunction` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_DecoratorFunction` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:103` and list its fields or members.

### GAP-089: Missing type: Addon_Elements

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:473
**Export:** Addon_Elements

**Issue:** the type `Addon_Elements` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Elements` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:473` and list its fields or members.

### GAP-090: Missing type: Addon_LegacyStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:93
**Export:** Addon_LegacyStoryFn

**Issue:** the type `Addon_LegacyStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_LegacyStoryFn` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:93` and list its fields or members.

### GAP-091: Missing type: Addon_LoadFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:160
**Export:** Addon_LoadFn

**Issue:** the type `Addon_LoadFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_LoadFn` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:160` and list its fields or members.

### GAP-092: Missing type: Addon_Loadable

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:162
**Export:** Addon_Loadable

**Issue:** the type `Addon_Loadable` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Loadable` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:162` and list its fields or members.

### GAP-093: Missing type: Addon_Loader

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:465
**Export:** Addon_Loader

**Issue:** the type `Addon_Loader` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Loader` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:465` and list its fields or members.

### GAP-094: Missing type: Addon_LoaderFunction

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:106
**Export:** Addon_LoaderFunction

**Issue:** the type `Addon_LoaderFunction` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_LoaderFunction` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:106` and list its fields or members.

### GAP-095: Missing type: Addon_Loaders

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:467
**Export:** Addon_Loaders

**Issue:** the type `Addon_Loaders` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Loaders` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:467` and list its fields or members.

### GAP-096: Missing type: Addon_MakeDecoratorResult

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:121
**Export:** Addon_MakeDecoratorResult

**Issue:** the type `Addon_MakeDecoratorResult` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_MakeDecoratorResult` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:121` and list its fields or members.

### GAP-097: Missing type: Addon_OptionsParameter

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:63
**Export:** Addon_OptionsParameter

**Issue:** the type `Addon_OptionsParameter` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_OptionsParameter` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:63` and list its fields or members.

### GAP-098: Missing type: Addon_OptionsParameterV7

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:72
**Export:** Addon_OptionsParameterV7

**Issue:** the type `Addon_OptionsParameterV7` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_OptionsParameterV7` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:72` and list its fields or members.

### GAP-099: Missing type: Addon_PageType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:393
**Export:** Addon_PageType

**Issue:** the type `Addon_PageType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_PageType` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:393` and list its fields or members.

### GAP-100: Missing type: Addon_PartialStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:90
**Export:** Addon_PartialStoryFn

**Issue:** the type `Addon_PartialStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_PartialStoryFn` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:90` and list its fields or members.

### GAP-101: Missing type: Addon_RenderOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:320
**Export:** Addon_RenderOptions

**Issue:** the type `Addon_RenderOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_RenderOptions` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:320` and list its fields or members.

### GAP-102: Missing type: Addon_RequireContext

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:161
**Export:** Addon_RequireContext

**Issue:** the type `Addon_RequireContext` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_RequireContext` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:161` and list its fields or members.

### GAP-103: Missing type: Addon_StoryApi

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:143
**Export:** Addon_StoryApi

**Issue:** the type `Addon_StoryApi` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StoryApi` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:143` and list its fields or members.

### GAP-104: Missing type: Addon_StoryContext

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:81
**Export:** Addon_StoryContext

**Issue:** the type `Addon_StoryContext` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StoryContext` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:81` and list its fields or members.

### GAP-105: Missing type: Addon_StoryContextUpdate

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:83
**Export:** Addon_StoryContextUpdate

**Issue:** the type `Addon_StoryContextUpdate` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StoryContextUpdate` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:83` and list its fields or members.

### GAP-106: Missing type: Addon_StoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:99
**Export:** Addon_StoryFn

**Issue:** the type `Addon_StoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StoryFn` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:99` and list its fields or members.

### GAP-107: Missing type: Addon_StorySortComparator

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:54
**Export:** Addon_StorySortComparator

**Issue:** the type `Addon_StorySortComparator` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StorySortComparator` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:54` and list its fields or members.

### GAP-108: Missing type: Addon_StorySortComparatorV7

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:56
**Export:** Addon_StorySortComparatorV7

**Issue:** the type `Addon_StorySortComparatorV7` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StorySortComparatorV7` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:56` and list its fields or members.

### GAP-109: Missing type: Addon_StorySortMethod

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:43
**Export:** Addon_StorySortMethod

**Issue:** the type `Addon_StorySortMethod` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StorySortMethod` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:43` and list its fields or members.

### GAP-110: Missing type: Addon_StorySortObjectParameter

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:44
**Export:** Addon_StorySortObjectParameter

**Issue:** the type `Addon_StorySortObjectParameter` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StorySortObjectParameter` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:44` and list its fields or members.

### GAP-111: Missing type: Addon_StorySortParameter

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:55
**Export:** Addon_StorySortParameter

**Issue:** the type `Addon_StorySortParameter` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StorySortParameter` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:55` and list its fields or members.

### GAP-112: Missing type: Addon_StorySortParameterV7

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:57
**Export:** Addon_StorySortParameterV7

**Issue:** the type `Addon_StorySortParameterV7` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StorySortParameterV7` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:57` and list its fields or members.

### GAP-113: Missing type: Addon_StoryWrapper

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:115
**Export:** Addon_StoryWrapper

**Issue:** the type `Addon_StoryWrapper` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_StoryWrapper` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:115` and list its fields or members.

### GAP-114: Missing type: Addon_TestProviderType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:444
**Export:** Addon_TestProviderType

**Issue:** the type `Addon_TestProviderType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_TestProviderType` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:444` and list its fields or members.

### GAP-115: Missing type: Addon_ToolbarConfig

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:476
**Export:** Addon_ToolbarConfig

**Issue:** the type `Addon_ToolbarConfig` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_ToolbarConfig` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:476` and list its fields or members.

### GAP-116: Missing type: Addon_Type

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:324
**Export:** Addon_Type

**Issue:** the type `Addon_Type` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Type` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:324` and list its fields or members.

### GAP-117: Missing type: Addon_Types

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:26
**Export:** Addon_Types

**Issue:** the type `Addon_Types` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_Types` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:26` and list its fields or members.

### GAP-118: Missing type: Addon_TypesEnum

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:493
**Export:** Addon_TypesEnum

**Issue:** the type `Addon_TypesEnum` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_TypesEnum` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:493` and list its fields or members.

### GAP-119: Missing type: Addon_TypesMapping

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:459
**Export:** Addon_TypesMapping

**Issue:** the type `Addon_TypesMapping` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_TypesMapping` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:459` and list its fields or members.

### GAP-120: Missing type: Addon_WrapperSettings

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:108
**Export:** Addon_WrapperSettings

**Issue:** the type `Addon_WrapperSettings` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_WrapperSettings` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:108` and list its fields or members.

### GAP-121: Missing type: Addon_WrapperType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:425
**Export:** Addon_WrapperType

**Issue:** the type `Addon_WrapperType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addon_WrapperType` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:425` and list its fields or members.

### GAP-122: Missing type: Addons_ArgTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:35
**Export:** Addons_ArgTypes

**Issue:** the type `Addons_ArgTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Addons_ArgTypes` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:35` and list its fields or members.

### GAP-123: Missing type: AfterEach

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:262
**Export:** AfterEach

**Issue:** the type `AfterEach` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AfterEach` in SKILL.md: read its definition at `code/core/src/csf/story.ts:262` and list its fields or members.

### GAP-124: Missing export: AnchorMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:98
**Export:** AnchorMdx

**Issue:** `AnchorMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnchorMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:98` and add its signature, its purpose and a usage example.

### GAP-125: Missing type: AnchorProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Anchor.tsx:6
**Export:** AnchorProps

**Issue:** the type `AnchorProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AnchorProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Anchor.tsx:6` and list its fields or members.

### GAP-126: Missing type: AngularJSON

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/cli/angular/helpers.ts:9
**Export:** AngularJSON

**Issue:** the type `AngularJSON` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AngularJSON` in SKILL.md: read its definition at `code/core/src/cli/angular/helpers.ts:9` and list its fields or members.

### GAP-127: Missing type: AngularLegacyBuildOptionsError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:241
**Export:** AngularLegacyBuildOptionsError

**Issue:** the type `AngularLegacyBuildOptionsError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AngularLegacyBuildOptionsError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:241` and list its fields or members.

### GAP-128: Missing type: AnnotatedStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:575
**Export:** AnnotatedStoryFn

**Issue:** the type `AnnotatedStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AnnotatedStoryFn` in SKILL.md: read its definition at `code/core/src/csf/story.ts:575` and list its fields or members.

### GAP-129: Missing type: AnyFramework

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:217
**Export:** AnyFramework

**Issue:** the type `AnyFramework` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AnyFramework` in SKILL.md: read its definition at `code/core/src/csf/story.ts:217` and list its fields or members.

### GAP-130: Missing type: ArgTypesEnhancer

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:233
**Export:** ArgTypesEnhancer

**Issue:** the type `ArgTypesEnhancer` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ArgTypesEnhancer` in SKILL.md: read its definition at `code/core/src/csf/story.ts:233` and list its fields or members.

### GAP-131: Missing type: ArgTypesExtractor

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/types.ts:8
**Export:** ArgTypesExtractor

**Issue:** the type `ArgTypesExtractor` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ArgTypesExtractor` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/types.ts:8` and list its fields or members.

### GAP-132: Missing type: ArgTypesRequestPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/argtypes-info.ts:3
**Export:** ArgTypesRequestPayload

**Issue:** the type `ArgTypesRequestPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ArgTypesRequestPayload` in SKILL.md: read its definition at `code/core/src/core-events/data/argtypes-info.ts:3` and list its fields or members.

### GAP-133: Missing type: ArgTypesResponsePayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/argtypes-info.ts:7
**Export:** ArgTypesResponsePayload

**Issue:** the type `ArgTypesResponsePayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ArgTypesResponsePayload` in SKILL.md: read its definition at `code/core/src/core-events/data/argtypes-info.ts:7` and list its fields or members.

### GAP-134: Missing type: ArgsEnhancer

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:230
**Export:** ArgsEnhancer

**Issue:** the type `ArgsEnhancer` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ArgsEnhancer` in SKILL.md: read its definition at `code/core/src/csf/story.ts:230` and list its fields or members.

### GAP-135: Missing type: ArgsFromMeta

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:585
**Export:** ArgsFromMeta

**Issue:** the type `ArgsFromMeta` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ArgsFromMeta` in SKILL.md: read its definition at `code/core/src/csf/story.ts:585` and list its fields or members.

### GAP-136: Missing type: ArgsStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:321
**Export:** ArgsStoryFn

**Issue:** the type `ArgsStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ArgsStoryFn` in SKILL.md: read its definition at `code/core/src/csf/story.ts:321` and list its fields or members.

### GAP-137: Missing type: AutomigrateError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:656
**Export:** AutomigrateError

**Issue:** the type `AutomigrateError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AutomigrateError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:656` and list its fields or members.

### GAP-138: Missing type: BackgroundTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/backgrounds/types.ts:56
**Export:** BackgroundTypes

**Issue:** the type `BackgroundTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BackgroundTypes` in SKILL.md: read its definition at `code/core/src/backgrounds/types.ts:56` and list its fields or members.

### GAP-139: Missing type: BackgroundsGlobals

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/backgrounds/types.ts:47
**Export:** BackgroundsGlobals

**Issue:** the type `BackgroundsGlobals` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BackgroundsGlobals` in SKILL.md: read its definition at `code/core/src/backgrounds/types.ts:47` and list its fields or members.

### GAP-140: Missing type: BaseAnnotations

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:347
**Export:** BaseAnnotations

**Issue:** the type `BaseAnnotations` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BaseAnnotations` in SKILL.md: read its definition at `code/core/src/csf/story.ts:347` and list its fields or members.

### GAP-141: Missing type: BaseIndexEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:67
**Export:** BaseIndexEntry

**Issue:** the type `BaseIndexEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BaseIndexEntry` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:67` and list its fields or members.

### GAP-142: Missing type: BaseIndexInput

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:105
**Export:** BaseIndexInput

**Issue:** the type `BaseIndexInput` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BaseIndexInput` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:105` and list its fields or members.

### GAP-143: Missing type: BaseStory

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:316
**Export:** BaseStory

**Issue:** the type `BaseStory` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BaseStory` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:316` and list its fields or members.

### GAP-144: Missing type: BeforeAll

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:256
**Export:** BeforeAll

**Issue:** the type `BeforeAll` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BeforeAll` in SKILL.md: read its definition at `code/core/src/csf/story.ts:256` and list its fields or members.

### GAP-145: Missing type: BeforeEach

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:258
**Export:** BeforeEach

**Issue:** the type `BeforeEach` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BeforeEach` in SKILL.md: read its definition at `code/core/src/csf/story.ts:258` and list its fields or members.

### GAP-146: Missing type: BoundStory

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/story.ts:124
**Export:** BoundStory

**Issue:** the type `BoundStory` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BoundStory` in SKILL.md: read its definition at `code/core/src/types/modules/story.ts:124` and list its fields or members.

### GAP-147: Missing type: Builder

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:259
**Export:** Builder

**Issue:** the type `Builder` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Builder` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:259` and list its fields or members.

### GAP-148: Missing type: BuilderName

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:20
**Export:** BuilderName

**Issue:** the type `BuilderName` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BuilderName` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:20` and list its fields or members.

### GAP-149: Missing type: BuilderResult

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:156
**Export:** BuilderResult

**Issue:** the type `BuilderResult` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BuilderResult` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:156` and list its fields or members.

### GAP-150: Missing type: BuilderStats

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/builder.ts:1
**Export:** BuilderStats

**Issue:** the type `BuilderStats` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BuilderStats` in SKILL.md: read its definition at `code/core/src/types/modules/builder.ts:1` and list its fields or members.

### GAP-151: Missing type: Builder_EnvsRaw

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/builder.ts:12
**Export:** Builder_EnvsRaw

**Issue:** the type `Builder_EnvsRaw` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Builder_EnvsRaw` in SKILL.md: read its definition at `code/core/src/types/modules/builder.ts:12` and list its fields or members.

### GAP-152: Missing type: Builder_Unpromise

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/builder.ts:10
**Export:** Builder_Unpromise

**Issue:** the type `Builder_Unpromise` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Builder_Unpromise` in SKILL.md: read its definition at `code/core/src/types/modules/builder.ts:10` and list its fields or members.

### GAP-153: Missing type: Builder_WithRequiredProperty

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/builder.ts:6
**Export:** Builder_WithRequiredProperty

**Issue:** the type `Builder_WithRequiredProperty` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Builder_WithRequiredProperty` in SKILL.md: read its definition at `code/core/src/types/modules/builder.ts:6` and list its fields or members.

### GAP-154: Missing export: CLEAR_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:5
**Export:** CLEAR_ID

**Issue:** `CLEAR_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CLEAR_ID` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:5` and add its signature, its purpose and a usage example.

### GAP-155: Missing type: CLIBaseOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:175
**Export:** CLIBaseOptions

**Issue:** the type `CLIBaseOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CLIBaseOptions` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:175` and list its fields or members.

### GAP-156: Missing type: CLIOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:184
**Export:** CLIOptions

**Issue:** the type `CLIOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CLIOptions` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:184` and list its fields or members.

### GAP-157: Missing export: COVERAGE_DIRECTORY

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:19
**Export:** COVERAGE_DIRECTORY

**Issue:** `COVERAGE_DIRECTORY` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COVERAGE_DIRECTORY` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:19` and add its signature, its purpose and a usage example.

### GAP-158: Missing export: CYCLIC_KEY

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:6
**Export:** CYCLIC_KEY

**Issue:** `CYCLIC_KEY` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CYCLIC_KEY` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:6` and add its signature, its purpose and a usage example.

### GAP-159: Missing type: Call

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/instrumenter/types.ts:7
**Export:** Call

**Issue:** the type `Call` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Call` in SKILL.md: read its definition at `code/core/src/instrumenter/types.ts:7` and list its fields or members.

### GAP-160: Missing type: CallRef

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/instrumenter/types.ts:37
**Export:** CallRef

**Issue:** the type `CallRef` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CallRef` in SKILL.md: read its definition at `code/core/src/instrumenter/types.ts:37` and list its fields or members.

### GAP-161: Missing type: CallStates

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/instrumenter/types.ts:30
**Export:** CallStates

**Issue:** the type `CallStates` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CallStates` in SKILL.md: read its definition at `code/core/src/instrumenter/types.ts:30` and list its fields or members.

### GAP-162: Missing type: CleanupCallback

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:254
**Export:** CleanupCallback

**Issue:** the type `CleanupCallback` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CleanupCallback` in SKILL.md: read its definition at `code/core/src/csf/story.ts:254` and list its fields or members.

### GAP-163: Missing export: CodeOrSourceMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:39
**Export:** CodeOrSourceMdx

**Issue:** `CodeOrSourceMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CodeOrSourceMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:39` and add its signature, its purpose and a usage example.

### GAP-164: Missing type: ColorProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/controls/index.tsx:10
**Export:** ColorProps

**Issue:** the type `ColorProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ColorProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/controls/index.tsx:10` and list its fields or members.

### GAP-165: Missing type: CommonJsConfigNotSupportedError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:639
**Export:** CommonJsConfigNotSupportedError

**Issue:** the type `CommonJsConfigNotSupportedError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CommonJsConfigNotSupportedError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:639` and list its fields or members.

### GAP-166: Missing type: CompatibleString

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:739
**Export:** CompatibleString

**Issue:** the type `CompatibleString` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CompatibleString` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:739` and list its fields or members.

### GAP-167: Missing type: CompileOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/mdx-loader.ts:7
**Export:** CompileOptions

**Issue:** the type `CompileOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CompileOptions` in SKILL.md: read its definition at `code/addons/docs/src/mdx-loader.ts:7` and list its fields or members.

### GAP-168: Missing type: Component

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/types.ts:7
**Export:** Component

**Issue:** the type `Component` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Component` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/types.ts:7` and list its fields or members.

### GAP-169: Missing type: ComponentId

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:9
**Export:** ComponentId

**Issue:** the type `ComponentId` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ComponentId` in SKILL.md: read its definition at `code/core/src/csf/story.ts:9` and list its fields or members.

### GAP-170: Missing type: ComponentManifest

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:357
**Export:** ComponentManifest

**Issue:** the type `ComponentManifest` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ComponentManifest` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:357` and list its fields or members.

### GAP-171: Missing type: ComponentTitle

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:10
**Export:** ComponentTitle

**Issue:** the type `ComponentTitle` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ComponentTitle` in SKILL.md: read its definition at `code/core/src/csf/story.ts:10` and list its fields or members.

### GAP-172: Missing type: ComponentsManifest

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:375
**Export:** ComponentsManifest

**Issue:** the type `ComponentsManifest` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ComponentsManifest` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:375` and list its fields or members.

### GAP-173: Missing type: ComposeStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/composedStory.ts:76
**Export:** ComposeStoryFn

**Issue:** the type `ComposeStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ComposeStoryFn` in SKILL.md: read its definition at `code/core/src/types/modules/composedStory.ts:76` and list its fields or members.

### GAP-174: Missing type: ComposedStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/composedStory.ts:40
**Export:** ComposedStoryFn

**Issue:** the type `ComposedStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ComposedStoryFn` in SKILL.md: read its definition at `code/core/src/types/modules/composedStory.ts:40` and list its fields or members.

### GAP-175: Missing type: Conditional

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:58
**Export:** Conditional

**Issue:** the type `Conditional` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Conditional` in SKILL.md: read its definition at `code/core/src/csf/story.ts:58` and list its fields or members.

### GAP-176: Missing type: ConflictingStaticDirConfigError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:120
**Export:** ConflictingStaticDirConfigError

**Issue:** the type `ConflictingStaticDirConfigError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ConflictingStaticDirConfigError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:120` and list its fields or members.

### GAP-177: Missing export: Consumer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/root.tsx:316
**Export:** Consumer

**Issue:** `Consumer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Consumer` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:316` and add its signature, its purpose and a usage example.

### GAP-178: Missing type: ControlStates

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/instrumenter/types.ts:51
**Export:** ControlStates

**Issue:** the type `ControlStates` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ControlStates` in SKILL.md: read its definition at `code/core/src/instrumenter/types.ts:51` and list its fields or members.

### GAP-179: Missing type: ControlsTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/controls/types.ts:55
**Export:** ControlsTypes

**Issue:** the type `ControlsTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ControlsTypes` in SKILL.md: read its definition at `code/core/src/controls/types.ts:55` and list its fields or members.

### GAP-180: Missing type: CoreCommon_AddonEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:706
**Export:** CoreCommon_AddonEntry

**Issue:** the type `CoreCommon_AddonEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CoreCommon_AddonEntry` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:706` and list its fields or members.

### GAP-181: Missing type: CoreCommon_AddonInfo

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:707
**Export:** CoreCommon_AddonInfo

**Issue:** the type `CoreCommon_AddonInfo` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CoreCommon_AddonInfo` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:707` and list its fields or members.

### GAP-182: Missing type: CoreCommon_OptionsEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:705
**Export:** CoreCommon_OptionsEntry

**Issue:** the type `CoreCommon_OptionsEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CoreCommon_OptionsEntry` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:705` and list its fields or members.

### GAP-183: Missing type: CoreCommon_ResolvedAddonPreset

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:690
**Export:** CoreCommon_ResolvedAddonPreset

**Issue:** the type `CoreCommon_ResolvedAddonPreset` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CoreCommon_ResolvedAddonPreset` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:690` and list its fields or members.

### GAP-184: Missing type: CoreCommon_ResolvedAddonVirtual

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:697
**Export:** CoreCommon_ResolvedAddonVirtual

**Issue:** the type `CoreCommon_ResolvedAddonVirtual` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CoreCommon_ResolvedAddonVirtual` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:697` and list its fields or members.

### GAP-185: Missing type: CoreCommon_StorybookInfo

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:709
**Export:** CoreCommon_StorybookInfo

**Issue:** the type `CoreCommon_StorybookInfo` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CoreCommon_StorybookInfo` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:709` and list its fields or members.

### GAP-186: Missing type: CoreConfig

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:23
**Export:** CoreConfig

**Issue:** the type `CoreConfig` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CoreConfig` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:23` and list its fields or members.

### GAP-187: Missing type: CoreTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/core-annotations.ts:23
**Export:** CoreTypes

**Issue:** the type `CoreTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CoreTypes` in SKILL.md: read its definition at `code/core/src/csf/core-annotations.ts:23` and list its fields or members.

### GAP-188: Missing type: CoreWebpackCompiler

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/webpack.ts:1
**Export:** CoreWebpackCompiler

**Issue:** the type `CoreWebpackCompiler` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CoreWebpackCompiler` in SKILL.md: read its definition at `code/core/src/types/modules/webpack.ts:1` and list its fields or members.

### GAP-189: Missing type: CouldNotEvaluateFrameworkError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:103
**Export:** CouldNotEvaluateFrameworkError

**Issue:** the type `CouldNotEvaluateFrameworkError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CouldNotEvaluateFrameworkError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:103` and list its fields or members.

### GAP-190: Missing type: CreateNewStoryErrorPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/create-new-story.ts:21
**Export:** CreateNewStoryErrorPayload

**Issue:** the type `CreateNewStoryErrorPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CreateNewStoryErrorPayload` in SKILL.md: read its definition at `code/core/src/core-events/data/create-new-story.ts:21` and list its fields or members.

### GAP-191: Missing type: CreateNewStoryRequestPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/create-new-story.ts:1
**Export:** CreateNewStoryRequestPayload

**Issue:** the type `CreateNewStoryRequestPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CreateNewStoryRequestPayload` in SKILL.md: read its definition at `code/core/src/core-events/data/create-new-story.ts:1` and list its fields or members.

### GAP-192: Missing type: CreateNewStoryResponsePayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/create-new-story.ts:12
**Export:** CreateNewStoryResponsePayload

**Issue:** the type `CreateNewStoryResponsePayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CreateNewStoryResponsePayload` in SKILL.md: read its definition at `code/core/src/core-events/data/create-new-story.ts:12` and list its fields or members.

### GAP-193: Missing type: CriticalPresetLoadError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:260
**Export:** CriticalPresetLoadError

**Issue:** the type `CriticalPresetLoadError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CriticalPresetLoadError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:260` and list its fields or members.

### GAP-194: Missing type: CsfEnricher

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:388
**Export:** CsfEnricher

**Issue:** the type `CsfEnricher` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `CsfEnricher` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:388` and list its fields or members.

### GAP-195: Missing export: DEFAULT_FILES_PATTERN

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/normalize-stories.ts:15
**Export:** DEFAULT_FILES_PATTERN

**Issue:** `DEFAULT_FILES_PATTERN` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DEFAULT_FILES_PATTERN` in SKILL.md: read its definition at `code/core/src/common/utils/normalize-stories.ts:15` and add its signature, its purpose and a usage example.

### GAP-196: Missing export: DEFAULT_VIEWPORT

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/defaults.ts:232
**Export:** DEFAULT_VIEWPORT

**Issue:** `DEFAULT_VIEWPORT` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DEFAULT_VIEWPORT` in SKILL.md: read its definition at `code/core/src/viewport/defaults.ts:232` and add its signature, its purpose and a usage example.

### GAP-197: Missing export: DOCUMENTATION_FATAL_ERROR_LINK

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:17
**Export:** DOCUMENTATION_FATAL_ERROR_LINK

**Issue:** `DOCUMENTATION_FATAL_ERROR_LINK` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DOCUMENTATION_FATAL_ERROR_LINK` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:17` and add its signature, its purpose and a usage example.

### GAP-198: Missing export: DOCUMENTATION_LINK

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:16
**Export:** DOCUMENTATION_LINK

**Issue:** `DOCUMENTATION_LINK` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DOCUMENTATION_LINK` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:16` and add its signature, its purpose and a usage example.

### GAP-199: Missing type: DecoratorApplicator

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:336
**Export:** DecoratorApplicator

**Issue:** the type `DecoratorApplicator` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DecoratorApplicator` in SKILL.md: read its definition at `code/core/src/csf/story.ts:336` and list its fields or members.

### GAP-200: Missing type: DescriptionType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Description.tsx:9
**Export:** DescriptionType

**Issue:** the type `DescriptionType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DescriptionType` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Description.tsx:9` and list its fields or members.

### GAP-201: Missing type: DocgenFlowType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/types.ts:23
**Export:** DocgenFlowType

**Issue:** the type `DocgenFlowType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocgenFlowType` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/types.ts:23` and list its fields or members.

### GAP-202: Missing type: DocgenInfo

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/types.ts:42
**Export:** DocgenInfo

**Issue:** the type `DocgenInfo` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocgenInfo` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/types.ts:42` and list its fields or members.

### GAP-203: Missing type: DocgenPropDefaultValue

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/types.ts:36
**Export:** DocgenPropDefaultValue

**Issue:** the type `DocgenPropDefaultValue` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocgenPropDefaultValue` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/types.ts:36` and list its fields or members.

### GAP-204: Missing type: DocgenPropType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/types.ts:17
**Export:** DocgenPropType

**Issue:** the type `DocgenPropType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocgenPropType` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/types.ts:17` and list its fields or members.

### GAP-205: Missing type: DocgenType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/types.ts:10
**Export:** DocgenType

**Issue:** the type `DocgenType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocgenType` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/types.ts:10` and list its fields or members.

### GAP-206: Missing type: DocgenTypeScriptType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/types.ts:30
**Export:** DocgenTypeScriptType

**Issue:** the type `DocgenTypeScriptType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocgenTypeScriptType` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/types.ts:30` and list its fields or members.

### GAP-207: Missing type: DocsContainerProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18
**Export:** DocsContainerProps

**Issue:** the type `DocsContainerProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsContainerProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18` and list its fields or members.

### GAP-208: Missing type: DocsIndexEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:83
**Export:** DocsIndexEntry

**Issue:** the type `DocsIndexEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsIndexEntry` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:83` and list its fields or members.

### GAP-209: Missing type: DocsIndexInput

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:145
**Export:** DocsIndexInput

**Issue:** the type `DocsIndexInput` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsIndexInput` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:145` and list its fields or members.

### GAP-210: Missing type: DocsOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:313
**Export:** DocsOptions

**Issue:** the type `DocsOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsOptions` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:313` and list its fields or members.

### GAP-211: Missing type: DocsPreparedPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/channelApi.ts:75
**Export:** DocsPreparedPayload

**Issue:** the type `DocsPreparedPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsPreparedPayload` in SKILL.md: read its definition at `code/core/src/types/modules/channelApi.ts:75` and list its fields or members.

### GAP-212: Missing type: DocsProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Docs.tsx:12
**Export:** DocsProps

**Issue:** the type `DocsProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Docs.tsx:12` and list its fields or members.

### GAP-213: Missing type: DocsRenderFunction

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/docs.ts:109
**Export:** DocsRenderFunction

**Issue:** the type `DocsRenderFunction` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsRenderFunction` in SKILL.md: read its definition at `code/core/src/types/modules/docs.ts:109` and list its fields or members.

### GAP-214: Missing type: DocsStoryProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/types.ts:9
**Export:** DocsStoryProps

**Issue:** the type `DocsStoryProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsStoryProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/types.ts:9` and list its fields or members.

### GAP-215: Missing export: EVENTS

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/instrumenter/EVENTS.ts:1
**Export:** EVENTS

**Issue:** `EVENTS` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `EVENTS` in SKILL.md: read its definition at `code/core/src/instrumenter/EVENTS.ts:1` and add its signature, its purpose and a usage example.

### GAP-216: Missing export: EVENT_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:4
**Export:** EVENT_ID

**Issue:** `EVENT_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `EVENT_ID` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:4` and add its signature, its purpose and a usage example.

### GAP-217: Missing type: Easing

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/theming/types.ts:61
**Export:** Easing

**Issue:** the type `Easing` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Easing` in SKILL.md: read its definition at `code/core/src/theming/types.ts:61` and list its fields or members.

### GAP-218: Missing type: ElementA11yParameterError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-errors.ts:385
**Export:** ElementA11yParameterError

**Issue:** the type `ElementA11yParameterError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ElementA11yParameterError` in SKILL.md: read its definition at `code/core/src/preview-errors.ts:385` and list its fields or members.

### GAP-219: Missing type: ElementRef

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/instrumenter/types.ts:41
**Export:** ElementRef

**Issue:** the type `ElementRef` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ElementRef` in SKILL.md: read its definition at `code/core/src/instrumenter/types.ts:41` and list its fields or members.

### GAP-220: Missing type: Entry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:306
**Export:** Entry

**Issue:** the type `Entry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Entry` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:306` and list its fields or members.

### GAP-221: Missing type: Event

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/universal-store/types.ts:58
**Export:** Event

**Issue:** the type `Event` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Event` in SKILL.md: read its definition at `code/core/src/shared/universal-store/types.ts:58` and list its fields or members.

### GAP-222: Missing type: EventInfo

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/universal-store/types.ts:16
**Export:** EventInfo

**Issue:** the type `EventInfo` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `EventInfo` in SKILL.md: read its definition at `code/core/src/shared/universal-store/types.ts:16` and list its fields or members.

### GAP-223: Missing type: ExecuteCommandOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/utils/command.ts:19
**Export:** ExecuteCommandOptions

**Issue:** the type `ExecuteCommandOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ExecuteCommandOptions` in SKILL.md: read its definition at `code/core/src/common/utils/command.ts:19` and list its fields or members.

### GAP-224: Missing export: ExternalDocs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26
**Export:** ExternalDocs

**Issue:** `ExternalDocs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ExternalDocs` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26` and add its signature, its purpose and a usage example.

### GAP-225: Missing export: ExternalDocsContainer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12
**Export:** ExternalDocsContainer

**Issue:** `ExternalDocsContainer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ExternalDocsContainer` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12` and add its signature, its purpose and a usage example.

### GAP-226: Missing type: ExternalDocsProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11
**Export:** ExternalDocsProps

**Issue:** the type `ExternalDocsProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ExternalDocsProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11` and list its fields or members.

### GAP-227: Missing type: ExtractProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:17
**Export:** ExtractProps

**Issue:** the type `ExtractProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ExtractProps` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:17` and list its fields or members.

### GAP-228: Missing type: ExtractedJsDoc

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/jsdocParser.ts:23
**Export:** ExtractedJsDoc

**Issue:** the type `ExtractedJsDoc` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ExtractedJsDoc` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/jsdocParser.ts:23` and list its fields or members.

### GAP-229: Missing type: ExtractedJsDocParam

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/jsdocParser.ts:12
**Export:** ExtractedJsDocParam

**Issue:** the type `ExtractedJsDocParam` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ExtractedJsDocParam` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/jsdocParser.ts:12` and list its fields or members.

### GAP-230: Missing type: ExtractedJsDocReturns

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/jsdocParser.ts:18
**Export:** ExtractedJsDocReturns

**Issue:** the type `ExtractedJsDocReturns` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ExtractedJsDocReturns` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/jsdocParser.ts:18` and list its fields or members.

### GAP-231: Missing type: ExtractedProp

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:10
**Export:** ExtractedProp

**Issue:** the type `ExtractedProp` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ExtractedProp` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:10` and list its fields or members.

### GAP-232: Missing type: Feature

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/features.ts:1
**Export:** Feature

**Issue:** the type `Feature` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Feature` in SKILL.md: read its definition at `code/core/src/types/modules/features.ts:1` and list its fields or members.

### GAP-233: Missing type: FileComponentSearchRequestPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/file-component-search.ts:1
**Export:** FileComponentSearchRequestPayload

**Issue:** the type `FileComponentSearchRequestPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `FileComponentSearchRequestPayload` in SKILL.md: read its definition at `code/core/src/core-events/data/file-component-search.ts:1` and list its fields or members.

### GAP-234: Missing type: FileComponentSearchResponsePayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/file-component-search.ts:3
**Export:** FileComponentSearchResponsePayload

**Issue:** the type `FileComponentSearchResponsePayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `FileComponentSearchResponsePayload` in SKILL.md: read its definition at `code/core/src/core-events/data/file-component-search.ts:3` and list its fields or members.

### GAP-235: Missing type: FileOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/utils/cli.ts:24
**Export:** FileOptions

**Issue:** the type `FileOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `FileOptions` in SKILL.md: read its definition at `code/core/src/common/utils/cli.ts:24` and list its fields or members.

### GAP-236: Missing type: FileSystemCache

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/utils/file-cache.ts:29
**Export:** FileSystemCache

**Issue:** the type `FileSystemCache` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `FileSystemCache` in SKILL.md: read its definition at `code/core/src/common/utils/file-cache.ts:29` and list its fields or members.

### GAP-237: Missing type: FilterFunction

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/api.ts:77
**Export:** FilterFunction

**Issue:** the type `FilterFunction` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `FilterFunction` in SKILL.md: read its definition at `code/core/src/types/modules/api.ts:77` and list its fields or members.

### GAP-238: Missing type: FindPackageVersionsError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:580
**Export:** FindPackageVersionsError

**Issue:** the type `FindPackageVersionsError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `FindPackageVersionsError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:580` and list its fields or members.

### GAP-239: Missing type: GenerateNewProjectOnInitError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:441
**Export:** GenerateNewProjectOnInitError

**Issue:** the type `GenerateNewProjectOnInitError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `GenerateNewProjectOnInitError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:441` and list its fields or members.

### GAP-240: Missing type: GlobalStateUpdate

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:31
**Export:** GlobalStateUpdate

**Issue:** the type `GlobalStateUpdate` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `GlobalStateUpdate` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:31` and list its fields or members.

### GAP-241: Missing type: GlobalTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:168
**Export:** GlobalTypes

**Issue:** the type `GlobalTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `GlobalTypes` in SKILL.md: read its definition at `code/core/src/csf/story.ts:168` and list its fields or members.

### GAP-242: Missing type: GlobalsUpdatedPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/channelApi.ts:60
**Export:** GlobalsUpdatedPayload

**Issue:** the type `GlobalsUpdatedPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `GlobalsUpdatedPayload` in SKILL.md: read its definition at `code/core/src/types/modules/channelApi.ts:60` and list its fields or members.

### GAP-243: Missing type: GoogleFontsDownloadError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:305
**Export:** GoogleFontsDownloadError

**Issue:** the type `GoogleFontsDownloadError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `GoogleFontsDownloadError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:305` and list its fields or members.

### GAP-244: Missing type: GoogleFontsLoadingError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:319
**Export:** GoogleFontsLoadingError

**Issue:** the type `GoogleFontsLoadingError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `GoogleFontsLoadingError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:319` and list its fields or members.

### GAP-245: Missing type: HandledError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/utils/HandledError.ts:1
**Export:** HandledError

**Issue:** the type `HandledError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `HandledError` in SKILL.md: read its definition at `code/core/src/common/utils/HandledError.ts:1` and list its fields or members.

### GAP-246: Missing export: HeaderMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:215
**Export:** HeaderMdx

**Issue:** `HeaderMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HeaderMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:215` and add its signature, its purpose and a usage example.

### GAP-247: Missing export: HeadersMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:232
**Export:** HeadersMdx

**Issue:** `HeadersMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HeadersMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:232` and add its signature, its purpose and a usage example.

### GAP-248: Missing type: HeadingProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Heading.tsx:11
**Export:** HeadingProps

**Issue:** the type `HeadingProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `HeadingProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Heading.tsx:11` and list its fields or members.

### GAP-249: Missing type: HighlightTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/highlight/types.ts:3
**Export:** HighlightTypes

**Issue:** the type `HighlightTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `HighlightTypes` in SKILL.md: read its definition at `code/core/src/highlight/types.ts:3` and list its fields or members.

### GAP-250: Missing export: INITIAL_VIEWPORTS

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/defaults.ts:3
**Export:** INITIAL_VIEWPORTS

**Issue:** `INITIAL_VIEWPORTS` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `INITIAL_VIEWPORTS` in SKILL.md: read its definition at `code/core/src/viewport/defaults.ts:3` and add its signature, its purpose and a usage example.

### GAP-251: Missing type: IncompatiblePostCssConfigError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:595
**Export:** IncompatiblePostCssConfigError

**Issue:** the type `IncompatiblePostCssConfigError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `IncompatiblePostCssConfigError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:595` and list its fields or members.

### GAP-252: Missing type: IndexEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:88
**Export:** IndexEntry

**Issue:** the type `IndexEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `IndexEntry` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:88` and list its fields or members.

### GAP-253: Missing type: IndexEntryLegacy

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/addons.ts:53
**Export:** IndexEntryLegacy

**Issue:** the type `IndexEntryLegacy` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `IndexEntryLegacy` in SKILL.md: read its definition at `code/core/src/types/modules/addons.ts:53` and list its fields or members.

### GAP-254: Missing type: IndexInput

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:151
**Export:** IndexInput

**Issue:** the type `IndexInput` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `IndexInput` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:151` and list its fields or members.

### GAP-255: Missing type: IndexInputStats

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:90
**Export:** IndexInputStats

**Issue:** the type `IndexInputStats` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `IndexInputStats` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:90` and list its fields or members.

### GAP-256: Missing type: IndexedCSFFile

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:38
**Export:** IndexedCSFFile

**Issue:** the type `IndexedCSFFile` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `IndexedCSFFile` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:38` and list its fields or members.

### GAP-257: Missing type: IndexedStory

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:32
**Export:** IndexedStory

**Issue:** the type `IndexedStory` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `IndexedStory` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:32` and list its fields or members.

### GAP-258: Missing type: Indexer

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:56
**Export:** Indexer

**Issue:** the type `Indexer` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Indexer` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:56` and list its fields or members.

### GAP-259: Missing type: IndexerOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:28
**Export:** IndexerOptions

**Issue:** the type `IndexerOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `IndexerOptions` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:28` and list its fields or members.

### GAP-260: Missing type: InferTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/csf-factories.ts:41
**Export:** InferTypes

**Issue:** the type `InferTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `InferTypes` in SKILL.md: read its definition at `code/core/src/csf/csf-factories.ts:41` and list its fields or members.

### GAP-261: Missing type: InputType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:111
**Export:** InputType

**Issue:** the type `InputType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `InputType` in SKILL.md: read its definition at `code/core/src/csf/story.ts:111` and list its fields or members.

### GAP-262: Missing type: InstallationMetadata

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/js-package-manager/types.ts:2
**Export:** InstallationMetadata

**Issue:** the type `InstallationMetadata` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `InstallationMetadata` in SKILL.md: read its definition at `code/core/src/common/js-package-manager/types.ts:2` and list its fields or members.

### GAP-263: Missing type: InterPresetOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/presets.ts:24
**Export:** InterPresetOptions

**Issue:** the type `InterPresetOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `InterPresetOptions` in SKILL.md: read its definition at `code/core/src/common/presets.ts:24` and list its fields or members.

### GAP-264: Missing type: InvalidStoriesEntryError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:138
**Export:** InvalidStoriesEntryError

**Issue:** the type `InvalidStoriesEntryError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `InvalidStoriesEntryError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:138` and list its fields or members.

### GAP-265: Missing type: JsDocParam

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/PropDef.ts:3
**Export:** JsDocParam

**Issue:** the type `JsDocParam` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `JsDocParam` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/PropDef.ts:3` and list its fields or members.

### GAP-266: Missing type: JsDocParsingOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/jsdocParser.ts:30
**Export:** JsDocParsingOptions

**Issue:** the type `JsDocParsingOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `JsDocParsingOptions` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/jsdocParser.ts:30` and list its fields or members.

### GAP-267: Missing type: JsDocParsingResult

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/jsdocParser.ts:34
**Export:** JsDocParsingResult

**Issue:** the type `JsDocParsingResult` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `JsDocParsingResult` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/jsdocParser.ts:34` and list its fields or members.

### GAP-268: Missing type: JsDocReturns

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/PropDef.ts:8
**Export:** JsDocReturns

**Issue:** the type `JsDocReturns` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `JsDocReturns` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/PropDef.ts:8` and list its fields or members.

### GAP-269: Missing type: JsDocTags

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/PropDef.ts:12
**Export:** JsDocTags

**Issue:** the type `JsDocTags` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `JsDocTags` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/PropDef.ts:12` and list its fields or members.

### GAP-270: Missing type: JsPackageManager

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/js-package-manager/JsPackageManager.ts:70
**Export:** JsPackageManager

**Issue:** the type `JsPackageManager` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `JsPackageManager` in SKILL.md: read its definition at `code/core/src/common/js-package-manager/JsPackageManager.ts:70` and list its fields or members.

### GAP-271: Missing type: JsPackageManagerFactory

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/js-package-manager/JsPackageManagerFactory.ts:29
**Export:** JsPackageManagerFactory

**Issue:** the type `JsPackageManagerFactory` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `JsPackageManagerFactory` in SKILL.md: read its definition at `code/core/src/common/js-package-manager/JsPackageManagerFactory.ts:29` and list its fields or members.

### GAP-272: Missing type: KeyboardEventLike

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/manager-api/lib/shortcut.ts:14
**Export:** KeyboardEventLike

**Issue:** the type `KeyboardEventLike` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `KeyboardEventLike` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:14` and list its fields or members.

### GAP-273: Missing type: LegacyAnnotatedStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:565
**Export:** LegacyAnnotatedStoryFn

**Issue:** the type `LegacyAnnotatedStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `LegacyAnnotatedStoryFn` in SKILL.md: read its definition at `code/core/src/csf/story.ts:565` and list its fields or members.

### GAP-274: Missing type: LegacyStoryAnnotationsOrFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:571
**Export:** LegacyStoryAnnotationsOrFn

**Issue:** the type `LegacyStoryAnnotationsOrFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `LegacyStoryAnnotationsOrFn` in SKILL.md: read its definition at `code/core/src/csf/story.ts:571` and list its fields or members.

### GAP-275: Missing type: LegacyStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:316
**Export:** LegacyStoryFn

**Issue:** the type `LegacyStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `LegacyStoryFn` in SKILL.md: read its definition at `code/core/src/csf/story.ts:316` and list its fields or members.

### GAP-276: Missing type: LoadOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:165
**Export:** LoadOptions

**Issue:** the type `LoadOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `LoadOptions` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:165` and list its fields or members.

### GAP-277: Missing type: LoadedPreset

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:122
**Export:** LoadedPreset

**Issue:** the type `LoadedPreset` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `LoadedPreset` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:122` and list its fields or members.

### GAP-278: Missing type: LogItem

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/instrumenter/types.ts:60
**Export:** LogItem

**Issue:** the type `LogItem` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `LogItem` in SKILL.md: read its definition at `code/core/src/instrumenter/types.ts:60` and list its fields or members.

### GAP-279: Missing export: MAX_DEFAULT_VALUE_SUMMARY_LENGTH

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/utils.ts:4
**Export:** MAX_DEFAULT_VALUE_SUMMARY_LENGTH

**Issue:** `MAX_DEFAULT_VALUE_SUMMARY_LENGTH` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MAX_DEFAULT_VALUE_SUMMARY_LENGTH` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/utils.ts:4` and add its signature, its purpose and a usage example.

### GAP-280: Missing export: MAX_TYPE_SUMMARY_LENGTH

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/utils.ts:3
**Export:** MAX_TYPE_SUMMARY_LENGTH

**Issue:** `MAX_TYPE_SUMMARY_LENGTH` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MAX_TYPE_SUMMARY_LENGTH` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/utils.ts:3` and add its signature, its purpose and a usage example.

### GAP-281: Missing export: MINIMAL_VIEWPORTS

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/defaults.ts:234
**Export:** MINIMAL_VIEWPORTS

**Issue:** `MINIMAL_VIEWPORTS` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MINIMAL_VIEWPORTS` in SKILL.md: read its definition at `code/core/src/viewport/defaults.ts:234` and add its signature, its purpose and a usage example.

### GAP-282: Missing type: MainFileEvaluationError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:402
**Export:** MainFileEvaluationError

**Issue:** the type `MainFileEvaluationError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `MainFileEvaluationError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:402` and list its fields or members.

### GAP-283: Missing type: MainFileMissingError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:372
**Export:** MainFileMissingError

**Issue:** the type `MainFileMissingError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `MainFileMissingError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:372` and list its fields or members.

### GAP-284: Missing type: Manifests

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:386
**Export:** Manifests

**Issue:** the type `Manifests` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Manifests` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:386` and list its fields or members.

### GAP-285: Missing type: MdxCompileOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/mdx-loader.ts:5
**Export:** MdxCompileOptions

**Issue:** the type `MdxCompileOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `MdxCompileOptions` in SKILL.md: read its definition at `code/addons/docs/src/mdx-loader.ts:5` and list its fields or members.

### GAP-286: Missing type: MeasureTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/measure/types.ts:18
**Export:** MeasureTypes

**Issue:** the type `MeasureTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `MeasureTypes` in SKILL.md: read its definition at `code/core/src/measure/types.ts:18` and list its fields or members.

### GAP-287: Missing type: Middleware

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:236
**Export:** Middleware

**Issue:** the type `Middleware` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Middleware` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:236` and list its fields or members.

### GAP-288: Missing type: MissingAngularJsonError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:223
**Export:** MissingAngularJsonError

**Issue:** the type `MissingAngularJsonError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `MissingAngularJsonError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:223` and list its fields or members.

### GAP-289: Missing type: MissingBuilderError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:284
**Export:** MissingBuilderError

**Issue:** the type `MissingBuilderError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `MissingBuilderError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:284` and list its fields or members.

### GAP-290: Missing type: MockCall

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/mocking-utils/extract.ts:21
**Export:** MockCall

**Issue:** the type `MockCall` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `MockCall` in SKILL.md: read its definition at `code/core/src/mocking-utils/extract.ts:21` and list its fields or members.

### GAP-291: Missing type: ModuleExport

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/story.ts:32
**Export:** ModuleExport

**Issue:** the type `ModuleExport` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ModuleExport` in SKILL.md: read its definition at `code/core/src/types/modules/story.ts:32` and list its fields or members.

### GAP-292: Missing type: ModuleExports

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/story.ts:33
**Export:** ModuleExports

**Issue:** the type `ModuleExports` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ModuleExports` in SKILL.md: read its definition at `code/core/src/types/modules/story.ts:33` and list its fields or members.

### GAP-293: Missing type: ModuleImportFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/story.ts:34
**Export:** ModuleImportFn

**Issue:** the type `ModuleImportFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ModuleImportFn` in SKILL.md: read its definition at `code/core/src/types/modules/story.ts:34` and list its fields or members.

### GAP-294: Missing type: ModuleMockerInterceptor

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/mocking-utils/mocker-runtime.js:5
**Export:** ModuleMockerInterceptor

**Issue:** the type `ModuleMockerInterceptor` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ModuleMockerInterceptor` in SKILL.md: read its definition at `code/core/src/mocking-utils/mocker-runtime.js:5` and list its fields or members.

### GAP-295: Missing type: NamedOrDefaultProjectAnnotations

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/story.ts:52
**Export:** NamedOrDefaultProjectAnnotations

**Issue:** the type `NamedOrDefaultProjectAnnotations` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NamedOrDefaultProjectAnnotations` in SKILL.md: read its definition at `code/core/src/types/modules/story.ts:52` and list its fields or members.

### GAP-296: Missing type: NextJsSharpError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-errors.ts:315
**Export:** NextJsSharpError

**Issue:** the type `NextJsSharpError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NextJsSharpError` in SKILL.md: read its definition at `code/core/src/preview-errors.ts:315` and list its fields or members.

### GAP-297: Missing type: NextjsRouterMocksNotAvailable

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-errors.ts:332
**Export:** NextjsRouterMocksNotAvailable

**Issue:** the type `NextjsRouterMocksNotAvailable` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NextjsRouterMocksNotAvailable` in SKILL.md: read its definition at `code/core/src/preview-errors.ts:332` and list its fields or members.

### GAP-298: Missing type: NoMatchingExportError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:350
**Export:** NoMatchingExportError

**Issue:** the type `NoMatchingExportError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NoMatchingExportError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:350` and list its fields or members.

### GAP-299: Missing type: NoStatsForViteDevError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:566
**Export:** NoStatsForViteDevError

**Issue:** the type `NoStatsForViteDevError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NoStatsForViteDevError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:566` and list its fields or members.

### GAP-300: Missing type: Node

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/mocking-utils/esmWalker.ts:44
**Export:** Node

**Issue:** the type `Node` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Node` in SKILL.md: read its definition at `code/core/src/mocking-utils/esmWalker.ts:44` and list its fields or members.

### GAP-301: Missing type: NormalizedStoriesSpecifier

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:20
**Export:** NormalizedStoriesSpecifier

**Issue:** the type `NormalizedStoriesSpecifier` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NormalizedStoriesSpecifier` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:20` and list its fields or members.

### GAP-302: Missing type: NpmOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/cli/NpmOptions.ts:3
**Export:** NpmOptions

**Issue:** the type `NpmOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NpmOptions` in SKILL.md: read its definition at `code/core/src/cli/NpmOptions.ts:3` and list its fields or members.

### GAP-303: Missing type: Of

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/useOf.ts:11
**Export:** Of

**Issue:** the type `Of` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Of` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/useOf.ts:11` and list its fields or members.

### GAP-304: Missing type: OpenInEditorRequestPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/open-in-editor.ts:1
**Export:** OpenInEditorRequestPayload

**Issue:** the type `OpenInEditorRequestPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `OpenInEditorRequestPayload` in SKILL.md: read its definition at `code/core/src/core-events/data/open-in-editor.ts:1` and list its fields or members.

### GAP-305: Missing type: OpenInEditorResponsePayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/open-in-editor.ts:3
**Export:** OpenInEditorResponsePayload

**Issue:** the type `OpenInEditorResponsePayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `OpenInEditorResponsePayload` in SKILL.md: read its definition at `code/core/src/core-events/data/open-in-editor.ts:3` and list its fields or members.

### GAP-306: Missing type: OutlineTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/outline/types.ts:18
**Export:** OutlineTypes

**Issue:** the type `OutlineTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `OutlineTypes` in SKILL.md: read its definition at `code/core/src/outline/types.ts:18` and list its fields or members.

### GAP-307: Missing export: PANEL_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:3
**Export:** PANEL_ID

**Issue:** `PANEL_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PANEL_ID` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:3` and add its signature, its purpose and a usage example.

### GAP-308: Missing export: PRIMARY_STORY

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/types.ts:3
**Export:** PRIMARY_STORY

**Issue:** `PRIMARY_STORY` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PRIMARY_STORY` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/types.ts:3` and add its signature, its purpose and a usage example.

### GAP-309: Missing type: PackageJsonInfo

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/js-package-manager/JsPackageManager.ts:64
**Export:** PackageJsonInfo

**Issue:** the type `PackageJsonInfo` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PackageJsonInfo` in SKILL.md: read its definition at `code/core/src/common/js-package-manager/JsPackageManager.ts:64` and list its fields or members.

### GAP-310: Missing type: PackageJsonWithDepsAndDevDeps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/js-package-manager/PackageJson.ts:3
**Export:** PackageJsonWithDepsAndDevDeps

**Issue:** the type `PackageJsonWithDepsAndDevDeps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PackageJsonWithDepsAndDevDeps` in SKILL.md: read its definition at `code/core/src/common/js-package-manager/PackageJson.ts:3` and list its fields or members.

### GAP-311: Missing type: PackageJsonWithMaybeDeps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/js-package-manager/PackageJson.ts:6
**Export:** PackageJsonWithMaybeDeps

**Issue:** the type `PackageJsonWithMaybeDeps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PackageJsonWithMaybeDeps` in SKILL.md: read its definition at `code/core/src/common/js-package-manager/PackageJson.ts:6` and list its fields or members.

### GAP-312: Missing type: PackageManagerName

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/js-package-manager/JsPackageManager.ts:23
**Export:** PackageManagerName

**Issue:** the type `PackageManagerName` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PackageManagerName` in SKILL.md: read its definition at `code/core/src/common/js-package-manager/JsPackageManager.ts:23` and list its fields or members.

### GAP-313: Missing type: PackageMetadata

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/js-package-manager/types.ts:1
**Export:** PackageMetadata

**Issue:** the type `PackageMetadata` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PackageMetadata` in SKILL.md: read its definition at `code/core/src/common/js-package-manager/types.ts:1` and list its fields or members.

### GAP-314: Missing type: ParseJsDoc

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/jsdocParser.ts:41
**Export:** ParseJsDoc

**Issue:** the type `ParseJsDoc` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ParseJsDoc` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/jsdocParser.ts:41` and list its fields or members.

### GAP-315: Missing type: PartialArgsStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/composedStory.ts:30
**Export:** PartialArgsStoryFn

**Issue:** the type `PartialArgsStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PartialArgsStoryFn` in SKILL.md: read its definition at `code/core/src/types/modules/composedStory.ts:30` and list its fields or members.

### GAP-316: Missing type: PartialStoryFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:311
**Export:** PartialStoryFn

**Issue:** the type `PartialStoryFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PartialStoryFn` in SKILL.md: read its definition at `code/core/src/csf/story.ts:311` and list its fields or members.

### GAP-317: Missing type: Path

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/csf.ts:94
**Export:** Path

**Issue:** the type `Path` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Path` in SKILL.md: read its definition at `code/core/src/types/modules/csf.ts:94` and list its fields or members.

### GAP-318: Missing type: PlayFunctionContext

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:290
**Export:** PlayFunctionContext

**Issue:** the type `PlayFunctionContext` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PlayFunctionContext` in SKILL.md: read its definition at `code/core/src/csf/story.ts:290` and list its fields or members.

### GAP-319: Missing type: Positioned

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/mocking-utils/esmWalker.ts:39
**Export:** Positioned

**Issue:** the type `Positioned` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Positioned` in SKILL.md: read its definition at `code/core/src/mocking-utils/esmWalker.ts:39` and list its fields or members.

### GAP-320: Missing type: PreparedMeta

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/story.ts:117
**Export:** PreparedMeta

**Issue:** the type `PreparedMeta` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PreparedMeta` in SKILL.md: read its definition at `code/core/src/types/modules/story.ts:117` and list its fields or members.

### GAP-321: Missing type: Preset

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:298
**Export:** Preset

**Issue:** the type `Preset` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Preset` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:298` and list its fields or members.

### GAP-322: Missing type: PresetConfig

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:128
**Export:** PresetConfig

**Issue:** the type `PresetConfig` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PresetConfig` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:128` and list its fields or members.

### GAP-323: Missing type: PresetProperty

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:679
**Export:** PresetProperty

**Issue:** the type `PresetProperty` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PresetProperty` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:679` and list its fields or members.

### GAP-324: Missing type: PresetPropertyFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:683
**Export:** PresetPropertyFn

**Issue:** the type `PresetPropertyFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PresetPropertyFn` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:683` and list its fields or members.

### GAP-325: Missing type: PresetValue

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:677
**Export:** PresetValue

**Issue:** the type `PresetValue` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PresetValue` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:677` and list its fields or members.

### GAP-326: Missing type: Presets

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:72
**Export:** Presets

**Issue:** the type `Presets` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Presets` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:72` and list its fields or members.

### GAP-327: Missing type: PreviewAddon

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/csf-factories.ts:74
**Export:** PreviewAddon

**Issue:** the type `PreviewAddon` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PreviewAddon` in SKILL.md: read its definition at `code/core/src/csf/csf-factories.ts:74` and list its fields or members.

### GAP-328: Missing type: PreviewAnnotation

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:695
**Export:** PreviewAnnotation

**Issue:** the type `PreviewAnnotation` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PreviewAnnotation` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:695` and list its fields or members.

### GAP-329: Missing type: ProjectType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/cli/projectTypes.ts:1
**Export:** ProjectType

**Issue:** the type `ProjectType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ProjectType` in SKILL.md: read its definition at `code/core/src/cli/projectTypes.ts:1` and list its fields or members.

### GAP-330: Missing type: PropDef

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/PropDef.ts:25
**Export:** PropDef

**Issue:** the type `PropDef` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PropDef` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/PropDef.ts:25` and list its fields or members.

### GAP-331: Missing type: PropDefaultValue

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/PropDef.ts:23
**Export:** PropDefaultValue

**Issue:** the type `PropDefaultValue` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PropDefaultValue` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/PropDef.ts:23` and list its fields or members.

### GAP-332: Missing type: PropDescriptor

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/store/filterArgTypes.ts:5
**Export:** PropDescriptor

**Issue:** the type `PropDescriptor` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PropDescriptor` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/filterArgTypes.ts:5` and list its fields or members.

### GAP-333: Missing type: PropSummaryValue

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/PropDef.ts:17
**Export:** PropSummaryValue

**Issue:** the type `PropSummaryValue` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PropSummaryValue` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/PropDef.ts:17` and list its fields or members.

### GAP-334: Missing type: PropType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/PropDef.ts:22
**Export:** PropType

**Issue:** the type `PropType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PropType` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/PropDef.ts:22` and list its fields or members.

### GAP-335: Missing type: PropsExtractor

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/types.ts:6
**Export:** PropsExtractor

**Issue:** the type `PropsExtractor` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PropsExtractor` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/types.ts:6` and list its fields or members.

### GAP-336: Missing type: Provider

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/manager-api/root.tsx:316
**Export:** Provider

**Issue:** the type `Provider` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Provider` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:316` and list its fields or members.

### GAP-337: Missing type: ProviderDoesNotExtendBaseProviderError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/manager-errors.ts:23
**Export:** ProviderDoesNotExtendBaseProviderError

**Issue:** the type `ProviderDoesNotExtendBaseProviderError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ProviderDoesNotExtendBaseProviderError` in SKILL.md: read its definition at `code/core/src/manager-errors.ts:23` and list its fields or members.

### GAP-338: Missing type: ReactTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/renderers/react/src/types.ts:33
**Export:** ReactTypes

**Issue:** the type `ReactTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ReactTypes` in SKILL.md: read its definition at `code/renderers/react/src/types.ts:33` and list its fields or members.

### GAP-339: Missing type: Ref

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:135
**Export:** Ref

**Issue:** the type `Ref` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Ref` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:135` and list its fields or members.

### GAP-340: Missing type: RemoveAddonOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/utils/remove.ts:9
**Export:** RemoveAddonOptions

**Issue:** the type `RemoveAddonOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `RemoveAddonOptions` in SKILL.md: read its definition at `code/core/src/common/utils/remove.ts:9` and list its fields or members.

### GAP-341: Missing type: RenderContextCallbacks

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/docs.ts:14
**Export:** RenderContextCallbacks

**Issue:** the type `RenderContextCallbacks` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `RenderContextCallbacks` in SKILL.md: read its definition at `code/core/src/types/modules/docs.ts:14` and list its fields or members.

### GAP-342: Missing type: RenderPhase

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/preview-web/render/StoryRender.ts:36
**Export:** RenderPhase

**Issue:** the type `RenderPhase` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `RenderPhase` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/render/StoryRender.ts:36` and list its fields or members.

### GAP-343: Missing type: Renderer

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:193
**Export:** Renderer

**Issue:** the type `Renderer` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Renderer` in SKILL.md: read its definition at `code/core/src/csf/story.ts:193` and list its fields or members.

### GAP-344: Missing type: RendererName

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:21
**Export:** RendererName

**Issue:** the type `RendererName` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `RendererName` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:21` and list its fields or members.

### GAP-345: Missing type: Report

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/store/reporter-api.ts:1
**Export:** Report

**Issue:** the type `Report` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Report` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/reporter-api.ts:1` and list its fields or members.

### GAP-346: Missing type: ReporterAPI

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/store/reporter-api.ts:8
**Export:** ReporterAPI

**Issue:** the type `ReporterAPI` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ReporterAPI` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/reporter-api.ts:8` and list its fields or members.

### GAP-347: Missing type: RequestData

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/request-response.ts:1
**Export:** RequestData

**Issue:** the type `RequestData` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `RequestData` in SKILL.md: read its definition at `code/core/src/core-events/data/request-response.ts:1` and list its fields or members.

### GAP-348: Missing type: RequestResponseError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/manager-api/lib/request-response.ts:4
**Export:** RequestResponseError

**Issue:** the type `RequestResponseError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `RequestResponseError` in SKILL.md: read its definition at `code/core/src/manager-api/lib/request-response.ts:4` and list its fields or members.

### GAP-349: Missing type: ResolvedModuleExport

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/docs.ts:47
**Export:** ResolvedModuleExport

**Issue:** the type `ResolvedModuleExport` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ResolvedModuleExport` in SKILL.md: read its definition at `code/core/src/types/modules/docs.ts:47` and list its fields or members.

### GAP-350: Missing type: ResolvedModuleExportFromType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/docs.ts:34
**Export:** ResolvedModuleExportFromType

**Issue:** the type `ResolvedModuleExportFromType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ResolvedModuleExportFromType` in SKILL.md: read its definition at `code/core/src/types/modules/docs.ts:34` and list its fields or members.

### GAP-351: Missing type: ResolvedModuleExportType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/docs.ts:24
**Export:** ResolvedModuleExportType

**Issue:** the type `ResolvedModuleExportType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ResolvedModuleExportType` in SKILL.md: read its definition at `code/core/src/types/modules/docs.ts:24` and list its fields or members.

### GAP-352: Missing type: ResponseData

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/request-response.ts:6
**Export:** ResponseData

**Issue:** the type `ResponseData` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ResponseData` in SKILL.md: read its definition at `code/core/src/core-events/data/request-response.ts:6` and list its fields or members.

### GAP-353: Missing type: SBArrayType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:10
**Export:** SBArrayType

**Issue:** the type `SBArrayType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBArrayType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:10` and list its fields or members.

### GAP-354: Missing type: SBEnumType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:23
**Export:** SBEnumType

**Issue:** the type `SBEnumType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBEnumType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:23` and list its fields or members.

### GAP-355: Missing type: SBIntersectionType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:27
**Export:** SBIntersectionType

**Issue:** the type `SBIntersectionType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBIntersectionType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:27` and list its fields or members.

### GAP-356: Missing type: SBLiteralType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:35
**Export:** SBLiteralType

**Issue:** the type `SBLiteralType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBLiteralType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:35` and list its fields or members.

### GAP-357: Missing type: SBNodeType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:14
**Export:** SBNodeType

**Issue:** the type `SBNodeType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBNodeType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:14` and list its fields or members.

### GAP-358: Missing type: SBObjectType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:19
**Export:** SBObjectType

**Issue:** the type `SBObjectType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBObjectType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:19` and list its fields or members.

### GAP-359: Missing type: SBOtherType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:43
**Export:** SBOtherType

**Issue:** the type `SBOtherType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBOtherType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:43` and list its fields or members.

### GAP-360: Missing type: SBScalarType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:6
**Export:** SBScalarType

**Issue:** the type `SBScalarType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBScalarType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:6` and list its fields or members.

### GAP-361: Missing type: SBTupleType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:39
**Export:** SBTupleType

**Issue:** the type `SBTupleType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBTupleType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:39` and list its fields or members.

### GAP-362: Missing type: SBType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:48
**Export:** SBType

**Issue:** the type `SBType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:48` and list its fields or members.

### GAP-363: Missing type: SBUnionType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/SBType.ts:31
**Export:** SBUnionType

**Issue:** the type `SBUnionType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SBUnionType` in SKILL.md: read its definition at `code/core/src/csf/SBType.ts:31` and list its fields or members.

### GAP-364: Missing export: SNIPPET_RENDERED

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/shared.ts:5
**Export:** SNIPPET_RENDERED

**Issue:** `SNIPPET_RENDERED` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SNIPPET_RENDERED` in SKILL.md: read its definition at `code/core/src/docs-tools/shared.ts:5` and add its signature, its purpose and a usage example.

### GAP-365: Missing export: STATUS_STORE_CHANNEL_EVENT_NAME

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:64
**Export:** STATUS_STORE_CHANNEL_EVENT_NAME

**Issue:** `STATUS_STORE_CHANNEL_EVENT_NAME` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `STATUS_STORE_CHANNEL_EVENT_NAME` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:64` and add its signature, its purpose and a usage example.

### GAP-366: Missing export: STATUS_TYPE_ID_A11Y

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:68
**Export:** STATUS_TYPE_ID_A11Y

**Issue:** `STATUS_TYPE_ID_A11Y` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `STATUS_TYPE_ID_A11Y` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:68` and add its signature, its purpose and a usage example.

### GAP-367: Missing export: STATUS_TYPE_ID_COMPONENT_TEST

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:67
**Export:** STATUS_TYPE_ID_COMPONENT_TEST

**Issue:** `STATUS_TYPE_ID_COMPONENT_TEST` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `STATUS_TYPE_ID_COMPONENT_TEST` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:67` and add its signature, its purpose and a usage example.

### GAP-368: Missing export: STORE_CHANNEL_EVENT_NAME

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:63
**Export:** STORE_CHANNEL_EVENT_NAME

**Issue:** `STORE_CHANNEL_EVENT_NAME` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `STORE_CHANNEL_EVENT_NAME` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:63` and add its signature, its purpose and a usage example.

### GAP-369: Missing export: SUPPORTED_ESLINT_EXTENSIONS

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/eslintPlugin.ts:15
**Export:** SUPPORTED_ESLINT_EXTENSIONS

**Issue:** `SUPPORTED_ESLINT_EXTENSIONS` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SUPPORTED_ESLINT_EXTENSIONS` in SKILL.md: read its definition at `code/core/src/cli/eslintPlugin.ts:15` and add its signature, its purpose and a usage example.

### GAP-370: Missing type: SaveStoryRequestPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/save-story.ts:1
**Export:** SaveStoryRequestPayload

**Issue:** the type `SaveStoryRequestPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SaveStoryRequestPayload` in SKILL.md: read its definition at `code/core/src/core-events/data/save-story.ts:1` and list its fields or members.

### GAP-371: Missing type: SaveStoryResponsePayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/save-story.ts:8
**Export:** SaveStoryResponsePayload

**Issue:** the type `SaveStoryResponsePayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SaveStoryResponsePayload` in SKILL.md: read its definition at `code/core/src/core-events/data/save-story.ts:8` and list its fields or members.

### GAP-372: Missing type: SavingGlobalSettingsFileError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:626
**Export:** SavingGlobalSettingsFileError

**Issue:** the type `SavingGlobalSettingsFileError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SavingGlobalSettingsFileError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:626` and list its fields or members.

### GAP-373: Missing type: SelectionStore

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17
**Export:** SelectionStore

**Issue:** the type `SelectionStore` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SelectionStore` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17` and list its fields or members.

### GAP-374: Missing type: ServerApp

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:242
**Export:** ServerApp

**Issue:** the type `ServerApp` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ServerApp` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:242` and list its fields or members.

### GAP-375: Missing type: SetGlobalsPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/channelApi.ts:54
**Export:** SetGlobalsPayload

**Issue:** the type `SetGlobalsPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SetGlobalsPayload` in SKILL.md: read its definition at `code/core/src/types/modules/channelApi.ts:54` and list its fields or members.

### GAP-376: Missing type: SetStoriesPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/channelApi.ts:38
**Export:** SetStoriesPayload

**Issue:** the type `SetStoriesPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SetStoriesPayload` in SKILL.md: read its definition at `code/core/src/types/modules/channelApi.ts:38` and list its fields or members.

### GAP-377: Missing type: SetStoriesStory

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/channelApi.ts:14
**Export:** SetStoriesStory

**Issue:** the type `SetStoriesStory` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SetStoriesStory` in SKILL.md: read its definition at `code/core/src/types/modules/channelApi.ts:14` and list its fields or members.

### GAP-378: Missing type: SetStoriesStoryData

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/channelApi.ts:34
**Export:** SetStoriesStoryData

**Issue:** the type `SetStoriesStoryData` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SetStoriesStoryData` in SKILL.md: read its definition at `code/core/src/types/modules/channelApi.ts:34` and list its fields or members.

### GAP-379: Missing type: Settings

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/cli/globalSettings.ts:91
**Export:** Settings

**Issue:** the type `Settings` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Settings` in SKILL.md: read its definition at `code/core/src/cli/globalSettings.ts:91` and list its fields or members.

### GAP-380: Missing type: SetupAddonInConfigOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/common/utils/setup-addon-in-config.ts:11
**Export:** SetupAddonInConfigOptions

**Issue:** the type `SetupAddonInConfigOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SetupAddonInConfigOptions` in SKILL.md: read its definition at `code/core/src/common/utils/setup-addon-in-config.ts:11` and list its fields or members.

### GAP-381: Missing export: SourceContainer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38
**Export:** SourceContainer

**Issue:** `SourceContainer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SourceContainer` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38` and add its signature, its purpose and a usage example.

### GAP-382: Missing export: SourceContext

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27
**Export:** SourceContext

**Issue:** `SourceContext` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SourceContext` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27` and add its signature, its purpose and a usage example.

### GAP-383: Missing type: SourceContextProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22
**Export:** SourceContextProps

**Issue:** the type `SourceContextProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceContextProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22` and list its fields or members.

### GAP-384: Missing type: SourceItem

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15
**Export:** SourceItem

**Issue:** the type `SourceItem` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceItem` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15` and list its fields or members.

### GAP-385: Missing type: SourceParameters

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:16
**Export:** SourceParameters

**Issue:** the type `SourceParameters` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceParameters` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Source.tsx:16` and list its fields or members.

### GAP-386: Missing type: SourceProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:28
**Export:** SourceProps

**Issue:** the type `SourceProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Source.tsx:28` and list its fields or members.

### GAP-387: Missing type: SourceType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/shared.ts:7
**Export:** SourceType

**Issue:** the type `SourceType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceType` in SKILL.md: read its definition at `code/core/src/docs-tools/shared.ts:7` and list its fields or members.

### GAP-388: Missing type: Stats

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:152
**Export:** Stats

**Issue:** the type `Stats` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Stats` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:152` and list its fields or members.

### GAP-389: Missing type: Status

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/status-store/index.ts:20
**Export:** Status

**Issue:** the type `Status` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Status` in SKILL.md: read its definition at `code/core/src/shared/status-store/index.ts:20` and list its fields or members.

### GAP-390: Missing type: StatusByTypeId

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/status-store/index.ts:17
**Export:** StatusByTypeId

**Issue:** the type `StatusByTypeId` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StatusByTypeId` in SKILL.md: read its definition at `code/core/src/shared/status-store/index.ts:17` and list its fields or members.

### GAP-391: Missing type: StatusStore

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/status-store/index.ts:45
**Export:** StatusStore

**Issue:** the type `StatusStore` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StatusStore` in SKILL.md: read its definition at `code/core/src/shared/status-store/index.ts:45` and list its fields or members.

### GAP-392: Missing type: StatusStoreByTypeId

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/status-store/index.ts:61
**Export:** StatusStoreByTypeId

**Issue:** the type `StatusStoreByTypeId` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StatusStoreByTypeId` in SKILL.md: read its definition at `code/core/src/shared/status-store/index.ts:61` and list its fields or members.

### GAP-393: Missing type: StatusTypeId

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/status-store/index.ts:16
**Export:** StatusTypeId

**Issue:** the type `StatusTypeId` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StatusTypeId` in SKILL.md: read its definition at `code/core/src/shared/status-store/index.ts:16` and list its fields or members.

### GAP-394: Missing type: StatusValue

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/status-store/index.ts:9
**Export:** StatusValue

**Issue:** the type `StatusValue` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StatusValue` in SKILL.md: read its definition at `code/core/src/shared/status-store/index.ts:9` and list its fields or members.

### GAP-395: Missing type: StatusesByStoryIdAndTypeId

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/status-store/index.ts:18
**Export:** StatusesByStoryIdAndTypeId

**Issue:** the type `StatusesByStoryIdAndTypeId` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StatusesByStoryIdAndTypeId` in SKILL.md: read its definition at `code/core/src/shared/status-store/index.ts:18` and list its fields or members.

### GAP-396: Missing type: StepFunction

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:297
**Export:** StepFunction

**Issue:** the type `StepFunction` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StepFunction` in SKILL.md: read its definition at `code/core/src/csf/story.ts:297` and list its fields or members.

### GAP-397: Missing type: StepLabel

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:295
**Export:** StepLabel

**Issue:** the type `StepLabel` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StepLabel` in SKILL.md: read its definition at `code/core/src/csf/story.ts:295` and list its fields or members.

### GAP-398: Missing type: StepRunner

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:341
**Export:** StepRunner

**Issue:** the type `StepRunner` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StepRunner` in SKILL.md: read its definition at `code/core/src/csf/story.ts:341` and list its fields or members.

### GAP-399: Missing type: Store_CSFExports

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/composedStory.ts:23
**Export:** Store_CSFExports

**Issue:** the type `Store_CSFExports` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Store_CSFExports` in SKILL.md: read its definition at `code/core/src/types/modules/composedStory.ts:23` and list its fields or members.

### GAP-400: Missing type: StoriesEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:18
**Export:** StoriesEntry

**Issue:** the type `StoriesEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoriesEntry` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:18` and list its fields or members.

### GAP-401: Missing type: StoriesSpecifier

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:6
**Export:** StoriesSpecifier

**Issue:** the type `StoriesSpecifier` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoriesSpecifier` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:6` and list its fields or members.

### GAP-402: Missing type: StoriesWithPartialProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/composedStory.ts:60
**Export:** StoriesWithPartialProps

**Issue:** the type `StoriesWithPartialProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoriesWithPartialProps` in SKILL.md: read its definition at `code/core/src/types/modules/composedStory.ts:60` and list its fields or members.

### GAP-403: Missing type: StoryAnnotationsOrFn

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:581
**Export:** StoryAnnotationsOrFn

**Issue:** the type `StoryAnnotationsOrFn` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryAnnotationsOrFn` in SKILL.md: read its definition at `code/core/src/csf/story.ts:581` and list its fields or members.

### GAP-404: Missing type: StoryContextForEnhancers

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:219
**Export:** StoryContextForEnhancers

**Issue:** the type `StoryContextForEnhancers` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryContextForEnhancers` in SKILL.md: read its definition at `code/core/src/csf/story.ts:219` and list its fields or members.

### GAP-405: Missing type: StoryContextForLoaders

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:284
**Export:** StoryContextForLoaders

**Issue:** the type `StoryContextForLoaders` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryContextForLoaders` in SKILL.md: read its definition at `code/core/src/csf/story.ts:284` and list its fields or members.

### GAP-406: Missing type: StoryContextUpdate

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:239
**Export:** StoryContextUpdate

**Issue:** the type `StoryContextUpdate` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryContextUpdate` in SKILL.md: read its definition at `code/core/src/csf/story.ts:239` and list its fields or members.

### GAP-407: Missing type: StoryFinishedPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/phases.ts:3
**Export:** StoryFinishedPayload

**Issue:** the type `StoryFinishedPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryFinishedPayload` in SKILL.md: read its definition at `code/core/src/core-events/data/phases.ts:3` and list its fields or members.

### GAP-408: Missing type: StoryId

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:8
**Export:** StoryId

**Issue:** the type `StoryId` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryId` in SKILL.md: read its definition at `code/core/src/csf/story.ts:8` and list its fields or members.

### GAP-409: Missing type: StoryIdentifier

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:18
**Export:** StoryIdentifier

**Issue:** the type `StoryIdentifier` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryIdentifier` in SKILL.md: read its definition at `code/core/src/csf/story.ts:18` and list its fields or members.

### GAP-410: Missing type: StoryIndex

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:174
**Export:** StoryIndex

**Issue:** the type `StoryIndex` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryIndex` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:174` and list its fields or members.

### GAP-411: Missing type: StoryIndexEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:74
**Export:** StoryIndexEntry

**Issue:** the type `StoryIndexEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryIndexEntry` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:74` and list its fields or members.

### GAP-412: Missing type: StoryIndexInput

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:137
**Export:** StoryIndexInput

**Issue:** the type `StoryIndexInput` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryIndexInput` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:137` and list its fields or members.

### GAP-413: Missing type: StoryIndexV2

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:159
**Export:** StoryIndexV2

**Issue:** the type `StoryIndexV2` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryIndexV2` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:159` and list its fields or members.

### GAP-414: Missing type: StoryIndexV3

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:169
**Export:** StoryIndexV3

**Issue:** the type `StoryIndexV3` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryIndexV3` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:169` and list its fields or members.

### GAP-415: Missing type: StoryKind

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:14
**Export:** StoryKind

**Issue:** the type `StoryKind` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryKind` in SKILL.md: read its definition at `code/core/src/csf/story.ts:14` and list its fields or members.

### GAP-416: Missing type: StoryName

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:11
**Export:** StoryName

**Issue:** the type `StoryName` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryName` in SKILL.md: read its definition at `code/core/src/csf/story.ts:11` and list its fields or members.

### GAP-417: Missing type: StoryPreparedPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/channelApi.ts:67
**Export:** StoryPreparedPayload

**Issue:** the type `StoryPreparedPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryPreparedPayload` in SKILL.md: read its definition at `code/core/src/types/modules/channelApi.ts:67` and list its fields or members.

### GAP-418: Missing type: StoryProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:60
**Export:** StoryProps

**Issue:** the type `StoryProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Story.tsx:60` and list its fields or members.

### GAP-419: Missing type: StoryRenderOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/docs.ts:19
**Export:** StoryRenderOptions

**Issue:** the type `StoryRenderOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryRenderOptions` in SKILL.md: read its definition at `code/core/src/types/modules/docs.ts:19` and list its fields or members.

### GAP-420: Missing type: StorySources

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20
**Export:** StorySources

**Issue:** the type `StorySources` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StorySources` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20` and list its fields or members.

### GAP-421: Missing type: StorybookConfigOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:224
**Export:** StorybookConfigOptions

**Issue:** the type `StorybookConfigOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StorybookConfigOptions` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:224` and list its fields or members.

### GAP-422: Missing type: StorybookConfigRaw

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:390
**Export:** StorybookConfigRaw

**Issue:** the type `StorybookConfigRaw` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StorybookConfigRaw` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:390` and list its fields or members.

### GAP-423: Missing type: StorybookCoverageReporterOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/vitest/src/node/coverage-reporter.ts:9
**Export:** StorybookCoverageReporterOptions

**Issue:** the type `StorybookCoverageReporterOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StorybookCoverageReporterOptions` in SKILL.md: read its definition at `code/addons/vitest/src/node/coverage-reporter.ts:9` and list its fields or members.

### GAP-424: Missing type: StorybookInternalParameters

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/csf.ts:89
**Export:** StorybookInternalParameters

**Issue:** the type `StorybookInternalParameters` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StorybookInternalParameters` in SKILL.md: read its definition at `code/core/src/types/modules/csf.ts:89` and list its fields or members.

### GAP-425: Missing type: StorybookTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/csf.ts:85
**Export:** StorybookTypes

**Issue:** the type `StorybookTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StorybookTypes` in SKILL.md: read its definition at `code/core/src/types/modules/csf.ts:85` and list its fields or members.

### GAP-426: Missing type: StrictArgTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:163
**Export:** StrictArgTypes

**Issue:** the type `StrictArgTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StrictArgTypes` in SKILL.md: read its definition at `code/core/src/csf/story.ts:163` and list its fields or members.

### GAP-427: Missing type: StrictInputType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:148
**Export:** StrictInputType

**Issue:** the type `StrictInputType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StrictInputType` in SKILL.md: read its definition at `code/core/src/csf/story.ts:148` and list its fields or members.

### GAP-428: Missing type: StrictParameters

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:36
**Export:** StrictParameters

**Issue:** the type `StrictParameters` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StrictParameters` in SKILL.md: read its definition at `code/core/src/csf/story.ts:36` and list its fields or members.

### GAP-429: Missing type: SupportedBuilder

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/builders.ts:1
**Export:** SupportedBuilder

**Issue:** the type `SupportedBuilder` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SupportedBuilder` in SKILL.md: read its definition at `code/core/src/types/modules/builders.ts:1` and list its fields or members.

### GAP-430: Missing type: SupportedFramework

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/frameworks.ts:2
**Export:** SupportedFramework

**Issue:** the type `SupportedFramework` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SupportedFramework` in SKILL.md: read its definition at `code/core/src/types/modules/frameworks.ts:2` and list its fields or members.

### GAP-431: Missing type: SupportedRenderer

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/renderers.ts:1
**Export:** SupportedRenderer

**Issue:** the type `SupportedRenderer` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SupportedRenderer` in SKILL.md: read its definition at `code/core/src/types/modules/renderers.ts:1` and list its fields or members.

### GAP-432: Missing type: SvelteViteWithSvelteKitError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:335
**Export:** SvelteViteWithSvelteKitError

**Issue:** the type `SvelteViteWithSvelteKitError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SvelteViteWithSvelteKitError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:335` and list its fields or members.

### GAP-433: Missing type: SyncPayload

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/instrumenter/types.ts:66
**Export:** SyncPayload

**Issue:** the type `SyncPayload` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SyncPayload` in SKILL.md: read its definition at `code/core/src/instrumenter/types.ts:66` and list its fields or members.

### GAP-434: Missing export: TEST_PROVIDER_STORE_CHANNEL_EVENT_NAME

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:65
**Export:** TEST_PROVIDER_STORE_CHANNEL_EVENT_NAME

**Issue:** `TEST_PROVIDER_STORE_CHANNEL_EVENT_NAME` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TEST_PROVIDER_STORE_CHANNEL_EVENT_NAME` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:65` and add its signature, its purpose and a usage example.

### GAP-435: Missing export: TOOL_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/constants.ts:4
**Export:** TOOL_ID

**Issue:** `TOOL_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TOOL_ID` in SKILL.md: read its definition at `code/core/src/viewport/constants.ts:4` and add its signature, its purpose and a usage example.

### GAP-436: Missing export: TRIGGER_TEST_RUN_REQUEST

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:71
**Export:** TRIGGER_TEST_RUN_REQUEST

**Issue:** `TRIGGER_TEST_RUN_REQUEST` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TRIGGER_TEST_RUN_REQUEST` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:71` and add its signature, its purpose and a usage example.

### GAP-437: Missing export: TRIGGER_TEST_RUN_RESPONSE

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:72
**Export:** TRIGGER_TEST_RUN_RESPONSE

**Issue:** `TRIGGER_TEST_RUN_RESPONSE` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TRIGGER_TEST_RUN_RESPONSE` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:72` and add its signature, its purpose and a usage example.

### GAP-438: Missing export: TUTORIAL_VIDEO_LINK

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/constants.ts:15
**Export:** TUTORIAL_VIDEO_LINK

**Issue:** `TUTORIAL_VIDEO_LINK` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TUTORIAL_VIDEO_LINK` in SKILL.md: read its definition at `code/addons/vitest/src/constants.ts:15` and add its signature, its purpose and a usage example.

### GAP-439: Missing type: TagOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:348
**Export:** TagOptions

**Issue:** the type `TagOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TagOptions` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:348` and list its fields or members.

### GAP-440: Missing type: TagsOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:355
**Export:** TagsOptions

**Issue:** the type `TagsOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TagsOptions` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:355` and list its fields or members.

### GAP-441: Missing type: Task

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/vitest/src/vitest-plugin/setup-file.ts:15
**Export:** Task

**Issue:** the type `Task` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Task` in SKILL.md: read its definition at `code/addons/vitest/src/vitest-plugin/setup-file.ts:15` and list its fields or members.

### GAP-442: Missing type: TeardownRenderToCanvas

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/story.ts:37
**Export:** TeardownRenderToCanvas

**Issue:** the type `TeardownRenderToCanvas` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TeardownRenderToCanvas` in SKILL.md: read its definition at `code/core/src/types/modules/story.ts:37` and list its fields or members.

### GAP-443: Missing type: TestBuildConfig

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:342
**Export:** TestBuildConfig

**Issue:** the type `TestBuildConfig` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TestBuildConfig` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:342` and list its fields or members.

### GAP-444: Missing type: TestBuildFlags

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:320
**Export:** TestBuildFlags

**Issue:** the type `TestBuildFlags` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TestBuildFlags` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:320` and list its fields or members.

### GAP-445: Missing type: TestFunction

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/csf/story.ts:306
**Export:** TestFunction

**Issue:** the type `TestFunction` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TestFunction` in SKILL.md: read its definition at `code/core/src/csf/story.ts:306` and list its fields or members.

### GAP-446: Missing type: TestProviderId

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/test-provider-store/index.ts:16
**Export:** TestProviderId

**Issue:** the type `TestProviderId` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TestProviderId` in SKILL.md: read its definition at `code/core/src/shared/test-provider-store/index.ts:16` and list its fields or members.

### GAP-447: Missing type: TestProviderState

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/test-provider-store/index.ts:11
**Export:** TestProviderState

**Issue:** the type `TestProviderState` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TestProviderState` in SKILL.md: read its definition at `code/core/src/shared/test-provider-store/index.ts:11` and list its fields or members.

### GAP-448: Missing type: TestProviderStateByProviderId

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/test-provider-store/index.ts:17
**Export:** TestProviderStateByProviderId

**Issue:** the type `TestProviderStateByProviderId` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TestProviderStateByProviderId` in SKILL.md: read its definition at `code/core/src/shared/test-provider-store/index.ts:17` and list its fields or members.

### GAP-449: Missing type: TestProviderStoreById

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/test-provider-store/index.ts:199
**Export:** TestProviderStoreById

**Issue:** the type `TestProviderStoreById` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TestProviderStoreById` in SKILL.md: read its definition at `code/core/src/shared/test-provider-store/index.ts:199` and list its fields or members.

### GAP-450: Missing type: TestTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/test/preview.ts:165
**Export:** TestTypes

**Issue:** the type `TestTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TestTypes` in SKILL.md: read its definition at `code/core/src/test/preview.ts:165` and list its fields or members.

### GAP-451: Missing type: TypeSystem

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/docs-tools/argTypes/docgen/types.ts:51
**Export:** TypeSystem

**Issue:** the type `TypeSystem` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TypeSystem` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/types.ts:51` and list its fields or members.

### GAP-452: Missing type: TypescriptOptions

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:282
**Export:** TypescriptOptions

**Issue:** the type `TypescriptOptions` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TypescriptOptions` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:282` and list its fields or members.

### GAP-453: Missing export: UNKNOWN_ARGS_HASH

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36
**Export:** UNKNOWN_ARGS_HASH

**Issue:** `UNKNOWN_ARGS_HASH` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `UNKNOWN_ARGS_HASH` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36` and add its signature, its purpose and a usage example.

### GAP-454: Missing type: UncaughtManagerError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/manager-errors.ts:34
**Export:** UncaughtManagerError

**Issue:** the type `UncaughtManagerError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UncaughtManagerError` in SKILL.md: read its definition at `code/core/src/manager-errors.ts:34` and list its fields or members.

### GAP-455: Missing type: UniversalStore

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/universal-store/index.ts:82
**Export:** UniversalStore

**Issue:** the type `UniversalStore` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UniversalStore` in SKILL.md: read its definition at `code/core/src/shared/universal-store/index.ts:82` and list its fields or members.

### GAP-456: Missing type: UnknownArgTypesError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-errors.ts:345
**Export:** UnknownArgTypesError

**Issue:** the type `UnknownArgTypesError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UnknownArgTypesError` in SKILL.md: read its definition at `code/core/src/preview-errors.ts:345` and list its fields or members.

### GAP-457: Missing type: UnsupportedViewportDimensionError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-errors.ts:365
**Export:** UnsupportedViewportDimensionError

**Issue:** the type `UnsupportedViewportDimensionError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UnsupportedViewportDimensionError` in SKILL.md: read its definition at `code/core/src/preview-errors.ts:365` and list its fields or members.

### GAP-458: Missing type: UpgradeStorybookToLowerVersionError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:530
**Export:** UpgradeStorybookToLowerVersionError

**Issue:** the type `UpgradeStorybookToLowerVersionError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UpgradeStorybookToLowerVersionError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:530` and list its fields or members.

### GAP-459: Missing type: UpgradeStorybookUnknownCurrentVersionError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:551
**Export:** UpgradeStorybookUnknownCurrentVersionError

**Issue:** the type `UpgradeStorybookUnknownCurrentVersionError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UpgradeStorybookUnknownCurrentVersionError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:551` and list its fields or members.

### GAP-460: Missing type: UseStatusStore

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/status-store/index.ts:67
**Export:** UseStatusStore

**Issue:** the type `UseStatusStore` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UseStatusStore` in SKILL.md: read its definition at `code/core/src/shared/status-store/index.ts:67` and list its fields or members.

### GAP-461: Missing type: UseTestProviderStore

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/test-provider-store/index.ts:330
**Export:** UseTestProviderStore

**Issue:** the type `UseTestProviderStore` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UseTestProviderStore` in SKILL.md: read its definition at `code/core/src/shared/test-provider-store/index.ts:330` and list its fields or members.

### GAP-462: Missing type: UserEvent

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/test/testing-library.ts:119
**Export:** UserEvent

**Issue:** the type `UserEvent` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UserEvent` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:119` and list its fields or members.

### GAP-463: Missing type: UserEventObject

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/test/index.ts:15
**Export:** UserEventObject

**Issue:** the type `UserEventObject` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UserEventObject` in SKILL.md: read its definition at `code/core/src/test/index.ts:15` and list its fields or members.

### GAP-464: Missing type: V3CompatIndexEntry

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/indexer.ts:153
**Export:** V3CompatIndexEntry

**Issue:** the type `V3CompatIndexEntry` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `V3CompatIndexEntry` in SKILL.md: read its definition at `code/core/src/types/modules/indexer.ts:153` and list its fields or members.

### GAP-465: Missing type: VersionCheck

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/types/modules/core-common.ts:144
**Export:** VersionCheck

**Issue:** the type `VersionCheck` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `VersionCheck` in SKILL.md: read its definition at `code/core/src/types/modules/core-common.ts:144` and list its fields or members.

### GAP-466: Missing type: View

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/preview-web/View.ts:3
**Export:** View

**Issue:** the type `View` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `View` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/View.ts:3` and list its fields or members.

### GAP-467: Missing type: Viewport

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:1
**Export:** Viewport

**Issue:** the type `Viewport` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Viewport` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:1` and list its fields or members.

### GAP-468: Missing type: ViewportGlobals

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:56
**Export:** ViewportGlobals

**Issue:** the type `ViewportGlobals` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ViewportGlobals` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:56` and list its fields or members.

### GAP-469: Missing type: ViewportMap

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:14
**Export:** ViewportMap

**Issue:** the type `ViewportMap` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ViewportMap` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:14` and list its fields or members.

### GAP-470: Missing type: ViewportTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:65
**Export:** ViewportTypes

**Issue:** the type `ViewportTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ViewportTypes` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:65` and list its fields or members.

### GAP-471: Missing type: WebpackCompilationError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:191
**Export:** WebpackCompilationError

**Issue:** the type `WebpackCompilationError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `WebpackCompilationError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:191` and list its fields or members.

### GAP-472: Missing type: WebpackInvocationError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:172
**Export:** WebpackInvocationError

**Issue:** the type `WebpackInvocationError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `WebpackInvocationError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:172` and list its fields or members.

### GAP-473: Missing type: WebpackMissingStatsError

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/server-errors.ts:155
**Export:** WebpackMissingStatsError

**Issue:** the type `WebpackMissingStatsError` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `WebpackMissingStatsError` in SKILL.md: read its definition at `code/core/src/server-errors.ts:155` and list its fields or members.

### GAP-474: Missing type: WhatsNewCache

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/whats-new.ts:1
**Export:** WhatsNewCache

**Issue:** the type `WhatsNewCache` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `WhatsNewCache` in SKILL.md: read its definition at `code/core/src/core-events/data/whats-new.ts:1` and list its fields or members.

### GAP-475: Missing type: WhatsNewData

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/core-events/data/whats-new.ts:6
**Export:** WhatsNewData

**Issue:** the type `WhatsNewData` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `WhatsNewData` in SKILL.md: read its definition at `code/core/src/core-events/data/whats-new.ts:6` and list its fields or members.

### GAP-476: Missing export: Wrapper

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Wrapper.tsx:10
**Export:** Wrapper

**Issue:** `Wrapper` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Wrapper` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Wrapper.tsx:10` and add its signature, its purpose and a usage example.

### GAP-477: Missing export: actions

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/runtime/actions.ts:5
**Export:** actions

**Issue:** `actions` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `actions` in SKILL.md: read its definition at `code/core/src/actions/runtime/actions.ts:5` and add its signature, its purpose and a usage example.

### GAP-478: Missing export: addExtensionsToRelativeImports

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/bin/loader.ts:64
**Export:** addExtensionsToRelativeImports

**Issue:** `addExtensionsToRelativeImports` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `addExtensionsToRelativeImports` in SKILL.md: read its definition at `code/core/src/bin/loader.ts:64` and add its signature, its purpose and a usage example.

### GAP-479: Missing export: addToDevDependenciesIfNotPresent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:106
**Export:** addToDevDependenciesIfNotPresent

**Issue:** `addToDevDependenciesIfNotPresent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `addToDevDependenciesIfNotPresent` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:106` and add its signature, its purpose and a usage example.

### GAP-480: Missing export: adjustTemplate

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:230
**Export:** adjustTemplate

**Issue:** `adjustTemplate` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `adjustTemplate` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:230` and add its signature, its purpose and a usage example.

### GAP-481: Missing export: anchorBlockIdFromId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Anchor.tsx:4
**Export:** anchorBlockIdFromId

**Issue:** `anchorBlockIdFromId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `anchorBlockIdFromId` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Anchor.tsx:4` and add its signature, its purpose and a usage example.

### GAP-482: Missing export: argsHash

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11
**Export:** argsHash

**Issue:** `argsHash` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `argsHash` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11` and add its signature, its purpose and a usage example.

### GAP-483: Missing export: assertIsFn

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:19
**Export:** assertIsFn

**Issue:** `assertIsFn` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `assertIsFn` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:19` and add its signature, its purpose and a usage example.

### GAP-484: Missing export: automockModule

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/automock.ts:47
**Export:** automockModule

**Issue:** `automockModule` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `automockModule` in SKILL.md: read its definition at `code/core/src/mocking-utils/automock.ts:47` and add its signature, its purpose and a usage example.

### GAP-485: Missing export: babelParser

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/extract.ts:44
**Export:** babelParser

**Issue:** `babelParser` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `babelParser` in SKILL.md: read its definition at `code/core/src/mocking-utils/extract.ts:44` and add its signature, its purpose and a usage example.

### GAP-486: Missing export: background

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:44
**Export:** background

**Issue:** `background` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `background` in SKILL.md: read its definition at `code/core/src/theming/base.ts:44` and add its signature, its purpose and a usage example.

### GAP-487: Missing export: beforeAll

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/renderers/react/src/entry-preview.tsx:49
**Export:** beforeAll

**Issue:** `beforeAll` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `beforeAll` in SKILL.md: read its definition at `code/renderers/react/src/entry-preview.tsx:49` and add its signature, its purpose and a usage example.

### GAP-488: Missing export: builderPackages

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-info.ts:64
**Export:** builderPackages

**Issue:** `builderPackages` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `builderPackages` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-info.ts:64` and add its signature, its purpose and a usage example.

### GAP-489: Missing export: cache

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/cache.ts:4
**Export:** cache

**Issue:** `cache` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `cache` in SKILL.md: read its definition at `code/core/src/common/utils/cache.ts:4` and add its signature, its purpose and a usage example.

### GAP-490: Missing export: checkAddonOrder

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/check-addon-order.ts:39
**Export:** checkAddonOrder

**Issue:** `checkAddonOrder` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `checkAddonOrder` in SKILL.md: read its definition at `code/core/src/common/utils/check-addon-order.ts:39` and add its signature, its purpose and a usage example.

### GAP-491: Missing export: checkRef

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-refs.ts:61
**Export:** checkRef

**Issue:** `checkRef` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `checkRef` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-refs.ts:61` and add its signature, its purpose and a usage example.

### GAP-492: Missing export: cliStoriesTargetPath

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:161
**Export:** cliStoriesTargetPath

**Issue:** `cliStoriesTargetPath` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `cliStoriesTargetPath` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:161` and add its signature, its purpose and a usage example.

### GAP-493: Missing export: coerceSemver

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:242
**Export:** coerceSemver

**Issue:** `coerceSemver` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `coerceSemver` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:242` and add its signature, its purpose and a usage example.

### GAP-494: Missing export: color

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:1
**Export:** color

**Issue:** `color` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `color` in SKILL.md: read its definition at `code/core/src/theming/base.ts:1` and add its signature, its purpose and a usage example.

### GAP-495: Missing export: commonGlobOptions

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/common-glob-options.ts:4
**Export:** commonGlobOptions

**Issue:** `commonGlobOptions` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `commonGlobOptions` in SKILL.md: read its definition at `code/core/src/common/utils/common-glob-options.ts:4` and add its signature, its purpose and a usage example.

### GAP-496: Missing export: compilerPackages

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-info.ts:71
**Export:** compilerPackages

**Issue:** `compilerPackages` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `compilerPackages` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-info.ts:71` and add its signature, its purpose and a usage example.

### GAP-497: Missing export: config

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/runtime/configureActions.ts:3
**Export:** config

**Issue:** `config` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `config` in SKILL.md: read its definition at `code/core/src/actions/runtime/configureActions.ts:3` and add its signature, its purpose and a usage example.

### GAP-498: Missing export: configureEslintPlugin

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/eslintPlugin.ts:265
**Export:** configureEslintPlugin

**Issue:** `configureEslintPlugin` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `configureEslintPlugin` in SKILL.md: read its definition at `code/core/src/cli/eslintPlugin.ts:265` and add its signature, its purpose and a usage example.

### GAP-499: Missing export: configureFlatConfig

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/eslintPlugin.ts:55
**Export:** configureFlatConfig

**Issue:** `configureFlatConfig` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `configureFlatConfig` in SKILL.md: read its definition at `code/core/src/cli/eslintPlugin.ts:55` and add its signature, its purpose and a usage example.

### GAP-500: Missing export: controlOrMetaKey

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:7
**Export:** controlOrMetaKey

**Issue:** `controlOrMetaKey` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `controlOrMetaKey` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:7` and add its signature, its purpose and a usage example.

### GAP-501: Missing export: controlOrMetaSymbol

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:6
**Export:** controlOrMetaSymbol

**Issue:** `controlOrMetaSymbol` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `controlOrMetaSymbol` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:6` and add its signature, its purpose and a usage example.

### GAP-502: Missing export: convert

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/convert/index.ts:8
**Export:** convert

**Issue:** `convert` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `convert` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/convert/index.ts:8` and add its signature, its purpose and a usage example.

### GAP-503: Missing export: convertToFilePath

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/vitest-plugin/test-utils.ts:25
**Export:** convertToFilePath

**Issue:** `convertToFilePath` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `convertToFilePath` in SKILL.md: read its definition at `code/addons/vitest/src/vitest-plugin/test-utils.ts:25` and add its signature, its purpose and a usage example.

### GAP-504: Missing export: copyTemplate

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:122
**Export:** copyTemplate

**Issue:** `copyTemplate` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `copyTemplate` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:122` and add its signature, its purpose and a usage example.

### GAP-505: Missing export: copyTemplateFiles

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:168
**Export:** copyTemplateFiles

**Issue:** `copyTemplateFiles` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `copyTemplateFiles` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:168` and add its signature, its purpose and a usage example.

### GAP-506: Missing export: createFileSystemCache

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/file-cache.ts:160
**Export:** createFileSystemCache

**Issue:** `createFileSystemCache` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `createFileSystemCache` in SKILL.md: read its definition at `code/core/src/common/utils/file-cache.ts:160` and add its signature, its purpose and a usage example.

### GAP-507: Missing export: createLogStream

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/cli.ts:114
**Export:** createLogStream

**Issue:** `createLogStream` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `createLogStream` in SKILL.md: read its definition at `code/core/src/common/utils/cli.ts:114` and add its signature, its purpose and a usage example.

### GAP-508: Missing export: createPlaywrightTest

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:319
**Export:** createPlaywrightTest

**Issue:** `createPlaywrightTest` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `createPlaywrightTest` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:319` and add its signature, its purpose and a usage example.

### GAP-509: Missing export: createSummaryValue

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/utils.ts:14
**Export:** createSummaryValue

**Issue:** `createSummaryValue` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `createSummaryValue` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/utils.ts:14` and add its signature, its purpose and a usage example.

### GAP-510: Missing export: default

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/a11y/src/postinstall.ts:5
**Export:** default

**Issue:** `default` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `default` in SKILL.md: read its definition at `code/addons/a11y/src/postinstall.ts:5` and add its signature, its purpose and a usage example.

### GAP-511: Missing export: definePreviewAddon

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/csf/csf-factories.ts:78
**Export:** definePreviewAddon

**Issue:** `definePreviewAddon` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `definePreviewAddon` in SKILL.md: read its definition at `code/core/src/csf/csf-factories.ts:78` and add its signature, its purpose and a usage example.

### GAP-512: Missing export: detectPnp

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/detect.ts:4
**Export:** detectPnp

**Issue:** `detectPnp` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `detectPnp` in SKILL.md: read its definition at `code/core/src/cli/detect.ts:4` and add its signature, its purpose and a usage example.

### GAP-513: Missing export: docs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/preset.ts:224
**Export:** docs

**Issue:** `docs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `docs` in SKILL.md: read its definition at `code/addons/docs/src/preset.ts:224` and add its signature, its purpose and a usage example.

### GAP-514: Missing export: doesVariableOrFunctionDeclarationExist

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:17
**Export:** doesVariableOrFunctionDeclarationExist

**Issue:** `doesVariableOrFunctionDeclarationExist` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `doesVariableOrFunctionDeclarationExist` in SKILL.md: read its definition at `code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:17` and add its signature, its purpose and a usage example.

### GAP-515: Missing export: emitTransformCode

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15
**Export:** emitTransformCode

**Issue:** `emitTransformCode` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `emitTransformCode` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15` and add its signature, its purpose and a usage example.

### GAP-516: Missing export: enhanceArgTypes

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/enhanceArgTypes.ts:5
**Export:** enhanceArgTypes

**Issue:** `enhanceArgTypes` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `enhanceArgTypes` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/enhanceArgTypes.ts:5` and add its signature, its purpose and a usage example.

### GAP-517: Missing export: ensure

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/ensure.ts:10
**Export:** ensure

**Issue:** `ensure` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ensure` in SKILL.md: read its definition at `code/core/src/theming/ensure.ts:10` and add its signature, its purpose and a usage example.

### GAP-518: Missing export: eventMatchesShortcut

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:124
**Export:** eventMatchesShortcut

**Issue:** `eventMatchesShortcut` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `eventMatchesShortcut` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:124` and add its signature, its purpose and a usage example.

### GAP-519: Missing export: eventToShortcut

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:21
**Export:** eventToShortcut

**Issue:** `eventToShortcut` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `eventToShortcut` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:21` and add its signature, its purpose and a usage example.

### GAP-520: Missing export: executeCommand

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/command.ts:49
**Export:** executeCommand

**Issue:** `executeCommand` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `executeCommand` in SKILL.md: read its definition at `code/core/src/common/utils/command.ts:49` and add its signature, its purpose and a usage example.

### GAP-521: Missing export: executeCommandSync

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/command.ts:63
**Export:** executeCommandSync

**Issue:** `executeCommandSync` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `executeCommandSync` in SKILL.md: read its definition at `code/core/src/common/utils/command.ts:63` and add its signature, its purpose and a usage example.

### GAP-522: Missing export: executeNodeCommand

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/command.ts:79
**Export:** executeNodeCommand

**Issue:** `executeNodeCommand` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `executeNodeCommand` in SKILL.md: read its definition at `code/core/src/common/utils/command.ts:79` and add its signature, its purpose and a usage example.

### GAP-523: Missing type: experimental_MockUniversalStore

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/shared/universal-store/mock.ts:40
**Export:** experimental_MockUniversalStore

**Issue:** the type `experimental_MockUniversalStore` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `experimental_MockUniversalStore` in SKILL.md: read its definition at `code/core/src/shared/universal-store/mock.ts:40` and list its fields or members.

### GAP-524: Missing export: experimental_enrichCsf

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/renderers/react/src/enrichCsf.ts:10
**Export:** experimental_enrichCsf

**Issue:** `experimental_enrichCsf` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `experimental_enrichCsf` in SKILL.md: read its definition at `code/renderers/react/src/enrichCsf.ts:10` and add its signature, its purpose and a usage example.

### GAP-525: Missing export: experimental_manifests

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/manifest.ts:135
**Export:** experimental_manifests

**Issue:** `experimental_manifests` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `experimental_manifests` in SKILL.md: read its definition at `code/addons/docs/src/manifest.ts:135` and add its signature, its purpose and a usage example.

### GAP-526: Missing export: experimental_requestResponse

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/request-response.ts:13
**Export:** experimental_requestResponse

**Issue:** `experimental_requestResponse` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `experimental_requestResponse` in SKILL.md: read its definition at `code/core/src/manager-api/lib/request-response.ts:13` and add its signature, its purpose and a usage example.

### GAP-527: Missing export: experimental_serverChannel

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/preset.ts:59
**Export:** experimental_serverChannel

**Issue:** `experimental_serverChannel` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `experimental_serverChannel` in SKILL.md: read its definition at `code/addons/vitest/src/preset.ts:59` and add its signature, its purpose and a usage example.

### GAP-528: Missing export: experimental_useStatusStore

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/stores/status.ts
**Export:** experimental_useStatusStore

**Issue:** `experimental_useStatusStore` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `experimental_useStatusStore` in SKILL.md: read its definition at `code/core/src/manager-api/stores/status.ts` and add its signature, its purpose and a usage example.

### GAP-529: Missing export: experimental_useTestProviderStore

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/stores/test-provider.ts
**Export:** experimental_useTestProviderStore

**Issue:** `experimental_useTestProviderStore` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `experimental_useTestProviderStore` in SKILL.md: read its definition at `code/core/src/manager-api/stores/test-provider.ts` and add its signature, its purpose and a usage example.

### GAP-530: Missing export: experimental_useUniversalStore

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/shared/universal-store/use-universal-store-manager.ts:16
**Export:** experimental_useUniversalStore

**Issue:** `experimental_useUniversalStore` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `experimental_useUniversalStore` in SKILL.md: read its definition at `code/core/src/shared/universal-store/use-universal-store-manager.ts:16` and add its signature, its purpose and a usage example.

### GAP-531: Missing export: extractComponentDescription

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:106
**Export:** extractComponentDescription

**Issue:** `extractComponentDescription` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractComponentDescription` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:106` and add its signature, its purpose and a usage example.

### GAP-532: Missing export: extractComponentProps

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:70
**Export:** extractComponentProps

**Issue:** `extractComponentProps` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractComponentProps` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:70` and add its signature, its purpose and a usage example.

### GAP-533: Missing export: extractComponentSectionArray

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:35
**Export:** extractComponentSectionArray

**Issue:** `extractComponentSectionArray` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractComponentSectionArray` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:35` and add its signature, its purpose and a usage example.

### GAP-534: Missing export: extractComponentSectionObject

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:54
**Export:** extractComponentSectionObject

**Issue:** `extractComponentSectionObject` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractComponentSectionObject` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:54` and add its signature, its purpose and a usage example.

### GAP-535: Missing export: extractEslintInfo

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/eslintPlugin.ts:217
**Export:** extractEslintInfo

**Issue:** `extractEslintInfo` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractEslintInfo` in SKILL.md: read its definition at `code/core/src/cli/eslintPlugin.ts:217` and add its signature, its purpose and a usage example.

### GAP-536: Missing export: extractFrameworkPackageName

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-framework-name.ts:34
**Export:** extractFrameworkPackageName

**Issue:** `extractFrameworkPackageName` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractFrameworkPackageName` in SKILL.md: read its definition at `code/core/src/common/utils/get-framework-name.ts:34` and add its signature, its purpose and a usage example.

### GAP-537: Missing export: extractMockCalls

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/extract.ts:85
**Export:** extractMockCalls

**Issue:** `extractMockCalls` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractMockCalls` in SKILL.md: read its definition at `code/core/src/mocking-utils/extract.ts:85` and add its signature, its purpose and a usage example.

### GAP-538: Missing export: extractRenderer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-renderer-name.ts:37
**Export:** extractRenderer

**Issue:** `extractRenderer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractRenderer` in SKILL.md: read its definition at `code/core/src/common/utils/get-renderer-name.ts:37` and add its signature, its purpose and a usage example.

### GAP-539: Missing export: extractTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Title.tsx:24
**Export:** extractTitle

**Issue:** `extractTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractTitle` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Title.tsx:24` and add its signature, its purpose and a usage example.

### GAP-540: Missing export: filterPresetsConfig

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/presets.ts:35
**Export:** filterPresetsConfig

**Issue:** `filterPresetsConfig` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `filterPresetsConfig` in SKILL.md: read its definition at `code/core/src/common/presets.ts:35` and add its signature, its purpose and a usage example.

### GAP-541: Missing export: findConfigFile

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-info.ts:105
**Export:** findConfigFile

**Issue:** `findConfigFile` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findConfigFile` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-info.ts:105` and add its signature, its purpose and a usage example.

### GAP-542: Missing export: findEslintFile

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/eslintPlugin.ts:18
**Export:** findEslintFile

**Issue:** `findEslintFile` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findEslintFile` in SKILL.md: read its definition at `code/core/src/cli/eslintPlugin.ts:18` and add its signature, its purpose and a usage example.

### GAP-543: Missing export: findFilesUp

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/paths.ts:64
**Export:** findFilesUp

**Issue:** `findFilesUp` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findFilesUp` in SKILL.md: read its definition at `code/core/src/common/utils/paths.ts:64` and add its signature, its purpose and a usage example.

### GAP-544: Missing export: formatFileContent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/formatter.ts:51
**Export:** formatFileContent

**Issue:** `formatFileContent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `formatFileContent` in SKILL.md: read its definition at `code/core/src/common/utils/formatter.ts:51` and add its signature, its purpose and a usage example.

### GAP-545: Missing export: frameworkPackages

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-info.ts:39
**Export:** frameworkPackages

**Issue:** `frameworkPackages` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `frameworkPackages` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-info.ts:39` and add its signature, its purpose and a usage example.

### GAP-546: Missing export: frameworkToBuilder

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/framework.ts:41
**Export:** frameworkToBuilder

**Issue:** `frameworkToBuilder` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `frameworkToBuilder` in SKILL.md: read its definition at `code/core/src/common/utils/framework.ts:41` and add its signature, its purpose and a usage example.

### GAP-547: Missing export: frameworkToRenderer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/framework.ts:3
**Export:** frameworkToRenderer

**Issue:** `frameworkToRenderer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `frameworkToRenderer` in SKILL.md: read its definition at `code/core/src/common/utils/framework.ts:3` and add its signature, its purpose and a usage example.

### GAP-548: Missing export: getAbsolutePathWrapperAsCallExpression

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:141
**Export:** getAbsolutePathWrapperAsCallExpression

**Issue:** `getAbsolutePathWrapperAsCallExpression` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAbsolutePathWrapperAsCallExpression` in SKILL.md: read its definition at `code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:141` and add its signature, its purpose and a usage example.

### GAP-549: Missing export: getAbsolutePathWrapperName

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:57
**Export:** getAbsolutePathWrapperName

**Issue:** `getAbsolutePathWrapperName` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAbsolutePathWrapperName` in SKILL.md: read its definition at `code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:57` and add its signature, its purpose and a usage example.

### GAP-550: Missing export: getAddonNames

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-addon-names.ts:5
**Export:** getAddonNames

**Issue:** `getAddonNames` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAddonNames` in SKILL.md: read its definition at `code/core/src/common/utils/get-addon-names.ts:5` and add its signature, its purpose and a usage example.

### GAP-551: Missing export: getArbitraryModuleIdentifier

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/esmWalker.ts:341
**Export:** getArbitraryModuleIdentifier

**Issue:** `getArbitraryModuleIdentifier` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getArbitraryModuleIdentifier` in SKILL.md: read its definition at `code/core/src/mocking-utils/esmWalker.ts:341` and add its signature, its purpose and a usage example.

### GAP-552: Missing export: getAutoRefs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-refs.ts:12
**Export:** getAutoRefs

**Issue:** `getAutoRefs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAutoRefs` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-refs.ts:12` and add its signature, its purpose and a usage example.

### GAP-553: Missing export: getAutomockCode

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/automock.ts:17
**Export:** getAutomockCode

**Issue:** `getAutomockCode` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAutomockCode` in SKILL.md: read its definition at `code/core/src/mocking-utils/automock.ts:17` and add its signature, its purpose and a usage example.

### GAP-554: Missing export: getBabelDependencies

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:73
**Export:** getBabelDependencies

**Issue:** `getBabelDependencies` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getBabelDependencies` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:73` and add its signature, its purpose and a usage example.

### GAP-555: Missing export: getConfigInfo

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-info.ts:111
**Export:** getConfigInfo

**Issue:** `getConfigInfo` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getConfigInfo` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-info.ts:111` and add its signature, its purpose and a usage example.

### GAP-556: Missing export: getCoreAnnotations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/csf/core-annotations.ts:33
**Export:** getCoreAnnotations

**Issue:** `getCoreAnnotations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getCoreAnnotations` in SKILL.md: read its definition at `code/core/src/csf/core-annotations.ts:33` and add its signature, its purpose and a usage example.

### GAP-557: Missing export: getCsfFactoryAnnotations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10
**Export:** getCsfFactoryAnnotations

**Issue:** `getCsfFactoryAnnotations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getCsfFactoryAnnotations` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10` and add its signature, its purpose and a usage example.

### GAP-558: Missing export: getDirectoryFromWorkingDir

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/normalize-stories.ts:25
**Export:** getDirectoryFromWorkingDir

**Issue:** `getDirectoryFromWorkingDir` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getDirectoryFromWorkingDir` in SKILL.md: read its definition at `code/core/src/common/utils/normalize-stories.ts:25` and add its signature, its purpose and a usage example.

### GAP-559: Missing export: getDocgenDescription

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:18
**Export:** getDocgenDescription

**Issue:** `getDocgenDescription` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getDocgenDescription` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:18` and add its signature, its purpose and a usage example.

### GAP-560: Missing export: getDocgenSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:14
**Export:** getDocgenSection

**Issue:** `getDocgenSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getDocgenSection` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:14` and add its signature, its purpose and a usage example.

### GAP-561: Missing export: getEnvConfig

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/cli.ts:69
**Export:** getEnvConfig

**Issue:** `getEnvConfig` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getEnvConfig` in SKILL.md: read its definition at `code/core/src/common/utils/cli.ts:69` and add its signature, its purpose and a usage example.

### GAP-562: Missing export: getFieldsForGetAbsolutePathWrapper

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:114
**Export:** getFieldsForGetAbsolutePathWrapper

**Issue:** `getFieldsForGetAbsolutePathWrapper` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getFieldsForGetAbsolutePathWrapper` in SKILL.md: read its definition at `code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:114` and add its signature, its purpose and a usage example.

### GAP-563: Missing export: getFrameworkName

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-framework-name.ts:9
**Export:** getFrameworkName

**Issue:** `getFrameworkName` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getFrameworkName` in SKILL.md: read its definition at `code/core/src/common/utils/get-framework-name.ts:9` and add its signature, its purpose and a usage example.

### GAP-564: Missing export: getInterpretedFile

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/interpret-files.ts:19
**Export:** getInterpretedFile

**Issue:** `getInterpretedFile` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getInterpretedFile` in SKILL.md: read its definition at `code/core/src/common/utils/interpret-files.ts:19` and add its signature, its purpose and a usage example.

### GAP-565: Missing export: getIsExternal

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/resolve.ts:58
**Export:** getIsExternal

**Issue:** `getIsExternal` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getIsExternal` in SKILL.md: read its definition at `code/core/src/mocking-utils/resolve.ts:58` and add its signature, its purpose and a usage example.

### GAP-566: Missing export: getMockerRuntime

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/runtime.ts:8
**Export:** getMockerRuntime

**Issue:** `getMockerRuntime` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getMockerRuntime` in SKILL.md: read its definition at `code/core/src/mocking-utils/runtime.ts:8` and add its signature, its purpose and a usage example.

### GAP-567: Missing export: getPackageDetails

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/js-package-manager/JsPackageManager.ts:45
**Export:** getPackageDetails

**Issue:** `getPackageDetails` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getPackageDetails` in SKILL.md: read its definition at `code/core/src/common/js-package-manager/JsPackageManager.ts:45` and add its signature, its purpose and a usage example.

### GAP-568: Missing export: getPresets

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/presets.ts:318
**Export:** getPresets

**Issue:** `getPresets` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getPresets` in SKILL.md: read its definition at `code/core/src/common/presets.ts:318` and add its signature, its purpose and a usage example.

### GAP-569: Missing export: getPrettier

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/formatter.ts:25
**Export:** getPrettier

**Issue:** `getPrettier` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getPrettier` in SKILL.md: read its definition at `code/core/src/common/utils/formatter.ts:25` and add its signature, its purpose and a usage example.

### GAP-570: Missing export: getProjectRoot

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/paths.ts:11
**Export:** getProjectRoot

**Issue:** `getProjectRoot` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getProjectRoot` in SKILL.md: read its definition at `code/core/src/common/utils/paths.ts:11` and add its signature, its purpose and a usage example.

### GAP-571: Missing export: getRealPath

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/resolve.ts:124
**Export:** getRealPath

**Issue:** `getRealPath` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getRealPath` in SKILL.md: read its definition at `code/core/src/mocking-utils/resolve.ts:124` and add its signature, its purpose and a usage example.

### GAP-572: Missing export: getRefs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-refs.ts:95
**Export:** getRefs

**Issue:** `getRefs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getRefs` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-refs.ts:95` and add its signature, its purpose and a usage example.

### GAP-573: Missing export: getRendererDir

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/dirs.ts:53
**Export:** getRendererDir

**Issue:** `getRendererDir` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getRendererDir` in SKILL.md: read its definition at `code/core/src/cli/dirs.ts:53` and add its signature, its purpose and a usage example.

### GAP-574: Missing export: getRendererName

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-renderer-name.ts:11
**Export:** getRendererName

**Issue:** `getRendererName` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getRendererName` in SKILL.md: read its definition at `code/core/src/common/utils/get-renderer-name.ts:11` and add its signature, its purpose and a usage example.

### GAP-575: Missing export: getStoryChildren

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/csf/csf-factories.ts:278
**Export:** getStoryChildren

**Issue:** `getStoryChildren` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getStoryChildren` in SKILL.md: read its definition at `code/core/src/csf/csf-factories.ts:278` and add its signature, its purpose and a usage example.

### GAP-576: Missing export: getStoryId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:62
**Export:** getStoryId

**Issue:** `getStoryId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getStoryId` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Story.tsx:62` and add its signature, its purpose and a usage example.

### GAP-577: Missing export: getStoryProps

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:75
**Export:** getStoryProps

**Issue:** `getStoryProps` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getStoryProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Story.tsx:75` and add its signature, its purpose and a usage example.

### GAP-578: Missing export: getStoryTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-story-id.ts:49
**Export:** getStoryTitle

**Issue:** `getStoryTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getStoryTitle` in SKILL.md: read its definition at `code/core/src/common/utils/get-story-id.ts:49` and add its signature, its purpose and a usage example.

### GAP-579: Missing export: getStorybookConfiguration

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-configuration.ts:7
**Export:** getStorybookConfiguration

**Issue:** `getStorybookConfiguration` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getStorybookConfiguration` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-configuration.ts:7` and add its signature, its purpose and a usage example.

### GAP-580: Missing export: getVersionSafe

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:145
**Export:** getVersionSafe

**Issue:** `getVersionSafe` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getVersionSafe` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:145` and add its signature, its purpose and a usage example.

### GAP-581: Missing export: globToRegexp

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/glob-to-regexp.ts:3
**Export:** globToRegexp

**Issue:** `globToRegexp` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `globToRegexp` in SKILL.md: read its definition at `code/core/src/common/utils/glob-to-regexp.ts:3` and add its signature, its purpose and a usage example.

### GAP-582: Missing export: globalPackages

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager/globals/globals.ts:24
**Export:** globalPackages

**Issue:** `globalPackages` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `globalPackages` in SKILL.md: read its definition at `code/core/src/manager/globals/globals.ts:24` and add its signature, its purpose and a usage example.

### GAP-583: Missing export: globalSettings

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/globalSettings.ts:61
**Export:** globalSettings

**Issue:** `globalSettings` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `globalSettings` in SKILL.md: read its definition at `code/core/src/cli/globalSettings.ts:61` and add its signature, its purpose and a usage example.

### GAP-584: Missing export: globalsNameReferenceMap

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager/globals/globals.ts:2
**Export:** globalsNameReferenceMap

**Issue:** `globalsNameReferenceMap` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `globalsNameReferenceMap` in SKILL.md: read its definition at `code/core/src/manager/globals/globals.ts:2` and add its signature, its purpose and a usage example.

### GAP-585: Missing export: groupBy

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/utils.ts:2
**Export:** groupBy

**Issue:** `groupBy` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `groupBy` in SKILL.md: read its definition at `code/core/src/common/utils/utils.ts:2` and add its signature, its purpose and a usage example.

### GAP-586: Missing export: hasDocgen

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:4
**Export:** hasDocgen

**Issue:** `hasDocgen` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `hasDocgen` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:4` and add its signature, its purpose and a usage example.

### GAP-587: Missing export: hasStorybookDependencies

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:248
**Export:** hasStorybookDependencies

**Issue:** `hasStorybookDependencies` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `hasStorybookDependencies` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:248` and add its signature, its purpose and a usage example.

### GAP-588: Missing export: importMetaResolve

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/shared/utils/module.ts:15
**Export:** importMetaResolve

**Issue:** `importMetaResolve` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `importMetaResolve` in SKILL.md: read its definition at `code/core/src/shared/utils/module.ts:15` and add its signature, its purpose and a usage example.

### GAP-589: Missing export: importModule

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/shared/utils/module.ts:65
**Export:** importModule

**Issue:** `importModule` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `importModule` in SKILL.md: read its definition at `code/core/src/shared/utils/module.ts:65` and add its signature, its purpose and a usage example.

### GAP-590: Missing export: includeConditionalArg

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/csf/includeConditionalArg.ts:31
**Export:** includeConditionalArg

**Issue:** `includeConditionalArg` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `includeConditionalArg` in SKILL.md: read its definition at `code/core/src/csf/includeConditionalArg.ts:31` and add its signature, its purpose and a usage example.

### GAP-591: Missing export: internal_checklistStore

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/stores/checklist.ts:14
**Export:** internal_checklistStore

**Issue:** `internal_checklistStore` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `internal_checklistStore` in SKILL.md: read its definition at `code/core/src/manager-api/stores/checklist.ts:14` and add its signature, its purpose and a usage example.

### GAP-592: Missing export: internal_getArgTypesData

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/renderers/react/src/preset.ts:87
**Export:** internal_getArgTypesData

**Issue:** `internal_getArgTypesData` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `internal_getArgTypesData` in SKILL.md: read its definition at `code/renderers/react/src/preset.ts:87` and add its signature, its purpose and a usage example.

### GAP-593: Missing export: internal_universalChecklistStore

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/stores/checklist.ts:9
**Export:** internal_universalChecklistStore

**Issue:** `internal_universalChecklistStore` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `internal_universalChecklistStore` in SKILL.md: read its definition at `code/core/src/manager-api/stores/checklist.ts:9` and add its signature, its purpose and a usage example.

### GAP-594: Missing export: interpolate

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/interpolate.ts:10
**Export:** interpolate

**Issue:** `interpolate` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `interpolate` in SKILL.md: read its definition at `code/core/src/common/utils/interpolate.ts:10` and add its signature, its purpose and a usage example.

### GAP-595: Missing export: invalidateProjectRootCache

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/paths.ts:59
**Export:** invalidateProjectRootCache

**Issue:** `invalidateProjectRootCache` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `invalidateProjectRootCache` in SKILL.md: read its definition at `code/core/src/common/utils/paths.ts:59` and add its signature, its purpose and a usage example.

### GAP-596: Missing export: invariant

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/utils.ts:18
**Export:** invariant

**Issue:** `invariant` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `invariant` in SKILL.md: read its definition at `code/core/src/common/utils/utils.ts:18` and add its signature, its purpose and a usage example.

### GAP-597: Missing export: isAddonA11yEnabled

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/a11y/src/preset.ts:3
**Export:** isAddonA11yEnabled

**Issue:** `isAddonA11yEnabled` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isAddonA11yEnabled` in SKILL.md: read its definition at `code/addons/a11y/src/preset.ts:3` and add its signature, its purpose and a usage example.

### GAP-598: Missing export: isCI

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/envs.ts:80
**Export:** isCI

**Issue:** `isCI` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isCI` in SKILL.md: read its definition at `code/core/src/common/utils/envs.ts:80` and add its signature, its purpose and a usage example.

### GAP-599: Missing export: isConfigAlreadySetup

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/postinstall.ts:410
**Export:** isConfigAlreadySetup

**Issue:** `isConfigAlreadySetup` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isConfigAlreadySetup` in SKILL.md: read its definition at `code/addons/vitest/src/postinstall.ts:410` and add its signature, its purpose and a usage example.

### GAP-600: Missing export: isCorePackage

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/cli.ts:141
**Export:** isCorePackage

**Issue:** `isCorePackage` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isCorePackage` in SKILL.md: read its definition at `code/core/src/common/utils/cli.ts:141` and add its signature, its purpose and a usage example.

### GAP-601: Missing export: isDefaultValueBlacklisted

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/utils/defaultValue.ts:3
**Export:** isDefaultValueBlacklisted

**Issue:** `isDefaultValueBlacklisted` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isDefaultValueBlacklisted` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/utils/defaultValue.ts:3` and add its signature, its purpose and a usage example.

### GAP-602: Missing export: isExternal

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/resolve.ts:112
**Export:** isExternal

**Issue:** `isExternal` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isExternal` in SKILL.md: read its definition at `code/core/src/mocking-utils/resolve.ts:112` and add its signature, its purpose and a usage example.

### GAP-603: Missing export: isFunctionNode

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/esmWalker.ts:320
**Export:** isFunctionNode

**Issue:** `isFunctionNode` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isFunctionNode` in SKILL.md: read its definition at `code/core/src/mocking-utils/esmWalker.ts:320` and add its signature, its purpose and a usage example.

### GAP-604: Missing export: isGetAbsolutePathWrapperNecessary

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:76
**Export:** isGetAbsolutePathWrapperNecessary

**Issue:** `isGetAbsolutePathWrapperNecessary` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isGetAbsolutePathWrapperNecessary` in SKILL.md: read its definition at `code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:76` and add its signature, its purpose and a usage example.

### GAP-605: Missing export: isInDestructuringAssignment

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/esmWalker.ts:333
**Export:** isInDestructuringAssignment

**Issue:** `isInDestructuringAssignment` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isInDestructuringAssignment` in SKILL.md: read its definition at `code/core/src/mocking-utils/esmWalker.ts:333` and add its signature, its purpose and a usage example.

### GAP-606: Missing export: isMacLike

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/platform.ts:5
**Export:** isMacLike

**Issue:** `isMacLike` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isMacLike` in SKILL.md: read its definition at `code/core/src/manager-api/lib/platform.ts:5` and add its signature, its purpose and a usage example.

### GAP-607: Missing export: isMeta

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/csf/csf-factories.ts:115
**Export:** isMeta

**Issue:** `isMeta` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isMeta` in SKILL.md: read its definition at `code/core/src/csf/csf-factories.ts:115` and add its signature, its purpose and a usage example.

### GAP-608: Missing export: isModuleDirectory

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/extract.ts:16
**Export:** isModuleDirectory

**Issue:** `isModuleDirectory` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isModuleDirectory` in SKILL.md: read its definition at `code/core/src/mocking-utils/extract.ts:16` and add its signature, its purpose and a usage example.

### GAP-609: Missing export: isNodeInPattern

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/esmWalker.ts:66
**Export:** isNodeInPattern

**Issue:** `isNodeInPattern` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isNodeInPattern` in SKILL.md: read its definition at `code/core/src/mocking-utils/esmWalker.ts:66` and add its signature, its purpose and a usage example.

### GAP-610: Missing export: isPreservingSymlinks

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/symlinks.ts:1
**Export:** isPreservingSymlinks

**Issue:** `isPreservingSymlinks` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isPreservingSymlinks` in SKILL.md: read its definition at `code/core/src/common/utils/symlinks.ts:1` and add its signature, its purpose and a usage example.

### GAP-611: Missing export: isPreview

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/csf/csf-factories.ts:84
**Export:** isPreview

**Issue:** `isPreview` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isPreview` in SKILL.md: read its definition at `code/core/src/csf/csf-factories.ts:84` and add its signature, its purpose and a usage example.

### GAP-612: Missing export: isSatelliteAddon

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/cli.ts:143
**Export:** isSatelliteAddon

**Issue:** `isSatelliteAddon` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isSatelliteAddon` in SKILL.md: read its definition at `code/core/src/common/utils/cli.ts:143` and add its signature, its purpose and a usage example.

### GAP-613: Missing export: isShortcutTaken

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:10
**Export:** isShortcutTaken

**Issue:** `isShortcutTaken` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isShortcutTaken` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:10` and add its signature, its purpose and a usage example.

### GAP-614: Missing export: isStaticProperty

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/esmWalker.ts:311
**Export:** isStaticProperty

**Issue:** `isStaticProperty` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isStaticProperty` in SKILL.md: read its definition at `code/core/src/mocking-utils/esmWalker.ts:311` and add its signature, its purpose and a usage example.

### GAP-615: Missing export: isStaticPropertyKey

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/esmWalker.ts:315
**Export:** isStaticPropertyKey

**Issue:** `isStaticPropertyKey` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isStaticPropertyKey` in SKILL.md: read its definition at `code/core/src/mocking-utils/esmWalker.ts:315` and add its signature, its purpose and a usage example.

### GAP-616: Missing export: isStory

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/csf/csf-factories.ts:173
**Export:** isStory

**Issue:** `isStory` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isStory` in SKILL.md: read its definition at `code/core/src/csf/csf-factories.ts:173` and add its signature, its purpose and a usage example.

### GAP-617: Missing export: isTooLongForDefaultValueSummary

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/utils.ts:10
**Export:** isTooLongForDefaultValueSummary

**Issue:** `isTooLongForDefaultValueSummary` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isTooLongForDefaultValueSummary` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/utils.ts:10` and add its signature, its purpose and a usage example.

### GAP-618: Missing export: isTooLongForTypeSummary

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/utils.ts:6
**Export:** isTooLongForTypeSummary

**Issue:** `isTooLongForTypeSummary` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isTooLongForTypeSummary` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/utils.ts:6` and add its signature, its purpose and a usage example.

### GAP-619: Missing export: isValidDocgenSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:10
**Export:** isValidDocgenSection

**Issue:** `isValidDocgenSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isValidDocgenSection` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:10` and add its signature, its purpose and a usage example.

### GAP-620: Missing export: keyToSymbol

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:137
**Export:** keyToSymbol

**Issue:** `keyToSymbol` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `keyToSymbol` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:137` and add its signature, its purpose and a usage example.

### GAP-621: Missing export: load

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/bin/loader.ts:90
**Export:** load

**Issue:** `load` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `load` in SKILL.md: read its definition at `code/core/src/bin/loader.ts:90` and add its signature, its purpose and a usage example.

### GAP-622: Missing export: loadAllPresets

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/presets.ts:330
**Export:** loadAllPresets

**Issue:** `loadAllPresets` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `loadAllPresets` in SKILL.md: read its definition at `code/core/src/common/presets.ts:330` and add its signature, its purpose and a usage example.

### GAP-623: Missing export: loadEnvs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/envs.ts:9
**Export:** loadEnvs

**Issue:** `loadEnvs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `loadEnvs` in SKILL.md: read its definition at `code/core/src/common/utils/envs.ts:9` and add its signature, its purpose and a usage example.

### GAP-624: Missing export: loadManagerOrAddonsFile

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/load-manager-or-addons-file.ts:9
**Export:** loadManagerOrAddonsFile

**Issue:** `loadManagerOrAddonsFile` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `loadManagerOrAddonsFile` in SKILL.md: read its definition at `code/core/src/common/utils/load-manager-or-addons-file.ts:9` and add its signature, its purpose and a usage example.

### GAP-625: Missing export: loadPreset

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/presets.ts:156
**Export:** loadPreset

**Issue:** `loadPreset` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `loadPreset` in SKILL.md: read its definition at `code/core/src/common/presets.ts:156` and add its signature, its purpose and a usage example.

### GAP-626: Missing export: loadPreviewOrConfigFile

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/load-preview-or-config-file.ts:7
**Export:** loadPreviewOrConfigFile

**Issue:** `loadPreviewOrConfigFile` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `loadPreviewOrConfigFile` in SKILL.md: read its definition at `code/core/src/common/utils/load-preview-or-config-file.ts:7` and add its signature, its purpose and a usage example.

### GAP-627: Missing export: logConfig

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/log-config.ts:3
**Export:** logConfig

**Issue:** `logConfig` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `logConfig` in SKILL.md: read its definition at `code/core/src/common/utils/log-config.ts:3` and add its signature, its purpose and a usage example.

### GAP-628: Missing export: merge

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/merge.ts
**Export:** merge

**Issue:** `merge` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `merge` in SKILL.md: read its definition at `code/core/src/manager-api/lib/merge.ts` and add its signature, its purpose and a usage example.

### GAP-629: Missing export: modifyErrorMessage

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/vitest-plugin/setup-file.ts:22
**Export:** modifyErrorMessage

**Issue:** `modifyErrorMessage` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `modifyErrorMessage` in SKILL.md: read its definition at `code/addons/vitest/src/vitest-plugin/setup-file.ts:22` and add its signature, its purpose and a usage example.

### GAP-630: Missing type: module.exports

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/vitest/src/node/coverage-reporter.ts:56
**Export:** module.exports

**Issue:** the type `module.exports` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `module.exports` in SKILL.md: read its definition at `code/addons/vitest/src/node/coverage-reporter.ts:56` and list its fields or members.

### GAP-631: Missing export: mount

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/renderers/react/src/mount.ts:5
**Export:** mount

**Issue:** `mount` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `mount` in SKILL.md: read its definition at `code/renderers/react/src/mount.ts:5` and add its signature, its purpose and a usage example.

### GAP-632: Missing export: nodePathsToArray

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/paths.ts:73
**Export:** nodePathsToArray

**Issue:** `nodePathsToArray` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `nodePathsToArray` in SKILL.md: read its definition at `code/core/src/common/utils/paths.ts:73` and add its signature, its purpose and a usage example.

### GAP-633: Missing export: normalizeExtends

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/eslintPlugin.ts:250
**Export:** normalizeExtends

**Issue:** `normalizeExtends` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `normalizeExtends` in SKILL.md: read its definition at `code/core/src/cli/eslintPlugin.ts:250` and add its signature, its purpose and a usage example.

### GAP-634: Missing export: normalizeNewlines

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/utils.ts:21
**Export:** normalizeNewlines

**Issue:** `normalizeNewlines` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `normalizeNewlines` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/utils.ts:21` and add its signature, its purpose and a usage example.

### GAP-635: Missing export: normalizeStoriesEntry

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/normalize-stories.ts:38
**Export:** normalizeStoriesEntry

**Issue:** `normalizeStoriesEntry` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `normalizeStoriesEntry` in SKILL.md: read its definition at `code/core/src/common/utils/normalize-stories.ts:38` and add its signature, its purpose and a usage example.

### GAP-636: Missing export: normalizeStoryPath

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/paths.ts:82
**Export:** normalizeStoryPath

**Issue:** `normalizeStoryPath` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `normalizeStoryPath` in SKILL.md: read its definition at `code/core/src/common/utils/paths.ts:82` and add its signature, its purpose and a usage example.

### GAP-637: Missing export: optimizeViteDeps

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/preset.ts:224
**Export:** optimizeViteDeps

**Issue:** `optimizeViteDeps` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `optimizeViteDeps` in SKILL.md: read its definition at `code/addons/docs/src/preset.ts:224` and add its signature, its purpose and a usage example.

### GAP-638: Missing export: optionOrAltSymbol

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:8
**Export:** optionOrAltSymbol

**Issue:** `optionOrAltSymbol` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `optionOrAltSymbol` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:8` and add its signature, its purpose and a usage example.

### GAP-639: Missing export: optionalEnvToBoolean

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/envs.ts:61
**Export:** optionalEnvToBoolean

**Issue:** `optionalEnvToBoolean` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `optionalEnvToBoolean` in SKILL.md: read its definition at `code/core/src/common/utils/envs.ts:61` and add its signature, its purpose and a usage example.

### GAP-640: Missing export: parseJsDoc

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/jsdocParser.ts:75
**Export:** parseJsDoc

**Issue:** `parseJsDoc` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `parseJsDoc` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/jsdocParser.ts:75` and add its signature, its purpose and a usage example.

### GAP-641: Missing export: parseList

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/cli.ts:62
**Export:** parseList

**Issue:** `parseList` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `parseList` in SKILL.md: read its definition at `code/core/src/common/utils/cli.ts:62` and add its signature, its purpose and a usage example.

### GAP-642: Missing export: pauseAnimations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18
**Export:** pauseAnimations

**Issue:** `pauseAnimations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `pauseAnimations` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18` and add its signature, its purpose and a usage example.

### GAP-643: Missing export: posix

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/posix.ts:4
**Export:** posix

**Issue:** `posix` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `posix` in SKILL.md: read its definition at `code/core/src/common/utils/posix.ts:4` and add its signature, its purpose and a usage example.

### GAP-644: Missing export: readFileAsJson

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:25
**Export:** readFileAsJson

**Issue:** `readFileAsJson` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `readFileAsJson` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:25` and add its signature, its purpose and a usage example.

### GAP-645: Missing export: readTemplate

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/readTemplate.ts:3
**Export:** readTemplate

**Issue:** `readTemplate` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `readTemplate` in SKILL.md: read its definition at `code/core/src/common/utils/readTemplate.ts:3` and add its signature, its purpose and a usage example.

### GAP-646: Missing export: removeAddon

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/remove.ts:24
**Export:** removeAddon

**Issue:** `removeAddon` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `removeAddon` in SKILL.md: read its definition at `code/core/src/common/utils/remove.ts:24` and add its signature, its purpose and a usage example.

### GAP-647: Missing export: rendererPackages

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/get-storybook-info.ts:22
**Export:** rendererPackages

**Issue:** `rendererPackages` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `rendererPackages` in SKILL.md: read its definition at `code/core/src/common/utils/get-storybook-info.ts:22` and add its signature, its purpose and a usage example.

### GAP-648: Missing export: resolveAddonName

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/presets.ts:68
**Export:** resolveAddonName

**Issue:** `resolveAddonName` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `resolveAddonName` in SKILL.md: read its definition at `code/core/src/common/presets.ts:68` and add its signature, its purpose and a usage example.

### GAP-649: Missing export: resolveExternalModule

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/resolve.ts:34
**Export:** resolveExternalModule

**Issue:** `resolveExternalModule` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `resolveExternalModule` in SKILL.md: read its definition at `code/core/src/mocking-utils/resolve.ts:34` and add its signature, its purpose and a usage example.

### GAP-650: Missing export: resolveImport

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/interpret-files.ts:25
**Export:** resolveImport

**Issue:** `resolveImport` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `resolveImport` in SKILL.md: read its definition at `code/core/src/common/utils/interpret-files.ts:25` and add its signature, its purpose and a usage example.

### GAP-651: Missing export: resolveMock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/resolve.ts:74
**Export:** resolveMock

**Issue:** `resolveMock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `resolveMock` in SKILL.md: read its definition at `code/core/src/mocking-utils/resolve.ts:74` and add its signature, its purpose and a usage example.

### GAP-652: Missing export: resolvePackageDir

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/shared/utils/module.ts:28
**Export:** resolvePackageDir

**Issue:** `resolvePackageDir` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `resolvePackageDir` in SKILL.md: read its definition at `code/core/src/shared/utils/module.ts:28` and add its signature, its purpose and a usage example.

### GAP-653: Missing export: resolvePathInStorybookCache

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/resolve-path-in-sb-cache.ts:20
**Export:** resolvePathInStorybookCache

**Issue:** `resolvePathInStorybookCache` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `resolvePathInStorybookCache` in SKILL.md: read its definition at `code/core/src/common/utils/resolve-path-in-sb-cache.ts:20` and add its signature, its purpose and a usage example.

### GAP-654: Missing export: resolveWithExtension

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/bin/loader.ts:34
**Export:** resolveWithExtension

**Issue:** `resolveWithExtension` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `resolveWithExtension` in SKILL.md: read its definition at `code/core/src/bin/loader.ts:34` and add its signature, its purpose and a usage example.

### GAP-655: Missing export: resolveWithExtensions

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/resolve.ts:140
**Export:** resolveWithExtensions

**Issue:** `resolveWithExtensions` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `resolveWithExtensions` in SKILL.md: read its definition at `code/core/src/mocking-utils/resolve.ts:140` and add its signature, its purpose and a usage example.

### GAP-656: Missing export: resolvedReact

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/preset.ts:208
**Export:** resolvedReact

**Issue:** `resolvedReact` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `resolvedReact` in SKILL.md: read its definition at `code/addons/docs/src/preset.ts:208` and add its signature, its purpose and a usage example.

### GAP-657: Missing export: responsiveViewport

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/responsiveViewport.tsx:4
**Export:** responsiveViewport

**Issue:** `responsiveViewport` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `responsiveViewport` in SKILL.md: read its definition at `code/core/src/viewport/responsiveViewport.tsx:4` and add its signature, its purpose and a usage example.

### GAP-658: Missing export: rewriteSbMockImportCalls

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/extract.ts:54
**Export:** rewriteSbMockImportCalls

**Issue:** `rewriteSbMockImportCalls` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `rewriteSbMockImportCalls` in SKILL.md: read its definition at `code/core/src/mocking-utils/extract.ts:54` and add its signature, its purpose and a usage example.

### GAP-659: Missing export: safeResolveModule

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/shared/utils/module.ts:126
**Export:** safeResolveModule

**Issue:** `safeResolveModule` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `safeResolveModule` in SKILL.md: read its definition at `code/core/src/shared/utils/module.ts:126` and add its signature, its purpose and a usage example.

### GAP-660: Missing export: satisfies

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/satisfies.ts:2
**Export:** satisfies

**Issue:** `satisfies` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `satisfies` in SKILL.md: read its definition at `code/core/src/common/utils/satisfies.ts:2` and add its signature, its purpose and a usage example.

### GAP-661: Missing export: scanAndTransformFiles

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/scan-and-transform-files.ts:13
**Export:** scanAndTransformFiles

**Issue:** `scanAndTransformFiles` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `scanAndTransformFiles` in SKILL.md: read its definition at `code/core/src/common/utils/scan-and-transform-files.ts:13` and add its signature, its purpose and a usage example.

### GAP-662: Missing export: serverRequire

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/interpret-require.ts:17
**Export:** serverRequire

**Issue:** `serverRequire` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `serverRequire` in SKILL.md: read its definition at `code/core/src/common/utils/interpret-require.ts:17` and add its signature, its purpose and a usage example.

### GAP-663: Missing export: setCompodocJson

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/angular/index.ts:1
**Export:** setCompodocJson

**Issue:** `setCompodocJson` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `setCompodocJson` in SKILL.md: read its definition at `code/addons/docs/src/angular/index.ts:1` and add its signature, its purpose and a usage example.

### GAP-664: Missing export: setIsNodeInPattern

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/mocking-utils/esmWalker.ts:63
**Export:** setIsNodeInPattern

**Issue:** `setIsNodeInPattern` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `setIsNodeInPattern` in SKILL.md: read its definition at `code/core/src/mocking-utils/esmWalker.ts:63` and add its signature, its purpose and a usage example.

### GAP-665: Missing export: setJSONDoc

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/ember/index.ts:1
**Export:** setJSONDoc

**Issue:** `setJSONDoc` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `setJSONDoc` in SKILL.md: read its definition at `code/addons/docs/src/ember/index.ts:1` and add its signature, its purpose and a usage example.

### GAP-666: Missing export: setup

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/vitest-plugin/global-setup.ts:71
**Export:** setup

**Issue:** `setup` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `setup` in SKILL.md: read its definition at `code/addons/vitest/src/vitest-plugin/global-setup.ts:71` and add its signature, its purpose and a usage example.

### GAP-667: Missing export: setupAddonInConfig

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/setup-addon-in-config.ts:24
**Export:** setupAddonInConfig

**Issue:** `setupAddonInConfig` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `setupAddonInConfig` in SKILL.md: read its definition at `code/core/src/common/utils/setup-addon-in-config.ts:24` and add its signature, its purpose and a usage example.

### GAP-668: Missing export: shortcutMatchesShortcut

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:102
**Export:** shortcutMatchesShortcut

**Issue:** `shortcutMatchesShortcut` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `shortcutMatchesShortcut` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:102` and add its signature, its purpose and a usage example.

### GAP-669: Missing export: shortcutToAriaKeyshortcuts

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:180
**Export:** shortcutToAriaKeyshortcuts

**Issue:** `shortcutToAriaKeyshortcuts` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `shortcutToAriaKeyshortcuts` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:180` and add its signature, its purpose and a usage example.

### GAP-670: Missing export: shortcutToHumanString

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/lib/shortcut.ts:175
**Export:** shortcutToHumanString

**Issue:** `shortcutToHumanString` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `shortcutToHumanString` in SKILL.md: read its definition at `code/core/src/manager-api/lib/shortcut.ts:175` and add its signature, its purpose and a usage example.

### GAP-671: Missing export: simulateDOMContentLoaded

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31
**Export:** simulateDOMContentLoaded

**Issue:** `simulateDOMContentLoaded` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `simulateDOMContentLoaded` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31` and add its signature, its purpose and a usage example.

### GAP-672: Missing export: simulatePageLoad

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83
**Export:** simulatePageLoad

**Issue:** `simulatePageLoad` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `simulatePageLoad` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83` and add its signature, its purpose and a usage example.

### GAP-673: Missing export: slugs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Heading.tsx:15
**Export:** slugs

**Issue:** `slugs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `slugs` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Heading.tsx:15` and add its signature, its purpose and a usage example.

### GAP-674: Missing export: staticDirs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/preset.ts:308
**Export:** staticDirs

**Issue:** `staticDirs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `staticDirs` in SKILL.md: read its definition at `code/addons/vitest/src/preset.ts:308` and add its signature, its purpose and a usage example.

### GAP-675: Missing export: str

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/docgen/utils/string.ts:1
**Export:** str

**Issue:** `str` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `str` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/docgen/utils/string.ts:1` and add its signature, its purpose and a usage example.

### GAP-676: Missing export: stringifyEnvs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/envs.ts:47
**Export:** stringifyEnvs

**Issue:** `stringifyEnvs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `stringifyEnvs` in SKILL.md: read its definition at `code/core/src/common/utils/envs.ts:47` and add its signature, its purpose and a usage example.

### GAP-677: Missing export: stringifyProcessEnvs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/envs.ts:53
**Export:** stringifyProcessEnvs

**Issue:** `stringifyProcessEnvs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `stringifyProcessEnvs` in SKILL.md: read its definition at `code/core/src/common/utils/envs.ts:53` and add its signature, its purpose and a usage example.

### GAP-678: Missing export: suggestESLintPlugin

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/eslintPlugin.ts:331
**Export:** suggestESLintPlugin

**Issue:** `suggestESLintPlugin` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `suggestESLintPlugin` in SKILL.md: read its definition at `code/core/src/cli/eslintPlugin.ts:331` and add its signature, its purpose and a usage example.

### GAP-679: Missing export: supportedExtensions

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/bin/loader.ts:19
**Export:** supportedExtensions

**Issue:** `supportedExtensions` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `supportedExtensions` in SKILL.md: read its definition at `code/core/src/bin/loader.ts:19` and add its signature, its purpose and a usage example.

### GAP-680: Missing export: syncPreviewAddonsWithMainConfig

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/sync-main-preview-addons.ts:31
**Export:** syncPreviewAddonsWithMainConfig

**Issue:** `syncPreviewAddonsWithMainConfig` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `syncPreviewAddonsWithMainConfig` in SKILL.md: read its definition at `code/core/src/common/utils/sync-main-preview-addons.ts:31` and add its signature, its purpose and a usage example.

### GAP-681: Missing export: syncStorybookAddons

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/sync-main-preview-addons.ts:16
**Export:** syncStorybookAddons

**Issue:** `syncStorybookAddons` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `syncStorybookAddons` in SKILL.md: read its definition at `code/core/src/common/utils/sync-main-preview-addons.ts:16` and add its signature, its purpose and a usage example.

### GAP-682: Missing export: teardown

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/vitest-plugin/global-setup.ts:77
**Export:** teardown

**Issue:** `teardown` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `teardown` in SKILL.md: read its definition at `code/addons/vitest/src/vitest-plugin/global-setup.ts:77` and add its signature, its purpose and a usage example.

### GAP-683: Missing export: temporaryDirectory

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/cli.ts:18
**Export:** temporaryDirectory

**Issue:** `temporaryDirectory` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `temporaryDirectory` in SKILL.md: read its definition at `code/core/src/common/utils/cli.ts:18` and add its signature, its purpose and a usage example.

### GAP-684: Missing export: temporaryFile

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/cli.ts:47
**Export:** temporaryFile

**Issue:** `temporaryFile` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `temporaryFile` in SKILL.md: read its definition at `code/core/src/common/utils/cli.ts:47` and add its signature, its purpose and a usage example.

### GAP-685: Missing export: testStory

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/vitest-plugin/test-utils.ts:34
**Export:** testStory

**Issue:** `testStory` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `testStory` in SKILL.md: read its definition at `code/addons/vitest/src/vitest-plugin/test-utils.ts:34` and add its signature, its purpose and a usage example.

### GAP-686: Missing export: tokens

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:104
**Export:** tokens

**Issue:** `tokens` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `tokens` in SKILL.md: read its definition at `code/core/src/theming/base.ts:104` and add its signature, its purpose and a usage example.

### GAP-687: Missing export: transformImportFiles

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/transform-imports.ts:19
**Export:** transformImportFiles

**Issue:** `transformImportFiles` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `transformImportFiles` in SKILL.md: read its definition at `code/core/src/common/utils/transform-imports.ts:19` and add its signature, its purpose and a usage example.

### GAP-688: Missing export: typography

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:59
**Export:** typography

**Issue:** `typography` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `typography` in SKILL.md: read its definition at `code/core/src/theming/base.ts:59` and add its signature, its purpose and a usage example.

### GAP-689: Missing export: uninstrumentedUserEvent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:121
**Export:** uninstrumentedUserEvent

**Issue:** `uninstrumentedUserEvent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `uninstrumentedUserEvent` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:121` and add its signature, its purpose and a usage example.

### GAP-690: Missing export: useAddonState

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/root.tsx:458
**Export:** useAddonState

**Issue:** `useAddonState` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useAddonState` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:458` and add its signature, its purpose and a usage example.

### GAP-691: Missing export: useArgTypes

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/root.tsx:501
**Export:** useArgTypes

**Issue:** `useArgTypes` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useArgTypes` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:501` and add its signature, its purpose and a usage example.

### GAP-692: Missing export: useGlobalTypes

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/root.tsx:491
**Export:** useGlobalTypes

**Issue:** `useGlobalTypes` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useGlobalTypes` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:491` and add its signature, its purpose and a usage example.

### GAP-693: Missing export: useSharedState

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/root.tsx:371
**Export:** useSharedState

**Issue:** `useSharedState` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useSharedState` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:371` and add its signature, its purpose and a usage example.

### GAP-694: Missing export: useSourceProps

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:101
**Export:** useSourceProps

**Issue:** `useSourceProps` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useSourceProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Source.tsx:101` and add its signature, its purpose and a usage example.

### GAP-695: Missing export: useStoryPrepared

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/root.tsx:341
**Export:** useStoryPrepared

**Issue:** `useStoryPrepared` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useStoryPrepared` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:341` and add its signature, its purpose and a usage example.

### GAP-696: Missing export: useStorybookApi

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/root.tsx:297
**Export:** useStorybookApi

**Issue:** `useStorybookApi` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useStorybookApi` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:297` and add its signature, its purpose and a usage example.

### GAP-697: Missing export: useStorybookState

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/manager-api/root.tsx:293
**Export:** useStorybookState

**Issue:** `useStorybookState` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useStorybookState` in SKILL.md: read its definition at `code/core/src/manager-api/root.tsx:293` and add its signature, its purpose and a usage example.

### GAP-698: Missing export: validateConfigurationFiles

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/validate-configuration-files.ts:14
**Export:** validateConfigurationFiles

**Issue:** `validateConfigurationFiles` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `validateConfigurationFiles` in SKILL.md: read its definition at `code/core/src/common/utils/validate-configuration-files.ts:14` and add its signature, its purpose and a usage example.

### GAP-699: Missing export: validateFrameworkName

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/validate-config.ts:16
**Export:** validateFrameworkName

**Issue:** `validateFrameworkName` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `validateFrameworkName` in SKILL.md: read its definition at `code/core/src/common/utils/validate-config.ts:16` and add its signature, its purpose and a usage example.

### GAP-700: Missing export: versions

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/versions.ts
**Export:** versions

**Issue:** `versions` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `versions` in SKILL.md: read its definition at `code/core/src/common/versions.ts` and add its signature, its purpose and a usage example.

### GAP-701: Missing export: viteCorePlugins

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/builders/builder-vite/src/preset.ts:19
**Export:** viteCorePlugins

**Issue:** `viteCorePlugins` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `viteCorePlugins` in SKILL.md: read its definition at `code/builders/builder-vite/src/preset.ts:19` and add its signature, its purpose and a usage example.

### GAP-702: Missing export: waitForAnimations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54
**Export:** waitForAnimations

**Issue:** `waitForAnimations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `waitForAnimations` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54` and add its signature, its purpose and a usage example.

### GAP-703: Missing export: webpack

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/preset.ts:224
**Export:** webpack

**Issue:** `webpack` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `webpack` in SKILL.md: read its definition at `code/addons/docs/src/preset.ts:224` and add its signature, its purpose and a usage example.

### GAP-704: Missing export: wrapValueWithGetAbsolutePathWrapper

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:191
**Export:** wrapValueWithGetAbsolutePathWrapper

**Issue:** `wrapValueWithGetAbsolutePathWrapper` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `wrapValueWithGetAbsolutePathWrapper` in SKILL.md: read its definition at `code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:191` and add its signature, its purpose and a usage example.

### GAP-705: Missing export: writeFileAsJson

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/cli/helpers.ts:42
**Export:** writeFileAsJson

**Issue:** `writeFileAsJson` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `writeFileAsJson` in SKILL.md: read its definition at `code/core/src/cli/helpers.ts:42` and add its signature, its purpose and a usage example.

### GAP-706: Stale documentation: A

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:184
**Export:** A

**Issue:** SKILL.md documents `A`, which the enumerated source API surface lacks

**Remediation:** Check `A` against the source and update or remove its documentation at SKILL.md:184: the enumerated source surface does not export it.

### GAP-707: Stale documentation: ActionBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** ActionBar

**Issue:** SKILL.md documents `ActionBar`, which the enumerated source API surface lacks

**Remediation:** Check `ActionBar` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-708: Stale documentation: ActionList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** ActionList

**Issue:** SKILL.md documents `ActionList`, which the enumerated source API surface lacks

**Remediation:** Check `ActionList` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-709: Stale documentation: AddonPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** AddonPanel

**Issue:** SKILL.md documents `AddonPanel`, which the enumerated source API surface lacks

**Remediation:** Check `AddonPanel` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-711: Stale documentation: Badge

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Badge

**Issue:** SKILL.md documents `Badge`, which the enumerated source API surface lacks

**Remediation:** Check `Badge` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-712: Stale documentation: Bar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** Bar

**Issue:** SKILL.md documents `Bar`, which the enumerated source API surface lacks

**Remediation:** Check `Bar` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-714: Stale documentation: Blockquote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Blockquote

**Issue:** SKILL.md documents `Blockquote`, which the enumerated source API surface lacks

**Remediation:** Check `Blockquote` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-715: Stale documentation: Button

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:44
**Export:** Button

**Issue:** SKILL.md documents `Button`, which the enumerated source API surface lacks

**Remediation:** Check `Button` against the source and update or remove its documentation at SKILL.md:44: the enumerated source surface does not export it.

### GAP-716: Stale documentation: CHANNEL_CREATED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** CHANNEL_CREATED

**Issue:** SKILL.md documents `CHANNEL_CREATED`, which the enumerated source API surface lacks

**Remediation:** Check `CHANNEL_CREATED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-717: Stale documentation: CSSObject

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:178
**Export:** CSSObject

**Issue:** SKILL.md documents `CSSObject`, which the enumerated source API surface lacks

**Remediation:** Check `CSSObject` against the source and update or remove its documentation at references/core-api.md:178: the enumerated source surface does not export it.

### GAP-718: Stale documentation: CacheProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:171
**Export:** CacheProvider

**Issue:** SKILL.md documents `CacheProvider`, which the enumerated source API surface lacks

**Remediation:** Check `CacheProvider` against the source and update or remove its documentation at references/core-api.md:171: the enumerated source surface does not export it.

### GAP-719: Stale documentation: Card

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** Card

**Issue:** SKILL.md documents `Card`, which the enumerated source API surface lacks

**Remediation:** Check `Card` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-720: Stale documentation: Channel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:127
**Export:** Channel

**Issue:** SKILL.md documents `Channel`, which the enumerated source API surface lacks

**Remediation:** Check `Channel` against the source and update or remove its documentation at references/core-api.md:127: the enumerated source surface does not export it.

### GAP-721: Stale documentation: CheckboxControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:192
**Export:** CheckboxControl

**Issue:** SKILL.md documents `CheckboxControl`, which the enumerated source API surface lacks

**Remediation:** Check `CheckboxControl` against the source and update or remove its documentation at references/doc-blocks.md:192: the enumerated source surface does not export it.

### GAP-722: Stale documentation: ClassNames

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:171
**Export:** ClassNames

**Issue:** SKILL.md documents `ClassNames`, which the enumerated source API surface lacks

**Remediation:** Check `ClassNames` against the source and update or remove its documentation at references/core-api.md:171: the enumerated source surface does not export it.

### GAP-723: Stale documentation: Code

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Code

**Issue:** SKILL.md documents `Code`, which the enumerated source API surface lacks

**Remediation:** Check `Code` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-724: Stale documentation: Collapsible

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** Collapsible

**Issue:** SKILL.md documents `Collapsible`, which the enumerated source API surface lacks

**Remediation:** Check `Collapsible` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-725: Stale documentation: ColorControlProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:173
**Export:** ColorControlProps

**Issue:** SKILL.md documents `ColorControlProps`, which the enumerated source API surface lacks

**Remediation:** Check `ColorControlProps` against the source and update or remove its documentation at references/doc-blocks.md:173: the enumerated source surface does not export it.

### GAP-727: Stale documentation: ConfigFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** ConfigFile

**Issue:** SKILL.md documents `ConfigFile`, which the enumerated source API surface lacks

**Remediation:** Check `ConfigFile` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-728: Stale documentation: CsfFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** CsfFile

**Issue:** SKILL.md documents `CsfFile`, which the enumerated source API surface lacks

**Remediation:** Check `CsfFile` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-729: Stale documentation: DL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** DL

**Issue:** SKILL.md documents `DL`, which the enumerated source API surface lacks

**Remediation:** Check `DL` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-732: Stale documentation: Div

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Div

**Issue:** SKILL.md documents `Div`, which the enumerated source API surface lacks

**Remediation:** Check `Div` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-734: Stale documentation: ErrorFormatter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** ErrorFormatter

**Issue:** SKILL.md documents `ErrorFormatter`, which the enumerated source API surface lacks

**Remediation:** Check `ErrorFormatter` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-735: Stale documentation: FlexBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** FlexBar

**Issue:** SKILL.md documents `FlexBar`, which the enumerated source API surface lacks

**Remediation:** Check `FlexBar` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-736: Stale documentation: Form

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** Form

**Issue:** SKILL.md documents `Form`, which the enumerated source API surface lacks

**Remediation:** Check `Form` against the source and update or remove its documentation at references/core-api.md:313: the enumerated source surface does not export it.

### GAP-738: Stale documentation: GLOBALS_UPDATED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** GLOBALS_UPDATED

**Issue:** SKILL.md documents `GLOBALS_UPDATED`, which the enumerated source API surface lacks

**Remediation:** Check `GLOBALS_UPDATED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-739: Stale documentation: Global

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:56
**Export:** Global

**Issue:** SKILL.md documents `Global`, which the enumerated source API surface lacks

**Remediation:** Check `Global` against the source and update or remove its documentation at references/core-api.md:56: the enumerated source surface does not export it.

### GAP-741: Stale documentation: H1

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** H1

**Issue:** SKILL.md documents `H1`, which the enumerated source API surface lacks

**Remediation:** Check `H1` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-742: Stale documentation: H6

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** H6

**Issue:** SKILL.md documents `H6`, which the enumerated source API surface lacks

**Remediation:** Check `H6` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-743: Stale documentation: HR

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** HR

**Issue:** SKILL.md documents `HR`, which the enumerated source API surface lacks

**Remediation:** Check `HR` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-745: Stale documentation: IconButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** IconButton

**Issue:** SKILL.md documents `IconButton`, which the enumerated source API surface lacks

**Remediation:** Check `IconButton` against the source and update or remove its documentation at references/core-api.md:313: the enumerated source surface does not export it.

### GAP-747: Stale documentation: Keyframes

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:178
**Export:** Keyframes

**Issue:** SKILL.md documents `Keyframes`, which the enumerated source API surface lacks

**Remediation:** Check `Keyframes` against the source and update or remove its documentation at references/core-api.md:178: the enumerated source surface does not export it.

### GAP-748: Stale documentation: LI

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** LI

**Issue:** SKILL.md documents `LI`, which the enumerated source API surface lacks

**Remediation:** Check `LI` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-751: Stale documentation: MaybeMocked

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:62
**Export:** MaybeMocked

**Issue:** SKILL.md documents `MaybeMocked`, which the enumerated source API surface lacks

**Remediation:** Check `MaybeMocked` against the source and update or remove its documentation at references/core-api.md:62: the enumerated source surface does not export it.

### GAP-752: Stale documentation: Mock

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:53
**Export:** Mock

**Issue:** SKILL.md documents `Mock`, which the enumerated source API surface lacks

**Remediation:** Check `Mock` against the source and update or remove its documentation at references/core-api.md:53: the enumerated source surface does not export it.

### GAP-753: Stale documentation: MockInstance

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:62
**Export:** MockInstance

**Issue:** SKILL.md documents `MockInstance`, which the enumerated source API surface lacks

**Remediation:** Check `MockInstance` against the source and update or remove its documentation at references/core-api.md:62: the enumerated source surface does not export it.

### GAP-754: Stale documentation: Modal

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** Modal

**Issue:** SKILL.md documents `Modal`, which the enumerated source API surface lacks

**Remediation:** Check `Modal` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-755: Stale documentation: NodePath

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** NodePath

**Issue:** SKILL.md documents `NodePath`, which the enumerated source API surface lacks

**Remediation:** Check `NodePath` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-756: Stale documentation: OL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** OL

**Issue:** SKILL.md documents `OL`, which the enumerated source API surface lacks

**Remediation:** Check `OL` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-757: Stale documentation: P

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** P

**Issue:** SKILL.md documents `P`, which the enumerated source API surface lacks

**Remediation:** Check `P` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-758: Stale documentation: PREVIEW_INITIALIZED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** PREVIEW_INITIALIZED

**Issue:** SKILL.md documents `PREVIEW_INITIALIZED`, which the enumerated source API surface lacks

**Remediation:** Check `PREVIEW_INITIALIZED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-759: Stale documentation: Placeholder

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** Placeholder

**Issue:** SKILL.md documents `Placeholder`, which the enumerated source API surface lacks

**Remediation:** Check `Placeholder` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-760: Stale documentation: Popover

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** Popover

**Issue:** SKILL.md documents `Popover`, which the enumerated source API surface lacks

**Remediation:** Check `Popover` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-761: Stale documentation: PopoverProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** PopoverProvider

**Issue:** SKILL.md documents `PopoverProvider`, which the enumerated source API surface lacks

**Remediation:** Check `PopoverProvider` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-762: Stale documentation: PostMessageTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:330
**Export:** PostMessageTransport

**Issue:** SKILL.md documents `PostMessageTransport`, which the enumerated source API surface lacks

**Remediation:** Check `PostMessageTransport` against the source and update or remove its documentation at references/core-api.md:330: the enumerated source surface does not export it.

### GAP-763: Stale documentation: Pre

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Pre

**Issue:** SKILL.md documents `Pre`, which the enumerated source API surface lacks

**Remediation:** Check `Pre` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-764: Stale documentation: RadioControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:192
**Export:** RadioControl

**Issue:** SKILL.md documents `RadioControl`, which the enumerated source API surface lacks

**Remediation:** Check `RadioControl` against the source and update or remove its documentation at references/doc-blocks.md:192: the enumerated source surface does not export it.

### GAP-767: Stale documentation: SELECT_STORY

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** SELECT_STORY

**Issue:** SKILL.md documents `SELECT_STORY`, which the enumerated source API surface lacks

**Remediation:** Check `SELECT_STORY` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-768: Stale documentation: STORY_PREPARED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** STORY_PREPARED

**Issue:** SKILL.md documents `STORY_PREPARED`, which the enumerated source API surface lacks

**Remediation:** Check `STORY_PREPARED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-769: Stale documentation: STORY_RENDERED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** STORY_RENDERED

**Issue:** SKILL.md documents `STORY_RENDERED`, which the enumerated source API surface lacks

**Remediation:** Check `STORY_RENDERED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-770: Stale documentation: STORY_SPECIFIED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** STORY_SPECIFIED

**Issue:** SKILL.md documents `STORY_SPECIFIED`, which the enumerated source API surface lacks

**Remediation:** Check `STORY_SPECIFIED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-771: Stale documentation: ScrollArea

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** ScrollArea

**Issue:** SKILL.md documents `ScrollArea`, which the enumerated source API surface lacks

**Remediation:** Check `ScrollArea` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-772: Stale documentation: Select

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** Select

**Issue:** SKILL.md documents `Select`, which the enumerated source API surface lacks

**Remediation:** Check `Select` against the source and update or remove its documentation at references/core-api.md:313: the enumerated source surface does not export it.

### GAP-773: Stale documentation: SelectControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:192
**Export:** SelectControl

**Issue:** SKILL.md documents `SelectControl`, which the enumerated source API surface lacks

**Remediation:** Check `SelectControl` against the source and update or remove its documentation at references/doc-blocks.md:192: the enumerated source surface does not export it.

### GAP-774: Stale documentation: Spaced

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** Spaced

**Issue:** SKILL.md documents `Spaced`, which the enumerated source API surface lacks

**Remediation:** Check `Spaced` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-775: Stale documentation: Span

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Span

**Issue:** SKILL.md documents `Span`, which the enumerated source API surface lacks

**Remediation:** Check `Span` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-778: Stale documentation: StoryIndexGenerator

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:340
**Export:** StoryIndexGenerator

**Issue:** SKILL.md documents `StoryIndexGenerator`, which the enumerated source API surface lacks

**Remediation:** Check `StoryIndexGenerator` against the source and update or remove its documentation at references/core-api.md:340: the enumerated source surface does not export it.

### GAP-781: Stale documentation: StorybookIcon

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:319
**Export:** StorybookIcon

**Issue:** SKILL.md documents `StorybookIcon`, which the enumerated source API surface lacks

**Remediation:** Check `StorybookIcon` against the source and update or remove its documentation at references/core-api.md:319: the enumerated source surface does not export it.

### GAP-782: Stale documentation: StorybookLogo

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:319
**Export:** StorybookLogo

**Issue:** SKILL.md documents `StorybookLogo`, which the enumerated source API surface lacks

**Remediation:** Check `StorybookLogo` against the source and update or remove its documentation at references/core-api.md:319: the enumerated source surface does not export it.

### GAP-784: Stale documentation: SyntaxHighlighter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** SyntaxHighlighter

**Issue:** SKILL.md documents `SyntaxHighlighter`, which the enumerated source API surface lacks

**Remediation:** Check `SyntaxHighlighter` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-785: Stale documentation: TabBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabBar

**Issue:** SKILL.md documents `TabBar`, which the enumerated source API surface lacks

**Remediation:** Check `TabBar` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-786: Stale documentation: TabButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabButton

**Issue:** SKILL.md documents `TabButton`, which the enumerated source API surface lacks

**Remediation:** Check `TabButton` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-787: Stale documentation: TabList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabList

**Issue:** SKILL.md documents `TabList`, which the enumerated source API surface lacks

**Remediation:** Check `TabList` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-788: Stale documentation: TabPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabPanel

**Issue:** SKILL.md documents `TabPanel`, which the enumerated source API surface lacks

**Remediation:** Check `TabPanel` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-789: Stale documentation: TabWrapper

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabWrapper

**Issue:** SKILL.md documents `TabWrapper`, which the enumerated source API surface lacks

**Remediation:** Check `TabWrapper` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-791: Stale documentation: Tabs

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** Tabs

**Issue:** SKILL.md documents `Tabs`, which the enumerated source API surface lacks

**Remediation:** Check `Tabs` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-792: Stale documentation: TabsView

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabsView

**Issue:** SKILL.md documents `TabsView`, which the enumerated source API surface lacks

**Remediation:** Check `TabsView` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-795: Stale documentation: ThemeProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/addons.md:112
**Export:** ThemeProvider

**Issue:** SKILL.md documents `ThemeProvider`, which the enumerated source API surface lacks

**Remediation:** Check `ThemeProvider` against the source and update or remove its documentation at references/addons.md:112: the enumerated source surface does not export it.

### GAP-797: Stale documentation: ToggleButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** ToggleButton

**Issue:** SKILL.md documents `ToggleButton`, which the enumerated source API surface lacks

**Remediation:** Check `ToggleButton` against the source and update or remove its documentation at references/core-api.md:313: the enumerated source surface does not export it.

### GAP-798: Stale documentation: Toolbar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** Toolbar

**Issue:** SKILL.md documents `Toolbar`, which the enumerated source API surface lacks

**Remediation:** Check `Toolbar` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-799: Stale documentation: Tooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** Tooltip

**Issue:** SKILL.md documents `Tooltip`, which the enumerated source API surface lacks

**Remediation:** Check `Tooltip` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-800: Stale documentation: TooltipLinkList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** TooltipLinkList

**Issue:** SKILL.md documents `TooltipLinkList`, which the enumerated source API surface lacks

**Remediation:** Check `TooltipLinkList` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-801: Stale documentation: TooltipNote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** TooltipNote

**Issue:** SKILL.md documents `TooltipNote`, which the enumerated source API surface lacks

**Remediation:** Check `TooltipNote` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-802: Stale documentation: UL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** UL

**Issue:** SKILL.md documents `UL`, which the enumerated source API surface lacks

**Remediation:** Check `UL` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-803: Stale documentation: UPDATE_STORY_ARGS

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** UPDATE_STORY_ARGS

**Issue:** SKILL.md documents `UPDATE_STORY_ARGS`, which the enumerated source API surface lacks

**Remediation:** Check `UPDATE_STORY_ARGS` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-804: Stale documentation: WebsocketTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:330
**Export:** WebsocketTransport

**Issue:** SKILL.md documents `WebsocketTransport`, which the enumerated source API surface lacks

**Remediation:** Check `WebsocketTransport` against the source and update or remove its documentation at references/core-api.md:330: the enumerated source surface does not export it.

### GAP-805: Stale documentation: WithTooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** WithTooltip

**Issue:** SKILL.md documents `WithTooltip`, which the enumerated source API surface lacks

**Remediation:** Check `WithTooltip` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-806: Stale documentation: Zoom

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** Zoom

**Issue:** SKILL.md documents `Zoom`, which the enumerated source API surface lacks

**Remediation:** Check `Zoom` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-808: Stale documentation: addToGlobalContext

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** addToGlobalContext

**Issue:** SKILL.md documents `addToGlobalContext`, which the enumerated source API surface lacks

**Remediation:** Check `addToGlobalContext` against the source and update or remove its documentation at references/core-api.md:336: the enumerated source surface does not export it.

### GAP-809: Stale documentation: automock

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:339
**Export:** automock

**Issue:** SKILL.md documents `automock`, which the enumerated source API surface lacks

**Remediation:** Check `automock` against the source and update or remove its documentation at references/core-api.md:339: the enumerated source surface does not export it.

### GAP-811: Stale documentation: colors

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** colors

**Issue:** SKILL.md documents `colors`, which the enumerated source API surface lacks

**Remediation:** Check `colors` against the source and update or remove its documentation at references/core-api.md:335: the enumerated source surface does not export it.

### GAP-812: Stale documentation: componentTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** componentTransform

**Issue:** SKILL.md documents `componentTransform`, which the enumerated source API surface lacks

**Remediation:** Check `componentTransform` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-813: Stale documentation: core

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:25
**Export:** core

**Issue:** SKILL.md documents `core`, which the enumerated source API surface lacks

**Remediation:** Check `core` against the source and update or remove its documentation at SKILL.md:25: the enumerated source surface does not export it.

### GAP-814: Stale documentation: createBrowserChannel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:330
**Export:** createBrowserChannel

**Issue:** SKILL.md documents `createBrowserChannel`, which the enumerated source API surface lacks

**Remediation:** Check `createBrowserChannel` against the source and update or remove its documentation at references/core-api.md:330: the enumerated source surface does not export it.

### GAP-816: Stale documentation: createTest

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/framework-config.md:143
**Export:** createTest

**Issue:** SKILL.md documents `createTest`, which the enumerated source API surface lacks

**Remediation:** Check `createTest` against the source and update or remove its documentation at references/framework-config.md:143: the enumerated source surface does not export it.

### GAP-820: Stale documentation: enrichCsf

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** enrichCsf

**Issue:** SKILL.md documents `enrichCsf`, which the enumerated source API surface lacks

**Remediation:** Check `enrichCsf` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-821: Stale documentation: expect

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:46
**Export:** expect

**Issue:** SKILL.md documents `expect`, which the enumerated source API surface lacks

**Remediation:** Check `expect` against the source and update or remove its documentation at SKILL.md:46: the enumerated source surface does not export it.

### GAP-824: Stale documentation: experimental_loadStorybook

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:340
**Export:** experimental_loadStorybook

**Issue:** SKILL.md documents `experimental_loadStorybook`, which the enumerated source API surface lacks

**Remediation:** Check `experimental_loadStorybook` against the source and update or remove its documentation at references/core-api.md:340: the enumerated source surface does not export it.

### GAP-825: Stale documentation: extract

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/addons.md:125
**Export:** extract

**Issue:** SKILL.md documents `extract`, which the enumerated source API surface lacks

**Remediation:** Check `extract` against the source and update or remove its documentation at references/addons.md:125: the enumerated source surface does not export it.

### GAP-826: Stale documentation: findByRole

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:108
**Export:** findByRole

**Issue:** SKILL.md documents `findByRole`, which the enumerated source API surface lacks

**Remediation:** Check `findByRole` against the source and update or remove its documentation at SKILL.md:108: the enumerated source surface does not export it.

### GAP-828: Stale documentation: generate

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:14
**Export:** generate

**Issue:** SKILL.md documents `generate`, which the enumerated source API surface lacks

**Remediation:** Check `generate` against the source and update or remove its documentation at SKILL.md:14: the enumerated source surface does not export it.

### GAP-829: Stale documentation: generateStoryFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:340
**Export:** generateStoryFile

**Issue:** SKILL.md documents `generateStoryFile`, which the enumerated source API surface lacks

**Remediation:** Check `generateStoryFile` against the source and update or remove its documentation at references/core-api.md:340: the enumerated source surface does not export it.

### GAP-830: Stale documentation: getByRole

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:65
**Export:** getByRole

**Issue:** SKILL.md documents `getByRole`, which the enumerated source API surface lacks

**Remediation:** Check `getByRole` against the source and update or remove its documentation at SKILL.md:65: the enumerated source surface does not export it.

### GAP-833: Stale documentation: getSessionId

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** getSessionId

**Issue:** SKILL.md documents `getSessionId`, which the enumerated source API surface lacks

**Remediation:** Check `getSessionId` against the source and update or remove its documentation at references/core-api.md:336: the enumerated source surface does not export it.

### GAP-835: Stale documentation: getStorySortParameter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** getStorySortParameter

**Issue:** SKILL.md documents `getStorySortParameter`, which the enumerated source API surface lacks

**Remediation:** Check `getStorySortParameter` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-836: Stale documentation: getStorybookMetadata

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** getStorybookMetadata

**Issue:** SKILL.md documents `getStorybookMetadata`, which the enumerated source API surface lacks

**Remediation:** Check `getStorybookMetadata` against the source and update or remove its documentation at references/core-api.md:336: the enumerated source surface does not export it.

### GAP-837: Stale documentation: isMockFunction

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:136
**Export:** isMockFunction

**Issue:** SKILL.md documents `isMockFunction`, which the enumerated source API surface lacks

**Remediation:** Check `isMockFunction` against the source and update or remove its documentation at references/core-api.md:136: the enumerated source surface does not export it.

### GAP-839: Stale documentation: jsx

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:170
**Export:** jsx

**Issue:** SKILL.md documents `jsx`, which the enumerated source API surface lacks

**Remediation:** Check `jsx` against the source and update or remove its documentation at references/core-api.md:170: the enumerated source surface does not export it.

### GAP-841: Stale documentation: logTracker

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** logTracker

**Issue:** SKILL.md documents `logTracker`, which the enumerated source API surface lacks

**Remediation:** Check `logTracker` against the source and update or remove its documentation at references/core-api.md:335: the enumerated source surface does not export it.

### GAP-843: Stale documentation: parser

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** parser

**Issue:** SKILL.md documents `parser`, which the enumerated source API surface lacks

**Remediation:** Check `parser` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-844: Stale documentation: prompt

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** prompt

**Issue:** SKILL.md documents `prompt`, which the enumerated source API surface lacks

**Remediation:** Check `prompt` against the source and update or remove its documentation at references/core-api.md:335: the enumerated source surface does not export it.

### GAP-845: Stale documentation: queryByRole

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:60
**Export:** queryByRole

**Issue:** SKILL.md documents `queryByRole`, which the enumerated source API surface lacks

**Remediation:** Check `queryByRole` against the source and update or remove its documentation at references/core-api.md:60: the enumerated source surface does not export it.

### GAP-846: Stale documentation: recast

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** recast

**Issue:** SKILL.md documents `recast`, which the enumerated source API surface lacks

**Remediation:** Check `recast` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-847: Stale documentation: redirect

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:339
**Export:** redirect

**Issue:** SKILL.md documents `redirect`, which the enumerated source API surface lacks

**Remediation:** Check `redirect` against the source and update or remove its documentation at references/core-api.md:339: the enumerated source surface does not export it.

### GAP-848: Stale documentation: resolve

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:339
**Export:** resolve

**Issue:** SKILL.md documents `resolve`, which the enumerated source API surface lacks

**Remediation:** Check `resolve` against the source and update or remove its documentation at references/core-api.md:339: the enumerated source surface does not export it.

### GAP-849: Stale documentation: runtime

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:14
**Export:** runtime

**Issue:** SKILL.md documents `runtime`, which the enumerated source API surface lacks

**Remediation:** Check `runtime` against the source and update or remove its documentation at references/core-api.md:14: the enumerated source surface does not export it.

### GAP-852: Stale documentation: telemetry

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** telemetry

**Issue:** SKILL.md documents `telemetry`, which the enumerated source API surface lacks

**Remediation:** Check `telemetry` against the source and update or remove its documentation at references/core-api.md:336: the enumerated source surface does not export it.

### GAP-853: Stale documentation: transformSync

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** transformSync

**Issue:** SKILL.md documents `transformSync`, which the enumerated source API surface lacks

**Remediation:** Check `transformSync` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-854: Stale documentation: traverse

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** traverse

**Issue:** SKILL.md documents `traverse`, which the enumerated source API surface lacks

**Remediation:** Check `traverse` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-855: Stale documentation: types

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:96
**Export:** types

**Issue:** SKILL.md documents `types`, which the enumerated source API surface lacks

**Remediation:** Check `types` against the source and update or remove its documentation at SKILL.md:96: the enumerated source surface does not export it.

### GAP-856: Stale documentation: useStatusStore

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:153
**Export:** useStatusStore

**Issue:** SKILL.md documents `useStatusStore`, which the enumerated source API surface lacks

**Remediation:** Check `useStatusStore` against the source and update or remove its documentation at references/core-api.md:153: the enumerated source surface does not export it.

### GAP-857: Stale documentation: useTabsState

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** useTabsState

**Issue:** SKILL.md documents `useTabsState`, which the enumerated source API surface lacks

**Remediation:** Check `useTabsState` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-858: Stale documentation: useTestProviderStore

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:154
**Export:** useTestProviderStore

**Issue:** SKILL.md documents `useTestProviderStore`, which the enumerated source API surface lacks

**Remediation:** Check `useTestProviderStore` against the source and update or remove its documentation at references/core-api.md:154: the enumerated source surface does not export it.

### GAP-859: Stale documentation: useTheme

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:20
**Export:** useTheme

**Issue:** SKILL.md documents `useTheme`, which the enumerated source API surface lacks

**Remediation:** Check `useTheme` against the source and update or remove its documentation at references/core-api.md:20: the enumerated source surface does not export it.

### GAP-860: Stale documentation: useUniversalStore

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:151
**Export:** useUniversalStore

**Issue:** SKILL.md documents `useUniversalStore`, which the enumerated source API surface lacks

**Remediation:** Check `useUniversalStore` against the source and update or remove its documentation at references/core-api.md:151: the enumerated source surface does not export it.

### GAP-862: Stale documentation: vitestTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** vitestTransform

**Issue:** SKILL.md documents `vitestTransform`, which the enumerated source API surface lacks

**Remediation:** Check `vitestTransform` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-864: Stale documentation: withTheme

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:169
**Export:** withTheme

**Issue:** SKILL.md documents `withTheme`, which the enumerated source API surface lacks

**Remediation:** Check `withTheme` against the source and update or remove its documentation at references/core-api.md:169: the enumerated source surface does not export it.

### GAP-866: denominator deflation: effective_denominator below source public surface without tier_a_include

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** the re-derived surface counts 985 exports, 356.02% above `stats.effective_denominator` (216), and the brief has no `scope.tier_a_include`

**Remediation:** Set `stats.effective_denominator` in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json` to the public surface the source re-derives, or add `scope.tier_a_include` to the brief to name the authored tier the smaller count measures.

### GAP-867: denominator inflation: coarse scope.include union exceeds authored surface

**Severity:** Medium
**Category:** Coverage (denominator-inflation)
**Source:** forge-data/oms-storybook-react-vite/skill-brief.yaml

**Issue:** the `scope.include` union counts 985 exports, 343.69% above the 222 provenance entries, and the brief has no `scope.tier_a_include`

**Remediation:** Set `stats.effective_denominator` in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json` to the authored surface: the root barrel is an umbrella of re-exports, so a `scope.tier_a_include` glob would still count them.

### GAP-868: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_public_api=216, exports[].length=82 → 62% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json`; update-skill applies it as a metadata update.

### GAP-869: metadata drift — documented-surface export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_documented=216, provenance named-exports=222, confidence_distribution sum=572 → 62% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json`; update-skill applies it as a metadata update.

### GAP-871: Provenance line is not the definition of A11yGlobals

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/a11y/src/index.ts:1
**Export:** A11yGlobals

**Issue:** the provenance map records `A11yGlobals` at `code/addons/a11y/src/index.ts:1`, which is not the line that defines it; the lines that define it are 8.

**Remediation:** Set the provenance `source_line` of `A11yGlobals` in `code/addons/a11y/src/index.ts` to its definition line (8) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-873: Provenance line is not the definition of A11yReport

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/a11y/src/index.ts:1
**Export:** A11yReport

**Issue:** the provenance map records `A11yReport` at `code/addons/a11y/src/index.ts:1`, which is not the line that defines it; the lines that define it are 8.

**Remediation:** Set the provenance `source_line` of `A11yReport` in `code/addons/a11y/src/index.ts` to its definition line (8) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-875: Provenance line is not the definition of ADDON_ID

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/vitest/src/constants.ts:1
**Export:** ADDON_ID

**Issue:** the provenance map records `ADDON_ID` at `code/addons/vitest/src/constants.ts:1`, which is not the line that defines it; the lines that define it are 11.

**Remediation:** Set the provenance `source_line` of `ADDON_ID` in `code/addons/vitest/src/constants.ts` to its definition line (11) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-881: Provenance line is not the definition of Decorator

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/public-types.ts:55
**Export:** Decorator

**Issue:** the provenance map records `Decorator` at `code/renderers/react/src/public-types.ts:55`, which is not the line that defines it; the lines that define it are 77.

**Remediation:** Set the provenance `source_line` of `Decorator` in `code/renderers/react/src/public-types.ts` to its definition line (77) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-886: Provenance line is not the definition of DocsRenderer

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/docs/src/index.ts:1
**Export:** DocsRenderer

**Issue:** the provenance map records `DocsRenderer` at `code/addons/docs/src/index.ts:1`, which is not the line that defines it; the lines that define it are 8.

**Remediation:** Set the provenance `source_line` of `DocsRenderer` in `code/addons/docs/src/index.ts` to its definition line (8) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-887: Provenance line is not the definition of FrameworkOptions

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/frameworks/react-vite/src/types.ts:1
**Export:** FrameworkOptions

**Issue:** the provenance map records `FrameworkOptions` at `code/frameworks/react-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 14.

**Remediation:** Set the provenance `source_line` of `FrameworkOptions` in `code/frameworks/react-vite/src/types.ts` to its definition line (14) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-893: Provenance line is not the definition of Loader

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/public-types.ts:60
**Export:** Loader

**Issue:** the provenance map records `Loader` at `code/renderers/react/src/public-types.ts:60`, which is not the line that defines it; the lines that define it are 78.

**Remediation:** Set the provenance `source_line` of `Loader` in `code/renderers/react/src/public-types.ts` to its definition line (78) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-895: Provenance line is not the definition of PARAM_KEY

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/a11y/src/index.ts:1
**Export:** PARAM_KEY

**Issue:** the provenance map records `PARAM_KEY` at `code/addons/a11y/src/index.ts:1`, which is not the line that defines it; the lines that define it are 6.

**Remediation:** Set the provenance `source_line` of `PARAM_KEY` in `code/addons/a11y/src/index.ts` to its definition line (6) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-897: Provenance line is not the definition of ReactMeta

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/preview.tsx:1
**Export:** ReactMeta

**Issue:** the provenance map records `ReactMeta` at `code/renderers/react/src/preview.tsx:1`, which is not the line that defines it; the lines that define it are 147.

**Remediation:** Set the provenance `source_line` of `ReactMeta` in `code/renderers/react/src/preview.tsx` to its definition line (147) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-898: Provenance line is not the definition of ReactPreview

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/preview.tsx:1
**Export:** ReactPreview

**Issue:** the provenance map records `ReactPreview` at `code/renderers/react/src/preview.tsx:1`, which is not the line that defines it; the lines that define it are 102.

**Remediation:** Set the provenance `source_line` of `ReactPreview` in `code/renderers/react/src/preview.tsx` to its definition line (102) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-899: Provenance line is not the definition of ReactRenderer

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/types.ts:1
**Export:** ReactRenderer

**Issue:** the provenance map records `ReactRenderer` at `code/renderers/react/src/types.ts:1`, which is not the line that defines it; the lines that define it are 8.

**Remediation:** Set the provenance `source_line` of `ReactRenderer` in `code/renderers/react/src/types.ts` to its definition line (8) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-900: Provenance line is not the definition of ReactStory

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/preview.tsx:1
**Export:** ReactStory

**Issue:** the provenance map records `ReactStory` at `code/renderers/react/src/preview.tsx:1`, which is not the line that defines it; the lines that define it are 249.

**Remediation:** Set the provenance `source_line` of `ReactStory` in `code/renderers/react/src/preview.tsx` to its definition line (249) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-905: Provenance line is not the definition of StoryContext

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/public-types.ts:65
**Export:** StoryContext

**Issue:** the provenance map records `StoryContext` at `code/renderers/react/src/public-types.ts:65`, which is not the line that defines it; the lines that define it are 79.

**Remediation:** Set the provenance `source_line` of `StoryContext` in `code/renderers/react/src/public-types.ts` to its definition line (79) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-907: Provenance line is not the definition of StoryFn

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/public-types.ts:35
**Export:** StoryFn

**Issue:** the provenance map records `StoryFn` at `code/renderers/react/src/public-types.ts:35`, which is not the line that defines it; the lines that define it are 38.

**Remediation:** Set the provenance `source_line` of `StoryFn` in `code/renderers/react/src/public-types.ts` to its definition line (38) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-908: Provenance line is not the definition of StorybookConfig

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/frameworks/react-vite/src/types.ts:1
**Export:** StorybookConfig

**Issue:** the provenance map records `StorybookConfig` at `code/frameworks/react-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 66.

**Remediation:** Set the provenance `source_line` of `StorybookConfig` in `code/frameworks/react-vite/src/types.ts` to its definition line (66) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-909: Provenance line is not the definition of StorybookConfigVite

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/types.ts:1
**Export:** StorybookConfigVite

**Issue:** the provenance map records `StorybookConfigVite` at `code/builders/builder-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 17.

**Remediation:** Set the provenance `source_line` of `StorybookConfigVite` in `code/builders/builder-vite/src/types.ts` to its definition line (17) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-911: Provenance line is not the definition of TEST_PROVIDER_ID

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/vitest/src/constants.ts:1
**Export:** TEST_PROVIDER_ID

**Issue:** the provenance map records `TEST_PROVIDER_ID` at `code/addons/vitest/src/constants.ts:1`, which is not the line that defines it; the lines that define it are 12.

**Remediation:** Set the provenance `source_line` of `TEST_PROVIDER_ID` in `code/addons/vitest/src/constants.ts` to its definition line (12) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-912: Provenance line is not the definition of ThemeProvider

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/theming/index.ts:10
**Export:** ThemeProvider

**Issue:** the provenance map records `ThemeProvider` at `code/core/src/theming/index.ts:10`, which is not the line that defines it; the lines that define it are 17.

**Remediation:** Set the provenance `source_line` of `ThemeProvider` in `code/core/src/theming/index.ts` to its definition line (17) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-913: Provenance line is not the definition of ThemesGlobals

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/themes/src/index.ts:1
**Export:** ThemesGlobals

**Issue:** the provenance map records `ThemesGlobals` at `code/addons/themes/src/index.ts:1`, which is not the line that defines it; the lines that define it are 6.

**Remediation:** Set the provenance `source_line` of `ThemesGlobals` in `code/addons/themes/src/index.ts` to its definition line (6) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-918: Provenance line is not the definition of ViteBuilder

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/types.ts:1
**Export:** ViteBuilder

**Issue:** the provenance map records `ViteBuilder` at `code/builders/builder-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 10.

**Remediation:** Set the provenance `source_line` of `ViteBuilder` in `code/builders/builder-vite/src/types.ts` to its definition line (10) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-919: Provenance line is not the definition of ViteFinal

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/types.ts:1
**Export:** ViteFinal

**Issue:** the provenance map records `ViteFinal` at `code/builders/builder-vite/src/types.ts:1`, which is not the line that defines it; the lines that define it are 12.

**Remediation:** Set the provenance `source_line` of `ViteFinal` in `code/builders/builder-vite/src/types.ts` to its definition line (12) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-920: Provenance line is not the definition of __definePreview

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/renderers/react/src/preview.tsx:1
**Export:** __definePreview

**Issue:** the provenance map records `__definePreview` at `code/renderers/react/src/preview.tsx:1`, which is not the line that defines it; the lines that define it are 55.

**Remediation:** Set the provenance `source_line` of `__definePreview` in `code/renderers/react/src/preview.tsx` to its definition line (55) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-924: Provenance line is not the definition of action

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/actions/runtime/action.ts:1
**Export:** action

**Issue:** the provenance map records `action` at `code/core/src/actions/runtime/action.ts:1`, which is not the line that defines it; the lines that define it are 50.

**Remediation:** Set the provenance `source_line` of `action` in `code/core/src/actions/runtime/action.ts` to its definition line (50) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-925: Provenance line is not the definition of bail

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** bail

**Issue:** the provenance map records `bail` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 37.

**Remediation:** Set the provenance `source_line` of `bail` in `code/builders/builder-vite/src/index.ts` to its definition line (37) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-926: Provenance line is not the definition of build

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** build

**Issue:** the provenance map records `build` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 63.

**Remediation:** Set the provenance `source_line` of `build` in `code/builders/builder-vite/src/index.ts` to its definition line (63) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-927: Provenance line is not the definition of configureActions

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/actions/runtime/configureActions.ts:1
**Export:** configureActions

**Issue:** the provenance map records `configureActions` at `code/core/src/actions/runtime/configureActions.ts:1`, which is not the line that defines it; the lines that define it are 9.

**Remediation:** Set the provenance `source_line` of `configureActions` in `code/core/src/actions/runtime/configureActions.ts` to its definition line (9) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-928: Provenance line is not the definition of css

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/theming/index.ts:10
**Export:** css

**Issue:** the provenance map records `css` at `code/core/src/theming/index.ts:10`, which is not the line that defines it; the lines that define it are 13.

**Remediation:** Set the provenance `source_line` of `css` in `code/core/src/theming/index.ts` to its definition line (13) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-931: Provenance line is not the definition of hasVitePlugins

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** hasVitePlugins

**Issue:** the provenance map records `hasVitePlugins` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 15.

**Remediation:** Set the provenance `source_line` of `hasVitePlugins` in `code/builders/builder-vite/src/index.ts` to its definition line (15) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-932: Provenance line is not the definition of keyframes

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/theming/index.ts:10
**Export:** keyframes

**Issue:** the provenance map records `keyframes` at `code/core/src/theming/index.ts:10`, which is not the line that defines it; the lines that define it are 16.

**Remediation:** Set the provenance `source_line` of `keyframes` in `code/core/src/theming/index.ts` to its definition line (16) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-935: Provenance line is not the definition of spyOn

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/test/spy.ts:1
**Export:** spyOn

**Issue:** the provenance map records `spyOn` at `code/core/src/test/spy.ts:1`, which is not the line that defines it; the lines that define it are 41.

**Remediation:** Set the provenance `source_line` of `spyOn` in `code/core/src/test/spy.ts` to its definition line (41) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-936: Provenance line is not the definition of start

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** start

**Issue:** the provenance map records `start` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 41.

**Remediation:** Set the provenance `source_line` of `start` in `code/builders/builder-vite/src/index.ts` to its definition line (41) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-937: Provenance line is not the definition of storeOptions

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/addons/vitest/src/constants.ts:1
**Export:** storeOptions

**Issue:** the provenance map records `storeOptions` at `code/addons/vitest/src/constants.ts:1`, which is not the line that defines it; the lines that define it are 21.

**Remediation:** Set the provenance `source_line` of `storeOptions` in `code/addons/vitest/src/constants.ts` to its definition line (21) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-939: Provenance line is not the definition of useTheme

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/core/src/theming/index.ts:10
**Export:** useTheme

**Issue:** the provenance map records `useTheme` at `code/core/src/theming/index.ts:10`, which is not the line that defines it; the lines that define it are 18.

**Remediation:** Set the provenance `source_line` of `useTheme` in `code/core/src/theming/index.ts` to its definition line (18) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-949: Provenance line is not the definition of withoutVitePlugins

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** code/builders/builder-vite/src/index.ts:1
**Export:** withoutVitePlugins

**Issue:** the provenance map records `withoutVitePlugins` at `code/builders/builder-vite/src/index.ts:1`, which is not the line that defines it; the lines that define it are 14.

**Remediation:** Set the provenance `source_line` of `withoutVitePlugins` in `code/builders/builder-vite/src/index.ts` to its definition line (14) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-710: Documented extra: BabelFile

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf-tools/CsfFile.ts:31
**Export:** BabelFile

**Issue:** `references/core-api.md:342` documents `BabelFile`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BabelFile` is a documented extra, a name the source still declares at `code/core/src/csf-tools/CsfFile.ts:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-713: Documented extra: BaseProjectAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/csf.ts:38
**Export:** BaseProjectAnnotations

**Issue:** `references/core-api.md:262` documents `BaseProjectAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BaseProjectAnnotations` is a documented extra, a name the source still declares at `code/core/src/types/modules/csf.ts:38` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-730: Documented extra: Decorator

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/public-types.ts:77
**Export:** Decorator

**Issue:** `SKILL.md:151` documents `Decorator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Decorator` is a documented extra, a name the source still declares at `code/renderers/react/src/public-types.ts:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-731: Documented extra: DecoratorHelpers

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/decorators/index.ts:5
**Export:** DecoratorHelpers

**Issue:** `references/addons.md:121` documents `DecoratorHelpers`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DecoratorHelpers` is a documented extra, a name the source still declares at `code/addons/themes/src/decorators/index.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-737: Documented extra: FrameworkOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/react-vite/src/types.ts:14
**Export:** FrameworkOptions

**Issue:** `references/core-api.md:12` documents `FrameworkOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FrameworkOptions` is a documented extra, a name the source still declares at `code/frameworks/react-vite/src/types.ts:14` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-750: Documented extra: Loader

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/public-types.ts:78
**Export:** Loader

**Issue:** `SKILL.md:151` documents `Loader`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Loader` is a documented extra, a name the source still declares at `code/renderers/react/src/public-types.ts:78` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-765: Documented extra: Refs

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:314
**Export:** Refs

**Issue:** `references/story-types.md:247` documents `Refs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Refs` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:314` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-776: Documented extra: StoriesHash

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:304
**Export:** StoriesHash

**Issue:** `references/story-types.md:250` documents `StoriesHash`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoriesHash` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:304` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-779: Documented extra: StoryObj

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/public-types.ts:47
**Export:** StoryObj

**Issue:** `SKILL.md:45` documents `StoryObj`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryObj` is a documented extra, a name the source still declares at `code/renderers/react/src/public-types.ts:47` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-780: Documented extra: StorybookConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/react-vite/src/types.ts:66
**Export:** StorybookConfig

**Issue:** `SKILL.md:188` documents `StorybookConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StorybookConfig` is a documented extra, a name the source still declares at `code/frameworks/react-vite/src/types.ts:66` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-783: Documented extra: StyledComponent

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/angular/template/stories/basics/component-with-style/styled.component.ts:9
**Export:** StyledComponent

**Issue:** `references/core-api.md:178` documents `StyledComponent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StyledComponent` is a documented extra, a name the source still declares at `code/frameworks/angular/template/stories/basics/component-with-style/styled.component.ts:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-790: Documented extra: Table

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/components/components/typography/elements/Table.tsx:6
**Export:** Table

**Issue:** `references/core-api.md:312` documents `Table`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Table` is a documented extra, a name the source still declares at `code/core/src/components/components/typography/elements/Table.tsx:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-793: Documented extra: Theme

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:10
**Export:** Theme

**Issue:** `references/addons.md:98` documents `Theme`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Theme` is a documented extra, a name the source still declares at `code/addons/themes/src/decorators/provider.decorator.tsx:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-794: Documented extra: ThemeAddonState

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:1
**Export:** ThemeAddonState

**Issue:** `references/addons.md:114` documents `ThemeAddonState`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemeAddonState` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-796: Documented extra: ThemesParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:6
**Export:** ThemesParameters

**Issue:** `references/addons.md:115` documents `ThemesParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemesParameters` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-807: Documented extra: __definePreview

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/preview.tsx:55
**Export:** __definePreview

**Issue:** `references/core-api.md:18` documents `__definePreview`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__definePreview` is a documented extra, a name the source still declares at `code/renderers/react/src/preview.tsx:55` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-810: Documented extra: babelParse

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/babel/babelParse.ts:28
**Export:** babelParse

**Issue:** `references/core-api.md:337` documents `babelParse`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `babelParse` is a documented extra, a name the source still declares at `code/core/src/babel/babelParse.ts:28` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-815: Documented extra: createCache

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/theming/index.ts:33
**Export:** createCache

**Issue:** `references/core-api.md:172` documents `createCache`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `createCache` is a documented extra, a name the source still declares at `code/core/src/theming/index.ts:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-817: Documented extra: css

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/pseudo-states/src/stories/CustomElement.tsx:1
**Export:** css

**Issue:** `references/core-api.md:20` documents `css`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `css` is a documented extra, a name the source still declares at `code/addons/pseudo-states/src/stories/CustomElement.tsx:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-818: Documented extra: defineMain

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/react-vite/src/node/index.ts:3
**Export:** defineMain

**Issue:** `references/core-api.md:13` documents `defineMain`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `defineMain` is a documented extra, a name the source still declares at `code/frameworks/react-vite/src/node/index.ts:3` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-822: Documented extra: experimental_getStatusStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/index.ts:8
**Export:** experimental_getStatusStore

**Issue:** `references/core-api.md:153` documents `experimental_getStatusStore`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/manager-api/index.ts`

**Remediation:** No change: `experimental_getStatusStore` is a documented extra, a name the source still declares at `code/core/src/manager-api/index.ts:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-823: Documented extra: experimental_getTestProviderStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/index.ts:15
**Export:** experimental_getTestProviderStore

**Issue:** `references/core-api.md:154` documents `experimental_getTestProviderStore`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/manager-api/index.ts`

**Remediation:** No change: `experimental_getTestProviderStore` is a documented extra, a name the source still declares at `code/core/src/manager-api/index.ts:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-831: Documented extra: getPreviewBodyTemplate

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/template.ts:10
**Export:** getPreviewBodyTemplate

**Issue:** `references/core-api.md:340` documents `getPreviewBodyTemplate`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getPreviewBodyTemplate` is a documented extra, a name the source still declares at `code/core/src/common/utils/template.ts:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-832: Documented extra: getPreviewHeadTemplate

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/template.ts:29
**Export:** getPreviewHeadTemplate

**Issue:** `references/core-api.md:340` documents `getPreviewHeadTemplate`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getPreviewHeadTemplate` is a documented extra, a name the source still declares at `code/core/src/common/utils/template.ts:29` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-834: Documented extra: getStoryHref

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/components/components/utils/getStoryHref.ts:15
**Export:** getStoryHref

**Issue:** `references/core-api.md:318` documents `getStoryHref`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getStoryHref` is a documented extra, a name the source still declares at `code/core/src/components/components/utils/getStoryHref.ts:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-838: Documented extra: isPropValid

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/theming/index.ts:34
**Export:** isPropValid

**Issue:** `references/core-api.md:173` documents `isPropValid`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `isPropValid` is a documented extra, a name the source still declares at `code/core/src/theming/index.ts:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-840: Documented extra: keyframes

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager/components/TourGuide/HighlightElement.tsx:5
**Export:** keyframes

**Issue:** `references/core-api.md:165` documents `keyframes`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `keyframes` is a documented extra, a name the source still declares at `code/core/src/manager/components/TourGuide/HighlightElement.tsx:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-842: Documented extra: mocks

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/component-testing/mocks/index.ts:1
**Export:** mocks

**Issue:** `references/core-api.md:131` documents `mocks`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mocks` is a documented extra, a name the source still declares at `code/core/src/component-testing/mocks/index.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-851: Documented extra: styled

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/theming/index.ts:6
**Export:** styled

**Issue:** `references/addons.md:112` documents `styled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `styled` is a documented extra, a name the source still declares at `code/core/src/theming/index.ts:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-870: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=216, documented=572

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-872: Provenance line not verified for A11yGlobals_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:16
**Export:** A11yGlobals_exact

**Issue:** the line-check rules found no definition line for `A11yGlobals_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 16 defines `A11yGlobals_exact`; if another line does, set the provenance `source_line` to it.

### GAP-874: Provenance line not verified for A11yReport_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:5
**Export:** A11yReport_exact

**Issue:** the line-check rules found no definition line for `A11yReport_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 5 defines `A11yReport_exact`; if another line does, set the provenance `source_line` to it.

### GAP-876: Provenance line not verified for ArgTypes

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ArgTypes

**Issue:** the line-check rules found no definition line for `ArgTypes` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ArgTypes`; if another line does, set the provenance `source_line` to it.

### GAP-877: Provenance line not verified for Canvas

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Canvas

**Issue:** the line-check rules found no definition line for `Canvas` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Canvas`; if another line does, set the provenance `source_line` to it.

### GAP-878: Provenance line not verified for ColorPalette

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ColorPalette

**Issue:** the line-check rules found no definition line for `ColorPalette` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ColorPalette`; if another line does, set the provenance `source_line` to it.

### GAP-879: Provenance line not verified for ComponentEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** ComponentEntry

**Issue:** the line-check rules found no definition line for `ComponentEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 27 defines `ComponentEntry`; if another line does, set the provenance `source_line` to it.

### GAP-880: Provenance line not verified for Controls

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Controls

**Issue:** the line-check rules found no definition line for `Controls` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Controls`; if another line does, set the provenance `source_line` to it.

### GAP-882: Provenance line not verified for Description

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Description

**Issue:** the line-check rules found no definition line for `Description` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Description`; if another line does, set the provenance `source_line` to it.

### GAP-883: Provenance line not verified for DocsContainer

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContainer

**Issue:** the line-check rules found no definition line for `DocsContainer` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContainer`; if another line does, set the provenance `source_line` to it.

### GAP-884: Provenance line not verified for DocsContext

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContext

**Issue:** the line-check rules found no definition line for `DocsContext` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContext`; if another line does, set the provenance `source_line` to it.

### GAP-885: Provenance line not verified for DocsEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** DocsEntry

**Issue:** the line-check rules found no definition line for `DocsEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 34 defines `DocsEntry`; if another line does, set the provenance `source_line` to it.

### GAP-888: Provenance line not verified for GroupEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** GroupEntry

**Issue:** the line-check rules found no definition line for `GroupEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 21 defines `GroupEntry`; if another line does, set the provenance `source_line` to it.

### GAP-889: Provenance line not verified for HashEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** HashEntry

**Issue:** the line-check rules found no definition line for `HashEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 67 defines `HashEntry`; if another line does, set the provenance `source_line` to it.

### GAP-890: Provenance line not verified for IconGallery

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** IconGallery

**Issue:** the line-check rules found no definition line for `IconGallery` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `IconGallery`; if another line does, set the provenance `source_line` to it.

### GAP-891: Provenance line not verified for IndexHash

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** IndexHash

**Issue:** the line-check rules found no definition line for `IndexHash` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 80 defines `IndexHash`; if another line does, set the provenance `source_line` to it.

### GAP-892: Provenance line not verified for LeafEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** LeafEntry

**Issue:** the line-check rules found no definition line for `LeafEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 66 defines `LeafEntry`; if another line does, set the provenance `source_line` to it.

### GAP-894: Provenance line not verified for Markdown

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Markdown

**Issue:** the line-check rules found no definition line for `Markdown` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Markdown`; if another line does, set the provenance `source_line` to it.

### GAP-896: Provenance line not verified for Primary

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Primary

**Issue:** the line-check rules found no definition line for `Primary` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Primary`; if another line does, set the provenance `source_line` to it.

### GAP-901: Provenance line not verified for RootEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** RootEntry

**Issue:** the line-check rules found no definition line for `RootEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 15 defines `RootEntry`; if another line does, set the provenance `source_line` to it.

### GAP-902: Provenance line not verified for Source

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Source

**Issue:** the line-check rules found no definition line for `Source` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Source`; if another line does, set the provenance `source_line` to it.

### GAP-903: Provenance line not verified for Stories

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Stories

**Issue:** the line-check rules found no definition line for `Stories` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Stories`; if another line does, set the provenance `source_line` to it.

### GAP-904: Provenance line not verified for Story

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Story

**Issue:** the line-check rules found no definition line for `Story` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Story`; if another line does, set the provenance `source_line` to it.

### GAP-906: Provenance line not verified for StoryEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** StoryEntry

**Issue:** the line-check rules found no definition line for `StoryEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 45 defines `StoryEntry`; if another line does, set the provenance `source_line` to it.

### GAP-910: Provenance line not verified for Subtitle

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Subtitle

**Issue:** the line-check rules found no definition line for `Subtitle` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Subtitle`; if another line does, set the provenance `source_line` to it.

### GAP-914: Provenance line not verified for ThemesGlobals_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/types.ts:20
**Export:** ThemesGlobals_def

**Issue:** the line-check rules found no definition line for `ThemesGlobals_def` in `code/addons/themes/src/types.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/types.ts` and confirm that line 20 defines `ThemesGlobals_def`; if another line does, set the provenance `source_line` to it.

### GAP-915: Provenance line not verified for Title

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Title

**Issue:** the line-check rules found no definition line for `Title` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Title`; if another line does, set the provenance `source_line` to it.

### GAP-916: Provenance line not verified for Typeset

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Typeset

**Issue:** the line-check rules found no definition line for `Typeset` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Typeset`; if another line does, set the provenance `source_line` to it.

### GAP-917: Provenance line not verified for Unstyled

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Unstyled

**Issue:** the line-check rules found no definition line for `Unstyled` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Unstyled`; if another line does, set the provenance `source_line` to it.

### GAP-921: Provenance line not verified for a11y_decorators

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:12
**Export:** a11y_decorators

**Issue:** the line-check rules found no definition line for `a11y_decorators` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 12 defines `a11y_decorators`; if another line does, set the provenance `source_line` to it.

### GAP-922: Provenance line not verified for a11y_initialGlobals

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:98
**Export:** a11y_initialGlobals

**Issue:** the line-check rules found no definition line for `a11y_initialGlobals` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 98 defines `a11y_initialGlobals`; if another line does, set the provenance `source_line` to it.

### GAP-923: Provenance line not verified for a11y_parameters

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:105
**Export:** a11y_parameters

**Issue:** the line-check rules found no definition line for `a11y_parameters` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 105 defines `a11y_parameters`; if another line does, set the provenance `source_line` to it.

### GAP-929: Provenance line not verified for definePreview

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/preview-api/index.ts:1
**Export:** definePreview

**Issue:** the line-check rules found no definition line for `definePreview` in `code/core/src/preview-api/index.ts`; check by hand

**Remediation:** Open `code/core/src/preview-api/index.ts` and confirm that line 1 defines `definePreview`; if another line does, set the provenance `source_line` to it.

### GAP-930: Provenance line not verified for fireEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:43
**Export:** fireEvent

**Issue:** the line-check rules found no definition line for `fireEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 43 defines `fireEvent`; if another line does, set the provenance `source_line` to it.

### GAP-933: Provenance line not verified for mockChannel_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:3
**Export:** mockChannel_def

**Issue:** the line-check rules found no definition line for `mockChannel_def` in `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts`; check by hand

**Remediation:** Open `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts` and confirm that line 3 defines `mockChannel_def`; if another line does, set the provenance `source_line` to it.

### GAP-934: Provenance line not verified for screen

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:107
**Export:** screen

**Issue:** the line-check rules found no definition line for `screen` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 107 defines `screen`; if another line does, set the provenance `source_line` to it.

### GAP-938: Provenance line not verified for useOf

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** useOf

**Issue:** the line-check rules found no definition line for `useOf` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `useOf`; if another line does, set the provenance `source_line` to it.

### GAP-940: Provenance line not verified for userEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:123
**Export:** userEvent

**Issue:** the line-check rules found no definition line for `userEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 123 defines `userEvent`; if another line does, set the provenance `source_line` to it.

### GAP-941: Provenance line not verified for waitFor

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:108
**Export:** waitFor

**Issue:** the line-check rules found no definition line for `waitFor` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 108 defines `waitFor`; if another line does, set the provenance `source_line` to it.

### GAP-942: Provenance line not verified for withThemeByClassName

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByClassName

**Issue:** the line-check rules found no definition line for `withThemeByClassName` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByClassName`; if another line does, set the provenance `source_line` to it.

### GAP-943: Provenance line not verified for withThemeByClassName_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/class-name.decorator.tsx:19
**Export:** withThemeByClassName_exact

**Issue:** the line-check rules found no definition line for `withThemeByClassName_exact` in `code/addons/themes/src/decorators/class-name.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/class-name.decorator.tsx` and confirm that line 19 defines `withThemeByClassName_exact`; if another line does, set the provenance `source_line` to it.

### GAP-944: Provenance line not verified for withThemeByDataAttribute

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByDataAttribute

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByDataAttribute`; if another line does, set the provenance `source_line` to it.

### GAP-945: Provenance line not verified for withThemeByDataAttribute_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/data-attribute.decorator.tsx:19
**Export:** withThemeByDataAttribute_exact

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute_exact` in `code/addons/themes/src/decorators/data-attribute.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/data-attribute.decorator.tsx` and confirm that line 19 defines `withThemeByDataAttribute_exact`; if another line does, set the provenance `source_line` to it.

### GAP-946: Provenance line not verified for withThemeFromJSXProvider

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeFromJSXProvider

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeFromJSXProvider`; if another line does, set the provenance `source_line` to it.

### GAP-947: Provenance line not verified for withThemeFromJSXProvider_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:23
**Export:** withThemeFromJSXProvider_exact

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider_exact` in `code/addons/themes/src/decorators/provider.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/provider.decorator.tsx` and confirm that line 23 defines `withThemeFromJSXProvider_exact`; if another line does, set the provenance `source_line` to it.

### GAP-948: Provenance line not verified for within

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:110
**Export:** within

**Issue:** the line-check rules found no definition line for `within` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 110 defines `within`; if another line does, set the provenance `source_line` to it.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
