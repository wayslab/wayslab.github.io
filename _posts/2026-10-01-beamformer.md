---
layout: publication
title: "BeamFormer: Transformer-based Beam Management for 6G Networks"
short_title: "BeamFormer"
tags: 6g AI
authors: "Sunqiang Feng, Swastik Kanjilal, Kun Qian, Ish Kumar Jain"
cover: /assets/images/beamformer/beamformer_cover.png
disp_cover: "False"
author_list:
    - name: Sunqiang Feng
    - name: Swastik Kanjilal
    - name: Kun Qian
    - name: Ish Kumar Jain
conference: "ACM MobiCom 2026"
conference_site: https://www.acm.org/
paper: https://dl.acm.org/doi/pdf/10.1145/3745756.3809229
description:
    - text: "Beam management is a critical challenge in next-generation 6G wireless networks, where increasingly large antenna arrays require efficient and accurate beam alignment. Conventional beam sweeping methods incur substantial measurement and signaling overhead, making them difficult to scale to dense antenna arrays and dynamic wireless environments. In this work, we present BeamFormer, a Transformer-based framework that formulates beam management as a beam-spectrum reconstruction problem."
      image: /assets/images/beamformer/beamformer_architecture.png
      image_width: 800

    - text: "By using a small number of measured reference beams, BeamFormer predicts the complete beam spectrum and identifies high-quality beam directions without exhaustively scanning the entire beam space. This approach directly addresses the overhead bottleneck of traditional beam search while enabling faster adaptation to changing propagation conditions. The method is particularly attractive for future 6G systems, where beam alignment must be both low-latency and robust across diverse environments and antenna configurations."

    - text: "We evaluate the system using both simulations and real-world 28 GHz software-defined radio testbeds across different environments, frequencies, and antenna configurations. Our results show that BeamFormer can reconstruct a large beam space within milliseconds while substantially reducing beam measurement overhead. The framework achieves an average beam alignment improvement of 6.7 dB over existing approaches and a reconstruction latency of approximately 1.8 ms for a 1,600-beam spectrum. These findings demonstrate the potential of Transformer-based beam prediction as a practical approach for low-overhead, real-time beam management in future 6G networks."
      image: /assets/images/beamformer/beamformer_exp.png
      image_width: 800

citation:
    - text: 'Sunqiang Feng, Swastik Kanjilal, Kun Qian, Ish Kumar Jain. "BeamFormer: Transformer-based Beam Management for 6G Networks." ACM MobiCom, 2026.'
---
