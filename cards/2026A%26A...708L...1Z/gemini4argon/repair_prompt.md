# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...708L...1Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Benchmarking pre-main sequence stellar evolutionary tracks using disk-based dynamical stellar masses

# Introduction

Theoretical models of star formation and pre-main sequence (PMS) evolution are fundamental for deriving the physical properties of Young Stellar Objects (YSOs). The positions of YSOs on the Hertzsprung-Russell (HR) diagram provide the main pathway to estimate stellar masses and ages for entire populations. These quantities are central to studies of star and planet formation and the evolution of protoplanetary disks (e.g., (cite: 2000ApJ...540..255P; 2008ASPC..384..200H; 2011ApJ...738..140H; 2012ApJ...746..154P; 2022ApJ...930...39V; Manara_2023; Ratzenbock_2023a)). Accurate YSO masses are also important on large samples, since several fundamental parameters, such as mass accretion rate and protoplanetary disk mass, scale with stellar mass ((cite: 2003ApJ...592..266M; Andrews_2013; Ansdell_2017)) and are required to derive accretion rates themselves ((cite: 2016ARA&A..54..135H)). Ages are particularly difficult to constrain ((cite: 2014prpl.conf..219S)) and, when inferred from evolutionary models, are strongly model dependent. More accurate ages from theoretical models would enable direct comparisons with other timescale indicators, thereby improving our understanding of the dynamics and physics of the processes involved in star formation (e.g., Lithium depletion or cluster expansion, (cite: 2022A&A...659A..85F) and (cite: 2024NatAs...8..216M), respectively).

Since the seminal works of (cite: 1961PASJ...13..450H) and (cite: 1965ApJ...142..841H), PMS models have progressively incorporated a wide range of physical components, including convection, atmospheric evolution, accretion history, rotation, magnetic fields, opacities, and cold stellar spots. Benchmarking these models with independent measurements is needed to improve their physics and define the stellar mass and age ranges where they work best (e.g., (cite: Simon_2000; Simon_2017; Simon_2019; Rosenfeld_2012; Guilloteau_2014; Czekala_2016; Yen_2018; Sheehan_2019)). In this work we compare stellar masses derived from protoplanetary disk rotation, i.e. “dynamical” masses independent of stellar evolutionary models, with stellar masses predicted by modern PMS evolutionary models using observed effective temperatures and luminosities. Specifically, we test the models of (cite: Baraffe2015), (cite: Feiden2016) (non-magnetic and magnetic), PARSEC v2.0 ((cite: Nguyen_2022)), (cite: Siess_2000), and SPOTS ((cite: Somers_2020), with different cold photospheric spot coverages). This comparison provides a direct benchmark of their predictive power and the relevance of their underlying physics.

# Sample

The targets were selected based on the availability of accurate dynamical masses, reliable stellar parameters, and precise *Gaia* parallaxes ($\varpi/\sigma(\varpi)>10$). The parent sample comprises 37 disks in the Upper Scorpius region from (cite: Carpenter2025), for which (cite: Zallio_2026) measured dynamical stellar masses modeling ALMA Band 7 $^{12}$CO $J = 3-2$ visibilities.

