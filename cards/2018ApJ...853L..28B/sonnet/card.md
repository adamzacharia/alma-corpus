# Fast, Collimated Outflow in the Western Nucleus of Arp 220

`2018ApJ...853L..28B` | The Astrophysical Journal Letters 2018 | first author: Barcos-Muñoz, Loreto | arXiv: 1712.06381 | DOI: 10.3847/2041-8213/aaa28d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is there a spatially and spectrally resolved molecular outflow in the western nucleus of Arp 220, and what are its properties and driving mechanism?  
  > "Here, we present the first spatially and spectrally resolved image of the fast collimated molecular outflow in the western nucleus of Arp 220." (Introduction)
- Target **Arp 220 (western nucleus)**: coordinates _not stated_; z/distance z = 0.018126; luminosity distance 77 Mpc  
  > "At a luminosity distance of 77 Mpc (z = 0.018126)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00702.S, 2015.1.00113.S
- bands: _not stated_
- frequencies and spectral setup: four spectral windows, each 1.875 GHz wide; 13.6 km/s resolution near HCN  
  > "We configured the correlator to process four spectral windows, each 1.875 GHz wide." (ALMA Observations of Arp 220); "After on-line smoothing, the spectral resolution near our line of interest was 13.6 km s$^{-1}$." (ALMA Observations of Arp 220)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: maximum baseline ≈ 11 km  
  > "The maximum baseline used was $\approx 11$ km" (ALMA Observations of Arp 220)
- angular resolution: _not stated_
- max recoverable scale: 1.1"  
  > "with the largest recoverable angular scale of 1.1$\ensuremath{''}$" (ALMA Observations of Arp 220)
- sensitivity: continuum rms 14.4 uJy/beam; HCN median rms 0.35 mJy/beam per channel  
  > "The median rms noise per channel is $\sigma_{\rm HCN}$=0.35 mJy beam$^{-1}$ (5 K)." (ALMA Observations of Arp 220)
- time on source: 2 hours  
  > "The total integration time on source was 2 hours." (ALMA Observations of Arp 220)
- observing dates: three sessions, 2015 Oct 15 to Oct 29  
  > "We observed Arp 220 in three sessions between 2015 October 15 and 2015 October 29" (ALMA Observations of Arp 220)
- pi or archival as stated: PI L. Barcos-Muñoz; CO data from Scoville17 and Sakamoto17  
  > "(PI: L. Barcos-Muñoz)" (ALMA Observations of Arp 220)
- Line: HCN 1–0 (88.6316 GHz)
- Other facility **ALMA CO(1–0) data (Scoville17, Sakamoto17)**: CO map for confirming the outflow; 104 GHz continuum for spectral index  
  > "we produced a similar map of CO emission using ALMA observations presented by (cite: Scoville17) and (cite: Sakamoto17)." (Further Evidence for the Outflow)
- External data: 104 GHz continuum image used for the 92–104 GHz spectral index map  
  > "Combining our image with their data, we created a spectral index map between 92 and 104 GHz." (Further Evidence for the Outflow) [from (cite: Sakamoto17)]
- External data: disk inclination 53.5 deg  
  > "(inclination 53.5$^{\circ}$; (cite: BM15))" (Properties of the Outflow) [from (cite: BM15)]
- External data: systemic velocity 5355 ± 15 km/s  
  > "We assume $\mathrm{v_{sys} = 5355 \pm 15~km~s^{-1}}$ for the western nucleus (cite: Sakamoto09)." (Results) [from (cite: Sakamoto09)]
- External data: 33 GHz continuum for the 33–92 GHz spectral index map  
  > "panel a of Figure [4](#fig:fig4) shows the spectral index map between 33 and 92 GHz." (Further Evidence for the Outflow) [from (cite: BM15)]

## Processing

### Calibration

- pipeline or manual: observatory-provided reduction script, then iterative self-calibration on continuum  
  > "We first ran the observatory-provided reduction script." (ALMA Observations of Arp 220); "produced an image of the 92.2 GHz (3.3 mm) continuum emission, which we iteratively self-calibrated." (ALMA Observations of Arp 220)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: derived from continuum and applied to line data  
  > "We applied the self-calibration derived from the continuum to the line data." (ALMA Observations of Arp 220)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted using line-free channels  
  > "Then, we subtracted the continuum and imaged the full spectral window containing the HCN (1–0) line" (ALMA Observations of Arp 220)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: HCN cube smoothed to 0.12"x0.09", PA≈-6.7 deg  
  > "we smoothed the cube to a common angular resolution for HCN (1–0) of 0$\ensuremath{''}12\times0.09\ensuremath{''}$, P.A.$\approx-6.7^{\circ}$." (ALMA Observations of Arp 220)
