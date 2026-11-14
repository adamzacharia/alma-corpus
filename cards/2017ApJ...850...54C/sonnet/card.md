# ALMA CO(3-2) Observations of Star-forming Filaments in a Gas-poor Dwarf Spheroidal Galaxy

`2017ApJ...850...54C` | The Astrophysical Journal 2017 | first author: Consiglio, S. Michelle | arXiv: 1710.10282 | DOI: 10.3847/1538-4357/aa93dc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How is the dense molecular gas in NGC 5253 distributed and kinematically organised at ~5 pc scale, and what are the properties of the clouds around the supernebula?  
  > "The $^{12}$CO(3–2) Line: How is the Dense Gas in NGC 5253 Distributed?" (3 The 12CO(3-2) Line)
- Target **NGC 5253**: coordinates two fields at 13:39:56.62 -31:38:33.5 and 13:39:55.91 -31:38:26.5 (ICRS)  
  > "the nearby (3.8 Mpc) dwarf galaxy NGC 5253" (6 Summary and Conclusions); "centered on 13:39:56.62 -31.38.33.5 and 13:39:55.91 -31.38.26.5 (ICRS)" (2 Observations); z/distance 3.8 Mpc  
  > "the nearby (3.8 Mpc) dwarf galaxy NGC 5253" (6 Summary and Conclusions); "centered on 13:39:56.62 -31.38.33.5 and 13:39:55.91 -31.38.26.5 (ICRS)" (2 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00105.S
- bands: Band 7  
  > "NGC 5253 was observed in ALMA Band 7 as a Cycle 2 (Early Science) program" (2 Observations)
- frequencies and spectral setup: 244.14 kHz channels, 1 km/s  
  > "Spectral resolution of 244.14 kHz, or 1 km s$^{-1}$ per channel resolves the CO(3–2) lines." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: uv range ~24.5-900 kλ  
  > "The uv range covers $\sim$24.5-900 k$\lambda$" (2 Observations)
- angular resolution: 0.33x0.27 arcsec (12CO), 0.33x0.29 arcsec (13CO)  
  > "The beam size is 0.33$''$ x 0.27$''$ at p.a.=-89.8$^o$ for $^{12}$CO(3–2)" (2 Observations)
- max recoverable scale: 4-8 arcsec  
  > "the largest structures sampled are 4-8$''$" (2 Observations)
- sensitivity: RMS 2.7 mJy/bm (12CO), 3.2 mJy/bm (13CO) per 1 km/s channel  
  > "The RMS in a single 1 km s$^{-1}$ channel is 2.7 mJy/bm for $^{12}$CO(3-2) and 3.2 mJy/bm for $^{13}$CO." (2 Observations)
- time on source: 8383 s on both sources  
  > "were observed simultaneously with 8383 seconds on both sources" (2 Observations)
- observing dates: 2015 June 4 and 5  
  > "on 2015 4 and 5 June" (2 Observations)
- pi or archival as stated: Cycle 2 program, PI J. Turner  
  > "ID = 2012.1.00105.S, PI = J. Turner" (2 Observations)
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Other facility **VLA 6 cm**: 6 cm radio continuum image compared with CO  
  > "a VLA 6 cm image (cite: 1998AJ....116.1212T) is overlaid on the ALMA CO(3–2) map" (5 Dense Gas and Star Formation)
- Other facility **HST/ACS**: archival image and Halpha comparison  
  > "superimposed on an archival HST/ACS image of the galaxy" (3.1)
- Other facility **SMA**: previous CO(3-2) map used for flux comparison  
  > "The integrated flux density recovered in the lower resolution SMA synthesis map of (cite: 2015Natur.519..331T) was 110 $\pm 20$ Jy $\rm km~s^{-1}$." (2 Observations)
- Other facility **OVRO**: CO(2-1) images for gas masses  
  > "images of CO(2–1) from the Owens Valley Millimeter (OVRO) Array (cite: 2002AJ....124..877M) for gas masses" (5 Dense Gas and Star Formation)
- External data: CO(3-2)/CO(1-0) ratio R31=7 from II Zw 40  
  > "the line ratio, R$_{31}$=$\frac{I_{CO32}}{I_{CO10}}$=7, observed in II Zw 40 (cite: 2016ApJ...833L...6C)" (4.3) [from (cite: 2016ApJ...833L...6C)]
- External data: Single-dish CO(3-2) flux 3.4 K km/s in 22 arcsec CSO beam  
  > "The single dish integrated flux density reported by (cite: 2001AJ....121..740M) with the 22$''$ CSO beam was 3.4 K km/s" (2 Observations) [from (cite: 2001AJ....121..740M)]
- External data: Streamer gas mass ~1.7e6 Msun from CO(2-1)  
  > "The estimated gas mass of the streamer based on CO(2-1) is $\sim 1.7\times 10^6$ M$_\odot$ (cite: 2002AJ....124..877M)." (5) [from (cite: 2002AJ....124..877M)]
- External data: Cloud D temperature 300 K from RADEX CO(3-2)/(2-1) models  
  > "For Cloud D1 we adopt a temperature of 300 K, based on RADEX models of the CO(3–2)/CO(2–1) line ratio (cite: 2015Natur.519..331T)" (6) [from (cite: 2015Natur.519..331T)]
- External data: Median depletion time 0.8 Gyr for local low-metallicity galaxies  
  > "less than the median value of 0.8 Gyr for local low metallicity galaxies as determined by (cite: 2011AJ....142...37S)" (5) [from (cite: 2011AJ....142...37S)]

## Processing

### Calibration

- pipeline or manual: Calibration with JAO code in CASA  
  > "Data calibration was performed using the code produced by the Joint ALMA Observatories with CASA (Common Astronomy Software Applications)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass J1427-42064, phase J1342-2900)  
  > "Bandpass, flux, and phase were calibrated with J1427-42064, Titan, and J1342-2900, respectively." (2 Observations)
- flux scale uncertainty: better than 10%  
  > "Absolute flux density calibration is estimated to be better than 10% in Band 7 Cycle 2" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: MOM0 sums channels >±1σ; MOM1 cutoff ±5σ  
  > "Integrated intensity images (MOM0) were created by summing emission in all channels that was greater than $\pm 1\sigma$" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: subtracted in uv plane  
  > "Continuum emission was subtracted in the (u,v) plane before creating line maps." (2 Observations)
- line free channels: _not stated_
- primary beam correction: flux measured on primary-beam-corrected MOM0 maps  
  > "All measurements are made from velocity-selected, primary beam corrected MOM0 integrated flux density maps." (Table 1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.33x0.27 arcsec PA -89.8 (12CO)  
  > "The beam size is 0.33$''$ x 0.27$''$ at p.a.=-89.8$^o$ for $^{12}$CO(3–2)" (2 Observations)
- final rms: 2.7 mJy/bm (12CO), 3.2 (13CO) per channel  
  > "The RMS in a single 1 km s$^{-1}$ channel is 2.7 mJy/bm for $^{12}$CO(3-2) and 3.2 mJy/bm for $^{13}$CO." (2 Observations)

### Inherited from earlier work

- Individual clump properties from cprops to be published elsewhere  
  > "Their individual characteristics will be published elsewhere (cite: ConsiglioXXX2017)." (4.3) [from (cite: ConsiglioXXX2017)]
- Flux calibration accuracy from ALMA Technical Handbook  
  > "Absolute flux density calibration is estimated to be better than 10% in Band 7 Cycle 2 (cite: Lundgren_2013)." (2 Observations) [from (cite: Lundgren_2013)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- tclean/imaging parameters: weighting, robust, cell, image size, deconvolver, masks
- line-free channels for continuum subtraction
- rest frequencies and velocity ranges per cloud
- cprops parameters
- how the sigma for moment cutoffs was defined and whether MOM1 used the same masks
- aperture definitions for cloud fluxes
- flux calibrator model and Titan details
- Starburst99 and radio flux inputs for depletion times

## Analysis recipe

1. **make line maps and moments**: Continuum subtracted in uv plane; MOM0 and MOM1 from channel maps  
  > "Continuum emission was subtracted in the (u,v) plane before creating line maps." (2 Observations)
   - software: CASA
   - parameter: MOM0 cut ±1σ, MOM1 cut ±5σ  
  > "for the intensity-weighted mean velocity map (MOM1); the cutoff was $\pm 5\sigma$." (2 Observations)
   - fitting: _not stated_
   - validation: Recovered flux compared with CSO and SMA  
  > "We detect $\approx$50% of the expected integrated flux density the SMA maps in the form of individual clumps" (2 Observations)
2. **identify clumps and measure cloud fluxes**: cprops clump finding; cloud fluxes summed over 12CO-defined velocity ranges in primary-beam-corrected MOM0  
  > "Clumps have been individually identified using cprops,a clump finding code designed to identify clumps using velocity and spatial information" (4.3)
   - software: cprops
   - fitting: _not stated_
   - validation: 13CO uncertainty from channel rms times sqrt(Nchan Nbeam)  
  > "computed from the individual channel rms times $\sqrt{N_{chan}N_{beam}}$" (Table 1)
3. **derive masses from 12CO assuming a conversion factor**: Convert CO(3-2) to CO(1-0) with R31=7, apply XCO  
  > "For a conversion factor of X$_{CO} = 4.7 \times 10^{20}$ cm$^{-2}$ (K km$^{-1}$)$^{-1}$" (4.3)
   - parameter: R31=7, XCO=4.7e20  
  > "using a conversion factor of $\alpha_{CO}$=4.7$\times$10$^{20}$ cm$^{-2}$ (K kms$^{-1}$)$^{-1}$, and an estimated CO(3–2)/CO(1–0) ratio of 7" (Table 1)
   - assumption: optically thick emission; masses include He  
  > "Mass derived assuming optically thick emission" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
4. **derive optically thin masses from 13CO**: Optically thin 13CO mass at 20 K (300 K for D1) with Galactic [CO]/[H2] and isotopic ratio 40  
  > "Mass derived assuming optically thin $^{13}$CO flux density and 20 K, a Galactic value of \[CO\]/\[H$_2$\]=$8.5\times 10^{-5}$ and an isotopic ratio of 40" (Table 1)
   - assumption: Rayleigh-Jeans approximation not used  
  > "The Rayleigh-Jeans approximation is not used." (Table 1)
   - fitting: _not stated_
   - validation: Compared with 12CO masses; differ by order of magnitude  
  > "differ by an order of magnitude" (6)
5. **estimate gas depletion times**: Radio 6 cm free-free to Nlyc via Starburst99 relation, SFR over 5 Myr, divide gas mass by SFR  
  > "the estimated mass depletion timescale is $\tau_{dep}$=M$_{gas}$/SFR$\approx$0.3 Gyr for the Streamer" (5)
   - software: Starburst99
   - parameter: 5 Myr star formation timescale  
  > "For a mean star formation timescale of 5 Myr for the star formation" (5)
   - assumption: Kroupa IMF  
  > "Using Starburst99 models and a full Kroupa IMF" (5)
   - fitting: _not stated_
   - validation: uncertain to factors of 3-5  
  > "We estimate that this number is uncertain to factors of 3–5" (5)

## Software

- **CASA** : calibration and imaging  
  > "Data calibration was performed using the code produced by the Joint ALMA Observatories with CASA" (2 Observations)
- **cprops** : clump identification  
  > "Clumps have been individually identified using cprops" (4.3)
- **RADEX** : models of CO line ratio for D1 temperature (from earlier work)  
  > "based on RADEX models of the CO(3–2)/CO(2–1) line ratio" (6)
- **Starburst99** : mass to Lyman continuum relation  
  > "Using Starburst99 models and a full Kroupa IMF" (5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Beam 12CO(3-2) | 0.33 x 0.27 at PA -89.8 | not stated | arcsec, deg | 1 | The beam size is 0.33$''$ x 0.27$''$ at p.a.=-89.8$^o$ for $^{12}$CO(3–2) |
| Systemic velocity adopted | 380 | ±5 | km/s | 1 | We adopt 380 km s$^{-1}$  as the central velocity |
| 12CO/13CO ratio Cloud D1 | 40 | +30/-20 | dimensionless | 2 | / D1 / 55.965 / 24.36 / 385 / 2.4 / 0.06$\pm$0.05 / 40$^{+30}_{-20}$ / 100 / 3.0 / |
| 12CO(3-2) overall sum | 51 | 10% | Jy km/s | 2 | / Overall Sum / 56.3 / 30 / 380 / 51 / 5.5 / 9 / 2073 / 53.6 / |
| Clump masses from 12CO | 3.3-35e4 | not stated | Msun | 3 | the CO(3–2) integrated line intensities correspond to clump masses of 3.3-35$\times$10$^{4}$ $\rm M_\odot$ |
| Optically thin 13CO cloud masses | 0.6-11e3 | not stated | Msun | 4 | we obtain cloud masses M$_{Cl}\sim$0.6-11$\times 10^{3} M_\odot$ (Table 1) |
| Streamer depletion time | 0.3 | factor 3-5 | Gyr | 5 | $\tau_{dep}$=M$_{gas}$/SFR$\approx$0.3 Gyr for the Streamer |
| Cloud D depletion time | 8 | not stated | Myr | 5 | the gas depletion timescale is $\tau_{SF}\sim$8 Myr |
| Fraction of SMA flux recovered | ~50 | not stated | percent | 1 | We detect $\approx$50% of the expected integrated flux density the SMA maps |

## Qualitative findings

- CO(3-2) clumps form kinematically distinct filaments; Streamer and Southern filament appear infalling  
  > "Some of the filaments appear to be falling into the galaxy and may be fueling its current star formation." (abstract)
- CO clumps anti-correlated with Halpha but correlated with radio free-free  
  > "are anti-correlated with H$\alpha$ on $\sim$5 pc scales, but are well-correlated with radio free-free emission" (abstract)

## Claim tuples

- H: Is the dense gas organised in kinematically distinct filaments, and are they infalling? | E: MOM0 and MOM1 of 12CO(3-2) at 0.3 arcsec | R: Streamer ~20-40 km/s red, Cloud F 20-30 km/s blue, Southern filament ~50 km/s red of v_sys 380 | F: Filaments are distinct; Streamer and Southern filament likely infalling, Cloud F infalling on far side | **supported**
- H: Is Cloud D1 optically thin in CO(3-2)? | E: 12CO/13CO flux ratios per cloud | R: D1 ratio ~40, D2 ~12, others ~6-8 | F: D1 and D2 may be optically thin, possibly because hot | **partially**
- H: Is star formation in Cloud D1 unusually efficient? | E: Compare gas mass with SFR from radio continuum | R: tau_dep ~8 Myr, ~100 times shorter than typical low-metallicity galaxy | F: Star formation in D1 is extraordinarily efficient | **supported**

## Reasoning

- Why this data: Higher resolution to resolve cluster-scale dense gas than SMA  
  > "the $\sim$4$''$ $\times$2$''$ beam of the SMA images does not separate the dense gas at the cluster scale." (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short spacings; about half of expected flux recovered  
  > "much has been resolved out because of the lack of short spacings in the array" (2 Observations)
- Limitation (authors): Unknown R31 in NGC 5253 is a systematic uncertainty in gas masses  
  > "the unknown value of R$_{31}$ in NGC 5253 is a source of systematic uncertainty in the gas masses" (4.3)
- Caveat (inferred, ours): Mass estimates differ by an order of magnitude between methods
- Caveat (inferred, ours): XCO and abundance ratios taken from Galactic or other-galaxy values
- Caveat (inferred, ours): D1 13CO detection is marginal
- Caveat (inferred, ours): Table coordinates contain apparent typos (Southern Filament Dec 367)

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgments; public status not explicit  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2012.1.00105.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: CASA version
- Missing: cloud aperture and velocity definitions
- Missing: cprops settings
- Data volume (inferred): ~50-100 GB raw for two Band 7 pointings
- Score (inferred): 3/5, Data archival and results numeric, but imaging and extraction details are sparse.
- Rediscovery candidate: no, Imaging and aperture recipes are insufficiently specified to redo the cloud measurements unambiguously.

## Links

- Method: (cite: 2006PASP..118..590R) (cprops clump finding)
- Companion: (cite: 2015Natur.519..331T) (Earlier SMA CO(3-2) study of the supernebula)
- Companion: (cite: 2017XXXT) (Companion study of Cloud D kinematics and stellar mass)

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 56,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
