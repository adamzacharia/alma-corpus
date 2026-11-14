# Galactic 'Snake' IRDC G11.11-0.12: a site of multiple hub-filament systems and colliding filamentary clouds

`2024MNRAS.527.5895D` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Dewangan, L. K. | arXiv: 2310.20404 | DOI: 10.1093/mnras/stad3384

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the multi-scale structure, kinematics and star formation processes (hub-filament systems, cloud collision) in the IRDC G11.11-0.12, including the inner environment of G11P1 seen with ALMA?  
  > "To probe star formation processes, we present a multi-scale and multi-wavelength investigation of the ‘Snake’ nebula/infrared dark cloud G11.11$-$0.12" (abstract)
- Target **IRDC G11.11-0.12 (Snake nebula) / G11P1**: coordinates central l = 11.119 deg, b = -0.0647 deg (field); G11P1 = clump c7 at l=11.107, b=-0.114  
  > "The reliable distance (i.e., $\sim$2.92 kpc) of these clumps (see Table [\[tab2xx\]](#tab2xx) for physical parameters) has been determined by (cite: urquhart18)" (1 Introduction); z/distance ~2.92 kpc  
  > "The reliable distance (i.e., $\sim$2.92 kpc) of these clumps (see Table [\[tab2xx\]](#tab2xx) for physical parameters) has been determined by (cite: urquhart18)" (1 Introduction); distance from Urquhart et al. 2018 (cite: urquhart18)  
  > "The reliable distance (i.e., $\sim$2.92 kpc) of these clumps (see Table [\[tab2xx\]](#tab2xx) for physical parameters) has been determined by (cite: urquhart18)" (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.00101.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.34 x 0.27 arcsec  
  > "ALMA data | 1.16 mm, H$^{13}$CO$^{+}$(3–2) | $\sim$0.34 $\times$ 0.27" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma ~185 uJy/beam (continuum); line velocity resolution ~0.56 km/s  
  > "ALMA continuum map at 1.16 mm (1$\sigma$ $\sim$185 $\mu$Jy beam$^{-1}$) and H$^{13}$CO$^{+}$(3–2) line data (velocity resolution $\sim$0.56 km s$^{-1}$)" (2 Data sets and analysis)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, downloaded from ALMA science archive; PI Sanhueza  
  > "which were downloaded from the ALMA science archive" (2 Data sets and analysis)
- Line: H13CO+ J=3-2 (not stated)
- Other facility **Spitzer GLIMPSE/MIPSGAL**: 8.0 and 24 um images, YSO photometry  
  > "We employed the GLIMPSE-I Spring ’07 highly reliable catalog to obtain photometric magnitudes of point-like sources" (2 Data sets and analysis)
- Other facility **JWST NIRCam**: Near-IR images of G11P1 and G11P6  
  > "We utilized the level-3 science ready *JWST* Near-Infrared Camera" (2 Data sets and analysis)
- Other facility **SEDIGISM (APEX)**: 13CO and C18O (2-1) cubes  
  > "The $^{13}$CO(2–1) and C$^{18}$O(2–1) line data cubes were obtained from the SEDIGISM survey" (2 Data sets and analysis)
- Other facility **RAMPS**: NH3(1,1) data  
  > "Radio Ammonia Mid-Plane Survey (RAMPS) | NH$_{3}$(1, 1) | $\sim$34.7" (Table 1)
- Other facility **Herschel Hi-GAL**: Column density and temperature maps  
  > "we display the *Herschel* column density ($N(\mathrm H_2)$) and temperature ($T_\mathrm{d}$) maps" (3.2.2)
- External data: ATLASGAL clump distances, velocities, masses, temperatures  
  > "The reliable distances and velocities of the ATLASGAL 870 $\mu$m dust continuum clumps distributed toward our selected target area were collected from the published work of (cite: urquhart18)" (2 Data sets and analysis) [from (cite: urquhart18)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Primary-beam corrected continuum map downloaded from archive  
  > "We examined the primary-beam corrected ALMA continuum map at 1.16 mm" (2 Data sets and analysis)
- flux calibrator: J1924-2914 (flux and bandpass); J1832-2039 phase  
  > "The quasar J1924-2914 was utilized for the flux calibration and the bandpass calibrator, while the quasar J1832-2039 was utilized for phase calibration" (2 Data sets and analysis)
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
- primary beam correction: Maps primary-beam corrected  
  > "We examined the primary-beam corrected ALMA continuum map at 1.16 mm" (2 Data sets and analysis)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA calibration description deferred to earlier papers  
  > "while the quasar J1832-2039 was utilized for phase calibration (cite: lopez21; sanhueza21)." (2 Data sets and analysis) [from (cite: lopez21; sanhueza21)]
- Herschel hires column density/temperature map procedure  
  > "The steps needed to obtain these maps using the *hires* are described in (cite: getsf_2022) (cite: dewangan23)." (3.2.2) [from (cite: getsf_2022) (cite: dewangan23)]

### Not stated but needed to reproduce (our reading)

- ALMA array configuration, observing dates, central frequencies, and pipeline/CASA version
- Imaging parameters (weighting, robust, cell, image size, CLEAN threshold) of the archive continuum and line cubes
- Continuum-subtraction and line-free channels for H13CO+
- clumpfind threshold and step settings, scousepy fitting parameters beyond SAA size
- Gas-to-dust ratio value R_t used in mass formula

## Analysis recipe

1. **identify continuum sources in ALMA 1.16 mm map**: clumpfind decomposition at contour levels 0.03 and 0.055 x 10.4 mJy/beam, giving sources A, B-D, b1-b3; astrodendro as independent check  
  > "The *clumpfind* IDL program (cite: williams94) has been employed in the ALMA continuum map at 1.16 mm to depict continuum sources." (3.4.2)
   - software: clumpfind, astrodendro
   - parameter: astrodendro min_value = 0.5, min_delta = 0.2 mJy/beam, min_npix = 2 beams  
  > "The input parameters, namely “min_value” and “min_delta”, were set to 0.5 and 0.2 mJy beam$^{-1}$, respectively." (3.4.2)
   - fitting: _not stated_
   - validation: clumpfind and astrodendro results agree closely  
  > "the results obtained from both the *clumpfind* algorithm and the *astrodendro* tool exhibit close agreement with each other" (3.4.2)
2. **derive continuum source masses**: M = D^2 F_nu R_t / (B_nu(T_d) kappa_nu) (Hildebrand 1983)  
  > "we adopted $\kappa_\nu$ = 1.13 cm$^2$ g$^{-1}$ at 1.1 mm (cite: ossenkopf94; contreras18), $T_d$ = \[10, 15, 25\] K, and $D$ = 2.92 kpc." (3.4.2)
   - assumption: kappa=1.13 cm2/g at 1.1 mm; Td = 10, 15, 25 K; D = 2.92 kpc  
  > "we adopted $\kappa_\nu$ = 1.13 cm$^2$ g$^{-1}$ at 1.1 mm (cite: ossenkopf94; contreras18), $T_d$ = \[10, 15, 25\] K, and $D$ = 2.92 kpc." (3.4.2)
   - fitting: _not stated_
   - validation: mass uncertainty ~20-50% from opacity, temperature and flux  
  > "One may consider the uncertainty in the estimated mass to be typically $\sim$20% to $\sim$50%." (3.4.2)
3. **H13CO+ moment maps, spectra, PV diagrams and velocity components**: Moment 0/1/2, peak velocity maps, average spectra in 19 circles (0.8 arcsec radius), PV diagrams; scousepy spectral decomposition with 3x3 pixel SAAs  
  > "For the spectral decomposition of the H$^{13}$CO$^{+}$ spectra, we used the SAAs of size 3 $\times$ 3 pixels in the tool *SCOUSEPY*." (3.4.3)
   - software: SCOUSEPY
   - parameter: moment-0 over [24.9, 36.3] km/s; two components at [24.9, 30.2] and [30.9, 36.3] km/s  
  > "Figure [11](#fig11)f displays the distribution of the ALMA H$^{13}$CO$^{+}$(3–2) emission at two different velocities ranges at \[24.9, 30.2\] and \[30.9, 36.3\] km s$^{-1}$" (3.4.3)
   - fitting: multi-Gaussian fits in scousepy  
  > "The averaged spectra are then automatically fitted with multiple gaussian components (if present)." (3.3.1 Spatial and velocity structure of molecular gas in G11)
   - validation: _not stated_

## Software

- **clumpfind** : ALMA continuum source decomposition  
  > "The *clumpfind* IDL program (cite: williams94) has been employed in the ALMA continuum map at 1.16 mm" (3.4.2)
- **astrodendro** : dendrogram sub-structures in ALMA continuum  
  > "we have also employed the python-based *astrodendro* tool (cite: Rosolowsky2008)" (3.4.2)
- **SCOUSEPY** : spectral decomposition and ppv maps  
  > "These maps are generated using the tool *SCOUSEPY* (cite: henshaw16; henshaw19)" (3.3.1)
- **getsf** : Herschel source and filament extraction  
  > "Figure [7](#fig8xc)c presents the overlay of filament skeletons (scales $\sim$13$''$.5–256$''$) and *getsf* extracted sources" (3.3.2)
- **hires** : Herschel column density maps  
  > "The steps needed to obtain these maps using the *hires* are described in (cite: getsf_2022)" (3.2.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mass of ALMA source A at Td=10/15/25 K | 95.5 / 50 / 25 | ~20-50% | Msun | 2 | A / 274.11 / 14.5 / 95.5 / 50.0 / 25.0 |
| Masses of b1, b2, b3 at Td=10/15/25 K | b1 14.6/7.6/3.8; b2 28.3/14.8/7.4; b3 7.8/4.1/2.0 | ~20-50% | Msun | 2 | which are \[14.6, 7.6, 3.8\], \[28.3, 14.8, 7.4\], and \[7.8, 4.1, 2.0\] *M$_{\odot}$* at $T_d$ = \[10, 15, 25\] K |
| Dendrogram fluxes L1, I1, I2, I3, I4 | 154.55, 18.32, 13.34, 34.62, 8.83 | not stated | mJy | 1 | The total fluxes of L1, I1, I2, I3, and I4 are 154.55, 18.32, 13.34, 34.62, and 8.83 mJy, respectively. |
| H13CO+ velocity separation of two components | ~2 | not stated | km/s | 3 | two velocity peaks or cloud components with a velocity separation of $\sim$2 km s$^{-1}$ are present |
| Total mass of elongated cloud from 13CO (Tex=10 K) | ~10.6e4 | 30-50% | Msun | 0 | we have determined the total mass of the elongated cloud (see a dashed curve in Figure [4](#fig5)f) to be $\sim$10.6 $\times 10^4$($\sim$9 $\times 10^4$) *M$_{\odot}$* at $T_\mathrm{ex}$ = 10(20) K. |

## Qualitative findings

- ALMA continuum shows finger-like features (3500-10000 AU) around a dusty envelope (~18000 AU) with embedded sources.  
  > "The ALMA 1.16 mm continuum map shows multiple finger-like features (extent $\sim$3500–10000 AU) surrounding a dusty envelope-like feature (extent $\sim$18000 AU)" (abstract)

## Claim tuples

- H: Does G11P1 host two velocity components at small scale? | E: ALMA H13CO+(3-2) spectra, PV diagrams and moment maps toward the envelope | R: Two peaks near 29 and 31 km/s, separation ~2 km/s | F: Small-scale two-component structure consistent with large-scale components, suggesting collision | **supported**
- H: G11 hosts multiple hub-filament systems | E: Spitzer and JWST image inspection | R: Four IR-dark HFS candidates plus G11P1-HFS | F: Multiple HFSs at multiple scales | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: No complementary distribution of the two clouds was found, which does not favour a simple cloud-cloud collision signature  
  > "The analysis of the molecular line data does not favour the presence of any complementary distribution of two clouds in our target area." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Sub-filaments and HFS candidates need higher-resolution observations to validate  
  > "to validate the existence of sub-filaments and IR-dark HFS candidates, we require new continuum and line observations (resolution $<$ 2$''$)" (3.2.1)
- Caveat (inferred, ours): HFS and collision identification is largely visual
- Caveat (inferred, ours): Velocity separation of 2 km/s is small for collision claims
- Caveat (inferred, ours): Mass uncertainties depend on assumed Td and gas-to-dust ratio

## Reproducibility

- Data public (paper): ALMA continuum from public JVO archive; other data public  
  > "The ALMA continuum data underlying this article are available from the publicly accessible JVO ALMA FITS archive" (Data availability)
- Products in archive: _not stated_
- Missing: ALMA imaging details and gas-to-dust ratio
- Missing: clumpfind parameters, scousepy settings
- Data volume (inferred): ~10-50 GB for ALMA project data
- Score (inferred): 3/5, Public data and simple mass recipe, but ALMA processing and several parameters unstated; ALMA is a minor part.
- Rediscovery candidate: no, ALMA processing details missing and much of the result is qualitative or visual.

## Links

- Method: Williams et al. 1994 (cite: williams94) (clumpfind)
- Method: Rosolowsky 2008 (cite: Rosolowsky2008) (astrodendro)
- Companion: (cite: sanhueza21) (ALMA data source/calibration)
- Related: SEDIGISM
- Related: ATLASGAL
- Related: RAMPS
- Related: Hi-GAL
- Related: GLIMPSE
- Related: JWST program 1182

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 36,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
