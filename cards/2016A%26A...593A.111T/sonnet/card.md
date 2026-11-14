# Brown dwarf disks with ALMA: Evidence for truncated dust disks in Ophiuchus

`2016A&A...593A.111T` | Astronomy and Astrophysics 2016 | first author: Testi, L. | arXiv: 1606.06448 | DOI: 10.1051/0004-6361/201628623

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the dust masses and outer structure of disks around young brown dwarfs in rho Oph, and how do they compare with Taurus brown dwarfs and T Tauri disks?  
  > "All 17 young brown dwarfs in our sample were observed at 890 $\mu$m in the continuum at $\sim0.\!^{\prime\prime}5$ angular resolution." (abstract)
- Target **17 Class II brown dwarfs in rho Oph (e.g. ISO-Oph160, ISO-Oph193)**: coordinates RA 16:26-16:28, Dec -24 (Table 1 lists each)  
  > "for the adopted distance D=122 pc" (Disk sizes and surface density profile); "The sample includes 17 spectrally confirmed $\rho$ Oph BDs with infrared excess" (2 The sample); z/distance D=122 pc  
  > "for the adopted distance D=122 pc" (Disk sizes and surface density profile); "The sample includes 17 spectrally confirmed $\rho$ Oph BDs with infrared excess" (2 The sample); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00037.S, 2011.0.00259.S
- bands: Band 7, ~338 GHz (890 um)  
  > "We used the ALMA Band 7 receivers tuned to a frequency of $\sim$338 GHz" (3 Observations and results)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: ~6 GHz  
  > "the total effective bandwidth usable for continuum was approximately 6 GHz" (3 Observations and results)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5"x0.4"  
  > "The full width at half maximum of the synthesized beam is approximately $0.\!^{\prime\prime}5\times 0.\!^{\prime\prime}4$ for all maps." (3 Observations and results)
- max recoverable scale: _not stated_
- sensitivity: chosen to detect ~0.5 Earth masses of dust  
  > "The sensitivity of our observations was chosen to detect $\sim0.5$ M$_\oplus$ of dust." (abstract)
- time on source: 3 min for most; 6 min for six objects  
  > "The total time on source for our targets was three minutes for the majority of the sources" (3 Observations and results)
- observing dates: April 25 and 26, 2014; 35 and 36 antennas  
  > "ALMA observed our sources on April 25 and 26, 2014 with 35 and 36 antennas, respectively." (3 Observations and results)
- pi or archival as stated: _not stated_
- Line: 13CO J=3-2 (not stated)
- External data: Stellar parameters (SpT, Teff, Av, L, M) for sample  
  > "1: Manara et al. (2015); 2: data from Alves de Oliveira et al. (2012) and references therein (see text)" (Table 1) [from Manara et al. (2015); Alves de Oliveira et al. (2012); Muzic et al. (2012); Liu et al. (2015)]
- External data: 850 um fluxes of rho Oph T Tauri stars used for comparison disk masses  
  > "we used the 850 $\mu$m fluxes from" (5.2 Comparison between BDs and TTS disk masses) [from not stated (cite key lost in text)]
- External data: ALMA 890 um Taurus BD data (2M0444+2512, CIDA 1, CFHT Tau4) reanalysed  
  > "the reanalysis of the Taurus BD disks ALMA 890 $\mu$m observations from" (8 Model fits to the structure of Taurus BD disks) [from Ricci et al. 2014 (inferred; cite key lost)]

## Processing

### Calibration

