---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261103T065503Z-bad58550'
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
testDate: '2026-11-03T06:55:03Z'
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

**Mode Rationale:** metadata.json declares `skill_type: 'single'`, an individual skill, so the test runs in naive mode (API-surface coverage; coherence is structural only and is not a scored category).

**Analysis Plan:**
- Coverage Check: Deep tier, full source access to the pinned workspace clone (e486d38): enumerate the public export surface the brief scopes (stratified `tier_a_include` set), match each name against SKILL.md and references/, and check signatures and type coverage against the source with AST-backed reads.
- Coherence Check: structural checks only (reference files resolve, no broken internal links, SKILL.md sections well formed, metadata coherence); no cross-skill integration checks in naive mode.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces
**Denominator:** Stratified scope, denominator: tier_a_include union (118 files matched, 280 exports union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: absent
- `scope.tier_a_include` union: 280    ← chosen (barrel branch, `surfaceSet: tier_a_include`, ladder step 2)
- `scope.include` union: 985
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
| `ADDON_ID` | const | yes | - | code/addons/vitest/src/constants.ts:11 | WARN |
| `API_EventMap` | interface | yes | - | code/core/src/manager-api/root.tsx:318 | WARN |
| `API_KeyCollection` | type | yes | - | code/core/src/manager-api/modules/shortcuts.ts:99 | WARN |
| `ActionBar` | - | yes | - | - | WARN |
| `ActionDisplay` | interface | yes | - | code/core/src/actions/models/ActionDisplay.ts:3 | PASS |
| `ActionList` | - | yes | - | - | WARN |
| `ActionOptions` | type | yes | - | code/core/src/actions/models/ActionOptions.ts:11 | PASS |
| `ActionsFunction` | interface | yes | - | code/core/src/actions/models/ActionsFunction.ts:4 | PASS |
| `ActionsMap` | type | yes | - | code/core/src/actions/models/ActionsMap.ts:3 | PASS |
| `AddContext` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:27 | WARN |
| `AddonPanel` | - | yes | - | code/core/src/components/components/addon-panel/addon-panel.tsx:36 | WARN |
| `Anchor` | function | yes | yes | code/addons/docs/src/blocks/blocks/Anchor.tsx:10 | PASS |
| `AnchorMdx` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:98 | WARN |
| `AnchorProps` | interface | no | - | code/addons/docs/src/blocks/blocks/Anchor.tsx:6 | WARN |
| `Animation` | type | yes | - | code/core/src/theming/types.ts:60 | PASS |
| `ArgTypes` | const | yes | yes | code/addons/docs/src/blocks/blocks/ArgTypes.tsx:108 | PASS |
| `Args` | interface | yes | - | code/core/src/csf/story.ts:153 | WARN |
| `BabelFile` | - | yes | - | - | WARN |
| `Background` | type | yes | - | code/core/src/theming/types.ts:58 | PASS |
| `Badge` | - | yes | - | code/core/src/components/components/Badge/Badge.tsx:88 | WARN |
| `Bar` | - | yes | - | - | WARN |
| `BaseProjectAnnotations` | - | yes | - | - | WARN |
| `Blockquote` | - | yes | - | - | WARN |
| `BooleanConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:14 | PASS |
| `BooleanControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Boolean.tsx:117 | PASS |
| `BooleanProps` | type | yes | - | code/addons/docs/src/blocks/controls/Boolean.tsx:104 | PASS |
| `BooleanValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:13 | PASS |
| `Brand` | interface | yes | - | code/core/src/theming/types.ts:64 | PASS |
| `BuilderOptions` | type | yes | - | code/builders/builder-vite/src/types.ts:21 | PASS |
| `Button` | - | yes | - | code/core/src/components/components/Button/Button.tsx:53 | WARN |
| `CHANNEL_CREATED` | - | yes | - | - | WARN |
| `CLEAR_ID` | const | no | - | code/core/src/actions/constants.ts:5 | WARN |
| `COMPONENT_TESTING_PANEL_ID` | const | yes | - | code/core/src/component-testing/constants.ts:2 | WARN |
| `CSFFile` | type | yes | - | code/core/src/types/modules/story.ts:92 | WARN |
| `CSSObject` | - | yes | - | - | WARN |
| `CYCLIC_KEY` | const | no | - | code/core/src/actions/constants.ts:6 | WARN |
| `CacheProvider` | - | yes | - | - | WARN |
| `CalledExtractOnStoreError` | class | yes | - | code/core/src/preview-errors.ts:77 | WARN |
| `CalledPreviewMethodBeforeInitializationError` | class | yes | - | code/core/src/preview-errors.ts:107 | WARN |
| `Canvas` | const | yes | yes | code/addons/docs/src/blocks/blocks/Canvas.tsx:100 | PASS |
| `Card` | - | yes | - | code/core/src/components/components/Card/Card.tsx:98 | WARN |
| `Category` | enum | yes | - | code/core/src/manager-errors.ts:12 | WARN |
| `Channel` | - | yes | - | - | WARN |
| `CheckboxControl` | - | yes | - | - | WARN |
| `ClassNameStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/class-name.decorator.tsx:8 | PASS |
| `ClassNames` | - | yes | - | - | WARN |
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
| `Combo` | interface | yes | - | code/core/src/manager-api/root.tsx:116 | WARN |
| `Component` | type | no | - | code/addons/docs/src/blocks/blocks/types.ts:7 | WARN |
| `ComponentAnnotations` | interface | yes | - | code/core/src/csf/story.ts:452 | WARN |
| `ComponentEntry` | - | yes | - | - | WARN |
| `ConfigFile` | - | yes | - | - | WARN |
| `ContextObjectWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:6 | PASS |
| `ContextSpecWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:16 | PASS |
| `Control` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:82 | PASS |
| `ControlProps` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:3 | PASS |
| `ControlType` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:71 | PASS |
| `Controls` | const | yes | yes | code/addons/docs/src/blocks/blocks/Controls.tsx:109 | PASS |
| `CsfFile` | - | yes | - | - | WARN |
| `DEFAULT_VIEWPORT` | const | no | - | code/core/src/viewport/defaults.ts:232 | WARN |
| `DL` | - | yes | - | - | WARN |
| `DataAttributeStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/data-attribute.decorator.tsx:8 | PASS |
| `DateConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:29 | PASS |
| `DateControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:69 | PASS |
| `DateProps` | type | yes | - | code/addons/docs/src/blocks/controls/Date.tsx:68 | PASS |
| `DateValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:28 | PASS |
| `Decorator` | - | yes | - | code/frameworks/angular/src/client/public-types.ts:50 | WARN |
| `DecoratorFunction` | type | yes | - | code/core/src/actions/models/DecoratorFunction.ts:1 | PASS |
| `DecoratorHelpers` | - | yes | - | - | WARN |
| `Description` | const | yes | yes | code/addons/docs/src/blocks/blocks/Description.tsx:74 | PASS |
| `DescriptionType` | enum | no | - | code/addons/docs/src/blocks/blocks/Description.tsx:9 | WARN |
| `Div` | - | yes | - | - | WARN |
| `Docs` | function | yes | yes | code/addons/docs/src/blocks/blocks/Docs.tsx:17 | PASS |
| `DocsContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:23 | PASS |
| `DocsContainerProps` | interface | no | - | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18 | WARN |
| `DocsContext` | class | yes | - | code/core/src/preview-api/modules/preview-web/docs-context/DocsContext.ts:20 | PASS |
| `DocsEntry` | - | yes | - | - | WARN |
| `DocsPage` | function | yes | - | code/addons/docs/src/blocks/blocks/DocsPage.tsx:12 | PASS |
| `DocsProps` | type | yes | - | code/addons/docs/src/blocks/blocks/Docs.tsx:12 | PASS |
| `DocsRenderer` | class | yes | - | code/addons/docs/src/DocsRenderer.tsx:48 | PASS |
| `DocsStory` | const | yes | yes | code/addons/docs/src/blocks/blocks/DocsStory.tsx:42 | PASS |
| `DocsStoryProps` | type | no | - | code/addons/docs/src/blocks/blocks/types.ts:9 | WARN |
| `DocsTypes` | interface | yes | - | code/addons/docs/src/types.ts:254 | PASS |
| `EVENT_ID` | const | no | - | code/core/src/actions/constants.ts:4 | WARN |
| `Easing` | type | no | - | code/core/src/theming/types.ts:61 | WARN |
| `EmptyIndexError` | class | yes | - | code/core/src/preview-errors.ts:161 | WARN |
| `ErrorFormatter` | - | yes | - | - | WARN |
| `ExternalDocs` | function | no | - | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26 | WARN |
| `ExternalDocsContainer` | function | no | - | code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12 | WARN |
| `ExternalDocsProps` | type | no | - | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11 | WARN |
| `FULL_RUN_TRIGGERS` | const | yes | - | code/addons/vitest/src/constants.ts:61 | WARN |
| `FilesControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Files.tsx:40 | PASS |
| `FilesControlProps` | interface | yes | - | code/addons/docs/src/blocks/controls/Files.tsx:11 | PASS |
| `FlexBar` | - | yes | - | - | WARN |
| `Form` | - | yes | - | code/core/src/components/components/Form/Form.tsx:11 | WARN |
| `FrameworkOptions` | - | yes | - | code/frameworks/angular/src/types.ts:16 | WARN |
| `FunctionInterpolation` | type | yes | - | code/core/src/theming/index.ts:26 | PASS |
| `GLOBALS_UPDATED` | - | yes | - | - | WARN |
| `Global` | - | yes | - | - | WARN |
| `GlobalState` | type | yes | - | code/core/src/viewport/types.ts:16 | PASS |
| `GlobalStateUpdate` | type | no | - | code/core/src/viewport/types.ts:31 | WARN |
| `Globals` | interface | yes | - | code/core/src/csf/story.ts:165 | WARN |
| `GroupEntry` | - | yes | - | - | WARN |
| `H1` | - | yes | - | - | WARN |
| `H6` | - | yes | - | - | WARN |
| `HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:3 | PASS |
| `HR` | - | yes | - | - | WARN |
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
| `ImplicitActionsDuringRendering` | class | yes | - | code/core/src/preview-errors.ts:56 | WARN |
| `IncludeExcludeOptions` | interface | yes | - | code/core/src/csf/index.ts:38 | WARN |
| `IndexHash` | - | yes | - | - | WARN |
| `InitialViewportKeys` | type | yes | - | code/core/src/viewport/defaults.ts:230 | PASS |
| `Interpolation` | type | yes | - | code/core/src/theming/index.ts:27 | PASS |
| `InvalidFrameworkNameError` | class | yes | - | code/core/src/server-errors.ts:86 | WARN |
| `Keyframes` | - | yes | - | - | WARN |
| `LI` | - | yes | - | - | WARN |
| `LeafEntry` | - | yes | - | - | WARN |
| `Loader` | - | yes | - | code/core/src/components/components/Loader/Loader.tsx:109 | WARN |
| `MINIMAL_VIEWPORTS` | const | no | - | code/core/src/viewport/defaults.ts:234 | WARN |
| `ManagerContext` | const | yes | - | code/core/src/manager-api/root.tsx:80 | WARN |
| `ManagerProviderProps` | type | yes | - | code/core/src/manager-api/root.tsx:121 | WARN |
| `Markdown` | const | yes | yes | code/addons/docs/src/blocks/blocks/Markdown.tsx:55 | PASS |
| `MaybeMocked` | - | yes | - | - | WARN |
| `MdxFileWithNoCsfReferencesError` | class | yes | - | code/core/src/preview-errors.ts:145 | WARN |
| `Meta` | function | yes | yes | code/addons/docs/src/blocks/blocks/Meta.tsx:15 | PASS |
| `MissingFrameworkFieldError` | class | yes | - | code/core/src/server-errors.ts:70 | WARN |
| `MissingRenderToCanvasError` | class | yes | - | code/core/src/preview-errors.ts:91 | WARN |
| `MissingStoryAfterHmrError` | class | yes | - | code/core/src/preview-errors.ts:39 | WARN |
| `MissingStoryFromCsfFileError` | class | yes | - | code/core/src/preview-errors.ts:192 | WARN |
| `Mock` | - | yes | - | - | WARN |
| `MockInstance` | - | yes | - | - | WARN |
| `MockUniversalStore` | class | yes | - | code/core/src/shared/universal-store/mock.ts:40 | WARN |
| `Modal` | - | yes | - | code/core/src/components/components/Modal/Modal.tsx:242 | WARN |
| `MountMustBeDestructuredError` | class | yes | - | code/core/src/preview-errors.ts:226 | WARN |
| `NoRenderFunctionError` | class | yes | - | code/core/src/preview-errors.ts:256 | WARN |
| `NoStoryMatchError` | class | yes | - | code/core/src/preview-errors.ts:176 | WARN |
| `NoStoryMountedError` | class | yes | - | code/core/src/preview-errors.ts:269 | WARN |
| `NodePath` | - | yes | - | - | WARN |
| `NormalizedComponentAnnotations` | type | yes | - | code/core/src/types/modules/story.ts:66 | WARN |
| `NormalizedOptionsConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:62 | PASS |
| `NormalizedProjectAnnotations` | type | yes | - | code/core/src/types/modules/story.ts:55 | WARN |
| `NormalizedStoryAnnotations` | type | yes | - | code/core/src/types/modules/story.ts:78 | WARN |
| `NumberConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:32 | PASS |
| `NumberControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:28 | PASS |
| `NumberValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:31 | PASS |
| `NxProjectDetectedError` | class | yes | - | code/core/src/server-errors.ts:56 | WARN |
| `OL` | - | yes | - | - | WARN |
| `ObjectConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:41 | PASS |
| `ObjectControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Object.tsx:166 | PASS |
| `ObjectProps` | type | yes | - | code/addons/docs/src/blocks/controls/Object.tsx:164 | PASS |
| `ObjectValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:40 | PASS |
| `Of` | type | no | - | code/addons/docs/src/blocks/blocks/useOf.ts:11 | WARN |
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
| `P` | - | yes | - | - | WARN |
| `PANEL_ID` | const | no | - | code/core/src/actions/constants.ts:3 | WARN |
| `PARAM_KEY` | const | yes | - | code/addons/a11y/src/constants.ts:3 | PASS |
| `PREVIEW_INITIALIZED` | - | yes | - | - | WARN |
| `PRIMARY_STORY` | const | no | - | code/addons/docs/src/blocks/blocks/types.ts:3 | WARN |
| `Parameters` | interface | yes | - | code/core/src/csf/story.ts:32 | WARN |
| `Placeholder` | - | yes | - | - | WARN |
| `PlayFunction` | type | yes | - | code/core/src/csf/story.ts:302 | WARN |
| `Popover` | - | yes | - | - | WARN |
| `PopoverProvider` | - | yes | - | - | WARN |
| `PostMessageTransport` | - | yes | - | - | WARN |
| `Pre` | - | yes | - | code/core/src/components/components/typography/elements/Pre.tsx:6 | WARN |
| `PreparedStory` | type | yes | - | code/core/src/types/modules/story.ts:99 | WARN |
| `PresetColor` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:17 | PASS |
| `Preview` | class | yes | - | code/core/src/preview-api/modules/preview-web/Preview.tsx:60 | PASS |
| `PreviewWeb` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWeb.tsx:11 | PASS |
| `PreviewWithSelection` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWithSelection.tsx:77 | PASS |
| `Primary` | const | yes | - | code/addons/docs/src/blocks/blocks/Primary.tsx:16 | PASS |
| `ProjectAnnotations` | interface | yes | - | code/core/src/csf/story.ts:421 | WARN |
| `PropDescriptor` | type | no | - | code/core/src/preview-api/modules/store/filterArgTypes.ts:5 | WARN |
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
| `Refs` | - | yes | - | - | WARN |
| `RenderContext` | type | yes | - | code/core/src/types/modules/story.ts:129 | WARN |
| `RenderToCanvas` | type | yes | - | code/core/src/types/modules/story.ts:38 | WARN |
| `Report` | interface | no | - | code/core/src/preview-api/modules/store/reporter-api.ts:1 | WARN |
| `ReporterAPI` | class | no | - | code/core/src/preview-api/modules/store/reporter-api.ts:8 | WARN |
| `RootEntry` | - | yes | - | - | WARN |
| `SCROLL_INTO_VIEW` | const | yes | - | code/core/src/highlight/constants.ts:6 | PASS |
| `SELECT_STORY` | - | yes | - | - | WARN |
| `STORYBOOK_ADDON_TEST_CHANNEL` | const | yes | - | code/addons/vitest/src/constants.ts:13 | WARN |
| `STORY_PREPARED` | - | yes | - | - | WARN |
| `STORY_RENDERED` | - | yes | - | - | WARN |
| `STORY_SPECIFIED` | - | yes | - | - | WARN |
| `ScrollArea` | - | yes | - | - | WARN |
| `Select` | - | yes | - | code/core/src/components/components/Select/Select.tsx:201 | WARN |
| `SelectControl` | - | yes | - | - | WARN |
| `SelectionStore` | interface | no | - | code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17 | WARN |
| `SelectorWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:3 | PASS |
| `SeparatorOptions` | interface | yes | - | code/core/src/csf/index.ts:63 | WARN |
| `SortType` | type | yes | - | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:186 | PASS |
| `Source` | const | yes | yes | code/addons/docs/src/blocks/blocks/Source.tsx:181 | PASS |
| `SourceContainer` | function | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38 | WARN |
| `SourceContext` | const | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27 | WARN |
| `SourceContextProps` | interface | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22 | WARN |
| `SourceItem` | interface | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15 | WARN |
| `SourceParameters` | type | no | - | code/addons/docs/src/blocks/blocks/Source.tsx:16 | WARN |
| `SourceProps` | type | no | - | code/addons/docs/src/blocks/blocks/Source.tsx:28 | WARN |
| `Spaced` | - | yes | - | - | WARN |
| `Span` | - | yes | - | - | WARN |
| `State` | interface | yes | - | code/core/src/instrumenter/types.ts:72 | WARN |
| `StatusTypeIdMismatchError` | class | yes | - | code/core/src/manager-errors.ts:50 | WARN |
| `StoreOptions` | interface | yes | - | code/core/src/manager-api/store.ts:45 | WARN |
| `Store_CSFExports` | type | yes | - | code/core/src/types/modules/composedStory.ts:23 | WARN |
| `Stories` | const | yes | yes | code/addons/docs/src/blocks/blocks/Stories.tsx:74 | PASS |
| `StoriesHash` | - | yes | - | - | WARN |
| `Story` | const | yes | yes | code/addons/docs/src/blocks/blocks/Story.tsx:134 | PASS |
| `StoryAnnotations` | type | yes | - | code/core/src/csf/story.ts:543 | WARN |
| `StoryContext` | interface | yes | - | code/core/src/csf/story.ts:268 | WARN |
| `StoryEntry` | - | yes | - | - | WARN |
| `StoryFn` | type | yes | - | code/core/src/csf/story.ts:327 | WARN |
| `StoryIndexFetchError` | class | yes | - | code/core/src/preview-errors.ts:125 | WARN |
| `StoryIndexGenerator` | - | yes | - | - | WARN |
| `StoryObj` | - | yes | - | code/frameworks/angular/src/client/public-types.ts:45 | WARN |
| `StoryProps` | type | yes | - | code/addons/docs/src/blocks/blocks/Story.tsx:60 | PASS |
| `StorySources` | type | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20 | WARN |
| `StoryStore` | class | yes | - | code/core/src/preview-api/modules/store/StoryStore.ts:51 | PASS |
| `StoryStoreAccessedBeforeInitializationError` | class | yes | - | code/core/src/preview-errors.ts:211 | WARN |
| `StorybookConfig` | - | yes | - | code/frameworks/angular/src/types.ts:40 | WARN |
| `StorybookConfigVite` | type | yes | - | code/builders/builder-vite/src/types.ts:17 | PASS |
| `StorybookError` | class | yes | - | code/core/src/storybook-error.ts:25 | WARN |
| `StorybookIcon` | - | yes | - | - | WARN |
| `StorybookLogo` | - | yes | - | - | WARN |
| `StorybookParameters` | interface | yes | - | code/core/src/types/modules/csf.ts:75 | WARN |
| `StorybookTheme` | interface | yes | - | code/core/src/theming/types.ts:71 | PASS |
| `StrictArgs` | interface | yes | - | code/core/src/csf/story.ts:157 | WARN |
| `StyledComponent` | - | yes | - | - | WARN |
| `Subheading` | const | yes | yes | code/addons/docs/src/blocks/blocks/Subheading.tsx:23 | PASS |
| `Subtitle` | const | yes | yes | code/addons/docs/src/blocks/blocks/Subtitle.tsx:55 | PASS |
| `SyntaxHighlighter` | - | yes | - | - | WARN |
| `TEST_PROVIDER_ID` | const | yes | - | code/addons/vitest/src/constants.ts:12 | WARN |
| `TOOL_ID` | const | no | - | code/core/src/viewport/constants.ts:4 | WARN |
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
| `TestRunResult` | type | yes | - | code/addons/vitest/src/constants.ts:81 | WARN |
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
| `TriggerTestRunRequestPayload` | type | yes | - | code/addons/vitest/src/constants.ts:74 | WARN |
| `TriggerTestRunResponsePayload` | type | yes | - | code/addons/vitest/src/constants.ts:83 | WARN |
| `Typeset` | function | yes | yes | code/addons/docs/src/blocks/components/Typeset.tsx:50 | PASS |
| `Typography` | type | yes | - | code/core/src/theming/types.ts:59 | PASS |
| `UL` | - | yes | - | - | WARN |
| `UNKNOWN_ARGS_HASH` | const | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36 | WARN |
| `UPDATE_STORY_ARGS` | - | yes | - | - | WARN |
| `Unstyled` | const | yes | yes | code/addons/docs/src/blocks/blocks/Unstyled.tsx:9 | PASS |
| `UrlStore` | class | yes | - | code/core/src/preview-api/modules/preview-web/UrlStore.ts:94 | PASS |
| `UserEvent` | interface | no | - | code/core/src/test/testing-library.ts:119 | WARN |
| `UserEventObject` | type | no | - | code/core/src/test/index.ts:15 | WARN |
| `View` | interface | no | - | code/core/src/preview-api/modules/preview-web/View.ts:3 | WARN |
| `ViewMode` | type | yes | - | code/core/src/csf/story.ts:247 | WARN |
| `Viewport` | interface | no | - | code/core/src/viewport/types.ts:1 | WARN |
| `ViewportGlobals` | interface | no | - | code/core/src/viewport/types.ts:56 | WARN |
| `ViewportMap` | type | no | - | code/core/src/viewport/types.ts:14 | WARN |
| `ViewportParameters` | interface | yes | - | code/core/src/viewport/types.ts:33 | PASS |
| `ViewportStyles` | interface | yes | - | code/core/src/viewport/types.ts:9 | PASS |
| `ViewportType` | type | yes | - | code/core/src/viewport/types.ts:7 | PASS |
| `ViewportTypes` | interface | no | - | code/core/src/viewport/types.ts:65 | WARN |
| `ViteBuilder` | type | yes | - | code/builders/builder-vite/src/types.ts:10 | PASS |
| `ViteFinal` | type | yes | - | code/builders/builder-vite/src/types.ts:12 | PASS |
| `WebRenderer` | interface | yes | - | code/core/src/types/modules/story.ts:28 | WARN |
| `WebView` | class | yes | - | code/core/src/preview-api/modules/preview-web/WebView.ts:42 | PASS |
| `WebsocketTransport` | - | yes | - | - | WARN |
| `WithTooltip` | - | yes | - | - | WARN |
| `Wrapper` | const | no | - | code/addons/docs/src/blocks/blocks/Wrapper.tsx:10 | WARN |
| `Zoom` | - | yes | - | code/core/src/components/components/Zoom/Zoom.tsx:4 | WARN |
| `__definePreview` | - | yes | - | - | WARN |
| `action` | function | yes | yes | code/core/src/actions/runtime/action.ts:50 | PASS |
| `actions` | function | no | - | code/core/src/actions/runtime/actions.ts:5 | WARN |
| `addToGlobalContext` | - | yes | - | - | WARN |
| `addons` | const | yes | - | code/addons/docs/src/preset.ts:155 | WARN |
| `afterEach` | function | yes | yes | code/addons/a11y/src/preview.tsx:14 | WARN |
| `anchorBlockIdFromId` | function | no | - | code/addons/docs/src/blocks/blocks/Anchor.tsx:4 | WARN |
| `applyHooks` | function | yes | yes | code/core/src/preview-api/modules/addons/hooks.ts:184 | PASS |
| `argsHash` | function | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11 | WARN |
| `assertIsFn` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:19 | WARN |
| `automock` | - | yes | - | - | WARN |
| `babelParse` | - | yes | - | - | WARN |
| `background` | const | no | - | code/core/src/theming/base.ts:44 | WARN |
| `bail` | function | yes | yes | code/builders/builder-vite/src/index.ts:37 | WARN |
| `build` | function | yes | yes | code/builders/builder-vite/src/index.ts:63 | WARN |
| `canvas` | - | yes | - | - | WARN |
| `clearAllMocks` | function | yes | yes | code/core/src/test/spy.ts:77 | PASS |
| `color` | const | no | - | code/core/src/theming/base.ts:1 | WARN |
| `colors` | - | yes | - | - | WARN |
| `combineArgs` | function | yes | yes | code/core/src/preview-api/modules/store/args.ts:84 | PASS |
| `combineParameters` | function | yes | yes | code/core/src/preview-api/modules/store/parameters.ts:11 | PASS |
| `combineTags` | function | yes | - | code/core/src/csf/index.ts:81 | WARN |
| `componentTransform` | - | yes | - | - | WARN |
| `composeConfigs` | function | yes | yes | code/core/src/preview-api/modules/store/csf/composeConfigs.ts:43 | PASS |
| `composeStepRunners` | function | yes | yes | code/core/src/preview-api/modules/store/csf/stepRunners.ts:27 | PASS |
| `composeStories` | function | yes | no | code/core/src/preview-api/modules/store/csf/portable-stories.ts:274 | FAIL |
| `composeStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:90 | PASS |
| `config` | const | no | - | code/core/src/actions/runtime/configureActions.ts:3 | WARN |
| `configureActions` | function | yes | - | code/core/src/actions/runtime/configureActions.ts:9 | PASS |
| `core` | - | yes | - | - | WARN |
| `corePresets` | const | yes | - | code/builders/builder-vite/src/index.ts:67 | WARN |
| `create` | function | yes | yes | code/core/src/theming/create.ts:29 | PASS |
| `createBrowserChannel` | - | yes | - | - | WARN |
| `createCache` | - | yes | - | - | WARN |
| `createGlobal` | const | yes | - | code/core/src/theming/global.ts:101 | PASS |
| `createPlaywrightTest` | function | no | - | code/core/src/preview-api/modules/store/csf/portable-stories.ts:319 | WARN |
| `createReset` | const | yes | - | code/core/src/theming/global.ts:25 | PASS |
| `createTest` | - | yes | - | - | WARN |
| `css` | - | yes | - | - | WARN |
| `darken` | const | yes | - | code/core/src/theming/utils.ts:62 | PASS |
| `decorateStory` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:10 | PASS |
| `decorators` | const | yes | - | code/addons/a11y/src/preview.tsx:12 | WARN |
| `defaultDecorateStory` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:49 | PASS |
| `defineMain` | - | yes | yes | code/frameworks/angular/src/node/index.ts:3 | WARN |
| `definePreview` | - | yes | no | code/frameworks/angular/src/client/preview.ts:45 | FAIL |
| `deprecate` | const | yes | - | code/core/src/client-logger/index.ts:75 | WARN |
| `emitTransformCode` | function | no | - | code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15 | WARN |
| `enrichCsf` | - | yes | - | code/core/src/csf-tools/enrichCsf.ts:144 | WARN |
| `ensure` | function | no | - | code/core/src/theming/ensure.ts:10 | WARN |
| `esmWalker` | function | yes | - | code/core/src/mocking-utils/esmWalker.ts:71 | WARN |
| `expect` | - | yes | - | - | WARN |
| `experimental_UniversalStore` | class | yes | - | code/core/src/shared/universal-store/index.ts:82 | WARN |
| `experimental_getStatusStore` | - | yes | - | code/core/src/core-server/stores/status.ts | WARN |
| `experimental_getTestProviderStore` | - | yes | - | code/core/src/core-server/stores/test-provider.ts | WARN |
| `experimental_loadStorybook` | - | yes | - | - | WARN |
| `extract` | - | yes | - | - | WARN |
| `extractTitle` | function | no | - | code/addons/docs/src/blocks/blocks/Title.tsx:24 | WARN |
| `filterArgTypes` | function | yes | yes | code/core/src/preview-api/modules/store/filterArgTypes.ts:10 | PASS |
| `findByRole` | - | yes | - | - | WARN |
| `fireEvent` | - | yes | - | - | WARN |
| `fn` | function | yes | yes | code/core/src/test/spy.ts:48 | PASS |
| `format` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:22 | PASS |
| `formatDate` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:26 | PASS |
| `formatTime` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:34 | PASS |
| `generate` | - | yes | - | - | WARN |
| `generateStoryFile` | - | yes | - | - | WARN |
| `getByRole` | - | yes | - | - | WARN |
| `getCsfFactoryAnnotations` | function | no | - | code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10 | WARN |
| `getPreferredColorScheme` | function | yes | - | code/core/src/theming/utils.ts:66 | PASS |
| `getPreviewBodyTemplate` | - | yes | - | - | WARN |
| `getPreviewHeadTemplate` | - | yes | - | - | WARN |
| `getSessionId` | - | yes | - | - | WARN |
| `getStoryHref` | - | yes | - | code/core/src/components/components/utils/getStoryHref.ts:15 | WARN |
| `getStoryId` | function | no | - | code/addons/docs/src/blocks/blocks/Story.tsx:62 | WARN |
| `getStoryProps` | function | no | - | code/addons/docs/src/blocks/blocks/Story.tsx:75 | WARN |
| `getStorySortParameter` | - | yes | - | - | WARN |
| `getStorybookInfo` | function | yes | - | code/core/src/common/utils/get-storybook-info.ts:139 | WARN |
| `getStorybookMetadata` | - | yes | - | - | WARN |
| `hasVitePlugins` | function | yes | yes | code/builders/builder-vite/src/utils/has-vite-plugins.ts:13 | PASS |
| `ignoreSsrWarning` | const | yes | - | code/core/src/theming/index.ts:43 | PASS |
| `inferControls` | function | yes | - | code/core/src/preview-api/modules/store/inferControls.ts:66 | PASS |
| `initialGlobals` | const | yes | - | code/addons/a11y/src/preview.tsx:98 | WARN |
| `initializeThemeState` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:34 | PASS |
| `instrument` | function | yes | - | code/core/src/instrumenter/instrumenter.ts:749 | WARN |
| `isExportStory` | function | yes | - | code/core/src/csf/index.ts:51 | WARN |
| `isMockFunction` | - | yes | - | - | WARN |
| `isPropValid` | - | yes | - | - | WARN |
| `jsx` | - | yes | - | - | WARN |
| `keyframes` | - | yes | - | - | WARN |
| `lighten` | const | yes | - | code/core/src/theming/utils.ts:61 | PASS |
| `loadMainConfig` | function | yes | - | code/core/src/common/utils/load-main-config.ts:14 | WARN |
| `logTracker` | - | yes | - | - | WARN |
| `logger` | const | yes | - | code/core/src/client-logger/index.ts:23 | WARN |
| `makeDecorator` | function | yes | - | code/core/src/preview-api/modules/addons/make-decorator.ts:44 | PASS |
| `mockChannel` | function | yes | yes | code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:3 | PASS |
| `mocked` | function | yes | yes | code/core/src/test/spy.ts:119 | PASS |
| `mocks` | - | yes | - | - | WARN |
| `mount` | function | yes | no | code/renderers/react/src/mount.ts:5 | FAIL |
| `normalizeArrays` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeArrays.ts:1 | PASS |
| `normalizeProjectAnnotations` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:17 | PASS |
| `normalizeStories` | function | yes | - | code/core/src/common/utils/normalize-stories.ts:108 | WARN |
| `normalizeStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeStory.ts:25 | PASS |
| `onMockCall` | function | yes | yes | code/core/src/test/spy.ts:35 | PASS |
| `once` | function | yes | - | code/core/src/client-logger/index.ts:57 | WARN |
| `parameters` | const | yes | - | code/addons/a11y/src/preview.tsx:105 | WARN |
| `parse` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:17 | PASS |
| `parseDate` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:11 | PASS |
| `parseKind` | function | yes | - | code/core/src/csf/index.ts:69 | WARN |
| `parseTime` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:18 | PASS |
| `parser` | - | yes | - | - | WARN |
| `pauseAnimations` | function | no | - | code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18 | WARN |
| `pluckThemeFromContext` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:16 | PASS |
| `prepareMeta` | function | yes | yes | code/core/src/preview-api/modules/store/csf/prepareStory.ts:171 | PASS |
| `prepareStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/prepareStory.ts:37 | PASS |
| `pretty` | function | yes | - | code/core/src/client-logger/index.ts:77 | WARN |
| `prompt` | - | yes | - | - | WARN |
| `queryByRole` | - | yes | - | - | WARN |
| `recast` | - | yes | - | - | WARN |
| `redirect` | - | yes | - | - | WARN |
| `resetAllMocks` | function | yes | yes | code/core/src/test/spy.ts:89 | PASS |
| `resolve` | - | yes | - | - | WARN |
| `responsiveViewport` | const | no | - | code/core/src/viewport/responsiveViewport.tsx:4 | WARN |
| `restoreAllMocks` | function | yes | yes | code/core/src/test/spy.ts:98 | PASS |
| `runtime` | - | yes | - | - | WARN |
| `sanitize` | function | yes | - | code/core/src/csf/index.ts:8 | WARN |
| `sanitizeStoryContextUpdate` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:30 | PASS |
| `sb` | const | yes | - | code/core/src/test/index.ts:54 | PASS |
| `screen` | - | yes | - | - | WARN |
| `setDefaultProjectAnnotations` | function | yes | - | code/core/src/preview-api/modules/store/csf/portable-stories.ts:49 | PASS |
| `setProjectAnnotations` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:73 | PASS |
| `simulateDOMContentLoaded` | function | no | - | code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31 | WARN |
| `simulatePageLoad` | function | no | - | code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83 | WARN |
| `slugs` | const | no | - | code/addons/docs/src/blocks/blocks/Heading.tsx:15 | WARN |
| `sortStoriesV7` | function | yes | yes | code/core/src/preview-api/modules/store/sortStories.ts:37 | PASS |
| `spyOn` | function | yes | yes | code/core/src/test/spy.ts:41 | PASS |
| `srOnlyStyles` | const | yes | - | code/core/src/theming/global.ts:12 | PASS |
| `start` | function | yes | yes | code/builders/builder-vite/src/index.ts:41 | WARN |
| `storeOptions` | const | yes | - | code/addons/vitest/src/constants.ts:21 | WARN |
| `storyNameFromExport` | function | yes | - | code/core/src/csf/index.ts:35 | WARN |
| `storybookTest` | function | no | - | code/addons/vitest/src/vitest-plugin/index.ts:164 | WARN |
| `styled` | - | yes | - | - | WARN |
| `telemetry` | - | yes | - | - | WARN |
| `themes` | const | yes | - | code/core/src/theming/create.ts:20 | PASS |
| `toId` | function | yes | yes | code/core/src/csf/index.ts:27 | WARN |
| `toTestId` | function | yes | - | code/core/src/csf/index.ts:31 | WARN |
| `tokens` | const | no | - | code/core/src/theming/base.ts:104 | WARN |
| `transformSync` | - | yes | - | - | WARN |
| `traverse` | - | yes | - | - | WARN |
| `types` | - | yes | - | - | WARN |
| `typography` | const | no | - | code/core/src/theming/base.ts:59 | WARN |
| `uninstrumentedUserEvent` | const | no | - | code/core/src/test/testing-library.ts:121 | WARN |
| `useArgs` | function | yes | yes | code/core/src/preview-api/modules/addons/hooks.ts:614 | PASS |
| `useCallback` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:344 | PASS |
| `useChannel` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:530 | PASS |
| `useEffect` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:498 | PASS |
| `useGlobals` | function | yes | yes | code/core/src/preview-api/modules/addons/hooks.ts:649 | PASS |
| `useMemo` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:322 | PASS |
| `useOf` | function | yes | - | code/addons/docs/src/blocks/blocks/useOf.ts:18 | PASS |
| `useParameter` | function | yes | yes | code/core/src/preview-api/modules/addons/hooks.ts:590 | PASS |
| `useReducer` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:457 | PASS |
| `useRef` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:367 | PASS |
| `useSourceProps` | function | no | - | code/addons/docs/src/blocks/blocks/Source.tsx:101 | WARN |
| `useState` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:418 | PASS |
| `useStatusStore` | - | yes | - | - | WARN |
| `useStoryContext` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:560 | PASS |
| `useTabsState` | - | yes | - | - | WARN |
| `useTestProviderStore` | - | yes | - | - | WARN |
| `useTheme` | - | yes | - | - | WARN |
| `useThemeParameters` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:20 | PASS |
| `useUniversalStore` | - | yes | - | - | WARN |
| `userEvent` | - | yes | - | - | WARN |
| `userOrAutoTitle` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:86 | PASS |
| `userOrAutoTitleFromSpecifier` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:49 | PASS |
| `viteFinal` | function | yes | yes | code/addons/docs/src/preset.ts:159 | WARN |
| `vitestTransform` | - | yes | - | - | WARN |
| `waitFor` | - | yes | - | - | WARN |
| `waitForAnimations` | function | no | - | code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54 | WARN |
| `withActions` | const | yes | - | code/core/src/actions/decorator.ts:59 | PASS |
| `withTheme` | - | yes | - | - | WARN |
| `withThemeByClassName` | function | yes | yes | code/addons/themes/src/decorators/class-name.decorator.tsx:19 | PASS |
| `withThemeByDataAttribute` | function | yes | yes | code/addons/themes/src/decorators/data-attribute.decorator.tsx:19 | PASS |
| `withThemeFromJSXProvider` | function | yes | yes | code/addons/themes/src/decorators/provider.decorator.tsx:23 | PASS |
| `within` | - | yes | - | - | WARN |
| `withoutVitePlugins` | function | yes | yes | code/builders/builder-vite/src/utils/without-vite-plugins.ts:2 | PASS |

### Coverage Summary

- **Exports Found:** 280
- **Documented:** 206 (73.57%)
- **Missing Documentation:** 74
- **Signature Mismatches:** 3
- **Stale Documentation:** 249, documented extras included
- **Scoped Out by the Brief:** `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx), `AngularMeta` (code/frameworks/angular/src/client/preview.ts), `AngularOptions` (code/frameworks/angular/src/types.ts), `AngularPreview` (code/frameworks/angular/src/client/preview.ts), `AngularRenderer` (code/frameworks/angular/src/client/types.ts), `AngularStory` (code/frameworks/angular/src/client/preview.ts), `BabelFileClass` (code/core/src/babel/index.ts), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts), `Bar` (code/core/src/components/components/Bar/Bar.tsx), `BaseLocationProvider` (code/core/src/router/router.tsx), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx), `BuildIndexOptions` (code/core/src/core-server/build-index.ts), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts), `CacheEntry` (code/core/src/telemetry/event-cache.ts), `Channel` (code/core/src/channels/main.ts), `ChannelHandler` (code/core/src/channels/types.ts), `ChannelTransport` (code/core/src/channels/types.ts), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts), `CsfFile` (code/core/src/csf-tools/CsfFile.ts), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts), `DL` (code/core/src/components/components/typography/elements/DL.tsx), `Dependency` (code/core/src/telemetry/types.ts), `Div` (code/core/src/components/components/typography/elements/Div.tsx), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts), `ErrorCollector` (code/core/src/telemetry/error-collector.ts), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx), `EventType` (code/core/src/telemetry/types.ts), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts), `H1` (code/core/src/components/components/typography/elements/H1.tsx), `H2` (code/core/src/components/components/typography/elements/H2.tsx), `H3` (code/core/src/components/components/typography/elements/H3.tsx), `H4` (code/core/src/components/components/typography/elements/H4.tsx), `H5` (code/core/src/components/components/typography/elements/H5.tsx), `H6` (code/core/src/components/components/typography/elements/H6.tsx), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts), `HR` (code/core/src/components/components/typography/elements/HR.tsx), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts), `IStory` (code/frameworks/angular/src/client/types.ts), `InitPayload` (code/core/src/telemetry/types.ts), `LI` (code/core/src/components/components/typography/elements/LI.tsx), `LinkProps` (code/core/src/router/types.ts), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx), `Location` (code/core/src/router/router.tsx), `LocationProvider` (code/core/src/router/router.tsx), `LogLevel` (code/core/src/node-logger/logger/logger.ts), `MemoryRouter` (code/core/src/router/router.tsx), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts), `NavigateFunction` (code/core/src/router/types.ts), `NavigateOptions` (code/core/src/router/types.ts), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts), `OL` (code/core/src/components/components/typography/elements/OL.tsx), `Other` (code/core/src/router/types.ts), `P` (code/core/src/components/components/typography/elements/P.tsx), `Payload` (code/core/src/telemetry/types.ts), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx), `Popover` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts), `PreactRenderer` (code/renderers/preact/src/types.ts), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx), `RenderData` (code/core/src/router/types.ts), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx), `Route` (code/core/src/router/router.tsx), `RouterData` (code/core/src/router/types.ts), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx), `Separator` (code/core/src/components/components/Bar/Separator.tsx), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx), `Span` (code/core/src/components/components/typography/elements/Span.tsx), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts), `StaticStory` (code/core/src/csf-tools/CsfFile.ts), `StoryData` (code/core/src/router/utils.ts), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts), `StoryTest` (code/core/src/csf-tools/CsfFile.ts), `StorybookAddon` (code/core/src/telemetry/types.ts), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx), `StorybookMetadata` (code/core/src/telemetry/types.ts), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts), `SvelteRenderer` (code/renderers/svelte/src/types.ts), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts), `TT` (code/core/src/components/components/typography/elements/TT.tsx), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx), `TabButton` (code/core/src/components/components/Tabs/Button.tsx), `TabList` (code/core/src/components/components/Tabs/TabList.tsx), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts), `TelemetryData` (code/core/src/telemetry/types.ts), `TelemetryEvent` (code/core/src/telemetry/types.ts), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts), `UL` (code/core/src/components/components/typography/elements/UL.tsx), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts), `WebComponentsStory` (code/renderers/web-components/src/preview.ts), `WebComponentsTypes` (code/renderers/web-components/src/types.ts), `WebsocketTransport` (code/core/src/channels/websocket/index.ts), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts), `babelParseExpression` (code/core/src/babel/babelParse.ts), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts), `babelPrint` (code/core/src/babel/babelParse.ts), `buildArgsParam` (code/core/src/router/utils.ts), `buildDevStandalone` (code/core/src/core-server/build-dev.ts), `buildIndexStandalone` (code/core/src/core-server/build-index.ts), `buildStaticStandalone` (code/core/src/core-server/build-static.ts), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts), `cleanPaths` (code/core/src/telemetry/sanitize.ts), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx), `colors` (code/core/src/node-logger/index.ts), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts), `components` (code/core/src/components/index.ts), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx), `createBrowserChannel` (code/core/src/channels/index.ts), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts), `experimental_loadStorybook` (code/core/src/core-server/load.ts), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts), `extractSource` (code/core/src/csf-tools/enrichCsf.ts), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts), `formatCsf` (code/core/src/csf-tools/CsfFile.ts), `framework` (code/core/src/core-server/presets/common-override-preset.ts), `generate` (code/core/src/babel/index.ts), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts), `getCustomElements` (code/renderers/web-components/src/framework-api.ts), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts), `getLastEvents` (code/core/src/telemetry/event-cache.ts), `getMatch` (code/core/src/router/utils.ts), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts), `getServerPort` (code/core/src/core-server/utils/server-address.ts), `getSessionId` (code/core/src/telemetry/session-id.ts), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts), `hrefTo` (code/addons/links/src/utils.ts), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts), `isExampleStoryId` (code/core/src/telemetry/index.ts), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts), `isValidComponent` (code/renderers/web-components/src/framework-api.ts), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts), `linkTo` (code/addons/links/src/utils.ts), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts), `loadCsf` (code/core/src/csf-tools/CsfFile.ts), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx), `navigate` (code/addons/links/src/utils.ts), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts), `parsePath` (code/core/src/router/utils.ts), `parserOptions` (code/core/src/babel/babelParse.ts), `printConfig` (code/core/src/csf-tools/ConfigFile.ts), `printCsf` (code/core/src/csf-tools/CsfFile.ts), `prompt` (code/core/src/node-logger/prompts/index.ts), `protectUrls` (code/core/src/node-logger/wrap-utils.ts), `queryFromLocation` (code/core/src/router/utils.ts), `readConfig` (code/core/src/csf-tools/ConfigFile.ts), `readCsf` (code/core/src/csf-tools/CsfFile.ts), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts), `resetComponents` (code/core/src/components/index.ts), `resolveExpression` (code/core/src/babel/expression-resolver.ts), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts), `sanitizeError` (code/core/src/telemetry/sanitize.ts), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts), `setCustomElements` (code/renderers/web-components/src/framework-api.ts), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts), `stories` (code/core/src/core-server/presets/common-override-preset.ts), `stringifyQuery` (code/core/src/router/utils.ts), `telemetry` (code/core/src/telemetry/index.ts), `traverse` (code/core/src/babel/index.ts), `typescript` (code/core/src/core-server/presets/common-override-preset.ts), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts), `useNavigate` (code/core/src/router/router.tsx), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts), `withLinks` (code/addons/links/src/utils.ts), `withReset` (code/core/src/components/components/typography/lib/common.tsx), `withTelemetry` (code/core/src/core-server/withTelemetry.ts), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts), `writeCsf` (code/core/src/csf-tools/CsfFile.ts)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 73.57% |
| Signature Accuracy | 96.51% |
| Type Coverage | 75.83% |

### Coverage Notes

- Inventory (§1): delegated to four parallel subagents (SKILL.md with the split-body cross-check; `references/core-api.md`; `references/framework-config.md` + `references/csf3-patterns.md`; `references/story-types.md` + `references/doc-blocks.md` + `references/addons.md`), because SKILL.md's `## Full*` headings are stubs. Each subagent wrote its JSON to the run folder and the four parts were concatenated, unchanged, into `inventory-response.txt` (565 entries, 461 distinct names, 473 name+kind items). `validate-inventory.py`: valid; spot-check sampled `A`, `StoryFn`, `withoutVitePlugins`, none absent.
- Denominator (§2b): `surface.json` `denominator` = clause `stratified-scope`, branch `barrel`, `surfaceSet` `tier_a_include`, `ladderStep` 2, `absentSet` null, `rebuild` null, entry points `barrel`. metadata.json carries no `stats.effective_denominator`, so ladder step 1 has nothing to take; the named `tier_a_include` set (280 names over 118 defining files, the 48 globs of brief note 10) is the denominator, and the barrel branch names each undocumented export. The extractor's own `effective_denominator` (280, basis `tier_a_include`) agrees.
- Guards (§4): `guards.deflation` not applicable (no stored scalar), `guards.inflation` not applicable, `guards.staleScope` did not fire (no unmatched `scope.include` or `tier_a_include` glob, nothing restored). Umbrella ratio 0.93 over 12 root entries (54 names, 50 re-exported).
- Extraction (§2): `skf-extract-public-api.py --mode full --head-cap 0` status `ok`, 1274 files in scope, not truncated, no fallback. `file_issues` reports an ast-grep syntax error in 5 files (`code/core/src/csf/csf-factories.ts:75`, `code/core/src/instrumenter/typings.d.ts:8`, `code/core/src/mocking-utils/esmWalker.ts:37`, `code/core/src/test/spy.ts:15` (`export type * from '@vitest/spy'`), `code/core/src/typings.d.ts:28`), listed in `extraction.readByEye`; the status is `ok`, not `incomplete`, so §2 reads none of them by eye. `extractionGaps[]` names 7 exports with no file (`BabelFile`, `GeneratorOptions`, `NodePath`, `analyzeMdx`, `babelParse`, `instance`, `transformSync`); none is in the `tier_a_include` set.
- Signatures (§2, §2b): `score-signatures.py plan` listed 86 comparisons over 60 files; four subagents compared them (one response file per source file, `signatures-1.txt` … `signatures-60.txt`). 3 mismatches (Critical `signature-mismatch`): `composeStories` (compared at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:274`), `definePreview` (compared at `code/frameworks/angular/src/client/preview.ts:45`) and `mount` (compared at `code/renderers/react/src/mount.ts:5`). Type Coverage counts the `tier_a_include` set's 120 types: 91 documented, 29 missing.
- Split-body cross-check (§1b): 1 mismatch, `composeStories` (SKILL.md:117 vs `references/story-types.md:181`), recorded as a High `split-body-mismatch` gap at the reference line.
- Stale names (§2c): 249 documented names are not in the `tier_a_include` set (mostly Tier B names the skill documents on purpose, per brief note 10). `classify-stale` marked 14 `fabricated: true` (every provenance entry cites a file that does not define the name): `ComponentEntry`, `DocsEntry`, `GroupEntry`, `HashEntry`, `IndexHash`, `LeafEntry`, `RootEntry`, `StoryEntry`, `definePreview`, `fireEvent`, `screen`, `userEvent`, `waitFor`, `within`. These are recorded as Critical `fabricated-signature` gaps. Names it finds declared become Info `observation` gaps; the rest are Medium `stale-documentation` gaps. Ledger: 14 Critical `fabricated-signature`, 105 Info `observation`, 130 Medium `stale-documentation`.
- Numerator ground truth (§2b): `skipped` (no inflation signature: metadata carries no `stats.effective_denominator`).
- Metadata coherence (§4b): one Medium finding (`stats.exports_public_api` 1335 vs `exports[]` 83, 94% drift) and one Info finding (barrel 1335 vs documented 223).
- Coverage gaps recorded (§5b): 3 Critical `signature-mismatch`, 14 Critical `fabricated-signature`, 1 High `split-body-mismatch`, 45 Medium `missing-export`, 29 Medium `missing-type`, 130 Medium `stale-documentation`, 1 Medium `metadata-drift`, 1 Info `multi-denominator`, 105 Info `observation`, 45 Info `provenance-unverified` (374 records).
- Provenance line check (§4c): 47 stale map entries; 45 are `line-not-definition` with no definition line found, recorded as Info `provenance-unverified` gaps; the 2 `file-missing` items are not reported by this section.


## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | - | - | No structural finding: required sections satisfied (`description` by `Overview`, `usage` by `Quick Start`, `api_surface` by `Key API Summary`); 10 code fences, balanced, none bare; no table drift; no `scripts/` or `assets/` folder; every function and method export is used in the usage-family scope (`zero_usage` empty); no async/sync contradiction among the 15 called exports (`expect` is described as awaited and awaited in 3 of 4 calls; the other async wording describes `play`, not the export). | - |

**Structural Issues:** 0

- Migration & deprecation (§2b): `forge-data/oms-storybook-react-vite/10.3.5/evidence-report.md` exists but has no YAML frontmatter, so `t2_future_count` is absent: treated as Case 4 and skipped (the rule's note: "Section 4b verification skipped — evidence-report.md not found"; here the report is present but predates the pinned field).

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| 1 | references/story-types.md | `composeStories` | SKILL.md says `storybook/preview-api` exports core's renderer-agnostic `composeStories(storiesImport, globalConfig, composeStoryFn?)` (required `globalConfig`); the reference says the React renderer's symbol is re-exported from `storybook/preview-api` too, so all three would be the same function. Recorded by coverage-check §1b. | 117 | 181 |

**Exports Cross-Checked:** 21
**Mismatches Found:** 1

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

**Result:** **FAIL**, not scored: the hard gate blocked this run on 18 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 374
**Blocking (Critical + High):** 18
**Non-blocking (Medium + Low + Info):** 356

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 17 | Read the source code and write or correct the documentation |
| High | 1 | Read the source code and write or correct the documentation |
| Medium | 205 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 151 | Optional improvements, no action required |
| **Total** | **374** | |

### GAP-001: Signature mismatch: composeStories

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:274
**Export:** composeStories

**Issue:** documented `composeStories(csfExports, projectAnnotations?)`, source `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory)`: Wrong optionality: the second parameter (globalConfig: ProjectAnnotations<Renderer>) is required in the source declaration, but documented as optional (projectAnnotations?). Parameter names also differ (storiesImport/globalConfig vs csfExports/projectAnnotations); omitting the optional third composeStoryFn is not itself a mismatch.

**Remediation:** Update the documented signature of `composeStories` from `composeStories(csfExports, projectAnnotations?)` to `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory)`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:274`.

