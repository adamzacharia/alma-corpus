# High Angular Resolution ALMA Images of Dust and Molecules in the SN 1987A Ejecta

`2019ApJ...886...51C` | The Astrophysical Journal 2019 | first author: Cigan, Phil | arXiv: 1910.02960 | DOI: 10.3847/1538-4357/ab4b46

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the spatial distribution, mass, composition and temperature of dust in the SN 1987A ejecta, how does it relate to CO and SiO gas, and is there evidence of a heated compact source?  
  > "Here, we revisit the dust mass and grain composition using the ALMA photometry." (Introduction)
- Target **SN 1987A**: coordinates RA 5h35m27.998s, Dec -69d16m11.107s (ICRS)  
  > "located at a distance of $51.4 \pm 1.2$ kpc in the Large Magellanic Cloud (cite: Panagia1999)" (Introduction); "Our derived ring+ejecta system center used in this work is $\alpha$=5$^{\rm h}$35$^{\rm m}$27.998s, $\delta$=–69$^{\circ}$16$^{\prime}$11.107$''$ (ICRS), $\pm$18 mas" (3 Description of Images); z/distance 51.4 ± 1.2 kpc  
  > "located at a distance of $51.4 \pm 1.2$ kpc in the Large Magellanic Cloud (cite: Panagia1999)" (Introduction); "Our derived ring+ejecta system center used in this work is $\alpha$=5$^{\rm h}$35$^{\rm m}$27.998s, $\delta$=–69$^{\circ}$16$^{\prime}$11.107$''$ (ICRS), $\pm$18 mas" (3 Description of Images); distance from Panagia1999  
  > "located at a distance of $51.4 \pm 1.2$ kpc in the Large Magellanic Cloud (cite: Panagia1999)" (Introduction); "Our derived ring+ejecta system center used in this work is $\alpha$=5$^{\rm h}$35$^{\rm m}$27.998s, $\delta$=–69$^{\circ}$16$^{\prime}$11.107$''$ (ICRS), $\pm$18 mas" (3 Description of Images)

## Data provenance

- ALMA projects: 2013.1.00063.S
- bands: Band 7 (870 um) and Band 9 (450 um); plus Band 6 from Matsuura2017  
  > "The Band–7 (870$\mu$m) and 9 (450$\mu$m) integrations utilized between 34 and 36 antennae with baselines spanning 15m to 2.3km." (2.1 Observations and Reduction)
