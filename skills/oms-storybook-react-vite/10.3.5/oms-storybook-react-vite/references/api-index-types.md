# `storybook/internal/types` — Export Index

The types `storybook/internal/types` exports (entry `code/core/src/types/index.ts`) that the topic references do not document: the manager API state and entry shapes (`API_*`), addon registration types (`Addon_*`), indexer, preset, builder and core-common config types. Story authors rarely import them; `story-types.md` covers the CSF types every story file uses.

Each row gives the export's declaration as the source writes it at the cited line (`[SRC:...]` for a line read from the source, `[AST:...]` for one an ast-grep recipe matched) and the first sentence of its JSDoc when it has one. An export re-exported under another name says which local name it renames.

## Contents

- [`storybook/internal/types`](#storybookinternaltypes) — 213 exports

## `storybook/internal/types`

Entry: `code/core/src/types/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `Actor` | type | `export type Actor = {` | `[SRC:code/core/src/shared/universal-store/types.ts:L11]` |
| `Addon_AddStoryArgs` | interface | `export interface Addon_AddStoryArgs<StoryFnReturnType = unknown> {` | `[SRC:code/core/src/types/modules/addons.ts:L123]` |
| `Addon_Annotations` | interface | `export interface Addon_Annotations<TArgs, StoryFnReturnType> extends Addon_BaseAnnotations<TArgs, StoryFnReturnType> {` | `[SRC:code/core/src/types/modules/addons.ts:L216]` |
| `Addon_ArgsStoryFn` | type | `export type Addon_ArgsStoryFn<ReturnType = unknown> = ArgsStoryFnForFramework<Addon_ReturnTypeFramework<ReturnType>>;` | `[SRC:code/core/src/types/modules/addons.ts:L96]` |
| `Addon_ArgType` | interface | `export interface Addon_ArgType<TArg = unknown> extends InputType {` | `[SRC:code/core/src/types/modules/addons.ts:L31]` |
| `Addon_BaseAnnotations` | interface | `export interface Addon_BaseAnnotations<TArgs, StoryFnReturnType, TRenderer extends Renderer = Renderer> {` | `[SRC:code/core/src/types/modules/addons.ts:L170]` |
| `Addon_BaseDecorators` | type | `export type Addon_BaseDecorators<StoryFnReturnType> = Array<(story: () => StoryFnReturnType, context: Addon_StoryContext) => StoryFnReturnType>;` | `[SRC:code/core/src/types/modules/addons.ts:L166]` |
| `Addon_BaseMeta` | interface | `export interface Addon_BaseMeta<ComponentType> {` | `[SRC:code/core/src/types/modules/addons.ts:L251]` |
| `Addon_BaseStoryFn` | type | `export type Addon_BaseStoryFn<TArgs, StoryFnReturnType> = {` | `[SRC:code/core/src/types/modules/addons.ts:L312]` |
| `Addon_BaseStoryObject` | type | `export type Addon_BaseStoryObject<TArgs, StoryFnReturnType> = {` | `[SRC:code/core/src/types/modules/addons.ts:L307]` |
| `Addon_BaseType` | interface | `export interface Addon_BaseType {` | `[SRC:code/core/src/types/modules/addons.ts:L329]` |
| `Addon_ClientApiAddon` | type | `export type Addon_ClientApiAddon<StoryFnReturnType = unknown> = Addon_Type & {` | `[SRC:code/core/src/types/modules/addons.ts:L131]` |
| `Addon_ClientApiAddons` | interface | `export interface Addon_ClientApiAddons<StoryFnReturnType> {` | `[SRC:code/core/src/types/modules/addons.ts:L135]` |
| `Addon_ClientApiReturnFn` | type | `export type Addon_ClientApiReturnFn<StoryFnReturnType = unknown> = (...args: any[]) => Addon_StoryApi<StoryFnReturnType>;` | `[SRC:code/core/src/types/modules/addons.ts:L139]` |
| `Addon_ClientStoryApi` | interface | `export interface Addon_ClientStoryApi<StoryFnReturnType = unknown> {}` | `[SRC:code/core/src/types/modules/addons.ts:L158]` |
| `Addon_Collection` | interface | `export interface Addon_Collection<T = Addon_Type> {` | `[SRC:code/core/src/types/modules/addons.ts:L470]` |
| `Addon_Comparator` | type | `export type Addon_Comparator<T> = ((a: T, b: T) => boolean) \| ((a: T, b: T) => number);` | `[SRC:code/core/src/types/modules/addons.ts:L42]` |
| `Addon_Config` | interface | `export interface Addon_Config {` | `[SRC:code/core/src/types/modules/addons.ts:L479]` |
| `Addon_DecoratorFunction` | type | `export type Addon_DecoratorFunction<StoryFnReturnType = unknown> = DecoratorFunctionForFramework<Addon_ReturnTypeFramework<StoryFnReturnType>>;` | `[SRC:code/core/src/types/modules/addons.ts:L103]` |
| `Addon_Elements` | interface | `export interface Addon_Elements {` | `[SRC:code/core/src/types/modules/addons.ts:L473]` |
| `Addon_LegacyStoryFn` | type | `export type Addon_LegacyStoryFn<ReturnType = unknown> = LegacyStoryFnForFramework<Addon_ReturnTypeFramework<ReturnType>>;` | `[SRC:code/core/src/types/modules/addons.ts:L93]` |
| `Addon_Loadable` | type | `export type Addon_Loadable = Addon_RequireContext \| [Addon_RequireContext] \| Addon_LoadFn;` | `[SRC:code/core/src/types/modules/addons.ts:L162]` |
| `Addon_Loader` | type | `export type Addon_Loader<API> = (api: API) => void;` | `[SRC:code/core/src/types/modules/addons.ts:L465]` |
| `Addon_LoaderFunction` | type | `export type Addon_LoaderFunction = LoaderFunctionForFramework<Addon_ReturnTypeFramework<unknown>>;` | `[SRC:code/core/src/types/modules/addons.ts:L106]` |
| `Addon_Loaders` | interface | `export interface Addon_Loaders<API> {` | `[SRC:code/core/src/types/modules/addons.ts:L467]` |
| `Addon_LoadFn` | type | `export type Addon_LoadFn = () => any;` | `[SRC:code/core/src/types/modules/addons.ts:L160]` |
| `Addon_MakeDecoratorResult` | type | `export type Addon_MakeDecoratorResult = (...args: any) => any;` | `[SRC:code/core/src/types/modules/addons.ts:L121]` |
| `Addon_OptionsParameter` | interface | `export interface Addon_OptionsParameter extends Object {` | `[SRC:code/core/src/types/modules/addons.ts:L63]` |
| `Addon_OptionsParameterV7` | interface | `export interface Addon_OptionsParameterV7 extends Object {` | `[SRC:code/core/src/types/modules/addons.ts:L72]` |
| `Addon_PageType` | interface | `export interface Addon_PageType {` | `[SRC:code/core/src/types/modules/addons.ts:L393]` |
| `Addon_PartialStoryFn` | type | `export type Addon_PartialStoryFn<ReturnType = unknown> = PartialStoryFnForFramework<Addon_ReturnTypeFramework<ReturnType>>;` | `[SRC:code/core/src/types/modules/addons.ts:L90]` |
| `Addon_RenderOptions` | interface | `export interface Addon_RenderOptions {` | `[SRC:code/core/src/types/modules/addons.ts:L320]` |
| `Addon_RequireContext` | type | `export type Addon_RequireContext = any;` | `[SRC:code/core/src/types/modules/addons.ts:L161]` |
| `Addon_StoryApi` | interface | `export interface Addon_StoryApi<StoryFnReturnType = unknown> {` | `[SRC:code/core/src/types/modules/addons.ts:L143]` |
| `Addon_StoryContext` | type | `export type Addon_StoryContext<TRenderer extends Renderer = Renderer> =` | `[SRC:code/core/src/types/modules/addons.ts:L81]` |
| `Addon_StoryContextUpdate` | type | `export type Addon_StoryContextUpdate = Partial<Addon_StoryContext>;` | `[SRC:code/core/src/types/modules/addons.ts:L83]` |
| `Addon_StoryFn` | type | `export type Addon_StoryFn<ReturnType = unknown> = StoryFnForFramework<Addon_ReturnTypeFramework<ReturnType>>;` | `[SRC:code/core/src/types/modules/addons.ts:L99]` |
| `Addon_StorySortComparator` | type | `export type Addon_StorySortComparator = Addon_Comparator<IndexEntryLegacy>;` | `[SRC:code/core/src/types/modules/addons.ts:L54]` |
| `Addon_StorySortComparatorV7` | type | `export type Addon_StorySortComparatorV7 = Addon_Comparator<IndexEntry>;` | `[SRC:code/core/src/types/modules/addons.ts:L56]` |
| `Addon_StorySortMethod` | type | `export type Addon_StorySortMethod = 'configure' \| 'alphabetical';` | `[SRC:code/core/src/types/modules/addons.ts:L43]` |
| `Addon_StorySortObjectParameter` | interface | `export interface Addon_StorySortObjectParameter {` | `[SRC:code/core/src/types/modules/addons.ts:L44]` |
| `Addon_StorySortParameter` | type | `export type Addon_StorySortParameter = Addon_StorySortComparator \| Addon_StorySortObjectParameter;` | `[SRC:code/core/src/types/modules/addons.ts:L55]` |
| `Addon_StorySortParameterV7` | type | `export type Addon_StorySortParameterV7 =` | `[SRC:code/core/src/types/modules/addons.ts:L57]` |
| `Addon_StoryWrapper` | type | `export type Addon_StoryWrapper = (storyFn: Addon_LegacyStoryFn, context: Addon_StoryContext, settings: Addon_WrapperSettings) => any;` | `[SRC:code/core/src/types/modules/addons.ts:L115]` |
| `Addon_TestProviderType` | interface | `export interface Addon_TestProviderType {` | `[SRC:code/core/src/types/modules/addons.ts:L444]` |
| `Addon_ToolbarConfig` | interface | `export interface Addon_ToolbarConfig {` | `[SRC:code/core/src/types/modules/addons.ts:L476]` |
| `Addon_Type` | type | `export type Addon_Type =` | `[SRC:code/core/src/types/modules/addons.ts:L324]` |
| `Addon_Types` | type | `export type Addon_Types = Exclude<Addon_TypesEnum, Addon_TypesEnum.experimental_PAGE \| Addon_TypesEnum.experimental_TEST_PROVIDER>;` | `[SRC:code/core/src/types/modules/addons.ts:L26]` |
| `Addon_TypesEnum` | enum | `export enum Addon_TypesEnum {` | `[SRC:code/core/src/types/modules/addons.ts:L493]` |
| `Addon_TypesMapping` | interface | `export interface Addon_TypesMapping extends Record<Addon_TypeBaseNames, Addon_BaseType> {` | `[SRC:code/core/src/types/modules/addons.ts:L459]` |
| `Addon_WrapperSettings` | interface | `export interface Addon_WrapperSettings {` | `[SRC:code/core/src/types/modules/addons.ts:L108]` |
| `Addon_WrapperType` | interface | `export interface Addon_WrapperType {` | `[SRC:code/core/src/types/modules/addons.ts:L425]` |
| `Addons_ArgTypes` | type | `export type Addons_ArgTypes<TArgs = Args> = {` | `[SRC:code/core/src/types/modules/addons.ts:L35]` |
| `API_ActiveTabsType` | type | `export type API_ActiveTabsType = 'sidebar' \| 'canvas' \| 'addons';` | `[SRC:code/core/src/types/modules/api.ts:L111]` |
| `API_BaseEntry` | interface | `export interface API_BaseEntry {` | `[SRC:code/core/src/types/modules/api-stories.ts:L6]` |
| `API_ComponentEntry` | interface | `export interface API_ComponentEntry extends API_BaseEntry {` | `[SRC:code/core/src/types/modules/api-stories.ts:L27]` |
| `API_ComposedRef` | interface | `export interface API_ComposedRef extends API_LoadedRefData {` | `[SRC:code/core/src/types/modules/api.ts:L163]` |
| `API_ComposedRefUpdate` | type | `export type API_ComposedRefUpdate = Partial<Pick<API_ComposedRef, \| 'title' \| 'type' \| 'expanded' \| 'index' \| 'filteredIndex' \| 'versions' \| 'loginUrl' \| 'version' \| 'indexError' \| 'previewInitialized' \| 'sourceUrl' \| 'internal_index'>>;` | `[SRC:code/core/src/types/modules/api.ts:L177]` |
| `API_DocsEntry` | interface | `export interface API_DocsEntry extends API_BaseEntry {` | `[SRC:code/core/src/types/modules/api-stories.ts:L34]` |
| `API_FilterFunction` | type | `export type API_FilterFunction = (item: API_PreparedIndexEntry & { statuses: StatusByTypeId }) => boolean;` | `[SRC:code/core/src/types/modules/api-stories.ts:L128]` |
| `API_GroupEntry` | interface | `export interface API_GroupEntry extends API_BaseEntry {` | `[SRC:code/core/src/types/modules/api-stories.ts:L21]` |
| `API_HashEntry` | type | `export type API_HashEntry =` | `[SRC:code/core/src/types/modules/api-stories.ts:L67]` |
| `API_IframeRenderer` | type | `export type API_IframeRenderer = (storyId: string, viewMode: API_ViewMode, id: string, baseUrl: string, scale: number, queryParams: Record<string, any>) => ReactElement<any, any> \| null;` | `[SRC:code/core/src/types/modules/api.ts:L57]` |
| `API_IndexHash` | interface | `export interface API_IndexHash {` — The `IndexHash` is our manager-side representation of the `StoryIndex`. | `[SRC:code/core/src/types/modules/api-stories.ts:L80]` |
| `API_Layout` | interface | `export interface API_Layout {` | `[SRC:code/core/src/types/modules/api.ts:L79]` |
| `API_LayoutCustomisations` | interface | `export interface API_LayoutCustomisations {` | `[SRC:code/core/src/types/modules/api.ts:L98]` |
| `API_LeafEntry` | type | `export type API_LeafEntry = API_DocsEntry \| API_StoryEntry \| API_TestEntry;` | `[SRC:code/core/src/types/modules/api-stories.ts:L66]` |
| `API_LoadedRefData` | interface | `export interface API_LoadedRefData {` | `[SRC:code/core/src/types/modules/api.ts:L156]` |
| `API_MatchOptions` | interface | `export interface API_MatchOptions {` | `[SRC:code/core/src/types/modules/api.ts:L30]` |
| `API_Notification` | interface | `export interface API_Notification {` | `[SRC:code/core/src/types/modules/api.ts:L132]` |
| `API_OptionsData` | type | `export type API_OptionsData = {` | `[SRC:code/core/src/types/modules/api-stories.ts:L96]` |
| `API_PanelPositions` | type | `export type API_PanelPositions = 'bottom' \| 'right';` | `[SRC:code/core/src/types/modules/api.ts:L110]` |
| `API_PreparedIndexEntry` | type | `export type API_PreparedIndexEntry = IndexEntry & {` | `[SRC:code/core/src/types/modules/api-stories.ts:L85]` |
| `API_PreparedStoryIndex` | interface | `export interface API_PreparedStoryIndex {` | `[SRC:code/core/src/types/modules/api-stories.ts:L91]` |
| `API_Provider` | interface | `export interface API_Provider<API> {` | `[SRC:code/core/src/types/modules/api.ts:L44]` |
| `API_ProviderData` | interface | `export interface API_ProviderData<API> {` | `[SRC:code/core/src/types/modules/api.ts:L39]` |
| `API_RefId` | type | `export type API_RefId = string;` | `[SRC:code/core/src/types/modules/api.ts:L196]` |
| `API_Refs` | type | `export type API_Refs = Record<string, API_ComposedRef>;` | `[SRC:code/core/src/types/modules/api.ts:L195]` |
| `API_RefUrl` | type | `export type API_RefUrl = string;` | `[SRC:code/core/src/types/modules/api.ts:L197]` |
| `API_ReleaseNotes` | interface | `export interface API_ReleaseNotes {` | `[SRC:code/core/src/types/modules/api-stories.ts:L100]` |
| `API_RenderOptions` | type | `export type API_RenderOptions = Addon_RenderOptions;` | `[SRC:code/core/src/types/modules/api.ts:L22]` |
| `API_RootEntry` | interface | `export interface API_RootEntry extends API_BaseEntry {` | `[SRC:code/core/src/types/modules/api-stories.ts:L15]` |
| `API_RouteOptions` | interface | `export interface API_RouteOptions {` | `[SRC:code/core/src/types/modules/api.ts:L24]` |
| `API_SetRefData` | type | `export type API_SetRefData = Partial<API_ComposedRef & { setStoriesData: SetStoriesStoryData; storyIndex: StoryIndex; }>;` | `[SRC:code/core/src/types/modules/api.ts:L147]` |
| `API_Settings` | interface | `export interface API_Settings {` | `[SRC:code/core/src/types/modules/api-stories.ts:L106]` |
| `API_SidebarOptions` | interface | `export interface API_SidebarOptions<API = any> {` | `[SRC:code/core/src/types/modules/api.ts:L113]` |
| `API_StateMerger` | type | `export type API_StateMerger<S> = (input: S) => S;` | `[SRC:code/core/src/types/modules/api.ts:L37]` |
| `API_StoryEntry` | interface | `export interface API_StoryEntry extends API_BaseEntry {` | `[SRC:code/core/src/types/modules/api-stories.ts:L45]` |
| `API_StoryMapper` | type | `export type API_StoryMapper = (ref: API_ComposedRef, story: SetStoriesStory) => SetStoriesStory;` | `[SRC:code/core/src/types/modules/api.ts:L154]` |
| `API_TestEntry` | interface | `export interface API_TestEntry extends Omit<API_StoryEntry, 'subtype' \| 'children'> {` | `[SRC:code/core/src/types/modules/api-stories.ts:L62]` |
| `API_UI` | interface | `export interface API_UI {` | `[SRC:code/core/src/types/modules/api.ts:L104]` |
| `API_UIOptions` | interface | `export interface API_UIOptions {` | `[SRC:code/core/src/types/modules/api.ts:L66]` |
| `API_UnknownEntries` | interface | `export interface API_UnknownEntries {` | `[SRC:code/core/src/types/modules/api-stories.ts:L116]` |
| `API_Version` | interface | `export interface API_Version {` | `[SRC:code/core/src/types/modules/api-stories.ts:L110]` |
| `API_Versions` | interface | `export interface API_Versions {` | `[SRC:code/core/src/types/modules/api-stories.ts:L122]` |
| `API_ViewMode` | type | `export type API_ViewMode = OrString<'story' \| 'docs' \| 'settings'> \| undefined;` | `[SRC:code/core/src/types/modules/api.ts:L20]` |
| `BaseIndexEntry` | interface | `export interface BaseIndexEntry {` | `[SRC:code/core/src/types/modules/indexer.ts:L67]` |
| `BaseIndexInput` | type | `export type BaseIndexInput = {` — The base input for indexing a story or docs entry. | `[SRC:code/core/src/types/modules/indexer.ts:L105]` |
| `BaseStory` | type | `export type BaseStory<TArgs, StoryFnReturnType> =` | `[SRC:code/core/src/types/modules/addons.ts:L316]` |
| `BoundStory` | type | `export type BoundStory<TRenderer extends Renderer = Renderer> = PreparedStory<TRenderer> & {` | `[SRC:code/core/src/types/modules/story.ts:L124]` |
| `Builder` | interface | `export interface Builder<Config, BuilderStats extends Stats = Stats> {` | `[SRC:code/core/src/types/modules/core-common.ts:L259]` |
| `Builder_EnvsRaw` | type | `export type Builder_EnvsRaw = Record<string, string>;` | `[SRC:code/core/src/types/modules/builder.ts:L12]` |
| `Builder_Unpromise` | type | `export type Builder_Unpromise<T extends Promise<any>> = T extends Promise<infer U> ? U : never;` | `[SRC:code/core/src/types/modules/builder.ts:L10]` |
| `Builder_WithRequiredProperty` | type | `export type Builder_WithRequiredProperty<Type, Key extends keyof Type> = Type & {` | `[SRC:code/core/src/types/modules/builder.ts:L6]` |
| `BuilderName` | type | `export type BuilderName = 'webpack5' \| '@storybook/builder-webpack5' \| string;` | `[SRC:code/core/src/types/modules/core-common.ts:L20]` |
| `BuilderResult` | interface | `export interface BuilderResult {` | `[SRC:code/core/src/types/modules/core-common.ts:L156]` |
| `BuilderStats` | interface | `export interface BuilderStats {` | `[SRC:code/core/src/types/modules/builder.ts:L1]` |
| `CLIBaseOptions` | interface | `export interface CLIBaseOptions {` | `[SRC:code/core/src/types/modules/core-common.ts:L175]` |
| `CLIOptions` | interface | `export interface CLIOptions extends CLIBaseOptions {` | `[SRC:code/core/src/types/modules/core-common.ts:L184]` |
| `CompatibleString` | type | `export type CompatibleString<T extends string> = T \| (string & {});` — Given a generic string type, returns that type but ensures that a string in general is compatible with it. | `[SRC:code/core/src/types/modules/core-common.ts:L739]` |
| `ComponentManifest` | interface | `export interface ComponentManifest {` | `[SRC:code/core/src/types/modules/core-common.ts:L357]` |
| `ComponentsManifest` | interface | `export interface ComponentsManifest {` | `[SRC:code/core/src/types/modules/core-common.ts:L375]` |
| `ComposedStoryFn` | type | `export type ComposedStoryFn<TRenderer extends Renderer = Renderer, TArgs = Args> = PartialArgsStoryFn<TRenderer, TArgs> & {` — A story that got recomposed for portable stories, containing all the necessary data to be rendered in external environments | `[SRC:code/core/src/types/modules/composedStory.ts:L40]` |
| `ComposeStoryFn` | interface | `export interface ComposeStoryFn<TRenderer extends Renderer = Renderer, TArgs extends Args = Args> {` — Type used for integrators of portable stories, as reference when creating their own composeStory function | `[SRC:code/core/src/types/modules/composedStory.ts:L76]` |
| `CoreCommon_AddonEntry` | type | `export type CoreCommon_AddonEntry = string \| CoreCommon_OptionsEntry;` | `[SRC:code/core/src/types/modules/core-common.ts:L706]` |
| `CoreCommon_AddonInfo` | type | `export type CoreCommon_AddonInfo = { name: string; inEssentials: boolean };` | `[SRC:code/core/src/types/modules/core-common.ts:L707]` |
| `CoreCommon_OptionsEntry` | type | `export type CoreCommon_OptionsEntry = { name: string };` | `[SRC:code/core/src/types/modules/core-common.ts:L705]` |
| `CoreCommon_ResolvedAddonPreset` | interface | `export interface CoreCommon_ResolvedAddonPreset {` | `[SRC:code/core/src/types/modules/core-common.ts:L690]` |
| `CoreCommon_ResolvedAddonVirtual` | interface | `export interface CoreCommon_ResolvedAddonVirtual {` | `[SRC:code/core/src/types/modules/core-common.ts:L697]` |
| `CoreCommon_StorybookInfo` | interface | `export interface CoreCommon_StorybookInfo {` | `[SRC:code/core/src/types/modules/core-common.ts:L709]` |
| `CoreConfig` | interface | `export interface CoreConfig {` | `[SRC:code/core/src/types/modules/core-common.ts:L23]` |
| `CoreWebpackCompiler` | enum | `export enum CoreWebpackCompiler {` | `[SRC:code/core/src/types/modules/webpack.ts:L1]` |
| `CsfEnricher` | type | `export type CsfEnricher = (csf: CsfFile, csfSource: CsfFile) => Promise<void>;` | `[SRC:code/core/src/types/modules/core-common.ts:L388]` |
| `DocsIndexEntry` | type | `export type DocsIndexEntry = BaseIndexEntry & {` | `[SRC:code/core/src/types/modules/indexer.ts:L83]` |
| `DocsIndexInput` | type | `export type DocsIndexInput = BaseIndexInput & {` — The input for indexing a docs entry. | `[SRC:code/core/src/types/modules/indexer.ts:L145]` |
| `DocsOptions` | type | `export type DocsOptions = {` | `[SRC:code/core/src/types/modules/core-common.ts:L313]` |
| `DocsPreparedPayload` | interface | `export interface DocsPreparedPayload {` | `[SRC:code/core/src/types/modules/channelApi.ts:L75]` |
| `DocsRenderFunction` | type | `export type DocsRenderFunction<TRenderer extends Renderer> = (docsContext: DocsContextProps<TRenderer>, docsParameters: Parameters, element: HTMLElement) => Promise<void>;` | `[SRC:code/core/src/types/modules/docs.ts:L109]` |
| `Entry` | type | `export type Entry = string;` — An additional script that gets injected into the preview or the manager, | `[SRC:code/core/src/types/modules/core-common.ts:L306]` |
| `Event` | type | `export type Event<TState, TEvent extends BaseEvent> = TEvent \| InternalEvent<TState>;` | `[SRC:code/core/src/shared/universal-store/types.ts:L58]` |
| `EventInfo` | type | `export type EventInfo = {` | `[SRC:code/core/src/shared/universal-store/types.ts:L16]` |
| `Feature` | enum | `export enum Feature {` | `[SRC:code/core/src/types/modules/features.ts:L1]` |
| `FilterFunction` | type | `export type FilterFunction = (entry: API_PreparedIndexEntry, excluded?: boolean) => boolean;` | `[SRC:code/core/src/types/modules/api.ts:L77]` |
| `GlobalsUpdatedPayload` | interface | `export interface GlobalsUpdatedPayload {` | `[SRC:code/core/src/types/modules/channelApi.ts:L60]` |
| `IndexedCSFFile` | interface | `export interface IndexedCSFFile {` | `[SRC:code/core/src/types/modules/indexer.ts:L38]` |
| `IndexedStory` | interface | `export interface IndexedStory {` | `[SRC:code/core/src/types/modules/indexer.ts:L32]` |
| `IndexEntry` | type | `export type IndexEntry = StoryIndexEntry \| DocsIndexEntry;` | `[SRC:code/core/src/types/modules/indexer.ts:L88]` |
| `IndexEntryLegacy` | type | `export type IndexEntryLegacy = [StoryId, any, Parameters, Parameters];` | `[SRC:code/core/src/types/modules/addons.ts:L53]` |
| `Indexer` | type | `export type Indexer = BaseIndexer & {` — An indexer describes which filenames it handles, and how to index each individual file - turning it into an entry in the index. | `[SRC:code/core/src/types/modules/indexer.ts:L56]` |
| `IndexerOptions` | interface | `export interface IndexerOptions {` | `[SRC:code/core/src/types/modules/indexer.ts:L28]` |
| `IndexInput` | type | `export type IndexInput = StoryIndexInput \| DocsIndexInput;` | `[SRC:code/core/src/types/modules/indexer.ts:L151]` |
| `IndexInputStats` | interface | `export interface IndexInputStats {` | `[SRC:code/core/src/types/modules/indexer.ts:L90]` |
| `LoadedPreset` | interface | `export interface LoadedPreset {` | `[SRC:code/core/src/types/modules/core-common.ts:L122]` |
| `LoadOptions` | interface | `export interface LoadOptions {` | `[SRC:code/core/src/types/modules/core-common.ts:L165]` |
| `Manifests` | type | `export type Manifests = { components?: ComponentsManifest } & Record<ManifestName, unknown>;` | `[SRC:code/core/src/types/modules/core-common.ts:L386]` |
| `Middleware` | type | `export type Middleware<T extends IncomingMessage = IncomingMessage> = (req: T & IncomingMessage, res: ServerResponse, next: (err?: string \| Error) => Promise<void> \| void) => Promise<void> \| void;` | `[SRC:code/core/src/types/modules/core-common.ts:L236]` |
| `ModuleExport` | type | `export type ModuleExport = any;` | `[SRC:code/core/src/types/modules/story.ts:L32]` |
| `ModuleExports` | type | `export type ModuleExports = Record<string, ModuleExport>;` | `[SRC:code/core/src/types/modules/story.ts:L33]` |
| `ModuleImportFn` | type | `export type ModuleImportFn = (path: Path) => Promise<ModuleExports>;` | `[SRC:code/core/src/types/modules/story.ts:L34]` |
| `NamedOrDefaultProjectAnnotations` | type | `export type NamedOrDefaultProjectAnnotations<TRenderer extends Renderer = Renderer> =` | `[SRC:code/core/src/types/modules/story.ts:L52]` |
| `NormalizedStoriesSpecifier` | type | `export type NormalizedStoriesSpecifier = Required<StoriesSpecifier> & {` | `[SRC:code/core/src/types/modules/indexer.ts:L20]` |
| `PartialArgsStoryFn` | type | `export type PartialArgsStoryFn<TRenderer extends Renderer = Renderer, TArgs = Args> = (args?: TArgs) => (TRenderer & { T: TArgs; })['storyResult'];` — A story function with partial args, used internally by composeStory | `[SRC:code/core/src/types/modules/composedStory.ts:L30]` |
| `Path` | type | `export type Path = string;` | `[SRC:code/core/src/types/modules/csf.ts:L94]` |
| `PreparedMeta` | type | `export type PreparedMeta<TRenderer extends Renderer = Renderer> = Omit<StoryContextForEnhancers<TRenderer>, 'name' \| 'story'> & {` | `[SRC:code/core/src/types/modules/story.ts:L117]` |
| `Preset` | type | `export type Preset =` | `[SRC:code/core/src/types/modules/core-common.ts:L298]` |
| `PresetConfig` | type | `export type PresetConfig =` | `[SRC:code/core/src/types/modules/core-common.ts:L128]` |
| `PresetProperty` | type | `export type PresetProperty<K, TStorybookConfig = StorybookConfigRaw> =` | `[SRC:code/core/src/types/modules/core-common.ts:L679]` |
| `PresetPropertyFn` | type | `export type PresetPropertyFn<K, TStorybookConfig = StorybookConfigRaw, TOptions = {}> = (config: TStorybookConfig[K extends keyof TStorybookConfig ? K : never], options: Options & TOptions) =>` | `[SRC:code/core/src/types/modules/core-common.ts:L683]` |
| `Presets` | interface | `export interface Presets {` | `[SRC:code/core/src/types/modules/core-common.ts:L72]` |
| `PresetValue` | type | `export type PresetValue<T> = T \| ((config: T, options: Options) => T \| Promise<T>);` | `[SRC:code/core/src/types/modules/core-common.ts:L677]` |
| `PreviewAnnotation` | type | `export type PreviewAnnotation = string \| { bare: string; absolute: string };` | `[SRC:code/core/src/types/modules/core-common.ts:L695]` |
| `Ref` | interface | `export interface Ref {` | `[SRC:code/core/src/types/modules/core-common.ts:L135]` |
| `RenderContextCallbacks` | type | `export type RenderContextCallbacks<TRenderer extends Renderer> = Pick<RenderContext<TRenderer>, 'showMain' \| 'showError' \| 'showException'>;` | `[SRC:code/core/src/types/modules/docs.ts:L14]` |
| `RendererName` | type | `export type RendererName = string;` | `[SRC:code/core/src/types/modules/core-common.ts:L21]` |
| `ResolvedModuleExport` | type | `export type ResolvedModuleExport<TRenderer extends Renderer = Renderer> = {` | `[SRC:code/core/src/types/modules/docs.ts:L47]` |
| `ResolvedModuleExportFromType` | type | `export type ResolvedModuleExportFromType<TType extends ResolvedModuleExportType, TRenderer extends Renderer = Renderer> = TType extends 'component'` — What do we know about an of={} call? | `[SRC:code/core/src/types/modules/docs.ts:L34]` |
| `ResolvedModuleExportType` | type | `export type ResolvedModuleExportType = 'component' \| 'meta' \| 'story';` | `[SRC:code/core/src/types/modules/docs.ts:L24]` |
| `ServerApp` | interface | `export interface ServerApp<T extends IncomingMessage = IncomingMessage> {` | `[SRC:code/core/src/types/modules/core-common.ts:L242]` |
| `SetGlobalsPayload` | interface | `export interface SetGlobalsPayload {` | `[SRC:code/core/src/types/modules/channelApi.ts:L54]` |
| `SetStoriesPayload` | type | `export type SetStoriesPayload =` | `[SRC:code/core/src/types/modules/channelApi.ts:L38]` |
| `SetStoriesStory` | interface | `export interface SetStoriesStory {` | `[SRC:code/core/src/types/modules/channelApi.ts:L14]` |
| `SetStoriesStoryData` | interface | `export interface SetStoriesStoryData {` | `[SRC:code/core/src/types/modules/channelApi.ts:L34]` |
| `Stats` | interface | `export interface Stats {` | `[SRC:code/core/src/types/modules/core-common.ts:L152]` |
| `Status` | interface | `export interface Status {` | `[SRC:code/core/src/shared/status-store/index.ts:L20]` |
| `StatusByTypeId` | type | `export type StatusByTypeId = Record<StatusTypeId, Status>;` | `[SRC:code/core/src/shared/status-store/index.ts:L17]` |
| `StatusesByStoryIdAndTypeId` | type | `export type StatusesByStoryIdAndTypeId = Record<StoryId, StatusByTypeId>;` | `[SRC:code/core/src/shared/status-store/index.ts:L18]` |
| `StatusStore` | type | `export type StatusStore = {` | `[SRC:code/core/src/shared/status-store/index.ts:L45]` |
| `StatusStoreByTypeId` | type | `export type StatusStoreByTypeId = StatusStore & {` | `[SRC:code/core/src/shared/status-store/index.ts:L61]` |
| `StatusTypeId` | type | `export type StatusTypeId = string;` | `[SRC:code/core/src/shared/status-store/index.ts:L16]` |
| `StatusValue` | type | `export type StatusValue =` | `[SRC:code/core/src/shared/status-store/index.ts:L9]` |
| `Store_CSFExports` | type | `export type Store_CSFExports<TRenderer extends Renderer = Renderer, TArgs extends Args = Args> = {` | `[SRC:code/core/src/types/modules/composedStory.ts:L23]` |
| `StoriesEntry` | type | `export type StoriesEntry = string \| StoriesSpecifier;` | `[SRC:code/core/src/types/modules/indexer.ts:L18]` |
| `StoriesSpecifier` | interface | `export interface StoriesSpecifier {` | `[SRC:code/core/src/types/modules/indexer.ts:L6]` |
| `StoriesWithPartialProps` | type | `export type StoriesWithPartialProps<TRenderer extends Renderer, TModule> = {` — Based on a module of stories, it returns all stories within it, filtering non-stories Each story will have partial props, as their props should be handled when composing stories | `[SRC:code/core/src/types/modules/composedStory.ts:L60]` |
| `StorybookConfigOptions` | interface | `export interface StorybookConfigOptions {` | `[SRC:code/core/src/types/modules/core-common.ts:L224]` |
| `StorybookConfigRaw` | interface | `export interface StorybookConfigRaw {` | `[SRC:code/core/src/types/modules/core-common.ts:L390]` |
| `StorybookInternalParameters` | interface | `export interface StorybookInternalParameters extends StorybookParameters {` | `[SRC:code/core/src/types/modules/csf.ts:L89]` |
| `StorybookTypes` | interface | `export interface StorybookTypes {` | `[SRC:code/core/src/types/modules/csf.ts:L85]` |
| `StoryIndex` | interface | `export interface StoryIndex {` | `[SRC:code/core/src/types/modules/indexer.ts:L174]` |
| `StoryIndexEntry` | type | `export type StoryIndexEntry = BaseIndexEntry & {` | `[SRC:code/core/src/types/modules/indexer.ts:L74]` |
| `StoryIndexInput` | type | `export type StoryIndexInput = BaseIndexInput & {` — The input for indexing a story entry. | `[SRC:code/core/src/types/modules/indexer.ts:L137]` |
| `StoryIndexV2` | interface | `export interface StoryIndexV2 {` | `[SRC:code/core/src/types/modules/indexer.ts:L159]` |
| `StoryIndexV3` | interface | `export interface StoryIndexV3 {` | `[SRC:code/core/src/types/modules/indexer.ts:L169]` |
| `StoryPreparedPayload` | interface | `export interface StoryPreparedPayload {` | `[SRC:code/core/src/types/modules/channelApi.ts:L67]` |
| `StoryRenderOptions` | type | `export type StoryRenderOptions = {` | `[SRC:code/core/src/types/modules/docs.ts:L19]` |
| `SupportedBuilder` | enum | `export enum SupportedBuilder {` | `[SRC:code/core/src/types/modules/builders.ts:L1]` |
| `SupportedFramework` | enum | `export enum SupportedFramework {` | `[SRC:code/core/src/types/modules/frameworks.ts:L2]` |
| `SupportedRenderer` | enum | `export enum SupportedRenderer {` | `[SRC:code/core/src/types/modules/renderers.ts:L1]` |
| `TagOptions` | interface | `export interface TagOptions {` | `[SRC:code/core/src/types/modules/core-common.ts:L348]` |
| `TagsOptions` | type | `export type TagsOptions = Record<Tag, Partial<TagOptions>>;` | `[SRC:code/core/src/types/modules/core-common.ts:L355]` |
| `TeardownRenderToCanvas` | type | `export type TeardownRenderToCanvas = () => MaybePromise<void>;` | `[SRC:code/core/src/types/modules/story.ts:L37]` |
| `TestBuildConfig` | interface | `export interface TestBuildConfig {` | `[SRC:code/core/src/types/modules/core-common.ts:L342]` |
| `TestBuildFlags` | interface | `export interface TestBuildFlags {` | `[SRC:code/core/src/types/modules/core-common.ts:L320]` |
| `TestProviderId` | type | `export type TestProviderId = string;` | `[SRC:code/core/src/shared/test-provider-store/index.ts:L16]` |
| `TestProviderState` | type | `export type TestProviderState =` | `[SRC:code/core/src/shared/test-provider-store/index.ts:L11]` |
| `TestProviderStateByProviderId` | type | `export type TestProviderStateByProviderId = Record<TestProviderId, TestProviderState>;` | `[SRC:code/core/src/shared/test-provider-store/index.ts:L17]` |
| `TestProviderStoreById` | type | `export type TestProviderStoreById = BaseTestProviderStore & {` — Represents a store for a specific test provider, identified by its unique ID. | `[SRC:code/core/src/shared/test-provider-store/index.ts:L199]` |
| `TypescriptOptions` | interface | `export interface TypescriptOptions {` — Options for TypeScript usage within Storybook. | `[SRC:code/core/src/types/modules/core-common.ts:L282]` |
| `UniversalStore` | class | `export class UniversalStore<State, CustomEvent extends { type: string; payload?: any } = { type: string; payload?: any }> {` — A universal store implementation that synchronizes state across different environments using a channel-based communication. | `[SRC:code/core/src/shared/universal-store/index.ts:L82]` |
| `UseStatusStore` | type | `export type UseStatusStore = <T = StatusesByStoryIdAndTypeId>(selector?: (statuses: StatusesByStoryIdAndTypeId) => T) => T;` | `[SRC:code/core/src/shared/status-store/index.ts:L67]` |
| `UseTestProviderStore` | type | `` export type UseTestProviderStore = <T = TestProviderStateByProviderId>(/** * Optional selector function to extract or transform specific parts of the state * * @example * * ```typescript * * const allProviderStates = useTestProviderStore(); * * * const myProviderState = useTestProviderStore((state) => state['my-test-provider']); * * * const statusCounts = useTestProviderStore((state) => { *   const counts = { *     pending: 0, *     running: 0, *     succeeded: 0, *     crashed: 0, *   }; * *   Object.values(state).forEach((status) => { *     if (status === 'test-provider-state:pending') counts.pending++; *     else if (status === 'test-provider-state:running') counts.running++; *     else if (status === 'test-provider-state:succeeded') counts.succeeded++; *     else if (status === 'test-provider-state:crashed') counts.crashed++; *   }); * *   return counts; * }); * * * const allTestsCompleted = useTestProviderStore((state) => { *   return Object.values(state).every(*     (status) => *       status === 'test-provider-state:succeeded' \|\| *       status === 'test-provider-state:crashed' *   ); * }); `` — React OR preview hook for accessing the state of _all_ test providers. | `[SRC:code/core/src/shared/test-provider-store/index.ts:L330]` |
| `V3CompatIndexEntry` | interface | `export interface V3CompatIndexEntry extends Omit<StoryIndexEntry, 'type' \| 'tags' \| 'subtype'> {` | `[SRC:code/core/src/types/modules/indexer.ts:L153]` |
| `VersionCheck` | interface | `export interface VersionCheck {` | `[SRC:code/core/src/types/modules/core-common.ts:L144]` |