### GAP-002: Signature mismatch: definePreview

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/frameworks/angular/src/client/preview.ts:45
**Export:** definePreview

**Issue:** documented `definePreview(...): ReactPreview`, source `export function __definePreview<Addons extends PreviewAddon<never>[]>(input: { addons: Addons } & ProjectAnnotations<AngularRenderer & InferTypes<Addons>>): AngularPreview<AngularRenderer & InferTypes<Addons>>`: Wrong return type: the Angular declaration at this line returns AngularPreview<AngularRenderer & InferTypes<Addons>>, not ReactPreview.

**Remediation:** Update the documented signature of `definePreview` from `definePreview(...): ReactPreview` to `export function __definePreview<Addons extends PreviewAddon<never>[]>(input: { addons: Addons } & ProjectAnnotations<AngularRenderer & InferTypes<Addons>>): AngularPreview<AngularRenderer & InferTypes<Addons>>`, the signature the source defines at `code/frameworks/angular/src/client/preview.ts:45`.

### GAP-003: Signature mismatch: mount

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/renderers/react/src/mount.ts:5
**Export:** mount

**Issue:** documented `mount(JSX element (e.g. <Button {...args} />))`, source `export const mount: BaseAnnotations<ReactRenderer>["mount"] = (context: StoryContext) => async (ui) => { ...; return context.canvas; }  // BaseAnnotations mount = (context: StoryContext<TRenderer, TArgs>) => TRenderer["mount"]; ReactRenderer mount = (ui?: JSX.Element) => Promise<Canvas>`: Wrong parameter: the declared export is curried. Its only parameter is context: StoryContext, and it returns the function that takes the element (ui?: JSX.Element) => Promise<Canvas>. The JSX element belongs to the inner function, i.e. the play-context mount, where it is optional. The docs present it as the direct parameter of the exported mount.

