# From Gas to Stars in Energetic Environments: Dense Gas Clumps in the 30 Doradus Region within the Large Magellanic Cloud

`2014ApJ...793...37A` | The Astrophysical Journal 2014 | first author: Anderson, Crystal N. | arXiv: 1406.4055 | DOI: 10.1088/0004-637X/793/1/37

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry, nearby_galaxies
- Question: Do dense gas clumps in 30Dor-10, under an extreme UV field and sub-solar metallicity, differ in properties from dense clumps in other LMC star-forming GMCs, and is the filament gravitationally unstable?  
  > "This extreme star-forming region, located in the Large Magellanic Cloud (LMC), is characterized by a very intense ultraviolet ionizing radiation field and sub-solar metallicity" (abstract)
- Target **30Dor-10 (30 Doradus, LMC)**: coordinates _not stated_; z/distance ~50 kpc  
  > "The Large Magellanic Cloud (LMC), is one of the closest galaxy (D$\sim$ 50 kpc)" (1 Introduction); distance from assumed distance to the LMC  
  > "The Large Magellanic Cloud (LMC), is one of the closest galaxy (D$\sim$ 50 kpc)" (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **ATCA**: HCO+(1-0) and HCN(1-0) mosaic maps of 30Dor-10 (primary data)  
  > "We observed the dense gas cloud, 30Dor-10 with the ATCA" (2 Observations and Data Reduction)
- Other facility **MAGMA (Mopra)**: CO data for bulk GMC properties  
  > "we therefore use MAGMA for calculations of the bulk properties of the entire GMC" (3.2.1 Fraction of Dense Gas)
- External data: ALMA 12CO, 13CO, C18O maps of 30Dor-10 and clump decomposition (103 CO sub-clumps), used for comparison  
  > "while the ALMA data resolve 103 CO sub-clumps" (4.1 30Dor-10 ALMA and ATCA Comparison) [from Indebetouw et al. 2013 (cite: 2013ApJ...774...73I)]
- External data: HCO+/HCN clump properties for N159, N113, N105A, N44  
  > "ATCA observations similar to ours were performed on the star forming regions N159, N105A, N44, and N113 by S12" (3.2 Clumps Properties) [from Seale et al. 2012 (cite: 2012ApJ...751...42S)]
- External data: YSO and H2O maser catalog  
  > "H$_{2}$O masers and YSO counterparts (Gruendl et al. 2009) are overlaid on Figure 2." (3 Results) [from Gruendl & Chu 2009 (cite: 2009ApJS..184..172G)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus  
  > "Flux calibration was performed using Uranus." (2 Observations and Data Reduction)
- flux scale uncertainty: ~50% absolute; <=10% relative between lines  
  > "The absolute flux calibration uncertainty is estimated to be $\sim$50%." (2 Observations and Data Reduction)
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
- final beam: 6.8" x 5.8" (1.6 pc x 1.4 pc)  
  > "giving a synthesized beam FWHM of 6.8$^{\prime\prime}$$\times$ 5.8$^{\prime\prime}$" (2 Observations and Data Reduction)
- final rms: 10 mJy/beam per 0.84 km/s channel  
  > "is 10 mJy/beam in a 0.84 km s$^{-1}$ channel." (2 Observations and Data Reduction)

### Inherited from earlier work

- Clump identification with CPROPS following the same method, for direct comparison  
  > "We follow the method of Wong et al. (2011) hereafter W11 and S12, respectively to facilitate direct comparison with these studies." (3.1 Clump Identification) [from Rosolowsky & Leroy 2006; Wong et al. 2011; Seale et al. 2012]
- Clump parameters (linewidth, virial mass, LTE mass, radius) derived as in S12  
  > "Following, S12, we derive the same clump properties i.e linewidth ($\Delta v$), virial mass (M$_{\rm vir}$), LTE mass (M$_{\rm LTE}$), and radius." (3.1.1 Clump Parameters) [from Seale et al. 2012]

### Not stated but needed to reproduce (our reading)

- CPROPS parameters (T_edge, threshold settings, extrapolation options)
- MIRIAD imaging parameters (weighting, cell, deconvolution, mosaic setup)
- Archive location of the ATCA data
- Filament length used for mass per unit length

## Analysis recipe

1. **Identify clumps**: CPROPS on HCO+ cube with 3 sigma dilated mask  
  > "Clump regions of significant emission in the ATCA data are identified by finding volume pixels ("voxels") with emission greater than a 3$\sigma$ threshold." (3.1 Clump Identification)
   - software: CPROPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive clump masses**: Virial mass 1040 sigma_v^2 R; LTE mass from HCO+ column density  
  > "M_{\rm vir}[M_{\odot}]=1040\sigma_{\rm v}^{2}\rm R" (3.1.1 Clump Parameters)
   - assumption: Tex = 30 K, X_HCO+ ~ 1e-9  
  > "An excitation temperature (T$_{\rm ex}$) of 30 K is adopted" (3.1.1 Clump Parameters)
   - fitting: _not stated_
   - validation: _not stated_
3. **Test filament stability and spacing**: Compare M/L to critical value 2cs^2/G; compare spacing to varicose instability wavelength  
  > "the virial mass per unit length of M$_{vir}/L \sim 10^{3}~ M_{\odot}$/pc which is much larger than the critical clump mass per unit length" (4.2 Filaments)
   - assumption: rho_c ~1e4 cm^-3 as in Nessie  
  > "assuming the same central volume density as in the "Nessie" filament, $\rho_{c}$$\sim$10$^{4}$ cm$^{-3}$" (4.2 Filaments)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : Data reduction, imaging, cube creation  
  > "Data were reduced, imaged and cubes created using ATNF MIRIAD software package (Sault et al. 1995)." (2 Observations and Data Reduction)
- **CPROPS** : Clump identification and properties  
  > "Properties of individual clumps are determined using CPROPS (see section 3.1)" (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of HCO+ clumps | 13 | not stated | dimensionless | 1 | We detect 13 clumps in HCO$^{+}$(1-0) |
| Mvir/MLTE of resolved clumps | ~6 | not stated | dimensionless | 2 | exhibit a ratio of M$_{\rm vir}$/$\rm M_{\rm LTE}$ $\sim$6 |
| Critical mass per unit length (T=30 K) | ~45 | not stated | Msun/pc | 3 | $\left(\frac{M}{L}\right)_{\rm crit} \sim 45~ M_{\odot}$/pc |
| Predicted clump spacing lambda_max | ~5.7 | not stated | pc | 3 | we get a $\lambda_{\rm max}$$\sim$5.7 pc |
| L(HCN)/L(HCO+) for 30Dor-10 | 0.2 | 0.1 | dimensionless | 1 | 0.2(0.1) |

## Qualitative findings

- Dense clumps in 30Dor-10 are not significantly different in mass or dense gas fraction from other LMC GMCs but have broader linewidths.  
  > "the 30Dor-10 clumps have similar mass but wider linewidths and similar HCN/HCO$^{+}$ (1-0) line ratios" (abstract)

## Claim tuples

- H: The linear clump structure is a gravitationally unstable filament | E: Compared Mvir/L to critical M/L | R: Mvir/L ~1e3 vs critical ~45 Msun/pc | F: Filament is unstable and collapsing | **supported**
- H: Clump spacing arises from varicose fluid instability | E: Compared observed spacing to lambda_max | R: 4.8-7.0 pc vs 5.7 pc | F: Consistent | **supported**
- H: Intense UV field alters dense gas properties | E: Compared clumps with other LMC GMCs | R: Similar masses, dense gas fraction and HCN/HCO+; wider linewidths | F: Dense gas well shielded | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Marginally resolved clumps have large radius uncertainties; only 4 of 13 clumps deconvolved.  
  > "Since CPROPS only obtained deconvolved radii for four of the 13 clumps" (3.2 Clumps Properties)
- Caveat (inferred, ours): LTE masses depend on assumed Tex and abundance
- Caveat (inferred, ours): ALMA is only a comparison dataset; the main data are ATCA
- Caveat (inferred, ours): Filament length/projection not quantified

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ATCA project code and archive access
- Missing: CPROPS settings
- Missing: MIRIAD imaging parameters
- Data volume (inferred): small (ATCA, <10 GB)
- Score (inferred): 3/5, ATCA data with partial recipe; ALMA is only a literature comparison.
- Rediscovery candidate: no, Main data are ATCA, with incomplete imaging settings and no ALMA reduction.

## Links

- Method: Rosolowsky & Leroy 2006 (cite: 2006PASP..118..590R) (CPROPS algorithm)
- Companion: Seale et al. 2012 (cite: 2012ApJ...751...42S) (Comparison sample of LMC GMCs)
- Companion: Indebetouw et al. 2013 (cite: 2013ApJ...774...73I) (ALMA CO data of 30Dor-10)
- Related: MAGMA

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00471.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 23,
  "rate": 0.354
 },
 "evidence_ok": true
}
```
