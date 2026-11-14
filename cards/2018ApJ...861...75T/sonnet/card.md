# SiO Masers in the Galactic Bulge and Disk: Kinematics from the BAaDE Survey

`2018ApJ...861...75T` | The Astrophysical Journal 2018 | first author: Trapp, A. C. | arXiv: 1805.04522 | DOI: 10.3847/1538-4357/aac382

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, stellar_physics, evolved_stars
- Question: What are the kinematics of SiO maser AGB stars toward the Galactic bulge and plane, and what do they say about disk versus bulge/bar populations and their ages?  
  > "We see a clean division into two kinematic populations: a kinematically cold ($\sigma \sim 50\rm\ km\ sec^{-1}$) population that we propose is in the foreground disk" (abstract)
- Target **BAaDE SiO maser sources toward Galactic bulge/plane (~2700 sources)**: coordinates -15 < l < +12 deg, -6 < b < +6 deg  
  > "Adopting 8.3 kpc to the Galactic Center, and correcting for foreground extinction" (abstract); z/distance 8.3 kpc (bulge, common); 3.4 kpc (cold disk population)  
  > "Adopting 8.3 kpc to the Galactic Center, and correcting for foreground extinction" (abstract); distance from Gillessen et al. 2016 for 8.3 kpc  
  > "Adopting 8.3 kpc to the Galactic Center, and correcting for foreground extinction" (abstract)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: SiO at 43.1 GHz (J=1-0 v=1), 42.8 GHz (v=2), and 86 GHz (J=2-1 v=1), observed with ALMA or VLA  
  > "42.8 GHz with $J = 1 \rightarrow 0 (v = 2)$, and 86 GHz with $J = 2 \rightarrow 1 (v = 1)$." (Data Acquisition)
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
- Line: SiO J=2-1 v=1 (86 GHz)
- Other facility **VLA**: SiO maser detections and velocities for the bulge side at positive longitude  
  > "follow-up with the VLA and ALMA to detect the masers" (Data Acquisition)
- Other facility **2MASS**: J, H, Ks photometry for CMDs  
  > "giving access to $J$, $H$, and $Ks$ magnitudes." (Data Acquisition)
- Other facility **MSX**: Mid-IR colour-based candidate selection and positions  
  > "We initially select a candidate catalog based on mid-infrared photometry from MSX" (Data Acquisition)
- External data: Extinction map used for dereddening  
  > "we correct for interstellar dust using an extinction map from Nidever et al. (2012a)." (Data Acquisition) [from Nidever et al. (2012a)]
- External data: SiO maser Ks-band bolometric corrections from 2MASS-MSX colors  
  > "Messineo (2004) SiO maser $Ks$-band bolometric corrections using 2MASS-MSX colors (pg. 60)" (Analysis of the Kinematic Populations) [from Messineo (2004)]
- External data: BRAVA, GIBS and APOGEE kinematic data for comparison  
  > "We compare our data to three of these major bulge surveys that have made their data public" (Introduction) [from Rich et al. 2007; Kunder et al. 2012; Zoccali et al. 2014; Nidever et al. 2012b]

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

- Sample selection, observing technique, data reduction and velocity derivation deferred to the BAaDE catalog paper  
  > "We give a brief description of our sample selection here; the details are fully described in Sjouwerman et al. (2018) (in prep.)." (Data Acquisition) [from Sjouwerman et al. (2018) (in prep.)]
- Candidate selection from MSX colors  
  > "was selected from the MSX colors (MSX PSC version 2.3, Egan et al. 2003) as described by Sjouwerman et al. (2009)." (Data Acquisition) [from Sjouwerman et al. (2009)]
- Galactocentric velocity frame correction, LSR 220 km/s  
  > "we correct our frame of reference to Galactocentric following Beaulieau et al. (2000)." (Data Acquisition) [from Beaulieu et al. (2000)]

### Not stated but needed to reproduce (our reading)

- ALMA/VLA observing setups, calibration and imaging steps
- ALMA project codes and which sources came from which array
- Velocity extraction procedure from spectra
- Exact Ks cuts and binning for dispersion maps and rotation-curve fits
- Fitting method for rotation slopes and dispersions
- Skewness and Gauss-Hermite h3 fitting details
- Source catalog (not yet published)

