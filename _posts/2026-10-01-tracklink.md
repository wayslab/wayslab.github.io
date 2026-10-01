---
layout: publication
title: "TrackLink: Enabling Near-Field Beamfocusing and MIMO for Fast Moving LEO Satellites"
short_title: "TrackLink"
tags: Communications
cover: /assets/images/pubpic/tracklink_cover.png
authors: "Rohith Reddy Vennam, Eric Xiang, Dinesh Bharadia, and Ish Kumar Jain"
author_list:
    - name: Rohith Reddy Vennam
    - name: Eric Xiang
    - name: Dinesh Bharadia
    - name: Ish Kumar Jain
      email: jaini@rpi.edu
eqcon: false
conference: "Under submission to INFOCOM '27"
paper: /files/tracklink_infocom27.pdf
description:
    - title: Abstract
      image: /assets/images/pubpic/tracklink_cover.png
      text: "Distributed near-field ground arrays can combine commodity panels for dish-class gain and line-of-sight MIMO rank. Low Earth orbit (LEO) motion, however, makes their kilometer-scale focus both extremely narrow and short lived: public ephemeris can point each panel, but cannot maintain carrier-phase coherence across the full aperture, and a measured channel is stale before a later uplink reaches the satellite. Existing localize-then-focus and channel-reuse methods therefore cannot meet the narrow-angle and fast-clock requirements together. We present TrackLink, a ground-side system that separates slow analog pointing from fast digital phase maintenance. On the downlink, TrackLink anchors the effective per-panel channel with a full-channel pilot and tracks only phase increments with sparse pilots. On the uplink, where no future measurement exists, it factors the channel into a computable geometric term and a measured quasi-static residual, then predicts the phase at satellite arrival. The ground panels share a frequency reference and periodically phase-calibrate their transmit and receive chains; remaining calibration error is included in the residual. To acquire this predictor from a coarse orbital prior, CFFR combines a measured wrapped-phase intercept, an unwrapped geometric increment, and a closed-form fringe-rate correction, avoiding fine satellite localization and global ambiguity search. Satellite-side equalization preserves multiplexing without returning calibration feedback. In simulations using the published STARLINK-1821 orbit, TrackLink realizes 12.02 dB of uplink array gain at a 10 ms turnaround, 0.02 dB from perfect channel knowledge, while stale CSI falls to the incoherent floor. CFFR has zero observed catastrophic failures across the tested 1 m-30 km prior-error sweep at 910x fewer operations than exhaustive search, assuming the residual remains quasi-static over the prediction horizon."
osd: "TrackLink is a ground-side system that maintains near-field beamfocusing and LoS-MIMO from a kilometer-scale distributed array to a fast-moving LEO satellite by separating slow analog pointing from fast digital phase prediction, realizing 12.02 dB of uplink array gain at a 10 ms turnaround in STARLINK-1821 orbit simulations."
---
