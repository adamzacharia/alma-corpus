# Growth of carbon chains in IRC +10216 mapped with ALMA

`2017A&A...601A...4A` | Astronomy and Astrophysics 2017 | first author: Agúndez, M. | arXiv: 1702.04429 | DOI: 10.1051/0004-6361/201630274

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: How do linear carbon chains (polyynes and cyanopolyynes) form and grow in the envelope of the C-star IRC +10216, and where are they located radially?  
  > "We have carried out a combined observational and modeling study of the formation of carbon chains in the C-star envelope IRC +10216" (abstract)
- Target **IRC +10216**: coordinates RA 09h47m57.446s, Dec +13d16m43.86s (J2000)  
  > "Observations were centered on the position of the star, with coordinates J2000.0 R.A.=09$^{\rm h}$47$^{\rm m}$57$^{\rm s}$446 and Dec.=13$^{\circ}$16$'$43$''$86" (2 Observations); "For the distance, we use the recent value of 123 pc determined by (cite: gro2012) (2012)." (4 Model); z/distance 123 pc  
  > "Observations were centered on the position of the star, with coordinates J2000.0 R.A.=09$^{\rm h}$47$^{\rm m}$57$^{\rm s}$446 and Dec.=13$^{\circ}$16$'$43$''$86" (2 Observations); "For the distance, we use the recent value of 123 pc determined by (cite: gro2012) (2012)." (4 Model); distance from Groenewegen et al. 2012  
  > "Observations were centered on the position of the star, with coordinates J2000.0 R.A.=09$^{\rm h}$47$^{\rm m}$57$^{\rm s}$446 and Dec.=13$^{\circ}$16$'$43$''$86" (2 Observations); "For the distance, we use the recent value of 123 pc determined by (cite: gro2012) (2012)." (4 Model)

## Data provenance

- ALMA projects: 2013.1.00432.S
- bands: Band 3 (3 mm), 84.0-115.5 GHz, Cycle 2  
  > "A $\lambda~3$ mm spectral survey of IRC +10216 covering the frequency range 84.0-115.5 GHz was carried out with ALMA band 3 during Cycle 2." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact and extended 12m array configurations  
  > "Observations were obtained with compact and extended array configurations." (2 Observations)
- baselines: _not stated_
- angular resolution: ~1 arcsec (merged); ~3 arcsec for C6H (compact only)  
  > "providing an angular resolution of $\sim$1$''$." (2 Observations); "the angular resolution of the C$_6$H map is of the order of $\sim$3$''$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: C2H N=1-0, J=3/2-1/2 F=1-0 (87328.625 MHz)
- Line: CN N=1-0, J=3/2-1/2 F=1/2-1/2 (113499.644 MHz)
- Line: HC3N J=10-9 (also 11-10, 12-11) (not stated)
- Line: HC5N J=32-31 (up to J=43-42) (not stated)
- Other facility **IRAM 30m**: short-spacing data to recover flux filtered by the interferometer  
  > "Additional observations were performed with the IRAM 30m telescope to recover the flux filtered out by the interferometer." (2 Observations)
- External data: Stellar and envelope parameters, parent molecule abundances, mass loss rate 2e-5 Msun/yr  
  > "The parameters of the star and envelope have been taken from (cite: agu2012) (2012), i.e., the adopted mass loss rate is $2\times10^{-5}$ $M_{\odot}$ yr$^{-1}$." (4 Model) [from (cite: agu2012)]
- External data: Systemic velocity -26.5 km/s and expansion velocity 14.5 km/s  
  > "where $V_{\rm sys} = -26.5$ km s$^{-1}$ for IRC +10216; (cite: cer2000) 2000" (2 Observations) [from (cite: cer2000)]

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
- continuum subtraction: continuum subtracted before merging with IRAM 30m short spacings  
  > "data from the ALMA compact and extended configurations were merged, after continuum subtraction, with the short-spacings data obtained with IRAM 30m" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: e.g. 1.07x0.92 arcsec (C2H), 0.85x0.74 (CN), 1.14x0.98 (C4H), 1.10x0.92 (C3N), 1.08x0.81 (HC3N), 1.11x0.99 (HC5N)  
  > "In this map the synthesized beam is $1\mbox{\rlap{.}$''$}07\times0\mbox{\rlap{.}$''$}92$" (2 Observations)
- final rms: 0.4-1.3 mJy/beam per 3 km/s channel depending on species  
  > "the rms per 3 km s$^{-1}$ channel is 0.4 mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Full spectral survey description deferred  
  > "A thorough description of the spectral survey will be presented elsewhere (Cernicharo et al., in preparation)." (2 Observations) [from Cernicharo et al., in preparation]
- Radiative transfer: multi-shell LVG code and physical model of IRC +10216  
  > "The radiative transfer calculations have been performed with the multi-shell LVG code and physical model of IRC +10216 used by (cite: agu2012) (2012)" (4.2 Radiative transfer) [from (cite: agu2012)]

### Not stated but needed to reproduce (our reading)

- ALMA/CASA calibration and imaging procedure, versions, weighting, cell/image size
- Details of merging with IRAM 30m data
- Line-free channels and continuum subtraction method
- Exact synthesized beams and rms for C6H stacked map and list of 19 C6H lines
- Method of azimuthal averaging and strip extraction
- Chemical network files and IR pumping parameters for full reproduction
- Flux calibrator and calibration uncertainty

## Analysis recipe

1. **Map line emission of carbon chains**: Merge ALMA compact+extended data with IRAM 30m after continuum subtraction; map channel at Vsys averaged over 3 km/s; stack 19 C6H lines using compact data only  
  > "stacked the maps of a selected list of 19 lines, all free of blending and observed with a sufficient quality" (2 Observations)
   - fitting: _not stated_
   - validation: Compared different transitions of same species (Appendix)  
  > "Here we present the emission maps of each individual line and discuss whether the different lines of a given species have brightness distributions significantly different among them" (Appendix: Emission maps in different rotational transitions)