**Remediation:** Update the documented signature of `mount` from `mount(JSX element (e.g. <Button {...args} />))` to `export const mount: BaseAnnotations<ReactRenderer>["mount"] = (context: StoryContext) => async (ui) => { ...; return context.canvas; }  // BaseAnnotations mount = (context: StoryContext<TRenderer, TArgs>) => TRenderer["mount"]; ReactRenderer mount = (ui?: JSX.Element) => Promise<Canvas>`, the signature the source defines at `code/renderers/react/src/mount.ts:5`.

### GAP-109: Fabricated signature: ComponentEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** ComponentEntry

**Issue:** SKILL.md documents `ComponentEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `ComponentEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:27`).

### GAP-116: Fabricated signature: DocsEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** DocsEntry

**Issue:** SKILL.md documents `DocsEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `DocsEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:34`).

### GAP-126: Fabricated signature: GroupEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** GroupEntry

**Issue:** SKILL.md documents `GroupEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `GroupEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:21`).

### GAP-130: Fabricated signature: HashEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** HashEntry

**Issue:** SKILL.md documents `HashEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `HashEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:67`).

### GAP-134: Fabricated signature: IndexHash

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** IndexHash

**Issue:** SKILL.md documents `IndexHash`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `IndexHash` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:80`).

### GAP-138: Fabricated signature: LeafEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** LeafEntry

**Issue:** SKILL.md documents `LeafEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `LeafEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:66`).

