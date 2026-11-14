# ALMA CO Observations of the Gamma-Ray Supernova Remnant RX J1713.7-3946: Discovery of Shocked Molecular Cloudlets and Filaments at 0.01 pc Scales

`2020ApJ...904L..24S` | The Astrophysical Journal Letters 2020 | first author: Sano, H. | arXiv: 2011.05018 | DOI: 10.3847/2041-8213/abc884

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Does the northwestern shell of RX J1713.7-3946 contain small-scale (0.01 pc) molecular cloudlets and filaments that explain X-ray hotspots, magnetic field amplification and gamma-ray spectra?  
  > "previous studies could not spatially resolve tiny molecular clouds relating to the X-ray hotspots and filaments at 0.05 pc scales" (Introduction)
- Target **RX J1713.7-3946 (northwestern shell)**: coordinates 17h11m48.0s, -39d30m57.6s (field center)  
  > "interactions with dense gas clouds at the closed distance of 1 kpc" (Introduction); "centered at ($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$) $=$ ($17^\mathrm{h}11^\mathrm{m}48.0s$, $-39\ensuremath{^\circ}30\ensuremath{'}57.6\ensuremath{''}$)" (5.1 ALMA CO); z/distance 1 kpc  
  > "interactions with dense gas clouds at the closed distance of 1 kpc" (Introduction); "centered at ($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$) $=$ ($17^\mathrm{h}11^\mathrm{m}48.0s$, $-39\ensuremath{^\circ}30\ensuremath{'}57.6\ensuremath{''}$)" (5.1 ALMA CO); distance from earlier work (Fukui 2003; Moriguchi 2005; Sano 2010; Maxted 2012)  
  > "interactions with dense gas clouds at the closed distance of 1 kpc" (Introduction); "centered at ($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$) $=$ ($17^\mathrm{h}11^\mathrm{m}48.0s$, $-39\ensuremath{^\circ}30\ensuremath{'}57.6\ensuremath{''}$)" (5.1 ALMA CO)

## Data provenance

- ALMA projects: 2017.1.01406.S
- bands: Band 3 (86–116 GHz)  
  > "using the ALMA Band 3 (86–116 GHz) during Cycle 5" (5.1 ALMA CO)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 46 12-m antennas, 12 7-m antennas, 4 TP antennas  
  > "We used 46 antennas of 12-m array, 12 antennas of 7-m array, and four antennas of total power (TP) array." (5.1 ALMA CO)
- configurations: _not stated_
- baselines: 8.9 to 313.7 m (3.4–120.6 kλ)  
  > "The combined baseline length of 12-m and 7-m arrays is from 8.9 to 313.7 m" (5.1 ALMA CO)
- angular resolution: 4.37" x 3.89", PA -86.6 deg (~0.02 pc)  
  > "The beam size of feathered image is $4.37\ensuremath{''} \times 3.89\ensuremath{''}$ with a position angle of $-86.6\ensuremath{^\circ}$" (5.1 ALMA CO)
- max recoverable scale: _not stated_
- sensitivity: ~0.13 K at 0.4 km/s velocity resolution  
  > "The typical noise fluctuations of the feathered image are $\sim$0.13 K at a velocity resolution of 0.4 km s$^{-1}$." (5.1 ALMA CO)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI H. Sano, Cycle 5  
  > "(PI: H. Sano, proposal ID 2017.1.01406.S)" (5.1 ALMA CO)
- Line: 12CO J=1-0 (115 GHz)
- Other facility **Chandra ACIS-I**: Archival X-ray images (1–2.5 keV) for hotspot variability comparison  
  > "We utilized archival X-ray data obtained using *Chandra*, for which the observation IDs are 736, 5560, 6370, 10090, 10091, 10092, and 12671" (5.2 Chandra X-rays)
- External data: X-ray hotspots and minor peaks identified in the NW shell  
  > "the X-ray minor peaks and X-ray hotspots identified by (cite: 2020ApJ...899..102H) are located in the intercloud regions" (Results) [from (cite: 2020ApJ...899..102H)]
- External data: Intercloud electron density ~0.10–0.13 cm^-3  
  > "considering the electron density in an intercloud region $\sim$0.10–0.13 cm$^{-3}$ (cite: 2015ApJ...814...29K)" (2.2 Magnetic field amplification) [from (cite: 2015ApJ...814...29K)]
- External data: Shock velocity 3900 km/s  
  > "$V_\mathrm{s} = 3900$ km s$^{-1}$ (cite: 2016PASJ...68..108T)" (2.2 Magnetic field amplification) [from (cite: 2016PASJ...68..108T)]