2. **Derive radial brightness profiles**: Strip at PA=45 deg and azimuthal averages of maps  
  > "Information on the radial distribution of the species can be obtained by azimuthal average of the brightness distribution" (3 Observed spatial distributions)
   - fitting: _not stated_
   - validation: _not stated_
3. **Chemical model of the expanding envelope**: Gas-phase kinetic model, isotropic expansion from 2e14 cm, UV illumination by Draine field, NH/AV reduced 1.5x, cosmic ray rate 1.2e-17 s-1  
  > "The adopted cosmic-ray ionization rate of H$_2$ is $1.2\times10^{-17}$ s$^{-1}$" (4.1 Chemical model)
   - software: Meudon PDR code
   - assumption: Distance 123 pc; C2H2 and HCN abundances 8e-5 and 4e-5 relative to H2  
  > "the adopted abundances relative to H$_2$ are $8\times10^{-5}$ and $4\times10^{-5}$, respectively" (4.1 Chemical model)
   - fitting: No fit; NH/AV tuned to reproduce observed radial location  
  > "For the purpose of reproducing the observed radial location of carbon chains, we have adopted a $N_{\rm H}$ / $A_V$ ratio 1.5 times lower than the canonical interstellar value" (Model, Chemical model: formation of carbon chains)
   - validation: Compared to observed radial brightness  
  > "A comparison between the observed and calculated $\lambda$ 3 mm emission distributions of carbon chains allows us to draw conclusions about the formation mechanism of carbon chains in IRC +10216." (Discussion)
4. **Radiative transfer to predicted brightness**: Multi-shell LVG with IR pumping, converting abundance profiles to brightness profiles  
  > "The radiative transfer calculations have been performed with the multi-shell LVG code and physical model of IRC +10216 used by (cite: agu2012) (2012)" (Radiative transfer models: emission of carbon chains)
   - software: multi-shell LVG code
   - assumption: Radicals treated as linear 1Sigma molecules; generic 15 micron vibrational band for C4H, C6H, C3N  
  > "we have collapsed the fine rotational structure and simply treated these species as linear molecules with a $^1\Sigma$ electronic state." (Radiative transfer models: emission of carbon chains)
   - fitting: _not stated_
   - validation: Compared with azimuthally averaged observed profiles  
  > "the observed brightness radial distributions are the result of an azimuthal average of the brightness distributions shown in Fig. [1](#fig:map_all)." (Discussion)

## Software

- **Meudon PDR code** : photodissociation rates and dust shielding  
  > "using the Meudon PDR code ((cite: lep2006) 2006)" (4.1 Chemical model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Shell width (overall) | 5-10 | not stated | arcsec | 1 | a hollow, 5-10$''$ wide, spherical shell located at a radius of 10-20$''$ from the star |
| Hydrocarbon radical radial maximum | 15.5-16 | not stated | arcsec | 2 | reach their maximum brightness at the same radial position, between $15\mbox{\rlap{.}$''$}5$ and 16$''$ |
| Sub-shell width | 1-2 | not stated | arcsec | 1 | thinner sub-shells which are 1-2$''$ wide and not fully concentric |

## Qualitative findings

- HC3N appears earlier (from ~7 arcsec) and CN extends beyond 30 arcsec  
  > "The radial distribution of CN is also markedly different from the rest of the species as it extends out to radial distances beyond 30$''$." (3 Observed spatial distributions)

## Claim tuples

- H: Carbon chains are confined to the outer envelope with radial stratification dependent on species | E: ALMA+IRAM 30m maps of seven species at ~1 arcsec | R: Hollow shells at 10-20 arcsec composed of thin non-concentric arcs; hydrocarbons co-located, cyanides diverse | F: Mass loss discontinuous and non-isotropic | **supported**
- H: UV-driven gas-phase growth explains observed chain distributions | E: Chemical + LVG radiative transfer model compared with radial profiles | R: Model reasonably reproduces observations except HC5N onset | F: Polyynes grow via C2H/C4H reactions, cyanopolyynes via CN/C3N with polyynes | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Spherical isotropic model cannot reproduce arcs; comparison only first order; IR pumping uncertain for C4H, C6H, C3N  
  > "the comparison between the calculated and observed emission distributions can only be done to first order, and not at the sub-arcsecond level" (5 Discussion)
- Caveat (inferred, ours): Calibration and imaging details absent
- Caveat (inferred, ours): NH/AV scaling tuned to match observations, reducing model independence
- Caveat (inferred, ours): No quantitative error bars on radial positions
- Caveat (inferred, ours): Model-observation comparison qualitative

## Reproducibility

- Data public (paper): ALMA project acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00432.S." (Footnote 1)
- Products in archive: _not stated_
- Missing: CASA imaging parameters
- Missing: IRAM 30m data and merging procedure
- Missing: LVG and chemistry code
- Missing: Fits of radial profiles
- Data volume (inferred): Large (hundreds of GB; full Band 3 spectral survey, two configs)
- Score (inferred): 3/5, Data identifiable but processing and model code are largely undescribed; results mostly qualitative.
- Rediscovery candidate: no, Recipe incomplete and results mostly qualitative/morphological.

## Links

- Method: Agúndez et al. 2012 (physical and radiative transfer model)
- Companion: Cernicharo et al., in preparation (spectral survey description)
- Related: ALMA Cycle 0 IRC +10216 observations

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
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
  "facts": 65,
  "stated": 29,
  "rate": 0.446
 },
 "evidence_ok": true
}
```
