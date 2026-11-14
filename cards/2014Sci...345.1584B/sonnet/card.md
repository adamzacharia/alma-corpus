# Detection of a branched alkyl molecule in the interstellar medium: iso-propyl cyanide

`2014Sci...345.1584B` | Science 2014 | first author: Belloche, Arnaud | arXiv: 1410.2607 | DOI: 10.1126/science.1256678

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Can a branched alkyl molecule (iso-propyl cyanide) be detected in the ISM, and how does its abundance compare with its straight-chain isomer and with chemical model predictions?  
  > "We report an interstellar detection of a branched alkyl molecule, iso-propyl cyanide (i-C$_3$H$_7$CN), with an abundance 0.4 times that of its straight-chain structural isomer." (abstract)
- Target **Sgr B2(N) northern hot core**: coordinates field center RA 17h47m19.87s, Dec -28d22m16s (J2000), between the two hot cores  
  > "The field was centered at $\alpha_{\rm J2000}$=17$^{\rm h}$47$^{\rm m}$19.87$^{\rm s}$, $\delta_{\rm J2000}$=$-28^\circ$22$'$16$''$" (Materials and Methods); "It is located close to the Galactic Center, which is $8.34 \pm 0.16$ kpc from the Sun(cite: Reid14)." (main text); z/distance 8.34 kpc  
  > "The field was centered at $\alpha_{\rm J2000}$=17$^{\rm h}$47$^{\rm m}$19.87$^{\rm s}$, $\delta_{\rm J2000}$=$-28^\circ$22$'$16$''$" (Materials and Methods); "It is located close to the Galactic Center, which is $8.34 \pm 0.16$ kpc from the Sun(cite: Reid14)." (main text); distance from Reid et al. 2014 (Reid14)  
  > "The field was centered at $\alpha_{\rm J2000}$=17$^{\rm h}$47$^{\rm m}$19.87$^{\rm s}$, $\delta_{\rm J2000}$=$-28^\circ$22$'$16$''$" (Materials and Methods); "It is located close to the Galactic Center, which is $8.34 \pm 0.16$ kpc from the Sun(cite: Reid14)." (main text)

## Data provenance

- ALMA projects: 2011.0.00017.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-110.7 GHz in four overlapping setups; four 1875 MHz spectral windows each; 244 kHz channels smoothed to 488 kHz  
  > "The full frequency range between 84.1 and 110.7 GHz was covered with four slightly overlapping spectral setups." (Observations); "The channel spacing was 244 kHz, but the spectra were smoothed to 488 kHz (1.7–1.3 km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: 22-26 antennas in selected tracks  
  > "The number of antennas for the selected tracks varied between 22 and 26." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typically 2.0'' x 1.4'' (min 1.6'' x 1.2'', max 3.0'' x 1.4'')  
  > "The size (HPBW) of the synthesized beam depends on the setup and the sideband but is typically $2.0'' \times 1.4''$ (minimum $1.6'' \times 1.2''$, maximum $3.0'' \times 1.4''$)." (Data reduction)
- max recoverable scale: _not stated_
- sensitivity: median rms 4.4-9.9 mJy/beam per track  
  > "The median rms noise level reached for each selected track varies between 4.4 and 9.9 mJy/beam." (Data reduction)
- time on source: ten tracks of ~0.6-2 h each; only the longest track per setup used  
  > "for a total of ten observing tracks lasting between $\sim 0.6$ and 2 h each, but only the longest track of each setup was used in this work." (Observations)
- observing dates: August-October 2012  
  > "The observations were carried out with the Atacama Large Millimeter/submillimeter Array (ALMA) between August and October 2012." (Observations)
- pi or archival as stated: _not stated_
- Line: i-PrCN about 50 transitions detected (not stated)
- Line: n-PrCN about 120 transitions detected (not stated)
- Other facility **IRAM 30m**: Earlier single-dish 3 mm line survey used to build the preliminary emission model  
  > "We constructed a preliminary model of the emission of all molecules previously detected, on the basis of our analysis of the previous single-dish survey of Sgr B2(N)(cite: Belloche13)." (main text)