## Analysis recipe

1. **Match masers to 2MASS**: Positional match between MSX and 2MASS with a 5 arcsec radius; brighter and redder source chosen when multiple  
  > "using a search radius of 5 arcsec. For sources with more than one match within this radius, the brighter and redder sources were chosen." (Data Acquisition)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert velocities to Galactocentric frame**: Correct LoS velocities following Beaulieu et al. (2000)  
  > "we adopt the circular velocity of the Local Standard of Rest as $220\rm~km~s^{-1}$ (Kerr & Lynden-Bell 1986)" (Data Acquisition)
   - fitting: _not stated_
   - validation: _not stated_
3. **Separate hot/cold kinematic populations**: Velocity dispersion heat-map on 2MASS CMD after subtracting rotation curve; split by Ks magnitude  
  > "These velocity dispersions were derived after subtracting the rotation curve of the sources" (Kinematics Across the Color-magnitude diagram)
   - parameter: Hot: Ks>5.5 (VLA), Ks>6 (ALMA); faint: Ks>~12  
  > "we label the fainter stars ($Ks > 5.5$ for VLA stars; $Ks > 6$ for ALMA stars) as the kinematically “hot" population" (Kinematics Across the Color-magnitude diagram)
   - fitting: _not stated_
   - validation: Compared with BRAVA, GIBS, APOGEE rotation and dispersion  
  > "We assign the BAaDE hot component to the bulge primarily because of the agreement in both rotation and velocity dispersion with BRAVA, GIBS, and the APOGEE hot component." (The Kinematically Hot Population)
4. **Luminosity functions**: Bolometric magnitudes from Ks with Messineo bolometric corrections, dereddening for hot population  
  > "i) a common distance of 8.3 kpc (Gillessen et al. 2016), ii) Messineo (2004) SiO maser $Ks$-band bolometric corrections using 2MASS-MSX colors (pg. 60)" (The Kinematically Hot Population)
   - assumption: 8.3 kpc for hot, 3.4 kpc for cold population  
  > "a common distance of 3.4 kpc (typical distance to a disk star towards the GC)" (The Kinematically Cold Population)
   - fitting: _not stated_
   - validation: _not stated_
5. **Simple disk models to test assignments**: 2-D foreground disk model with flat rotation curve, circular orbits, exponential disk; predict rotation slope  
  > "This model predicts a rotation slope of $\sim7\rm~km~s^{-1}~deg^{-1}$." (The Kinematically Cold Population)
   - parameter: sigma 50 km/s, scale length 3 kpc, inner radius 4 kpc  
  > "a velocity dispersion of $50\rm~km~s^{-1}$, an exponential disk with scale length 3 kpc, and an inner radius of 4 kpc" (The Kinematically Cold Population)
   - fitting: _not stated_
   - validation: Compared to observed cold slope 5.5 km/s/deg  
  > "cold kinematic component (slope = $5.5\rm~km~s^{-1}~deg^{-1}$; see Fig. [6](#SLOPE))" (The Kinematically Cold Population)
6. **LOSVD skewness and substructure**: Fisher-Pearson skewness and Gauss-Hermite h3 as function of position; double-Gaussian look for high-velocity peaks  
  > "Skewness is calculated as the Fisher-Pearson coefficient of skewness" (Line of Sight Velocity Distribution)
   - fitting: _not stated_
   - validation: Skewness and h3 agree positionally  
  > "There is strong positional agreement between the two methods." (Line of Sight Velocity Distribution)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Hot population velocity dispersion | ~100 | not stated | km/s | 3 | a kinematically hot ($\sigma \sim 100\rm\ km\ sec^{-1}$) candidate bulge/bar population |
