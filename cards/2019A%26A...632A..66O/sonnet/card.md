# ALMA observations of PKS 1549-79: a case of feeding and feedback in a young radio quasar

`2019A&A...632A..66O` | Astronomy and Astrophysics 2019 | first author: Oosterloo, Tom | arXiv: 1910.07865 | DOI: 10.1051/0004-6361/201936248

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: How are accretion and outflow of molecular gas distributed in the young radio quasar PKS 1549-79, and what drives the outflow?  
  > "Thus, in PKS 1549$-$79 we see the co-existence of accretion and the ejection of gas." (abstract)
- Target **PKS 1549-79**: coordinates _not stated_; z/distance z = 0.1525; 1 arcsec = 2.67 kpc (H0=70, flat, OmegaM=0.3)  
  > "PKS 1549$-$79, an object where the AGN is in the crucial early phases of its evolution" (Introduction); "one of the closest ($z=0.1525$) examples of a young, radio-loud quasar" (Introduction); distance from adopted cosmology  
  > "PKS 1549$-$79, an object where the AGN is in the crucial early phases of its evolution" (Introduction); "one of the closest ($z=0.1525$) examples of a young, radio-loud quasar" (Introduction)

## Data provenance

- ALMA projects: 2017.1.01571.S
- bands: Band 3 (CO(1-0)) and Band 7 (CO(3-2))  
  > "The observations were done in Band 3 making use of the correlator in Frequency Division Mode." (2.1 Observations of CO(1-0) and 3-mm continuum); "The observations were done in Band 7, again making use of the correlator in Frequency Division Mode." (2.2 Observations of CO(3-2) and 1-mm continuum)
- frequencies and spectral setup: CO(1-0): 1.875 GHz bandwidth, 1920 channels, native 3.0 km/s; CO(3-2) same setup, ~1.0 km/s  
  > "The total bandwidth used was 1.875 GHz, corresponding to 5625 $\,$km$\,$s$^{-1}$ using 1920 channels" (2.1 Observations of CO(1-0) and 3-mm continuum)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-10 (CO(1-0)); C43-5 (CO(3-2))  
  > "using Atacama Large Millimeter/submillimeter Array (ALMA) in configuration C43-10" (2.1 Observations of CO(1-0) and 3-mm continuum); "using ALMA in configuration C43-5" (2.2 Observations of CO(3-2) and 1-mm continuum)
- baselines: CO(1-0): 35 kλ to ~5 Mλ; CO(3-2): 15 kλ to 1 Mλ  
  > "the shortest baseline being 35 k$\lambda$ and a maximum baseline of almost 5 M$\lambda$" (2.1 Observations of CO(1-0) and 3-mm continuum); "the shortest baseline being 15 k$\lambda$ and a maximum baseline of 1 M$\lambda$" (2.2 Observations of CO(3-2) and 1-mm continuum)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: CO(1-0): 6804 s in 3 sessions; CO(3-2): 0.75 hr  
  > "resulting in a total on-source time of 6804 sec" (2.1 Observations of CO(1-0) and 3-mm continuum); "The total on-source observing time was 0.75 hr." (2.2 Observations of CO(3-2) and 1-mm continuum)
- observing dates: CO(1-0): Oct 8 and 15, 2017; CO(3-2): Sep 20, 2018  
  > "two on Oct 8, 2017 and one on Oct 15, 2017" (2.1 Observations of CO(1-0) and 3-mm continuum); "in a single observing session on Sep 20, 2018" (2.2 Observations of CO(3-2) and 1-mm continuum)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (not stated)
- Line: CO 3-2 (not stated)
- Other facility **Australian LBA (VLBI, 2.3 GHz)**: 2.3-GHz VLBI image of the radio jet (project V235, June 2007)  
  > "PKS 1549$-$79 was observed at 2.3 GHz in June 2007 (project V235) using the Australian Long Baseline Array (LBA)" (3 VLBI observations)
- External data: HST [O III] image of the ionised outflow  
  > "the [O III] outflow seen in the HST image of (cite: Batcheldor07)" (7.2 Possible scenarios for the outflow) [from (cite: Batcheldor07)]
- External data: Earlier 2.3-GHz VLBI image (1988-1992)  
  > "compared our VLBI image with the 2.3 GHz VLBI image presented in (cite: Holt06)" (5.1 The structure of the radio continuum) [from (cite: Holt06)]
- External data: Bolometric luminosity and ionised outflow rate  
  > "(cite: Holt06) estimated the bolometric luminosity of PKS 1549$-$79 to be between $9\times 10^{45}$ $\,$erg$\,$s$^{-1}$ and $4 \times 10^{47}$" (4.5 The molecular outflow) [from (cite: Holt06)]

## Processing

### Calibration

