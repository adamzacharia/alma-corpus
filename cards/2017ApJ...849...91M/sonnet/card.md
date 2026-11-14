# Physical Properties of 15 Quasars at z ≳ 6.5

`2017ApJ...849...91M` | The Astrophysical Journal 2017 | first author: Mazzucchelli, C. | arXiv: 1710.01251 | DOI: 10.3847/1538-4357/aa9185

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the physical properties (black hole masses, accretion rates, CIV blueshifts, FeII/MgII, near zone sizes, [CII]/IR luminosities) of the 15 known quasars at z>~6.5, including six newly discovered from Pan-STARRS1?  
  > "Our goal is to implement a coherent investigation of several key quasar properties (i.e., black hole mass, accretion rate, near zone size and infrared luminosity), and compare them to lower redshift samples." (Introduction)
- Target **PSO J231.6576-20.8335**: coordinates 15:26:37.841 -20:50:00.66  
  > "PSO J231.6576–20.8335 | 15:26:37.841 | –20:50:00.66 | 6.5864 | 0.0005 | \[CII\]" (Table 5); z/distance z=6.5864  
  > "PSO J231.6576–20.8335 | 15:26:37.841 | –20:50:00.66 | 6.5864 | 0.0005 | \[CII\]" (Table 5); distance from [CII] redshift from ALMA survey (Decarli, in prep)  
  > "PSO J231.6576–20.8335 | 15:26:37.841 | –20:50:00.66 | 6.5864 | 0.0005 | \[CII\]" (Table 5)
- Target **PSO J167.6415-13.4960**: coordinates 11:10:33.976 -13:29:45.60  
  > "PSO J167.6415–13.4960 | 11:10:33.976 | –13:29:45.60 | 6.5148 | 0.0005 | \[CII\]" (Table 5); z/distance z=6.5148  
  > "PSO J167.6415–13.4960 | 11:10:33.976 | –13:29:45.60 | 6.5148 | 0.0005 | \[CII\]" (Table 5); distance from [CII] redshift from ALMA survey (Decarli, in prep)  
  > "PSO J167.6415–13.4960 | 11:10:33.976 | –13:29:45.60 | 6.5148 | 0.0005 | \[CII\]" (Table 5)
- Target **PSO J183.1124+05.0926**: coordinates 12:12:26.981 +05:05:33.49  
  > "PSO J183.1124+05.0926 | 12:12:26.981 | +05:05:33.49 | 6.4386 | 0.0004 | \[CII\]" (Table 5); z/distance z=6.4386  
  > "PSO J183.1124+05.0926 | 12:12:26.981 | +05:05:33.49 | 6.4386 | 0.0004 | \[CII\]" (Table 5); distance from [CII] redshift from ALMA survey (Decarli, in prep)  
  > "PSO J183.1124+05.0926 | 12:12:26.981 | +05:05:33.49 | 6.4386 | 0.0004 | \[CII\]" (Table 5)

## Data provenance

- ALMA projects: 2012.1.00882.S, 2015.1.01115.S
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
- Line: [CII] 158 um fine-structure line (not stated)
- Other facility **IRAM NOEMA**: [CII] line and continuum for PSO323+12, PSO338+29, PSO006+39, HSC1205  
  > "Four quasars in our sample (PSO323+12, PSO338+29, PSO006+39 and HSC1205) have been observed with the NOrthern Extended Millimeter Array (NOEMA)" (3.3 NOEMA observations)
- Other facility **Pan-STARRS1**: z-dropout candidate selection catalog (PV3)  
  > "We use here the third internal release of the 3$\pi$ stacked catalog (PS1 PV3, in the internal naming convention)." (Introduction)
- Other facility **Magellan/FIRE, VLT/FORS2, X-Shooter, Keck/LRIS and others**: optical/NIR spectroscopy for MgII/CIV analysis  
  > "These observations have been obtained with a variety of telescopes and spectrographs: VLT/FORS2, P200/DBSP, MMT/Red Channel, Magellan/FIRE, VLT/X-Shooter" (3.2 Spectroscopic follow-up)
