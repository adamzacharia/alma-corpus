# ALMA detection of a disc-dominated [C II] emission line at z=4.6 in the luminous QSO J1554+1937

`2015MNRAS.452...88K` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Kimball, Amy E. | arXiv: 1505.05262 | DOI: 10.1093/mnras/stv1160

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What is the origin (rotating disc vs bulge) of the broad [C II] line in the luminous z=4.6 QSO J1554+1937, and how does this affect its position relative to the local M-sigma relation?  
  > "As disc rotation may be a common origin for [C II] emission at high redshifts, these results stress that careful consideration of dynamical origins is required" (abstract)
- Target **SDSS J155426.16+193703.0 (J1554+1937)**: coordinates J2000 08 coordinates implied by name: 15:54:26.16 +19:37:03.0  
  > "With a redshift of $z=4.612$, the QSO SDSS J155426.16+193703.0 (hereafter J1554+1937) has the highest redshift of these most luminous QSOs from the Krawczyk et al. catalog." (2 Target selection and ALMA observations); z/distance z=4.612 (optical); [C II] z=4.627  
  > "With a redshift of $z=4.612$, the QSO SDSS J155426.16+193703.0 (hereafter J1554+1937) has the highest redshift of these most luminous QSOs from the Krawczyk et al. catalog." (2 Target selection and ALMA observations); distance from SDSS DR9 visual redshift; [C II] line centre  
  > "With a redshift of $z=4.612$, the QSO SDSS J155426.16+193703.0 (hereafter J1554+1937) has the highest redshift of these most luminous QSOs from the Krawczyk et al. catalog." (2 Target selection and ALMA observations)

## Data provenance

- ALMA projects: 2012.1.00604.S
- bands: Band 7 (275-373 GHz)  
  > "The redshift of J1554+1937 makes its [C II] line accessible to ALMA’s Band 7 (275–373 GHz)." (2 Target selection and ALMA observations)
