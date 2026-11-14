# Maser emission from the CO envelope of the asymptotic giant branch star W Hydrae

`2021A&A...654A..18V` | Astronomy and Astrophysics 2021 | first author: Vlemmings, W. H. T. | arXiv: 2109.05048 | DOI: 10.1051/0004-6361/202141656

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Is there CO maser emission in the J=3-2 line around the AGB star W Hya, where does it come from, and what pumps it  
  > "While radiative transfer models have shown that molecular levels of CO can become mildly inverted, causing maser emission, CO maser emission has yet to be confirmed observationally." (abstract); "Here we present the first unambiguous detection of CO maser emission, in the $J=3-2$ transition, around the oxygen-rich AGB star W Hya." (Introduction)
- Target **W Hya**: coordinates _not stated_; z/distance approximately 100 pc  
  > "W Hya is a semi-regular variable star located at $\approx 100$ pc from the Sun (cite: Vlemmings03; vanLeeuwen2007)" (Introduction); distance from (cite: Vlemmings03; vanLeeuwen2007)  
  > "W Hya is a semi-regular variable star located at $\approx 100$ pc from the Sun (cite: Vlemmings03; vanLeeuwen2007)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01446.S, 2016.A.00029.S, 2016.2.00025.S, 2017.1.00824.S
- bands: ALMA band 7  
  > "The first epoch of observations of W Hya in ALMA band 7, which included the CO $J=3-2$ transition at $345.796$ GHz" (2 Observations and data reduction)
- frequencies and spectral setup: spectral line mode; spw containing CO J=3-2 (345.796 GHz) with native resolution 0.98 MHz (~0.9 km/s) in both epochs  
  > "All observations were taken in spectral line mode, and the spectral window (spw) that contained the CO $J=3-2$ transition provided a native spectral resolution of 0.98 MHz ($\sim0.9$ km s$^{-1}$) for both epochs." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: long baseline observations (specific configurations not given)  
  > "Using ALMA long baseline observations, we have confirmed that mild maser inversion occurs in the CSE of the AGB star W Hya." (Conclusions)
- baselines: _not stated_
- angular resolution: 31x21 mas (-63 deg from north) and 29x21 mas (-68 deg) for the two epochs  
  > "The resulting beam sizes were $31\times21$ mas ($-63^\circ$ from north) and $29\times21$ mas ($-68^\circ$)." (2 Observations and data reduction)
- max recoverable scale: approximately 0.6 arcsec  
  > "The maximum recoverable scale is approximately $0.6\ensuremath{''}$." (2 Observations and data reduction)
- sensitivity: rms ~3.5 mJy/beam near the CO line in both epochs  
  > "the rms noise near the CO line was $\sim3.5$ mJy beam$^{-1}$ for both epochs due to the different weighting adopted." (2 Observations and data reduction)
- time on source: ~2.1 hr (epoch 1, three executions); ~35 min (epoch 2)  
  > "were taken as part of ALMA project 2015.1.01446.S (PI: Takigawa) in three executions between 30 Nov and 5 Dec 2015 for a total on-source time of $\sim2.1$ hr" (2 Observations and data reduction); "The second epoch was observed as part of project 2016.A.00029.S (PI: Vlemmings) on 25 Nov 2017 with an on-source observing time of $\sim35$ min." (2 Observations and data reduction)
- observing dates: 30 Nov to 5 Dec 2015 (epoch 1); 25 Nov 2017 (epoch 2)  
  > "The second epoch was observed as part of project 2016.A.00029.S (PI: Vlemmings) on 25 Nov 2017 with an on-source observing time of $\sim35$ min." (2 Observations and data reduction)
- pi or archival as stated: 2015.1.01446.S PI Takigawa; 2016.A.00029.S PI Vlemmings; data previously presented in Vlemmings17 and Vlemmings19  
  > "The observations of W Hya presented in this paper were previously presented in (cite: Vlemmings17) and (cite: Vlemmings19)." (2 Observations and data reduction)
