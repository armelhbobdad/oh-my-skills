[oms-cocoindex v0.3.37]|root: .claude/skills/oms-cocoindex/
|IMPORTANT: oms-cocoindex v0.3.37 — read SKILL.md before writing cocoindex code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: FlowBuilder, DataScope, DataSlice, Flow, FlowLiveUpdater, flow_def(), open_flow(), transform_flow(), init(), LlmSpec
|key-types:SKILL.md#key-types — VectorSimilarityMetric (COSINE_SIMILARITY/L2_DISTANCE/INNER_PRODUCT), LlmApiType (12 providers), GeneratedField.UUID, Vector[T, Dim], Int64/Float32/Float64
|gotchas: add_flow_def/remove_flow are DEPRECATED (use open_flow/Flow.close); cocoindex.storages is deprecated alias for cocoindex.targets; cocoindex is Alpha — API may change across minor versions, this skill is pinned to v0.3.37.
