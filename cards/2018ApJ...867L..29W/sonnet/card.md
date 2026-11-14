# Revealing the Environmental Dependence of Molecular Gas Content in a Distant X-Ray Cluster at z = 2.51

`2018ApJ...867L..29W` | The Astrophysical Journal Letters 2018 | first author: Wang, Tao | arXiv: 1810.10558 | DOI: 10.3847/2041-8213/aaeb2c

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: How do the molecular gas content and star formation efficiency of massive star-forming galaxies in the z=2.51 X-ray cluster CLJ1001 depend on their position (accretion state) in the cluster?  
  > "We find a large variety in the gas content of these cluster galaxies, which is correlated with their relative positions (or accretion states), with those closer to the cluster core being increasingly gas-poor." (abstract)
- Target **CLJ1001**: coordinates _not stated_; z/distance z=2.51  
  > "CLJ1001 is estimated to have total mass of $M \sim10^{13.9\pm0.2} M_{\odot}$ and virial radius of $R_{\rm 200c} \sim$ 340 kpc" (Introduction); distance from X-ray cluster identified in Wang et al. 2016 (W16)  
  > "CLJ1001 is estimated to have total mass of $M \sim10^{13.9\pm0.2} M_{\odot}$ and virial radius of $R_{\rm 200c} \sim$ 340 kpc" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00539.S
