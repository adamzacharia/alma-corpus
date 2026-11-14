# Probing the Relationship Between Early Star Formation and CO in the Dwarf Irregular Galaxy WLM with JWST

`2024AJ....167..274A` | The Astronomical Journal 2024 | first author: Archer, Haylee N. | arXiv: 2404.12482 | DOI: 10.3847/1538-3881/ad3f18

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: How does early star formation (JWST NIR clumps) relate to CO cores and FUV in the low-metallicity dwarf irregular galaxy WLM?  
  > "(2) the relationship between early star formation and CO in low metallicity environments." (Introduction)
- Target **WLM (Wolf-Lundmark-Melotte)**: coordinates _not stated_; z/distance approximately 980 kpc  
  > "Wolf-Lundmark-Melotte (WLM) is a nearby dwarf irregular galaxy (dIrr) in the Local Group at a distance of approximately 980 kpc (cite: Leaman_2012; Lee_2021)." (Introduction); distance from Leaman et al. 2012; Lee et al. 2021  
  > "Wolf-Lundmark-Melotte (WLM) is a nearby dwarf irregular galaxy (dIrr) in the Local Group at a distance of approximately 980 kpc (cite: Leaman_2012; Lee_2021)." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00208.S, 2018.1.00337.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beam 0.9" x 1.3" (Cycle 1), 0.6" x 0.5" (Cycle 6)  
  > "The beam size was $0.9\ensuremath{''} \times 1.3\ensuremath{''}$ for Cycle 1 and $0.6\ensuremath{''} \times 0.5\ensuremath{''}$ for Cycle 6" (2.1 CO cores)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (Cycle 1) (not stated)
- Line: CO J=2-1 (Cycle 6) (not stated)
- Other facility **JWST NIRCam (ERS 1334)**: F090W, F150W, F250M, F430M images  
  > "The F090W ($\lambda = 0.9\ \mu m$), F150W ($\lambda = 1.5\ \mu m$), F250M ($\lambda = 2.5\ \mu m$), and F430M ($\lambda = 4.3\ \mu m$) NIRCam images come from" (2.2 JWST ERS #1334)
- Other facility **GALEX**: FUV image  
  > "The FUV image comes from the NASA Galaxy Evolution Explorer (*GALEX*[^1]) satellite" (2.3 FUV)
- Other facility **Spitzer IRAC**: 8 micron image  
  > "We examined our objects in a Spitzer Infrared Array Camera (IRAC) 8 $\mu$m image of WLM" (Discussion)
- External data: CO core catalog (35 cores from CO(2-1), CPROPS properties)  
  > "Rubio et al. (in preparation) used the CPROPS algorithm (cite: Rosolowsky_2006) in the ALMA CO(2–1) data-cube to identify the molecular clouds." (2.1 CO cores) [from Rubio et al. in preparation]
- External data: 10 CO(1-0) cores  
  > "Further details on the CO(1–0) detection are described by (cite: Rubio_2015)." (2.1 CO cores) [from (cite: Rubio_2015)]
- External data: SEDs of normal, AGN and starburst galaxies used for IR bolometric correction  
  > "we found the luminosity of each object using the SEDs from Table 2 of (cite: Xu_2001)" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates) [from (cite: Xu_2001)]

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

- ALMA CO data reduction and cloud identification taken from companion work  
  > "Further details on the CO(1–0) detection are described by (cite: Rubio_2015)." (2.1 CO cores) [from (cite: Rubio_2015); Rubio et al. in preparation]
