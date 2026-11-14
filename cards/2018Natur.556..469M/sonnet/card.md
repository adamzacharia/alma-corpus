# A massive core for a cluster of galaxies at a redshift of 4.3

`2018Natur.556..469M` | Nature 2018 | first author: Miller, T. B. | arXiv: 1804.09231 | DOI: 10.1038/s41586-018-0025-2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Is SPT2349-56 a dense, massive protocluster core of starbursting galaxies at z=4.3, and how does it compare with other protoclusters and models?  
  > "A comparison with other known protoclusters at high redshifts shows that SPT2349-56 is a uniquely massive and dense system that could be building one of the most massive structures in the Universe today." (abstract)
- Target **SPT2349-56**: coordinates southern LABOCA component RA 23:49:42.70, Dec -56:38:23.4  
  > "peak intensity at 21$''$ resolution of 50 mJy/beam for the brighter, southern component (RA 23:49:42.70, DEC -56:38:23.4)" (Methods); "all lying at ***z* = 4.31**" (abstract); z/distance z = 4.304 (mean, biweight)  
  > "peak intensity at 21$''$ resolution of 50 mJy/beam for the brighter, southern component (RA 23:49:42.70, DEC -56:38:23.4)" (Methods); "all lying at ***z* = 4.31**" (abstract); distance from ALMA CO(4-3) and [CII] line redshifts  
  > "peak intensity at 21$''$ resolution of 50 mJy/beam for the brighter, southern component (RA 23:49:42.70, DEC -56:38:23.4)" (Methods); "all lying at ***z* = 4.31**" (abstract)

## Data provenance

