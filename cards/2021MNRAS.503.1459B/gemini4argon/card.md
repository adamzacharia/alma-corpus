# Dynamical model of an obscuring clumpy torus in AGNs - I. Velocity and velocity dispersion maps for interpretation of ALMA observations

`2021MNRAS.503.1459B` | Monthly Notices of the Royal Astronomical Society 2021 | first author: Bannikova, E. Yu | arXiv: 2102.12130 | DOI: 10.1093/mnras/stab468

Card schema 1.0 | model gemini-4-argon | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Develop a dynamical N-body model of a self-gravitating obscuring clumpy torus in an AGN to construct velocity, velocity dispersion, and temperature maps and interpret ALMA and VLTI/MIDI observations.  
  > "We have developed the dynamical model of a clumpy torus in an active galactic nucleus (AGN) and compared to recent ALMA observations." (Abstract); "In this paper we develop a dynamical model of an obscuring clumpy torus in AGNs with the purpose of interpreting the ALMA velocity and velocity dispersion maps together with the temperature distribution." (Conclusions)
- Target **NGC 1068**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC 1326**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC 1672**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00052.S, 2015.0.00404.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
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
- Line: HCN (3-2) (not stated)
- Line: CO (3-2) (not stated)
- Other facility **VLTI/MIDI**: Mid-infrared temperature distribution maps of the torus in NGC 1068 from the literature for comparison with model temperature maps.  
  > "Finally, we obtain the temperature distribution maps with parameters that correspond to our model velocity maps for NGC 1068. They show stratification in temperature distribution with the shape of the high temperature region as in the VLTI/MIDI map." (Abstract); "The first direct observation of the torus in NGC 1068 in MIR was made by means of VLTI/MIDI (cite: Jaffe2004; Raban2009)." (Introduction)
- External data: ALMA HCN(3-2) velocity and velocity dispersion maps and v_obs = 20 km s^-1 at 3 pc for NGC 1068  
  > "We compare our model maps with ALMA observations in HCN(3-2) and CO(3-2) molecular lines in the millimetre band which provide the velocity and velocity dispersion maps for the nearest Seyfert galaxies (cite: Imanishi2018; Combes2019)." (Interpretation of ALMA observations for Seyfert galaxies); "(cite: Imanishi2018) obtained the velocity distribution in the torus of NGC 1068 with the observational velocity value $v_{obs} = 20$ km s$^{-1}$on 3pc." (The velocity dispersion map and the mass of SMBH in NGC 1068) [from (cite: Imanishi2018)]
- External data: ALMA CO(3-2) velocity dispersion maps and torus major radii (R = 10 pc for NGC 1672 and R = 8 pc for NGC 1326)  
  > "Their velocity dispersion maps are presented in fig. [15](#fig:alma) *bottom* from (cite: Combes2019)." (NGC 1326 and NGC 1672 velocity dispersion maps); "The major radii of the tori were taken from the ALMA observational maps: $R=10$ pc for NGC 1672 and $R=8$ pc for NGC 1326." (NGC 1326 and NGC 1672 velocity dispersion maps) [from (cite: Combes2019)]
- External data: Torus mass M_torus = 1 x 10^5 M_sun and radius R_torus = 3.5 pc in NGC 1068 from ALMA CO(6-5)  
  > "(cite: Garcia2016) presented the CO(6-5) mean velocity map of the torus in NGC 1068, which provided a torus mass of $M_\text{torus} = 1\times 10^5 M_\odot$, a radius of $R_\text{torus} = 3.5$ pc" (Introduction) [from (cite: Garcia2016)]
- External data: Bolometric luminosity of NGC 1068 L_bol = 5.65 x 10^44 erg s^-1  
  > "An estimate of the bolometric luminosity for NGC 1068 (cite: Pier1994) is $L_{\text{bol}}=5.65 \times 10^{44}$ erg s$^{-1}$." (Temperature of clouds in the torus) [from (cite: Pier1994)]
- External data: VLTI/MIDI temperature distribution observations of the torus in NGC 1068  
  > "The first direct observation of the torus in NGC 1068 in MIR was made by means of VLTI/MIDI (cite: Jaffe2004; Raban2009)." (Introduction) [from (cite: Jaffe2004; Raban2009)]
