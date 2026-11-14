# The Co-evolution of Disks and Stars in Embedded Stages: The Case of the Very-low-mass Protostar IRAS 15398-3359

`2018ApJ...864L..25O` | The Astrophysical Journal Letters 2018 | first author: Okoda, Yuki | arXiv: 1809.00500 | DOI: 10.3847/2041-8213/aad8ba

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, protoplanetary_disks
- Question: Is there a rotationally-supported disk around the very low-mass Class 0 protostar IRAS 15398-3359, and what is the protostellar mass from its kinematics?  
  > "Thus, we need to confirm the existence of the disk component around the protostar suggested by (cite: Oya et al.(2014)) and use it to measure the protostellar mass." (Introduction)
- Target **IRAS 15398-3359**: coordinates field center (15h43m02.242s, -34d09m06.70s) J2000  
  > "IRAS 15398$-$3359 is a low-mass protostar in the Lupus 1 molecular cloud at a distance of 155 pc (cite: Lombardi et al.(2008))." (Introduction); z/distance 155 pc  
  > "IRAS 15398$-$3359 is a low-mass protostar in the Lupus 1 molecular cloud at a distance of 155 pc (cite: Lombardi et al.(2008))." (Introduction); distance from Lombardi et al. (2008)  
  > "IRAS 15398$-$3359 is a low-mass protostar in the Lupus 1 molecular cloud at a distance of 155 pc (cite: Lombardi et al.(2008))." (Introduction)

## Data provenance

- ALMA projects: 2013.1.01157.S
- bands: Band 6, 261-263 GHz  
  > "Spectral lines of CCH and SO were observed with the Band 6 receiver at frequency range from 261 to 263 GHz." (Observation)