- frequencies and spectral setup: Two 2-GHz spectral windows centred at 337 and 339 GHz (~30 km/s resolution); two other windows at 348-352 GHz  
  > "We placed the centres of two of the 2-GHz spectral windows at 337 and 339 GHz" (2 Target selection and ALMA observations); "Two other spectral windows covered the frequency range 348–352 GHz." (2 Target selection and ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration  
  > "The observations were performed using a compact configuration, resulting in angular resolution of approximately 1 arcsec at 340 GHz." (2 Target selection and ALMA observations)
- baselines: maximum baseline ≈400 m  
  > "Based on the maximum baseline length of $\approx400$ m, the smallest angular scale we could resolve at 338 GHz is 0.46$''$." (3 Data Analysis)
- angular resolution: ~1 arcsec at 340 GHz; beam 1.2" x 0.7"  
  > "The synthesized beam size (analogous to the ‘point-spread function’ in optical/IR observations) is 1.2$''$ $\times$ 0.7$''$" (3 Data Analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 5.2 minutes with 25 antennas  
  > "J1554+1937 was observed for 5.2 minutes with 25 available antennas." (2 Target selection and ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2 -> 2P1/2 (157.74 micron)
- Other facility **SDSS**: Optical spectrum and redshift of UV lines; C IV black hole mass from Shen et al.  
  > "We consider the ‘true’ redshift of the ultraviolet lines to be the visually determined redshift reported in SDSS Data Release 9" (4.1 Redshift offset)
- Other facility **FIRST/NVSS**: Radio upper limit  
  > "thus its 1.4-GHz flux density is less than $\sim1$ mJy." (2 Target selection and ALMA observations)
- External data: Bolometric luminosity and target selection from QSO catalog  
  > "We first identified luminous QSOs as potential targets from the multi-wavelength QSO catalog of (cite: krawczyk13)" (2 Target selection and ALMA observations) [from (cite: krawczyk13)]
- External data: SMBH mass (2.8±0.5)e10 Msun from C IV width  
  > "(cite: shenEtal11) estimated the SMBH in J1554+1937 to have a mass of $M_\mathrm{BH} = (2.8\pm0.5)\times10^{10}~M_\odot$." (4.6 Measuring the central black hole mass) [from (cite: shenEtal11)]
- External data: Linear v0-sigma relation  
  > "We therefore use the linear relation from (cite: pizzella05) to represent the relationship between $\sigma$ and $v_0$." (4.5) [from (cite: pizzella05)]
- External data: Local M-sigma relation  
  > "we are now equipped to compare J1554+1937 to the local $M$–$\sigma$ relation (cite: kormendyHo_review)" (4.7) [from (cite: kormendyHo_review)]
- Simulation/model as data: Idealised disc model line profiles (v0=480 km/s, sigma_v=75 km/s, i=60 deg; rc/r0 = 0.5, 1, 2)  
  > "we assign the parameters $v_0=480$ km s$^{-1}$, $\sigma_v=75$ km s$^{-1}$, and $i=60\ensuremath{^\circ}$." (4.3 [C II] line profile)

## Processing

### Calibration

- pipeline or manual: NAASC-provided Python scripts, minor modifications to reduce flagged edge channels  
  > "We performed minor modifications to the scripts in order to reduce the number of frequency channels flagged at the spectral window edges." (3 Data Analysis)
- casa version: CASA 4.2  
  > "The scripts were executed in version 4.2 of CASA" (3 Data Analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (phase calibrator J1619+2247)  
  > "Titan was used as the absolute flux calibration source and nearby QSO J1619+2247 (6.6 degrees distant) as the phase calibrator." (2 Target selection and ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: single round of phase-only self-calibration using combined continuum and line data  
  > "We performed a single round of phase-only self-calibration using solutions from the combined continuum and line data." (3 Data Analysis)

### Imaging

- task: CASA clean  
  > "We produced our own set of de-convolved images using CASA’s `clean` task" (3 Data Analysis)
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5  
  > "we used Briggs weighting with parameter setting `robust=0.5`" (3 Data Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from data cube  
  > "We isolated the line emission by subtracting the continuum from the data cube." (3 Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.2" x 0.7" (7.8x4.6 kpc)  
  > "is 1.2$''$ $\times$ 0.7$''$, corresponding to $7.8\times4.6$ kpc at $z=4.6$" (3 Data Analysis)
- final rms: continuum ~0.15 mJy/beam; moment 0 ~0.4 Jy/beam km/s; channel ~2 mJy  
  > "the rms noise level in the continuum image is approximately 0.15 mJy beam$^{-1}$" (3 Data Analysis)

### Inherited from earlier work

- Bolometric luminosity definition (1 micron-0.62 nm)  
  > "Following the recommendation of Krawczyk et al., we define a QSO’s bolometric luminosity as the energy in the (rest-frame) wavelength range 1 $\mu$m–0.62 nm (2 keV)." (2 Target selection and ALMA observations) [from Krawczyk et al. (cite: krawczyk13)]
- Aperture correction sigma_e/2 = 0.93 sigma_e/8  
  > "We apply the correction given by (cite: jorgensenFranxKjaergaard95)" (4.5) [from (cite: jorgensenFranxKjaergaard95)]

### Not stated but needed to reproduce (our reading)

- Channel width and cell/image size used in clean
- Line-free channels used for continuum subtraction and continuum map
- Clean threshold, masking and iterations
- Self-calibration solution interval
- How the moment maps and 20 per cent half-width were measured (visual)
- Details of the line profile model fitting/inclination integration
- Number of execution blocks and observing date

## Analysis recipe

1. **Calibrate and image**: Run NAASC scripts in CASA 4.2, clean with Briggs weighting, one round of phase-only self-calibration  
  > "We produced our own set of de-convolved images using CASA’s `clean` task, for which we used Briggs weighting with parameter setting `robust=0.5`." (3 Data Analysis)
   - software: CASA, clean
   - parameter: robust=0.5  
  > "we used Briggs weighting with parameter setting `robust=0.5`" (3 Data Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum and line sizes and fluxes**: Gaussian fit in the uv-plane with uvmodelfit for continuum and line; moment 0, 1, 2 maps  
  > "we performed a Gaussian fit to the data in the UV-plane using the CASA task `uvmodelfit`" (3 Data Analysis)
   - software: CASA, uvmodelfit
   - parameter: moment 0 over 337.3-338.2 GHz; moment 1 pixels with S/N ≥4 of ~2 mJy rms  
  > "using the frequency range 337.3–338.2 GHz" (3 Data Analysis)
   - fitting: Gaussian in uv-plane  
  > "To estimate the source size, we performed a Gaussian fit to the data in the UV-plane using the CASA task `uvmodelfit`" (Data Analysis)
   - validation: Moment 0 S/N ~10 at edges indicates velocity gradient is real  
  > "In the moment 0 map, the S/N is $\sim10$ at the edges of this region, indicating that this gradient is real." (3 Data Analysis)
3. **Model disc line profiles**: Idealised disc with v(r)=v0[1-exp(-r/r0)], exponential surface brightness, Gaussian dispersion, inclination, integrated over disc  
  > "We assume a fiducial velocity ($v$) rotation curve that initially rises exponentially, then levels off with some characteristic radius $r_0$" (4.3 [C II] line profile)
   - assumption: v0 and inclination degenerate  
  > "the parameters for inclination ($i$) and maximum velocity ($v_0$) are degenerate in this model." (4.3 [C II] line profile)
   - fitting: rough visual comparison, no formal fit  
  > "We avoid complex modelling at present, as the low spatial resolution of the current observations does not constrain the possible dynamical theories." (Analysis, [C II] line profile)
   - validation: _not stated_
4. **Dynamical mass**: Mdyn/Msun ≈1.16e5 v0^2 D with v0 sin i from half-width at 20% of maximum  
  > "$M_\mathrm{dyn}/M_\odot\approx1.16\times10^{5}v_0^2D$" (4.4)
   - assumption: rotating disc; D=1.6 kpc (line) or 2.0 kpc (continuum)  
  > "If we assume a rotating disc geometry for the origin of the \[C II\] line, we can estimate the dynamical mass within the disc radius" (Analysis, Estimating dynamical mass for a rotating disc)
   - fitting: _not stated_
   - validation: _not stated_
5. **Bulge velocity dispersion from disc rotation**: Pizzella et al. linear v0-sigma relation, then aperture correction to r_e/2  
  > "Using their formulation, we find that $\sigma_{e/2} = 0.93\times\sigma_{e/8}$" (4.5)
   - assumption: host has a classical bulge  
  > "Applying the $v_0/\sigma$ relation to J1554+1937 thus requires the assumption that its host galaxy contains a classical bulge." (4.5)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare with M-sigma**: Place the source relative to the Kormendy & Ho relation with SMBH mass from Shen et al. for various inclinations  
  > "We show the estimated locations for J1554+1937 for different potential values of the unknown disc inclination" (4.7)
   - assumption: intrinsic scatter 0.29 dex  
  > "Given that the intrinsic scatter of the $M$–$\sigma$ relation is 0.29 dex" (4.7)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2: Calibration scripts, clean imaging, uvmodelfit  
  > "The scripts were executed in version 4.2 of CASA" (3 Data Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C II] FWHM | 735 | not stated | km/s | 2 | The FWHM is 735 km s$^{-1}$. |
| [C II] redshift | 4.627 | not stated | dimensionless | 2 | The actual redshift of the line is approximately 4.627 |
| Continuum flux density at ~344 GHz | 12.70 | 0.12 | mJy | 2 | The integrated flux density resulting from the fit is $12.70\pm0.12$ mJy at $\sim344$ GHz. |
| [C II] integrated flux | 9.40 | 0.40 | Jy km/s | 2 | The integrated flux density is to be $9.40\pm0.40$ Jy km s$^{-1}$ |
| [C II] line luminosity | 5.9e9 | not stated | Lsun | 2 | corresponding to a line luminosity of $5.9\times10^9~\mathrm{L}_\odot$ |
| Dynamical mass x sin^2 i (continuum size) | 5.3e10 | 1.3e10 | Msun | 4 | $M_\mathrm{dyn}\times\sin^2(i)\approx(5.3\pm1.3)\times10^{10}~M_\odot$ |
| Minimum sigma_e/2 | 310 | not stated | km/s | 5 | therefore $\sigma_{e/2}\ensuremath{\gtrsim}310$ km s$^{-1}$ for J1554+1937 |
| Eddington ratio | 0.15 | not stated | dimensionless | 6 | the Eddington ratio ($L_\mathrm{bol}/L_\mathrm{Edd}$) is 0.15 |

## Qualitative findings

- Velocity gradient east to west suggests large-scale rotation; velocity dispersion peaks at centre (beam smearing).  
  > "The velocity map shows a clear gradient of higher to lower velocity from the east to the west." (3 Data Analysis)

## Claim tuples

- H: Is the broad [C II] line from a rotating disc? | E: Moment maps and idealised disc line profile models | R: Gradient and flat-topped/double-peaked profile consistent with disc; v0 sin i ~480 km/s | F: A disc origin is plausible but outflow/merger origins cannot be excluded at this resolution | **partially**
- H: Is the QSO over-massive relative to the local M-sigma relation? | E: Estimate sigma from disc v0 and compare to M_BH | R: Consistent or offset at most an order of magnitude; bulge assumption gives ~2 orders | F: Assuming disc origin, the source is likely consistent with local relation | **supported**

## Reasoning

- Why this data: Compact configuration chosen for high sensitivity for a continuum detection experiment  
  > "we opted for an array configuration that would achieve high sensitivity at the cost of spatial resolution." (2 Target selection and ALMA observations)
- Why this method: _not stated_
- Alternative: Bulge origin, outflow and merger origins of the [C II] velocity gradient considered  
  > "Bi-directional outflows of ionized gas are another possible origin for the [C II] velocity gradient." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Low spatial resolution prevents determining inclination and detailed kinematics  
  > "The poor spatial resolution prevents us from determining the inclination" (4.4)
- Caveat (inferred, ours): Disc interpretation rests on marginally resolved data
- Caveat (inferred, ours): Chain of empirical relations calibrated at low z and lower velocities
- Caveat (inferred, ours): C IV black hole mass is uncertain
- Caveat (inferred, ours): v0 estimated visually without formal uncertainty

## Reproducibility

- Data public (paper): ALMA data acknowledged with project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00604.S." (acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: Continuum and line-free channel definitions
- Missing: Exact moment map thresholds and line-width measurement
- Data volume (inferred): ~ a few GB (single short Band 7 execution)
- Score (inferred): 3/5, Short single dataset with public ALMA data and simple recipe, but several imaging details and visual measurements are unspecified.
- Rediscovery candidate: yes, Single archival dataset, numeric results (flux, FWHM, sizes) are recoverable with standard CASA steps.

## Links

- Companion: Krawczyk et al. 2013 (cite: krawczyk13) (QSO catalog from which target was selected)
- Related: Willott et al. 2013, Wang et al. 2013 [C II] ALMA QSO studies

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 49,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
