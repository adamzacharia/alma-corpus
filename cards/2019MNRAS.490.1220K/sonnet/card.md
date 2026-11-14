# ALMACAL - VI. Molecular gas mass density across cosmic time via a blind search for intervening molecular absorbers

`2019MNRAS.490.1220K` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Klitsch, Anne | arXiv: 1909.08624 | DOI: 10.1093/mnras/stz2660

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, agn_and_quasars, milky_way_ism
- Question: What is the cosmic molecular gas mass density and CO column density distribution, constrained via a blind search for intervening CO absorbers towards ALMA calibrators?  
  > "We use intervening CO absorption lines in the spectra of mm-bright background sources to provide a census of the molecular gas mass density of the Universe." (abstract)
- Target **ALMACAL calibrators (880 observed; 622 with redshift)**: coordinates _not stated_; z/distance z <= 3 (calibrator redshifts)  
  > "This amounts to observations of 880 calibrators." (2 ALMACAL observations and data reduction); "This results in redshift measurements of 622 calibrators." (2 ALMACAL observations and data reduction); distance from Bonato2018 compilation, Mahony2011, Simbad, NED  
  > "This amounts to observations of 880 calibrators." (2 ALMACAL observations and data reduction); "This results in redshift measurements of 622 calibrators." (2 ALMACAL observations and data reduction)
