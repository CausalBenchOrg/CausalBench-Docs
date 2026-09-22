# CausalBench

CausalBench is an open benchmarking platform for evaluating causal-learning models with reusable datasets, metrics, and experiment definitions. It runs experiments on your own machine, records the software and hardware context, and lets collaborators reproduce a benchmark from versioned components.

!!! info "Beta software"
    CausalBench is under active development. These pages were checked against the published `causalbench-asu` 0.2.4 package and [upstream snapshot `ceb45da`](https://github.com/CausalBenchOrg/CausalBench/commit/ceb45da42db79bdc06c86de116c507e2f37fa033) from September 17, 2026, which declares the unpublished 0.2.5 version. Registry contents and permissions are live service data, so component IDs shown in papers or tutorials may not be available to every account.

## What CausalBench provides

CausalBench has two cooperating parts:

| Part | What it does |
| --- | --- |
| [Web platform](https://causalbench.org) | Browse registered datasets, models, metrics, contexts, and benchmark results. |
| [Python package](https://github.com/CausalBenchOrg/CausalBench) | Download components, execute scenarios locally, collect results and system metadata, and publish records. |

The platform is organized around a small set of versioned objects:

1. A **task** defines the input and output contract.
2. **Datasets**, **models**, and **metrics** implement that contract.
3. A **context** selects compatible components and their settings.
4. CausalBench expands the context into dataset–model **scenarios** and executes them locally.
5. A **run** records metric outputs, timing, and execution-environment information.

[Learn the mental model](concepts.md) or see the [glossary](basics.md) for precise definitions.

## Start here

If you want to run an existing benchmark:

1. [Install CausalBench and set up authentication](install.md).
2. [Run a published context](quickstart.md).
3. [Inspect, compare, and optionally publish the run](contexts.md#inspect-a-run).

If you want to contribute an experiment:

1. Read [contexts and runs](contexts.md) to understand component compatibility.
2. Package a [dataset](components/datasets.md), [model or metric](components/models-metrics.md), or [task](components/tasks.md).
3. Follow the [pre-publication checklist](reproducibility.md#before-publication).

## Minimal example

After installation, a published context can be fetched and run with four lines:

```python
from causalbench.modules import Context

context = Context(module_id=2, version=1)
run = context.execute()
print(run)
```

Fetching requires a [CausalBench account](https://causalbench.org) and network access. Execution happens on the current machine, including unsandboxed task, model, and metric code downloaded by the context; review those components first. The example deliberately does **not** publish anything; publishing is a separate, explicit step.

Context `2/1` uses the PC implementation from `gcastle`, which also imports PyTorch; follow the [quickstart prerequisites](quickstart.md#before-you-begin) before running it. Other registry models can require different third-party libraries.

## Resources

- [Browse benchmarks](https://causalbench.org/home/benchmarks)
- [Download the quickstart notebook](files/CausalBench-Quickstart.ipynb)
- [Read the papers and citation information](papers.md)
- [Report a package issue](https://github.com/CausalBenchOrg/CausalBench/issues)
- [Improve these docs](https://github.com/CausalBenchOrg/CausalBench-Docs)

## Demo video

[Watch the CausalBench demo on Google Drive](https://drive.google.com/file/d/1ichCZiSYtXG-4Q1DEVnW0pUR8nZLPo_W/preview).
