# Extremely Low Molecular Gas Content in the Vicinity of a Red Nugget Galaxy at z = 1.91

`2021ApJ...908..163M` | The Astrophysical Journal 2021 | first author: Morishita, T. | arXiv: 2011.06051 | DOI: 10.3847/1538-4357/abd800

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is there molecular gas (via [C I]) in or around the compact quiescent galaxy GDS24569 that could drive further size evolution or explain its quenching?  
  > "in search of molecular gas in its vicinity via the \[C I\] $^3$P$_1$-$^3$P$_0$ line." (abstract)
- Target **GDS24569**: coordinates _not stated_; z/distance z = 1.91  
  > "Our primary target, GDS24569, is a massive ($\log M_*/M_{\odot}\sim11$) galaxy at $z=1.91$" (2.1 Target galaxy); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.01127.S
- bands: Band 5  
  > "Interferometric observations with Band 5 were executed in ALMA cycle 7" (2.2 ALMA Cycle 7 observation)
- frequencies and spectral setup: three 1.875 GHz spectral windows; one on [C I] (~169 GHz), others centered at 168.5 and 170.4 GHz for continuum  
  > "We set three 1.875 GHz-width spectral windows, one of which was tuned to cover the \[C I\] frequency of the target ($\sim169$ GHz)" (2.2 ALMA Cycle 7 observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.0 x 0.8 arcsec^2  
  > "resulting in the final beam size of $1.0\times\,0.8$ arcsec$^2$" (2.2 ALMA Cycle 7 observation)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 27 (Data1), 34 (Data2), 21 uJy/beam combined  
  > "27 $\mu$Jy / beam and 34 $\mu$Jy / beam for Data1 and Data2, respectively, and 21 $\mu$Jy / beam for the combined data cube" (3.1 Dust Continuum Emission)
- time on source: 107 minutes per dataset  
  > "originally executed in November 2019 with on-source exposure of 107 minutes" (2.2 ALMA Cycle 7 observation)
- observing dates: November 2019 (Data2), January 2020 (Data1)  
  > "The observations were compensated in January 2020, with the target in the center as it was originally planned (Data1)." (2.2 ALMA Cycle 7 observation)
- pi or archival as stated: PI T. Morishita, Cycle 7  
  > "(PID. 2019.1.01127.S, PI T. Morishita)" (2.2 ALMA Cycle 7 observation)
- Line: [C I] 3P1-3P0 (492 GHz)
- Other facility **HST/3D-HST/Spitzer**: broadband photometry and grism spectra for SED fitting  
  > "we retrieve broadband photometry of HST and Spitzer up to IRAC CH4, originally published by the 3D-HST team" (3.4 Panchromatic analysis of GDS24569)
- Other facility **Herschel PACS**: 100 and 160 um upper limits  
  > "upper limits on MIPS $70\mu$m, Herschel PACS $100$ and $160\,\mu$m from the GOODS Herschel program" (3.4 Panchromatic analysis of GDS24569)
- Other facility **Chandra 7Ms**: X-ray counterpart check  
  > "No X-ray counterpart is found in the Chandra 7M sec catalog (cite: luo17)" (3.4 Panchromatic analysis of GDS24569)
- External data: HST/Spitzer broadband photometry and grism spectra of GDS24569  
  > "From (cite: morishita19), we retrieve broadband photometry of HST and Spitzer up to IRAC CH4, originally published by the 3D-HST team" (3.4 Panchromatic analysis of GDS24569) [from (cite: morishita19); (cite: skelton14)]
- External data: Spitzer MIPS 24um flux  
  > "We also include Spitzer MIPS $24\mu$m flux from (cite: whitaker14)" (3.4 Panchromatic analysis of GDS24569) [from (cite: whitaker14)]
- External data: X[CI] = 1.5e-5 conversion factor  
  > "We adopt a molecular \[C I\]-to-${\rm H_2}$ conversion factor $X{[\textrm{C}~\textsc{i}]}=1.5\times10^{-5}$ taken from (cite: jiao19)." (3.3 Upper limits in molecular gas mass) [from (cite: jiao19)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean; pixel 0.16 arcsec, ~28 km/s (~15.6 MHz) channels  
  > "We ran the tclean task of CASA on each of the datasets, with parameters of pixel scale 0.16 arcsec and velocity resolution element $\sim28$ km / s ($\sim15.6$ MHz)." (2.2 ALMA Cycle 7 observation)
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
- final beam: 1.0 x 0.8 arcsec^2  
  > "resulting in the final beam size of $1.0\times\,0.8$ arcsec$^2$" (2.2 ALMA Cycle 7 observation)
- final rms: _not stated_

### Inherited from earlier work

- Blind detection method with spectral, spatial and reliability criteria  
  > "we also apply a blind detection method introduced in (cite: damato20), that relies on spectral, spatial and reliability criteria." (3.2.2 D'Amato method) [from (cite: damato20)]
- SED fitting setup  
  > "Following (cite: morishita19), we simultaneously fit these photometric+spectroscopic data points by using synthetic spectral templates." (3.4 Panchromatic analysis of GDS24569) [from (cite: morishita19)]
- M_H2 recipe from [CI] luminosity  
  > "Following a recipe by (cite: papadopoulos04), molecular hydrogen gas mass is inferred by:" (3.3 Upper limits in molecular gas mass) [from (cite: papadopoulos04)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration (pipeline vs manual)
- tclean deconvolver, weighting/robust, masking, cleaning threshold, image size
- continuum subtraction and line-free channels
- how the two datasets were combined
- primary beam correction details
- SED fitting priors, sampler settings, and star-formation-history parametrization
- exact conversion of rms to 3-sigma flux limit

## Analysis recipe

1. **Image cubes and continuum**: tclean on each dataset; continuum from collapsing full cube over -4000 to 3000 km/s; rms with imstat  
  > "we show a continuum map created by collapsing the spectral data cube over the entire velocity range, $-4000$-$3000$ km / s." (3.1 Dust Continuum Emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Blind clump search with Starlink clumpfind**: clumpfind on each cube with rms from 1000 random beam apertures in annuli; inverted-sign cubes as control  
  > "we extract apertures of beam size in 1000 randomly selected positions in each cube, to measure RMSs in annuli at every 10 pixels from the center." (3.2.1 Starlink Clumpfind Algorithm)
   - software: starlink clumpfind
   - parameter: VELORES=5, MINPIX=50, FWHMBEAM=3; RMS 45-130 uJy/beam/element  
  > "(VELORES=5, MINPIX=50, and FWHMBEAM=3)" (3.2.1 Starlink Clumpfind Algorithm)
   - fitting: _not stated_
   - validation: Detections not common to both cubes and similar numbers in sign-inverted cubes, so judged artifacts  
  > "We find a similar number of detections with a similar spatial distribution as for the real cubes." (3.2.1 Starlink Clumpfind Algorithm)
3. **Second blind search (D'Amato)**: S/N cube with local noise from 10-beam boxes; scan for Nch contiguous channels above S/N threshold; reject using negative cube  
  > "We choose a box with an area equal to that of 10 beams" (3.2.2 D'Amato method)
   - parameter: Nch=2-5, S/N threshold 1.5, 2, 2.5, 3; Npx=2,3,4  
  > "For each combination of $\mathrm{N_{ch}}$ and S/N threshold, we try $\mathrm{N_{px}}=2, 3, 4$." (3.2.2 D'Amato method)
   - fitting: Gaussian fit to tentative line  
  > "The line is narrow, and fitted with a gaussian of FWHM $=84$ km / s" (3.2.2 D'Amato method)
   - validation: Cross-check in independent Data1; line not recovered, left tentative  
  > "We thus leave this detection as tentative" (3.2.2 D'Amato method)
4. **H2 mass upper limit**: Papadopoulos et al. 2004 [CI] to M_H2 equation with 3 sigma limit  
  > "By substituting these numbers in the equation above, we obtain a conservative $3\sigma$ upper limit on molecular hydrogen mass of $\sim7.1\times 10^{9}\,M_\odot$" (3.3 Upper limits in molecular gas mass)
   - parameter: Delta v = 300 km/s; Q10=0.5; A10=7.93e-8 s^-1; Helium factor 1.36  
  > "We set $\Delta v=300$ km / s based on stellar velocity dispersion measurements in massive compact quiescent galaxies" (3.3 Upper limits in molecular gas mass)
   - assumption: X[CI]=1.5e-5, Q10=0.5 (LTE, optically thin)  
  > "We adopt the excitation factor $Q_{10}=0.5$ as a fiducial value, assuming local thermodynamic equilibrium" (3.3 Upper limits in molecular gas mass)
   - fitting: _not stated_
   - validation: _not stated_
5. **Panchromatic SED fit for dust mass and SFH**: gsf fit of photometry, grism spectra and ALMA/FIR upper limits with FSPS templates plus Draine & Li dust emission  
  > "We re-fit the dataset with a SED fitting code, `gsf` (ver.1.4[^1])." (3.4 Panchromatic analysis of GDS24569)
   - software: gsf, FSPS, piXedfit
   - parameter: MILES, Salpeter IMF, ages 0.01-3 Gyr, logZ -0.8 to 0.6 step 0.05, Calzetti dust, DL07 LMC model qPAH=2.37%  
  > "we limit the calculation to their LMC model with $q_{\rm PAH}=2.37\%$." (3.4 Panchromatic analysis of GDS24569)
   - fitting: _not stated_
   - validation: Dust mass cross-checked with piXedfit: log Mdust = 8.2 (+0.4/-0.6)  
  > "The code returns $\log M_{\rm dust}/M_\odot = 8.2_{-0.6}^{+0.4}$, in good agreement with the dust mass estimated by `gsf`." (3.4 Panchromatic analysis of GDS24569)

## Software

- **CASA** : tclean imaging and imstat rms  
  > "We ran the tclean task of CASA on each of the datasets" (2.2 ALMA Cycle 7 observation)
- **starlink clumpfind** : blind clump detection  
  > "We first run the clumpfind algorithm, implemented in the `starlink` package" (3.2.1 Starlink Clumpfind Algorithm)
- **gsf** 1.4: SED fitting  
  > "We re-fit the dataset with a SED fitting code, `gsf` (ver.1.4[^1])." (3.4 Panchromatic analysis of GDS24569)
- **piXedfit** : alternative SED fit for dust mass  
  > "We also fit our photometric data points with another SED fitting code, `piXedfit`" (3.4 Panchromatic analysis of GDS24569)
- **FSPS** : SED templates  
  > "We generate the fitting templates by using `fsps` (cite: conroy09fsps)" (3.4 Panchromatic analysis of GDS24569)
- **EMCEE** : listed in software acknowledgement  
  > "python-fsps (cite: foreman14), EMCEE (cite: foreman13)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3 sigma upper limit on M_H2 | 7.1e9 | not stated | Msun | 4 | $3\sigma$ upper limit on molecular hydrogen mass of $\sim7.1\times 10^{9}\,M_\odot$ |
| 3 sigma upper limit on [CI] integrated flux | 42 | not stated | mJy km/s/beam | 4 | $S_{[\textrm{C}~\textsc{i}]}\Delta v\sim42$ mJy km / s / beam as a $3\sigma$ upper limit |
| gas mass fraction upper limit | <5% | not stated | percent | 4 | characterizing a significantly low gas mass fraction |
| log dust mass (gsf) | 8.3 | 0.6 | log Msun | 5 | The best-fit result returns dust mass $\log M_{\rm dust}/M_\odot=8.3\pm{0.6}$. |
| dust-to-stellar mass ratio | 1.4e-3 | not stated | dimensionless | 5 | $M_{\rm dust}/M_* \sim 1.4\times10^{-3}$ |
| tentative line S/N at +1200 km/s | 4.1 | not stated | sigma | 3 | we find one tentative detection ($4.1\,\sigma$) at $+1200$ km / s |
| tentative line flux | 7.5 | not stated | mJy km/s | 3 | $S_{[\textrm{C}~\textsc{i}]} \Delta v \sim 7.5$ mJy km / s |

## Qualitative findings

- No continuum source detected near GDS24569; no robust [CI] clumps found out to ~300 kpc.  
  > "No continuum source is detected near the position of GDS24569." (3.1 Dust Continuum Emission)

## Claim tuples

- H: Does GDS24569 or its vicinity host molecular gas that could drive size growth? | E: Blind [CI] searches in two ALMA Band 5 cubes | R: No robust detections; one tentative 4.1 sigma line only in one dataset | F: No significant gas clumps in or around GDS24569 | **supported**
- H: Is the gas fraction of GDS24569 low? | E: [CI]-based M_H2 upper limit | R: M_H2 < 7.1e9 Msun, f_gas < 5% | F: Extremely low gas fraction | **supported**
- H: Is GDS24569 dust-rich relative to local early types? | E: SED fitting with FIR limits | R: Mdust/M* ~1e-3 | F: 10-100x higher than local ETGs | **partially**

## Reasoning

- Why this data: [CI] chosen as a gas tracer over CO(4-3) because of lower excitation temperature  
  > "While CO(4-3) is also available in the same spectral window, it is not optimal to search for cool gas owing to its slightly higher excitation temperature (55.3 K)." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Q10 cannot be constrained without other line ratios; the tentative line is not confirmed in Data1.  
  > "none of these values can be constrained without line ratios to other excitation levels" (3.3 Upper limits in molecular gas mass)
- Caveat (inferred, ours): Gas mass limit depends strongly on assumed X[CI], Q10 and 300 km/s line width
- Caveat (inferred, ours): CASA imaging and calibration details are missing
- Caveat (inferred, ours): Dust mass rests on limited FIR data and a single DL07 model

## Reproducibility

- Data public (paper): Project code given but public status not stated  
  > "Interferometric observations with Band 5 were executed in ALMA cycle 7 (PID. 2019.1.01127.S, PI T. Morishita)." (ALMA Cycle 7 observation)
- Products in archive: _not stated_
- Missing: CASA version and tclean parameters
- Missing: how the combined cube was built
- Missing: gsf priors and SFH configuration
- Missing: clump search exact noise settings per run
- Data volume (inferred): ~10-50 GB (two short Band 5 executions)
- Score (inferred): 5/5, Data is identifiable and the methods are described, but imaging and SED fitting details are incomplete.
- Rediscovery candidate: no, Results are mainly non-detection limits and key imaging parameters are not stated.

## Links

- Method: (cite: damato20) (Blind line detection algorithm)
- Method: (cite: papadopoulos04) ([CI] to H2 mass recipe)
- Method: (cite: morishita19) (SED fitting method and data)
- Companion: (cite: morishita16) (Satellite galaxy census around GDS24569)
- Related: XDF
- Related: 3D-HST
- Related: GOODS Herschel
- Related: CLEAR
- Related: FIGS

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
