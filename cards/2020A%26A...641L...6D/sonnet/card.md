# Discovery of molecular gas fueling galaxy growth in a protocluster at z = 1.7

`2020A&A...641L...6D` | Astronomy and Astrophysics 2020 | first author: D'Amato, Q. | arXiv: 2008.13665 | DOI: 10.1051/0004-6361/202038711

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Are there additional gas-rich members of the z=1.7 overdensity around the FRII radio galaxy, and how much molecular gas is in them and in the FRII host?  
  > "In order to detect other overdensity members and possibly unveil large gas reservoirs, we obtained new Atacama Large Millimeter/submillimeter Array (ALMA) observations of the region" (1 Introduction)
- Target **FRII radio galaxy and J1030+0524 field overdensity**: coordinates _not stated_; z/distance z=1.6987  
  > "high-redshift radio galaxy (HzRG) at z=1.6987, located at the center of the so-called J1030+0524 field" (1 Introduction); distance from LUCI optical redshift  
  > "high-redshift radio galaxy (HzRG) at z=1.6987, located at the center of the so-called J1030+0524 field" (1 Introduction)

## Data provenance

- ALMA projects: 2018.1.01601.S
- bands: Band 3 (84 – 116 GHz), three-pointing mosaic  
  > "We performed a three-pointing mosaic observations with ALMA Band 3 (84 – 116 GHz) during Cycle 6" (2 Observations and data analysis)
