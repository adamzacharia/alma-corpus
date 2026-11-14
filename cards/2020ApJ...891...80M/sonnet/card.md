# Properties of M Dwarf Flares at Millimeter Wavelengths

`2020ApJ...891...80M` | The Astrophysical Journal 2020 | first author: MacGregor, A. Meredith | arXiv: 2001.10546 | DOI: 10.3847/1538-4357/ab711d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: stellar_physics, star_formation
- Question: What are the properties and likely emission mechanism of millimeter flares from M dwarfs (AU Mic and Proxima Cen) detected by ALMA?  
  > "We report on two millimeter flares detected by ALMA at 220 GHz from AU Mic, a nearby M dwarf." (abstract)
- Target **AU Mic**: coordinates _not stated_; z/distance 9.725±0.005 pc  
  > "Assuming a distance to the source of $9.725\pm0.005$ pc from *Gaia* (cite: Gaia:2018)" (3 Detection of a Millimeter Flare from AU Mic); distance from Gaia (Gaia Collaboration 2018)  
  > "Assuming a distance to the source of $9.725\pm0.005$ pc from *Gaia* (cite: Gaia:2018)" (3 Detection of a Millimeter Flare from AU Mic)
- Target **Proxima Cen**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00198.S, 2011.0.00142.S, 2016.A.00013.S
- bands: Band 6, 222 GHz (1.35 mm)  
  > "AU Mic was observed with the ALMA 12-m array at 222 GHz (1.35 mm) three times" (2 New ALMA Observations of AU Mic)
- frequencies and spectral setup: Continuum SPWs at 213.5, 216.0, 228.5 GHz (2 GHz each); one SPW on CO J=2-1 (1.875 GHz)  
  > "Three continuum spectral windows were defined at central frequencies of 213.5, 216.0, and 228.5 GHz with a total bandwidth of 2 GHz each." (2 New ALMA Observations of AU Mic)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, 37 antennas  
  > "The SB executed on 2015 June 24, which we consider in this paper, had 37 antennas" (2 New ALMA Observations of AU Mic)
- configurations: _not stated_
- baselines: 30-1320 m for the 2015 June 24 SB  
  > "had 37 antennas with baselines between $30-1320$ m" (2 New ALMA Observations of AU Mic)
- angular resolution: 0.42" x 0.30" (natural weighting)  
  > "natural weight (synthesized beam size of $0.42\ensuremath{''} \times 0.30\ensuremath{''}$)" (3 Detection of a Millimeter Flare from AU Mic)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 33 min on-source (2015 June 24)  
  > "for a total of $33$ min on-source" (2 New ALMA Observations of AU Mic)
- observing dates: 2014 March 26, 2014 August 18, 2015 June 24  
  > "three times on 2014 March 26, 2014 August 18, and 2015 June 24" (2 New ALMA Observations of AU Mic)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538001 GHz)
- External data: Proxima Cen ALMA flare light curve, peak luminosity, spectral index and polarization  
  > "recently detected Proxima Cen millimeter flare with a peak luminosity of $2.04\pm0.15\times10^{14}$ erg s$^{−1}$ Hz$^{-1}$ (cite: macgregor2018)" (3 Detection of a Millimeter Flare from AU Mic) [from (cite: macgregor2018)]
- External data: Quiescent AU Mic flux densities 390, 150, 220 uJy  
  > "obtain values of 390, 150, and 220 $\mu$Jy for the 2014 March 26, 2014 August 18, and 2015 June 24 observations" (3 Detection of a Millimeter Flare from AU Mic) [from (cite: Daley:2019)]
- External data: Flare frequency distribution of inactive early M dwarfs  
  > "We estimate a corresponding flare frequency using the FFD of inactive early M dwarfs from (cite: hawley2014)." (4.2.1) [from (cite: hawley2014)]
- External data: AU Mic coronal density and loop size  
  > "the electron density range is 3$\times$10$^{12}-$2$\times$10$^{13}$ cm$^{-3}$, with a size of 1-2 R$_{\star}$ (cite: katsova1999)" (4.2.3) [from (cite: katsova1999)]

## Processing

### Calibration