- Simulation/model as data: Direct N-body simulations of a self-gravitating clumpy torus with N = 8k, 16k, 32k, 64k, and 128k clouds in the gravitational field of a SMBH using the phi-GPU code.  
  > "In this paper we present the result of the torus evolution for a set of numbers of clouds: $N$=8k; 16k; 32k; 64k; 128k." (Initial conditions); "At variance with our previous work, where we used the Euler integrator for the numerical solution of the equations of motion, here we adopt a more precise algorithm, namely the $\varphi-$GPU code." (\varphi-GPU code)
- Simulation/model as data: Ray-tracing simulations of velocity, velocity dispersion, and temperature maps through optically thick spherical clouds.  
  > "To take into account all these factors, we make use of the a ray tracing algorithm in the following way." (Velocity and velocity dispersion maps); "Construction of the temperature distribution maps differs from that of velocity and velocity dispersion maps as it includes an additional – zeroth – step in the above described algorithm." (Temperature of clouds in the torus)

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

- General AGN evolution scenario for choosing initial conditions of the N-body simulations  
  > "The initial conditions for the $N$-body simulations are chosen in accordance with the general idea of the AGN evolution proposed in (cite: Bannikova2015; Bannikova2017)." (Initial conditions) [from (cite: Bannikova2015; Bannikova2017)]
- Approach of composing the gravitational potential of an elliptical torus from infinitely thin rings  
  > "To obtain the gravitational potential of the elliptical torus, we compose it of potentials of infinitely thin rings, *i.e.* we apply the same approach which we used for the case of a circular torus (cite: Bannikova2011)." (Box-orbits as an explanation for the oscillations of the torus cross-section sizes) [from (cite: Bannikova2011)]
- Total number of clouds N = 128k for obscuration condition  
  > "We use the result of our $N$-body simulations for $N$=128k clouds in correspondence with the previous estimation of the obscuration condition (cite: Nenkova2008b; Bannikova2012)." (Velocity and velocity dispersion maps) [from (cite: Nenkova2008b; Bannikova2012)]

### Not stated but needed to reproduce (our reading)

- Order of the Hermite integration scheme (4th, 6th, or 8th) actually used in the production phi-GPU runs
- Random number seed or realization details for initial orbital element distributions
- Exact snapshot time (in orbital periods) from the N=128k simulation used to construct the ray-traced velocity, dispersion, and temperature maps
- Quantitative goodness-of-fit metric (if any) used to select the best parameters for NGC 1068, NGC 1326, and NGC 1672

## Analysis recipe

1. **Perform N-body simulations of a self-gravitating clumpy torus around a SMBH**: Direct N-body numerical integration using high-order Hermite integration and hierarchical block time steps in the phi-GPU code, evolving random initial Keplerian orbits with a polar wind cone cut-off up to 1000 orbital periods.  
  > "This package uses a high order Hermite integration scheme and individual block time steps (the code supports time integration of particle orbits with schemes of 4$^{\rm th}$, 6$^{\rm th}$ and even 8$^{\rm th}$ order)." (\varphi-GPU code); "Fig. [6](#fig:density_plot) shows the density plots of all $N$=128k clouds in projection on the meridian co-moving plane at $t = 0, 2, 48, 115, 320, 1000$ orbital periods." (Results of N-body simulations)
   - software: phi-GPU
   - parameter: Units: G = M_smbh = R = 1; N = 8k, 16k, 32k, 64k, 128k; softening parameter epsilon = 0.01; integration accuracy parameter tau = 0.01  
  > "In the following we will use the system of units $G=M_{\text{smbh}}=R=1$, where $G$ is the gravitational constant and $M_{\text{smbh}}$ is the SMBH mass." (Initial conditions); "The results of the simulations do not differ substantially by varying $\varepsilon$, so we use $\varepsilon = 0.01$ in the following simulations." (Initial conditions); "After the total energy check, we see that the optimal $\tau$ parameter (speed vs. accuracy) is around 0.01." (Results of N-body simulations)
   - parameter: Initial orbital elements: a_k in [0.6, 1.4], e_k in [0, 0.9], i_k in [0, pi/2 - theta], wind half-opening angle theta = 30 deg or 45 deg, Omega_k, omega_k, nu_k uniform in [0, 2pi]  
  > "We leave the half-opening angle $\theta$ of the wind cone as a free parameter, experimenting with two values ($30^\circ$, $45^\circ$)." (Initial conditions); "In such a system of units we set the semi-major axes of particles in the range: $a_k=[0.6,..,1.4]$, so that the mean radius of the system in the equatorial plane $a_{\text{mean}}=R=1$ (an analogue of the major radius of the torus)." (Initial conditions); "The eccentricities are in the interval $e_k=[0,..,0.9]$ and the inclinations of the orbits measured from the equatorial plane in the range $i_k=[0,..,\pi/2-\theta]$." (Initial conditions)
   - assumption: Dissipationless system (cloud collisions and radiation pressure on dynamics neglected), equal cloud masses m_k, torus-to-SMBH mass ratio M_torus / M_smbh = 0.02  
  > "In our $N$-body simulations the cloud masses share the same value $m_k$. Resting on observational data, we also chose the torus–mass–to–SMBH–mass ratio $M_\text{torus}/M_{\text{smbh}} = 0.02$." (Initial conditions); "These oscillations have been derived under the assumption that the system is dissipationless." (Results of N-body simulations)
   - fitting: Gaussian fit along z-axis and log-normal fit along radial (rho) axis to the equilibrium cloud density distribution to determine effective radius r_eff containing 50% of particles.  
  > "Now, we estimate the size of the resulting distribution by the best-fitting Gaussian function along the $z$-axis:" (Results of N-body simulations); "and by log-normal law along the $\rho$ axis:" (Results of N-body simulations)
   - validation: Total energy conservation checked across 6 values of tau (0.020 to 0.001) on the N=8k model; total energy conserved up to a few x 10^-4 and virial parameter oscillates around zero.  
  > "For this reason we start the $N$=8k model with 6 different values of $\tau$ = 0.020, 0.010, 0.007, 0.005, 0.002, 0.001." (Results of N-body simulations); "The total energy is conserved with a good accuracy, up to a few $\times 10^{-4}$ for each numerical experiment corresponding to a given number of the clouds in the system (fig. [2](#fig:energy))." (Results of N-body simulations)
