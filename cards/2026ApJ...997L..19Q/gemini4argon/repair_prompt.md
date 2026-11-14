# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026ApJ...997L..19Q\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Isotopic Ratios in the Disk of HD 163296

## Abstract

Isotopic abundance ratios in protoplanetary disks are critical for understanding volatile inheritance and chemical evolution in planet-forming environments. We present Atacama Large Millimeter/submillimeter Array observations of the rare isotopologue $^{13}$C$^{18}$O(2–1) at $\sim$0.3$''$ resolution from the disk around the Herbig Ae star HD 163296, combined with archival observations of C$^{17}$O(2–1), C$^{18}$O(1–0), and C$^{17}$O(1–0), to empirically constrain carbon and oxygen isotopic ratios without detailed disk modeling. Both the C$^{17}$O/$^{13}$C$^{18}$O(2–1) and C$^{18}$O/C$^{17}$O(1–0) flux ratios rise sharply across the CO snowline and flatten beyond 1.5$''$ ($r \gtrsim 150$ au), where the emission becomes optically thin. This transition, reflecting a steep drop in CO column density set by the disk’s thermal structure, makes HD 163296 an optimal case for isotopic analysis. Using beam-averaged intensities of the four transitions measured in this optically thin region, we derive isotopic ratios of $^{12}$C/$^{13}$C = $75.3^{+14.7}_{-11.4}$ and $^{18}$O/$^{17}$O = $3.28^{+0.31}_{-0.26}$, both consistent with local interstellar medium values. The $^{16}$O/$^{18}$O ratio remains weakly constrained due to moderate optical depth in the C$^{18}$O(1–0) line and degeneracy with CO column density. These results demonstrate that rare CO isotopologues can provide robust, empirical constraints on isotopic ratios in disks when sharp structural transitions allow for the identification of optically thin regions, and establish HD 163296 as a benchmark for extending such studies to other systems with resolved snowline structures.

show\]cqi1@bu.edu

# Introduction

Isotopic abundance ratios in disk gases provide key clues about the chemical heritage and evolution of planetary systems. In particular, the carbon ($^{12}$C/$^{13}$C) and oxygen ($^{18}$O/$^{17}$O) isotope ratios link protoplanetary disks to their parent molecular clouds and to solar system material. The local interstellar medium (ISM) exhibits a carbon isotope ratio significantly lower than the modern solar value (the ISM $^{12}$C/$^{13}$C $\approx$ 68–70 vs. $\approx$ 89 in terrestrial material; e.g., (cite: Milam2005)), reflecting Galactic chemical evolution. Measurements of CN in comets show $^{12}$C/$^{13}$C $\sim$ 91$\pm$4 (cite: Manfroid2009), suggesting that carbon in cometary ices, and by extension in the protosolar disk, was not strongly fractionated compared to Earth. Protoplanetary disks, which mediate the inheritance or resetting of these isotopic ratios, are therefore key to tracing the chemical connection between the ISM and planetary systems.

Recent observations show that isotopic ratios in disks can deviate from ISM values due to disk-specific physical conditions and isotope-selective chemistry that alter CO isotopologue abundances with radius. In TW Hya, an analysis of optically thin line wings finds $^{12}$CO/$^{13}$CO $\simeq 21 \pm 5$ at $r \sim$70–110 au, rising to $\gtrsim$84 beyond $\sim$130 au, revealing strong spatial variations in the carbon isotope ratio (cite: Yoshida2022). Models that explicitly incorporate isotope-selective chemistry, including selective photodissociation and low-temperature exchange reactions, are essential to reproduce and interpret such spatial variations. Selective photodissociation arises because rare isotopologues such as C$^{18}$O and C$^{17}$O experience reduced self‑ and mutual shielding compared to $^{12}$CO and $^{13}$CO, making them more easily dissociated in UV‑irradiated surface layers or in disks with significant grain growth (cite: Visser2009). Low‑temperature exchange reactions can further enhance $^{13}$CO in cold, CO‑depleted regions where ion–molecule chemistry is efficient (cite: Furuya2022; Lee2024). These pathways naturally produce vertical gradients in isotopologue abundances, since photodissociation dominates in the warm surface while exchange reactions operate more effectively in the cold midplane. As a result, midplane‑tracing lines may yield different apparent isotopic ratios than lines that preferentially arise from higher disk layers. Recent thermochemical implementations in DALI and NAUTILUS, which include isotope‑selective photodissociation, grain‑surface CO processing, and CO-–CO$_2$ interconversion, demonstrate that these combined effects generate substantial radial and vertical structure in CO isotopologue abundances and can bias gas‑mass determinations if not accounted for (cite: Miotello2016; Miotello2021; Ruaud2022; Deng2023; Deng2025). For oxygen, optically thin HCO$^+$ isotopologue ratios toward TW Hya yield $^{13}$CO/C$^{18}$O = $8.3 \pm 2.6$, consistent with the local ISM (cite: Furuya2022), suggesting no strong evidence for $^{18}$O depletion in the bulk CO gas.

