# An ALMA survey of submillimetre galaxies in the Extended Chandra Deep Field South: high-resolution 870 μm source counts

`2013MNRAS.432....2K` | Monthly Notices of the Royal Astronomical Society 2013 | first author: Karim, A. | arXiv: 1210.0249 | DOI: 10.1093/mnras/stt196

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do the single-dish 870-um SMG number counts, especially the bright end, hold up when the LESS sources are resolved at ~1.5 arcsec with ALMA, or are they inflated by blending of multiple fainter SMGs?  
  > "This low resolution means that it is possible that several faint sources within a beam will appear as a single brighter source, changing the shape of the number counts" (Introduction)
- Target **LESS submillimetre sources in the ECDFS (122 of 126)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00294.S
- bands: Band 7, centred at 344 GHz (870 um)  
  > "The available 8-GHz bandwidth was centered at an observed frequency of 344 GHz (i.e. 870 $\mu$m) and we employed a dual polarization setup." (Observations and calibration)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Cycle 0 compact configuration, typically 15 antennas  
  > "Typically 15 antennas were available for each block." (Observations and calibration)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typical clean beam ~1.8"x1.2" (natural weighting)  
  > "Using natural weighting we achieve a typical restoring (clean) beam of $\sim$ 1.8$''\times$ 1.2$''$" (Observations and calibration)
- max recoverable scale: _not stated_
- sensitivity: average rms ~0.4 mJy/beam  
  > "The average root mean square (rms, $\sigma$) of the background noise in the maps is $\sigma \sim$ 0.4 mJy beam$^{-1}$" (Observations and calibration)
- time on source: ~120 s per field  
  > "Each science field, centered on the catalogued position of a given LESS source from W09, was observed for a total of $\sim$ 120 seconds." (Observations and calibration)
- observing dates: 2011 October 18 to 2011 November 3, eight observing blocks  
  > "The observing campaign was carried out in eight observing blocks (ALMA measurement sets; MS hereafter) between 2011 October 18 and 2011 November 3." (Observations and calibration)
- pi or archival as stated: _not stated_
- Other facility **APEX/LABOCA (LESS)**: 870-um parent survey and source catalogue of 126 sources  
  > "which obtained a deep, $\sigma_{\rm 870\mu m}\sim$ 1.2 mJy, homogeneous 870-$\mu$m map of the full ECDFS detecting 126 submillimetre sources." (Introduction)
- External data: LESS source catalogue, deboosted fluxes and single-dish counts  
  > "The result was the LABOCA ECDFS submillimetre survey (cite: WEIS09) (LESS and W09 hereafter)" (Introduction) [from (cite: WEIS09)]
- External data: SHADES counts scaled to LESS  
  > "those from the SCUBA HAlf Degree Extragalactic Survey (SHADES; (cite: COPP06)) scaled to the LESS data as described by W09." (Results and discussion) [from (cite: COPP06)]
- External data: Model counts of Baugh et al. for comparison  
  > "we also compare our SMG counts in Figure [3](#fig:counts) to the predicted counts from the model of (cite: BAUG05)" (Results and discussion) [from (cite: BAUG05)]

## Processing

### Calibration