- frequencies and spectral setup: 2 x 4 GHz spws covering 84.1–87.7 and 98.0–99.9 GHz; 1920 channels of 976.5 kHz (3.2 km/s)  
  > "Each *spw* is sampled in 1920 channels of 976.5 kHz width, corresponding to 3.2 km/s at the mean frequency of the *spws*." (2 Observations and data analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 2.161 x 1.655 arcsec (robust 0.5)  
  > "corresponding to a restoring beam with a major (minor) axis of 2.161 (1.655) arcsec" (2.1 Imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: six ~50.5 min execution blocks  
  > "The observations consist of six ${\sim}50.5$ min execution blocks" (2 Observations and data analysis)
- observing dates: 18, 28 and 31 December 2018  
  > "carried out on $18^{\mathrm{}}$ (two execution blocks), $28^{\mathrm{}}$ (one execution block), and $31^{\mathrm{}}$ (three execution blocks) December 2018" (2 Observations and data analysis)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **HST**: i, z, H images; counterparts, H magnitude and z-H colour  
  > "All galaxies have an optical counterpart; their HST $H$-band magnitude $H_{AB}$ and color index $z-H$ are reported in Table" (2.2 S/N cube and detections)
- Other facility **VLT/MUSE**: spectroscopic members of overdensity (from earlier work)  
  > "Based on spectroscopic data obtained with the Very Large Telescope Multi Unit Spectroscopic Explorer (MUSE)" (1 Introduction)
- Other facility **Chandra**: deep 480 ks X-ray data, diffuse emission  
  > "By means of deep (480 ks) *Chandra* observations of the field, they also discovered an X-ray diffuse emission" (1 Introduction)
- Other facility **VLA**: 1.4 GHz radio map of FRII  
  > "from deep 1.4 GHz Very Large Array (VLA) observations of the field" (1 Introduction)
- External data: CO(2-1) luminosity function used to estimate interlopers  
  > "based on the CO luminosity functions derived by the ASPECS project (cite: decarli_2019)" (2.2 S/N cube and detections) [from (cite: decarli_2019)]
- External data: r21 = 0.76  
  > "We assumed $r_{21}=0.76$ from the study of star-forming disk galaxies at z=1.5 by (cite: daddi_2015)" (3 Results) [from (cite: daddi_2015)]
- External data: X-ray column density N_H,X ~1.5e24 cm^-2 and MUSE members from Gilli et al.  
  > "derived from the X-ray spectrum ($N_{H,X}{\sim}~1.5 \times 10^{24}~ \mathrm{cm^{-2}}$; )" (4.2 FRII host galaxy) [from (cite: gilli_2019)]

## Processing

### Calibration

- pipeline or manual: CASA calibration pipeline  
  > "We performed the data calibration and flagging through the calibration pipeline of the Common Astronomy Software Applications (CASA) package" (2 Observations and data analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 and J1038+0512 (flux/bandpass and phase)  
  > "The quasars J1058+0133 and J1038+0512 served as flux and bandpass and phase calibrator, respectively." (2 Observations and data analysis)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "The robust weighting was set to 0.5" (2.1 Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: polynomial fit to remaining spectral range, subtracted  
  > "The continuum, estimated from the remaining observed spectral range, was fit using a polynomial and subtracted from the data set" (2.1 Imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 30 km/s channel width, ±3000 km/s around 85.426 GHz  
  > "A 30 km/s channel width was chosen for the datacube" (2.1 Imaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Virial mass procedure  
  > "following the procedure of (cite: cucciati_2018), finding $M_{sys,vir} {\sim}6 \times 10^{13}~\mathrm{M_\odot}$" (4.1 Gas-rich members) [from (cite: cucciati_2018)]
- Position uncertainty formula  
  > "The 1$\sigma$ uncertainty on the detection position is set to $0.5$ $\times$ $\langle FWHM \rangle$ $\times$ $\mathrm{S/N}^{-1}$ (cite: papadopoulos_2008)" (2.2 S/N cube and detections) [from (cite: papadopoulos_2008)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- tclean parameters: cell size, image size, deconvolver, threshold, masking
- polynomial order and line-free channels for continuum subtraction
- MCMC settings and priors
- HST reduction (Morishita et al. in prep.)
- how the ALMA luminosity-based 3 sigma mass upper limits were computed in detail

## Analysis recipe

1. **make continuum-subtracted datacube**: Datacube of full mosaic within ±3000 km/s of 85.426 GHz, polynomial continuum subtraction, 30 km/s channels, robust 0.5  
  > "we therefore produced a datacube (with the CASA task) of the entire FoV covered by the mosaic, within ${\pm 3000}$ km/s" (2.1 Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **detect line emitters**: Custom sliding-window code on S/N cube (local rms in 10-beam regions); reliability assessed with negative cube; grid of S/N_w, N_ch, N_px  
  > "The detection code works as follows: first, it scans each pixel of each channel (i.e., each spaxel) of the S/N cube" (5.1 S/N cube and source detection code)
   - parameter: S/N_w=1.5-3.0, N_ch=2-4, N_px=2-4  
  > "$\mathrm{N_{ch}} = 2, 3, 4$ (corresponding to 60, 90, and 120 km/s, respectively) and $\mathrm{N_{px}} = 2, 3, 4$" (5.1 S/N cube and source detection code)
   - fitting: _not stated_
   - validation: Keep only detections with no negative detections at the same parameters; interloper estimate from ASPECS  
  > "A conservative detection criterion is to select only the sources found with any given parameter set for which no negative detection are found." (5.1 S/N cube and source detection code)
3. **extract and fit spectra**: 3σ-blanked cube defines the extraction region; integrated spectra fit with single or double Gaussian  
  > "we performed a Markov chain Monte Carlo (MCMC) fit of the integrated spectra exploiting the Python package (cite: foreman_2013), using either a single or double Gaussian model" (2.3 Spectral analysis and moments)
   - software: emcee
   - fitting: _not stated_
   - validation: _not stated_
4. **derive line luminosity and H2 mass**: L'CO from Solomon 1992 formula; M_H2=(alpha_CO/r21) L'  
  > "We derived the molecular hydrogen mass as $M_{H_2}$ = $(\alpha_{CO}/r_{21})$ $L'_{CO(2-1)}$ $M_{\odot}$" (3 Results)
   - assumption: r21=0.76, alpha_CO=4.3  
  > "a Galactic $\alpha_{\rm CO}=4.3$ $\mathrm{~M_{\odot}~(K~km~s^{-1}~pc^2)^{-1}}$" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **size of FRII CO emission**: 2D Gaussian fit of 3σ moment 0 with CASA task, deconvolved  
  > "We derived its angular size performing a 2D Gaussian fit of the 3$\sigma$ moment 0 with the CASA task ." (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
6. **SFR, system mass and column density**: SFR from Schmidt-Kennicutt relation using gas mass and size; virial mass from velocity dispersion; N_H,ISM for edge-on thin disk  
  > "We therefore decided to derive an upper limit for the column density assuming an edge-on disk" (4.2 FRII host galaxy)
   - assumption: disk diameter = a, height 1 kpc, inclination 90 deg  
  > "we assumed a thin disk having the diameter equal to $a$ and constant height equal to 1 kpc" (4.2 FRII host galaxy)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration pipeline, imaging, continuum subtraction, 2D Gaussian fit  
  > "through the calibration pipeline of the Common Astronomy Software Applications (CASA) package" (2 Observations and data analysis)
- **emcee** : MCMC fit of spectra (Foreman-Mackey et al. 2013)  
  > "exploiting the Python package (cite: foreman_2013)" (2.3 Spectral analysis and moments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| FRII core M_H2 | 19.3e10 (alpha_CO/4.3, 0.76/r21 scaled) | +0.1/-0.1 | Msun | 4 | 19.3$\mathrm{^{+0.1}_{-0.1}}$ |
| FRII CO major axis | 3.2 (27 kpc) | 2.0 arcsec (17 kpc) | arcsec | 5 | major axis $a =$ $3.2 \pm 2.0$ arcsec and a minor axis $b =$ $2.0 \pm 1.6$ arcsec |
| LOS velocity dispersion | ~440 | not stated | km/s | 6 | we derive a line-of-sight (LOS) velocity dispersion of ${\sim}$440 km/s |
| N_H,ISM | ~5.5e23 | not stated | cm^-2 | 6 | We found $N_{H,ISM}{\sim}~5.5 \times 10^{23} ~\mathrm{cm^{-2}}$. |
| mean system redshift | 1.694 | 0.001 | dimensionless | 0 | The mean redshift of the system (including all the known members) is z = 1.694 $\pm$ 0.001. |

## Qualitative findings

- ALMA-detected members all have red HST counterparts; no CO detected in MUSE UV-bright members  
  > "we do not detect any molecular gas reservoir around the known UV-bright, star-forming members discovered by MUSE" (abstract)

## Claim tuples

- H: ALMA reveals new gas-rich members of the overdensity | E: Band 3 CO(2-1) mosaic, blind detection | R: three new CO sources at z=1.6925-1.6864 plus FRII core, with M_H2 1.5-4.8e10 Msun | F: Overdensity has 11 members | **supported**
- H: FRII is the BCG progenitor | E: Compare gas, position, velocity, stellar mass | R: central, large gas reservoir, velocity offset ~200 km/s | F: FRII is the likely BCG progenitor | **partially**
- H: Host ISM contributes to nuclear obscuration | E: Edge-on disk column density from gas mass and size | R: N_H,ISM ~5.5e23 vs N_H,X ~1.5e24 | F: ISM may contribute significantly | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Large uncertainty on FRII source size; alpha_CO may be lower for FRII  
  > "Because of the large uncertainty on the source size, the inclination angle and disk thickness of the molecular gas are unconstrained" (4.2 FRII host galaxy)
- Caveat (inferred, ours): FRII size only marginally resolved
- Caveat (inferred, ours): Galactic alpha_CO assumed for all, including AGN host
- Caveat (inferred, ours): SFRs from SK relation with poorly known sizes
- Caveat (inferred, ours): Total mass estimates rely on strong assumptions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Detection code not released
- Missing: tclean parameters
- Missing: MCMC priors
- Missing: HST data not yet published
- Data volume (inferred): ~10-50 GB
- Score (inferred): 4/5, Archival ALMA data and clear formulae, but imaging parameters, versions and custom code are missing.
- Rediscovery candidate: yes, Public ALMA project code, numeric results (line fluxes, masses), mostly complete recipe.

## Links

- Companion: (cite: gilli_2019) (Discovery of overdensity and MUSE members)
- Companion: (cite: nanni_2018) (Radio and X-ray analysis of the FRII)
- Related: ASPECS
- Related: J1030+0524 field

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 36,
  "rate": 0.468
 },
 "evidence_ok": true
}
```