2. **Model analytical potential of an elliptical torus and test for box orbits**: Compose the gravitational potential of a torus with elliptical cross-section from infinitely thin rings, approximate the inner potential with a 4th-order power series, and numerically integrate 3D test-particle equations of motion.  
  > "To obtain the gravitational potential of the elliptical torus, we compose it of potentials of infinitely thin rings, *i.e.* we apply the same approach which we used for the case of a circular torus (cite: Bannikova2011)." (Box-orbits as an explanation for the oscillations of the torus cross-section sizes); "The numerical solution of the equations ([\[eq:eff_mot\]](#eq:eff_mot)) allows us to obtain the coordinates of a particle in the inner potential of the torus ([\[eq_series\]](#eq_series)) and the central mass." (Box-orbits as an explanation for the oscillations of the torus cross-section sizes)
   - parameter: Geometrical parameter r_0 = 0.5, ellipticity alpha = 1.2; initial particle conditions x_0 = 0.55, v_y0 = 16.36, v_z0 = 0.7  
  > "for parameters of the central region of the torus cross-section approximately corresponding to the equilibrium state of the torus from $N$-body simulations: $r_0=0.5$, $\alpha = 1.2$." (Box-orbits as an explanation for the oscillations of the torus cross-section sizes); "The resulting trajectory in a co-moving system is presented in fig. [9](#fig:box-orbit) for the following (non-zero) initial conditions: $x_0=0.55$, $v_{y0} = 16.36$, $v_{z0}=0.7$." (Box-orbits as an explanation for the oscillations of the torus cross-section sizes)
   - assumption: Smooth gravitational potential of a torus with an elliptical cross-section.  
  > "In order to test this hypothesis, we consider the motion of a particle in the smooth potential of a torus with an elliptical cross-section since the central part of the torus cross-section has an elliptical shape (fig. [6](#fig:density_plot) *right bottom*)." (Box-orbits as an explanation for the oscillations of the torus cross-section sizes)
   - fitting: Best-fitting the numerical integration of the exact integral potential with a 4th-order power series to obtain coefficients a_ik.  
  > "The coefficients of the series ([\[eq_series\]](#eq_series)) were obtained by best fitting the result of the numerical integration of ([\[eq_PotTor\]](#eq_PotTor))." (Box-orbits as an explanation for the oscillations of the torus cross-section sizes)
   - validation: Comparison of the z-coordinate oscillation period (~100 orbital periods) of the analytical box orbit with the cross-section oscillation scale in the N-body simulations.  
  > "Indeed, fig. [9](#fig:box-orbit) (*bottom, left*) demonstrates the oscillation of the $z$-coordinate with a period approximately equal to 100 orbital periods. This corresponds to the oscillation scale of the torus cross-section along $z$-axis (fig. [8](#fig:sizeh))." (Box-orbits as an explanation for the oscillations of the torus cross-section sizes)
