# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...710A..63L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Constraining the magnetic field strength of a flaring radio core in the compact steep spectrum source 3C 138

Compact steep spectrum (CSS) sources generally show weak Doppler boosting, yet some exceptions show multi-year-scale radio flux variability and high-energy activity. Since 2022, the CSS quasar 3C 138 has been in a radio high state accompanied by multiple gamma-ray outbursts, offering unique opportunities to study changes in jet physical conditions.

We estimated the synchrotron self-absorption (SSA) magnetic field ($B_{\rm SSA}$) in the SSA core of 3C 138 during its high state and compared it with the equipartition magnetic field ($B_{\rm eq}$) to assess the core field environment.

Using extended Korean Very long-baseline interferometry Network (KVN) data at 22, 43, 86, and 129 GHz (2024–2025), we calibrated the visibilities and modeled resolved components with circular Gaussians. A single-zone SSA model fitted to the core spectrum provided the turnover frequency and peak flux density, from which we estimated the $B_{\rm SSA}$ and $B_{\rm eq}$. We used Very Large Array and Atacama Large Millimeter/submillimeter Array data to constrain the broadband spectra with the same model.

The KVN SSA core shows a turnover at about 33 GHz and a peak flux of about 1.45 Jy. The inferred $B_{\rm SSA}$ is far below equipartition, with $B_{\rm SSA}/B_{\rm eq}\approx0.05$.

The flux variability of 3C 138 is driven by a compact, particle-dominated core. Shock-driven particle injection in the inner jet could account for the core brightening and the production of X-ray/gamma-ray emissions through an inverse-Compton process without requiring extreme relativistic beaming effects.

# Introduction

Compact steep spectrum (CSS) sources represent a category of radio-loud active galactic nuclei with projected sizes smaller than 20 kpc and steep spectra ($\alpha<-0.5$, $S_{\nu}\propto\nu^{\alpha}$) above a few hundred megahertz (cite: fanti1989). They are generally interpreted as young radio sources in early evolutionary stages (e.g., younger than $10^5$ years), though their compactness may also be explained by confinement within a dense interstellar medium with a $N_ {\rm H}$ of approximately $10^{21}$–$10^{24}$ cm$^{-2}$ (cite: o2021).

Consistent with weak Doppler boosting, most CSS objects show only modest radio variability (approximately 10% on approximately 1 year timescales; (cite: o1998compact)). Yet on multi-year timescales, quasars within the CSS class can exhibit marked flux-density and spectral changes (e.g., 3C 216, B1828+487, 3C 380, and 3C 138; (cite: torniainen2005long)). A population study has shown that the few known gamma-ray-bright young radio sources are predominantly quasars and occupy a blazar-like locus in the photon-index versus gamma-ray-luminosity plane, favoring a jet origin for the high-energy emission. In these objects, the radio output is dominated by the core and the approaching jet (cite: principe2021gamma). Taken together, these results point to evolving physical conditions in compact, inner regions of CSS quasars.

The CSS quasar 3C 138 ($z=0.759$; (cite: hewitt1989first)) is one such case, showing both radio variability and detected high-energy activity. 3C 138 is a well-known amplitude and polarization calibrator (cite: perley2017accurate). On kiloparsec scales it shows a highly polarized, one-sided jet extending approximately 400 mas northeastward to a bright hot spot. Very long-baseline interferometry (VLBI) studies have revealed superluminal motion in the inner jet (cite: shen2001superluminal), strong Faraday rotation, and a nonuniform Faraday screen near the core (cite: cotton2003faraday), indicating an active nucleus embedded in a complex environment. These properties make 3C 138 a suitable laboratory for testing how the physical conditions within the core (e.g., the magnetic field strength) behave during variability.

Since 2022, 3C 138 has entered an enhanced activity phase across multiple bands. RATAN-600 monitoring shows a steady flux increase at 11–22 GHz, with pronounced rises at 11.2 and 22.3 GHz in 2024–2025 (cite: atel17104). Very Large Array (VLA) data indicate that the flux density is substantially elevated relative to historical levels, with the enhancement reaching factors of about 2 near 22 GHz, 3 near 33 GHz, and 4 near 45 GHz (cite: perley2017accurate). Meanwhile, the *Fermi* Large Area Telescope (cite: Atwood2009) detected gamma-ray flares from 3C 138, accompanied by enhanced X-ray emission (cite: atel17142), in 2024 October and 2025 May (cite: atel16845; atel17180). These contemporaneous radio and high-energy changes point to renewed energization in the inner jet and motivated a focused examination of the core’s magnetic field environment.

In this paper we present the first simultaneous VLBI imaging of 3C 138 in its flaring phase at 22, 43, 86, and 129 GHz with the Korean VLBI Network (KVN). From these multifrequency data we identify the synchrotron self-absorption (SSA) core and estimate its magnetic field strength ($B_{\rm SSA}$). We compare $B_{\rm SSA}$ with the equipartition estimate $B_{\rm eq}$ and use the ratio $B_{\rm SSA}/B_{\rm eq}$ to assess whether the core is dominated by particles or magnetic field energy. We then discuss what this inferred energy balance implies for the origin of the radio brightening and its connection to the high-energy activity. The adopted cosmology is $H_{0} = 67.8~{\rm km~s^{-1}~Mpc^{-1}}$, $\Omega_{\rm m} = 0.308$, and $\Omega_{\rm \Lambda} = 0.692$ (cite: wright2006). At $z = 0.759$, 1 mas corresponds to 7.58 pc, and $1~{\rm mas~yr^{-1}} = 43.5~c$.

# Observations and data reduction

## KVN observations