- External data: Gyro-factor eta = 1  
  > "Adopting observed values of $\eta$ = 1 (cite: 2019ApJ...877...96T)" (2.2 Magnetic field amplification) [from (cite: 2019ApJ...877...96T)]
- External data: H.E.S.S. TeV gamma-ray map  
  > "Figure [1](#fig1)a shows the overall TeV gamma-ray morphology of RX J1713.7$-$3946 (cite: 2018A&A...612A...6H)." (Results) [from (cite: 2018A&A...612A...6H)]

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

- task: tclean  
  > "We utilized the “tclean” task with natural weighting and “multi-scale” deconvolution algorithm" (5.1 ALMA CO)
- deconvolver: multi-scale  
  > "“multi-scale” deconvolution algorithm implemented in the CASA package" (5.1 ALMA CO)
- weighting robust: natural weighting  
  > "We utilized the “tclean” task with natural weighting" (5.1 ALMA CO)
- uv taper: uvtaper applied (value not given)  
  > "We applied “uvtaper” during the clean processes to improve the imaging quality." (5.1 ALMA CO)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m+7-m cleaned, then feathered with TP  
  > "We combined the cleaned interferometer data (12-m+7-m) and calibrated TP array data by using “feather” task." (5.1 ALMA CO)
- smoothing: _not stated_
- final beam: 4.37" x 3.89", PA -86.6 deg  
  > "The beam size of feathered image is $4.37\ensuremath{''} \times 3.89\ensuremath{''}$" (5.1 ALMA CO)
- final rms: ~0.13 K at 0.4 km/s  
  > "The typical noise fluctuations of the feathered image are $\sim$0.13 K at a velocity resolution of 0.4 km s$^{-1}$." (5.1 ALMA CO)

### Inherited from earlier work

- Magnetic field estimate method from X-ray variability  
  > "following the method by (cite: 2007Natur.449..576U) and (cite: 2020ApJ...899..102H)" (2.2 Magnetic field amplification) [from (cite: 2007Natur.449..576U); (cite: 2020ApJ...899..102H)]
- CO-to-H2 conversion factor 2.0e20  
  > "$N(\mathrm{H_2}) / W(\mathrm{CO}) = 2.0 \times 10^{20}$ (K km s$^{-1}$)$^{-1}$ cm$^{-2}$" (Table 1 notes) [from (cite: 1993ApJ...416..587B)]
- Penetration depth formula  
  > "According to (cite: 2012ApJ...744...71I), the penetration depth of a relativistic particle into molecular clouds $l_\mathrm{pd}$ can be described as below" (2.3 Prospects for gamma-ray spectra) [from (cite: 2012ApJ...744...71I)]

### Not stated but needed to reproduce (our reading)

- uvtaper value
- multiscale scales, cell and image size, masking and clean threshold
- feather parameters and TP calibration details
- continuum subtraction and channel selection
- calibration details and whether pipeline products used
- Gaussian fitting and cloudlet selection procedure
- Chandra epoch-by-epoch image smoothing and hotspot significance method
- gamma-ray spectrum model parameters for Figure 4

## Analysis recipe

1. **Image CO data**: tclean with natural weighting, multiscale, uvtaper; feather 12m+7m with TP  
  > "We utilized the “tclean” task with natural weighting and “multi-scale” deconvolution algorithm implemented in the CASA package" (5.1 ALMA CO)
   - software: CASA 5.6.0
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive cloudlet properties**: Single Gaussian fits to CO spectra; size from half-maximum contour; mass from N(H2)  
  > "Observed properties of cloudlets obtained by single Gaussian fitting with $^{12}$CO($J$=1–0) emission line." (Table 1 notes)
   - assumption: mu = 2.8, X = 2.0e20, D = 1 kpc  
  > "We used $\mu = 2.8$ and an equation of $N(\mathrm{H_2}) / W(\mathrm{CO}) = 2.0 \times 10^{20}$" (Table 1 notes)
   - fitting: single Gaussian  
  > "Observed properties of cloudlets obtained by single Gaussian fitting with $^{12}$CO($J$=1–0) emission line." (Table 1 notes)
   - validation: _not stated_