- External data: Rotational spectroscopy predictions for i-PrCN and n-PrCN (CDMS)  
  > "Predictions of the rotational spectra of *i*-PrCN and *n*-PrCN were taken from the CDMS(cite: CDMS2), version 1 and 2, respectively." (Laboratory spectroscopy) [from Müller et al. 2005 (cite: CDMS2); Müller et al. 2011 (cite: i-PrCN_rot_2011)]
- External data: Vibrational state data for partition function corrections  
  > "We use data from Durig et al.(cite: i-PrCN_etc_FIR_1972) for *i*-PrCN and from Durig et al.(cite: n-PrCN_vib_2001) for *n*-PrCN." (Laboratory spectroscopy) [from (cite: i-PrCN_etc_FIR_1972); (cite: n-PrCN_vib_2001)]
- External data: Dust mass opacity 0.01 cm2/g at 230 GHz  
  > "Assuming a dust mass opacity of 0.01 cm$^{2}$ g$^{-1}$ at 230 GHz(cite: Ossenkopf94)" (Continuum emission) [from Ossenkopf & Henning 1994 (cite: Ossenkopf94)]
- Simulation/model as data: MAGICKAL chemical kinetics model of hot core collapse and warm-up (~700 species), used to interpret observed abundances  
  > "The chemical model solves the fully-coupled time-dependent chemical kinetics of nearly 700 unique chemical species" (Astrochemical numerical simulations)

## Processing

### Calibration

- pipeline or manual: CASA calibration with bandpass B1730-130, flux Neptune (Titan for setup 2), phase J1700-261; self-calibration on a strong line  
  > "The bandpass calibration was carried out on the quasar B1730-130. The absolute flux density scale was derived from Neptune (except for the selected track of the second setup that used Titan)." (Data reduction)
