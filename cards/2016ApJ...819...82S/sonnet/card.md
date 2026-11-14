# Properties of the Interstellar Medium in Star-Forming Galaxies at z ~ 1.4 Revealed with ALMA

`2016ApJ...819...82S` | The Astrophysical Journal 2016 | first author: Seko, Akifumi | arXiv: 1601.06783 | DOI: 10.3847/0004-637X/819/1/82

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How do molecular gas mass, gas fraction, dust mass, gas-to-dust ratio and depletion time of main-sequence galaxies at z~1.4 depend on stellar mass and metallicity?  
  > "we aim to reveal the relations between the molecular gas mass or its fraction and the stellar mass or metallicity for main sequence galaxies at $z\sim1.4$." (Introduction)
- Target **20 star-forming galaxies from Yabe et al. 2012 (SXDS fields, e.g. SXDS1_13015)**: coordinates Per-galaxy RA/Dec in Table 1 (e.g. SXDS1_13015: 02:17:13.63, -05:09:39.8)  
  > "We selected 20 of these 71 galaxies as ALMA targets to cover a wide range of stellar mass ($4\times10^9$ - $4\times10^{11}~M_\odot$)" (Samples); z/distance z_spec 1.28-1.59 (from Halpha)  
  > "We selected 20 of these 71 galaxies as ALMA targets to cover a wide range of stellar mass ($4\times10^9$ - $4\times10^{11}~M_\odot$)" (Samples); distance from Subaru/FMOS near-IR spectroscopy of Halpha (Yabe12)  
  > "We selected 20 of these 71 galaxies as ALMA targets to cover a wide range of stellar mass ($4\times10^9$ - $4\times10^{11}~M_\odot$)" (Samples)

## Data provenance

- ALMA projects: 2011.0.00648.S
- bands: Band 6, 222.094-252.583 GHz  
  > "The observed frequencies were 222.094 GHz to 252.583 GHz (band-6)." (4.1 Observations)