- frequencies and spectral setup: 61 kHz resolution, 59 MHz bandwidth, 0.07 km/s velocity resolution  
  > "The backend correlator was set to a resolution of 61 kHz and a bandwidth of 59 MHz." (Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14.90 to 1559.16 m, 41 antennas  
  > "Forty-one antennas were used in the observations, where the baseline length ranged from 14.90 to 1559.16 m." (Observation)
- angular resolution: about 0.2 arcsec (~30 au)  
  > "we conducted the ALMA observations at a higher angular resolution of 0.2$''$ ($\sim$ 30 au)" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.12 mJy/beam continuum; 4 mJy/beam CCH and SO per 61 kHz channel  
  > "The rms noise levels for the continuum, the CCH emission, and the SO emission are 0.12 mJy bea$\rm m^{-1}$, 4 mJy bea$\rm m^{-1}$, and 4 mJy bea$\rm m^{-1}$, respectively" (Observation)
- time on source: 21.61 minutes  
  > "The total on-source time was 21.61 minutes." (Observation)
- observing dates: 2015 July 20 (Cycle 2)  
  > "Observations of IRAS 15398$-$3359 were carried out with ALMA in its Cycle 2 operation on 2015 July 20." (Observation)
- pi or archival as stated: _not stated_
- Line: CCH N=3-2, J=7/2-5/2, F=4-3 (262.0042600 GHz)
- Line: CCH N=3-2, J=7/2-5/2, F=3-2 (262.0064820 GHz)
- Line: SO 6_7-5_6 (261.8437210 GHz)
- External data: Dust mass absorption coefficient 6.8e-4 cm2/g at 1.2 mm  
  > "we **employ** the mass absorption coefficient of 6.8 $\times$ 10$^{-4}$ cm$^{2}$ g$^{-1}$ at 1.2 mm (cite: Ward-thompson et al.(2000))" (3.2.1 Keplerian Motion) [from Ward-Thompson et al. (2000)]
- External data: Luminosity 1.8 Lsun used for accretion rate  
  > "by using $L$ of 1.8 $L_\odot$ (cite: Jorgensen et al.(2013))" (3.3) [from Jorgensen et al. (2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan sets flux scale; bandpass calibrator J1517-2422  
  > "where the absolute flux density scale was derived from Titan." (Observation)
- flux scale uncertainty: 10%  
  > "the absolute calibration accuracy is 10 %" (Observation)
- self calibration: not applied  
  > "Self-calibration was not applied in this study, since the continuum emission is not bright enough." (Observation)

### Imaging

- task: _not stated_
- deconvolver: CLEAN  
  > "Images were prepared by using the CLEAN algorithm" (Observation)
- weighting robust: Briggs, robust = 0.5  
  > "Briggs’ weighting with a robustness parameter of 0.5 was employed" (Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted directly from visibilities  
  > "the line images were obtained after subtracting the continuum component directly from the visibilities" (Observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.21x0.15 (PA 58); CCH 0.36x0.29 (PA 60); SO 0.22x0.16 (PA 55) arcsec  
  > "0.21$''$$\times$0.15$''$ (P.A. 58$^\circ$) for the continuum image" (Observation)
- final rms: _not stated_

### Inherited from earlier work

- Infalling-rotating envelope model used for CCH PV comparison  
  > "the infalling-rotating envelope model (cite: Oya et al.(2014))" (3.2.2 Infalling-rotating Envelope) [from Oya et al. (2014)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline/manual calibration details
- Line-free channels for continuum
- Image size and cell size, CLEAN threshold and masks
- Fitting method for Keplerian PV model and mass uncertainty (chi2, grid)
- Inclination and systemic velocity treatment in the Toomre Q calculation, disk radius/gas-to-dust ratio
- Model details for infalling-rotating envelope

## Analysis recipe

1. **Measure continuum position and peak**: 2D Gaussian fit to continuum image  
  > "The coordinates of the peak position and its intensity are derived from a 2D Gaussian fit to the image" (3.1 Distribution)
   - fitting: _not stated_
   - validation: Compared with previous 0.8 and 0.6 mm fluxes assuming optically thin dust, beta~2  
  > "assuming optically thin emission from dust with the opacity law $\kappa \propto \nu^{\beta}$ with $\beta \simeq$ 2" (3.1 Distribution)
2. **Protostellar mass from SO Keplerian PV**: Compare PV diagram along P.A. 130 deg with Keplerian rotation model  
  > "the blue contours represent the model of Keplerian rotation with a protostellar mass of 0.007 $M_\odot$." (3.2.1 Keplerian Motion)
   - parameter: systemic velocity 5.5 km/s  
  > "we employ a systemic velocity of 5.5 km s$^{-1}$" (3.2.1 Keplerian Motion)
   - assumption: Keplerian rotation, no radiative transfer or self-absorption  
  > "the effects of radiative transfer and self-absorption are not included in the model" (3.2.1 Keplerian Motion)
   - fitting: _not stated_
   - validation: Infalling-rotating envelope model with centrifugal barrier 1 au fails to reproduce observed velocity sign  
  > "the PV diagram cannot be explained by the infalling-rotating envelope, even if the radius of the centrifugal barrier is set to 1 au" (3.2.1 Keplerian Motion)
3. **Dust mass and Toomre Q**: Dust mass from 1.2 mm continuum at T=20 and 100 K; Toomre Q assuming Keplerian motion  
  > "the dust mass evaluated from the 1.2 mm continuum data is between 0.006 and 0.001 $M_\odot$ for an assumed dust temperature of 20 K and 100 K" (3.2.1 Keplerian Motion)
   - assumption: kappa = 6.8e-4 cm2/g at 1.2 mm; T = 20-100 K  
  > "mass absorption coefficient of 6.8 $\times$ 10$^{-4}$ cm$^{2}$ g$^{-1}$ at 1.2 mm" (3.2.1 Keplerian Motion)
   - fitting: _not stated_
   - validation: _not stated_
4. **CCH envelope model comparison**: Overlay infalling-rotating envelope model on CCH PV diagrams with M=0.007 Msun, centrifugal barrier 40 au  
  > "where the radius of the centrifugal barrier is assumed to be at 40 au" (3.2.2 Infalling-rotating Envelope)
   - parameter: systemic velocity 5.3 km/s gives better fit  
  > "the systemic velocity of 5.3 km s$^{-1}$, which is similar to the previous report (cite: Yen et al.(2017)), gives a better fit" (3.2.2 Infalling-rotating Envelope)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Protostellar mass | 0.007 | +0.004/-0.003 | Msun | 2 | The protostellar mass is estimated to be 0.007$^{+0.004}_{-0.003}$ $M_\odot$ from the velocity profile of the SO emission. |
| Centrifugal barrier radius | 40 | not stated | au | 4 | the radius of the centrifugal barrier is estimated to be 40 au from the comparison with the model |
| Continuum peak intensity at 1.2 mm | 6.98 | 0.12 | mJy/beam | 1 | The peak intensity of 6.98$\pm$0.12 mJy bea$\rm m^{-1}$ at 1.2 mm |
| Toomre Q | 0.4 (20 K) to 5 (100 K) | not stated | dimensionless | 3 | The derived Q parameter is 0.4 and 5 for temperatures of 20 K and 100 K, respectively. |
| Dust mass | 0.006 (20 K) to 0.001 (100 K) | not stated | Msun | 3 | between 0.006 and 0.001 $M_\odot$ for an assumed dust temperature of 20 K and 100 K |
| Current accretion rate | 2.1e-5 | not stated | Msun/yr | 0 | We evaluate the current accretion rate $\dot{M}_{\rm acc}\ \rm to\  be \ 2.1\times 10^{-5}$ $M_\odot$ yr$^{-1}$ |

## Qualitative findings

- CCH traces the infalling-rotating envelope and outflow cavity with a double peak ~70 au from the continuum peak; SO is compact and peaks at the protostar  
  > "The intensity peak of CCH appears on both sides at a distance of about 70 au from the continuum peak." (3.1 Distribution)

## Claim tuples

- H: A Keplerian disk exists around IRAS 15398-3359 and gives its mass | E: SO PV diagram compared to Keplerian model | R: Velocity shift up to ~3 km/s; M = 0.007 (+0.004/-0.003) Msun | F: A rotating disk has formed around a very low-mass protostar | **supported**
- H: CCH kinematics is consistent with an infalling-rotating envelope given this mass | E: CCH PV diagrams with envelope model | R: Model roughly explains data with centrifugal barrier 40 au | F: Envelope consistent with infall-rotation | **supported**
- H: The disk may be gravitationally unstable | E: Toomre Q from dust mass at 20-100 K | R: Q = 0.4-5 | F: Disk partly unstable | **partially**

## Reasoning

- Why this data: Higher resolution needed to confirm disk and measure mass; N=3-2 CCH lines chosen for larger hyperfine separation  
  > "we here chose the $N=3-2$ lines having a larger separation of the hyperfine components" (Observation)
- Why this method: _not stated_
- Alternative: Infalling-rotating envelope with 1 au barrier rejected for SO  
  > "the PV diagram cannot be explained by the infalling-rotating envelope, even if the radius of the centrifugal barrier is set to 1 au" (3.2.1 Keplerian Motion)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass may be an upper limit or apparent value because of non-Keplerian gravity and unresolved material  
  > "In this case, the derived mass could be an upper limit to the mass of the prototstar." (3.2.1 Keplerian Motion)
- Caveat (inferred, ours): Mass fit has no stated method or goodness of fit
- Caveat (inferred, ours): Systemic velocity differs between SO and CCH fits
- Caveat (inferred, ours): Self-absorption not modeled
- Caveat (inferred, ours): Disk mass depends on assumed temperature

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Fitting procedure and models for PV analysis
- Missing: CASA version and imaging parameters
- Data volume (inferred): ~10-30 GB for a single short Cycle 2 Band 6 execution
- Score (inferred): 4/5, Single dataset with stated project code; imaging partly specified, but PV model fitting details missing.
- Rediscovery candidate: no, Mass fitting recipe is not specified enough.

## Links

- Method: Oya et al. (2014) (Infalling-rotating envelope model)
- Companion: Jorgensen et al. (2013) (Earlier ALMA observations of the same source)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 35,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
