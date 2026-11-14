# Giant star-forming clumps?

`2020MNRAS.495L...1I` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Ivison, R. J. | arXiv: 2003.07863 | DOI: 10.1093/mnrasl/slaa046

Card schema 1.0 | model gpt-6.1-sol | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, star_formation
- Question: Does the Cosmic Eyelash contain significant dusty star-forming clumps?  
  > "Our images reveal that the dust continuum emission from the Cosmic Eyelash is smoothly distributed" (Summary); "with no evidence of significant star-forming clumps down to a spatial scale of $\approx 80$ pc" (Summary)
- Target **SMM J21352−0102 / Cosmic Eyelash**: coordinates _not stated_; z/distance z=2.3  
  > "SMM J21352$-$0102, or the Cosmic Eyelash" (Introduction); "We present sensitive, high-spatial-resolution ALMA continuum imaging of the Cosmic Eyelash, at $z=2.3$" (Summary); "This was determined by (cite: swinbank10) via detection of CO $J=1$–0 using the Green Bank Telescope" (Introduction); distance from _not stated_
- Target **MACS J2135−01**: coordinates _not stated_; z/distance z = 0.325  
  > "The Cosmic Eyelash lies behind the $z = 0.325$ galaxy cluster, MACS J2135$-$01, which amplifies it gravitationally by a factor, $\mu=37.5$." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00175.S, 2012.1.01029.S, 2013.1.00164.S, 2016.1.00282.S
- bands: bands 6 and 7  
  > "The Cosmic Eyelash has been observed several times with ALMA, predominantly in bands 6 and 7." (Observations and data reduction)
- frequencies and spectral setup: Average frequencies 251.0, 303.9, 345.0 and 356.4 GHz; dual-polarisation TDM; 2 GHz usable bandwidth per spectral window  
  > "| 2016.1.00282.S | CH$^+$ | 251.0 | 21 | $225 \times 160$ |" (Table 1); "All observations were conducted in dual-polarisation mode with low-spectral-resolution time-division mode (TDM) spectral windows, i.e. with 2 GHz of usable bandwidth." (Observations and data reduction); "| 2012.1.00175.S | H$_2$O | 356.4 | 48 | $232 \times 167$ |
| 2012.1.01029.S | SC | 345.0 | 60 | $282 \times 246$ |" (Table 1)
- continuum bandwidth: Single-continuum mode: Δν = 7.5 GHz  
  > "One project used ALMA’s maximum-bandwidth ($\Delta \nu = 7.5$ GHz) ‘single-continuum’ (SC) mode" (Observations and data reduction)
- arrays: _not stated_
- configurations: 2012.1.01029.S: extended and compact configuration  
  > "contains both an extended and compact configuration and is thus particularly sensitive to low-brightness extended emission." (Observations and data reduction); "Each configuration of the 2012.1.01029.S data was mapped and self-calibrated separately." (Observations and data reduction)
- baselines: _not stated_
- angular resolution: Band 6: 0.23 × 0.16 arcsec²; best Band 7: 0.17 × 0.15 arcsec²; SC: 0.28 × 0.25 arcsec²  
  > "the synthesised beam measured $0.23 \times 0.16$ arcsec$^2$ (FWHM)" (Observations and data reduction); "The synthesised beam was somewhat smaller than that of the band-6 map, $0.17 \times 0.15$ arcsec$^2$ at PA = $66^{\circ}$." (Observations and data reduction); "The synthesised beam of the band-7 pure-continuum map was competitive with the other maps, $0.28 \times 0.25$ arcsec$^2$, PA = $104^{\circ}$" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: Continuum rms: 21 μJy beam−1 at 251.0 GHz; 27 at 303.9 GHz; 48 at 356.4 GHz; 60 at 345.0 GHz  
  > "The r.m.s. noise level was $\sigma = 21\,\mu$Jy beam$^{-1}$" (Observations and data reduction); "our map has a significantly higher dynamic range and a sensitivity of $\sigma = 27\,\mu$Jy beam$^{-1}$." (Observations and data reduction); "| 2012.1.00175.S | H$_2$O | 356.4 | 48 | $232 \times 167$ |
