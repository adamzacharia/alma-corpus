# The Redshift and Star Formation Mode of AzTEC2: A Pair of Massive Galaxies at z = 4.63

`2020ApJ...890..171J` | The Astrophysical Journal 2020 | first author: Jiménez-Andrade, E. F. | arXiv: 2001.06997 | DOI: 10.3847/1538-4357/ab6dec

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the redshift of the SMG AzTEC2, and what star formation mode (cold gas accretion vs merger) drives its two components?  
  > "to unveil the redshift and conditions for star formation in AzTEC2." (1. INTRODUCTION)
- Target **AzTEC2-A and AzTEC2-B**: coordinates A: 10:00:08.042 +02:26:12.19; B: 10:00:07.842 +02:26:13.32  
  > "RA, Dec hh:mm:ss.sss, dd:mm:ss.ss 10:00:08.042 +02:26:12.19 10:00:07.842 +02:26:13.32" (Table 1); z/distance z = 4.626 (A), 4.633 (B)  
  > "RA, Dec hh:mm:ss.sss, dd:mm:ss.ss 10:00:08.042 +02:26:12.19 10:00:07.842 +02:26:13.32" (Table 1); distance from CO(5-4) and [CII] lines (this work)  
  > "RA, Dec hh:mm:ss.sss, dd:mm:ss.ss 10:00:08.042 +02:26:12.19 10:00:07.842 +02:26:13.32" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00568.S