- bands: JVLA Ka-band (CO(1-0)); ALMA band 3 for CO(3-2) (supporting)  
  > "the observations were carried out in the Ka-band with the D configuration" (2.1 JVLA CO(1-0) observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: JVLA D configuration  
  > "the observations were carried out in the Ka-band with the D configuration" (2.1 JVLA CO(1-0) observations)
- baselines: _not stated_
- angular resolution: ~2.88" x 2.52" (JVLA cube)  
  > "The resulting data cube has synthesized beam size of $\sim2.88^{\prime\prime} \times 2.52^{\prime\prime}$" (2.1 JVLA CO(1-0) observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~33-40 uJy/beam per channel (JVLA)  
  > "with a rms of $\sim 33-40~\mu$Jy beam$^{-1}$ per channel at the phase center." (2.1 JVLA CO(1-0) observations)
- time on source: ~13 hours (JVLA total integration)  
  > "The total integration time is $\sim$13 hours." (2.1 JVLA CO(1-0) observations)
- observing dates: December 2015 (JVLA)  
  > "Our JVLA observations of CLJ1001 were performed in December 2015 under the program 15B-290 (PI: Tao Wang)." (2.1 JVLA CO(1-0) observations)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (not stated)
- Line: CO 3-2 (not stated)
- Other facility **JVLA**: CO(1-0) cubes (main data)  
  > "Our JVLA observations of CLJ1001 were performed in December 2015 under the program 15B-290 (PI: Tao Wang)." (2.1 JVLA CO(1-0) observations)
- Other facility **Subaru/MOIRCS**: Narrow-band Halpha emitter positions  
  > "Here we only use their positions to search for CO(1-0) line emissions." (2.2 Subaru/MOIRCS narrow-band imaging)
- Other facility **ALMA**: 870 um detections for L_IR of five members; band 3 CO(3-2) for velocity ranges  
  > "five cluster members are detected at 870 $\mu$m with ALMA" (4.1 Star formation efficiency)
- External data: Mass-metallicity relation used to get metallicity and alpha_CO  
  > "The same mass-metallicity relation used in (cite: Genzel:2015) is also applied to determine the metallicity for the CO-detected galaxies in our sample" (2.4 Molecular gas masses from CO(1-0)) [from (cite: Genzel:2015)]
- External data: 24 um fluxes  
  > "we derive $L_{IR}$ based on their 24 $\mu$m fluxes (cite: Muzzin:2013a)" (4.1 Star formation efficiency) [from (cite: Muzzin:2013a)]
- External data: 3 GHz radio continuum  
  > "3 GHz (cite: Smolcic:2017) radio continuum" (4.1 Star formation efficiency) [from (cite: Smolcic:2017)]

## Processing

### Calibration

- pipeline or manual: CASA standard pipeline (JVLA data)  
  > "The data were reduced using the Common Astronomy Software Application (CASA) package (cite: McMullin:2007) with a standard pipeline." (2.1 JVLA CO(1-0) observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C147 (JVLA)  
  > "We observed 3C147 for flux calibration during the full observations" (2.1 JVLA CO(1-0) observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "a spectral resolution of 30 km s$^{-1}$ with a natural weighting scheme for imaging" (2.1 JVLA CO(1-0) observations)
- uv taper: _not stated_
- cell size: 0.5 arcsec  
  > "We chose 0.5$^{\prime\prime}$ pixels" (2.1 JVLA CO(1-0) observations)
- image size: _not stated_
- masking: CLEAN threshold of 3 sigma of each cube  
  > "Image deconvolution was performed with a CLEAN threshold of 3$\sigma$ of each cube." (2.1 JVLA CO(1-0) observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to line intensities  
  > "The measured integrated CO(1-0) line intensities, after primary beam correction, are listed in Table" (3.3 Extraction of CO(1-0) emitters)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- alpha_CO determination  
  > "We determine $\alpha_{\rm CO}$  for the cluster galaxy sample following (cite: Genzel:2015) and (cite: Tacconi:2018)." (2.4 Molecular gas masses from CO(1-0)) [from (cite: Genzel:2015); (cite: Tacconi:2018)]
- CO luminosity derivation  
  > "with the CO line luminosity $L_{\mathrm{CO(1-0)}}^{\prime}$ derived following (cite: Solomon:2005)" (2.4 Molecular gas masses from CO(1-0)) [from (cite: Solomon:2005)]
- L_IR of ALMA-detected members and cluster properties  
  > "As shown in W16 (cite: Bussmann:2015), five cluster members are detected at 870 $\mu$m with ALMA" (4.1 Star formation efficiency) [from W16 (Wang et al. 2016), (cite: Bussmann:2015)]

### Not stated but needed to reproduce (our reading)

- ALMA band 3 and 870 um data reduction details (CO(3-2) in preparation)
- SED fitting code and templates details for L_IR
- velocity ranges used for each moment-0 map
- stellar masses and SFR derivation
- cluster velocity dispersion and center values for k_b
- line-free channels/continuum subtraction for JVLA data

## Analysis recipe

1. **Extract CO(1-0) fluxes**: 2-D Gaussian fit with IMFIT to moment-0 maps at fixed positions from HST/F160W or NB images; checked with uv-plane fluxes  
  > "We measured the CO(1-0) line fluxes for each object by running a 2-D Gaussian fit with CASA (IMFIT) on the velocity-integrated (moment-0) map." (3.3 Extraction of CO(1-0) emitters)
   - software: CASA, GILDAS
   - parameter: velocity range chosen to maximize S/N; CO(3-2) used for low S/N  
  > "The velocity range used to create the moment-0 map of each object was determined so to maximize the signal-to-noise of the detection." (3.3 Extraction of CO(1-0) emitters)
   - fitting: _not stated_
   - validation: uv-plane flux measurement with GILDAS gives consistent results  
  > "we have also measured directly their total fluxes in the *uv*-plane with GILDAS[^1], a procedure that gives consistent results." (3.3 Extraction of CO(1-0) emitters)
2. **Derive molecular gas masses**: M(H2)=alpha_CO L'_CO  
  > "through $M(H_{2}) = \alpha_{\rm CO} L_{\rm CO}^{\prime}$" (2.4 Molecular gas masses from CO(1-0))
   - assumption: metallicity from mass-metallicity relation, close to solar; alpha_CO close to Milky Way value  
  > "As a result, the derived $\alpha_{\rm CO}$ is close to the Milky value for this sample" (2.4 Molecular gas masses from CO(1-0))
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive L_IR and SFE**: SED fit for ALMA-detected; otherwise 24 um and 3 GHz with average SED templates and FIR-radio relation; Halpha SFR for ID-12  
  > "by using the average infrared SED templates for galaxies at $z\sim 2.5$ (cite: Schreiber:2018a) and FIR-radio relation (cite: Delhaize:2017)" (4.1 Star formation efficiency)
   - assumption: Chabrier IMF; H0=70, OmegaM=0.3, OmegaL=0.7  
  > "A (cite: Chabrier:2003) initial mass function is adopted to derive stellar masses and SFRs." (Introduction)
   - fitting: _not stated_
   - validation: IR-SED and 3 GHz derived L_IR agree for four of five ALMA-detected sources  
  > "which are in good agreement" (4.1 Star formation efficiency)
4. **Relate gas and SFE to phase-space position**: Compute k_b=(|dv|/sigma_cluster)(R/R200c) and compare mu_gas, SFR, SFE with k_b and distance to MS  
  > "we plot $\mu_{\rm gas}$ versus $k_{b} = (|\Delta v|/\sigma_{\rm cluster}) \times (R/R_{200c})$ for the cluster galaxies." (4.2 Clustercentric radius dependence)
   - assumption: MS relation at z=2.5 from Schreiber et al. 2015  
  > "derived using the MS relation at z=2.5 (cite: Schreiber:2015)" (4.1 Star formation efficiency)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction, imaging, IMFIT  
  > "The data were reduced using the Common Astronomy Software Application (CASA) package (cite: McMullin:2007) with a standard pipeline." (2.1 JVLA CO(1-0) observations)
- **GILDAS** : uv-plane flux check  
  > "we have also measured directly their total fluxes in the *uv*-plane with GILDAS[^1]" (3.3 Extraction of CO(1-0) emitters)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO(1-0) detected members | 14 | not stated | galaxies | 1 | In total 14 H$\alpha$-emitters are detected with S/N $>$ 3 |
| Gas depletion time of central galaxies | ~0.4 | not stated | Gyr | 4 | Their gas depletion time ($t_{\rm dep}$ = 1/SFE) is around $t_{\rm dep} \sim 0.4$Gyrs |
| Cluster dynamical time | ~0.5 | not stated | Gyr | 4 | $t_{\rm dyn} \sim R_{200c}/\sigma_{\rm cluster} \sim 0.5$ Gyr |
| k_b of gas-rich to gas-poor transition | ~0.1 | not stated | dimensionless | 4 | The transition between the gas-rich and -poor populations takes place at around $k_{b} \sim 0.1$. |

## Qualitative findings

- Galaxies near the cluster core are gas-poor, while those in outskirts are gas-rich with large scatter; central galaxies have elevated SFE.  
  > "the galaxies in the cluster center exhibit an elevated star formation efficiency (SFE=SFR/$M_{\rm gas}$) compared to field galaxies" (abstract)

## Claim tuples

- H: Gas content of massive cluster SFGs depends on position in the cluster | E: JVLA CO(1-0) census of 14 members compared with phase-space position k_b | R: mu_gas decreases toward the cluster core; transition at k_b~0.1 | F: Environment rapidly reduces gas content near the core | **supported**
- H: SFR suppression is delayed relative to gas suppression | E: Compare SFE and SFR vs k_b | R: Central galaxies have elevated SFE with t_dep ~0.4 Gyr, comparable to t_dyn | F: Central galaxies will exhaust gas within one orbit and form a passive core by z~2 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Extracting spectra at known member positions yields fainter, higher-fidelity detections than a blind search  
  > "This approach allows us to detect sources with fainter fluxes and with higher fidelity than a blind search." (3.3 Extraction of CO(1-0) emitters)
- How they decided it was enough: _not stated_
- Limitation (authors): Sensitivity drops with radius so only gas-rich systems are detectable at large radii, though the sample is argued to be mass-complete  
  > "only gas-rich systems can be detected at large radii." (4.2 Clustercentric radius dependence)
- Caveat (inferred, ours): The main data are JVLA; ALMA plays only a supporting role
- Caveat (inferred, ours): Small sample from one cluster
- Caveat (inferred, ours): alpha_CO assumed near Milky Way value
- Caveat (inferred, ours): Phase-space interpretation depends on projected positions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA band 3 CO(3-2) analysis (in preparation)
- Missing: L_IR SED fitting details
- Missing: stellar mass catalog details and cluster velocity dispersion
- Missing: Data availability not stated
- Data volume (inferred): ~50-100 GB (JVLA D-config 13 h Ka-band plus ALMA)
- Score (inferred): 3/5, Main JVLA recipe is partly described, but ALMA, SED and many parameters are deferred to other papers.
- Rediscovery candidate: no, Key inputs come from other papers or work in preparation, and the main data are JVLA rather than ALMA.

## Links

- Method: (cite: Genzel:2015); (cite: Tacconi:2018) (alpha_CO prescription)
- Companion: (cite: WangT:2016b) (cluster discovery and earlier data (W16))
- Related: JVLA program 15B-290
- Related: COSMOS
- Related: UltraVista

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.01155.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 39,
  "rate": 0.542
 },
 "evidence_ok": true
}
```
