---
title: "LOFIC HDR: The Technology Reshaping Mobile Imaging in 2026"
date: 2026-06-15
layout: post
excerpt: "A technical look at Lateral Overflow Integration Capacitor HDR technology — why it matters, who is winning, and what comes next."
---

Every flagship phone in 2026 uses LOFIC or a variant. Here is how it works and who leads.

---

## The HDR Bottleneck

Mobile CIS HDR has always been about tradeoffs:

| Technology | Dynamic Range | Artifacts | Pixel Impact |
|:-----------|:-------------:|:---------:|:------------:|
| Multi-exposure (DCG) | 100-110 dB | Motion blur, ghosting | Minimal |
| Dual conversion gain | 90-100 dB | Seamless, but range limited | ~10% area |
| **LOFIC** | **130-140 dB** | **None** | **~5% area** |

Multi-exposure HDR captures the same scene at short, medium, and long integration times, then fuses them in the ISP. You get decent dynamic range, but anything that moves shows up in multiple positions across frames. That ghosting artifact has been the bane of every camera engineer working on HDR video.

Dual Conversion Gain (DCG) eliminates ghosting by switching gain mid-exposure. But the FD capacitance caps range at ~100 dB. Fine for most scenes, falls apart at tunnel exits or backlit portraits.

LOFIC solves both problems in one exposure.

---

## How LOFIC Works (For Engineers)

A 4T pixel uses a floating diffusion (FD) node with fixed charge capacity. For a 1.0µm pixel, that is typically 30,000-60,000 e⁻. When the FD saturates, extra photoelectrons spill into neighbors (blooming) or get lost.

LOFIC adds a small capacitor through a dedicated transfer gate:

```
                 VDD
                  |
    RST ──┐      RST
          |       |
    PD ──TG── FD ──┐── SF ──> Output
                   |   |
    LOFIC_TG ──||──┘   |
                C      VSS
              LOFIC
              (Capacitor)
```

**Three operation modes:**

1. **Low-light**: LOFIC_TG OFF. Standard 4T operation, high conversion gain. Read noise around 1.5 e⁻. FWC hits 30,000 e⁻.

2. **Bright-light**: LOFIC_TG ON. The capacitor connects in parallel with the FD, bumping total capacitance by 2-4×. FWC jumps to 80,000-120,000 e⁻. Conversion gain drops.

3. **Dual-readout**: Read twice. First with LOFIC off (shadow detail), then with LOFIC on (highlight retention). A per-pixel fusion algorithm combines both into a single 130-140 dB frame.

Both readouts happen within the same exposure. No temporal offset means zero motion artifacts. For video, this is single-exposure HDR at 60 fps or higher, no stitching artifacts.

---

## Who Has What

| Feature | Sony | Samsung | OmniVision | SmartSens |
|:--------|:----:|:-------:|:----------:|:---------:|
| LOFIC production | ✅ STARVIS 3 (IMX908, Mar 2026) | ❌ R&D | ✅ TheiaCel (OV50H/X) | ✅ LOFIC 3.0 (SCC90XS) |
| Single-exposure HDR | 110 dB | -- | 130-140 dB | 105 dB |
| Pixel pitch supported | 2.0µm+ (automotive) | -- | 0.7-1.2µm | 0.61µm |
| 200MP + LOFIC | ❌ | ❌ | ❌ | ✅ SCC90XS |
| Mass production maturity | Ramping | 2 years behind | **3 generations mature** | Rapid iteration |

Sony's STARVIS 3 (IMX908) looks good on paper, but it targets automotive at 2.0µm+ pixel pitch. For mobile sensors at 0.7-1.0µm, Sony has not shown a LOFIC product yet.

OmniVision's TheiaCel pair (OV50H at 1.2µm, OV50X at 1.0µm) is the mobile LOFIC leader. Three generations of refinement give them 130-140 dB single-exposure HDR with only ~5% area overhead.

SmartSens SCC90XS is the dark horse: 0.61µm pixel, LOFIC, and 200MP in one sensor. Pushing LOFIC below 0.7µm is non-trivial. The capacitance ratio has to hold up at that pitch, and from the datasheet numbers, it mostly does.

---

## Small Pixel Physics

Below 1.0µm, every electron matters:

| Pixel Pitch | FWC (4T) | FWC (LOFIC) | SNR Boost |
|:-----------:|:--------:|:-----------:|:---------:|
| 1.0µm | 60,000 e⁻ | 180,000 e⁻ | +4.8 dB |
| 0.8µm | 38,000 e⁻ | 114,000 e⁻ | +4.8 dB |
| 0.61µm | 22,000 e⁻ | 66,000 e⁻ | +4.8 dB |

The SNR gain is a function of capacitance ratio, not pixel size. A 3× FWC boost gives a consistent 4.8 dB in highlight-region SNR regardless of pitch.

Small-pixel sensors are photon-starved by nature. LOFIC does not fix shot noise in the shadows (you need larger pixels or better QE for that). What it does: it rescues highlights that would otherwise clip. A LOFIC-equipped 0.61µm pixel can hold a scene that would need a 1.0µm pixel without LOFIC. That is a meaningful area and cost advantage.

---

## 2026-2027 Outlook

| Year | Milestone | Implication |
|:----:|:---------|:------------|
| **2026 H2** | Xiaomi 15 Ultra with OV50X (TheiaCel) | Mass-market validation |
| **2026 H2** | Sony Xperia (potential IMX908 mobile variant) | Sony's mobile LOFIC debut? |
| **2027 H1** | SmartSens SCC90XS in Chinese flagships | 200MP LOFIC goes mainstream |
| **2027 H2** | Samsung ISOCELL LOFIC samples | Late entrant, but IDM advantage |

LOFIC has moved from automotive niche to mainstream mobile imaging. The companies with mature LOFIC IP (OmniVision/Will Semi, SmartSens) have a 2-3 year head start over Samsung and a mobile-specific edge over Sony.

---

*Not investment advice. Data from public datasheets, patent filings, and industry briefings as of June 2026.*