| 2012.1.01029.S | SC | 345.0 | 60 | $282 \times 246$ |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH+ not stated (not stated)
- Line: OH+ not stated (not stated)
- Line: H2O not stated (not stated)
- Other facility **Submillimeter Array (SMA)**: Published 345-GHz image for comparison with ALMA  
  > "which shows the SMA image[^3] of (cite: swinbank10) alongside our deep ALMA band-6 continuum image." (Results); "using the eight-element Submillimeter Array (SMA) in its most extended (VEX) configuration" (Introduction)
- Other facility **Green Bank Telescope**: Published CO J=1–0 redshift  
  > "This was determined by (cite: swinbank10) via detection of CO $J=1$–0 using the Green Bank Telescope" (Introduction)
- External data: SMA continuum image and previously identified clump positions  
  > "which shows the SMA image[^3] of (cite: swinbank10) alongside our deep ALMA band-6 continuum image." (Results); "Spatially resolved analysis performed at the positions of the clumps identified by (cite: swinbank10), which we have shown here to be spurious" (Results) [from (cite: swinbank10)]
- External data: Parametric mass model of the MACS J2135−01 cluster core  
  > "We have produced an updated version of the parametric mass model of the MACS J2135$-$01 cluster core described in (cite: swinbank10) using lenstool[^4] (cite: jullokneib09)." (Lens modeling) [from (cite: swinbank10)]
- External data: Blind redshift z=2.3 from CO J=1–0  
  > "it was the first SMG sufficiently bright to allow a blind redshift to be obtained, $z=2.3$." (Introduction); "This was determined by (cite: swinbank10) via detection of CO $J=1$–0 using the Green Bank Telescope" (Introduction) [from (cite: swinbank10)]
- External data: Cosmic Eyelash SED peaking at λobs ≈ 350 μm with flux density ≈ 500 mJy  
  > "With its spectral energy distribution (SED) peaking at $\lambda_{\rm obs} \approx 350\,\mu$m at a flux density, $\approx 500$ mJy (cite: ivison10fts)" (Introduction) [from (cite: ivison10fts)]
- External data: Published simulations showing spurious clumps in high-resolution low-SNR interferometric observations  
  > "the simulations of (cite: hodge16), which showed that high-resolution low-SNR interferometric observations yield a clumpy distribution when there are no clumps." (Results) [from (cite: hodge16)]
- Simulation/model as data: Earlier parametric cluster mass model, updated for the ALMA constraints  
  > "We have produced an updated version of the parametric mass model of the MACS J2135$-$01 cluster core described in (cite: swinbank10) using lenstool[^4] (cite: jullokneib09)." (Lens modeling)
- Simulation/model as data: Published low-SNR simulations used to interpret the earlier apparent clumps  
  > "the simulations of (cite: hodge16), which showed that high-resolution low-SNR interferometric observations yield a clumpy distribution when there are no clumps." (Results)
- Simulation/model as data: Arp 220 extreme starburst SED as an alternative for the clump limit  
  > "Adopting the extreme starburst SED of Arp 220, our limit moves $1.6\times$ higher." (Lens modeling)

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline calibration; Common Astronomy Software Application data reduction  
  > "Data reduction was carried out using the Common Astronomy Software Application package, with calibration performed using the ALMA Science Pipeline." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase, then amplitude and phase; 2012.1.01029.S configurations separately; additional combined-dataset self-calibration for relative astrometry and flux-density scales  
  > "Self-calibration was used (first in phase, then in amplitude and phase) to produce the final continuum maps." (Observations and data reduction); "Each configuration of the 2012.1.01029.S data was mapped and self-calibrated separately." (Observations and data reduction); "Additional self-calibration of the combined datasets was necessary to correct for small errors in the relative astrometry and flux-density scales." (Observations and data reduction)

### Imaging

