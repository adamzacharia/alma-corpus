# MeerKAT HI commissioning observations of MHONGOOSE galaxy ESO 302-G014

`2020A&A...643A.147D` | Astronomy and Astrophysics 2020 | first author: de Blok, W. J. G. | arXiv: 2009.09766 | DOI: 10.1051/0004-6361/202038894

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: What is the H I morphology of dwarf galaxy ESO 302-G014 in MeerKAT commissioning data, and does it indicate a minor interaction or accretion?  
  > "We used the available H i data sets, along with ancillary data at other wavelengths, to study the morphology of the MHONGOOSE sample galaxy, ESO 302-G014, which is a nearby gas-rich dwarf galaxy." (abstract)
- Target **ESO 302-G014**: coordinates 03 51 40.90 -38 27 08.0 (J2000, Appendix table)  
  > "The galaxy has a recessional velocity of $871$ km s$^{-1}$, translating into an assumed distance of 11.7 Mpc, as derived in (cite: meurer_et_al_2006) from the heliocentric velocity using the model by (cite: mould_et_al_2000)." (2 ESO 302-G014); z/distance 11.7 Mpc (871 km/s)  
  > "The galaxy has a recessional velocity of $871$ km s$^{-1}$, translating into an assumed distance of 11.7 Mpc, as derived in (cite: meurer_et_al_2006) from the heliocentric velocity using the model by (cite: mould_et_al_2000)." (2 ESO 302-G014); distance from Meurer et al. 2006 using Mould et al. 2000 flow model  
  > "The galaxy has a recessional velocity of $871$ km s$^{-1}$, translating into an assumed distance of 11.7 Mpc, as derived in (cite: meurer_et_al_2006) from the heliocentric velocity using the model by (cite: mould_et_al_2000)." (2 ESO 302-G014)

## Data provenance

- ALMA projects: 2017.1.00129.S
- bands: ALMA Band 3 (total power)  
  > "The ALMA 12-m total power (TP) array observations were carried out as part of a programme to observe 64 Fornax galaxies in band 3" (2 ESO 302-G014)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 54 arcsec, velocity resolution 2.9 km/s  
  > "The angular resolution of the TP observations is $54''$, and the velocity resolution 2.9 km s$^{-1}$." (2 ESO 302-G014)
- max recoverable scale: _not stated_
- sensitivity: 0.16 Jy/beam in 10 km/s channels  
  > "The noise level is 0.16 Jy beam$^{-1}$ in channels of 10 km s$^{-1}$." (2 ESO 302-G014)
- time on source: _not stated_
- observing dates: May 2018, 2h45m  
  > "The TP on-the-fly observations were carried out for 2$^h$45$^m$ in May 2018 with three 12m-antennae." (2 ESO 302-G014)
- pi or archival as stated: Archival; PI K. Morokuma  
  > "as part of the project 2017.1.00129.S (PI K. Morokuma)" (2 ESO 302-G014)
- Line: CO J=1-0 (not stated)
- Other facility **MeerKAT**: H I commissioning data (MeerKAT-16, 64 4k, 64 32k) and 1.4 GHz continuum  
  > "The first commissioning observations of ESO 302-G014 were done in early 2018 with the MeerKAT-16 array." (3 MeerKAT observations)
- Other facility **HST**: ACS/WFC3 images in four filters  
  > "The HST data consist of a ACS/WFC3 pointing in four filters (F606W, F336W, F657N, F160W)" (2 ESO 302-G014)
- Other facility **DECaLS**: g, r, z optical images  
  > "we used data from the Dark Energy Camera Legacy Survey (DECaLS; (cite: dey_et_al_2019))." (2 ESO 302-G014)
- External data: SINGG R-band and Halpha data, SFR, distance and HI mass  
  > "an H i mass of $3 \cdot 10^8$ $M_{\odot}$(cite: meurer_et_al_2006)" (2 ESO 302-G014) [from (cite: meurer_et_al_2006)]
- External data: GBT HI flux  
  > "a flux of $10.4 \pm 0.4$ Jy km s$^{-1}$($3.4 \cdot 10^8$ $M_{\odot}$) was derived." (4.2 Fluxes and total H i masses) [from (cite: sorgho_et_al_2019)]

## Processing

### Calibration

- pipeline or manual: ALMA data calibrated with CASA (MeerKAT data with CARACal)  
  > "The data were calibrated with the Common Astronomy Software Applications (CASA, (cite: mcmullin_et_al_2007))." (2 ESO 302-G014)
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
- smoothing: CO spectrum integrated over 130x130 arcsec area centred on optical position  
  > "an integrated CO spectrum was produced by integrating over an area of $130'' \times
