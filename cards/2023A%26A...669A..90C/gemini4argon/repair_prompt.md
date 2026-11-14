# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...669A..90C\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Magnetically regulated collapse in the B335 protostar?\
II. Observational constraints on gas ionization and magnetic field coupling

Whether or not magnetic fields play a key role in dynamically shaping the products of the star formation process is still largely debated. For example, in magnetized protostellar formation models, magnetic braking plays a major role in the regulation of the angular momentum transported from large envelope scales to the inner envelope, and is expected to be responsible for the resulting protostellar disk sizes. However, non-ideal magnetohydrodynamic effects that rule the coupling of the magnetic field to the gas also depend heavily on the local physical conditions, such as the ionization fraction of the gas. The purpose of this work is to observationally characterize the level of ionization of the gas at small envelope radii and to investigate its relation to the efficiency of the coupling between the star-forming gas and the magnetic field in the Class 0 protostar B335. We obtained molecular line emission maps of B335 with ALMA, which we use to measure the deuteration fraction of the gas, $R_{\rm D}$, its ionization fraction, $\chi_{\rm e}$, and the cosmic-ray ionization rate, $\zeta_{\rm CR}$, at envelope radii $\lesssim$1000 au. We find large fractions of ionized gas, $\chi_{\rm e}$ $\simeq 1-8 \times 10^{-6}$. Our observations also reveal an enhanced ionization that increases at small envelope radii, reaching values up to $\zeta_{\rm CR}$ $\simeq 10^{-14}$ s$^{-1}$ at a few hundred astronomical units (au) from the central protostellar object. We show that this extreme $\zeta_{\rm CR}$ can be attributed to the presence of cosmic rays accelerated close to the protostar. We report the first resolved map of $\zeta_{\rm CR}$ at scales $\lesssim 1000$ au in a solar-type Class 0 protostar, finding remarkably high values. Our observations suggest that local acceleration of cosmic rays, and not the penetration of interstellar Galactic cosmic rays, may be responsible for the gas ionization in the inner envelope, potentially down to disk-forming scales. If confirmed, our findings imply that protostellar disk properties may also be determined by local processes that set the coupling between the gas and the magnetic field, and not only by the amount of angular momentum available at large envelope scales and the magnetic field strength in protostellar cores. We stress that the gas ionization we find in B335 significantly stands out from the typical values routinely used in state-of-the-art models of protostellar formation and evolution. If the local processes of ionization uncovered in B335 are prototypical to low-mass protostars, our results call for a revision of the treatment of ionizing processes in magnetized models for star and disk formation.

# Introduction

Observational studies have shown that magnetic fields are present at all scales where star formation processes are at work, permeating molecular clouds, prestellar cores, and protostellar envelopes (cite: Girart2006; Alves2014; Zhang2014; Soler2019). While magnetized models of star formation were developed early on, it is only recently that complex physics has been included in numerical magnetohydrodynamic (MHD) models, and that the predictions of dedicated models are directly compared to observations of star-forming regions. One of the major achievements of magnetized models is the prediction of the small sizes of protostellar disks, regulated by magnetic braking (cite: Dapp2012; Hennebelle2019; Zhao2020a). Recent observations have indeed shown that disks are compact, and are almost an order of magnitude smaller than those produced in purely hydrodynamical models (cite: Maury2019; Lebreuilly2021).

In magnetized collapse models, non-ideal MHD effects play a major role in the regulation of magnetic flux during the early stages of protostellar formation (cite: Machida2011; Li2011; Marchand2020). Hence, these processes indirectly limit the angular momentum transported by the magnetic field from large envelope scales to the inner envelope, and set the resulting disk size. However, these resistive processes depend heavily on the local physical conditions, such as dust grain properties (electric charge and size), gas density and temperature, density of ions and electrons, and the cosmic-ray (CR) ionization rate, $\zeta_{\rm CR}$ (cite: Zhao2020a). Observationally, only very few measurements of these quantities have been obtained toward solar-type protostars: the effective coupling of magnetic fields to the infalling-rotating material, at scales where the circumstellar material feeds the growth in mass of the protostellar embryo and its disk, is therefore still largely unknown.

B335, located at a distance of 164.5 pc (cite: Watson2020), is an isolated Bok Globule which contains an embedded Class 0 protostar (cite: Keene1983). The core is associated with an east–west outflow that is prominently detected in CO, with an inclination of 10$^\circ$ on the plane of the sky and an opening angle of 45$^\circ$ (cite: Hirano1988; Hirano1992; Stutz2008; Yen2010). Its isolation and relative proximity makes B335 an ideal object with which to test models of star formation. Asymmetric double-peaked line profiles observed in the molecular emission of the gas toward the envelope have been interpreted as optically thick lines tracing infalling motions, and have been extensively used to derive mass-infall rates from 10$^{-7}$ to $\sim$3$\times$10$^{-6}$ $M_\odot$ yr$^{-1}$ at radii of 100-2000 au (cite: Zhou1993; Yen2010; Evans2015). However, new observations of optically thin emission from less abundant molecules reveal the presence of two velocity components tracing asymmetric motions at these envelope scales, which could contribute significantly to the double-peaked line profiles (cite: Cabedo2021b). These results suggest that simple spherically symmetric infall models might not be adequate to describe the collapse of the B335 envelope, and tentatively unveil the existence of preferential accretion streamlines along outflow cavity walls.

B335 is also an excellent prototype for the study of magnetized star-formation models, because it has been proposed as an example of a protostar where the disk size is set by a magnetically regulated collapse (cite: Maury2018). This hypothesis rests mainly on two observations. First, the rotation of the gas observed at large envelope radii is not found at small envelope radii ($<$ 1000 au) and no kinematic signature of a disk was reported down to $\sim$ 10 au (cite: Kurono2013; Yen2015b). Second, observations of polarized dust emission have revealed an "hourglass" magnetic field morphology (Paper I) in the inner envelope: comparisons to MHD models of protostellar formation (cite: Masson2016; Hennebelle2020) suggest that the B335 envelope is threaded by a rather strong magnetic field which is highly coupled to the infalling-rotating gas, preventing disk growth out to large radii. The purpose of the analysis presented here is to characterize the level of ionization and its origin in order to test the model scenario proposed in Paper I, and put observational constraints on the efficiency of the coupling of the magnetic field to the star-forming gas in the inner envelope of B335.