3. **Construct model velocity and velocity dispersion maps via ray tracing and compare with ALMA observations**: Orient the N=128k torus at inclination angle alpha, divide the sky plane into 30x30 cells matching ALMA resolution, trace 100x100 parallel rays per cell onto optically thick spherical clouds, and average line-of-sight velocities per cell.  
  > "Since we want to use our model velocity and velocity dispersion maps to interpret the ALMA observations of NGC 1068, we have first rescaled our model maps to the observational maps of (cite: Imanishi2018) (their figure 2) and divided the common area into $30 \times 30$ cells to match the resolution." (Velocity and velocity dispersion maps); "Then we send $100\times100$ parallel rays to each cell from an observer to the clumpy structure." (Velocity and velocity dispersion maps)
   - parameter: N = 128k clouds; grid = 30 x 30 cells; 100 x 100 rays per cell; relative cloud radii epsilon_cl = 0.01, 0.025; inclination angles alpha = 30 deg, 45 deg, 60 deg, 90 deg; scale factor R = 3.5 pc (NGC 1068), R = 10 pc (NGC 1672), R = 8 pc (NGC 1326)  
  > "We use the result of our $N$-body simulations for $N$=128k clouds in correspondence with the previous estimation of the obscuration condition (cite: Nenkova2008b; Bannikova2012)." (Velocity and velocity dispersion maps); "In our maps, 3 pc correspond to 3 cells owing to a scale factor $R=3.5$ pc chosen to match the observational velocity map in (cite: Imanishi2018) (fig.[11](#fig:map_01))." (The velocity dispersion map and the mass of SMBH in NGC 1068); "The major radii of the tori were taken from the ALMA observational maps: $R=10$ pc for NGC 1672 and $R=8$ pc for NGC 1326." (NGC 1326 and NGC 1672 velocity dispersion maps)
   - assumption: Clouds are optically thick spheres (if a ray hits a cloud, it does not pass through it).  
  > "The clouds are considered to have high optical depth, so that if a ray hits a cloud, it does not go through it (fig. [10](#fig:SketchRaytracing))." (Velocity and velocity dispersion maps)
   - fitting: Mean velocity in rows of cells at 3 pc (3 cells) on left and right sides of the SMBH matched to v_obs = 20 km/s for NGC 1068; parameter grid search for qualitative visual match to ALMA velocity dispersion maps of NGC 1326 and NGC 1672.  
  > "To obtain the analogue of the observational velocity we find the mean value of the velocity for rows of cells at the left and at the right sides of the SMBH position located at a distance of 3 pc on a velocity map for a given inclination angle $\alpha$." (The velocity dispersion map and the mass of SMBH in NGC 1068); "We produced a set of velocity dispersion maps for different combinations of parameters with the purpose of finding the best coincidence with the observational maps." (NGC 1326 and NGC 1672 velocity dispersion maps)
   - validation: Tested alternative scenarios (power-law increase of cloud radii with distance, and non-equilibrium initial state) via ray tracing to check if they produce velocity dispersion anisotropy.  
  > "In order to check the above scenarios, we repeated the ray tracing experiments assuming a power law increase of the cloud radii with the distance to the SMBH." (The velocity dispersion map and the mass of SMBH in NGC 1068)
