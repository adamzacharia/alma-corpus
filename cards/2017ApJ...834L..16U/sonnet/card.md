# ALMA Reveals Strong [C II] Emission in a Galaxy Embedded in a Giant Lyα Blob at z = 3.1

`2017ApJ...834L..16U` | The Astrophysical Journal Letters 2017 | first author: Umehata, Hideki | arXiv: 1701.00043 | DOI: 10.3847/2041-8213/834/2/L16

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do the dusty star-forming galaxies and other galaxies embedded in the giant Lyα blob SSA22-LAB1 at z=3.1 emit [CII] 158 µm, and what does the [CII]/IR and [CII]/[NII] ratio imply about their ISM?  
  > "Of three dusty star-forming galaxies previously discovered by ALMA 860 $\mu$m dust continuum survey toward SSA22-LAB1, we detected the [CII] line from one, LAB1-ALMA3" (abstract)
- Target **SSA22-LAB1 (LAB1-ALMA1, ALMA2, ALMA3, C11, K1, S1)**: coordinates ALMA3: 22:17:26.11 +00:12:32.4 (J2000)  
  > "| LAB1-ALMA3 | 22:17:26.11 | +00:12:32.4 | $3.0993\pm0.0004$ | [CII] 158 $\mu$m | 1 |" (Table 1); "SSA22-LAB1 (hereafter LAB1, (cite: 2000ApJ...532..170S)) is a giant LAB discovered in the $z=3.1$ SSA22 proto-cluster region" (2 Observations and data reduction); z/distance z=3.0993±0.0004 (ALMA3)  
  > "| LAB1-ALMA3 | 22:17:26.11 | +00:12:32.4 | $3.0993\pm0.0004$ | [CII] 158 $\mu$m | 1 |" (Table 1); "SSA22-LAB1 (hereafter LAB1, (cite: 2000ApJ...532..170S)) is a giant LAB discovered in the $z=3.1$ SSA22 proto-cluster region" (2 Observations and data reduction); distance from [CII] line, this work  
  > "| LAB1-ALMA3 | 22:17:26.11 | +00:12:32.4 | $3.0993\pm0.0004$ | [CII] 158 $\mu$m | 1 |" (Table 1); "SSA22-LAB1 (hereafter LAB1, (cite: 2000ApJ...532..170S)) is a giant LAB discovered in the $z=3.1$ SSA22 proto-cluster region" (2 Observations and data reduction)

## Data provenance

- ALMA projects: 2013.1.00159.S, 2013.1.00704.S
- bands: Band 8 ([CII]); Band 7 ([NII] and continuum)  
  > "We observed LAB1 with ALMA in band 8 as a part of an ALMA cycle-2 program" (2 Observations and data reduction)
- frequencies and spectral setup: FDM spectral scan, two windows: 461.03–462.78 and 462.91–464.66 GHz  
  > "The incomplete observation resulted in frequency coverage of 461.03–462.78 GHz and 462.91–464.66 GHz" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-5  
  > "The array configuration was C34-5 and the baseline lengths were 21–784 m." (2 Observations and data reduction)
- baselines: 21–784 m  
  > "The array configuration was C34-5 and the baseline lengths were 21–784 m." (2 Observations and data reduction)
- angular resolution: 0.27x0.26 arcsec (full cube); 0.53x0.52 arcsec (tapered)  
  > "has a typical synthesized beam FWHM of $0^{\prime\prime}.27\times0^{\prime\prime}.26$ (P.A. 46 deg)" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 3.5 mJy/beam per 80 km/s channel (tapered band 8 cube)  
  > "The typical rms level is $\approx$ 3.5 mJy beam$^{-1}$ at the phase center per 80 km s$^{-1}$ channel in the tapered cube." (2 Observations and data reduction)
- time on source: 4.5 minutes  
  > "The on-source time was 4.5 minutes." (2 Observations and data reduction)
- observing dates: 16 June 2015  
  > "Observations were carried out on 16 June 2015" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: [CII] 158 µm 2P3/2→2P1/2 (1900.537 GHz)
- Line: [NII] 205 µm (1461.131 GHz)
- Other facility **HST STIS**: optical image for comparison  
  > "$HST$ STIS optical image[^2] ((cite: 2003ApJ...599...92C))" (3.1 [CII] 158 µm in LAB1-ALMA3)
- External data: 860 µm continuum sources and flux density S860=0.73±0.05 mJy for ALMA3  
  > "$S_{\rm 860 \mu m}=0.73\pm0.05$ mJy ((cite: 2016ApJ...832...37G))" (3.1 [CII] 158 µm in LAB1-ALMA3) [from (cite: 2016ApJ...832...37G)]