- task: TCLEAN  
  > "Imaging was performed subsequently, using TCLEAN with a Briggs weighting scheme (robust $=-0.5$)." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs; robust = −0.5  
  > "Imaging was performed subsequently, using TCLEAN with a Briggs weighting scheme (robust $=-0.5$)." (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Combine all baselines into a spectrum; identify and flag line-contaminated channel ranges  
  > "Contamination from molecular lines was identified by combining all baselines to produce a spectrum, with affected channel ranges then flagged." (Observations and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Band 6: 0.23 × 0.16 arcsec², PA 93°; 303.9 GHz: 0.17 × 0.15 arcsec², PA 66°; SC: 0.28 × 0.25 arcsec², PA 104°  
  > "the synthesised beam measured $0.23 \times 0.16$ arcsec$^2$ (FWHM), with the major axis at a position angle (PA, measured East of North) of $93^{\circ}$." (Observations and data reduction); "The synthesised beam was somewhat smaller than that of the band-6 map, $0.17 \times 0.15$ arcsec$^2$ at PA = $66^{\circ}$." (Observations and data reduction); "The synthesised beam of the band-7 pure-continuum map was competitive with the other maps, $0.28 \times 0.25$ arcsec$^2$, PA = $104^{\circ}$" (Observations and data reduction)
- final rms: 251.0 GHz: 21; 303.9 GHz: 27; 356.4 GHz: 48; 345.0 GHz: 60 μJy beam−1  
  > "The r.m.s. noise level was $\sigma = 21\,\mu$Jy beam$^{-1}$" (Observations and data reduction); "our map has a significantly higher dynamic range and a sensitivity of $\sigma = 27\,\mu$Jy beam$^{-1}$." (Observations and data reduction); "| 2012.1.00175.S | H$_2$O | 356.4 | 48 | $232 \times 167$ |
| 2012.1.01029.S | SC | 345.0 | 60 | $282 \times 246$ |" (Table 1)

### Inherited from earlier work

- Band-6 dataset previously published in a CH+ survey  
  > "The most sensitive map was obtained from the band-6 data (rest-frame 360 $\mu$m, where we probe emission from cold dust), published previously as part of a survey of luminous, dusty galaxies in the CH$^+$ line (cite: falgarone17)." (Observations and data reduction) [from (cite: falgarone17)]
- Starting parametric mass model of the cluster core  
  > "We have produced an updated version of the parametric mass model of the MACS J2135$-$01 cluster core described in (cite: swinbank10) using lenstool[^4] (cite: jullokneib09)." (Lens modeling) [from (cite: swinbank10)]
- Residual-peak fidelity assessment using positive and negative peaks  
  > "We followed the approach of (cite: walter16) to assess the fidelity of the residual peaks as a function of SNR, albeit needing to adopt large SNR bins, searching for both positive and negative peaks." (Lens modeling) [from (cite: walter16)]
- Traditional LIR-to-SFR conversion  
  > "Adopting the traditional conversion from $L_{\rm IR}$ to SFR (cite: ke12)" (Lens modeling) [from (cite: ke12)]
- Initial mass function  
  > "Throughout, we adopt the (cite: chabrier03) initial mass function" (Introduction) [from (cite: chabrier03)]

### Not stated but needed to reproduce (our reading)

- Exact execution blocks and the role of acknowledged project 2013.1.00164.S, which is absent from Table 1.
- CASA and ALMA Science Pipeline versions and calibration scripts.
- Exact flagged channel ranges and final usable continuum bandwidth for each dataset.
- Self-calibration solution intervals, reference antennas, solution thresholds and applied relative astrometric or flux-scale corrections.
- TCLEAN cell size, image size, deconvolver, masks, stopping threshold and primary-beam treatment.
- Exact dataset/configuration combination and weighting procedure.
- Updated lens-model parameters, constraint coordinates and parameter uncertainties.
- Source-fit optimizer, objective or likelihood, bounds or priors, noise treatment and uncertainty calculation.
- Residual peak-finding settings, SNR-bin edges and fidelity implementation.
- Numerical SED template, normalization procedure and adopted LIR-to-SFR coefficient.

## Analysis recipe

1. **Construct continuum maps**: Identify line contamination in an all-baseline spectrum, flag affected channels, image with TCLEAN and self-calibrate  
  > "Contamination from molecular lines was identified by combining all baselines to produce a spectrum, with affected channel ranges then flagged." (Observations and data reduction); "Imaging was performed subsequently, using TCLEAN with a Briggs weighting scheme (robust $=-0.5$)." (Observations and data reduction); "Self-calibration was used (first in phase, then in amplitude and phase) to produce the final continuum maps." (Observations and data reduction)
   - software: Common Astronomy Software Application, TCLEAN
   - parameter: Briggs robust = −0.5  
  > "Imaging was performed subsequently, using TCLEAN with a Briggs weighting scheme (robust $=-0.5$)." (Observations and data reduction)
   - parameter: Self-calibrate 2012.1.01029.S configurations separately, then combined datasets  
  > "Each configuration of the 2012.1.01029.S data was mapped and self-calibrated separately." (Observations and data reduction); "Additional self-calibration of the combined datasets was necessary to correct for small errors in the relative astrometry and flux-density scales." (Observations and data reduction)
   - fitting: _not stated_
   - validation: Band-6 and band-7 images have the same morphological characteristics  
  > "In all important respects the ALMA band-6 image has the same morphological characteristics as our band-7 imaging" (Results)
2. **Reassess the apparent clumps**: Compare deep ALMA continuum images with the published SMA image  
  > "which shows the SMA image[^3] of (cite: swinbank10) alongside our deep ALMA band-6 continuum image." (Results)
   - parameter: Band-6 image ≈ 40× deeper after accounting for the 2.6× dust-emission drop between 345 and 251 GHz  
  > "The ALMA image is $\approx 40\times$ deeper than the SMA image, even after accounting for the $2.6\times$ drop in observed dust emission between 345 and 251 GHz." (Results)
   - fitting: _not stated_
   - validation: Consistent smooth morphology in bands 6 and 7  
  > "In all important respects the ALMA band-6 image has the same morphological characteristics as our band-7 imaging" (Results); "On the scales probed here, roughly 200 mas in the image plane, the dust continuum emission from the Cosmic Eyelash is remarkably smooth, not clumpy." (Results)
3. **Update the gravitational lens model**: Update the earlier parametric cluster-core mass model using ALMA image-pair centroids as constraints  
  > "We have produced an updated version of the parametric mass model of the MACS J2135$-$01 cluster core described in (cite: swinbank10) using lenstool[^4] (cite: jullokneib09)." (Lens modeling); "We take the centroids of the ALMA image pair in Figs [1](#fig:sma_alma)–[2](#fig:eyelashcont) as constraints." (Lens modeling)
   - software: lenstool
   - assumption: Λ-CDM: Ωm = 0.3, ΩΛ = 0.7, H0 = 70 km s−1 Mpc−1; 1 arcsec = 8.2 kpc at z=2.3  
  > "a standard $\Lambda$-CDM cosmology with $\Omega_{\rm m} = 0.3$, $\Omega_\Lambda = 0.7$ and $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$, where 1 arcsec at $z=2.3$ corresponds to 8.2 kpc." (Introduction)
   - fitting: _not stated_
   - validation: Small lens-model mismatch motivates independent fits to the two images  
  > "Because of a small mis-match in the lens model,[^5] to reproduce both images simultaneously we performed the fit on each image independently" (Lens modeling)
4. **Fit the intrinsic continuum morphology**: Forward-model Sérsic sources through the fixed lens model, convolve with the ALMA beam, and re-grid to the image-plane pixel grid; compare one and two components  
  > "We took a forward-model approach, assuming a Sérsic profile for the source, convolving by the ALMA beam and re-gridding to the same pixel grid in the image plane." (Lens modeling); "this time comprising two independent Sérsic profiles" (Lens modeling)
   - parameter: Band 7, 303.9 GHz  
  > "our best ALMA continuum image of the Cosmic Eyelash (Band 7, 303.9 GHz)" (Lens modeling)
   - parameter: Optimise centroid, PA, axis ratio and FWHM; keep mass model fixed  
  > "The source parameters (centroid, PA, axis ratio and FWHM) were optimised while keeping the mass model fixed." (Lens modeling)
   - assumption: Parametric Sérsic source morphology  
  > "We took a forward-model approach, assuming a Sérsic profile for the source" (Lens modeling)
   - fitting: Fit each lensed image independently; use recovered-parameter variations to estimate lens-model systematic errors  
  > "we performed the fit on each image independently, using the variations in the recovered parameters as an estimate of systematic errors due to the lens model." (Lens modeling)
   - validation: Single-component fit leaves >50σ core residuals; assess two-component residuals for mirrored substructure  
  > "The best source parameters with a single Sérsic profile reproduced the observed configurations well, with significant ($>50\sigma$) residuals near the core of each image, symmetrical about the critical line." (Lens modeling); "We found no mirrored sub-structure in the residual map" (Lens modeling)
5. **Test residual peaks for real clumps**: Assess residual-peak fidelity versus SNR using positive and negative peaks, following (cite: walter16)  
  > "We followed the approach of (cite: walter16) to assess the fidelity of the residual peaks as a function of SNR, albeit needing to adopt large SNR bins, searching for both positive and negative peaks." (Lens modeling)
   - parameter: Large SNR bins  
  > "albeit needing to adopt large SNR bins, searching for both positive and negative peaks." (Lens modeling)
   - fitting: _not stated_
   - validation: No mirroring, deeper negative peaks, and fidelity never better than 50 per cent even at 10σ  
  > "the deepest negative peaks reach 360 $\mu$Jy which suggests — along with the lack of mirroring — that the sub-structure we see is not real." (Lens modeling); "We found no reliable candidates, even at $10\sigma$: the fidelity of the brightest peaks was never better than 50 per cent." (Lens modeling)
6. **Derive clump luminosity and SFR limits**: Scale the maximum positive residual to the Cosmic Eyelash SED, account for lens magnification, and convert LIR to SFR  
  > "If we scale the maximum positive residual, which is magnified by roughly $8\times$ and $1.6\times$ along the major and minor axes, to the well-sampled SED of the Cosmic Eyelash" (Lens modeling); "Adopting the traditional conversion from $L_{\rm IR}$ to SFR (cite: ke12)" (Lens modeling)
   - parameter: Maximum positive residual: 260 μJy  
  > "a brightest peak of 260 $\mu$Jy, roughly $10\sigma$ above the noise" (Lens modeling)
   - parameter: Residual magnification: roughly 8× along major axis and 1.6× along minor axis  
  > "which is magnified by roughly $8\times$ and $1.6\times$ along the major and minor axes" (Lens modeling)
   - parameter: Rest-frame 8–1000 μm luminosity  
  > "we find that its rest-frame 8–1000-$\mu$m luminosity cannot exceed $24\times 10^9$ L$_\odot$." (Lens modeling)
   - assumption: Clump SED scaled from the well-sampled Cosmic Eyelash SED  
  > "to the well-sampled SED of the Cosmic Eyelash" (Lens modeling)
   - assumption: (cite: chabrier03) initial mass function  
  > "Throughout, we adopt the (cite: chabrier03) initial mass function" (Introduction)
   - assumption: (cite: ke12) LIR-to-SFR conversion  
  > "Adopting the traditional conversion from $L_{\rm IR}$ to SFR (cite: ke12)" (Lens modeling)
   - fitting: _not stated_
   - validation: Alternative Arp 220 SED raises the limit by 1.6×  
  > "Adopting the extreme starburst SED of Arp 220, our limit moves $1.6\times$ higher." (Lens modeling)

## Software

- **Common Astronomy Software Application** : Data reduction  
  > "Data reduction was carried out using the Common Astronomy Software Application package" (Observations and data reduction)
- **ALMA Science Pipeline** : Calibration  
  > "with calibration performed using the ALMA Science Pipeline." (Observations and data reduction)
- **TCLEAN** : Continuum imaging with Briggs weighting  
  > "Imaging was performed subsequently, using TCLEAN with a Briggs weighting scheme (robust $=-0.5$)." (Observations and data reduction)
- **lenstool** : Update the parametric cluster-core mass model  
  > "We have produced an updated version of the parametric mass model of the MACS J2135$-$01 cluster core described in (cite: swinbank10) using lenstool[^4] (cite: jullokneib09)." (Lens modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Extended component effective radius | 4.42 | ± 1.21 | kpc | 4 | / $4.42\pm 1.21$ / 0.46  / $134\pm4$ / $6.2\pm0.9$ /  $0.45\pm0.22$   / |
| Extended component axis ratio | 0.46 | not stated | dimensionless | 4 | / $4.42\pm 1.21$ / 0.46  / $134\pm4$ / $6.2\pm0.9$ /  $0.45\pm0.22$   / |
| Extended component PA | 134 | ±4 | deg | 4 | / $4.42\pm 1.21$ / 0.46  / $134\pm4$ / $6.2\pm0.9$ /  $0.45\pm0.22$   / |
| Extended component total flux | 6.2 | ±0.9 | mJy | 4 | / $4.42\pm 1.21$ / 0.46  / $134\pm4$ / $6.2\pm0.9$ /  $0.45\pm0.22$   / |
| Extended component Sérsic index | 0.45 | ±0.22 | dimensionless | 4 | / $4.42\pm 1.21$ / 0.46  / $134\pm4$ / $6.2\pm0.9$ /  $0.45\pm0.22$   / |
| Compact component effective radius | 1.23 | ± 0.02 | kpc | 4 | / $1.23\pm 0.02$ / 0.44  / $155\pm6$ / $8.3\pm1.3$ /  $0.51\pm0.06$   / |
| Compact component axis ratio | 0.44 | not stated | dimensionless | 4 | / $1.23\pm 0.02$ / 0.44  / $155\pm6$ / $8.3\pm1.3$ /  $0.51\pm0.06$   / |
| Compact component PA | 155 | ±6 | deg | 4 | / $1.23\pm 0.02$ / 0.44  / $155\pm6$ / $8.3\pm1.3$ /  $0.51\pm0.06$   / |
| Compact component total flux | 8.3 | ±1.3 | mJy | 4 | / $1.23\pm 0.02$ / 0.44  / $155\pm6$ / $8.3\pm1.3$ /  $0.51\pm0.06$   / |
| Compact component Sérsic index | 0.51 | ±0.06 | dimensionless | 4 | / $1.23\pm 0.02$ / 0.44  / $155\pm6$ / $8.3\pm1.3$ /  $0.51\pm0.06$   / |
| Source-plane separation of component central positions | within 0.01 | not stated | arcsec | 4 | two components lying very close in central position (within 0.01 arcsec or $\approx 80$ pc in the source plane) |
| Brightest positive residual peak | 260 | not stated | μJy | 5 | a brightest peak of 260 $\mu$Jy, roughly $10\sigma$ above the noise |
| Depth of deepest negative residual peaks | 360 | not stated | μJy | 5 | the deepest negative peaks reach 360 $\mu$Jy |
| Brightest residual-peak fidelity | never better than 50 | not stated | per cent | 5 | We found no reliable candidates, even at $10\sigma$: the fidelity of the brightest peaks was never better than 50 per cent. |
| Source-plane major-axis scale probed by unresolved residuals | ≈ 80 | not stated | pc | 5 | they are unresolved down to $\approx 80$ pc in the source plane[^6] along the major axis. |
| Clump rest-frame 8–1000-μm luminosity limit | <24 × 10^9 | not stated | L⊙ | 6 | with rest-frame 8–1000-$\mu$m luminosities below $24\times 10^9$ L$_\odot$ |
| Individual clump SFR limit | <2.6 | not stated | M⊙ yr−1 | 6 | individual SFRs no higher than 1 per cent of the total, so $<2.6$ M$_\odot$ yr$^{-1}$. |
| Individual clump fraction of total SFR | no higher than 1 | not stated | per cent | 6 | individual SFRs no higher than 1 per cent of the total |
| Increase in clump limit using Arp 220 SED | 1.6 | not stated | dimensionless | 6 | Adopting the extreme starburst SED of Arp 220, our limit moves $1.6\times$ higher. |

## Qualitative findings

- The dust continuum is smooth on the probed scales  
  > "On the scales probed here, roughly 200 mas in the image plane, the dust continuum emission from the Cosmic Eyelash is remarkably smooth, not clumpy." (Results)
- The earlier SMA continuum clumps are spurious  
  > "the remarkable symmetry of the resulting structure about the likely caustic lent credibility to a clumpy morphology that we show here to be spurious." (Results)
- Two nearly coincident Sérsic components reproduce the continuum morphology  
  > "can be reproduced using two coincident Sérsic profiles with effective radii, 1.2 and 4.4 kpc" (Summary)
- No reliable residual clump candidates  
  > "We found no reliable candidates, even at $10\sigma$: the fidelity of the brightest peaks was never better than 50 per cent." (Lens modeling)

## Claim tuples

- H: The Cosmic Eyelash contains pronounced dusty star-forming clumps on approximately 100-pc scales. | E: Compare deeper ALMA continuum maps with the earlier SMA morphology and test lens-model residual peaks. | R: Smooth continuum; no reliable residual candidates even at 10σ. | F: The previously reported continuum clumps are spurious on the scales probed. | **refuted**
- H: A smooth parametric source can reproduce the observed continuum. | E: Forward-model one and two Sérsic profiles through a fixed lens model. | R: One component leaves >50σ core residuals; two coincident components have effective radii 1.2 and 4.4 kpc. | F: Two smooth Sérsic components reproduce the continuum without significant star-forming clumps. | **supported**
- H: Any unresolved residual clump could contribute substantial ongoing star formation. | E: Scale the maximum positive residual using lens magnification and the Cosmic Eyelash SED, then convert infrared luminosity to SFR. | R: Individual clump SFRs <2.6 M⊙ yr−1 and no higher than 1 per cent of the total. | F: Significant individual star-forming clumps are excluded at the quoted spatial scale under the adopted SED and conversion. | **refuted**

## Reasoning

- Why this data: Select sensitive, high-resolution observations with line-free channels; include compact and extended configurations for low-brightness extended emission  
  > "From these, we have selected a subset with good sensitivity ($\le 50\,\mu$Jy beam$^{-1}$) and angular resolution ($\Delta \theta \le 0.3$ arcsec)." (Observations and data reduction); "these data contain a significant fraction of line-free channels that allow sensitive continuum maps to be made." (Observations and data reduction); "contains both an extended and compact configuration and is thus particularly sensitive to low-brightness extended emission." (Observations and data reduction)
- Why this method: Fit two smooth components because one leaves significant symmetric core residuals; fit each image independently to assess lens-model systematics  
  > "The best source parameters with a single Sérsic profile reproduced the observed configurations well, with significant ($>50\sigma$) residuals near the core of each image, symmetrical about the critical line." (Lens modeling); "we performed the fit on each image independently, using the variations in the recovered parameters as an estimate of systematic errors due to the lens model." (Lens modeling)
- Alternative: Single Sérsic source: significant >50σ core residuals  
  > "The best source parameters with a single Sérsic profile reproduced the observed configurations well, with significant ($>50\sigma$) residuals near the core of each image, symmetrical about the critical line." (Lens modeling)
- Alternative: Two-component morphology could represent a merger-induced dusty starburst or a star-forming disk with a central starburst  
  > "two independent Sérsic profiles, as might be expected for a merger-induced dusty starburst (cite: engel10) or for a star-forming disk with a central starburst" (Lens modeling)
- Alternative: Arp 220 SED raises the clump limit by 1.6×  
  > "Adopting the extreme starburst SED of Arp 220, our limit moves $1.6\times$ higher." (Lens modeling)
- Alternative: A top-heavy stellar initial mass function would reduce the SFR limits  
  > "recent evidence for a top-heavy stellar initial mass function in starbursts (cite: zhang18; schneider18; motte18) would reduce these SFR limits significantly" (Lens modeling)
- How they decided it was enough: Residuals lack mirroring and have no reliable positive-peak candidates; brightest-peak fidelity never exceeds 50 per cent  
  > "We found no mirrored sub-structure in the residual map" (Lens modeling); "We found no reliable candidates, even at $10\sigma$: the fidelity of the brightest peaks was never better than 50 per cent." (Lens modeling)
- Limitation (authors): Small lens-model mismatch prevents a simultaneous fit to both images  
  > "Because of a small mis-match in the lens model,[^5] to reproduce both images simultaneously we performed the fit on each image independently" (Lens modeling)
- Limitation (authors): Fidelity assessment requires large SNR bins  
  > "albeit needing to adopt large SNR bins, searching for both positive and negative peaks." (Lens modeling)
- Limitation (authors): Approximately 80-pc source-plane resolution applies along the major axis  
  > "they are unresolved down to $\approx 80$ pc in the source plane[^6] along the major axis." (Lens modeling)
- Limitation (authors): SFR limit depends on the adopted SED and stellar initial mass function  
  > "Adopting the extreme starburst SED of Arp 220, our limit moves $1.6\times$ higher." (Lens modeling); "recent evidence for a top-heavy stellar initial mass function in starbursts (cite: zhang18; schneider18; motte18) would reduce these SFR limits significantly" (Lens modeling)
- Caveat (inferred, ours): The approximately 80-pc limit is directional; it should not be treated as isotropic source-plane resolution.
- Caveat (inferred, ours): Residual fidelity is not an injection-and-recovery completeness measurement for clumps of different sizes and locations.
- Caveat (inferred, ours): Independent image fits sample some lens-model systematics but do not establish full mass-model uncertainty propagation.
- Caveat (inferred, ours): The luminosity and SFR limits assume a clump SED and conversion that may differ from the global galaxy values.
- Caveat (inferred, ours): The stated sensitivity selection is ≤50 μJy beam−1, while the included single-continuum dataset has 60 μJy beam−1.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Execution-block inventory and explanation of project 2013.1.00164.S.
- Missing: Reduction scripts, software versions, channel flags and complete imaging/self-calibration settings.
- Missing: Updated lens-model files and image-centroid constraints.
- Missing: Source-fitting code, objective function, parameter bounds and uncertainty methodology.
- Missing: Peak-finding and fidelity settings.
- Missing: SED data/template and exact infrared-luminosity-to-SFR conversion.
- Data volume (inferred): Not estimable from the supplied text: execution counts, observing durations and visibility volumes are absent.
- Score (inferred): 5/5, 5/10: project identifiers, weighting, map quality, analysis sequence and numeric fit results are supplied, but calibration details, fitting implementation and updated lens-model files are missing.
- Rediscovery candidate: no, Main results are numeric, but public availability is not stated and the reduction and lens/source-fitting recipe is incomplete.

## Links

- Method: (cite: jullokneib09) (lenstool reference for the parametric lens model.)
- Method: (cite: swinbank10) (Starting cluster mass model and earlier SMA clump interpretation.)
- Method: (cite: walter16) (Residual-peak fidelity method using positive and negative peaks.)
- Method: (cite: ke12) (Infrared-luminosity-to-SFR conversion.)
- Method: (cite: chabrier03) (Adopted initial mass function.)
- Method: (cite: hodge16) (Published low-SNR simulations informing the interpretation of apparent clumps.)
- Companion: (cite: falgarone17) (Previously published the band-6 data as part of a CH+ survey.)
- Companion: (cite: indriolo18) (Previously published a continuum map from the 303.9-GHz dataset.)
- Companion: (cite: swinbank10) (Earlier Cosmic Eyelash discovery, SMA continuum clumps, redshift and cluster lens model.)
- Related: Survey of luminous, dusty galaxies in the CH+ line (cite: falgarone17)

## Checks

```json
{
 "quotes": 148,
 "quotes_ok": 148,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00164.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 109,
  "stated": 77,
  "rate": 0.706
 },
 "evidence_ok": true
}
```
