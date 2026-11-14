# Emergence of an Ultrared, Ultramassive Galaxy Cluster Core at z = 4

`2020ApJ...898..133L` | The Astrophysical Journal 2020 | first author: Long, Arianna S. | arXiv: 2003.13694 | DOI: 10.3847/1538-4357/ab9d1f

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, star_formation
- Question: What are the stellar, gas and halo-mass properties of the individual DSFGs in the z=4.002 Distant Red Core protocluster, and how do they compare with field galaxies and the future evolution of the cluster?  
  > "We present here the first study analyzing stellar emission along with cold dust and gas continuum emission in a spectroscopically confirmed $z=4.002$ protocluster core rich with DSFGs" (abstract)
- Target **Distant Red Core (DRC, SGP-354388)**: coordinates _not stated_; z/distance z=4.002  
  > "The DRC core has a spectroscopic redshift of $z_\mathrm{spec}=4.002$, determined via ALMA 2 mm spectral scans" (4 Observations (ALMA)); distance from ALMA 2 mm spectral scans (Oteo et al. 2018)  
  > "The DRC core has a spectroscopic redshift of $z_\mathrm{spec}=4.002$, determined via ALMA 2 mm spectral scans" (4 Observations (ALMA))

## Data provenance

- ALMA projects: 2016.1.01287.S, 2013.1.00449.S, 2013.A.00014.S, 2013.1.00001.S
- bands: 2 mm (and 3 mm) continuum  
  > "S$\mathrm{_{2\,mm}}$" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: average synthesized beam 1.6 arcsec at 2 mm  
  > "carried out over two pointings, with an average synthesized beam size of $1.6^{\prime\prime}$" (2.5 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 6-5 (not stated)
- Other facility **HST WFC3 F125W**: 1.25 um imaging, new data  
  > "we used the F125W filter to observe a subset of eight ultra-red *Herschel* objects" (2.1 HST WFC3)
- Other facility **Gemini FLAMINGOS-2**: Ks-band imaging from Oteo et al.  
  > "we use the same reduced data presented in (cite: oteo18)" (2.2 Gemini FLAMINGOS-2)
- Other facility **Spitzer IRAC**: 3.6 and 4.5 um imaging  
  > "imaged the DRC at 3.6 $\mu$m and 4.5 $\mu$m" (2.3 Spitzer IRAC)
- Other facility **Herschel SPIRE (H-ATLAS)**: 250/350/500 um maps  
  > "Data Release 2 of the *H*-ATLAS survey" (2.4 Herschel SPIRE)
- External data: ALMA 2 mm and 3 mm flux densities, CO(6-5) luminosities and redshifts  
  > "As presented in (cite: oteo18), successful spectroscopic confirmation of DRC members required several spectral scans" (2.5 ALMA) [from (cite: oteo18)]
- External data: alpha_850 = 6.7e19 gas-mass calibration  
  > "We use the value given in Scoville et al. where $\alpha_{\mathrm{850 \mu m}} = 6.7\pm1.7 \times 10^{19}\,$erg s$^{-1}$ Hz$^{-1}$ M$_\odot^{-1}$" (5.2 Gas Properties) [from (cite: scoville)]

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

- ALMA data reduction and 2 mm photometry taken from earlier work  
  > "We refer the reader to (cite: oteo18) for the full chronicle, and briefly summarize the data used in this work below." (2.5 ALMA) [from (cite: oteo18)]
- Gemini Ks data reduction  
  > "we use the same reduced data presented in (cite: oteo18) (Section 2.5, therein)" (2.2 Gemini FLAMINGOS-2) [from (cite: oteo18)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (CASA version, weighting, clean) not given
- Exact 2 mm and 3 mm flux extraction method
- ALMA coordinates of each DRC component
- CIGALE grid values for stellar age and some module parameters

## Analysis recipe

1. **Near-IR photometry and counterpart matching**: SExtractor FLUX_ISO photometry; sum counterparts within 1.14 arcsec (8 kpc) of each ALMA 2 mm centroid  
  > "capturing all observed-frame near-IR bright objects within a physically motivated radius on the order of galactic scales: $\sim8$ kpc" (3.2)
   - software: SExtractor
   - fitting: _not stated_
   - validation: Compared with 2MASS stars, <10% difference  
  > "find a $<10\%$ difference in flux density estimates" (3.1)
2. **Deblend SPIRE and IRAC**: XID+ with ALMA priors for SPIRE; TPHOT with HST priors for IRAC  
  > "Using ALMA positional priors for each DRC component, we deblend the far-IR emission with the probabilistic deblender XID+" (3.3)
   - software: XID+, TPHOT, SExtractor, SWarp, PyPHER
   - fitting: _not stated_
   - validation: 85-100% IRAC flux recovered; residual maps inspected  
  > "we recover $85-100\%$ of the original IRAC flux" (3.4)
3. **SED fitting**: CIGALE with Chabrier IMF, delayed SFH, BC03, Calzetti attenuation, Draine dust models  
  > "a (cite: chabrier) IMF with a delayed star formation history; the (cite: bruz03) stellar population synthesis models" (4 SED Modeling)
   - software: CIGALE
   - fitting: Bayesian; S/N<2 as upper limits  
  > "Detections with S/N $<2$ are used as upper limits in the SED fitting process" (4 SED Modeling)
   - validation: Reduced chi2<2 except DRC-2; checked vs rest-frame H-band mass-to-light  
  > "all of the best-fit model SEDs have reduced $\chi^{2} < 2$, except for DRC-2 with $\chi^{2}_\mathrm{red} \approx 3$" (4 SED Modeling)
4. **Molecular gas masses from 2 mm dust continuum**: Scoville et al. RJ-tail method  
  > "We derive molecular gas masses using the method outlined in (cite: scoville)." (5.2)
   - assumption: Td = 25 K mass-weighted dust temperature  
  > "assumed to be 25 K to be consistent with other work" (5.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Halo mass estimates**: Behroozi abundance matching, summed or single halo, and 5% baryon fraction  
  > "We use the stellar-to-halo abundance matching relationship in (cite: behroozi)" (6)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CIGALE** : SED fitting  
  > "We use the CIGALE (cite: cigale; cigale3; cigale2) SED modeling tool" (4 SED Modeling)
- **XID+** : SPIRE deblending  
  > "we deblend the far-IR emission with the probabilistic deblender XID+" (3.3)
- **TPHOT** : IRAC deblending  
  > "we deblend the IRAC photometry using TPHOT" (3.4)
- **SExtractor** : source extraction  
  > "we use the SOURCE EXTRACTOR package (cite: setractor) in single-image mode" (3.1)
- **Astropy** : general analysis  
  > "This research made use of Astropy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average stellar mass | 9e10 | ±6e10 | Msun | 3 | averaging at $9\pm6\times10^{10}$ M$_\odot$ |
| Average molecular gas mass | 1.76e11 | ±2.36e11 | Msun | 4 | average M$_\mathrm{H_2} = 1.76\pm2.36\times10^{11}$ M$_\odot$ |
| Mean gas depletion time | 260 | ±180 | Myr | 4 | deplete their gas in an average of $\sim260\pm180$ Myr |
| Summed halo mass (abundance matching) | 5e13 | ±2e13 | Msun | 5 | total cluster halo mass of $5\pm2\times10^{13}$ M$_{\odot}$ |
| Average gas fraction | 52 | ±20 | percent | 4 | average f$_\mathrm{gas}=52\pm20\%$ |

## Qualitative findings


## Claim tuples

- H: Are DRC members more massive or more star-forming than field galaxies? | E: SED fitting and comparison to main-sequence samples | R: Members are massive, within 1 sigma of the main sequence | F: Protocluster galaxies are a high-mass extension of the main sequence | **supported**
- H: Will the DRC become an ultra-massive cluster? | E: Halo mass estimates and evolution tracks | R: z=4 halo ~1e14 Msun; z=0 >=1e15 | F: DRC is a massive cluster progenitor | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): SED fits are degenerate, with the mid-IR unconstrained  
  > "complex SED modeling techniques can be highly degenerate when there are more free parameters than data points to constrain them" (4 SED Modeling)
- Caveat (inferred, ours): Gas masses depend on assumed Td=25 K
- Caveat (inferred, ours): Summing multiple counterparts may overestimate stellar mass
- Caveat (inferred, ours): Halo masses beyond the calibration range of abundance matching

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CIGALE parameter grids not fully listed
- Missing: ALMA flux extraction not described
- Data volume (inferred): ~10-50 GB if ALMA products are used
- Score (inferred): 3/5, Mostly SED fitting on literature and non-ALMA data; ALMA fluxes are inherited.
- Rediscovery candidate: no, Depends on ALMA fluxes from another paper and on unspecified CIGALE settings.

## Links

- Method: (cite: scoville) (gas mass method)
- Method: (cite: oteo18) (ALMA data and redshifts)
- Companion: (cite: oteo18) (original DRC ALMA study)
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 29,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
