# Studying star-forming processes at core and clump scales: the case of the young stellar object G29.862-0.0044

`2020A&A...641A.104A` | Astronomy and Astrophysics 2020 | first author: Areal, M. B. | arXiv: 2007.07852 | DOI: 10.1051/0004-6361/202038243

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the core- and clump-scale physical and chemical properties and outflow/jet structure of the massive YSO G29.862-0.0044, from near-IR, ALMA, ASTE and JCMT CO data?  
  > "we perform a deep study of the YSO G29.862$-$0.0044 (YSO-G29) at core and clump spatial scales." (abstract)
- Target **YSO G29.862-0.0044 (YSO-G29)**: coordinates 18:45:59.566 -2:45:5.518 (J2000, ALMA 1.3 mm peak)  
  > "is embedded in the southern portion of a molecular cloud located at a distance of about 6.2 kpc, related to the star-forming region G29.96$-$0.02 (W43-South, (cite: carl13))" (Introduction); "18:45:59.566 | -2:45:5.518" (Table 2); z/distance 6.2 kpc  
  > "is embedded in the southern portion of a molecular cloud located at a distance of about 6.2 kpc, related to the star-forming region G29.96$-$0.02 (W43-South, (cite: carl13))" (Introduction); "18:45:59.566 | -2:45:5.518" (Table 2); distance from W43-South molecular cloud distance (Carlhoff et al. 2013)  
  > "is embedded in the southern portion of a molecular cloud located at a distance of about 6.2 kpc, related to the star-forming region G29.96$-$0.02 (W43-South, (cite: carl13))" (Introduction); "18:45:59.566 | -2:45:5.518" (Table 2)

## Data provenance