Other carbon-bearing molecules in disks show different isotopic behaviors. (cite: Hily-Blant2019) reported that the disk-averaged H$^{12}$CN/H$^{13}$CN ratio in TW Hya is $86 \pm 4$, higher than the local ISM value and closer to the solar value. In contrast, (cite: Yoshida2024) measured the $^{12}$CN/$^{13}$CN ratio to be $70^{+9}_{-6}$ at 30–80 au, consistent with the ISM, but differing from the ratios found for CO and HCN in the same disk. These results highlight that different molecules can trace distinct reservoirs of carbon and may carry different isotopic signatures, underscoring the complexity of disk chemistry and the importance of molecule-specific diagnostics.

Accurate determinations of C and O isotopic ratios in disks are needed for understanding disk chemistry and for comparison to solar system materials. From the observational perspective, there are two key challenges: optical depth and sensitivity. First, the abundant CO isotopologue lines are often optically thick, and therefore, the line emission does not directly correspond to column density. While rare species like C$^{18}$O are typically assumed to be optically thin, recent studies demonstrate that C$^{18}$O (and even C$^{17}$O) can become optically thick in bright disks (cite: Law2021), leading to biased abundance estimates if optical depth is not properly accounted for. The optical depth of CO isotopologue lines depends sensitively on the disk’s vertical temperature structure. As shown by (cite: Qi2024), disks with a thick vertically isothermal region around the midplane (VIRaM layer) exhibit a sharp drop in CO column density across the CO snow line, which provides a well-defined boundary where emission transitions from optically thick to optically thin. In contrast, disks with a thin VIRaM layer show a more gradual radial decrease in CO column density, making it difficult to identify the optically thin region observationally. Second, although the outermost disk regions eventually reach low enough column densities to ensure low optical depth emission from the rare, optically thin CO isotopologues, their emission is intrinsically weak, often precluding robust detections with current instruments and limiting isotopic ratio measurements.

Given the challenges of disentangling optical depth effects from underlying disk structure when interpreting CO isotopologue emission, it is essential to develop observational strategies that enable robust and preferably model-independent determinations. Measuring flux ratios of multiple rare CO isotopologues observed at the same excitation level, such as C$^{17}$O and C$^{18}$O in the $J=1\rightarrow0$ transition or $^{13}$C$^{18}$O and C$^{17}$O in the $J=2\rightarrow1$ transition, provides an empirical means to constrain isotopic ratios while minimizing assumptions. This approach parallels hyperfine analyses of molecules like CN and HCN (cite: Hily-Blant2019), but is here applied to CO isotopologues. The present study is the first to use high signal-to-noise $^{13}$C$^{18}$O(2–1) observations of the HD 163296 disk to empirically identify an optically thin region beyond the sharply defined CO snowline, directly from the flux ratio behavior, without relying on detailed physical or chemical modeling. This enables more direct and model-independent determinations of the $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O ratios in a protoplanetary disk. The methodology established here provides a framework for extending isotopic studies to other systems with resolved snowline structures.

