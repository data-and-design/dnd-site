---
title: 'Olli with Hypergraphs: An Extensible Architecture for Accessible Charts and Diagrams'
authors:
  - key: jzong
venue: vis-access
year: 2026
date: 2026-11-08
# doi: null
pdf_url: /publications/olli-with-hypergraphs.pdf
themes: [access]
projects: [olli]
---

## Abstract

Olli is an open-source library that renders data visualizations as keyboard-navigable structured textual descriptions for screen reader users. Olli has represented a chart as a tree derived from the chart’s visual encodings; however, two systems have critiqued the restriction to trees. Data Navigator observed that hierarchical trees cannot express relations such as spatial adjacency or membership in multiple groups. Benthic argued that hypergraphs avoid the limitations of trees and graphs because a hypergraph can consistently express both hierarchy and adjacency. In response, this paper presents a new architecture for Olli that uses hypergraphs as its core internal representation. Domain plugins for charts and diagrams lower their specifications to the hypergraph, and a shared navigation runtime traverses the hypergraph. The new architecture unifies Olli with Benthic, and Olli’s customizable description and interactive filtering now apply to charts and diagrams alike. Authors can specify Olli structures at three levels of abstraction: Vega-Lite and Bluefish specifications via adapters, Olli’s own domain specifications, or raw hyperedges. Navigation on the shared runtime behaves consistently across domains but fits each graphic less closely than navigation authored specifically for that graphic. We invite the community to build new domains and to conduct empirical studies on Olli’s shared runtime.