# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2018ApJ...860L..13P\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# **Kinematic evidence for an embedded protoplanet in a circumstellar disc**

## Abstract

Discs of gas and dust surrounding young stars are the birthplace of planets. However, the direct detection of protoplanets forming within discs has proved elusive to date. We present the detection of a large, localized deviation from Keplerian velocity in the protoplanetary disc surrounding the young star HD 163296. The observed velocity pattern is consistent with the dynamical effect of a two-Jupiter-mass planet orbiting at a radius $\approx$ 260 au from the star.

# Introduction

![](obs_1channel.pdf)

Direct observations of forming planets in protoplanetary discs is the ultimate goal of disc studies. The disc usually outshines the planet, requiring observations at high contrast and angular resolution. Detections by direct imaging have been reported in several discs: HD 100546 (cite: Quanz2013a; Brittain2014; Quanz2015; Currie2015), LkCa 15 (cite: Kraus2012; Sallum2015), HD 169142 (cite: Quanz2013b; Biller2014; Reggiani2014), and MWC 758 (cite: Reggiani2018). Yet, most of the detections to date have been subsequently challenged (cite: Thalmann2015; Thalmann2016; Rameau2017; Ligi2018). The quest continues.

An alternative approach is to search for indirect signatures imprinted by planets on their host disc. The Atacama Large Millimetre Array (ALMA), and adaptive optics systems have revealed a variety of structures: gaps and rings (cite: ALMA-Partnership2015; Andrews2016; Isella2016a), spirals (cite: Benisty2015; Stolker2016), that could be signposts of planets, but numerous other explanations also exist that do not require planets (cite: Takahashi2014; Flock2015; Gonzalez2015; Loren2015; Zhang2015; Bethune2016). Embedded planets in circumstellar discs will launch spiral waves at Lindblad resonances both inside and outside of their orbit (cite: Ogilvie2002), disturbing the local Keplerian velocity pattern. Hydrodynamic simulations show that the impact on the velocity pattern should be detectable by high spectral resolution ALMA line observations (cite: Perez2015b). Deviations from Keplerian rotation have been detected around circumbinary discs, with streamers at near free-fall velocities (cite: Casassus2015a; Price2018) and radial flows or warps (cite: Walsh2017).

HD 163296 is a $\sim$4.4Myr old Herbig Ae star located at a distance of $101.5
\pm 1.2$ pc from the Sun (cite: Gaia-Collaboration2018). We rescaled all relevant quantities from previous papers based on the new Gaia distance. HD 163296 has a mass of $1.9$ M$_{\odot}$ (cite: Flaherty2015), a luminosity of $25$ L$_{\odot}$ (cite: Natta2004), and an A1Ve spectral type, with effective temperature 9300 K. Observations with the Hubble Space Telescope (HST) revealed a disc in scattered light that extends as far out as 375 au (cite: Grady2000). Interestingly, (cite: Grady2000) inferred the presence of a giant planet at $\approx$ 270 au based on the gap observed in scattered light at that radius. (cite: de-Gregorio-Monsalvo2013) presented ALMA data and showed that the gaseous component of the disc extends to distances of at least R$_\mathrm{out-CO}=$415 au in CO while the continuum is detected only to R$_\mathrm{out-Dust}=$200 au. Higher resolution ALMA imaging revealed a bright inner disc component within the inner $0.\! ''5$, and a spectacular series of three rings at $\approx$ 65 au, 100 au, with a fainter ring at 160 au (cite: Isella2016a).

![](channel_maps.pdf)

In this Letter, we present the detection of a local deviation from the Keplerian velocity pattern found in high spectral resolution ALMA imaging. By comparing with models we find this to be consistent with the presence of a few-Jupiter mass protoplanet in the disc.

# Observations and data reduction

We use archival ALMA data. Observations were performed on 2012 June 9, 11, 22, and July 6 at Band 7 (2011.0.000010.SV), and on 2015 August 5, 8, and 9 at Band 6 (2013.1.00601.S). A complete description of the data was presented in (cite: de-Gregorio-Monsalvo2013) and (cite: Isella2016a). For the Band 7 data, we re-used the maps produced by (cite: de-Gregorio-Monsalvo2013), with a $0.52''
\times 0.38''$ beam at PA=82$^\circ$, and a channel width of 0.11 km s$^{-1}$.