- pipeline or manual: Processed with CASA; details deferred to H13  
  > "A detailed description of the raw data and its calibration as well as imaging is presented in H13." (Observations and calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars and Uranus for absolute flux; B 0537-441 bandpass; B 0402-362 phase  
  > "Mars, as well as Uranus, have been used to calibrate the absolute flux scale." (Observations and calibration)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Using natural weighting we achieve a typical restoring (clean) beam of $\sim$ 1.8$''\times$ 1.2$''$" (Observations and calibration)
- uv taper: _not stated_
- cell size: 0.2 arcsec  
  > "Each map has a pixel size of 0.2$''$ and a total extent of 128 pixels in each dimension" (Observations and calibration)
- image size: 128 pixels per side  
  > "Each map has a pixel size of 0.2$''$ and a total extent of 128 pixels in each dimension" (Observations and calibration)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: 17.3" FWHM Gaussian primary beam  
  > "is $17.3''$ in diameter." (Observations and calibration)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Raw data calibration, imaging, source extraction details and full catalogue  
  > "A detailed description of the raw data and its calibration as well as imaging is presented in H13." (Observations and calibration) [from (cite: HODG13)]
- Uncertainty recipes for elliptical Gaussian fits with correlated noise  
  > "The recipes we follow to determine the full uncertainty for elliptical source fits in the presence of correlated noise in radio maps have been motivated by (cite: COND97)" (3.1 Source extraction and characterization) [from (cite: COND97)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration steps (deferred to H13)
- Imaging task parameters, clean threshold and masks
- Source finder code is not public/named
- Parametrisations of f_recovered and f_spurious versus SNR
- Which 88 maps were selected, and the bin edges for the counts
- Flux scale uncertainty

## Analysis recipe

1. **Select best maps**: Keep maps with beam axial ratio <2 and rms <0.6 mJy/beam, giving 88 maps  
  > "beam-axial ratio $<$ 2 and rms noise level $\sigma<$ 0.6 mJy beam$^{-1}$" (Observations and calibration)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract sources**: Peaks above 2.5 sigma modelled with MH-MCMC elliptical Gaussian fits in 2x2 arcsec regions; point-source three-parameter model peak flux adopted  
  > "Metropolis-Hastings Markov chain Monte Carlo (MH-MCMC) algorithm to determine the best six parameter fit for an elliptical Gaussian" (3.1 Source extraction and characterization)
   - software: IDL source extraction code
   - fitting: MH-MCMC; fitting error from posterior after correcting for chain autocorrelation  
  > "For each parameter in the fit its posterior distribution determines the fitting error, after correcting for auto-correlation in the Markov chain." (3.1 Source extraction and characterization)
   - validation: _not stated_
3. **Determine detection threshold via simulations**: Insert five sources into source-removed maps, 16 times per map (7,400 sources), rerun extraction; measure recovered and spurious fractions  
  > "This process is repeated 16 times per map. Thus, in total we insert 7,400 sources into the 88 ALMA maps." (3.2 Source extraction efficiency and flux recovery)
   - parameter: 3.5 sigma limit: ~99% recovered, ~1.6% spurious  
  > "the source extraction recovers $\sim$ 99% of all $>$ 3.5$\sigma$ sources, while a sample selected above this threshold contains only $\sim$ 1.6% spurious detections" (3.2 Source extraction efficiency and flux recovery)
   - fitting: _not stated_
   - validation: Compared summed ALMA fluxes weighted by LABOCA beam with W09 deboosted fluxes  
  > "the resulting median ALMA/LABOCA flux density ratio and bootstrap error is 0.83$^{+0.09}_{-0.04}$" (3.2 Source extraction efficiency and flux recovery)
4. **Derive differential and cumulative counts**: Per-source probability p=2-f_recovered-f_spurious, summed per flux bin and normalised by effective area; 1000 flux resamples, standard deviation added in quadrature to Poisson error  
  > "derive the counts for 1,000 resamples" (4.1 Derivation of ALMA 870 um source counts)
   - parameter: A_ALMA = (88/126) x 0.35 deg^2  
  > "where $N_{\rm{maps}}({\rm ALMA})=$ 88 is the number of ALMA maps used in this study, $A_{\rm{LESS}}=$ 0.35 deg$^2$" (4.1 Derivation of ALMA 870 um source counts)
   - assumption: Gaussian flux errors  
  > "We thereby assume that the individual error distributions are Gaussian" (4.1 Derivation of ALMA 870 um source counts)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit broken power law**: Double power law with break fixed at 8 mJy; parameter errors by bootstrapping over resamples  
  > "we choose to fix the break point at 8 mJy." (4.2 The absence of the bright SMG population)
   - fitting: Parametric fit to differential counts above LESS limit; bootstrap errors  
  > "The uncertainty range for each parameter is thereby derived by bootstrapping over the parametric fits to all our resamples." (4.1 Derivation of ALMA 870 um source counts)
   - validation: _not stated_
6. **Infer SFR and gas-mass limits**: Absence of >9 mJy SMGs implies SFR limit ~1e3 Msun/yr; gas mass limit via free-fall time ~50 Myr  
  > "For a free-fall time of $\sim$ 50 Myrs as found by (cite: KENN98) for local starbursts, the implied cold gas mass limit is $\mathrel{\raise 0.35ex\hbox{$\scriptstyle <$}\kern-0.6em\lower 0.40ex\hbox{{$\scriptstyle \sim$}}}$ $5 \times 10^{10}$ M$_\odot$." (4.2 The absence of the bright SMG population)
   - assumption: Salpeter IMF; z>1  
  > "(for a (cite: SALP55) IMF)" (4.2 The absence of the bright SMG population)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data processing and imaging  
  > "The data were processed with the Common Astronomy Software Application" (Observations and calibration)
- **IDL source extraction software** : peak finding and MH-MCMC Gaussian fitting  
  > "Our IDL-implemented source extraction software first identifies individual signal peaks above a 2.5-$\sigma$ threshold" (3.1 Source extraction and characterization)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of >3.5 sigma SMGs in 88 maps | 99 | not stated | sources | 3 | In total we detect 99 individual SMGs at $>$ 3.5 $\sigma$ in the 88 maps used. |
| Median ALMA/LABOCA flux ratio (3.5 sigma) | 0.83 | +0.09/-0.04 | dimensionless | 3 | the resulting median ALMA/LABOCA flux density ratio and bootstrap error is 0.83$^{+0.09}_{-0.04}$ |
| Median ALMA/LABOCA flux ratio (3 sigma) | 0.97 | +0.07/-0.04 | dimensionless | 3 | results in a median flux ratio of 0.97$^{+0.07}_{-0.04}$ |
| Broken power-law faint-end slope alpha | 2.0 | +0.5/-0.4 | dimensionless | 5 | $1208^{+902}_{-993}$ / 8 / $2.0^{+0.5}_{-0.4}$ / $6.9^{+2.8}_{-2.3}$ |
| Broken power-law bright-end slope beta | 6.9 | +2.8/-2.3 | dimensionless | 5 | $1208^{+902}_{-993}$ / 8 / $2.0^{+0.5}_{-0.4}$ / $6.9^{+2.8}_{-2.3}$ |
| Normalisation N* | 1208 | +902/-993 | mJy^-1 deg^-2 | 5 | $1208^{+902}_{-993}$ |
| Cumulative counts N(>4.2 mJy) | 167.3 | 28.6 | deg^-2 | 4 | / $4.2$ / 167.3 $~(28.6)$ / |

## Qualitative findings

- No ALMA SMG above ~9 mJy despite twelve LESS sources >9 mJy; brightest sources split into multiple fainter SMGs  
  > "None of our maps detect an SMG with a flux $\mathrel{\raise 0.35ex\hbox{$\scriptstyle >$}\kern-0.6em\lower 0.40ex\hbox{{$\scriptstyle \sim$}}}$ 9 mJy despite twelve sources with 870-$\mu$m fluxes $>$ 9 mJy in the LESS survey." (4.2 The absence of the bright SMG population)

## Claim tuples

- H: Single-dish counts are strongly biased by blending | E: Count SMGs in 88 ALMA maps and compare with LESS and SHADES | R: Counts broadly agree with single-dish at intermediate flux but show a deficit above ~8 mJy | F: Bulk of sources are not blends, but bright sources (>~9 mJy) are multiples | **supported**
- H: There is a maximum SFR for SMGs | E: Interpret absence of bright SMGs | R: SFR <~1e3 Msun/yr; gas mass >5e10 Msun space density <1e-5 Mpc^-3 | F: Natural limit to SMG SFR | **partially**

## Reasoning

- Why this data: ALMA at the same 870 um wavelength as LABOCA enables direct flux comparison and high resolution  
  > "This choice of observing frequency enables a direct comparison to the flux densities of the submillimetre sources measured in the original LABOCA survey." (Observations and calibration)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Counts below the LESS flux limit are biased because fields were targeted near brighter sources  
  > "Below the LESS flux limit the source counts derived from our ALMA maps must be considered biased" (4.1 Derivation of ALMA 870 um source counts)
- Caveat (inferred, ours): Resolved-out extended emission or sub-threshold SMGs could explain flux shortfall
- Caveat (inferred, ours): Break point fixed by hand at 8 mJy with very large parameter uncertainties
- Caveat (inferred, ours): Area scaling assumes uniform sensitivity across the primary beam

## Reproducibility

- Data public (paper): Programme ID given; public status not stated in the paper  
  > "The ALMA observations were carried out under program ADS/JAO.ALMA#2011.0.00294.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and imaging recipe (in H13)
- Missing: Source extraction code
- Missing: f_recovered/f_spurious parametrisations
- Missing: Exact flux bins
- Data volume (inferred): ~10-50 GB (Cycle 0, 8 MSs, 122 short fields)
- Score (inferred): 3/5, Counts method is clear and data public in archive, but calibration, imaging and extraction code details are deferred to H13.
- Rediscovery candidate: no, Recipe depends on an unreleased extraction code and H13 for calibration details.

## Links

- Method: Condon 1997 (cite: COND97) (Error recipes for elliptical Gaussian fits)
- Companion: Hodge et al. 2013 (cite: HODG13) (Data, calibration, imaging and full SMG catalogue)
- Companion: Weiss et al. 2009 (cite: WEIS09) (LESS parent survey)
- Related: LESS (LABOCA ECDFS Submillimetre Survey)
- Related: SHADES

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 38,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
