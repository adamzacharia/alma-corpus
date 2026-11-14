# Resolving the Interstellar Medium in Ultraluminous Infrared QSO Hosts with ALMA

`2019ApJ...887...24T` | The Astrophysical Journal 2019 | first author: Tan, Qing-Hua | arXiv: 1910.10360 | DOI: 10.3847/1538-4357/ab50be

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What are the distribution, kinematics and dynamical masses of the molecular gas (CO(1-0)) and 3-mm continuum in local ultraluminous IR QSO hosts, and how do BH accretion and star formation relate?  
  > "aimed at characterizing the distribution and kinematics of molecular ISM of local IR QSO host galaxies." (1 Introduction)
- Target **Eight IR QSOs (I ZW 1, IRAS 06269-0543, IRAS F11119+3257, IRAS Z11598-0112, IRAS F15069+1808, IRAS F15462-0450, IRAS F22454-1744, IRAS F23411+0228)**: coordinates phase centers in Table 1, e.g. I ZW 1 00:53:34.9 +12:41:36.2  
  > "I ZW 1 & 00:53:34.9 & 12:41:36.2 & Aug. 2016 & 108.644" (Table 1); "eight IR QSOs at $z=0.06-0.19$" (1 Introduction); z/distance z = 0.06-0.19 (z_CO in Table 3, e.g. I ZW 1 0.06115)  
  > "I ZW 1 & 00:53:34.9 & 12:41:36.2 & Aug. 2016 & 108.644" (Table 1); "eight IR QSOs at $z=0.06-0.19$" (1 Introduction); distance from CO redshift from Gaussian fit to ALMA spectrum; LCDM H0=70, Om=0.3, OL=0.7  
  > "I ZW 1 & 00:53:34.9 & 12:41:36.2 & Aug. 2016 & 108.644" (Table 1); "eight IR QSOs at $z=0.06-0.19$" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.01147.S
- bands: Band 3  
  > "We used the ALMA band 3 receiver" (2 ALMA Observations)