- pipeline or manual: Initial CASA calibration with observatory scripts; extra bandpass and self-cal in MIRIAD  
  > "These calibrated $uv$ data were exported to MIRIAD (cite: Sault95) which was used to perform additional bandpass- and self calibration" (2.1 Observations of CO(1-0) and 3-mm continuum)
- casa version: CASA v5.1.1  
  > "The initial calibration was done in CASA (v5.1.1; (cite: McMullin07))" (2.1 Observations of CO(1-0) and 3-mm continuum)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1617-5848 (CO(1-0)); J1427-4206 (CO(3-2))  
  > "The flux calibration was done using scans on the source J1617–5848." (2.1 Observations of CO(1-0) and 3-mm continuum); "The flux calibration was done using observations of J1427–4206." (2.2 Observations of CO(3-2) and 1-mm continuum)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration in MIRIAD; time-variable bandpass from phase calibrator J1617-7717 for CO(1-0)  
  > "we used the scans of the phase calibrator J1617–7717 (which has a flux density of 2.9 Jy) that were interleaved with the scans on PKS 1549$-$79 to derive a time-variable bandpass calibration" (2.1 Observations of CO(1-0) and 3-mm continuum)

### Imaging

- task: Continuum subtraction in image plane, imaging and cleaning in MIRIAD  
  > "All further reduction steps (continuum subtraction in the image plane, imaging, cleaning) were also done in MIRIAD." (2.1 Observations of CO(1-0) and 3-mm continuum)
- deconvolver: _not stated_
- weighting robust: Natural weighting for low-noise cube; uniform for 100 GHz continuum  
  > "we produced a data cube using natural weighting to obtain the lowest noise level" (2.1 Observations of CO(1-0) and 3-mm continuum); "at full spatial resolution using uniform weighting with a resulting beam of 0.047$''$ $\times$ 0.026$''$" (2.1 Observations of CO(1-0) and 3-mm continuum)
- uv taper: Tapering to 0.167x0.126 arcsec (large-scale cube) and to match CO(3-2) beam; taper values not stated  
  > "we also made a cube with lower spatial resolution by tapering the data." (2.1 Observations of CO(1-0) and 3-mm continuum)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Super-resolved images from clean model components smoothed with 0.01" (100 GHz) and 0.05" (300 GHz) Gaussians  
  > "we have smoothed the model components for presentation purposes with a Gaussian with a resolution of 0.01$''$ corresponding to 27 pc" (2.1 Observations of CO(1-0) and 3-mm continuum)
- final beam: CO(1-0) 0.09x0.055 (natural), 0.167x0.126 (taper); CO(3-2) 0.31x0.16; 100 GHz cont 0.047x0.026; 300 GHz cont 0.29x0.13  
  > "| CO(3-2)   |           | 0.31   | 0.16   | –22.2    | 60                   | 0.24              |                         |   |" (Table 1 obs)
- final rms: CO(1-0) 0.085 mJy/beam at 120 km/s; CO(3-2) 0.24 mJy/beam at 60 km/s; 100 GHz continuum 85 µJy/beam; 300 GHz continuum 0.25 mJy/beam  
  > "The noise of the cube used is 0.24 mJy beam$^{-1}$(for a velocity resolution of 60 $\,$km$\,$s$^{-1}$)." (2.2 Observations of CO(3-2) and 1-mm continuum)

### Inherited from earlier work

- Reduction of CO(3-2) follows that of CO(1-0)  
  > "The data reduction followed a very similar path as described for the CO(1-0)" (2.2 Observations of CO(3-2) and 1-mm continuum) [from Section 2.1 of this paper]
- Flux integral to mass uses CO conversion factors of 4.6 (tails) and 0.3 K km/s pc2 (centre)  
  > "For a conversion factor of 0.3 K $\,$km$\,$s$^{-1}$pc$^2$ representative of such conditions (cite: Bolatto13)" (4.4 The molecular gas masses) [from (cite: Bolatto13)]
- Thin-shell outflow rate Mdot = M V / R  
  > "We use the time-average thin-shell approach $\dot{M} = M_{\rm out}V_{\rm out}/R_{\rm out}$ ((cite: Rupke05))" (4.5 The molecular outflow) [from (cite: Rupke05)]

### Not stated but needed to reproduce (our reading)

