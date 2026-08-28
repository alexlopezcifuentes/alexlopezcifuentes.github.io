---
title: "Temporal Sensitivity Analysis of Tessera Embeddings"
collection: publications
category: preprints
permalink: /publication/2026-tessera-temporal-sensitivity-analysis/
excerpt: 'A controlled study of how Tessera foundation-model embeddings degrade as the observation window shrinks from a full year to a single day, evaluated on LUCAS, DynamicEarthNet and PASTIS-R.'
date: 2026-08-27
venue: 'arXiv preprint arXiv:2608.27175'
paperurl: 'https://arxiv.org/abs/2608.27175'
citation: 'Julia Guerrero-Viu, Alex López-Cifuentes, Ignacio Pérez-Villar, Fabio Pacifici. (2026). &quot;Temporal Sensitivity Analysis of Tessera Embeddings.&quot; <i>arXiv:2608.27175</i>.'
---

Full-length version of the [MORSE workshop extended abstract](/publication/2026-tessera-temporal-sensitivity/) presented at CVPR 2026.

The strongest Earth observation foundation models build their embeddings from a full year of observations, which sits badly with applications that need land-use and land-cover maps updated often. We keep the [Tessera](https://openaccess.thecvf.com/content/CVPR2026/html/Feng_TESSERA_Temporal_Embeddings_of_Surface_Spectra_for_Earth_Representation_and_CVPR_2026_paper.html) encoder frozen and recompute its embeddings over shrinking observation windows, from a year down to a single day, feeding them to a linear probe and a UNet segmentation head and benchmarking against from-scratch networks on LUCAS, DynamicEarthNet and PASTIS-R.

The value of the embeddings turns out to be task-dependent. Where classes are separated by phenology, as with the crop types of PASTIS-R, they reach a mean Intersection-over-Union of 58.3, about 46% above the best from-scratch model. Where classes are temporally stable, such as forests in DynamicEarthNet and LUCAS, embedding-based and from-scratch models only match under full supervision, though the embeddings stay markedly more label-efficient.

Degradation under shorter windows is gradual and class-dependent. Contracting the window from one year to one month costs 39% of the segmentation accuracy on PASTIS-R but only 5% on DynamicEarthNet, and single-day embeddings still classify land cover in LUCAS at 3.4 times the chance level. Temporal coverage is therefore a tunable cost rather than a fixed prerequisite, which opens up near-real-time mapping and faster refresh cycles.

Joint work with Julia Guerrero-Viu, Ignacio Pérez-Villar and Fabio Pacifici at Xoople.