- pipeline or manual: Reduced in CASA with scripts provided with the data  
  > "The raw ALMA data were reduced in `CASA` (cite: Petry:2012) using the scripts provided with the data." (2 New ALMA Observations of AU Mic)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux), J1924-2914 (bandpass), J2056-3208 (phase)  
  > "For absolute flux calibration and bandpass calibration, Titan and J1924-2914 were used, respectively." (2 New ALMA Observations of AU Mic)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean (version 4.7.0)  
  > "we used the `clean` task in `CASA` (version 4.7.0)." (2 New ALMA Observations of AU Mic)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Figure [1](#fig:image) (left panel) shows a natural weight" (3 Detection of a Millimeter Flare from AU Mic)
- uv taper: only baselines >100 kλ used to isolate stellar emission  
  > "we only image baselines $>100$ k$\lambda$." (3 Detection of a Millimeter Flare from AU Mic)
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

- Original analysis/description of the AU Mic observations  
  > "The original analysis and description of these observations are presented in (cite: Daley:2019)." (2 New ALMA Observations of AU Mic) [from (cite: Daley:2019)]
- Proxima Cen ALMA data and flare analysis  
  > "Recent observations with the Atacama Large Millimeter/submillimeter Array (ALMA) unexpectedly detected flaring emission from Proxima Cen at millimeter wavelengths (cite: macgregor2018)." (Introduction) [from (cite: macgregor2018)]
- Line-of-sight path length and B_parallel assumptions  
  > "Following the approach of (cite: phillips1996), we take the line of sight path length to be one tenth the loop size and $B_{||}$ to be 10 G." (4.2.3) [from (cite: phillips1996)]

### Not stated but needed to reproduce (our reading)

- Proxima Cen project code and data reduction details
- Clean parameters (image size, cell size, niter, threshold)
- Initial point-source parameters and fit settings for uvmodelfit
- Flare-peak time definition and how Gaussian fits were done for t1/2
- Flare luminosity/spectral index error propagation
- Details of the non-linear least squares polarization fit
- How the delta from spectral index is converted (Dulk formula numerical settings)

## Analysis recipe

1. **Image flare epoch**: Natural-weight clean image of baselines >100 kλ  
  > "In order to isolate the stellar emission from disk emission, we only image baselines $>100$ k$\lambda$." (3 Detection of a Millimeter Flare from AU Mic)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Light curve**: Fit point source models to visibilities in 5 s intervals  
  > "we fit point source models to the millimeter visibilities in 5 sec intervals using the `uvmodelfit` task in `CASA`." (3 Detection of a Millimeter Flare from AU Mic)
   - software: CASA uvmodelfit
   - assumption: Distance 9.725 pc  
  > "Assuming a distance to the source of $9.725\pm0.005$ pc from *Gaia*" (3 Detection of a Millimeter Flare from AU Mic)
   - fitting: _not stated_
   - validation: No variability in gain calibrator flux densities on similar timescales  
  > "We note that no variability is seen in the gain calibrator flux densities (interleaved with the source observations) on similar timescales." (3 Detection of a Millimeter Flare from AU Mic)
3. **Spectral index and linear polarization**: Fit point sources separately to lower and upper sidebands; fit XX and YY separately to get |Q/I|=(XX-YY)/2I  
  > "we fit point source models independently to the millimeter visibilities from the lower (213.5 and 216 GHz spectral windows) and upper (228.5 and 230.5 GHz spectral windows) sidebands." (3 Detection of a Millimeter Flare from AU Mic)
   - software: CASA
   - assumption: Stokes U unconstrained so |Q/I| is a lower limit  
  > "We note that $|Q/I|$ is only a lower limit to the true linear polarization fraction" (3 Detection of a Millimeter Flare from AU Mic)
   - fitting: _not stated_
   - validation: Compared calibrator results with ALMA calibrator catalogue; quiescent parallactic-angle fit gives instrumental polarization ~1%; XX-YY difference image shows 4σ peak at flare  
  > "At face value, these results suggest that the instrumental contribution to any measured polarization is at the $\sim1\%$ level for these observations." (3 Detection of a Millimeter Flare from AU Mic)
4. **Flare event rates**: Number of flares over total on-source time with Gehrels 95% intervals  
  > "We use the expressions of (cite: Gehrels1986) to estimate 95% confidence intervals for the small numbers of events detected and associated error on the event rate." (4.1.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Emission mechanism constraints**: Faraday rotation limits on density and B; gyrosynchrotron/synchrotron formulae of Dulk 1985 for electron index; non-thermal energy contours  
  > "Using the formulae for homogeneous sources (cite: Dulk:1985), the derived particle distribution indices for these M dwarfs are consistent with a hard distribution of electrons" (4.3.1)
   - assumption: Peak frequency 50 GHz for energy contours  
  > "The peak frequency of the emission was assumed to be 50 GHz" (4.3.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: Data reduction, clean imaging, uvmodelfit  
  > "we used the `clean` task in `CASA` (version 4.7.0)." (2 New ALMA Observations of AU Mic)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AU Mic flare peak flux density | 16.8 | 0.3 | mJy | 2 | reach a peak flux density of $16.8\pm0.3$ mJy |
| AU Mic peak luminosity | 1.96e15 | 0.04e15 | erg/s/Hz | 2 | this yields a peak luminosity of $1.96\pm0.04\times10^{15}$ erg s$^{-1}$ Hz$^{-1}$ |
| AU Mic spectral index (A1) | -1.3 | 0.4 (peak fit); 0.05 (Table 1) | dimensionless | 3 | yielding a spectral index of $\alpha = -1.3\pm0.4$ |
| |Q/I| at flare peak | 0.12 | 0.04 | dimensionless | 3 | yields $/Q/I/ = 0.12\pm0.04$ |
| AU Mic flare rate | ~20 | 95% range 3.6-63 | events/day | 4 | yielding an event rate of $\sim20$ events day$^{-1}$ with a 95% confidence level range of $3.6-63$ events day$^{-1}$ |
| Proxima Cen flare rate | 4 | range 1.4-9.4 | events/day | 4 | giving an event rate of 4 events day$^{-1}$ with range $1.4-9.4$ events day$^{-1}$ |
| Electron distribution index delta (A1, gyrosynchrotron) | 2.80 | 0.06 | dimensionless | 5 | $\delta_\text{A1}=2.80\pm0.06$ and $\delta_\text{P4}=3.3\pm0.5$ |
| Quiescent polarization percentage | 0.008 | 0.004 | dimensionless | 3 | The best-fit polarization percentage is $0.008\pm0.004$ |

## Qualitative findings

- Flares are short with symmetric light curves lacking exponential tails, suggesting precipitation-dominated emission  
  > "suggests that trapping is not particularly effective in these millimeter flaring events." (4.2.2)

## Claim tuples

- H: Millimeter flares from M dwarfs are common | E: Event rates from AU Mic and Proxima Cen monitoring time | R: ~20 and 4 events/day | F: Millimeter flares occur commonly but were undetected until now | **supported**
- H: The AU Mic flare is linearly polarized despite no polarization calibration | E: XX/YY fits plus quiescent parallactic-angle analysis | R: |Q/I|=0.12±0.04; quiescent instrument ~1% | F: Polarization detection robust | **partially**
- H: Emission mechanism is synchrotron or gyrosynchrotron | E: Spectral index, Faraday rotation and energetics | R: Negative alpha, linear polarization, low density needed | F: Synchrotron favored from precipitating electrons | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Trapped electrons rejected as it cannot give fast bursts with linear polarization  
  > "the characteristics of the observed events seem to rule out trapping of electrons." (4.3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): No polarization calibration; small sample  
  > "it is difficult to draw firm conclusions from such a small sample." (5 Conclusions)
- Caveat (inferred, ours): Instrumental polarization could mimic the signal at 12% level
- Caveat (inferred, ours): Flare spectral index from two sidebands has large uncertainty
- Caveat (inferred, ours): Event rate based on two flares
- Caveat (inferred, ours): Single-frequency data cannot distinguish mechanisms

## Reproducibility

- Data public (paper): Archival ALMA data cited by project code  
  > "we present analysis of archival ALMA data aimed at imaging the disk" (Introduction)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: uvmodelfit starting parameters
- Missing: Proxima Cen data details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple point-source fits, but few parameters are given.
- Rediscovery candidate: yes, Public data, simple recipe, numeric flare flux and index results.

## Links

- Method: (cite: Vidal:2016) (Polarization recovery from dual-pol ALMA data)
- Companion: (cite: macgregor2018) (Proxima Cen millimeter flare)
- Companion: (cite: Daley:2019) (Original analysis of AU Mic data)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00142.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 37,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