- ALMA projects: 2015.1.01543.T, 2016.0.00236.T
- bands: Band 3 (CO(4-3), 86-88 GHz) and Band 7 (276 GHz continuum; [CII] at 358.3 GHz)  
  > "Observations using ALMA Band-3 targeted the CO(4-3) line in SPT2349-56 centred in the lowest frequency of the spectral windows adopted (86-88 GHz)" (ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 3: 36 antennas, baselines 15-704 m; Band 7: 40-2 configuration, 15-459 m, 40 antennas  
  > "The array used 36 antennas with baselines ranging from 15 to 704 m" (ALMA); "in a 40-2 array configuration with baseline lengths of 15-459 m" (ALMA)
- baselines: _not stated_
- angular resolution: ~1'' (Band 3 and Band 7 continuum), ~0.5'' ([CII]), natural weighting  
  > "giving a naturally weighted synthesized beam size of $\sim0.5''$" (ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 3 47 min; Band 7 continuum 22 min; [CII] 14 min  
  > "An on-source integration time of 14 min was obtained" (ALMA); "Data was taken on June 24th, 2016 with a 47 min integration time." (ALMA)
- observing dates: 24 Jun 2016 (Band 3); 14 Dec 2016 (Band 7 continuum); 23 Mar 2017 ([CII])  
  > "Observations were obtained on December 14th, 2016" (ALMA)
- pi or archival as stated: _not stated_
- Line: CO 4-3 (not stated)
- Line: [CII] 2P3/2-2P1/2 (1900.5 GHz)
- Line: CO 2-1 (ATCA) (230.5380 GHz)
- Other facility **APEX-LABOCA**: 870-um imaging  
  > "We obtained 870-$\mu$m imaging of SPT2349-56 using LABOCA on the APEX telescope." (APEX - LABOCA)
- Other facility **ATCA**: CO(2-1) follow-up  
  > "We used the Australia Telescope Compact Array (ATCA) in its H168 hybrid array configuration" (ATCA CO(2-1))
- Other facility **Spitzer IRAC**: 3.6 and 4.5 um imaging  
  > "This field was twice observed at 3.6 and 4.5 $\mu$m with the Infrared Array Camera" (Spitzer imaging)
- Other facility **Herschel SPIRE**: 250, 350, 500 um imaging  
  > "Multi-colour imaging with Herschel-SPIRE (250, 350, 500-$\mu$m)" (abstract)
- External data: CO(4-3)/CO(1-0) brightness temperature ratio r41 = 0.41 ± 0.07  
  > "$r_{4,1}~=~0.41\pm 0.07$ found from the average of a sample of unlensed SMGs" (Derivation of physical properties) [from (cite: Bothwell2012)]
- External data: SFR-to-S870 ratio 150 ± 50 Msun/yr/mJy  
  > "We adopt an SFR-to-$S_{\rm 870\,\mu m}$ ratio of 150 $\pm$ 50 M$_{\odot}$ yr$^{-1}$/mJy" (Derivation of physical properties) [from (cite: Barger2014)]
- External data: Protocluster comparison sample from compilation  
  > "The data are drawn from a recent compilation(cite: Casey2016) and original references therein." (Protocluster comparison sample) [from (cite: Casey2016)]
- Simulation/model as data: MultiDark N-body + abundance matching + S870 fitting function, 100 Monte Carlo realizations  
  > "We employ the MultiDark(cite: Prada2012) N-body simulation" (Simulations)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline / ALMA-supplied calibration, reprocessed in CASA  
  > "The data were re-processed using CASA and the standard ALMA-supplied calibration using natural beam weighting to maximize sensitivity." (ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 3: Pallas; Band 7 continuum: Ceres; [CII]: J2357-5311  
  > "Pallas and J2343-5626 were used to calibrate the flux and phase respectively." (ALMA); "Ceres and J2357-5311 were used as flux and phase calibrators respectively." (ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Data was processed using the standard ALMA pipeline using natural beam weighting." (ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Blind search on cube without continuum subtraction; for spectra continuum level fitted as free parameter and subtracted  
  > "We use a data cube channelized at 100 km/s, without primary beam correction and continuum subtraction." (Blind search for [CII])
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Spectra binned to 75 km/s, smoothed with Gaussian FWHM 100 km/s for presentation  
  > "binned into 75 km s$^{-1}$ channels" (ALMA)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Blind line search procedure follows ASPECS  
  > "we follow the procedure used to detect line emitters in the ASPECS survey(cite: Aravena2016)" (Blind search for [CII]) [from (cite: Aravena2016)]

### Not stated but needed to reproduce (our reading)

- Imaging cell size, image size, cleaning and masking parameters for ALMA cubes
- CASA version used for reprocessing
- Continuum-free channel selection
- How positions and flux densities were measured for continuum sources (aperture/fit)
- Exact SERCH kernel and noise estimation settings
- CIGALE module parameters and photometry
- Frequency range used for 870-um and 1.1-mm continuum

## Analysis recipe

1. **Blind [CII] line search**: AIPS SERCH on Band 7 cube with Gaussian kernels 200-600 km/s, peaks SNR>4, CLUMPFIND to isolate candidates, purity from negative peaks  
  > "We used a set of different Gaussian kernels, from 200 to 600 km/s and searched for all line peaks with SNR$>$4.0." (Blind search for [CII])
   - software: AIPS SERCH, CLUMPFIND
   - parameter: 100 km/s channels, SNR>4 peaks; 14 candidates all with SNR>6.3  
  > "Out of the 14 \[CII\] line candidates detected, all have SNR$>$6.3" (Blind search for [CII])
   - fitting: _not stated_
   - validation: Negative peak counts: none above SNR 5.8, so SNR>6 candidates are 100% pure  
  > "all positive line candidates with SNR$>$6.0 are likely real (100% purity)" (Blind search for [CII])
2. **Extract spectra and fit line redshifts and widths**: 1D spectra from line centroid, Gaussian least-squares fit with free continuum  
  > "A Gaussian line profile is fit using a least-squares method, providing errors to the velocity offsets from $z=4.304$" (ALMA)
   - fitting: least-squares Gaussian  
  > "A Gaussian line profile is fit using a least-squares method" (ALMA)
   - validation: _not stated_
3. **Derive SFR and gas masses**: SFR from 870-um flux density x 150 Msun/yr/mJy; gas mass from CO(4-3) via r41 and alpha_CO=0.8 x1.36 for helium; [CII] used where CO undetected  
  > "We use a conservative conversion factor $\alpha_{CO} = 0.8" (Derivation of physical properties); "When CO(4-3) is not significantly detected, we use our \[CII\] line luminosity and the average CO(4-3)/\[CII\] ratio for our detected sample" (Derivation of physical properties)
   - assumption: alpha_CO = 0.8, r41 = 0.41, helium factor 1.36, SFR/S870 = 150±50  
  > "multiply by 1.36 to account for the addition of helium" (Derivation of physical properties)
   - fitting: _not stated_
   - validation: ATCA CO(2-1) confirms gas reservoir and assumed line ratio  
  > "confirms that the assumed line intensity ratio, CO(4-3) to CO(1-0), used in the Methods when calculating the total gas mass is consistent with the average measurements from ATCA." (abstract)
4. **Redshift and velocity dispersion, dynamical mass**: Biweight estimator for mean z and sigma; Evrard2008 mass-dispersion relation assuming virialization  
  > "We determine the mean redshift using the biweight estimator(cite: Beers1990)" (main text)
   - assumption: approximately virialized  
  > "Under the assumption that SPT2349-56 is approximately virialized" (main text)
   - fitting: _not stated_
   - validation: Gapper and Gaussian fit agree within 3%; Millennium and N-body filament searches  
  > "Other common methods (gapper(cite: Beers1990), Gaussian fit) agree to within 3% and provide similar errors." (main text)
5. **Total SED and IR luminosity**: CIGALE fit to combined 250-850 um photometry plus IRAC sum  
  > "We have used Code Investigating GALaxy Emission (CIGALE)" (Spectral energy distribution)
   - software: CIGALE
   - assumption: single-component SFH, solar metallicity, Chabrier IMF  
  > "The SED modelling assumes a single-component star formation history and solar metallicity" (Spectral energy distribution)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare with protoclusters and models**: Curves of growth of 870-um flux vs area compared to literature and MultiDark-based model  
  > "One hundred Monte Carlo iterations are performed for each snapshot" (Simulations)
   - software: Rockstar
   - fitting: _not stated_
   - validation: Centre shifts of ~1' change curves <10%  
  > "did not boost the curves by more than 10%" (Protocluster comparison sample)

## Software

- **CASA** : reprocessing ALMA data; ATCA imaging  
  > "The data were re-processed using CASA" (ALMA)
- **AIPS SERCH** : blind line search  
  > "We used the Astronomical Image Processing System (AIPS) task SERCH." (Blind search for [CII])
- **CLUMPFIND** : isolating line candidates  
  > "we used the IDL routine CLUMPFIND(cite: Williams2011)" (Blind search for [CII])
- **MIRIAD** : ATCA editing, calibration, imaging  
  > "The software package MIRIAD (cite: Sault1995)" (ATCA CO(2-1))
- **CIGALE** : SED fitting  
  > "We have used Code Investigating GALaxy Emission (CIGALE)" (Spectral energy distribution)
- **FASTPHOT** : SPIRE deblending  
  > "The code, FASTPHOT(cite: Bethermin2010)" (Analysis of the surrounding field)
- **BoA** : LABOCA reduction  
  > "The data was reduced and imaged using the BoA reduction package" (APEX - LABOCA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean redshift | 4.3040 | +0.0020/-0.0019 | dimensionless | 4 | $\left<z\right>_{\rm bi} = 4.3040^{+0.0020}_{-0.0019}$ |
| velocity dispersion | 408 | +82/-56 | km/s | 4 | $\sigma_{\rm bi} = 408^{+82}_{-56}$ |
| dynamical mass | 1.16e13 | 0.70e13 | Msun | 4 | $M_{\rm dyn} = (1.16 \pm 0.70) \times 10^{13}$ |
| total SFR of 14 sources | 6000 | 600 | Msun/yr | 3 | The total SFR of the 14 sources is $6000 \pm 600$ |
| IR luminosity 8-1100 um | 8.0e13 | 1.0e13 | Lsun | 5 | $(8.0\pm1.0)\times10^{13}$ L$_\odot$ |
| total gas mass | ~6e11 (Xco/0.8) | not stated | Msun | 3 | total gas mass of $\sim6\times10^{11}$ |
| LABOCA total 870 um flux | 110.0 | 9.5 | mJy | 0 | 110.0$\pm$9.5 mJy |

## Qualitative findings

- 14 line emitters at z~4.31 within ~130 kpc; surface overdensity >10x field and volume density >1000x field  
  > "This galaxy surface density is more than 10 times the average blank field value" (abstract)

## Claim tuples

- H: Is SPT2349-56 a dense protocluster core? | E: Blind [CII] search and CO/continuum on ALMA | R: 14 galaxies at z=4.31 in ~130 kpc | F: A massive galaxy cluster core in advanced formation | **supported**
- H: Is it more concentrated than other protoclusters and theoretical expectations? | E: Curves of growth vs literature and MultiDark model | R: Model reaches ~10% of observed flux | F: Uniquely dense; challenges models | **supported**
- H: Is it a bound halo rather than a line-of-sight filament? | E: Kinematics, N-body searches, filament widths | R: At least 12 of 14 appear bound | F: Likely bound but filament not fully excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Line-of-sight filament of separate halos judged less likely  
  > "we argue that SPT2349-56 is less likely to consist of multiple groups, widely separated on a line of sight filament" (Geometry and Dynamics)
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamical mass is an upper limit if not virialized; line-of-sight projection cannot be completely ruled out  
  > "which is an upper limit if the system has not yet virialized" (main text)
- Caveat (inferred, ours): Only 14 galaxies for dispersion with large errors
- Caveat (inferred, ours): alpha_CO=0.8 lower limit gas masses
- Caveat (inferred, ours): SFR from a fixed S870 ratio
- Caveat (inferred, ours): Small ALMA field, no wide mapping

## Reproducibility

- Data public (paper): ALMA programs cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.0.00236.T and ADS/JAO.ALMA#2015.1.01543.T." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: CASA version
- Missing: SED fitting inputs
- Missing: Source measurement method
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Data are identified and main steps described, but imaging and measurement details are sparse.
- Rediscovery candidate: no, Imaging and source-extraction details are missing, and project data may not be public.

## Links

- Method: (cite: Aravena2016) (blind line search procedure)
- Companion: (cite: Strandet2016) (ALMA redshift survey that identified z=4.3)
- Related: SPT-SZ 2500 deg2 survey
- Related: ASPECS

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.0.00236.T"
 ],
 "obscore_codes_not_in_card": [
  "2016.1.00236.T"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 49,
  "rate": 0.583
 },
 "evidence_ok": true
}
```
