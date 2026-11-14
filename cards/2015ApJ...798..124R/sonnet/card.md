# ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146

`2015ApJ...798..124R` | The Astrophysical Journal 2015 | first author: Ricci, L. | arXiv: 1410.8265 | DOI: 10.1088/0004-637X/798/2/124

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What is the radial distribution of mm-sized dust in the HD 107146 debris disk, and is there a gap or dip in the dust surface density?  
  > "We analyze the ALMA interferometric visibilities using debris disk models with radial profiles for the dust surface density parametrized as *i*) a single power-law, *ii*) a single power-law with a gap, and *iii*) a double power-law." (abstract)
- Target **HD 107146**: coordinates phase center (12:19:06.358, 16:32:52.091) J2000  
  > "At a Hipparcos-measured distance of 27.5 $\pm$ 0.4 pc (cite: vanLeeuwen:2007) HD 107146 has the same spectral type as the Sun (G2V)" (1 Introduction); "the phase center for all observations were set to ($\alpha$, $\delta$) = (12:19:06.358, 16:32:52.091) J2000" (2 Observations and data reduction); z/distance 27.5 ± 0.4 pc  
  > "At a Hipparcos-measured distance of 27.5 $\pm$ 0.4 pc (cite: vanLeeuwen:2007) HD 107146 has the same spectral type as the Sun (G2V)" (1 Introduction); "the phase center for all observations were set to ($\alpha$, $\delta$) = (12:19:06.358, 16:32:52.091) J2000" (2 Observations and data reduction); distance from Hipparcos (van Leeuwen 2007)  
  > "At a Hipparcos-measured distance of 27.5 $\pm$ 0.4 pc (cite: vanLeeuwen:2007) HD 107146 has the same spectral type as the Sun (G2V)" (1 Introduction); "the phase center for all observations were set to ($\alpha$, $\delta$) = (12:19:06.358, 16:32:52.091) J2000" (2 Observations and data reduction)

## Data provenance

- ALMA projects: 2011.0.00470.S
- bands: 1.25 mm continuum (mean 239.5 GHz), Cycle 0  
  > "for a mean frequency of 239.5 GHz ($\lambda=1.25$ mm)" (2 Observations and data reduction)
- frequencies and spectral setup: four spectral windows at 230.5, 232.5, 246.5, 248.5 GHz; 1.875 GHz bandwidth each; 0.488 MHz channels  
  > "Dual-polarization observations were obtained in four bands centered on frequencies of 230.5, 232.5, 246.5, and 248.5 GHz" (2 Observations and data reduction); "Each spectral window was configured to provide a bandwidth of 1.875 GHz per polarization with a channel spacing of 0.488 MHz" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 16-24 per block  
  > "2012 Dec 16       | 23       | 15–382" (Table 1)
- configurations: _not stated_
- baselines: 15-402 m (shortest 15 m)  
  > "2013 Jan 1        | 24       | 15–402" (Table 1)
- angular resolution: 1.15'' x 0.84'' (natural weighting, ~32 x 23 AU); 2.52'' x 2.25'' with 2'' taper  
  > "This weighting scheme gives a synthesized beam of $1.15'' \times 0.84''$, corresponding to a spatial resolution of about $32 \times 23$ AU" (3.1 Continuum Images)
- max recoverable scale: _not stated_
- sensitivity: 1σ = 0.030 mJy/beam (natural), 0.057 mJy/beam (outer taper)  
  > "the 1$\sigma$ noise levels on the natural and outer taper weighted maps are 0.030 and 0.057 mJy/beam, respectively" (3.1 Continuum Images)
- time on source: _not stated_
- observing dates: 2012 Jan 11, Jan 27 (two blocks), 2012 Dec 16, 2013 Jan 1  
  > "2012 Jan 11       | 17       | 19–269         | 2.29   | Mars  | 3C273    | J1224$+$213" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- External data: Millimeter flux densities at 0.88, 1.32 and 3.0 mm used for the spectral index  
  > "By combining the flux densities measured for the HD 107146 debris disk at 0.88 mm, 1.25 mm, 1.32 mm and 3.0 mm by (cite: Hughes:2011), this work, (cite: Corder:2009) and (cite: Carpenter:2005), respectively" (4.1 Debris Disk Model) [from Hughes:2011; Corder:2009; Carpenter:2005]