- JWST observations and image processing  
  > "Further information on the ERS program and acquired images can be found in (cite: Weisz_2023)." (2.2 JWST ERS #1334) [from (cite: Weisz_2023)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and CASA details (from Rubio et al. in prep)
- Aperture definitions and sizes for each object (drawn visually)
- Criteria for visually deciding near/away from CO
- PROSPECTOR priors and fixed metallicity
- Conversion of CO luminosity to molecular mass

## Analysis recipe

1. **Define object types**: Visual identification of NIR clumps on a three-color JWST image, classified by FUV knots and CO cores  
  > "The determination of whether a NIR object is near or away from a CO core is made visually" (2.4 Object types)
   - fitting: _not stated_
   - validation: _not stated_
2. **Aperture photometry**: APPHOT aperture photometry with aperture matched to object size; converted to AB mag  
  > "The size of the aperture for each object corresponded to the size of the object" (2.4 Object types)
   - software: IRAF
   - parameter: 4% NIRCam zeropoint uncertainty  
  > "We calculated our uncertainties using photon statistics convolved with the known 4% NIRCam zeropoint uncertainty" (2.4 Object types)
   - fitting: _not stated_
   - validation: Background galaxy contamination estimated ~0.14 per object  
  > "this equates to about 0.14 unresolved background galaxies within each object." (2.4 Object types)
3. **Blackbody temperatures from colors**: Planck law with synthetic photometry for F090W–F150W and F250M–F430M  
  > "We calculated the blackbody temperatures corresponding to the color for the given filters using the Planck law and the OBSERVATE routine" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
   - software: sedpy
   - fitting: _not stated_
   - validation: _not stated_
4. **Masses from TIR luminosity**: Summed JWST luminosity times ~4 to get TIR, divided by bolometric luminosity per solar mass of 1 Myr population  
  > "We then took the TIR luminosity divided by this conversion for bolometric luminosity per solar mass of young stars at 1 Myr to get the mass of our objects." (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
   - parameter: SED-to-JWST ratio ~4  
  > "which we found to be approximately 4, to convert the summed luminosities in the four *JWST* bands to total IR (TIR) luminosities" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
   - assumption: Age 1 Myr, bolometric magnitude -2.69 (SMC metallicity)  
  > "Taking the bolometric magnitude of a young stellar population at less than 1 Myr age to be -2.69 for Small Magellanic Cloud (SMC) metallicity of 20% solar" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
   - fitting: _not stated_
   - validation: Compared with PROSPECTOR masses; 10 Myr test  
  > "Increasing the age to 10 Myr, which changes the bolometric magnitude of the stellar population from -2.69 to +0.81, increases the mass of the object" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
5. **Comparison masses with SED fitting**: PROSPECTOR SSP fit, free mass, dust optical depth, age; fixed metallicity  
  > "The mass, diffuse dust *V*-band optical depth, and age were free parameters." (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
   - software: prospector, dynesty
   - fitting: Dynamic nested sampling with dynesty  
  > "We used dynamic nested sampling with the Python package DYNESTY" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
   - validation: Ages and optical depths unreasonable, so TIR masses adopted  
  > "We found that the optical depths and ages derived from this method were not reasonable for our objects" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)

## Software

- **IRAF APPHOT** : Aperture photometry  
  > "using the Image Reduction and Analysis Facility (IRAF) (cite: Tody_1986) routine APPHOT" (2.4 Object types)
- **sedpy** : Synthetic photometry for blackbody temperatures  
  > "OBSERVATE routine from the Python package SEDPY" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
- **prospector** : SED fitting masses  
  > "SED fitting toolbox PROSPECTOR" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
- **dynesty** : Nested sampling  
  > "We used dynamic nested sampling with the Python package DYNESTY" (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
- **CPROPS** : CO cloud identification (Rubio et al., in prep)  
  > "used the CPROPS algorithm (cite: Rosolowsky_2006) in the ALMA CO(2–1) data-cube to identify the molecular clouds" (2.1 CO cores)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Type 1 objects overlapping 8 micron sources | 60 | not stated | % | 0 | For type 1 objects, 60% overlap 8 $\mu$m sources and 40% overlap $V$ sources |
| Type 2 objects overlapping 8 micron sources | 15 | not stated | % | 0 | For type 2 objects, 15% overlap 8 $\mu$m sources and 48% overlap $V$ sources |
| Type 3 objects overlapping 8 micron sources | 5 | not stated | % | 0 | For type 3 objects, 5% overlap 8 $\mu$m sources and 0% overlap $V$ sources |
| Type 1 object mass range | ~1 to 5930 | not stated | Msun | 4 | Type 1 objects range from approximately $1$ to $5930\ M_\odot$ |
| Type 2 object mass range | ~1 to 66 | not stated | Msun | 4 | cover a range of masses approximately $1$ to $66\ M_\odot$ |
| Type 3 object mass range | ~1 to 33 | not stated | Msun | 4 | Type 3 objects span the lowest range of masses from approximately $1$ to $33\ M_\odot$ |

## Qualitative findings

- Objects of all types have similar colors, magnitudes and temperatures  
  > "We find that objects of all three types have comparable NIR colors and magnitudes." (Summary and Conclusions)

## Claim tuples

- H: Objects near CO have different masses than objects away from CO | E: Compared TIR-luminosity masses of three object types | R: Type 1 objects have higher masses | F: Objects near CO are more massive, but PROSPECTOR masses show the same range for all types | **partially**
- H: Objects near CO are embedded clusters at earlier stage | E: Overlap with Spitzer 8 micron sources | R: 60% of type 1 vs 15% and 5% | F: Suggestive of earlier embedded stage, but ages are required | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: PROSPECTOR masses rejected because derived ages and optical depths unreasonable  
  > "As such, we opted to use the masses computed with the TIR method for this work." (2.5 Blackbody Temperature, Luminosity, and Mass Estimates)
- How they decided it was enough: _not stated_
- Limitation (authors): No accurate ages for the objects  
  > "However, we cannot be certain without accurate age estimates for the objects." (Discussion)
- Caveat (inferred, ours): Mass results depend strongly on assumed 1 Myr age and method
- Caveat (inferred, ours): Visual object/type classification is subjective
- Caveat (inferred, ours): Mass dependence on method undermines main claim
- Caveat (inferred, ours): Small samples per type

## Reproducibility

- Data public (paper): JWST data in MAST; ALMA CO catalog from unpublished work  
  > "All the *JWST* data used in this paper can be found in MAST" (2.2 JWST ERS #1334)
- Products in archive: _not stated_
- Missing: Cycle 6 CO core catalog unpublished (Rubio et al. in prep)
- Missing: Aperture positions and radii only partly tabulated
- Missing: PROSPECTOR settings
- Data volume (inferred): ~10 GB (JWST images; ALMA cubes not reprocessed)
- Score (inferred): 3/5, JWST data public and photometry recipe fairly clear, but visual selection, CO catalog from in-prep work, and ALMA used only via catalog.
- Rediscovery candidate: no, ALMA data used only as external catalog; visual selection and unpublished inputs.

## Links

- Method: (cite: Rosolowsky_2006) (CPROPS cloud identification)
- Method: (cite: Xu_2001) (SEDs for TIR correction)
- Companion: (cite: Rubio_2015) (CO(1-0) ALMA detection)
- Companion: (cite: archer_2022) (CO cores, FUV and HI in WLM)
- Companion: (cite: Weisz_2023) (JWST ERS program)
- Related: JWST Resolved Stellar Populations ERS (PID 1334)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "facts": 77,
  "stated": 33,
  "rate": 0.429
 },
 "evidence_ok": true
}
```
