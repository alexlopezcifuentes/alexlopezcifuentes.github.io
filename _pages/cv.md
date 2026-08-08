---
layout: archive
title: "CV"
seo_title: "CV — Alex López-Cifuentes, PhD | Computer Vision & Earth Observation"
description: "Curriculum vitae of Alex López-Cifuentes, PhD: Lead Research Scientist at Xoople, computer vision and deep learning for Earth observation."
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

<!--
  Las secciones de Publications y Talks de mas abajo se generan solas a partir
  de _publications/ y _talks/. No hay que tocarlas: al anadir un paper nuevo
  aparece aqui automaticamente.

  Las secciones escritas a mano (Education, Experience, Service...) si hay que
  mantenerlas. Los TODO marcan lo que falta por rellenar.
-->

Education
======
* **PhD in Computer Vision and Deep Learning**, Universidad Autónoma de Madrid, 2022
  * Thesis: *Context-Driven Vision for Image and Video Analysis*
  * Video Processing and Understanding Lab (VPU)
  * Advisors: Marcos Escudero-Viñolo, Jesús Bescós
* **MSc**, Universidad Autónoma de Madrid, 2017
  * Thesis: *Online Contextual Updating in Multi-Camera Scenarios*
  <!-- TODO: nombre exacto del master -->
* **BSc in Telecommunications Engineering**, Universidad Autónoma de Madrid, 2015
  * Thesis: *Identificación Automática de Materiales Usando el Sensor Kinect*

Experience
======
* **Lead Research Scientist**, [Xoople](https://xoople.com) — Madrid, Spain
  <!-- TODO: fecha de inicio -->
  * Computer vision and deep learning for Earth observation
  * Foundation models and self-supervised embeddings over multi-modal satellite time series
  * Land-cover classification and Earth surface monitoring

<!--
  TODO: puestos anteriores. Copialos de LinkedIn con este formato:

* **Cargo**, Empresa — Ciudad, Pais (aaaa–aaaa)
  * Que hacias, en una o dos lineas
-->

* **Predoctoral Researcher**, Video Processing and Understanding Lab, Universidad Autónoma de Madrid
  <!-- TODO: rango de fechas -->
  * Scene recognition, multi-camera pedestrian detection, knowledge distillation and explainability

Skills
======
* **Research**: representation learning, self-supervised learning, foundation models, semantic segmentation, scene understanding, knowledge distillation, explainable AI
* **Earth observation**: Sentinel-1/2 time series, multi-modal remote sensing, land-cover classification
* **Engineering**: Python, PyTorch, C++, MATLAB, MLOps, distributed training (Slurm)

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

Talks and presentations
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>

<!--
  Bloque de Teaching: vacio de momento. Descomenta cuando anadas ficheros a
  _teaching/ (y reactiva la entrada "Teaching" en _data/navigation.yml).

Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
-->

<!-- TODO: revision de articulos, comites, supervision de estudiantes, premios -->
