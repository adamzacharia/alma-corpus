# Jet Motion, Internal Working Surfaces, and Nested Shells in the Protostellar System HH 212

`2015ApJ...805..186L` | The Astrophysical Journal 2015 | first author: Lee, Chin-Fei | arXiv: 1503.07362 | DOI: 10.1088/0004-637X/805/2/186

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What are the jet motion, shock structures (knots, internal working surfaces), nested CO shells and wiggle of the HH 212 protostellar jet, and is a wide-angle wind needed?  
  > "We study the shock structures in the jet, the morphological relationship between the CO outflow and the jet, and discuss if there is a need of a wide-angle tenuous wind around the jet." (Introduction)
- Target **HH 212 (IRAS 05413-0104)**: coordinates RA(J2000)=05h43m51.4107s, Dec=-01d02m53.167s (continuum peak)  
  > "The central source is assumed to be at the peak position of the continuum, which is $\alpha_{(2000)}=05^\mathrm{h} 43^\mathrm{m} 51^\mathrm{s}_{^\textrm{.}} 4107$" (Observations); "HH 212 system is nearby in the L1630 cloud of Orion at a distance of $\sim$ 400 pc." (Introduction); z/distance ~400 pc  
  > "The central source is assumed to be at the peak position of the continuum, which is $\alpha_{(2000)}=05^\mathrm{h} 43^\mathrm{m} 51^\mathrm{s}_{^\textrm{.}} 4107$" (Observations); "HH 212 system is nearby in the L1630 cloud of Orion at a distance of $\sim$ 400 pc." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00647.S
- bands: _not stated_
- frequencies and spectral setup: CO J=3-2 and SiO J=8-7 observed at ~0.21 km/s per channel; 9-pointing mosaic  
  > "Both CO J=3-2 and SiO J=8-7 lines were observed at a velocity resolution of $\sim$ 0.21 km s$^{-1}$ per channel." (Observations); "A 9-pointing mosaic was used to observe the jet in this system within $\sim$ $40''$ from the central source." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: SiO 0.53x0.47 arcsec PA~20 deg; CO 0.56x0.47 arcsec PA 43 deg (super-uniform weighting)  
  > "With super-uniform weighting, the synthesized beam has a size of $0^{\prime\prime}_{^\textrm{.}}53$$\times$$0^{\prime\prime}_{^\textrm{.}}47$ at a position angle (P.A.) of $\sim$ 20$^\circ$ in SiO" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~7.7 mJy/beam (0.32 K) SiO; ~7.2 mJy/beam (0.28 K) CO  
  > "The rms noise level is $\sim$ 7.7 mJy beam$^{-1}$ (i.e., 0.32 K) for the SiO channel maps" (Observations)
- time on source: _not stated_
- observing dates: 2012 December 1, Cycle 0  
  > "Observations of the HH 212 protostellar system were carried out with ALMA on 2012 December 1 during the Early Science Cycle 0 phase." (Observations)
- pi or archival as stated: _not stated_
- Line: SiO J=8-7 (not stated)
- Line: CO J=3-2 (not stated)
- Other facility **SMA**: Earlier SiO map (~6 years earlier) used for proper motion  
  > "by measuring the position shifts of their SiO emission peaks with respect to those seen at $\sim$ 6 years earlier in our previous SMA map in (cite: Lee2008)." (Proper Motion)
- Other facility **H2 imaging (VLT)**: Earlier H2 jet map for comparison  
  > "It was made by combining the 3 observations in October 2000, October 2001, and January 2002 (cite: McCaughrean2002)" (Results)
- External data: H2 map of the jet from 2000-2002  
  > "It was made by combining the 3 observations in October 2000, October 2001, and January 2002 (cite: McCaughrean2002)" (Results) [from McCaughrean et al. 2002 (cite: McCaughrean2002)]
- External data: Previous SMA SiO map  
  > "We first convolved our previous SMA SiO map to the resolution of our ALMA map" (Proper Motion) [from (cite: Lee2008)]
- External data: Accretion rate ~5e-6 Msun/yr  
  > "Since the accretion rate has been estimated to be $\sim
5\times10^{-6}$ $M_\odot$ yr$^{-1}$ (cite: Lee2014)" (Jet Density and Mass-Loss Rate) [from (cite: Lee2014)]

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
- weighting robust: super-uniform weighting  
  > "With super-uniform weighting, the synthesized beam has a size of" (Observations)
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

