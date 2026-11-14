# Local Starburst Conditions and Formation of GRB 980425/SN 1998bw within a Collisional Ring

`2020ApJ...899..165A` | The Astrophysical Journal 2020 | first author: Arabsalmani, M. | arXiv: 2007.01317 | DOI: 10.3847/1538-4357/aba3c0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, transients
- Question: What are the molecular gas properties and depletion times on cloud scales near GRB 980425 in ESO 184-G82, and was the progenitor formed in situ or ejected from a starburst cluster?  
  > "Here we present the first spatially resolved study of molecular gas and its depletion time in a GRB host galaxy." (Introduction)
- Target **ESO 184-G82 (host of GRB 980425)**: coordinates _not stated_; z/distance z = 0.0086  
  > "ESO 184–G82 at $z=0.0086$ is the host galaxy of the closest known GRB, GRB 980425" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01750.S
- bands: Band 6  
  > "We used the Band-6 receivers of the ALMA 12-m Array in C43-5 configuration" (2.1 ALMA)
- frequencies and spectral setup: FDM window centred on 228.534 GHz, 1920 channels, ~1.3 km/s resolution, 1.875 GHz usable bandwidth  
  > "This spectral window was sub-divided into 1920 channels, yielding a velocity resolution of $\sim$1.3 km s$^{-1}$" (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-5, max baseline 1400 m  
  > "in C43-5 configuration (with a maximum baseline of 1400 m)" (2.1 ALMA)
- baselines: _not stated_
- angular resolution: 0.35" x 0.25" (62 x 44 pc)  
  > "we get a synthesised beam size of 0.35$^{\prime\prime}$$\times$0.25$^{\prime\prime}$  (62 pc $\times$ 44 pc at the distance of the galaxy)" (2.1 ALMA)
- max recoverable scale: 6.7 arcsec  
  > "The maximum recoverable scale for this configuration is 6.7$^{\prime\prime}$" (2.1 ALMA)
- sensitivity: ~0.4 mJy/beam/channel near line, ~0.6 at primary beam edges  
  > "a root-mean-square (rms) noise of $\sim$0.4 mJy/beam/channel close to the central frequency of the cube where we expect the line." (2.1 ALMA)
- time on source: 5 hours total  
  > "The observations were for a total time of 5 hours" (2.1 ALMA)
- observing dates: November 16, 2018  
  > "on November 16, 2018" (2.1 ALMA)
- pi or archival as stated: PI: Arabsalmani  
  > "PI: Arabsalmani" (2.1 ALMA)
- Line: CO J=2-1 (not stated)
- Other facility **HST**: MIRVIS/Clear image, GO-8648  
  > "Program ID: GO-8648, PI: Kirshner" (2.2 Ancillary data)
- Other facility **VLT/MUSE**: Halpha map for SFR  
  > "Program ID: 095.D-0172(A); PI: Kuncarayakti" (2.2 Ancillary data)
- External data: Metallicity range 0.28-0.44 Zsun  
  > "We therefore adopt a full metallicity range of $0.28-0.44\,Z_{\odot}$ reported by (cite: Kruhler17-2017A&A...602A..85K)" (3 Measurements and Results) [from (cite: Kruhler17-2017A&A...602A..85K)]
- External data: alpha_CO 12-40 from metallicity-dependent prescription  
  > "we adopt the metallicity-dependent $\alpha_{\rm CO}$ suggested by (cite: Wolfire10-2010ApJ...716.1191W)" (3 Measurements and Results) [from (cite: Wolfire10-2010ApJ...716.1191W)]
- External data: CO(2-1)/CO(1-0) ratio 0.8  
  > "We also assume a ratio of 0.8 for the brightness temperature luminosity of the CO(2-1) to CO(1-0) lines" (3 Measurements and Results) [from (cite: Leroy09-2009AJ....137.4670L)]
- External data: HI ring identification  
  > "which was identified through Hi 21 cm emission observations presented in (cite: Arabsalmani19-2019MNRAS.485.5411A)" (3 Measurements and Results) [from (cite: Arabsalmani19-2019MNRAS.485.5411A)]

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline  
  > "The data are calibrated using the ALMA Science Pipeline" (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5  
  > "With Briggs weighting with robust=0.5" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: AIPS MOMNT mask: Gaussian FWHM 6 pixels spatial smoothing, Hanning over 3 channels, threshold ~2x rms  
  > "choose a threshold flux of approximately 2 times the root-mean-square (RMS) noise in a line-free channel of the spectral cube" (2.1 ALMA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to cube  
  > "Due to the primary beam correction applied to the cube" (2.1 ALMA)
- array combination: _not stated_
- smoothing: cube velocity resolution ~3 km/s  
  > "produce a spectral cube with a velocity resolution of $\sim$3 km s$^{-1}$" (2.1 ALMA)
- final beam: 0.35" x 0.25"  
  > "synthesised beam size of 0.35$^{\prime\prime}$$\times$0.25$^{\prime\prime}$" (2.1 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- Moment-2 to FWHM conversion  
  > "We then convert it to the FWHM velocity, FWHM$_{\rm mom-2}$ (cite: Rosolowsky06-2006PASP..118..590R)." (3 Measurements and Results) [from (cite: Rosolowsky06-2006PASP..118..590R)]
- SFR calibration from Halpha, Salpeter IMF  
  > "using the calibration of (cite: Kennicutt98-1998ApJ...498..541K), assuming a Salpeter initial mass function (IMF)" (3 Measurements and Results) [from (cite: Kennicutt98-1998ApJ...498..541K)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Imaging task parameters (cell, image size, deconvolver, niter, threshold)
- Line-free channels / continuum subtraction method
- Flux calibrator and flux scale uncertainty
- Halpha map extraction regions for gas complexes
- Exact MUSE reduction and Halpha flux measurement details
- Distance used for physical scales

## Analysis recipe

1. **Calibrate and image CO(2-1) cube and continuum**: ALMA pipeline calibration, imaging with Briggs robust=0.5, 3 km/s channels; continuum from 227.7-228.5 and 228.7-229.4 GHz  
  > "We also make a continuum image combining the frequency windows of $227.7-228.5$ GHz and $228.7-229.4$ GHz." (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps**: AIPS MOMNT with smoothed-mask  
  > "We obtain the total-intensity and intensity-weighted velocity field maps of the CO(2-1) emission line using the MOMNT task in ‘classic’ AIPS" (2.1 ALMA)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify clumps**: Local peaks in moment-0 separated by at least one beam; accept if detected in >=2 adjacent channels with total >=5 sigma; PV diagrams checked for substructure  
  > "If the emission in the region is detected in at least two adjacent channels, and with a total significance of at least 5$\sigma$, we identify it as a clump." (3 Measurements and Results)
   - fitting: _not stated_
   - validation: PV diagrams searched for kinematic substructure; none found  
  > "Such a search, however, did not reveal any such structure in any of the gas clumps." (3 Measurements and Results)
4. **Measure fluxes, luminosities and line widths**: Integrate adjacent channels above rms; significance = flux/(sqrt(N) x rms); FWHM from moment-2 max and Gaussian fits, corrected for resolution  
  > "The significance of detection for each clump is calculated by dividing the total flux by $\rm \sqrt{N} \times$ rms-noise-per-channel" (3 Measurements and Results)
   - fitting: Gaussian fits to spectra  
  > "We also fit Gaussian functions to the spectra of all the clumps" (3 Measurements and Results)
   - validation: Two FWHM methods compared; consistent except C2  
  > "We find the two measurements to be consistent for all the clumps but C2." (3 Measurements and Results)
5. **Derive molecular gas masses**: M_mol from L'CO(2-1) with r21=0.8 and alpha_CO=12-40  
  > "We therefore use a range of $\alpha_{\rm CO} = 12-40\, M_{\odot}\,\rm(K\,km\,s^{-1}\,pc^{2})^{-1}$" (3 Measurements and Results)
   - assumption: metallicity 0.28-0.44 Zsun; CO(2-1)/CO(1-0)=0.8  
  > "estimate the molecular gas mass of all the clumps over this metallicity range" (3 Measurements and Results)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compute SFR and depletion times per gas complex**: Total Halpha flux from MUSE in CO-defined regions, Kennicutt98 calibration, Salpeter IMF, no extinction correction; tau_dep = M_mol/SFR  
  > "we do not apply such a correction" (3 Measurements and Results)
   - assumption: E(B-V)=0.05 mag, extinction correction negligible  
  > "galaxy-averaged attenuation of $E_{B-V}$ of 0.05 mag" (3 Measurements and Results)
   - fitting: _not stated_
   - validation: _not stated_
7. **Upper limit on depletion time at GRB position**: 3 sigma per channel over >=2 channels in ~150 pc region at GRB position  
  > "The upper limit is based on the CO(2-1) emission having a significance of 3$\sigma$ in each channel, and spread over at least two channels" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging (named implicitly via package reference)  
  > "The data are calibrated using the ALMA Science Pipeline, part of the package (cite: McMullin07-2007ASPC..376..127M)." (2.1 ALMA)
- **AIPS** classic: MOMNT moment maps  
  > "using the MOMNT task in ‘classic’ AIPS" (2.1 ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO clumps | 11 | not stated | dimensionless | 3 | We detect eleven molecular gas clumps in the galaxy, seven of which are within the gas ring. |
| Continuum flux of HII region | 0.197 | 0.064 | mJy | 1 | We measured an integrated flux of $0.197 \pm 0.064$ mJy for the continuum in this region |
| Brightest clump C5 integrated flux | 177.6 | 6.9 | mJy km/s | 4 | / C5    / 26  / 177.6$\pm$6.9     / 14.7 $\times 10^4$ |
| C5 molecular gas mass | 22-74 | not stated | 1e5 Msun | 5 | 22$-$74 |
| Spread of tau_dep | 1.9 | not stated | dex | 6 | We find the molecular gas depletion times to show a variation of 1.9 dex |
| Upper limit tau_dep at GRB position | 0.37-1.25 | not stated | Gyr | 7 | we estimate an upper limit of $0.37-1.25$ Gyr for the molecular gas depletion time at the GRB position |
| Offset of GRB from nearest clumps C8-C9 | 1.6 arcsec (~280 pc) | not stated | arcsec | 0 | The location of GRB 980425 is offset by about 1.6$^{\prime\prime}$  ($\sim$280 pc) from the centre of the closest clumps, C8-C9 |

## Qualitative findings

- No molecular gas detected at GRB position; native cloud likely dispersed by feedback  
  > "we do not detect any molecular gas at the position of GRB 980425" (4 Discussion)

## Claim tuples

- H: Does the galaxy host local starburst conditions despite normal global properties? | E: Compare clump-scale depletion times with other galaxies | R: 1.9 dex spread in tau_dep | F: Local starburst mode exists in the galaxy | **supported**
- H: Are clump masses sufficient to form massive clusters? | E: Estimate gas masses with alpha_CO 12-40 | R: clump masses >=1e5 Msun | F: Sufficient for clusters >1e4 Msun | **supported**
- H: Was the GRB progenitor formed in situ or ejected? | E: Compare GRB position to clumps, stellar age and runaway velocities | R: Nearest clump 280 pc away; 90 km/s needed; stars at GRB site ~5 Myr | F: In situ formation most likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Runaway from the WR region (~300 km/s) judged rare; ejection from C8-C9 considered more likely than from WR region  
  > "Such a large runaway velocity, though possible, is very rare" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Clump sizes unreliable, not reported, because they are smaller than the beam  
  > "The size measurements are therefore not reliable and hence we do not report these measurements." (3 Measurements and Results)
- Limitation (authors): Cloud-scale depletion times are not consistently measurable owing to gas-star offsets  
  > "it is not possible to *consistently* measure the efficiency of star formation, or the depletion time, on cloud scales" (3 Measurements and Results)
- Caveat (inferred, ours): alpha_CO uncertain by factor >3, so mass and tau_dep absolute values are loose
- Caveat (inferred, ours): SFR from coarser MUSE resolution applied to complexes with few measurements
- Caveat (inferred, ours): 1.9 dex spread depends on assumed fixed alpha_CO and varying resolution comparisons
- Caveat (inferred, ours): Only one galaxy; small clump statistics

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "project code: 2018.1.01750.S; PI: Arabsalmani" (2.1 ALMA)
- Products in archive: _not stated_
- Missing: CASA/pipeline versions and tclean parameters
- Missing: clump region definitions and moment map masks beyond MOMNT settings
- Missing: MUSE Halpha region definitions
- Data volume (inferred): ~50-100 GB raw for one 5 h Band 6 execution set; plus MUSE cube
- Score (inferred): 3/5, Data identified and main steps described, but imaging/region details missing; results numeric in a table.
- Rediscovery candidate: yes, Single ALMA project, simple measurements, tabulated numeric results; some details need guessing.

## Links

- Method: (cite: Wolfire10-2010ApJ...716.1191W) (alpha_CO metallicity dependence)
- Method: (cite: Kennicutt98-1998ApJ...498..541K) (SFR from Halpha)
- Companion: (cite: Arabsalmani19-2019MNRAS.485.5411A) (HI ring and collision scenario)
- Companion: (cite: Arabsalmani19-2019ApJ...882...31A) (similar ALMA study of SLSN host)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
