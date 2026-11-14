# The High Molecular Gas Content, and the Efficient Conversion of Neutral into Molecular Gas, in Jellyfish Galaxies

`2020ApJ...897L..30M` | The Astrophysical Journal Letters 2020 | first author: Moretti, Alessia | arXiv: 2006.13612 | DOI: 10.3847/2041-8213/ab9f3b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Do the molecular gas content of four GASP jellyfish galaxies follow the scaling relations of normal galaxies, or are they depleted/enriched in molecular gas?  
  > "we analyze the ALMA Band 3 data of the four GASP galaxies observed in cycle 5 to understand whether their molecular gas content is following the scaling relations of normal galaxies" (Introduction)
- Target **JO201, JO204, JO206, JW100**: coordinates _not stated_; z/distance z~0.05  
  > "Stellar masses and redshifts are given in (cite: gaspX)" (Introduction); distance from redshifts from GASP paper (cite: gaspX)  
  > "Stellar masses and redshifts are given in (cite: gaspX)" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00496.S
- bands: Band 3  
  > "we analyze the ALMA Band 3 data of the four GASP galaxies observed in cycle 5" (Introduction)
- frequencies and spectral setup: CO(1-0); velocity resolution 3.1 km/s smoothed to 20 km/s; mosaics  
  > "The spectral configuration used yields a velocity resolution of 3.1 km/s, which has been smoothed to 20 km/s in the final datacubes" (Data and analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams ~1.3-2.0 arcsec (~1 kpc)  
  > "JO201 | 110.307 | 1.99 | 1.57 | -84.6 | 0.5 | 20" (Table 1)
- max recoverable scale: 20-24 arcsec (Table 1)  
  > "JW100 | 108.644 | 2 | 1.7 | 8.3 | 0.9 | 24" (Table 1)
- sensitivity: rms 0.5-0.9 mJy/beam  
  > "JO206 | 109.677 | 1.60 | 1.30 | -87.4 | 0.7 | 23" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 1-0 (115.271 GHz)
- Other facility **VLT/MUSE**: Halpha maps, SFRs, metallicities, disk definition  
  > "ESO program 196.B-0578 (VLT/MUSE)" (Acknowledgments)
- Other facility **MeerKAT / HI data**: HI masses (preliminary for JW100)  
  > "(preliminary from MeerKat data for JW100)" (2 H2/HI)
- External data: xCOLDGASS molecular gas fractions for field galaxies  
  > "mean values found for starforming main sequence galaxies in the xCOLDGASS sample by (cite: Saintonge2017)" (Results) [from (cite: Saintonge2017)]
- External data: SFRs from star-forming spaxels  
  > "SFRs measured within the disk using the star forming spaxels from (cite: vulcani+2018_sf)" (Results) [from (cite: vulcani+2018_sf)]
- External data: Virgo cluster H2 data  
  > "The Virgo cluster data by (cite: Corbelli+2012)" (Results) [from (cite: Corbelli+2012)]
- External data: xGASS Rmol in spiral disks  
  > "values in spiral disks derived from the xGASS sample assuming a radial fit to the HI mass distribution (cite: Wang+2020)" (2 H2/HI) [from (cite: Wang+2020)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.4.0-7  
  > "The data have been calibrated and imaged using the CASA software (version 5.4.0-7; McMullin 2007)" (Data and analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% on measured fluxes  
  > "The uncertainty on the measured fluxes is of the order of $10\%$." (Data and analysis)
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
- smoothing: velocity smoothed to 20 km/s  
  > "which has been smoothed to 20 km/s in the final datacubes" (Data and analysis)
- final beam: see Table 1 (e.g. 1.99x1.57 arcsec JO201)  
  > "JO201 | 110.307 | 1.99 | 1.57 | -84.6 | 0.5 | 20" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging  
  > "as described in (cite: GASPXXII)" (Data and analysis) [from (cite: GASPXXII)]
- SoFiA detection masks for moment-zero maps  
  > "as described in (cite: GASPXXII) for JW100" (Data and analysis) [from (cite: GASPXXII)]
- Disk definition from stellar isophote  
  > "We use here as disk definition the one given in Gullieuszik+ submitted" (Data and analysis) [from Gullieuszik+ submitted]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, deconvolver, cell, masking)
- continuum subtraction and line-free channels
- SoFiA parameters
- flux calibrators and self-calibration
- luminosity distances used
- metallicity calibrations and alpha_CO values per galaxy details
- integrated CO fluxes not tabulated

## Analysis recipe

1. **Make CO(1-0) cubes and moment-0 maps**: CASA calibration/imaging, SoFiA masks, moment-zero  
  > "using the SoFiA software (cite: sofia) to construct detection masks for each ALMA datacube" (Data and analysis)
   - software: CASA, SoFiA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive H2 masses in disk and tail**: Watson & Koda 2016 relation with alpha_CO variants  
  > "we have used the CO(1-0) emission to derive the CO flux and the $\rm H_{2}$ mass using the following equation from (cite: WatsonKoda2016)" (Results)
   - assumption: alpha_CO = 4.3 (MW), Accurso2017 metallicity-dependent, Amorin2016 low values  
  > "First, we used the Milky Way $\alpha_{CO}$ that is equal to 4.3" (Results)
   - assumption: distance from main sequence 0.15 dex  
  > "we assumed the average value found for jellyfish galaxies in (cite: vulcani+2018_sf), i.e. 0.15 dex" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare gas fractions and depletion times with field galaxies**: f_H2 = MH2/Mstar and tau_dep = MH2/SFR compared to xCOLDGASS  
  > "depletion times, defined as $M_{\rm H_2}/SFR$" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute Rmol and total gas fractions**: Rmol=MH2/MHI vs xGASS; sum of H2+HI vs Catinella2018  
  > "disk molecular gas fraction $R_{mol}=M_{H_2}/M_{HI}$ of these three galaxies" (2 H2/HI)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0-7: calibration and imaging  
  > "calibrated and imaged using the CASA software (version 5.4.0-7; McMullin 2007)" (Data and analysis)
- **SoFiA** : detection masks for moment-zero maps  
  > "using the SoFiA software (cite: sofia) to construct detection masks" (Data and analysis)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2 mass in disk (MW alpha_CO) JO201 | 16.5e9 | not stated | Msun | 2 | 16.5\[46%\] |
| H2 depletion time JW100 (alpha_CO=4.3) | 9.1 | not stated | Gyr | 3 | 23.7\[ 8%\] / 0.6% / 9.1 |
| Rmol range in disks | 4 to ~100 | not stated | dimensionless | 4 | $R_{mol}$ in the disk of our galaxies turns out to be very high (ranging from 4 to $\sim 100$ ) |
| f_H2 enhancement vs xCOLDGASS (MW alpha_CO) | ~5 | not stated | dimensionless | 3 | higher than the mean values in xCOLDGASS galaxies by an average factor of $\sim 5$ |

## Qualitative findings

- Total gas (H2+HI) is normal for stellar mass, suggesting efficient HI to H2 conversion by ram pressure  
  > "the total gas (molecular+neutral) associated to our jellyfish galaxies (considering both what is left in the disk and what is in the tail) is normal for their stellar mass" (2 H2/HI)

## Claim tuples

- H: Jellyfish galaxies have molecular gas content like normal galaxies | E: CO(1-0) ALMA H2 masses vs xCOLDGASS | R: f_H2 ~4-5 times higher; 8-24e9 Msun | F: Jellyfish disks are H2 rich unless alpha_CO is very low | **supported**
- H: Ram pressure efficiently converts HI into H2 | E: Rmol and total gas fraction vs normal spirals | R: Rmol 4 to ~100, total gas normal | F: efficient HI to H2 conversion | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Ram pressure unbinding GMCs gives lower alpha_CO; tested with Amorin2016 formulation  
  > "ram-pressure acting on the infalling galaxies could in principle unbind the already existing giant molecular clouds (GMCs) in the galaxy disk" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): No single-dish CO(1-0) data so fluxes are lower limits  
  > "We do not have single dish data at the CO(1-0) frequency to assess the possible flux loss, and therefore our data are, strictly speaking, lower limits." (Data and analysis)
- Caveat (inferred, ours): Results depend heavily on alpha_CO; low-alpha_CO values extrapolated beyond calibration
- Caveat (inferred, ours): Only four galaxies, all with AGN
- Caveat (inferred, ours): Metallicity calibration differs from that used by Accurso2017
- Caveat (inferred, ours): HI data preliminary

## Reproducibility

- Data public (paper): ALMA project code given, public status not stated  
  > "ADS/JAO.ALMA#2017.1.00496.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (deferred to GASPXXII)
- Missing: Integrated CO fluxes
- Missing: Distances
- Missing: HI masses, SFRs and disk masks from other papers
- Data volume (inferred): ~100 GB raw for four mosaics
- Score (inferred): 3/5, Data identified and key equation given, but processing deferred to other papers and external inputs needed.
- Rediscovery candidate: no, Recipe incomplete and relies on unpublished/external inputs.

## Links

- Method: (cite: GASPXXII) (ALMA calibration, imaging and SoFiA analysis)
- Method: (cite: WatsonKoda2016) (H2 mass equation)
- Companion: (cite: gaspX) (APEX CO and stellar masses/redshifts)
- Companion: (cite: GASPXXVIII) (HI data)
- Related: GASP
- Related: xCOLDGASS
- Related: xGASS

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 34,
  "rate": 0.472
 },
 "evidence_ok": true
}
```