### GAP-177: Fabricated signature: RootEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** RootEntry

**Issue:** SKILL.md documents `RootEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `RootEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:15`).

### GAP-196: Fabricated signature: StoryEntry

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** StoryEntry

**Issue:** SKILL.md documents `StoryEntry`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `StoryEntry` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/types/modules/api-stories.ts:45`).

### GAP-258: Fabricated signature: definePreview

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/preview-api/index.ts:1
**Export:** definePreview

**Issue:** SKILL.md documents `definePreview`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `definePreview` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/preview-api/index.ts:1`).

### GAP-269: Fabricated signature: fireEvent

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:43
**Export:** fireEvent

**Issue:** SKILL.md documents `fireEvent`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `fireEvent` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:43`).

### GAP-305: Fabricated signature: screen

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:107
**Export:** screen

**Issue:** SKILL.md documents `screen`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `screen` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:107`).

### GAP-321: Fabricated signature: userEvent

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:123
**Export:** userEvent

**Issue:** SKILL.md documents `userEvent`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `userEvent` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:123`).

### GAP-324: Fabricated signature: waitFor

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:108
**Export:** waitFor

**Issue:** SKILL.md documents `waitFor`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `waitFor` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:108`).

### GAP-326: Fabricated signature: within

**Severity:** Critical
**Category:** Coverage (fabricated-signature)
**Source:** code/core/src/test/testing-library.ts:110
**Export:** within

**Issue:** SKILL.md documents `within`, which the source API surface lacks and the cited file does not define

**Remediation:** Remove `within` from SKILL.md and references/, or correct it to the export the source defines: no file its provenance cites defines it (`code/core/src/test/testing-library.ts:110`).

### GAP-374: Split-body mismatch: composeStories

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/story-types.md:181
**Export:** composeStories

**Issue:** SKILL.md:117 says the storybook/preview-api composeStories is core's renderer-agnostic composeStories(storiesImport, globalConfig, composeStoryFn?) with a required globalConfig, but references/story-types.md:181 says the symbol defined in code/renderers/react/src/portable-stories.tsx is re-exported from @storybook/react, @storybook/react-vite and storybook/preview-api, so all three would be the same function.

**Remediation:** In references/story-types.md line 181, drop `storybook/preview-api` from the list of packages that re-export the React renderer's composeStories/setProjectAnnotations, and state, as SKILL.md line 117 does, that storybook/preview-api exports core's renderer-agnostic composeStories(storiesImport, globalConfig, composeStoryFn?) defined at code/core/src/preview-api/modules/store/csf/portable-stories.ts:274, whose globalConfig is required.

### GAP-004: Missing export: AddContext

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:27
**Export:** AddContext

**Issue:** `AddContext` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AddContext` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:27` and add its signature, its purpose and a usage example.

### GAP-005: Missing export: AnchorMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:98
**Export:** AnchorMdx

**Issue:** `AnchorMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnchorMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:98` and add its signature, its purpose and a usage example.

### GAP-006: Missing type: AnchorProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Anchor.tsx:6
**Export:** AnchorProps

**Issue:** the type `AnchorProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AnchorProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Anchor.tsx:6` and list its fields or members.

### GAP-007: Missing export: CLEAR_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:5
**Export:** CLEAR_ID

**Issue:** `CLEAR_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CLEAR_ID` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:5` and add its signature, its purpose and a usage example.

### GAP-008: Missing export: CYCLIC_KEY

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:6
**Export:** CYCLIC_KEY

**Issue:** `CYCLIC_KEY` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CYCLIC_KEY` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:6` and add its signature, its purpose and a usage example.

### GAP-009: Missing export: CodeOrSourceMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:39
**Export:** CodeOrSourceMdx

**Issue:** `CodeOrSourceMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CodeOrSourceMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:39` and add its signature, its purpose and a usage example.

### GAP-010: Missing type: ColorProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/controls/index.tsx:10
**Export:** ColorProps

**Issue:** the type `ColorProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ColorProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/controls/index.tsx:10` and list its fields or members.

### GAP-011: Missing type: Component

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/types.ts:7
**Export:** Component

**Issue:** the type `Component` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Component` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/types.ts:7` and list its fields or members.

### GAP-012: Missing export: DEFAULT_VIEWPORT

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/defaults.ts:232
**Export:** DEFAULT_VIEWPORT

**Issue:** `DEFAULT_VIEWPORT` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DEFAULT_VIEWPORT` in SKILL.md: read its definition at `code/core/src/viewport/defaults.ts:232` and add its signature, its purpose and a usage example.

### GAP-013: Missing type: DescriptionType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Description.tsx:9
**Export:** DescriptionType

**Issue:** the type `DescriptionType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DescriptionType` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Description.tsx:9` and list its fields or members.

### GAP-014: Missing type: DocsContainerProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18
**Export:** DocsContainerProps

**Issue:** the type `DocsContainerProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsContainerProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18` and list its fields or members.

### GAP-015: Missing type: DocsStoryProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/types.ts:9
**Export:** DocsStoryProps

**Issue:** the type `DocsStoryProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsStoryProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/types.ts:9` and list its fields or members.

### GAP-016: Missing export: EVENT_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:4
**Export:** EVENT_ID

**Issue:** `EVENT_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `EVENT_ID` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:4` and add its signature, its purpose and a usage example.

### GAP-017: Missing type: Easing

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/theming/types.ts:61
**Export:** Easing

**Issue:** the type `Easing` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Easing` in SKILL.md: read its definition at `code/core/src/theming/types.ts:61` and list its fields or members.

### GAP-018: Missing export: ExternalDocs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26
**Export:** ExternalDocs

**Issue:** `ExternalDocs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ExternalDocs` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26` and add its signature, its purpose and a usage example.

### GAP-019: Missing export: ExternalDocsContainer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12
**Export:** ExternalDocsContainer

**Issue:** `ExternalDocsContainer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ExternalDocsContainer` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12` and add its signature, its purpose and a usage example.

### GAP-020: Missing type: ExternalDocsProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11
**Export:** ExternalDocsProps

**Issue:** the type `ExternalDocsProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ExternalDocsProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11` and list its fields or members.

### GAP-021: Missing type: GlobalStateUpdate

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:31
**Export:** GlobalStateUpdate

**Issue:** the type `GlobalStateUpdate` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `GlobalStateUpdate` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:31` and list its fields or members.

### GAP-022: Missing export: HeaderMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:215
**Export:** HeaderMdx

**Issue:** `HeaderMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HeaderMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:215` and add its signature, its purpose and a usage example.

### GAP-023: Missing export: HeadersMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:232
**Export:** HeadersMdx

**Issue:** `HeadersMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HeadersMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:232` and add its signature, its purpose and a usage example.

### GAP-024: Missing type: HeadingProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Heading.tsx:11
**Export:** HeadingProps

**Issue:** the type `HeadingProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `HeadingProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Heading.tsx:11` and list its fields or members.

### GAP-025: Missing type: HighlightTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/highlight/types.ts:3
**Export:** HighlightTypes

**Issue:** the type `HighlightTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `HighlightTypes` in SKILL.md: read its definition at `code/core/src/highlight/types.ts:3` and list its fields or members.

### GAP-026: Missing export: INITIAL_VIEWPORTS

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/defaults.ts:3
**Export:** INITIAL_VIEWPORTS

**Issue:** `INITIAL_VIEWPORTS` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `INITIAL_VIEWPORTS` in SKILL.md: read its definition at `code/core/src/viewport/defaults.ts:3` and add its signature, its purpose and a usage example.

### GAP-027: Missing export: MINIMAL_VIEWPORTS

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/defaults.ts:234
**Export:** MINIMAL_VIEWPORTS

**Issue:** `MINIMAL_VIEWPORTS` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MINIMAL_VIEWPORTS` in SKILL.md: read its definition at `code/core/src/viewport/defaults.ts:234` and add its signature, its purpose and a usage example.

### GAP-028: Missing type: Of

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/useOf.ts:11
**Export:** Of

**Issue:** the type `Of` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Of` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/useOf.ts:11` and list its fields or members.

### GAP-029: Missing export: PANEL_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:3
**Export:** PANEL_ID

**Issue:** `PANEL_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PANEL_ID` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:3` and add its signature, its purpose and a usage example.

### GAP-030: Missing export: PRIMARY_STORY

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/types.ts:3
**Export:** PRIMARY_STORY

**Issue:** `PRIMARY_STORY` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PRIMARY_STORY` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/types.ts:3` and add its signature, its purpose and a usage example.

### GAP-031: Missing type: PropDescriptor

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/store/filterArgTypes.ts:5
**Export:** PropDescriptor

**Issue:** the type `PropDescriptor` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PropDescriptor` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/filterArgTypes.ts:5` and list its fields or members.

### GAP-032: Missing type: ReactTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/renderers/react/src/types.ts:33
**Export:** ReactTypes

**Issue:** the type `ReactTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ReactTypes` in SKILL.md: read its definition at `code/renderers/react/src/types.ts:33` and list its fields or members.

### GAP-033: Missing type: Report

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/store/reporter-api.ts:1
**Export:** Report

**Issue:** the type `Report` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Report` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/reporter-api.ts:1` and list its fields or members.

### GAP-034: Missing type: ReporterAPI

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/store/reporter-api.ts:8
**Export:** ReporterAPI

**Issue:** the type `ReporterAPI` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ReporterAPI` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/reporter-api.ts:8` and list its fields or members.

### GAP-035: Missing type: SelectionStore

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17
**Export:** SelectionStore

**Issue:** the type `SelectionStore` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SelectionStore` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17` and list its fields or members.

### GAP-036: Missing export: SourceContainer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38
**Export:** SourceContainer

**Issue:** `SourceContainer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SourceContainer` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38` and add its signature, its purpose and a usage example.

### GAP-037: Missing export: SourceContext

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27
**Export:** SourceContext

**Issue:** `SourceContext` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SourceContext` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27` and add its signature, its purpose and a usage example.

### GAP-038: Missing type: SourceContextProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22
**Export:** SourceContextProps

**Issue:** the type `SourceContextProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceContextProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22` and list its fields or members.

### GAP-039: Missing type: SourceItem

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15
**Export:** SourceItem

**Issue:** the type `SourceItem` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceItem` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15` and list its fields or members.

### GAP-040: Missing type: SourceParameters

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:16
**Export:** SourceParameters

**Issue:** the type `SourceParameters` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceParameters` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Source.tsx:16` and list its fields or members.

### GAP-041: Missing type: SourceProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:28
**Export:** SourceProps

**Issue:** the type `SourceProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Source.tsx:28` and list its fields or members.

### GAP-042: Missing type: StorySources

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20
**Export:** StorySources

**Issue:** the type `StorySources` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StorySources` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20` and list its fields or members.

### GAP-043: Missing export: TOOL_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/constants.ts:4
**Export:** TOOL_ID

**Issue:** `TOOL_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TOOL_ID` in SKILL.md: read its definition at `code/core/src/viewport/constants.ts:4` and add its signature, its purpose and a usage example.

### GAP-044: Missing export: UNKNOWN_ARGS_HASH

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36
**Export:** UNKNOWN_ARGS_HASH

**Issue:** `UNKNOWN_ARGS_HASH` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `UNKNOWN_ARGS_HASH` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36` and add its signature, its purpose and a usage example.

### GAP-045: Missing type: UserEvent

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/test/testing-library.ts:119
**Export:** UserEvent

**Issue:** the type `UserEvent` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UserEvent` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:119` and list its fields or members.

### GAP-046: Missing type: UserEventObject

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/test/index.ts:15
**Export:** UserEventObject

**Issue:** the type `UserEventObject` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UserEventObject` in SKILL.md: read its definition at `code/core/src/test/index.ts:15` and list its fields or members.

### GAP-047: Missing type: View

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/preview-web/View.ts:3
**Export:** View

**Issue:** the type `View` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `View` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/View.ts:3` and list its fields or members.

### GAP-048: Missing type: Viewport

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:1
**Export:** Viewport

**Issue:** the type `Viewport` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Viewport` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:1` and list its fields or members.

### GAP-049: Missing type: ViewportGlobals

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:56
**Export:** ViewportGlobals

**Issue:** the type `ViewportGlobals` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ViewportGlobals` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:56` and list its fields or members.

### GAP-050: Missing type: ViewportMap

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:14
**Export:** ViewportMap

**Issue:** the type `ViewportMap` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ViewportMap` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:14` and list its fields or members.

### GAP-051: Missing type: ViewportTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:65
**Export:** ViewportTypes

**Issue:** the type `ViewportTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ViewportTypes` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:65` and list its fields or members.

### GAP-052: Missing export: Wrapper

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Wrapper.tsx:10
**Export:** Wrapper

**Issue:** `Wrapper` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Wrapper` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Wrapper.tsx:10` and add its signature, its purpose and a usage example.

### GAP-053: Missing export: actions

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/runtime/actions.ts:5
**Export:** actions

**Issue:** `actions` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `actions` in SKILL.md: read its definition at `code/core/src/actions/runtime/actions.ts:5` and add its signature, its purpose and a usage example.

### GAP-054: Missing export: anchorBlockIdFromId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Anchor.tsx:4
**Export:** anchorBlockIdFromId

**Issue:** `anchorBlockIdFromId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `anchorBlockIdFromId` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Anchor.tsx:4` and add its signature, its purpose and a usage example.

### GAP-055: Missing export: argsHash

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11
**Export:** argsHash

**Issue:** `argsHash` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `argsHash` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11` and add its signature, its purpose and a usage example.

### GAP-056: Missing export: assertIsFn

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:19
**Export:** assertIsFn

**Issue:** `assertIsFn` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `assertIsFn` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:19` and add its signature, its purpose and a usage example.

### GAP-057: Missing export: background

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:44
**Export:** background

**Issue:** `background` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `background` in SKILL.md: read its definition at `code/core/src/theming/base.ts:44` and add its signature, its purpose and a usage example.

### GAP-058: Missing export: color

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:1
**Export:** color

**Issue:** `color` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `color` in SKILL.md: read its definition at `code/core/src/theming/base.ts:1` and add its signature, its purpose and a usage example.

### GAP-059: Missing export: config

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/runtime/configureActions.ts:3
**Export:** config

**Issue:** `config` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `config` in SKILL.md: read its definition at `code/core/src/actions/runtime/configureActions.ts:3` and add its signature, its purpose and a usage example.

### GAP-060: Missing export: createPlaywrightTest

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:319
**Export:** createPlaywrightTest

**Issue:** `createPlaywrightTest` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `createPlaywrightTest` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:319` and add its signature, its purpose and a usage example.

### GAP-061: Missing export: emitTransformCode

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15
**Export:** emitTransformCode

**Issue:** `emitTransformCode` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `emitTransformCode` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15` and add its signature, its purpose and a usage example.

### GAP-062: Missing export: ensure

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/ensure.ts:10
**Export:** ensure

**Issue:** `ensure` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ensure` in SKILL.md: read its definition at `code/core/src/theming/ensure.ts:10` and add its signature, its purpose and a usage example.

### GAP-063: Missing export: extractTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Title.tsx:24
**Export:** extractTitle

**Issue:** `extractTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractTitle` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Title.tsx:24` and add its signature, its purpose and a usage example.

### GAP-064: Missing export: getCsfFactoryAnnotations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10
**Export:** getCsfFactoryAnnotations

**Issue:** `getCsfFactoryAnnotations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getCsfFactoryAnnotations` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10` and add its signature, its purpose and a usage example.

### GAP-065: Missing export: getStoryId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:62
**Export:** getStoryId