3. **Compare CO with Chandra X-rays per epoch**: 1–2.5 keV exposure-corrected images from reprocessed Chandra data compared with CO  
  > "We then created energy-filtered, exposure-corrected images using the “fluximage” task for each observation, where the energy band of 1–2.5 keV." (5.2 Chandra X-rays)
   - software: CIAO 4.12, chandra_repro, fluximage
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate magnetic field from hotspot variability**: Synchrotron cooling time (4 months, 1 keV) and acceleration time equations  
  > "Considering the short decay time of four months and $\varepsilon = 1$ keV, we can obtain $\sim$3 mG toward the X-ray hotspot." (2.2 Magnetic field amplification)
   - assumption: eta=1, Vs=3900 km/s  
  > "Adopting observed values of $\eta$ = 1 (cite: 2019ApJ...877...96T) and $V_\mathrm{s} = 3900$ km s$^{-1}$ (cite: 2016PASJ...68..108T)" (2.2 Magnetic field amplification)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.0: ALMA data processing, tclean, feather  
  > "The data were processed using the Common Astronomy Software Application (cite: 2007ASPC..376..127M) package version 5.6.0." (5.1 ALMA CO)
- **CIAO** 4.12 (CALDB 4.9.1): Chandra reprocessing and imaging  
  > "We used Chandra Interactive Analysis of Observations (cite: 2006SPIE.6270E..1VF) software version 4.12 with CALDB 4.9.1" (5.2 Chandra X-rays)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Beam size | 4.37 x 3.89, PA -86.6 | not stated | arcsec, deg | 1 | The beam size of feathered image is $4.37\ensuremath{''} \times 3.89\ensuremath{''}$ |
| Image rms | 0.13 | not stated | K | 1 | $\sim$0.13 K at a velocity resolution of 0.4 km s$^{-1}$ |
| CL1 mass | 0.37 | not stated | Msun | 2 | CL1 ............ / 17 12 02.95 / $-$39 32 20.4 / $10.9 \pm 0.6$ / $-14.20 \pm 0.05$ / $1.94 \pm 0.14$ / 0.08 / 0.37 / $2.6\times10^4$ |
| Cloudlet diameters | ~0.06–0.10 | not stated | pc | 2 | The typical diameters and masses of molecular cloudlets are $\sim$0.06–0.10 pc and $\sim$0.1–0.5 $M_{\odot}$, respectively. |
| B from decay time | ~3 | not stated | mG | 4 | we can obtain $\sim$3 mG toward the X-ray hotspot |
| B from acceleration time | ~300 | not stated | uG | 4 | the magnetic field strength $B$ is estimated to $\sim$300 $\mu$G |
| ISM density contrast | ~1e5 | not stated | dimensionless | 0 | the ISM density contrast is estimated to $\sim$$10^5$ |

## Qualitative findings

- Dozens of molecular cloudlets and filaments lie along X-ray filaments, while X-ray hotspots sit in intercloud regions.  
  > "these hotspots are located on the intercloud or low-density region, but not in the direction of dense cloudlets." (Results)

## Claim tuples

- H: Small-scale dense cloudlets exist in the NW shell and interact with shocks | E: ALMA 12CO(1-0) mapping at ~0.02 pc | R: Cloudlets with radii 0.03–0.05 pc and ~1e4 cm^-3 found along X-ray filaments | F: Shocked cloudlets and filaments resolved; inhomogeneous ISM supports a wind-bubble scenario | **supported**
- H: X-ray hotspots arise from shock-cloudlet interactions with amplified B | E: Compare CO with Chandra epochs; estimate B from variability | R: B ~ 0.3–3 mG; hotspots offset 0.05–0.15 pc from CO peaks | F: Hotspots generated by shock-cloudlet interaction with mG fields | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Interpretation of hotspots relies on projected separations and an assumed cylinder geometry
- Caveat (inferred, ours): Single X-factor assumed for CO to H2 at 0.01 pc scales
- Caveat (inferred, ours): Magnetic field estimates differ by 10x between two methods
- Caveat (inferred, ours): Gamma-ray prospects are speculative, no data

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (uvtaper, scales, mask, threshold)
- Missing: Chandra smoothing and hotspot detection method
- Missing: Cloudlet selection list
- Data volume (inferred): ~100 GB to 1 TB for 12m+7m+TP mosaic plus Chandra
- Score (inferred): 3/5, Data are identifiable and archival but imaging details are sparse and results are largely qualitative with simple numerics.
- Rediscovery candidate: no, Imaging recipe incomplete and main results are qualitative/interpretive.

## Links

- Companion: (cite: 2020ApJ...899..102H) (X-ray hotspot analysis used for comparison)
- Companion: (cite: 2007Natur.449..576U) (Discovery of X-ray variability)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 36,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