- External data: Dust absorption coefficients from porous-grain dust model  
  > "The absorption coefficients $Q^{\rm{abs}}_\nu(a)$ were extracted from the dust models of (cite: Ricci:2010a)" (4.1 Debris Disk Model) [from Ricci:2010a]
- External data: Stellar Teff = 5841 K and log(Lbol/Lsun) = 0.04  
  > "$L^{\star}_{\nu}$ was derived from a black body with effective temperature $T = 5841$ K and bolometric luminosity $Log(L_\mathrm{bol}/L_\odot) = 0.04$ (cite: Carpenter:2008; Hillenbrand:2008)" (4.1 Debris Disk Model) [from Carpenter:2008; Hillenbrand:2008]

## Processing

### Calibration

- pipeline or manual: calibrated by NRAO staff  
  > "The ALMA data were calibrated by NRAO staff using the CASA software package version 4.1 (cite: McMullin:2007)." (2 Observations and data reduction)
- casa version: CASA 4.1  
  > "The ALMA data were calibrated by NRAO staff using the CASA software package version 4.1 (cite: McMullin:2007)." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars or Titan, Butler-JPL-Horizon 2012 models  
  > "Flux calibration was established by observing either Mars or Titan, and adopting the Butler-JPL-Horizon 2012 models, resulting in an accuracy of $10\%$." (2 Observations and data reduction)
