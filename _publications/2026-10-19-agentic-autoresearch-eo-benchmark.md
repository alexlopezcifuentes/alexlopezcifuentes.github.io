---
title: "Evaluation of Agentic Autoresearch in an Earth Observation Benchmark"
collection: publications
category: conferences
permalink: /publication/2026-agentic-autoresearch-eo-benchmark
excerpt: 'The first agentic autoresearch framework for Earth observation model development: autonomous agents that download, build, train and evaluate models on the PANGAEA benchmark, reaching state of the art on four datasets.'
date: 2026-10-19
venue: 'Agentic AI for Earth Observation Workshop (BIFOLD and the European Space Agency), Berlin'
citation: 'Alejandro López-Cifuentes, Juan Ignacio Bravo Pérez-Villar. (2026). &quot;Evaluation of Agentic Autoresearch in an Earth Observation Benchmark.&quot; <i>Agentic AI for Earth Observation Workshop</i>, Berlin. Oral presentation.'
---

Accepted as an **oral presentation** at the [Agentic AI for Earth Observation Workshop](https://agentic-eo.berlin/), organised by BIFOLD and the European Space Agency in Berlin, 19–21 October 2026.

Agentic frameworks have reached Earth observation, but so far they *solve* tasks with pre-existing models rather than *build* better ones. This work asks the other question: what happens if you put the agentic loop in charge of discovering the model?

We introduce the first agentic autoresearch framework for EO model development, in which autonomous agents iteratively download, build, train and evaluate models on the [PANGAEA benchmark](https://arxiv.org/abs/2412.04204). It runs in two modes — a recipe-only search over a fixed UNet, and a free-architecture search that settles on a pretrained DOFA-Large.

Against 22 pretrained foundation models and the from-scratch baselines, both agents produce the highest `#Top2` count on the benchmark. The UNet run reaches state of the art on Sen1Floods11, SpaceNet7 and AI4SmallFarms; the DOFA run on FiveBillionPixels.

Joint work with Juan Ignacio Bravo Pérez-Villar at Xoople.