- Line: CO J=3-2 (345.796 GHz)
- Other facility **ACA**: recent ACA observations of CO (4.5x3.6 arcsec beam) used to compare with the model  
  > "We include a comparison of the model with recent ACA observations" (4.3.1 Continuum pumping)
- Other facility **ALMA CO J=2-1 observations of R Dor**: high angular resolution CO J=2-1 spectrum of R Dor used for comparison (no maser, narrow absorption seen)  
  > "we do see this effect in high angular resolution observations of the CO $J=2-1$ emission around the nearby AGB star R Dor" (4.3.1 Continuum pumping)
- External data: CO envelope model parameters of the baseline model (Table 1) and distance adopted from the model  
  > "taken from (cite: Khouri14); we do not adjust the distance and adopt the value used in the model." (4.3.1 Continuum pumping) [from (cite: Khouri14)]
- External data: CO transition frequencies, energy levels, Einstein coefficients and collisional rate coefficients  
  > "The transition frequencies, energy levels, and Einstein coefficients were taken from the CDMS and JPL databases (cite: Muller01; Picket98) and the collisional rate coefficients come from (cite: Yang10)." (4.3.1 Continuum pumping) [from (cite: Muller01; Picket98; Yang10)]
- External data: Observed 4.6 micron infrared spectrum used to constrain pump radiation (85% transmission of the stellar black body)  
  > "Based on observations around 4.6 $\mu$m (cite: Justtanont14) we include an overall decrease in the stellar radiation field around this wavelength, adopting a transmission of 85% of the stellar black body." (4.3.2 Line overlap) [from (cite: Justtanont14)]
- Simulation/model as data: One-dimensional Monte Carlo radiative transfer models of CO (J=0-81, v=0,1) for a single aperture towards the star, compared with the maser spectrum  
  > "we perform one-dimensional radiative transfer models using the Monte Carlo radiative transfer code" (4.3.1 Continuum pumping); "We include the CO rotational levels $J=0$ to $J=81$ and the vibrational levels $v=0$ and $v=1$." (4.3.1 Continuum pumping)

## Processing

### Calibration

- pipeline or manual: manual calibration scripts provided by the observatory  
  > "The initial calibration (of the bandpass, amplitude, absolute flux-density scale, and phase) was done using the Common Astronomy Software Applications (CASA) package (cite: McMullin07), using the manual calibration scripts provided by the observatory." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: two rounds of phase self-calibration on the stellar continuum; continuum S/N improved by a factor of three  
  > "After the initial calibration we performed two rounds of phase self-calibration on the strong stellar continuum." (2 Observations and data reduction); "The self-calibration improved the continuum signal-to-noise ratio (S/N) by a factor of three." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting, robust = -1.0 (epoch 1) and 0.5 (epoch 2)  
  > "Imaging of the CO lines was done using Briggs weighting with a robust parameter of $-1.0$ and $0.5,$ respectively for the two epochs, in order to achieve a similar angular resolution." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: single-day spectra convolved to a common beam  
  > "taken towards the peak identified in the combined epoch 1 image and convolved to a common beam size" (3 Results)
- final beam: 31x21 mas (-63 deg) and 29x21 mas (-68 deg); common beam 30x21 mas used for the single-day comparison  
  > "The resulting beam sizes were $31\times21$ mas ($-63^\circ$ from north) and $29\times21$ mas ($-68^\circ$)." (2 Observations and data reduction); "If the maser emission is more compact than the common beam of $30\times21$ mas" (3 Results)
- final rms: ~3.5 mJy/beam near the CO line, both epochs  
  > "the rms noise near the CO line was $\sim3.5$ mJy beam$^{-1}$ for both epochs due to the different weighting adopted." (2 Observations and data reduction)

### Inherited from earlier work