4. **Derive cloud temperatures and construct temperature distribution maps for NGC 1068**: Calculate equilibrium blackbody cloud temperatures heated by an anisotropically emitting Shakura-Sunyaev accretion disk using ray tracing from the center, then project onto a 100x100 cell observer grid via line-of-sight ray tracing.  
  > "We send the rays from the accretion disk over the whole range of steradians with a step that is equal to the angular size of a cloud at 3 pc distance." (Temperature of clouds in the torus); "For this reason, the next step is to divide the image into $100\times100$ cells and each cell gets the value of the mean temperature within it." (Temperature of clouds in the torus)
   - parameter: Accretion rate M_dot = 0.2 M_sun/year (from L_bol = 5.65 x 10^44 erg/s); image grid = 100 x 100 cells; epsilon_cl = 0.01 and 0.025; theta = 45 deg  
  > "Taking into account ([\[eq10.9\]](#eq10.9)), we obtain the accretion rate in NGC 1068 to be $\dot{M} \approx 0.2 M_\odot$/year." (Temperature of clouds in the torus); "Fig.[18](#fig:temp_maps_01) and [19](#fig:temp_maps_025) show the temperature distribution maps for a single cloud radius $\varepsilon_{\rm cl} = 0.01$ and $\varepsilon_{\rm cl} = 0.025$ respectively, for the initial half-opening angle of the wind $\theta=45^\circ$." (Temperature of clouds in the torus)
   - assumption: Standard geometrically thin, optically thick accretion disk; spherical clouds in thermodynamic equilibrium with disk radiation absorbed over half their surface; anisotropic disk flux F(theta) = (1/3) cos(theta)(1 + 2 cos(theta)); optically thick clouds with no internal radiative transfer between clouds.  
  > "Assume that the clouds are in thermodynamic equilibrium with the accretion disk. Within the framework of a standard geometrically thin and optically thick accretion disk, the energy flux emitted by the disk surface has the form (cite: Shakura1973):" (Temperature of clouds in the torus); "To take it into account in our model, we use an angular dependence for the flux (cite: Phillips1986; Netzer1987) for the semi-infinite scattering atmosphere:" (Temperature of clouds in the torus)
   - fitting: _not stated_
   - validation: Compared derived cloud temperatures and hot-region morphology with VLTI/MIDI mid-infrared observations of NGC 1068.  
  > "So, for the given accretion rate and torus scales, the temperature satisfies the observational values (cite: Jaffe2004; Raban2009)." (Temperature of clouds in the torus)

## Software