- External data: [CII] redshifts of PSO231-20, PSO167-13, PSO183+05 from ALMA survey  
  > "The redshifts of PSO231-20, PSO167-13 and PSO183+05 are measured from the \[CII\] line, observed in our ALMA survey of cool gas and dust in $z\gtrsim6$ quasars" (5.1 Redshifts) [from (cite: DecarliSub)]
- External data: Near zone sizes of 34 quasars at 5.77<z<6.54 for comparison  
  > "Recently, (cite: Eilers17) addressed some of these caveats, deriving near zone sizes of 34 quasars at $5.77 \lesssim z \lesssim 6.54$." (Introduction) [from (cite: Eilers17)]

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

- Near zone analysis follows Eilers17 (PCA continuum modeling with Paris11 PCS, luminosity scaling)  
  > "In our study, we follow the approach by (cite: Eilers17), mainly referring to (cite: Paris11) who provide PCS functions" (5.10 Near Zones) [from (cite: Eilers17)]
- Candidate selection follows and expands earlier PS1 searches  
  > "We follow and expand the selection illustrated both in (cite: Banados16), which was focused on lower redshift objects ($z\sim$ 6), and in (cite: Venemans15)." (2 Candidate Selection) [from (cite: Banados16), (cite: Venemans15)]

### Not stated but needed to reproduce (our reading)

- ALMA data are only used via the Decarli et al. in prep [CII] redshifts; no ALMA calibration or imaging given
- NOEMA line-fit windows and continuum map procedure not detailed
- Exact SED/spectrum fitting window adjustments for sky lines not given

## Analysis recipe

1. **Derive systemic redshifts**: [CII] flat+Gaussian fit to NOEMA spectra; ALMA [CII] redshifts from literature; MgII or template otherwise  
  > "A flat continuum and a Gaussian profile are fitted to the spectra, as shown in Figure [4](#figCIIline), allowing us to derive $z_{\mathrm{[CII]}}$" (5.1 Redshifts)
   - software: GILDAS clic, GILDAS mapping
   - fitting: _not stated_
   - validation: _not stated_
2. **Black hole masses and Eddington ratios**: Fit power law + Balmer continuum + FeII template + MgII Gaussian by chi2; Vestergaard & Osmer 2009 virial relation; Shen08 bolometric correction  
  > "We derive the mass of the black hole following (cite: VestergaardOsmer09):" (5.6 Black Hole Masses)
   - assumption: Eddington luminosity L_Edd = 1.3e38 M_BH; L_bol = 5.15 lambda L3000  
  > "\frac{L_{\mathrm{bol}}}{\mathrm{erg\, s^{-1}}} = 5.15 \times \frac{\lambda L_{\lambda,3000}}{\mathrm{erg\, s^{-1}}}" (5.6 Black Hole Masses)
   - fitting: chi2 minimization; 14th/86th percentiles as 1 sigma  
  > "We consider the 14th and 86th interquartiles of the $\chi^{2}$ distribution as our 1$\sigma$ confidence levels." (5.5 Mg II and Fe II emission modeling)
   - validation: Compared with luminosity-matched SDSS sample (1000 random draws)  
  > "we repeat this trial for 1000 times" (5.6 Black Hole Masses)
3. **FIR/TIR and [CII] luminosities**: Modified blackbody scaled to continuum flux; integrate 42.5-122.5 um (FIR) and 8-1000 um (TIR)  
  > "We take $T_{d}=47$ K and $\beta=1.6$, which are typical values assumed in the literature (cite: Beelen06)." (5.9 Infrared and [CII] luminosities)
   - assumption: T_d = 47 K, beta = 1.6, optically thin  
  > "We take $T_{d}=47$ K and $\beta=1.6$, which are typical values assumed in the literature (cite: Beelen06)." (5.9 Infrared and [CII] luminosities)
   - fitting: _not stated_
   - validation: _not stated_
