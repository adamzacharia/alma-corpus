# Multiphase Gas Flows in the Nearby Seyfert Galaxy ESO428-G014. Paper I

`2020ApJ...890...29F` | The Astrophysical Journal 2020 | first author: Feruglio, C. | arXiv: 1904.01483 | DOI: 10.3847/1538-4357/ab67bd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How are the molecular gas distribution, kinematics, inflow and outflow in the Compton-thick Seyfert ESO428-G14 related to its hard X-ray emission and warm H2?  
  > "ALMA observations of molecular gas tracers with high enough angular resolution have the potential to shed light on the cold gas and dust component in the host galaxy and in the inner nuclear region." (Introduction)
- Target **ESO428-G14**: coordinates _not stated_; z/distance D~23.3 Mpc (112 pc/arcsec)  
  > "D$\sim$23.3 Mpc, NED; which corresponds to a physical scale of 112 pc/arcsec" (Introduction); distance from NED  
  > "D$\sim$23.3 Mpc, NED; which corresponds to a physical scale of 112 pc/arcsec" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00086.S
- bands: Band 6  
  > "These are band 6 observations acquired with the 12 m array during May 2016" (2.1 ALMA)
- frequencies and spectral setup: 228-232 and 242.6-246.6 GHz; four spectral windows; max spectral resolution 2.5 km/s  
  > "in the frequency ranges 228-232 and 242.6-246.6 GHz, which cover the CO(2-1) line and the underlying 1.3 mm continuum." (2.1 ALMA); "The data have maximum spectral resolution of 2.5 km/s." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "These are band 6 observations acquired with the 12 m array during May 2016" (2.1 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.76x0.69 arcsec continuum; 0.8x0.67 arcsec CO(2-1)  
  > "we obtain a synthesised beam of $0.76\times0.69$ arcsec$^2$ at a $\rm PA= 32$ deg." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 0.027 mJy/beam continuum; 1.25 mJy/beam per 2.5 km/s channel  
  > "The reached r.m.s. noise in the clean map is 0.027 mJy/beam in the continuum in the aggregated bandwidth." (2.1 ALMA); "reaching a r.m.s. noise level of 1.25 mJy/beam in 2.5 km s$^{-1}$ wide channels after cleaning" (2.1 ALMA)
- time on source: 29 minutes including overheads  
  > "Observation time, including overheads, was 29 minutes." (2.1 ALMA)
- observing dates: May 2016  
  > "These are band 6 observations acquired with the 12 m array during May 2016" (2.1 ALMA)
- pi or archival as stated: archival data  
  > "We retrieved data of ESO428-G14 from the ALMA archive (program ID 2015.1.00086.S)." (2.1 ALMA)
- Line: CO J=2-1 (not stated)
- Other facility **Chandra**: archival X-ray data, as analyzed in Paper III  
  > "We also used archival Chandra data, as analyzed in Paper III." (2 Data and Analysis)
- Other facility **MUSE@VLT**: [OIII] 5007 velocity map  
  > "We analysed MUSE@VLT archival data of ESO428-G14." (2.2 MUSE and SINFONI)
- Other facility **SINFONI@VLT**: H2 1-0 S(1) 2.12 um map  
  > "to obtain a map of the $\rm H_2$ 1$-$0 S(1) emission line at 2.12 $\mu$m" (2.2 MUSE and SINFONI)
- External data: Inclination first guess from minor/major axis ratio  
  > "the inclination of the disk $i=58$ deg, derived from the minor/major axis ratio (NED)" (3.1 Circumnuclear region) [from NED]
- External data: AGN bolometric luminosity 4.1e43 erg/s  
  > "intrinsic bolometric luminosity $\rm L_{bol, AGN}=4.1\times 10^{43}~erg/s$ (Levenson et al. 2006)" (Introduction) [from Levenson et al. 2006]

## Processing

### Calibration

- pipeline or manual: calibrated measurement set created under CASA  
  > "We created the calibrated measurement set under software CASA (McMullin et al. 2007)." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: GILDAS Mapping, mx clean  
  > "we imaged the data using Mapping (Guilloteau & Lucas 2000)" (2.1 ALMA)
- deconvolver: mx; MRC (Wakker & Schwarz 1988) check; threshold 0.5 rms  
  > "We also deconvolved using the `MRC` cleaning algorithm (Wakker & Schwarz 1988) to highlight multi scale emission." (2.1 ALMA)
- weighting robust: natural weighting; Robust weighting for high-res cube (value not given)  
  > "We then imaged the continuum visibilities by adopting a natural weighting scheme" (2.1 ALMA); "we imaged and de-convolved applying Robust weighting within GILDAS" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction with uv-subtract in GILDAS  
  > "we subtracted the continuum in the *uv-plane* from the visibility set using the task *uv-subtract* within GILDAS." (2.1 ALMA)
- line free channels: exclude CO(2-1) sky frequency +/-300 km/s  
  > "excluding the range set by the CO(2-1) sky frequency plus/minus 300 km/s" (2.1 ALMA)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.8x0.67 arcsec PA -59; Robust 0.57x0.53 arcsec PA -55; super-resolution 0.4x0.4 arcsec  
  > "restoring with a clean beam size of $0.4\times0.4$ arcsec, chosen to approximately match the *Chandra* PSF (super-resolution)" (2.1 ALMA)
- final rms: 1.25 mJy/beam per 2.5 km/s (natural); 5.8e-4 Jy/beam (Robust and super-res)  
  > "r.m.s. $5.8\times 10^{-4}$ Jy/beam per 2.5 km/s channel" (2.1 ALMA)

### Inherited from earlier work

- Chandra data analysis  
  > "We also used archival Chandra data, as analyzed in Paper III." (2 Data and Analysis) [from Fabbiano et al 2018b, Paper III]
- SINFONI K-band data description  
  > "We used the K-band data described in May et al. (2018)" (2.2 MUSE and SINFONI) [from May et al. (2018)]
- Outflow rate relation  
  > "(Fiore et al. 2017), where the maximum outflow velocity $\rm v_{max}=v+2\sigma$" (4.3 Feedback) [from Fiore et al. 2017]

### Not stated but needed to reproduce (our reading)

- Robust parameter value for the enhanced-resolution cube
- Cell size and image size
- Mask definitions for clean and the 2 sigma integration regions
- 3DBarolo parameters (rings, free parameters, ring widths, mask, centre)
- Details of the line-width and v_max used for outflow mass and rate, and R_of
- How L'CO to H2 conversion and N(H2) were computed (beam area, region)
- Details of FIR/SFR conversion from the M82 SED
- Primary beam correction
- Which CASA version and calibration (archive scripts or manual)
- Reason for alpha_CO=0.8 in outflow versus 3.2 elsewhere

## Analysis recipe

1. **Image continuum and CO cube**: Convert calibrated MS to GILDAS uv table; average line-free spws for continuum; uv-subtract; natural-weighted mx clean; also Robust and super-resolution cubes  
  > "We then converted it into a visibility table in GILDAS format, and we imaged the data using Mapping (Guilloteau & Lucas 2000)." (2.1 ALMA)
   - software: CASA, GILDAS Mapping
   - parameter: clean threshold 0.5 times rms  
  > "produced a clean cube by using the `mx` cleaning algorithm down to a detection threshold 0.5 times the r.m.s. noise" (2.1 ALMA)
   - fitting: _not stated_
   - validation: mx and MRC give consistent results; super-resolution fluxes agree within 15-20% with Robust  
  > "We obtain consistent results between `mx` and `MRC`." (2.1 ALMA)
2. **Measure fluxes, CO luminosity and gas mass**: Integrate flux above 2 sigma; convert to L'CO and M(H2) assuming thermalised lines  
  > "By assuming that the CO lines are thermalised, and adopting a luminosity-to-mass conversion factor" (3.1 Circumnuclear region)
   - assumption: alpha_CO=3.2 (0.8 for outflow); CO thermalised; D=23.3 Mpc  
  > "adopting a luminosity-to-mass conversion factor $\rm \alpha_{CO}=3.2~ M_{\odot}~ K^{-1}~(km/s^{-1})~ pc^2$" (3.1 Circumnuclear region)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model disk kinematics and derive dynamical mass**: Fit inclined rotating disk with 3DBarolo; residual cube from data minus model; Mdyn=R v^2/G  
  > "We used the $\rm ^{3D}BAROLO$ code (Di Teodoro & Fraternali 2015) to model the CO(2-1) kinematics of ESO428-G14 with an inclined rotating disk model." (3.1 Circumnuclear region)
   - software: 3DBarolo
   - parameter: initial PA=35 deg, i=58 deg  
  > "we input the PA of the observed velocity gradient, $35$ deg, and the inclination of the disk $i=58$ deg" (3.1 Circumnuclear region)
   - fitting: 3DBarolo disk fit; priors not stated  
  > "We used the $\rm ^{3D}BAROLO$ code (Di Teodoro & Fraternali 2015) to model the CO(2-1) kinematics of ESO428-G14 with an inclined rotating disk model." (Results, Circumnuclear region)
   - validation: _not stated_
4. **Characterise outflow and inflow**: Extract residual-cube spectra, fit Gaussians; outflow rate = 3 M v_max/R with v_max=v+2sigma; inflow rate = v M/R_in  
  > "We derive the outflow rate through the relation" (4.3 Feedback)
   - parameter: R_in=100 pc, v=50 km/s  
  > "where $R_{in}=100$ pc and $v_{max,R_{in}}=50$ km/s" (4.2 Feeding)
   - fitting: Gaussian fits to spectra  
  > "By fitting the spectra with Gaussian functions" (3.1 Circumnuclear region)
   - validation: _not stated_

## Software

- **CASA** : calibrated measurement set  
  > "We created the calibrated measurement set under software CASA (McMullin et al. 2007)." (2.1 ALMA)
- **GILDAS (Mapping)** : imaging, cleaning, uv-subtract  
  > "we imaged the data using Mapping (Guilloteau & Lucas 2000)" (2.1 ALMA)
- **3DBarolo** : rotating disk modelling  
  > "We used the $\rm ^{3D}BAROLO$ code (Di Teodoro & Fraternali 2015)" (3.1 Circumnuclear region)
- **CubExtractor (CubeBKGSub, CubEx, Cub2Im)** : MUSE [OIII] continuum subtraction, mask and moment 1  
  > "Then we used *CubEx* and *Cub2Im* to create a 3D mask and the first moment of the \[OIII\] flux distribution." (2.2 MUSE and SINFONI)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm continuum flux density | 3.10 | 0.03 | mJy | 2 | $\rm S_{1.3mm}=3.10\pm0.03$ mJy |
| CO(2-1) integrated flux | 63.3 | 0.1 | Jy km/s | 2 | $\rm S_{CO}=63.3\pm0.1$ Jy km/s |
| Molecular gas mass within ~1 kpc | 6.7e7 (alpha_CO/3.2) | not stated | Msun | 2 | $\rm M(H_2)=6.7\times10^7~(\alpha_{CO}/3.2)~M_{\odot}$ |
| Disk inclination | 57 | 5 | deg | 3 | $i=57\pm5$ deg |
| Circular velocity | 135 | 5 | km/s | 3 | $v_{rot}=135\pm5$ km/s |
| Dynamical mass within ~1 kpc | 5e9 | not stated | Msun | 3 | $M_{dyn }=R \times v_{rot}^2/G=5\times 10^9~\rm M_{\odot}$ |
| Inflow rate | 2 (alpha_CO/3.2) | not stated | Msun/yr | 4 | $\rm \dot M_{in}=v_{max,R_{in}}\times M(H_{2})/R_{in}= 2 ~  (\alpha_{CO}/3.2)~M_{\odot}/yr$ |
| Molecular outflow rate | 0.8 (alpha_CO/0.8) | not stated | Msun/yr | 4 | $\rm \dot M_{of}\approx0.8~(\alpha_{CO}/0.8)~M_{\odot}/yr$ |
| N(H2) in inner bar | 2e23 | not stated | cm^-2 | 2 | $\rm N(H_2) \approx 2\times10^{23}~ cm^{-2}$ |

## Qualitative findings

- CO cavity coincident with hard X-ray emission is filled with warm H2  
  > "The hard X-ray emitting CO cavity is filled with warm molecular gas, traced by the 2.12 $\mu$m $\rm H_2$ emission line." (5 Conclusions)

## Claim tuples

- H: Does the nuclear molecular gas show inflow towards the AGN? | E: PV diagrams and residuals from 3DBarolo disk model with enhanced resolution cube | R: Velocity up to -130 and 150 km/s in inner ~100 pc, deviating from rotation | F: Kinematics consistent with inflow or inner bar that overlaps the Compton-thick region | **supported**
- H: Is there a molecular outflow? | E: Residual cube spectra Gaussian fits and outflow rate formula | R: Bi-conical residuals to ~700 pc; outflow rate ~0.8 Msun/yr | F: Bi-conical molecular outflow detected, with warm H2 tracing inner part | **supported**
- H: Does hard X-ray emission arise from scattering by dense clouds? | E: Compare CO, H2 and Chandra maps | R: X-ray region is CO-deprived but filled with warm H2 | F: Supports scattering from warm molecular gas | **partially**

## Reasoning

- Why this data: High-resolution archival CO and continuum data could shed light on cold gas near the AGN  
  > "ALMA observations of molecular gas tracers with high enough angular resolution have the potential to shed light on the cold gas and dust component" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Flux filtered by the interferometer on large scales is hard to quantify  
  > "it is difficult to exactly quantify the fraction of flux which may have been filtered out by the interferometer on large scales." (4.1 Molecular disk)
- Limitation (authors): N(H2) is a lower limit due to beam dilution and depends on alpha_CO  
  > "This $\rm N(H_2)$ is a lower limit of the true column density due to beam dilution." (4.2 Feeding)
- Caveat (inferred, ours): Outflow separated from disk rotation is hard where they overlap; no uncertainties on outflow rate
- Caveat (inferred, ours): Different alpha_CO for outflow (0.8) and disk (3.2) with little justification
- Caveat (inferred, ours): Super-resolution imaging may bias nuclear morphology
- Caveat (inferred, ours): Short 29 min dataset limits S/N
- Caveat (inferred, ours): Inflow versus bar-driven motion not distinguished

## Reproducibility

- Data public (paper): Public ALMA archive data  
  > "we have checked the ALMA archive and found public data" (Introduction)
- Products in archive: _not stated_
- Missing: Full 3DBarolo configuration
- Missing: Robust weighting value and image geometry
- Missing: Region masks for spectra extraction
- Missing: SFR and FIR conversion details
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public data and GILDAS/3DBarolo recipe, but many parameters are unspecified.
- Rediscovery candidate: no, Key analysis parameters are incomplete and mass/outflow derivation is loosely specified.

## Links

- Method: Di Teodoro & Fraternali 2015 (3DBarolo)
- Method: Fiore et al. 2017 (outflow rate relation)
- Method: Wakker & Schwarz 1988 (MRC deconvolution)
- Companion: Fabbiano et al. 2018b, Paper III (Chandra data analysis)
- Companion: May et al. 2018 (SINFONI data and outflow)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 74,
  "stated": 47,
  "rate": 0.635
 },
 "evidence_ok": true
}
```