We conducted simultaneous VLBI observations at 22, 43, 86, and 129 GHz on 2024 December 12 and 2025 January 10 with the extended KVN, which comprises the original three 21 m antennas (Yonsei, Ulsan, and Tamna) plus KVN Pyeongchang (KPC). The addition of KPC increased the total number of baselines to six, enabling amplitude self-calibration and improving image fidelity. Each three-hour session consisted of eight 15-minute scans (about 2 h on source) and used right-circular polarization (RCP) only. The data were correlated with DiFX (December 2024) and a GPU-based correlator (January 2025), then calibrated in the Astronomical Image Processing System (cite: greisen2003aips) with a KVN pipeline (cite: hodgson2016automatic). Interferometric imaging and circular two-dimensional Gaussian model fitting were performed with Difmap (cite: shepherd1997difmap). For image total flux density, we used 10% (22/43 GHz), 20% (86 GHz), and 30% (129 GHz) uncertainties (cite: lee2016interferometric). Any potential bias from circular polarization in the RCP-only mode is expected to be negligible compared to these amplitude-scale uncertainties. Uncertainties of the Gaussian model parameters were estimated following (cite: Fomalont1999) and (cite: lee2008global).

## Archive data

To capture total flux variations, including large-scale jet emission, we used VLA data (1–50 GHz) from the observing-support test project TCAL0009 (PI: Lorant Sjouwerman) and processed the data with the Common Astronomy Software Applications pipeline, version 6.5.4 (cite: mcmullin2007casa; 2022PASP..134k4501C). We focused on four epochs (2022 March 20, 2023 July 1, 2024 December 20, and 2025 January 19). For 2022 and 2023, we selected the first A-configuration observation from each year, while the 2024 and 2025 data were chosen to be contemporaneous with the two KVN observations. We also used the Atacama Large Millimeter/submillimeter Array (ALMA) Calibrator Source Catalogue[^1] (cite: kneissl2023operational), which provides well-calibrated flux estimates for standard ALMA calibrators, thereby extending our spectral coverage to the millimeter/submillimeter regime (approximately $97.5$–$343$ GHz). Complementing our KVN analysis, we used three higher-resolution Very Long Baseline Array (VLBA) epochs at 23.5 GHz (2022 December 14, 2024 June 18, and 2025 June 21) from project UC003 (PI: Phillip Cigan) to trace the flux and structural evolution of the VLBA core and the inner jet.

# Results and analysis

## Multifrequency flux and morphology