**Issue:** `getStoryId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getStoryId` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Story.tsx:62` and add its signature, its purpose and a usage example.

### GAP-066: Missing export: getStoryProps

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:75
**Export:** getStoryProps

**Issue:** `getStoryProps` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getStoryProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Story.tsx:75` and add its signature, its purpose and a usage example.

### GAP-067: Missing export: pauseAnimations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18
**Export:** pauseAnimations

**Issue:** `pauseAnimations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `pauseAnimations` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18` and add its signature, its purpose and a usage example.

### GAP-068: Missing export: responsiveViewport

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/responsiveViewport.tsx:4
**Export:** responsiveViewport

**Issue:** `responsiveViewport` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `responsiveViewport` in SKILL.md: read its definition at `code/core/src/viewport/responsiveViewport.tsx:4` and add its signature, its purpose and a usage example.

### GAP-069: Missing export: simulateDOMContentLoaded

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31
**Export:** simulateDOMContentLoaded

**Issue:** `simulateDOMContentLoaded` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `simulateDOMContentLoaded` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31` and add its signature, its purpose and a usage example.

### GAP-070: Missing export: simulatePageLoad

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83
**Export:** simulatePageLoad

**Issue:** `simulatePageLoad` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `simulatePageLoad` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83` and add its signature, its purpose and a usage example.

### GAP-071: Missing export: slugs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Heading.tsx:15
**Export:** slugs

**Issue:** `slugs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `slugs` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Heading.tsx:15` and add its signature, its purpose and a usage example.

### GAP-072: Missing export: storybookTest

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/vitest/src/vitest-plugin/index.ts:164
**Export:** storybookTest

**Issue:** `storybookTest` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `storybookTest` in SKILL.md: read its definition at `code/addons/vitest/src/vitest-plugin/index.ts:164` and add its signature, its purpose and a usage example.

### GAP-073: Missing export: tokens

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:104
**Export:** tokens

**Issue:** `tokens` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `tokens` in SKILL.md: read its definition at `code/core/src/theming/base.ts:104` and add its signature, its purpose and a usage example.

### GAP-074: Missing export: typography

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:59
**Export:** typography

**Issue:** `typography` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `typography` in SKILL.md: read its definition at `code/core/src/theming/base.ts:59` and add its signature, its purpose and a usage example.

### GAP-075: Missing export: uninstrumentedUserEvent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:121
**Export:** uninstrumentedUserEvent

**Issue:** `uninstrumentedUserEvent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `uninstrumentedUserEvent` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:121` and add its signature, its purpose and a usage example.

### GAP-076: Missing export: useSourceProps

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:101
**Export:** useSourceProps

**Issue:** `useSourceProps` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useSourceProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Source.tsx:101` and add its signature, its purpose and a usage example.

### GAP-077: Missing export: waitForAnimations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54
**Export:** waitForAnimations

**Issue:** `waitForAnimations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `waitForAnimations` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54` and add its signature, its purpose and a usage example.

### GAP-078: Stale documentation: A

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:204
**Export:** A

**Issue:** SKILL.md documents `A`, which the enumerated source API surface lacks

**Remediation:** Check `A` against the source and update or remove its documentation at SKILL.md:204: the enumerated source surface does not export it.

### GAP-082: Stale documentation: ActionBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** ActionBar

**Issue:** SKILL.md documents `ActionBar`, which the enumerated source API surface lacks

**Remediation:** Check `ActionBar` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-083: Stale documentation: ActionList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** ActionList

**Issue:** SKILL.md documents `ActionList`, which the enumerated source API surface lacks

**Remediation:** Check `ActionList` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-084: Stale documentation: AddonPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** AddonPanel

**Issue:** SKILL.md documents `AddonPanel`, which the enumerated source API surface lacks

**Remediation:** Check `AddonPanel` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-085: Stale documentation: Args

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:131
**Export:** Args

**Issue:** SKILL.md documents `Args`, which the enumerated source API surface lacks

**Remediation:** Check `Args` against the source and update or remove its documentation at SKILL.md:131: the enumerated source surface does not export it.

### GAP-087: Stale documentation: Badge

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Badge

**Issue:** SKILL.md documents `Badge`, which the enumerated source API surface lacks

**Remediation:** Check `Badge` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-088: Stale documentation: Bar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** Bar

**Issue:** SKILL.md documents `Bar`, which the enumerated source API surface lacks

**Remediation:** Check `Bar` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-090: Stale documentation: Blockquote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Blockquote

**Issue:** SKILL.md documents `Blockquote`, which the enumerated source API surface lacks

**Remediation:** Check `Blockquote` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-091: Stale documentation: Button

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:44
**Export:** Button

**Issue:** SKILL.md documents `Button`, which the enumerated source API surface lacks

**Remediation:** Check `Button` against the source and update or remove its documentation at SKILL.md:44: the enumerated source surface does not export it.

### GAP-092: Stale documentation: CHANNEL_CREATED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** CHANNEL_CREATED

**Issue:** SKILL.md documents `CHANNEL_CREATED`, which the enumerated source API surface lacks

**Remediation:** Check `CHANNEL_CREATED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-095: Stale documentation: CSSObject

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:178
**Export:** CSSObject

**Issue:** SKILL.md documents `CSSObject`, which the enumerated source API surface lacks

**Remediation:** Check `CSSObject` against the source and update or remove its documentation at references/core-api.md:178: the enumerated source surface does not export it.

### GAP-096: Stale documentation: CacheProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:171
**Export:** CacheProvider

**Issue:** SKILL.md documents `CacheProvider`, which the enumerated source API surface lacks

**Remediation:** Check `CacheProvider` against the source and update or remove its documentation at references/core-api.md:171: the enumerated source surface does not export it.

### GAP-099: Stale documentation: Card

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** Card

**Issue:** SKILL.md documents `Card`, which the enumerated source API surface lacks

**Remediation:** Check `Card` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-101: Stale documentation: Channel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:127
**Export:** Channel

**Issue:** SKILL.md documents `Channel`, which the enumerated source API surface lacks

**Remediation:** Check `Channel` against the source and update or remove its documentation at references/core-api.md:127: the enumerated source surface does not export it.

### GAP-102: Stale documentation: CheckboxControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:192
**Export:** CheckboxControl

**Issue:** SKILL.md documents `CheckboxControl`, which the enumerated source API surface lacks

**Remediation:** Check `CheckboxControl` against the source and update or remove its documentation at references/doc-blocks.md:192: the enumerated source surface does not export it.

### GAP-103: Stale documentation: ClassNames

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:171
**Export:** ClassNames

**Issue:** SKILL.md documents `ClassNames`, which the enumerated source API surface lacks

**Remediation:** Check `ClassNames` against the source and update or remove its documentation at references/core-api.md:171: the enumerated source surface does not export it.

### GAP-104: Stale documentation: Code

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Code

**Issue:** SKILL.md documents `Code`, which the enumerated source API surface lacks

**Remediation:** Check `Code` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-105: Stale documentation: Collapsible

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** Collapsible

**Issue:** SKILL.md documents `Collapsible`, which the enumerated source API surface lacks

**Remediation:** Check `Collapsible` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-106: Stale documentation: ColorControlProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:173
**Export:** ColorControlProps

**Issue:** SKILL.md documents `ColorControlProps`, which the enumerated source API surface lacks

**Remediation:** Check `ColorControlProps` against the source and update or remove its documentation at references/doc-blocks.md:173: the enumerated source surface does not export it.

### GAP-110: Stale documentation: ConfigFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** ConfigFile

**Issue:** SKILL.md documents `ConfigFile`, which the enumerated source API surface lacks

**Remediation:** Check `ConfigFile` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-111: Stale documentation: CsfFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** CsfFile

**Issue:** SKILL.md documents `CsfFile`, which the enumerated source API surface lacks

**Remediation:** Check `CsfFile` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-112: Stale documentation: DL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** DL

**Issue:** SKILL.md documents `DL`, which the enumerated source API surface lacks

**Remediation:** Check `DL` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-115: Stale documentation: Div

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Div

**Issue:** SKILL.md documents `Div`, which the enumerated source API surface lacks

**Remediation:** Check `Div` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-118: Stale documentation: ErrorFormatter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** ErrorFormatter

**Issue:** SKILL.md documents `ErrorFormatter`, which the enumerated source API surface lacks

**Remediation:** Check `ErrorFormatter` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-120: Stale documentation: FlexBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** FlexBar

**Issue:** SKILL.md documents `FlexBar`, which the enumerated source API surface lacks

**Remediation:** Check `FlexBar` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-121: Stale documentation: Form

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** Form

**Issue:** SKILL.md documents `Form`, which the enumerated source API surface lacks

**Remediation:** Check `Form` against the source and update or remove its documentation at references/core-api.md:313: the enumerated source surface does not export it.

### GAP-123: Stale documentation: GLOBALS_UPDATED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** GLOBALS_UPDATED

**Issue:** SKILL.md documents `GLOBALS_UPDATED`, which the enumerated source API surface lacks

**Remediation:** Check `GLOBALS_UPDATED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-124: Stale documentation: Global

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:56
**Export:** Global

**Issue:** SKILL.md documents `Global`, which the enumerated source API surface lacks

**Remediation:** Check `Global` against the source and update or remove its documentation at references/core-api.md:56: the enumerated source surface does not export it.

### GAP-127: Stale documentation: H1

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** H1

**Issue:** SKILL.md documents `H1`, which the enumerated source API surface lacks

**Remediation:** Check `H1` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-128: Stale documentation: H6

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** H6

**Issue:** SKILL.md documents `H6`, which the enumerated source API surface lacks

**Remediation:** Check `H6` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-129: Stale documentation: HR

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** HR

**Issue:** SKILL.md documents `HR`, which the enumerated source API surface lacks

**Remediation:** Check `HR` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-131: Stale documentation: IconButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** IconButton

**Issue:** SKILL.md documents `IconButton`, which the enumerated source API surface lacks

**Remediation:** Check `IconButton` against the source and update or remove its documentation at references/core-api.md:313: the enumerated source surface does not export it.

### GAP-136: Stale documentation: Keyframes

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:178
**Export:** Keyframes

**Issue:** SKILL.md documents `Keyframes`, which the enumerated source API surface lacks

**Remediation:** Check `Keyframes` against the source and update or remove its documentation at references/core-api.md:178: the enumerated source surface does not export it.

### GAP-137: Stale documentation: LI

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** LI

**Issue:** SKILL.md documents `LI`, which the enumerated source API surface lacks

**Remediation:** Check `LI` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-142: Stale documentation: MaybeMocked

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:62
**Export:** MaybeMocked

**Issue:** SKILL.md documents `MaybeMocked`, which the enumerated source API surface lacks

**Remediation:** Check `MaybeMocked` against the source and update or remove its documentation at references/core-api.md:62: the enumerated source surface does not export it.

### GAP-148: Stale documentation: Mock

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:135
**Export:** Mock

**Issue:** SKILL.md documents `Mock`, which the enumerated source API surface lacks

**Remediation:** Check `Mock` against the source and update or remove its documentation at SKILL.md:135: the enumerated source surface does not export it.

### GAP-149: Stale documentation: MockInstance

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:62
**Export:** MockInstance

**Issue:** SKILL.md documents `MockInstance`, which the enumerated source API surface lacks

**Remediation:** Check `MockInstance` against the source and update or remove its documentation at references/core-api.md:62: the enumerated source surface does not export it.

### GAP-151: Stale documentation: Modal

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** Modal

**Issue:** SKILL.md documents `Modal`, which the enumerated source API surface lacks

**Remediation:** Check `Modal` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-156: Stale documentation: NodePath

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** NodePath

**Issue:** SKILL.md documents `NodePath`, which the enumerated source API surface lacks

**Remediation:** Check `NodePath` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-161: Stale documentation: OL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** OL

**Issue:** SKILL.md documents `OL`, which the enumerated source API surface lacks

**Remediation:** Check `OL` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-162: Stale documentation: P

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** P

**Issue:** SKILL.md documents `P`, which the enumerated source API surface lacks

**Remediation:** Check `P` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-163: Stale documentation: PREVIEW_INITIALIZED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** PREVIEW_INITIALIZED

**Issue:** SKILL.md documents `PREVIEW_INITIALIZED`, which the enumerated source API surface lacks

**Remediation:** Check `PREVIEW_INITIALIZED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-164: Stale documentation: Parameters

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:11
**Export:** Parameters

**Issue:** SKILL.md documents `Parameters`, which the enumerated source API surface lacks

**Remediation:** Check `Parameters` against the source and update or remove its documentation at references/core-api.md:11: the enumerated source surface does not export it.

### GAP-165: Stale documentation: Placeholder

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** Placeholder

**Issue:** SKILL.md documents `Placeholder`, which the enumerated source API surface lacks

**Remediation:** Check `Placeholder` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-166: Stale documentation: PlayFunction

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:259
**Export:** PlayFunction

**Issue:** SKILL.md documents `PlayFunction`, which the enumerated source API surface lacks

**Remediation:** Check `PlayFunction` against the source and update or remove its documentation at references/core-api.md:259: the enumerated source surface does not export it.

### GAP-167: Stale documentation: Popover

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** Popover

**Issue:** SKILL.md documents `Popover`, which the enumerated source API surface lacks

**Remediation:** Check `Popover` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-168: Stale documentation: PopoverProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** PopoverProvider

**Issue:** SKILL.md documents `PopoverProvider`, which the enumerated source API surface lacks

**Remediation:** Check `PopoverProvider` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-169: Stale documentation: PostMessageTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:330
**Export:** PostMessageTransport

**Issue:** SKILL.md documents `PostMessageTransport`, which the enumerated source API surface lacks

**Remediation:** Check `PostMessageTransport` against the source and update or remove its documentation at references/core-api.md:330: the enumerated source surface does not export it.

### GAP-170: Stale documentation: Pre

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Pre

**Issue:** SKILL.md documents `Pre`, which the enumerated source API surface lacks

**Remediation:** Check `Pre` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-172: Stale documentation: ProjectAnnotations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:134
**Export:** ProjectAnnotations

**Issue:** SKILL.md documents `ProjectAnnotations`, which the enumerated source API surface lacks

**Remediation:** Check `ProjectAnnotations` against the source and update or remove its documentation at SKILL.md:134: the enumerated source surface does not export it.

### GAP-173: Stale documentation: RadioControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:192
**Export:** RadioControl

**Issue:** SKILL.md documents `RadioControl`, which the enumerated source API surface lacks

**Remediation:** Check `RadioControl` against the source and update or remove its documentation at references/doc-blocks.md:192: the enumerated source surface does not export it.

### GAP-178: Stale documentation: SELECT_STORY

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** SELECT_STORY

**Issue:** SKILL.md documents `SELECT_STORY`, which the enumerated source API surface lacks

**Remediation:** Check `SELECT_STORY` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-180: Stale documentation: STORY_PREPARED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** STORY_PREPARED

**Issue:** SKILL.md documents `STORY_PREPARED`, which the enumerated source API surface lacks

**Remediation:** Check `STORY_PREPARED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-181: Stale documentation: STORY_RENDERED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** STORY_RENDERED

**Issue:** SKILL.md documents `STORY_RENDERED`, which the enumerated source API surface lacks

**Remediation:** Check `STORY_RENDERED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-182: Stale documentation: STORY_SPECIFIED

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** STORY_SPECIFIED

**Issue:** SKILL.md documents `STORY_SPECIFIED`, which the enumerated source API surface lacks

**Remediation:** Check `STORY_SPECIFIED` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-183: Stale documentation: ScrollArea

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** ScrollArea

**Issue:** SKILL.md documents `ScrollArea`, which the enumerated source API surface lacks

**Remediation:** Check `ScrollArea` against the source and update or remove its documentation at references/core-api.md:314: the enumerated source surface does not export it.

### GAP-184: Stale documentation: Select

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** Select

**Issue:** SKILL.md documents `Select`, which the enumerated source API surface lacks

**Remediation:** Check `Select` against the source and update or remove its documentation at references/core-api.md:313: the enumerated source surface does not export it.

### GAP-185: Stale documentation: SelectControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:192
**Export:** SelectControl

**Issue:** SKILL.md documents `SelectControl`, which the enumerated source API surface lacks

**Remediation:** Check `SelectControl` against the source and update or remove its documentation at references/doc-blocks.md:192: the enumerated source surface does not export it.

### GAP-187: Stale documentation: Spaced

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** Spaced

**Issue:** SKILL.md documents `Spaced`, which the enumerated source API surface lacks

**Remediation:** Check `Spaced` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-188: Stale documentation: Span

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Span

**Issue:** SKILL.md documents `Span`, which the enumerated source API surface lacks

**Remediation:** Check `Span` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-199: Stale documentation: StoryIndexGenerator

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:340
**Export:** StoryIndexGenerator

**Issue:** SKILL.md documents `StoryIndexGenerator`, which the enumerated source API surface lacks

**Remediation:** Check `StoryIndexGenerator` against the source and update or remove its documentation at references/core-api.md:340: the enumerated source surface does not export it.

### GAP-204: Stale documentation: StorybookIcon

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:319
**Export:** StorybookIcon

**Issue:** SKILL.md documents `StorybookIcon`, which the enumerated source API surface lacks

**Remediation:** Check `StorybookIcon` against the source and update or remove its documentation at references/core-api.md:319: the enumerated source surface does not export it.

### GAP-205: Stale documentation: StorybookLogo

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:319
**Export:** StorybookLogo

**Issue:** SKILL.md documents `StorybookLogo`, which the enumerated source API surface lacks

**Remediation:** Check `StorybookLogo` against the source and update or remove its documentation at references/core-api.md:319: the enumerated source surface does not export it.

### GAP-209: Stale documentation: SyntaxHighlighter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** SyntaxHighlighter

**Issue:** SKILL.md documents `SyntaxHighlighter`, which the enumerated source API surface lacks

**Remediation:** Check `SyntaxHighlighter` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-211: Stale documentation: TabBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabBar

**Issue:** SKILL.md documents `TabBar`, which the enumerated source API surface lacks