130''$ centered on the optical position." (2 ESO 302-G014)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- H I mass uncertainties derived with the prescription of Koribalski et al.  
  > "Uncertainties in the integrated fluxes and H i masses were derived for the MeerKAT-16 and 32k data using the prescription given in (cite: koribalski_et_al_2004)." (4.2 Fluxes and total H i masses) [from (cite: koribalski_et_al_2004)]

### Not stated but needed to reproduce (our reading)

- CASA version for the ALMA TP calibration
- Exact CO conversion factor and line-integration velocity range
- How the 32 +/- 5 Jy km/s uncertainty was derived
- ALMA CO line rest frequency and SPW setup

## Analysis recipe

1. **CO flux to molecular gas mass**: Integrated CO(1-0) spectrum over 130x130 arcsec; Solomon & Vanden Bout Eq. 3 with standard CO-to-H2 factor  
  > "Using Eq. 3 from (cite: solomon_et_al_2005) and a standard CO-to-H$_2$ conversion factor, we find the molecular gas mass to be $4.6 \cdot 10^7\,M_\odot$" (5.3 A potential link with star formation)
   - software: CASA
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration of ALMA TP data  
  > "The data were calibrated with the Common Astronomy Software Applications (CASA, (cite: mcmullin_et_al_2007))." (2 ESO 302-G014)
- **CARACal** pre-release: MeerKAT data reduction  
  > "The data were reduced using a pre-release version of the Containerized Automated Radio Astronomy Calibration (CARACal) pipeline" (3.1 MeerKAT-16 observation)
- **SoFiA** : source finding and moment maps of MeerKAT cubes  
  > "The map was created using the SoFiA source finder (cite: serra_et_al_2015)." (4 Description of the HI data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated CO(1-0) flux | 32 | 5 | Jy km/s | 1 | we find an integrated CO$(J=1-0)$ flux $S({\rm CO})\,dV$ of $32 \pm 5$ Jy km/s |
| Molecular gas mass | 4.6e7 | not stated | Msun | 1 | we find the molecular gas mass to be $4.6 \cdot 10^7\,M_\odot$ |
| Molecular to atomic mass ratio | ~0.12 | not stated | dimensionless | 1 | The molecular to atomic mass ratio is $\sim 0.12$ |

## Qualitative findings

- Disc is regular at high column density but lopsided at low column density, with a western HI filament and an isolated southern cloud  
  > "we find that ESO 302-G014 has a lopsided, asymmetric outer disc with a low column density." (abstract)

## Claim tuples

- H: Is there significant molecular gas supporting a recent interaction-triggered star formation? | E: Integrated ALMA TP CO(1-0) spectrum and converted to H2 mass | R: CO flux 32 +/- 5 Jy km/s; M(H2)=4.6e7 Msun, nearly equal to stellar mass | F: Significant molecular gas supports an interaction scenario with a low-mass companion | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Ram pressure stripping considered unlikely to explain the morphology  
  > "In summary, ram pressure stripping is, therefore, not expected to play a major role in defining the H i morphology of ESO 302-G014." (5.1 Ram pressure stripping scenario)
- How they decided it was enough: _not stated_
- Limitation (authors): Possible dwarf companion association cannot be confirmed with current data  
  > "but based on the current data, we cannot confirm any association with ESO 302-G014." (abstract)
- Caveat (inferred, ours): Molecular mass relies on an unspecified standard CO-to-H2 factor, likely too low for a low-metallicity dwarf
- Caveat (inferred, ours): ALMA TP CO is marginally resolved at 54 arcsec, so the flux is a single integrated number

## Reproducibility

- Data public (paper): ALMA data described as archival  
  > "has led to the availability of much archival data for this galaxy, including observations by ALMA and HST." (2 ESO 302-G014)
- Products in archive: _not stated_
- Missing: CO conversion factor, velocity range for integration, CASA version and TP imaging parameters
- Data volume (inferred): <10 GB for the ALMA TP part
- Score (inferred): 3/5, The ALMA part is a minor single-number CO measurement with sparse processing details.
- Rediscovery candidate: no, The ALMA recipe is incomplete and the main results come from MeerKAT.

## Links

- Method: (cite: jozsa_et_al_2020) (CARACal pipeline)
- Method: (cite: serra_et_al_2015) (SoFiA source finder)
- Companion: (cite: de_blok_et_al_2016) (MHONGOOSE survey description)
- Related: MHONGOOSE
- Related: HALOGAS
- Related: SINGG

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 25,
  "rate": 0.424
 },
 "evidence_ok": true
}
```