We detected and imaged the target at 22, 43, and 86 GHz at both epochs. The 129 GHz image is available only for the first epoch due to poor weather. Representative images from 2024 December are shown in Fig. [1](#fig:kvn_image). Over the two epochs, the total CLEAN flux at 22–86 GHz shows at most modest month-scale variability, with no statistically significant change (Table [1](#tab:kvn_imgparam)).

Via Gaussian model fitting, we identified two components separated by about 5 mas, with the fainter eastern component lying to the southeast of the brighter western one at a position angle (PA) of about $105^\circ$ (Table [3](#tab:kvn_modelfit)). The eastern component is clearly resolved, with fitted sizes larger than the minimum resolvable size, whereas the western component is more compact and is constrained as an upper limit in some bands (cite: lobanov2005resolution). The component flux densities and most fitted component sizes remain consistent between the two epochs within the measurement uncertainties. The larger 86 GHz size of the western component in the second epoch is likely influenced mainly by poorer data quality and calibration effects. The 23.5 GHz VLBA results show two components with a similar separation and PA to those measured with the KVN (Fig. [5](#fig:vlba_image)). Unlike the eastern component, which remains approximately stable on year timescales, the western component brightened by a factor of about 2.6 from 2022 to 2025 (Table [5](#tab:vlba_modelfit)). On kiloparsec scales, VLA images reveal a northeastward jet with a PA of approximately $40^\circ$ to $60^\circ$ (Table [\[tab:vla_modelfit\]](#tab:vla_modelfit)), indicating a clear PA offset between the compact two-component structure and the extended jet. As shown in Fig. [6](#fig:VLA_flux_time), the VLA core brightens substantially toward the high-frequency bands from 2022 to 2025, while the jet flux varies only weakly. This behavior implies that the observed increase in the integrated VLA flux is dominated by the core component.

![](fig/3C138_KVN_22_2024-12-12.png)

![](fig/3C138_KVN_43_2024-12-12.png)

![](fig/3C138_KVN_86_2024-12-12.png)

![](fig/3C138_KVN_129_2024-12-12.png)

+:-----:+:-------:+:---------------:+:-----------:+:--------:+:--------------:+:-------:+:-:+
| Band  | Freq    | $S_{\rm CLEAN}$ | $S_{\rm p}$ | $\sigma$ | Beam size      | Beam PA |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| \(1\) | \(2\)   | \(3\)           | \(4\)       | \(5\)    | \(6\)          | \(7\)   |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| 2024 December 12                                                                      |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| K     | 21.801  | $1.61 \pm 0.16$ | 1.29        | 1.1      | $6.7\times3.5$ | $-76.9$ |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| Q     | 43.346  | $1.70 \pm 0.17$ | 1.37        | 0.6      | $3.7\times1.7$ | $-73.8$ |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| W     | 86.436  | $1.15 \pm 0.23$ | 1.03        | 1.7      | $1.8\times0.8$ | $-74.2$ |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| D     | 129.398 | $1.11 \pm 0.33$ | 0.90        | 4.5      | $1.0\times0.6$ | $-66.1$ |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| 2025 January 10                                                                       |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| K     | 21.801  | $1.45 \pm 0.14$ | 1.17        | 0.8      | $6.8\times4.2$ | $-70.7$ |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| Q     | 43.346  | $1.52 \pm 0.15$ | 1.23        | 1.2      | $3.7\times2.1$ | $-72.2$ |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+
| W     | 86.436  | $1.14 \pm 0.23$ | 0.95        | 1.7      | $1.8\times0.9$ | $-70.7$ |   |
+-------+---------+-----------------+-------------+----------+----------------+---------+---+

: KVN image parameters.

Table notes: Column designations: (1) observing band, (2) central frequency in GHz, (3) total CLEAN flux density with its uncertainty in Jy, (4) peak flux density in Jy beam$^{-1}$, (5) image noise level in mJy beam$^{-1}$, (6) synthesized beam size in mas $\times$ mas, and (7) beam position angle in degrees.

## Spectral analysis

The simultaneous four-band KVN observations enabled us to determine the spectra of the two components and identify the core. Figure [2](#fig:KVN_spectrum) presents the spectra of the first epoch. The western component exhibits an apparently flatter spectrum than the eastern one, with an inverted slope between 22 and 43 GHz, which is characteristic of an SSA core. We therefore fitted the eastern component with a single power law (PL), $S_\nu \propto \nu^{\alpha}$, where $\alpha$ is the spectral index, and modeled the western component with a single-zone SSA model (cite: turler2000modelling): $$\begin{equation}
S_\nu = S_{\rm m} \left(\frac{\nu}{\nu_{\rm m}}\right)^{\alpha_{\rm t}}
\frac{1-\exp\left[-\,\tau_{\rm m}\left(\nu /\nu_{\rm m}\right)^{\alpha_{\rm t}-\alpha_0}\right]}
{1-\rm \exp\left(-\tau_m\right)}\,,
\end{equation}$$ where $\alpha_{\rm t}$ and $\alpha_0$ are the thick and thin spectral indices, and $\nu_{\rm m}$ and $S_{\rm m}$ are the SSA turnover frequency and peak flux density. The spectral fitting results for the two components are shown in Fig. [2](#fig:KVN_spectrum).

To probe the time variability of the broadband spectrum, we interpolated the ALMA flux densities using Gaussian-process (GP) regression, paired them with the four VLA epochs, and fitted the combined VLA+ALMA spectra with both a PL model and a PL+SSA model for each epoch. We then selected the preferred model by comparing the reduced $\chi^2$ and the Bayesian information criterion. As the two arrays are not simultaneous, and have unmatched angular resolutions, these fits should be interpreted with caution. The best-fit parameters are presented in Table [2](#tab:plssa_fits), and the fitting results are plotted in Fig. [7](#fig:vla-alma_fitting).

![](fig/core_jet_spectrum_SSA_f24sl01a_2024-12-12.png)

# Discussion

## SSA core spectrum and temporal evolution

The KVN western component shows a flat–inverted spectrum between 22 and 43 GHz and is well described by an SSA model, supporting its identification as the SSA core. The eastern feature follows a single steep PL, consistent with an optically thin inner jet component (Fig. [2](#fig:KVN_spectrum)).

For the VLA data, as shown in Fig. [7](#fig:vla-alma_fitting), a spectral inflection is detected only in 2024 and 2025, whereas the 2022–2023 spectra are adequately described by a single steep PL. This indicates a transition from a PL-only state to a PL+SSA state. Within the PL+SSA state, the optically thin slope ($\alpha_0$) of the SSA component further steepens, suggesting the high-energy electron population is evolving. If driven by a propagating shock, one would expect enhanced millimeter polarization, systematic electric vector position angle (EVPA) evolution, and higher-frequency light-curve peaks to precede those at lower frequencies.

Because the VLA flux increase is core-dominated (Sect. [3.1](#sec:flux)) and the VLA core blends the two KVN components, the integrated VLA+ALMA behavior can be used as a qualitative proxy for the SSA evolution of the KVN core. The turnover frequency inferred from VLA+ALMA is systematically higher than that from the KVN core, which may reflect residual mixing with optically thin emission and/or intrinsic inhomogeneity within the KVN core region, such that a one-zone SSA model yields an effective turnover frequency.

## Magnetic field strength

We estimated the SSA magnetic field strength and the equipartition magnetic field strength of the KVN core for the first epoch (2024 December 12) using the SSA spectral parameters listed in Fig. [2](#fig:KVN_spectrum), together with the SSA region size ($d_{\rm m}$) scaled from the bright-state VLBA core size and the Doppler factor ($\delta$) estimated from VLBA core variability (Appendix [6](#app:Bfield)).

We adopted $d_{\rm m}=0.07\pm0.01$ mas and $\delta_{\rm var}=2.36^{+0.35}_{-0.38}$, noting that $\delta_{\rm var}$ is an approximate constraint and likely a lower limit given the sparse temporal sampling and possible unresolved substructure. Using these parameters, we derived $B_{\rm SSA}=10.12^{+9.59}_{-5.11}$ mG and $B_{\rm eq}=200.77^{+44.08}_{-33.79}$ mG, which yields $B_{\rm SSA}/B_{\rm eq}=0.05^{+0.06}_{-0.03}\ll 1$. This indicates that the SSA core is particle-dominated.

The dominant uncertainty arises from $d_{\rm m}$ (scaled from the VLBA core size). We propagated uncertainties via Monte Carlo sampling, and we further tested the sensitivity of the result to the assumed geometric and opacity scalings by varying jet-opening index and the core-shift index within plausible ranges. In all cases, we obtain $B_{\rm SSA}/B_{\rm eq}\ll 1$ (Fig. [4](#fig:B_dependence)), so the particle-dominated conclusion is robust.

## Core brightening and high-energy emission

Multifrequency, multi-scale data show that the flux rise since 2022 is core-dominated (Fig. [6](#fig:VLA_flux_time)), meaning a kiloparsec-scale jet–interstellar medium interaction is likely not the primary driver of the integrated flux increase. VLBA images show a steady brightening of the western core, while the eastern knot and the kiloparsec-scale VLA jet remain nearly constant, pointing to processes within the VLBI core.

The KVN SSA core magnetic field strength is far below the equipartition value, implying a particle-dominated region and an increase in synchrotron emitting electrons, possibly associated with shock-driven particle acceleration. ALMA polarization monitoring further shows a gradual increase in polarized flux after 2022 (cite: kameno20253c), consistent with a more ordered magnetic field.

If a shock is responsible, a new component may be forming but still unresolved. Using the inverted minimum-resolvable-size relation, we find that the image rms required to resolve a separation of two KVN core sizes is 5.71, 19.1, 2.10, and 17.3 mJy at 22, 43, 86, and 129 GHz in the first epoch, and 0.8, 1.2, and 1.7 mJy in the second epoch at 22, 43, and 86 GHz, which is comparable to or higher than our achieved rms at each frequency at both epochs. Yet no new component is detected near the core, suggesting that any emerging feature remains blended with the core and has not reached a resolvable downstream separation.

Using the inferred $\delta_{\rm var}$, we estimate that the corresponding apparent speed is at most of order $2c$, corresponding to a proper motion of about $0.05$ mas yr$^{-1}$. Under a separability criterion of two VLBA core sizes (about $0.12$ mas), a newly emerging component would therefore require at least a few years to become clearly separated from the core. If the viewing angle is instead as large as $\theta=34^\circ$, as inferred by (cite: shen2001superluminal), then the corresponding separation timescale would be even longer.

Either case implies only mild Doppler boosting. Nevertheless, with efficient acceleration, inverse-Compton processes can produce X-ray to gamma-ray radiation under modest Doppler boosting, as suggested by *Fermi*-LAT detections of young radio galaxies and compact symmetric objects (cite: Migliori2016; principe2020ngc3894; principe2021gamma). Continued high-frequency, high-resolution polarization VLBI observations will allow us to test this scenario by constraining the emergence timescale of a new component and by tracking polarization and EVPA evolution in the core.

# Conclusion

Using two-epoch, four-band KVN imaging of the CSS source 3C 138, we identified the western of the two KVN-resolved components as the SSA core. The turnover frequency inferred from the integrated VLA+ALMA spectra is higher than that from the KVN core spectrum, which can be attributed to resolution blending of the compact core with additional emitting regions in the lower-resolution data. The multi-year radio brightening is core-dominated and the core magnetic field is below equipartition, implying a particle-dominated emitting region with only mild Doppler boosting. Shock-driven particle injection in the inner jet could account for the contemporaneous X-/gamma-ray emission without extreme beaming. Although no new knot is resolved, a slowly emerging feature may still be blended within the VLBI core. Continued high-frequency, high-resolution VLBI monitoring will be needed to test this scenario.

# Acknowledgements

We are grateful to the staff of the KVN who helped to operate the array and to correlate the data. The KVN and a high-performance computing cluster are facilities operated by the KASI (Korea Astronomy and Space Science Institute). The KVN observations and correlations are supported through the high-speed network connections among the KVN sites provided by the KREONET (Korea Research Environment Open NETwork), which is managed and operated by the KISTI (Korea Institute of Science and Technology Information). This work is supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (2020R1A2C2009003, RS-2025-00562700). The authors acknowledge use of the Very Long Baseline Array under the US Naval Observatory’s time allocation. This work supports USNO’s ongoing research into the celestial reference frame and geodesy. This work also made use of data from the Very Large Array operated by the National Radio Astronomy Observatory (NRAO). The NRAO and the Green Bank Observatory are facilities of the U.S. National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work makes use of ALMA data (ADS/JAO.ALMA#2011.0.00001.CAL). ALMA is a partnership of ESO, NSF (USA), and NINS (Japan), together with NRC (Canada), NSTC/ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

# Magnetic field strength estimates

This appendix provides the details of the magnetic-field calculations presented in Sect. [4.2](#sec:KVN_core_B).

## Size scaling for the SSA region

The 23.5 GHz VLBA core appears larger in the fainter epoch (2022) but becomes much smaller in the brighter epochs (2024–2025; Table [5](#tab:vlba_modelfit)). This behavior is consistent with the faint-state core being effectively broadened by blending of multiple sub-components within the finite VLBA resolution, whereas the bright-state emission is dominated by a more compact region. We therefore adopt the 2025 June VLBA core size ($d_{\rm VLBA}=0.06\pm0.01$ mas), measured in a bright-state epoch close in time to the KVN observations and with a well-constrained model fit (e.g., a fitted size exceeding the minimum resolvable size), as the reference size to scale the SSA region angular size $d_{\rm m}$, following $$\begin{equation}
d_{\rm m}
= 1.6\,d_{\rm VLBA}
\left(\frac{\nu_{\rm m}}{\nu_{\rm VLBA}}\right)^{-\epsilon/k_{\rm r}}~[\rm mas]\,,
\label{eq:dm_app}
\end{equation}$$ where the factor $1.6$ converts the full width at half maximum of a circular Gaussian component to the equivalent angular diameter of a uniform disk (cite: pearson1995), $\epsilon$ describes the jet opening ($\epsilon\simeq1$ for a conical jet and $\epsilon<1$ for a collimating flow), and $k_{\rm r}$ is the index that characterizes the frequency dependence of the core position, $r_{\rm core}\propto \nu^{-1/k_{\rm r}}$ (cite: lobanov1998ultracompact). We adopt $k_{\rm r}=1$ as a commonly used empirical value in core-shift scaling (cite: lobanov1998ultracompact), and the median $\epsilon$ value of 0.97 from (cite: algaba2017resolving).

## Variability Doppler factor

We estimate the variability Doppler factor from the temporal evolution of the VLBA core flux density $S(t)$ at 23.5 GHz. Following Eq. ([\[eq:tau_var\]](#eq:tau_var)), we fit the VLBA core light curve in log space with a least-squares method, $$\begin{equation}
\ln S = \ln S_0 + \frac{t-t_0}{\tau_{\rm var}}\,,
\label{eq:tau_var}
\end{equation}$$ where the fitted slope equals $1/\tau_{\rm var}$ (Fig. [3](#fig:tau_var)), and $\tau_{\rm var}$ is the variability timescale in days.

![](fig/VLBA_core_tvar_fit_letter.png)

We then estimate the observed variability brightness temperature $T_{\rm B}^{\rm var}$, assuming that the variability is dominated by a circular Gaussian emitting region (cite: kang2021): $$\begin{equation}
T_{\rm B}^{\rm var} = 4.077 \times 10^{13}
\left(\frac{D_{\rm L}}{\nu\,\tau_{\rm var}}\right)^2
\frac{\Delta S}{(1+z)^4}~{\rm K}\,,
\label{eq:tb_var}
\end{equation}$$ where $z$ is the redshift, $D_{\rm L}$ is the luminosity distance in Mpc, $\nu$ is the observing frequency in GHz, and $\Delta S$ (Jy) is the flux density difference between the peak and the value at peak/$e$.

Assuming an equipartition brightness temperature ($T_{\rm B,eq}$) as the maximum intrinsic brightness temperature, the variability Doppler factor can be estimated (cite: fuhrmann2008; hovatta2009; kang2021) as $$\begin{equation}
\delta_{\rm var} = (1+z)\left(\frac{T_{\rm B}^{\rm var}}{T_{\rm B,eq}}\right)^{1/3}\,.
\label{eq:delta_app}
\end{equation}$$ Here we adopt $T_{\rm B,eq}=5\times10^{10}$ K (cite: hovatta2009).

Given the sparse sampling of the VLBA core flux density (three epochs) and the possibility of unresolved substructure within the VLBA core, the derived $\tau_{\rm var}$ should be regarded as an upper limit. Consequently, $T_{\rm B}^{\rm var}$ and $\delta_{\rm var}$ are likely underestimated, and $\delta_{\rm var}$ should be treated as an approximate constraint and potentially a lower limit.

## Magnetic field strength formulae

Given $S_{\rm m}$, $\nu_{\rm m}$, and $\alpha_0$ from the SSA fit (Fig. [2](#fig:KVN_spectrum)), together with $d_{\rm m}$ and $\delta_{\rm var}$, we compute the SSA magnetic field strength from (cite: marscher1983accurate): $$\begin{equation}
B_{\rm SSA}=10^{-2}\,b(\alpha_0)\,
\left(\frac{S_{\rm m}}{\rm Jy}\right)^{-2}
\left(\frac{d_{\rm m}}{\rm mas}\right)^{4}
\left(\frac{\nu_{\rm m}}{\rm GHz}\right)^{5}
\left(\frac{\delta}{1+z}\right)^{-1}~[{\rm mG}]\,,
\label{eq:Bssa_app}
\end{equation}$$ where $b(\alpha_0)$ is a factor that depends on the optically thin spectral index, and $\delta$ is the Doppler factor.

The equipartition magnetic field strength is estimated following (cite: kataoka2005x): $$\begin{align}
B_{\rm eq} &= 1.23\times10^{-4}\,
\eta^{2/7}(1+z)^{11/7}
\left(\frac{D_{\rm L}}{100~{\rm Mpc}}\right)^{-2/7} \notag\\
&\quad\times
\left(\frac{\nu_{\rm m}}{5~{\rm GHz}}\right)^{1/7}
\left(\frac{S_{\rm m}}{100~{\rm mJy}}\right)^{2/7}
\left(\frac{10^3 d_{\rm m}}{0.3~{\rm arcsec}}\right)^{-6/7}
\delta^{-5/7}~{\rm [G]}\,,
\label{eq:Beq_app}
\end{align}$$ assuming $\eta=1$ (the ratio of proton + electron to electron energy densities).

The inferred $B_{\rm SSA}$ is proportional to $\delta^{-1}$, $B_{\rm eq}$ to $\delta^{-5/7}$, and thus $B_{\rm SSA}/B_{\rm eq}$ to $\delta^{-2/7}$. Since $\delta_{\rm var}$ is likely underestimated, the derived $B_{\rm SSA}$, $B_{\rm eq}$, and $B_{\rm SSA}/B_{\rm eq}$ should be interpreted as upper limits, subject to a corresponding systematic uncertainty.

## Uncertainty propagation and sensitivity tests

The dominant uncertainty in the magnetic field estimates arises from the SSA region angular size $d_{\rm m}$, which is scaled from the VLBA core size $d_{\rm VLBA}$ (Eq. [\[eq:dm_app\]](#eq:dm_app)). The VLBA core size $d_{\rm VLBA}$ at 23.5 GHz is obtained from circular Gaussian model fitting, and the statistical uncertainties of the fitted parameters are estimated from the post-fit image rms and the component signal-to-noise ratio using the first order approximation of (cite: Fomalont1999).

To account for the strong non-linearity of Eqs. ([\[eq:dm_app\]](#eq:dm_app))–([\[eq:Beq_app\]](#eq:Beq_app)), we propagated uncertainties via Monte Carlo sampling by drawing $S_{\rm m}$, $\nu_{\rm m}$ and $\alpha_0$ from the SSA-fit posterior and $d_{\rm VLBA}$ from its inferred distribution. In addition, we explored the impact of the geometric and opacity scalings in Eq. ([\[eq:dm_app\]](#eq:dm_app)) by varying the jet-opening index ($\epsilon$) and the core-shift index ($k_{\rm r}$) within plausible ranges (Fig. [4](#fig:B_dependence)).

![image](fig/BSSA_Beq_ratio_kr_2024-12-12_Tb.png) ![image](fig/BSSA_Beq_ratio_epsilon_2024-12-12_Tb.png)

# Additional images and plots

![](fig/0521+163_VLBA_23_2022-12-14.png)

![](fig/0521+163_VLBA_23_2024-06-18.png)

![](fig/0521+163_VLBA_23_2025-06-21.png)

![](fig/VLA_core_jet_flux_vs_time_22-25.png)

![](fig/total_flux_vla-alma_2022-03-20_cal_gp_pl_ssa_fix-alphat_cal_gp.png)

![](fig/total_flux_vla-alma_2023-07-01_cal_gp_pl_ssa_fix-alphat_cal_gp.png)

![](fig/total_flux_vla-alma_2024-12-20_cal_gp_pl_ssa_fix-alphat_cal_gp.png)

![](fig/total_flux_vla-alma_2025-01-19_cal_gp_pl_ssa_fix-alphat_cal_gp.png)

# Additional tables

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Obs. date | $\alpha_{\rm PL}$ | $S_{\rm m}$ | $\nu_{\rm m}$ | $\alpha_0$ |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) |
| 2022-03-20 | $-0.68\pm0.02$ | $\cdots$ | $\cdots$ | $\cdots$ |
| 2023-07-01 | $-0.63\pm0.01$ | $\cdots$ | $\cdots$ | $\cdots$ |
| 2024-12-20 | $-0.53\pm0.03$ | $0.62_{-0.25}^{+0.30}$ | $52.88_{-20.19}^{+28.84}$ | $-1.00_{-0.43}^{+0.20}$ |
| 2025-01-19 | $-0.50\pm0.03$ | $0.63_{-0.24}^{+0.22}$ | $70.61_{-29.53}^{+29.34}$ | $-1.39_{-0.40}^{+0.43}$ |

: PL+SSA fits to the VLA+ALMA spectra.

Table notes: Column designation: (1) Observing date, (2) spectral index of the PL component, (3) peak flux density (Jy) of the SSA component, corresponding (4) turnover frequency (GHz) and (5) optically thin spectral index.

+:-----:+:-------:+:-----:+:-----------------:+:-----------------:+:---------------:+:-----------------:+:----------:+:------------------:+:--------------:+
| Band  | Freq    | ID    | $S_{\rm tot}$     | Radius            | $\theta$        | $d$               | $d_{\min}$ | $\sigma_{\rm rms}$ | $S_{\rm peak}$ |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| \(1\) | \(2\)   | \(3\) | \(4\)             | \(5\)             | \(6\)           | \(7\)             | \(8\)      | \(9\)              | \(10\)         |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| 2024-12-12                                                                                                                                               |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| K     | 21.801  | W     | $1.193 \pm 0.136$ | $\cdots$          | $\cdots$        | $<0.312$          | 0.362      | 7.687              | 1.200          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |         | E     | $0.399 \pm 0.059$ | $5.115 \pm 0.047$ | $104.2 \pm 0.5$ | $0.891 \pm 0.094$ | 0.477      | 4.265              | 0.385          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| Q     | 43.346  | W     | $1.390 \pm 0.079$ | $\cdots$          | $\cdots$        | $0.277 \pm 0.011$ | 0.095      | 2.242              | 1.367          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |         | E     | $0.307 \pm 0.046$ | $5.176 \pm 0.030$ | $104.6 \pm 0.3$ | $0.548 \pm 0.060$ | 0.254      | 3.360              | 0.286          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| W     | 86.436  | W     | $1.027 \pm 0.059$ | $\cdots$          | $\cdots$        | $0.051 \pm 0.002$ | 0.046      | 1.671              | 1.025          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |         | E     | $0.125 \pm 0.019$ | $5.177 \pm 0.017$ | $104.6 \pm 0.2$ | $0.305 \pm 0.033$ | 0.124      | 1.363              | 0.115          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| D     | 129.398 | W     | $0.861 \pm 0.216$ | $\cdots$          | $\cdots$        | $<0.099$          | 0.123      | 26.369             | 0.878          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |         | E     | $0.137 \pm 0.037$ | $5.407 \pm 0.021$ | $104.5 \pm 0.2$ | $0.209 \pm 0.043$ | 0.143      | 4.868              | 0.121          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| 2025-01-10                                                                                                                                               |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| K     | 21.801  | W     | $1.080 \pm 0.119$ | $\cdots$          | $\cdots$        | $0.455 \pm 0.035$ | 0.391      | 6.468              | 1.081          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |         | E     | $0.357 \pm 0.058$ | $5.142 \pm 0.059$ | $103.8 \pm 0.6$ | $1.016 \pm 0.118$ | 0.584      | 4.592              | 0.345          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| Q     | 43.346  | W     | $1.237 \pm 0.087$ | $\cdots$          | $\cdots$        | $0.271 \pm 0.014$ | 0.129      | 3.044              | 1.223          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |         | E     | $0.233 \pm 0.044$ | $4.948 \pm 0.031$ | $105.9 \pm 0.4$ | $0.459 \pm 0.062$ | 0.348      | 4.033              | 0.226          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| W     | 86.436  | W     | $0.980 \pm 0.044$ | $\cdots$          | $\cdots$        | $0.170 \pm 0.005$ | 0.040      | 0.982              | 0.962          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |         | E     | $0.156 \pm 0.019$ | $5.333 \pm 0.015$ | $104.7 \pm 0.2$ | $0.346 \pm 0.030$ | 0.108      | 1.095              | 0.144          |
+-------+---------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+

: Model-fit parameters of the KVN components.

Table notes: Column designation: (1) observing band, (2) central frequency in GHz, (3) component identification: W–western component (core), E–eastern component (jet), (4) model flux density in Jy, (5) radius in mas, (6) PA in degrees, (7) component size in mas, (8) minimum resolvable size in mas, (9) uncertainty of post-fit rms in mJy, (10) peak flux density of the model in Jy beam$^{-1}$. Uncertainties correspond to 1$\sigma$ errors.

+:-----:+:-----:+:---------------:+:-----------:+:--------:+:--------------:+:-------:+
| Band  | Freq  | $S_{\rm CLEAN}$ | $S_{\rm p}$ | $\sigma$ | Beam size      | Beam PA |
+-------+-------+-----------------+-------------+----------+----------------+---------+
| \(1\) | \(2\) | \(3\)           | \(4\)       | \(5\)    | \(6\)          | \(7\)   |
+-------+-------+-----------------+-------------+----------+----------------+---------+
| 2022-12-14                                                                          |
+-------+-------+-----------------+-------------+----------+----------------+---------+
| K     | 23.5  | $0.54 \pm 0.08$ | 0.33        | 3.2      | $1.0\times0.6$ | 1.5     |
+-------+-------+-----------------+-------------+----------+----------------+---------+
| 2024-06-18                                                                          |
+-------+-------+-----------------+-------------+----------+----------------+---------+
| K     | 23.5  | $0.85 \pm 0.13$ | 0.70        | 5.0      | $2.5\times0.4$ | $-46.5$ |
+-------+-------+-----------------+-------------+----------+----------------+---------+
| 2025-06-21                                                                          |
+-------+-------+-----------------+-------------+----------+----------------+---------+
| K     | 23.5  | $1.18 \pm 0.18$ | 0.95        | 6.1      | $1.1\times0.3$ | $-9.9$  |
+-------+-------+-----------------+-------------+----------+----------------+---------+

: VLBA image parameters.

Table notes: Column designation: (1) observing band, (2) central frequency in GHz, (3) total CLEAN flux density with its uncertainty in Jy, (4) peak flux density in Jy beam$^{-1}$, (5) image noise level in mJy beam$^{-1}$, (6) synthesized beam size in mas $\times$ mas, and (7) beam PA in degrees.

+:-----:+:-----:+:-----:+:-----------------:+:-----------------:+:---------------:+:-----------------:+:----------:+:------------------:+:--------------:+
| Band  | Freq  | ID    | $S_{\rm tot}$     | Radius            | $\theta$        | $d$               | $d_{\min}$ | $\sigma_{\rm rms}$ | $S_{\rm peak}$ |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| \(1\) | \(2\) | \(3\) | \(4\)             | \(5\)             | \(6\)           | \(7\)             | \(8\)      | \(9\)              | \(10\)         |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| 2022-12-14                                                                                                                                             |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| K     | 23.5  | W     | $0.372 \pm 0.052$ | $\cdots$          | $\cdots$        | $0.223 \pm 0.023$ | 0.075      | 3.521              | 0.339          |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |       | E     | $0.187 \pm 0.041$ | $5.254 \pm 0.027$ | $104.9 \pm 0.3$ | $0.329 \pm 0.055$ | 0.121      | 4.241              | 0.156          |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| 2024-06-18                                                                                                                                             |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| K     | 23.5  | W     | $0.701 \pm 0.079$ | $\cdots$          | $\cdots$        | $<0.044$          | 0.072      | 4.428              | 0.703          |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |       | E     | $0.137 \pm 0.037$ | $5.216 \pm 0.031$ | $113.5 \pm 0.3$ | $0.290 \pm 0.062$ | 0.192      | 4.615              | 0.105          |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| 2025-06-21                                                                                                                                             |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
| K     | 23.5  | W     | $0.960 \pm 0.144$ | $\cdots$          | $\cdots$        | $0.056 \pm 0.006$ | 0.054      | 10.706             | 0.936          |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+
|       |       | E     | $0.207 \pm 0.073$ | $5.430 \pm 0.025$ | $106.1 \pm 0.3$ | $0.181 \pm 0.050$ | 0.137      | 11.682             | 0.164          |
+-------+-------+-------+-------------------+-------------------+-----------------+-------------------+------------+--------------------+----------------+

: Model-fit parameters of the VLBA components.

Table notes: Column designation: (1) observing band, (2) central frequency in GHz, (3) component identification: W–western component (core), E–eastern component (jet), (4) model flux density in Jy, (5) radius in mas, (6) PA in degrees, (7) component size in mas, (8) minimum resolvable size in mas, (9) uncertainty of post-fit rms in mJy, (10) peak flux density of the model in Jy beam$^{-1}$. Uncertainties correspond to 1$\sigma$ errors.

+:-----:+:------:+:---------------:+:-----------:+:--------:+:--------------------:+:-------:+:-:+
| Band  | Freq   | $S_{\rm CLEAN}$ | $S_{\rm p}$ | $\sigma$ | Beam size            | Beam PA |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| \(1\) | \(2\)  | \(3\)           | \(4\)       | \(5\)    | \(6\)                | \(7\)   |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| 2022-03-20                                                                                 |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| L     | 1.517  | $8.04 \pm 0.40$ | 7.88        | 6.1      | $1766.1\times1143.1$ | 65.6    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| S     | 3.045  | $5.56 \pm 0.28$ | 5.32        | 10.4     | $958.7\times649.2$   | 74.9    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| C     | 5.499  | $3.88 \pm 0.19$ | 3.59        | 9.4      | $728.4\times430.4$   | 76.4    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| X     | 8.999  | $2.71 \pm 0.14$ | 1.92        | 12.6     | $391.5\times229.6$   | 57.3    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| U     | 13.999 | $1.71 \pm 0.09$ | 1.21        | 9.7      | $271.0\times144.5$   | 56.8    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| K     | 22.199 | $1.27 \pm 0.19$ | 0.85        | 4.8      | $161.7\times92.3$    | 59.5    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| A     | 32.019 | $1.16 \pm 0.17$ | 0.68        | 5.3      | $109.6\times53.0$    | 72.1    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| Q     | 40.999 | $1.07 \pm 0.16$ | 0.62        | 1.8      | $66.8\times49.6$     | 51.1    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| 2023-07-01                                                                                 |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| L     | 1.517  | $7.85 \pm 0.39$ | 7.70        | 4.7      | $2132.8\times1160.7$ | 43.7    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| S     | 3.045  | $5.92 \pm 0.30$ | 5.39        | 8.5      | $855.4\times496.7$   | 49.4    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| C     | 5.499  | $4.22 \pm 0.21$ | 3.45        | 9.9      | $546.9\times382.3$   | 59.9    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| X     | 8.999  | $2.95 \pm 0.15$ | 2.08        | 13.2     | $393.5\times235.2$   | 56.1    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| U     | 13.999 | $2.39 \pm 0.12$ | 1.21        | 12.0     | $146.2\times118.4$   | 55.3    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| K     | 22.199 | $1.64 \pm 0.25$ | 0.95        | 6.2      | $128.4\times91.2$    | 60.6    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| A     | 32.019 | $1.25 \pm 0.19$ | 0.82        | 4.7      | $132.3\times56.2$    | 50.0    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| Q     | 40.999 | $1.21 \pm 0.18$ | 0.77        | 1.7      | $67.9\times52.7$     | 70.0    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| 2024-12-20                                                                                 |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| L     | 1.517  | $8.49 \pm 0.42$ | 8.31        | 6.9      | $2011.2\times1534.9$ | 19.3    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| S     | 3.045  | $5.86 \pm 0.29$ | 5.56        | 10.0     | $983.3\times702.7$   | 66.1    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| C     | 5.499  | $4.43 \pm 0.22$ | 3.91        | 16.8     | $656.3\times410.3$   | 65.9    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| U     | 13.999 | $2.53 \pm 0.13$ | 2.04        | 13.0     | $222.3\times152.9$   | 58.2    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| K     | 22.199 | $2.30 \pm 0.35$ | 1.76        | 6.5      | $121.2\times94.9$    | 53.4    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| A     | 32.019 | $2.13 \pm 0.32$ | 1.72        | 4.6      | $109.0\times68.7$    | 35.3    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| Q     | 40.999 | $2.29 \pm 0.34$ | 1.84        | 1.9      | $69.7\times49.9$     | 48.9    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| 2025-01-19                                                                                 |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| L     | 1.517  | $8.38 \pm 0.42$ | 8.14        | 5.7      | $1836.9\times1388.9$ | 39.5    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| S     | 3.045  | $5.90 \pm 0.29$ | 5.52        | 13.8     | $894.0\times652.6$   | 74.3    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| C     | 5.499  | $4.44 \pm 0.22$ | 3.97        | 18.2     | $684.6\times408.0$   | 73.8    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| U     | 13.999 | $2.72 \pm 0.14$ | 2.14        | 15.7     | $207.7\times140.9$   | 55.2    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| K     | 22.199 | $2.43 \pm 0.36$ | 1.87        | 5.3      | $115.0\times91.2$    | 52.2    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| A     | 32.019 | $2.33 \pm 0.35$ | 1.84        | 3.7      | $97.8\times69.2$     | 43.6    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+
| Q     | 40.999 | $2.45 \pm 0.37$ | 1.99        | 1.9      | $70.7\times52.5$     | 49.5    |   |
+-------+--------+-----------------+-------------+----------+----------------------+---------+---+

: VLA image parameters.

Table notes: Column designation: (1) observing band, (2) central frequency in GHz, (3) total CLEAN flux density with its uncertainty in Jy, (4) peak flux density in Jy beam$^{-1}$, (5) image noise level in mJy beam$^{-1}$, (6) synthesized beam size in mas $\times$ mas, and (7) beam PA in degrees.

[^1]: <https://almascience.eso.org/sc/>

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Scale 23.5 GHz VLBA core size to the SSA turnover frequency to get d_m; fit VLBA core light curve in log space to get variability timescale tau_var, T_B^var, and delta_var; compute B_SSA and B_eq and propagate uncertainties via Monte Carlo sampling.",
  "failed_quote": "To account for the strong non-linearity of Eqs. (2)–(7), we propagated uncertainties via Monte Carlo sampling by drawing $S_{\\rm m}$, $\\nu_{\\rm m}$ and $\\alpha_0$ from the SSA-fit posterior and $d_{\\rm VLBA}$ from its inferred distribution."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Least-squares fit to VLBA core light curve in log space; Monte Carlo sampling for magnetic field uncertainty propagation.",
  "failed_quote": "Following Eq. (3), we fit the VLBA core light curve in log space with a least-squares method,"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[1]",
  "value": "Least-squares fit to VLBA core light curve in log space; Monte Carlo sampling for magnetic field uncertainty propagation.",
  "failed_quote": "To account for the strong non-linearity of Eqs. (2)–(7), we propagated uncertainties via Monte Carlo sampling by drawing $S_{\\rm m}$, $\\nu_{\\rm m}$ and $\\alpha_0$ from the SSA-fit posterior and $d_{\\rm VLBA}$ from its inferred distribution."
 },
 {
  "path": "reasoning.why_this_method.evidence[1]",
  "value": "Gaussian-process regression interpolates non-simultaneous ALMA calibrator measurements to match VLA epochs; Monte Carlo sampling accounts for the strong non-linearity of the magnetic field equations.",
  "failed_quote": "To account for the strong non-linearity of Eqs. (2)–(7), we propagated uncertainties via Monte Carlo sampling by drawing $S_{\\rm m}$, $\\nu_{\\rm m}$ and $\\alpha_0$ from the SSA-fit posterior and $d_{\\rm VLBA}$ from its inferred distribution."
 }
]
```
