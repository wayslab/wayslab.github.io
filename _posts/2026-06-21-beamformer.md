---
layout: publication
title: "BeamFormer: Transformer-based Beam Management for 6G Networks"
short_title: "BeamFormer"
tags: AI 6g
cover: /assets/images/pubpic/beamformer_cover.png
authors: "Shunqiang Feng, Swastik Kanjilal, Kun Qian, and Ish Kumar Jain"
author_list:
    - name: Shunqiang Feng
      email: shunqiang@virginia.edu
    - name: Swastik Kanjilal
      email: kanjis2@rpi.edu
    - name: Kun Qian
      email: kunqian@virginia.edu
    - name: Ish Kumar Jain
      email: jaini@rpi.edu
eqcon: false
conference: "ACM MobiSys 2026"
conference_site: https://doi.org/10.1145/3745756.3809229
paper: /files/beamformer_mobisys26.pdf
github: https://github.com/Shunqiang-Feng/BeamFormer
github_desc: "Transformer-based beam spectrum generation for 6G beam management"
description:
    - title: Abstract
      image: /assets/images/pubpic/beamformer_cover.png
      text: "The forthcoming 6G wireless network is anticipated to augment base stations with much denser antenna arrays, achieving ultra-narrow beamforming and orders of magnitude higher capacity than 5G. However, the resulting beam management for such antenna arrays imposes prohibitive overhead, as the number of beam measurements needed for full directional coverage increases sharply. Inspired by recent advances in generative models, we propose BeamFormer, a transformer-based framework that generates full beam spectra from a few reference beam measurements. The success of applying transformers to accurate, fast, and robust beam management stems from joint architectural innovations, including beam pattern encoding, latent beam processing with linear complexity, and universal reference beam optimization. We synthesize a large channel dataset to train BeamFormer, and evaluate it using both the simulation dataset across multiple FR2/FR3 frequencies and the real dataset from 28 GHz software-defined radio testbeds. Compared to existing approaches, BeamFormer achieves better beam alignment with an average gain of 6.7 dB. Moreover, BeamFormer achieves a 1.8 ms delay to generate a beam spectrum with 1,600 beams, empowering real-time beam management for future 6G. The source code and dataset are publicly accessible at GitHub."
osd: "BeamFormer is a transformer-based beam management framework that generates full beam spectra from a few reference beam measurements, achieving a 6.7 dB average beam-alignment gain and generating a 1,600-beam spectrum in 1.8 ms for real-time 6G beam management."
---
