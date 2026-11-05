# Designing an IHC experiment

Which fixative, buffer, detergent, blocking serum, fluorophore, mounting medium
and microscope to use, and why. This is the reasoning behind
[immunostaining.md](immunostaining-YYYYMMDD.md) — read it when your target does not work
with the standard protocol, or when you are setting up something new.

Last update: 2026-09-08（経緯を `## Revision history` へ移した。手順は変えていない）

## The lab standard, in one block

- 4% PFA/PBS transcardial perfusion
- Vibratome sectioning
- Free-floating immunostaining
  - Permeabilisation: PBS-T (0.2% Triton X-100 in D-PBS), RT, 5 min × 2
  - Blocking: 5% NGS in PBS-T, RT, 30–60 min
  - Primary antibody: diluted in blocking buffer, 4 °C or RT
  - Secondary antibody: diluted in blocking buffer, 4 °C or RT
- Mounting
- Imaging

Everything below is what you change, and what it costs you, when the standard
does not work.

## Fixative

| | Use | Notes |
| --- | --- | --- |
| **PFA** | the standard aldehyde crosslinker | Watch the pH if you are going to clear the tissue |
| **Glutaraldehyde** | preserving morphology, fast fixation; EM | **Not for immunostaining** — antigenicity drops, autofluorescence rises |
| **Glyoxal** | a classical fixative that has been re-evaluated recently | Markedly improves staining of synaptic molecules |

Glyoxal references:
[EMBO J 2018](https://link.springer.com/article/10.15252/embj.201695709),
[Sci Adv 2023](https://www.science.org/doi/10.1126/sciadv.adf7084),
[Synaptic Systems glyoxal protocol](https://sysy.com/protocols/protocol-ihc-tissue-preparation-glyoxal).

> **PFA that was dissolved with sodium hydroxide is bad for clearing.** Alkaline
> PFA over-fixes. Melt it in a microwave and make a large batch to store instead
> (from the CUBIC notes — see [tissue-clearing.md](tissue-clearing-YYYYMMDD.md)).

## Antigen retrieval

Unmasks antigens in formalin-fixed tissue. Two families:

- **Heat-induced (HIER)** — low pH (citrate buffer) or high pH (TE buffer)
- **Enzymatic (PIER)** — trypsin, pepsin, proteinase K

**Not required for PFA-fixed mouse brain**, but it helps for some targets —
pepsin for PSD proteins, and it is standard for peptides (substance P,
enkephalin). The procedure is in
[immunostaining.md](immunostaining-YYYYMMDD.md#optional-antigen-retrieval).

## Buffer

| | Use |
| --- | --- |
| **PBS** | the lab standard for immunostaining |
| **TBS** | occasionally used; **better for phosphoproteins**, because PBS carries a lot of phosphate that interferes |
| **PB** | sometimes used for perfusion. No NaCl, which is said to stop the tissue shrinking or the surface aggregating, so PFA reaches deeper and crosslinks more evenly |

## Detergent

**Triton X-100** is the standard, usually at 0.2–0.5% final.

- CMC is 0.24 mM (~0.0155% w/v) — above that it forms micelles and solubilises
  protein
- **It is viscous, so be careful pipetting it.** If you end up below the intended
  final concentration the membrane does not get permeabilised at all

NP40, saponin, digitonin and SDS are not much used in histology. Methanol,
ethanol and acetone are not either, though methanol fixation is sometimes useful
for immunocytochemistry.

## Blocking

**Match the serum to the secondary antibody's host.** The lab normally uses NGS.
See the table in [immunostaining.md](immunostaining-YYYYMMDD.md#standard-solutions).

## Fluorophore and colour

Standard secondaries: **Alexa488, Alexa546, Alexa647**. Special microscopy (STED
and the like) needs fluorophores chosen for that method.

Nuclear stains:

| | Excitation / emission | Dilution |
| --- | --- | --- |
| Hoechst (33342, 33258) | 350 / 461 nm | 100–1000× |
| DAPI | 354 / 456 nm | 100–1000× |
| PI | 530 / 620 nm | 1 mg/mL stock, use at 1–10 µg/mL (100–1000×) |
| TO-PRO-3 | — | 1000× (see [immunostaining.md](immunostaining-YYYYMMDD.md)) |

**Check the filter set of the microscope you will actually use** — for the
Keyence, [microscopy/keyence-bz-x810.md](equipment/keyence-bz-x810-YYYYMMDD.md).
Generally: V/B, B/G (Alexa488), Y/R (Alexa546), R/FR (Alexa647).

> **Assign colours in this order: Green → Red → Far Red / Violet.** Green and
> red are bright and visible to the eye, so **put what you most want to see in
> green and the second most in red.**

[Fluorochrome brightness chart](https://www.bu.edu/flow-cytometry/files/2013/06/Fluorochromes-Brightness-Chart.pdf)
(a copy is also in the `histology` Drive folder).

## Mounting medium

| | When |
| --- | --- |
| **PBS** | **Try this first.** It is the same buffer you stained in, so it cannot change the staining pattern |
| **Prolong, VECTASHIELD, etc.** | For long-term storage. Expensive — decide whether you really need it. **Can affect the staining pattern** |
| **Clearing reagents** | Dramatically better fluorescence images, and cheap. Not yet a lab standard — see [tissue-clearing.md](tissue-clearing-YYYYMMDD.md) |

## Microscope

| | Principle | Good for |
| --- | --- | --- |
| **Wide field** | area excitation, area detection | Thin specimens only. Thick ones get out-of-plane fluorescence bleeding in |
| **Structured illumination** (Keyence BZ-X, Nikon N-SIM) | area excitation, area detection, with a grid pattern | Pseudo Z-sectioning: only the parts with strong grid contrast are kept. **The grid contrast falls off with depth**, so the sectioning weakens deeper in |
| **Confocal** (Zeiss AiryScan, Nikon NSPARC) | point excitation, point detection | Genuine Z-sectioning via the pinhole. Works on thick specimens |

**For vibratome sections: confocal > Keyence BZ-X > wide field.**

Every microscope goes darker with depth, and that is refraction and scattering in
the tissue, not the optics. **Clearing removes most of it, and improves the
image on any of the three.**

## Scheduling

**n/a — this is a design guide, not a procedure.** It records which fixative, retrieval, buffer, detergent, blocking, fluorophore, mounting medium and microscope to choose and why; nothing here is carried out on its own. The durations quoted in [The lab standard, in one block](#the-lab-standard-in-one-block) belong to the run that uses them — [immunostaining.md](immunostaining-YYYYMMDD.md#scheduling).

## Revision history

| Date | Change |
| --- | --- |
| 2026-08-28 | back-filled from git: 1cbf4bc. **Derived, not confirmed by a person** — see [protocol.md](../../research-guidelines/30-experiment/protocol.md#back-filled-dates). |

## Source

[histology_nlm](https://docs.google.com/document/d/1KtndBnJZxJSUV9PwgTtYsO23E3PUImZCMAaGiYRW1fs/edit)
§General (Overview through Fluorescent microscope selection). The PFA/clearing
note is from the CUBIC document.