**Remediation:** Check `TabBar` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-212: Stale documentation: TabButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabButton

**Issue:** SKILL.md documents `TabButton`, which the enumerated source API surface lacks

**Remediation:** Check `TabButton` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-213: Stale documentation: TabList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabList

**Issue:** SKILL.md documents `TabList`, which the enumerated source API surface lacks

**Remediation:** Check `TabList` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-214: Stale documentation: TabPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabPanel

**Issue:** SKILL.md documents `TabPanel`, which the enumerated source API surface lacks

**Remediation:** Check `TabPanel` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-215: Stale documentation: TabWrapper

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabWrapper

**Issue:** SKILL.md documents `TabWrapper`, which the enumerated source API surface lacks

**Remediation:** Check `TabWrapper` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-217: Stale documentation: Tabs

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** Tabs

**Issue:** SKILL.md documents `Tabs`, which the enumerated source API surface lacks

**Remediation:** Check `Tabs` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-218: Stale documentation: TabsView

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TabsView

**Issue:** SKILL.md documents `TabsView`, which the enumerated source API surface lacks

**Remediation:** Check `TabsView` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-222: Stale documentation: ThemeProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/addons.md:112
**Export:** ThemeProvider

**Issue:** SKILL.md documents `ThemeProvider`, which the enumerated source API surface lacks

**Remediation:** Check `ThemeProvider` against the source and update or remove its documentation at references/addons.md:112: the enumerated source surface does not export it.

### GAP-224: Stale documentation: ToggleButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** ToggleButton

**Issue:** SKILL.md documents `ToggleButton`, which the enumerated source API surface lacks

**Remediation:** Check `ToggleButton` against the source and update or remove its documentation at references/core-api.md:313: the enumerated source surface does not export it.

### GAP-225: Stale documentation: Toolbar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** Toolbar

**Issue:** SKILL.md documents `Toolbar`, which the enumerated source API surface lacks

**Remediation:** Check `Toolbar` against the source and update or remove its documentation at references/core-api.md:317: the enumerated source surface does not export it.

### GAP-226: Stale documentation: Tooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** Tooltip

**Issue:** SKILL.md documents `Tooltip`, which the enumerated source API surface lacks

**Remediation:** Check `Tooltip` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-227: Stale documentation: TooltipLinkList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** TooltipLinkList

**Issue:** SKILL.md documents `TooltipLinkList`, which the enumerated source API surface lacks

**Remediation:** Check `TooltipLinkList` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-228: Stale documentation: TooltipNote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** TooltipNote

**Issue:** SKILL.md documents `TooltipNote`, which the enumerated source API surface lacks

**Remediation:** Check `TooltipNote` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-231: Stale documentation: UL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** UL

**Issue:** SKILL.md documents `UL`, which the enumerated source API surface lacks

**Remediation:** Check `UL` against the source and update or remove its documentation at references/core-api.md:312: the enumerated source surface does not export it.

### GAP-232: Stale documentation: UPDATE_STORY_ARGS

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:331
**Export:** UPDATE_STORY_ARGS

**Issue:** SKILL.md documents `UPDATE_STORY_ARGS`, which the enumerated source API surface lacks

**Remediation:** Check `UPDATE_STORY_ARGS` against the source and update or remove its documentation at references/core-api.md:331: the enumerated source surface does not export it.

### GAP-233: Stale documentation: ViewMode

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:270
**Export:** ViewMode

**Issue:** SKILL.md documents `ViewMode`, which the enumerated source API surface lacks

**Remediation:** Check `ViewMode` against the source and update or remove its documentation at references/core-api.md:270: the enumerated source surface does not export it.

### GAP-235: Stale documentation: WebsocketTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:330
**Export:** WebsocketTransport

**Issue:** SKILL.md documents `WebsocketTransport`, which the enumerated source API surface lacks

**Remediation:** Check `WebsocketTransport` against the source and update or remove its documentation at references/core-api.md:330: the enumerated source surface does not export it.

### GAP-236: Stale documentation: WithTooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** WithTooltip

**Issue:** SKILL.md documents `WithTooltip`, which the enumerated source API surface lacks

**Remediation:** Check `WithTooltip` against the source and update or remove its documentation at references/core-api.md:316: the enumerated source surface does not export it.

### GAP-237: Stale documentation: Zoom

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** Zoom

**Issue:** SKILL.md documents `Zoom`, which the enumerated source API surface lacks

**Remediation:** Check `Zoom` against the source and update or remove its documentation at references/core-api.md:318: the enumerated source surface does not export it.

### GAP-239: Stale documentation: addToGlobalContext

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** addToGlobalContext

**Issue:** SKILL.md documents `addToGlobalContext`, which the enumerated source API surface lacks

**Remediation:** Check `addToGlobalContext` against the source and update or remove its documentation at references/core-api.md:336: the enumerated source surface does not export it.

### GAP-240: Stale documentation: addons

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:9
**Export:** addons

**Issue:** SKILL.md documents `addons`, which the enumerated source API surface lacks

**Remediation:** Check `addons` against the source and update or remove its documentation at SKILL.md:9: the enumerated source surface does not export it.

### GAP-242: Stale documentation: automock

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:339
**Export:** automock

**Issue:** SKILL.md documents `automock`, which the enumerated source API surface lacks

**Remediation:** Check `automock` against the source and update or remove its documentation at references/core-api.md:339: the enumerated source surface does not export it.

### GAP-247: Stale documentation: colors

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** colors

**Issue:** SKILL.md documents `colors`, which the enumerated source API surface lacks

**Remediation:** Check `colors` against the source and update or remove its documentation at references/core-api.md:335: the enumerated source surface does not export it.

### GAP-249: Stale documentation: componentTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** componentTransform

**Issue:** SKILL.md documents `componentTransform`, which the enumerated source API surface lacks

**Remediation:** Check `componentTransform` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-250: Stale documentation: core

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:25
**Export:** core

**Issue:** SKILL.md documents `core`, which the enumerated source API surface lacks

**Remediation:** Check `core` against the source and update or remove its documentation at SKILL.md:25: the enumerated source surface does not export it.

### GAP-251: Stale documentation: corePresets

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/framework-config.md:159
**Export:** corePresets

**Issue:** SKILL.md documents `corePresets`, which the enumerated source API surface lacks

**Remediation:** Check `corePresets` against the source and update or remove its documentation at references/framework-config.md:159: the enumerated source surface does not export it.

### GAP-252: Stale documentation: createBrowserChannel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:330
**Export:** createBrowserChannel

**Issue:** SKILL.md documents `createBrowserChannel`, which the enumerated source API surface lacks

**Remediation:** Check `createBrowserChannel` against the source and update or remove its documentation at references/core-api.md:330: the enumerated source surface does not export it.

### GAP-254: Stale documentation: createTest

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/framework-config.md:143
**Export:** createTest

**Issue:** SKILL.md documents `createTest`, which the enumerated source API surface lacks

**Remediation:** Check `createTest` against the source and update or remove its documentation at references/framework-config.md:143: the enumerated source surface does not export it.

### GAP-256: Stale documentation: decorators

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:35
**Export:** decorators

**Issue:** SKILL.md documents `decorators`, which the enumerated source API surface lacks

**Remediation:** Check `decorators` against the source and update or remove its documentation at SKILL.md:35: the enumerated source surface does not export it.

### GAP-259: Stale documentation: deprecate

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:334
**Export:** deprecate

**Issue:** SKILL.md documents `deprecate`, which the enumerated source API surface lacks

**Remediation:** Check `deprecate` against the source and update or remove its documentation at references/core-api.md:334: the enumerated source surface does not export it.

### GAP-260: Stale documentation: enrichCsf

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** enrichCsf

**Issue:** SKILL.md documents `enrichCsf`, which the enumerated source API surface lacks

**Remediation:** Check `enrichCsf` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-262: Stale documentation: expect

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:46
**Export:** expect

**Issue:** SKILL.md documents `expect`, which the enumerated source API surface lacks

**Remediation:** Check `expect` against the source and update or remove its documentation at SKILL.md:46: the enumerated source surface does not export it.

### GAP-266: Stale documentation: experimental_loadStorybook

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:340
**Export:** experimental_loadStorybook

**Issue:** SKILL.md documents `experimental_loadStorybook`, which the enumerated source API surface lacks

**Remediation:** Check `experimental_loadStorybook` against the source and update or remove its documentation at references/core-api.md:340: the enumerated source surface does not export it.

### GAP-267: Stale documentation: extract

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/addons.md:125
**Export:** extract

**Issue:** SKILL.md documents `extract`, which the enumerated source API surface lacks

**Remediation:** Check `extract` against the source and update or remove its documentation at references/addons.md:125: the enumerated source surface does not export it.

### GAP-268: Stale documentation: findByRole

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:108
**Export:** findByRole

**Issue:** SKILL.md documents `findByRole`, which the enumerated source API surface lacks

**Remediation:** Check `findByRole` against the source and update or remove its documentation at SKILL.md:108: the enumerated source surface does not export it.

### GAP-270: Stale documentation: generate

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:14
**Export:** generate

**Issue:** SKILL.md documents `generate`, which the enumerated source API surface lacks

**Remediation:** Check `generate` against the source and update or remove its documentation at SKILL.md:14: the enumerated source surface does not export it.

### GAP-271: Stale documentation: generateStoryFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:340
**Export:** generateStoryFile

**Issue:** SKILL.md documents `generateStoryFile`, which the enumerated source API surface lacks

**Remediation:** Check `generateStoryFile` against the source and update or remove its documentation at references/core-api.md:340: the enumerated source surface does not export it.

### GAP-272: Stale documentation: getByRole

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:65
**Export:** getByRole

**Issue:** SKILL.md documents `getByRole`, which the enumerated source API surface lacks

**Remediation:** Check `getByRole` against the source and update or remove its documentation at SKILL.md:65: the enumerated source surface does not export it.

### GAP-275: Stale documentation: getSessionId

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** getSessionId

**Issue:** SKILL.md documents `getSessionId`, which the enumerated source API surface lacks

**Remediation:** Check `getSessionId` against the source and update or remove its documentation at references/core-api.md:336: the enumerated source surface does not export it.

### GAP-277: Stale documentation: getStorySortParameter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** getStorySortParameter

**Issue:** SKILL.md documents `getStorySortParameter`, which the enumerated source API surface lacks

**Remediation:** Check `getStorySortParameter` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-279: Stale documentation: getStorybookMetadata

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** getStorybookMetadata

**Issue:** SKILL.md documents `getStorybookMetadata`, which the enumerated source API surface lacks

**Remediation:** Check `getStorybookMetadata` against the source and update or remove its documentation at references/core-api.md:336: the enumerated source surface does not export it.

### GAP-283: Stale documentation: isMockFunction

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:136
**Export:** isMockFunction

**Issue:** SKILL.md documents `isMockFunction`, which the enumerated source API surface lacks

**Remediation:** Check `isMockFunction` against the source and update or remove its documentation at references/core-api.md:136: the enumerated source surface does not export it.

### GAP-285: Stale documentation: jsx

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:170
**Export:** jsx

**Issue:** SKILL.md documents `jsx`, which the enumerated source API surface lacks

**Remediation:** Check `jsx` against the source and update or remove its documentation at references/core-api.md:170: the enumerated source surface does not export it.

### GAP-288: Stale documentation: logTracker

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** logTracker

**Issue:** SKILL.md documents `logTracker`, which the enumerated source API surface lacks

**Remediation:** Check `logTracker` against the source and update or remove its documentation at references/core-api.md:335: the enumerated source surface does not export it.

### GAP-289: Stale documentation: logger

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:35
**Export:** logger

**Issue:** SKILL.md documents `logger`, which the enumerated source API surface lacks

**Remediation:** Check `logger` against the source and update or remove its documentation at references/core-api.md:35: the enumerated source surface does not export it.

### GAP-291: Stale documentation: mount

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/csf3-patterns.md:10
**Export:** mount

**Issue:** SKILL.md documents `mount`, which the enumerated source API surface lacks

**Remediation:** Check `mount` against the source and update or remove its documentation at references/csf3-patterns.md:10: the enumerated source surface does not export it.

### GAP-293: Stale documentation: once

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:117
**Export:** once

**Issue:** SKILL.md documents `once`, which the enumerated source API surface lacks

**Remediation:** Check `once` against the source and update or remove its documentation at SKILL.md:117: the enumerated source surface does not export it.

### GAP-296: Stale documentation: parser

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** parser

**Issue:** SKILL.md documents `parser`, which the enumerated source API surface lacks

**Remediation:** Check `parser` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-298: Stale documentation: prompt

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** prompt

**Issue:** SKILL.md documents `prompt`, which the enumerated source API surface lacks

**Remediation:** Check `prompt` against the source and update or remove its documentation at references/core-api.md:335: the enumerated source surface does not export it.

### GAP-299: Stale documentation: queryByRole

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:60
**Export:** queryByRole

**Issue:** SKILL.md documents `queryByRole`, which the enumerated source API surface lacks

**Remediation:** Check `queryByRole` against the source and update or remove its documentation at references/core-api.md:60: the enumerated source surface does not export it.

### GAP-300: Stale documentation: recast

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** recast

**Issue:** SKILL.md documents `recast`, which the enumerated source API surface lacks

**Remediation:** Check `recast` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-301: Stale documentation: redirect

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:339
**Export:** redirect

**Issue:** SKILL.md documents `redirect`, which the enumerated source API surface lacks

**Remediation:** Check `redirect` against the source and update or remove its documentation at references/core-api.md:339: the enumerated source surface does not export it.

### GAP-302: Stale documentation: resolve

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:339
**Export:** resolve

**Issue:** SKILL.md documents `resolve`, which the enumerated source API surface lacks

**Remediation:** Check `resolve` against the source and update or remove its documentation at references/core-api.md:339: the enumerated source surface does not export it.

### GAP-303: Stale documentation: runtime

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:14
**Export:** runtime

**Issue:** SKILL.md documents `runtime`, which the enumerated source API surface lacks

**Remediation:** Check `runtime` against the source and update or remove its documentation at references/core-api.md:14: the enumerated source surface does not export it.

### GAP-310: Stale documentation: telemetry

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** telemetry

**Issue:** SKILL.md documents `telemetry`, which the enumerated source API surface lacks

**Remediation:** Check `telemetry` against the source and update or remove its documentation at references/core-api.md:336: the enumerated source surface does not export it.

### GAP-313: Stale documentation: transformSync

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** transformSync

**Issue:** SKILL.md documents `transformSync`, which the enumerated source API surface lacks

**Remediation:** Check `transformSync` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-314: Stale documentation: traverse

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:342
**Export:** traverse

**Issue:** SKILL.md documents `traverse`, which the enumerated source API surface lacks

**Remediation:** Check `traverse` against the source and update or remove its documentation at references/core-api.md:342: the enumerated source surface does not export it.

### GAP-315: Stale documentation: types

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:96
**Export:** types

**Issue:** SKILL.md documents `types`, which the enumerated source API surface lacks

**Remediation:** Check `types` against the source and update or remove its documentation at SKILL.md:96: the enumerated source surface does not export it.

### GAP-316: Stale documentation: useStatusStore

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:153
**Export:** useStatusStore

**Issue:** SKILL.md documents `useStatusStore`, which the enumerated source API surface lacks

**Remediation:** Check `useStatusStore` against the source and update or remove its documentation at references/core-api.md:153: the enumerated source surface does not export it.

### GAP-317: Stale documentation: useTabsState

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** useTabsState

**Issue:** SKILL.md documents `useTabsState`, which the enumerated source API surface lacks

**Remediation:** Check `useTabsState` against the source and update or remove its documentation at references/core-api.md:315: the enumerated source surface does not export it.

### GAP-318: Stale documentation: useTestProviderStore

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:154
**Export:** useTestProviderStore

**Issue:** SKILL.md documents `useTestProviderStore`, which the enumerated source API surface lacks

**Remediation:** Check `useTestProviderStore` against the source and update or remove its documentation at references/core-api.md:154: the enumerated source surface does not export it.

### GAP-319: Stale documentation: useTheme

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:20
**Export:** useTheme

**Issue:** SKILL.md documents `useTheme`, which the enumerated source API surface lacks

**Remediation:** Check `useTheme` against the source and update or remove its documentation at references/core-api.md:20: the enumerated source surface does not export it.

### GAP-320: Stale documentation: useUniversalStore

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:151
**Export:** useUniversalStore

**Issue:** SKILL.md documents `useUniversalStore`, which the enumerated source API surface lacks

**Remediation:** Check `useUniversalStore` against the source and update or remove its documentation at references/core-api.md:151: the enumerated source surface does not export it.

### GAP-322: Stale documentation: viteFinal

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/framework-config.md:27
**Export:** viteFinal

**Issue:** SKILL.md documents `viteFinal`, which the enumerated source API surface lacks

**Remediation:** Check `viteFinal` against the source and update or remove its documentation at references/framework-config.md:27: the enumerated source surface does not export it.

### GAP-323: Stale documentation: vitestTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:337
**Export:** vitestTransform

**Issue:** SKILL.md documents `vitestTransform`, which the enumerated source API surface lacks

**Remediation:** Check `vitestTransform` against the source and update or remove its documentation at references/core-api.md:337: the enumerated source surface does not export it.

### GAP-325: Stale documentation: withTheme

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:169
**Export:** withTheme

**Issue:** SKILL.md documents `withTheme`, which the enumerated source API surface lacks

**Remediation:** Check `withTheme` against the source and update or remove its documentation at references/core-api.md:169: the enumerated source surface does not export it.

### GAP-327: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_public_api=1335, exports[].length=83 → 94% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json`; update-skill applies it as a metadata update.

### GAP-079: Documented extra: ADDON_ID

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:11
**Export:** ADDON_ID

**Issue:** `references/addons.md:193` documents `ADDON_ID`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ADDON_ID` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:11` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-080: Documented extra: API_EventMap

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:318
**Export:** API_EventMap

