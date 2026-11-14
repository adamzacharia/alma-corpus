# Stellar structures, molecular gas, and star formation across the PHANGS sample of nearby galaxies

`2021A&A...656A.133Q` | Astronomy and Astrophysics 2021 | first author: Querejeta, M. | arXiv: 2109.04491 | DOI: 10.1051/0004-6361/202140695

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How is molecular gas and star formation organised across the PHANGS sample of nearby galaxies, and what role does galactic environment (bars, spiral arms, centres) play?  
  > "How is molecular gas and star formation organised across the PHANGS sample of nearby galaxies? What role does galactic environment play?" (1 Introduction)
- Target **PHANGS–ALMA main sample of 74 nearby star-forming galaxies**: coordinates _not stated_; z/distance D up to ~17 Mpc  
  > "we focus on the nominal PHANGS–ALMA sample of 74 galaxies, which covers most of the nearby, massive, star-forming galaxies with moderate inclinations selected to have distances out to $D \approx 17$ Mpc" (2.1 Sample); distance from compilation of Anand et al. 2021 (PHANGS sample table v1.6)  
  > "we focus on the nominal PHANGS–ALMA sample of 74 galaxies, which covers most of the nearby, massive, star-forming galaxies with moderate inclinations selected to have distances out to $D \approx 17$ Mpc" (2.1 Sample)

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.00803.S, 2013.1.01161.S, 2015.1.00121.S, 2015.1.00782.S, 2015.1.00925.S, 2015.1.00956.S, 2016.1.00386.S, 2017.1.00886.L, 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m, 7 m and total power combined  
  > "Our observations combine ALMA 12 m-array, 7 m-array and total-power (TP) single-dish data in order to recover emission from all spatial scales." (2.3 PHANGS–ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 arcsec (50-150 pc)  
  > "Our typical ALMA angular resolution of ${\sim}1\ensuremath{''}$ translates into a physical scale of $50{-}150$ pc." (2.3 PHANGS–ALMA data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Other facility **Spitzer IRAC 3.6 micron**: Images used to define stellar-structure environmental masks (S4G, SINGS, archival, and new observations)  
  > "We construct a set of 2D environmental masks relying on *Spitzer* IRAC $3.6$ $\mu$m images" (1 Introduction)
- Other facility **WISE and GALEX**: 22 micron and FUV/NUV for kpc-scale SFRs  
  > "we adopt a linear combination of *GALEX* FUV and *WISE* $22$ $\mu$m as long as both bands are available" (2.4 Star formation rate measurements)
- Other facility **MPG 2.2 m WFI / du Pont 2.5 m**: Narrow-band Halpha images for ~1 arcsec SFR  
  > "A total of 65 galaxies from the PHANGS–ALMA parent sample were observed between 2016 and 2019 with the Wide Field Imager (WFI) at the MPG 2.2-metre telescope" (2.4 Star formation rate measurements)
- External data: PHANGS sample table v1.6 (distances, stellar mass, effective radius)  
  > "We adopt the distances, centre, and orientation parameters from the PHANGS sample table (release v1.6, late-2020; (cite: 2021arXiv210407739L))." (2.3 PHANGS–ALMA data) [from (cite: 2021arXiv210407739L)]
- External data: Disc centre, inclination, position angle from CO kinematics  
  > "the centre, inclination and position angle of the disc come from the CO kinematic analysis presented in (cite: 2020ApJ...897..122L)" (2.3 PHANGS–ALMA data) [from (cite: 2020ApJ...897..122L)]
- External data: Bar, ring, lens and spiral catalogues for S4G galaxies  
  > "For galaxies in S$^4$G, we mostly follow (cite: 2015A&A...582A..86H), who homogeneously defined the size of bars visually on *Spitzer* $3.6$ $\mu$m images." (3.1 Bars) [from (cite: 2015A&A...582A..86H)]
- External data: S4G Pipeline 4 GALFIT bulge/disc decompositions  
  > "the GALFIT (cite: 2002AJ....124..266P; 2010AJ....139.2097P) photometric decompositions from Pipeline 4 (cite: 2015ApJS..219....4S)" (2.2.1 Products from the S4G survey) [from (cite: 2015ApJS..219....4S)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: PHANGS-ALMA public data cubes version 4.0 used  
  > "We use the PHANGS data cubes publicly released in mid-2021 (PHANGS–ALMA version 4.0)." (2.3 PHANGS–ALMA data)
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
- masking: Simple inclusive masks spanning full galaxy velocity range per line of sight; velocity windows in Table 1  
  > "These maps were computed using very simple and inclusive masks, constructed to span the full velocity coverage of the galaxy along each line of sight" (2.3 PHANGS–ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m+7 m+TP; 7 m+TP used for spiral-width criterion  
  > "we used ALMA 7 m+TP observations (instead of the higher-resolution 12 m+7 m+TP data) because spiral arms are more clearly identifiable" (3.2 Spiral arms and interarm regions)
- smoothing: Maps convolved to common 1.5 kpc resolution for kpc-scale analysis  
  > "intensity maps that were convolved to a common physical resolution of $1.5$ kpc" (2.3 PHANGS–ALMA data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA survey design, calibration, imaging and cubes  
  > "the survey is presented in detail in (cite: 2021arXiv210407739L)" (2.3 PHANGS–ALMA data) [from (cite: 2021arXiv210407739L)]
- Metallicity-dependent alpha_CO prescription  
  > "Our preferred approach is to use a metallicity-dependent $\alpha_{\rm CO}$ conversion factor as detailed in (cite: 2020ApJ...892..148S)" (2.3 PHANGS–ALMA data) [from (cite: 2020ApJ...892..148S)]
- kpc-scale hexagonal-aperture measurements database  
  > "we rely on measurements at matched kpc resolution from the PHANGS multi-wavelength database presented in (cite: 2020ApJ...901L...8S)" (2.3 PHANGS–ALMA data) [from (cite: 2020ApJ...901L...8S)]
- UV+IR SFR coefficients  
  > "The coefficients that scale the luminosity in each band ($\nu L_\nu$) to SFRs follow the prescription presented in (cite: 2019ApJS..244...24L)." (2.4 Star formation rate measurements) [from (cite: 2019ApJS..244...24L)]

### Not stated but needed to reproduce (our reading)

- The Halpha SFR survey (Razza et al.) and kpc database (Sun et al.) are in prep.; exact data products not available
- Bisector fit implementation and uncertainty estimation for KS relation not given
- Exact hexagon-to-environment assignment code and mask files require the released masks
- Hand-adjusted spiral endpoints and visual bar/ring widths not reproducible from text
- Linear-combination coefficients for Halpha+22um and UV+22um SFRs not given

## Analysis recipe

1. **Build environmental masks**: Define centre, bar, spiral, interarm, disc from Spitzer 3.6um via visual bar/ring/lens ellipses, log-spiral fits with CO-based width, and GALFIT bulge/disc; assign pixels uniquely  
  > "we define five basic dominant environments: (1) centre, (2) bar, (3) spiral arms, (4) interarm, and (5) disc without spiral masks." (3.8 Uniquely assigning pixels)
   - software: GALFIT, astrometry.net, MOPEX
   - parameter: spiral width grown in 500 pc steps until flux ratio between steps falls below 1.25  
  > "The final width was established when the ratio of CO flux from one step to the next falls below an empirical threshold of $1.25$" (3.2 Spiral arms and interarm regions)
   - fitting: _not stated_
   - validation: Masks inspected on gas and SF maps with several rounds of quality flagging by three co-authors  
  > "This involved several rounds of quality flagging by three co-authors (MQ, ES, SEM)" (3.2 Spiral arms and interarm regions)
2. **Convert CO to molecular surface density and census**: Sigma_mol = alpha_CO R21^-1 I_CO cos(i); integrate area, H2 mass and SFR per environment at ~1 arcsec within ALMA field of view  
  > "$\Sigma_{\rm mol} = \alpha_{\rm CO}\, R_{21}^{-1}\, I_{\rm CO}^{21} \cos(i)$" (2.3 PHANGS–ALMA data)
   - parameter: R21 = 0.65  
  > "We adopt a line ratio of $R_{21}=0.65$" (2.3 PHANGS–ALMA data)
   - assumption: alpha_CO = 4.35 Z'^-1.6; metallicity gradient -0.1 dex per Re  
  > "a fixed radial metallicity gradient in each galaxy ($-0.1\,{\rm dex}\,R_{\rm e}^{-1}$" (2.3 PHANGS–ALMA data)
   - fitting: _not stated_
   - validation: Repeated for galaxies with FoV > R25  
  > "This confirms that the results in Table [\[table:stats\]] and Fig. [4] are not strongly influenced by differences in the ALMA coverage among galaxies." (4.1 Census)
3. **Kpc-scale surface densities, depletion times and KS relation per environment**: Assign hexagonal apertures to an environment if >=80% of CO and SFR flux lies in it; compute medians, depletion times; bisector power-law fits; within-galaxy contrasts  
  > "A given hexagonal aperture is assigned to one of the environments considered here (centre, bar, spiral, interarm, or disc without spiral masks) if at least $80$% of the CO emission and SFR in the hexagon falls within the footprint" (4.2 Radial trends)
   - parameter: 1 kpc hexagon spacing, 1.5 kpc resolution  
  > "with a separation of $1$ kpc in the plane of the sky between centres of adjacent hexagons" (2.3 PHANGS–ALMA data)
   - fitting: bisector power-law fit  
  > "including the best-fit power-law regressions to the data using a bisector fit" (4.3 Surface densities and depletion time)
   - validation: Threshold varied 70-90%; alternative alpha_CO prescriptions  
  > "Therefore, we can conclude that the choice of threshold does not strongly impact our results." (Sanity checks)

## Software

- **GALFIT** : Bulge/disc decompositions (S4G pipeline 4)  
  > "carried out systematic decompositions of the entire S$^4$G sample with GALFIT" (3.5 Bulges)
- **MOPEX** : Reducing new Spitzer IRAC imaging  
  > "We reduced the data using MOPEX, starting from the corrected basic calibrated data files" (2.2.2 Additional archival and new observations)
- **astrometry.net** : Astrometric correction of IRAC images  
  > "we ran all the IRAC images through [astrometry.net](astrometry.net) to correct for possible small astrometric offsets" (2.2.2 Additional archival and new observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Global molecular KS slope | 0.97 | 0.06 | dimensionless | 3 | The slope fitted to all the PHANGS data points together is close to 1 ($N = 0.97 \pm 0.06$). |
| Centre fraction of area | 0.66 | not stated | % | 2 | Area [kpc$^2$] / 92 (0.66 %) |
| Centre fraction of SFR | 25.2 | not stated | % | 2 | SFR [$M_\odot$ yr$^{-1}$] / 23.9 (25.2 %) |
| Median depletion time centres / bars | 1.2 / 2.1 | not stated | Gyr | 3 | Centres have the shortest depletion times (i.e. they are more efficient at forming stars), with a median of $1.2$ Gyr, while bars have the longest depletion times (median of $2.1$ Gyr). |
| Median arm/interarm ratio of Sigma_mol and Sigma_SFR | 2.78 and 2.47 | not stated | dimensionless | 3 | with a median value of $2.78$ and $2.47$, respectively |
| Median arm/interarm depletion-time ratio | 1.25 | not stated | dimensionless | 3 | with a median factor $1.25$ |

## Qualitative findings

- Molecular gas and SFR are evenly distributed across environments despite very different areas  
  > "molecular gas and star formation are quite evenly distributed among centres, bars, spiral arms, interarm, and discs without spirals" (6 Summary)

## Claim tuples

- H: Do spiral arms enhance star formation efficiency? | E: Arm/interarm contrasts of depletion time within galaxies at kpc scale | R: Median arm/interarm depletion-time ratio 1.25 | F: Arms pile up gas but do not shorten depletion times | **supported**
- H: Is star formation suppressed in bars? | E: Compare depletion times in bars vs disc/interarm | R: Bar depletion times comparable | F: Bars not systematically less efficient | **supported**
- H: Molecular KS relation is linear across environments | E: Bisector fits per environment | R: N=0.97±0.06 globally | F: Slopes consistent with unity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Alternative alpha_CO prescriptions (constant MW, N12, B13) tested  
  > "we also consider alternative prescriptions for the conversion factor in Appendix [7]" (2.3 PHANGS–ALMA data)
- How they decided it was enough: _not stated_
- Limitation (authors): Spiral masks are broad; contrasts may be resolution-dependent; centre results sensitive to alpha_CO and AGN contamination  
  > "We also recall that we are performing measurements at kpc-resolution, but the contrast might be resolution-dependent." (4.4)
- Caveat (inferred, ours): Masks rely on subjective visual choices
- Caveat (inferred, ours): Selection effect: spiral masks only in massive galaxies
- Caveat (inferred, ours): ALMA field of view limits coverage of outer discs

## Reproducibility

- Data public (paper): PHANGS-ALMA v4.0 cubes and the masks are publicly released  
  > "We use the PHANGS data cubes publicly released in mid-2021 (PHANGS–ALMA version 4.0)." (2.3 PHANGS–ALMA data)
- Products in archive: _not stated_
- Missing: Kpc-scale SFR database (Sun et al. in prep.)
- Missing: Halpha maps (Razza et al. in prep.)
- Missing: Fit code details
- Data volume (inferred): Large; PHANGS-ALMA cubes for 74 galaxies, hundreds of GB to TB (but released moment maps are much smaller)
- Score (inferred): 3/5, Data and masks are public, but the pipeline depends on unpublished databases and visual choices; ALMA data processing is inherited.
- Rediscovery candidate: no, Key inputs (kpc database, SFR maps) are in preparation and mask construction is partly subjective.

## Links

- Method: (cite: 2021arXiv210407739L) (PHANGS-ALMA survey design and reduction)
- Method: (cite: 2020ApJ...892..148S) (alpha_CO prescription)
- Method: (cite: 2015A&A...582A..86H) (Bar and spiral measurements in S4G)
- Companion: (cite: 2020ApJ...901L...8S) (PHANGS cloud-scale environment dependence)
- Companion: (cite: 2021ApJ...913..113M) (Alternative arm/interarm contrasts in PHANGS)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: PHANGS-HST
- Related: S4G
- Related: SINGS

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 38,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