- frequencies and spectral setup: Sub-bands of four 2 GHz blocks of 128 channels (15.625 MHz each)  
  > "Each sub-band is comprised of four 2 GHz blocks of 128 channels (15.625 MHz each)." (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 2.3 km  
  > "baselines spanning 15m to 2.3km" (2.1 Observations and Reduction)
- angular resolution: ~80 mas (Band 9 beam 0.08x0.06 arcsec)  
  > "We present high angular resolution ($\sim$80 mas) ALMA continuum images of the SN 1987A system" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 12.5-20.9 min per sub-band  
  > "2015-07-25 | 10379 | J0538-4405 | J0635-7516 | J0601-7036 | 20.9" (Table 1)
- observing dates: 2015-06-28 to 2015-09-25 (SN days 10352-10441)  
  > "The data were taken over several days in the latter half of 2015, between 10352 and 10441 days after the initial explosion." (2.1 Observations and Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=6-5 (691.47 GHz)
- Line: SiO J=7-6 (303.93 GHz)
- Line: CO J=2-1 (230.54 GHz)
- Line: SiO J=5-4 and 6-5 (217.10 and 260.52 GHz)
- Other facility **Herschel**: FIR flux densities used in SED fits  
  > "we use the *Herschel* flux densities from (cite: Matsuura2015) in our model fits" (4.2 Modified Blackbody Fits)
- Other facility **HST**: Halpha image for comparison  
  > "The SN 1987A ring and ejecta continuum image at 315 GHz is shown in comparison to H$\alpha$ in Fig. [2](#fig:hstcomp)." (3 Description of Images)
- External data: CO J=2-1, SiO J=5-4, 6-5 data cubes (Cycle 2+3)  
  > "we also utilize the CO $J$=2 $\!\rightarrow\!$ 1, SiO $J$=5 $\!\rightarrow\!$ 4, and SiO $J$=6 $\!\rightarrow\!$ 5[^1] data as described in (cite: Abellan2017)" (2.3 Molecular Line Data) [from (cite: Abellan2017)]
- External data: Cycle 2 Band 6 continuum images  
  > "We also utilize here the Cycle 2 Band–6 imaging data presented by (cite: Matsuura2017), to provide continuum information below 300 GHz." (2.2 Defining Continuum Wavelength Ranges) [from (cite: Matsuura2017)]
- External data: Herschel ejecta flux densities  
  > "we use the *Herschel* flux densities from (cite: Matsuura2015) in our model fits" (4.2 Modified Blackbody Fits) [from (cite: Matsuura2015)]
- External data: Nucleosynthesis yields for dust mass limits  
  > "Considering the 18 $M_\odot$ $Z=0.008Z_\odot$ progenitor model from (cite: Nomoto2013), the total mass of the key limiting metals C, N, Ne, Mg, Si, S, and Fe is 0.77 $M_\odot$" (6.1 Dust Properties) [from (cite: Nomoto2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.1  
  > "Each data set was reduced separately with Common Astronomy Software Applications package (cite: CASA), version 4.5.1." (2.1 Observations and Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-454 for all blocks  
  > "The same flux calibrator, J0519-454, was used for all observation blocks." (Table 1)
- flux scale uncertainty: 10% in Bands 6&7, 20% in Band 9  
  > "We include an additional 10% uncertainty for systematic (calibration) error in Bands 6 & 7, and 20% in Band–9" (4.1 Photometry)
- self calibration: Tried; negligible impact, not applied  
  > "was determined to have a negligible impact on the images." (2.1 Observations and Reduction)

### Imaging

- task: tclean  
  > "Once calibrated, the `tclean` algorithm was used to deconvolve and image the data." (2.1 Observations and Reduction)
- deconvolver: _not stated_
- weighting robust: natural for continuum and CO 6-5; robust=-1 for SiO 7-6  
  > "SiO $J$=7 $\!\rightarrow\!$ 6 was imaged with `robust`$=-1$ in order to better spatially resolve the central features of interest." (2.3 Molecular Line Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: zeroth order in uv plane (uvcontsub); image-plane compared  
  > "Initially we used  to subtract a (zeroth order) continuum in the visibility plane." (3 Description of Images)
- line free channels: continuum windows chosen free of line emission using Matsuura2017 line model (Table 2 ranges)  
  > "Only windows that were free from molecular line emission (shown by the grey vertical bands) were used to make continuum images" (2.2 Defining Continuum Wavelength Ranges)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Band 6 restored to common 0.30 arcsec circular beam; SiO cubes convolved to the 7-6 beam, 0.015 arcsec pixels  
  > "The Band–6 images were restored to a common circular beam with full-width at half-maximum (FWHM) of 0.30$''$." (2.2 Defining Continuum Wavelength Ranges)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Cube reduction of CO 2-1, SiO 5-4, 6-5  
  > "For full details of their data reduction technique, we refer the reader to their Section 2." (2.3 Molecular Line Data) [from (cite: Abellan2017)]
- Dust SED fitting with many kappa profiles  
  > "following (cite: Indebetouw2014) and (cite: Matsuura2015)" (4.2 Modified Blackbody Fits) [from (cite: Indebetouw2014); (cite: Matsuura2015)]
- Ring-center alignment technique  
  > "These images have been aligned following a technique in (cite: Alp2018a) where the ring emission is used to derive a reference center" (3 Description of Images) [from (cite: Alp2018a)]

### Not stated but needed to reproduce (our reading)

- Robust value or weighting detail for continuum images beyond 'natural'
- Line-free channel/velocity ranges for the uvcontsub fit
- Clean thresholds, masks, image sizes and cell sizes
- Spectral windows used in each continuum image beyond Table 2
- Priors and likelihood details of the MLE/MCMC fit
- Which Herschel flux values were used
- Preliminary Cycle 6 flux densities (Matsuura et al., in prep)
- Details of the radex grid sampling and matching criterion
- Calibration scripts/pipeline versus manual

## Analysis recipe

1. **Reduce and image continuum and line data**: CASA calibration, tclean imaging of line-free windows and cubes; 300 km/s channels  
  > "were created with `tclean` in , with a spectral resolution of 300 km s$^{-1}$" (2.3 Molecular Line Data)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: Dust-CO anticorrelation checked against continuum construction, uv vs image subtraction and dirty map  
  > "Thus the apparent anti-correlation seen in the dust and CO distributions is robust to changes in the data processing." (3 Description of Images)
2. **Measure ejecta, ring and total photometry**: Elliptical apertures for ejecta and annuli for ring; uncertainties from random-position aperture RMS, ring smearing, and calibration, added in quadrature  
  > "All of these uncertainties were added in quadrature to estimate the overall uncertainty in a given band" (4.1 Photometry)
   - software: CASA
   - parameter: 315 GHz ejecta aperture 0.42x0.36 arcsec, PA 25 deg  
  > "$r_\mathrm{MAJ} \times r_\mathrm{MIN}$ = 0.42$''$$\times$0.36$''$ and major axis P.A. of 25$^\circ$" (4.1 Photometry)
   - fitting: _not stated_
   - validation: Simulated observations of synthetic sources to check missing diffuse flux  
  > "we simulated observations for multiple synthetic sources resembling SN 1987A but with varying extended ellipse components" (4.1 Photometry)
3. **Fit modified blackbodies to ejecta SED**: Optically thin modBB with 134 kappa profiles; 28 representative; bootstrap of 1000 samplings; good fit chi2_nu<2  
  > "in total we used 134 $\kappa_{\rm {abs}}(\lambda)$ profiles" (4.2 Modified Blackbody Fits)
   - software: emcee
   - parameter: grain radius 0.1 um (0.01 um for PAH)  
  > "we adopt a grain radius of $a=0.01$ $\mu$m for PAHs, and $a=0.1$ $\mu$m for all other models" (4.2 Modified Blackbody Fits)
   - assumption: Distance 51.4 kpc; optically thin emission; Herschel 70 and 500 um as upper limits  
  > "We assume that the emission is optically thin across this wavelength range." (4.2 Modified Blackbody Fits)
   - fitting: MLE with bootstrap, emcee MCMC, and OLS give consistent results  
  > "The OLS, MLE, and MCMC routines all yield consistent fits for a given dust emission profile." (4.2 Modified Blackbody Fits)
   - validation: chi2_nu<2 criterion plus nucleosynthesis mass limits  
  > "we set a quality threshold whereby $\chi_\nu^2 < 2$" (4.2 Modified Blackbody Fits)
4. **Fit ring synchrotron spectrum**: Power-law fit with ALMA Cycle 2 ring flux and Callingham2016 data  
  > "An updated fit, using the ALMA Cycle 2 ring flux densities and the more recent 1–9 GHz measurements from (cite: Callingham2016) from day 9686" (4.3 The Ring)
   - fitting: _not stated_
   - validation: Compared with Cendes2018 model within 5%  
  > "The ALMA ring flux densities are generally in excellent agreement (within 5%) with the (cite: Cendes2018) model prediction" (4.3 The Ring)
5. **Constrain gas conditions with non-LTE radiative transfer**: radex on SiO line ratios (regions A and B) and CO 6-5/2-1 ratios; uniform sphere; H2 collisional partner  
  > "we use the non-LTE (Local Thermal Equilibrium) line radiative transfer code radex (cite: VanderTak2007)." (5.1 Analysis of Molecular Lines Using RADEX)
   - software: radex
   - parameter: n_coll 1e3-1e10 cm-3, T_kin 10-200 K, N_SiO 1e12-1e18 cm-2, FWHM 400 km/s, filling factor 1-50%  
  > "The adopted ranges of the parameters are $n_{\rm coll}$=$10^{3}$–$10^{10}$ cm$^{-3}$ and $T_{\rm kin}$=10–200 K." (5.1 Analysis of Molecular Lines Using RADEX)
   - assumption: 10% calibration uncertainty on line intensities  
  > "we adopted 10 % of the line intensities for this analysis" (5.1 Analysis of Molecular Lines Using RADEX)
   - fitting: _not stated_
   - validation: _not stated_
6. **Quantify dust-CO anticorrelation**: Weighted normalized cross-correlation with (S/N)^2 weights; wavelet analysis over scales  
  > "The pixel weights used were the map (S/N)$^2$." (3 Description of Images)
   - fitting: _not stated_
   - validation: Wavelet scale tests  
  > "Below these scales, $r$ remains negative, so the anti-correlation is not sensitive to small changes in image resolution." (3 Description of Images)
7. **Limit dust mass with nucleosynthesis yields**: Compare fitted masses with metal yields from Nomoto2013 and Woosley models  
  > "Simple upper limits to the dust masses of various dust species can be estimated by calculating the resulting mass for 100% of the elements in the nucleosynthesis models being locked into dust" (6.1 Dust Properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.1: calibration, tclean imaging, imfit, uvcontsub/imcontsub  
  > "Each data set was reduced separately with Common Astronomy Software Applications package (cite: CASA), version 4.5.1." (2.1 Observations and Reduction)
- **emcee** : MCMC SED fitting  
  > "bayesian estimation with Markov Chain Monte Carlo (MCMC) posterior distributions, using the `emcee` package (cite: emcee)" (4.2 Modified Blackbody Fits)
- **radex** : non-LTE line modelling of SiO and CO  
  > "we use the non-LTE (Local Thermal Equilibrium) line radiative transfer code radex (cite: VanderTak2007)." (5.1 Analysis of Molecular Lines Using RADEX)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust-CO 6-5 correlation r | -0.30 | 0.08 | dimensionless | 6 | The resulting correlation measure is $r$=–0.30 $\pm$ 0.08 |
| Ejecta flux density at 679.22 GHz | 36.2 | ±7.2 (+7.2/-7.2 sys) | mJy | 2 | 679.22 / 11.5 / 36.2 $\pm$ 7.2 $^{+7.2}_{-7.2}$ |
| Power-law greybody beta | 2.05 | +0.11/-0.10 | dimensionless | 3 | $\beta=2.05^{+0.11}_{-0.10}$, ${M_{\mathrm dust}}$ $=1.53^{+0.13}_{-0.13}$ $M_\odot$ |
| Dust mass (power-law, kappa850=0.07) | 1.53 | ±0.13 | Msun | 3 | ${M_{\mathrm dust}}$ $=1.53^{+0.13}_{-0.13}$ $M_\odot$ |
| Dust mass vs kappa850 relation | M = 0.117 / kappa850 | not stated | Msun | 3 | ${M_{\mathrm dust} [M_\odot]} = 0.117 \times \kappa_{850}\, ^{-1}$ |
| Ring spectral index | -0.70 | 0.06 | dimensionless | 4 | results in a slightly lower $\alpha = -0.70 \pm 0.06$ |
| Blob compact-source flux at 679 GHz | 1-2 | not stated | mJy | 0 | the estimated flux density of the compact source is of order 1–2 mJy |
| Revised ejecta dust mass | 0.2-0.4 (carbon or silicate); <0.7 mixture | not stated | Msun | 7 | We revise the ejecta dust mass to $\mathrm{M_{dust}} = 0.2-0.4$$M_\odot$ for carbon or silicate grains |
| Blob offset from progenitor position | 72 mas east, 44 mas north | not stated | mas | 0 | offset 72 mas to the east and 44 mas to the north of the position of the progenitor star |

## Qualitative findings

- Ejecta dust is clumpy and asymmetric and fills the Halpha hole  
  > "Dust in the ejecta is asymmetric and clumpy, and overall the dust fills the spatial void seen in H$\alpha$ images" (abstract)

## Claim tuples

- H: Dust clumps are linked to CO distribution | E: Compare Band 9 dust with CO 6-5 image and cross-correlate | R: r=-0.30±0.08 anticorrelation | F: Dust and CO are locationally linked; carbonaceous dust may have formed after CO dissociation | **partially**
- H: Dust peak region is warmer or denser, perhaps heated by a compact source | E: radex SiO and CO ratios plus blob flux estimate | R: Blob at molecular hole with warmer-gas scenarios | F: Heating by a compact object is most likely, but density cannot be excluded | **partially**
- H: Ejecta dust mass is revised given composition and yields | E: modBB fits with many dust models plus nucleosynthesis limits | R: T 18-23 K; masses 0.2-0.4 Msun, <0.7 for mixture | F: Revised dust mass lower than previous large estimates | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Many kappa profiles used because the largest uncertainty is the submm mass absorption coefficient  
  > "The largest source of uncertainty in the observed dust mass is the choice of dust emission profile" (4.3 Results of the dust fits)
- Alternative: 44Ti heating rejected as unlikely to give a single central blob  
  > "it is unlikely that gas heated by $^{44}$Ti decay would be more centrally distributed and also be co-located with a small blob of gas and dust at one small region in the very inner ejecta" (6.3 The blob: gas and dust heated by the compact source)
- How they decided it was enough: _not stated_
- Limitation (authors): Only one frequency band for the blob, so its nature is unclear  
  > "we caution that we only have one frequency band and as such, the nature of the dust peak is not clear" (6.3 Interpreting the Bright Point Source)
- Limitation (authors): Band 6&7 fluxes systematically low, likely from decorrelation or flux scaling  
  > "Potential causes, as noted in § [2.1](#sec:observations), include decorrelation from poor weather or a mis-scaling of the flux calibrator." (4.1 Photometry)
- Caveat (inferred, ours): Band 6/7 flux offset of ~50% adds large systematic uncertainty to the SED fit
- Caveat (inferred, ours): Dust mass depends strongly on the assumed kappa
- Caveat (inferred, ours): CO 6-5 S/N is low, so the anticorrelation is moderate
- Caveat (inferred, ours): Compact-source interpretation rests on a single Band 9 detection
- Caveat (inferred, ours): Herschel data are unresolved and from a different epoch

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Exact Herschel fluxes and fit priors
- Missing: Line-free channel ranges
- Missing: Gabler et al. and Matsuura et al. in-prep data
- Data volume (inferred): Several hundred GB raw across nine execution blocks (Bands 7 and 9)
- Score (inferred): 3/5, Data identified and the SED/radex methods are described, but imaging details are sparse and several inputs are external or in preparation.
- Rediscovery candidate: no, Imaging details are incomplete and the analysis depends on external Herschel data and unpublished inputs.

## Links

- Method: (cite: Abellan2017) (CO and SiO data reduction)
- Method: (cite: Matsuura2015) (Dust SED fitting approach)
- Method: (cite: Alp2018a) (Center alignment technique)
- Companion: (cite: Matsuura2017) (Cycle 2 Band 6 and molecular line study)
- Companion: (cite: Indebetouw2014) (Cycle 0 ALMA dust)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00280.S",
  "2015.1.00631.S",
  "2016.1.00077.S",
  "2017.1.00221.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 54,
  "rate": 0.635
 },
 "evidence_ok": true
}
```