- Observation details reported elsewhere  
  > "The details of these observations have been reported in (cite: Lee2014), and thus only important information is reported here." (Observations) [from (cite: Lee2014)]
- Systemic velocity 1.7+-0.1 km/s LSR  
  > "$V_\textrm{\scriptsize sys}= 1.7\pm0.1$ km s$^{-1}$ LSR, as in (cite: Lee2007)" (Observations) [from (cite: Lee2007)]
- CO excitation temperature ~50 K  
  > "As discussed in (cite: Lee2007), the mean excitation temperature of the CO emission can be assumed to be $\sim$ 50 K." (Jet Density and Mass-Loss Rate) [from (cite: Lee2007)]
- Density conversion from CO column density via Eq. 17  
  > "using the conversion equation, e.g., Eq. 17 in (cite: Lee2014)" (Jet Density and Mass-Loss Rate) [from (cite: Lee2014)]

### Not stated but needed to reproduce (our reading)

- Calibration details, CASA version and calibrators (deferred to Lee et al. 2014)
- Cleaning parameters, masking, continuum subtraction
- Method for measuring knot peak positions and map alignment
- Fitting method for the wiggle model
- Velocity-integration choices beyond those listed

## Analysis recipe

1. **Map nested CO shells and jet**: Channel maps and velocity-integrated CO and SiO maps compared with H2 map  
  > "For the SiO map, we use the velocity from $-$23.03 to 17.53 km s$^{-1}$, instead of $-$21.1 to 16 km s$^{-1}$." (Molecular Jet in SiO and CO)
   - parameter: HV CO: -21.65 to -8.95 and 9.56 to 18.77 km/s  
  > "On the redshifted side, we use 9.56 to 18.77 km s$^{-1}$, instead of 3.4 to 13.3 km s$^{-1}$." (Molecular Jet in SiO and CO)
   - fitting: _not stated_
   - validation: _not stated_
2. **Proper motion of knots**: Compare SiO peak positions with convolved SMA map, aligned on continuum peaks  
  > "We first convolved our previous SMA SiO map to the resolution of our ALMA map and then aligned the two maps with the continuum peaks." (Proper Motion)
   - assumption: jet in plane of sky so velocity ~ tangential velocity  
  > "Since the jet is almost in the plane of the sky, the jet velocity can be approximated to this tangential velocity." (Proper Motion)
   - fitting: _not stated_
   - validation: _not stated_
3. **Jet density and mass-loss rate**: Optically thin LTE CO column density, converted to H2 density, then mass-loss rate  
  > "Assuming LTE, the column density of CO is estimated to be $\sim 2.3 \times 10^{16}$ cm$^{-2}$." (Jet Density and Mass-Loss Rate)
   - parameter: mean CO intensity ~1.2 Jy/beam km/s between NK1 and NK5  
  > "The mean CO intensity there is found to be $\sim$ 1.2 Jy beam$^{-1}$ km s$^{-1}$." (Jet Density and Mass-Loss Rate)
   - assumption: Tex~50 K, CO abundance 8.5e-5, jet diameter ~0.2 arcsec  
  > "With a CO abundance of $8.5 \times 10^{-5}$ and a jet diameter of $\sim$ $0^{\prime\prime}_{^\textrm{.}}2$" (Jet Density and Mass-Loss Rate)
   - fitting: _not stated_
   - validation: Compared with HCO+ derived density  
  > "similar to the mean value derived from HCO$^+$ in (cite: Lee2014)" (Jet Density and Mass-Loss Rate)
4. **Model the jet wiggle**: Sinusoidal model with linear amplitude growth then constant beyond z0, fit to northern jet and applied point-symmetrically to south  
  > "the amplitude of the wiggle is assumed to first increase linearly with the distance and then remain constant at $z\geq z_0$" (Jet Wiggle)
   - parameter: theta0~0.5 deg, lambda~5.6 arcsec, phi0~0 deg, z0~10 arcsec  
  > "the best parameters are $\theta_0 \sim$ 0.5$^\circ$$\pm$0.2$^\circ$" (Jet Wiggle)
   - assumption: point-symmetric wiggle about source  
  > "we first model the wiggle in the northern jet and then apply the model to the southern jet assuming a point-symmetric wiggle about the central source." (Jet Wiggle)
   - fitting: _not stated_
   - validation: Visual comparison with combined CO, SiO and H2 maps  
  > "the model with $z_0 \sim$ $10''$ (4000 AU) can give a better match up to $\sim$ $34''$" (Jet Wiggle)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean knot position shift | 0.36 | 0.15 | arcsec | 2 | the mean position shift is estimated to be $\sim$ $0^{\prime\prime}_{^\textrm{.}}36$$\pm$$0^{\prime\prime}_{^\textrm{.}}15$ |