We used casa scripts provided by ALMA to calibrate the Band 6 data. As the data from the night of August 9 showed significantly higher noise and flux levels, we selected only the data from the August 5 and 8 for the analysis. We performed three successive rounds of phase self-calibration, the last with solutions calculated for each individual integration (6s), followed by a phase and amplitude self-calibration. The continuum self-calibration solutions were applied to the CO lines. Imaging was performed at 0.1 km s$^{-1}$ resolution, using Briggs weighting with a robust parameter of -0.5 to obtain a synthesized beam of $0.28'' \times
0.18''$ at PA=-88$^\circ$. We did not subtract the continuum emission in order to avoid underestimating the gas temperature and affecting the apparent morphology of the emission (cite: Weaver2018). At the location of the detected velocity deviation, continuum emission is negligible, and an analysis on continuum-subtracted data would lead to the same results.

# Results and analysis

The disc shows the typical butterfly pattern of discs in Keplerian rotation (cite: de-Gregorio-Monsalvo2013; Rosenfeld2013a). In a given channel, the emission is concentrated along an isovelocity curve, corresponding to the region of the disc where the projected velocity is equal to the channel velocity. The emission from the upper and lower surfaces — above and below the midplane as seen by the observer — and from the near and far sides of these surfaces, is well separated (Fig. [1](#fig:one_channel), and schematic view in Fig. [3](#fig:toy_model)).

In a recent paper (cite: Pinte2018) we showed how to reconstruct the position and velocity of each of the CO layers, for discs at intermediate inclination, by simple geometrical arguments based on the emission in each channel map. HD 163296 displays a similar scale height and velocity profile to the T Tauri star IM Lupi (cite: Pinte2018), with a flared CO emitting surface and decreasing velocities and temperature with radius (C. Pinte et al., in prep.).

Significantly, HD 163296 shows an asymmetry between the southeast and northwest sides of the disc at a cylindrical radius of $\approx$ 260 au, outside of the third dust ring seen in continuum emission. This asymmetry is most evident in channels at a projected velocity of $\approx 6.8 \pm 0.2$ km s$^{-1}$ ($\approx 1$ km s$^{-1}$ from the systemic velocity). Fig. [1](#fig:one_channel) shows the corresponding individual velocity channels. The emission feature — highlighted by the dotted circle — corresponds to a kink in the upper-surface isovelocity curve northwest of the central object at velocities close to ${\rm d}v=+1\,$ km s$^{-1}$. The symmetric channel (${\rm d}v=-1\,$ km s$^{-1}$,) shows a smooth Keplerian profile to the southeast. We detect a similar deformation of the isovelocity curves at the same location in both $^{12}$CO $J=2-1$ and $3-2$ transitions (Fig. [2](#fig:channel_maps)). While it is not as obvious in the Band 7 Early-Science data due to the limited spatial resolution, the deformation of the isovelocity curve is present and could already be seen, with the benefit of hindsight from our Band 6 detection, in (cite: de-Gregorio-Monsalvo2013) and (cite: Rosenfeld2013a). The asymmetry is not detectable in the less abundant isotologues $^{13}$CO and C$^{18}$O, where the emission is more diffuse and fainter because of the lower optical depth.

The deformation of the emission is localised to an area approximately $0.5''$ in size (indicated by the dotted circle in Figures [1](#fig:one_channel) and [2](#fig:channel_maps)) and to channel maps at velocities between 0.8 and 1.2 km s$^{-1}$ from the systemic velocity (top row of Fig. [2](#fig:channel_maps)). This argues for a localised perturbation and excludes an origin from any large-scale structure in the disc.

![](Toy_model.png)

# Models and discussion

The detected asymmetry matches our expectations for a local deviation from Keplerian velocity caused by a massive body embedded in the disc. A local deviation of $\approx$ 0.4 km s$^{-1}$ is enough to reproduce the observed spatial shift (Fig. [1](#fig:one_channel), bottom-right panel). The dotted lines shown in the bottom-right panel delineate what would be $\approx$ 15% deviations in the local velocity field, which is the approximate extent of the deviation from Keplerian rotation. Most significantly, the shape of the deviation in the emission maps is similar to the prediction by (cite: Perez2015b) for the kinematic signatures of an embedded planet, where the wake of the spiral generated by the planet was shown to produce a kink in the emission due to the deviation from the Keplerian rotation around the central star.

The basic feature of the channel maps can be explained with a simple model assuming emission from two infinitely thin emitting surfaces. Figure [3](#fig:toy_model) shows the expected emission arising from such a model, showing the butterfly signature from the disc. Asymmetries of the velocity field, added in an ad hoc manner in the model for illustrative purposes, are evident as small bumps on the line emissions.

To go beyond this simple model and infer the mass of the putative planet, we performed a series of 3D global simulations using the phantom Smoothed Particle Hydrodynamics (SPH) code (cite: Price2017). We adopted the gas disc parameters from (cite: de-Gregorio-Monsalvo2013). We employed gas-only simulations, ignoring the effect of dust, using 1 million SPH particles and a central mass of 1.9 M$_\odot$. The inner radius of the disc in our model was set to 50 au (mainly to speed up the calculations as the inner disc is irrelevant for our present purpose), with an initial outer radius set to 500 au. We set the gas mass between those radii to $10^{-2}$ M$_\odot$, and use an exponentially tapered power-law surface density profile with a critical radius of 100 au, power-law index of $p = -1.0$, and an exponent $\gamma =$ 0.8. The disc aspect ratio was set to 0.08 at 50 au, with a vertically isothermal profile. We set the artificial viscosity in the code in order to obtain an average (cite: ShakuraSunyaev1973) viscosity of $10^{-3}$ (cite: Lodato2010), in agreement with the upper limits found by (cite: Flaherty2015; Flaherty2017).

We embedded a single planet in the disc orbiting at 260 au with a mass of either 1, 2, 3, or 5 M$_{\rm Jup}$. We used sink particles (cite: Bate95) to represent the star and planet. We set the accretion radius of the planet to half of the Hill radius (7.05, 8.85, 10.15 and 12 au, respectively), with an accretion radius of 10 au for the central star. The model surface density is plotted in Fig. [4](#fig:phantom) for the 2 M$_\mathrm{jup}$ planet. We evolved the models for 35 orbits of the planet ($\approx 100,000$ years), which is sufficient to establish the flow pattern around the planet.

![image](splash_2Mj.pdf) ![image](splash_2Mj_v.pdf)

![](mcfost+phantom.pdf)

To compute the temperature and synthetic line maps, we used the mcfost Monte Carlo radiative transfer code (cite: Pinte06; Pinte09), assuming $T_\mathrm{gas} = T_\mathrm{dust}$, and local thermodynamic equilibrium as we are looking at low-$J$ CO lines. The central star was represented by a sphere of radius 2.1 R$_\odot$, radiating isotropically with a Kurucz spectrum at 9,250 K. We used a Voronoi tesselation where each cell corresponds to an SPH particle, avoiding the need to interpolate between the SPH and radiative transfer codes. We set the CO abundance following the prescription in Appendix B of (cite: Pinte2018) to account for freeze-out where T $< 20$ K, as well as photo-dissociation and photo-desorption in locations where the UV radiation is high. We adopted a turbulent velocity of 50 m s$^{-1}$, consistent with the upper limits found by (cite: Flaherty2015) and (cite: Flaherty2017). We assumed a population of astrosilicate (cite: Draine03) grains with sizes ranging from 0.03 to 1000$\mu$m and following a power-law $\mathrm{d}n(a) \propto a^{-3.5}\mathrm{d}a$, a gas-to-dust ratio of 100, and computed the dust optical properties using Mie theory.

Figure [5](#fig:mcfost-phantom) presents the predicted emission in $^{12}$CO $J=2-1$ of our theoretical models for four different planet masses. A 2 M$_\mathrm{jup}$ planet appears to reproduce a deformation of the $^{12}$CO isovelocity curve that is consistent with the observations. At 1 M$_\mathrm{jup}$, the planet only produces a small deformation that is barely visible in the channel maps, while a more massive planet triggers a strong spiral arm that would have been detected in channel maps at least up to 0.5 km s$^{-1}$ from the nominal velocity of 1 km s$^{-1}$. The twisted emission in the channel maps is a direct consequence of deviation from Keplerian velocity generated by the planet along the wake of the spiral arms (Fig. [4](#fig:phantom), right panel). (cite: Perez2015b) also predicted that the circumplanetary disc can be detected as a compact emission separated in velocity from the circumstellar disc emission. The circumplanetary disc radius is about one-third of the Hill radius (cite: Ayliffe2009). A 2–5 Jupiter mass planet would produce a circumplanetary disc with a diameter smaller than 6–8 au, respectively. At the current spatial resolution of the ALMA observations, its flux will be diluted in the beam ($\approx$ 20 au).

Note that for the adopted disc parameters, the planet migrates by about 30 au during the simulation, and the synthetic maps display the velocity deviation slightly closer to the star than in the data. At this rate, the planet would reach the star in about 1 Myr (though we overestimate the migration rate by a factor of 2–3 due to the relatively large sink particle radius that we adopted; see (cite: Ayliffe2010)). If the detection is confirmed, the survival of such an embedded planet could put additional constraints on the disc surface density profile and viscosity.

(cite: Grady2000) detected a gap in the scattered light images with HST/STIS at 260 au, and estimated the mass of a potential planet to be 0.4 M$_\mathrm{jup}$ (based on some simple analytical derivation). (cite: Isella2016a) also detected a small dip in the integrated CO brightness profile at $\approx 2.2$” (see their Figure 1, or Figure 5 in (cite: Liu2018)). In our model, the gap appears in scattered light for a planet mass larger than 2 M$_\mathrm{jup}$, but remains undetected in the synthetic CO maps. The final profile of a planetary gap establishes itself on a viscous timescale however (thousands of orbits with a viscosity of $10^{-3}$), however, and the gap width and depth in our models are only lower limits.

The effect of the planet appears fainter in the $^{13}$CO channels maps than in the $^{12}$CO maps, even if the planet is located in the midplane. This is due to optical depth and vertical temperature gradient effects: the $^{12}$CO is coming from a vertically narrow and warm layer above the midplane, while the $^{13}$CO is originating from a deeper, thicker layer, where the disc is almost vertically isothermal, resulting in a uniform emissivity that washes out some of the kinematics signal.

Are we seeing the signature of an embedded planet? Can we exclude wishful thinking? The strongest evidence is that the perturbation to the disc kinematics is highly localised in both space and velocity. This excludes any mechanism that merely produces axisymmetric rings in discs. This excludes, for example, ice lines (cite: Zhang2015), self-induced dust traps (cite: Gonzalez2015), instabilities (cite: Takahashi2014; Loren2015) and zonal flows (cite: Flock2015). A spiral wave could in principle result from the disc self-gravity, but multiple, large-scale spirals would be expected in that case (cite: Dipierro2015a) which the localized deviation seen in HD 163296 would seem to exclude.

The localised nature of the kinematic perturbation, that it occurs close to the gap found by (cite: Grady2000), and the similarity to the signatures predicted by our hydrodynamic models is a strong evidence for a young protoplanet in a gas-rich disc. However, confirmation with direct imaging is the only way to be sure. The relatively large planet mass and its known location in the disc means direct imaging follow-up might be able to detect it, depending on how embedded it is in disc. So far, no point source has so far been detected at the location of the potential planet with near-IR adaptive optics systems. A 2 M$_\mathrm{Jup}$ planet is consistent with the upper limits (for an unobscured planet) obtained by adaptive optics systems, such as SPHERE (cite: Muro-Arena2018) and Keck L’ (cite: Guidi2018). Using the formalism developed in (cite: Pinte2018), we find that the velocity kink is located at a distance of $\approx$ 260 au, and an elevation above the midplane of $\approx$ 70 au. Assuming that the potential planet is located in the midplane, it would be at a projected distance of 2.3$\pm$0.2" and PA = -3$\pm$5$^\circ$ from the star, where we estimated the uncertainties by locating the velocity deviation with half of a beam accuracy. If the planet orbit is slightly inclined compared to the disc’s plane, the position on the sky will be shifted along a line going from the northeast to the southwest directions.

Can massive planets form at a distance of 250 au from the star? The location of giant planets in the outer regions of discs would be broadly consistent with gravitational instability. On the other hand, the timescale for core accretion may also be reasonable given that HD 163296 is a relatively old disc ($\approx$ 5 Myr). The planet may also have undergone outward migration, depending upon the initial profile of the disc. It is beyond the scope of this Letter to speculate further.

# Summary

We detected a 15% deviation from Keplerian flow around the star in the disc around HD 163296. The deviation was detected in both Band 6 and Band 7 in two different transitions of $^{12}$CO and matches the kinematic signature predicted for an embedded protoplanet.

Comparing the observations to a series of 3D hydrodynamic and radiative transfer models of embedded planets suggests that the kinematic feature is caused by a planet of of $\approx$ 2 M$_{\rm Jup}$ in the midplane. Such a planet would be located at a distance of $\approx$ 260 au.

# Acknowledgments

This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00010.SV and ADS/JAO.­ALMA#2013.1.00601.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work was performed on the ozSTAR national facility at Swinburne University of Technology. ozSTAR is funded by Swinburne and the Australian Government’s Education Investment Fund. We thank the anonymous referee for insightful comments and suggestions. C.P. and D.J.P. acknowledge funding from the Australian Research Council via FT170100040, FT13010003,4 and DP180104235. F.M. and C.P. acknowledge funding from ANR of France (ANR-16-CE31-0013).

# Facilities

ALMA.

# Software

CASA (cite: McMullin07), phantom (cite: Price2017), splash (cite: Price2007), mcfost (cite: Pinte06; Pinte09).

natexlab

(ref: ALMA-Partnership2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: Andrews2016) Andrews, S. M., Wilner, D. J., Zhu, Z., et al. 2016, ApJL, 820, L40, doi: [`10.3847/2041-8205/820/2/L40`](http://doi.org/10.3847/2041-8205/820/2/L40)

(ref: Ayliffe2009) Ayliffe, B. A., & Bate, M. R. 2009, MNRAS, 397, 657, doi: [`10.1111/j.1365-2966.2009.15002.x`](http://doi.org/10.1111/j.1365-2966.2009.15002.x)

(ref: Ayliffe2010) —. 2010, MNRAS, 408, 876, doi: [`10.1111/j.1365-2966.2010.17221.x`](http://doi.org/10.1111/j.1365-2966.2010.17221.x)

(ref: Bate95) Bate, M. R., Bonnell, I. A., & Price, N. M. 1995, MNRAS, 277, 362

(ref: Benisty2015) Benisty, M., Juhasz, A., Boccaletti, A., et al. 2015, A&A, 578, L6

(ref: Bethune2016) Béthune, W., Lesur, G., & Ferreira, J. 2016, A&A, 589, A87

(ref: Biller2014) Biller, B. A., Males, J., Rodigas, T., et al. 2014, ApJL, 792, L22, doi: [`10.1088/2041-8205/792/1/L22`](http://doi.org/10.1088/2041-8205/792/1/L22)

(ref: Brittain2014) Brittain, S. D., Carr, J. S., Najita, J. R., Quanz, S. P., & Meyer, M. R. 2014, ApJ, 791, 136, doi: [`10.1088/0004-637X/791/2/136`](http://doi.org/10.1088/0004-637X/791/2/136)

(ref: Casassus2015a) Casassus, S., Marino, S., Pérez, S., et al. 2015, ApJ, 811, 92

(ref: Currie2015) Currie, T., Cloutier, R., Brittain, S., et al. 2015, ApJL, 814, L27, doi: [`10.1088/2041-8205/814/2/L27`](http://doi.org/10.1088/2041-8205/814/2/L27)

(ref: de-Gregorio-Monsalvo2013) de Gregorio-Monsalvo, I., Ménard, F., Dent, W., et al. 2013, A&A, 557, A133

(ref: Dipierro2015a) Dipierro, G., Pinilla, P., Lodato, G., & Testi, L. 2015, MNRAS, 451, 974, doi: [`10.1093/mnras/stv970`](http://doi.org/10.1093/mnras/stv970)

(ref: Draine03) Draine, B. T. 2003, ApJ, 598, 1017, doi: [`10.1086/379118`](http://doi.org/10.1086/379118)

(ref: Flaherty2015) Flaherty, K. M., Hughes, A. M., Rosenfeld, K. A., et al. 2015, ApJ, 813, 99

(ref: Flaherty2017) Flaherty, K. M., Hughes, A. M., Rose, S. C., et al. 2017, ApJ, 843, 150

(ref: Flock2015) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68, doi: [`10.1051/0004-6361/201424693`](http://doi.org/10.1051/0004-6361/201424693)

(ref: Gaia-Collaboration2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, ArXiv e-prints. [`https://arxiv.org/abs/1804.09365`](https://arxiv.org/abs/1804.09365)

(ref: Gonzalez2015) Gonzalez, J.-F., Laibe, G., Maddison, S. T., Pinte, C., & Ménard, F. 2015, MNRAS, 454, L36, doi: [`10.1093/mnrasl/slv120`](http://doi.org/10.1093/mnrasl/slv120)

(ref: Grady2000) Grady, C. A., Devine, D., Woodgate, B., et al. 2000, ApJ, 544, 895

(ref: Guidi2018) Guidi, G. et al. 2018, submitted

(ref: Isella2016a) Isella, A., Guidi, G., Testi, L., et al. 2016, Physical Review Letters, 117, 251101

(ref: Kraus2012) Kraus, A. L., & Ireland, M. J. 2012, ApJ, 745, 5, doi: [`10.1088/0004-637X/745/1/5`](http://doi.org/10.1088/0004-637X/745/1/5)

(ref: Ligi2018) Ligi, R., Vigan, A., Gratton, R., et al. 2018, MNRAS, 473, 1774, doi: [`10.1093/mnras/stx2318`](http://doi.org/10.1093/mnras/stx2318)

(ref: Liu2018) Liu, S.-F., Jin, S., Li, S., Isella, A., & Li, H. 2018, ArXiv e-prints. [`https://arxiv.org/abs/1803.05437`](https://arxiv.org/abs/1803.05437)

(ref: Lodato2010) Lodato, G., & Price, D. J. 2010, MNRAS, 405, 1212

(ref: Loren2015) Lorén-Aguilar, P., & Bate, M. R. 2015, MNRAS, 453, L78, doi: [`10.1093/mnrasl/slv109`](http://doi.org/10.1093/mnrasl/slv109)

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Muro-Arena2018) Muro-Arena, G. A., Dominik, C., Waters, L. B. F. M., et al. 2018, ArXiv e-prints. [`https://arxiv.org/abs/1802.03328`](https://arxiv.org/abs/1802.03328)

(ref: Natta2004) Natta, A., Testi, L., Neri, R., Shepherd, D. S., & Wilner, D. J. 2004, A&A, 416, 179, doi: [`10.1051/0004-6361:20035620`](http://doi.org/10.1051/0004-6361:20035620)

(ref: Ogilvie2002) Ogilvie, G. I., & Lubow, S. H. 2002, MNRAS, 330, 950, doi: [`10.1046/j.1365-8711.2002.05148.x`](http://doi.org/10.1046/j.1365-8711.2002.05148.x)

(ref: Perez2015b) Perez, S., Dunhill, A., Casassus, S., et al. 2015, ApJL, 811, L5

(ref: Pinte09) Pinte, C., Harries, T. J., Min, M., et al. 2009, A&A, 498, 967, doi: [`10.1051/0004-6361/200811555`](http://doi.org/10.1051/0004-6361/200811555)

(ref: Pinte06) Pinte, C., Ménard, F., Duchêne, G., & Bastien, P. 2006, A&A, 459, 797, doi: [`10.1051/0004-6361:20053275`](http://doi.org/10.1051/0004-6361:20053275)

(ref: Pinte2018) Pinte, C., Ménard, F., Duchêne, G., et al. 2018, A&A, 609, A47

(ref: Price2007) Price, D. J. 2007, PASA, 24, 159

(ref: Price2017) Price, D. J., Wurster, J., Nixon, C., et al. 2017, ArXiv e-prints. [`https://arxiv.org/abs/1702.03930`](https://arxiv.org/abs/1702.03930)

(ref: Price2018) Price, D. J., Cuello, N., Pinte, C., et al. 2018, MNRAS, doi: [`10.1093/mnras/sty647`](http://doi.org/10.1093/mnras/sty647)

(ref: Quanz2015) Quanz, S. P., Amara, A., Meyer, M. R., et al. 2015, ApJ, 807, 64, doi: [`10.1088/0004-637X/807/1/64`](http://doi.org/10.1088/0004-637X/807/1/64)

(ref: Quanz2013a) —. 2013a, ApJL, 766, L1, doi: [`10.1088/2041-8205/766/1/L1`](http://doi.org/10.1088/2041-8205/766/1/L1)

(ref: Quanz2013b) Quanz, S. P., Avenhaus, H., Buenzli, E., et al. 2013b, ApJL, 766, L2, doi: [`10.1088/2041-8205/766/1/L2`](http://doi.org/10.1088/2041-8205/766/1/L2)

(ref: Rameau2017) Rameau, J., Follette, K. B., Pueyo, L., et al. 2017, AJ, 153, 244, doi: [`10.3847/1538-3881/aa6cae`](http://doi.org/10.3847/1538-3881/aa6cae)

(ref: Reggiani2014) Reggiani, M., Quanz, S. P., Meyer, M. R., et al. 2014, ApJL, 792, L23, doi: [`10.1088/2041-8205/792/1/L23`](http://doi.org/10.1088/2041-8205/792/1/L23)

(ref: Reggiani2018) Reggiani, M., Christiaens, V., Absil, O., et al. 2018, A&A, 611, A74, doi: [`10.1051/0004-6361/201732016`](http://doi.org/10.1051/0004-6361/201732016)

(ref: Rosenfeld2013a) Rosenfeld, K. A., Andrews, S. M., Hughes, A. M., Wilner, D. J., & Qi, C. 2013, ApJ, 774, 16

(ref: Sallum2015) Sallum, S., Follette, K. B., Eisner, J. A., et al. 2015, Nature, 527, 342, doi: [`10.1038/nature15761`](http://doi.org/10.1038/nature15761)

(ref: ShakuraSunyaev1973) Shakura, N. I., & Sunyaev, R. A. 1973, A&A, 24, 337

(ref: Stolker2016) Stolker, T., Dominik, C., Avenhaus, H., et al. 2016, ArXiv e-prints

(ref: Takahashi2014) Takahashi, S. Z., & Inutsuka, S.-i. 2014, ApJ, 794, 55, doi: [`10.1088/0004-637X/794/1/55`](http://doi.org/10.1088/0004-637X/794/1/55)

(ref: Thalmann2015) Thalmann, C., Mulders, G. D., Janson, M., et al. 2015, ApJL, 808, L41, doi: [`10.1088/2041-8205/808/2/L41`](http://doi.org/10.1088/2041-8205/808/2/L41)

(ref: Thalmann2016) Thalmann, C., Janson, M., Garufi, A., et al. 2016, ApJL, 828, L17, doi: [`10.3847/2041-8205/828/2/L17`](http://doi.org/10.3847/2041-8205/828/2/L17)

(ref: Walsh2017) Walsh, C., Daley, C., Facchini, S., & Juhász, A. 2017, A&A, 607, A114, doi: [`10.1051/0004-6361/201731334`](http://doi.org/10.1051/0004-6361/201731334)

(ref: Weaver2018) Weaver, E., Isella, A., & Boehler, Y. 2018, ApJ, 853, 113, doi: [`10.3847/1538-4357/aaa481`](http://doi.org/10.3847/1538-4357/aaa481)

(ref: Zhang2015) Zhang, K., Blake, G. A., & Bergin, E. A. 2015, ApJL, 806, L7, doi: [`10.1088/2041-8205/806/1/L7`](http://doi.org/10.1088/2041-8205/806/1/L7)

</paper>

## Items to check

```json
[
 {
  "path": "reasoning.limitations_admitted[1].evidence[0]",
  "value": "Migration rate overestimated by a factor of 2-3 and gap widths and depths are only lower limits",
  "failed_quote": "we overestimate the migration rate by a factor of 2–5 due to the relatively large sink particle radius"
 }
]
```
