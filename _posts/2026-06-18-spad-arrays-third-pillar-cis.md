---
title: "SPAD Arrays: The Third Pillar of CIS Is Taking Shape"
date: 2026-06-18
layout: post
excerpt: "SPAD arrays are not replacing conventional CIS pixels. They are opening an entirely new application space that conventional pixels cannot address."
---

For decades, CIS meant one thing: capturing images. SPAD arrays change that equation — they capture time, not just light.

The marker to watch: in 2026, every major CIS player now has a SPAD product in volume production or final qualification. This was not true in 2024.

---

## What a SPAD Is (Short Version)

A SPAD is a PN junction biased above breakdown voltage. When a single photon triggers an avalanche, the current spike is large enough to detect with simple digital circuitry. No amplifier needed. No CDS. No ADC in the pixel.

The tradeoff: the pixel is blind for a recovery period after each detection (dead time, typically 10-100 ns). And the avalanche current generates heat and noise. But for ranging applications, the sensitivity advantage over conventional pixels is 3-4 orders of magnitude.

![SPAD avalanche principle](/Xinnova/assets/illustrations/spad-principle.svg)
*Fig.TECH.03 — A single photon triggers an avalanche above breakdown voltage. The output is a clean digital pulse.*

---

## What Changed in 2025-2026

**1. Backside illumination for SPADs.** The first BSI SPAD products entered production in 2024-2025. By illuminating the SPAD from the backside, quantum efficiency in the near-infrared (940 nm) improved from ~10% (frontside) to >30%. This doubled the effective ranging distance.

**2. Pixel miniaturization.** SPAD pixels have shrunk from 10µm (2020) to 5-6µm (2025). A 100×100 SPAD array at 6µm pitch fits in a 0.6×0.6 mm die — small enough for smartphone integration.

**3. On-chip histogram processing.** Early SPAD arrays required an external processor to build time-correlated histograms. Current-generation devices integrate the TDC and histogram builder on-chip, reducing system cost and power.

---

## Who Ships What

![SPAD vendor landscape](/Xinnova/assets/illustrations/spad-vendors.svg)
*Fig.DATA.05 — Four vendor categories as of June 2026*

Sony is the clear leader here. Their IMX611 processes 1 million depth points per frame with 10 cm accuracy out to 50 meters. That is competitive with mechanical LiDAR at a fraction of the cost and size.

SmartSens is the dark horse worth watching. Unlike OmniVision (no public SPAD roadmap), SmartSens has been building SPAD capability since 2024 and is targeting security and automotive segments where their existing customer base overlaps.

---

## The Investment Angle

SPAD is not a replacement market. It is an incremental market — new applications that could not exist without single-photon sensitivity.

![SPAD market forecast](/Xinnova/assets/illustrations/spad-market.svg)
*Fig.DATA.04 — Mobile dToF grows at 40% CAGR; automotive LiDAR at 60%*

| Application | 2024 Market | 2028E Market | CAGR |
|:-----------|:----------:|:-----------:|:----:|
| Mobile dToF | $0.3B | $1.2B | 40% |
| Automotive LiDAR | $0.5B | $3.5B | 60% |
| Medical/Industrial | $0.2B | $0.5B | 25% |

Sony benefits most in the short term (they have the best products). For public market investors, the indirect exposure through companies that supply or assemble SPAD-based systems may be the more practical route.

---

## Bottom Line

SPAD arrays are the third major sensing modality for CIS, alongside 2D imaging and event-based vision. The technology is past the science project phase and entering volume production. The next 24 months will determine which players capture the automotive LiDAR slot.

---

*Not investment advice. Data from public datasheets, patent filings, and industry briefings as of June 2026.*
