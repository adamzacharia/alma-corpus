# Codex review: sed-fitting
VERDICT: FIX

## Findings

- SR-01 | medium | attribution | “989 papers, 558 … high-z”; “CIGALE 98”; “Bagpipes 31” | The pack states **1001 papers**, **565 high_z_galaxies**, **101 CIGALE** and **33 bagpipes** mentions. | Update the description, counts paragraph, software table and source-list totals consistently.

- SR-02 | medium | attribution | “CIGALE/MAGPHYS: report … log-uniform priors … uniform for T_dust” | The cited 2024ApJ...965..108U assigns this estimation procedure to **CIGALE**, steps 5–6. Its MAGPHYS comparison does not establish the same procedure for MAGPHYS. | Attribute these settings specifically to that paper’s CIGALE analysis; document MAGPHYS separately.

- SR-03 | medium | attribution | “dust-based gas mass with CO-based and dynamical mass (within a factor 2 …)” | 2020MNRAS.498.4192F step 5 reports factor-two agreement with dynamical estimates, but its CO estimate is **2.5 times larger**, approximately a 1σ discrepancy. | Separate the dynamical and CO comparisons and retain their qualifications.

- SR-04 | medium | attribution | “T_peak … peak of the rest-frame S_nu taken in wavelength convention (2020MNRAS.498.4192F)” | The supplied entry supports **2898/λ_peak**, but does not specify that peak’s ordinate. The pack explicitly establishes a Jy peak only for 2024ApJ...965..108U. | Remove the unsupported ordinate attribution; distinguish the reported definition from any convention independently established later.

- SR-05 | medium | attribution | “9”, “15”, “27 / 16 / 16 / 15”, “61 / 20 / 14”, “12 listed papers” | These exact regex-derived totals cannot be reproduced from the supplied, truncated parameter/assumption lists. The claimed line range also belongs to a different pack version. This does not establish that the totals are false. | Supply the counted bibcodes and matching entries for each total, or remove the exact totals pending an audit against this pack.

- SR-06 | medium | unsupported | “checked against the earlier pack … kept as examples” | An unavailable earlier pack is not evidence supplied for this review. Examples include the observed-frame temperature bound for 2014A&A...568A..92M and the wide priors for 2019ApJ...871...85L; their current entries are bibliographic only. | Remove these settings or include their supporting evidence. An “earlier pack” label does not validate them.

- SR-07 | medium | unsupported | “fix beta=1.8 … alpha=2.5 with fewer than 4 … T=35 K with fewer than 2”; “lambda_0=150 um” | The supplied pack gives only bibliographic entries for these claims about 2017ApJ...840..101C and the opacity setting attributed to 2017ApJ...844..123F. Likewise, it does not supply the claimed **58.5 versus 33 K** comparison for 2014A&A...562A..67G. | Remove the source-specific numerical claims until supporting entries are supplied; retain correctly labelled general identifiability and opacity cautions.

- SR-08 | medium | unsupported | “at least 0.13 dex”; “about 20% of L_FIR”; “0.41 × 1.34e13 = 770” | The supplied entries do not establish the subtraction uncertainty for 2017ApJ...844..123F, the warm-dust percentage for 2017ApJ...844L..10S, or the AGN fraction and luminosity used in the 2024ApJ...962....1S calculation. Only the latter paper’s **1.40e-10 coefficient** is supplied. | Retain the supported coefficient; remove unsupported numerical budgets and worked inputs. Describe the remaining effects qualitatively.

- SR-09 | medium | unsupported | “SMGs … 25–45 K”; reference row points to “SKILL.md table” | This sensitivity range has no supporting pack entry or independent citation. The supplied 2015A&A...584A..78C entry instead tests **20–60 K**, alongside redshift and beta variations. | Cite a supported population-specific test range; eliminate the circular reference and avoid presenting an editorial range as literature practice.

- SR-10 | medium | science | “The model must never exceed a limit” | This is the explicit prescription of 2021A&A...649A.152K, not a universal treatment of noisy nondetections. The pack also documents measured low-S/N flux fitting in 2018MNRAS.481.1976Z and nominal values with large uncertainties in 2018ApJ...869...27V. | Present hard rejection as one paper’s method. Otherwise specify the measurement or censored-data likelihood and the code’s limit semantics.

- SR-11 | medium | science | “14.7 K at z=4.43”; “23.4 K at z=7.5”; prior “12.6<T_d” | The stated formula, **2.73(1+z)**, gives approximately **14.8 K** and **23.2 K**. Moreover, the 2025A&A...695L..15F pack lists both a 12.6 K bound and a CMB-based bound at z=4.601, where the formula gives **15.3 K**. The pack itself is inconsistent here. | Separate quoted paper values from calculated values, flag the conflicting prior, and enforce a physically consistent temperature bound in new fits.

- SR-12 | medium | omission | “AGN component only if Delta BIC > 10” | 2024ApJ...965..108U applies this comparison with sample restrictions: AGN components are always excluded for tiers 2–6. It also rejects one threshold-passing classification using other images and SED evidence. | State the restricted applicability, define ΔBIC and use non-reduced χ²; require independent plausibility checks before accepting an AGN classification.

- SR-13 | medium | omission | “Blending, apertures, redshift” and verification checklist | Redshift-induced scatter is reported, but there is no actionable requirement to propagate redshift uncertainty. 2024ApJ...965..108U explicitly admits omitting photo-z errors from its main analysis and underestimating model errors. | Require redshift uncertainty propagation or conditional refits, and record the cosmology used for luminosity distances.

- SR-14 | medium | omission | “Same emission in every band: a common solid angle” | Matching apertures or beams does not ensure matching interferometric spatial filtering. The pack explicitly records matching the minimum uv-distance across bands in 2023PASJ...75..874M. | Add a check of overlapping spatial-frequency coverage and recovered angular scales before interpreting continuum colours.

- SR-15 | medium | omission | “Resolved Galactic maps: PPMAP with 8 MBB temperature components” | The 2024A&A...687A.217D workflow also handles saturated maps, tests interpolation, refines temperature ranges, and admits beam dilution and ring artifacts. These safeguards are absent from the abbreviated recipe. | Add preprocessing and artifact checks, including with/without-interpolation comparisons and sensitivity to beam dilution and temperature-grid boundaries.

- SR-16 | medium | omission | “Full list” of SFR conversions | The conversion table omits **SFR = 8×10^-11 L_IR**, explicitly calibrated in 2024ApJ...964...95S and used for its three optical–NIR nondetections. This is a central source card, not an incidental example. | Include the sample-calibrated relation, its 100 Myr SFH basis and restricted use; distinguish it from standard IR calibrations.

- SR-17 | low | usability | “Gaussian or uv-plane fit (CASA imfit …)” | The placement can imply that `imfit` fits visibilities; it fits image-plane Gaussian components. | Explicitly separate image-plane `imfit` from visibility-fitting tools.

## Notes

The thin-flux and general-opacity slab formulas are consistent with each other.
The stated missing-setting sums—79 line-free, 21 primary-beam and 51 flux-scale mentions—match the listed labels.
Bibliographic inclusion alone cannot validate a numerical setting or software attribution.
No explicit held-out target names or labelled team-experience claims appear in the supplied skill; the unseen source list remains unassessed.