- bands: ALMA Band 7 (887 um)  
  > "ALMA Band 7 observations (project 2015.1.00568.S, PI: C. Casey)" (3. OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: 335.5-339.5 GHz and 347.5-351.5 GHz  
  > "covered the frequency ranges of 335.5 − 339.5 GHz and 347.5 − 351.5 GHz." (3. OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: 12 m main array, two configurations  
  > "The 12 m main array was used in two different configurations" (3. OBSERVATIONS AND DATA REDUCTION)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median beam 0.23 x 0.18 arcsec2 (PA=51 deg)  
  > "a median restoring beam of 0.23 × 0.18 arcsec 2 (PA=51 ◦ )" (3. OBSERVATIONS AND DATA REDUCTION)
- max recoverable scale: ~4.7 arcsec  
  > "maximum recoverable angular scale of ∼4.7 arcsec" (3. OBSERVATIONS AND DATA REDUCTION)
- sensitivity: 1 sigma ~ 1 mJy/beam per 50 MHz channel  
  > "We reached a final sensitivity of 1 σ ≃ 1 mJy beam −1 for a 50 MHz channel width" (3. OBSERVATIONS AND DATA REDUCTION)
- time on source: _not stated_
- observing dates: April 23 and September 1, 2016  
  > "were conducted on April 23 and September 1, 2016." (3. OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: CO 5-4 (not stated)
- Line: [CII] 2P3/2-2P1/2 (not stated)
- Other facility **NOEMA**: Band 1 CO(5-4) spectra and 2.9 mm continuum, 1.7x0.9 arcsec resolution  
  > "Follow-up observations were hence taken with NOEMA in Band 1 over two tracks on January 26 and 29, 2019" (3. OBSERVATIONS AND DATA REDUCTION)
- Other facility **LMT/RSR**: tentative CO(5-4) detection at z~4.6  
  > "revealed a tentative detection of the 12 CO(5 → 4) line emission at z ∼ 4.6." (3. OBSERVATIONS AND DATA REDUCTION)
- External data: COSMOS photometric catalog (24um-21cm) used in SED fit  
  > "information from the COSMOS photometric catalog compiled by Jin et al. (2018) and Liu et al. (2018)" (4.3) [from Jin et al. (2018); Liu et al. (2018)]
- External data: 2 mm GISMO-2 photometry  
  > "The photometric measurement at 2 mm recently obtained with the GISMO-2 bolometer camera (Magnelli et al. 2019) is also included" (4.3) [from Magnelli et al. 2019]
- External data: L[CII]/LIR = 7 (+4/-2)e-4 for 4<z<5 SMGs  
  > "(see compilation in Table B.1 of Lagache et al. 2018)" (4.3) [from Lagache et al. 2018]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline scripts with CASA  
  > "Data re duction and imaging were performed following the standard steps of the ALMA reduction pipeline scripts with CASA." (3. OBSERVATIONS AND DATA REDUCTION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5  
  > "a Briggs weighting (robust=0.5) was used" (3. OBSERVATIONS AND DATA REDUCTION)
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
- final beam: 0.23 x 0.18 arcsec2 (PA=51 deg)  
  > "a median restoring beam of 0.23 × 0.18 arcsec 2 (PA=51 ◦ )" (3. OBSERVATIONS AND DATA REDUCTION)
- final rms: _not stated_

### Inherited from earlier work

- SED fitting procedure and Monte Carlo sampling (N=15000)  
  > "by following the SED fitting procedure presented by Liu et al. (2018)" (4.3) [from Liu et al. (2018)]
- LMT/RSR data reduction  
  > "Data reduction was performed in a similar way as described in Zavala et al. (2015, 2018)." (3. OBSERVATIONS AND DATA REDUCTION) [from Zavala et al. (2015, 2018)]

### Not stated but needed to reproduce (our reading)

- CASA version
- tclean parameters (cell, image size, masks, niter, threshold)
- continuum-subtraction and line-free channels
- visibility weights/flux calibrators
- Visilens lens model parameters
- rest frequencies adopted
- CO excitation ratio basis
- NOEMA/GILDAS version

## Analysis recipe

1. **estimate lensing magnification**: Visilens modelling of each foreground galaxy as isothermal ellipsoid  
  > "We use the Visilens code (Spilker et al. 2016) to estimate the gravitational amplification factor" (4.1)
   - software: Visilens
   - assumption: Einstein mass = 2.5 M*  
  > "assuming the Einstein mass to be 2.5 M ⋆ (Auger et al. 2009)" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **measure lines and redshifts**: 2D Gaussian fits to moment maps and Levenberg-Marquardt Gaussian line fits of spectra extracted in apertures 1.5x FWHM  
  > "Through a least-squares algorithm (Levenberg-Marquardt), we find that a model with two Gaussian components describes better the line profile" (4.2)
   - fitting: two Gaussians for A (chi2 2.0 vs 2.6 single); single for B  
  > "yielding a reduced χ 2 of 2.0 and 2.6, respectively" (4.2)
   - validation: CO and [CII] lines combine to unambiguous redshift  
  > "we can unambiguously associate them with 12 CO(5 → 4) and [C II]" (4.2)
3. **molecular gas mass**: CO(5-4) corrected for CMB (1/0.8), L'CO(1-0)=L'CO(5-4)/0.32, Mgas=alphaCO L'  
  > "Then, L ′ CO(1 → 0) = [1/0.32] × L ′ CO(5 → 4)" (4.3)
   - assumption: alphaCO = 2.5, Tkin~40 K  
  > "Here we adopt a mean α CO = 2.5 M ⊙ K −1 km −1 s pc −2" (4.3)
   - fitting: _not stated_
   - validation: compared with dust-based gas mass (gas-to-dust 100)  
  > "These values are in good agreement with the M gas estimates derived from our" (4.3)
4. **LIR, Mdust, SFR**: mid-IR to mm SED fit with five components, then split between A and B by 887/2924 um ratio; SFR from Kennicutt 1998  
  > "We then fit the SED with five components" (4.3)
   - assumption: Chabrier IMF; qIR=2.4  
  > "Assuming a Chabrier Initial Mass Function" (4.3)
   - fitting: Monte Carlo sampling N=15000  
  > "The fitting is performed through Monte Carlo sampling (with N = 15000, following Liu et al. (2018))" (4.3)
   - validation: independent LIR from L[CII]/LIR ratio  
  > "these new and independent L IR estimates corroborate those derived via SED fitting." (4.3)
5. **[CII] kinematics and dynamical mass**: PV diagram along major axis (0.3 arcsec width), arctan rotation curve fit, inclination from dust ellipticity, Mdyn sin^2(i)=Rv^2/G at R=0.5 arcsec  
  > "We thus adopt the arctan model to fit the rotation curve of AzTEC2-A." (4.5)
   - assumption: gas and dust co-spatial; sigma<=100 km/s upper limit  
  > "Assuming a co-spatial distribution of interstellar dust and gas" (4.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA reduction and imaging  
  > "standard steps of the ALMA reduction pipeline scripts with CASA" (3. OBSERVATIONS AND DATA REDUCTION)
- **GILDAS** : NOEMA data reduction  
  > "The data reduction was performed with the software GILDAS using the NOEMA standard pipeline" (3. OBSERVATIONS AND DATA REDUCTION)
- **mapping** : NOEMA imaging, natural weighting  
  > "imaging was done with the package mapping using natural weighting" (3. OBSERVATIONS AND DATA REDUCTION)
- **Visilens** : lens magnification  
  > "We use the Visilens code (Spilker et al. 2016)" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| redshift AzTEC2-A | 4.626 | 0.001 | dimensionless | 2 | leading to a redshift solution of z = 4.626 ± 0.001 |
| redshift AzTEC2-B | 4.633 | 0.001 | dimensionless | 2 | for AzTEC2-B we estimate a redshift of z = 4.633 ± 0.001 |
| magnification A, B | 1.5, 1.35 | not stated | dimensionless | 1 | µ A = 1.5 (µ B = 1.35) |
| lensing-corrected Mgas(alphaCO/2.5) A | 2.1e11 | 0.4e11 | Msun | 3 | M gas ( α CO /2.5) = 2.1 ± 0.4 × 10 11 M ⊙ |
| SFR A (lensing-corrected) | 1920 | 100 | Msun/yr | 4 | SFR=1920 ± 100 M ⊙ yr − 1 |
| SFR B (lensing-corrected) | 710 | 35 | Msun/yr | 4 | (710 ± 35 M ⊙ yr − 1 ) |
| log(muLIR) total complex | 13.59 | 0.02 | log Lsun | 4 | log( µL IR /L ⊙ ) = 13.59 ± 0.02 |
| vrot de-projected | 660 | 130 | km/s | 5 | v rot int = v asym = 660 ± 130 km s −1 |
| inclination | 39 | 3 | deg | 5 | We then derive _i_ = arcsin(0 _._ 23 _±_ 0 _._ 02 _/_ 0 _._ 36 _±_ 0 _._ 02) = 39 _±_ 3 _[◦]_ |
| Mdyn | 2.6e11 | +1.2/-0.9e11 | Msun | 5 | dynamical mass of M dyn ( i = 39 ◦ ) = 2.6 |

## Qualitative findings

- Previous z~1 association is ruled out; AzTEC2 is a pair of massive galaxies at z~4.63 with a ~375 km/s offset  
  > "These robust line detections and counterpart association rule out the preliminary redshift solution" (4.2)

## Claim tuples

- H: Is AzTEC2 at z~1? | E: CO(5-4) with NOEMA and [CII] with ALMA | R: z=4.626 and 4.633 | F: Previous z=1.12 association ruled out | **supported**
- H: AzTEC2-A hosts a rotating disk | E: [CII] velocity field, PV arctan fit | R: vrot=660 km/s, sigma<=100, vrot/sigma>=5 | F: Rotation-dominated disk | **partially**
- H: Star formation mode is cold accretion vs merger | E: LIR/L'CO, KS plane, depletion times | R: A resembles massive disks like GN20 | F: Elevated accretion plus torques from companion likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: post-merger scenario cannot be excluded  
  > "A post-merger scenario, however, can not be excluded" (4.5)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA [CII] lines at spectral window edges; channels above +200 km/s missing, biasing kinematics  
  > "the absence of velocity channels above +200 km s −1 biases the spatial distribution of the [C II] line emission" (4.5)
- Caveat (inferred, ours): Arctan fit to partial rotation curve; vrot depends on dust-based inclination
- Caveat (inferred, ours): alphaCO and CO excitation assumed
- Caveat (inferred, ours): L_IR split between A and B assumes same SED
- Caveat (inferred, ours): Lens model simple

## Reproducibility

- Data public (paper): ALMA data cited by project code; NOEMA project W18EU  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2015.1.00568.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and tclean settings
- Missing: line-free channels and continuum subtraction
- Missing: lens model inputs
- Missing: PV extraction and arctan fit details
- Data volume (inferred): ~50-100 GB ALMA raw data (one Band 7 project)
- Score (inferred): 4/5, Public data and simple analysis, but imaging and fitting settings are sparse.
- Rediscovery candidate: no, Key results require NOEMA data and external photometry; imaging settings are incomplete.

## Links

- Method: Liu et al. (2018) (SED fitting procedure)
- Method: Spilker et al. (2016) (Visilens)
- Companion: Brisbin et al. 2017 (earlier ALMA imaging of AzTEC2)
- Related: COSMOS
- Related: AzTEC
- Related: ALPINE

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 43,
  "rate": 0.566
 },
 "evidence_ok": true
}
```