- Observation set-up details including flux and gain calibrators  
  > "Further observation details, including the flux and gain calibrators used, are given in (cite: Vlemmings17) and (cite: Vlemmings19)." (2 Observations and data reduction) [from (cite: Vlemmings17) and (cite: Vlemmings19)]
- Data themselves previously published in earlier papers  
  > "The observations of W Hya presented in this paper were previously presented in (cite: Vlemmings17) and (cite: Vlemmings19)." (2 Observations and data reduction) [from (cite: Vlemmings17) and (cite: Vlemmings19)]
- Method of artificially scaling the 4.6 micron radiation field by a factor M for wavelengths below 5 micron  
  > "we artificially adjust the strength of the 4.6 $\mu$m radiation field, following the same method as in (cite: Morris80)" (4.3.1 Continuum pumping) [from (cite: Morris80)]
- Line overlap pumping implemented in simplified form  
  > "as well as a simplified implementation of the line overlap pumping described in (cite: Piehler91)." (Introduction) [from (cite: Piehler91)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method used to image the CO line
- Self-calibration solution intervals, reference antenna and which spw/channels were used for self-calibration
- Cell size, image size, deconvolver, masking and clean threshold
- Flux calibrator and flux scale uncertainty (deferred to Vlemmings17/Vlemmings19)
- Exact method to measure peak brightness temperature (Rayleigh-Jeans or full Planck) and the aperture used for the single-beam spectra
- How the 2016.2.00025.S and 2017.1.00824.S projects (acknowledged) were used, if at all
- Details of the ACA data used for comparison (project, reduction)
- The mcp model grid, the exact atmospheric absorption profile and the IR line-by-line radiation field scaling used for line overlap models
- Coordinates and stellar velocity of W Hya

## Analysis recipe

1. **calibrate and self-calibrate the ALMA band 7 data**: manual calibration scripts from the observatory, then two rounds of phase self-calibration on the stellar continuum  
  > "using the manual calibration scripts provided by the observatory." (2 Observations and data reduction); "After the initial calibration we performed two rounds of phase self-calibration on the strong stellar continuum." (2 Observations and data reduction)
   - software: CASA
   - parameter: continuum S/N improved by a factor of three  
  > "The self-calibration improved the continuum signal-to-noise ratio (S/N) by a factor of three." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **image the CO J=3-2 line at matched resolution in both epochs**: Briggs weighting with robust -1.0 (epoch 1) and 0.5 (epoch 2) to obtain similar angular resolution  
  > "Imaging of the CO lines was done using Briggs weighting with a robust parameter of $-1.0$ and $0.5,$ respectively for the two epochs, in order to achieve a similar angular resolution." (2 Observations and data reduction)
   - software: CASA
   - parameter: beams 31x21 mas and 29x21 mas; rms ~3.5 mJy/beam  
  > "The resulting beam sizes were $31\times21$ mas ($-63^\circ$ from north) and $29\times21$ mas ($-68^\circ$)." (2 Observations and data reduction); "the rms noise near the CO line was $\sim3.5$ mJy beam$^{-1}$ for both epochs due to the different weighting adopted." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **measure maser brightness temperature, optical depth, line width, morphology and variability**: subtract the stellar continuum, measure peak Tb in the emission maps, extract single-beam spectra at the peak, and image the three days of epoch 1 separately with a common beam  
  > "After subtracting the $\sim2700$ K stellar continuum, the peak of the emission has a brightness temperature of $T_b\approx1950$ K in the two epochs." (3 Results); "we also individually imaged the three days in epoch 1 (30 Nov, 3 Dec, and 5 Dec)." (3 Results)
   - parameter: stellar continuum brightness temperature ~2700 K subtracted  
  > "After subtracting the $\sim2700$ K stellar continuum" (3 Results)
   - assumption: maser amplifies the underlying stellar continuum, so Tb implies optical depth tau  
  > "As the emission is amplifying the underlying stellar continuum, the brightness temperatures imply a maser optical depth of $\tau\approx-0.55$." (3 Results)
   - assumption: if the emission is compact or made of multiple components, Tb is a lower limit  
  > "if it consists of multiple more compact components, the derived $T_b$ presents a lower limit." (3 Results)
   - fitting: FWHM of the brightest spectral component given (fit method not stated)  
  > "The brightest spectral component has a full width at half maximum (FWHM) of $1.9$ and $2.2$ km s$^{-1}$ in the two epochs, respectively." (3 Results)
   - validation: continuum flux varies by less than 2.5% over the three days, so maser variability is not a flux calibration uncertainty  
  > "the continuum flux varies by less than $2.5\%$ over the three days so the flux variation is not due to an uncertainty in the flux calibration." (3 Results)
4. **compare maser velocity with other masers of W Hya**: compare the CO maser velocity with literature OH and H2O maser peak velocities  
  > "This means that the maser coincides in velocity with the brightest 1665 and 1667 MHz OH maser at $35.6$ km s$^{-1}$" (4.2 Velocity)
   - assumption: a common velocity reflects the largest coherent velocity path length towards the star, giving an amplified stellar image in many maser species  
  > "It is thus more likely that the velocity of the CO maser and the other features corresponds to the largest coherent velocity path length towards the star" (4.2 Velocity)
   - fitting: _not stated_
   - validation: _not stated_
5. **model continuum pumping with 1-D radiative transfer**: one-dimensional Monte Carlo radiative transfer of CO with the baseline envelope model of Khouri14, observed through a single aperture of size 2R* towards the star, with the extended-atmosphere CO absorption profile added on top of the stellar black body; then multiply the radiation field below 5 micron by a factor M  
  > "we model the observations of a single aperture (with a size of $2R_*$) towards the star using the parameters for the CO envelope given in Table" (4.3.1 Continuum pumping); "we multiply the radiation field for all wavelengths $<5~\mu$m by a factor $M$." (4.3.1 Continuum pumping)
   - software: mcp
   - parameter: M~3 gives a maser of sufficient strength; need V0~4.2 km/s, beta~2.5, Vt~1.0 km/s to match maser velocity and width  
  > "we require a larger velocity at the inner envelope ($V_0\approx4.2$ km s$^{-1}$), a slightly steeper acceleration ($\beta\approx 2.5$), and larger turbulent velocity component ($V_t\approx 1.0$ km s$^{-1}$)." (4.3.1 Continuum pumping)
   - assumption: model is one-dimensional so only emission along the line of sight to the star is compared; distance not adjusted from the adopted model value  
  > "Since the model is one-dimensional we only compare the emission along the line of sight to the star." (4.3.1 Continuum pumping)
   - fitting: manual variation of three parameters (V0, beta, Vt) by hand to reproduce the maser; no sampler or likelihood  
  > "Varying these three parameters, we can reproduce the maser as seen in the representative model" (4.3.1 Continuum pumping)
   - validation: model compared with the ACA spectrum; further constraints from lower resolution data not considered while adjusting  
  > "While making these changes, we did not consider further constraints from the lower angular resolution observations." (4.3.1 Continuum pumping)
6. **constrain mass-loss rate range and test dust-shell pumping**: vary the mass-loss rate in the maser model and compare with the lower resolution (ACA) observations; add a dust shell to supply the 4.6 micron excess and check against the observed infrared spectrum  
  > "Specifically for W Hya, most of this range can be ruled out by the lower angular resolution observations, limiting the rate to between $1.5-3.0\times10^{-7}$ M$_\odot$ yr$^{-1}$." (4.3.1 Continuum pumping); "In our models we can reproduce the required continuum excess by including a dust shell with an optical depth at 4.6 $\mu$m of $\sim0.2$" (4.3.1 Continuum pumping)
   - software: mcp
   - fitting: _not stated_
   - validation: dust-shell solution rejected because it conflicts with the observed infrared spectrum  
  > "affecting the spectral energy distribution in a way that is not supported by the observed infrared spectrum (cite: Justtanont14)" (4.3.1 Continuum pumping)
7. **test line-overlap pumping of the v=0-1 4.6 micron lines**: change the relative radiation field seen by individual v=0-1 IR lines (J=0 to 5) in the model, with an 85% transmission of the stellar black body near 4.6 micron  
  > "Here we focus on the effect on the IR lines of the $\Delta J\pm1$ transitions between the ground state and the first vibrationally excited state for $J=0$ up to $J=5$." (4.3.2 Line overlap)
   - software: mcp
   - assumption: the observed single transition can be reproduced by many different combinations of relative IR pumping  
  > "The current observations of a single transition can be reproduced by many different combinations of relative pumping in the IR." (4.3.2 Line overlap)
   - fitting: _not stated_
   - validation: not stated; larger-scale CO profiles from line-overlap models do not match the observations  
  > "it is clear that the models that can reproduce the maser emission also produce changes in the larger scale emission that do not match the observations." (4.3.2 Line overlap)

## Software

- **CASA** : initial calibration (and, implicitly, imaging)  
  > "was done using the Common Astronomy Software Applications (CASA) package (cite: McMullin07)" (2 Observations and data reduction)
- **mcp** : Monte Carlo radiative transfer models of CO excitation  
  > "we perform one-dimensional radiative transfer models using the Monte Carlo radiative transfer code" (4.3.1 Continuum pumping)
- **CDMS and JPL databases** : CO transition frequencies, energy levels and Einstein coefficients  
  > "The transition frequencies, energy levels, and Einstein coefficients were taken from the CDMS and JPL databases (cite: Muller01; Picket98)" (4.3.1 Continuum pumping)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| maser peak brightness temperature (after continuum subtraction) | 1950 | not stated | K | 3 | the peak of the emission has a brightness temperature of $T_b\approx1950$ K in the two epochs. |
| maser optical depth | -0.55 | not stated | dimensionless | 3 | the brightness temperatures imply a maser optical depth of $\tau\approx-0.55$. |
| FWHM of the brightest spectral component (epoch 1, epoch 2) | 1.9, 2.2 | not stated | km/s | 3 | The brightest spectral component has a full width at half maximum (FWHM) of $1.9$ and $2.2$ km s$^{-1}$ in the two epochs, respectively. |
| maser velocity | ~35 | not stated | km/s | 3 | The velocity of the CO maser remained stable at $\sim35$ km s$^{-1}$ over the two epochs with a FWHM velocity width of $\sim2$ km s$^{-1}$. |
| brightness temperature on 30 Nov, 3 Dec, 5 Dec 2015 | 1330, 2000, 1570 | not stated | K | 3 | The emission brightness temperature appears to change from $T_b\approx1330$ K on 30 Nov to $T_b\approx2000$ K on 3 Dec and to $T_b\approx1570$ K on 5 Dec 2015. |
| maser variability over five days | +-20% | not stated | percent | 3 | This indicates that there could be variability of the order of $\pm20\%$ within only a five-day timescale. |
| continuum flux variation over the three days | <2.5% | not stated | percent | 3 | the continuum flux varies by less than $2.5\%$ over the three days |
| radiation field boost factor at 4.6 micron needed for a maser of sufficient strength | M~3 | not stated | dimensionless | 5 | a maser of sufficient strength can be generated if the radiation field at 4.6 $\mu$m is increased by a factor $M\sim3$. |
| inner envelope velocity V0 required | 4.2 | not stated | km/s | 5 | we require a larger velocity at the inner envelope ($V_0\approx4.2$ km s$^{-1}$) |
| velocity-law exponent beta required | 2.5 | not stated | dimensionless | 5 | a slightly steeper acceleration ($\beta\approx 2.5$) |
| turbulent velocity Vt required | 1.0 | not stated | km/s | 5 | larger turbulent velocity component ($V_t\approx 1.0$ km s$^{-1}$) |
| radius where J=3-2 population inversion peaks | ~7 | not stated | au | 5 | Population inversion in the $J=3-2$ line persists throughout most of the CSE and peaks around $7$ au. |
| mass-loss rate range generating maser emission in the model | 0.5-5e-7 | not stated | Msun/yr | 6 | maser emission is generated, from different parts of the envelope, for mass-loss rates between $0.5-5\times10^{-7}$ M$_\odot$ yr$^{-1}$. |
| mass-loss rate of W Hya allowed by lower resolution data | 1.5-3.0e-7 | not stated | Msun/yr | 6 | limiting the rate to between $1.5-3.0\times10^{-7}$ M$_\odot$ yr$^{-1}$. |
| dust-shell optical depth at 4.6 micron needed to reproduce the continuum excess | ~0.2 | not stated | dimensionless | 6 | a dust shell with an optical depth at 4.6 $\mu$m of $\sim0.2$ |

## Qualitative findings

- CO J=3-2 maser emission amplifies the stellar continuum, predominantly at the limb of the star, because CO absorption from the extended atmosphere is strongest towards the stellar centre  
  > "The maser predominantly amplifies the limb of the star because CO $J=3-2$ absorption from the extended stellar atmosphere is strongest towards the centre of the star." (abstract)
- maser morphology changed markedly between the two epochs while velocity stayed stable  
  > "The morphology of the bright masing CO emission has markedly changed between the two observing sessions." (3 Results)
- maser velocity coincides with the variable high-frequency H2O maser component and the OH amplified stellar image  
  > "The CO maser velocity corresponds to a previously observed variable component of high-frequency H$_2$O masers and with the OH maser that was identified as the amplified stellar image." (abstract)
- dust excess is not sufficient to supply the 4.6 micron radiation field; line overlap in the extended atmosphere is the likely pump  
  > "Excess from dust in the circumstellar envelope of W Hya is not sufficient to contribute significantly to the required radiation field at 4.6 $\mu$m." (abstract)

## Claim tuples

- H: CO J=3-2 emission around W Hya contains unambiguous maser emission | E: High angular resolution ALMA band 7 observations at two epochs, continuum-subtracted CO J=3-2 maps and single-beam spectra | R: Peak Tb about 1950 K above the 2700 K stellar continuum in both epochs, implying tau of about -0.55 | F: First unambiguous detection of CO maser emission, amplifying the stellar continuum | **supported**
- H: The maser changes with time and with background structure | E: Compared the two epochs (2015, 2017) and imaged three days of epoch 1 separately with a common beam | R: Morphology changed markedly between epochs; Tb varied between about 1330 K and 2000 K over five days while the continuum varied by less than 2.5% | F: Changes reflect the underlying stellar and extended-atmosphere structure and small foreground masing changes | **supported**
- H: The 4.6 micron continuum radiation (dust) can pump the CO J=3-2 maser | E: 1-D Monte Carlo CO radiative transfer with the 4.6 micron field boosted by a factor M and with an added dust shell | R: M~3 and adjusted V0, beta, Vt reproduce the maser, requiring a dust shell of tau(4.6 micron)~0.2 that conflicts with the observed infrared spectrum | F: Continuum pumping by dust is not a viable explanation | **refuted**
- H: Line overlap of absorption and emission lines near 4.6 micron pumps the maser | E: Changed the relative radiation field seen by individual v=0-1 IR lines in the model | R: Maser J=3-2 inversion produced by selective pumping, consistent with the estimated mass-loss rates of W Hya; the pump cannot be uniquely constrained from one transition | F: Line overlap is highly likely the main pumping mechanism; multi-transition observations are needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: CO rotational and vibrational excitation modeled with radiative transfer to test whether inversion occurs and what pumps it  
  > "In order to investigate the occurrence of the CO maser in the $J=3-2$ transition, we perform one-dimensional radiative transfer models" (4.3.1 Continuum pumping)
- Alternative: Pumping by an increased continuum IR radiation field from circumstellar dust was rejected because the required 4.6 micron excess is not supported by the observed infrared spectrum  
  > "we conclude that this is not a viable solution. We thus investigate pumping that can occur due to line overlap around 4.6 $\mu$m." (4.3.1 Continuum pumping)
- Alternative: Transverse motions of dense clumps across the stellar disk rejected as the cause of the morphology change (would need ~10 km/s)  
  > "transverse motions of dense clumps across the full stellar disk within two years would, at the distance of W Hya, require a transverse velocity of $\sim10$ km s$^{-1}$" (4.1 Morphology and variability)
- How they decided it was enough: _not stated_
- Limitation (authors): The emission region is complex and the derived Tb is a lower limit if it consists of multiple compact components  
  > "if it consists of multiple more compact components, the derived $T_b$ presents a lower limit." (3 Results)
- Limitation (authors): Models are one-dimensional and were not adjusted to match the lower angular resolution observations  
  > "Because of the large number of degeneracies including the individual line pumping, we did not attempt to adjust the standard CSE model to simultaneously reproduce the larger scale observations." (4.3.2 Line overlap)
- Limitation (authors): Pumping cannot be more exactly determined with only one observed CO maser transition  
  > "A more exact determination of the relative pumping of these lines is not possible with the current observations of only one CO maser transition" (Conclusions)
- Caveat (inferred, ours): Peak Tb and tau depend on beam dilution, the adopted 2700 K continuum and the continuum-subtraction/line-free channel choice, none of which are detailed
- Caveat (inferred, ours): The two epochs use different robust values, so the beam shapes differ and absolute flux/Tb comparisons carry beam-matching systematics
- Caveat (inferred, ours): Models are hand-tuned (V0, beta, Vt, M) with no formal fit, no uncertainties and a degenerate line-overlap setup
- Caveat (inferred, ours): Claim of 'no other explanation' relies on the 1-D model with a user-adjusted atmospheric absorption profile

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Line-free channel selection and continuum subtraction method
- Missing: Self-calibration solution intervals and reference antenna
- Missing: Cell/image size, deconvolver, masking and clean threshold
- Missing: Flux and gain calibrators (deferred to Vlemmings17, Vlemmings19)
- Missing: The mcp model inputs for the line-overlap runs, the atmospheric absorption profile and the line-by-line pump scaling
- Missing: ACA data details used in the model comparison
- Data volume (inferred): Band 7 long-baseline spectral-line data for two epochs (about 2.1 hr and 35 min on source); likely tens of GB raw per project, plus ACA data
- Score (inferred): 3/5, Project codes, dates, on-source times, robust values and beams are given, and the main results are numeric, but calibrators, self-cal solints, continuum subtraction and imaging parameters are deferred to earlier papers or omitted, and the radiative transfer models are hand-tuned with partial inputs
- Rediscovery candidate: yes, ALMA projects are named and the main measurements (peak Tb, tau, FWHM, variability) can be redone from archival data, although the imaging recipe is incomplete and the data's public status is not stated in the paper

## Links

- Method: (cite: Vlemmings17) (earlier presentation of the same ALMA observations with calibrator details)
- Method: (cite: Vlemmings19) (earlier presentation of the same ALMA observations with calibrator details)
- Method: (cite: Morris80) (method of scaling the 4.6 micron radiation field for CO maser inversion)
- Method: (cite: Piehler91) (line-overlap pumping of CO masers)
- Companion: (cite: Khouri14) (source of the baseline CO envelope model parameters)
- Companion: (cite: Vlemmings03) (OH maser amplifying the stellar image, velocity comparison)

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.2.00025.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 63,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