- ALMA projects: 2015.1.01312.S
- bands: _not stated_
- frequencies and spectral setup: cubes centred at 226.71 GHz (CH3OCHO) and 239.01 GHz (CH3CN); 1.5 km/s velocity resolution  
  > "with central frequencies at 226.71 and 239.01 GHz, respectively" (2.2.1 ALMA data); "The velocity spectral resolution is 1.5 km s$^{-1}$." (2.2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.78'' x 0.60'' beam (~0.02 pc, ~4000 au at 6.2 kpc)  
  > "The beam size of both data cubes is 0.78$''$ $\times$ 0.60$''$" (2.2.1 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Obtained from the ALMA Science Archive  
  > "were obtained from the ALMA Science Archive" (2.2.1 ALMA data)
- Line: CH3OCHO 20(2,19)-19(2,18)E (not stated)
- Line: CH3CN J=13-12 K=0-3 (239.137 GHz (K=0))
- Other facility **Gemini-North NIRI**: near-IR broad and narrow-band imaging  
  > "The images were acquired with the Near InfraRed Imager and Spectrometer" (2.1 Near-IR data)
- Other facility **ASTE**: HCN, HNC, HCO+ J=4-3 and C2H N=4-3 spectra  
  > "were carried out on August 2019 with the 10-m ASTE telescope" (2.2.3 ASTE observations)
- Other facility **JCMT (COHRS, CHIMPS)**: 12CO and C18O J=3-2 public data  
  > "two public databases of observations carried out with the 15-m James Clerck Maxwell Telescope" (2.2.2 12CO and C18O data)
- External data: Bolometric luminosity ~4.5e4 Lsun, scaled to 6.2 kpc  
  > "about $4.5 \times 10^{4}$ L$_{\odot}$ (based on the luminosity of (cite: mottram11) corrected to the assumed distance of 6.2 kpc)" (4.1 Core scales) [from (cite: mottram11)]
- External data: Dust temperature ~26 K from PPMAP Hi-GAL map  
  > "(T$_{dust} \sim 26$ K) obtained from the dust temperature map" (4.2 Clump scales) [from (cite: marsh17)]

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
- continuum subtraction: CASA imcontsub  
  > "The task *imcontsub* was used to subtract the continuum from the spectral lines." (2.2.1 ALMA data)
- line free channels: _not stated_
- primary beam correction: flux density corrected for primary beam response  
  > "the integrated flux density corrected for primary beam response are presented in Cols. 3 and 4" (3.1 At core scales)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.78'' x 0.60''  
  > "The beam size of both data cubes is 0.78$''$ $\times$ 0.60$''$" (2.2.1 ALMA data)
- final rms: _not stated_

### Inherited from earlier work

- Mass formula and dust opacity 0.01 cm2/g at 1.3 mm  
  > "We estimate the mass of gas of the central core from the dust continuum emission at 1.3 mm following (cite: kau08)" (3.1.2 Mass and density of the core) [from (cite: kau08; osse94)]
- Rotational diagram method for interferometric data  
  > "Following (cite: miao95), for interferometric observations, the left-hand side of Eq. [\[RotDia\]](#RotDia) can also be estimated by," (3.1.1) [from (cite: miao95; turner91)]
- Virial mass k=190 for r^-1 density  
  > "where $k=190$ by assuming a density distribution $\propto r^{-1}$ (cite: mac88)" (3.1.2) [from (cite: mac88)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration/imaging details (pipeline version, CASA version, weighting, cleaning) for the archival cubes
- Continuum-free channels used for imcontsub
- Continuum image construction and beam/size fitting method
- Rest frequencies and line strength values used, and Q_rot value
- Flux density measurement aperture/method for core
- Gaussian-fit procedure and uncertainties for CH3CN lines

## Analysis recipe

1. **Extract continuum and line maps from ALMA cubes**: Continuum subtraction with imcontsub, integrated line maps, channel maps, 1.3 mm continuum core parameters  
  > "The task *imcontsub* was used to subtract the continuum from the spectral lines." (2.2.1 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **CH3CN rotational diagram for Trot and column density**: Gaussian fits to K components, linear fit of rotation diagram  
  > "The free parameters, ($N_{tot}/Q_{rot}$) and $T_{rot}$ were determined by a linear fitting of Eq. [\[RotDia\]](#RotDia)" (3.1.1)
   - assumption: LTE, optically thin lines, beam filling factor of unity  
  > "By assuming LTE conditions, optically thin lines, and a beam filling factor equal to the unity" (3.1.1)
   - fitting: linear fit of ln(Nu/gu) vs Eu  
  > "The free parameters, ($N_{tot}/Q_{rot}$) and $T_{rot}$ were determined by a linear fitting of Eq. [\[RotDia\]](#RotDia) (see Fig. [9](#trot))." (Physical parameters from the CH$_{3}$CN emission)
   - validation: _not stated_
3. **Core gas mass, density and virial mass**: Dust continuum mass formula; virial mass from CH3CN width  
  > "we obtain $M_{gas} \sim 8$ M$_\odot$." (3.1.2)
   - parameter: S = 0.051 Jy, kappa = 0.01 cm2/g, dv = 6.7 km/s, R = 0.01 pc  
  > "considering the integrated flux intensity $S_{\nu}$ = 0.051 Jy at 1.3 mm (see Table [2](#contparams)), we obtain $M_{gas} \sim 8$ M$_\odot$." (Mass and density of the core)
   - assumption: Tdust = Tkin = Trot; spherical geometry  
  > "Assuming LTE conditions ($T_{kin}$=$T_{rot}$), and that the gas and dust are thermally coupled ($T_{dust}$=$T_{kin}$)" (3.1.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Clump-scale gas diagnostics from ASTE and JCMT**: Gaussian fits to spectra; HCN/HNC ratio converted to kinetic temperature with Hacar et al. 2020 Eq. 3  
  > "by using their Eq. 3, we obtain T$_{\rm K} \sim 23$ K towards G29-YSO" (4.2 Clump scales)
   - software: NEWSTAR
   - fitting: Gaussian fitting  
  > "Table [4](#molec) lists the parameters obtained from the Gaussian fitting to each spectrum presented in Figs.[11](#c18ospect),[12](#hcspect) and [13](#c2hspect)." (At clump scales)
   - validation: compared with PPMAP Tdust ~26 K  
  > "This value is in quite agreement with the dust temperature at the YSO position (T$_{dust} \sim 26$ K)" (4.2 Clump scales)

## Software

- **CASA** : handle ALMA data, continuum subtraction  
  > "The Common Astronomy Software Applications (CASA) was used to handle these data." (2.2.1 ALMA data)
- **DRAGONS** 2.1.0: NIRI data reduction  
  > "The NIRI data was reduced with DRAGONS, the Gemini’s new Python-base data reduction platform (version 2.1.0)" (2.1 Near-IR data)
- **Theli** : NIRI data reduction  
  > "and Theli (cite: sch13; erben05)" (2.1 Near-IR data)
- **NEWSTAR** : ASTE data reduction  
  > "The data were reduced with NEWSTAR" (2.2.3 ASTE observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm core peak intensity | 26.2 | not stated | mJy/beam | 1 | 26.2    / 51.6 |
| 1.3 mm core integrated flux density | 51.6 | not stated | mJy | 1 | 26.2    / 51.6 |
| CH3CN rotational temperature | 82 | not stated | K | 2 | We derive a $T_{rot}$ of about 82 K |
| CH3CN column density | 1e15 | not stated | cm^-2 | 2 | we obtain a CH$_3$CN column density of about $10^{15}$ cm$^{-2}$ |
| Core gas mass | 8 | not stated | Msun | 3 | we obtain $M_{gas} \sim 8$ M$_\odot$ |
| Virial mass | 70 | not stated | Msun | 3 | Thus, we obtain $M_{vir} \sim 70$ M$_\odot$. |
| HCN/HNC integrated ratio | 2.3 | not stated | dimensionless | 4 | The HCN/HNC integrated ratio is $\sim 2.3$. |
| Clump kinetic temperature from HCN/HNC | 23 | not stated | K | 4 | we obtain T$_{\rm K} \sim 23$ K towards G29-YSO |

## Qualitative findings

- Source is a 'light' hot molecular core likely containing a rotating toroid/disk  
  > "We conclude that we are indeed observing a “light” hot molecular core, which probably contains a rotating toroid/disk." (4.1 Core scales)
- Only a red-shifted outflow is seen; source likely at far edge of clump  
  > "One possible explanation is that the YSO is located in the furthest edge of the molecular clump along the line of sight" (4.2 Clump scales)

## Claim tuples

- H: Is YSO-G29 a hot molecular core? | E: ALMA CH3CN and CH3OCHO, 1.3 mm continuum, rotation diagram, mass | R: Trot ~82 K, N ~1e15 cm^-2, Mgas ~8 Msun, Mvir ~70 Msun | F: A light hot molecular core | **supported**
- H: Do clump-scale tracers indicate a high-mass protostellar object? | E: ASTE HCN, HNC, HCO+, C2H; HCN/HNC ratio | R: HCN/HNC ~2.3, TK ~23 K, C2H widths consistent with HMPOs | F: Consistent with HMPO stage | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Blue 12CO component rejected as outflow; associated with another cold clump  
  > "Thus, this blue component in the $^{12}$CO cannot be considered as a molecular outflow." (3.2 At clump scales)
- How they decided it was enough: _not stated_
- Limitation (authors): Near-IR dataset incomplete for determining H2 excitation mechanism  
  > "Our near-IR data set is not complete for specifying this" (4.1 Core scales)
- Caveat (inferred, ours): Single-temperature LTE assumptions and a single Gaussian fit for the mass and rotation diagram; no uncertainties given
- Caveat (inferred, ours): Archival ALMA processing undocumented
- Caveat (inferred, ours): Virial mass vs gas mass sensitive to assumed k and size, with a coarse beam

## Reproducibility

- Data public (paper): ALMA data from the public archive; COHRS/CHIMPS public  
  > "were obtained from the ALMA Science Archive" (2.2.1 ALMA data)
- Products in archive: _not stated_
- Missing: ASTE and NIRI raw data access
- Missing: ALMA calibration/imaging parameters
- Missing: Line fit uncertainties and Qrot value
- Data volume (inferred): ~10-50 GB for the archival ALMA project
- Score (inferred): 3/5, Public ALMA data and simple analyses, but processing and fitting details are sparse and several results lack uncertainties.
- Rediscovery candidate: yes, Public archival ALMA data with a simple numeric recipe (Trot, mass, virial mass), though some settings are missing.

## Links

- Method: (cite: kau08) (mass from dust continuum)
- Method: (cite: miao95) (interferometric rotation diagram)
- Method: (cite: hacar20) (HCN/HNC ratio to kinetic temperature)
- Companion: (cite: sch19) (previous paper of the series on core/clump scales (Sgr B2(N) CH3OCHO))
- Related: COHRS
- Related: CHIMPS
- Related: RMS survey
- Related: ATLASGAL
- Related: Hi-GAL

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 37,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
