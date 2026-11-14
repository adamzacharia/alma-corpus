# ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). IV. Thioformaldehyde (H<SUB>2</SUB>CS) in protoplanetary discs: spatial distributions and binding energies

`2020A&A...644A.120C` | Astronomy and Astrophysics 2020 | first author: Codella, C. | arXiv: 2011.02305 | DOI: 10.1051/0004-6361/202039309

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry, star_formation
- Question: What are the radial and vertical distributions of H2CS in Class I/early Class II disks, and do computed H2CS binding energies imply thermal desorption can explain the gas-phase H2CS?  
  > "To trace the radial and vertical spatial distribution of H$_2$CS, a key species of the S-bearing chemistry, in protoplanetary disks." (abstract)
- Target **HL Tau**: coordinates 04h31m38.44s, +18d13m57.65s (J2000, continuum peak)  
  > "with an inclination angle $i$ of 47$\ensuremath{^\circ}$ (cite: ALMA2015; Carrasco2019)" (3.1 Continuum and H2CS spatial distributions); z/distance _not stated_; distance from _not stated_
- Target **IRAS 04302+2247**: coordinates 04h33m16.47s, +22d53m20.36s (J2000, continuum peak)  
  > "located at $d$ = 161 pc (cite: Galli2019)" (3.1 Continuum and H2CS spatial distributions); z/distance 161 pc  
  > "located at $d$ = 161 pc (cite: Galli2019)" (3.1 Continuum and H2CS spatial distributions); distance from Galli et al. 2019  
  > "located at $d$ = 161 pc (cite: Galli2019)" (3.1 Continuum and H2CS spatial distributions)
- Target **DG Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **DG Tau B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Haro 6-13**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00846.S, 2018.1.01037.S
- bands: Band 6  
  > "All Band 6 observations were taken in an extended array configuration" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1.4 km or 17 m to 3.7 km  
  > "with baselines ranging from 15 m to 1.4 km or from 17 m to 3.7 km" (2 Observations)
- angular resolution: ~0.3" x 0.3"  
  > "The synthesized beam (HPBW) is $\sim$ 0.3$''$ $\times$ 0.3$''$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 68 uJy (HL Tau), 40 uJy (IRAS04302); ~0.8 mJy/beam per 1.2 km/s channel  
  > "The r.m.s. for continuum images are about 68 $\mu$Jy (HL Tau) and 40 $\mu$Jy (IRAS 04302+2247)." (2 Observations); "The r.m.s. per each channel is about 0.8 mJy beam$^{-1}$." (2 Observations)
- time on source: _not stated_
- observing dates: Cycle 4 (DG Tau, DG Tau B); Cycle 6 (HL Tau, IRAS 04302, Haro 6-13)  
  > "ALMA Cycle 4 observations of DG Tau and DG Tau B and Cycle 6 observations of HL Tau, IRAS 04302+2247, and Haro 6-13" (2 Observations)
- pi or archival as stated: PI: L. Podio (ALMA-DOT)  
  > "ADS/JAO.ALMA 2018.1.01037.S (PI L. Podio) ALMA data" (Acknowledgements)
- Line: o-H2CS 7(1,6)-6(1,5) (244048.5 MHz)
- External data: H2CO and CS vertical/moment 0 distributions of IRAS04302 for comparison  
  > "the H$_2$CS vertical intensity profile can be compared with those of CS and formaldehyde (H$_2$CO), by (cite: Podio2020)." (5.2 Comparison between H2CS, CS, and H2CO) [from Podio et al. 2020a (cite: Podio2020)]
- External data: 13C17O(3-2) ALMA map/flux of HL Tau used to get N_CO and abundance  
  > "(cite: Booth2020) published an ALMA map of the $^{13}$C$^{17}$O(3–2) emission at a similar angular scale as our H$_2$CS maps." (3.3 H2CS column densities and abundances) [from Booth & Ilee 2020 (cite: Booth2020)]