**Issue:** `references/story-types.md:248` documents `API_EventMap`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `API_EventMap` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:318` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-081: Documented extra: API_KeyCollection

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/modules/shortcuts.ts:99
**Export:** API_KeyCollection

**Issue:** `references/story-types.md:249` documents `API_KeyCollection`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `API_KeyCollection` is a documented extra, a name the source still declares at `code/core/src/manager-api/modules/shortcuts.ts:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-086: Documented extra: BabelFile

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf-tools/CsfFile.ts:31
**Export:** BabelFile

**Issue:** `references/core-api.md:342` documents `BabelFile`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BabelFile` is a documented extra, a name the source still declares at `code/core/src/csf-tools/CsfFile.ts:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-089: Documented extra: BaseProjectAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/csf.ts:38
**Export:** BaseProjectAnnotations

**Issue:** `references/core-api.md:262` documents `BaseProjectAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BaseProjectAnnotations` is a documented extra, a name the source still declares at `code/core/src/types/modules/csf.ts:38` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-093: Documented extra: COMPONENT_TESTING_PANEL_ID

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:5
**Export:** COMPONENT_TESTING_PANEL_ID

**Issue:** `references/addons.md:196` documents `COMPONENT_TESTING_PANEL_ID`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `COMPONENT_TESTING_PANEL_ID` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-094: Documented extra: CSFFile

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:92
**Export:** CSFFile

**Issue:** `references/core-api.md:274` documents `CSFFile`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CSFFile` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:92` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-097: Documented extra: CalledExtractOnStoreError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:77
**Export:** CalledExtractOnStoreError

**Issue:** `references/core-api.md:299` documents `CalledExtractOnStoreError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CalledExtractOnStoreError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-098: Documented extra: CalledPreviewMethodBeforeInitializationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:107
**Export:** CalledPreviewMethodBeforeInitializationError

**Issue:** `references/core-api.md:299` documents `CalledPreviewMethodBeforeInitializationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CalledPreviewMethodBeforeInitializationError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:107` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-100: Documented extra: Category

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:15
**Export:** Category

**Issue:** `references/core-api.md:301` documents `Category`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/preview-errors.ts`

**Remediation:** No change: `Category` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-107: Documented extra: Combo

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:116
**Export:** Combo

**Issue:** `references/story-types.md:242` documents `Combo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Combo` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:116` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-108: Documented extra: ComponentAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/story.ts:452
**Export:** ComponentAnnotations

**Issue:** `SKILL.md:208` documents `ComponentAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ComponentAnnotations` is a documented extra, a name the source still declares at `code/core/src/csf/story.ts:452` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-113: Documented extra: Decorator

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/public-types.ts:77
**Export:** Decorator

**Issue:** `SKILL.md:133` documents `Decorator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Decorator` is a documented extra, a name the source still declares at `code/renderers/react/src/public-types.ts:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-114: Documented extra: DecoratorHelpers

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/decorators/index.ts:5
**Export:** DecoratorHelpers

**Issue:** `references/addons.md:121` documents `DecoratorHelpers`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DecoratorHelpers` is a documented extra, a name the source still declares at `code/addons/themes/src/decorators/index.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-117: Documented extra: EmptyIndexError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:161
**Export:** EmptyIndexError

**Issue:** `references/core-api.md:299` documents `EmptyIndexError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EmptyIndexError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:161` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-119: Documented extra: FULL_RUN_TRIGGERS

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:61
**Export:** FULL_RUN_TRIGGERS

**Issue:** `references/addons.md:199` documents `FULL_RUN_TRIGGERS`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FULL_RUN_TRIGGERS` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:61` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-122: Documented extra: FrameworkOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/react-vite/src/types.ts:14
**Export:** FrameworkOptions

**Issue:** `references/core-api.md:12` documents `FrameworkOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FrameworkOptions` is a documented extra, a name the source still declares at `code/frameworks/react-vite/src/types.ts:14` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-125: Documented extra: Globals

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/story.ts:165
**Export:** Globals

**Issue:** `references/core-api.md:264` documents `Globals`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Globals` is a documented extra, a name the source still declares at `code/core/src/csf/story.ts:165` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-132: Documented extra: ImplicitActionsDuringRendering

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:56
**Export:** ImplicitActionsDuringRendering

**Issue:** `references/core-api.md:299` documents `ImplicitActionsDuringRendering`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ImplicitActionsDuringRendering` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-133: Documented extra: IncludeExcludeOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:38
**Export:** IncludeExcludeOptions

**Issue:** `references/core-api.md:292` documents `IncludeExcludeOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IncludeExcludeOptions` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:38` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-135: Documented extra: InvalidFrameworkNameError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/server-errors.ts:86
**Export:** InvalidFrameworkNameError

**Issue:** `references/core-api.md:305` documents `InvalidFrameworkNameError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `InvalidFrameworkNameError` is a documented extra, a name the source still declares at `code/core/src/server-errors.ts:86` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-139: Documented extra: Loader

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/public-types.ts:78
**Export:** Loader

**Issue:** `SKILL.md:171` documents `Loader`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Loader` is a documented extra, a name the source still declares at `code/renderers/react/src/public-types.ts:78` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-140: Documented extra: ManagerContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:80
**Export:** ManagerContext

**Issue:** `references/story-types.md:245` documents `ManagerContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ManagerContext` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:80` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-141: Documented extra: ManagerProviderProps

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:121
**Export:** ManagerProviderProps

**Issue:** `references/story-types.md:246` documents `ManagerProviderProps`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ManagerProviderProps` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:121` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-143: Documented extra: MdxFileWithNoCsfReferencesError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:145
**Export:** MdxFileWithNoCsfReferencesError

**Issue:** `references/core-api.md:299` documents `MdxFileWithNoCsfReferencesError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MdxFileWithNoCsfReferencesError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:145` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-144: Documented extra: MissingFrameworkFieldError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/server-errors.ts:70
**Export:** MissingFrameworkFieldError

**Issue:** `references/core-api.md:305` documents `MissingFrameworkFieldError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MissingFrameworkFieldError` is a documented extra, a name the source still declares at `code/core/src/server-errors.ts:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-145: Documented extra: MissingRenderToCanvasError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:91
**Export:** MissingRenderToCanvasError

**Issue:** `references/core-api.md:299` documents `MissingRenderToCanvasError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MissingRenderToCanvasError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:91` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-146: Documented extra: MissingStoryAfterHmrError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:39
**Export:** MissingStoryAfterHmrError

**Issue:** `references/core-api.md:299` documents `MissingStoryAfterHmrError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MissingStoryAfterHmrError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-147: Documented extra: MissingStoryFromCsfFileError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:192
**Export:** MissingStoryFromCsfFileError

**Issue:** `references/core-api.md:299` documents `MissingStoryFromCsfFileError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MissingStoryFromCsfFileError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:192` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-150: Documented extra: MockUniversalStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/shared/universal-store/mock.ts:40
**Export:** MockUniversalStore

**Issue:** `references/core-api.md:152` documents `MockUniversalStore`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MockUniversalStore` is a documented extra, a name the source still declares at `code/core/src/shared/universal-store/mock.ts:40` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-152: Documented extra: MountMustBeDestructuredError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:226
**Export:** MountMustBeDestructuredError

**Issue:** `references/core-api.md:299` documents `MountMustBeDestructuredError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MountMustBeDestructuredError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:226` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-153: Documented extra: NoRenderFunctionError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:256
**Export:** NoRenderFunctionError

**Issue:** `references/core-api.md:299` documents `NoRenderFunctionError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NoRenderFunctionError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:256` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-154: Documented extra: NoStoryMatchError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:176
**Export:** NoStoryMatchError

**Issue:** `references/core-api.md:299` documents `NoStoryMatchError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NoStoryMatchError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:176` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-155: Documented extra: NoStoryMountedError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:269
**Export:** NoStoryMountedError

**Issue:** `references/core-api.md:299` documents `NoStoryMountedError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NoStoryMountedError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:269` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-157: Documented extra: NormalizedComponentAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:66
**Export:** NormalizedComponentAnnotations

**Issue:** `references/core-api.md:117` documents `NormalizedComponentAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NormalizedComponentAnnotations` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:66` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-158: Documented extra: NormalizedProjectAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:55
**Export:** NormalizedProjectAnnotations

**Issue:** `references/core-api.md:113` documents `NormalizedProjectAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NormalizedProjectAnnotations` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:55` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-159: Documented extra: NormalizedStoryAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:78
**Export:** NormalizedStoryAnnotations

**Issue:** `references/core-api.md:117` documents `NormalizedStoryAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NormalizedStoryAnnotations` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:78` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-160: Documented extra: NxProjectDetectedError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/server-errors.ts:56
**Export:** NxProjectDetectedError

**Issue:** `references/core-api.md:305` documents `NxProjectDetectedError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NxProjectDetectedError` is a documented extra, a name the source still declares at `code/core/src/server-errors.ts:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-171: Documented extra: PreparedStory

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:99
**Export:** PreparedStory

**Issue:** `references/core-api.md:120` documents `PreparedStory`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PreparedStory` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-174: Documented extra: Refs

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:314
**Export:** Refs

**Issue:** `references/story-types.md:247` documents `Refs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Refs` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:314` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-175: Documented extra: RenderContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:129
**Export:** RenderContext

**Issue:** `references/core-api.md:277` documents `RenderContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RenderContext` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:129` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-176: Documented extra: RenderToCanvas

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:38
**Export:** RenderToCanvas

**Issue:** `references/core-api.md:273` documents `RenderToCanvas`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RenderToCanvas` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:38` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-179: Documented extra: STORYBOOK_ADDON_TEST_CHANNEL

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:13
**Export:** STORYBOOK_ADDON_TEST_CHANNEL

**Issue:** `references/addons.md:195` documents `STORYBOOK_ADDON_TEST_CHANNEL`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `STORYBOOK_ADDON_TEST_CHANNEL` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:13` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-186: Documented extra: SeparatorOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:63
**Export:** SeparatorOptions

**Issue:** `references/core-api.md:293` documents `SeparatorOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SeparatorOptions` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:63` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-189: Documented extra: State

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:82
**Export:** State

**Issue:** `references/core-api.md:79` documents `State`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `State` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:82` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-190: Documented extra: StatusTypeIdMismatchError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:295
**Export:** StatusTypeIdMismatchError

**Issue:** `references/core-api.md:299` documents `StatusTypeIdMismatchError`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/preview-errors.ts`

**Remediation:** No change: `StatusTypeIdMismatchError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:295` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-191: Documented extra: StoreOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:77
**Export:** StoreOptions

**Issue:** `references/story-types.md:244` documents `StoreOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoreOptions` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-192: Documented extra: Store_CSFExports

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/composedStory.ts:23
**Export:** Store_CSFExports

**Issue:** `references/core-api.md:95` documents `Store_CSFExports`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Store_CSFExports` is a documented extra, a name the source still declares at `code/core/src/types/modules/composedStory.ts:23` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-193: Documented extra: StoriesHash

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:304
**Export:** StoriesHash

**Issue:** `references/story-types.md:250` documents `StoriesHash`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoriesHash` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:304` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-194: Documented extra: StoryAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/story.ts:543
**Export:** StoryAnnotations

**Issue:** `SKILL.md:208` documents `StoryAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryAnnotations` is a documented extra, a name the source still declares at `code/core/src/csf/story.ts:543` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-195: Documented extra: StoryContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/public-types.ts:79
**Export:** StoryContext

**Issue:** `SKILL.md:171` documents `StoryContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryContext` is a documented extra, a name the source still declares at `code/renderers/react/src/public-types.ts:79` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-197: Documented extra: StoryFn

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/public-types.ts:38
**Export:** StoryFn

**Issue:** `SKILL.md:208` documents `StoryFn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryFn` is a documented extra, a name the source still declares at `code/renderers/react/src/public-types.ts:38` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-198: Documented extra: StoryIndexFetchError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:125
**Export:** StoryIndexFetchError

**Issue:** `references/core-api.md:299` documents `StoryIndexFetchError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryIndexFetchError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:125` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-200: Documented extra: StoryObj

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/public-types.ts:47
**Export:** StoryObj

**Issue:** `SKILL.md:45` documents `StoryObj`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryObj` is a documented extra, a name the source still declares at `code/renderers/react/src/public-types.ts:47` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-201: Documented extra: StoryStoreAccessedBeforeInitializationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:211
**Export:** StoryStoreAccessedBeforeInitializationError

**Issue:** `references/core-api.md:299` documents `StoryStoreAccessedBeforeInitializationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryStoreAccessedBeforeInitializationError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:211` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-202: Documented extra: StorybookConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/react-vite/src/types.ts:66
**Export:** StorybookConfig

**Issue:** `SKILL.md:208` documents `StorybookConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StorybookConfig` is a documented extra, a name the source still declares at `code/frameworks/react-vite/src/types.ts:66` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-203: Documented extra: StorybookError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/storybook-error.ts:25
**Export:** StorybookError

**Issue:** `references/core-api.md:299` documents `StorybookError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StorybookError` is a documented extra, a name the source still declares at `code/core/src/storybook-error.ts:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-206: Documented extra: StorybookParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/csf.ts:75
**Export:** StorybookParameters

**Issue:** `references/core-api.md:271` documents `StorybookParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StorybookParameters` is a documented extra, a name the source still declares at `code/core/src/types/modules/csf.ts:75` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-207: Documented extra: StrictArgs

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/story.ts:157
**Export:** StrictArgs

**Issue:** `SKILL.md:133` documents `StrictArgs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StrictArgs` is a documented extra, a name the source still declares at `code/core/src/csf/story.ts:157` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-208: Documented extra: StyledComponent

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/angular/template/stories/basics/component-with-style/styled.component.ts:9
**Export:** StyledComponent

**Issue:** `references/core-api.md:178` documents `StyledComponent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StyledComponent` is a documented extra, a name the source still declares at `code/frameworks/angular/template/stories/basics/component-with-style/styled.component.ts:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-210: Documented extra: TEST_PROVIDER_ID

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:12
**Export:** TEST_PROVIDER_ID

**Issue:** `references/addons.md:194` documents `TEST_PROVIDER_ID`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TEST_PROVIDER_ID` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-216: Documented extra: Table

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/components/components/typography/elements/Table.tsx:6
**Export:** Table

**Issue:** `references/core-api.md:312` documents `Table`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Table` is a documented extra, a name the source still declares at `code/core/src/components/components/typography/elements/Table.tsx:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-219: Documented extra: TestRunResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:81
**Export:** TestRunResult

**Issue:** `references/addons.md:201` documents `TestRunResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TestRunResult` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:81` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-220: Documented extra: Theme

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:10
**Export:** Theme

**Issue:** `references/addons.md:98` documents `Theme`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Theme` is a documented extra, a name the source still declares at `code/addons/themes/src/decorators/provider.decorator.tsx:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-221: Documented extra: ThemeAddonState

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:1
**Export:** ThemeAddonState

**Issue:** `references/addons.md:114` documents `ThemeAddonState`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemeAddonState` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-223: Documented extra: ThemesParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:6
**Export:** ThemesParameters

**Issue:** `references/addons.md:115` documents `ThemesParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemesParameters` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-229: Documented extra: TriggerTestRunRequestPayload

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:74
**Export:** TriggerTestRunRequestPayload

**Issue:** `references/addons.md:200` documents `TriggerTestRunRequestPayload`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TriggerTestRunRequestPayload` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:74` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-230: Documented extra: TriggerTestRunResponsePayload

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:83
**Export:** TriggerTestRunResponsePayload

**Issue:** `references/addons.md:202` documents `TriggerTestRunResponsePayload`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TriggerTestRunResponsePayload` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:83` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-234: Documented extra: WebRenderer

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:28
**Export:** WebRenderer

**Issue:** `references/core-api.md:272` documents `WebRenderer`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `WebRenderer` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:28` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-238: Documented extra: __definePreview

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/preview.tsx:55
**Export:** __definePreview

**Issue:** `references/core-api.md:18` documents `__definePreview`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__definePreview` is a documented extra, a name the source still declares at `code/renderers/react/src/preview.tsx:55` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-241: Documented extra: afterEach

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/a11y/src/preview.tsx:14
**Export:** afterEach

**Issue:** `references/addons.md:58` documents `afterEach`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `afterEach` is a documented extra, a name the source still declares at `code/addons/a11y/src/preview.tsx:14` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-243: Documented extra: babelParse

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/babel/babelParse.ts:28
**Export:** babelParse

**Issue:** `references/core-api.md:337` documents `babelParse`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `babelParse` is a documented extra, a name the source still declares at `code/core/src/babel/babelParse.ts:28` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-244: Documented extra: bail

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/builders/builder-vite/src/index.ts:37
**Export:** bail

**Issue:** `references/framework-config.md:156` documents `bail`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `bail` is a documented extra, a name the source still declares at `code/builders/builder-vite/src/index.ts:37` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-245: Documented extra: build

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/builders/builder-vite/src/index.ts:63
**Export:** build

**Issue:** `SKILL.md:142` documents `build`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `build` is a documented extra, a name the source still declares at `code/builders/builder-vite/src/index.ts:63` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-246: Documented extra: canvas

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/measure/box-model/canvas.ts:1
**Export:** canvas

**Issue:** `SKILL.md:64` documents `canvas`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `canvas` is a documented extra, a name the source still declares at `code/core/src/measure/box-model/canvas.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-248: Documented extra: combineTags

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:81
**Export:** combineTags

**Issue:** `references/core-api.md:290` documents `combineTags`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `combineTags` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:81` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-253: Documented extra: createCache

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/theming/index.ts:33
**Export:** createCache

**Issue:** `references/core-api.md:172` documents `createCache`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `createCache` is a documented extra, a name the source still declares at `code/core/src/theming/index.ts:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-255: Documented extra: css

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/pseudo-states/src/stories/CustomElement.tsx:1
**Export:** css

