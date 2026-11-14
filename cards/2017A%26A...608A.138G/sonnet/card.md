# The ALMA Frontier Fields Survey. III. 1.1 mm emission line identifications in Abell 2744, MACSJ 0416.1-2403, MACSJ 1149.5+2223, Abell 370, and Abell S1063

`2017A&A...608A.138G` | Astronomy and Astrophysics 2017 | first author: González-López, J. | arXiv: 1704.03007 | DOI: 10.1051/0004-6361/201730961

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Can serendipitous emission lines be detected in the 1.1 mm continuum-oriented ALMA Frontier Fields mosaics of five lensing clusters, and are they reliable and identifiable with NIR counterparts?  
  > "Our aim is to detect emission lines present in continuum oriented observations." (abstract)
- Target **Abell 2744 (A2744)**: coordinates _not stated_; z/distance z=0.308  
  > "Abell 2744 ($z$$=$0.308); MACSJ0416.1-2403 ($z$$=$0.396); MACSJ1149.5+2223 ($z$$=$0.543); Abell 370 ($z$$=$0.375), Abell S1063 ($z$$=$0.348)" (2.1 Observations); distance from _not stated_
- Target **MACSJ0416.1-2403**: coordinates _not stated_; z/distance z=0.396  
  > "MACSJ0416.1-2403 ($z$$=$0.396)" (Data, Observations); distance from _not stated_
- Target **MACSJ1149.5+2223**: coordinates _not stated_; z/distance z=0.543  
  > "MACSJ1149.5+2223 ($z$$=$0.543)" (Data, Observations); distance from _not stated_
- Target **Abell 370**: coordinates _not stated_; z/distance z=0.375  
  > "Abell 370 ($z$$=$0.375)" (Data, Observations); distance from _not stated_
