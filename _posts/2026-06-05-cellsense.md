---
layout: publication
title: "CellSense: A Sub-6 GHz Cellular ISAC System for Clutter-Robust Passive Sensing"
short_title: "CellSense"
tags: ISAC 6g
authors: "Bibhor Kumar, Ish Kumar Jain, Vijay K. Shah"
cover: /assets/images/cellsense/cellsense.png
disp_cover: "False"
# needed for publications/
author_list:
    - name: Bibhor Kumar
    - name: Ish Kumar Jain
    - name: Vijay K. Shah
conference: "MILCOM 2026"
conference_site: https://www.milcom.org/
paper: https://arxiv.org/pdf/2606.07900
description:
    - text: "Future wireless networks are increasingly expected to provide sensing, localization, and environmental awareness in addition to reliable communication. Cellular infrastructure offers a uniquely attractive platform for such integrated sensing and communication (ISAC) because it is already deployed at scale, operates over wide coverage areas, and can reuse existing spectrum and infrastructure. However, sub-6 GHz cellular sensing remains significantly underexplored compared with millimeter-wave and more specialized radar systems. CellSense addresses this gap by turning a standard 5G cellular stack into a practical passive sensing system that can track objects in the environment while preserving communication functionality."

    - text: "The core idea behind CellSense is to exploit the structure of 5G downlink OFDM signals, together with a clutter-aware signal processing pipeline, to separate moving targets from the static background. Rather than requiring dedicated radar hardware or custom waveforms, the system cooperates with existing communication protocols and uses the cellular link itself as a sensing substrate. This approach is particularly valuable in real-world deployments where clutter, multipath, and blockage can otherwise overwhelm weak target reflections. By combining communication-native signal processing with robust clutter rejection, CellSense achieves accurate passive sensing in both indoor and outdoor settings."

    - text: "The authors validate the system through Sionna-based OFDM simulations and an experimental USRP prototype running the OpenAirInterface stack. Results show that CellSense can maintain high detection rates and sub-meter localization accuracy in cluttered environments, while also characterizing the communication-sensing tradeoff as pilot density changes. In particular, the system reports a 74% detection probability with 1.43 m error in an indoor warehouse scenario and up to 94% detection with 0.33 m error in an outdoor deployment. These results demonstrate that sub-6 GHz cellular infrastructure can serve as a practical and scalable ISAC platform for passive sensing, opening the door to more robust, ubiquitous environmental awareness in next-generation wireless networks."

citation:
    - text: 'Bibhor Kumar, Ish Kumar Jain, Vijay K. Shah. "CellSense: A Sub-6 GHz Cellular ISAC System for Clutter-Robust Passive Sensing." arXiv:2606.07900, 2026.'
---