- pipeline or manual: Standard calibration by ESO ALMA Regional Centre  
  > "Standard calibration was performed by the ESO ALMA Regional Centre" (3 Observations and results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Titan was used as flux calibrator" (3 Observations and results)
- flux scale uncertainty: within 5%  
  > "the flux density scale is expected to be accurate within 5%" (3 Observations and results)
- self calibration: not attempted; sources too faint  
  > "None of the sources were sufficiently bright to attempt self-calibration." (3 Observations and results)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Imaging was performed using natural weighting of the visibilities" (3 Observations and results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.5"x0.4"  
  > "The full width at half maximum of the synthesized beam is approximately $0.\!^{\prime\prime}5\times 0.\!^{\prime\prime}4$ for all maps." (3 Observations and results)
- final rms: _not stated_

### Inherited from earlier work

- Visibility-fitting two-layer disk model and MCMC procedure  
  > "Following , we performed a fit to the visibilities using a simple two-layer disk model" (Disk sizes and surface density profile) [from not stated (cite lost; likely Tazzari et al. 2016)]
- Upper limit computation  
  > "(see Barenfeld et al. 2016, submitted)" (3 Observations and results) [from Barenfeld et al. 2016, submitted]
- Dust opacity kappa_890=2 cm2/g  
  > "we adopt a dust opacity $\kappa_{890 \mu m}$=2 cm$^2$/g, as in" (Disk masses) [from not stated (cite lost)]
- Flare reduction factor 3 of two-layer model  
  > "with flare reduced by a factor 3 to match the typical values of the far-infrared excess observed in BDs (Daemgen et al. 2016, submitted)" (Disk sizes and surface density profile) [from Daemgen et al. 2016, submitted]

### Not stated but needed to reproduce (our reading)

- Number of spectral windows and exact frequencies
- CASA version used for imaging and uvmodelfit
- Image size, cell size, and clean parameters
- MCMC walker number, chain length, burn-in
- Which Taurus paper data were reanalysed and their project codes
- Reference for TTS 850 um fluxes and stellar parameters assumptions
- Exact priors ranges for parameters

## Analysis recipe

1. **Image and measure continuum fluxes**: Natural-weighted images; peak flux and rms from images; total flux via uvmodelfit with Gaussian (point source for three faintest)  
  > "we fitted Gaussian sources to the visibilities of all detected sources except for the three fainter ones, for which we used a point source." (3 Observations and results)
   - software: CASA
   - parameter: Upper limits = 3 x rms above measured flux (null if negative)  
  > "computed as three times the rms level above the measured flux (assumed null when negative)" (3 Observations and results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive dust and disk masses**: Optically thin isothermal formula F=kappa B(T) M/D^2 with T=25 (L/Lsun)^0.25 K  
  > "a temperature that depends on the stellar luminosity as $T$=25 (L$_\ast$/L$_\odot$$)^{0.25}$K" (Disk masses)
   - assumption: kappa_890=2 cm2/g; gas-to-dust 100; D=122 pc  
  > "Total (gas+dust) disk mass computed from M$_{dust}$ assuming a gas=to-dust mass ratio of 100." (Table 2)
   - fitting: _not stated_
   - validation: Temperature uncertainty less than factor 2; compared with Herschel-based masses  
  > "(less than a factor 2 in all our objects)" (Disk masses)
3. **Fit visibilities of ISO-Oph160 and ISO-Oph193 for surface density profile**: Two-layer disk radiative model, truncated power law vs exponentially tapered Sigma(R), synthetic 890 um image sampled at observed uv points  
  > "For each model we compute the 890 $\mu$m synthetic image and we sample its Fourier transform at the (u,v) plane location of the observations." (Disk sizes and surface density profile)
   - software: affine-invariant MCMC ensemble sampler
   - parameter: Inner radius 0.1 AU; Sigma0 at R0=10 AU; grain a 10 nm-1 um (q=3.5) surface, 10 nm-1.4 cm (q=3) midplane  
  > "In all cases we adopt an inner radius of 0.1 AU, as the results do not depend on its exact value." (Disk sizes and surface density profile)
   - assumption: Mie opacity; 5.4% silicates, 20.6% carbonaceous, 44% water ice, 30% vacuum; dust-to-gas 1e-2  
  > "5.4% astronomical silicates, 20.6% carbonaceaous material, 44% water ice, and 30% vacuum" (Disk sizes and surface density profile)
   - fitting: Bayesian MCMC, likelihood exp(-chi^2), flat priors; free: Mdisk, two Sigma parameters, inclination, PA, plus two centre-offset nuisance parameters  
  > "We estimate the Bayesian probability using $exp(-\chi^2)$ as likelihood with flat priors." (Disk sizes and surface density profile)
   - validation: Minimum normalized chi2 1.00-1.38; residual images  
  > "the minimum normalized $\chi^2$ range between 1.00 and 1.38" (Disk sizes and surface density profile)
4. **Reanalyse Taurus BD disks**: Same procedure applied to Taurus 890 um data  
  > "We applied the procedure and parameters as described in Sect. [4.2](#s_rad) to derive comparable results" (8 Model fits to the structure of Taurus BD disks)
   - fitting: _not stated_
   - validation: truncated power-law results consistent with earlier study  
  > "The truncated power law parameters from our reanalysis are consistent with previous results" (5.3 Comparison with Taurus BD disks structure)
5. **Compare Mdisk/Mstar of BDs and TTS**: Recomputed TTS masses with same method; Anderson-Darling test between BD and 0.2-1 Msun TTS samples, upper limits treated as measurements  
  > "We performed the Anderson-Darling test[^1] between these two samples and find $\sim$1.6% probability that the two are drawn from the same parent distribution" (5.2 Comparison between BDs and TTS disk masses)
   - software: scipy.stats
   - assumption: TTS L and M from spectral types assuming 1 Myr isochrone  
  > "assuming that all the stars lie on a 1 Myr isocrone" (5.2 Comparison between BDs and TTS disk masses)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : uvmodelfit Gaussian/point-source fits to visibilities  
  > "computed using the CASA task `uvmodelfit`" (3 Observations and results)
- **scipy.stats** : Anderson-Darling test  
  > "We used the `scipy.stats` python implementation of the test" (footnote)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detection fraction | 11/17 (~65%) | not stated | dimensionless | 1 | We detected 11/17 ($\sim 65$%) objects |
| Dust masses of detected disks | ~0.5-6.3 | not stated | Earth masses | 2 | the disk masses are $\sim 0.5- 6.3$ M$_\oplus$ |
| ISO-Oph160 Rc | 24 | +2/-3 | AU | 3 | ISO-Oph160 / $24_{-3}^{+ 2}$ |
| ISO-Oph193 Rout | 22 | +16/-2 | AU | 3 | ISO-Oph193 / $23_{-3}^{+11}$ / $-0.34_{-0.7}^{+ 0.8}$ / $22_{-2}^{+16}$ |
| Anderson-Darling probability same parent distribution | ~1.6% | not stated | % | 5 | find $\sim$1.6% probability that the two are drawn from the same parent distribution |
| ISO-Oph193 total flux | 8.7 | not stated | mJy | 1 | ISO-Oph193 / 7.82$\pm$0.20 / 8.7 / $\sim$0.2 / 4.8 / 1.43 |

## Qualitative findings

- Most BD disks unresolved with size <~24 AU; the two brightest resolved disks have flat Sigma and sharp edge at ~25 AU unlike Taurus BDs  
  > "Both objects have a flat surface density and a sharp cutoff at about" (6 Conclusions and summary)

## Claim tuples

- H: Planet formation is difficult in BD disks | E: Measure dust masses for 17 rho Oph BDs | R: Dust masses 0.5-6 Earth masses | F: Supra-Jupiter companions likely from binary-like formation | **supported**
- H: rho Oph BD disks differ in structure from Taurus BD disks | E: Visibility modelling of two brightest rho Oph disks and reanalysis of Taurus disks | R: Rout ~22 AU with sharp edges vs 136-153 AU in Taurus | F: Environment may cause different disk properties; only ~2.5 sigma | **partially**
- H: BD disks have lower Mdisk/Mstar than TTS disks | E: Anderson-Darling test of rho Oph BDs vs TTS | R: ~1.6% probability of same parent | F: Possible deficit, tentative | **partially**

## Reasoning

- Why this data: Unbiased sample of all confirmed Class II BDs in rho Oph at proposal time  
  > "The sample is unbiased, as it contained all the spectroscopically confirmed Class II BDs at the time of the proposal" (6 Conclusions and summary)
- Why this method: _not stated_
- Alternative: Alternative temperature law T_vdP=22 (L)^0.16 considered; T_A kept as most conservative  
  > "in this paper we have used $T_A$ to compute dust masses" (7 Temperature)
- How they decided it was enough: _not stated_
- Limitation (authors): Samples incomplete and stellar parameters uncertain; identical dust properties across disk assumed  
  > "the stellar parameters of the $\rho$ Oph TTS are very uncertain" (5.2)
- Caveat (inferred, ours): Only two disks resolved; sharp edge may reflect assumed uniform dust properties
- Caveat (inferred, ours): Temperature choice biases masses
- Caveat (inferred, ours): TTS comparison sample heterogeneous with ad hoc stellar parameters

## Reproducibility

- Data public (paper): Project codes given in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00037.S and ADS/JAO.ALMA#2011.0.00259.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MCMC disk-model code not named or released
- Missing: Imaging parameters
- Missing: TTS literature fluxes
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public data and clear mass recipe, but modelling code and imaging details are missing.
- Rediscovery candidate: no, Fluxes and masses are reproducible, but the visibility modelling relies on unnamed in-house code.

## Links

- Method: Tazzari et al. 2016 (likely source of disk modelling method (inferred; cite lost))
- Companion: Barenfeld et al. 2016, submitted (Upper limit method)
- Companion: Daemgen et al. 2016, submitted (Temperature and flaring of BD disks)
- Related: Upper Sco ALMA survey
- Related: Taurus BD ALMA

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 43,
  "rate": 0.573
 },
 "evidence_ok": true
}
```
