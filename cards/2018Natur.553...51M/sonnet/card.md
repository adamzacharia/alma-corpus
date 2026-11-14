# Galaxy growth in a massive halo in the first billion years of cosmic history

`2018Natur.553...51M` | Nature 2018 | first author: Marrone, D. P. | arXiv: 1712.03020 | DOI: 10.1038/nature24629

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the structure, physical conditions, masses and host halo rarity of the z=6.900 dusty galaxy SPT0311-58, resolved with high-resolution ALMA imaging?  
  > "High-resolution imaging reveals this source to be a pair of extremely massive star-forming galaxies." (abstract)
- Target **SPT0311-58 (E and W)**: coordinates SPT-S J031132-5823.4  
  > "The frequencies and spacings of these lines unambiguously place the galaxy at $z=6.900(2)$, corresponding to a cosmic age of 780 Myr" (main text); z/distance z = 6.900(2)  
  > "The frequencies and spacings of these lines unambiguously place the galaxy at $z=6.900(2)$, corresponding to a cosmic age of 780 Myr" (main text); distance from ALMA band 3 spectral scan (CO and [CI] lines), Strandet et al. 2017  
  > "The frequencies and spacings of these lines unambiguously place the galaxy at $z=6.900(2)$, corresponding to a cosmic age of 780 Myr" (main text)

## Data provenance

