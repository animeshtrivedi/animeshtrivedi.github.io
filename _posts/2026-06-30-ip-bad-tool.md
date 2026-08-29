---
layout: default
title: "💻 Enhancing support for agentic trace replay in inference-perf"
category: news
tags: whatsnew
permalink: /2026-june-ip-agent-tool/
---

## Enhancing support for error-free agentic trace replay in inference-perf 

Agentic systems getting more and more popular. However, how to benchmark them in a realistic and deterministic manner is an open question. One can always just run the workload on a real system, however, this is a time-consuming and expensive process. An alternate is to collect traces when such run is done, and replay those traces on a live LLM model. However, when replaying such traces the live model can and will behave differently than the recorded model's responses and tool call selections. Furthermore, live LLM model can sometime generate malformed tool-call response which can have dramatic effect on the trace replay. A single malformed tool call can cause subsequent requests in the trace to fail with HTTP 400, potentially invalidating entire traces and skewing benchmark results.

  * RFC [https://github.com/kubernetes-sigs/inference-perf/issues/535](https://github.com/kubernetes-sigs/inference-perf/issues/535)
  * PR [https://github.com/kubernetes-sigs/inference-perf/pull/538](https://github.com/kubernetes-sigs/inference-perf/pull/538)

I proposed a more robust way to handle malformed tool-call responses during OpenTelemetry trace replay in inference-perf. The proposed solution introduces configurable “demotion” strategies that allow inference-perf to safely continue replaying traces while handling malformed tool calls and their orphaned tool responses. This made the overall agentic trace replay in inference-perf more reliable and error-free. 