- Target **Abell S1063**: coordinates _not stated_; z/distance z=0.348  
  > "Abell S1063 ($z$$=$0.348)" (Data, Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00999.S, 2015.1.01425.S
- bands: Band 6 (1.1 mm), LO 263.14 GHz  
  > "The Local Oscillator frequency was set to 263.14 GHz ($\approx$1.1 mm), with two spectral windows (SPWs) placed in each sideband." (2.1 Observations)
- frequencies and spectral setup: 4 SPWs, 1875 MHz each, 0.488 MHz channels, 7.45 GHz total; averaged to 7.813 MHz (~9 km/s)  
  > "The correlator was set to Frequency Division Mode (FDM) with a bandwidth of 1875 MHz and a channel spacing of 0.488 MHz." (2.1 Observations); "resulting in a final spectral resolution of 7.813 MHz ($\sim9{{\rm \thinspace km\thinspace s}^{-1}}$)" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 126 pointings per field, ~4.6 arcmin^2 mosaics  
  > "Each field was covered with 126 pointings to create mosaics spanning an area of $\approx4.6$ square arcminutes" (2.1 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Natural-weighting beams from 0.63''x0.49'' (A2744) to 1.52''x0.85'' (MACSJ0416)  
  > "These cubes have synthesized beam sizes of 0.63$''$$\times$0.49$''$ and position angle of 86.16$^\circ$ for A2744" (2.2 Imaging)
- max recoverable scale: _not stated_
- sensitivity: ~0.8-1.0 (lower sideband) and ~0.9-1.3 (upper sideband) mJy/beam per 15.626 MHz channel  
  > "we obtain sensitivity ranges of $\approx$0.8–1.0 and $\approx$0.9–1.3 mJy beam$^{-1}$ over a 15.626 MHz channel" (2.2 Imaging)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 up to 9-8 (identifications) (not stated)
- Other facility **HST/Spitzer Frontier Fields imaging**: Deep NIR counterparts and photometry for line associations and photometric redshifts  
  > "we expect that an emission line candidate co-spatial to a NIR detected galaxy should increase the probability of this candidate being real and thus use the NIR images for this purpose." (3.3 Association with optical/NIR counterparts)
- Other facility **GLASS**: Grism spectroscopic redshift for MACSJ0416-EL03 counterpart (z=1.849)  
  > "The NIR galaxy has been detected as part of the Grism Lens-Amplified Survey from Space (cite: Treu2015) with a redshift of $z=1.849$." (Discussion)
- External data: H-alpha based SFRs and morphology classification for A370-EL01 and AS1063-EL01 hosts  
  > "(cite: Vulcani2016) presented H$\alpha$ observations for several galaxies of the FFs" (Molecular gas) [from Vulcani2016]
- External data: Lens models for magnifications (FF archive)  
  > "We estimate the magnification values as in (cite: Coe2015), by taking the 16th, 50th and 84th percentiles" (Magnification values) [from Coe2015]
- External data: 1.1 mm continuum source redshifts, e.g. A2744-ID02 z~2.482  
  > "The redshift for A2744-ID02 is reported in (cite: Laporte2017) as $z\approx2.482$ for the brightest red clump." (Redshift and line identification) [from Laporte2017]
- Simulation/model as data: Simulated Gaussian-noise cubes (>100) convolved with the real synthesized beams, used to estimate false detection probability  
  > "together with the $95\%$ confidence region assessed by simulating over 100 data cubes" (3.2 False rate detection through simulations)

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
- weighting robust: natural weighting  
  > "We created data cubes of the observations using natural weighting, which provides the best sensitivity" (2.2 Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cubes at 2, 4, 8, 16x native resolution (15.6-125 MHz); spectral Gaussian convolution sigma 2-48x native  
  > "The $\sigma_{\rm convolution}$ values used for the Gaussian convolution range from 2 to 48 times the native resolution" (3.1 Method)
- final beam: 0.63x0.49'' (A2744), 1.52x0.85'' (MACSJ0416), 1.20x1.08'' (MACSJ1149), 1.25x1.00'' (A370), 0.96x0.79'' (AS1063)  
  > "1.25$''$$\times$1.00$''$ and $-$89.58$^\circ$ for A370" (2.2 Imaging)
- final rms: _not stated_

### Inherited from earlier work

- Configuration, reduction and continuum imaging of cycle 2 data  
  > "In GL17, we presented the configuration, reduction and continuum imaging of the cycle 2 observations." (2.1 Observations) [from (cite: Gonzalez-Lopez2017)]
- Cycle 3 observation details  
  > "Full details of the cycle 3 observations will be presented in (cite: Gonzalez-Lopez2017b)." (2.1 Observations) [from (cite: Gonzalez-Lopez2017b)]
- Magnification estimation method  
  > "We estimate the magnification values as in (cite: Coe2015)" (Magnification values) [from (cite: Coe2015)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (deferred to GL17)
- Spectral line-search code/software not named or released
- Exact S/N rms estimation scheme per channel
- Cell size, image size, and masking for cubes
- MAGPHYS SED fit settings and priors
- Which lens models/versions per cluster in full

## Analysis recipe

1. **Build multi-resolution cubes**: Natural-weighted dirty cubes per SPW binned to 2,4,8,16x native channels  
  > "we generated four data cubes per SPW, each with a different spectral resolution." (3.1 Method)
   - fitting: _not stated_
   - validation: _not stated_
2. **Search for line candidates**: Convolve spectrally with Gaussians, take per-channel rms, select cells S/N>=5  
  > "we take the rms in each spectral channel and select those cells with $S/N\geq5$." (3.1 Method)
   - assumption: Gaussian line profile  
  > "Therefore assuming a Gaussian shape for emission line search is justified." (3.1 Method)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate false detection probability P_S/N**: Run same search on simulated Gaussian-noise cubes (PBC>=0.5 cells, convolved with real beam); P=N(>S/N)/N_total  
  > "We define this probability as $P_{S/N}=N_{>S/N}/N_{total}$" (3.2 False rate detection through simulations)
   - parameter: liberal threshold P_S/N<=0.99 gives 26 candidates  
  > "This cut yields a total of 26 candidates" (3.2 False rate detection through simulations)
   - assumption: Gaussian, spatially and spectrally independent noise  
  > "We assume here that the noise in the ALMA-FFs data can be approximated by a Gaussian distribution" (3.2 False rate detection through simulations)
   - fitting: _not stated_
   - validation: Compared real vs simulated S/N distributions and with negative-image FDR  
  > "A comparison between simulations and negative image FDR probabilities for each cluster is shown in Fig. [4]" (3.2 False rate detection through simulations)
4. **Associate with NIR counterparts**: Corrected-Poisson P_sep=1-exp(n pi sep^2); P=P_S/N x P_sep; reliable if P<=0.05 and P_S/N<=0.99  
  > "We select as reliable emission line candidates those candidates with $P\leq0.05$ and $P_{S/N}\le0.99$." (3.3 Association with optical/NIR counterparts)
   - fitting: _not stated_
   - validation: Second method with random simulated positions gave similar probabilities  
  > "We confirmed that both estimators return similar probabilities" (3.3 Association with optical/NIR counterparts)
5. **Fit line profiles**: Gaussian fit to spectra at candidate centroids assuming point sources  
  > "obtained from fitting a Gaussian function to the spectra extracted at the centroid positions of the line candidates, assuming point sources" (4 Results)
   - fitting: _not stated_
   - validation: Compared with flux integrated from collapsed line map  
  > "We can compare the flux estimated from assuming a point source with that obtained from integrating the collapsed line." (4 Results)
6. **Identify lines and estimate redshift/SFR**: SED fitting of NIR photometry of nearest counterpart; match CO/CI/[NII]/[CII] lines to redshift  
  > "We use the NIR photometry of the nearest counterpart to estimate the SFR by fitting the spectral energy distribution using the high-redshift MAGPHYS code" (Redshift and line identification)
   - software: MAGPHYS, Hyperz
   - assumption: Redshift of nearest counterpart applies to the line  
  > "We make the implicit assumption here that the photometric or spectroscopic redshift of the nearest counterpart applies also to the emission line" (Redshift and line identification)
   - fitting: _not stated_
   - validation: Compare predicted vs observed line flux; velocity shift vs optical redshift  
  > "we further compared the observed line fluxes with those estimated from the observed SFRs and redshifts to weed out inconsistent identifications." (Summary and conclusion)
7. **Magnifications and molecular gas masses**: Percentiles of FF lens-model magnifications; M_H2 from CO luminosity with alpha_CO and CO excitation ratio; t_dep=M_H2/SFR  
  > "We can then estimate the depletion timescales over which the star-formation would use up the available molecular gas, $t_{\rm dep}={\rm M}_{\rm H2}/{\rm SFR}$." (Molecular gas)
   - assumption: alpha_CO=0.8 (DSFG/ULIRG) or 3.6 (low-z/cluster); R71=R81~0.39, R31~0.56  
  > "For CO(3-2), we use a value of $R_{31}\sim0.56$." (Molecular gas)
   - fitting: _not stated_
   - validation: Expected continuum from Scoville2016 compared with observed continuum  
  > "For A2744-EL01, the expected continuum level is $\sim$0.4 mJy; this should have been detected in the $S/N\geq5$ analysis presented in GL17." (Discussion, Molecular gas)

## Software

- **MAGPHYS (high-z)** : SED fitting for photometric redshift and SFR  
  > "fitting the spectral energy distribution using the high-redshift MAGPHYS code" (Redshift and line identification)
- **Hyperz** : alternative photometric redshift  
  > "$z=0.28^{+0.05}_{-0.03}$ using *Hyperz*" (Redshift and line identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of line candidates with P_S/N<=0.99 | 26 | not stated | dimensionless | 3 | This cut yields a total of 26 candidates |
| Reliable candidates (P<=0.05) | 9 | not stated | dimensionless | 4 | Among these, we find nine candidates with $P\leq0.05$ |
| A2744-EL01 CO(8-7) redshift | 2.61975 | 0.0003 | dimensionless | 6 | CO(8-7) at $z=2.61975\pm0.0003$ |
| A370-EL01 CO(3-2) redshift | 0.35962 | 0.00001 | dimensionless | 6 | $z_{\rm CO}=0.35962\pm0.00001$ |
| A2744-EL01 molecular gas mass | 2.4e10 (alpha_CO=0.8, R81=0.39, mu=1.9) | 0.4e10 | Msun | 7 | ${\rm M}_{\rm H2}=(2.4\pm0.4)\times10^{10}\times\left(\frac{\alpha_{\rm CO}}{0.8}\right) |
| Depletion time A370-EL01 | ~0.9 | not stated | Gyr | 7 | we find depletion times of $t_{\rm dep}\sim0.9$ Gyr and $t_{\rm dep}\sim0.07$ Gyr, respectively. |
| Line detection rate (P_S/N<=0.6) | 0.05 | +0.02/-0.02 | GHz^-1 arcmin^-2 | 0 | we obtain a detection rate of $0.05^{+0.02}_{-0.02}$ GHz$^{-1}$ square arcmin$^{-1}$ in the ALMA-FFs |

## Qualitative findings

- AS1063-EL01 host is a jellyfish galaxy with CO offset consistent with ram-pressure stripping direction  
  > "The host galaxy of AS1063-EL01 is classified as a so-called ’jellyfish’ galaxy with signs of ram pressure stripping" (Molecular gas)

## Claim tuples

- H: Serendipitous lines can be found and identified in continuum-oriented mosaics with deep NIR data | E: Line search in five FF cubes, MC false-detection probabilities, NIR association | R: 26 candidates, 9 reliable, 6 with secure/tentative CO identifications | F: Feasible but yields few high-significance lines compared to blind scans | **supported**
- H: Negative-image FDR is unreliable versus Monte Carlo | E: Compared simulation and negative-image probabilities | R: Negative image gives noisier, sharper probabilities | F: Monte Carlo simulations should be used | **supported**
- H: Gas properties of identified counterparts | E: M_H2 and depletion times from CO | R: t_dep ~0.02-0.9 Gyr | F: MACSJ0416-EL03 and AS1063-EL01 starburst-like; others main-sequence-like (alpha_CO dependent) | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Negative-image FDR rejected in favor of Monte Carlo  
  > "We propose that Monte Carlo simulations can yield a more realistic understanding" (3.2 False rate detection through simulations)
- How they decided it was enough: _not stated_
- Limitation (authors): Many candidates are narrow (FWHM<50 km/s) and may be noise; narrow frequency coverage limits secure identifications  
  > "we acknowledge that the narrow emission line candidates selected have a higher probability of being false" (Emission line widths)
- Caveat (inferred, ours): Line identifications depend on assumed counterpart redshift and single lines
- Caveat (inferred, ours): Molecular masses depend strongly on alpha_CO and excitation assumed
- Caveat (inferred, ours): Gaussian-noise assumption tested only on MACSJ0416

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Search code not released
- Missing: Calibrated cubes and CASA settings deferred to GL17
- Missing: Counterpart catalogs and SED setup not given
- Data volume (inferred): Large: five 126-pointing band 6 mosaics, likely hundreds of GB to ~1 TB raw
- Score (inferred): 3/5, Clear search and probability recipe, but search code, cube parameters and calibration are not specified.
- Rediscovery candidate: no, Recipe incomplete (no code, imaging details deferred to other papers) and depends on external catalogs.

## Links

- Method: Gonzalez-Lopez2017 (GL17) (ALMA-FF cycle 2 configuration, reduction and imaging)
- Method: Coe2015 (magnification estimation method)
- Companion: Laporte2017 (ALMA-FF continuum sources and redshifts)
- Companion: Gonzalez-Lopez2017b (cycle 3 observations and low-significance continuum sources)
- Related: Frontier Fields
- Related: ASPECS

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.1425.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 45,
  "rate": 0.474
 },
 "evidence_ok": true
}
```