- flux scale uncertainty: 10%  
  > "resulting in an accuracy of $10\%$" (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean, multi-frequency synthesis  
  > "The CASA task `clean` was used to Fourier invert the complex visibilities to create an image of the dust emission and to perform multi-frequency synthesis deconvolution." (3.1 Continuum Images)
- deconvolver: _not stated_
- weighting robust: natural weighting, Briggs robust = 2  
  > "obtained with natural weighting using a Briggs robust parameter of 2" (3.1 Continuum Images)
- uv taper: Gaussian uv-taper, on-sky FWHM 2 arcsec  
  > "weighted with a Gaussian uv-taper with an on-sky FWHM of 2 arcsec" (3.1 Continuum Images)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.030 mJy/beam natural; 0.057 mJy/beam taper  
  > "the 1$\sigma$ noise levels on the natural and outer taper weighted maps are 0.030 and 0.057 mJy/beam, respectively" (3.1 Continuum Images)

### Inherited from earlier work

- Dust opacity / grain model  
  > "The absorption coefficients $Q^{\rm{abs}}_\nu(a)$ were extracted from the dust models of (cite: Ricci:2010a)" (4.1 Debris Disk Model) [from Ricci:2010a]
- Relation between q, beta and beta_s  
  > "(cite: Draine:2006) derived a relation between $q$, the spectral index $\beta$ of the dust opacity" (4.1 Debris Disk Model) [from Draine:2006]

### Not stated but needed to reproduce (our reading)

- Number of emcee walkers and iterations (only 'several hundreds') and burn-in
- Priors and bounds on model parameters
- Clean threshold, mask, cell and image size of the CLEAN images
- Whether CASA clean or other tools were used for the visibility extraction and weight rescaling in detail
- Which spectral windows/channels were used for continuum (line-free channels excluded CO)
- Exact dust opacity table values and grain composition fractions
- CO imaging parameters (weightings, channel widths)

## Analysis recipe

1. **rescale visibility uncertainties and correct proper motion**: Rescaled weights by median ratio of observed dispersion in uv cells to reported uncertainties; adjusted visibility phases for proper motion  
  > "The median ratio between the observed dispersion within a cell and the uncertaintiues reported in the ALMA data was computed using cells containing $\ge$10 visibilities." (2 Observations and data reduction)
   - software: CASA
   - parameter: cells with >=10 visibilities  
  > "using cells containing $\ge$10 visibilities" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **image continuum and measure integrated flux**: clean imaging with natural and tapered weighting; flux integrated over area above 2σ in the tapered map  
  > "This was obtained by integrating the surface brightness over the area showing emission at" (3.1 Continuum Images)
   - software: CASA
   - fitting: _not stated_
   - validation: compared with CARMA flux of 10.4 ± 1.4 mJy  
  > "consistent at $\approx 1\sigma$ with the measurement of 10.4 $\pm$ 1.4 mJy by (cite: Corder:2009)" (3.1 Continuum Images)
3. **derive grain size slope q from mm spectral index**: Fit mm SED alpha, beta = alpha - 2, then Draine (2006) relation for q  
  > "We then obtained $q = 3.25 \pm 0.09$ from the (cite: Draine:2006) relation." (4.1 Debris Disk Model)
   - parameter: a_min ≈ 1.7 μm (blow-out), a_max = 2 cm  
  > "For this reason we adopted $a_{\rm{max}} = 2$ cm." (4.1 Debris Disk Model)
   - assumption: optically thin, Rayleigh-Jeans emission; rho = 1.2 g/cm3  
  > "the dust emission at these wavelengths is optically thin and in the Rayleigh-Jeans regime" (4.1 Debris Disk Model)
   - fitting: _not stated_
   - validation: _not stated_
4. **fit disk models to visibilities**: Model image multiplied by Gaussian primary beam (24.3''), Fourier transformed and sampled at observed uv points; chi2 minimised for single power-law, power-law with gap, double power-law  
  > "The model visibilities were obtained through a Fourier transform of the image and sampling the model using the same $(u,v)$ data points in the ALMA observations." (4.2 Models - data comparison)
   - software: emcee
   - parameter: model image 2048x2048 pixels of 0.015''; flux scaled as nu^(2+beta), beta=0.4  
  > "The model image has a size of 2048x2048 pixel with 0.015$''$ pixels." (4.2 Models - data comparison)
   - assumption: axisymmetric, geometrically and optically thin disk; constant dust opacity across disk  
  > "Our models consider a debris disk as an axisymmetric, geometrically thin and optically thin layer of solids." (4.1 Debris Disk Model)
   - fitting: emcee affine-invariant MCMC, several hundred walkers and iterations; best values are the mode of marginalized posteriors with 68.3% intervals  
  > "For each surface density parameterization, `emcee` was run with several hundreds walkers (see (cite: Foreman:2013)) for several hundreds iterations." (4.2 Models - data comparison)
   - validation: Different walker starting positions tested; residual maps and visibility profiles inspected  
  > "We also ran several trials by either varying or not varying the starting positions of the walkers" (4.2 Models - data comparison)
5. **compare models statistically**: F-test and Akaike information criterion between nested models  
  > "In this case we can use the $F-$test to investigate whether this decrease of the $\chi^2$-value with models with two extra parameters is statistically significant" (5.2 Single power-law with gap)
   - fitting: _not stated_
   - validation: _not stated_
6. **CO upper limit and planet mass from gap width**: LTE CO column/mass upper limit from non-detection; chaotic/crossing zone relation for planet mass using gap width  
  > "we derived a $3\sigma$ upper limit for the mass of gaseous CO of $M_{\rm{CO}} < 1.9 \times 10^{-6}~M_{\oplus}$" (7 The non-detection of CO)
   - parameter: Tex = 50 K, FWHM 1.9 km/s, inclination ~20 deg  
  > "uniform excitation temperature of 50 K throughout the disk" (7 The non-detection of CO)
   - assumption: LTE  
  > "after assuming LTE" (7 The non-detection of CO)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.1: calibration and clean imaging  
  > "The ALMA data were calibrated by NRAO staff using the CASA software package version 4.1" (2 Observations and data reduction)
- **emcee** : MCMC fitting of visibility models  
  > "The best-fit model parameters and parameter uncertainties were found using `emcee`" (4.2 Models - data comparison)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated flux density at 1.25 mm | 12.5 | 1.3 | mJy | 2 | The integrated flux density from the disk is 12.5 $\pm$ 1.3 mJy at 1.25 mm. |
| Millimeter spectral index alpha | 2.42 | 0.16 | dimensionless | 3 | we measured a millimeter spectral index $\alpha = 2.42 \pm 0.16$ |
| Grain size distribution slope q | 3.25 | 0.09 | dimensionless | 3 | We then obtained $q = 3.25 \pm 0.09$ |
| Gap radius (single power-law with gap) | 80.9 | +1.8/-2.6 | AU | 4 | $R_{\rm{gap}}$ \[AU\] / ... / $80.9^{+1.8}_{-2.6}$ |
| Gap width | 9.0 | +1.0/-1.5 | AU | 4 | radial width $\Delta R_{\rm{gap}} = 9.0^{+1.0}_{-1.5}$ AU |
| Single power-law slope p | 0.74 | +0.06/-0.05 | dimensionless | 4 | The $p$ value of $0.74^{+0.06}_{-0.05}$ indicates a surface density which is increasing with radius |
| Double power-law R_break | 68.5 | +6.2/-2.6 | AU | 4 | $R_{\rm{break}} = 68.5^{+6.2}_{-2.6}$ AU |
| Inclination (single power-law) | 20.6 | 1.9 | deg | 4 | $i$ \[deg\] / $20.6 \pm 1.9$ |
| Delta chi2 gap vs single power-law | 43.0 | not stated | dimensionless | 5 | which is lower by $\Delta\chi^2=43.0$ than the case of a single power-law model with no gap |
| F-test statistic gap vs no gap | 8e-10 | not stated | dimensionless | 5 | The $F$-test statistics in this case has a value of $8 \times 10^{-10}$ |
| CO mass 3σ upper limit (Tex=50 K) | 1.9e-6 | not stated | Earth masses | 6 | $M_{\rm{CO}} < 1.9 \times 10^{-6}~M_{\oplus}$ |
| Dust mass of best-fit models | ≈0.2 | not stated | Earth masses | 4 | have a dust mass of $\approx 0.2~M_{\oplus}$ |
| Planet mass from gap, crossing zone (coefficient 2.1) | 6.1 | +2.1/-3.1 | Earth masses | 6 | We obtain $6.1^{+2.1}_{-3.1}~M_{\oplus}$ and $4.1^{+1.4}_{-2.1}~M_{\oplus}$ |

## Qualitative findings

- Dust surface density increases with radius in the outer disk, unlike primordial disks  
  > "at least in the outer regions of the HD 107146 debris disk, the dust surface density *increases* with the distance from the central star." (9.2 Origin of the HD 107146 debris disk)

## Claim tuples

- H: Does the disk have a depletion in dust at intermediate radii? | E: Fit single power-law, gap and double power-law models to visibilities | R: Gap and double power-law models fit significantly better (F-test 8e-10); gap at ~81 AU, width ~9 AU | F: Dust depletion at ~70-80 AU, though data cannot distinguish gap from double power-law | **supported**
- H: Is there gas (CO) in the disk? | E: Search for CO J=2-1 emission | R: No detection; M_CO < 1.9e-6 Earth masses | F: Very low CO-to-dust ratio, disfavoring photoelectric instability origin of a gap | **supported**
- H: Could a planet carve the gap? | E: Apply chaotic/crossing zone relations to gap width | R: Planet mass ~1-6 Earth masses | F: A few-Earth-mass planet at ~80 AU is a possible explanation if the gap is confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fitted visibilities rather than images to avoid deconvolution effects and flux filtering  
  > "The models were fitted to the complex visibilities rather than the images to avoid non-linear effects of the image deconvolution" (4.2 Models - data comparison)
- Alternative: Photoelectric instability rejected as gap origin due to CO limit  
  > "is made unlikely by our very tight upper limit to the CO-to-dust mass ratio" (9.1 A gap in the disk?)
- How they decided it was enough: _not stated_
- Limitation (authors): Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density  
  > "The ALMA data presented in this paper do not allow us to distinguish between these possible different functional forms" (5.3 Double power-law)
- Caveat (inferred, ours): Constant dust opacity assumed, degenerate with surface density
- Caveat (inferred, ours): Cycle 0 resolution only marginally resolves the 8-9 AU gap
- Caveat (inferred, ours): Summary quotes CO J=3-2 whereas data are J=2-1 (inconsistency)
- Caveat (inferred, ours): MCMC convergence not documented

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00470.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: emcee walker/iteration counts and priors
- Missing: Exact clean parameters (mask, threshold, cell, image size)
- Missing: Dust opacity table of Ricci et al. 2010a
- Data volume (inferred): ~10-50 GB raw for five Cycle 0 execution blocks
- Score (inferred): 3/5, Public data and clear model equations, but MCMC settings, priors and imaging details are missing.
- Rediscovery candidate: yes, Public data, explicit model parameterization, numeric results (gap radius/width, chi2).

## Links

- Method: Ricci:2010a (dust model for absorption coefficients)
- Method: Draine:2006 (q-beta relation)
- Method: Foreman:2013 (emcee)
- Companion: Hughes:2011 (SMA observations of the same disk)
- Companion: Corder:2009 (CARMA observations of the same disk)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 47,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