| Jet tangential velocity | 115 | 50 | km/s | 2 | giving rise to a tangential velocity of $\sim$ 115$\pm50$ km s$^{-1}$ |
| CO column density | 2.3e16 | not stated | cm^-2 | 3 | the column density of CO is estimated to be $\sim 2.3 \times 10^{16}$ cm$^{-2}$ |
| Mean jet H2 density | 5.6e5 | not stated | cm^-3 | 3 | the mean jet density is estimated to be $\sim 5.6 \times 10^5$ cm$^{-3}$ |
| Two-sided mass-loss rate | 1.1e-6 | not stated | Msun/yr | 3 | $\dot{M}_j\sim 1.1\times10^{-6}$ $M_\odot$ yr$^{-1}$ |
| Wiggle wavelength | 5.6 | 1.0 | arcsec | 4 | $\lambda
\sim$ $5^{\prime\prime}_{^\textrm{.}}6$$\pm$$1^{\prime\prime}_{^\textrm{.}}0$ (or 2240$\pm$400 AU) |
| Wiggle period | 93 | not stated | yr | 4 | Since the jet velocity is $\sim$ 115 km s$^{-1}$, the period of the wiggle is $\sim$ 93 years. |
| Wiggle half-opening angle | 0.5 | 0.2 | deg | 4 | $\theta_0 \sim$ 0.5$^\circ$$\pm$0.2$^\circ$ |

## Qualitative findings

- Jet is more continuous than in SMA data; some knots have small bow shocks curving back to the axis, as in pulsed-jet simulations  
  > "Some of the knots are now seen associated with small bow shocks, with their bow wings curving back to the jet axis, as seen in pulsed jet simulations." (abstract)

## Claim tuples

- H: Do knots SK4 and SK5 trace internal working surfaces with sideways ejection? | E: SiO and CO peak offsets and PV diagrams along the jet axis | R: Arclike PV structures; CO peak upstream of SiO | F: Knots likely trace IWSs from jet velocity variation | **supported**
- H: Is a significant wide-angle wind present? | E: Morphology of bow shocks and internal shells | R: Highly curved bow shocks and narrow shells | F: Wide-angle wind, if present, is insignificant | **supported**
- H: What is the origin of the jet wiggle? | E: Wiggle modelling with amplitude growth then saturation | R: Amplitude rises then stays constant (~0.1 arcsec) | F: Precession has difficulty; kink instability is a possible origin | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Jet precession from a binary companion rejected because it predicts amplitude growing with distance  
  > "However, if this is the case, the amplitude of the wiggle is expected to grow with the distance (cite: Raga2009), inconsistent with our observations." (Jet Wiggle)
- How they decided it was enough: _not stated_
- Limitation (authors): Southern jet not continuous beyond ~10 arcsec, so point symmetry unconfirmed  
  > "further observations are still needed to confirm that the wiggle of the jet is really point symmetric about the central source." (Jet Wiggle)
- Caveat (inferred, ours): Proper motion has ~43% uncertainty from few knots and different instruments/resolutions
- Caveat (inferred, ours): Wiggle fit uncertainties and method unspecified
- Caveat (inferred, ours): Temperature, abundance, and jet diameter assumptions drive mass-loss rate

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging details (in Lee et al. 2014)
- Missing: Fitting procedure for wiggle
- Missing: Previous SMA map for proper motion
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data are Cycle 0 and the project code is given, but processing is deferred to another paper and the fitting is not described.
- Rediscovery candidate: no, Processing details are missing and the proper motion needs non-ALMA SMA data.

## Links

- Method: Lee et al. 2014 (cite: Lee2014) (Describes the observations and the density conversion)
- Companion: Lee et al. 2007, 2008 (cite: Lee2007; Lee2008) (Previous SMA studies of the HH 212 jet)
- Related: 2011.0.00122.S (PI C.-F. Lee, duplicate proposal)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00122.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 32,
  "rate": 0.438
 },
 "evidence_ok": true
}
```