- Target **J1415+1320**: coordinates _not stated_; z/distance z = 0.2467  
  > "intrinsic CO(1-0) absorption in the spectrum of the background calibrator J1415+1320 ($z = 0.2467$)" (3.1 Blind Search for Intervening Absorbers); distance from Wiklind1994  
  > "intrinsic CO(1-0) absorption in the spectrum of the background calibrator J1415+1320 ($z = 0.2467$)" (3.1 Blind Search for Intervening Absorbers)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: Spectra bandwidth 0.03 MHz to 2 GHz, 256 to 3840 channels; 28,644 spectra, each spectral window separately  
  > "the spectra have varying bandwidth and spectral resolution, ranging from 0.03 MHz to 2 GHz, and from 256 to 3840 channels" (3.1 Blind Search for Intervening Absorbers)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array only, Cycles 1 to 6  
  > "We only consider data taken with the ALMA 12-m array." (2 ALMACAL observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: >1500 hours on ALMACAL sources  
  > "the total integration time spent on ALMACAL sources is $>1500$ hours" (Introduction)
- observing dates: Cycles 1-6, before 4 December 2018  
  > "from PI observations from Cycles 1 to 6, taken before the 4$^{\rm th}$ December 2018" (2 ALMACAL observations and data reduction)
- pi or archival as stated: Archival calibrator data from PI observations  
  > "We extract from the ALMA archive all phase, amplitude and bandpass calibrator data from PI observations" (2 ALMACAL observations and data reduction)
- Line: CO J=1-0 to 5-4 (not stated)
- Other facility **IllustrisTNG100 simulation**: Predicted H2 column density distribution function  
  > "Here we use the TNG100 volume of the IllustrisTNG simulations" (3.3)
- External data: Redshift compilation of calibrators  
  > "we use the compilation of redshifts from the database presented by (cite: Bonato2018)" (2) [from (cite: Bonato2018)]
- External data: z~0 H2 column density distribution/cumulative absorbers from BIMA SONG  
  > "cumulative number of absorbers expected based on the results from BIMA SONG observations of local star-forming galaxies (cite: Zwaan2006)" (3.2) [from (cite: Zwaan2006)]
- External data: N(CO)/N(H2) = 3e-6 (range 1e-7 to 1e-5)  
  > "mean column density ratio of $N({\rm CO})/ N(\mbox{H}_2) = 3 \times 10^{-6}$ (cite: Burgh2007)" (3.2) [from (cite: Burgh2007)]
- External data: Absorption FWHM of 40 km/s  
  > "an expected FWHM of the absorption line of $40$ km s$^{-1}$ (cite: Wiklind2018)" (3.2) [from (cite: Wiklind2018)]
- Simulation/model as data: IllustrisTNG100 H2 column density distribution at z=0.199 and 0.839, path length 10 cMpc/h  
  > "The column density is integrated over a path length of 10 cMpc $h^{-1}$." (3.3)

## Processing

### Calibration

- pipeline or manual: Custom: point-source fit to uv data, bandpass via ratios of calibrator pairs  
  > "the spectrum of the calibrator is extracted directly from the $uv$ data, by fitting a point source model at the phase centre" (2)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Limiting CO column densities computed following Mangum2015  
  > "We then calculate the limiting CO column densities probed in our survey following (cite: Mangum2015)." (3.2) [from (cite: Mangum2015)]
- H2 modelling of TNG  
  > "using the $\mbox{H}_2$ modeling methodology of (cite: Popping2019)" (3.3) [from (cite: Popping2019)]
- CDDF gridding procedure  
  > "the column density distribution function gridding procedure as described in (cite: Nelson2019)" (3.3) [from (cite: Nelson2019)]

### Not stated but needed to reproduce (our reading)

- ALMA project list and exact execution blocks used
- Butterworth filter order and implementation
- Exact noise estimation per spectrum
- Software versions and code for spectrum extraction
- Redshift lists of the 622 calibrators
- Details of the rho(H2) scaling of Zwaan2006 functional form

## Analysis recipe

1. **extract and flatten spectra**: Point-source fit in uv data per spectral window, XX and YY added in quadrature; bandpass by ratios of calibrator pairs; mask edges and atmospheric lines; Butterworth low-pass second-order correction  
  > "we apply a bandpass correction by taking ratios of the spectra of pairs of calibrators from the same execution block." (2)
   - parameter: mask 5% edge channels; 0.2 GHz around atmospheric lines; template of structures wider than 200 km/s  
  > "we mask 5 per cent of the channels on each end of the spectrum to remove edge effects." (2)
   - fitting: _not stated_
   - validation: Recovery of known intrinsic CO(1-0) absorber in J1415+1320  
  > "This detection validates the robustness of our finding algorithm." (3.1)
2. **blind absorption line search**: 5 sigma threshold in two consecutive channels after smoothing with kernels 10-190 km/s; remove edge, Galactic, artefact, atmospheric and implausible-redshift candidates  
  > "We use a range of smoothing kernels between 10 and 190 $\rm km\, s^{-1}$ in steps of 10 $\rm km\, s^{-1}$." (3.1)
   - software: SPLATALOGUE
   - fitting: _not stated_
   - validation: _not stated_
3. **column density limits and distribution function**: Redshift path and comoving path per spectrum for CO J=1-0..5-4; 5 sigma N(CO) limits; convert to N(H2); CDDF per 1 dex bin and cumulative number per dX  
  > "we use a bin width of $\Delta N = 1$ dex" (3.2)
   - parameter: 5 sigma threshold, FWHM 40 km/s  
  > "we perform the calculation using the $5 \sigma$ level from each spectrum as the detection threshold" (3.2)
   - assumption: Tex = T_CMB at the absorber redshift; N(CO)/N(H2)=3e-6  
  > "We assume an excitation temperature equal to the CMB temperature at the redshift probed with the spectrum" (3.2)
   - assumption: H0=70, Om=0.3, OL=0.7  
  > "$H_0 = 70 {\rm km s^{-1} Mpc^{-1}}$, $\Omega_{\rm m} = 0.3$ and $\Omega_{\Lambda} = 0.7$" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **IllustrisTNG prediction**: H2 CDDF from TNG100 at z=0.199, 0.839 with variations in H2 model (3), path length (5), grid size (3)  
  > "which vary the $\mbox{H}_2$ model employed (three versions), the projection depth / effective path length (five values)" (3.3)
   - software: IllustrisTNG
   - fitting: _not stated_
   - validation: Compared with EAGLE  
  > "We have conducted the same analysis on the results from the EAGLE simulation" (3.3)
5. **molecular gas mass density limits**: Scale Zwaan2006 z~0 cumulative absorber function to upper limits, integrate N(H2)*dn for log N>21 in ASPECS-like redshift bins  
  > "We scale it to our upper limits and integrate over differential number of absorbers multiplied by the respective column density." (3.4)
   - assumption: Only log N(H2)>21 contributes (low-N contributes 3% per Zwaan2006)  
  > "Therefore, we integrate only column densities log($N({\rm \mbox{H}_2})$) $>$ 21." (3.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Butterworth low-pass filter** : Second-order bandpass correction  
  > "we use a Butterworth low-pass filter developed as a maximally flat low-pass filter for signal processing" (2)
- **SPLATALOGUE** : Filtering Galactic molecular lines  
  > "we match the candidate list with a list of frequencies corresponding to rare molecular species from SPLATALOGUE" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total redshift path Δz | 182.2 | not stated | dimensionless | 3 | The cumulative redshift path surveyed, $\Delta z$, is 182.2 for CO transitions between $J = 1-0$ and $J = 5-4$. |
| rho(H2) upper limit 0.003<z<0.369 | <10^8.26 | not stated | Msun Mpc^-3 | 5 | / 0.003 – 0.369 / $< 10^{8.26}$ / |
| rho(H2) upper limit 0.2713<z<0.6306 | <10^8.32 | not stated | Msun Mpc^-3 | 5 | / 0.2713 – 0.6306 / $< 10^{8.32}$ / |
| rho(H2) upper limit 0.695<z<1.1744 | <10^8.39 | not stated | Msun Mpc^-3 | 5 | / 0.6950 – 1.1744 / $< 10^{8.39}$ / |
| rho(H2) upper limit 1.006<z<1.738 | <10^8.21 | not stated | Msun Mpc^-3 | 5 | / 1.006 – 1.738 / $< 10^{8.21}$ / |
| Maximum molecular gas radius | 4.8 kpc (z<0.5), 4.6 kpc (z>0.5) | not stated | kpc | 0 | We derive a maximum radius of 4.8 kpc at $z < 0.5$ and 4.6 kpc at $z > 0.5$. |
| Comoving path length ΔX | 123 (z<0.5), 205 (z>0.5) | not stated | dimensionless | 3 | a total comoving pathlength of $\Delta X = 123$. At $z>0.5$, $\Delta z = 89$ and $\Delta X = 205$. |

## Qualitative findings

- No intervening extragalactic molecular absorbers detected; one intrinsic CO(1-0) absorber in J1415+1320 and multiple Galactic lines  
  > "no extragalactic intervening molecular absorbers are detected" (abstract)

## Claim tuples

- H: Can a blind absorption survey constrain the molecular column density distribution beyond z~0? | E: Search 28,644 ALMACAL spectra for CO absorption | R: No intervening detections; Δz=182; N(H2)>1e16 probed | F: Upper limits on CDDF consistent with z=0 measurements and reach five orders of magnitude lower column density | **supported**
- H: Do the limits constrain IllustrisTNG? | E: Compare limits with TNG100 predicted CDDF | R: Limits within about 1 dex of predictions at low column density | F: Already provide constraints but uncertainties are large | **partially**

## Reasoning

- Why this data: Large integration time and sky coverage of calibrators allow an unbiased, cosmic-variance-free search  
  > "the total integration time spent on ALMACAL sources is $>1500$ hours, orders of magnitude more than what would be attainable in a targeted ALMA survey programme" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lensing magnification bias of background quasars remains a systematic issue  
  > "the uncertainties introduced by lensing of the background quasar by the foreground absorber will remain a systematic issue" (4)
- Limitation (authors): Conversion N(CO) to N(H2) is uncertain and not constant  
  > "the column density ratio of $N({\rm CO})/ N(\mbox{H}_2)$ over a large range of H$_2$ column densities is not constant" (3.2)
- Caveat (inferred, ours): Excitation temperature set to T_CMB biases limits
- Caveat (inferred, ours): Only 622 of 880 calibrators have redshifts, and the samples differ in WISE colours
- Caveat (inferred, ours): rho(H2) relies on scaling the Zwaan2006 functional form
- Caveat (inferred, ours): Limits only with no detections limit significance

## Reproducibility

- Data public (paper): Data from the ALMA archive  
  > "We extract from the ALMA archive all phase, amplitude and bandpass calibrator data" (2)
- Products in archive: _not stated_
- Missing: Project codes and execution block list
- Missing: Extraction/search code
- Missing: Calibrator redshift table
- Data volume (inferred): more than 26 TB of reduced-resolution calibrated data; raw archive larger
- Score (inferred): 3/5, Data are public and the algorithm is described, but code, project list and many parameters are not given.
- Rediscovery candidate: no, Massive data volume and custom unreleased pipeline; main results are upper limits.

## Links

- Method: (cite: Bonato2018) (ALMACAL calibrator sample and redshift database)
- Method: (cite: Popping2019) (H2 modelling methodology for TNG)
- Related: ALMACAL
- Related: ASPECS
- Related: COLDz
- Related: IllustrisTNG

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00193.S",
  "2012.1.00268.S",
  "2012.1.00275.S",
  "2012.1.00303.S",
  "2012.1.00374.S",
  "2012.1.00496.S",
  "2012.1.00743.S",
  "2012.1.01069.S",
  "2012.1.01099.S",
  "2013.1.00111.S",
  "2013.1.00166.S",
  "2013.1.00553.S",
  "2013.1.00645.S",
  "2013.1.00658.S",
  "2013.1.00916.S",
  "2013.1.00988.S",
  "2013.1.01034.S",
  "2013.1.01110.S",
  "2013.1.01175.S",
  "2013.1.01195.S",
  "2015.1.00041.S",
  "2015.1.00188.S",
  "2015.1.00350.S",
  "2015.1.00410.S",
  "2015.1.00530.S",
  "2015.1.00669.S",
  "2015.1.00678.S",
  "2015.1.00856.S",
  "2015.1.00896.S",
  "2015.1.00986.S",
  "2015.1.01005.S",
  "2015.1.01054.S",
  "2015.1.01133.S",
  "2015.1.01222.S",
  "2015.1.01548.S",
  "2015.1.01602.S",
  "2016.1.00115.S",
  "2016.1.00119.S",
  "2016.1.00138.S",
  "2016.1.00447.S",
  "2016.1.00630.S",
  "2016.1.01135.S",
  "2016.1.01164.S",
  "2016.1.01284.S",
  "2016.1.01326.S",
  "2016.1.01398.S",
  "2016.1.01456.S",
  "2017.1.00280.S",
  "2017.1.00321.S",
  "2017.1.00707.S",
  "2017.1.00717.S",
  "2017.1.00941.S",
  "2017.1.00964.S",
  "2017.1.01027.S",
  "2017.1.01093.S",
  "2017.1.01347.S",
  "2017.1.01658.S",
  "2018.1.00035.L",
  "2018.1.00162.S",
  "2018.1.00276.S",
  "2018.1.00306.S",
  "2018.1.00538.S",
  "2018.1.00585.S",
  "2018.1.00781.S",
  "2018.1.00900.S",
  "2018.1.00992.S",
  "2018.1.01038.S",
  "2018.1.01119.S",
  "2018.1.01194.S",
  "2018.1.01241.S",
  "2018.1.01344.S",
  "2018.1.01438.S",
  "2018.1.01617.T",
  "2018.1.01740.S",
  "2018.1.01766.T",
  "2018.1.01812.S",
  "2018.A.00065.T",
  "2019.1.00061.S",
  "2019.1.00130.S",
  "2019.1.00260.S",
  "2019.1.00337.S",
  "2019.1.00397.S",
  "2019.1.00411.S",
  "2019.1.00447.S",
  "2019.1.00458.S",
  "2019.1.00597.S",
  "2019.1.00708.S",
  "2019.1.00801.S",
  "2019.1.01022.S",
  "2019.1.01027.S",
  "2019.1.01118.S",
  "2019.1.01136.S",
  "2019.1.01178.S",
  "2019.1.01190.S",
  "2019.1.01317.S",
  "2019.1.01337.S",
  "2019.1.01422.S",
  "2019.1.01437.S",
  "2019.1.01742.S",
  "2019.1.01813.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 39,
  "rate": 0.487
 },
 "evidence_ok": true
}
```