- casa version: CASA 4.2.0, r28322  
  > "The data were calibrated and imaged with CASA (Version 4.2.0, r28322)." (Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (Titan for setup 2)  
  > "The absolute flux density scale was derived from Neptune (except for the selected track of the second setup that used Titan)." (Data reduction)
- flux scale uncertainty: ~15%  
  > "we estimate the absolute calibration uncertainty on the flux density to be on the order of 15%." (Data reduction)
- self calibration: three or four iterations using a strong spectral line in each setup  
  > "Three or four iterations of self-calibration were performed using a strong spectral line detected toward Sgr B2(N) in each setup." (Data reduction)

### Imaging

- task: CLEAN in CASA  
  > "The images were produced with the CLEAN deconvolution algorithm in CASA." (Data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: first-order baseline fitted to selected line-free channels; separate sets for northern and southern parts  
  > "A first-order baseline was fitted to these selected channels and the result of the fit was used to split each data cube into two cubes, one for the line emission and one for the continuum emission." (Data reduction)
- line free channels: six groups of few channels per spectral window, selected by eye  
  > "For each spectral window of each setup, we selected six groups of few channels that seemed to be free of strong line emission." (Data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: spectra smoothed to 488 kHz  
  > "The channel spacing was 244 kHz, but the spectra were smoothed to 488 kHz (1.7–1.3 km s$^{-1}$)." (Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Line identification strategy follows the IRAM 30m survey  
  > "The line identification in the ALMA spectra was performed following the same strategy as for our previous, single-dish, spectral-line survey of Sgr B2(N) with the IRAM 30 m telescope(cite: Belloche13)." (Line identification and spectral modeling) [from Belloche et al. 2013 (cite: Belloche13)]
- Chemical model as described by Garrod 2013; n-PrCN mechanisms from Belloche09  
  > "during the collapse and warm-up of the hot core, as described by Garrod(cite: Garrod13)." (Astrochemical numerical simulations) [from Garrod 2013 (cite: Garrod13); Belloche et al. 2009 (cite: Belloche09)]
- Contaminating-molecule subtraction in population diagrams as in previous n-PrCN detection  
  > "like we did for our previous single-dish detection of *n*-PrCN(cite: Belloche09)" (Line identification and spectral modeling) [from Belloche et al. 2009 (cite: Belloche09)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel ranges used for continuum subtraction
- CLEAN parameters (weighting/robust, cell size, image size, masks, threshold)
- Which spectral line and reference antenna/solint used for self-calibration
- Full list and frequencies of i-PrCN and n-PrCN transitions used in population diagrams
- Weeds LTE parameters for all other molecules in the preliminary model
- Details of free-free contamination of the continuum
- Chemical model rate values and parameters beyond input files

## Analysis recipe

1. **Calibrate and image the ALMA data**: Calibration and CLEAN imaging in CASA with self-calibration; continuum separated by baseline fitting  
  > "The data were calibrated and imaged with CASA (Version 4.2.0, r28322)." (Data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Absolute calibration accuracy estimated from track redundancy and spectral overlap (~15%)  
  > "Based on the redundancies of the tracks and the spectral overlap between the setups, we estimate the absolute calibration uncertainty on the flux density to be on the order of 15%." (Data reduction)
2. **Identify lines via LTE modeling**: LTE model of all molecules with 5 parameters (column density, temperature, source size, velocity offset, linewidth) per spectral window  
  > "with five parameters: column density, temperature, source size, velocity offset, and linewidth." (Line identification and spectral modeling)
   - software: Weeds, CLASS
   - assumption: LTE  
  > "The emission of each molecule across the full 3 mm atmospheric window is modeled assuming local thermodynamic equilibrium" (Line identification and spectral modeling)
   - fitting: _not stated_
   - validation: Only transitions not severely blended with other species are used  
  > "Only the transitions that are not severely blended with transitions of other species are shown in these figures." (Line identification and spectral modeling)
3. **Measure source size from integrated-intensity maps**: Elliptical Gaussian fit to maps of least contaminated transitions  
  > "The emission toward the northern hot core was fitted with an elliptical Gaussian for each map." (Line identification and spectral modeling)
   - fitting: _not stated_
   - validation: Setup 3 excluded owing to largest beam and astrometry readjustment  
  > "Ignoring the transitions from the third setup that has the largest beam and for which the absolute astrometry was readjusted" (Line identification and spectral modeling)
4. **Derive rotation temperature**: Population diagram linear fit after subtracting contaminating-molecule model  
  > "Finally, we constructed population diagrams(cite: Goldsmith99) for *i*-PrCN and *n*-PrCN using the transitions that are not too severely blended with emission from other identified species." (Line identification and spectral modeling)
   - assumption: Optically thin transitions  
  > "provided the transitions are optically thin (which is verified to be true a posteriori)" (Line identification and spectral modeling)
   - fitting: linear fit to population diagram  
  > "a linear fit to these data points can give a rough estimate of the rotation temperature characterizing the emission of the molecules, provided the transitions are optically thin" (Materials and Methods, Line identification and spectral modeling)
   - validation: Optical thinness verified a posteriori  
  > "provided the transitions are optically thin (which is verified to be true a posteriori)" (Line identification and spectral modeling)
5. **Derive column densities and abundance ratio**: LTE model with size 1.0'', Trot 153 K, linewidth 5 km/s, with correction for vibrationally excited states  
  > "With the size and temperature derived above and a linewidth measurement of 5 km s$^{-1}$, we obtain a good fit to all transitions" (main text)
   - software: Weeds
   - parameter: Vibrational partition function factors at 150 K: 1.64 (i-PrCN), 2.09 (g-n-PrCN), 2.36 (a-n-PrCN)  
  > "increase the partition function values at 150 K by factors of 1.64, 2.09, and 2.36 for *i*-PrCN, *g-n*-PrCN, and *a-n*-PrCN, respectively." (Laboratory spectroscopy)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive H2 column density from continuum**: Thermal dust emission at 98.8 GHz with opacity, beta, T assumed; extrapolated to 1'' with r^-1.5 density profile  
  > "We extrapolate these results for the more compact region where the PrCN emission comes from (FWHM $\sim 1.0''$) by assuming spherical symmetry and a density profile proportional to $r^{-1.5}$(cite: Osorio99)." (Continuum emission)
   - assumption: kappa=0.01 cm2/g at 230 GHz, beta=1.0, mu=2.8 per H2, T=150 K, all continuum from dust, distance 8.34 kpc  
  > "a dust emissivity index $\beta = 1.0$, a mean molecular weight per H$_2$ molecule of 2.8, a temperature of 150 K, and that all the continuum flux is due to thermal dust emission" (Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
7. **Simulate hot-core chemistry**: MAGICKAL: free-fall collapse to nH 2e8 cm-3, then static warm-up to 400 K, modified rate equations  
  > "The first is a free-fall collapse from a total hydrogen density, $n_{\rm H}$, of 3000 to $2 \times 10^8$ cm$^{-3}$." (Astrochemical numerical simulations)
   - software: MAGICKAL
   - assumption: Radical-site bias favoring secondary carbon; other rates and binding energies identical between isomers  
  > "All other rates and binding energies are assumed to be identical between the *i*-PrCN and *n*-PrCN forms." (Astrochemical numerical simulations)
   - fitting: _not stated_
   - validation: Compared model peak temperatures with observed rotation temperature and abundance ratios  
  > "This agrees well with the rotation temperatures that we determine from observational data for these molecules." (main text)

## Software

- **CASA** 4.2.0 (r28322): calibration, fixvis astrometry correction, self-calibration, CLEAN imaging  
  > "The data were calibrated and imaged with CASA (Version 4.2.0, r28322)." (Data reduction)
- **Weeds** April 2014 version: LTE line identification and spectral modeling  
  > "The main difference is that we used Weeds(cite: Maret11) (version of April 2014) which is part of the CLASS software" (Line identification and spectral modeling)
- **CLASS/GILDAS** : host for Weeds  
  > "which is part of the CLASS software (see http://www.iram.fr/IRAMFR/GILDAS)" (Line identification and spectral modeling)
- **MAGICKAL** : time-dependent gas-grain hot-core chemistry  
  > "The recently developed chemical kinetics model MAGICKAL (Model for Astrophysical Gas and Ice Chemical Kinetics And Layering, ) was used to simulate the time-dependent chemistry of the source." (main text)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved source size of PrCN emission | 1.0 | 0.3 | arcsec (FWHM) | 3 | we derive a deconvolved angular size of $1.0'' \pm 0.3''$ (FWHM) for the region where both species emit. |
| Rotation temperature (n-PrCN) | 153 | 12 (SEM) | K | 4 | We derive $T_{\rm ex} = 154 \pm 99$ K for *i*-PrCN and $153 \pm 12$ K (SEM) for *n*-PrCN. |
| i-PrCN column density | 7.2e16 | 1.4e16 (SEM) | cm^-2 | 5 | we derive column densities of $7.2 \pm 1.4 \times 10^{16}$ cm$^{-2}$ and $1.8 \pm 0.4 \times 10^{17}$ cm$^{-2}$ (SEM), respectively |
| n-PrCN column density | 1.8e17 | 0.4e17 (SEM) | cm^-2 | 5 | we derive column densities of $7.2 \pm 1.4 \times 10^{16}$ cm$^{-2}$ and $1.8 \pm 0.4 \times 10^{17}$ cm$^{-2}$ (SEM), respectively |
| [i-PrCN]/[n-PrCN] | 0.40 | 0.06 (SEM) | dimensionless | 5 | which yields an abundance ratio \[*i*-PrCN\]/\[*n*-PrCN\] of $0.40 \pm 0.06$ (SEM) |
| i-PrCN abundance relative to H2 | 1.3e-8 | 0.2e-8 | dimensionless | 6 | we deduce average abundances relative to H$_2$ of $1.3 \pm 0.2 \times 10^{-8}$ for *i*-PrCN and $3.2 \pm 0.5 \times 10^{-8}$ (SEM) for *n*-PrCN |
| n-PrCN abundance relative to H2 | 3.2e-8 | 0.5e-8 | dimensionless | 6 | we deduce average abundances relative to H$_2$ of $1.3 \pm 0.2 \times 10^{-8}$ for *i*-PrCN and $3.2 \pm 0.5 \times 10^{-8}$ (SEM) for *n*-PrCN |
| Peak continuum flux density at 98.8 GHz, northern hot core | 0.24 | not stated | Jy/1.8''x1.3'' beam | 6 | The peak flux density measured toward the northern hot core at 98.8 GHz is 0.24 Jy/1.8$''$$\times$1.3$''$-beam. |
| Average N_H2(1'') | 5.6e24 | 0.4e24 (rms) | cm^-2 | 6 | $N_{{\rm H}_2}(1'') = 5.6 \pm 0.4 \times 10^{24}$ cm$^{-2}$, $M(1'') = 232 \pm 17$ $M_\odot$ |
| Model i-PrCN/n-PrCN peak ratio | 2.2 | not stated | dimensionless | 7 | they show a slight bias toward *i*-PrCN production (2.2:1), rather than the observed bias toward *n*-PrCN (0.4:1). |

## Qualitative findings

- Branched i-PrCN detected with abundance comparable to its straight-chain isomer, suggesting branched molecules may be generally abundant in star-forming regions  
  > "This detection suggests that branched carbon-chain molecules may be generally abundant in the ISM." (abstract)
- Model forms both isomers on grain ices via radical addition with different dominant pathways  
  > "both isomers are produced within or upon dust grain ice mantles through the addition of molecular radicals, albeit via differing reaction pathways" (abstract)

## Claim tuples

- H: Branched alkyl molecules exist in the ISM | E: ALMA 3 mm survey of Sgr B2(N) northern hot core with LTE modeling | R: About 50 i-PrCN transitions detected; [i]/[n]=0.40±0.06 | F: i-PrCN detected, first branched alkyl molecule in the ISM | **supported**
- H: Grain-surface radical chemistry can produce both isomers | E: MAGICKAL hot-core model | R: Both isomers form at 55-75 K in ices; peak gas phase at 160 K; model ratio 2.2:1 vs observed 0.4:1 | F: Mechanism reproduces temperatures but overpredicts i-PrCN, possibly due to uncertain surface rates | **partially**

## Reasoning

- Why this data: Northern hot core has narrower lines, making faint rare species easier to detect  
  > "The detection of faint lines from rare species is therefore easier toward the former and we focus on this one in the present work." (main text)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Preliminary LTE model not fully optimized for ALMA; abundance uncertainties exclude free-free contamination and dust property uncertainties  
  > "This model has not been fully optimized for ALMA yet but it is already sufficiently reliable to allow for detecting new molecules in the ALMA spectra." (Line identification and spectral modeling); "take neither possible contamination of the continuum emission by free-free emission nor uncertainties on the dust properties into account." (main text)
- Caveat (inferred, ours): Rotation temperature of i-PrCN poorly constrained (154±99 K); shared parameters assumed for both isomers
- Caveat (inferred, ours): Line blending near confusion limit may bias column densities
- Caveat (inferred, ours): Model ratio disagrees with observation by factor ~5
- Caveat (inferred, ours): Continuum-derived N(H2) depends on assumed T, beta, opacity and extrapolation

## Reproducibility

- Data public (paper): Interferometric data available in the ALMA archive; chemical model input files online  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgments)
- Products in archive: _not stated_
- Code: Chemical model input files available online  
  > "The chemical model input files are located at www.astro.cornell.edu/$\sim$rgarrod/resources." (Acknowledgments)
- Missing: CLEAN settings
- Missing: Exact line-free channels
- Missing: Full list of transitions used
- Missing: Full Weeds model of other molecules
- Data volume (inferred): Large: four setups x 4 spectral windows, a few hundred GB raw
- Score (inferred): 3/5, Public data and clear LTE recipe, but imaging settings, channel selections and the full contaminant model are unstated.
- Rediscovery candidate: no, Requires a full Weeds model of all contaminating species and unstated imaging choices.

## Links

- Method: Maret et al. 2011 (cite: Maret11) (Weeds software)
- Method: Goldsmith & Langer 1999 (cite: Goldsmith99) (population diagram method)
- Companion: Belloche et al. 2013 (cite: Belloche13) (IRAM 30m survey used for preliminary model)
- Companion: Garrod 2013 (cite: Garrod13) (chemical model)
- Related: EMoCA (Exploring Molecular Complexity with ALMA)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 55,
  "rate": 0.647
 },
 "evidence_ok": true
}
```