- External data: BE literature values for H2CS and CS (Das, Wakelam)  
  > "| H$_2$CS | 4258 | 3000–4600 | 3110 | 4400 |" (Table 1) [from Das2018; Wakelam2017]

## Processing

### Calibration

- pipeline or manual: standard CASA pipeline  
  > "A standard data reduction was performed with CASA pipeline version 4.7.2." (2 Observations)
- casa version: _not stated_
- pipeline version: CASA pipeline 4.7.2  
  > "A standard data reduction was performed with CASA pipeline version 4.7.2." (2 Observations)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: on continuum, applied to continuum-subtracted line cube  
  > "Self-calibration was performed on the continuum emission and then applied to the continuum-subtracted line datacube." (2 Observations)

### Imaging

- task: TCLEAN  
  > "The line spectral cube was produced through TCLEAN." (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust weighting (value not given)  
  > "We used robust weighting in order to maximise the spatial resolution, and set a channel width of 1.2 km s$^{-1}$." (2 Observations)
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
- final beam: ~0.3" x 0.3"  
  > "The synthesized beam (HPBW) is $\sim$ 0.3$''$ $\times$ 0.3$''$." (2 Observations)
- final rms: ~0.8 mJy/beam per channel  
  > "The r.m.s. per each channel is about 0.8 mJy beam$^{-1}$." (2 Observations)

### Inherited from earlier work

- DG Tau observations/reduction described in earlier paper  
  > "The DG Tau and DG Tau B observations were described by (cite: Podio2019), and (cite: Garufi2020b), respectively." (2 Observations) [from Podio2019; Garufi2020b]
- BE method: HF-3c/B3LYP-D3(BJ) on P-ice (010) slab and AWS scaling factors  
  > "as recently proposed by (cite: Ferrero2020) to predict the BEs of a set of 21 molecules using the periodic *ab initio* program CRYSTAL17" (4 Binding energies) [from Ferrero2020]

### Not stated but needed to reproduce (our reading)

- robust value, clean threshold, mask and cell/image size for tclean
- line-free channels and continuum-subtraction details
- self-calibration solints
- spectral setup details and per-source observing dates/calibrators
- exact line-integration regions for fluxes and emitting areas
- how 13C17O flux was converted to N_CO (isotope ratios beyond one quoted)
- BE computation details (basis, unit-cell, ZPE correction)

## Analysis recipe

1. **Image continuum and H2CS cubes**: Pipeline calibration, self-calibration on continuum, tclean of continuum-subtracted line cube with robust weighting  
  > "The line spectral cube was produced through TCLEAN." (2 Observations)
   - software: CASA, tclean
   - parameter: channel width 1.2 km/s  
  > "set a channel width of 1.2 km s$^{-1}$" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and kinematics**: Moment 0 (channels >=3 sigma), moment 8 and moment 1 maps, channel maps and spectra; V proportional to R ring signature  
  > "All the channels showing emission of at least 3$\sigma$ (see Sect. 2) have been used, namely: 3–11 km s$^{-1}$ (HL Tau) and 2–10 km s$^{-1}$ (IRAS04302)." (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: moment 8 maps confirm moment 0 maps  
  > "The moment 8 images definitely confirm what found with the moment 0 maps." (3.1)
3. **H2CS column densities and upper limits**: LTE optically thin column density from flux over emitting area; upper limits at 5 sigma of moment 0 maps  
  > "Assuming (i) Local Thermodynamic Equilibrium (LTE), and (ii) optically thin emission, the column densities of the H$_2$CS are derived." (3.3)
   - parameter: HL Tau area 1.35 arcsec^2, flux 148 mJy km/s; IRAS04302 area 0.72 arcsec^2, flux 78 mJy km/s  
  > "In HL Tau the observed emitting area is 1.35 arcsec$^2$ (from the moment 0 map) the flux is 148 mJy km s$^{-1}$ (2.6 K km s$^{-1}$)." (3.3)
   - assumption: T = 20–150 K, ortho-to-para = 3  
  > "We conservatively adopted a temperature between 20 K and 150 K. An ortho-to-para ratio of 3, i.e. the statistical value, has been assumed" (3.3)
   - fitting: _not stated_
   - validation: LVG check gives opacity <=0.1 for N~1e14  
  > "the Large Velocity Gradient approach confirms that column densities around 10$^{14}$ cm$^{-2}$ implies for the o-H$_2$CS(7$_{\rm 1,6}$–6$_{\rm 1,5}$) line an opacity of $\leq$ 0.1." (3.3)
4. **HL Tau H2CS abundance**: N_CO from 13C17O flux (Booth & Ilee 2020) then [CO]/[H]=5e-5  
  > "Using \[CO\]/\[H\] = 5 $\times$ 10$^{-5}$, the H$_2$CS abundance (with respect to H) results to be $X(H_2CS)$ $\simeq$ 10$^{-14}$." (3.3)
   - assumption: 13C17O optically thin; 12C16O/13C17O ratio abundance 8.3e-6; Tex 20-150 K  
  > "given that its abundance ratio with respect to $^{12}$C$^{16}$O is 8.3 $\times$ 10$^{-6}$ (cite: Milam2005)" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Vertical/radial profile comparison with H2CO and CS in IRAS04302**: Radial averaging over 3 pixels (0.18") at 60 and 115 au; compare vertical profiles and moment 0 with Podio et al. 2020  
  > "we averaged the emission radially over 3 pixels (0.18$''$, corresponding to $\sim$ 29 au) around the selected radius." (5.2)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compute H2CS and CS binding energies**: HF-3c optimisation then B3LYP-D3(BJ)/A-VTZ* single points with BSSE on P-ice (010) slab; AWS values by scaling with factors 0.859 and 0.775 from Ferrero et al.  
  > "to define the final B3LYP-D3(BJ)/A-VTZ\* //HF-3c model chemistry. BEs were also corrected for BSSE." (4)
   - software: CRYSTAL17
   - assumption: AWS scaling factors from CO and H2CO apply to CS and H2CS  
  > "Then by assuming the same scaling factors also for the present CS and H$_2$CS cases, we scaled the BEs for the crystalline ice" (4)
   - fitting: _not stated_
   - validation: compared with literature BEs (Das 2018; Wakelam 2017)  
  > "Table [1](#tbe) compares our results with the available literature data, all coming from computer simulations." (5.1)

## Software

- **CASA** pipeline 4.7.2: calibration, tclean imaging, moment maps  
  > "A standard data reduction was performed with CASA pipeline version 4.7.2." (2 Observations)
- **CRYSTAL17** : periodic ab initio binding energy calculations  
  > "using the periodic *ab initio* program CRYSTAL17 (cite: Dovesi2018)" (4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2CS column density HL Tau | 0.9–1.4e14 | not stated | cm^-2 | 3 | turns out to be 0.9–1.4 $\times$ 10$^{14}$ cm$^{-2}$ |
| H2CS column density upper limit DG Tau B | <=2e13 | not stated | cm^-2 | 3 | $N_{\rm  H_2CS}$ $\leq$ 2 $\times$ 10$^{13}$ cm$^{-2}$ (DG Tau B) |
| H2CS column density upper limit DG Tau and Haro 6-13 | <=4e13 | not stated | cm^-2 | 3 | $N_{\rm  H_2CS}$ $\leq$ 4 $\times$ 10$^{13}$ cm$^{-2}$ (DG Tau and Haro 6-13) |
| [H2CS]/[H] in HL Tau | ~1e-14 | not stated | dimensionless | 4 | $X(H_2CS)$ $\simeq$ 10$^{-14}$ |
| N_CO HL Tau | 5–10e23 | not stated | cm^-2 | 4 | we derive $N_{\rm  CO}$ $\simeq$ 5–10 $\times$ 10$^{23}$ cm$^{-2}$ |
| H2CS BE crystalline | 4258 | not stated | K | 6 | / H$_2$CS / 4258 / 3000–4600 / 3110 / 4400 / |
| H2CS BE AWS | 3000–4600 | not stated | K | 6 | / H$_2$CS / 4258 / 3000–4600 / 3110 / 4400 / |
| CS BE crystalline | 3861 | not stated | K | 6 | / CS      /  3861  / 2700–4000 /  2217   /    3200     / |
| East/West vertical asymmetry IRAS04302 | 1.8 at 60 au; 1.5 at 115 au | not stated | dimensionless | 5 | brighter than in the western side by a factor 1.8 at 60 au radial distance and a factor 1.5 at 115 au |

## Qualitative findings

- H2CS in HL Tau and IRAS04302 is in a rotating ring with an inner dip; emission peaks at z≈±50 au in IRAS04302, co-spatial with H2CO and CS  
  > "H$_2$CS is confined in a rotating ring with an inner dip towards the protostar" (Conclusions)

## Claim tuples

- H: H2CS emission in Class I disks is ring-like and traces the warm molecular layer | E: ALMA Band 6 imaging of five disks; moment maps, kinematics, vertical profiles | R: Detected in HL Tau and IRAS04302 as rings with outer radii 140 and 115 au; peaks at z≈50 au | F: H2CS traces the warm molecular layer like CS and H2CO but peaks closer to the star | **supported**
- H: Thermal desorption can explain gas-phase H2CS at large radii | E: Computed BEs for crystalline ice and scaled AWS | R: BE 3000–4600 K implies sublimation only where Tdust >= 50–80 K | F: Emission beyond 100 au likely from non-thermal desorption | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Amorphous ice not modelled directly because its structure is unknown and cells would be very large; scaling used instead  
  > "i) the experimental atomistic structure of the AWS is unknown; ii) AWS model should be based on very large unit cell" (4)
- How they decided it was enough: _not stated_
- Limitation (authors): Crystalline BEs are upper limits; AWS BEs are estimated by scaling without computations  
  > "This means that the BEs resulting from the crystalline model should be taken as an upper limit" (4)
- Caveat (inferred, ours): Abundance relies on 13C17O flux from another paper and broad temperature range
- Caveat (inferred, ours): Column densities are beam-averaged with assumed LTE and emitting areas
- Caveat (inferred, ours): No uncertainties on most numbers
- Caveat (inferred, ours): AWS BEs from scaling of CO/H2CO factors are unvalidated for sulfur species

## Reproducibility

- Data public (paper): ALMA projects cited; public status not explicitly stated  
  > "This paper uses the ADS/JAO.ALMA 2016.1.00846.S and ADS/JAO.ALMA 2018.1.01037.S (PI L. Podio) ALMA data." (Acknowledgements)
- Products in archive: _not stated_
- Missing: tclean parameters (robust, mask, threshold)
- Missing: continuum subtraction channels
- Missing: self-calibration parameters
- Missing: exact flux integration regions
- Missing: BE calculation inputs and ZPE treatment
- Data volume (inferred): ~50-100 GB for five Band 6 datasets (raw), less for products
- Score (inferred): 5/5, Public ALMA data and simple LTE calculations, but imaging parameters and BE details are missing.
- Rediscovery candidate: no, Imaging recipe incomplete and BE calculation needs specialised periodic DFT.

## Links

- Method: Ferrero et al. 2020 (cite: Ferrero2020) (BE computational method and AWS scaling)
- Companion: Podio et al. 2020a (cite: Podio2020) (IRAS04302 H2CO, CS, CO data)
- Companion: Podio et al. 2019 (cite: Podio2019) (DG Tau observations)
- Companion: Garufi et al. 2020 (cite: Garufi2020b) (DG Tau B observations)
- Related: ALMA-DOT
- Related: ALMA PILS
- Related: ALMA FAUST
- Related: CALYPSO
- Related: SOLIS
- Related: ASAI

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 43,
  "rate": 0.489
 },
 "evidence_ok": true
}
```