**Issue:** `references/core-api.md:20` documents `css`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `css` is a documented extra, a name the source still declares at `code/addons/pseudo-states/src/stories/CustomElement.tsx:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-257: Documented extra: defineMain

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/react-vite/src/node/index.ts:3
**Export:** defineMain

**Issue:** `references/core-api.md:13` documents `defineMain`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `defineMain` is a documented extra, a name the source still declares at `code/frameworks/react-vite/src/node/index.ts:3` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-261: Documented extra: esmWalker

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/mocking-utils/esmWalker.ts:71
**Export:** esmWalker

**Issue:** `references/core-api.md:339` documents `esmWalker`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `esmWalker` is a documented extra, a name the source still declares at `code/core/src/mocking-utils/esmWalker.ts:71` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-263: Documented extra: experimental_UniversalStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/index.ts:3
**Export:** experimental_UniversalStore

**Issue:** `references/core-api.md:150` documents `experimental_UniversalStore`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/manager-api/index.ts`

**Remediation:** No change: `experimental_UniversalStore` is a documented extra, a name the source still declares at `code/core/src/manager-api/index.ts:3` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-264: Documented extra: experimental_getStatusStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/index.ts:8
**Export:** experimental_getStatusStore

**Issue:** `references/core-api.md:153` documents `experimental_getStatusStore`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/manager-api/index.ts`

**Remediation:** No change: `experimental_getStatusStore` is a documented extra, a name the source still declares at `code/core/src/manager-api/index.ts:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-265: Documented extra: experimental_getTestProviderStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/index.ts:15
**Export:** experimental_getTestProviderStore

**Issue:** `references/core-api.md:154` documents `experimental_getTestProviderStore`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/manager-api/index.ts`

**Remediation:** No change: `experimental_getTestProviderStore` is a documented extra, a name the source still declares at `code/core/src/manager-api/index.ts:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-273: Documented extra: getPreviewBodyTemplate

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/template.ts:10
**Export:** getPreviewBodyTemplate

**Issue:** `references/core-api.md:340` documents `getPreviewBodyTemplate`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getPreviewBodyTemplate` is a documented extra, a name the source still declares at `code/core/src/common/utils/template.ts:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-274: Documented extra: getPreviewHeadTemplate

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/template.ts:29
**Export:** getPreviewHeadTemplate

**Issue:** `references/core-api.md:340` documents `getPreviewHeadTemplate`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getPreviewHeadTemplate` is a documented extra, a name the source still declares at `code/core/src/common/utils/template.ts:29` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-276: Documented extra: getStoryHref

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/components/components/utils/getStoryHref.ts:15
**Export:** getStoryHref

**Issue:** `references/core-api.md:318` documents `getStoryHref`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getStoryHref` is a documented extra, a name the source still declares at `code/core/src/components/components/utils/getStoryHref.ts:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-278: Documented extra: getStorybookInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/get-storybook-info.ts:139
**Export:** getStorybookInfo

**Issue:** `references/core-api.md:329` documents `getStorybookInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getStorybookInfo` is a documented extra, a name the source still declares at `code/core/src/common/utils/get-storybook-info.ts:139` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-280: Documented extra: initialGlobals

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/a11y/src/preview.tsx:98
**Export:** initialGlobals

**Issue:** `references/addons.md:64` documents `initialGlobals`, which the enumerated source API surface lacks and the source still declares; of the 9 files that declare it, the skill cites only `code/addons/a11y/src/preview.tsx`

**Remediation:** No change: `initialGlobals` is a documented extra, a name the source still declares at `code/addons/a11y/src/preview.tsx:98` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-281: Documented extra: instrument

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/instrumenter/instrumenter.ts:749
**Export:** instrument

**Issue:** `references/core-api.md:332` documents `instrument`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `instrument` is a documented extra, a name the source still declares at `code/core/src/instrumenter/instrumenter.ts:749` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-282: Documented extra: isExportStory

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:51
**Export:** isExportStory

**Issue:** `references/core-api.md:288` documents `isExportStory`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `isExportStory` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:51` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-284: Documented extra: isPropValid

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/theming/index.ts:34
**Export:** isPropValid

**Issue:** `references/core-api.md:173` documents `isPropValid`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `isPropValid` is a documented extra, a name the source still declares at `code/core/src/theming/index.ts:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-286: Documented extra: keyframes

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager/components/TourGuide/HighlightElement.tsx:5
**Export:** keyframes

**Issue:** `references/core-api.md:165` documents `keyframes`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `keyframes` is a documented extra, a name the source still declares at `code/core/src/manager/components/TourGuide/HighlightElement.tsx:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-287: Documented extra: loadMainConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/load-main-config.ts:14
**Export:** loadMainConfig

**Issue:** `references/core-api.md:329` documents `loadMainConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `loadMainConfig` is a documented extra, a name the source still declares at `code/core/src/common/utils/load-main-config.ts:14` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-290: Documented extra: mocks

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/component-testing/mocks/index.ts:1
**Export:** mocks

**Issue:** `references/core-api.md:131` documents `mocks`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mocks` is a documented extra, a name the source still declares at `code/core/src/component-testing/mocks/index.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-292: Documented extra: normalizeStories

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/normalize-stories.ts:108
**Export:** normalizeStories

**Issue:** `references/core-api.md:329` documents `normalizeStories`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `normalizeStories` is a documented extra, a name the source still declares at `code/core/src/common/utils/normalize-stories.ts:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-294: Documented extra: parameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/a11y/src/preview.tsx:105
**Export:** parameters

**Issue:** `SKILL.md:35` documents `parameters`, which the enumerated source API surface lacks and the source still declares; of the 23 files that declare it, the skill cites only `code/addons/a11y/src/preview.tsx`

**Remediation:** No change: `parameters` is a documented extra, a name the source still declares at `code/addons/a11y/src/preview.tsx:105` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-295: Documented extra: parseKind

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:69
**Export:** parseKind

**Issue:** `references/core-api.md:289` documents `parseKind`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `parseKind` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:69` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-297: Documented extra: pretty

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/client-logger/index.ts:77
**Export:** pretty

**Issue:** `references/core-api.md:334` documents `pretty`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pretty` is a documented extra, a name the source still declares at `code/core/src/client-logger/index.ts:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-304: Documented extra: sanitize

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:8
**Export:** sanitize

**Issue:** `references/core-api.md:291` documents `sanitize`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `code/core/src/csf/index.ts`

**Remediation:** No change: `sanitize` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-306: Documented extra: start

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/builders/builder-vite/src/index.ts:41
**Export:** start

**Issue:** `SKILL.md:169` documents `start`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `start` is a documented extra, a name the source still declares at `code/builders/builder-vite/src/index.ts:41` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-307: Documented extra: storeOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:21
**Export:** storeOptions

**Issue:** `references/addons.md:198` documents `storeOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `storeOptions` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-308: Documented extra: storyNameFromExport

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:35
**Export:** storyNameFromExport

**Issue:** `references/core-api.md:287` documents `storyNameFromExport`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `storyNameFromExport` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-309: Documented extra: styled

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/theming/index.ts:6
**Export:** styled

**Issue:** `references/addons.md:112` documents `styled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `styled` is a documented extra, a name the source still declares at `code/core/src/theming/index.ts:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-311: Documented extra: toId

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:27
**Export:** toId

**Issue:** `references/core-api.md:285` documents `toId`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `toId` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:27` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-312: Documented extra: toTestId

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:31
**Export:** toTestId

**Issue:** `references/core-api.md:286` documents `toTestId`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `toTestId` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-328: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=1335, documented=223

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-329: Provenance line not verified for A11yGlobals_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:16
**Export:** A11yGlobals_exact

**Issue:** the line-check rules found no definition line for `A11yGlobals_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 16 defines `A11yGlobals_exact`; if another line does, set the provenance `source_line` to it.

### GAP-330: Provenance line not verified for A11yReport_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/types.ts:5
**Export:** A11yReport_exact

**Issue:** the line-check rules found no definition line for `A11yReport_exact` in `code/addons/a11y/src/types.ts`; check by hand

**Remediation:** Open `code/addons/a11y/src/types.ts` and confirm that line 5 defines `A11yReport_exact`; if another line does, set the provenance `source_line` to it.

### GAP-331: Provenance line not verified for ArgTypes

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ArgTypes

**Issue:** the line-check rules found no definition line for `ArgTypes` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ArgTypes`; if another line does, set the provenance `source_line` to it.

### GAP-332: Provenance line not verified for Canvas

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Canvas

**Issue:** the line-check rules found no definition line for `Canvas` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Canvas`; if another line does, set the provenance `source_line` to it.

### GAP-333: Provenance line not verified for ColorPalette

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** ColorPalette

**Issue:** the line-check rules found no definition line for `ColorPalette` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `ColorPalette`; if another line does, set the provenance `source_line` to it.

### GAP-334: Provenance line not verified for ComponentEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** ComponentEntry

**Issue:** the line-check rules found no definition line for `ComponentEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 27 defines `ComponentEntry`; if another line does, set the provenance `source_line` to it.

### GAP-335: Provenance line not verified for Controls

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Controls

**Issue:** the line-check rules found no definition line for `Controls` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Controls`; if another line does, set the provenance `source_line` to it.

### GAP-336: Provenance line not verified for Description

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Description

**Issue:** the line-check rules found no definition line for `Description` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Description`; if another line does, set the provenance `source_line` to it.

### GAP-337: Provenance line not verified for DocsContainer

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContainer

**Issue:** the line-check rules found no definition line for `DocsContainer` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContainer`; if another line does, set the provenance `source_line` to it.

### GAP-338: Provenance line not verified for DocsContext

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** DocsContext

**Issue:** the line-check rules found no definition line for `DocsContext` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `DocsContext`; if another line does, set the provenance `source_line` to it.

### GAP-339: Provenance line not verified for DocsEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** DocsEntry

**Issue:** the line-check rules found no definition line for `DocsEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 34 defines `DocsEntry`; if another line does, set the provenance `source_line` to it.

### GAP-340: Provenance line not verified for GroupEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** GroupEntry

**Issue:** the line-check rules found no definition line for `GroupEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 21 defines `GroupEntry`; if another line does, set the provenance `source_line` to it.

### GAP-341: Provenance line not verified for HashEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** HashEntry

**Issue:** the line-check rules found no definition line for `HashEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 67 defines `HashEntry`; if another line does, set the provenance `source_line` to it.

### GAP-342: Provenance line not verified for IconGallery

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** IconGallery

**Issue:** the line-check rules found no definition line for `IconGallery` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `IconGallery`; if another line does, set the provenance `source_line` to it.

### GAP-343: Provenance line not verified for IndexHash

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** IndexHash

**Issue:** the line-check rules found no definition line for `IndexHash` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 80 defines `IndexHash`; if another line does, set the provenance `source_line` to it.

### GAP-344: Provenance line not verified for LeafEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** LeafEntry

**Issue:** the line-check rules found no definition line for `LeafEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 66 defines `LeafEntry`; if another line does, set the provenance `source_line` to it.

### GAP-345: Provenance line not verified for Markdown

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Markdown

**Issue:** the line-check rules found no definition line for `Markdown` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Markdown`; if another line does, set the provenance `source_line` to it.

### GAP-346: Provenance line not verified for Primary

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Primary

**Issue:** the line-check rules found no definition line for `Primary` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Primary`; if another line does, set the provenance `source_line` to it.

### GAP-347: Provenance line not verified for RootEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** RootEntry

**Issue:** the line-check rules found no definition line for `RootEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 15 defines `RootEntry`; if another line does, set the provenance `source_line` to it.

### GAP-348: Provenance line not verified for Source

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Source

**Issue:** the line-check rules found no definition line for `Source` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Source`; if another line does, set the provenance `source_line` to it.

### GAP-349: Provenance line not verified for Stories

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Stories

**Issue:** the line-check rules found no definition line for `Stories` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Stories`; if another line does, set the provenance `source_line` to it.

### GAP-350: Provenance line not verified for Story

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Story

**Issue:** the line-check rules found no definition line for `Story` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Story`; if another line does, set the provenance `source_line` to it.

### GAP-351: Provenance line not verified for StoryEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** StoryEntry

**Issue:** the line-check rules found no definition line for `StoryEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 45 defines `StoryEntry`; if another line does, set the provenance `source_line` to it.

### GAP-352: Provenance line not verified for Subtitle

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Subtitle

**Issue:** the line-check rules found no definition line for `Subtitle` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Subtitle`; if another line does, set the provenance `source_line` to it.

### GAP-353: Provenance line not verified for ThemesGlobals_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/types.ts:20
**Export:** ThemesGlobals_def

**Issue:** the line-check rules found no definition line for `ThemesGlobals_def` in `code/addons/themes/src/types.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/types.ts` and confirm that line 20 defines `ThemesGlobals_def`; if another line does, set the provenance `source_line` to it.

### GAP-354: Provenance line not verified for Title

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Title

**Issue:** the line-check rules found no definition line for `Title` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Title`; if another line does, set the provenance `source_line` to it.

### GAP-355: Provenance line not verified for Typeset

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Typeset

**Issue:** the line-check rules found no definition line for `Typeset` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Typeset`; if another line does, set the provenance `source_line` to it.

### GAP-356: Provenance line not verified for Unstyled

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** Unstyled

**Issue:** the line-check rules found no definition line for `Unstyled` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `Unstyled`; if another line does, set the provenance `source_line` to it.

### GAP-357: Provenance line not verified for a11y_decorators

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:12
**Export:** a11y_decorators

**Issue:** the line-check rules found no definition line for `a11y_decorators` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 12 defines `a11y_decorators`; if another line does, set the provenance `source_line` to it.

### GAP-358: Provenance line not verified for a11y_initialGlobals

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:98
**Export:** a11y_initialGlobals

**Issue:** the line-check rules found no definition line for `a11y_initialGlobals` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 98 defines `a11y_initialGlobals`; if another line does, set the provenance `source_line` to it.

### GAP-359: Provenance line not verified for a11y_parameters

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/a11y/src/preview.tsx:105
**Export:** a11y_parameters

**Issue:** the line-check rules found no definition line for `a11y_parameters` in `code/addons/a11y/src/preview.tsx`; check by hand

**Remediation:** Open `code/addons/a11y/src/preview.tsx` and confirm that line 105 defines `a11y_parameters`; if another line does, set the provenance `source_line` to it.

### GAP-360: Provenance line not verified for definePreview

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/preview-api/index.ts:1
**Export:** definePreview

**Issue:** the line-check rules found no definition line for `definePreview` in `code/core/src/preview-api/index.ts`; check by hand

**Remediation:** Open `code/core/src/preview-api/index.ts` and confirm that line 1 defines `definePreview`; if another line does, set the provenance `source_line` to it.

### GAP-361: Provenance line not verified for fireEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:43
**Export:** fireEvent

**Issue:** the line-check rules found no definition line for `fireEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 43 defines `fireEvent`; if another line does, set the provenance `source_line` to it.

### GAP-362: Provenance line not verified for mockChannel_def

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:3
**Export:** mockChannel_def

**Issue:** the line-check rules found no definition line for `mockChannel_def` in `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts`; check by hand

**Remediation:** Open `code/core/src/preview-api/modules/addons/storybook-channel-mock.ts` and confirm that line 3 defines `mockChannel_def`; if another line does, set the provenance `source_line` to it.

### GAP-363: Provenance line not verified for screen

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:107
**Export:** screen

**Issue:** the line-check rules found no definition line for `screen` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 107 defines `screen`; if another line does, set the provenance `source_line` to it.

### GAP-364: Provenance line not verified for useOf

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks.ts:1
**Export:** useOf

**Issue:** the line-check rules found no definition line for `useOf` in `code/addons/docs/src/blocks.ts`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks.ts` and confirm that line 1 defines `useOf`; if another line does, set the provenance `source_line` to it.

### GAP-365: Provenance line not verified for userEvent

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:123
**Export:** userEvent

**Issue:** the line-check rules found no definition line for `userEvent` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 123 defines `userEvent`; if another line does, set the provenance `source_line` to it.

### GAP-366: Provenance line not verified for waitFor

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:108
**Export:** waitFor

**Issue:** the line-check rules found no definition line for `waitFor` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 108 defines `waitFor`; if another line does, set the provenance `source_line` to it.

### GAP-367: Provenance line not verified for withThemeByClassName

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByClassName

**Issue:** the line-check rules found no definition line for `withThemeByClassName` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByClassName`; if another line does, set the provenance `source_line` to it.

### GAP-368: Provenance line not verified for withThemeByClassName_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/class-name.decorator.tsx:19
**Export:** withThemeByClassName_exact

**Issue:** the line-check rules found no definition line for `withThemeByClassName_exact` in `code/addons/themes/src/decorators/class-name.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/class-name.decorator.tsx` and confirm that line 19 defines `withThemeByClassName_exact`; if another line does, set the provenance `source_line` to it.

### GAP-369: Provenance line not verified for withThemeByDataAttribute

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByDataAttribute

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByDataAttribute`; if another line does, set the provenance `source_line` to it.

### GAP-370: Provenance line not verified for withThemeByDataAttribute_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/data-attribute.decorator.tsx:19
**Export:** withThemeByDataAttribute_exact

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute_exact` in `code/addons/themes/src/decorators/data-attribute.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/data-attribute.decorator.tsx` and confirm that line 19 defines `withThemeByDataAttribute_exact`; if another line does, set the provenance `source_line` to it.

### GAP-371: Provenance line not verified for withThemeFromJSXProvider

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeFromJSXProvider

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeFromJSXProvider`; if another line does, set the provenance `source_line` to it.

### GAP-372: Provenance line not verified for withThemeFromJSXProvider_exact

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:23
**Export:** withThemeFromJSXProvider_exact

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider_exact` in `code/addons/themes/src/decorators/provider.decorator.tsx`; check by hand

**Remediation:** Open `code/addons/themes/src/decorators/provider.decorator.tsx` and confirm that line 23 defines `withThemeFromJSXProvider_exact`; if another line does, set the provenance `source_line` to it.

### GAP-373: Provenance line not verified for within

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/test/testing-library.ts:110
**Export:** within

**Issue:** the line-check rules found no definition line for `within` in `code/core/src/test/testing-library.ts`; check by hand

**Remediation:** Open `code/core/src/test/testing-library.ts` and confirm that line 110 defines `within`; if another line does, set the provenance `source_line` to it.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