- frequencies and spectral setup: spectral window centered on CO(1-0); 0.488 MHz resolution (1.3-1.5 km/s)  
  > "The spectral resolution is 0.488 MHz, or 1.3$-$1.5 km s$^{-1}$ at the observed line frequency." (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, 36-44 12m antennas  
  > "with 36$-$44 12m diameter antennas in the extended configuration with baselines 15$-$3637 m" (2 ALMA Observations)
- baselines: _not stated_
- angular resolution: ~0.45 arcsec (robust 0.5), ~0.8 kpc at z=0.1  
  > "The typical full width at half maximum (FWHM) synthesized beam size is $\sim$0.$''$45 by using Briggs weighting with a robust parameter of 0.5" (2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.4-0.9 mJy/beam per 25 km/s channel; continuum 30-78 uJy  
  > "The achieved 1$\sigma$ rms noise levels in the spectral velocity resolution of 25 km s$^{-1}$ are 0.4$-$0.9 mJy beam$^{-1}$." (2 ALMA Observations)
- time on source: ~17 min per source on average  
  > "The average on-source integration time on the target was $\sim$17 minutes per source" (2 ALMA Observations)
- observing dates: 2016 August to 2017 August  
  > "were carried out between 2016 August and 2017 August" (2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Other facility **IRAM 30m**: single-dish CO(1-0) spectra for flux comparison (Xia+12)  
  > "our interferometric data typically recover $\sim$ 80% of the observed single-dish flux" (3.3)
- Other facility **VLA**: FIRST/1.4 GHz 20 cm peaks; archival 8.4 GHz data (AB0670) for I ZW 1  
  > "we collected and processed the A configuration 8.4 GHz radio data (project ID: AB0670) from VLA data archive" (4.1)
- Other facility **SDSS / Pan-STARRS1 / HST**: optical images for overlay  
  > "overlay of the CO(1$-$0) emission and the SDSS $u$-band (or Pan-STARRS1 (PS1) $g$-band if SDSS data are not available) image" (3.1)
- External data: Black hole masses and AGN bolometric luminosities  
  > "virial black hole masses from (cite: hao05) using H$\beta$ broad emission line and $\lambda L_{\lambda,5100\textup{\AA}}$ measurements." (Table 4 notes) [from (cite: hao05)]
- External data: Far-IR luminosities from IRAS 60 and 100 um flux densities and single-dish CO  
  > "the far-IR luminosities were calculated based on the flux densities measured at IRAS 60 $\mu$m and 100 $\mu$m (cite: xia12)" (4.2) [from (cite: xia12)]
- External data: Archival ALMA CO(1-0) of IRAS F11119+3257 at 2.8 arcsec  
  > "we combined our high-resolution CO data with the archival ALMA CO data ($\sim$ 2$''$ .8 resolution) observed by (cite: veilleux17)" (3.2) [from (cite: veilleux17)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline mode  
  > "in pipeline mode, by executing the calibration scripts corresponding to the release data of the observations" (2 ALMA Observations)
- casa version: CASA 4.7.0 and 4.7.2 (4.7.2 for IRAS F11119+3257 and F23411+0228)  
  > "CASA[^1] (cite: mcmullin07) 4.7.0 and 4.7.2 (for IRAS F11119+3257 and IRAS F23411+0228" (2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0006-0623, J0750+1231, J0854+2006, J1229+0203, J1550+0527, J2258-2758 (also bandpass)  
  > "Bandpass calibration was performed through observations of J0006$-$0623, J0750+1231, J0854+2006, J1229+0203, J1550+0527, and J2258$-$2758, which were also used as flux calibrators." (2 ALMA Observations)
- flux scale uncertainty: 5-10%  
  > "The typical uncertainty of flux calibration is estimated to be 5$-$10%." (2 ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean (MFS continuum)  
  > "by combining the line-free channels from the spectral window in multi-frequency synthesis mode using the CASA task `clean`" (2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5 for beams in Table; robust = 2.0 adopted for analysis  
  > "we adopt the cubes of both line and continuum produced by Briggs cleaning with robust parameter of 2.0 for data analysis" (2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane zeroth-order polynomial with uvcontsub  
  > "fitting a $uv$-plane model of the continuum emission with a zeroth-order polynomial that was then subtracted using the `uvcontsub` task" (2 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: two configurations combined for IRAS F23411+0228  
  > "$^{d}$ Combination of the two configuration data." (Table 1)
- smoothing: velocity channels of 25 km/s  
  > "The achieved 1$\sigma$ rms noise levels in the spectral velocity resolution of 25 km s$^{-1}$" (2 ALMA Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Alpha_CO = 0.8 ULIRG-like conversion factor  
  > "ULIRG-like CO luminosity-to-H$_2$ mass conversion factor, $\alpha_{\rm CO}$, of 0.8 $M_\odot$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: downes98)" (3.3) [from (cite: downes98)]
- Rotating-disk dynamical mass relation and R = 0.75 x CO FWHM  
  > "$M_{\rm dyn}\approx 2.3\times 10^5 v_{\rm cir}^2 R$ (cite: wang10)" (3.5) [from (cite: wang10); (cite: wang13)]
- Virial mass estimator M=5 sigma^2 R/G  
  > "$M_{\rm dyn} = 5\sigma^2 R/G$ (cite: pettini01)" (3.5) [from (cite: pettini01)]
- L_IR = 1.3 L_FIR and SFR = 1.49e-10 L_IR  
  > "by adopting $L_{\rm IR} = 1.3 L_{\rm FIR}$ (cite: decarli18)" (4.2) [from (cite: decarli18); (cite: kennicutt12)]
- L'CO-L_IR relation for CO-based SFR  
  > "observed for starburst galaxies (cite: sargent14)" (4.2) [from (cite: sargent14)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Clean threshold, mask, cell and image size
- Whether archive pipeline products or re-run scripts were used
- 3D-BAROLO configuration (ring geometry, fixed parameters, fitting options)
- Aperture and velocity ranges for CO integration beyond Fig 2
- UVMULTIFIT initial guesses and fit settings
- Details of the log-linear bisector fit to Macc vs SFR and the high-z compilation
- Rest frequency adopted for CO(1-0)

## Analysis recipe

1. **Image continuum and line cubes**: clean in MFS for continuum; uvcontsub then clean for cubes; robust 2.0 for analysis  
  > "The continuum emission was subtracted in the $uv$-plane before making the line images." (2 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO fluxes, redshifts and line widths; compare with IRAM 30m**: Gaussian fits to spectra from circular apertures or >=2 sigma regions; compared to single-dish  
  > "The redshift and line width were measured from a Gaussian fit to the CO line." (3.3)
   - software: CASA
   - fitting: Gaussian (double Gaussian for I ZW 1, IRAS 06269-0543)  
  > "except for I ZW 1 and IRAS 06269$-$0543, where the CO spectrum is fitted using a double-Gaussian model" (Table 3 notes)
   - validation: ALMA recovers ~80% of single-dish flux  
  > "our interferometric data typically recover $\sim$ 80% of the observed single-dish flux." (3.3)
3. **Measure source sizes**: uv-plane model fitting of CO (circular + elliptical Gaussian) and continuum (circular Gaussian)  
  > "we directly fit models to the interferometric observables (i.e., the visibilities) in the $uv$-plane" (3.4)
   - software: UVMULTIFIT
   - assumption: symmetric Gaussian surface brightness  
  > "Assuming that the surface brightness distribution of the CO line and continuum follow a symmetric Gaussian profile" (3.4)
   - fitting: chi^2 minimization  
  > "The best fit is determined by $\chi^2$ minimization." (3.4)
   - validation: _not stated_
4. **Fit rotation curves**: 3D tilted-ring models with inclination from axis ratio; V_rot and sigma at turnover radius  
  > "fitting 3D tilted-ring models to emission-line data cubes with $^{3\rm{D}}$BAROLO code" (3.2)
   - software: 3D-BAROLO, CASA
   - assumption: thin disk, i = arccos(amin/amaj)  
  > "$i$ = cos$^{-1}$($a_{\rm min}$/$a_{\rm maj}$)" (3.2)
   - fitting: _not stated_
   - validation: IRAS F11119+3257 poorly fit; other three well fit  
  > "Except IRAS F11119+3257, which is poorly fit by models, the kinematics for the remaining three galaxies can be well-fitted by models." (3.2)
5. **Derive CO luminosity and gas mass**: Solomon+97 L'CO formula; M_H2 = alpha_CO L'CO  
  > "The molecular gas mass derived by $M_{\rm H_2}=\alpha_{\rm CO} L^\prime_{\rm CO}$" (3.3)
   - assumption: alpha_CO = 0.8, constant for all  
  > "we adopt a constant $\alpha_{\rm CO}$ to estimate the molecular gas mass for all the galaxies in our sample" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate dynamical masses**: rotating disk Mdyn=2.3e5 v^2 R (v=0.75 FWHM/sin i if no model); virial 5 sigma^2 R/G for irregular  
  > "$v_{\rm cir}$ = 0.75 $\Delta v_{\rm FWHM}$/sin$i$" (3.5)
   - assumption: R = 0.75 x CO FWHM major axis  
  > "which we assume equal to 0.75 times the CO FWHM major axis of the extended component" (3.5)
   - fitting: _not stated_
   - validation: FWHM-based v_cir roughly twice model-derived values  
  > "found the $v_{\rm cir}$ inferred by the FWHM of CO line are roughly twice higher than that derived from model fitting" (3.5)
7. **Compare BH accretion rate with SFR**: Macc = Lbol/(eta c^2); SFR from FIR or CO-predicted IR; log-linear bisector fit  
  > "The BH accretion rate is derived as $\dot{M}_{\rm acc}=L_{\rm bol}/\eta c^2$ assuming an accretion efficiency $\eta=0.1$." (4.2)
   - assumption: eta=0.1; Eddington accretion when Lbol unavailable for high-z  
  > "we estimated the $\dot{M}_{\rm acc}$ by assuming Eddington accretion" (4.2)
   - fitting: logarithmic linear least-squares bisector fit  
  > "a logarithmic linear least-squares bisector fit" (4.2)
   - validation: Spearman correlation test  
  > "The Spearman rank correlation coefficient for this correlation is 0.77 with a high significance ($P<10^{-5}$)" (4.2)

## Software

- **CASA** 4.7.0 and 4.7.2: calibration, clean, uvcontsub, immoments  
  > "The ALMA data were calibrated with CASA[^1] (cite: mcmullin07) 4.7.0 and 4.7.2" (2 ALMA Observations)
- **3D-BAROLO** : 3D tilted-ring fitting of CO cubes  
  > "fitting 3D tilted-ring models to emission-line data cubes with $^{3\rm{D}}$BAROLO code" (3.2)
- **UVMULTIFIT** : uv-plane size fitting  
  > "by using `UVMULTIFIT` tool(cite: martividal14)" (3.4)
- **AICER** : compositing optical/CO overlay images  
  > "These plots were produced using the software AICER" (Footnote 3)
- **GILDAS** : listed in software section; use not described  
  > "GILDAS" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median CO extended-component size | 3.2 | not stated | kpc | 3 | $\sim$ 1.2$-$7.0 kpc with a median of 3.2 kpc |
| 3-mm continuum size | 0.4-1.0 (median 0.6) | not stated | kpc | 3 | $\sim$ 0.4$-$1.0 kpc with a median of 0.6 kpc |
| Vrot/sigma for three disk hosts | 4-6 | not stated | dimensionless | 4 | is in the range of 4$-$6 for the three galaxies |
| Dynamical mass range | 7.4e9 - 6.9e10 | not stated | Msun | 6 | give masses between $7.4\times10^9$ and $6.9\times10^{10}$ $M_\odot$ |
| Mgas/Mdyn median | 0.22 | 0.04 | dimensionless | 6 | with a median value of 0.22$\pm$0.04 for IR QSOs |
| Macc ∝ SFR power-law index | 1.68 | 0.17 | dimensionless | 7 | $\dot{M}_{\rm acc}\propto {\rm SFR}^{(1.68\pm0.17)}$ |
| Median Macc/SFR for IR QSOs | 6.0e-3 | not stated | dimensionless | 7 | The median value of $\dot{M}_{\rm acc}$/SFR is **$6.0\times10^{-3}$** for IR QSOs |
| Fraction of single-dish flux recovered | ~80 | not stated | % | 2 | our interferometric data typically recover $\sim$ 80% of the observed single-dish flux |
| MBH/Mdyn range | 0.02-0.36 (median 0.08) | not stated | % | 7 | ranging from 0.02% to 0.36% with a median value of 0.08% |

## Qualitative findings

- Hosts divide into rotating disks, compact disturbed CO, and mergers with companions  
  > "which can be roughly classified into three categories" (abstract)

## Claim tuples

- H: Are IR QSO hosts resolved in CO and is 3-mm continuum more compact than the gas? | E: Band 3 imaging and uv-plane size fits | R: All 8 resolved in CO (median 3.2 kpc); continuum sizes 0.4-1.0 kpc | F: Continuum more centrally concentrated than molecular gas | **supported**
- H: Do IR QSO hosts show rotation-dominated gas? | E: 3D-BAROLO fits to isolated hosts | R: Three hosts have Vrot/sigma = 4-6 | F: Rotation-dominated in those three | **supported**
- H: Are BH accretion and star formation connected? | E: Macc vs SFR for local and high-z QSOs | R: Slope 1.68±0.17, Spearman 0.77 | F: Trend indicates likely direct AGN-SF connection | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fit visibilities directly to avoid imaging-reconstruction uncertainties in sizes  
  > "To avoid possible uncertainties produced by the image reconstruction process that will be introduced into the size measurement" (3.4)
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamical masses depend strongly on inclination and disk assumption; classification based on small sample  
  > "These estimates of $M_{\rm dyn}$ can be significantly affected by the uncertainty of inclination and the assumption of a rotating disk" (3.5)
- Caveat (inferred, ours): Single constant alpha_CO=0.8 applied to all, including possible AGN-excited gas
- Caveat (inferred, ours): Dynamical masses from crude size and linewidth estimators; Gaussian sizes underestimate extended gas
- Caveat (inferred, ours): Macc-SFR fit mixes heterogeneous literature samples and methods; low-z SFRs partly CO-based
- Caveat (inferred, ours): Inclination from CO axis ratio is uncertain

## Reproducibility

- Data public (paper): ALMA project data cited; archive proprietary status not discussed  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01147.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: BAROLO settings
- Missing: high-z comparison compilation
- Missing: line-free channels
- Data volume (inferred): ~50-100 GB raw for 8 Band 3 targets (pipeline products smaller)
- Score (inferred): 3/5, Single public project and standard CASA steps, but imaging and BAROLO details are missing and the SFR-accretion part relies on external compilations.
- Rediscovery candidate: yes, Archive data from one project; the recipe (imaging, uv size fits, dynamical mass formulae) is mostly specified and the results are numeric.

## Links

- Method: (cite: diteodoro15) (3D-BAROLO tilted-ring fitting)
- Method: (cite: martividal14) (UVMULTIFIT visibility fitting)
- Companion: (cite: xia12) (IRAM 30m CO survey of the IR QSO parent sample)
- Companion: (cite: hao05) (IR QSO sample, BH masses and Lbol)
- Related: IRAM 30m CO survey of IR QSOs (Xia+12)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
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
  "facts": 87,
  "stated": 59,
  "rate": 0.678
 },
 "evidence_ok": true
}
```