4. **Near zone sizes**: R_NZ where transmitted flux <0.1 at 20 A smoothing; PCA continuum; rescale to M1450=-27; power-law fit vs redshift  
  > "$R_{\mathrm{NZ}}$ is the distance from the central source where the transmitted flux drops below 0.1, once the spectrum has been smoothed to a resolution of 20  Å." (5.10 Near Zones)
   - fitting: Power law in (1+z)/7  
  > "The best fit of the evolution of $R_{\mathrm{NZ,corr}}$ with $z$, modeled as a power law function, gives the following:" (5.10 Near Zones)
   - validation: Compared with Eilers17  
  > "The values obtained are consistent, within the errors, with the results of (cite: Eilers17)" (5.10 Near Zones)

## Software

- **GILDAS (clic, mapping)** : NOEMA data processing and analysis  
  > "Data were processed with the latest release of the software clic in the GILDAS suite, and analyzed using the software mapping" (3.3 NOEMA observations)
- **Astropy** : acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean log L_bol/L_Edd, z>~6.5 quasars | -0.41 | scatter 0.44 | dex | 2 | $\langle \mathrm{log} (L_{\mathrm{bol}}/L_{\mathrm{Edd}}) \rangle$=-0.41, with a scatter of 0.34 and 0.44 |
| Near zone evolution fit | R_NZ,corr = 4.49 (1+z)/7)^-1.00 | ±0.92 norm, ±0.20 slope | pMpc | 4 | R_{\mathrm{NZ,corr}} = (4.49 \pm 0.92) \times \left( \frac{1+z}{7} \right) ^{-1.00 \pm 0.20} |
| Mean CIV blueshift high-z | 2940 | std 1761 | km/s | 0 | 2940, 2438 and 1761 km s$^{-1}$ |

## Qualitative findings

- High-z quasars show large CIV blueshifts, similar accretion to luminosity-matched low-z quasars, and shallow near zone evolution  
  > "we confirm a shallow evolution of the decreasing quasar near zone sizes with redshift" (abstract)

## Claim tuples

- H: Do z>6.5 quasars accrete at different rates from lower-z quasars? | E: MgII-based BH masses compared with luminosity-matched SDSS samples | R: mean log Eddington ratio -0.41 vs -0.47 | F: No convincing evolution in accretion rate | **supported**
- H: Do near zone sizes evolve steeply with redshift? | E: PCA-based near zone sizes for 11 quasars combined with Eilers17 | R: slope -1.00±0.20 | F: Shallow evolution | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): High-z sample biased to high luminosities  
  > "We also note that the high$-$redshift sample is biased towards higher luminosities" (6 Discussion and Conclusions)
- Caveat (inferred, ours): ALMA data only indirect; core ALMA reduction not documented
- Caveat (inferred, ours): FeII fluxes very uncertain
- Caveat (inferred, ours): BH mass zero-point scatter 0.55 dex

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Decarli et al. ALMA [CII] redshifts (in prep)
- Missing: custom fitting routines
- Data volume (inferred): small for ALMA part (only redshift inputs); optical/NIR spectra are separate
- Score (inferred): 2/5, ALMA plays a minor role and key recipe details are in unpublished or custom work.
- Rediscovery candidate: no, ALMA data not central; analysis based on non-ALMA spectra and custom code.

## Links

- Method: (cite: Eilers17) (near zone method)
- Method: (cite: Banados16) (selection and redshift methods)
- Companion: (cite: DecarliSub) (ALMA [CII] survey of z>~6 quasars)
- Related: Pan-STARRS1
- Related: ALMA survey of z>6 quasars

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 31,
  "rate": 0.419
 },
 "evidence_ok": true
}
```