- frequencies and spectral setup: 4 correlator setups, LO 231.198, 236.168, 240.380, 244.166 GHz; 3-4 SPWs each of 1.875 GHz; 488.28 kHz resolution  
  > "The frequencies of local oscillator in each setup were 231.198 GHz, 236.168 GHz, 240.380 GHz, and 244.166 GHz." (4.1 Observations); "Each SPW had a bandwidth of 1.875 GHz." (4.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 23-25 12 m antennas  
  > "The number of 12 m antennas was 23-25." (4.1 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.6-1.3 arcsec synthesized beam  
  > "The synthesized beam size was $0''.6-1''.3$" (4.2 Data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum 0.04-0.1 mJy/beam; channel maps (~50 km/s) 0.5-1 mJy/beam  
  > "The noise level of continuum map was $0.04-0.1~\mathrm{mJy~beam^{-1}}$" (4.2 Data reduction)
- time on source: 8-15 min per galaxy  
  > "The on-source time for each galaxy was $8-15~\mathrm{min}$." (4.1 Observations)
- observing dates: 2012 August 9, 11, 15, 26  
  > "The observations were carried out in 2012 August 9, 11, 15, and 26" (4.1 Observations)
- pi or archival as stated: Cycle 0 program, PI K. Ohta  
  > "ALMA cycle0 session (ID=2011.0.00648.S, PI=K. Ohta)" (4.1 Observations)
- Line: 12CO J=5-4 (not stated)
- Other facility **Subaru/FMOS**: Halpha and [NII] spectroscopy: redshifts and N2 metallicities  
  > "The gas metallicities are derived from the N2 method by using the H$\alpha$ and \[NII\]$\lambda$ 6584 emission lines" (Samples)
- Other facility **GALEX, CFHTLS, SXDS, UKIDSS UDS, Spitzer SpUDS**: Photometry for stellar mass and SFR (via Yabe12)  
  > "Stellar mass was derived by spectral energy distribution (SED) fitting (cite: Sawi12) with the optical to mid-infrared data" (Samples)
- External data: Stellar masses, SFRs, redshifts, metallicities of the sample  
  > "Sample galaxies used in this study are taken from (cite: Yabe12)." (Samples) [from (cite: Yabe12)]
- External data: CO(5-4)/CO(1-0) luminosity ratio of 0.23  
  > "the average CO(5-4)/CO(1-0) luminosity ratio is 0.23" (5.1 Individual galaxy) [from (cite: Dadd15)]
- External data: Metallicity-dependent alpha_CO relation (eq. 7)  
  > "We adopt the equation (7) by (cite: Genz12)" (5.1 Individual galaxy) [from (cite: Genz12)]
- External data: Dust temperature 25-35 K for main-sequence galaxies at z=1.2-1.7  
  > "the dust temperatures of main sequence galaxies at $z=1.2-1.7$ are $25-35~\mathrm{K}$" (6.1 Individual galaxy) [from (cite: Magn14)]
- External data: Local comparison samples for gas mass, depletion time, gas-to-dust ratio  
  > "We compare the results with those in local galaxies (CO Legacy Database for Galex Arecibo SDSS Survey (cite: Sain11a)" (5.2.1) [from (cite: Sain11a; Bose14a; Bose14b; Remy14; Lero11)]

## Processing

### Calibration

- pipeline or manual: Re-calibration with CASA after fixing phase calibrator coordinates and interpolating flagged flux calibrator data  
  > "we made re-calibrations with the corrected coordinates of the phase calibrator and with the interpolated value for the flagged data of the flux calibrator." (4.2 Data reduction)
- casa version: CASA 4.2  
  > "version 4.2 package in a standard manner" (4.2 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, Uranus, Callisto; 2012 Solar system models  
  > "The flux calibration was made with the Ganymede, Uranus, and Callisto." (4.1 Observations); "We used the 2012 models of the Solar system objects for flux calibrations." (4.2 Data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, natural weighting  
  > "The maps were made with the CASA task CLEAN with natural weighting." (4.2 Data reduction)
- deconvolver: No cleaning (zero iterations, dirty maps)  
  > "The number of iteration was zero (i.e., dirty maps)" (4.2 Data reduction)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Maps centered on K-band centroid of each galaxy  
  > "The center position of each map coincided with the centroid of the galaxy in the K-band image." (4.2 Data reduction)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB in uv-data; continuum maps from LSB+USB line-free channels  
  > "We subtracted the continuum emission in uv-data by using the CASA task UVCONTSUB." (4.2 Data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.6-1.3 arcsec (Table 3)  
  > "The synthesized beam size was $0''.6-1''.3$" (4.2 Data reduction)
- final rms: continuum 0.04-0.1 mJy/beam; channel 0.5-1 mJy/beam at ~50 km/s  
  > "the noise level of each channel map was $0.5-1~\mathrm{mJy~beam^{-1}}$." (4.2 Data reduction)

### Inherited from earlier work

- Sample selection, stellar masses, SFRs, metallicities  
  > "Sample galaxies used in this study are taken from (cite: Yabe12)." (Samples) [from (cite: Yabe12)]
- alpha_CO metallicity dependence and metallicity calibration conversion  
  > "we convert the metallicity using an empirical relation between the two metallicity calibrations of (cite: Kewl08)" (5.1 Individual galaxy) [from (cite: Genz12); (cite: Kewl08)]
- Image stacking justified by uv-stacking comparison  
  > "they found that image-stacking produced similar results to $uv$-stacking" (5.2 Stacking analysis) [from (cite: Lind15)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channels used for continuum
- Primary-beam correction details
- Cell and image size
- Rest frequency values and line-width/flux extraction method for individual detections
- Stacking details: alignment, resampling number, how redshift shifts were handled
- Fitting method for L_IR template SED
- Welch t-test procedure details
- Exact corrected phase-calibrator coordinates

## Analysis recipe

1. **Recalibrate and image**: CASA recalibration with corrected phase calibrator position; UVCONTSUB; dirty maps with natural weighting; ~50 km/s channel maps  
  > "The maps were made with the CASA task CLEAN with natural weighting." (4.2 Data reduction)
   - software: CASA
   - parameter: zero CLEAN iterations  
  > "The number of iteration was zero (i.e., dirty maps)" (4.2 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect CO lines**: Moment-0 maps with varying velocity width 50-1000 km/s and central velocity within +/-200 km/s; S/N growth curve in central box +/-0.5 arcsec; detection if S/N>3 and spectrum S/N>3  
  > "We define the “central box", which is the region within $\pm0''.5$ in right ascension and declination from the map center." (5 Source detection)
   - software: CASA IMMOMENTS
   - parameter: detection S/N>3; marginal continuum 2-3  
  > "We consider detections for cases where the peak SN in the central box is $>3$, and marginal detections if the peak SN is $2-3$." (5 Source detection)
   - fitting: _not stated_
   - validation: Peak positions of detected sources within 0.3 arcsec of center confirm box size  
  > "The peak positions of all the detected source are within $\pm0''.3$ in right ascension and declination from the map center" (5 Source detection)
3. **Derive CO luminosity and molecular gas mass**: L'CO(5-4) from flux; scale to CO(1-0) by 0.23; M_mol = alpha_CO L'CO(1-0) with metallicity-dependent alpha_CO; 2 sigma upper limits (200 km/s width) for non-detections  
  > "We take a 2$\sigma_{200}$ upper limit for the CO(5-4) flux density and a velocity width of 200 $\mathrm{km~s^{-1}}$." (5.1 Individual galaxy)
   - assumption: CO(5-4)/CO(1-0)=0.23 (factor 2 uncertainty); alpha_CO from Genz12 eq. 7; LCDM H0=70, Om=0.3, OL=0.7  
  > "We adopt this value for the conversion of CO(5-4) luminosity to CO(1-0) luminosity." (5.1 Individual galaxy)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive dust mass**: Modified blackbody from the continuum flux at rest ~0.5 mm; 2 sigma upper limits  
  > "We take a $2\sigma$ upper limit as $S_\mathrm{cont}$" (6.1 Individual galaxy)
   - assumption: kappa_d(125 um)=1.875 m2/kg, beta=1.5, T_dust=30 K  
  > "We adopt $\kappa_\mathrm{d}(125~\mu\mathrm{m}) = 1.875~\mathrm{m^2~kg^{-1}}$ (cite: Hild83), and $\beta = 1.5$." (6.1 Individual galaxy)
   - fitting: _not stated_
   - validation: Dust mass varies by 1.2 for T=25/35 K and by 2 for beta=1.0/2.0  
  > "The dust mass can change by a factor of 1.2 when we adopt dust temperatures of $25\ \mathrm{or}\ 35$ K" (6.1 Individual galaxy)
5. **Stacking of subsamples**: Pixel-by-pixel 1/sigma^2 weighted average of dirty channel maps (50 km/s bins, +/-1000 km/s) and continuum maps for mass and metallicity subsamples; errors by random resampling; Welch's t-test  
  > "The images are stacked on a pixel by pixel basis using weighted average. The weights are calculated as $1/\sigma^{2}$" (5.2 Stacking analysis)
   - parameter: two most massive galaxies excluded  
  > "we did not include the two most massive galaxies, SXDS1_35572 and SXDS1_79307, in our stacking analysis." (5.2 Stacking analysis)
   - fitting: _not stated_
   - validation: Significance via Welch's t test  
  > "We carried out the Welch’s $t$ test to evaluate the significance of difference between the stacked values of the subsamples." (5.2.1)
6. **Gas-to-dust ratio and depletion time**: GDR = M_mol/M_dust; t_dep = M_mol/SFR using UV-based SFR and SFR from L_IR (template SED fit) plus uncorrected UV  
  > "$L_\mathrm{IR}$ are derived by fitting a template SED of main sequence galaxies at $z\sim1.5$ (cite: Magd12b) to the continuum data obtained in this observation." (8 Molecular gas mass against SFR, and gas depletion time)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2: Calibration, UVCONTSUB, CLEAN imaging, IMMOMENTS  
  > "Common Astronomy Software Applications (cite: McMu07) version 4.2 package" (4.2 Data reduction)
- **Hyperz** : Photometric redshifts in the parent sample (Yabe12)  
  > "Photometric redshift was derived with Hyperz (cite: Bolz00)." (Samples)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO detections | 11 of 20 | not stated | galaxies | 2 | We detected CO($J=5-4$) emission lines from 11 galaxies. |
| Molecular gas mass of detected galaxies | (3.9-12)e10 | not stated | Msun | 3 | $(3.9-12)\times10^{10}~M_\odot$ and $0.25-0.94$, respectively |
| Gas fraction, smaller/larger stellar mass stacks | 0.55 and 0.34 | ±0.09, ±0.08 | dimensionless | 5 | The gas mass fractions are $0.55\pm0.09$ and $0.34\pm0.08$ for the smaller and larger stellar mass subsamples |
| Gas fraction, lower/higher metallicity stacks | 0.65 and 0.32 | ±0.07, ±0.09 | dimensionless | 5 | The gas mass fractions are $0.65\pm0.07$ and $0.32\pm0.09$ for the lower and higher metallicity subsamples |
| Dust mass of detected galaxies | (3.9-38)e7 | not stated | Msun | 4 | Dust masses of the detected galaxies are $(3.9-38)\times10^{7}~M_\odot$. |
| Gas-to-dust ratio, lower/higher metallicity stacks | 568 and 401 | ±261, ±142 | dimensionless | 6 | are $568\pm261$ and $401\pm142$, respectively |
| Depletion time, smaller/larger stellar mass stacks | 3.9e8 and 2.6e8 | ±1.2e8, ±0.6e8 | yr | 6 | $(3.9\pm1.2)\times10^{8}~\mathrm{yr}$ and $(2.6\pm0.6)\times10^{8}~\mathrm{yr}$ |
| Continuum detections | 2 detected, 5 marginal | not stated | galaxies | 2 | We detected continuum emission from two galaxies with $\mathrm{SN} > 3$. |

## Qualitative findings

- Gas fractions at z~1.4 are much higher than local spirals and decrease with stellar mass and metallicity  
  > "The molecular gas mass fraction decreases with increasing stellar mass" (abstract)
- Depletion time tends to decrease with stellar mass and metallicity, unlike local galaxies  
  > "which contrasts with the trends in local galaxies." (abstract)

## Claim tuples

- H: Gas fraction depends on stellar mass and metallicity at z~1.4, including lower masses | E: CO(5-4) detections and stacking in mass and metallicity bins | R: f_gas 0.55 vs 0.34 (mass) and 0.65 vs 0.32 (metallicity) | F: Gas fraction decreases with both stellar mass and metallicity | **supported**
- H: Gas-to-dust ratio at z~1.4 differs from local | E: Gas masses from CO and dust masses from continuum | R: GDR 568 and 401 in stacks | F: 3-4 times larger than local at fixed metallicity | **supported**
- H: Depletion time trends match local galaxies | E: Stacked M_mol/SFR versus stellar mass and metallicity | R: t_dep ~3e8 yr, decreasing with mass/metallicity | F: Opposite to local trends, though weakly significant | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dirty maps used because S/N is modest and CLEAN could add uncertainty; same procedure for all galaxies for stacking  
  > "we were afraid the uncertainty in the maps increases by CLEAN" (4.2 Data reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas masses exclude the factor ~2 uncertainty of the luminosity ratio and alpha_CO  
  > "does not include the uncertainty of the luminosity ratio and $\alpha_\mathrm{CO}$ (uncertainty of a factor of $\sim2$)" (5.1 Individual galaxy)
- Limitation (authors): N2 metallicities may be overestimated by 0.1-0.2 dex  
  > "the metallicity derived with N2 method is systematically overestimated by $0.1-0.2$ dex" (Samples)
- Caveat (inferred, ours): Single mid-J CO line requires large extrapolation to CO(1-0)
- Caveat (inferred, ours): Fixed T_dust and beta from single-band continuum
- Caveat (inferred, ours): Sample SFR bias and unreliable SFRs of two massive galaxies
- Caveat (inferred, ours): Many significance tests on small subsamples

## Reproducibility

- Data public (paper): ALMA Cycle 0 project acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00648.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Stacking implementation details
- Missing: Line-free channel choices
- Missing: Corrected phase calibrator coordinates
- Missing: Parent-sample properties come from Yabe12 and Yabe14
- Data volume (inferred): Tens of GB raw (Cycle 0, 20 targets, 4 setups)
- Score (inferred): 3/5, Data identified and recipe largely clear, but stacking and imaging details are missing and inputs come from other papers.
- Rediscovery candidate: no, Recipe incomplete (stacking, line-free channels, SFR/metallicity inputs from external papers).

## Links

- Method: (cite: Lind15) (Image versus uv stacking)
- Method: (cite: Genz12) (Metallicity-dependent alpha_CO)
- Companion: (cite: Yabe12) (Parent sample and FMOS data)
- Companion: (cite: Seko14) (CO(2-1) gas-to-dust ratios in three z~1.4 galaxies)
- Related: FMOS-COSMOS/SXDS Halpha survey (Yabe et al.)
- Related: PHIBSS (Tacconi et al.)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 53,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
