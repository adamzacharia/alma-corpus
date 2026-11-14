# Codex review: dust-continuum-mass
VERDICT: FIX
## Findings

- SR-01 | medium | attribution | “Built from 915 ALMA papers”; “RADMC-3D 34”; “emcee 21” | The supplied pack states **927** papers, **radmc-3d 35**, and **emcee 22**. These stale totals recur in both files. | Update corpus metadata and software counts; identify the actual subset underlying parameter recounts instead of implying they cover the current pack.

- SR-02 | medium | attribution | “dust-to-gas 0.0024 / 0.0016 / 0.002 … LMC / SMC hot cores” | The parameters table assigns 2026ApJ...999..194I to the Magellanic Clouds. The pack identifies it as an **Outer Galaxy** hot core in Sh 2-283; its 0.0024 ratio is supported, that location is not. | Split the row and label each paper’s environment correctly.

- SR-03 | medium | attribution | “OpacityTool 3 (2025A&A...696A.232G)” | That paper’s pack entry attributes its opacities to **optool with DSHARP**, not OpacityTool. The pack explicitly names OpacityTool for 2020ApJ...904...37W. | Correct the example and keep the distinct software names separate.

- SR-04 | medium | attribution | “beta … Range seen: 0 to 2.2” | The pack gives β_IR = **2.5** for 2024MNRAS.533.3098A, including its adopted optical-depth calculation. | Extend the stated range or explicitly restrict it to a documented subset.

- SR-05 | medium | unsupported | “4594 +/- 2848 … (card)”; “T = 25 K … ^0.17”; “kappa … 0.23 m2/kg at 1.33 mm” | The supplied pack does not establish these values for 2020ApJ...892..147S, 2017ApJ...846...70P, and 2025A&A...693A.151M respectively. Saying a value came from a separate card does not supply that evidence. | Remove these attributions or add the supporting card excerpts to the evidence pack; audit other supplementary parameter rows the same way.

- SR-06 | medium | unsupported | “2 sigma … 2025ApJ...993L..40S; 2024ApJ...963....1O (card)” | Neither supplied entry establishes a 2σ continuum limit. Likewise, the pack does not establish the cited 3σ practice for 2019ApJ...875L...9W. The clearly labelled **skill default** is acceptable. | Retain supported examples, such as 2015A&A...583A..66H, and remove or substantiate the other significance attributions.

- SR-07 | medium | unsupported | “SciPy … clump modified-blackbody least squares”; “ASURV … 2016ApJ...828...46A”; “linmix … 2020A&A...633A.114S” | The supplied entries do not establish these paper-specific software uses. Aggregate counts establish that software appears somewhere, not which paper used it. | Supply the relevant method excerpts or present these tools as general implementation options without those paper attributions.

- SR-08 | medium | unsupported | “interferometer-to-single-dish ratio 0.53”; “only 43% … recovered”; “median offset 0.23 dex” | These numerical claims are not supplied for 2014ApJ...787...48X, 2016ApJ...832..148V, or 2021A&A...652A..98G. Several other numerical verification claims similarly exceed the visible evidence. | Remove unsupported numbers or add their verified excerpts; retain the supported missing-flux examples.

- SR-09 | medium | science | “the intensity can never exceed f B_nu(T_d)” | The preceding equation uses **background-subtracted** intensity, whose maximum is **f[B_nu(T_d) − B_nu(T_bg)]**. Testing against fB alone can admit an impossible logarithm argument, particularly with a substantial CMB background. | Use the contrast consistently and require 0 ≤ ΔI/[f(B_d−B_bg)] < 1; treat saturation as an optical-depth lower bound.

- SR-10 | medium | omission | “Choose the opacity law … kappa_nu” | The skill never explicitly requires **absorption opacity**, rather than total absorption-plus-scattering extinction, in the thin thermal-emission formula. The pack explicitly calls the 2.3 cm²/g value an absorption opacity in 2019MNRAS.488.1005P. | Label the formula’s coefficient κ_abs and distinguish it from scattering and extinction coefficients returned by opacity tools.

- SR-11 | medium | omission | “prefer a temperature measured … (SED fit…)”; “compare thin masses with an RT … grid” | Missing acceptance checks matter here: 2021A&A...652A..66P says its fitted temperature follows the prior; 2025A&A...694A.295P says ProDiMo cannot fit NIR/MIR and ALMA simultaneously and provides little mass constraint. | Require checks of wavelength coverage, prior sensitivity, residuals and parameter boundaries before accepting fitted temperatures or RT masses as validation.

- SR-12 | medium | omission | “Say which phases your result covers” | Phase bookkeeping omits **helium**. The pack explicitly gives a 1.36 helium correction for 2022A&A...664A..63X and molecular hydrogen plus atomic helium for 2021ApJ...910...75L. | State whether every gas mass, gas-to-dust ratio and α_850 calibration includes helium; reconcile conventions before comparisons.

- SR-13 | medium | omission | “Build a clean continuum flux” | No explicit beam/aperture matching check accompanies multiband intensities and temperature comparisons. The pack’s 2025ApJ...991...59B entry explicitly regrids and smooths the 870 μm image to the 1.2 mm image. | Require compatible resolution, extraction regions and spatial-scale coverage before combining resolved measurements.

- SR-14 | high | usability | “2014ApJ...789L...4T” in opacity and count-membership tables | This is the MC27/L1521F paper, linking the skill to an object explicitly prohibited by WRITER CONTEXT. A methods-only bibliography citation still names a prohibited paper. | Remove the citation and its membership entries; replace the example with an allowed source and recompute affected counts.

## Notes
The main thin-mass formula, redshift factor and Rayleigh–Jeans correction are sound.
Optical-depth, filling-factor and conditional-limit warnings are useful.
Unsupported findings identify missing supplied evidence, not proof that the underlying papers disagree.
The truncated pack cannot independently substantiate the claimed complete parameter membership counts.