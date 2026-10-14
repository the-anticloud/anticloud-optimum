# OPTIMUM

![license](https://img.shields.io/badge/license-license-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-chip_quantization-lightgrey)

> Anticloud-hardened packaging of the upstream project `OPTIMUM` in category **CHIP QUANTIZATION**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** CHIP QUANTIZATION · **Upstream:** https://github.com/huggingface/optimum · **Upstream pin:** `0df84f23884f7c5b6cc76c0bdc9597edd306034f` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

<!---
Copyright 2025 The HuggingFace Team. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

<h1 align="center"><p>🤗 Optimum</p></h1>

<p align="center">
<a href="https://pypi.org/project/optimum/"><img alt="PyPI - License" src="https://img.shields.io/pypi/l/optimum"/></a>
<a href="https://pypi.org/project/optimum/"><img alt="PyPI - Python Version" src="https://img.shields.io/pypi/pyversions/optimum"/></a>
<a href="https://pypi.org/project/optimum/"><img alt="PyPI - Version" src="https://img.shields.io/pypi/v/optimum"/></a>
<a href="https://pypi.org/project/optimum/"><img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/optimum"/></a>
<a href="https://huggingface.co/docs/optimum/index"><img alt="Documentation" src="https://img.shields.io/website/http/huggingface.co/docs/optimum/index.svg?down_color=red&down_message=offline&up_message=online"/></a>
</p>

<p align="center">
Optimum is an extension of Transformers 🤖 Diffusers 🧨 TIMM 🖼️ and Sentence-Transformers 🤗, providing a set of optimization tools and enabling maximum efficiency to train and run models on targeted hardware, while keeping things easy to use.
</p>

## Installation

Optimum can be installed using `pip` as follows:

```bash
python -m pip install optimum
```

If you'd like to use the accelerator-specific features of Optimum, you can check the documentation and install the required dependencies according to the table below:

| Accelerator                                                                         | Installation                                                                |
| :---------------------------------------------------------------------------------- | :-------------------------------------------------------------------------- |
| [ONNX](https://huggingface.co/docs/optimum-onnx/en/index)                           | `pip install --upgrade --upgrade-strategy eager optimum[onnx]`              |
| [ONNX Runtime](https://huggingface.co/docs/optimum-onnx/onnxruntime/overview)       | `pip install --upgrade --upgrade-strategy eager optimum[onnxruntime]`       |
| [ONNX Runtime GPU](https://huggingface.co/docs/optimum-onnx/onnxruntime/overview)   | `pip install --upgrade --upgrade-strategy eager optimum[onnxruntime-gpu]`   |
| [OpenVINO](https://huggingface.co/docs/optimum/intel/index)                         | `pip install --upgrade --upgrade-strategy eager optimum[openvino]`          |
| [NVIDIA TensorRT-LLM](https://huggingface.co/docs/optimum/main/en/nvidia_overview)  | `docker run -it --gpus all --ipc host huggingface/optimum-nvidia`           |
| [AMD Instinct GPUs and Ryzen AI NPU](https://huggingface.co/docs/optimum/amd/index) | `pip install --upgrade --upgrade-strategy eager optimum[amd]`               |
| [AWS Trainum & Inferentia](https://huggingface.co/docs/optimum-neuron/index)        | `pip install --upgrade --upgrade-strategy eager optimum[neuronx]`           |
| [Intel Gaudi Accelerators (HPU)](https://huggingface.co/docs/optimum/habana/index)  | `pip install --upgrade --upgrade-strategy eager optimum[habana]`            |
| [FuriosaAI](https://huggingface.co/docs/optimum/furiosa/index)                      | `pip install --upgrade --upgrade-strategy eager optimum[furiosa]`           |

The `--upgrade --upgrade-strategy eager` option is needed to ensure the different packages are upgraded to the latest possible version.

To install from source:

```bash
python -m pip install git+https://github.com/huggingface/optimum.git
```

For the accelerator-specific features, append `optimum[accelerator_type]` to the above command:

```bash
python -m pip install optimum[onnxruntime]@git+https://github.com/huggingface/optimum.git
```

## Accelerated Inference

Optimum provides multiple tools to export and run optimized models on various ecosystems:

- [ONNX](https://huggingface.co/docs/optimum-onnx/en/onnx/usage_guides/export_a_model) / [ONNX Runtime](https://huggingface.co/docs/optimum-onnx/en/onnxruntime/usage_guides/models), one of the most popular open formats for model export, and a high-performance inference engine for deployment.
- [OpenVINO](https://huggingface.co/docs/optimum/intel/inference), a toolkit for optimizing, quantizing and deploying deep learning models on Intel hardware.
- [ExecuTorch](https://huggingface.co/docs/optimum-executorch/guides/export), PyTorch’s native solution for on-device inference across mobile and edge devices.
- [Intel Gaudi Accelerators](https://huggingface.co/docs/optimum/main/en/habana/usage_guides/accelerate_inference) enabling optimal performance on first-gen Gaudi, Gaudi2 and Gaudi3.
- [AWS Inferentia](https://huggingface.co/docs/optimum-neuron/en/guides/models) for accelerated inference on Inf2 and Inf1 instances.
- [NVIDIA TensorRT-LLM](https://huggingface.co/blog/optimum-nvidia).

The [export](https://huggingface.co/docs/optimum/exporters/overview) and optimizations can be done both programmatically and with a command line.

### ONNX + ONNX Runtime

🚨🚨🚨 ONNX integration was moved to [`optimum-onnx`](https://github.com/huggingface/optimum-onnx) so make sure to follow the installation instructions 🚨🚨🚨

Before you begin, make sure you have all the necessary libraries installed :

```bash
pip install --upgrade --upgrade-strategy eager optimum[onnx]
```

It is possible to export Transformers, Diffusers, Sentence Transformers and Timm models to the [ONNX](https://onnx.ai/) format and perform graph optimization as well as quantization easily.

For more information on

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Python** (manifests: pyproject.toml; scanned in UPSTREAM_CLONE)
- Top-level source layout: `notebooks/`, `optimum/`, `tests/`
- Snapshot size: **105 files**, **16292 lines of code** (measured; see Benchmarks)
- Primary languages: `.py` (74), `.mdx` (15), `.md` (6), `(none)` (3), `.yml` (2), `.cfg` (1)
- Upstream commit pinned for this packaging: `0df84f23884f7c5b6cc76c0bdc9597edd306034f`

---

## Installation

Optimum can be installed using `pip` as follows:

```bash
python -m pip install optimum
```

If you'd like to use the accelerator-specific features of Optimum, you can check the documentation and install the required dependencies according to the table below:

| Accelerator                                                                         | Installation                                                                |
| :---------------------------------------------------------------------------------- | :-------------------------------------------------------------------------- |
| [ONNX](https://huggingface.co/docs/optimum-onnx/en/index)                           | `pip install --upgrade --upgrade-strategy eager optimum[onnx]`              |
| [ONNX Runtime](https://huggingface.co/docs/optimum-onnx/onnxruntime/overview)       | `pip install --upgrade --upgrade-strategy eager optimum[onnxruntime]`       |
| [ONNX Runtime GPU](https://huggingface.co/docs/optimum-onnx/onnxruntime/overview)   | `pip install --upgrade --upgrade-strategy eager optimum[onnxruntime-gpu]`   |
| [OpenVINO](https://huggingface.co/docs/optimum/intel/index)                         | `pip install --upgrade --upgrade-strategy eager optimum[openvino]`          |
| [NVIDIA TensorRT-LLM](https://huggingface.co/docs/optimum/main/en/nvidia_overview)  | `docker run -it --gpus all --ipc host huggingface/optimum-nvidia`           |
| [AMD Instinct GPUs and Ryzen AI NPU](https://huggingface.co/docs/optimum/amd/index) | `pip install --upgrade --upgrade-strategy eager optimum[amd]`               |
| [AWS Trainum & Inferentia](https://huggingface.co/docs/optimum-neuron/index)        | `pip install --upgrade --upgrade-strategy eager optimum[neuronx]`           |
| [Intel Gaudi Accelerators (HPU)](https://huggingface.co/docs/optimum/habana/index)  | `pip install --upgrade --upgrade-strategy eager optimum[habana]`            |
| [FuriosaAI](https://huggingface.co/docs/optimum/furiosa/index)                      | `pip install --upgrade --upgrade-strategy eager optimum[furiosa]`           |

The `--upgrade --upgrade-strategy eager` option is needed to ensure the different packages are upgraded to the latest possible version.

To install from source:

```bash
python -m pip install git+https://github.com/huggingface/optimum.git
```

For the accelerator-specific features, append `optimum[accelerator_type]` to the above command:

```bash
python -m pip install optimum[onnxruntime]@git+https://github.com/huggingface/optimum.git
```

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

<h1 align="center"><p>🤗 Optimum</p></h1>

<p align="center">
<a href="https://pypi.org/project/optimum/"><img alt="PyPI - License" src="https://img.shields.io/pypi/l/optimum"/></a>
<a href="https://pypi.org/project/optimum/"><img alt="PyPI - Python Version" src="https://img.shields.io/pypi/pyversions/optimum"/></a>
<a href="https://pypi.org/project/optimum/"><img alt="PyPI - Version" src="https://img.shields.io/pypi/v/optimum"/></a>
<a href="https://pypi.org/project/optimum/"><img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/optimum"/></a>
<a href="https://huggingface.co/docs/optimum/index"><img alt="Documentation" src="https://img.shields.io/website/http/huggingface.co/docs/optimum/index.svg?down_color=red&down_message=offline&up_message=online"/></a>
</p>

<p align="center">
Optimum is an extension of Transformers 🤖 Diffusers 🧨 TIMM 🖼️ and Sentence-Transformers 🤗, providing a set of optimization tools and enabling maximum efficiency to train and run models on targeted hardware, while keeping things easy to use.
</p>

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

</p>

<p align="center">
Optimum is an extension of Transformers 🤖 Diffusers 🧨 TIMM 🖼️ and Sentence-Transformers 🤗, providing a set of optimization tools and enabling maximum efficiency to train and run models on targeted hardware, while keeping things easy to use.
</p>

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Python |
| Manifests detected | pyproject.toml |
| Files in snapshot | 105 |
| Lines of code | 16292 |
| Dependency references | 11 |
| Dependencies by ecosystem | pypi: 11 |
| Upstream license | Apache-2.0 |
| Overlay license | Anticommons 0.1.0 |

Top dependency references recorded in the benchmark snapshot:

| Ecosystem | Name | Version | Source file |
|-----------|------|---------|-------------|
| pypi | __version__ | =  | setup.py |
| pypi | transformers | >=4.29 | setup.py |
| pypi | torch | >=1.11 | setup.py |
| pypi | huggingface_hub | >=1.31.0 | setup.py |
| pypi | black | ~=23.1 | setup.py |
| pypi | ruff | ==0.1.5 | setup.py |
| pypi | evaluate | >=0.2.0 | setup.py |
| pypi | optimum-habana | >=1.17.0 | setup.py |
| pypi | optimum-intel | >=1.23.0 | setup.py |
| pypi | optimum-quanto | >=0.2.4 | setup.py |
| pypi | optimum-cli | =optimum.commands.optimum_cli:main | setup.py |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

No configuration section was found in the upstream readme. Configuration-relevant files detected in this project directory:

- `Makefile`
- `pyproject.toml`
- `setup.cfg`

Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

*Excerpt from upstream `CONTRIBUTING.md`:*

# How to contribute to Optimum?

Optimum is an open source project, so all contributions and suggestions are welcome.

You can contribute in many different ways: giving ideas, answering questions, reporting bugs, proposing enhancements, improving the documentation, fixing bugs,...

Many thanks in advance to every contributor.

## How to work on an open Issue?
You have the list of open Issues at: https://github.com/huggingface/optimum/issues

Some of them may have the label `help wanted`: that means that any contributor is welcomed!

If you would like to work on any of the open Issues:

1. Make sure it is not already assigned to someone else. You have the assignee (if any) on the top of the right column of the Issue page.

2. You can self-assign it by commenting on the Issue page with one of the keywords: `#take` or `#self-assign`.

3. Work on your self-assigned issue and eventually create a Pull Request.

## How to create a Pull Request?
1. Fork the [project](https://github.com/huggingface/optimum) by clicking on the 'Fork' button on the project's page. This creates a copy of the code under your GitHub user account.

2. source your fork to your local disk, and add the base project as a remote:

	```bash
	git source git@github.com:<your Github handle>/optimum.git
	cd optimum
	git remote add upstream https://github.com/huggingface/optimum.git
	```

3. Create a new branch to hold your development changes:

	```bash
	git checkout -b a-descriptive-name-for-my-changes
	```

	**do not** work on the `main` branch.

4. Set up a development environment by running the following command in a virtual environment:

	```bash
	pip install -e ".[dev]"
	```

   (If optimum was already installed in the virtual environment, remove
   it with `pip uninstall optimum` before reinstalling it in editable
   mode with the `-e` flag.)

5. Develop the features on your branch.

6. Format your code. Run black and ruff so that your newly added files look nice with the following command:

	```bash
	make style
	```

7.  Once you're happy with your changes, add the changed files using `git add` and make a commit with `git commit` to record your changes locally:

	```bash
	git add modified_file.py
	git commit
	```

	It is a good idea to sync your copy of the code with the original
	project regularly. This way you can quickly account for changes:

	```bash
	git fetch upstream
	git rebase upstream/main
    ```

   Push the changes to your account using:

   ```bash
   git push -u or

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: Apache-2.0** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
                                 Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
      otherwise, or (ii) ownership of fifty percent (50%) or more of the
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original Apache-2.0 terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `Apache-2.0` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `OPTIMUM` (category: CHIP QUANTIZATION)
- **Upstream URL:** https://github.com/huggingface/optimum
- **Pinned commit (SHA):** `0df84f23884f7c5b6cc76c0bdc9597edd306034f`
- **Branch:** main
- **Pin provenance:** GitHub API commits/main. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`a8249f49302da74f23519b4180dc2dc569eed4302ed00d7563a6c5f8717981f1`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