Our letter is organized as follows. In Section [2](#sec:obs) we describe the Atacama Large Millimeter/submillimeter Array (ALMA) observations and present the radial profiles of the CO isotopologues, highlighting the sharp CO snowline transition. Then, we quantify how the same transition flux ratios trace optical depth and apply this diagnostic to HD 163296. In Section [3](#sec:mcmc) we use beam-averaged line intensities in the optically thin outer disk to constrain isotopic ratios through Markov Chain Monte Carlo (MCMC) fitting. In Section [4](#sec:conclusions) we summarize our conclusions and discuss the implications of our results for disk chemistry and comparisons with other disks and solar system reservoirs.

# Observations and Results

The disk around the Herbig Ae star HD 163296 provides an optimal environment to search for optically thin regions in rare CO isotopologue emission, owing to its previously established sharp CO snowline transition at a readily accessible spatial scale (cite: Qi2024). New, deep ALMA observations of the $^{13}$C$^{18}$O(2–1) line provide the basis for a fresh examination. A detailed description of the observations (Project ID: 2021.1.00899.S, PI: K. Zhang) is given by T. Armitage et al. (ApJ accepted). The data reduction and imaging were performed using `CASA` v6.6.3 (cite: McMullin2007; CASA+2022), following standard pipeline calibration, self-calibration for improved signal-to-noise, and imaging with the `tclean` task using Briggs weighting (robust 0.5). The final image has a beam size of $0.28\ensuremath{''} \times 0.25\ensuremath{''}$, CLEANed to a $3\sigma$ threshold, corrected for the so called (cite: Jorsater1995) effect (cite: Czekala2021), and primary beam corrected. The velocity field of the $^{13}$C$^{18}$O(2–1) emission is consistent with Keplerian rotation in the disk and matches the kinematic pattern traced by the other CO isotopologues (see Appendix [5](#app:13c18o_mom1)).

Figure [1](#fig:13c18o21_profile) shows the radial profile of the $^{13}$C$^{18}$O(2–1) integrated intensity and its radial derivative. The intensity decreases smoothly with radius, and the derivative exhibits a clear local minimum at 0.75$''$, coincident with the CO snowline radius inferred from other CO isotopologues (cite: Qi2024). This feature indicates a sharp drop in the CO column across the snowline. At this location, the midplane temperature is approximately 20 K, near the CO freezeout threshold; the $^{13}$C$^{18}$O(2–1) transition has $E_u/k \approx 15$ K and thus traces gas close to this thermal boundary. (cite: Qi2024) performed forward radiative‐transfer calculations for the C$^{17}$O(2–1), C$^{18}$O(1–0), and C$^{17}$O(1–0) lines and showed that the observed dip in the radial derivative of the integrated-intensity profile cannot be produced by plausible excitation gradients alone and a sharp drop in the CO column density at the snowline is required. Because $^{13}$C$^{18}$O(2–1) is optically thinner than those transitions, the persistence of the derivative dip in this line further indicates that the feature is not an opacity artifact. In combination with the archival C$^{17}$O and C$^{18}$O data, the new $^{13}$C$^{18}$O observations allow us to constrain the region where all lines are optically thin, enabling a direct empirical determination of the isotopic ratios.

![](dataprofile_13c18o21b.png)

To enable accurate flux ratio measurements, we reimaged each transition to a common circularized beam of $0.52\ensuremath{''}$, defined by the major axis of the synthesized beam for C$^{17}$O(2–1) with robust 0.5 weighting and a $u,v$ taper, following the MAPS cleaning strategy (cite: Czekala2021). The JvM correction and primary beam correction were applied consistently to all transitions, and deprojected, azimuthally averaged radial profiles were extracted using the `radial_profile` function from `GoFish` (cite: Teague2019). Figure [2](#fig:ratio_profiles) presents the resulting radial profiles of the C$^{17}$O/$^{13}$C$^{18}$O(2–1) and C$^{18}$O/C$^{17}$O(1–0) flux ratios. For the C$^{17}$O/$^{13}$C$^{18}$O(2–1) profile, we propagate both the statistical map uncertainties and a 7.1% systematic calibration term that represents the worst case of uncorrelated 5% absolute flux errors between the Band 6 datasets, whereas for the C$^{18}$O/C$^{17}$O(1–0) profile we include only statistical uncertainties because the two Band 3 lines share a common flux scale and their calibration errors are highly correlated. A detailed discussion of flux calibration uncertainty propagation for these ratios is given in Appendix [6](#app:uncertainty_ratios).

Both ratios remain relatively flat inside 0.75$''$, consistent with high optical depth, then rise rapidly across the CO snowline and converge to plateaus beyond 1.5$''$ ($r \gtrsim 150$ au), where all lines become optically thin. This rapid increase, followed by a common plateau, reflects the steep decline in CO column density across the CO snowline (cite: Qi2024). Because the intrinsic snowline transition is demonstrated to be sharp, the $0.52\ensuremath{''}$ beam broadens the observed rise in the flux ratios over a radial range of approximately 0.5$''$. This modest beam smearing smooths the slope of the transition but does not affect the optically thin plateau values that are used for the isotopic ratio analysis. The C$^{17}$O/$^{13}$C$^{18}$O(2–1) ratio approaches approximately 20, consistent with the ISM value expected under optically thin emission conditions for both lines, while the C$^{18}$O/C$^{17}$O(1–0) ratio stabilizes near 2.7, implying moderate optical depth in the C$^{18}$O(1–0) line for ISM-like abundances (see Section [2.1](#sec:ratios)). Together, these behaviors identify the outer region around and beyond 1.5$''$ where isotopic ratios can be reliably constrained.

![image](ratios0.52arcsec_c17o13c18o21b.png) ![image](ratios0.52arcsec_c18oc17o10b.png)

## Constraining Optical Depths with Same-transition Isotopologue Flux Ratios

To quantify how same-transition isotopologue flux ratios vary with line-center optical depth, we performed a systematic non-LTE radiative transfer analysis using the `RADEX` code (cite: vanderTak2007) through the Python package `SpectralRadex` (cite: Holdship2021). We adopted molecular data from the LAMDA database (cite: Schoier2005), using collisional rate coefficients from (cite: Yang2010). Collisions with both ortho- and para-H$_2$ were included, assuming an ortho-to-para ratio of 3:1, and level populations were solved with the Cosmic Microwave Background (CMB) as the only background radiation field ($T_{\rm bg} = 2.73$ K). We adopted canonical ISM isotopic ratios (cite: Wilson1999): $^{12}$C/$^{13}$C$= 69$, $^{16}$O/$^{18}$O$= 557$, and $^{18}$O/$^{17}$O$= 3.6$, and explored a grid of kinetic temperatures ($T_{\rm kin} = 30$, 50, 70 K), molecular hydrogen densities ($n_{\rm H_2} = 10^5$–$10^8$ cm$^{-3}$), and CO column densities ($\log N_{\rm CO} = 16$–19).

At each grid point, we derived the isotopologue column densities for C$^{17}$O, C$^{18}$O, and $^{13}$C$^{18}$O from the adopted abundance ratios, then used `RADEX` to compute the line-center optical depth $\tau$ and integrated line flux (in K km s$^{-1}$) for the primary transition (either C$^{18}$O(1–0) or C$^{17}$O(2–1)). The flux ratio was then calculated relative to its rarer counterpart, $^{13}$C$^{18}$O(2–1) or C$^{17}$O(1–0), respectively. Figure [3](#fig:ratio_vs_tau) shows the flux ratios as a function of line-center optical depth.

In the optically thin regime ($\tau \ll 1$), the flux ratios converge to the values set by the adopted ISM isotopic abundances: 19.2 for C$^{17}$O/$^{13}$C$^{18}$O(2–1), corresponding to $^{12}$C/$^{13}$C divided by $^{18}$O/$^{17}$O ($69/3.6$) and 3.6 for C$^{18}$O/C$^{17}$O(1–0), reflecting the $^{18}$O/$^{17}$O ratio. We explicitly tested the sensitivity of these ratio-$\tau$ curves to $\pm30$% variations in the assumed isotopic ratios (Appendix [7](#app:sensitivity)) and found that while the thin-limit plateau shifts as expected, the shape of the ratio as a function of $\tau$ over the $\tau \lesssim 0.3$ regime used to identify the optically thin zone in HD 163296 is essentially unchanged. As the optical depth increases ($\tau \gtrsim 1$), the more abundant line saturates, and the ratio declines rapidly, largely independent of temperature or density across the disk-relevant range. Because both lines in each pair arise from the same $J \rightarrow J-1$ transition and have nearly identical frequencies, their ratios substantially reduce sensitivity to excitation temperature and beam dilution, though vertical differences in the emitting layers can introduce residual effects.

These theoretical expectations match our observations of HD 163296: the measured ratios in Figure [2](#fig:ratio_profiles) rise steeply across the snowline and then level off beyond 1.5$''$. This agreement demonstrates that the ratios provide a direct diagnostic of optical depth and confirms that the outer disk of HD 163296 offers a robust optically thin region suitable for empirical isotopic ratio determinations.

![](ratio_vs_tau_combined2.png)

# MCMC Fitting to Constrain Isotopic Ratios

As described in Section [2](#sec:obs), all CO isotopologue data were reimaged to a common circularized beam of $0.52\ensuremath{''}$ to enable accurate flux ratio measurements. This common beam is essential for consistent comparison across transitions. We then used the `radial_profile` function from the `GoFish` package (cite: Teague2019) to extract deprojected, azimuthally averaged radial intensity profiles. To constrain the isotopic ratios in the optically thin region, we retrieved the integrated intensity in an annulus centered at 1.5$''$, which is effectively smoothed over the $0.52\ensuremath{''}$ beam. These beam-averaged values are summarized in Table [1](#tab:fluxes) and per–channel rms values at the working spectral resolutions are listed in Appendix [8](#app:line-noise), Table [3](#tab:line_noise).

| Transition | Flux (mJy beam$^{-1}$ km s$^{-1}$) | Flux (K km s$^{-1}$) |
|:---|:--:|:--:|
| C$^{17}$O(1–0) | $5.82 \pm 0.29$ | $2.09 \pm 0.10$ |
| C$^{18}$O(1–0) | $15.49 \pm 0.25$ | $5.80 \pm 0.09$ |
| $^{13}$C$^{18}$O(2–1) | $3.33 \pm 0.41$ | $0.34 \pm 0.04$ |
| C$^{17}$O(2–1) | $74.85 \pm 1.17$ | $6.70 \pm 0.10$ |

: Beam-averaged CO isotopologue integrated intensities at 1.5$''$ (around 150 au) in HD 163296

Because the optically thin area is confined to the outer disk and the rare isotopologue lines are weak, we adopted this single beam-averaged annulus at 1.5$''$ for quantitative fitting. Within the uncertainties, no significant radial trend is detected in either ratio across the outer disk region (Fig. [2](#fig:ratio_profiles)), so a single representative radius is sufficient for the isotopic analysis.

We used an MCMC approach to fit these intensities using `RADEX` with seven free parameters: kinetic temperature ($T_{\rm kin}$), molecular hydrogen density ($n_{\rm H_2}$), CO column density ($N_{\rm CO}$), line width ($\Delta V$), and three isotopic ratios ($^{12}$C/$^{13}$C, $^{16}$O/$^{18}$O, and $^{18}$O/$^{17}$O). Priors were chosen to be uninformative but physically bounded: we adopted uniform priors in linear space for $T_{\rm kin}\!\sim\!{\cal U}(10,200)$ K and $\Delta V\!\sim\!{\cal U}(0.1,0.6)$ km s$^{-1}$, and uniform-in-log priors for the scale parameters $\log_{10} n_{\rm H_2}\!\sim\!{\cal U}(4,9)$ and $\log_{10} N_{\rm CO}\!\sim\!{\cal U}(16,20)$. For the isotopic ratios, we used broad uniform priors, $^{12}$C/$^{13}$C$\!\sim\!{\cal U}(10,200)$, $^{16}$O/$^{18}$O$\!\sim\!{\cal U}(100,1000)$, and $^{18}$O/$^{17}$O$\!\sim\!{\cal U}(1,10)$, so that the posteriors are driven by the data rather than by the priors. Table [2](#tab:mcmc_results) summarizes the median posterior values and their 68% confidence intervals.

| Parameter                          |          Value          |
|:-----------------------------------|:-----------------------:|
| $T_{\rm kin}$ (K)                  | $112.1^{+50.5}_{-38.3}$ |
| $\log_{10}(n_{\rm H_2}$/cm$^{-3}$) | $6.05^{+1.34}_{-1.26}$  |
| $\log_{10}(N_{\rm CO}$/cm$^{-2}$)  | $19.25^{+0.25}_{-0.32}$ |
| $\Delta V$ (km s$^{-1}$)           | $0.32^{+0.18}_{-0.15}$  |
| $^{12}$C/$^{13}$C                  | $75.3^{+14.7}_{-11.4}$  |
| $^{16}$O/$^{18}$O                  |   $599^{+276}_{-310}$   |
| $^{18}$O/$^{17}$O                  | $3.28^{+0.31}_{-0.26}$  |

: MCMC Parameter Estimates at 1.5$''$ (around 150 au)

The best-fit isotopic ratios at 1.5$''$ and comparisons with ISM values (cite: Wilson1999) are as follows:

- $^{12}$C/$^{13}$C = $75.3^{+14.7}_{-11.4}$, consistent with the ISM value of $69 \pm 6$;

- $^{18}$O/$^{17}$O = $3.28^{+0.31}_{-0.26}$, consistent with the ISM value of $3.6 \pm 0.2$;

- $^{16}$O/$^{18}$O = $599^{+276}_{-310}$, consistent with the ISM value of $557 \pm 30$ within large uncertainties.

These results confirm that, in the optically thin outer disk of HD 163296, the carbon and oxygen isotopic ratios are broadly consistent with those of the local ISM. The corner plot of the posterior distributions, which illustrates parameter covariances and uncertainties, is shown in Appendix [9](#app:posterior). As demonstrated by the calibration sensitivity tests in Appendix [10](#app:calib), $5$–$10$% flux scale offsets do not shift the inferred isotopic ratios beyond their quoted uncertainties. The $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O ratios show minimal covariance with the physical parameters, indicating that they are constrained directly by the $^{13}$C$^{18}$O and C$^{17}$O fluxes in the optically thin regime. The relatively clean constraints on these ratios underscore the value of rare isotopologues for probing intrinsic elemental abundances in disks. In contrast, the $^{16}$O/$^{18}$O ratio remains weakly constrained because C$^{18}$O(1–0) is only marginally optically thick at line center and because of strong parameter covariance. In particular, $^{16}$O/$^{18}$O correlates positively with $\log N_{\rm CO}$: higher oxygen isotope ratios can be offset by lower CO columns while preserving the C$^{18}$O intensity. The $T_{\rm kin}$, $n_{\rm H_2}$, and $\Delta V$ parameters also show broad, unconstrained posteriors, as expected for optically thin conditions in which line intensities are relatively insensitive to these quantities. We note that in our `RADEX` calculations, $\Delta V$ represents the local thermal plus microturbulent FWHM, not the beam-smeared Keplerian shear. The posterior value $\Delta V\sim0.3$ km s$^{-1}$ therefore reflects local broadening at the emitting layer rather than the total observed profile width.

# Conclusions and future work

We have shown that same-transition isotopologue flux ratios provide a direct and model-independent diagnostic of optical depth in protoplanetary disks. New ALMA observations of the rare $^{13}$C$^{18}$O(2–1) line confirm the sharp CO snowline transition in the HD 163296 disk at 0.75$''$. Together with archival C$^{17}$O and C$^{18}$O data reimaged to a common circularized beam, these observations reveal flux ratios that rise steeply across the snowline and converge to constant values beyond 1.5$''$, identifying an outer region where all lines are optically thin. The beam-averaged line intensities from this region were used in an MCMC analysis to derive isotopic ratios. The results yield $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O values consistent with local ISM abundances, while $^{16}$O/$^{18}$O remains poorly constrained due to residual optical depth in the C$^{18}$O(1–0) line. These findings demonstrate that rare CO isotopologues provide robust, empirical constraints on isotopic ratios in disks and establish a framework for extending such studies to other systems with resolved snowline structures.

The ISM-like $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O ratios in HD 163296’s outer disk suggest that the bulk gas reservoir has remained largely unprocessed since formation. Comparable results have been reported in other disks, such as PDS 70 (cite: Rampinelli2025), whereas TW Hya shows strong CO fractionation in the inner disk but near-ISM ratios at larger radii (cite: Hily-Blant2019; Yoshida2022). These comparisons indicate that isotope-selective processes, while present in localized regions or specific molecules, may not strongly alter the outer disk gas, or that efficient mixing with unfractionated material preserves ISM-like compositions. The preservation of interstellar carbon and oxygen isotope ratios in HD 163296 parallels the record in primitive solar system reservoirs, where bulk carbon and oxygen remain close to cosmic values, while nitrogen and hydrogen exhibit large anomalies in comets and meteorites (cite: Altwegg2019; Rubin2019). Together, these results support the view that outer disks can serve as relatively pristine isotopic reservoirs, linking the chemistry of the parent cloud to the material incorporated into planetesimals and comets.

The connection to solar system materials is suggestive but necessarily tentative, because our measurements trace gas in the outer disk, whereas meteoritic and cometary values primarily record ices and refractory solids. Gas–-ice exchange, selective photodissociation, low-temperature isotope exchange, and transport across snowlines can decouple gas-phase and solid-phase isotopic signatures. In this context, the ISM-like gas ratios in HD 163296 indicate that the outer disk can preserve interstellar compositions, but do not by themselves establish the isotopic makeup of the ices that seed planetesimals. A broader, method-consistent survey that combines gas and solid tracers will be needed to discriminate inheritance from disk-level resetting.

Deeper integrations and, still rarer, optically thinner tracers will sharpen these constraints and enable radial tests. In particular, spatially resolved measurements of $^{13}$C$^{18}$O(1–0) and $^{13}$C$^{17}$O(1–0), obtained with matched beams and uniform calibration, would reduce covariance with $N_{\rm CO}$ and directly probe the $^{16}$O/$^{18}$O ratio in the thin limit. Higher sensitivity will also permit annulus-by-annulus fits beyond $1.5\ensuremath{''}$ to search for subtle radial trends and vertical gradients via same–transition ratios. Looking ahead, the ngVLA’s superior 3 mm sensitivity and subarcsecond resolution at the CO isotopologue (1–0) frequencies will map these faint lines over large areas, providing a powerful, model-independent census of carbon and oxygen isotopic ratios across disks.

We thank the anonymous referee for a constructive report, which improved the paper. C.Q. thanks Floris van der Tak and Alice Booth for helpful discussions. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00884.S, ADS/JAO.ALMA#2018.1.01055.L, and\
ADS/JAO.ALMA#2021.1.00899.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc.

# Facilities

ALMA

# Software

Astropy (cite: Astropy2013; Astropy2018; Astropy2022), `bettermoments` (cite: Teague2018), `CASA` (cite: CASA+2022), `emcee` (cite: emcee), `GoFish` (cite: Teague2019), Matplotlib (cite: Hunter2007), NumPy (cite: vanderWalt2011), `RADEX` (cite: vanderTak2007), `SpectralRadex` (cite: Holdship2021).

# Kinematics of $^{13}$C$^{18}$O(2–1) Emission

To verify that the detected $^{13}$C$^{18}$O(2–1) emission arises from the disk and follows Keplerian rotation, we present the moment-1 (intensity-weighted velocity) map in Figure [4](#fig:13c18o_moments), overlaid with moment-0 (integrated intensity) contours. These maps were generated using the `bettermoments` package (cite: Teague2018), with a $2\sigma$ intensity clip to mitigate noise bias. The velocity pattern clearly traces a Keplerian gradient aligned with the disk’s major axis, and the emission is confined within the disk extent seen in other isotopologues (cite: Qi2011).

![](hd163296_13c18o21_momc.png)

# Flux Calibration Uncertainty Propagation for Ratios

Absolute flux calibration uncertainties introduce systematic errors into line ratio measurements, particularly when the lines are observed in different frequency bands or at different epochs. We adopt the standard ALMA absolute calibration uncertainty of approximately 5% per dataset. The propagated fractional uncertainty on a flux ratio $R = F_1/F_2$ can be expressed as $$\begin{equation}
\frac{\sigma_R}{R} \approx \sqrt{\epsilon_1^2 + \epsilon_2^2 - 2\rho \epsilon_1\epsilon_2},
\end{equation}$$ where $\epsilon_i$ are the fractional flux calibration uncertainties for the two datasets, and $\rho$ is the correlation coefficient between their amplitude calibration.

For ratios between lines observed in the *same* band and session, such as C$^{18}$O(1–0) and C$^{17}$O(1–0), the calibration errors are highly correlated ($\rho \approx 1$). In this case, the propagated uncertainty from flux calibration is negligible, and the ratio uncertainty is dominated by statistical map noise and small relative effects between spectral windows (typically $\lesssim 1$–2%).

For ratios involving lines observed in *different* bands or epochs, such as C$^{17}$O(2–1)/$^{13}$C$^{18}$O(2–1), the correlation is lower. In the worst-case scenario where the calibration errors are uncorrelated ($\rho = 0$), the systematic contribution to the ratio uncertainty is $\sqrt{2} \times$ 5% $\approx$ 7.1%. We therefore include a 7.1% systematic calibration uncertainty in quadrature for the C$^{17}$O/$^{13}$C$^{18}$O(2–1) ratio in Figure [2](#fig:ratio_profiles).

Beam matching, primary beam correction, and JvM correction are common-mode processing steps applied consistently across all datasets. These steps do not introduce additional systematic uncertainty into the ratio measurements, although minor imperfections in beam circularization or JvM application may contribute small residual effects.

# Sensitivity of the Ratio–Optical Depth Diagnostic to Assumed Isotopic Ratios

We tested whether our optical depth inference depends on the adopted elemental isotope ratios in the `RADEX` grids. We focus on the same-transition ratios used in the main text: C$^{17}$O/$^{13}$C$^{18}$O(2–1) and C$^{18}$O/C$^{17}$O(1–0).

#### Test A: independent variation of $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O.

Figure [5](#fig:appendix_c17o13c18o_sens) shows how the C$^{17}$O/$^{13}$C$^{18}$O(2–1) ratio changes when $^{12}$C/$^{13}$C is varied by $\pm$30% at fixed $^{18}$O/$^{17}$O (left), and when $^{18}$O/$^{17}$O is varied by $\pm$30% at fixed $^{12}$C/$^{13}$C (right). As expected, the optically thin limit shifts with the assumed elemental ratios: $$\left.\mathrm{C}^{17}\mathrm{O}/{}^{13}\mathrm{C}^{18}\mathrm{O}\right|_{\tau\rightarrow 0}
= (^{12}\mathrm{C}/^{13}\mathrm{C})/(^{18}\mathrm{O}/^{17}\mathrm{O}).$$ However, after normalizing each curve by its own thin-limit value, the ratio–$\tau$ profiles collapse to nearly identical shapes. This demonstrates that the optical depth response—the turnover away from the thin-limit plateau—is essentially insensitive to $\pm$30% variations in either elemental ratio.

#### Test B: coherent scaling of the full elemental set.

Figure [6](#fig:appendix_ratio_tau_sens) shows the effect of scaling all isotopic ratios coherently by $\pm$30% around the ISM values. Both the C$^{17}$O/$^{13}$C$^{18}$O(2–1) and C$^{18}$O/C$^{17}$O(1–0) ratio profiles are examined. As in Test A, the absolute thin-limit plateaus shift as expected, but the normalized ratio–$\tau$ curves agree to within $\lesssim$1–2% for $\tau \lesssim 0.3$, the regime used to identify the optically thin region in HD 163296.

#### Summary.

Both tests show that while the absolute optically thin limit encodes the elemental isotope ratios, the shape of the ratio–optical depth relation—which we use to locate the optically thin region beyond $1.5\ensuremath{''}$ is robust to plausible ($\pm$30%) variations in $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O. Our optical depth mapping and selection of the thin region are therefore not sensitive to the exact isotope ratios assumed in the modeling grid.

![](c17o_13c18o_independent_sensitivity.png)

![](ratio_tau_sensitivity.png)

# Line Properties and Noise

Table [3](#tab:line_noise) summarizes the rest frequencies, spectral channel widths, and per–channel rms sensitivities for the reimaged data products used in this work. All datasets were tapered and Briggs weighted to a common circularized beam (FWHM $0.52\ensuremath{''}$). The quoted $\sigma_{\rm chan}$ values are measured in line–free channels at the tabulated spectral resolutions.

| Transition | $\nu_{\rm rest}$ (GHz) | Channel width (km s$^{-1}$) | $\sigma_{\rm chan}$ (mJy beam$^{-1}$) |
|:---|:--:|:--:|:--:|
| C$^{17}$O(1–0) | 112.359 | 0.50 | 0.51 |
| C$^{18}$O(1–0) | 109.782 | 0.50 | 0.48 |
| $^{13}$C$^{18}$O(2–1) | 209.419 | 0.32 | 1.17 |
| C$^{17}$O(2–1) | 224.714 | 0.32 | 2.54 |

: CO isotopologue line properties and per–channel noise (common circularized beam)

# Posterior Structure and Parameter Covariance

#### Full posterior corner plot.

Figure [7](#fig:mcmc_corner) shows the corner plot of the posterior distributions from our MCMC analysis, highlighting covariances between parameters. The marginalized one–dimensional posteriors for $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O are well converged and approximately Gaussian, yielding precise estimates. In contrast, the posteriors for $^{16}$O/$^{18}$O, $\log N_{\rm CO}$, and to a lesser extent $\Delta V$, are broader and show notable covariance, consistent with the moderate optical depth of C$^{18}$O(1–0) discussed in Section [3](#sec:mcmc). These trends also motivate the use of rarer and more optically thin tracers to improve constraints on $^{16}$O/$^{18}$O.

![](mcmc7_isotopratios2.png)

#### Two-dimensional covariance between $^{16}$O/$^{18}$O and $N_{\rm CO}$.

To visualize the specific degeneracy between the oxygen isotopic ratio and the CO column density, Figure [8](#fig:covar_R16_Nco) shows the two–dimensional posterior for $^{16}$O/$^{18}$O and $\log N_{\rm CO}$ from the same MCMC chains used in Figure [7](#fig:mcmc_corner). The distribution forms a ridge that runs from $\log_{10} N_{\rm CO} \sim 18.5$ with $^{16}$O/$^{18}$O $\sim 200$ up to $\log_{10} N_{\rm CO} \sim 19.6$ with $^{16}$O/$^{18}$O $\gtrsim 800$. This structure reflects the fact that, at the inferred optical depths of C$^{18}$O(1–0), an increase in $^{16}$O/$^{18}$O (which reduces $N_{\rm C^{18}O}$ at fixed $N_{\rm CO}$) can be compensated by a higher total CO column in order to match the observed C$^{18}$O intensity. This covariance explains why $^{16}$O/$^{18}$O is less tightly constrained than $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O, whose posteriors show minimal correlation with $N_{\rm CO}$.

![](covar_R16_Nco_joint.png)

# Calibration Sensitivity

We quantified how absolute–flux systematics propagate into the posteriors with two bracketing tests that leave the modeling and priors unchanged and only rescale the four measured, beam–averaged integrated intensities used in the MCMC.

#### Global $\pm 10\%$ rescaling.

All four lines were multiplied by the same gain factor ($g=0.90,\,1.00,\,1.10$). Relative to the baseline ($g=1.00$), the median shifts were small: $\Delta(^{12}\mathrm{C}/^{13}\mathrm{C})=\{-1.281,+0.507\}$, $\Delta(^{18}\mathrm{O}/^{17}\mathrm{O})=\{-0.001,+0.016\}$, $\Delta(^{16}\mathrm{O}/^{18}\mathrm{O})=\{-33.410,+14.826\}$, and $\Delta\log N_{\rm CO}=\{-0.054,+0.099\}$. As expected, a global gain leaves the within–band, same–transition ratios that set $^{12}\mathrm{C}/^{13}\mathrm{C}$ and $^{18}\mathrm{O}/^{17}\mathrm{O}$ essentially unchanged and primarily rescales $N_{\rm CO}$.

#### Per–band $\pm 10\%$ test (worst–case inter–band mismatch).

We scaled Band 3 (1–0 lines: C$^{18}$O, C$^{17}$O) and Band 6 (2–1 lines: $^{13}$C$^{18}$O, C$^{17}$O) in opposite directions to bracket a realistic inter–band calibration offset: $(g_{\rm B3},g_{\rm B6})=(1.10,0.90)$ and $(0.90,1.10)$. Median shifts relative to the baseline were $\Delta(^{12}\mathrm{C}/^{13}\mathrm{C})=\{+29.831,\,-16.296\}$, $\Delta(^{18}\mathrm{O}/^{17}\mathrm{O})=\{+0.537,\,-0.455\}$, $\Delta(^{16}\mathrm{O}/^{18}\mathrm{O})=\{-30.321,\,+29.024\}$, and $\Delta\log N_{\rm CO}=\{-0.100,\,+0.169\}$. These runs deliberately force a strong mismatch between the bands. The relatively large response of $^{12}\mathrm{C}/^{13}\mathrm{C}$ arises because the likelihood is defined on all four absolute fluxes, which couples the Band 3 and Band 6 data through shared parameters ($N_{\rm CO}$, $T_{\rm kin}$, $\Delta V$), even though the main observational leverage on $^{12}\mathrm{C}/^{13}\mathrm{C}$ comes from the same–transition ratio C$^{17}$O/$^{13}$C$^{18}$O(2–1) within Band 6.

| Scenario | $\Delta(^{12}\mathrm{C}/^{13}\mathrm{C})$ | $\Delta(^{18}\mathrm{O}/^{17}\mathrm{O})$ | $\Delta(^{16}\mathrm{O}/^{18}\mathrm{O})$ | $\Delta\log N_{\rm CO}$ |
|:---|:--:|:--:|:--:|:--:|
| Global $g=0.90$ | $-1.281$ | $-0.001$ | $-33.410$ | $-0.054$ |
| Global $g=1.10$ | $+0.507$ | $+0.016$ | $+14.826$ | $+0.099$ |
| Per-band $(g_{\rm B3},g_{\rm B6})=(1.10,0.90)$ | $+29.831$ | $+0.537$ | $-30.321$ | $-0.100$ |
| Per-band $(g_{\rm B3},g_{\rm B6})=(0.90,1.10)$ | $-16.296$ | $-0.455$ | $+29.024$ | $+0.169$ |

#### Summary.

All the corresponding median shifts are summarized in Table [\[tab:cal_sens\]](#tab:cal_sens). The global test leaves $^{12}\mathrm{C}/^{13}\mathrm{C}$ and $^{18}\mathrm{O}/^{17}\mathrm{O}$ stable while mainly shifting $N_{\rm CO}$. Even under these deliberately extreme inter–band offsets, the inferred $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O values remain statistically consistent with both the baseline solution and the local ISM within their quoted uncertainties, while $^{16}$O/$^{18}$O is further broadened but already poorly constrained. Together with the global $\pm 10\%$ scaling tests, these results show that our main isotopic conclusions, which rely on same–transition ratios in the optically thin outer disk, are robust against 5–10% absolute flux calibration systematics.

</paper>

## Items to check

```json
[
 {
  "path": "data.alma_project_codes[0].evidence[0]",
  "value": "2016.1.00884.S",
  "failed_quote": "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00884.S, ADS/JAO.ALMA#2018.1.01055.L, and ADS/JAO.ALMA#2021.1.00899.S."
 },
 {
  "path": "data.alma_project_codes[1].evidence[0]",
  "value": "2018.1.01055.L",
  "failed_quote": "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00884.S, ADS/JAO.ALMA#2018.1.01055.L, and ADS/JAO.ALMA#2021.1.00899.S."
 },
 {
  "path": "data.alma_project_codes[2].evidence[1]",
  "value": "2021.1.00899.S",
  "failed_quote": "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00884.S, ADS/JAO.ALMA#2018.1.01055.L, and ADS/JAO.ALMA#2021.1.00899.S."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "ALMA project codes ADS/JAO.ALMA#2016.1.00884.S, ADS/JAO.ALMA#2018.1.01055.L, and ADS/JAO.ALMA#2021.1.00899.S are cited.",
  "failed_quote": "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00884.S, ADS/JAO.ALMA#2018.1.01055.L, and ADS/JAO.ALMA#2021.1.00899.S."
 }
]
```