- External data: Spectroscopic redshift of ALMA3 from Hβ and [OIII]  
  > "reported a redshift of $z=3.1000\pm0.0003$ on the basis of H$\beta$ and [OIII] $\lambda$5007 lines" (3.1 [CII] 158 µm in LAB1-ALMA3) [from (cite: 2015ApJ...799...38K)]
- External data: Average ALESS SMG template for LIR  
  > "derived using an average SMG template from the ALESS survey ((cite: 2014MNRAS.438.1267S))" (3.1 [CII] 158 µm in LAB1-ALMA3) [from (cite: 2014MNRAS.438.1267S)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.4.0  
  > "The data were processed with the Common Astronomy Software Application (casa) ver. 4.4.0" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (amplitude); J2148+0657 (bandpass and phase)  
  > "Ceres was observed for amplitude calibration, and the quasar J2148+0657 was utilized for bandpass and phase calibration." (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, natural weighting  
  > "The cube was first created with the natural weighting using the casa task, clean." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: outertaper = 0.5 arcsec  
  > "adopting the taper parameter, outertaper = 0.5 arcsec" (2 Observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.53x0.52 arcsec PA -70 deg (tapered)  
  > "which has a typical synthesized beam, $0^{\prime\prime}.53\times0^{\prime\prime}.52$ (P.A. $-70$ deg)" (2 Observations and data reduction)
- final rms: 3.5 mJy/beam per 80 km/s channel; continuum 0.8 mJy/beam  
  > "The "dirty" map has a rms level of 0.8 mJy beam$^{-1}$ at the phase center" (2 Observations and data reduction)

### Inherited from earlier work

- Band 7 data/[NII] analysis and rest-frame 210 µm continuum  
  > "(Y. Matsuda et al. in preparation)" (2 Observations and data reduction) [from Y. Matsuda et al. in preparation]

### Not stated but needed to reproduce (our reading)

- Band 7 calibration and imaging details
- Clean threshold, mask, cell and image size
- Which channels were line-free for continuum
- Exact virial mass formula and factors
- Details of Gaussian fit and uncertainty method
- LIR template scaling details

## Analysis recipe

1. **Make cubes and continuum**: clean cube with natural weighting, plus tapered version; tapered continuum from line-free channels  
  > "we created a "tapered" continuum map at 463 GHz, using the line-free channels." (2 Observations and data reduction)
   - software: CASA
   - parameter: outertaper = 0.5 arcsec  
  > "adopting the taper parameter, outertaper = 0.5 arcsec" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure [CII] line and size**: Gaussian fit to spectrum; 2D elliptical Gaussian fit to tapered map  
  > "A gaussian fit to the line has $z=3.0993\pm0.0004$ with FWHM $275\pm30$ km s$^{-1}$." (3.1 [CII] 158 µm in LAB1-ALMA3)
   - software: CASA
   - fitting: Gaussian line profile; 2D elliptical Gaussian  
  > "A gaussian fit to the line has $z=3.0993\pm0.0004$ with FWHM $275\pm30$ km s$^{-1}$." (Results, [CII] 158 μm in LAB1-ALMA3)
   - validation: redshift compared with Kubo et al. optical redshift  
  > "hence our measurement is consistent" (3.1 [CII] 158 µm in LAB1-ALMA3)
3. **Derive LIR and dynamical mass**: LIR from ALESS average SMG template scaled to 860 µm flux; isotropic virial mass from line width and [CII] size  
  > "using an isotropic virial estimator (e.g., (cite: 2010ApJ...724..233E)) on the basis of the line width and [CII] size" (3.1 [CII] 158 µm in LAB1-ALMA3)
   - assumption: cosmology Om=0.3, OL=0.7, H0=70  
  > "we adopt a cosmology with $\Omega_{\rm m}=0.3, \Omega_\Lambda=0.7$, and H$_0$=70 km s$^{-1}$ Mpc$^{-1}$" (1 Introduction)
   - fitting: _not stated_
   - validation: LIR range 0.2-1.5e12 from varying templates noted  
  > "estimated it in the range $L_{\rm IR}\approx(0.2-1.5)\times10^{12} L_\odot$ using varying templates." (Results, [CII] 158 μm in LAB1-ALMA3)
4. **Upper limits for [NII] and other galaxies**: 3σ upper limits integrating cube over 300 km/s at source positions (or ALMA3 line width); [NII] 3σ point-source limit from tapered maps  
  > "we integrated the cube at the position in literatures over $300$ km s$^{-1}$ velocity range, and obtain 3$\sigma$ upper limits." (Table 1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4.0: data processing and clean imaging  
  > "The data were processed with the Common Astronomy Software Application (casa) ver. 4.4.0" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA3 redshift | 3.0993 | 0.0004 | dimensionless | 2 | $z=3.0993\pm0.0004$ with FWHM $275\pm30$ km s$^{-1}$ |
| [CII] FWHM | 275 | 30 | km/s | 2 | FWHM $275\pm30$ km s$^{-1}$ |
| [CII] integrated flux | 16.8 | 2.1 | Jy km/s | 2 | $I_\textsc{[Cii]}=16.8\pm2.1$ Jy km s$^{-1}$ |
| L[CII] | 5.7e9 | 0.7e9 | Lsun | 2 | $L_\textsc{[Cii]}=(5.7\pm0.7) \times10^{9} L_\ensuremath{\odot}$ |
| LIR | 5.8e11 | 0.4e11 | Lsun | 3 | $L_{\rm IR}\approx5.8\pm0.4\times10^{11} L_\odot$ |
| L[CII]/LIR | 0.010 | 0.001 | dimensionless | 3 | $L_\textsc{[Cii]}/L_{\rm IR}\approx0.010\pm0.001$ |
| Dynamical mass | 1.0e11 | not stated | Msun | 3 | $M_{\rm dyn, vir}\sim 1.0\times10^{11} M_\odot$ |
| [CII] deconvolved size | 0.62x0.55 arcsec (4.8x4.3 kpc) | 0.11, 0.10 arcsec | arcsec | 2 | deconvolved FWHM of ($0^{\prime\prime}.62\pm0^{\prime\prime}.11)\times(0^{\prime\prime}.55\pm0^{\prime\prime}.10$) |
| L[CII]/L[NII] lower limit | >55 | not stated | dimensionless | 4 | $L_\textsc{[Cii]}/L_\textsc{[Nii]}>55$ |
| [CII] upper limit ALMA1/ALMA2 | <2.3 | 3σ | Jy km/s | 4 | $I_\textsc{[Cii]}<2.3$ Jy km s$^{-1}$ |

## Qualitative findings

- [CII] emission is spatially resolved with complex velocity field, not a simple rotating disk  
  > "The [CII] velocity map (Fig. 2b) also shows complexity, which is not likely to be produced by a simple rotating disk." (3.1 [CII] 158 µm in LAB1-ALMA3)

## Claim tuples

- H: Do LAB1 member galaxies show [CII] emission? | E: Band 8 spectral scan of LAB1 | R: Only ALMA3 detected; ALMA1, ALMA2 and three UV/optical galaxies undetected | F: [CII] is detected from one of three dusty galaxies | **supported**
- H: Is ALMA3 [CII]/IR high relative to IR-luminous galaxies? | E: Compare L[CII]/LIR with [CII] deficit trend | R: ratio ≈0.01, ~order of magnitude higher | F: Different ISM conditions, e.g. extended star formation | **supported**
- H: What causes strong [CII]? | E: Use L[CII]/L[NII]>55 vs models | R: favors sub-solar metallicity, PDRs, possible shocks | F: Origin possibly linked to the LAB environment, but uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Doubly ionized nitrogen effect deemed unlikely because ALMA3 is dust detected  
  > "This effect is unlikely to be significant in ALMA3 because it is detected in dust continuum." (4 Discussion and Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Incomplete observation: only two of four spectral windows executed; ALMA1/2 lack spectroscopic redshifts  
  > "Among four planned spectral windows, only two were actually executed." (2 Observations and data reduction)
- Caveat (inferred, ours): Very short 4.5 min integration, modest S/N
- Caveat (inferred, ours): LIR uncertain by a factor of several from template choice
- Caveat (inferred, ours): Upper limits for ALMA1/2 assume unknown redshift
- Caveat (inferred, ours): Single detected source limits statistics on the environment link

## Reproducibility

- Data public (paper): ALMA project IDs given in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00159.S, ADS/JAO.ALMA#2013.1.00704.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters beyond weighting/taper
- Missing: Band 7 processing details (in preparation paper)
- Missing: Virial mass coefficient
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public data and clear basic imaging, but sparse imaging parameters and band 7 details deferred to unpublished work.
- Rediscovery candidate: yes, Public data, short recipe, numeric results (flux, luminosity, redshift) can be redone.

## Links

- Method: (cite: 2010ApJ...724..233E) (isotropic virial mass estimator)
- Method: (cite: 2014MNRAS.438.1267S) (SMG template for LIR)
- Companion: (cite: 2016ApJ...832...37G) (ALMA 860 µm survey of SSA22-LAB1)
- Companion: (cite: 2015ApJ...799...38K) (spectroscopic redshift of ALMA3)
- Related: ALMA 860 µm survey of LABs (Geach et al. 2016)
- Related: ALESS

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 37,
  "rate": 0.561
 },
 "evidence_ok": true
}
```