In Sect. [2](#sec:Observations), we present the ALMA observations used to constrain physical and chemical properties of the gas at envelope radii $\lesssim$ 1000 au. In Sect. [3](#sec:deutFrac) we derive the deuteration fraction, $R_{\rm D}$, from DCO$^{+}$ (J=3-2) and H$^{13}$CO$^+$ (J=3-2). In Sect. [4](#sec:IonFrac) we compute the ionization fraction, $\chi_{\rm e}$, and the $\zeta_{\rm CR}$. Finally, in Sect. [5](#sec:Discussion), we discuss our results concerning deuteration processes, the ionization, the possible influence of a local source of radiation and its effect on the coupling between the gas and the magnetic field.

# Observations and data reduction

Observations of the Class 0 protostellar object B335 were carried out with the ALMA interferometer during the Cycle 4 observation period, from October 2016 to September 2017, as part of the 2016.1.01552.S project. The centroid position of B335 is assumed to be $\alpha =$ 19:37:00.9 and $\delta =$ +07:34:09.6 (in J2000 coordinates) based on the dust continuum peak obtained by (cite: Maury2018).

We used DCO$^{+}$ (J=3-2) and H$^{13}$CO$^+$ (J=3-2) to obtain $R_{\rm D}$ and $\chi_{\rm e}$. We used H$^{13}$CO$^+$ (J=1-0) and C$^{17}$O (J=1-0) to derive the hydrogenation fraction, $R_{\rm H}$. Additionally, we observed the dust continuum at 110 GHz to derive the estimated line opacities, CO depletion factor, $f_{\rm D}$, and $\zeta_{\rm CR}$. We also targeted $^{12}$CO (J=2-1) and N$_{2}$D$^{+}$ (J=3-2) for comparison purposes. All lines were targeted using a combination of ALMA configurations to recover the largest length-scale range possible. As our data for H$^{13}$CO$^+$ (J=3-2) only include observations with the Atacama Compact Array (ACA), we used additional observations of this molecular line at smaller scales from the ALMA project 2015.1.01188.S. Technical details of the ALMA observations are shown in Appendix [7](#sec:ap_ObsDetails).

Calibration of the raw data was done using the standard script for Cycle 4 ALMA data and the Common Astronomy Software Applications (CASA), version 5.6.1-8. The continuum emission was self-calibrated with CASA. Line emission from $^{12}$CO (J=2-1) and N$_{2}$D$^{+}$ (J=3-2) was additionally calibrated using the self-calibrated continuum model at the appropriate frequency (231 GHz, not shown in this work).

Final images of the data were generated from the calibrated visibilities using the tCLEAN algorithm within CASA, using Briggs weighting with a robust parameter of 1 for all the tracers. As we want to compare our data to the C$^{17}$O (J=1-0) emission presented in (cite: Cabedo2021b), we adjust our imaging parameters to obtain matching beam maps with similar angular and spectral resolution. For DCO$^{+}$ (J=3-2) and H$^{13}$CO$^+$ (J=3-2), we restricted the baselines to a common "u,v" range between 9 and 140 $k\lambda$, and finally smoothed them to the same angular resolution. The preliminary analysis shows that both C$^{17}$O (J=1-0) and H$^{13}$CO$^+$ (J=1-0) emission is barely detected in the most extended configurations. We proceed by applying a common "uv tapering" of 1.5 $''$ to both lines. This procedure allows to decrease the weighting of the largest baselines in our analysis, giving more weight to the smaller baselines and allowing us to obtain a better signal-to-noise ratio (S/N). Furthermore, we smoothed the data to obtain exactly the same angular resolution. Additionally, we smooth C$^{17}$O (J=1-0) and the dust continuum at 110 GHz to obtain DCO$^{+}$ matching beam maps to compute $f_{\rm D}$. The imaging parameters used to obtain all the spectral cubes and their final characteristics are shown in Table [\[table:ImageChar\]](#table:ImageChar). Even though the characteristics and properties of the C$^{17}$O (J=1-0) maps are slightly different from the ones presented in (cite: Cabedo2021b) due to the differences in the imaging process, the line profiles show the same characteristics (i.e., line profiles are double-peaked and present the same velocity pattern at different offsets from the center of the source) confirming that the imaging process has no large effect on the shape of the line profile, and that the two velocity components can still be observed.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | DCO$^{+}$  | H$^{13}$CO$^+$  | $^{12}$CO  | N$_{2}$D$^{+}$  | H$^{13}$CO$^+$  | C$^{17}$O\*\* | cont. |  |  |
|  | (J=3-2) | (J=3-2) | (J=2-1) | (J=3-2) | (J=1-0) | (J=1-0) |  |  |  |
|  |  |  |  |  |  |  |  |  |  |
| Rest. Freq. (GHz) | 216.112 | 260.255 | 230.538 | 231.321 | 86.754 | 112.359 | 110 |  |  |
| $\Theta_{\rm LRS}$\* (arcsec) | 11.3 | 16.0 | 10.6 | 10.6 |  |  | 22.3 |  |  |
| Pixel size (arcsec) | 0.5 | 0.5 | 0.5 | 0.5 | 0.25 | 0.25 | 0.3 |  |  |
| $\Theta_{\rm maj}$ (arcsec) | 1.5 | 1.5 | 1.5 | 1.5 | 2.6 | 2.6 | 0.8 |  |  |
| $\Theta_{\rm min}$ (arcsec) | 1.5 | 1.5 | 1.5 | 1.5 | 2.6 | 2.6 | 0.7 |  |  |
| P.A. () | 0 | 0 | 0 | 0 | 0 | 0 | $-61.5$ |  |  |
| Spectral res. (km s$^{-1}$) | 0.2 | 0.2 | 0.2 | 0.2 | 0.15 | 0.15 | \- |  |  |
| rms (mJy beam$^{-1}$) | 22.37 | 53.15 | 143.5 | 6.00 | 18.58 | 10.57 | 0.065 |  |  |
| vel. range (km s$^{-1}$) | 7.8 - 8.9 | 7.5 - 8.9 | 7.6 - 9.4 | 7.7 - 8.9 | 7.4-9.2 | 4.7-6.5 | \- |  |  |
|  |  |  |  |  |  | 7.7-9.3 |  |  |  |
| rms (mJy beam$^{-1}$ km s$^{-1}$) | 11.17 | 21.28 | 634.6 | 5.23 | 17.17 | 17.58 | \- |  |  |

Largest recoverable scale, computed as $\Theta_{\rm LRS} = 206265(0.6\lambda/b_{\rm min})$ in arcsec, where $\lambda$ is the rest wavelength of the line, and $b_{\rm min}$ is the minimum baseline of the configuration, both in m ((cite: ALMAc4)).

\* The two velocity ranges correspond to the two resolved hyperfine components.

### **Data products**

From the data cubes, we obtained spectral maps that present the spectrum (in velocity units) at each pixel of a determined region around the center of the source. These maps allow us to evaluate the spectra at different offsets from the center of the envelope where the dust continuum emission peak localizes the protostar, and to detect any distinct line profile or velocity pattern. The obtained spectral maps are discussed in Appendix [8.1](#sec:ap_spectralMaps).

We derived the integrated intensity maps by integrating the molecular line emission over the velocity range in which it is emitting (the velocity range used for each molecule is shown in Table [\[table:ImageChar\]](#table:ImageChar)). Figure [1](#fig:intensity_maps) shows the dust continuum emission map at 110 GHz and the integrated intensity contours of C$^{17}$O (J=1-0), DCO$^{+}$ (J=3-2), H$^{13}$CO$^+$ (J=1-0), and H$^{13}$CO$^+$ (J=3-2). The H$^{13}$CO$^+$ (J=1-0) emission clearly appears more spatially extended than the other lines, roughly following most of the dust emission. The emission from this line extends further than the dust toward the southeast outflow cavity wall direction. The C$^{17}$O (J=1-0), DCO$^{+}$ (J=3-2), and H$^{13}$CO$^+$ (J=3-2) emission present a similar, relatively compact morphology centered around the dust peak and elongated along the north–south equatorial plane. However, the spatial extent along the equatorial plane is slightly more compact for the H$^{13}$CO$^+$ emission ($\sim$2100 au) than the DCO$^{+}$ emission ($\sim$2500 au), and both are more extended than C$^{17}$O ($\sim$1700 au). The DCO$^{+}$ peak intensity is clearly more displaced from the continuum peak than the H$^{13}$CO$^+$ (J=3-2) peak; this could be a local effect around the protostar due to the large temperature and irradiation conditions, which destroy DCO$^{+}$ (cite: Wootten1987; Butner1995). The C$^{17}$O (J=1-0) emission appears to be slightly extended along the outflow cavities.

![](Images/IntensityImages/c17o_dco_h13co_cont110_titles2.pdf)

As all the molecules present a double-peaked profile with similar velocity patterns to the ones observed in (cite: Cabedo2021b), namely two different velocity components with varying intensity across the source spatial extent, we use two independent velocity components to fit the line profiles simultaneously. Following (cite: Cabedo2021b), we modeled the spectrum at each pixel using the *HfS* fitting program (cite: Estalella2017). We obtained maps of peak velocity and velocity dispersion for each velocity component, deriving the corresponding uncertainties from the $\chi^2$ goodness of fit (cite: Estalella2017). A more detailed discussion of these maps is presented in Appendix [8.2](#sec:ap_LineMod). In addition, an estimate of line opacities is given in Appendix [9](#ssec:Opacity). In the following sections, the statistical uncertainties derived (shown in Figs. [2](#fig:deutFrac_maps), [4](#fig:ionFrac_maps), and [5](#fig:ionRate_maps)) are computed using standard error propagation analysis from the uncertainties of each parameter obtained with the line modeling (peak velocity, velocity dispersion, and opacity). Other systematic uncertainties are discussed separately in the corresponding sections.

# Deuteration fraction

The process of deuteration consists of an enrichment of the amount of deuterium with respect to hydrogen in molecular species. The deuteration fraction, $R_{\rm D}$ = \[D\]/\[H\], in molecular ions, in particular HCO$^{+}$, has been extensively used as an estimator of the degree of ionization in molecular gas (cite: Caselli1998; Fontani2017). Here, we apply this method to obtain maps of $R_{\rm D}$, computed as the column density ratio of DCO$^{+}$ (J=3-2) and its non-deuterated counterpart, H$^{13}$CO$^+$ (J=3-2):

$$\begin{equation}
        R_{\rm D} = \frac{1}{f_{\rm ^{12/13}C}}  
        \frac{N_{\rm DCO^{+}}}{N_{\rm H^{13}CO^{+}}}\,,
        \label{eq:deutFrac_colDens}
    
\end{equation}$$

where $N_{i}$ is the column density of each species and $f_{^{12/13}C}$ is the abundance ratio of $^{12}$C to $^{13}$C. The column density of both species is computed such as:

$$\begin{equation}
        \begin{split}
        N_i = &\frac{8 \pi}{\lambda^{3}A} \frac{1}{J_{\nu}(T_{\rm ex}) - J_{\nu}(T_{\rm bg})}\times \\ & \frac{1}{1-\exp(-h\nu/k_{\rm B}T_{\rm ex})} \frac{Q_{\rm rot}}{g_{u}\exp(-E_{l}/k_{\rm B}T_{\rm ex})}\times \\ & \int{I_{\rm 0} {\rm d} v},
        \end{split}
        \label{eq:colDens}
    
\end{equation}$$

where $\lambda$ is the wavelength of the transition, $A$ is the Einstein coefficient, $J_{v}(T)$ is the Planck function at the background (2.7 K) and at the excitation temperature of the line (assumed to be equal to the dust temperature at the observed scales, $T_{\rm ex}=T_{\rm d}=25$ K, (cite: Galametz2019), (cite: Cabedo2021b)), $k_{\rm B}$ is the Boltzmann constant, $g_{u}$ is the upper state degeneracy, $Q_{\rm rot}$ is the partition function at 25 K, $E_{l}$ is the energy of the lower level, and $\int{I_{0} {\rm d} v }$ is the integrated intensity. Values of these parameters for each molecule are listed in Table [1](#tab:colDens_pars).

| Transition | DCO$^{+}$ (J=3-2) | H$^{13}$CO$^+$ (J=3-2) | C$^{17}$O (J=1-0) |
|:---|:--:|:--:|:--:|
| $\log~(A/{\rm s}^{-1})$ | $-3.12$ | $-2.87$ | $-7.17$ |
| $g_{u}$ | 7 | 7 | 3 |
| $Q_{\rm rot}$ | 25.22 | 22.91 | 25 |
| $E_{l}$ (cm$^{-1}$) | 7.21 | 8.68 | 0.00 |
| $N_{i}^{\rm mean}$ (cm$^{-2}$) | 3$\times$10$^{11}$ | 7$\times$10$^{11}$ | 3$\times$10$^{13}$ |

: Parameters for the computation of the column density.

The top panels of Fig. [2](#fig:deutFrac_maps) show the $R_{\rm D}$ maps of B335 for the blue- and redshifted velocity components (left and right column, respectively). The mean values of $R_{\rm D}$ are $\sim$1-2%, being higher in the outer region of the envelope where the gas is expected to be colder, and decreasing toward the center where the protostar is located and the temperature is expected to rise. The bottom panels show that the statistical uncertainties are roughly one-tenth of the deuteration values. We note that the highest values of $R_{\rm D}$ are found for the blueshifted component, as high as 3.5%. However, these values have the largest associated errors due to the presence of a third velocity component in the line profiles of H$^{13}$CO$^+$ (J=3-2) and should not be totally trusted (see Appendix [8.1](#sec:ap_spectralMaps)). Finally, we note that while the average $R_{\rm D}$ values for both velocity components are similar, the most widespread blueshifted gas component shows larger $R_{\rm D}$ dispersion, with values from 0.06% to 2%, while the more localized redshifted gas exhibits more uniform values, between 0.01% and 1%.

![](Images/DeutFrac/DeutFrac_DCO_H13CO_err_cont110_scale2.pdf)

One of the main uncertainties of the deuteration analysis is the assumption that both DCO$^{+}$ (J=3-2) and H$^{13}$CO$^+$ (J=3-2) have the same $T_{\rm ex}$. This should be accurate enough, because both molecules present a similar geometry and dipolar moment and are assumed to be spatially coexistent. However, to check the effect that the variation of $T_{\rm ex}$ would produce in our values, we computed the column densities of both species at two additional temperatures, 20 and 30 K. While the DCO$^{+}$ column density does not change significantly at these two temperatures with respect to the value adopted (25 K), the H$^{13}$CO$^+$ column density changes by about 15%. Nevertheless, the new values are still in agreement with the derived values of $R_{\rm D}$ from DCO$^{+}$ reported in the literature (see Sect. [5.1](#sec:deuteration_discussion)).

# Ionization fraction and cosmic-ray ionization rate

We followed the method presented in (cite: Caselli1998) to compute $\chi_{\rm e}$ and $\zeta_{\rm CR}$ from $R_{\rm D}$. The two quantities are given by

$$\begin{equation}
        \chi_{\rm e} = \frac{2.7\times10^{-8}}{R_{\rm D}} - \frac{1.2\times10^{-6}}{f_{\rm D}},
        \label{eq:ionization_frac}
    
\end{equation}$$

and

$$\begin{equation}
        \zeta_{\rm CR} = \left[ 7.5\times10^{-4} \chi_{{\rm e}} + \frac{4.6\times10^{-10}}{f_{{\rm D}}} \right] \chi_{{\rm e}} n_{{\rm H_{2}}} R_{{\rm H}}\,,
        \label{eq:ionization_rate}
    
\end{equation}$$

where $f_{\rm D}$ is the depletion fraction of C and O, $n_{\rm H_{2}}$ is the H$_{2}$ volume density, and $R_{\rm H}$ is the hydrogenation fraction, $R_{\rm H}$ = \[HCO$^{+}$\]/\[CO\].

While this observational method to measure $\chi_{\rm e}$ of the gas relies on a simple chemical network and a rather strong hypothesis, it is widely used in the literature in dense cores and also toward protostars. The validity and shortcomings of the chemical models used to constrain ionization fractions are concisely discussed in Sect. [5.3](#sec:ionization_discussion).

## Estimate of the CO depletion in B335

As $R_{\rm D}$, and therefore $\chi_{\rm e}$, depend on the level of C and O depletion from the gas phase, we hypothesize that the CO abundance is proportional to the CO column density and estimated $f_{\rm D}$ as the ratio between the "expected", $N_{\rm CO}^{\rm exp}$, and the "observed" CO column density, $N_{\rm CO}^{\rm obs}$:

$$\begin{equation}
            f_{\rm D} = \frac{N_{\rm CO}^{\rm exp}}{N_{\rm CO}^{\rm obs}}\,.
            \label{eq:depletionFrac}
        
\end{equation}$$

Here, $N_{\rm CO}^{\rm exp}$ is computed as the product of the H$_{2}$ column density, $N_{\rm H_2}$, and the expected CO to H$_{2}$ abundance ratio, $X_{\rm CO}$ = \[CO\]/\[H$_{2}$\] = 10$^{-4}$ (cite: WilsonRodd1994; Gerner2014), and $N_{\rm CO}^{\rm obs}$ is derived as the product of the C$^{17}$O column density, $N_{\rm C^{17}O}$, and the C$^{17}$O to CO abundance ratio, $f_{\rm C^{17}O}$ = \[CO\]/\[C$^{17}$O\] = 2317 (cite: Wouterloot2008). Then, $f_{\rm D}$ is given by

$$\begin{equation}
            f_{\rm D} = \frac{N_{\rm H_2} X_{\rm CO}}{N_{\rm C^{17}O} f_{\rm C^{17}O}}\,.
            \label{eq:depletion}
        
\end{equation}$$

The H$_{2}$ column density has been estimated from the dust thermal emission at 110 GHz (see Fig. [1](#fig:intensity_maps)) corrected for the primary beam attenuation. Indeed, $N_{\rm H_2}$ depends directly on the flux density measured on the continuum map, the beam solid angle $\Omega_{\rm beam}$, the Planck function $B_{\nu}(T_{\rm d})$ at the dust temperature, and the dust mass opacity $\kappa_{\nu}$ (in units of cm$^2$ g$^{-1}$) at the frequency at which the dust thermal emission was observed:

$$\begin{equation}
           \label{eq:column-density}
           N_{\rm H_2} = -\frac{1}{\mu_{\rm H_2}  m_{\rm H}  \kappa_{\nu}}  \ln \left[ 1 - \frac{S_{\nu}^{\rm beam}}{\Omega_{\rm beam} B_{\nu}(T_d)}  \right]\,,
       
\end{equation}$$

where $\mu_{\rm H_2}=2.8$, $m_{\rm H}$ is the atomic hydrogen mass, and for the dust opacity we used a power-law fit given by

$$\begin{equation}
            \label{eq:kappa}
            \kappa_{\nu} = \frac{\kappa_0}{\chi_{\rm d}} \left( \frac{\nu}{\nu_0} \right) ^{\beta}.
        
\end{equation}$$

We adopt a dust mass absorption coefficient $\kappa_0 = 1.6$ cm$^2$ g$^{-1}$ at $\lambda_0 = 1.3$ mm, following (cite: Ossenkopf1994). We assume a standard gas-to-dust ratio $\chi_{\rm d}$ = 100, a dust emissivity exponent $\beta=0.76$ (cite: Galametz2019), and a dust temperature $T_{\rm d}=25$ K. The resulting $N_{\rm H_2}$ column densities probed in the ALMA dust continuum emission map range from $\sim 10^{20}$ cm$^{-2}$ at radii of $\sim 1600$ au up to a few $10^{22}$ cm$^{-2}$ at the protostar position. We note that the values of column density suffer from a systematic error due to assumptions on the parameters used to derive them (e.g., dust opacity, dust temperature). We estimate that the systematic error is about a factor of 3 to 5, being higher toward the peak position where standard dust properties and conditions of emission may not be met. We use Eq. [\[eq:colDens\]](#eq:colDens) to estimate the observed CO column density $N_{\rm CO} = N_{\rm C^{17}O} f_{\rm C^{17}O}$ from the C$^{17}$O emission map shown in Fig. [1](#fig:intensity_maps), assuming an excitation temperature of 25 K. The CO column density values are subject to systematic uncertainties due to the adopted gas temperature, as this latter is not well constrained and is expected to vary across the envelope. Altogether, the systematic uncertainty is about a factor of 2, and is higher toward the peak position where different gas temperatures are expected to be present along the line of sight.

Using Eq. [\[eq:depletion\]](#eq:depletion), we obtain the CO depletion fraction map shown in Fig. [3](#fig:depletionFrac). The depletion factor ranges from $\sim 20$ in the outer regions to $\sim 70$ in the center of the object. Propagating the errors from the column density maps they stem from, we expect these depletion values to have an uncertainty of a factor of 2 to 3, as the main source of errors —which are due to the assumed gas and dust temperatures— are lessened by the ratio. The CO depletion seems highly asymmetric around the protostar, being the lowest in the southeastern quadrant, while high values are associated to the protostar position and the northern region. We note that the regions with high $f_{\rm D}$ coincide with the regions of low deuteration shown in Fig. [2](#fig:deutFrac_maps).

![](Images/DepletionFactor/fD_h2_c17o_scale2.pdf)

## Ionization fraction of the gas

We obtained $\chi_{\rm e}$ using our $R_{\rm D}$ maps, shown in Sect. [3](#sec:deutFrac) and the CO depletion map, presented in Fig. [3](#fig:depletionFrac). The top panels of Fig. [4](#fig:ionFrac_maps) show the derived $\chi_{\rm e}$ and the bottom panels the associated uncertainties, for the blue- and red-shifted velocity components (left and right column, respectively). We obtained a mean value of $\chi_{\rm e}$ = $2\times10^{-6}$ for both components. Generally, these values are subject to statistical uncertainties of $\sim1.5\times10^{-6}$. The range of values found for $R_{\rm D}$ and $f_{\rm D}$ indicates that the $\chi_{\rm e}$ depends mostly on the level of deuteration, and therefore the systematic errors on the estimated $\chi_{\rm e}$ from Eq. [\[eq:ionization_frac\]](#eq:ionization_frac) are typically $<30\%$ and statistical uncertainties dominate in this case. As $R_{\rm D}$ decreases toward the center of the source, we find that $\chi_{\rm e}$ increases toward the center.

![](Images/IonFrac/IonFrac_fDMaps_def2.pdf)

## Derivation of the CR ionization rate

We produced $\zeta_{\rm CR}$ maps using Eq. [\[eq:ionization_rate\]](#eq:ionization_rate). We obtained $n_{\rm H_{2}}$ as $N_{\rm H_{2}}/L$, using the $N_{\rm H_{2}}$ map obtained in Sect. [4.1](#sec:depletion) and considering a core diameter, $L$, of 1720 au derived from the C$^{17}$O (J=1-0) emission (cite: Cabedo2021b). With this approximation, we find values of the volume density ranging from $\sim 10^{4}$ in the outer regions, to $\sim 10^{6}$ cm$^{-3}$ at the protostar position. We obtained $R_{\rm H}$ for both velocity components as the column density ratio of H$^{13}$CO$^+$ (J=1-0) to C$^{17}$O (J=1-0), and accounting for $f_{^{12/13}C}$ and $f_{\rm C^{17}O}$:

$$\begin{equation}
            R_{\rm H} = \frac{N_{\rm H^{13}CO^{+}} f_{^{12/13}C}}{N_{\rm C^{17}O} f_{\rm C^{17}O}}\,.
        
\end{equation}$$

Values of $R_{\rm H}$ are relatively uniform across the source, with mean values between 2 and $3\times 10^{-7}$ for the two velocity components. The statistical uncertainties of these values are generally one order of magnitude smaller than $R_{\rm H}$.

The two terms within the brackets in Eq. [\[eq:ionization_rate\]](#eq:ionization_rate) have values of the order of $\sim10^{-9}$ and $\sim10^{-11}$, respectively. Therefore, the derivation of $\zeta_{\rm CR}$ is very sensitive to $\chi_{\rm e}$ but not to $f_{\rm D}$. The top panels of Figure  [5](#fig:ionRate_maps) show the derived $\zeta_{\rm CR}$ and the bottom panels show the associated statistical uncertainties, for the blue- and redshifted velocity components (left and right column, respectively). As expected from the values of $\chi_{\rm e}$, $\zeta_{\rm CR}$ increases toward the center, reaching values of 7$\times$10$^{-14}$ s$^{-1}$ at the peak of the dust continuum. The uncertainties on $\zeta_{\rm CR}$ are large, due to all the errors coming from the modeling of the different molecules. Considering the systematic uncertainties on n$_{\rm H_{2}}$, and $R_{\rm H}$  we estimate the global uncertainty on $\zeta_{\rm CR}$ values, and find them to be of the same order of magnitude as the $\zeta_{\rm CR}$ values.

![](Images/IonRate/IonRate_fDMaps_def2.pdf)

To interpret the trend of $\zeta_{\rm CR}$ as a function of the distance from the density peak in an unbiased way, we considered profiles of $\zeta_{\rm CR}$ along directions from the density peak outward denoted by the position angle $\vartheta$, with $0\le\vartheta\le\pi$ (see the lower right panel of Fig. [6](#fig:zeta_vs_radii)). The envelope of the profiles is represented by the orange filled region in the upper left panel of Fig. [6](#fig:zeta_vs_radii). As the $\zeta_{\rm CR}$$(r,\vartheta)$ distributions between 40 and 700 au are skewed, for each radius $\bar{r}$ we considered the median value of $\zeta_{\rm CR}$$(\bar{r},\vartheta)$ and estimated the errors using the first and third quartiles. We find that the trend of $\zeta_{\rm CR}$ can be parameterized by two independent, decreasing power-law profiles $\zeta_{\rm CR}$$(r)\propto r^{s}$. At small radii, $r<270$ au, the slope of the power law, $s = -0.96 \pm 0.04$, is compatible with the diffusive regime of CR propagation. However, at $r>270$ au, $\zeta_{\rm CR}$ drops abruptly to $s = -3.77 \pm 0.30$, which cannot be explained by any propagation regime. The possible explanations for this result are explained with more details in Sect. [5.3](#sec:ionization_discussion).

![](Images/IonRate/zetaNcum_vs_r_Q1medQ3_final_paper.png)

# Discussion

## Local destruction of deuterated molecules

The deuteration fractions observed in Class 0 protostars range between 1% and 10%, with a large scatter from source to source and at the different protostellar scales (cite: Caselli2002; Roberts2002; Jorgensen2004). The \[DCO$^{+}$\]/\[H$^{13}$CO$^+$\] values that we find for B335 are therefore in broad agreement with the typical range reported in the literature, even accounting for temperature effects. However, (cite: Butner1995) found a \[DCO$^{+}$\]/\[HCO$^{+}$\] of $\simeq$3% in B335 at scales of $\sim$10000 au. This value is larger than the range of values we find with ALMA at smaller scales, which indicates a decrease in $R_{\rm D}$ toward the center of the envelope. Indeed, $R_{\rm D}$ decreases down to $<1$% toward the center and the northern region of the source. This decrease could be attributed to local radiation processes occurring during the protostellar phase, after the protostar has been formed. An increase in the local radiation could promote processes that would lead to the destruction of deuterated molecules due to the evaporation of neutrals to the gas phase (cite: Caselli1998; Jorgensen2004), or the increased abundance of ionized molecules like HCO$^{+}$ (cite: Gaches2019).

The decreasing trend in $R_{\rm D}$ is further confirmed by our observations of N$_{2}$D$^{+}$ (J=3-2). Figure [7](#fig:deutFrac_n2d_maps) shows the deuteration map overplotted with the N$_{2}$D$^{+}$ (J=3-2) integrated emission. A lack of N$_{2}$D$^{+}$ is observed in regions where $R_{\rm D}$ is lower, suggesting that the physical processes lowering the abundance of O-bearing deuterated molecules also lower the abundance of N-bearing deuterated species around the protostar.

![](Images/DeutFrac/H13CO_DCO_N2Dcont_colDens_def2.pdf)

## High values of C and O depletion in the source

At core scales, observations of the depletion in B335 have been rather inconclusive as some studies suggest very little CO depletion (JCMT 20-arcsec beam probing 3000 au, (cite: Murphy1997)), while others suggest a CO depletion of one order of magnitude, $f_{\rm D}$$\sim 10$, at similarly large scales (cite: Walmsley1987). Our spatially resolved observations reveal large values of CO depletion of the gas in the inner envelope of B335 at radii $<1000$ au. As shown in Fig. [3](#fig:depletionFrac), we find $f_{\rm D}$ ranging from 20 to 40 at radii of 1000 to 100 au, except at the core center where it increases up to 80. Such CO depletion at protostellar radii $100-1000$ au is somehow unexpected, if one assumes depletion is due to freeze-out onto dust grains. Indeed, gas and dust at such radii should have temperatures beyond $\sim20-30$ K, where the evaporation of CO from the surface of the dust should replenish it in the gas phase (cite: Anderl2016). The high depletion values found at the protostar position are highly uncertain due to unknown optical depth, and unconstrained dust and gas temperatures. We stress that the possible depletion increase toward the center in B335 should be confirmed with further observations of higher J transitions of CO.

Several observational studies of protostellar cores have found depletion factors $f_D>10$ at scales of $\sim 5000$ au, with some spatially resolved studies pointing to values up to $\sim 20$ (cite: Alonso-Albi2010; Christie2012; Yildiz2012; Fuente2012). Models of protostellar evolution with short warm-up timescales in the envelope (cite: Aikawa2012) show that $f_{\rm D}$ may remain high even inside the sublimation radius, especially at early stages, because of the conversion of CO into CH$_{3}$OH and CH$_{4}$ on the grain surfaces. Photodissociation due to the protostellar UV radiation could contribute to lowering the global CO abundance in the innermost layers of protostellar envelopes (cite: Visser2009b). Additionally, other sources of ionization, such as CRs, could decrease the abundance of CO in the gas phase by promoting its reaction for the formation of HCO$^{+}$ (cite: Gaches2019). This decrease in CO by transformation into HCO$^{+}$ could also explain the observed coincidence between regions with large CO depletion and low $R_{\rm D}$.

Another possible cause for the observed depletion could be the presence of relatively large dust grains, as observed in several protostars at similar scales by (cite: Galametz2019). Indeed, larger grains are less efficiently warmed up (cite: Hiqbal2018), limiting the desorption of CO ices to the gas phase. We note that the presence of large dust grains in the inner envelope of B335 could also favor enhanced ionization of the gas (cite: Walmsley2004), and thus also be consistent with our findings regarding ionization.

## Origin of the ionization

From the single-dish observations of (cite: Butner1995), (cite: Caselli1998) find ionization fractions of protostellar gas at core scales of the order of 10$^{-8}$–10$^{-6}$. In the B335 outer envelope where $n(\rm {H_2})  \sim 10^{4}$ cm$^{-3}$, these authors estimate $\chi_{\rm e}$ of a few $10^{-6}$. With our interferometric data, we measure $\chi_{\rm e}$ $\sim$ 2$\times$10$^{-6}$ in the inner envelope, where $n(\rm {H_2}) \sim 10^6$ cm$^{-3}$, with the largest values being $\chi_{\rm e}$ $\sim$9$\times$10$^{-6}$. We note that while all these aforementioned values are only providing line-of-sight averages for $\chi_{\rm e}$, the interferometric data only select a narrow range of spatial scales, making them less sensitive to line-of-sight averaging than single-dish data, and therefore they are more representative of local abundance variations.

We stress that, while the use of deuteration to measure $\chi_{\rm e}$ is a standard practice in the literature, it has been noted that such an approach may not give accurate results in low-density medium experiencing small deuteration fractions (e.g., $\sim 10^{3} \rm{cm}^{-3}$, (cite: Vaupre2014)). In this case, the abundances of DCO$^{+}$ and HCO$^{+}$ mostly depend on the $\zeta_{\rm CR}$$/n_H$ ratio and not only on $\zeta_{\rm CR}$, and using $R_D$ to get $\zeta_{\rm CR}$ is valid only when deuteration is $>2\%$: the measured values in B335 are mostly all lower than this threshold at radii $< 500$ au, which would suggest that our approach of using these observations to derive $\chi_{\rm e}$ is deficient. However, recent models have shown that in warm dense gas (T $\gtrsim$ 24 K and $n_{\rm H} \sim 10^6$ cm$^{-3}$), which is typical of the conditions probed here, the relation between $R_{\rm D}$ and $\zeta_{\rm CR}$ is more robust. (cite: Shingledecker2016) show that the scatter of $\zeta_{\rm CR}$ predicted by the Caselli model at low ionization values seems to be related to variations in the ortho-to-para ratio (OPR) of H$_2$. While the OPR is an unobservable parameter for dense gas conditions, and therefore cannot be measured for our source, the work of these latter authors shows that the dependence of the relation between $R_{\rm D}$ and $\zeta_{\rm CR}$ on OPR is weaker for evolved sources due to the stabilization of the OPR. This effect has been shown to happen sooner when $n_{\rm H}$ and the temperature are increased. This was also pointed out by (cite: Bron2021) who show that $R_{\rm D}$ is a robust estimator of $\zeta_{\rm CR}$ when the gas is subject to high ionization fractions ($\chi_{\rm e}$$\gtrsim 3 \times 10^{-7}$). As we are probing a dense region of the core with temperatures larger than 20 K and ionization from an embedded source, this supports our use of the Caselli method to measure $\zeta_{\rm CR}$.

The large $\chi_{\rm e}$ values could be produced by local UV and X-ray radiation produced in outflow shocks, altering the chemistry from the molecular content around the shocks (cite: Viti1999; Girart2002; Girart2005). However, ionization by far-UV (FUV) photons can be ruled out. Indeed, the maximum energy of FUV photons is around 13 eV, thus below the threshold for ionization of molecular hydrogen (15.44 eV). The second argument is related to the fact that the extinction cross-section at FUV wavelengths ($\simeq0.1~\mu$m) is $\sigma_{\rm UV}\simeq2\times10^{-21}$ cm$^2$ per hydrogen atom (cite: Draine2003). Thus, FUV photons are rapidly absorbed in a thin layer of column density equal to $(2\sigma_{\rm UV})^{-1}\simeq3\times10^{20}$ cm$^{-2}$.

The absorption cross-section of X-ray photons, $\sigma_{\rm X}$, in the range 1$-$10 keV is much smaller than at FUV frequencies (cite: Bethell2011). For example, at 1 keV and 10 keV, $\sigma_{\rm X}\simeq2\times10^{-22}$ cm$^2$ and $\simeq8\times10^{-25}$ cm$^2$ per H atom, respectively. While at 1 keV the corresponding absorption column density is still small, $(2\sigma_{\rm X})^{-1}\simeq2\times10^{21}$ cm$^{-2}$, at 10 keV it reaches about $6\times10^{23}$ cm$^{-2}$, much larger than the maximum H$_{2}$ column density, ${\bm N_{\rm H_{2}}}$, that we found. The latter was computed by integrating the dust continuum at 110 GHz along directions identified by the position angle $\vartheta$ (see lower right panel of Fig. [6](#fig:zeta_vs_radii)) and is representative of the column density in the outflow cavity. We therefore estimated the X-ray ionization rate, $\zeta_{\rm X}$, using the spectra described by (cite: Rab2017) for a typical and a flaring T Tauri star, assuming a stellar radius of $2R_\odot$. Results for $\zeta_{\rm X}$ are shown in the upper left panel of Fig. [6](#fig:zeta_vs_radii). It is evident that X-ray ionization cannot explain the values of the ionization rate estimated from observations. A fraction of these X-ray photons end up in the disk, which has much higher densities than the cavity, and so ${\bm N_{\rm H_{2}}}$ can easily reach values greater than $10^{24}$ cm$^{-2}$, as found by (cite: Grosso2020) for a Class 0 protostar. At such high ${\bm N_{\rm H_{2}}}$, $\zeta_{\rm X}$ decreases dramatically.

Once the high-energy radiation field is excluded as the main source of ionization rate estimated from observations, the only alternative left is CRs (see Sect. [4.3](#sec:IonRate)). However, the range of derived values is much higher than those expected from Galactic CRs (cite: Padovani2022). Following (cite: McKee1989), $\chi_{\rm e}$ $=1.3 \times10^{-5} n(\rm H_2)^{-1/2}$, and for the volume densities derived in Sect. [4.3](#sec:IonRate), we should expect $\chi_{\rm e}$ values of $10^{-7}$ to $10^{-8}$, which are between one and two orders of magnitude lower than the observed values in B335. As we also observed a significant increase in $\chi_{\rm e}$ toward the center, and especially of $\zeta_{\rm CR}$, the origin of the high values should be of local origin. In particular, we are most likely witnessing the local acceleration of CRs in shocks located in B335 as predicted by theoretical models (cite: Padovani2015; Padovani2016; Padovani2020). The values of $\zeta_{\rm CR}$ found in B335, between about $10^{-16}$ and $10^{-14}$ s$^{-1}$, are among the highest values reported in the literature toward star-forming regions (cite: Maret2007; Ceccarelli2014b; Fuente2016; Fontani2017; Favre2017; Bialy2022). We stress that this is the first time that $\zeta_{\rm CR}$ is measured at such small scales in a solar-type protostar and can be attributed to locally accelerated CRs, as well as the first time that a map of $\zeta_{\rm CR}$ is obtained.

There are two possible origins for the production of local CRs close to a protostar. One is in strong magnetized shocks along the outflow (cite: Padovani2015; Padovani2016; Fitz21; Padovani2021). Indeed, synchrotron radiation, which is the signature of the presence of relativistic electrons, has been detected in some outflows (cite: Carrasco10; Ainsworth14; RodriguezK16; RodriguezK19; Osorio17). The second possibility is in accretion shocks near the stellar surface (cite: Padovani2016; Gaches2018). Both mechanisms are expected to generate low-energy CRs ($\lesssim$ 100 MeV- 30 GeV) through the first-order Fermi acceleration mechanism with a rate of up to $\sim10^{-13}$ s$^{-1}$.

The ionization rate slope found in B335 for $r<270$ au is close to $-1$ and compatible with a diffusive regime, in agreement with predictions of theoretical models. Surprisingly, at radii larger than $\sim$ 250 au, the slope decreases below $-2$, thus beyond the geometrical dilution regime. We propose two possible explanations. On the one hand, local CRs may have accumulated enough column density to start being thermalized. On the other hand, at radii above about 250 au, both the dust emission and $\zeta_{\rm CR}$ maps gradually lose their central symmetry (see Figs. [1](#fig:intensity_maps) and  [5](#fig:ionRate_maps), respectively). For example, the continuum map shows two higher density arms toward the northeast and southeast. Therefore, the slope, calculated by averaging over the position angle distribution $\vartheta$, could be less than $-2$. The loss of symmetry at larger radii in the ionization maps might also be additional evidence as to the importance of non-symmetrical motions during the protostellar collapse (cite: Cabedo2021b). However, we note that these values are also affected by our limited angular resolution of 1.5 arcsec ($\sim$ 250 au), implying that only three or four points in the plot are completely independent, and that observations at larger angular resolution are needed in order to confirm the observed trend.

Previous observations indicate that B335 hosts a powerful and variable jet, which might explain a large production of local CRs (cite: Galfalk2007; Yen2010). Nevertheless, the exact origin of the local CR source is difficult to pinpoint due to our limited angular resolution. The column density calculated from the dust continuum map at 110 GHz (see lower left panel of Fig. [6](#fig:zeta_vs_radii)) is consistent with that expected in the outflow cavity. To calculate the minimum energy that protons must have in order to pass through a given column density without being thermalized, we can make use of the stopping range function (see Fig. 2 in (cite: Padovani2018)). At ${\bm N_{\rm H_{2}}}\simeq10^{22}$ cm$^{-2}$, protons with energies of about 10 MeV are thermalized and lose their ionizing power (see also the upper x-axis of Fig. [6](#fig:zeta_vs_radii)). As discussed above, if the shock is in the vicinity of the protostellar surface, a column density of the order of $10^{24}-10^{25}$ cm$^{-2}$ can easily be accumulated (cite: Grosso2020). In this case, the minimum proton energy required to prevent thermalization is 100 MeV and 400 MeV at $10^{24}$ and $10^{25}$ cm$^{-2}$, respectively. Models of local CR acceleration in low-mass protostars predict that accelerated protons can reach maximum energies of the order of 100 MeV and 10 GeV if the shock in which they are accelerated is located in the jet or close to the protostellar surface, respectively (cite: Padovani2015; Padovani2016). Thus, although the position of the shock that accelerates these local CRs in B335 is unknown, models suggest that the maximum energies of the protons are sufficiently high to explain the observed ionization.

Additionally, we note that B335 has been observed to exhibit an organized magnetic field at scales similar to the ones probed here (cite: Maury2018). This could also create favorable conditions for enhanced CR production. Finally, our results are in agreement with CR ionization models on protostellar cores with an embedded radiation source (cite: Gaches2019); these latter models also suggest that ionization models based solely on H$_{3}^{+}$ chemistry might underpredict $\chi_{\rm e}$ by one order of magnitude, except in regions where CR ionization is dominant.

## Magnetic field coupling and non-ideal MHD effects

The ionization fraction of the gas in a young accreting protostar is not only important to understand the early chemistry around solar-type stars, feeding the scales where disks and planets will form, but is also the critical parameter that determines $(i)$ the coupling between the magnetic field and the infalling-rotating gas in the envelope, and $(ii)$ the role of diffusive processes, such as ambipolar diffusion, which counteract the outward transport of angular momentum due to magnetic fields (a process known as magnetic braking). The higher the gas ionization, the more efficient the coupling, and the braking.

The large fraction of ionized gas unveiled by our observations in the inner envelope of B335 should lead to almost perfect coupling of the gas to the local magnetic field lines, generating a drastic braking of rotational motions. We note that these new results lend extra support to other observational evidence of a very efficient magnetic braking at work in B335, notable the highly pinched magnetic field lines observed at similar scales by (cite: Maury2018), and the failure to detect any disk larger than $\sim10$ au in this object (cite: Yen2015b); although a new kinematic analysis may be motivated in light of the detection of several velocity components in the accreting gas at scales of $\sim500$ au (cite: Cabedo2021b).

At the end of the pre-stellar stage, the fraction of ionized gas toward the central part of the core is expected to be very low, as Galactic CRs do not penetrate deeply and there is no local ionization source (cite: Padovani2013; Ceccarelli2014; Silsbee2019). Hence, the initial stages of protostellar evolution are proceeding under low ionization conditions at typical $\zeta_{\rm CR}$ $<10^{-16}\,\rm{s}^{-1}$ (cite: Padovani2018; Ivlev2019), which enhance the importance of non-ideal MHD processes (cite: Padovani2014), with efficient diffusion of magnetic flux outwards during the very first phases of the collapse, and reduced magnetic braking. If the local ionization processes we observe in B335 are prototypical of solar-type Class 0 protostars, then CRs accelerated in the proximity of the protostar could be responsible for changing the ionization fraction of the gas at disk-forming scales once the protostar is formed, setting quasi-ideal MHD conditions in the inner envelope. The timescale and magnitude of this transition from non-ideal MHD conditions to quasi-ideal MHD conditions may depend on the protostellar properties: more detailed modeling and observations toward other protostars are required to address this question. Moreover, we note that the observed large $\chi_{\rm e}$ is not in agreement with the values used to calculate the simplified chemical networks in non-ideal MHD models of protostellar formation and evolution (cite: Marchand2016; Zhao2020a), as gas ionization is usually predicted from the gas density following (cite: McKee1989). Thus, our observations suggest that careful treatment of ionizing processes in magnetized models may be crucial to properly describe the gas-magnetic field coupling at different scales in embedded protostars.

In this scenario, the properties of protostellar disks could be tightly related to the local acceleration of low-energy CRs, and the development of a highly ionized region around the protostar. Therefore, we would not expect the ionization fraction of the gas present at large scale in the surrounding cloud to be a key factor in setting the disk properties, as proposed for example by (cite: Kuffmeier2020). The scenario we propose is also in agreement with recent ALMA observations of the Class II disks in Orion that do not find supporting evidence of local cloud properties affecting the disk properties (cite: vanTerwisga2022).

# Conclusions and summary

This work provides new insights into the physico-chemical conditions of the gas in the young Class 0 protostar B335. For the first time, we derived a map of the gas $\chi_{\rm e}$ and of $\zeta_{\rm CR}$ at envelope scales $<1000$ au in a Class 0 protostar. Our results highlight the interplay between physical processes responsible for gas ionization at disk-forming scales, and its consequences for magnetized models of solar-type star formation. Here, we summarize the main results of our analysis:

- We used ALMA data to create molecular line emission maps and used these to characterize the physico-chemical properties of the dense gas in B335. We used the chemical recipe from (cite: Caselli1998) to derive $\chi_{\rm e}$ based on the deuteration fraction of HCO+ and of the $f_{\rm D}$. This recipe was recently shown to be valid for dense molecular gas, $\sim 10^6$ cm$^{-3}$, with a high ionization fraction ($\gtrsim 3 \times 10^{-7}$, (cite: Bron2021)). It allows us to characterize the ionization of the gas at envelope radii $\lesssim$ 1000 au: we find large fractions of ionized gas, $\chi_{\rm e}$, between 1 and $8\times10^{-6}$. These values are remarkably higher than the ones usually measured at core scales.

- We produced for the first time a map of $\zeta_{\rm CR}$, in the close environment of a young embedded protostar. Our analysis reveals very high values of $\zeta_{\rm CR}$ between $10^{-16}$ and $10^{-14}$ s$^{-1}$, increasing toward the central protostellar embryo at small envelope radii. This suggests that local acceleration of CRs, and not the penetration of interstellar CRs, may be responsible for the gas ionization in the inner envelope, potentially down to disk forming scales.

- The large fraction of ionized gas we find suggests an efficient coupling between the magnetic field and the gas in the inner envelope of B335. This interpretation is also supported by the observations of highly organized magnetic field lines, and no detection of a large rotationally supported disk in B335.

If our findings are found to be prototypical of the low-mass star formation process, they might imply that the collapse at scales $<1000$ au transitions from non-ideal to a quasi-ideal MHD once the central protostar starts ionizing its surrounding gas, and very efficient magnetic braking of the rotating-infalling protostellar gas might then take place. Protostellar disk properties may therefore be determined by local processes setting the magnetic field coupling, and not only by the amount of angular momentum available at large envelope scales and by the magnetic field strength in protostellar cores. We stress that the gas ionization we find in B335 significantly stands out from the typical values routinely used in state-of-the-art models of protostellar formation and evolution. Our observations suggest that a careful treatment of ionizing processes in these magnetized models may be crucial to properly describe the processes responsible for disk formation and early evolution. We also note that more observations of B335 at higher spatial resolution, and of other Class 0 protostars, are crucial to confirm our results.

# Acknowledgments

This project has received funding from the European Research Council (ERC) under the European Union Horizon 2020 research and innovation programme (MagneticYSOs project, grant agreement N$\ensuremath{^\circ}$ 679937). This work was also partially supported by the program Unidad de Excelencia María de Maeztu CEX2020-001058-M. JMG also acknowledges support by the grant PID2020-117710GB-I00 (MCI-AEI-FEDER, UE).

Additionally, this paper makes use of the following ALMA data: 2015.1.01188.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ

91 natexlab

(ref: Aikawa2012) Aikawa, Y., Wakelam, V., Hersant, F., Garrod, R. T., & Herbst, E. 2012, ApJ, 760, 40

(ref: Ainsworth14) Ainsworth, R. E., Scaife, A. M. M., Ray, T. P., et al. 2014, ApJL, 792, L18

(ref: Alonso-Albi2010) Alonso-Albi, T., Fuente, A., Crimier, N., et al. 2010, A&A, 518, A52

(ref: Alves2014) Alves, F. O., Frau, P., Girart, J. M., et al. 2014, A&A, 569, L1

(ref: Anderl2016) Anderl, S., Maret, S., Cabrit, S., et al. 2016, A&A, 591, A3

(ref: ALMAc4) Asayama, S., Biggs, A., de Gregorio, I., et al. 2016, ALMA Partnership

(ref: Bethell2011) Bethell, T. J. & Bergin, E. A. 2011, ApJ, 740, 7

(ref: Bialy2022) Bialy, S., Belli, S., & Padovani, M. 2022, A&A, 658, L13

(ref: Bron2021) Bron, E., Roueff, E., Gerin, M., et al. 2021, A&A, 645, A28

(ref: Butner1995) Butner, H. M., Lada, E. A., & Loren, R. B. 1995, ApJ, 448, 207

(ref: Cabedo2021b) Cabedo, V., Maury, A., Girart, J. M., & Padovani, M. 2021, A&A, 653, A166

(ref: Carrasco10) Carrasco-González, C., Rodrı́guez, L. F., Anglada, G., et al. 2010, Science, 330, 1209

(ref: Caselli2002) Caselli, P. 2002, , 50, 1133

(ref: Caselli1998) Caselli, P., Walmsley, C. M., Terzieva, R., & Herbst, E. 1998, ApJ, 499, 234

(ref: Ceccarelli2014) Ceccarelli, C., Caselli, P., Bockelée-Morvan, D., et al. 2014a, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 859

(ref: Ceccarelli2014b) Ceccarelli, C., Dominik, C., López-Sepulcre, A., et al. 2014b, ApJL, 790, L1

(ref: Christie2012) Christie, H., Viti, S., Yates, J., et al. 2012, MNRAS, 422, 968

(ref: Dapp2012) Dapp, W. B., Basu, S., & Kunz, M. W. 2012, A&A, 541, A35

(ref: Draine2003) Draine, B. T. 2003, ARA&A, 41, 241

(ref: Estalella2017) Estalella, R. 2017, PASP, 129, 025003

(ref: Evans2015) Evans, Neal J., I., Di Francesco, J., Lee, J.-E., et al. 2015, ApJ, 814, 22

(ref: Favre2017) Favre, C., López-Sepulcre, A., Ceccarelli, C., et al. 2017, A&A, 608, A82

(ref: Fitz21) Fitz Axen, M., Offner, S. S. S., Gaches, B. A. L., et al. 2021, ApJ, 915, 43

(ref: Fontani2017) Fontani, F., Ceccarelli, C., Favre, C., et al. 2017, A&A, 605, A57

(ref: Fuente2012) Fuente, A., Caselli, P., McCoey, C., et al. 2012, A&A, 540, A75

(ref: Fuente2016) Fuente, A., Cernicharo, J., Roueff, E., et al. 2016, A&A, 593, A94

(ref: Gaches2018) Gaches, B. A. L. & Offner, S. S. R. 2018, ApJ, 861, 87

(ref: Gaches2019) Gaches, B. A. L., Offner, S. S. R., & Bisbas, T. G. 2019, ApJ, 878, 105

(ref: Galametz2019) Galametz, M., Maury, A. J., Valdivia, V., et al. 2019, A&A, 632, A5

(ref: Galfalk2007) Gâlfalk, M. & Olofsson, G. 2007, A&A, 475, 281

(ref: Gerner2014) Gerner, T., Beuther, H., Semenov, D., et al. 2014, A&A, 563, A97

(ref: Girart2006) Girart, J. M., Rao, R., & Marrone, D. P. 2006, Science, 313, 812

(ref: Girart2005) Girart, J. M., Viti, S., Estalella, R., & Williams, D. A. 2005, A&A, 439, 601

(ref: Girart2002) Girart, J. M., Viti, S., Williams, D. A., Estalella, R., & Ho, P. T. P. 2002, A&A, 388, 1004

(ref: Grosso2020) Grosso, N., Hamaguchi, K., Principe, D. A., & Kastner, J. H. 2020, A&A, 638, L4

(ref: Hennebelle2020) Hennebelle, P., Commerçon, B., Lee, Y.-N., & Charnoz, S. 2020, A&A, 635, A67

(ref: Hennebelle2019) Hennebelle, P. & Inutsuka, S.-i. 2019, Frontiers in Astronomy and Space Sciences, 6, 5

(ref: Hirano1992) Hirano, N., Kameya, O., Kasuga, T., & Umemoto, T. 1992, ApJL, 390, L85

(ref: Hirano1988) Hirano, N., Kameya, O., Nakayama, M., & Takakubo, K. 1988, ApJL, 327, L69

(ref: Hiqbal2018) Iqbal, W. & Wakelam, V. 2018, A&A, 615, A20

(ref: Ivlev2019) Ivlev, A. V., Silsbee, K., Sipilä, O., & Caselli, P. 2019, ApJ, 884, 176

(ref: Jorgensen2004) Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2004, A&A, 416, 603

(ref: Keene1983) Keene, J., Davidson, J. A., Harper, D. A., et al. 1983, ApJL, 274, L43

(ref: Kuffmeier2020) Kuffmeier, M., Zhao, B., & Caselli, P. 2020, A&A, 639, A86

(ref: Kurono2013) Kurono, Y., Saito, M., Kamazaki, T., Morita, K.-I., & Kawabe, R. 2013, ApJ, 765, 85

(ref: Lebreuilly2021) Lebreuilly, U., Hennebelle, P., Colman, T., et al. 2021, ApJL, 917, L10

(ref: Li2011) Li, Z.-Y., Krasnopolsky, R., & Shang, H. 2011, ApJ, 738, 180

(ref: Machida2011) Machida, M. N., Inutsuka, S.-I., & Matsumoto, T. 2011, PASJ, 63, 555

(ref: Marchand2016) Marchand, P., Masson, J., Chabrier, G., et al. 2016, A&A, 592, A18

(ref: Marchand2020) Marchand, P., Tomida, K., Tanaka, K. E. I., Commerçon, B., & Chabrier, G. 2020, ApJ, 900, 180

(ref: Maret2007) Maret, S. & Bergin, E. A. 2007, ApJ, 664, 956

(ref: Masson2016) Masson, J., Chabrier, G., Hennebelle, P., Vaytet, N., & Commerçon, B. 2016, A&A, 587, A32

(ref: Maury2019) Maury, A. J., André, P., Testi, L., et al. 2019, A&A, 621, A76

(ref: Maury2018) Maury, A. J., Girart, J. M., Zhang, Q., et al. 2018, MNRAS, 477, 2760

(ref: McKee1989) McKee, C. F. 1989, ApJ, 345, 782

(ref: Murphy1997) Murphy, B. T., Little, L. T., & Kelly, M. L. 1998, MNRAS, 294, 635

(ref: Osorio17) Osorio, M., Dı́az-Rodrı́guez, A. K., Anglada, G., et al. 2017, ApJ, 840, 36

(ref: Ossenkopf1994) Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943

(ref: Padovani2022) Padovani, M., Bialy, S., Galli, D., et al. 2022, A&A, 658, A189

(ref: Padovani2013) Padovani, M. & Galli, D. 2013, in Astrophysics and Space Science Proceedings, Vol. 34, Cosmic Rays in Star-Forming Environments, ed. D. F. Torres & O. Reimer, 61

(ref: Padovani2014) Padovani, M., Galli, D., Hennebelle, P., Commerçon, B., & Joos, M. 2014, A&A, 571, A33

(ref: Padovani2015) Padovani, M., Hennebelle, P., Marcowith, A., & Ferrière, K. 2015, A&A, 582, L13

(ref: Padovani2018) Padovani, M., Ivlev, A. V., Galli, D., & Caselli, P. 2018, A&A, 614, A111

(ref: Padovani2020) Padovani, M., Ivlev, A. V., Galli, D., et al. 2020, Space Sci. Rev., 216, 29

(ref: Padovani2021) Padovani, M., Marcowith, A., Galli, D., Hunt, L. K., & Fontani, F. 2021, A&A, 649, A149

(ref: Padovani2016) Padovani, M., Marcowith, A., Hennebelle, P., & Ferrière, K. 2016, A&A, 590, A8

(ref: Rab2017) Rab, C., Güdel, M., Padovani, M., et al. 2017, A&A, 603, A96

(ref: Roberts2002) Roberts, H., Fuller, G. A., Millar, T. J., Hatchell, J., & Buckle, J. V. 2002, A&A, 381, 1026

(ref: RodriguezK16) Rodrı́guez-Kamenetzky, A., Carrasco-González, C., Araudo, A., et al. 2016, ApJ, 818, 27

(ref: RodriguezK19) Rodrı́guez-Kamenetzky, A., Carrasco-González, C., González-Martı́n, O., et al. 2019, MNRAS, 482, 4687

(ref: Shingledecker2016) Shingledecker, C. N., Bergner, J. B., Le Gal, R., et al. 2016, ApJ, 830, 151

(ref: Silsbee2019) Silsbee, K. & Ivlev, A. V. 2019, ApJ, 879, 14

(ref: Soler2019) Soler, J. D. 2019, A&A, 629, A96

(ref: Stutz2008) Stutz, A. M., Rubin, M., Werner, M. W., et al. 2008, ApJ, 687, 389

(ref: Thomas2008) Thomas, H. S. & Fuller, G. A. 2008, A&A, 479, 751

(ref: vanTerwisga2022) van Terwisga, S. E., Hacar, A., van Dishoeck, E. F., Oonk, R., & Portegies Zwart, S. 2022, arXiv e-prints, arXiv:2202.11057

(ref: Vaupre2014) Vaupré, S., Hily-Blant, P., Ceccarelli, C., et al. 2014, A&A, 568, A50

(ref: Visser2009b) Visser, R., van Dishoeck, E. F., & Black, J. H. 2009, A&A, 503, 323

(ref: Viti1999) Viti, S. & Williams, D. A. 1999, MNRAS, 310, 517

(ref: Walmsley2004) Walmsley, C. M., Flower, D. R., & Pineau des Forêts, G. 2004, A&A, 418, 1035

(ref: Walmsley1987) Walmsley, C. M. & Menten, K. M. 1987, in Circumstellar Matter, ed. I. Appenzeller & C. Jordan, Vol. 122, 71

(ref: Watson2020) Watson, D. M. 2020, Research Notes of the American Astronomical Society, 4, 88

(ref: WilsonRodd1994) Wilson, T. L. & Rood, R. 1994, ARA&A, 32, 191

(ref: Wootten1987) Wootten, A. 1987, in Astrochemistry, ed. M. S. Vardya & S. P. Tarafdar, Vol. 120, 311–319

(ref: Wouterloot2008) Wouterloot, J. G. A., Henkel, C., Brand, J., & Davis, G. R. 2008, A&A, 487, 237

(ref: Yen2015b) Yen, H.-W., Takakuwa, S., Koch, P. M., et al. 2015, ApJ, 812, 129

(ref: Yen2010) Yen, H.-W., Takakuwa, S., & Ohashi, N. 2010, ApJ, 710, 1786

(ref: Yildiz2012) Yıldız, U. A., Kristensen, L. E., van Dishoeck, E. F., et al. 2012, A&A, 542, A86

(ref: Zhang2014) Zhang, Q., Qiu, K., Girart, J. M., et al. 2014, ApJ, 792, 116

(ref: Zhao2020a) Zhao, B., Caselli, P., Li, Z.-Y., et al. 2020, MNRAS, 492, 3375

(ref: Zhou1993) Zhou, S., Evans, Neal J., I., Koempe, C., & Walmsley, C. M. 1993, ApJ, 404, 232

# Technical details of the ALMA observations

Table [\[table:technicalInfo\]](#table:technicalInfo) presents the technical details of the ALMA observations presented in this work, including the ALMA configuration, the date and time range, the central frequency, the obtained spectral resolution, and the different calibrators used.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Config. | Date | Timerange | Center freq | Spec. Res. | Flux cal. | Phase cal. | Bandpass cal. |
|  | (mm/dd/yy) | (hh:min:s.ms; UTC) | (GHz) | (km s$^{-1}$) |  |  |  |
| C40-1 | 19/03/2017 | 10:40:52.8 - 10:53:42.8 | 231.0 | 0.09 | J1751+0939 | J1851+0035 | J1751+0939 |
| C40-2 | 02/07/2017 | 15:30:38.9 - 15:49:59.2 | 110.0 | 0.08 | J1751+0939 | J1938+0448 | J1751+0939 |
| C40-3 | 12/06/2016 | 18:39:47.5 - 19:24:24.3 | 87.7 | 0.10 | J1751+0939 | J1938+0448 | J1751+0939 |
| C40-4 | 21/11/2016 | 22:41:22.0 - 23:28:19.8 | 231.0 | 0.09 | J2148+0657 | J1851+0035 | J2148+0657 |
| C40-5 | 10/22/2016 - 10/23/2016 | 23:34:05.4 - 00:02:51.3 | 110.0 | 0.08 | J2148+0657 | J1938+0448 | J2025+3343 |
| C40-6 | 10/10/2016 | 20:50:38.0 - 21:39:40.2 | 87.7 | 0.10 | J1751+0939 | J1938+0448 | J1751+0939 |
|  | 10/10/2016 | 22:43:07.4 - 23:24:00.4 | 87.7 | 0.10 | J1751+0939 | J1938+0448 | J1751+0939 |
|  | 10/11/2016 | 21:14:59.4 - 22:03:55.2 | 87.7 | 0.10 | J1751+0939 | J1938+0448 | J1751+0939 |

# Line profile analysis

## Spectral maps

The DCO$^{+}$ (J=3-2) and H$^{13}$CO$^+$ (J=3-2) spectral maps are presented in Figs. [8](#fig:dco_spectralMap) and [10](#fig:h13co_32_spectralMap). Both maps show emission in a region of 5.5$''$ $\times$ 5.5$''$ (900 au) around the center of the source, with each spectrum corresponding to a pixel of 0.5$''$ (82 au). The H$^{13}$CO$^+$ (J=1-0) shows only a region 4$''$ $\times$ 4$''$ (685 au) and each spectrum corresponds to 0.25$''$ (41 au).

The three tracers present the same pattern observed in C$^{17}$O (J=1-0), presented in (cite: Cabedo2021b). The line profiles are double-peaked with one of the two velocity components progressively disappearing at different offsets of the source, that is, the blueshifted component is dominant in the eastern region of the source while the redshifted component is present only in the western region. For the three transitions, the blueshifted component is always more intense than the redshifted one, which produces the blue asymmetric morphology observed in the integrated intensity images.

As none of the tracers present a morphology typical of the outflow cavity, we assume that they are not tracing outflowing gas and that the two velocity components are not caused by this effect. This is confirmed with the spectral maps where no signatures coming from outflowing gas —such as very broad lines or high velocity wings— can be observed in the line profiles. This is generally true, except for a small region on the southeast region of the H$^{13}$CO$^+$ (J=3-2) map, where an additional third velocity component, or "shoulder", can be observed. This additional component appears to be very broad, and at velocities of $\sim$7.6-–7.7 km s$^{-1}$. We do attribute this signature to outflow contamination, which is observed neither in DCO$^{+}$ (J=3-2) nor in H$^{13}$CO$^+$ (J=1-0). We consider that while the outflow might have some effect in the line profiles, this is negligible and is not the main cause of the double-peaked line profiles. The effect of large-scale filtering cannot be ruled out. This is particularly visible in the DCO$^{+}$ (J=3-2) and H$^{13}$CO$^+$ (J=3-2) where negative emission is observed in the center and west regions of the source. While these two effects can be a source of uncertainty in our analysis, we conclude that they alone cannot produce the observed line profiles and the velocity pattern through the source, and proceed with the line modeling with the assumption of two independent velocity components.

![](Images/SpectralMaps/DCO+_contsub_rob1_05arcsec_01kms_140kl_smth15arcsec_smll30arcsec_region_spectra_2.pdf)

![](Images/SpectralMaps/H13CO_10_FDS_uvtaper_025arcsec_region_spectra_2.pdf)

![](Images/SpectralMaps/H13CO_FullDS_contsub_05arcsec_140kl_smth15arcsec_smll30arcsec_region_spectra_2.pdf)

## Line profile modeling

In this case, as none of the transitions present a resolved hyperfine structure, the opacity of the line could not be obtained by modeling the line profile and only the peak velocity and velocity dispersion maps (as $\sigma$) are presented. The resulting maps for DCO$^{+}$ (J=3-2), H$^{13}$CO$^+$ (J=1-0), and H$^{13}$CO$^+$ (J=3-2) are shown in Figs. [11](#fig:dco_lineMod), [12](#fig:h13co_10_lineMod), and [13](#fig:h13co_32_lineMod). For the three tracers, the two separated velocity components occupy different regions of the source, indicating that they are probing gas with different motions. The morphology of the two components is similar for the three tracers, but it is slightly different from the fitting obtained with the C$^{17}$O (Fig. 5 in (cite: Cabedo2021b)), where the redshifted component is almost always present in the C$^{17}$O spectra.

Peak velocity value (top panels of Figs. [11](#fig:dco_lineMod), [12](#fig:h13co_10_lineMod) and [13](#fig:h13co_32_lineMod)) ranges are similar for all molecules (from $\sim$8 to 9 km s$^{-1}$), although the blueshifted component goes to slightly lower velocities for H$^{13}$CO$^+$ (J=3-2), being the lowest velocities $\sim$7.8 km s$^{-1}$. This decrease occurs toward the southeastern region of the core, at $\sim$5$''$ from the center. We attribute this to the presence of the third velocity component produced by outflow contamination observed in Fig. [10](#fig:h13co_32_spectralMap), which produces a bad model of the line profile. No gradient indicating rotation is observed in the velocity maps for any tracer.

Velocity dispersion (bottom panels of Figs. [11](#fig:dco_lineMod), [12](#fig:h13co_10_lineMod) and [13](#fig:h13co_32_lineMod)) ranges are also similar for all tracers (from 0.1 to 0.5 km s$^{-1}$). However, there are some main differences: velocity dispersion is generally larger for H$^{13}$CO$^+$ (J=3-2) with average values of $\sim$0.4 km s$^{-1}$, whereas for DCO$^{+}$ (J=3-2) and H$^{13}$CO$^+$ (J=1-0) mean values are around $\sim$ 0.25 km s$^{-1}$. Very large values of the velocity dispersion ($>$0.5 km s$^{-1}$) are observed in the same southeastern region of the blueshifted component of H$^{13}$CO$^+$ (J=3-2) which is a consequence of the poor fitting due to the third velocity component. Values for the velocity dispersion are generally larger for the blueshifted than for the redshifted velocity component, indicating the two components trace gas with different kinematics, i.e., different infall velocities are affected differently by turbulence. For all tracers and both velocity components, the velocity dispersion increases toward the center, as the temperature rises. This increase is smaller for the H$^{13}$CO$^+$ (J=1-0) emission (up to $\sim$0.35 km s$^{-1}$) than for the DCO$^{+}$ (J=3-2) and H$^{13}$CO$^+$ (J=3-2) (up to $\sim$0.5 km s$^{-1}$) indicating that H$^{13}$CO$^+$ (J=1-0) traces gas at colder temperatures and further to the center of the source.

In general, there is good agreement between the values obtained for DCO$^{+}$ (J=3-2) and H$^{13}$CO$^+$ (J=3-2), both for peak velocity and velocity components. Considering that we are tracing similar scales, this confirms that both tracers are tracing similar gas. However, C$^{17}$O presents some differences with respect to H$^{13}$CO$^+$ (J=1-0) which indicates that they are tracing slightly different gas, C$^{17}$O tracing warmer and denser gas closer to the protostar.

![](Images/LineModeling/dco_fitMaps_restr.pdf)

![](Images/LineModeling/h13co_10_uvtaper_025as_fit_maps_restr.pdf)

![](Images/LineModeling/h13co_fitMaps_restr.pdf)

# Estimation of the opacity effects

As the line profile modeling does not allow us to obtain the line opacities, we estimated the optical depth using the dust continuum emission and the molecular abundances in order to determine the impact on the parameters derived from the line modeling. We first compute the H$_{2}$ column density map from the dust continuum emission map at 110 GHz (shown in Fig. [1](#fig:intensity_maps)), assuming its emission is optically thin (e.g., tracing the full column density) and applying the following standard abundances: \[C$^{17}$O\] = 5$\times$10$^{-8}$ (cite: Thomas2008), \[DCO$^{+}$\] = 10$^{-11}$ and \[H$^{13}$CO$^+$\] = 10$^{-10}$ (cite: Jorgensen2004). Figure [14](#fig:opacities_110GhzCont) shows the expected optical depth maps for the four different molecular lines we obtain with this method. Values of the optical depth are generally low ($<$ 1), although they increase to larger values for all tracers in the central beam. We note that, as we are considering a constant temperature for the derivation of the H$_{2}$ column density, which is likely higher at the center, the H$_{2}$ column density values in the central compact source are probably smaller, and we are overestimating the optical depth in that region. It can be seen that both transitions of H$^{13}$CO$^+$ present larger values of optical depth than both C$^{17}$O (J=1-0) and DCO$^{+}$ (J=3-2). We acknowledge that these large values can potentially affect our deuteration measurements toward the central beam, but stress that the small optical depth values found in DCO$^{+}$ confirm that the two velocity components are not mainly produced by self-absorption effects. Outside of that central beam, the expected line opacities are generally smaller than 1, so we found no need for applying an opacity correction to our data.

![](Images/Opacity/from-110GHzCont_dco_h13co_c17o_od.pdf)

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Integrate molecular line emission over emitting velocity ranges to create moment 0 maps; extract pixel-by-pixel spectra and fit two independent velocity components simultaneously at each pixel using HfS.",
  "failed_quote": "We derived the integrated intensity maps by integrating the molecular line emission over the velocity range in which it is emitting (the velocity range used for each molecule is shown in Table [table:ImageChar])."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Constant dust and gas excitation temperature of 25 K; standard dust properties and gas-to-dust ratio of 100.",
  "failed_quote": "We use Eq. [eq:colDens] to estimate the observed CO column density $N_{\\rm CO} = N_{\\rm C^{17}O} f_{\\rm C^{17}O}$ from the C$^{17}$O emission map shown in Fig. 1, assuming an excitation temperature of 25 K."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Single spherically symmetric infall / self-absorption origin for double-peaked profiles: rejected because optically thin lines (like DCO+ and C17O) show the same two spatially separated velocity components.",
  "failed_quote": "we stress that the small optical depth values found in DCO$^{+}$ confirm that the two velocity components are not mainly produced by self-absorption effects."
 }
]
```