| Cold population velocity dispersion | ~50 | not stated | km/s | 3 | a kinematically cold ($\sigma \sim 50\rm\ km\ sec^{-1}$) population |
| Peak Mbol of hot population (8.3 kpc) | -5.5 | not stated | mag | 4 | The peak of bolometric luminosity is $M_{bol} \approx -5.5$ |
| Peak Mbol of cold population (3.4 kpc) | -4.5 | not stated | mag | 4 | The peak of bolometric luminosity is $M_{bol} \approx -4.5$ |
| Observed cold rotation slope | 5.5 | not stated | km/s/deg | 3 | cold kinematic component (slope = $5.5\rm~km~s^{-1}~deg^{-1}$; see Fig. [6](#SLOPE)) |
| Model foreground-disk rotation slope | ~7 | within 1.5 | km/s/deg | 5 | This model predicts a rotation slope of $\sim7\rm~km~s^{-1}~deg^{-1}$. |
| Model background-disk rotation slope | ~8 | within 2 | km/s/deg | 5 | This model predicts a rotation slope of $\sim 8 \rm~km~s^{-1}~deg^{-1}$. |

## Qualitative findings

- Hot population shows cylindrical rotation consistent with a bar  
  > "Fig. [10](#CYL) shows that the BAaDE hot kinematic population does exhibit cylindrical rotation, consistent with it being bar-shaped" (The Kinematically Hot Population)
- Skew is positive at positive longitudes and negative at negative longitudes  
  > "our velocity distributions are skewed positive at positive longitudes, and negative at negative longitudes, consistent with triaxial bar" (Line of Sight Velocity Distribution)

## Claim tuples

- H: SiO maser stars divide into disk and bulge kinematic populations | E: Dispersion and rotation vs Ks on the 2MASS CMD, compared with BRAVA, GIBS, APOGEE | R: Cold sigma~50 km/s for bright stars; hot sigma~100 km/s for fainter | F: Cold population is foreground disk, hot is bulge/bar | **supported**
- H: The maser stars are luminous and possibly intermediate-age AGB stars | E: Luminosity functions with bolometric corrections | R: Peak Mbol about -5.5 (hot) | F: Luminous, but in tension with high dispersion | **partially**
- H: There is kinematic substructure at high velocity | E: LOSVD examination in ALMA and VLA fields | R: Candidate peak near -200 km/s at (l,b)=(-8.5,0) | F: Candidate counterpart to Nidever et al. high-velocity group, possibly skew with low number statistics | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Skew in the hot component could come from cold-star contamination, judged unlikely to account for it  
  > "it is unlikely such a contamination could cause a skew as great as that seen in Fig. [15](#SKEW_1)" (Line of Sight Velocity Distribution)
- How they decided it was enough: _not stated_
- Limitation (authors): Population separation is crude; cross-contamination possible  
  > "However, while our separation is robust, it is not perfect, and some cross-contamination of disk and bulge may be present" (The Kinematically Cold Population)
- Limitation (authors): Sample is a non-uniform pilot subset  
  > "could lead to a lack of uniform spatial coverage in the *current* sample" (Data Acquisition)
- Caveat (inferred, ours): Ks magnitude cut as population separator is ad hoc and uncertainty-free
- Caveat (inferred, ours): Single distance per population broadens luminosities by about 1 mag
- Caveat (inferred, ours): No uncertainties on dispersions and slopes
- Caveat (inferred, ours): ALMA processing is entirely deferred to an unpublished paper

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Source catalog and velocities (in prep.)
- Missing: ALMA project codes and reduction
- Missing: Fitting procedures
- Data volume (inferred): Unknown; the ALMA SiO survey observations are likely modest per source, but many sources
- Score (inferred): 2/5, The paper relies on an unpublished catalog and gives no ALMA processing or fit details.
- Rediscovery candidate: no, Recipe and ALMA data details are deferred to an unpublished paper, and results are mostly figure-based.

## Links

- Method: Sjouwerman et al. (2018) (in prep.) (Full BAaDE program, techniques and catalog)
- Method: Sjouwerman et al. (2009) (MSX color-based candidate selection)
- Companion: Sjouwerman et al. 2015, 2017 (Earlier BAaDE descriptions)
- Related: BAaDE
- Related: BRAVA
- Related: GIBS
- Related: APOGEE
- Related: ARGOS

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.01180.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 31,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