- ALMA projects: 2015.1.00504.S, 2016.1.01293.S
- bands: Bands 3, 6, 7, 8 (84-432 GHz)  
  > "in four receiver bands (B3, B6, B7, B8, covering 84 to 432 GHz)" (Methods, ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-1 (B3), C40-4 (B7), C40-5 (B6), C40-4 (B8)  
  > "in ALMA configuration C36-1 (baseline lengths of 15-310 meters)" (Methods, ALMA); "The 158 $\mu\rm{m}$ line of \[C\] was observed on 2016 November 3 in ALMA configuration C40-5, which provided baseline lengths of 18–1120 meters." (Methods, ALMA Millimeter/Submillimeter Interferometry)
- baselines: _not stated_
- angular resolution: B3 3.3x3.5 arcsec; B7 0.3x0.5; B6 0.25x0.30; B8 0.2x0.3  
  > "0.25$\times$0.30" (Table 1); "The resulting data have 0.2$\times$0.3$^{\prime\prime}$ resolution." (Methods, ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms in 7.5 GHz continuum image: B3 35, B6 24, B7 12, B8 53 uJy/beam  
  > "Root-mean-square noise level in 7.5 GHz continuum image" (Table 1)
- time on source: B6 32.4 min; B7 6.5 min; B8 11.4+3x33.7 min; B3 1.0-1.5 min per tuning  
  > "2016-Nov-03 | 233.65 | 45 | 0.25$\times$0.30 | J0334-4008 | J0303-6211 | 0.5 | 32.4 | 24" (Table 1)
- observing dates: 2015 Dec 28, 2016 Jan 2 (B3); 2016 Nov 3 (B6); 2016 Nov 15-17 (B8)  
  > "Data were taken on 2015 December 28 and 2016 January 2 in ALMA configuration C36-1" (Methods, ALMA)
- pi or archival as stated: Cycle 3 project PI Strandet; Cycle 4 project PI Marrone  
  > "under projects 2015.1.00504.S (PI: Strandet) and 2016.1.01293.S (PI: Marrone)" (Methods, ALMA)
- Line: [CII] 158 um fine-structure (not stated)
- Line: [OIII] 88 um fine-structure (not stated)
- Other facility **HST ACS/WFC3**: Rest-UV/optical imaging of lens and SPT0311-58E  
  > "SPT0311–58 was observed for 5 orbits of *HST* imaging with ACS and WFC3/IR in Cycle 24" (Methods, HST Imaging)
- Other facility **Spitzer IRAC**: 3.6 and 4.5 um imaging  
  > "The observations consisted of 95 dithered 100 s exposures on-source in both operable IRAC arrays at 3.6 and 4.5 $\mu\rm{m}$." (Methods, Spitzer)
- Other facility **Gemini GMOS/FLAMINGOS-2**: i, z, Ks imaging and GMOS spectroscopy  
  > "we obtained deep $i$ and $z$ images of SPT0311–58" (Methods, Gemini)
- Other facility **Herschel SPIRE**: 250-500 um photometry for SED  
  > "we use *Herschel* photometry reported previously(cite: strandet17) to constrain the SED" (Methods, Lens Modeling)
- External data: Joint continuum/line modelling gas and dust masses of SPT0311-58 (total)  
  > "the best constraints on both of these quantities come from the joint analysis(cite: strandet17) of its far-infrared continuum and line emission" (main text) [from Strandet et al. 2017 (cite: strandet17)]
- External data: Dust and gas masses of comparison z>5 galaxies taken from literature  
  > "Mass estimates are literature values unmodified from the original publications" (Methods, Galaxy and Halo Masses) [from (cite: wang11; wang11b; walter12; riechers13; watson15; venemans16; venemans17; laporte17; decarli17)]
- External data: Herschel SPIRE photometry of SPT0311-58  
  > "we use *Herschel* photometry reported previously(cite: strandet17)" (Methods, Lens Modeling) [from (cite: strandet17)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (B3), J0334-4008 (B6), J2258-2758 (B7), J0538-4405 (B8)  
  > "2016-Nov-03 | 233.65 | 45 | 0.25$\times$0.30 | J0334-4008 | J0303-6211 | 0.5 | 32.4 | 24" (Table 1)
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
- final beam: B6 0.25x0.30; B7 0.31x0.49; B8 0.20x0.30 arcsec  
  > "2016-Jun-04 | 343.48 | 41 | 0.31$\times$0.49" (Table 1)
- final rms: 24 uJy/beam (B6), 12 (B7), 53 (B8) in 7.5 GHz continuum  
  > "Root-mean-square noise level in 7.5 GHz continuum image" (Table 1)

### Inherited from earlier work

- B3 spectral scan strategy and redshift coverage  
  > "further details on the redshift coverage are provided in previous works(cite: weiss13; strandet16)" (Methods, ALMA) [from (cite: weiss13; strandet16)]
- B3 data analysis details  
  > "Further details of the analysis are provided by Strandet et al.(cite: strandet17)." (Methods, ALMA) [from Strandet et al. (cite: strandet17)]
- visilens lens modelling code  
  > "Initial lens models were created using the `visilens` code, which is described in detail elsewhere(cite: spilker16)." (Methods, Lens Modeling) [from (cite: spilker16)]
- Rareness calculation method  
  > "we employ the method of Ref. (cite: harrison13)" (Methods, Halo Rareness) [from (cite: harrison13)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging procedure (tclean parameters, weighting, robust, cell/image size, masks)
- Continuum-subtraction and line-free channels for [CII] and [OIII]
- Self-calibration usage
- Spectral setups for B6/B8 beyond LO frequencies
- Pixellated lens code is proprietary; regularization and prior details not given
- Aperture used to measure intrinsic flux densities
- Lens model priors and MCMC settings

## Analysis recipe

1. **Lens modelling of continuum**: Fit visibilities with visilens (Sersic source components, SIE lens, MCMC), then pixellated reconstruction with gradient regularization at 160 and 90 um; 110 um reconstructed with fixed deflections  
  > "After determining the lens parameters using `visilens`, we used the best-fit values as initial input to a pixellated reconstruction code(cite: hezaveh16)." (Methods, Lens Modeling)
   - software: visilens, pixellated reconstruction code (proprietary)
   - parameter: Four Sersic components (1 E, 3 W) for visilens  
  > "modeled with four Sérsic components, one for the SPT0311–58E and three for W." (Methods, Lens Modeling)
   - assumption: Lens is a singular isothermal ellipsoid  
  > "the lens galaxy is modeled as a singular isothermal ellipsoid" (Methods, Lens Modeling)
   - fitting: MCMC sampling marginalizing over residual calibration uncertainty  
  > "posterior parameter distributions are sampled using a Markov Chain Monte Carlo technique" (Methods, Lens Modeling)
   - validation: Lens parameters consistent to <10% between wavelengths; source properties agree to <15% between codes  
  > "intrinsic source flux densities, sizes, and magnifications that agree to $<$15%" (Methods, Lens Modeling)
2. **Channelized [CII] lens modelling**: Pixellated reconstruction of 39 channels of 40 km/s using 160 um lens deflections, regularization fit per channel  
  > "using 39 consecutive channels of 40 km/s width, each with a peak signal-to-noise ranging from 9–34." (Methods, Lens Modeling)
   - software: pixellated reconstruction code (proprietary)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive magnifications**: Flux-weighted source-averaged magnifications from 90 um pixellated model  
  > "We determine the source magnifications using the 90 $\mu\rm{m}$ pixellated model" (Methods, Lens Modeling)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED modelling for LIR, SFR and stellar mass**: CIGALE fits with BC03, Chabrier IMF, Draine&Li dust, Calzetti attenuation, AGN fraction fixed to zero; lens photo-z with EAZY  
  > "The lens SED fitting is performed with the Code Investigating GALaxy Emission (CIGALE(cite: burgarella05; noll09)) assuming $z=1.43$." (Methods, SED)
   - software: CIGALE, EAZY
   - assumption: Solar metallicity, AGN contribution set to zero  
  > "The AGN contribution is set to zero as there are no photometric points to constrain the spectral range most affected by AGN power" (Methods, SED)
   - fitting: _not stated_
   - validation: Modified blackbody fit of FIR SED gives consistent LIR for W  
  > "A consistent luminosity is obtained by fitting the FIR SED with a modified blackbody(cite: blain03)." (Methods, SED)
5. **Gas, dust masses and halo masses**: Divide total masses by continuum ratio (6.7); alternative CO(3-2)->1-0 with alpha_CO=1.0; halo mass from gas mass/f_b=0.19 or M_b/M_halo=0.05  
  > "the cosmic baryon fraction(cite: planck16cosmo) $f_{\rm b}=0.19$ places a hard lower bound on the total halo mass of $4\times10^{11}$ $M_\odot$" (main text)
   - assumption: alpha_CO = 1.0 Msun (K km/s pc^2)^-1, thermalized CO emission  
  > "converting to $J=1-0$ under the conservative assumption of thermalized emission" (main text)
   - fitting: _not stated_
   - validation: _not stated_
6. **Halo rareness exclusion curves**: Harrison & Hotchkiss '>nu' statistic with Tinker08 mass function, Planck cosmology, 1 sigma curves for full sky, 2500 and 25 deg^2  
  > "we employ the ‘$>\nu$’ measure" (Methods, Halo Rareness)
   - software: hh13-cluster-rareness (matlab)
   - assumption: SPT sample complete for z>1.5 and Mhalo>1e11 Msun  
  > "We assume that the SPT sample of lensed DSFGs is complete for $z > 1.5$." (Methods, Halo Rareness)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **visilens** : Initial lens modelling of visibilities  
  > "The lensing reconstruction for the ALMA data was initially performed with the visilens code" (Code Availability)
- **CIGALE** 0.11.0: SED modelling  
  > "The SED modeling used the CIGALE code (<https://cigale.lam.fr/>), version 0.11.0." (Code Availability)
- **EAZY** : Photometric redshift of lens  
  > "The photometric redshift of the lens galaxy was estimated with EAZY" (Code Availability)
- **GALFIT** : Deblending Spitzer images  
  > "The image deblending for the *Spitzer* images used GALFIT" (Code Availability)
- **Source Extractor** : IRAC photometry  
  > "Photometry was performed on the mosaics using Source Extractor(cite: bertin96)" (Methods, Spitzer)
- **IRACproc/MOPEX** : IRAC mosaics  
  > "combined in the standard way(cite: ashby13) with IRACproc(cite: schuster06) and MOPEX" (Methods, Spitzer)
- **FATBOY** : FLAMINGOS-2 reduction  
  > "The data were reduced using the python-based FLAMINGOS-2 Data Pipeline, FATBOY" (Methods, Gemini)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Redshift | 6.900 | 0.002 | dimensionless | 0 | place the galaxy at $z=6.900(2)$ |
| Magnification E / W / total | 1.3 / 2.2 / 2.0 | not stated | dimensionless | 3 | $\mu_{\rm E} = 1.3$, $\mu_{\rm W} = 2.2$, $\mu_{\rm tot} = 2.0$ |
| Einstein radius | 0.29 | not stated | arcsec | 1 | The lens model for this source indicates $\theta_{E}=0.29$$^{\prime\prime}$ |
| LIR (E) | 4.6e12 | 1.2e12 | Lsun | 4 | $(4.6\pm 1.2)\times 10^{12}$ $L_\odot$ |
| LIR (W) | 33e12 | 7e12 | Lsun | 4 | ${{L}_{\rm IR}}=\ensuremath{(33\pm 7)\times 10^{12}}$ $L_\odot$ |
| SFR E / W | 540 / 2900 | 175 / 1800 | Msun/yr | 4 | 540$\pm$175 and 2900$\pm$1800 $M_\odot$ yr$^{-1}$ |
| Stellar mass E | 3.5e10 | 1.5e10 | Msun | 4 | $(3.5\pm 1.5)\times 10^{10}$ $M_\odot$ |
| Gas mass W (joint model) | 2.7e11 | 1.7e11 | Msun | 5 | $M_{\rm gas} = \ensuremath{(2.7\pm 1.7)\times 10^{11}}$ (W) |
| Dust mass W | 2.5e9 | 1.6e9 | Msun | 5 | $M_{\rm dust} = \ensuremath{(2.5\pm 1.6)\times 10^{9}}$ (W) |
| Gas mass W (CO, alpha_CO=1) | 6.6e10 | 1.7e10 | Msun | 5 | $M_{\rm gas} = \ensuremath{(6.6\pm 1.7)\times 10^{10}}$ (W) |
| Halo mass lower bound | 4e11 | not stated | Msun | 5 | places a hard lower bound on the total halo mass of $4\times10^{11}$ $M_\odot$ |
| Source-plane separation of E and W | 8 | not stated | kpc | 1 | the two galaxies are separated by a projected (proper) distance of 8 kpc in the source plane |

## Qualitative findings

- SPT0311-58E is separated from W by 700 km/s in [CII] and is a distinct galaxy; E has much higher [OIII]/[CII] consistent with lower metallicity  
  > "SPT0311–58E is separated from the brighter W source by 700 km s$^{-1}$ and is therefore a distinct galaxy." (main text)

## Claim tuples

- H: Is SPT0311-58 a single lensed system or two galaxies? | E: High-resolution ALMA continuum and [CII] imaging plus lens modelling | R: Two sources separated by 8 kpc and 700 km/s | F: A merging pair of massive dusty galaxies at z=6.9 | **supported**
- H: Is W more massive than any other z>6 galaxy? | E: Divide gas and dust masses by continuum ratio, compare with literature | R: Mgas ~2.7e11 Msun for W | F: W stands out above all known z>6 galaxies | **supported**
- H: Do the two galaxies have different physical conditions? | E: Compare [OIII], [CII] and continuum maps | R: E has much larger [OIII]/[CII] and [CII]/continuum | F: E resembles lower-metallicity galaxies | **partially**
- H: Is the host halo extremely rare in LCDM? | E: Halo mass from gas mass and Harrison & Hotchkiss exclusion curves | R: Halo mass >4e11 Msun, closest to exclusion curves | F: Marks an exceptional density peak but does not rule out LCDM | **supported**

## Reasoning

- Why this data: High-resolution multi-band imaging needed to resolve structure; B7 alone insufficient for lens configuration  
  > "lacking any spectral lines it was found to be insufficient to provide an unambiguous determination of the lensing configuration." (Methods, ALMA)
- Why this method: _not stated_
- Alternative: AGN contribution to IR luminosity rejected on morphological grounds  
  > "so we deem this wide range to be unphysical" (Methods, SED)
- How they decided it was enough: _not stated_
- Limitation (authors): IRAC fluxes for W unreliable due to blending with lens; stellar mass of W unconstrained  
  > "we do not believe the *Spitzer*/IRAC fluxes to be reliable" (Methods, Image de-blending)
- Caveat (inferred, ours): Gas and dust masses split between E and W by a continuum ratio from low-resolution joint model
- Caveat (inferred, ours): Halo mass relies on assumed baryon fractions
- Caveat (inferred, ours): Low magnification makes lens model systematics modest but uncertainties on W SFR are large
- Caveat (inferred, ours): alpha_CO assumed

## Reproducibility

- Data public (paper): ALMA and HST data public via archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01293.S and ADS/JAO.ALMA#2015.1.00504.S" (Data Availability)
- Products in archive: _not stated_
- Code: visilens public; pixellated lens code proprietary and not released; rareness code public  
  > "Pixelated reconstructions were performed using a proprietary code developed by a subset of the authors and additional non-authors, and we opt not to release this code in connection with this work." (Code Availability)
- Missing: Proprietary pixellated lens code
- Missing: CASA imaging parameters
- Missing: Joint continuum/line model details (Strandet et al. 2017)
- Data volume (inferred): ~50-200 GB raw for four bands across two projects
- Score (inferred): 3/5, Public data and public rareness code, but imaging recipe unstated and key lens code proprietary.
- Rediscovery candidate: no, Imaging details missing and the pixellated lens code is proprietary, though visilens could partially reproduce the lens results.

## Links

- Method: Hezaveh et al. 2016 (cite: hezaveh16) (Pixellated lens reconstruction)
- Method: Spilker et al. 2016 (cite: spilker16) (visilens)
- Method: Harrison & Hotchkiss 2013 (cite: harrison13) (Halo rareness)
- Companion: Strandet et al. 2017 (cite: strandet17) (Discovery, redshift and joint gas/dust modelling)
- Related: South Pole Telescope 2500 deg2 survey

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 52,
  "rate": 0.591
 },
 "evidence_ok": true
}
```