We excluded from the sample four disks with poorly constrained rotational profiles, and two multiple systems. We then excluded from our analysis four sources for which the moderate angular resolution prevented reliable constraints on the height of the CO emitting layer (the red sources in Fig. [2](#fig:M*_comparison)), together with a cloud-absorbed disk with an inconsistent dynamical mass ($M_{\star,\mathrm{dyn}}\sim1.4\> M_\odot$, but spectral type M2). The final sample is composed of 20 sources from the sample above that have well-determined stellar properties, which were derived from broad-band flux-calibrated medium-resolution spectra (Empey et al., in prep.) derived from VLT/X-Shooter and analyzed with `FRAPPE` ((cite: Claes_2024), based on (cite: Manara_2013)). These spectra are well-suited for young stars because they allow a better modeling of veiling, extinction, and spectral type for the targets (e.g., (cite: Herczeg_2014; Manara_2013; Manara_2020; Manara_2023)).

# Derivation of dynamical and evolutionary model–based stellar masses

The $^{12}$CO $J=3-2$ visibility modeling is described in detail in (cite: Zallio_2026). In brief, the analysis involved fitting a parametric model to ALMA visibilities using the `csalt` software[^2] (Andrews et al., in prep.), and sampling the posterior distribution with `emcee` ((cite: Foreman_2013)). A key free parameter in these models is the stellar mass, which sets the rotational velocity field of the disk and is thus directly constrained by the data. Since the statistical uncertainties reported from (cite: Zallio_2026) are unrealistically small, in Appendix [7](#appendix:masses) we describe how we assign uncertainties to these dynamical stellar mass measurements, denoted $M_{\star,\text{dyn}}$.

![](pictures/masses/violin_median_mass_ratios_with_points.png)

In addition to these dynamical masses, we derive stellar masses from the HR diagram ($M_{\star,\text{HRD}}$) using the effective temperatures $(T_{\text{eff}})$ and stellar luminosities $(L_\star)$ presented in Empey et al. (in prep.) for different PMS evolutionary models. In particular, we used the evolutionary models presented in (cite: Baraffe2015), the magnetic[^3] and non-magnetic tracks presented in (cite: Feiden2016), the PARSEC v2.0 tracks presented in (cite: Nguyen_2022), the tracks from (cite: Siess_2000), and the stellar SPOTS tracks presented in (cite: Somers_2020) with five different cold stellar spots fractional coverages of the stellar surface ($f=0\%$, $f=17\%$, $f=34\%$ $f=51\%$, and $f=85\%$). To extract stellar masses and ages (together with their uncertainties), we used the `python` package `ysoisochrone` developed by (cite: Deng_2025), based on the `IDL` code developed by (cite: Pascucci_2016), which uses a Bayesian inference approach. The HR grids used in this work are publicly available in the last version of `ysoisochrone`[^4]. More details and the HR diagrams for each model are presented in Appendix [8](#appendix:hrds) (see Fig. [4](#fig:hrd_spots_085)). In Table [2](#Table:masses_total) we show the collection of stellar masses used and derived in this work.

# Comparison of $M_{\star,\text{dyn}}$ and $M_{\star,\text{HRD}}$

In Figs. [1](#fig:violin) and [2](#fig:M*_comparison) we compare the dynamical stellar masses ($M_{\star,\text{dyn}}$) with the different evolutionary model-based stellar masses ($M_{\star,\text{HRD}}$). The fraction of sources with consistent mass estimates is reported as a percentage (see Fig. [2](#fig:M*_comparison)), providing a quantitative measure of consistency between the dynamical stellar masses and the stellar masses provided by each evolutionary model. In addition to the fraction of sources in agreement, we quantify the typical offset between dynamically-derived stellar masses and theoretical track-inferred stellar masses by computing the median mass ratio: $\langle R \rangle = \langle M_{\star,\text{dyn}} / M_{\star,\text{HRD}} \rangle$ where the median is taken over all sources included in the comparison. This ratio provides a robust, dimensionless measure of systematic differences: $\langle R \rangle \sim 1$ indicates that the evolutionary model predictions are consistent with the dynamical masses, while values smaller than or greater than unity indicate systematic over- or underestimation, respectively (see Figs. [1](#fig:violin), [2](#fig:M*_comparison)).

![](pictures/masses/Mcsalt_vs_isochrones_grid_3x3.png)

Each pre-main sequence evolutionary model covers a different mass range, as illustrated in the HR diagrams of Fig. [4](#fig:hrd_spots_085). To ensure a fair comparison among the models, we report the percentage of agreement and the median mass ratio $\langle R \rangle$ only for sources with a defined mass value in all evolutionary models (i.e., within the mass range $0.1 < M_\star < 1.3 \> M_\odot$). We also evaluated the fraction of sources with consistent mass estimates and $\langle R \rangle$ including upper and lower limits, and found that, apart from minor variations, the results remain unchanged.

# Results

Figs. [1](#fig:violin) and [2](#fig:M*_comparison) show that the best match with dynamical stellar masses is provided by the SPOTS pre-main sequence tracks with $f=17\%$ cold spot coverage ($100\%$ agreement within $\pm1\sigma$, where $\sigma$ is the quadratic sum of the model and dynamical mass uncertainties) in the stellar range $0.1-1.3$ $M_{\odot}$. Indeed, several authors (e.g., (cite: Grankin_2008), (cite: Gully-Santiago_2017), (cite: Gangi_2022), (cite: Facundo_2023; Facundo_2024)) invoked moderate to extreme filling factors ($f\sim17 - 90\%$) to model the spectra of Class II sources. (cite: Fang_2025) concluded that $f\sim34 - 51\%$ spot coverage was needed to achieve consistent age estimates across spectral types. We find that $f=17\%$ works better at predicting stellar masses than higher fractional spot coverages. SPOTS models with $f=17\%$ (constant for all the mass range of considered YSOs) predict stellar masses that are in between the measurements of (cite: Feiden2016) non-magnetic and magnetic tracks. When the stellar spot fraction increases (e.g., $f=51\%$, $f=85\%$; Fig. [2](#fig:M*_comparison)), the percentage of agreement decreases ($33\%$ for $f=51\%$, and $13\%$ for $f=85\%$). The SPOTS models with $f=0\%$ behave similarly to the tracks of (cite: Baraffe2015) and (cite: Feiden2016) non-magnetic (see Fig. [1](#fig:violin)), and have a percentage of agreement of $87\%$, similar to that of the (cite: Feiden2016) magnetic tracks.

The tracks of (cite: Baraffe2015) and (cite: Feiden2016) non-magnetic tracks give almost-identical mass measurements, and the same percentage of agreement ($93\%$), though both underestimate the dynamical stellar masses by $15\%$ and $12\%$, respectively. When considering (cite: Feiden2016) magnetic tracks, the percentage of agreement slightly decreases to $87\%$, and the evolutionary model-based stellar masses tend to overestimate the masses derived from disk rotation up to $20\%$.

Other works in the literature have compared the (cite: Feiden2016) magnetic and non-magnetic tracks. For example, (cite: Simon_2019) reported that the magnetic tracks of (cite: Feiden2016) work better than the non-magnetic ones in the stellar range $0.4-1.0$ $M_{\odot}$. (cite: Braun_2021) reported instead that the magnetic tracks work better than the non-magnetic ones in the stellar range $0.6-1.3$ $M_{\odot}$. Moreover, (cite: Towner_2025) recently showed that the magnetic tracks of (cite: Feiden2016) work best for stellar masses $M_\star\leq 1$ $M_{\odot}$, while the non-magnetic ones underestimate the dynamical masses by $\gtrsim25\%$. Our findings suggest that, on average, the agreement in the stellar range $0.1-1.3$ $M_{\odot}$ is similar among the two, but on average the magnetic tracks overestimate the dynamical masses by $\sim20\%$, while the non-magnetic ones underestimate the formers by $\sim 12\%$.

The evolutionary model-based stellar masses from the PARSEC v2.0 tracks show an agreement of $53\%$ with the masses from disk rotation, lower than what is found for other tracks. This result is expected, as the PARSEC v2.0 tracks were first developed for evolved and massive stars, and were then extended towards lower stellar mass values. The tracks of (cite: Siess_2000) give an agreement of $80\%$, worse than (cite: Baraffe2015) and (cite: Feiden2016), but better than those of PARSEC v2.0, and underestimate the dynamical stellar masses by $\sim26\%$.

To assess whether the mass discrepancies exhibit a stellar-mass dependence, we computed Spearman rank correlation coefficients between $(M_{\star,\rm{HRD}} - M_{\star,\rm{dyn}})/M_{\star,\rm{dyn}}$ and $M_{\star,\rm{dyn}}$. Most models show no statistically significant correlation ($p>0.05$), but PARSEC v2.0 and SPOTS models with $f\geq51\%$ display a negative correlation (Spearman coefficient $\rho\leq-0.77$, with $p<10^{-3}$), implying a significant mass-dependent bias.

One limitation of our analysis lies in the assumption of purely Keplerian rotation (including the dependence on the disk’s vertical height) within protoplanetary disks. This simplification neglects the impact of pressure gradients and the disk’s self-gravity, which can modify the velocity field. For instance, (cite: Andrews_2024) and (cite: Longarini_2025) demonstrated that deviations from Keplerian motion induced by pressure support can alter the inferred mass of the central object by as much as $5-10\%$. However, due to the limited angular ($0.1-0.3^{\prime\prime}$) and spectral ($\sim480$ ms$^{-1}$) resolution of the data presented in (cite: Carpenter2025), we emphasize that such deviations remain undetectable, and were therefore not considered in the analysis.

In Appendix [9](#appendix:mass_priors) we demonstrate how age estimates can be improved by prior knowledge of dynamical stellar masses. The comparison shown in Fig. [5](#fig:mass_prior) illustrates that incorporating mass priors from the analysis of (cite: Zallio_2026) can shift the ages inferred from HR diagram fitting with the SPOTS $f=17\%$ tracks by approximately $25\%$ when considering single sources, a result consistent with previous findings (e.g., (cite: Rosenfeld_2012)). In Fig. [6](#fig:ages) we show the distribution of inferred ages for the Upper Scorpius sources from each set of evolutionary tracks considered in this work, reporting the median value and highlighting how the choice of model leads to significantly different median age estimates. Finally, in Fig. [7](#fig:ages_prior), we show that when a prior on the stellar mass is considered for HR diagram fitting, the median inferred ages across different tracks become much more consistent, and the scatter among different evolutionary tracks reduces from $3.4$ Myr to $0.8$ Myr, an improvement $\gtrsim77\%$.

# Conclusions

By comparing accurate measurements of $^{12}$CO disk rotation with stellar masses derived from HR diagrams, we conclude:

1.  The SPOTS evolutionary tracks of (cite: Somers_2020) with $f=17\%$ best reproduce ($100\%$ agreement within $\pm1\sigma$ uncertainties) the dynamical stellar masses in the stellar range $0.1-1.3$ $M_{\odot}$.

2.  On average, the HR diagram masses derived using the magnetic tracks of (cite: Feiden2016), PARSEC v2.0 ((cite: Nguyen_2022)), and SPOTS ((cite: Somers_2020)) with $f=34\%$, $51\%$, $85 \%$ overestimate the dynamical masses by $\sim20\%$, $\sim21\%$, $\sim20\%$, $\sim27\%$, $\sim32\%$, respectively. Those provided by the tracks of (cite: Baraffe2015), (cite: Feiden2016) non-magnetic, (cite: Siess_2000) and SPOTS with $f=0\%$ underestimate them by $\sim15\%$, $\sim12\%$, $\sim26\%$, $\sim10\%$, respectively.

3.  When using stellar dynamical masses as mass priors for HR diagram fitting, the median inferred ages across different tracks become consistent, and the scatter decreases by $\gtrsim77\%$, while individual ages can vary by up to $\sim25\%$. For our sample, we evaluate a median age of $6.8$ Myr, with a scatter of $0.8$ Myr across the ten evolutionary tracks considered.

Since evolutionary models have a strong time-dependent aspect, our comparison demonstrates the consistency of disk-based stellar masses with HR diagram predictions at the age of Upper Scorpius ($4-14$ Myr, (cite: Ratzenbock_2023a; Ratzenbock_2023b)). Whether this agreement holds at different ages remains to be tested, and will be explored, for example, with the DEC/O Large Program for the younger ages.

# Data availability

Table [2](#Table:masses_total) is available in electronic form at the CDS via anonymous ftp to cdsarc.u-strasbg.fr (130.79.128.5) or via <http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/>, and on `GitHub`[^5].

# Acknowledgements

We thank the anonymous referee for their careful reading of the manuscript and constructive suggestions. L.Z., M.V. and G.R. are grateful to F. Pérez-Paolino and J. Bary for their important suggestions on pms evolutionary tracks, and to C. Pincon and A. Bressan for their feedback on interpreting the age distributions predicted by different evolutionary models. L.Z. and G.R. acknowledge support from the European Union (ERC Starting Grant DiscEvol, project number 101039651), and from Fondazione Cariplo, grant No. 2022-1217. C.F.M. is funded by the European Union (ERC, WANDA, 101039452). Views and opinions expressed are, however, those of the authors only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them. T.P.C. was supported by the Heising-Simons Foundation through a 51 Pegasi b Fellowship. Support for C.J.L. was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51535.001-A. This paper acknowledges the usage of ALMA data (project codes 2011.0.00526.S, 2012.1.00688.S, 2013.1.00395.S, 2018.1.00564.S), and VLT/X-Shooter spectra (project codes 097.C-0378, 0101.C-0866, 105.2082.003, 113.26NN.001, 113.26NN.003, 115.27XL.001).

# Author Affiliations

1.  **Dipartimento di Fisica ‘Aldo Pontremoli’**, Università degli Studi di Milano, via G. Celoria 16, I-20133 Milano, Italy.

2.  **European Southern Observatory**, Karl-Schwarzschild-Strasse 2, D-85748 Garching bei München, Germany.

3.  **Center for Astrophysics  Harvard & Smithsonian**, 60 Garden Street, Cambridge, MA 02138, USA.

4.  **University College Dublin (UCD)**, Department of Physics, Belfield, Dublin 4, Ireland.

5.  **Joint ALMA Observatory**, Avenida Alonso de Córdova 3107, Vitacura, Santiago, Chile.

6.  **Lunar and Planetary Laboratory, the University of Arizona**, Tucson, AZ 85721, USA.

7.  **Max Planck Institute for Extraterrestrial Physics**, Giessenbachstrasse 1, D-85748 Garching, Germany.

8.  **Max-Planck-Institut fur Astronomie (MPIA)**, Konigstuhl 17, 69117 Heidelberg, Germany.

9.  **Department of Astronomy, University of Virginia, Charlottesville**, VA 22904, USA.

10. **Institute of Astronomy, University of Cambridge**, Madingley Road, Cambridge, CB3 0HA, UK.

11. **Department of Astronomy, University of Michigan**, 1085 South University Avenue, Ann Arbor, MI 48109, USA.

12. **Department of Earth, Atmospheric, and Planetary Sciences, Massachusetts Institute of Technology**, Cambridge, MA 02139, USA.

13. **Univ. Grenoble Alpes, CNRS, IPAG**, F-38000 Grenoble, France.

14. **Academia Sinica Institute of Astronomy and Astrophysics**, 11F of Astronomy-Mathematics Building, AS/NTU, No.1, Sec 4, Roosevelt Rd, Taipei 106216, Taiwan.

# Uncertainties on the dynamical mass measurements due to inclination, stellar mass, and disk size

Since the stellar mass statistical uncertainties reported by (cite: Zallio_2026) are systematically underestimated due to limitations of fitting visibilities with parametric models, we decide to test the accuracy of the `csalt` dynamical mass measurements by creating and fitting a grid of numerical simulations. After creating `mcfost`[^6] ((cite: Pinte_2006; Pinte_2009)) radiative transfer models of $^{12}$CO $J=3-2$, we use built-in routines of `csalt` to transform them into radio-interferometric observed data, using the same total integration time ($\sim180$ s per disk), S/N, and antenna configurations of the observations analyzed in (cite: Zallio_2026), from the sample of (cite: Carpenter2025)). Our grid of models tests the accuracy of mass inferences for stars with masses of $1$, $0.5$, and $0.05$ $M_{\odot}$ to explore stellar mass values down to the sub-stellar range, with disks inclined at 8°, 30°, and 55°. We perform these simulations using a gas disk mass of $10^{-2}\>M_\star$, a dust disk mass of $10^{-4}\>M_\star$, and three different cut-off radii ($R_{\rm{c}}=5, 20, 50$ au), mimicking unresolved (less than 3 resolution elements in the diameter), resolved (between 3 and 5 resolution elements in the diameter), and extended (more than 5 resolution elements in the disk diameter) protoplanetary disk extension. These three cases correspond to a disk size[^7] $R_{90\%}<50$ au, $50\lesssim R_{90\%}\lesssim 90$ au, and $R_{90\%}>90$ au for the observations studied in (cite: Zallio_2026). We then perform fits using `csalt` with the parametric prescription A (see (cite: Zallio_2026); this is a complete disk prescription, which also considers for the emitting height of the optically thick $^{12}$CO layer) on the synthetic observation we created. Most of our fits return results in agreement with the true stellar mass, except for the sources with inc $=55$°, as shown in Fig. [3](#fig:McFost_models), where the discrepancy is $\sim10\%$ in the worst case.

![](pictures/McFost_plots/McFost_inc_vs_mstar_Rc_ALL_NOISY_subplot.png)

We use the statistical uncertainties returned by our fits per specific stellar mass range to assign mass uncertainties to the stellar dynamical masses reported in (cite: Zallio_2026). We evaluate the mean statistical uncertainty for each stellar bin and for each disk size (reported in the third column of Table [1](#table:M_*_uncertainty)) of the uncertainties returned from the `csalt` fits. This choice is motivated by the fact that the mean statistical uncertainties are found to be greater than the systematic uncertainty, and we therefore opt for a conservative approach. Then, we assign these uncertainties to our observations, as illustrated in Table [1](#table:M_*_uncertainty), using the disk sizes reported in (cite: Zallio_2026).

| Disk size $(R_{90\%})$ $[\text{au}]$ | $M_{\star,\text{dyn}}$ $[M_{\odot}]$ | Uncertainty $[M_{\odot}]$ |
|:---|:--:|---:|
|  | $M_\star\leq0.05$ | $0.03$ |
| $R_{90\%}\leq50$ | $0.05<M_\star\leq0.50$ | $0.15$ |
|  | $M_\star>0.50$ | $0.30$ |
|  | $M_\star\leq0.05$ | $0.02$ |
| $50<R_{90\%}\leq90$ | $0.05<M_\star\leq0.50$ | $0.10$ |
|  | $M_\star>0.50$ | $0.17$ |
|  | $M_\star\leq0.05$ | $0.03$ |
| $R_{90\%}>90$ | $0.05<M_\star\leq0.50$ | $0.15$ |
|  | $M_\star>0.50$ | $0.11$ |

: Table showing the logic used to assign the uncertainties to the dynamical stellar masses.

# HR diagrams

In Fig. [4](#fig:hrd_spots_085), we show the HR diagrams connected to the different evolutionary tracks used in this work. Since each model has a different validity based on different stellar ranges, some sources are found to fall outside (or very close to the edges of) the tracks. In these cases, it is not possible to derive masses and ages from HR diagram fitting using `ysoisochrone`. We highlight in orange the sources for which it was impossible to derive mass and age, while we show in red the five sources we exclude from the analysis, as reported in Sect. [2](#sec:data). The stellar masses are listed in Table [2](#Table:masses_total).

![image](pictures/HRDs/Baraffe+15.png) ![image](pictures/HRDs/Feiden,noB.png) ![image](pictures/HRDs/Feiden,B.png) ![image](pictures/HRDs/PARSECv2.0.png) ![image](pictures/HRDs/Siess+2000.png) ![image](pictures/HRDs/SPOTS,f=0.png)

![image](pictures/HRDs/SPOTS,f=17.png) ![image](pictures/HRDs/SPOTS,f=34.png) ![image](pictures/HRDs/SPOTS,f=51.png) ![image](pictures/HRDs/SPOTS,f=85.png)

# Stellar ages and the consequences of a prior on the stellar mass

## The impact of stellar mass priors on the age of single objects

Using `ysoisochrone`, we test how providing a prior on the stellar mass changes the results of HR diagram fitting (following what was done previously in the literature, e.g. (cite: Rosenfeld_2012)). In Fig. [5](#fig:mass_prior) (left), we show the result of HR diagram fitting using the SPOTS $f=17\%$ tracks ((cite: Somers_2020)) on one of the sources of our sample: the posterior distribution of age and mass is quite wide.

![image](pictures/mass_prior_test/J16395577-2347355_noprior.png) ![image](pictures/mass_prior_test/J16395577-2347355_prior.png)

When including a gaussian mass prior based on the dynamical mass and its associated uncertainty, the age-mass degeneracy reduces greatly, as shown in Fig. [5](#fig:mass_prior) (right). In the case of J16395577-2347355 (one of the most discrepant sources when considering SPOTS $f=17\%$) we show that the inferred median age changes by $\sim25\%$. When extending this analysis to the whole sample considered with SPOTS $f=17\%$, the median age changes from $6.3$ to $7$ Myr, as further shown in Figs. [6](#fig:ages), [7](#fig:ages_prior).

## Age distributions for different evolutionary tracks

In Fig. [6](#fig:ages), we present the age distributions derived from the HR diagram fits performed with `ysoisochrone`, without applying any mass priors. These distributions are based on the posterior ages obtained for each source. The visualization was produced using the `seaborn` package ((cite: Waskom2021)), which implements Kernel Density Estimation (KDE)[^8] to provide a smooth representation of the underlying probability density. The resulting distributions show substantial differences among the ten evolutionary models considered. The median age across the models is $\sim6.5$ Myr, with a scatter of $\sim3.4$ Myr.

Figure [7](#fig:ages_prior) displays the corresponding age distributions obtained after including priors on the stellar dynamical masses. When the mass prior is introduced, the differences among the distributions become notably smaller. The median age across the ten evolutionary tracks increases slightly to $\sim6.8$ Myr, while the scatter between the tracks decreases to $\sim0.8$ Myr.

![](pictures/ages/age_comparison.png)

![](pictures/ages/age_comparison_prior.png)

This result can be explained as follows. The dominant timescale for pre-main sequence stars is the Kelvin-Helmholtz timescale[^9], since the nuclear fusion has not started yet (see e.g., (cite: Hartmann_1998)). The stellar radius is fixed by knowing both $T_{eff}$ and $L_\star$, thus when we consider a prior on the stellar masses, we force the ages to converge to a fixed value.

| Source (2MASS) | $M_{\star,\texttt{dyn}}$ \[$M_{\odot}$\] | Baraffe+15 \[$M_{\odot}$\] | Feiden+16, no B \[$M_{\odot}$\] | Feiden+16, B \[$M_{\odot}$\] | PARSEC v2.0 \[$M_{\odot}$\] | Siess+2000 \[$M_{\odot}$\] | SPOTS $f=0\%$ \[$M_{\odot}$\] | SPOTS $f=17\%$ \[$M_{\odot}$\] | SPOTS $f=34\%$ \[$M_{\odot}$\] | SPOTS $f=51\%$ \[$M_{\odot}$\] | SPOTS $f=85\%$ \[$M_{\odot}$\] |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| J15583692-2257153 | $0.67 \pm 0.11$ | $>1.30$ | $1.64^{+0.47}_{-0.18}$ | $>1.70$ | $1.60^{+0.46}_{-0.17}$ | $1.74^{+0.21}_{-0.15}$ | $>1.30$ | $>1.30$ | $>1.30$ | $>1.30$ | $>1.30$ |
| J16035793-1942108 | $0.52 \pm 0.10$ | $0.42^{+0.15}_{-0.11}$ | $0.43^{+0.15}_{-0.10}$ | $0.64^{+0.19}_{-0.12}$ | $0.67^{+0.06}_{-0.09}$ | $0.37^{+0.11}_{-0.08}$ | $0.44^{+0.17}_{-0.12}$ | $0.51^{+0.16}_{-0.11}$ | $0.66^{+0.15}_{-0.12}$ | $0.69^{+0.16}_{-0.10}$ | $0.76^{+0.15}_{-0.07}$ |
| J16052157-1821412 | $1.12 \pm 0.11$ | $1.12^{+0.26}_{-0.19}$ | $0.96^{+0.22}_{-0.18}$ | $1.32^{+0.20}_{-0.09}$ | $0.88^{+0.18}_{-0.15}$ | $1.20^{+0.31}_{-0.16}$ | $1.12^{+0.17}_{-0.19}$ | $1.17^{+0.11}_{-0.15}$ | $>1.30$ | $>1.30$ | $>1.30$ |
| J16062861-2121297 | $0.53 \pm 0.10$ | $0.47^{+0.16}_{-0.11}$ | $0.47^{+0.15}_{-0.11}$ | $0.72^{+0.21}_{-0.12}$ | $0.70^{+0.05}_{-0.08}$ | $0.43^{+0.12}_{-0.10}$ | $0.49^{+0.19}_{-0.13}$ | $0.56^{+0.16}_{-0.13}$ | $0.72^{+0.17}_{-0.12}$ | $0.76^{+0.17}_{-0.10}$ | $0.81^{+0.10}_{-0.07}$ |
| J16095933-1800090 | $0.18 \pm 0.15$ | $0.20^{+0.04}_{-0.03}$ | $0.19^{+0.10}_{-0.04}$ | $0.28^{+0.05}_{-0.04}$ | $0.38^{+0.12}_{-0.06}$ | $0.20^{+0.04}_{-0.03}$ | $0.19^{+0.04}_{-0.03}$ | $0.22^{+0.04}_{-0.03}$ | $0.26^{+0.05}_{-0.04}$ | $0.35^{+0.08}_{-0.05}$ | $0.55^{+0.08}_{-0.07}$ |
| J16101264-2104446 | $1.23 \pm 0.11$ | $1.12^{+0.26}_{-0.19}$ | $0.96^{+0.22}_{-0.18}$ | $1.32^{+0.20}_{-0.09}$ | $0.86^{+0.17}_{-0.14}$ | $1.20^{+0.31}_{-0.16}$ | $1.12^{+0.17}_{-0.19}$ | $1.17^{+0.11}_{-0.15}$ | $>1.30$ | $>1.30$ | $>1.30$ |
| J16123916-1859284 | $0.60 \pm 0.11$ | $0.52^{+0.17}_{-0.12}$ | $0.54^{+0.16}_{-0.12}$ | $0.76^{+0.20}_{-0.10}$ | $0.71^{+0.09}_{-0.06}$ | $0.48^{+0.12}_{-0.11}$ | $0.55^{+0.16}_{-0.12}$ | $0.71^{+0.18}_{-0.13}$ | $0.76^{+0.15}_{-0.11}$ | $0.78^{+0.18}_{-0.08}$ | $0.83^{+0.08}_{-0.06}$ |
| J16140792-1938292 | $1.20 \pm 0.17$ | $>1.30$ | $1.33^{+0.16}_{-0.12}$ | $1.48^{+0.22}_{-0.13}$ | $1.30^{+0.16}_{-0.11}$ | $1.38^{+0.13}_{-0.12}$ | $>1.30$ | $>1.30$ | $>1.30$ | $>1.30$ | $>1.30$ |
| J16145024-2100599 | $0.67 \pm 0.11$ | $0.50^{+0.16}_{-0.11}$ | $0.51^{+0.15}_{-0.11}$ | $0.81^{+0.21}_{-0.12}$ | $0.70^{+0.14}_{-0.09}$ | $0.49^{+0.14}_{-0.10}$ | $0.52^{+0.18}_{-0.13}$ | $0.60^{+0.19}_{-0.13}$ | $0.78^{+0.20}_{-0.15}$ | $0.83^{+0.19}_{-0.12}$ | $0.89^{+0.11}_{-0.08}$ |
| J16152752-1847097 | $0.59 \pm 0.11$ | $0.52^{+0.17}_{-0.12}$ | $0.54^{+0.16}_{-0.12}$ | $0.78^{+0.20}_{-0.10}$ | $0.71^{+0.09}_{-0.06}$ | $0.48^{+0.12}_{-0.11}$ | $0.55^{+0.17}_{-0.12}$ | $0.71^{+0.18}_{-0.13}$ | $0.76^{+0.17}_{-0.11}$ | $0.79^{+0.16}_{-0.09}$ | $0.85^{+0.17}_{-0.06}$ |
| J16181445-2319251 | $0.21 \pm 0.15$ | $0.14^{+0.02}_{-0.02}$ | $<0.10$ | $0.22^{+0.04}_{-0.03}$ | $0.32^{+0.15}_{-0.07}$ | $<0.10$ | $<0.10$ | $0.19^{+0.04}_{-0.03}$ | $0.22^{+0.04}_{-0.03}$ | $0.26^{+0.04}_{-0.04}$ | $0.45^{+0.09}_{-0.07}$ |
| J16202291-2227041 | $0.39 \pm 0.10$ | $0.32^{+0.06}_{-0.05}$ | $0.32^{+0.06}_{-0.05}$ | $0.44^{+0.08}_{-0.06}$ | $0.55^{+0.08}_{-0.06}$ | $0.30^{+0.04}_{-0.03}$ | $0.32^{+0.07}_{-0.05}$ | $0.39^{+0.08}_{-0.06}$ | $0.46^{+0.08}_{-0.06}$ | $0.56^{+0.10}_{-0.06}$ | $0.71^{+0.10}_{-0.03}$ |
| J16202863-2442087 | $0.72 \pm 0.11$ | $0.51^{+0.16}_{-0.11}$ | $0.52^{+0.15}_{-0.12}$ | $0.79^{+0.23}_{-0.12}$ | $0.70^{+0.14}_{-0.09}$ | $0.49^{+0.14}_{-0.10}$ | $0.52^{+0.18}_{-0.14}$ | $0.60^{+0.17}_{-0.13}$ | $0.78^{+0.20}_{-0.13}$ | $0.83^{+0.17}_{-0.11}$ | $0.89^{+0.18}_{-0.06}$ |
| J16203960-2634284 | $0.55 \pm 0.11$ | $0.47^{+0.16}_{-0.11}$ | $0.47^{+0.15}_{-0.11}$ | $0.72^{+0.21}_{-0.12}$ | $0.70^{+0.05}_{-0.08}$ | $0.43^{+0.12}_{-0.10}$ | $0.49^{+0.19}_{-0.13}$ | $0.56^{+0.16}_{-0.13}$ | $0.72^{+0.17}_{-0.12}$ | $0.76^{+0.17}_{-0.10}$ | $0.81^{+0.10}_{-0.07}$ |
| J16215472-2752053 | $0.84 \pm 0.11$ | $0.83^{+0.19}_{-0.11}$ | $0.84^{+0.17}_{-0.09}$ | $0.91^{+0.09}_{-0.08}$ | $0.77^{+0.05}_{-0.07}$ | $0.83^{+0.22}_{-0.11}$ | $0.85^{+0.17}_{-0.09}$ | $0.87^{+0.18}_{-0.08}$ | $0.89^{+0.11}_{-0.08}$ | $0.91^{+0.09}_{-0.06}$ | $0.95^{+0.22}_{-0.08}$ |
| J16221532-2511349 | $0.47 \pm 0.15$ | $0.37^{+0.14}_{-0.10}$ | $0.38^{+0.14}_{-0.10}$ | $0.52^{+0.15}_{-0.12}$ | $0.64^{+0.08}_{-0.09}$ | $0.34^{+0.10}_{-0.07}$ | $0.39^{+0.21}_{-0.11}$ | $0.45^{+0.17}_{-0.12}$ | $0.54^{+0.17}_{-0.12}$ | $0.66^{+0.17}_{-0.11}$ | $0.72^{+0.11}_{-0.06}$ |
| J16230761-2516339 | $0.37 \pm 0.10$ | $0.39^{+0.12}_{-0.10}$ | $0.40^{+0.19}_{-0.10}$ | $0.47^{+0.16}_{-0.09}$ | $0.53^{+0.12}_{-0.05}$ | $0.30^{+0.10}_{-0.08}$ | $0.43^{+0.16}_{-0.10}$ | $0.49^{+0.13}_{-0.09}$ | $0.52^{+0.11}_{-0.07}$ | $0.55^{+0.11}_{-0.05}$ | $0.58^{+0.04}_{-0.04}$ |
| J16253798-1943162 | $0.72 \pm 0.11$ | $0.72^{+0.17}_{-0.11}$ | $0.73^{+0.15}_{-0.09}$ | $0.78^{+0.09}_{-0.07}$ | $0.71^{+0.11}_{-0.05}$ | $0.69^{+0.20}_{-0.12}$ | $0.72^{+0.17}_{-0.09}$ | $0.76^{+0.15}_{-0.08}$ | $0.78^{+0.18}_{-0.07}$ | $0.79^{+0.08}_{-0.07}$ | $0.83^{+0.10}_{-0.07}$ |
| J16293267-2543291 | $0.45 \pm 0.10$ | $0.35^{+0.12}_{-0.09}$ | $0.38^{+0.14}_{-0.10}$ | $0.52^{+0.15}_{-0.12}$ | $0.57^{+0.16}_{-0.12}$ | $0.35^{+0.09}_{-0.07}$ | $0.28^{+0.10}_{-0.13}$ | $0.44^{+0.19}_{-0.12}$ | $0.51^{+0.18}_{-0.12}$ | $0.68^{+0.19}_{-0.14}$ | $0.78^{+0.16}_{-0.08}$ |
| J16395577-2347355 | $0.38 \pm 0.15$ | $0.40^{+0.14}_{-0.10}$ | $0.41^{+0.13}_{-0.10}$ | $0.62^{+0.18}_{-0.13}$ | $0.62^{+0.11}_{-0.10}$ | $0.38^{+0.10}_{-0.09}$ | $0.43^{+0.22}_{-0.11}$ | $0.49^{+0.19}_{-0.13}$ | $0.56^{+0.16}_{-0.14}$ | $0.74^{+0.17}_{-0.12}$ | $0.81^{+0.16}_{-0.09}$ |
| Excluded (red; 2MASS) | $M_{\star,\texttt{dyn}}$ \[$M_{\odot}$\] | Baraffe+15 \[$M_{\odot}$\] | Feiden+16, no B \[$M_{\odot}$\] | Feiden+16, B \[$M_{\odot}$\] | PARSEC v2.0 \[$M_{\odot}$\] | Siess+2000 \[$M_{\odot}$\] | SPOTS $f=0\%$ \[$M_{\odot}$\] | SPOTS $f=17\%$ \[$M_{\odot}$\] | SPOTS $f=34\%$ \[$M_{\odot}$\] | SPOTS $f=51\%$ \[$M_{\odot}$\] | SPOTS $f=85\%$ \[$M_{\odot}$\] |
| J15583620-1946135 | $0.07 \pm 0.15$ | $0.32^{+0.06}_{-0.05}$ | $0.32^{+0.06}_{-0.05}$ | $0.44^{+0.08}_{-0.06}$ | $0.55^{+0.08}_{-0.06}$ | $0.30^{+0.04}_{-0.03}$ | $0.32^{+0.07}_{-0.05}$ | $0.39^{+0.08}_{-0.06}$ | $0.46^{+0.08}_{-0.06}$ | $0.56^{+0.10}_{-0.06}$ | $0.71^{+0.10}_{-0.03}$ |
| J16132190-2136136 | $0.59 \pm 0.30$ | $0.36^{+0.14}_{-0.09}$ | $0.38^{+0.14}_{-0.10}$ | $0.51^{+0.15}_{-0.11}$ | $0.64^{+0.08}_{-0.11}$ | $0.34^{+0.10}_{-0.07}$ | $0.38^{+0.20}_{-0.11}$ | $0.45^{+0.18}_{-0.12}$ | $0.52^{+0.17}_{-0.13}$ | $0.68^{+0.16}_{-0.11}$ | $0.74^{+0.15}_{-0.07}$ |
| J16222982-2002472 | $1.37 \pm 0.17$ | $0.38^{+0.12}_{-0.09}$ | $0.41^{+0.14}_{-0.10}$ | $0.60^{+0.17}_{-0.13}$ | $0.55^{+0.18}_{-0.11}$ | $0.40^{+0.10}_{-0.08}$ | $0.35^{+0.10}_{-0.08}$ | $0.37^{+0.12}_{-0.15}$ | $0.54^{+0.20}_{-0.13}$ | $0.62^{+0.18}_{-0.15}$ | $0.87^{+0.18}_{-0.11}$ |
| J16271273-2504017 | $1.15 \pm 0.17$ | $0.52^{+0.17}_{-0.12}$ | $0.54^{+0.16}_{-0.12}$ | $0.76^{+0.20}_{-0.10}$ | $0.71^{+0.09}_{-0.06}$ | $0.48^{+0.12}_{-0.11}$ | $0.55^{+0.16}_{-0.12}$ | $0.71^{+0.18}_{-0.13}$ | $0.76^{+0.15}_{-0.11}$ | $0.78^{+0.18}_{-0.08}$ | $0.83^{+0.08}_{-0.06}$ |
| J16274905-2602437 | $0.20 \pm 0.10$ | $0.52^{+0.17}_{-0.12}$ | $0.54^{+0.16}_{-0.12}$ | $0.78^{+0.20}_{-0.10}$ | $0.71^{+0.09}_{-0.06}$ | $0.48^{+0.12}_{-0.11}$ | $0.55^{+0.17}_{-0.12}$ | $0.71^{+0.18}_{-0.13}$ | $0.76^{+0.17}_{-0.11}$ | $0.79^{+0.16}_{-0.09}$ | $0.85^{+0.17}_{-0.06}$ |

: Table containing the stellar masses considered in this work. The disk-based dynamical masses were taken from (cite: Zallio_2026). The full table is available in the online material in machine-readable form and on `GitHub`[^[4](#footnote:github)^](#footnote:github).

[^1]: NASA Hubble Fellowship Program Sagan Fellow

[^2]: <https://github.com/seanandrews/csalt>

[^3]: As reported by the author on the `GitHub` page, the magnetic tracks available on <https://github.com/gfeiden/MagneticUpperSco> are incorrect for ages $\leq1$ Myr, containing numerical artifacts, which we corrected by interpolating the data and removing the outliers.

[^4]: <https://github.com/DingshanDeng/ysoisochrone>; the specific version (v1.3.3) used in this work is archived on Zenodo at <https://zenodo.org/records/18420752>

[^5]: <https://github.com/lzallio/Benchmarking_PMS_tracks>

[^6]: <https://github.com/cpinte/mcfost>

[^7]: We consider the radius that encompasses $90\%$ of the disk total flux $R_{90\%}$ as the gas disk radius.

[^8]: The Kernel Density Estimation (KDE) is a non-parametric method used to estimate the probability density function (PDF) of a continuous variable from a finite sample.

[^9]: The Kelvin-Helmholtz timescale is the time over which a star radiates away its gravitational potential energy at its current luminosity: $\tau_{KH} \sim GM_\star^2 / R_\star L_\star$, where $G$ is the gravitational constant, $M_\star$ the mass of the star, $R_\star$ its radius and $L_\star$ its luminosity.

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Feiden (2016) magnetic tracks for ages <= 1 Myr were corrected by interpolating data and removing numerical artifact outliers",
  "failed_quote": "As reported by the author on the `GitHub` page, the magnetic tracks available on https://github.com/gfeiden/MagneticUpperSco are incorrect for ages $\\leq1$ Myr, containing numerical artifacts, which we corrected by interpolating the data and removing the outliers."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Table 2 is publicly available at CDS and on GitHub (https://github.com/lzallio/Benchmarking_PMS_tracks); HR grids are public in ysoisochrone v1.3.3 on GitHub and Zenodo.",
  "failed_quote": "Table 2 is available in electronic form at the CDS via anonymous ftp to cdsarc.u-strasbg.fr (130.79.128.5) or via http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/, and on `GitHub`."
 }
]
```