- Robust values, taper parameters, cell and image sizes for MIRIAD imaging
- Clean masks and thresholds
- Line-free channels for continuum subtraction
- Self-calibration solution intervals for ALMA data
- Exact bandpass calibration procedure in MIRIAD
- Target coordinates
- Outflow radius used (120 pc vs 0.045") and exact mass-to-rate arithmetic
- Spectral index fitting procedure and flux uncertainties

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA calibration scripts, then MIRIAD bandpass/self-cal, imaging with various weightings and velocity resolutions  
  > "a number of cubes were made, adopting various weighting schemes and velocity resolutions in order to explore the optimum" (2.1 Observations of CO(1-0) and 3-mm continuum)
   - software: CASA, MIRIAD
   - assumption: z = 0.1525 for de-redshifting  
  > "All cubes were de-redshifted assuming a redshift of $z = 0.1525$." (2.1 Observations of CO(1-0) and 3-mm continuum)
   - fitting: _not stated_
   - validation: Super-resolved ALMA image compared with VLBI image  
  > "This very high resolution image compares very well with the 2.3-GHz VLBI image" (2.1 Observations of CO(1-0) and 3-mm continuum)
2. **CO(3-2)/CO(1-0) line ratio**: Matched-resolution cubes; N-S pv slices averaged over 0.375" in E-W; ratio in K where CO(1-0) > 0.4 K  
  > "The line ratio was only computed for those pixels where $S_{\rm CO(1-0)} > 0.4$ K." (4.3 Line ratios)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
3. **Molecular gas masses**: Integrate CO(1-0) flux of tails, disc, broad component; correct for overlap; apply conversion factors  
  > "The masses of the different components in the molecular gas were estimated from the CO(1-0) cube." (4.4 The molecular gas masses)
   - assumption: Conversion 4.6 K km/s pc2 for tails; 0.3 for central disc and broad component (optically thin)  
  > "For the extended tails we used a standard conversion of 4.6 K $\,$km$\,$s$^{-1}$ pc$^2$" (4.4 The molecular gas masses)
   - fitting: _not stated_
   - validation: Total H2 mass compared with FIR-based estimate; column density compared with X-ray and optical values  
  > "the total H$_2$ mass derived from our observations is close to the $6.7 \times 10^9$ $M_\odot$ estimated using the far-IR luminosity" (4.4 The molecular gas masses)
4. **Outflow rate and power**: Thin-shell Mdot = M V/R; kinetic power from Mdot/2 (v^2+3σ^2)  
  > "we assume an outflow velocity of 600 $\,$km$\,$s$^{-1}$. Using these numbers, we find the outflow rate to be about 650 $M_\odot$ yr$^{-1}$." (4.5 The molecular outflow)
   - assumption: v = 600 km/s, sigma = 510 km/s  
  > "we assume $v = 600$$\,$km$\,$s$^{-1}$ and $\sigma = 510$ $\,$km$\,$s$^{-1}$" (4.5 The molecular outflow)
   - fitting: _not stated_
   - validation: _not stated_
5. **Continuum flux densities and spectral indices**: Separate core and jet using VLBI and super-resolved ALMA images; indices between 2.3, 100, 300 GHz  
  > "using the VLBI- and the super-resolved ALMA data, we can separate the emission of the core region (including the inner jet and the counter jet) from that of the more extended jet" (5.2 Spectral index)
   - software: AIPS, Difmap
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: initial ALMA calibration  
  > "The initial calibration was done in CASA (v5.1.1; (cite: McMullin07))" (2.1 Observations of CO(1-0) and 3-mm continuum)
- **MIRIAD** : additional bandpass, self-calibration, continuum subtraction, imaging, cleaning  
  > "All further reduction steps (continuum subtraction in the image plane, imaging, cleaning) were also done in MIRIAD." (2.1 Observations of CO(1-0) and 3-mm continuum)
- **AIPS** : VLBI calibration and imaging  
  > "was performed using standard tasks in AIPS. The data were then independently imaged in both AIPS and Difmap." (3 VLBI observations)
- **Difmap** : VLBI imaging  
  > "The data were then independently imaged in both AIPS and Difmap." (3 VLBI observations)
- **DiFX** : VLBI correlation  
  > "The data were correlated using the DiFX software correlator at Swinburne University" (3 VLBI observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mass outflow rate (molecular) | 650 | lower limit, quite uncertain | Msun/yr | 4 | we find the outflow rate to be about 650 $M_\odot$ yr$^{-1}$ |
| H2 mass of tails | 9.7e9 | not stated | Msun | 3 | This results in an estimate for the H$_2$ mass of the tails of $9.7\times 10^9$ $M_\odot$. |
| H2 mass of broad component | 1.6e8 | not stated | Msun | 3 | the mass in the broad component is $1.6 \times 10^8$ $M_\odot$ and for the central disc $2.6 \times 10^8$ $M_\odot$ |
| H2 mass of central disc | 2.6e8 | not stated | Msun | 3 | the mass in the broad component is $1.6 \times 10^8$ $M_\odot$ and for the central disc $2.6 \times 10^8$ $M_\odot$ |
| Average R31 in core region | 1.25 (max 2.3) | not stated | dimensionless | 2 | The average value in the core region of $R_{\rm 31}$ is 1.25, with a maximum for $R_{\rm 31}$ of 2.3. |
| Spectral index of jet 2.3-100 GHz | -1.15 | not stated | dimensionless | 5 | / Jet / 1.78 / 0.023 / 0.0038 / –1.15 / –1.64 /  /  / |
| Spectral index of core 2.3-100 GHz | -0.57 | not stated | dimensionless | 5 | / Core / 3.02 / 0.354 / 0.147 / –0.57 / –0.80 /  /  / |
| Broad CO(1-0) profile width | ~2300 | not stated | km/s | 0 | CO(1-0) is detected over a very large velocity range, with a total width of about 2300 $\,$km$\,$s$^{-1}$ |
| 100 GHz continuum peak | 350 | rms 85 µJy/beam | mJy/beam | 1 | The peak in the continuum image is 350 mJy at the location of the core |

## Qualitative findings

- Molecular gas shows kpc-scale N-S tails with small velocity gradient (possible inflow), a rotating circumnuclear disc, and a broad central component  
  > "We detect three structures tracing the accretion and the outflow of molecular gas" (abstract)
- Radio structure is similar at 2.3 and 100 GHz; no superluminal motion found over 17 years  
  > "we do not see evidence of superluminal motion to explain the strong asymmetry observed on the hundred-pc scale" (5.1 The structure of the radio continuum)

## Claim tuples

- H: Is a molecular outflow present and where is it? | E: CO(1-0) spectrum at the core | R: Broad ~2300 km/s component unresolved (r<120 pc); rate ≥650 Msun/yr | F: Massive molecular outflow confined to the inner region, suggesting AGN drives it | **supported**
- H: Does the AGN alter gas excitation? | E: CO(3-2)/CO(1-0) ratio | R: R31 averages 1.25 in core, <0.5 in tails | F: Dense, hot gas in the circumnuclear disc | **supported**
- H: Does the outflow follow the Lbol scaling of ionised vs molecular outflows? | E: Compare molecular and ionised outflow rates | R: Warm outflow ~two orders of magnitude less massive | F: No agreement with claimed scaling; radio jet may matter | **supported**
- H: Could the outflow destroy the circumnuclear disc? | E: Disc gas mass divided by outflow rate | R: ~1e5 yr | F: AGN self-regulates accretion, while merger gas may rebuild disc | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting used for lowest noise given low CO(1-0) surface brightness; tapering for large scales  
  > "Given the low surface brightness of the CO(1-0) emission, we produced a data cube using natural weighting to obtain the lowest noise level" (2.1 Observations of CO(1-0) and 3-mm continuum)
- Alternative: Relativistic beaming explanation of jet asymmetry made less compelling by counter-jet detection  
  > "this makes the hypothesis of a the jet being along the line-of-sight less compelling than previously thought" (5.1 The structure of the radio continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow rate is quite uncertain: overlap with disc, conversion factor, velocity and size  
  > "This number is, however, quite uncertain." (4.5 The molecular outflow)
- Limitation (authors): Narrow CO(3-2) bandwidth prevents detecting the broad component  
  > "this is quite likely due to the limited bandwidth of the CO(3-2) data" (4. Results: the molecular gas)
- Caveat (inferred, ours): Conversion factor 0.3 is assumed and drives the masses and outflow rate
- Caveat (inferred, ours): Outflow velocity of 600 km/s and radius are assumed rather than fitted
- Caveat (inferred, ours): Overlap correction between disc and broad component is rough
- Caveat (inferred, ours): Driving mechanism cannot be discriminated
- Caveat (inferred, ours): Core spectral indices may be affected by non-simultaneous variable fluxes

## Reproducibility

- Data public (paper): Project code given in acknowledgements; archive status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01571.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MIRIAD imaging parameters
- Missing: Custom bandpass procedure details
- Missing: Self-cal parameters
- Missing: Line-free channels
- Missing: VLBI data (project V235) availability
- Data volume (inferred): ~100-300 GB raw (four sessions, 1920 channels, long baselines)
- Score (inferred): 3/5, Data identified and key quantities numeric, but imaging details are sparse and the MIRIAD custom processing is not fully specified.
- Rediscovery candidate: no, Recipe lacks imaging and bandpass parameters and the masses depend on assumed conversion factors and subjective overlap corrections.

## Links

- Method: (cite: Rupke05) (thin-shell outflow rate formula)
- Method: (cite: Bolatto13) (CO conversion factor for optically thin gas)
- Companion: (cite: Holt06) (earlier multiwavelength study of PKS 1549-79)
- Companion: Santoro et al. (in prep.) (optical/X-shooter study of the ionised outflow)
- Related: ATCA calibrator monitoring
- Related: GLEAM

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 48,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