- **phi-GPU** : Direct N-body simulations of the self-gravitating clumpy torus using high-order Hermite integration and block time steps on GPUs.  
  > "At variance with our previous work, where we used the Euler integrator for the numerical solution of the equations of motion, here we adopt a more precise algorithm, namely the $\varphi-$GPU code." (\varphi-GPU code); "The current version of the $\varphi-$GPU [^3] code uses a native GPU support and direct code access to the GPU using the NVIDIA native CUDA library." (\varphi-GPU code)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMBH mass in NGC 1068 (M_smbh) | 5e6 | not stated | M_odot | 3 | By comparing the model with the observational maps of NGC 1068 we find that the SMBH mass is $M_\text{smbh}=5\times 10^6 M_\odot$ for the range of the torus inclination angles $45^\circ - 60^\circ$.; As it can be seen from the Table [1](#tab:1068mass), the observational velocity $v_{obs} = 20$ km s$^{-1}$ for a SMBH mass $M_\text{smbh} = 5 \times 10^6 M_\odot$ is satisfied for the range of the torus inclination angles $\alpha=45^\circ - 60^\circ$ for the relative radius of the clouds $\varepsilon_{\rm cl} = 0.025$, which corresponds to $R_{\rm cl} \approx 0.1$ pc |
| Torus inclination angle in NGC 1068 (alpha) | 45 - 60 | not stated | deg | 3 | By comparing the model with the observational maps of NGC 1068 we find that the SMBH mass is $M_\text{smbh}=5\times 10^6 M_\odot$ for the range of the torus inclination angles $45^\circ - 60^\circ$. |
| Cloud radius in NGC 1068 (R_cl) | 0.1 | not stated | pc | 3 | As it can be seen from the Table [1](#tab:1068mass), the observational velocity $v_{obs} = 20$ km s$^{-1}$ for a SMBH mass $M_\text{smbh} = 5 \times 10^6 M_\odot$ is satisfied for the range of the torus inclination angles $\alpha=45^\circ - 60^\circ$ for the relative radius of the clouds $\varepsilon_{\rm cl} = 0.025$, which corresponds to $R_{\rm cl} \approx 0.1$ pc |
| SMBH mass in NGC 1672 (M_smbh) | 1e8 | not stated | M_odot | 3 | The best combinations of the parameters are the following; for NGC 1672, the SMBH mass $M_\text{smbh} = 1 \times 10^8 M_\odot$; the inclination angle of the torus $\alpha = 60^\circ$, with the relative cloud radius $\varepsilon_{\rm cl} =0.01$ or $\alpha = 45^\circ$ with $\varepsilon_{\rm cl} =0.025$ |
| SMBH mass in NGC 1326 (M_smbh) | 1.5e7 | not stated | M_odot | 3 | for NGC 1326, $M_\text{smbh} = 1.5 \times 10^7 M_\odot$; $\alpha = 60^\circ$ with $\varepsilon_{\rm cl} =0.01$ or $\alpha = 45^\circ$ with $\varepsilon_{\rm cl} =0.025$. |
| Accretion rate in NGC 1068 (M_dot) | 0.2 | not stated | M_odot/year | 4 | Taking into account ([\[eq10.9\]](#eq10.9)), we obtain the accretion rate in NGC 1068 to be $\dot{M} \approx 0.2 M_\odot$/year. |
| Maximum equilibrium cloud temperature at torus throat in NGC 1068 (T_cl^max) | 820 | not stated | K | 4 | For the accretion rate $\dot{M}=0.2 M_\odot/$ year, the equilibrium temperature has a maximum value $T_{\rm cl}^{\rm max} \simeq 820$ K at the inner edge (throat) of the torus with $r_{\rm min} \simeq 0.4$ pc; and a minimal value $T_{\rm cl}^{\rm min} \simeq 300$ K in the torus body region with $r_{\rm max} \simeq 3$ pc. |
| Minimum equilibrium cloud temperature in torus body in NGC 1068 (T_cl^min) | 300 | not stated | K | 4 | For the accretion rate $\dot{M}=0.2 M_\odot/$ year, the equilibrium temperature has a maximum value $T_{\rm cl}^{\rm max} \simeq 820$ K at the inner edge (throat) of the torus with $r_{\rm min} \simeq 0.4$ pc; and a minimal value $T_{\rm cl}^{\rm min} \simeq 300$ K in the torus body region with $r_{\rm max} \simeq 3$ pc. |
| Period of z-coordinate box-orbit oscillation | 100 | not stated | orbital periods | 2 | Indeed, fig. [9](#fig:box-orbit) (*bottom, left*) demonstrates the oscillation of the $z$-coordinate with a period approximately equal to 100 orbital periods. |

## Qualitative findings

- A self-gravitating system of clouds with random initial eccentricities and inclinations cut off by polar wind cones evolves into a stable, geometrically thick doughnut-shaped torus with a Gaussian vertical distribution and log-normal radial distribution.  
  > "Fig. [7](#fig:histog) demonstrates that in the equilibrium state the cloud distribution is Gaussian along the $z$-axis." (Results of N-body simulations); "There is instead an asymmetry along the radial direction which reflects the fact that in the equilibrium state the torus cross-section differs from circular; here the density distribution of clouds is best fitted by a log-normal law." (Results of N-body simulations)
- Oscillations of the torus cross-section along the z-axis are explained by box-orbits in the smooth axisymmetric gravitational potential of an elliptical torus.  
  > "On the basis of a new expression of the gravitational potential of the torus with an elliptical cross-section, it is shown that these oscillations are related to box-orbits in a smooth torus potential." (Conclusions)
- Velocity dispersion anisotropy observed by ALMA in NGC 1068 cannot be produced by random cloud size distributions or non-equilibrium torus states, supporting external accretion onto the torus.  
  > "Velocity and velocity dispersion maps for different sizes of clouds in the torus have not shown any anisotropy. This fact supports the idea that anisortopy is related to an external accretion." (Conclusions)
- Central peaks in ALMA velocity dispersion maps of NGC 1326 and NGC 1672 correspond to emission from fast-moving clouds in the visible throat of the torus.  
  > "We also construct the velocity dispersion maps for NGC 1326 and NGC 1672. They show that the peaks in the ALMA dispersion maps are related to the emission of the torus throat." (Abstract)

## Claim tuples

- H: Randomly inclined and eccentric cloud orbits around a SMBH with polar wind cones will self-gravitate into a stable, geometrically thick toroidal structure required by the AGN unified scheme. | E: Direct N-body simulations of up to N=128k clouds using the phi-GPU code evolved for 1000 orbital periods. | R: The vertical size increases during the first period and saturates into a stable thick cross-section with a Gaussian vertical distribution and log-normal radial distribution. | F: Existence of polar winds is sufficient for self-gravity to form and maintain a stable geometrically thick clumpy torus. | **supported**
- H: Persistent vertical oscillations of the central torus cross-section are caused by box-orbits in the smooth gravitational potential of the dense torus core. | E: Derived the analytical potential of a torus with an elliptical cross-section, fitted a 4th-order power series to the inner potential, and integrated a 3D test-particle trajectory. | R: The particle trajectory forms a concave box orbit whose z-coordinate oscillates with a period of approximately 100 orbital periods, matching the N-body cross-section oscillations. | F: Oscillations of the torus cross-section sizes are related to box-orbits in the smooth component of the torus gravitational potential. | **supported**
- H: Accounting for sub-Keplerian motion of outer torus clouds and optical depth obscuration yields a higher, more realistic SMBH mass for NGC 1068 than the transparent Keplerian approximation (9 x 10^5 M_sun). | E: Ray-tracing simulations of the N=128k torus matched to ALMA resolution to measure the visible velocity at 3 pc as a function of cloud radius and torus inclination. | R: The observed velocity v_obs = 20 km s^-1 at 3 pc is reproduced for M_smbh = 5 x 10^6 M_sun at inclinations alpha = 45 - 60 deg and cloud radius epsilon_cl = 0.025 (R_cl ~ 0.1 pc). | F: Taking torus self-gravity, projection, and cloud obscuration into account yields M_smbh = 5 x 10^6 M_sun for NGC 1068. | **supported**
- H: Anisotropy in the ALMA velocity dispersion map of NGC 1068 could be caused by random distributions of cloud sizes or a non-equilibrium torus state rather than external accretion. | E: Repeated ray-tracing experiments assuming a power-law increase of cloud radii with distance from the SMBH and for a non-equilibrium torus state. | R: Both sets of ray-tracing experiments produced symmetrical velocity dispersion maps without anisotropy. | F: Random cloud size variations and non-equilibrium states are ruled out as causes of the dispersion anisotropy, reinforcing external accretion onto the torus. | **refuted**
- H: Central peaks in the ALMA velocity dispersion maps of Seyfert galaxies (NGC 1326 and NGC 1672) and high-temperature regions in VLTI/MIDI maps of NGC 1068 originate from the visible inner throat of the clumpy torus. | E: Constructed ray-traced velocity dispersion maps for NGC 1326 and NGC 1672 and blackbody temperature distribution maps for NGC 1068 across cloud radii and inclinations. | R: Model dispersion maps reproduce central maxima when the torus throat is unobscured, and model temperature maps show hot (500-800 K) inner throat emission consistent with VLTI/MIDI morphology. | F: Peaks in ALMA velocity dispersion maps and the high-temperature MIR component are related to the torus throat. | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Direct N-body simulations with the high-order Hermite phi-GPU code are needed to self-consistently evolve up to 10^5 self-gravitating clouds (required for AGN obscuration) with high energy conservation, and ray tracing is needed to account for optical depth obscuration of inner clouds by outer clouds along the line of sight.  
  > "Since it is the result of the prolonged gravitational interactions of each cloud with all the others as well as with the central SMBH, in order to build a consistent model we need to use the results of $N$-body simulations." (Introduction); "At variance with our previous work, where we used the Euler integrator for the numerical solution of the equations of motion, here we adopt a more precise algorithm, namely the $\varphi-$GPU code." (\varphi-GPU code); "To take into account all these factors, we make use of the a ray tracing algorithm in the following way." (Velocity and velocity dispersion maps)
- Alternative: Keplerian torus initial conditions (considered in previous work Bannikova et al. 2012, where the cross-section spread out rather than reaching the vertically stretched equilibrium found here).  
  > "This behaviour differs from the case where the initial condition is a Keplerian torus (cite: Bannikova2012) since there the cross-section was spreading out." (Results of N-body simulations)
- Alternative: Power-law increase of cloud radii with distance or non-equilibrium torus state as explanations for velocity dispersion anisotropy in NGC 1068 (rejected because ray-tracing models remained symmetrical).  
  > "In order to check the above scenarios, we repeated the ray tracing experiments assuming a power law increase of the cloud radii with the distance to the SMBH." (The velocity dispersion map and the mass of SMBH in NGC 1068); "Again our results did not show any anisotropy. A non-equilibrium state of the torus also leads to a symmetrical shape of the resulting velocity dispersion maps." (The velocity dispersion map and the mass of SMBH in NGC 1068)
- How they decided it was enough: Selected N up to 128k to match the ~10^5 clouds required by radiative transfer SED models for obscuration, and chose integration parameter tau = 0.01 by testing 6 values on an N=8k model to balance computational speed and total energy drift.  
  > "From the comparison of the radiation transfer model and the observational SEDs of Sy galaxies in the MIR band, (cite: Nenkova2008b) concluded that the total number of clouds in the dusty torus must be around $10^5$." (Initial conditions); "After the total energy check, we see that the optimal $\tau$ parameter (speed vs. accuracy) is around 0.01." (Results of N-body simulations)
- Limitation (authors): The torus-to-SMBH mass ratio is fixed to M_torus/M_smbh = 0.02 rather than varied as a free parameter.  
  > "Actually, the ratio $M_{\text{torus}}/M_{\text{smbh}}$ should be a free parameter." (Initial conditions)
- Limitation (authors): Simulations assume a dissipationless system and neglect cloud collisions and tidal shearing/merging.  
  > "These oscillations have been derived under the assumption that the system is dissipationless. Were collisions included in the simulation, the result might be different." (Results of N-body simulations)
- Limitation (authors): Radiation pressure on cloud dynamics near the accretion disk is neglected.  
  > "Obviously, the dynamics of clouds located near the accretion disk can be also influenced by the radiation pressure (cite: Plewa2013; Venanzi2020). However we neglect here this effect, leaving its investigation to a future paper." (Box-orbits as an explanation for the oscillations of the torus cross-section sizes)
- Limitation (authors): Temperature distribution model uses a simple blackbody equilibrium approximation and neglects radiative transfer in a dusty medium within the torus.  
  > "As a result, we attribute to all the clouds some temperature that either depends on their distances to the SMBH or is just a background value (since we do not consider radiation transfer within the torus)." (Temperature of clouds in the torus); "To derive a temperature distribution that better corresponds to the observational data, one needs to model the SEDs taking into account the radiation transfer in a dusty medium." (Temperature of clouds in the torus)
- Caveat (inferred, ours): Comparisons to ALMA velocity and velocity dispersion maps of NGC 1068, NGC 1326, and NGC 1672 are performed visually/qualitatively or via simple single-radius velocity matching rather than quantitative 3D radiative transfer and interferometric visibility fitting.
- Caveat (inferred, ours): All clouds in the N-body simulation are assumed to have identical mass and constant radius, neglecting a realistic clump mass/size spectrum and gas dynamics (hydrodynamics, cloud destruction/formation).
- Caveat (inferred, ours): Line excitation and molecular abundance variations (e.g., HCN(3-2) vs CO(3-2) optical depth and critical density effects) are not modeled; clouds are treated as simple opaque geometrical spheres.

## Reproducibility

- Data public (paper): Simulation data and codes available upon request from the corresponding author; phi-GPU code available via FTP link.  
  > "Simulation data and codes used in this paper can be made available upon request by emailing the corresponding author." (Data availability); "`ftp://ftp.mao.kiev.ua/pub/berczik/phi-GPU/`" (Footnotes)
- Products in archive: _not stated_
- Code: phi-GPU code publicly available at ftp://ftp.mao.kiev.ua/pub/berczik/phi-GPU/; simulation data and custom ray-tracing codes available upon request.  
  > "Simulation data and codes used in this paper can be made available upon request by emailing the corresponding author." (Data availability); "`ftp://ftp.mao.kiev.ua/pub/berczik/phi-GPU/`" (Footnotes)
- Missing: Ray-tracing code implementation for velocity, dispersion, and temperature maps
- Missing: Exact simulation snapshot time used to generate the kinematic and temperature maps
- Missing: Exact order of the Hermite scheme (4th, 6th, or 8th) used in phi-GPU
- Data volume (inferred): A few GB (N-body particle snapshots for N up to 128k over 6400 steps and 30x30 / 100x100 ray-traced 2D maps)
- Score (inferred): 6/5, The physical equations, initial conditions, N-body parameters, and ray-tracing grid setups are clearly described and the N-body code (phi-GPU) URL is given, but custom ray-tracing scripts and simulation outputs are only available on request and no raw ALMA data reduction is performed.
- Rediscovery candidate: no, This is primarily a theoretical/numerical N-body and ray-tracing modeling paper that compares qualitatively against published ALMA moment maps from the literature rather than analyzing ALMA data directly.

## Links

- Method: (cite: HGM2007) (Introduced the j-particle MPI parallelization mode used in phi-GRAPE / phi-GPU.)
- Method: (cite: NM2008) (Earlier CPU serial N-body code (YEBISU) on which phi-GPU is based.)
- Method: (cite: SBZ2012; BSW2013) (Describe the public version and performance of the phi-GPU direct N-body code.)
- Method: (cite: Bannikova2011) (Method for composing the gravitational potential of a torus from infinitely thin rings.)
- Companion: (cite: Bannikova2012; Bannikova2020; Bannikova2015; Bannikova2017) (Earlier papers by the authors developing the AGN wind-cone scenario and smaller-N self-gravitating clumpy torus simulations.)

## Checks

```json
{
 "quotes": 105,
 "quotes_ok": 105,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 10,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.0.00404.S"
 ],
 "obscore_codes_not_in_card": [
  "2015.1.00404.S",
  "2016.1.00296.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 47,
  "rate": 0.505
 },
 "evidence_ok": true
}
```