- final beam: continuum beam 0.09"x0.07", PA≈-13 deg  
  > "The size of the synthesized beam is 0$\ensuremath{''}09 \times 0.07\ensuremath{''}$, position angle (P.A.) $\mathrm{\approx-13^{\circ}}$." (ALMA Observations of Arp 220)
- final rms: continuum 14.4 uJy/beam; HCN 0.35 mJy/beam per channel  
  > "$\mathrm{\sigma_{92GHz}=14.4\mu Jy~beam^{-1}}$ (0.36 K)" (ALMA Observations of Arp 220)

### Inherited from earlier work

- CO data and 104 GHz continuum taken from earlier ALMA papers  
  > "using ALMA observations presented by (cite: Scoville17) and (cite: Sakamoto17)" (Further Evidence for the Outflow) [from (cite: Scoville17); (cite: Sakamoto17)]
- HCN-to-mass conversion framework  
  > "(cite: Gao_HCN04) proposed a conversion factor $\mathrm{\alpha_{HCN}= 10 M_{\odot} (K~km~s^{-1} pc^{2})^{-1}}$" (Properties of the Outflow) [from (cite: Gao_HCN04)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Imaging task, weighting/robust, cell and image size, and deconvolver settings
- Line-free channel ranges and self-calibration solution intervals
- Which of the two project codes provides HCN versus CO data
- Derivation details of the alpha_HCN versus Tex relation
- Procedure for resolution/astrometry matching of continuum images and spectral index errors
- Fitting details for Gaussian lobe sizes
- Coordinates of phase center

## Analysis recipe

1. **Calibrate and image continuum and HCN cube**: Observatory script, continuum self-calibration, applied to line, continuum subtraction, smoothing to common beam  
  > "We applied the self-calibration derived from the continuum to the line data." (ALMA Observations of Arp 220)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Map outflow in high-velocity channels**: Moment-zero maps over velocity ranges avoiding disk; outflow PA from lobe peaks; PVD along 173 deg slit  
  > "where the lower velocity bounds are selected to avoid contamination from the rotating disk." (Results)
   - parameter: S/N>2.5 in consecutive channels; vsys=5355 km/s  
  > "We observe emission having $S/N>2.5$, in consecutive channels" (Results)
   - fitting: _not stated_
   - validation: Same procedure on CO and continuum  
  > "We beam-matched the CO to the HCN and selected high velocity channels in the same way that we did for HCN." (Further Evidence for the Outflow)
3. **Continuum spectral index maps**: Match resolution and astrometry; mask at S/N>5 at 104 GHz; compute 92–104 and 33–92 GHz indices with error maps  
  > "We match the resolution and astrometry of the two images and then masked them at $S/N>5$ for the 104 GHz image." (Further Evidence for the Outflow)
   - fitting: _not stated_
   - validation: Index remains positive when uncertainties included  
  > "From the latter we observe that the positive spectral indices features along the direction of the outflow, remain positive when including the uncertainties." (Further Evidence for the Outflow)
4. **Derive luminosities, masses, sizes, ages, outflow rates**: Integrate S/N>3 contours for luminosity; alpha_HCN or alpha_CO conversion; elliptical Gaussian size fit; inclination corrections; age=size/velocity; Mdot=M/age  
  > "We measure the size of the lobes by fitting them to an elliptical Gaussian profile." (Properties of the Outflow)
   - assumption: LTE, low optical depth, alpha_HCN≥0.24, alpha_CO=0.8, T_bg=2.73 K, inclination 53.5 deg, outflow perpendicular to disk  
  > "Assuming that the outflow is perpendicular to the disk (inclination 53.5$^{\circ}$; (cite: BM15))" (Properties of the Outflow)
   - fitting: Elliptical Gaussian fit to lobes  
  > "We measure the size of the lobes by fitting them to an elliptical Gaussian profile." (Properties of the Outflow)
   - validation: LTE brightness temperature matching agrees with alpha_HCN lower limits  
  > "These lower limits agree with what we obtained trying to match the observed brightness temperature by varying the column density" (Properties of the Outflow)

## Software

- **CASA** : data reduction, imaging and analysis  
  > "The data reduction, imaging and analysis were carried out using the Common Astronomy Software Application package (cite: McM07)." (ALMA Observations of Arp 220)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Max inclination-corrected HCN outflow velocity (north) | +856 | not stated | km/s | 4 | these reflect true outflow velocities of $+856$ and $-832$ km s$^{-1}$ |
| Max inclination-corrected HCN outflow velocity (south) | -832 | not stated | km/s | 4 | these reflect true outflow velocities of $+856$ and $-832$ km s$^{-1}$ |
| HCN luminosity north / south | 2.1e7 / 8.9e6 | not stated | K km/s pc^2 | 4 | we find an HCN luminosity of $L_{\rm HCN}\simeq2.1\times10^{7}$ |
| H2 mass from HCN north / south | ≥4.9e6 / ≥2.1e6 | lower limits | Msun | 4 | we obtain $M_{\rm H_2}\geqslant 4.9\times10^{6}$ M$_{\odot}$ and $2.1\times10^{6}$ M$_{\odot}$ for the north and south lobes |
| Mass outflow rate HCN north / south | 55 / 15 | lower limits | Msun/yr | 4 | Ṁ (M$_{\odot}$ yr$^{-1}$) / 55 / 12 / 15 / 35 |
| Outflow position angle | 173 | not stated | deg | 2 | we calculate a P.A. of about 173$^{\circ}$ for the outflow |
| Dynamical age | (0.9-2.3)e5 | not stated | yr | 4 | we find dynamical ages of $\simeq(0.9-2.3)\times10^5$ yr |

## Qualitative findings

- Outflow is bipolar along the disk minor axis, accelerates away from disk, and is also seen in CO (weaker) and dust continuum with alpha≥2  
  > "The extended emission to the north and south has $\alpha \geq 2$ indicating that dust emission likely represents the dominant continuum component." (Further Evidence for the Outflow)

## Claim tuples

- H: A collimated molecular outflow exists in the western nucleus | E: HCN(1–0) channel maps, moment maps and PVDs at 0.1" resolution | R: High-velocity emission perpendicular to disk, up to ~±850 km/s | F: Fast collimated bipolar outflow detected | **supported**
- H: The outflow carries dust and is seen in other tracers | E: CO maps and spectral index maps | R: CO lobes present; positive spectral index along outflow | F: Outflow seen in CO and dust | **supported**
- H: Driving mechanism can be identified | E: Compare energetics with SN, radiation pressure and AGN models | R: All can accommodate Edot~2e43 erg/s | F: Driver remains unclear | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gas mass from 104 GHz dust emission was tried but gave values near the nuclear dynamical mass, so rejected  
  > "we obtained values close to the dynamical mass of the entire nucleus" (Properties of the Outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Low-velocity outflow overlaps disk; masses highly uncertain, lower limits  
  > "The amount of mass implied by this HCN luminosity is highly uncertain." (Properties of the Outflow)
- Caveat (inferred, ours): Mass conversion factors are very uncertain
- Caveat (inferred, ours): Disk contamination of low-velocity channels
- Caveat (inferred, ours): Perpendicular-to-disk geometry assumed for deprojection

## Reproducibility

- Data public (paper): ALMA data cited by project codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00702.S and ADS/JAO.ALMA#2015.1.00113.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Self-calibration details
- Missing: Exact velocity channel and slit definitions beyond those given
- Data volume (inferred): ~100-300 GB (long-baseline Band 3 spectral line data; two projects)
- Score (inferred): 3/5, Data public and steps outlined, but imaging parameters and calibration details are missing.
- Rediscovery candidate: no, Imaging recipe is incomplete and main results are lower limits dependent on assumptions.

## Links

- Companion: (cite: Sakamoto17) (Provides the 104 GHz continuum and CO data used)
- Companion: (cite: Scoville17) (Provides ALMA CO data)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 37,
  "rate": 0.544
 },
 "evidence_ok": true
}
```
