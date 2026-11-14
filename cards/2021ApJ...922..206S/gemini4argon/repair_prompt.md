# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...922..206S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# The detection of a hot molecular core in the extreme outer Galaxy

## Abstract

Interstellar chemistry in low metallicity environments is crucial to understand chemical processes in the past metal-poor universe. Here we report the first detection of a hot molecular core in the extreme outer Galaxy, which is an excellent laboratory to study star formation and interstellar medium in a Galactic low-metallicity environment. The target star-forming region, WB89-789, is located at the galactocentric distance of 19 kpc. Our ALMA observations have detected a variety of carbon-, oxygen-, nitrogen-, sulfur-, and silicon-bearing species, including complex organic molecules (COMs) containing up to nine atoms, towards a warm ($>$100 K) and compact ($<$ 0.03 pc) region associated with a protostar ($\sim$8 $\times$ 10$^3$ L$_{\ensuremath{\odot}}$). A comparison of fractional abundances of COMs relative to CH$_3$OH between the outer Galactic hot core and an inner Galactic counterpart shows a remarkable similarity. On the other hand, the molecular abundances in the present source do not resemble those of low-metallicity hot cores in the . The detection of another embedded protostar associated with high-velocity SiO outflows is also reported.

# Introduction

Understanding the star formation and interstellar medium (ISM) at low metallicity is crucial to unveil physical and chemical processes in the past Galactic environment or those in high-redshift galaxies, where the metallicity was significantly lower compared to the present-day solar neighborhood.

Hot cores are one of the early stages of star formation and they play a key role in the formation of chemical complexity of the ISM. Physically, hot cores are defined as having small source size (0.1 pc), high density (10$^6$ cm$^{-3}$), and warm gas/dust temperature (100 K) (cite: vanD98; Kur00). Chemistry of hot cores is characterized by sublimation of ice mantles, which accumulated in the course of star formation. In cold molecular clouds and prestellar cores, gaseous molecules and atoms are frozen onto dust grains. With increasing dust temperatures by star formation activities, chemical reaction among heavy species become active on grain surfaces to form larger complex molecules (cite: Gar06). In addition, sublimated molecules, such as CH$_3$OH and NH$_3$, are subject to further gas-phase reactions (cite: NM04; Taq16). As a result, warm and dense gas around protostars become chemically rich, and embedded protostars are observed as one of the most powerful molecular line emitters, which is called a hot core. They are important targets for astrochemical studies of star-forming regions, because a variety of molecular species, including complex organic molecules (COMs), are often detected in hot cores (cite: Her09). Thus detailed studies on chemical properties of hot cores are important for understanding complex chemical processes triggered by star formation.

Recent ALMA (Atacama Large Millimeter/submillimeter Array) observations of hot molecular cores in a nearby low metallicity galaxy, the Large Magellanic Cloud (LMC), have suggested that the metallicity has a significant effect on their molecular compositions (cite: ST16b; ST20; Sew18); cf., the metallicity of the LMC is $\sim$1/2-1/3 of the solar neighborhood. A comparison of molecular abundances between LMC and Galactic hot cores suggests that organic molecules (e.g., CH$_3$OH, a classical hot core tracer) show a large abundance variation in low-metallicity hot cores (cite: ST20). There are organic-poor hot cores that are unique in the LMC (cite: ST16b), while there are relatively organic-rich hot cores, where the abundances of organic molecules roughly scale with the metallicity (cite: Sew18). Astrochemical simulations for low-metallicity hot cores suggest that dust temperature during the initial ice-forming stage would play a key role for making the chemical diversity of organic molecules (cite: Ach18; ST20). On the other hand, sulfur-bearing molecules such as SO$_2$ and SO are commonly detected in known LMC hot cores and their molecular abundances scale with the metallicity of the LMC. Although the reason is still under debate, the results suggest that SO$_2$ can be an alternative molecular species to trace hot core chemistry in metal-poor environments.

The above results suggest that molecular abundances in hot cores do not always simply scale with the elemental abundances of their parent environments. However, it is still unclear if the observed chemical characteristics of LMC hot cores are common in other low metallicity environments or they are uniquely seen only in the LMC. Currently, known low-metallicity hot core samples are limited to those in the LMC. It is thus vital to understand universal characteristics of interstellar chemistry by studying chemical compositions of star-forming cores in diverse metallicity environments.

Recent surveys (cite: And15; And18; Izu17; Wen21) have found a number of ($\sim$10-20) star-forming region candidates in the extreme outer Galaxy, which is defined as having galactocentric distance ($D_{GC}$) larger than 18 kpc (cite: Yas06; Kob08). The extreme outer Galaxy has a very different environment from those in the solar neighborhood, with lower metallicity (cite: Fer17; Wen19), lower gas density (cite: Nak16), and small or no perturbation from spiral arms. Such an environment is of great interest for studies of the star formation and ISM in the early phase of the Milky Way formation and those in dwarf galaxies (cite: Fer98; Kob08). The low metallicity environment is in common with the Magellanic Clouds, and thus the extreme outer Galaxy is an ideal laboratory to test the universality of the low metallicity molecular chemistry observed in the LMC and SMC.

Among star-forming regions in the extreme outer Galaxy, WB89-789 (IRAS 06145+1455; 06$^\mathrm{h}$17$^\mathrm{m}$24.2s, 14$\ensuremath{^\circ}$54$\ensuremath{'}$42$\ensuremath{''}$, J2000) has particularly young and active nature (cite: Bra94). It is located at the galactocentric distance of 19.0 kpc and the distance from Earth is 10.7 kpc (cite: Bra07). The metallicity of WB89-789 is estimated to be a factor of four lower than the solar value according to the Galactic oxygen abundance gradient reported in the literature (cite: Fer17; Wen19; Bra19; Are20; Are21). The region is associated with dense clouds traced by CS and CO (cite: Bra07). The total mass of the cloud is estimated to be 6 $\times$ 10$^3$ M$_{\ensuremath{\odot}}$ for a $\sim$10 pc diameter area (cite: Bra94). An H$_2$O maser is detected towards the region (cite: Wou93), but no centimeter radio continuum is found (cite: Bra07). Several class I protostar candidates are identified by previous infrared observations (cite: Bra07).

We here report the first detection of a hot molecular core in the extreme outer Galaxy based on submillimeter observations towards WB89-789 with ALMA. Section [2](#sec_tarobsred) describes the details of the target source, observations, and data reduction. The observed molecular line spectra and images, as well as analyses of physical and chemical properties of the source, are presented in Section [3](#sec_res). Discussion about the properties of the hot core and comparisons of molecular abundances with known Galactic and LMC hot cores are given in Section [4](#sec_disc). This section also presents the detection of another embedded protostar with high-velocity outflows in the WB89-789 region. The conclusions are given in Section [5](#sec_sum).

+-----------+---------------+-----------+-----------+----------+---------------+------------------------------------------------+---------------------+--------------------+
|           | Observation   | On-source | Mean      | Number   | Baseline      |                                                |                     | Channel            |
+:==========+:=============:+:=========:+:=========:+:========:+:=====:+:=====:+:==============================================:+:===================:+:==================:+
| 5-6       | Date          | Time      | PWV$^{a}$ | of       | Min   | Max   | Bem size$^{b}$                                 | MRS$^{c}$           | Spacing            |
+-----------+---------------+-----------+-----------+----------+-------+-------+------------------------------------------------+---------------------+--------------------+
|           |               | (min)     | \(mm\)    | Antennas | \(m\) | \(m\) | ($\ensuremath{''}$ $\times$ $\ensuremath{''}$) | ($\ensuremath{''}$) |                    |
+-----------+---------------+-----------+-----------+----------+-------+-------+------------------------------------------------+---------------------+--------------------+
| Band 6    | 2018 Dec 6 –  | 115.5     | 0.5–1.5   | 45–49    | 15.1  | 783.5 | 0.41 $\times$ 0.50                             | 5.6                 | 0.98 MHz           |
+-----------+---------------+-----------+-----------+----------+-------+-------+------------------------------------------------+---------------------+--------------------+
| (250 GHz) | 2019 Apr 16   |           |           |          |       |       |                                                |                     | (1.2 km s$^{-1}$)  |
+-----------+---------------+-----------+-----------+----------+-------+-------+------------------------------------------------+---------------------+--------------------+
| Band 7    | 2018 Apr 30 – | 64.1      | 0.6–1.0   | 43-44    | 15.1  | 500.2 | 0.46 $\times$ 0.52                             | 5.4                 | 0.98 MHz           |
+-----------+---------------+-----------+-----------+----------+-------+-------+------------------------------------------------+---------------------+--------------------+
| (350 GHz) | 2018 Aug 22   |           |           |          |       |       |                                                |                     | (0.85 km s$^{-1}$) |
+-----------+---------------+-----------+-----------+----------+-------+-------+------------------------------------------------+---------------------+--------------------+

: Observation summary

Table notes: $^{a}$ Precipitable water vapor. $^{b}$ The average beam size of continuum achieved by TCLEAN with the Briggs weighting and the robustness parameter of 0.5. Note that we use a common circular restoring beam size of 0.50$''$ for Band 6 and 7 data to construct the final images. $^{c}$ Maximum Recoverable Scale.

# Target, observations, and data reduction

## Target

The target star-forming region is WB89-789 (cite: Bra94). The region contains three Class I protostar candidates identified by near-infrared observations (cite: Bra07), and one of them is a main target of the present ALMA observations. The region observed with ALMA is indicated on a near-infrared two-color image shown in Figure [1](#IR_image). The observed position is notably reddened compared with other parts of WB89-789.

![](f1.eps)

## Observations

Observations were conducted with ALMA in 2018 and 2019 as a part of the Cycle 5 (2017.1.01002.S) and Cycle 6 (2018.1.00627.S) programs (PI: T. Shimonishi). A summary of the present observations is shown in Table [1](#tab_Obs). The pointing center of antennas is RA = 06$^\mathrm{h}$17$^\mathrm{m}$23$^\mathrm{s}$ and Dec = 14$\ensuremath{^\circ}$54$\ensuremath{'}$41$\ensuremath{''}$ (ICRS). The total on-source integration time is 115.5 minutes for Band 6 data and 64.1 minutes for Band 7. Flux and bandpass calibrators are J0510+1800, J0854+2006, and J0725-0054 for Band 6, while J0854+2006 and J0510+1800 for Band 7, respectively. Phase calibrators are J0631+2020 and J0613+1708 for Band 6 and J0643+0857 and J0359+1433 for Band 7. Four spectral windows are used to cover the sky frequencies of 241.40–243.31, 243.76-245.66, 256.90–258.81, and 258.76–260.66 GHz for Band 6, while 337.22–339.15, 339.03-340.96, 349.12–351.05, and 350.92–352.85 GHz for Band 7. The channel spacing is 0.98 MHz, which corresponds to 1.2 km s$^{-1}$ for Band 6 and 0.85 km s$^{-1}$ for Band 7. The total number of antennas is 45–49 for Band 6 and 43–44 for Band 7. The minimum–maximum baseline lengths are 15.1–783.5 m for Band 6 and 15.1–500.2 m for Band 7. A full-width at half-maximum (FWHM) of the primary beam is about 25$\ensuremath{''}$ for Band 6 and 18$\ensuremath{''}$ for Band 7.

## Data reduction

Raw data is processed with the *Common Astronomy Software Applications* (CASA) package. We use CASA 5.4.0 (Band 6) and 5.1.1 (Band 7) for the calibration and CASA 5.5.0 for the imaging. The synthesized beam sizes of 0.39$''$–0.42$''$ $\times$ 0.49$''$–0.52$''$ with a position angle of -36 degree for Band 6 and 0.45$''$–0.46$''$ $\times$ 0.51$''$–0.52$''$ with a position angle of - 54 degree for Band 7 are achieved with the Briggs weighting and the robustness parameter of 0.5. In this paper, we use a common circular restoring beam size of 0.50$''$, which corresponds to 0.026 pc (5350 au) at the distance of WB89-789. The synthesized images are corrected for the primary beam pattern using the impbcor task in CASA. The continuum image is constructed by selecting line-free channels. Before the spectral extraction, the continuum emission is subtracted from the spectral data using the CASA’s uvcontsub task.

The spectra and continuum flux are extracted from the 0.50$''$ diameter circular region centered at RA = 06$^\mathrm{h}$17$^\mathrm{m}$24.073s and Dec = 14$\ensuremath{^\circ}$54$\ensuremath{'}$42.27$''$ (ICRS), which corresponds to the submillimeter continuum center of the target and is equivalent to the hot core position. Hereafter, the source is referred to as WB89-789 SMM1.

| 2 atoms | 3 atoms | 4 atoms | 5 atoms | 6 atoms | 7 atoms | 8 atoms | 9 atoms |
|:---|:---|:---|:---|:---|:---|:---|:---|
| CN | HDO | H$_2$CO | c-C$_3$H$_2$ | CH$_3$OH | CH$_3$CHO | HCOOCH$_3$ | CH$_3$OCH$_3$ |
| NO | H$^{13}$CO$^+$ | HDCO | HC$_3$N | $^{13}$CH$_3$OH | c-C$_2$H$_4$O |  | C$_2$H$_5$OH |
| CS | HC$^{18}$O$^+$ | D$_2$CO | H$_2$CCO | CH$_2$DOH |  |  | C$_2$H$_5$CN |
| C$^{34}$S | H$^{13}$CN | HNCO | HCOOH | CH$_3$CN |  |  |  |
| C$^{33}$S | HC$^{15}$N | H$_2$CS |  | NH$_2$CO |  |  |  |
| SO | CCH |  |  |  |  |  |  |
| $^{34}$SO | SO$_2$ |  |  |  |  |  |  |
| $^{33}$SO | $^{34}$SO$_2$ |  |  |  |  |  |  |
| SiO | OCS |  |  |  |  |  |  |
|  | $^{13}$OCS |  |  |  |  |  |  |

: Summary of detected molecular species

# Results and analysis

## Spectra

Figures [2](#spec_B6)–[3](#spec_B7) show submillimeter spectra extracted from the continuum center of WB89-789 SMM1. Spectral lines are identified with the aid of the Cologne Database for Molecular Spectroscopy[^1] (cite: Mul01; Mul05) and the molecular database of the Jet Propulsion Laboratory[^2] (cite: Pic98).

Line parameters are measured by fitting a Gaussian profile to detected lines. We estimate the peak brightness temperature, the FWHM, the LSR velocity, and the integrated intensity for each line based on the fitting. For spectral lines for which a Gaussian profile does not fit well, their integrated intensities are calculated by directly integrating the spectrum over the frequency region of emission. Full details of the line fitting can be found in Appendix A (Tables of measured line parameters) and Appendix B (Figures of fitted spectra). The table also contains the estimated upper limits on important non-detection lines.

A variety of carbon-, oxygen-, nitrogen-, sulfur-, and silicon-bearing species, including COMs containing up to nine atoms, are detected from WB89-789 SMM1 (see Table [2](#tab_line_summary)). Multiple high excitation lines (upper state energy $>$100 K) are detected for many species. Measured line widths are typically 3–6 km s$^{-1}$. Most of lines consist of a single velocity component, but SiO has doppler shifted components at $V_{sys}$ $\pm$ 5 km s$^{-1}$ as indicated in Figure [14](#line_others) in Appendix B.

![](f2.eps)

![](f3.eps)

## Images

Figures [4](#images1)–[5](#images2) show synthesized images of continuum and molecular emission lines observed toward the target region. The images are constructed by integrating spectral data in the velocity range where the emission is detected. Most molecular lines, except for those of molecular radicals CN, CCH, and NO, have their intensity peak at the continuum center, which corresponds to the position of a hot core. Simple molecules such as H$^{13}$CO$^+$, H$^{13}$CN, CS, and SO are extended compared to the beam size. Secondary intensity peaks are also seen in those species. Complex molecules and HDO are concentrated at the hot core position. A characteristic symmetric distribution is seen in SiO. Further discussion about the distribution of the observed emission is presented in Section [4.2](#sec_disc_dist).

![](f4.eps)

![](f5.eps)

## Derivation of column densities, gas temperatures, and molecular abundances

### Rotation diagram analysis

Column densities and rotation temperatures are estimated based on the rotation diagram analysis for the molecular species where multiple transitions with different excitation energies are detected (Figure [6](#rd1)). We here assume an optically thin condition and the local thermodynamic equilibrium (LTE). We use the following formulae based on the standard treatment of the rotation diagram analysis (cite: Sut95; Gol99):

$$\begin{equation}
\log \left(\frac{ N_{u} }{ g_{u} } \right) = - \left(\frac {\log e}{T_{\mathrm{rot}}} \right) \left(\frac{E_{u}}{k} \right) + \log \left(\frac{N}{Q(T_{\mathrm{rot}})} \right),  \label{Eq_rd1}
\end{equation}$$ where $$\begin{equation}
\frac{ N_{u} }{ g_{u} } = \frac{ 3 k \int T_{\mathrm{b}} dV }{ 8 \pi^{3} \nu S \mu^{2} }, \label{Eq_rd2} \\ 
\end{equation}$$

and $N_{u}$ is a column density of molecules in the upper energy level, $g_{u}$ is the degeneracy of the upper level, $k$ is the Boltzmann constant, $\int T_{\mathrm{b}} dV$ is the integrated intensity estimated from the observations, $\nu$ is the transition frequency, $S$ is the line strength, $\mu$ is the dipole moment, $T_{\mathrm{rot}}$ is the rotational temperature, $E_{u}$ is the upper state energy, $N$ is the total column density, and $Q(T_{\mathrm{rot}})$ is the partition function at $T_{\mathrm{rot}}$. All the spectroscopic parameters required in the analysis are extracted from the CDMS or JPL database. Derived column densities and rotation temperatures are summarized in Table [3](#tab_N).

Most molecular species are well fitted by a single temperature component. Data points in diagrams of CH$_3$CN and C$_2$H$_5$CN are relatively scattered. For CH$_3$OH, CH$_3$CN, HNCO, SO$_2$, and HCOOCH$_3$, transitions with relatively large $S\mu^2$ values at low $E_{u}$ ($<$300 K) are excluded from the fit in order to avoid possible effect of optical thickness (see gray points in Fig. ).

Complex organic molecules, HDO, and SO$_2$ show high rotation temperatures ($>$130 K). This suggests that they are originated from a warm region associated with a protostar. On the other hand, C$^{33}$S and D$_2$CO, and H$_2$CS show lower temperatures, suggesting that they arise from a colder region in the outer part of the protostellar envelope.

![](f6.eps)

### Column densities of other molecules

Column densities of molecular species for which rotation diagram analysis is not applicable are estimated from Equation [\[Eq_rd1\]](#Eq_rd1) after solving it for $N$. Their rotation temperatures are estimated as follows, by taking into account that the sight-line of WB89-789 SMM1 contains both cold and warm gas components as described in Section [3.3.1](#sec_rd).

The rotation temperature of C$^{33}$S is applied to those of CS and C$^{34}$S, considering a similar distribution of isotopologues. Similarly, the rotation temperature of D$_2$CO is applied to H$_2$CO and HDCO, and that of SO$_2$ to $^{34}$SO$_2$. For other species, we assume that molecules with an extended spatial distribution trace a relatively low-temperature region rather than a high-temperature gas associated with a hot core. CN, CCH, H$^{13}$CO$^+$, HC$^{18}$O$^+$, H$^{13}$CN, HC$^{15}$N, NO, SiO, $^{34}$SO, $^{33}$SO, and c-C$_3$H$_2$ correspond to this case. We assume a rotation temperature of 35 K for those species, which is roughly equivalent to that of C$^{33}$S.

High gas temperatures are observed for COMs, SO$_2$, and HDO, which are associated with a compact hot core region. Average temperature of those species is $\sim$200 K. We assume this temperature for column density estimates (including upper limit) of c-C$_2$H$_4$O, HC$_3$N, $^{13}$CH$_3$CN, $^{13}$OCS, and CH$_3$SH. Estimated column densities are summarized in Table [3](#tab_N).

We have also estimated column densities of selected species based on non-LTE calculations with RADEX (cite: vdT07). For input parameters, we use the H$_2$ gas density of 2.1 $\times$ 10$^7$ cm$^{-3}$ according to our estimate in Section [3.3.3](#sec_h2) and the background temperature of 2.73 K. Kinetic temperatures are assumed to be the same as temperatures tabulated in Table [3](#tab_N). The line intensities and widths are taken from the tables in Appendix A [^3]. We assume an empirical 10$\%$ uncertainty for input line intensities. The resultant column densities are summarized in Table [3](#tab_N). The calculated non-LTE column densities are reasonably consistent with the LTE estimates.

### Column density of H$_2$, dust extinction, and gas mass

A column density of molecular hydrogen ($N_{\mathrm{H_2}}$) is estimated from the dust continuum data. We use the following equation to calculate $N_{\mathrm{H_2}}$ based on the standard treatment of optically thin dust emission:

$$\begin{equation}
N_{\mathrm{H_2}} = \frac{F_{\nu} / \Omega}{2 \kappa_{\nu} B_{\nu}(T_{d}) Z \mu m_{\mathrm{H}}} \label{Eq_h2}, 
\end{equation}$$

where $F_{\nu}/\Omega$ is the continuum flux density per beam solid angle as estimated from the observations, $\kappa_{\nu}$ is the mass absorption coefficient of dust grains coated by thin ice mantles at 1200/870 $\mu$m as taken from (cite: Oss94) and we here use 1.07 cm$^2$ g$^{-1}$ for 1200 $\mu$m and 1.90 cm$^2$ g$^{-1}$ for 870 $\mu$m, $T_{d}$ is the dust temperature and $B_{\nu}(T_{d})$ is the Planck function, $Z$ is the dust-to-gas mass ratio, $\mu$ is the mean atomic mass per hydrogen (cite: Cox00), and $m_{\mathrm{H}}$ is the hydrogen mass. We use the dust-to-gas mass ratio of 0.002, which is obtained by scaling the Galactic value of 0.008 by the metallicity of the WB89-789 region.

A line of sight towards a hot core contain dust grains with different temperatures because of the temperature gradient in a protostellar envelope. Representative dust temperature (i.e. mass-weighted average temperature) would fall somewhere in between that of a warm inner region and a cold outer region. (cite: ST20) presented a detailed analysis of effective dust temperature in the sight-line of a low-metallicity hot core in the LMC, based on a comparison of $N_{\mathrm{H_2}}$ derived by submillimeter dust continuum with the above method, model fitting of spectral energy distributions (SEDs), and the 9.7 $\mu$m silicate dust absorption depth. The paper concluded that $T_{d}$ = 60 K for the dust continuum analysis yields the $N_{\mathrm{H_2}}$ value which is consistent with those obtained by other different methods. This temperature corresponds to an intermediate value between a cold gas component ($\sim$50 K) represented by SO and a warm component ($\sim$150 K) represented by CH$_3$OH and SO$_2$ in this LMC hot core. The present hot core, WB89-789 SMM1, harbors similar temperature components as discussed in Sections [3.3.1](#sec_rd) and [3.3.2](#sec_n). We thus applied $T_{d}$ = 60 K for the present source. The continuum brightness of SMM1 is measured to be 11.33 $\pm$ 0.05 mJy/beam for 1200 $\mu$m and 28.0 $\pm$ 0.2 mJy/beam for 870 $\mu$m (3$\sigma$ uncertainty). Based on the above assumption, we obtain $N_{\mathrm{H_2}}$ = 1.6 $\times$ 10$^{24}$ cm$^{-2}$ for 1200 $\mu$m and $N_{\mathrm{H_2}}$ = 1.2 $\times$ 10$^{24}$ cm$^{-2}$ for the 870 $\mu$m. The $N_{\mathrm{H_2}}$ value changes by a factor of up to 1.6 when the assumed $T_{d}$ is varied between 40 K and 90 K.

Alternatively, a column density of molecular hydrogen can be determined by the model fitting of the observed spectral energy distribution (SED). The best-fit SED discussed in Section [4.1](#sec_disc_star) yields $A_V$ = 184 mag. We here use a standard value of $N_{\mathrm{H}}$/$E(B-V)$ = 5.8 $\times$ 10$^{21}$ cm$^{-2}$ mag$^{-1}$ (cite: Dra03) and a slightly high $A_{V}$/$E(B-V)$ ratio of 4 for dense clouds (cite: Whi01b). Taking into account a factor of four lower metallicity, we obtain $N_{\mathrm{H_2}}$/$A_{V}$ = 2.9 $\times$ 10$^{21}$ cm$^{-2}$ mag$^{-1}$, where we assume that all the hydrogen atoms are in the form of H$_2$. Using this conversion factor, we obtain $N_{\mathrm{H_2}}$ = 5.3 $\times$ 10$^{23}$ cm$^{-2}$. This $N_{\mathrm{H_2}}$ is similar to the $N_{\mathrm{H_2}}$ derived from the aforementioned method assuming $T_{d}$ = 150 K. Such $T_{d}$ may be somewhat high as a typical dust temperature in the line of sight, but it is not very unrealistic value given the observed temperature range of molecular gas towards WB89-789 SMM1.

In this paper, we use $N_{\mathrm{H_2}}$ = 1.1 $\times$ 10$^{24}$ cm$^{-2}$ as a representative value, which corresponds to the average of $N_{\mathrm{H_2}}$ derived by the dust continuum data and the SED fitting. This $N_{\mathrm{H_2}}$ corresponds to $A_V$ = 380 mag using the above conversion factor. Assuming the source diameter of 0.026 pc and the uniform spherical distribution of gas around a protostar, we estimate the gas number density to be $n_{\mathrm{H_2}}$ = 2.1 $\times$ 10$^7$ cm$^{-3}$, where the total gas mass of 13 M$_{\ensuremath{\odot}}$ is enclosed.

### Fractional abundances and isotope abundance ratios

Fractional abundances with respect to H$_2$ are shown in Table [4](#tab_X), which are calculated based on column densities estimated in Sections [3.3.1](#sec_rd)–[3.3.3](#sec_h2). The fractional abundances normalized by the CH$_3$OH column density are also discussed in Sections [4.3](#sec_disc_molab)-[4.4](#sec_disc_molab2), because of the non-negligible uncertainty associated with $N_{\mathrm{H_2}}$ (see Section [3.3.3](#sec_h2)).

Abundances of HCO$^{+}$, HCN, SO, CS, OCS, and CH$_3$OH are estimated from their isotopologues, H$^{13}$CO$^{+}$, H$^{13}$CN, $^{34}$SO, C$^{34}$S, O$^{13}$CS, and $^{13}$CH$_3$OH. Detections of isotopologue species for SO, CS, OCS, and CH$_3$OH imply that the main species would be optically thick. Isotope abundance ratios of $^{12}$C/$^{13}$C = 150 and $^{32}$S/$^{33}$S = 35 are assumed, which are obtained by extrapolating the relationship between isotope ratios and galactocentric distances reported in (cite: Wil94) and (cite: Hum20) to $D_{GC}$ = 19 kpc.

Abundance ratios are derived for several rare isotopologues; we obtain CH$_2$DOH/CH$_3$OH = 0.011 $\pm$ 0.002, D$_2$CO/HDCO = 0.45 $\pm$ 0.10, $^{34}$SO/$^{33}$SO = 5 $\pm$ 1, C$^{34}$S/C$^{33}$S = 2 $\pm$ 1, and $^{32}$SO$_2$/$^{34}$SO$_2$ = 20 $\pm$ 4. The $^{32}$SO$_2$/$^{34}$SO$_2$ ratio in WB89-789 SMM1 is similar to the solar $^{32}$S/$^{34}$S ratio (cite: Wil94), although we expect a slightly higher value in the outer Galaxy due to the $^{32}$S/$^{34}$S gradient in the Galaxy (cite: Chi96b; Hum20). Astrophysical implication for the deuterated species are discussed in Section [4.4](#sec_disc_molab2).

The rotation diagram of CH$_3$CN is rather scattered. Although its isotopologue line is not detected, optical thickness might affect the column density estimate, as CH$_3$CN is often optically thick in hot cores (cite: Fue14). To obtain a possible range of its column density, we use the rotation diagram of $^{12}$CH$_3$CN data to estimate a lower limit and the non-detection of the $^{13}$CH$_3$CN(19$_{0}$–18$_{0}$) line at 339.36630 GHz ($E_{u}$ = 163 K) for an upper limit.

We have also repeated the analysis for the spectra extracted from a 0.1 pc (1.93$''$) diameter region at the hot core position, for the sake of comparison with LMC hot cores (see Section [4.4](#sec_disc_molab2)). Those abundances are also summarized in Table [4](#tab_X). The abundances for a 0.1 pc area do not drastically vary from those for a 0.026 pc area. Molecules with compact spatial distribution (e.g., COMs) tend to decrease their abundances by a factor of $\sim$2–3 in the 0.1 pc data due to the beam dilution effect. In contrast, those with extended spatial distributions and intensity peaks outside the hot core region (H$^{13}$CO$^+$, CCH, CN, and NO) increases by a factor of $\sim$2 in the 0.1 pc data.

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| Molecule | $T$$_{rot}$ | $N$(X) | $N$(X) non-LTE | Size |
|  | \(K\) | (cm$^{-2}$) | (cm$^{-2}$) | ($\ensuremath{''}$) |
| H$_2$ | ... | 1.1 $\times$ 10$^{24}$ | ... | 0.85$^{c}$ |
| H$^{13}$CO$^+$ | 35 | (7.0 $\pm$ 0.1) $\times$ 10$^{12}$ | (7.6 $\pm$ 0.9) $\times$ 10$^{12}$ | $>$1.5$^{d}$ |
| HC$^{18}$O$^+$ | 35 | (5.8 $\pm$ 0.9) $\times$ 10$^{11}$ | (5.7 $\pm$ 0.6) $\times$ 10$^{11}$ | 1.18$^{d}$ |
| CCH | 35 | (2.7 $\pm$ 0.1) $\times$ 10$^{14}$ | ... | $>$2$^{d}$ |
| c-C$_3$H$_2$ | 35 | (9.5 $\pm$ 2.2) $\times$ 10$^{13}$ | (8.2 $\pm$ 0.9) $\times$ 10$^{13}$$^{a}$ | $>$1$^{d}$ |
| H$_2$CO | 39 | (1.1 $\pm$ 0.1) $\times$ 10$^{14}$ | (1.3 $\pm$ 0.1) $\times$ 10$^{14}$$^{a}$ | $>$1.5$^{d}$ |
| HDCO | 39 | (5.1 $\pm$ 0.3) $\times$ 10$^{13}$ | ... | $>$1$^{d}$ |
| D$_2$CO | *39$^{+6}_{-5}$* | *(2.3 $\pm$ 0.5) $\times$ 10$^{13}$* | ...... | $>$1$^{d}$ |
| CN | 35 | (3.3 $\pm$ 0.2) $\times$ 10$^{14}$ | (2.5 $\pm$ 0.3) $\times$ 10$^{14}$ | $>$2$^{d}$ |
| H$^{13}$CN | 35 | (1.2 $\pm$ 0.1) $\times$ 10$^{13}$ | (1.1 $\pm$ 0.1) $\times$ 10$^{13}$ | 0.92$^{d}$ |
| HC$^{15}$N | 35 | (6.3 $\pm$ 0.2) $\times$ 10$^{12}$ | (5.8 $\pm$ 0.6) $\times$ 10$^{12}$ | 0.75$^{d}$ |
| HC$_3$N | 200 | (2.7 $\pm$ 0.3) $\times$ 10$^{13}$ | (2.1 $\pm$ 0.2) $\times$ 10$^{13}$ | 0.65 |
| NO | 35 | (9.0 $\pm$ 2.5) $\times$ 10$^{14}$ | (8.9 $\pm$ 0.9) $\times$ 10$^{14}$ | $>$1.5$^{d}$ |
| HNCO | *237$^{+17}_{-15}$* | *(3.0 $\pm$ 0.2) $\times$ 10$^{14}$* | ... | 0.54 |
| CH$_3$CN | *279$^{+12}_{-11}$* | *(1.8 $\pm$ 0.1) $\times$ 10$^{14}$* | (8.6 $\pm$ 0.8) $\times$ 10$^{13}$ | 0.51 |
| $^{13}$CH$_3$CN | 200 | $<$5 $\times$ 10$^{12}$ | ... | ... |
| C$_2$H$_5$CN | *130$^{+20}_{-15}$* | *(6.3 $\pm$ 1.7) $\times$ 10$^{13}$* | ... | 0.52 |
| NH$_2$CO | *140$^{+8}_{-7}$* | *(4.2 $\pm$ 0.7) $\times$ 10$^{13}$* | ... | 0.56 |
| SiO | 35 | (2.5 $\pm$ 0.2) $\times$ 10$^{12}$ | (2.5 $\pm$ 0.3) $\times$ 10$^{12}$ | 0.65 |
| CS | 36 | (1.5 $\pm$ 0.2) $\times$ 10$^{14}$ | (2.0 $\pm$ 0.3) $\times$ 10$^{14}$ | $>$1.5 |
| C$^{34}$S | 36 | (3.1 $\pm$ 0.1) $\times$ 10$^{13}$ | ... | 0.70 |
| C$^{33}$S | *36$^{+4}_{-3}$* | *(1.5 $\pm$ 0.2) $\times$ 10$^{13}$* | ... | 0.61 |
| OCS | *106$^{+6}_{-5}$* | *(6.5 $\pm$ 0.5) $\times$ 10$^{14}$* | (6.4 $\pm$ 0.7) $\times$ 10$^{14}$ | 0.55 |
| $^{13}$OCS | 200 | (8.7 $\pm$ 2.4) $\times$ 10$^{13}$ | ... | 0.45 |
| H$_2$CS | *43$^{+3}_{-2}$* | *(1.5 $\pm$ 0.1) $\times$ 10$^{14}$* | (1.4 $\pm$ 0.2) $\times$ 10$^{14}$$^{a}$ | 0.62 |
| SO | *35$^{+1}_{-1}$* | *(4.0 $\pm$ 0.3) $\times$ 10$^{14}$* | (4.5 $\pm$ 0.5) $\times$ 10$^{14}$ | 0.70$^{d}$ |
| $^{34}$SO | 35 | (5.9 $\pm$ 0.1) $\times$ 10$^{13}$ | ... | 0.66 |
| $^{33}$SO | 35 | (1.1 $\pm$ 0.1) $\times$ 10$^{13}$ | ... | 0.53 |
| SO$_2$ | *166$^{+5}_{-5}$* | *(1.2 $\pm$ 0.1) $\times$ 10$^{15}$* | ... | 0.53 |
| $^{34}$SO$_2$ | 166 | (5.9 $\pm$ 0.9) $\times$ 10$^{13}$ | ... | 0.51 |
| CH$_3$SH | 200 | $<$3 $\times$ 10$^{14}$ | ... | ... |
| HDO | *217$^{+14}_{-12}$* | *(2.2 $\pm$ 0.2) $\times$ 10$^{15}$* | ... | 0.52 |
| CH$_3$OH | *245$^{+4}_{-4}$* | *(1.9 $\pm$ 0.1) $\times$ 10$^{16}$* | (2.6 $\pm$ 0.1) $\times$ 10$^{16}$$^{b}$ | 0.51 |
| $^{13}$CH$_3$OH | *181$^{+10}_{-9}$* | *(2.8 $\pm$ 0.2) $\times$ 10$^{15}$* | ... | 0.46 |
| CH$_2$DOH | *155$^{+18}_{-15}$* | *(4.6 $\pm$ 0.3) $\times$ 10$^{15}$* | ... | 0.52 |
| HCOOCH$_3$ | *181$^{+6}_{-5}$* | *(8.6 $\pm$ 0.4) $\times$ 10$^{15}$* | ... | 0.51 |
| CH$_3$OCH$_3$ | *137$^{+5}_{-4}$* | *(2.6 $\pm$ 0.1) $\times$ 10$^{15}$* | ... | 0.52 |
| C$_2$H$_5$OH | *136$^{+14}_{-12}$* | *(9.6 $\pm$ 1.3) $\times$ 10$^{14}$* | ... | 0.50 |
| CH$_3$CHO | *192$^{+52}_{-34}$* | *(6.4 $\pm$ 0.8) $\times$ 10$^{14}$* | ... | 0.49 |
| *trans*-HCOOH | *71$^{+11}_{-9}$* | *(2.7 $\pm$ 0.6) $\times$ 10$^{14}$* | ... | 0.58 |
| *cis*-HCOOH | *69$^{+50}_{-21}$* | *(2.4 $\pm$ 1.2) $\times$ 10$^{13}$* | ... | 0.49 |
| H$_2$CCO | *92$^{+14}_{-11}$* | *(1.0 $\pm$ 0.2) $\times$ 10$^{14}$* | ... | 0.55 |
| c-C$_2$H$_4$O | 200 | (8.9 $\pm$ 2.0) $\times$ 10$^{13}$ | ... | 0.47 |

: Estimated rotation temperatures, column densities, and source sizes

Table notes: Uncertainties and upper limits are of the 2 $\sigma$ level and do not include systematic errors due to adopted spectroscopic constants. See Sections [3.3.1](#sec_rd)-[3.3.3](#sec_h2) and [4.2](#sec_disc_dist) for details. $^{a}$ Assuming ortho/para ratio of three. $^{b}$ Assuming E-CH$_3$OH/A-CH$_3$OH ratio of unity (cite: Wir11). $^{c}$ Size of continuum emission. $^{d}$ Associated with extended component.

+:---------------+:-----------------------------------:+:-----------------------------------:+
| Molecule       | $N$(X)/$N_{\mathrm{H_2}}$                                                 |
+----------------+-------------------------------------+-------------------------------------+
|                | 0.026 pc area                       | 0.1 pc area                         |
+----------------+-------------------------------------+-------------------------------------+
| HCO$^+$$^{a}$  | (9.5 $\pm$ 3.2) $\times$ 10$^{-10}$ | (1.5 $\pm$ 0.3) $\times$ 10$^{-9}$  |
+----------------+-------------------------------------+-------------------------------------+
| H$_2$CO        | (1.0 $\pm$ 0.3) $\times$ 10$^{-10}$ | (1.2 $\pm$ 0.1) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| HDCO           | (4.7 $\pm$ 1.3) $\times$ 10$^{-11}$ | (3.9 $\pm$ 0.2) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+
| D$_2$CO        | (2.1 $\pm$ 0.7) $\times$ 10$^{-11}$ | (2.0 $\pm$ 0.3) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+
| C$_2$H         | (2.5 $\pm$ 0.7) $\times$ 10$^{-10}$ | (5.8 $\pm$ 1.2) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| c-C$_3$H$_2$   | (8.6 $\pm$ 3.1) $\times$ 10$^{-11}$ | (5.9 $\pm$ 1.2) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+
| CN             | (3.0 $\pm$ 0.8) $\times$ 10$^{-10}$ | (6.6 $\pm$ 1.3) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| HCN$^{a}$      | (1.7 $\pm$ 0.6) $\times$ 10$^{-9}$  | (1.2 $\pm$ 0.3) $\times$ 10$^{-9}$  |
+----------------+-------------------------------------+-------------------------------------+
| HC$_3$N        | (2.5 $\pm$ 0.7) $\times$ 10$^{-11}$ | (1.4 $\pm$ 0.1) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+
| NO             | (8.1 $\pm$ 3.2) $\times$ 10$^{-10}$ | (1.6 $\pm$ 0.1) $\times$ 10$^{-9}$  |
+----------------+-------------------------------------+-------------------------------------+
| HNCO           | (2.7 $\pm$ 0.8) $\times$ 10$^{-10}$ | (7.1 $\pm$ 0.6) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+
| CH$_3$CN$^{b}$ | (4.2 $\pm$ 2.7) $\times$ 10$^{-10}$ | (3.7 $\pm$ 2.8) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| C$_2$H$_5$CN   | (5.8 $\pm$ 2.2) $\times$ 10$^{-11}$ | (2.4 $\pm$ 0.9) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+
| NH$_2$CHO      | (3.8 $\pm$ 1.2) $\times$ 10$^{-11}$ | (1.8 $\pm$ 0.1) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+
| SiO            | (2.2 $\pm$ 0.6) $\times$ 10$^{-12}$ | (1.2 $\pm$ 0.1) $\times$ 10$^{-12}$ |
+----------------+-------------------------------------+-------------------------------------+
| CS$^{c}$       | (9.7 $\pm$ 3.3) $\times$ 10$^{-10}$ | (6.4 $\pm$ 1.3) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| SO$^{c}$       | (1.9 $\pm$ 0.5) $\times$ 10$^{-9}$  | (1.3 $\pm$ 0.3) $\times$ 10$^{-9}$  |
+----------------+-------------------------------------+-------------------------------------+
| OCS$^{a}$      | (1.2 $\pm$ 0.5) $\times$ 10$^{-8}$  | (4.1 $\pm$ 1.4) $\times$ 10$^{-9}$  |
+----------------+-------------------------------------+-------------------------------------+
| H$_2$CS        | (1.4 $\pm$ 0.4) $\times$ 10$^{-10}$ | (9.0 $\pm$ 1.0) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+
| SO$_2$         | (1.1 $\pm$ 0.3) $\times$ 10$^{-9}$  | (2.9 $\pm$ 0.1) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| CH$_3$SH       | $<$3 $\times$ 10$^{-10}$            | $<$2 $\times$ 10$^{-10}$            |
+----------------+-------------------------------------+-------------------------------------+
| HDO            | (2.0 $\pm$ 0.6) $\times$ 10$^{-9}$  | (7.7 $\pm$ 0.9) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| CH$_3$OH$^{a}$ | (3.8 $\pm$ 1.3) $\times$ 10$^{-7}$  | (1.7 $\pm$ 0.3) $\times$ 10$^{-7}$  |
+----------------+-------------------------------------+-------------------------------------+
| CH$_2$DOH      | (4.2 $\pm$ 1.2) $\times$ 10$^{-9}$  | (1.5 $\pm$ 0.2) $\times$ 10$^{-9}$  |
+----------------+-------------------------------------+-------------------------------------+
| HCOOCH$_3$     | (7.8 $\pm$ 2.2) $\times$ 10$^{-9}$  | (3.0 $\pm$ 0.2) $\times$ 10$^{-9}$  |
+----------------+-------------------------------------+-------------------------------------+
| CH$_3$OCH$_3$  | (2.3 $\pm$ 0.6) $\times$ 10$^{-9}$  | (1.0 $\pm$ 0.1) $\times$ 10$^{-9}$  |
+----------------+-------------------------------------+-------------------------------------+
| C$_2$H$_5$OH   | (8.7 $\pm$ 2.7) $\times$ 10$^{-10}$ | (3.3 $\pm$ 0.8) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| CH$_3$CHO      | (5.8 $\pm$ 1.8) $\times$ 10$^{-10}$ | (2.1 $\pm$ 0.4) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| HCOOH$^{d}$    | (2.7 $\pm$ 1.0) $\times$ 10$^{-10}$ | (1.2 $\pm$ 0.4) $\times$ 10$^{-10}$ |
+----------------+-------------------------------------+-------------------------------------+
| H$_2$CCO       | (9.2 $\pm$ 3.0) $\times$ 10$^{-11}$ | (3.7 $\pm$ 0.9) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+
| c-C$_2$H$_4$O  | (8.1 $\pm$ 2.8) $\times$ 10$^{-11}$ | (5.9 $\pm$ 1.2) $\times$ 10$^{-11}$ |
+----------------+-------------------------------------+-------------------------------------+

: Estimated fractional abundances

Table notes: Uncertainties and upper limits are of the 2$\sigma$ level. Column densities of molecules for a 0.026 pc area are summarized in Table [3](#tab_N). An empirical uncertainty of 30 $\%$ is assumed for $N_{\mathrm{H_2}}$. $^{a}$ Estimated from $^{13}$C isotopologue with $^{12}$C/$^{13}$C = 150 $^{b}$ Rotation diagram analysis of CH$_3$CN is used to derive a lower limit and the non-detection of $^{13}$CH$_3$CN for an upper limit. $^{c}$ Estimated from $^{34}$S isotopologue with $^{32}$S/$^{34}$S = 35 $^{d}$ Sum of $trans-$ and $cis-$species.

![](f7.eps)

# Discussion

## Hot molecular core and protostar associated with WB89-789 SMM1

The nature of WB89-789 SMM1 is characterized as (i) the compact distribution of warm gas ($\sim$0.03 pc, see Section [4.2](#sec_disc_dist)), (ii) the high gas temperature that can trigger the ice sublimation ($\geq$100 K, Section [3.3.1](#sec_rd)), (iii) the high density (2 $\times$ 10$^7$ cm$^{-3}$, Section [3.3.3](#sec_h2)), (iv) the association with a luminous protostar (see below), and (v) the presence of chemically rich molecular gas. Those properties suggest that the source is associated with a hot molecular core.

Figure [7](#sed) shows a SED of SMM1, where the data are collected from available databases and literatures (cite: Bra07; Wri10; Yam10). The bolometric luminosity of the source is estimated to be 8.4 $\times$ 10$^3$ L$_{\ensuremath{\odot}}$ based on the SED fitting with the model of (cite: Rob07). This luminosity is equivalent to a stellar mass of about 10 M$_{\ensuremath{\odot}}$ according to the mass-luminosity relationship of zero age main sequence (ZAMS) stars (cite: ZY07).

Note that far-infrared data, which is important for the luminosity determination of embedded sources, is insufficient for SMM1. Only upper limits are provided due to the low angular resolution of available *AKARI* FIS all-sky survey data. Thus the derived luminosity (and therefore mass) may be lower than the current estimate. Future high spatial resolution infrared observations in those missing wavelengths are highly required.

Alternatively, we can estimate the luminosity of SMM1 by scaling the luminosity of a low-metallicity LMC hot core, ST16, whose SED is well determined based on a comprehensive infrared from 1 to 1200 $\mu$m (cite: ST20). This LMC hot core has a total luminosity of 3.1 $\times$ 10$^5$ L$_{\ensuremath{\odot}}$ and a $K_s$-band magnitude (\[$K_s$\]) of 13.4 mag at 50 kpc, while SMM1 has \[$K_s$\] = 14.7 mag at 10.7 kpc. Scaling the luminosity of ST16 with the distance and $K_s$-band magnitude, we obtain 4.3 $\times$ 10$^3$ L$_{\ensuremath{\odot}}$ for SMM1, which is a factor of two lower than the estimate by the SED fitting. In either case, present estimates suggest that the luminosity of SMM1 would correspond to the lower-end of high-mass ZAMS or upper-end of intermediate-mass ZAMS.

![](f8.eps)

## Distribution of molecular line emission and dust continuum

The observed emission lines and continuum show different spatial distributions depending on species. Those distributions have important clues to understand their origins. A schematic illustration of the temperature structure and molecular gas distribution in WB89-789 SMM1 are shown in Figure [8](#schematic) based on the discussion in this section.

We have estimated the spatial extent of observed emission by fitting a two-dimensional Gaussian to the continuum center (Table [3](#tab_N)). Compact distributions (FWHM = 0.5$''$–0.6$''$, 0.026–0.031 pc), that is comparable with the beam size, are seen in HDO, COMs, CH$_3$CN, HNCO, OCS, and high-excitation SO$_2$ lines. HC$_3$N is slightly extended (FWHM = 0.65$''$). They are concentrated at the hot core position, suggesting that they are originated from a warm region where ice mantles are sublimated.

SO, $^{34}$SO, $^{33}$SO, and low-excitation SO$_2$ show relatively compact distributions (FWHM = 0.5$''$–0.7$''$, 0.026–0.036 pc) at the hot core position, but also show a secondary peak at the south side of the hot core. This secondary peak coincides with the peak of the NO emission. Other sulfur-bearing species such as C$^{34}$S, C$^{33}$S, and H$_2$CS show compact distributions centered at the hot core.

A characteristic distribution that is symmetric to the hot core position is seen in SiO. It shows a compact emission (FWHM = 0.65$''$) at the hot core center, but also shows other peaks at the north-east and south-west sides of the hot core. Those secondary peaks are slightly elongated. SiO is a well-known shock tracer. The observed structure would be originated from the shocked gas produced by bipolar protostellar outflows. A driving source of the outflows would be a protostar embedded in a hot core, since the distribution of SiO is symmetric to the hot core position.

Even extended distributions (FWHM $>$ 1.0$''$) are seen in CN, CCH, H$^{13}$CO$^{+}$, HC$^{18}$O$^{+}$, H$^{13}$CN, HC$^{15}$N, NO, CS, H$_2$CO, and HDCO, D$_2$CO, and low-excitation CH$_3$OH. Gas-phase reactions and non-thermal desorption of icy species would have non-negligible contribution to the formation of those species, because they are widely distributed beyond the hot core. We note that dust continuum, H$^{13}$CN, HC$^{15}$N have a moderately sharp peak (FWHM $<$ 1.0$''$) at the hot core position in addition to the extended component. c-C$_3$H$_2$ shows a patchy distribution, whose secondary peak at the south-west of the hot core does not with those of other species.

Molecular radicals (CN, CCH, and NO) do not have their emission peak at the hot core position. This would suggest that the chemistry outside the hot core region largely contributes to their production. CN and CCH are known to be abundant in photodissociation regions (PDRs), because atomic carbon is efficiently provided by photodissociation of CO under moderate UV fields (cite: Fue93; Ste95; Jan95; Rod98; Pet17). In the present source, their emission shows a similar spatial distribution. A similar distribution between CN and CCH has been also observed in a LMC hot core (cite: ST20); they argue that CN and CCH would trace PDR-like outflow cavity structures that are irradiated by the UV light from a protostar associated with a hot core. We speculate that this is also the case for WB89-789 SMM1.

Figure [9](#Mom1) shows velocity maps (moment 1) of CN and CCH lines. CN and CCH emission are elongated in the south-west direction from the hot core (see also Figure [4](#images1)). The figure also shows a possible direction of protostellar outflows expected from the spatial distribution of SiO. The elongated directions of CN and CCH coincide with the inferred direction of outflows. In addition, the elongated south-west parts of CN and CCH are blue-shifted by $\sim$1–2 km s$^{-1}$ compared to the hot core position. This may be due to outflow gas motion, although CN and CCH would trace an outflow cavity wall rather than outflow gas itself. Actually the observed velocity shift is smaller than a typical value of high-velocity wing components in massive protostellar outflows (cite: Beu02; Mau15). Future observations of optically-thick outflow tracers such as CO are necessary to confirm the presence of high-velocity gas associated with protostellar outflows.

![](f9.eps)

## Molecular abundances: Comparison with Galactic hot cores

Figure [10](#abu1) shows a comparison of molecular abundances between WB89-789 SMM1 and other known Galactic hot cores. The data for an intermediate-mass hot core, NGC7192 FIRS2, is adopted from (cite: Fue14). The abundances are based on the 220 GHz region observations for a 0.009 pc diameter area centered at the hot core. The luminosity of NGC7192 FIRS2 ($\sim$500 L$_{\ensuremath{\odot}}$) corresponds to that of a 5 M$_{\ensuremath{\odot}}$ ZAMS. The data for a high-mass source, the Orion hot core, is adopted from (cite: Sut95), which is based on the 340 GHz region observations for a 0.027 pc diameter area at the hot core. The abundance of HNCO is taken from (cite: Sch97).

The molecular abundances in WB89-789 SMM1 is generally lower than those of inner Galactic counterparts. The degree of the abundance decrease is roughly consistent with the lower metallicity of the WB89-789 region as indicated by the scale bar in Figure [10](#abu1). Particularly, SMM1 and the intermediate-mass hot core NGC7192 FIRS2 show similar molecular abundances after taking into account the four times lower metallicity of the former source. For the comparison with Orion, it seems that HC$_3$N, C$_2$H$_5$CN, and SO$_2$ are significantly less abundant in SMM1 even taking into account the lower metallicity, while CH$_3$OH is overabundant in SMM1 despite the low metallicity.

![](f10.eps)

![](f11.eps)

To further focus on chemical complexity at low metallicity, Figure [11](#abu2) shows a comparison of fractional abundances of COMs normalized by the CH$_3$OH column density for WB89-789 SMM1 and NGC7192 FIRS2. Such a comparison is useful for investigating chemistry of organic molecules in warm and dense gas around protostars (cite: Her09; Dro19), because CH$_3$OH is believed to be a parental molecule for the formation of even larger COMs (cite: NM04; Gar06). In addition, CH$_3$OH is a product of grain surface reaction, thus warm CH$_3$OH gas mainly arise from a high-temperature region, where ices are sublimated and characteristic hot core chemistry proceeds. Furthermore, the normalization by CH$_3$OH can cancel the metallicity effect in the abundance comparison.

The $N$(X)/$N$(CH$_3$OH) ratios are remarkably similar between WB89-789 SMM1 and NGC7192 FIRS2 as shown in Figure [11](#abu2) (a). The ratios of SMM1 coincide with those of NGC7192 FIRS2 within a factor of 2 for the most molecular species. The correlation coefficient is calculated to be 0.94, while it is 0.96 if CH$_3$CN is excluded. It seems that CH$_3$CN deviates from the overall trend, although the uncertainty is large due to the opacity effect (see [3.3.4](#sec_x)). C$_2$H$_5$OH also slightly deviates from the trend. The reason for their behavior is still unclear, but it may be related to the formation pathway of those molecules.

The above two comparisons suggest that chemical compositions of the hot core in the extreme outer Galaxy scale with the metallicity. In the WB89-789 region, the metallicity is expected to be four times lower compared to the solar neighborhood. The observed abundances of COMs in the SMM1 hot core is lower than the other Galactic hot cores, but the decrease is proportional to this metallicity. Furthermore, similar $N$(COMs)/$N$(CH$_3$OH) ratios suggest that CH$_3$OH is an important parental species for the formation of larger COMs in a hot core, as suggested by aforementioned theoretical studies.

CH$_3$OH ice is believed to form on grain surfaces and several formation processes are proposed by laboratory experiments; i.e., hydrogenation of CO, ultraviolet photolysis and radiolysis of ice mixtures (cite: Hud99; Wat07). It is known that CH$_3$OH is already formed in quiescent prestellar cores before star formation occurs (cite: Boo11). Solid CH$_3$OH will chemically evolve to larger COMs by a combination of photolysis, radiolysis, and grain heating during the warm-up phase that leads to the formation of a hot core (cite: Gar06). High-temperature gas-phase chemistry of sublimated CH$_3$OH would also contribute to the COMs formation (cite: NM04; Taq16). The present results suggest that various COMs can form even in a low-metallicity environment, if their parental molecule, CH$_3$OH, is efficiently produced in a star-forming core. We here note that observations of ice mantle compositions are not reported for the outer Galaxy so far . Future infrared observations of ice absorption bands towards embedded sources in the outer Galaxy are important.

![](f12.eps)

## Molecular abundances: Comparison with LMC hot cores

It is still unknown if the observed simply-metallicity-scaled chemistry of COMs in the WB89-789 SMM1 hot core is common in other hot core sources in the outer Galaxy. A comparison of the present data with those of hot cores in the LMC would provide a hint for understanding the universality of low-metallicity hot core chemistry. The metallicity of the LMC is reported to be lower than the solar value by a factor of two to three (cite: Duf82; Wes90; Rus92; Cho16), which is in common with the outer Galaxy.

Figure [12](#abu3) shows a comparison of molecular abundances between WB89-789 SMM1 and three LMC hot cores. The plotted molecular column densities for LMC hot cores are adopted from (cite: ST16) for ST11, (cite: ST20) for ST16, and (cite: Sew18) fro N113 A1. Another LMC hot core in (cite: Sew18), N113 B3, have similar molecular abundances with those of N113 A1. The $N_{\mathrm{H_2}}$ value of ST11 and N113 A1 is re-estimated using the same dust opacity data and dust temperature ($T_{d}$ = 60 K) as in this work; We obtained $N_{\mathrm{H_2}}$ = 1.2 $\times$ 10$^{24}$ cm$^{-2}$ for ST11 and $N_{\mathrm{H_2}}$ = 9.2 $\times$ 10$^{23}$ cm$^{-2}$ for N113 A1. The dust temperature assumed in ST16 is 60 K as described in Section [3.3.3](#sec_h2). Molecular column densities are estimated for circular/elliptical regions of 0.12 $\times$ 0.12 pc, 0.10 $\times$ 0.10 pc, and 0.21 $\times$ 0.13 pc for ST11, ST16, and N113 A1, respectively. For a fair comparison, we have re-calculated $N_{\mathrm{H_2}}$ and molecular column densities of SMM1 for a 0.1 pc (1.93$''$) diameter region. Those abundances are plotted in Figure [12](#abu3) and summarized in Table [4](#tab_X).

The chemical composition of the outer Galaxy hot core does not resemble those of LMC hot cores as seen in Figure [12](#abu3). The dissimilarity is also seen in the $N$(X)/$N$(CH$_3$OH) comparison between SMM1 and ST16 as shown in Figure [11](#abu2) (b), where the correlation coefficient is calculated to be 0.69.

(cite: ST20) argue that SO$_2$ will be a good tracer of low-metallicity hot core chemistry, because (i) it is commonly detected in LMC hot cores with similar abundances, and (ii) it is originated from a compact hot core region. SO also shows similar abundances within LMC hot cores. In WB89-789 SMM1, however, the abundances of SO$_2$ and SO relative to H$_2$ are lower by a factor of 28 and 5 compared with LMC hot cores. The measured rotation temperatures of SO$_2$ are similar between those hot cores, i.e., 166 K (SO$_2$) for SMM1, 232 K (SO$_2$) and 86 K ($^{34}$SO$_2$) for ST16, 190 K (SO$_2$) and 95 K ($^{34}$SO$_2$) for ST11. The SO$_2$ column densities for ST16 and ST11 are estimated from $^{34}$SO$_2$, while that for SMM1 is from SO$_2$. However, the SO$_2$ column density of SMM1 increases only by a factor of up to three when it is estimated from $^{34}$SO$_2$ (see Section [3.3.4](#sec_x)). Thus the low SO$_2$ abundance in the outer Galactic hot core would not be due to the optical thickness.

In contrast to the S-O bond bearing species, the C-S bond bearing species such as CS, H$_2$CS , and OCS do not show significant abundance decrease in WB89-789 SMM1. Thus it is not straightforward to attribute the low abundance of SO$_2$ (and perhaps SO) to the low elemental abundance ratio of sulfur in the outer Galaxy. Hot core chemistry models suggest that SO$_2$ is mainly produced in high-temperature gas-phase reactions in warm gas, using H$_2$S sublimated from ice mantles (cite: Cha97; NM04). This also applies to the SO$_2$ formation in low-metallicity sources as shown in astrochemical simulations for LMC hot cores (cite: ST20). We speculate that the different behavior of SO$_2$ in outer Galaxy and LMC hot cores may be related to differences in the evolutionary stage of hot cores. A different luminosity of host protostars may also contribute to the different sulfur chemistry; i.e., $\sim$8 $\times$ 10$^3$ L$_{\ensuremath{\odot}}$ for WB89-789-SMM1, while several $\times$ 10$^5$ L$_{\ensuremath{\odot}}$ for LMC hot cores. A different cosmic-ray ionization rate between the outer Galaxy and the LMC may also affect the chemical evolution, although the rate is not known for the outer Galaxy.

Among nitrogen-bearing molecules, NO shows interesting behavior in LMC hot cores. After corrected for the metallicity, NO is overabundant in LMC hot cores compared with Galactic counterparts despite the low elemental abundance of nitrogen in the LMC (cite: ST20). Only NO shows such behavior among the nitrogen-bearing molecules observed in LMC hot cores. In WB89-789 SMM1, however, such an overabundance of NO is not observed. The NO abundance of SMM1 is 1.6 $\times$ 10$^{-9}$ for a 0.1 pc region data. This is a factor of five lower than a typical NO abundance in Galactic high-mass hot cores (cite: Ziu91), which is consistent with a factor of four lower metallicity in WB89-789. The present high-spatial resolution data have revealed that NO does not mainly arise from a hot core region, as shown in Figure [4](#images1). It has an intensity peak at the south part of the hot core, where low-excitation lines of SO and SO$_2$ also have a secondary peak (Section [4.2](#sec_disc_dist)). Thus, shock chemistry or photochemistry, rather than high-temperature chemistry, would contribute to the production of NO in low-metallicity protostellar cores. In that case, a lower luminosity of SMM1 than those of LMC hot cores may contribute to the different behavior of NO.

For other nitrogen-bearing molecules, HNCO and CH$_3$CN, a clear difference is not identified between outer Galactic and LMC hot cores, although the number of data points is limited and the abundance uncertainty is large. The reason of the unusually low abundance of SiO in SMM1 is unknown. It may be related to different shock conditions or grain compositions, because dust sputtering by shock is mainly responsible for the production of SiO gas.

Formation of COMs is one of the important standpoints for low-metallicity hot core chemistry. It is reported that CH$_3$OH show a large abundance variation in LMC hot cores (cite: ST20). There are organic-poor hot cores such as ST11 and ST16, while N113 A1 and B3 are organic-rich. The CH$_3$OH abundance of WB89-789 SMM1 is higher than those of any known LMC hot cores. The abundances of HCOOCH$_3$ and CH$_3$OCH$_3$ in SMM1 are comparable with those of an organic-rich LMC hot core, N113 A1. Th detection of many other COMs in SMM1 suggests the source have experienced rich organic chemistry despite its low-metallicity nature.

Astrochemical simulations for LMC hot cores suggest that dust temperature at the initial ice-forming stage have a major effect on the abundance of CH$_3$OH gas in the subsequent hot core stage (cite: Ach18; ST20). Simulations of grain surface chemistry dedicated to the LMC environment also suggest that dust temperature is one of the key parameters for the formation of CH$_3$OH in dense cores (cite: Ach15; Pau18). This is because (i) CH$_3$OH is mainly formed by the grain surface reaction, and (ii) the hydrogenation reaction of CO, which is a dominant pathway for the CH$_3$OH formation, is sensitive to the dust temperature due to the high volatility of atomic hydrogen. For this reason, it is inferred that organic-rich hot cores had experienced a cold stage ($\lesssim$ 10K) that is sufficient for the CH$_3$OH formation before the hot core stage, while organic-poor ones might have missed such a condition for some reason. Alternatively, the slight difference in the hot core’s evolutionary stage may contribute to the CH$_3$OH abundance variation, because the high-temperature gas-phase chemistry is rapid and it can decrease CH$_3$OH gas at a late stage (cite: NM04; Gar06; Vas13; Bal15).

Low-metallicity hot core chemistry simulations in (cite: ST20) argue that the maximum achievable abundances of CH$_3$OH gas in a hot core stage significantly decrease as the visual extinction of the initial ice-forming stage decreases. On the other hand, the simulations show that the CH$_3$OH gas abundance is simply metallicity-scaled if the initial ice-forming stage is sufficiently shielded. In a well-shielded initial condition, the grain surface is cold enough to trigger the CO hydrogenation, and the resultant CH$_3$OH abundance is roughly regulated by the elemental abundances. The observed metallicity-scaled chemistry of COMs in WB89-789 SMM1 implies that the source had experienced such an initial condition before the hot core stage.

Deuterium chemistry is widely used in interpreting chemical and physical history of interstellar molecules (cite: Cas12; Cec14). The measured CH$_2$DOH/CH$_3$OH ratio in WB89-789 SMM1 is 1.1 $\pm$ 0.2 $\%$, which is comparable to the higher end of those ratios observed in high-mass protostars and the lower end of those in low-mass protostars (cite: Dro21). The ratio is orders of magnitude higher than the deuterium-to-hydrogen ratio in the solar neighborhood (cite: Lin06; Pro10) and that in the big-bang nucleosynthesis (cite: Bur02). This suggests that the efficient deuterium fractionation occurred upon the formation of CH$_3$OH in SMM1. The D$_2$CO/HDCO ratio is 45 $\pm$ 10 $\%$, which is comparable to those observed in low-mass and high-mass protostars (cite: Zah21). This would suggest that physical conditions for deuterium fractionation could be similar between WB89-789 SMM1 and inner Galactic protostars. Note that higher spatial resolution observations and detailed multiline analyses would affect the measured abundance of deuterated species as in (cite: Per18) for the case of a nearby low-mass protostar. The H$_2$CO column density derived in this work may be a lower limit because the line is often optically thick, thus we do not discuss the abundance ratio relative to H$_2$CO.

It is known that the deuterium fractionation efficiently proceeds at low temperature (cite: Rob03; Cas12; Taq14; Fur16). This is because the key reaction for the trigger of deuterium fractionation, H$^+_3$ + HD $\rightarrow$ H$_2$D$^+$ + H$_2$ + 232 K, is exothermic and its backward reaction cannot proceed below 20 K. In addition, gaseous neutral species such as CO and O efficiently destruct H$_2$D$^+$, thus their depletion at low temperature further enhances the deuterium fractionation (cite: Cas12). A sign of high deuterium fractionation observed in WB89-789 SMM1 suggests that the source had experienced such a cold environment during its formation. This picture is consistent with the implication obtained from the metallicity-scaled chemistry of COMs, which also suggests the occurrence of a cold and well-shielded initial condition as discussed above.

Although the low metallicity is common between the outer Galaxy and the LMC, their star-forming environments would be different; the LMC has more harsh environments as inferred from active massive star formation over the whole galaxy, while that for the outer Galaxy might be quiescent due to its low star formation activity. Those environmental differences need to be taken into account for further understanding of the chemical evolution of star-forming regions at low metallicity. Future extensive survey of protostellar objects towards the outer Galaxy is thus vitally important for further discussion. Astrochemical simulations dedicated to the environment of the outer Galaxy, and the application to lower-mass protostars, are also important.

## Another embedded protostar traced by high-velocity SiO gas

We have also detected a compact source associated with high-velocity SiO gas at the east side of WB89-789 SMM1. Hereafter, we refer to this source as WB89-789-SMM2. According to the SiO emission, the source is located at RA = 06$^\mathrm{h}$17$^\mathrm{m}$24.246s and Dec = 14$^\circ$54$\ensuremath{'}$43.25$''$ (ICRS), which is 2.7$''$ (0.14 pc) away from SMM2. Figure [13](#moment1_SiO)(a) shows the SiO(6-5) spectrum extracted from a 0.6$''$ diameter region centered at the above position. The SiO line is largely shifted to the blue and red sides relative to the systemic velocity in a symmetric fashion. The peaks of the shifted emission are located at $V_{sys}$ $\pm$ 25 km s$^{-1}$.

![](f13.eps)

Figure [13](#moment1_SiO)(b) shows a velocity map and integrated intensity distribution of SiO(6-5). In the figure, to focus on SiO in WB89-789-SMM2, the intensity is integrated over much wider velocity range (0–60 km s$^{-1}$) compared with that adopted in Figure [4](#images1) (31–38 km s$^{-1}$). The velocity map clearly indicates that the velocity structure of SiO in SMM2 is spatially symmetric to the SiO center. At this position, a local peak is seen in 1200 $\mu$m continuum as shown in the figure, suggesting the presence of an embedded source. SMM2 does not show any emission lines of COMs, and no alternative molecular lines are identified at the of doppler-shifted SiO emission. Also taking into account the clear spectral and spatial symmetry, the observed lines must be attributed to high-velocity SiO gas.

The spectral characteristics of the observed high-velocity SiO resemble those of extremely high velocity (EHV) outflows observed in Class 0 protostars (cite: Bac91; Taf10; Taf15; Tyc19). The EHV flows are known to appear as a discrete high-velocity ($V$ $\gtrsim$30 km s$^{-1}$) peak, and observed in the youngest stage of star formation (cite: Bac96; Mat19). The EHV flows extends up to several thousands au from the central protostar in SiO, and usually have collimated bipolar structures (cite: Bac91; Hir10; Tyc19; Mat19). The beam size of the present data is about 5000 au, thus such structures will not be spatially resolved. Actually, a symmetric spatial distribution of blue-/red-shifted SiO is only marginally resolved into two beam size regions (Fig. [13](#moment1_SiO)(b)). A spatial extent of SiO emission is about 1$\ensuremath{''}$ (0.052 pc). Assuming an outflow velocity of 25 km s$^{-1}$, we estimate a dynamical timescale of EHV flows to be at least 2000 years. This is roughly consistent with dynamical timescales of other EHV sources, which range from a few hundred to a few thousand years (cite: Bac96).

A 1200 $\mu$m continuum flux in a 0.6$''$ diameter region centered at SMM2 is 0.60 $\pm$ 0.05 mJy/beam. Assuming $T_{d}$ = 20 K, we obtain $N_{\mathrm{H_2}}$ = 3.2 $\times$ 10$^{23}$ cm$^{-2}$. This is equivalent to a gas number density of $n_{\mathrm{H_2}}$ = 4.9 $\times$ 10$^6$ cm$^{-3}$. If we assume a higher $T_{d}$, i.e. 40 K, then the derived column density is 2.5 times lower than the . In either case, the continuum data suggests the presence of high-density gas at this position.

Previous single-dish observations of CO detected extended ($\sim$20$\ensuremath{''}$) molecular outflows in the WB89-789 region (cite: Bra94; Bra07). The center of the outflow gas coincides with the position of the IRAS source (IRAS 06145+1455; 06$^\mathrm{h}$17$^\mathrm{m}$24.2s, 14$\ensuremath{^\circ}$54$\ensuremath{'}$42$\ensuremath{''}$, J2000). This position is consistent with those of SMM1 or SMM2, given the large beam size of CO(3-2) observations (14$\ensuremath{''}$) in (cite: Bra07). The observed CO outflow gas has an extended blue-shifted component (20 $<$ $V_{LSR}$ $<$ 31 km $s^{-1}$) towards the south-east direction from the center, while a red-shifted component (37 $<$ $V_{LSR}$ $<$ 55 km $s^{-1}$) is extended towards the north-west direction (cite: Bra07). This outflow direction coincides with that of the high-velocity SiO outflows observed in this work. The SiO outflows from SMM2 may have a common origin with the large-scale CO outflows.

In summary, it is likely that a compact, high-density, and embedded object is located at the position of WB89-789-SMM2. Presumably, a protostar associated with SMM2 is driving the observed high-velocity SiO gas flows. Its short dynamical timescale and similarity with EHV flows suggest that the object is at the youngest stage of star formation (Class 0/I). Non-detection of warm gas emission also supports its young nature. We note that the detailed structure of high-velocity SiO gas is not spatially resolved, and CO lines, which often trace high-velocity outflows, are not covered in the present data. Future high-spatial resolution observations of CO and other outflow tracers are key to further clarify the nature of WB89-789-SMM2.

# Summary

The extreme outer Galaxy is an excellent laboratory to study star formation and interstellar medium in The following conclusions are obtained in this work.

1.  A hot molecular core is for the first time detected in the extreme outer Galaxy (WB89-789-SMM1), based on submillimeter observations with ALMA towards the WB89-789 star-forming region located at the galactocentric distance of 19 kpc.

2.  A variety of carbon-, oxygen-, nitrogen-, sulfur-, and silicon-bearing species, including complex organic molecules containing up to nine atoms and larger than CH$_3$OH, are detected towards a warm ($>$100 K) and compact ($<$ 0.03 pc) region associated with a protostar ($\sim$8 $\times$ 10$^3$ L$_{\ensuremath{\odot}}$). The results suggest that a great molecular complexity exists even in a environment of the extreme outer Galaxy.

3.  

4.  Fractional abundances of CH$_3$OH and other COMs relative to H$_2$ generally scale with the metallicity of WB89-789, which is a factor of four lower than the solar value.

5.  A comparison of fractional abundances of COMs relative to the CH$_3$OH column density between the outer Galactic hot core and a Galactic intermediate-mass hot core show a remarkable similarity. The results suggest the metallicity-scaled chemistry for the formation of COMs in this source. CH$_3$OH is an important parental molecule for the COMs formation even in a environment.

6.  On the other hand, the molecular abundances of the present hot core do not resemble those of LMC hot cores. We speculate that different luminosities or star-forming environments between outer Galactic and LMC hot cores may contribute to this.

7.  According to astrochemical simulations of low-metallicity hot cores, the observed metallicity-scaled chemistry of COMs in WB89-789-SMM1 implies that the source had experienced well-shielded and cold ice-forming stage before the hot core stage.

8.  We have also detected another compact source (WB89-789-SMM2) associated with high-velocity SiO gas ($V_{sys}$ $\pm$ 25 km s$^{-1}$) in the same region. The characteristics of the source resemble those of EHV outflows observed in Class 0 protostars. Physical properties and dynamical timescale of this outflow source are discussed.

This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2017.1.01002.S ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work has made extensive use of the Cologne Database for Molecular Spectroscopy and the molecular database of the Jet Propulsion Laboratory. This work makes use of data products from the Two Micron All Sky Survey, which is a joint project of the University of Massachusetts and the Infrared Processing and Analysis Center/California Institute of Technology, funded by the National Aeronautics and Space Administration and the National Science Foundation. This work was supported by JSPS KAKENHI Grant Number .

# Software

CASA (cite: McM07))

natexlab

(ref: Ach15) Acharyya, K., & Herbst, E. 2015, ApJ, 812, 142

(ref: Ach18) —. 2018, ApJ, 859, 51

(ref: And15) Anderson, L. D., Armentrout, W. P., Johnstone, B. M., et al. 2015, ApJS, 221, 26

(ref: And18) Anderson, L. D., Armentrout, W. P., Luisi, M., et al. 2018, ApJS, 234, 33

(ref: Are20) Arellano-Córdova, K. Z., Esteban, C., Garcı́a-Rojas, J., & Méndez-Delgado, J. E. 2020, MNRAS, 496, 1051

(ref: Are21) —. 2021, MNRAS, 502, 225

(ref: Bac96) Bachiller, R. 1996, ARA&A, 34, 111

(ref: Bac91) Bachiller, R., Martin-Pintado, J., & Fuente, A. 1991, A&A, 243, L21

(ref: Bal15) Balucani, N., Ceccarelli, C., & Taquet, V. 2015, MNRAS, 449, L16

(ref: Beu02) Beuther, H., Schilke, P., Sridharan, T. K., et al. 2002, A&A, 383, 892

(ref: Boo11) Boogert, A. C. A., Huard, T. L., Cook, A. M., et al. 2011, ApJ, 729, 92

(ref: Bra19) Bragança, G. A., Daflon, S., Lanz, T., et al. 2019, A&A, 625, A120

(ref: Bra94) Brand, J., & Wouterloot, J. G. A. 1994, A&AS, 103, 503

(ref: Bra07) —. 2007, A&A, 464, 909

(ref: Bur02) Burles, S. 2002, , 50, 1245

(ref: Cas12) Caselli, P., & Ceccarelli, C. 2012, A&ARv, 20, 56

(ref: Cec14) Ceccarelli, C., Caselli, P., Bockelée-Morvan, D., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 859

(ref: Cha97) Charnley, S. B. 1997, ApJ, 481, 396

(ref: Chi96b) Chin, Y.-N., Henkel, C., Whiteoak, J. B., Langer, N., & Churchwell, E. B. 1996, A&A, 305, 960

(ref: Cho16) Choudhury, S., Subramaniam, A., & Cole, A. A. 2016, MNRAS, 455, 1855

(ref: Cox00) Cox, A. N. 2000, Allen’s astrophysical quantities (Springer)

(ref: Dra03) Draine, B. T. 2003, ARA&A, 41, 241

(ref: Dro19) Drozdovskaya, M. N., van Dishoeck, E. F., Rubin, M., Jørgensen, J. K., & Altwegg, K. 2019, MNRAS, 490, 50

(ref: Dro21) Drozdovskaya, M. N., Schroeder I, I. R. H. G., Rubin, M., et al. 2021, MNRAS, 500, 4901

(ref: Duf82) Dufour, R. J., Shields, G. A., & Talbot, Jr., R. J. 1982, ApJ, 252, 461

(ref: Fer98) Ferguson, A. M. N., Gallagher, J. S., & Wyse, R. F. G. 1998, AJ, 116, 673

(ref: Fer17) Fernández-Martı́n, A., Pérez-Montero, E., Vı́lchez, J. M., & Mampaso, A. 2017, A&A, 597, A84

(ref: Fue93) Fuente, A., Martin-Pintado, J., Cernicharo, J., & Bachiller, R. 1993, A&A, 276, 473

(ref: Fue14) Fuente, A., Cernicharo, J., Caselli, P., et al. 2014, A&A, 568, A65

(ref: Fur16) Furuya, K., van Dishoeck, E. F., & Aikawa, Y. 2016, A&A, 586, A127

(ref: Gar06) Garrod, R. T., & Herbst, E. 2006, A&A, 457, 927

(ref: Gol99) Goldsmith, P. F., & Langer, W. D. 1999, ApJ, 517, 209

(ref: Her09) Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: Hir10) Hirano, N., Ho, P. P. T., Liu, S.-Y., et al. 2010, ApJ, 717, 58

(ref: Hud99) Hudson, R. L., & Moore, M. H. 1999, Icarus, 140, 451

(ref: Hum20) Humire, P. K., Thiel, V., Henkel, C., et al. 2020, A&A, 642, A222

(ref: Izu17) Izumi, N., Kobayashi, N., Yasui, C., Saito, M., & Hamano, S. 2017, AJ, 154, 163

(ref: Jan95) Jansen, D. J., Spaans, M., Hogerheijde, M. R., & van Dishoeck, E. F. 1995, A&A, 303, 541

(ref: Kob08) Kobayashi, N., Yasui, C., Tokunaga, A. T., & Saito, M. 2008, ApJ, 683, 178

(ref: Kur00) Kurtz, S., Cesaroni, R., Churchwell, E., Hofner, P., & Walmsley, C. M. 2000, Protostars and Planets IV, 299

(ref: Lin06) Linsky, J. L., Draine, B. T., Moos, H. W., et al. 2006, ApJ, 647, 1106

(ref: Mat19) Matsushita, Y., Takahashi, S., Machida, M. N., & Tomisaka, K. 2019, ApJ, 871, 221

(ref: Mau15) Maud, L. T., Moore, T. J. T., Lumsden, S. L., et al. 2015, MNRAS, 453, 645

(ref: McM07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mul05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: Mul01) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: Nak16) Nakanishi, H., & Sofue, Y. 2016, PASJ, 68, 5

(ref: NM04) Nomura, H., & Millar, T. J. 2004, A&A, 414, 409

(ref: Oss94) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Pau18) Pauly, T., & Garrod, R. T. 2018, ApJ, 854, 13

(ref: Per18) Persson, M. V., Jørgensen, J. K., Müller, H. S. P., et al. 2018, A&A, 610, A54

(ref: Pet17) Pety, J., Guzmán, V. V., Orkisz, J. H., et al. 2017, A&A, 599, A98

(ref: Pic98) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: Pro10) Prodanović, T., Steigman, G., & Fields, B. D. 2010, MNRAS, 406, 1108

(ref: Rob03) Roberts, H., Herbst, E., & Millar, T. J. 2003, ApJL, 591, L41

(ref: Rob07) Robitaille, T. P., Whitney, B. A., Indebetouw, R., & Wood, K. 2007, ApJS, 169, 328

(ref: Rod98) Rodriguez-Franco, A., Martin-Pintado, J., & Fuente, A. 1998, A&A, 329, 1097

(ref: Rus92) Russell, S. C., & Dopita, M. A. 1992, ApJ, 384, 508

(ref: Sch97) Schutte, W. A., & Greenberg, J. M. 1997, A&A, 317, L43

(ref: Sew18) Sewiło, M., Indebetouw, R., Charnley, S. B., et al. 2018, ApJL, 853, L19

(ref: ST16) Shimonishi, T., Dartois, E., Onaka, T., & Boulanger, F. 2016a, A&A, 585, A107

(ref: ST20) Shimonishi, T., Das, A., Sakai, N., et al. 2020, ApJ, 891, 164

(ref: ST16b) Shimonishi, T., Onaka, T., Kawamura, A., & Aikawa, Y. 2016b, ApJ, 827, 72

(ref: Skr06) Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ, 131, 1163

(ref: Ste95) Sternberg, A., & Dalgarno, A. 1995, ApJS, 99, 565

(ref: Sut95) Sutton, E. C., Peng, R., Danchi, W. C., et al. 1995, ApJS, 97, 455

(ref: Taf15) Tafalla, M., Bachiller, R., Lefloch, B., et al. 2015, A&A, 573, L2

(ref: Taf10) Tafalla, M., Santiago-Garcı́a, J., Hacar, A., & Bachiller, R. 2010, A&A, 522, A91

(ref: Taq14) Taquet, V., Charnley, S. B., & Sipilä, O. 2014, ApJ, 791, 1

(ref: Taq16) Taquet, V., Wirström, E. S., & Charnley, S. B. 2016, ApJ, 821, 46

(ref: Tyc19) Tychoniec, Ł., Hull, C. L. H., Kristensen, L. E., et al. 2019, A&A, 632, A101

(ref: vdT07) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: vanD98) van Dishoeck, E. F., & Blake, G. A. 1998, ARA&A, 36, 317

(ref: Vas13) Vasyunin, A. I., & Herbst, E. 2013, ApJ, 769, 34

(ref: Wat07) Watanabe, N., Mouri, O., Nagaoka, A., et al. 2007, ApJ, 668, 1001

(ref: Wen19) Wenger, T. V., Balser, D. S., Anderson, L. D., & Bania, T. M. 2019, ApJ, 887, 114

(ref: Wen21) Wenger, T. V., Dawson, J. R., Dickey, J. M., et al. 2021, ApJS, 254, 36

(ref: Wes90) Westerlund, B. E. 1990, A&ARv, 2, 29

(ref: Whi01b) Whittet, D. C. B., Gerakines, P. A., Hough, J. H., & Shenoy, S. S. 2001, ApJ, 547, 872

(ref: Wil94) Wilson, T. L., & Rood, R. 1994, ARA&A, 32, 191

(ref: Wir11) Wirström, E. S., Geppert, W. D., Hjalmarson, Å., et al. 2011, A&A, 533, A24

(ref: Wou93) Wouterloot, J. G. A., Brand, J., & Fiegle, K. 1993, A&AS, 98, 589

(ref: Wri10) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868

(ref: Yam10) Yamamura, I., Makiuti, S., Ikeda, N., et al. 2010, VizieR Online Data Catalog, II/298

(ref: Yas06) Yasui, C., Kobayashi, N., Tokunaga, A. T., Terada, H., & Saito, M. 2006, ApJ, 649, 753

(ref: Zah21) Zahorecz, S., Jimenez-Serra, I., Testi, L., et al. 2021, A&A, 653, A45

(ref: ZY07) Zinnecker, H., & Yorke, H. W. 2007, ARA&A, 45, 481

(ref: Ziu91) Ziurys, L. M., McGonagle, D., Minh, Y., & Irvine, W. M. 1991, ApJ, 373, 535

# Measured line parameters

Tables [5](#tab_lines1)–[13](#tab_lines9) summarize measured line parameters (see Section [3.1](#sec_spc) for details).

The tabulated uncertainties and upper limits are of 2$\sigma$ level and do not include systematic errors due to continuum subtraction. Upper limits are estimated assuming $\Delta$$V$ = 4 km s$^{-1}$.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | $E_{u}$ | Frequency | $T_{br}$ | $\Delta$$V$ | $\int T_{br} dV$ | $V_{LSR}$ | RMS | Note |
|  |  | \(K\) | (GHz) | \(K\) | (km/s) | (K km/s) | (km/s) | \(K\) |  |
| HDO | 2$_{1,1}$–2$_{1,2}$ | 95 | 241.56155 | 0.99 $\pm$ 0.03 | 4.8 | 5.05 $\pm$ 0.29 | 34.6 | 0.04 | ... |
| HDO | 7$_{3,4}$–6$_{4,3}$ | 837 | 241.97357 | 0.28 $\pm$ 0.02 | 2.1 | 0.63 $\pm$ 0.12 | 34.1 | 0.04 | ... |
| H$^{13}$CO$^+$ | 3–2 | 25 | 260.25534 | 5.85 $\pm$ 0.02 | 2.3 | 14.23 $\pm$ 0.13 | 34.1 | 0.03 | ... |
| HC$^{18}$O$^+$ | 4–3 | 41 | 340.63069 | 0.64 $\pm$ 0.05 | 1.9 | 1.29 $\pm$ 0.20 | 34.1 | 0.07 | ... |
| CCH | N = 4–3, J = $\frac{9}{2}$–$\frac{7}{2}$, F = 5–4 | 42 | 349.33771 | 4.39 $\pm$ 0.04 | 2.6 | 12.32 $\pm$ 0.24 | 33.7 | 0.08 | \(1\) |
| CCH | N = 4–3, J = $\frac{7}{2}$–$\frac{5}{2}$, F = 4–3 | 42 | 349.39928 | 3.54 $\pm$ 0.04 | 2.8 | 10.49 $\pm$ 0.26 | 33.7 | 0.08 | \(1\) |
| c-C$_3$H$_2$ | 3$_{2,1}$–2$_{1,2}$ | 18 | 244.22215 | 0.23 $\pm$ 0.02 | 4.8 | 1.18 $\pm$ 0.27 | 33.6 | 0.04 | ... |
| c-C$_3$H$_2$ | 5$_{3,2}$–4$_{4,1}$ | 45 | 260.47975 | 0.09 $\pm$ 0.02 | 1.6 | 0.15 $\pm$ 0.10 | 32.9 | 0.03 | \(2\) |
| H$_2$CO | 5$_{1,5}$–4$_{1,4}$ | 62 | 351.76864 | 7.02 $\pm$ 0.05 | 3.7 | 27.32 $\pm$ 0.40 | 34.2 | 0.08 | ... |
| HDCO | 4$_{2,3}$–3$_{2,2}$ | 63 | 257.74870 | 0.94 $\pm$ 0.02 | 2.8 | 2.80 $\pm$ 0.14 | 34.3 | 0.03 | ... |
| HDCO | 4$_{2,2}$–3$_{2,1}$ | 63 | 259.03491 | 0.97 $\pm$ 0.02 | 2.9 | 3.00 $\pm$ 0.18 | 34.3 | 0.03 | ... |
| D$_2$CO | 4$_{1,3}$–3$_{1,2}$ | 35 | 245.53275 | 0.64 $\pm$ 0.03 | 2.3 | 1.54 $\pm$ 0.15 | 34.2 | 0.04 | ... |
| D$_2$CO | 6$_{2,5}$–5$_{2,4}$ | 80 | 349.63061 | 0.76 $\pm$ 0.04 | 2.4 | 1.92 $\pm$ 0.23 | 33.9 | 0.08 | ... |

: Line Parameters for HDO, H$^{13}$CO$^+$, HC$^{18}$O$^+$, CCH, c-C$_3$H$_2$, H$_2$CO, HDCO, D$_2$CO

Table notes: (1) Blend of two hyperfine components.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | $E_{u}$ | Frequency | $T_{br}$ | $\Delta$$V$ | $\int T_{br} dV$ | $V_{LSR}$ | RMS | Note |
|  |  | \(K\) | (GHz) | \(K\) | (km/s) | (K km/s) | (km/s) | \(K\) |  |
| H$^{13}$CN | 3–2 | 25 | 259.01180 | 3.25 $\pm$ 0.02 | 4.2 | 14.45 $\pm$ 0.19 | 34.3 | 0.03 | ... |
| HC$^{15}$N | 3–2 | 25 | 258.15700 | 1.95 $\pm$ 0.02 | 3.6 | 7.45 $\pm$ 0.19 | 34.3 | 0.03 | ... |
| CN | N = 3–2, J = $\frac{5}{2}$–$\frac{5}{2}$, F = $\frac{3}{2}$–$\frac{3}{2}$ | 33 | 339.44678 | 0.30 $\pm$ 0.04 | 2.6 | 0.82 $\pm$ 0.22 | 34.6 | 0.07 | ... |
| CN | N = 3–2, J = $\frac{5}{2}$–$\frac{5}{2}$, F = $\frac{5}{2}$–$\frac{5}{2}$ | 33 | 339.47590 | 0.39 $\pm$ 0.04 | 1.7 | 0.71 $\pm$ 0.17 | 34.0 | 0.07 | ... |
| CN | N = 3–2, J = $\frac{5}{2}$–$\frac{5}{2}$, F = $\frac{7}{2}$–$\frac{7}{2}$ | 33 | 339.51664 | 0.73 $\pm$ 0.04 | 1.8 | 1.38 $\pm$ 0.18 | 34.1 | 0.07 | ... |
| CN | N = 3–2, J = $\frac{5}{2}$–$\frac{3}{2}$, F = $\frac{5}{2}$–$\frac{5}{2}$ | 33 | 340.00813 | 0.95 $\pm$ 0.04 | 2.1 | 2.16 $\pm$ 0.20 | 33.9 | 0.07 | ... |
| CN | N = 3–2, J = $\frac{5}{2}$–$\frac{3}{2}$, F = $\frac{3}{2}$–$\frac{3}{2}$ | 33 | 340.01963 | 0.93 $\pm$ 0.04 | 1.8 | 1.81 $\pm$ 0.17 | 34.1 | 0.07 | ... |
| CN | N = 3–2, J = $\frac{5}{2}$–$\frac{3}{2}$, F = $\frac{7}{2}$–$\frac{5}{2}$ | 33 | 340.03155 | 3.08 $\pm$ 0.04 | 2.7 | 8.71 $\pm$ 0.25 | 33.8 | 0.07 | ... |
| CN | N = 3–2, J = $\frac{5}{2}$–$\frac{3}{2}$, F = $\frac{5}{2}$–$\frac{3}{2}$ | 33 | 340.03541 | 3.04 $\pm$ 0.04 | 2.1 | 6.87 $\pm$ 0.26 | 33.7 | 0.07 | \(1\) |
| CN | N = 3–2, J = $\frac{7}{2}$–$\frac{5}{2}$, F = $\frac{9}{2}$–$\frac{7}{2}$ | 33 | 340.24777 | 4.38 $\pm$ 0.03 | 2.4 | 11.32 $\pm$ 0.22 | 33.4 | 0.07 | \(1\) |
| CN | N = 3–2, J = $\frac{7}{2}$–$\frac{5}{2}$, F = $\frac{5}{2}$–$\frac{5}{2}$ | 33 | 340.26177 | 0.91 $\pm$ 0.04 | 1.9 | 1.85 $\pm$ 0.18 | 34.1 | 0.07 | ... |
| CN | N = 3–2, J = $\frac{7}{2}$–$\frac{5}{2}$, F = $\frac{7}{2}$–$\frac{7}{2}$ | 33 | 340.26495 | 1.02 $\pm$ 0.04 | 2.0 | 2.12 $\pm$ 0.18 | 33.9 | 0.07 | ... |
| NO | J = $\frac{7}{2}$–$\frac{5}{2}$, $\Omega$ = $\frac{1}{2}$, F = $\frac{9}{2}$$^+$–$\frac{7}{2}$$^-$ | 36 | 351.04352 | 0.29 $\pm$ 0.03 | 2.5 | 0.78 $\pm$ 0.22 | 33.7 | 0.08 | ... |
| NO | J = $\frac{7}{2}$–$\frac{5}{2}$, $\Omega$ = $\frac{1}{2}$, F = $\frac{7}{2}$$^+$–$\frac{5}{2}$$^-$ | 36 | 351.05171 | 0.50 $\pm$ 0.04 | 2.1 | 1.10 $\pm$ 0.20 | 34.3 | 0.08 | \(2\) |
| HNCO | 11$_{4,7}$–10$_{4,6}$ | 720 | 241.49864 | 0.32 $\pm$ 0.08 | 4.8 | 1.20 $\pm$ 0.13 | 33.8 | 0.04 | \(2\) |
| HNCO | 11$_{3,9}$–10$_{3,8}$ | 445 | 241.61930 | 0.51 $\pm$ 0.02 | 4.1 | 2.19 $\pm$ 0.25 | 33.6 | 0.04 | \(2\) |
| HNCO | 11$_{2,10}$–10$_{2,9}$ | 240 | 241.70385 | $<$0.60 | ... | $<$2.6 | ... | 0.04 | \(3\) |
| HNCO | 11$_{0,11}$–10$_{0,10}$ | 70 | 241.77403 | 0.93 $\pm$ 0.02 | 4.9 | 4.87 $\pm$ 0.26 | 34.6 | 0.04 | ... |
| HNCO | 11$_{1,10}$–10$_{1,9}$ | 113 | 242.63970 | 0.79 $\pm$ 0.02 | 5.0 | 4.18 $\pm$ 0.27 | 34.7 | 0.04 | ... |
| HNCO | 16$_{1,16}$–15$_{1,15}$ | 186 | 350.33306 | 0.69 $\pm$ 0.04 | 5.1 | 3.73 $\pm$ 0.44 | 34.5 | 0.08 | ... |
| HNCO | 16$_{4,13}$–15$_{4,12}$ | 794 | 351.24085 | $<$0.25 | ... | $<$1.1 | ... | 0.08 | \(3\) |
| HNCO | 16$_{3,14}$–15$_{3,13}$ | 518 | 351.41680 | 0.33 $\pm$ 0.04 | 5.2 | 1.83 $\pm$ 0.45 | 34.4 | 0.08 | \(2\) |
| HNCO | 16$_{2,15}$–15$_{2,14}$ | 314 | 351.53780 | 0.43 $\pm$ 0.03 | 5.4 | 2.47 $\pm$ 0.49 | 34.1 | 0.08 | ... |
| HNCO | 16$_{2,14}$–15$_{2,13}$ | 314 | 351.55157 | 0.46 $\pm$ 0.03 | 5.8 | 2.82 $\pm$ 0.53 | 35.2 | 0.08 | ... |
| HNCO | 16$_{0,16}$–15$_{0,15}$ | 143 | 351.63326 | 0.72 $\pm$ 0.04 | 4.0 | 3.02 $\pm$ 0.41 | 34.6 | 0.08 | ... |
| HNCO | 23$_{1,23}$–24$_{0,24}$ | 333 | 351.99487 | 0.33 $\pm$ 0.03 | 5.5 | 1.91 $\pm$ 0.47 | 35.9 | 0.08 | ... |
| CH$_3$CN | 14$_{10}$–13$_{10}$ | 806 | 257.03344 | 0.14 $\pm$ 0.02 | 2.4 | 0.36 $\pm$ 0.10 | 34.0 | 0.03 | \(2\) |
| CH$_3$CN | 14$_{9}$–13$_{-9}$ | 671 | 257.12704 | $<$0.35 | ... | $<$1.5 | ... | 0.03 | \(2\) (4) |
| CH$_3$CN | 14$_{8}$–13$_{8}$ | 549 | 257.21088 | 0.24 $\pm$ 0.01 | 6.3 | 1.64 $\pm$ 0.27 | 34.9 | 0.03 | \(2\) |
| CH$_3$CN | 14$_{7}$–13$_{7}$ | 442 | 257.28494 | 0.42 $\pm$ 0.02 | 4.9 | 2.20 $\pm$ 0.21 | 34.3 | 0.03 | \(2\) |
| CH$_3$CN | 14$_{6}$–13$_{-6}$ | 350 | 257.34918 | 0.90 $\pm$ 0.02 | 4.7 | 4.51 $\pm$ 0.20 | 34.4 | 0.03 | \(2\) |
| CH$_3$CN | 14$_{5}$–13$_{5}$ | 271 | 257.40358 | $<$1.00 | ... | $<$4.3 | ... | 0.03 | \(2\) (3) |
| CH$_3$CN | 14$_{4}$–13$_{4}$ | 207 | 257.44813 | 1.14 $\pm$ 0.02 | 4.3 | 5.22 $\pm$ 0.19 | 34.4 | 0.03 | \(2\) |
| CH$_3$CN | 14$_{3}$–13$_{-3}$ | 157 | 257.48279 | 1.55 $\pm$ 0.02 | 4.6 | 7.55 $\pm$ 0.20 | 34.5 | 0.03 | \(2\) |
| CH$_3$CN | 14$_{2}$–13$_{2}$ | 121 | 257.50756 | 1.56 $\pm$ 0.02 | 4.4 | 7.34 $\pm$ 0.20 | 34.6 | 0.03 | \(2\) |
| CH$_3$CN | 14$_{1}$–13$_{1}$ | 100 | 257.52243 | 1.63 $\pm$ 0.02 | 3.8 | 6.61 $\pm$ 0.18 | 34.7 | 0.03 | \(2\) |
| CH$_3$CN | 14$_{0}$–13$_{0}$ | 93 | 257.52738 | 1.69 $\pm$ 0.02 | 4.3 | 7.79 $\pm$ 0.18 | 34.4 | 0.03 | ... |
| CH$_3$CN | 19$_{6}$–18$_{-6}$ | 425 | 349.21231 | 0.73 $\pm$ 0.04 | 3.9 | 3.07 $\pm$ 0.35 | 34.2 | 0.08 | \(2\) |
| CH$_3$CN | 19$_{5}$–18$_{5}$ | 346 | 349.28601 | 0.81 $\pm$ 0.04 | 3.4 | 2.97 $\pm$ 0.30 | 34.3 | 0.08 | \(2\) |
| CH$_3$CN | 19$_{4}$–18$_{4}$ | 282 | 349.34634 | 0.92 $\pm$ 0.03 | 4.3 | 4.18 $\pm$ 0.40 | 34.4 | 0.08 | \(2\) |
| CH$_3$CN | 19$_{3}$–18$_{-3}$ | 232 | 349.39330 | 1.24 $\pm$ 0.03 | 4.1 | 5.38 $\pm$ 0.39 | 34.4 | 0.08 | \(5\) |
| CH$_3$CN | 19$_{2}$–18$_{2}$ | 196 | 349.42685 | 1.04 $\pm$ 0.04 | 4.2 | 4.72 $\pm$ 0.37 | 34.6 | 0.08 | \(2\) |
| CH$_3$CN | 19$_{1}$–18$_{1}$ | 175 | 349.44699 | 1.25 $\pm$ 0.03 | 4.1 | 5.42 $\pm$ 0.38 | 34.5 | 0.08 | \(5\) |
| CH$_3$CN | 19$_{0}$–18$_{0}$ | 168 | 349.45370 | 1.23 $\pm$ 0.04 | 3.9 | 5.10 $\pm$ 0.38 | 34.2 | 0.08 | ... |
| $^{13}$CH$_3$CN | 19$_{0}$–18$_{0}$ | 163 | 339.36630 | $<$0.11 | ... | $<$0.45 | ... | 0.05 | ... |
| HC$_3$N | 27–26 | 165 | 245.60632 | 1.55 $\pm$ 0.03 | 4.2 | 7.02 $\pm$ 0.25 | 34.3 | 0.04 | ... |

: Line Parameters for N-bearing molecules

Table notes: (1) Blend of three hyperfine components. (2) Blend of three two components. (3) Blend with CH$_3$OH. (4) Blend with HCOOCH$_3$. (5) Blend of four hyperfine components.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | $E_{u}$ | Frequency | $T_{br}$ | $\Delta$$V$ | $\int T_{br} dV$ | $V_{LSR}$ | RMS | Note |
|  |  | \(K\) | (GHz) | \(K\) | (km/s) | (K km/s) | (km/s) | \(K\) |  |
| SiO | 6–5 | 44 | 260.51801 | 0.64 $\pm$ 0.02 | 2.7 | 1.86 $\pm$ 0.13 | 34.1 | 0.03 | ... |
| SO | $N_J$ = 6$_{6}$–5$_{5}$ | 56 | 258.25583 | 5.34 $\pm$ 0.02 | 3.6 | 20.20 $\pm$ 0.19 | 34.1 | 0.03 | ... |
| SO | $N_J$ = 3$_{3}$–2$_{3}$ | 26 | 339.34146 | 0.49 $\pm$ 0.04 | 3.4 | 1.76 $\pm$ 0.34 | 34.0 | 0.07 | ... |
| SO | $N_J$ = 8$_{7}$–7$_{6}$ | 81 | 340.71416 | 3.85 $\pm$ 0.04 | 3.9 | 15.81 $\pm$ 0.39 | 34.2 | 0.07 | ... |
| $^{34}$SO | $N_J$ = 3$_{3}$–2$_{3}$ | 25 | 337.89225 | $<$0.15 | ... | $<$0.6 | ... | 0.07 | ... |
| $^{34}$SO | $N_J$ = 8$_{9}$–7$_{8}$ | 77 | 339.85727 | 0.69 $\pm$ 0.04 | 4.4 | 3.26 $\pm$ 0.38 | 33.0 | 0.07 | ... |
| $^{33}$SO | $N_J$ = 6$_{7}$–5$_{6}$ | 47 | 259.28403 | 0.34 $\pm$ 0.07 | 6.8 | 0.81 $\pm$ 0.06 | 33.5 | 0.03 | \(1\) (2) |
| CS | 5–4 | 35 | 244.93556 | 14.57 $\pm$ 0.03 | 3.2 | 49.51 $\pm$ 0.20 | 33.9 | 0.04 | ... |
| C$^{33}$S | 5–4 | 35 | 242.91361 | 1.31 $\pm$ 0.02 | 3.7 | 5.18 $\pm$ 0.21 | 34.2 | 0.04 | ... |
| C$^{33}$S | 7–6 | 65 | 340.05257 | 1.05 $\pm$ 0.04 | 3.9 | 4.35 $\pm$ 0.34 | 34.3 | 0.07 | ... |
| C$^{34}$S | 7–6 | 65 | 337.39646 | 2.46 $\pm$ 0.04 | 3.3 | 8.65 $\pm$ 0.31 | 34.1 | 0.07 | ... |
| H$_2$CS | 7$_{1,6}$–6$_{1,5}$ | 60 | 244.04850 | 2.91 $\pm$ 0.03 | 3.0 | 9.37 $\pm$ 0.19 | 34.2 | 0.04 | ... |
| H$_2$CS | 10$_{1,10}$–9$_{1,9}$ | 102 | 338.08319 | 1.68 $\pm$ 0.04 | 3.9 | 7.04 $\pm$ 0.36 | 34.2 | 0.07 | ... |
| OCS | 20–19 | 123 | 243.21804 | 1.82 $\pm$ 0.03 | 4.2 | 8.17 $\pm$ 0.24 | 34.3 | 0.04 | ... |
| OCS | 28–27 | 237 | 340.44927 | 1.26 $\pm$ 0.04 | 4.0 | 5.40 $\pm$ 0.39 | 34.5 | 0.07 | ... |
| OCS | 29–28 | 254 | 352.59957 | 1.05 $\pm$ 0.04 | 4.5 | 5.01 $\pm$ 0.40 | 34.3 | 0.08 | ... |
| O$^{13}$CS | 20–19 | 122 | 242.43543 | 0.20 $\pm$ 0.02 | 4.8 | 1.00 $\pm$ 0.32 | 34.9 | 0.04 | ... |
| SO$_2$ | 5$_{2,4}$–4$_{1,3}$ | 24 | 241.61580 | 0.88 $\pm$ 0.02 | 5.1 | 4.79 $\pm$ 0.28 | 34.2 | 0.04 | \(3\) |
| SO$_2$ | 26$_{8,18}$–27$_{7,21}$ | 480 | 243.24543 | $<$0.10 | ... | $<$0.4 | ... | 0.04 | ... |
| SO$_2$ | 14$_{0,14}$–13$_{1,13}$ | 94 | 244.25422 | 1.15 $\pm$ 0.02 | 6.3 | 7.67 $\pm$ 0.33 | 34.2 | 0.04 | ... |
| SO$_2$ | 26$_{3,23}$–25$_{4,22}$ | 351 | 245.33923 | 0.41 $\pm$ 0.02 | 2.8 | 1.21 $\pm$ 0.15 | 34.5 | 0.04 | ... |
| SO$_2$ | 10$_{3,7}$–10$_{2,8}$ | 73 | 245.56342 | 1.04 $\pm$ 0.02 | 5.3 | 5.86 $\pm$ 0.27 | 34.3 | 0.04 | ... |
| SO$_2$ | 7$_{3,5}$–7$_{2,6}$ | 48 | 257.09997 | 0.96 $\pm$ 0.02 | 5.6 | 5.76 $\pm$ 0.24 | 34.2 | 0.03 | \(4\) |
| SO$_2$ | 32$_{4,28}$–32$_{3,29}$ | 531 | 258.38872 | 0.46 $\pm$ 0.02 | 4.1 | 2.01 $\pm$ 0.21 | 33.9 | 0.03 | ... |
| SO$_2$ | 20$_{7,13}$–21$_{6,16}$ | 313 | 258.66697 | 0.32 $\pm$ 0.07 | 3.4 | 0.76 $\pm$ 0.08 | 33.1 | 0.03 | \(2\) |
| SO$_2$ | 9$_{3,7}$–9$_{2,8}$ | 63 | 258.94220 | 0.91 $\pm$ 0.02 | 5.4 | 5.26 $\pm$ 0.23 | 34.4 | 0.03 | ... |
| SO$_2$ | 18$_{4,14}$–18$_{3,15}$ | 197 | 338.30599 | 0.65 $\pm$ 0.03 | 4.4 | 3.09 $\pm$ 0.37 | 34.0 | 0.07 | ... |
| SO$_2$ | 20$_{1,19}$–19$_{2,18}$ | 199 | 338.61181 | $<$0.90 | ... | $<$3.8 | ... | 0.07 | \(5\) |
| SO$_2$ | 28$_{2,26}$–28$_{1,27}$ | 392 | 340.31641 | 0.48 $\pm$ 0.03 | 6.0 | 3.02 $\pm$ 0.50 | 34.5 | 0.07 | ... |
| SO$_2$ | 5$_{3,3}$–4$_{2,2}$ | 36 | 351.25722 | 0.75 $\pm$ 0.04 | 5.9 | 4.73 $\pm$ 0.51 | 34.1 | 0.08 | ... |
| SO$_2$ | 14$_{4,10}$–14$_{3,11}$ | 136 | 351.87387 | 0.70 $\pm$ 0.03 | 4.4 | 3.32 $\pm$ 0.38 | 34.0 | 0.08 | ... |
| $^{34}$SO$_2$ | 14$_{0,14}$–13$_{1,13}$ | 94 | 244.48152 | 0.34 $\pm$ 0.02 | 1.5 | 0.54 $\pm$ 0.09 | 33.6 | 0.04 | ... |
| $^{13}$CH$_3$SH | 14$_{1,14}$–13$_{1,13}$ A | 131 | 350.00956 | $<$0.15 | ... | $<$0.7 | ... | 0.08 | ... |

: Line Parameters for Si- and S-bearing molecules

Table notes: (1) Blend of four hyperfine components. (2) The integrated intensity is calculated by directly integrating the spectrum. (3) Partial blend with HNCO. (4) Blend with HCOOCH$_3$. (5) Blend with CH$_3$OH.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | $E_{u}$ | Frequency | $T_{br}$ | $\Delta$$V$ | $\int T_{br} dV$ | $V_{LSR}$ | RMS | Note |
|  |  | \(K\) | (GHz) | \(K\) | (km/s) | (K km/s) | (km/s) | \(K\) |  |
| CH$_3$OH | 25$_{3}$ A$^-$–25$_{2}$ A$^+$ | 804 | 241.58876 | 0.72 $\pm$ 0.02 | 4.5 | 3.49 $\pm$ 0.25 | 34.5 | 0.04 | ... |
| CH$_3$OH | 5$_{0}$ E–4$_{0}$ E | 48 | 241.70016 | 2.45 $\pm$ 0.03 | 4.0 | 10.57 $\pm$ 0.24 | 34.2 | 0.04 | ... |
| CH$_3$OH | 5$_{-1}$ E–4$_{-1}$ E | 40 | 241.76723 | 3.70 $\pm$ 0.03 | 3.2 | 12.53 $\pm$ 0.20 | 34.2 | 0.04 | ... |
| CH$_3$OH | 5$_{0}$ A$^+$–4$_{0}$ A$^+$ | 35 | 241.79135 | 4.15 $\pm$ 0.03 | 3.0 | 13.29 $\pm$ 0.19 | 34.1 | 0.04 | ... |
| CH$_3$OH | 5$_{4}$ A$^-$–4$_{4}$ A$^-$ | 115 | 241.80652 | 1.46 $\pm$ 0.02 | 4.3 | 6.65 $\pm$ 0.23 | 34.7 | 0.04 | \(1\) |
| CH$_3$OH | 5$_{-4}$ E–4$_{-4}$ E | 123 | 241.81325 | 1.33 $\pm$ 0.02 | 4.3 | 6.13 $\pm$ 0.23 | 34.7 | 0.04 | ... |
| CH$_3$OH | 5$_{3}$ A$^+$–4$_{3}$ A$^+$ | 85 | 241.83272 | 2.08 $\pm$ 0.02 | 4.2 | 9.35 $\pm$ 0.25 | 34.3 | 0.04 | \(2\) |
| CH$_3$OH | 5$_{2}$ A$^-$–4$_{2}$ A$^-$ | 73 | 241.84228 | 2.13 $\pm$ 0.02 | 5.0 | 11.37 $\pm$ 0.26 | 33.7 | 0.04 | \(1\) |
| CH$_3$OH | 5$_{-3}$ E–4$_{-3}$ E | 98 | 241.85230 | 1.54 $\pm$ 0.02 | 4.4 | 7.13 $\pm$ 0.23 | 34.6 | 0.04 | ... |
| CH$_3$OH | 5$_{1}$ E–4$_{1}$ E | 56 | 241.87903 | 2.26 $\pm$ 0.03 | 3.9 | 9.26 $\pm$ 0.23 | 34.4 | 0.04 | ... |
| CH$_3$OH | 5$_{2}$ A$^+$–4$_{2}$ A$^+$ | 73 | 241.88767 | 1.82 $\pm$ 0.03 | 3.9 | 7.63 $\pm$ 0.23 | 34.5 | 0.04 | ... |
| CH$_3$OH | 5$_{-2}$ E–4$_{-2}$ E | 61 | 241.90415 | 2.94 $\pm$ 0.03 | 3.8 | 11.83 $\pm$ 0.21 | 34.0 | 0.04 | \(1\) |
| CH$_3$OH | 14$_{-1}$ E–13$_{-2}$ E | 249 | 242.44608 | 1.28 $\pm$ 0.02 | 4.8 | 6.55 $\pm$ 0.25 | 34.6 | 0.04 | \(3\) |
| CH$_3$OH | 24$_{3}$ A$^-$–24$_{2}$ A$^+$ | 746 | 242.49024 | 0.88 $\pm$ 0.02 | 4.6 | 4.30 $\pm$ 0.25 | 34.4 | 0.04 | ... |
| CH$_3$OH | 5$_{1}$ A$^-$–4$_{1}$ A$^-$ | 50 | 243.91579 | 2.75 $\pm$ 0.02 | 3.6 | 10.69 $\pm$ 0.21 | 34.3 | 0.04 | ... |
| CH$_3$OH | 22$_{3}$ A$^-$–22$_{2}$ A$^+$ | 637 | 244.33037 | 1.06 $\pm$ 0.02 | 4.9 | 5.54 $\pm$ 0.27 | 34.6 | 0.04 | ... |
| CH$_3$OH | 9$_{1}$ E–8$_{0}$ E , $\nu_t$ = 1 | 396 | 244.33798 | 1.08 $\pm$ 0.02 | 4.7 | 5.38 $\pm$ 0.25 | 34.6 | 0.04 | ... |
| CH$_3$OH | 18$_{-6}$ E–17$_{-7}$ E , $\nu_t$ = 1 | 889 | 245.09450 | 0.31 $\pm$ 0.02 | 4.1 | 1.35 $\pm$ 0.26 | 34.3 | 0.04 | ... |
| CH$_3$OH | 21$_{3}$ A$^-$–21$_{2}$ A$^+$ | 586 | 245.22302 | 1.22 $\pm$ 0.03 | 4.2 | 5.50 $\pm$ 0.24 | 34.4 | 0.04 | ... |
| CH$_3$OH | 18$_{3}$ A$^+$–18$_{2}$ A$^-$ | 447 | 257.40209 | 1.50 $\pm$ 0.02 | 6.0 | 9.52 $\pm$ 0.25 | 34.0 | 0.03 | \(4\) |
| CH$_3$OH | 19$_{3}$ A$^+$–19$_{2}$ A$^-$ | 491 | 258.78025 | 1.22 $\pm$ 0.02 | 5.4 | 7.05 $\pm$ 0.23 | 34.1 | 0.03 | ... |
| CH$_3$OH | 17$_{2}$ A$^-$–16$_{1}$ A$^-$ , $\nu_t$ = 1 | 653 | 259.27369 | 0.79 $\pm$ 0.02 | 4.2 | 3.54 $\pm$ 0.19 | 34.6 | 0.03 | ... |
| CH$_3$OH | 24$_{1}$ E–24$_{0}$ E | 717 | 259.58140 | 0.62 $\pm$ 0.02 | 4.4 | 2.89 $\pm$ 0.18 | 34.7 | 0.03 | ... |
| CH$_3$OH | 20$_{-8}$ E–21$_{-7}$ E | 808 | 260.06432 | 0.43 $\pm$ 0.02 | 3.8 | 1.75 $\pm$ 0.17 | 34.8 | 0.03 | ... |
| CH$_3$OH | 20$_{3}$ A$^+$–20$_{2}$ A$^-$ | 537 | 260.38146 | 1.22 $\pm$ 0.01 | 4.7 | 6.02 $\pm$ 0.25 | 34.3 | 0.03 | ... |
| CH$_3$OH | 7$_{4}$ A$^+$–6$_{4}$ A$^+$ , $\nu_t$ = 2 | 679 | 337.27356 | 0.59 $\pm$ 0.04 | 4.3 | 2.68 $\pm$ 0.49 | 34.5 | 0.07 | \(1\) |
| CH$_3$OH | 7$_{-2}$ E–6$_{-2}$ E , $\nu_t$ = 2 | 710 | 337.27918 | 0.54 $\pm$ 0.03 | 2.7 | 1.54 $\pm$ 0.48 | 34.8 | 0.07 | ... |
| CH$_3$OH | 7$_{0}$ A$^+$–6$_{0}$ A$^+$ , $\nu_t$ = 2 | 573 | 337.28432 | 0.78 $\pm$ 0.03 | 5.3 | 4.36 $\pm$ 0.45 | 34.7 | 0.07 | ... |
| CH$_3$OH | 7$_{1}$ A$^+$–6$_{1}$ A$^+$ , $\nu_t$ = 1 | 390 | 337.29748 | 0.97 $\pm$ 0.03 | 4.1 | 4.25 $\pm$ 0.39 | 35.3 | 0.07 | \(1\) |
| CH$_3$OH | 7$_{2}$ E–6$_{2}$ E , $\nu_t$ = 2 | 651 | 337.30264 | 0.65 $\pm$ 0.03 | 4.2 | 2.94 $\pm$ 0.39 | 34.5 | 0.07 | ... |
| CH$_3$OH | 7$_{-1}$ E–6$_{-1}$ E , $\nu_t$ = 2 | 597 | 337.31236 | 0.57 $\pm$ 0.04 | 4.7 | 2.87 $\pm$ 0.41 | 34.3 | 0.07 | ... |
| CH$_3$OH | 7$_{6}$ A$^+$–6$_{6}$ A$^+$ , $\nu_t$ = 1 | 533 | 337.46370 | 0.62 $\pm$ 0.04 | 5.5 | 3.62 $\pm$ 0.47 | 34.6 | 0.07 | \(1\) |
| CH$_3$OH | 10$_{0}$ E–9$_{-9}$ E , $\nu_t$ = 1 | 916 | 337.47259 | 0.40 $\pm$ 0.04 | 5.6 | 2.38 $\pm$ 0.47 | 33.8 | 0.07 | ... |
| CH$_3$OH | 7$_{-6}$ E–6$_{-6}$ E , $\nu_t$ = 1 | 558 | 337.49056 | 0.71 $\pm$ 0.04 | 4.3 | 3.23 $\pm$ 0.36 | 34.8 | 0.07 | \(5\) |
| CH$_3$OH | 7$_{3}$ E–6$_{3}$ E , $\nu_t$ = 1 | 482 | 337.51914 | 0.80 $\pm$ 0.04 | 4.3 | 3.68 $\pm$ 0.38 | 34.9 | 0.07 | ... |
| CH$_3$OH | 7$_{5}$ A$^+$–6$_{5}$ A$^+$ , $\nu_t$ = 1 | 485 | 337.54612 | 0.84 $\pm$ 0.04 | 4.7 | 4.19 $\pm$ 0.39 | 34.7 | 0.07 | \(1\) |
| CH$_3$OH | 7$_{4}$ E–6$_{4}$ E , $\nu_t$ = 1 | 428 | 337.58168 | $<$1.00 | ... | $<$4.3 | ... | 0.07 | \(6\) |
| CH$_3$OH | 7$_{-2}$ E–6$_{-2}$ E , $\nu_t$ = 1 | 429 | 337.60529 | 0.87 $\pm$ 0.03 | 3.8 | 3.51 $\pm$ 0.53 | 35.0 | 0.07 | ... |
| CH$_3$OH | 7$_{-3}$ E–6$_{-3}$ E , $\nu_t$ = 1 | 387 | 337.61066 | 1.01 $\pm$ 0.03 | 3.7 | 4.03 $\pm$ 0.32 | 34.6 | 0.07 | \(1\) |
| CH$_3$OH | 7$_{2}$ A$^+$–6$_{2}$ A$^+$ , $\nu_t$ = 1 | 363 | 337.62575 | 1.03 $\pm$ 0.04 | 3.4 | 3.71 $\pm$ 0.30 | 34.7 | 0.07 | ... |
| CH$_3$OH | 7$_{2}$ A$^-$–6$_{2}$ A$^-$ , $\nu_t$ = 1 | 364 | 337.63575 | 1.00 $\pm$ 0.03 | 4.1 | 4.34 $\pm$ 0.39 | 34.6 | 0.07 | ... |
| CH$_3$OH | 7$_{0}$ E–6$_{0}$ E , $\nu_t$ = 1 | 365 | 337.64391 | 1.26 $\pm$ 0.03 | 7.9 | 10.58 $\pm$ 0.70 | 34.3 | 0.07 | \(2\) |
| CH$_3$OH | 7$_{3}$ A$^+$–6$_{3}$ A$^+$ , $\nu_t$ = 1 | 461 | 337.65520 | 0.98 $\pm$ 0.03 | 3.2 | 3.34 $\pm$ 0.33 | 34.4 | 0.07 | \(1\) |
| CH$_3$OH | 7$_{4}$ A$^+$–6$_{4}$ A$^+$ , $\nu_t$ = 1 | 546 | 337.68561 | 0.92 $\pm$ 0.04 | 4.0 | 3.89 $\pm$ 0.37 | 34.9 | 0.07 | \(2\) |
| CH$_3$OH | 7$_{-1}$ E–6$_{-1}$ E , $\nu_t$ = 1 | 478 | 337.70757 | 0.83 $\pm$ 0.04 | 4.9 | 4.39 $\pm$ 0.44 | 34.5 | 0.07 | ... |
| CH$_3$OH | 7$_{0}$ A$^+$–6$_{0}$ A$^+$ , $\nu_t$ = 1 | 488 | 337.74883 | 0.88 $\pm$ 0.04 | 4.2 | 3.96 $\pm$ 0.36 | 34.9 | 0.07 | ... |
| CH$_3$OH | 20$_{-6}$ E–21$_{-5}$ E | 676 | 337.83780 | 0.45 $\pm$ 0.04 | 3.5 | 1.69 $\pm$ 0.30 | 34.6 | 0.07 | ... |
| CH$_3$OH | 7$_{1}$ A$^-$–6$_{1}$ A$^-$ , $\nu_t$ = 2 | 748 | 337.87755 | 0.51 $\pm$ 0.04 | 3.2 | 1.75 $\pm$ 0.28 | 34.6 | 0.07 | ... |
| CH$_3$OH | 7$_{1}$ A$^-$–6$_{1}$ A$^-$ , $\nu_t$ = 1 | 390 | 337.96944 | 0.89 $\pm$ 0.04 | 4.4 | 4.13 $\pm$ 0.38 | 34.5 | 0.07 | ... |
| CH$_3$OH | 7$_{0}$ E–6$_{0}$ E | 78 | 338.12449 | 2.19 $\pm$ 0.04 | 3.4 | 7.84 $\pm$ 0.30 | 34.4 | 0.07 | ... |
| CH$_3$OH | 7$_{-1}$ E–6$_{-1}$ E | 71 | 338.34459 | 2.91 $\pm$ 0.04 | 3.5 | 10.81 $\pm$ 0.32 | 34.2 | 0.07 | ... |
| CH$_3$OH | 7$_{6}$ E–6$_{6}$ E | 244 | 338.40461 | 0.98 $\pm$ 0.04 | 3.8 | 4.00 $\pm$ 0.33 | 34.7 | 0.07 | ... |
| CH$_3$OH | 7$_{0}$ A$^+$–6$_{0}$ A$^+$ | 65 | 338.40870 | 3.41 $\pm$ 0.03 | 2.9 | 10.59 $\pm$ 0.28 | 34.1 | 0.07 | ... |
| CH$_3$OH | 7$_{-6}$ E–6$_{-6}$ E | 254 | 338.43097 | 0.88 $\pm$ 0.03 | 4.6 | 4.25 $\pm$ 0.38 | 34.6 | 0.07 | ... |
| CH$_3$OH | 7$_{6}$ A$^+$–6$_{6}$ A$^+$ | 259 | 338.44237 | 1.04 $\pm$ 0.04 | 4.3 | 4.79 $\pm$ 0.36 | 34.7 | 0.07 | \(1\) |
| CH$_3$OH | 7$_{-5}$ E–6$_{-5}$ E | 189 | 338.45654 | 1.12 $\pm$ 0.03 | 4.7 | 5.62 $\pm$ 0.39 | 34.5 | 0.07 | ... |
| CH$_3$OH | 7$_{5}$ E–6$_{5}$ E | 201 | 338.47523 | 1.15 $\pm$ 0.03 | 4.1 | 5.02 $\pm$ 0.34 | 34.6 | 0.07 | ... |
| CH$_3$OH | 7$_{5}$ A$^+$–6$_{5}$ A$^+$ | 203 | 338.48632 | 1.22 $\pm$ 0.03 | 4.9 | 6.42 $\pm$ 0.42 | 34.5 | 0.07 | \(1\) |
| CH$_3$OH | 7$_{-4}$ E–6$_{-4}$ E | 153 | 338.50407 | 1.31 $\pm$ 0.03 | 4.7 | 6.52 $\pm$ 0.41 | 34.8 | 0.07 | ... |
| CH$_3$OH | 7$_{4}$ E–6$_{4}$ E | 161 | 338.53026 | 1.30 $\pm$ 0.04 | 4.2 | 5.87 $\pm$ 0.35 | 34.4 | 0.07 | ... |
| CH$_3$OH | 7$_{3}$ A$^+$–6$_{3}$ A$^+$ | 115 | 338.54083 | 1.95 $\pm$ 0.04 | 5.5 | 11.45 $\pm$ 0.47 | 33.3 | 0.07 | \(1\) |
| CH$_3$OH | 7$_{-3}$ E–6$_{-3}$ E | 128 | 338.55996 | 1.40 $\pm$ 0.04 | 4.5 | 6.74 $\pm$ 0.38 | 34.4 | 0.07 | ... |
| CH$_3$OH | 7$_{3}$ E–6$_{3}$ E | 113 | 338.58322 | 1.46 $\pm$ 0.04 | 4.3 | 6.70 $\pm$ 0.37 | 34.6 | 0.07 | ... |
| CH$_3$OH | 7$_{1}$ E–6$_{1}$ E | 86 | 338.61494 | 1.95 $\pm$ 0.04 | 4.4 | 9.18 $\pm$ 0.38 | 34.4 | 0.07 | ... |
| CH$_3$OH | 7$_{2}$ A$^+$–6$_{2}$ A$^+$ | 103 | 338.63980 | 1.60 $\pm$ 0.04 | 4.1 | 6.97 $\pm$ 0.34 | 34.5 | 0.07 | ... |
| CH$_3$OH | 7$_{-2}$ E–6$_{-2}$ E | 91 | 338.72290 | 2.52 $\pm$ 0.04 | 4.1 | 10.98 $\pm$ 0.35 | 34.9 | 0.07 | \(1\) |
| CH$_3$OH | 21$_{3}$ E–21$_{2}$ E , $\nu_t$ = 1 | 951 | 339.42217 | $<$0.18 | ... | $<$0.8 | ... | 0.07 | ... |
| CH$_3$OH | 2$_{2}$ A$^+$–3$_{1}$ A$^+$ | 45 | 340.14114 | 1.08 $\pm$ 0.03 | 4.4 | 5.05 $\pm$ 0.38 | 35.2 | 0.07 | ... |
| CH$_3$OH | 16$_{6}$ A$^-$–17$_{5}$ A$^-$ | 509 | 340.39366 | 0.90 $\pm$ 0.04 | 4.0 | 3.87 $\pm$ 0.34 | 34.7 | 0.07 | ... |
| CH$_3$OH | 11$_{1}$ E–10$_{0}$ E , $\nu_t$ = 1 | 444 | 340.68397 | 0.98 $\pm$ 0.03 | 5.1 | 5.29 $\pm$ 0.46 | 34.8 | 0.07 | ... |
| CH$_3$OH | 15$_{3}$ E–16$_{4}$ E , $\nu_t$ = 1 | 695 | 350.28649 | 0.70 $\pm$ 0.03 | 4.9 | 3.65 $\pm$ 0.42 | 34.6 | 0.08 | ... |
| CH$_3$OH | 4$_{0}$ E–3$_{-1}$ E | 36 | 350.68766 | 1.87 $\pm$ 0.04 | 4.6 | 9.18 $\pm$ 0.40 | 34.1 | 0.08 | ... |
| CH$_3$OH | 18$_{3}$ E–18$_{2}$ E , $\nu_t$ = 1 | 812 | 350.72388 | $<$0.25 | ... | $<$1.1 | ... | 0.08 | ... |
| CH$_3$OH | 1$_{1}$ A$^+$–0$_{0}$ A$^+$ | 17 | 350.90510 | 2.38 $\pm$ 0.04 | 3.7 | 9.29 $\pm$ 0.33 | 34.4 | 0.08 | ... |
| CH$_3$OH | 9$_{5}$ E–10$_{4}$ E | 241 | 351.23648 | 0.97 $\pm$ 0.04 | 4.7 | 4.82 $\pm$ 0.40 | 34.5 | 0.08 | ... |
| $^{13}$CH$_3$OH | 4$_{2}$ A$^-$–5$_{1}$ A$^-$ | 60 | 242.37315 | 0.17 $\pm$ 0.02 | 5.1 | 0.93 $\pm$ 0.27 | 36.3 | 0.04 | ... |
| $^{13}$CH$_3$OH | 15$_{3}$ A$^+$–15$_{2}$ A$^-$ | 322 | 257.42179 | 0.48 $\pm$ 0.02 | 3.9 | 2.02 $\pm$ 0.18 | 34.5 | 0.03 | ... |
| $^{13}$CH$_3$OH | 16$_{3}$ A$^+$–16$_{2}$ A$^-$ | 358 | 258.15300 | 0.59 $\pm$ 0.02 | 4.6 | 2.90 $\pm$ 0.19 | 34.8 | 0.03 | \(7\) |
| $^{13}$CH$_3$OH | 17$_{3}$ A$^+$–17$_{2}$ A$^-$ | 396 | 259.03649 | $<$0.20 | ... | $<$0.9 | ... | 0.03 | \(8\) |
| $^{13}$CH$_3$OH | 2$_{1}$ E–1$_{0}$ E | 28 | 259.98653 | 0.54 $\pm$ 0.02 | 2.9 | 1.68 $\pm$ 0.16 | 34.5 | 0.03 | \(9\) |
| $^{13}$CH$_3$OH | 13$_{0}$ A$^+$–12$_{1}$ A$^+$ | 206 | 338.75995 | 0.60 $\pm$ 0.04 | 3.7 | 2.33 $\pm$ 0.32 | 34.4 | 0.07 | ... |
| $^{13}$CH$_3$OH | 1$_{1}$ A$^+$–0$_{0}$ A$^+$ | 17 | 350.10312 | 0.58 $\pm$ 0.04 | 3.1 | 1.87 $\pm$ 0.28 | 34.7 | 0.08 | ... |
| $^{13}$CH$_3$OH | 8$_{1}$ E–7$_{2}$ E | 103 | 350.42158 | 0.49 $\pm$ 0.04 | 4.6 | 2.38 $\pm$ 0.41 | 34.0 | 0.08 | ... |
| CH$_2$DOH | 11$_{2,9}$$o_1$–11$_{1,10}$$o_1$ | 177 | 242.03360 | 0.32 $\pm$ 0.03 | 1.8 | 0.60 $\pm$ 0.14 | 33.2 | 0.04 | ... |
| CH$_2$DOH | 5$_{2,3}$$e_0$–5$_{1,4}$$e_0$ | 48 | 243.22599 | 0.56 $\pm$ 0.02 | 2.9 | 1.74 $\pm$ 0.17 | 35.5 | 0.04 | ... |
| CH$_2$DOH | 4$_{2,2}$$e_0$–4$_{1,3}$$e_0$ | 38 | 244.84113 | 0.35 $\pm$ 0.02 | 4.2 | 1.55 $\pm$ 0.25 | 34.4 | 0.04 | ... |
| CH$_2$DOH | 10$_{2,8}$$o_1$–10$_{1,9}$$o_1$ | 153 | 244.98885 | 0.13 $\pm$ 0.02 | 3.9 | 0.54 $\pm$ 0.22 | 34.7 | 0.04 | ... |
| CH$_2$DOH | 5$_{2,3}$$o_1$–5$_{1,4}$$o_1$ | 68 | 257.39451 | 0.26 $\pm$ 0.02 | 2.2 | 0.61 $\pm$ 0.10 | 34.4 | 0.03 | ... |
| CH$_2$DOH | 4$_{2,3}$$e_1$–3$_{1,3}$$o_1$ | 48 | 257.89567 | 0.30 $\pm$ 0.02 | 2.3 | 0.72 $\pm$ 0.09 | 34.6 | 0.03 | ... |
| CH$_2$DOH | 4$_{2,3}$$e_0$–4$_{1,4}$$e_0$ | 38 | 258.33711 | 0.42 $\pm$ 0.02 | 2.8 | 1.25 $\pm$ 0.12 | 34.3 | 0.03 | ... |
| CH$_2$DOH | 9$_{0,9}$$e_0$–8$_{1,8}$$e_0$ | 96 | 337.34866 | 0.63 $\pm$ 0.04 | 2.8 | 1.84 $\pm$ 0.25 | 35.1 | 0.07 | ... |
| CH$_2$DOH | 6$_{1,6}$$e_0$–5$_{0,5}$$e_0$ | 48 | 338.95711 | 0.39 $\pm$ 0.04 | 3.5 | 1.46 $\pm$ 0.32 | 35.1 | 0.07 | ... |
| CH$_2$DOH | 15$_{2,14}$$o_1$–15$_{1,14}$$e_1$ | 292 | 339.48572 | 0.24 $\pm$ 0.03 | 2.2 | 0.56 $\pm$ 0.20 | 34.9 | 0.07 | ... |
| CH$_2$DOH | 6$_{2,4}$$e_1$–5$_{1,4}$$o_1$ | 72 | 340.12709 | 0.42 $\pm$ 0.03 | 3.5 | 1.55 $\pm$ 0.43 | 34.8 | 0.07 | ... |
| CH$_2$DOH | 13$_{1,13}$$e_0$–12$_{0,12}$$e_1$ | 196 | 340.24344 | 0.57 $\pm$ 0.03 | 2.9 | 1.76 $\pm$ 0.33 | 34.2 | 0.07 | \(10\) |
| CH$_2$DOH | 2$_{2,1}$$e_0$–1$_{1,0}$$e_0$ | 23 | 340.34829 | 0.29 $\pm$ 0.04 | 3.7 | 1.15 $\pm$ 0.32 | 34.1 | 0.07 | ... |
| CH$_2$DOH | 13$_{4,9}$$e_1$–13$_{3,11}$$o_1$ | 267 | 349.18383 | 0.24 $\pm$ 0.04 | 2.2 | 0.57 $\pm$ 0.22 | 34.3 | 0.08 | ... |
| CH$_2$DOH | 12$_{4,8}$$e_1$–12$_{3,10}$$o_1$ | 239 | 349.35613 | 0.22 $\pm$ 0.04 | 3.1 | 0.75 $\pm$ 0.30 | 35.3 | 0.08 | ... |
| CH$_2$DOH | 11$_{4,8}$$e_1$–11$_{3,8}$$o_1$ | 213 | 349.49521 | 0.22 $\pm$ 0.04 | 3.7 | 0.85 $\pm$ 0.32 | 34.3 | 0.08 | \(11\) |
| CH$_2$DOH | 11$_{4,7}$$e_1$–11$_{3,9}$$o_1$ | 213 | 349.50887 | 0.47 $\pm$ 0.04 | 1.6 | 0.80 $\pm$ 0.22 | 34.8 | 0.08 | ... |
| CH$_2$DOH | 10$_{4,6}$$e_1$–10$_{3,8}$$o_1$ | 190 | 349.64360 | 0.32 $\pm$ 0.04 | 2.8 | 0.97 $\pm$ 0.28 | 34.4 | 0.08 | ... |
| CH$_2$DOH | 9$_{4,5}$$e_1$–9$_{3,7}$$o_1$ | 168 | 349.76168 | 0.30 $\pm$ 0.04 | 7.2 | 2.31 $\pm$ 0.62 | 36.4 | 0.08 | \(12\) |
| CH$_2$DOH | 8$_{4,5}$$e_1$–8$_{3,5}$$o_1$ | 149 | 349.86211 | 0.34 $\pm$ 0.04 | 6.0 | 2.15 $\pm$ 0.55 | 33.4 | 0.08 | \(12\) |
| CH$_2$DOH | 7$_{4,4}$$e_1$–7$_{3,4}$$o_1$ | 132 | 349.95168 | 0.48 $\pm$ 0.03 | 3.4 | 1.73 $\pm$ 0.29 | 34.3 | 0.08 | \(12\) |
| CH$_2$DOH | 6$_{4,3}$$e_1$–6$_{3,3}$$o_1$ | 117 | 350.02735 | 0.64 $\pm$ 0.04 | 2.4 | 1.60 $\pm$ 0.26 | 34.2 | 0.08 | \(12\) |
| CH$_2$DOH | 5$_{4,2}$$e_1$–5$_{3,2}$$o_1$ | 104 | 350.09024 | 0.57 $\pm$ 0.04 | 2.0 | 1.21 $\pm$ 0.23 | 34.2 | 0.08 | \(12\) |
| CH$_2$DOH | 4$_{4,1}$$e_1$–4$_{3,1}$$o_1$ | 94 | 350.14130 | 0.33 $\pm$ 0.03 | 4.0 | 1.41 $\pm$ 0.37 | 33.8 | 0.08 | \(12\) |
| CH$_2$DOH | 6$_{2,5}$$e_1$–5$_{1,5}$$o_1$ | 72 | 350.45387 | 0.53 $\pm$ 0.03 | 2.6 | 1.46 $\pm$ 0.28 | 34.2 | 0.08 | ... |
| CH$_2$DOH | 5$_{1,4}$$e_1$–5$_{0,5}$$e_0$ | 49 | 350.63207 | 0.58 $\pm$ 0.04 | 3.2 | 1.98 $\pm$ 0.32 | 35.2 | 0.08 | ... |
| CH$_2$DOH | 2$_{2,1}$$o_1$–1$_{1,0}$$o_1$ | 42 | 351.60685 | $<$0.15 | ... | $<$0.7 | ... | 0.08 | ... |
| CH$_2$DOH | 8$_{1,8}$$e_0$–7$_{1,7}$$e_0$ | 80 | 351.79643 | 0.54 $\pm$ 0.04 | 2.5 | 1.44 $\pm$ 0.30 | 34.4 | 0.08 | ... |
| CH$_2$DOH | 2$_{2,0}$$o_1$–1$_{1,1}$$o_1$ | 42 | 352.34437 | $<$0.15 | ... | $<$0.7 | ... | 0.08 | ... |
| CH$_2$DOH | 8$_{1,8}$$e_1$–7$_{1,7}$$e_1$ | 93 | 352.80196 | 0.40 $\pm$ 0.04 | 2.6 | 1.10 $\pm$ 0.23 | 34.4 | 0.08 | ... |

: Line Parameters for CH$_3$OH, $^{13}$CH$_3$OH, and CH$_2$DOH

Table notes: (1) Blend of two CH$_3$OH lines with similar spectroscopic constants. (2) Blend of three CH$_3$OH lines with similar spectroscopic constants. (3) Possible blend with C$_2$H$_5$OH. (4) Blend with CH$_3$CN. (5) Blend with HCOOCH$_3$. (6) Blend with $^{34}$SO. (7) Partial blend with HC$^{15}$N. (8) Possible blend with HDCO. (9) Blend with CH$_3$OCH$_3$. (10) Partial blend with CN. (12) Blend of two CH$_2$DOH lines with similar spectroscopic constants.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | $E_{u}$ | Frequency | $T_{br}$ | $\Delta$$V$ | $\int T_{br} dV$ | $V_{LSR}$ | RMS | Note |
|  |  | \(K\) | (GHz) | \(K\) | (km/s) | (K km/s) | (km/s) | \(K\) |  |
| C$_2$H$_5$OH | 14$_{11,3}$–13$_{11,2}$ | 297 | 242.17548 | 0.15 $\pm$ 0.02 | 5.4 | 0.87 $\pm$ 0.40 | 34.7 | 0.04 | \(1\) |
| C$_2$H$_5$OH | 14$_{9,5}$–13$_{9,4}$ | 248 | 242.22129 | 0.16 $\pm$ 0.02 | 5.5 | 0.93 $\pm$ 0.29 | 33.7 | 0.04 | \(1\) |
| C$_2$H$_5$OH | 14$_{8,6}$–13$_{8,5}$ | 228 | 242.27115 | 0.13 $\pm$ 0.02 | 4.1 | 0.57 $\pm$ 0.23 | 34.6 | 0.04 | \(1\) |
| C$_2$H$_5$OH | 14$_{7,8}$–13$_{7,7}$ | 209 | 242.34984 | 0.30 $\pm$ 0.02 | 4.1 | 1.30 $\pm$ 0.23 | 35.7 | 0.04 | \(1\) |
| C$_2$H$_5$OH | 14$_{10,4}$–13$_{10,3}$ | 266 | 242.42987 | 0.36 $\pm$ 0.02 | 1.6 | 0.62 $\pm$ 0.08 | 35.3 | 0.04 | \(2\) |
| C$_2$H$_5$OH | 14$_{6,9}$–13$_{6,8}$ | 193 | 242.47550 | 0.35 $\pm$ 0.02 | 4.3 | 1.60 $\pm$ 0.23 | 34.6 | 0.04 | \(1\) |
| C$_2$H$_5$OH | 14$_{7,8}$–13$_{7,7}$ | 204 | 242.52422 | 0.37 $\pm$ 0.02 | 1.5 | 0.57 $\pm$ 0.08 | 34.9 | 0.04 | \(1\) |
| C$_2$H$_5$OH | 14$_{6,9}$–13$_{6,8}$ | 188 | 242.62561 | 0.42 $\pm$ 0.02 | 1.5 | 0.67 $\pm$ 0.08 | 34.6 | 0.04 | \(1\) |
| C$_2$H$_5$OH | 14$_{5,10}$–13$_{5,9}$ | 180 | 242.68502 | 0.13 $\pm$ 0.02 | 3.6 | 0.51 $\pm$ 0.19 | 34.6 | 0.04 | \(1\) |
| C$_2$H$_5$OH | 14$_{5,9}$–13$_{5,8}$ | 180 | 242.69305 | 0.35 $\pm$ 0.02 | 1.5 | 0.56 $\pm$ 0.08 | 34.7 | 0.04 | ... |
| C$_2$H$_5$OH | 14$_{3,12}$–13$_{3,11}$ | 160 | 242.77011 | 0.15 $\pm$ 0.02 | 3.4 | 0.55 $\pm$ 0.17 | 35.2 | 0.04 | ... |
| C$_2$H$_5$OH | 14$_{5,10}$–13$_{5,9}$ | 175 | 242.81644 | 0.09 $\pm$ 0.02 | 3.3 | 0.33 $\pm$ 0.18 | 33.8 | 0.04 | \(3\) |
| C$_2$H$_5$OH | 14$_{5,9}$–13$_{5,8}$ | 175 | 242.82512 | 0.10 $\pm$ 0.02 | 3.9 | 0.42 $\pm$ 0.21 | 35.6 | 0.04 | ... |
| C$_2$H$_5$OH | 14$_{4,11}$–13$_{4,10}$ | 169 | 242.99597 | 0.28 $\pm$ 0.03 | 3.1 | 0.91 $\pm$ 0.19 | 34.2 | 0.04 | ... |
| C$_2$H$_5$OH | 14$_{4,11}$–13$_{4,10}$ | 164 | 243.12034 | 0.38 $\pm$ 0.02 | 1.5 | 0.58 $\pm$ 0.08 | 35.2 | 0.04 | ... |
| C$_2$H$_5$OH | 14$_{4,10}$–13$_{4,9}$ | 169 | 243.20653 | 0.36 $\pm$ 0.02 | 1.7 | 0.64 $\pm$ 0.09 | 34.3 | 0.04 | ... |
| C$_2$H$_5$OH | 14$_{1,13}$–13$_{1,12}$ | 152 | 244.63396 | 0.24 $\pm$ 0.02 | 3.8 | 0.99 $\pm$ 0.21 | 34.5 | 0.04 | ... |
| C$_2$H$_5$OH | 14$_{3,11}$–13$_{3,10}$ | 160 | 245.32715 | 0.39 $\pm$ 0.02 | 1.4 | 0.60 $\pm$ 0.08 | 34.6 | 0.04 | ... |
| C$_2$H$_5$OH | 16$_{1,15}$–15$_{2,14}$ | 117 | 257.06090 | 0.26 $\pm$ 0.02 | 5.3 | 1.49 $\pm$ 0.23 | 34.1 | 0.03 | ... |
| C$_2$H$_5$OH | 14$_{3,11}$–13$_{2,11}$ | 156 | 259.32264 | 0.09 $\pm$ 0.02 | 4.3 | 0.40 $\pm$ 0.19 | 34.2 | 0.03 | \(3\) |
| C$_2$H$_5$OH | 15$_{9,6}$–14$_{9,5}$ | 261 | 259.53913 | 0.28 $\pm$ 0.02 | 2.4 | 0.71 $\pm$ 0.10 | 34.4 | 0.03 | \(1\) |
| C$_2$H$_5$OH | 15$_{7,9}$–14$_{7,8}$ | 222 | 259.69790 | 0.11 $\pm$ 0.02 | 4.7 | 0.57 $\pm$ 0.21 | 34.4 | 0.03 | \(1\) |
| C$_2$H$_5$OH | 15$_{10,5}$–14$_{10,4}$ | 279 | 259.75653 | 0.27 $\pm$ 0.02 | 2.4 | 0.69 $\pm$ 0.14 | 34.9 | 0.03 | \(1\) |
| C$_2$H$_5$OH | 15$_{9,6}$–14$_{9,5}$ | 255 | 259.77714 | 0.28 $\pm$ 0.02 | 1.5 | 0.43 $\pm$ 0.07 | 34.5 | 0.03 | \(1\) |
| C$_2$H$_5$OH | 15$_{8,8}$–14$_{8,7}$ | 235 | 259.81444 | 0.29 $\pm$ 0.02 | 2.3 | 0.72 $\pm$ 0.10 | 34.0 | 0.03 | \(1\) |
| C$_2$H$_5$OH | 15$_{6,10}$–14$_{6,9}$ | 206 | 259.85218 | 0.30 $\pm$ 0.02 | 2.3 | 0.74 $\pm$ 0.10 | 34.7 | 0.03 | \(1\) |
| C$_2$H$_5$OH | 15$_{7,9}$–14$_{7,8}$ | 216 | 259.88507 | 0.28 $\pm$ 0.02 | 3.1 | 0.93 $\pm$ 0.13 | 34.7 | 0.03 | \(1\) |
| C$_2$H$_5$OH | 15$_{3,13}$–14$_{3,12}$ | 172 | 260.04664 | 0.28 $\pm$ 0.02 | 2.2 | 0.64 $\pm$ 0.10 | 35.2 | 0.03 | ... |
| C$_2$H$_5$OH | 15$_{5,11}$–14$_{5,10}$ | 192 | 260.10761 | 0.09 $\pm$ 0.01 | 4.7 | 0.43 $\pm$ 0.24 | 34.5 | 0.03 | \(3\) |
| C$_2$H$_5$OH | 15$_{5,10}$–14$_{5,9}$ | 192 | 260.12276 | 0.11 $\pm$ 0.02 | 4.6 | 0.52 $\pm$ 0.20 | 34.5 | 0.03 | ... |
| C$_2$H$_5$OH | 15$_{3,13}$–14$_{3,12}$ | 168 | 260.14168 | 0.29 $\pm$ 0.02 | 3.5 | 1.06 $\pm$ 0.15 | 34.9 | 0.03 | ... |
| C$_2$H$_5$OH | 15$_{5,10}$–14$_{5,9}$ | 187 | 260.26613 | 0.27 $\pm$ 0.02 | 2.5 | 0.71 $\pm$ 0.11 | 33.9 | 0.03 | ... |
| C$_2$H$_5$OH | 15$_{4,12}$–14$_{4,11}$ | 181 | 260.45773 | 0.12 $\pm$ 0.02 | 4.4 | 0.57 $\pm$ 0.19 | 35.1 | 0.03 | ... |
| C$_2$H$_5$OH | 15$_{4,12}$–14$_{4,11}$ | 176 | 260.59133 | 0.28 $\pm$ 0.02 | 2.4 | 0.74 $\pm$ 0.10 | 34.5 | 0.03 | ... |
| C$_2$H$_5$OH | 20$_{2,19}$–19$_{2,18}$ | 234 | 338.88792 | 0.39 $\pm$ 0.04 | 5.0 | 2.07 $\pm$ 0.43 | 35.5 | 0.07 | \(4\) |
| C$_2$H$_5$OH | 16$_{7,9}$–16$_{6,10}$ | 176 | 338.67173 | 0.35 $\pm$ 0.04 | 4.7 | 1.76 $\pm$ 0.40 | 33.4 | 0.07 | \(1\) |
| C$_2$H$_5$OH | 14$_{7,7}$–14$_{6,8}$ | 150 | 339.06106 | 0.28 $\pm$ 0.03 | 4.0 | 1.21 $\pm$ 0.34 | 34.5 | 0.07 | \(1\) |
| C$_2$H$_5$OH | 13$_{7,6}$–13$_{6,7}$ | 138 | 339.20154 | 0.38 $\pm$ 0.03 | 1.9 | 0.79 $\pm$ 0.25 | 33.9 | 0.07 | \(1\) |
| C$_2$H$_5$OH | 12$_{7,5}$–12$_{6,6}$ | 127 | 339.31253 | 0.24 $\pm$ 0.03 | 4.9 | 1.24 $\pm$ 0.40 | 35.9 | 0.07 | ... |
| C$_2$H$_5$OH | 11$_{7,4}$–11$_{6,5}$ | 117 | 339.39844 | 0.25 $\pm$ 0.03 | 4.0 | 1.07 $\pm$ 0.33 | 34.6 | 0.07 | \(1\) |
| C$_2$H$_5$OH | 8$_{7,1}$–8$_{6,2}$ | 92 | 339.54409 | 0.30 $\pm$ 0.04 | 2.1 | 0.67 $\pm$ 0.20 | 34.4 | 0.07 | \(1\) |
| C$_2$H$_5$OH | 9$_{4,6}$–8$_{3,5}$ | 58 | 339.97892 | 0.24 $\pm$ 0.04 | 3.8 | 0.97 $\pm$ 0.32 | 35.0 | 0.07 | ... |
| C$_2$H$_5$OH | 20$_{4,16}$–19$_{4,15}$ | 252 | 350.36506 | 0.40 $\pm$ 0.04 | 3.9 | 1.65 $\pm$ 0.33 | 35.7 | 0.08 | \(5\) |
| C$_2$H$_5$OH | 20$_{2,19}$–19$_{1,18}$ | 179 | 350.53435 | 0.30 $\pm$ 0.04 | 3.3 | 1.06 $\pm$ 0.29 | 34.9 | 0.08 | ... |
| C$_2$H$_5$OH | 13$_{5,8}$–12$_{4,8}$ | 163 | 351.96548 | 0.25 $\pm$ 0.03 | 2.0 | 0.55 $\pm$ 0.18 | 35.3 | 0.08 | ... |

: Line Parameters for C$_2$H$_5$OH

Table notes: (1) Blend of two C$_2$H$_5$OH lines with similar spectroscopic constants. (2) Blend of four C$_2$H$_5$OH lines with similar spectroscopic constants. (4) Blend of three C$_2$H$_5$OH lines with similar spectroscopic constants. (5) Possible blend with CH$_3$CHO.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | $E_{u}$ | Frequency | $T_{br}$ | $\Delta$$V$ | $\int T_{br} dV$ | $V_{LSR}$ | RMS | Note |
|  |  | \(K\) | (GHz) | \(K\) | (km/s) | (K km/s) | (km/s) | \(K\) |  |
| HCOOCH$_3$ | 20$_{4,17}$–19$_{4,16}$ A $\nu_t$ = 1 | 322 | 242.61007 | 0.35 $\pm$ 0.02 | 2.4 | 0.92 $\pm$ 0.14 | 34.3 | 0.04 | ... |
| HCOOCH$_3$ | 19$_{5,14}$–18$_{5,13}$ A | 130 | 242.89603 | 0.74 $\pm$ 0.02 | 3.6 | 2.85 $\pm$ 0.19 | 34.5 | 0.04 | ... |
| HCOOCH$_3$ | 19$_{4,15}$–18$_{4,14}$ A $\nu_t$ = 1 | 313 | 244.06667 | 0.35 $\pm$ 0.02 | 3.4 | 1.28 $\pm$ 0.18 | 34.4 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{10,10}$–19$_{10,9}$ E $\nu_t$ = 1 | 378 | 244.11242 | 0.13 $\pm$ 0.02 | 4.0 | 0.56 $\pm$ 0.22 | 33.9 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{12,8}$–19$_{12,7}$ A $\nu_t$ = 1 | 407 | 244.19830 | 0.17 $\pm$ 0.02 | 4.8 | 0.89 $\pm$ 0.25 | 34.5 | 0.04 | \(1\) |
| HCOOCH$_3$ | 20$_{10,11}$–19$_{10,10}$ A $\nu_t$ = 1 | 377 | 244.52854 | 0.38 $\pm$ 0.02 | 3.0 | 1.21 $\pm$ 0.16 | 34.7 | 0.04 | \(1\) |
| HCOOCH$_3$ | 20$_{4,17}$–19$_{4,16}$ E | 135 | 244.58034 | 0.74 $\pm$ 0.02 | 4.6 | 3.64 $\pm$ 0.24 | 34.7 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{4,17}$–19$_{4,16}$ A | 135 | 244.59405 | 0.78 $\pm$ 0.02 | 3.6 | 3.02 $\pm$ 0.19 | 34.8 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{11,10}$–19$_{11,9}$ E $\nu_t$ = 1 | 391 | 244.72966 | 0.29 $\pm$ 0.03 | 2.2 | 0.67 $\pm$ 0.12 | 34.1 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{9,12}$–19$_{9,11}$ A $\nu_t$ = 1 | 365 | 244.84534 | 0.43 $\pm$ 0.02 | 2.9 | 1.33 $\pm$ 0.17 | 34.3 | 0.04 | \(1\) |
| HCOOCH$_3$ | 19$_{4,15}$–18$_{4,14}$ E $\nu_t$ = 1 | 313 | 244.90213 | 0.30 $\pm$ 0.02 | 3.6 | 1.17 $\pm$ 0.19 | 34.4 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{10,11}$–19$_{10,10}$ E $\nu_t$ = 1 | 377 | 245.08271 | 0.15 $\pm$ 0.02 | 4.0 | 0.65 $\pm$ 0.22 | 35.3 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{8,12}$–19$_{8,11}$ E $\nu_t$ = 1 | 354 | 245.26174 | 0.17 $\pm$ 0.02 | 5.0 | 0.88 $\pm$ 0.26 | 34.7 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{8,13}$–19$_{8,12}$ A $\nu_t$ = 1 | 354 | 245.34255 | 0.34 $\pm$ 0.02 | 3.2 | 1.14 $\pm$ 0.19 | 34.2 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{9,12}$–19$_{9,11}$ E $\nu_t$ = 1 | 365 | 245.54388 | 0.28 $\pm$ 0.02 | 2.5 | 0.75 $\pm$ 0.13 | 35.0 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{15,5}$–19$_{15,4}$ A | 273 | 245.65121 | 0.42 $\pm$ 0.02 | 3.2 | 1.43 $\pm$ 0.17 | 34.7 | 0.04 | \(1\) |
| HCOOCH$_3$ | 20$_{15,5}$–19$_{15,4}$ E | 273 | 245.65678 | 0.29 $\pm$ 0.02 | 3.1 | 0.98 $\pm$ 0.17 | 34.5 | 0.04 | ... |
| HCOOCH$_3$ | 20$_{15,6}$–19$_{15,5}$ E | 273 | 245.67298 | 0.33 $\pm$ 0.02 | 2.4 | 0.83 $\pm$ 0.13 | 34.1 | 0.04 | ... |
| HCOOCH$_3$ | 23$_{2,22}$–22$_{2,21}$ A $\nu_t$ = 1 | 343 | 256.99936 | 0.36 $\pm$ 0.02 | 4.2 | 1.62 $\pm$ 0.18 | 34.8 | 0.03 | ... |
| HCOOCH$_3$ | 23$_{1,22}$–22$_{1,21}$ A $\nu_t$ = 1 | 343 | 257.01547 | 0.36 $\pm$ 0.02 | 3.6 | 1.39 $\pm$ 0.16 | 34.3 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{9,12}$–20$_{9,11}$ E $\nu_t$ = 1 | 377 | 257.04978 | 0.46 $\pm$ 0.02 | 4.5 | 2.18 $\pm$ 0.19 | 34.2 | 0.03 | ... |
| HCOOCH$_3$ | 20$_{5,15}$–19$_{5,14}$ E | 143 | 257.22661 | 0.69 $\pm$ 0.02 | 4.1 | 3.03 $\pm$ 0.17 | 34.6 | 0.03 | ... |
| HCOOCH$_3$ | 20$_{5,15}$–19$_{5,14}$ A | 143 | 257.25267 | 0.76 $\pm$ 0.02 | 4.4 | 3.58 $\pm$ 0.21 | 34.4 | 0.03 | \(1\) |
| HCOOCH$_3$ | 21$_{9,13}$–20$_{9,12}$ A $\nu_t$ = 1 | 377 | 257.29779 | 0.42 $\pm$ 0.02 | 3.7 | 1.66 $\pm$ 0.16 | 34.0 | 0.03 | \(1\) |
| HCOOCH$_3$ | 20$_{4,16}$–19$_{4,15}$ E $\nu_t$ = 1 | 325 | 257.58889 | 0.38 $\pm$ 0.02 | 4.6 | 1.86 $\pm$ 0.21 | 35.4 | 0.03 | ... |
| HCOOCH$_3$ | 22$_{3,20}$–21$_{3,19}$ E | 152 | 257.69033 | 0.72 $\pm$ 0.02 | 3.7 | 2.88 $\pm$ 0.16 | 34.6 | 0.03 | ... |
| HCOOCH$_3$ | 22$_{3,20}$–21$_{3,19}$ A | 152 | 257.69949 | 0.73 $\pm$ 0.02 | 3.5 | 2.75 $\pm$ 0.15 | 34.5 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{8,13}$–20$_{8,12}$ E $\nu_t$ = 1 | 366 | 257.83109 | 0.27 $\pm$ 0.02 | 3.7 | 1.05 $\pm$ 0.16 | 34.1 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{8,14}$–20$_{8,13}$ A $\nu_t$ = 1 | 366 | 257.88987 | 0.24 $\pm$ 0.02 | 2.3 | 0.59 $\pm$ 0.11 | 33.8 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{8,13}$–20$_{8,12}$ A $\nu_t$ = 1 | 366 | 257.90613 | 0.26 $\pm$ 0.02 | 2.4 | 0.66 $\pm$ 0.11 | 35.3 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{16,5}$–20$_{16,4}$ E | 306 | 257.91989 | 0.25 $\pm$ 0.02 | 3.5 | 0.93 $\pm$ 0.15 | 34.0 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{16,6}$–20$_{16,5}$ E | 306 | 257.93383 | 0.21 $\pm$ 0.02 | 3.2 | 0.73 $\pm$ 0.15 | 34.7 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{15,6}$–20$_{15,5}$ A | 285 | 258.00176 | 0.46 $\pm$ 0.02 | 3.2 | 1.55 $\pm$ 0.14 | 34.4 | 0.03 | \(1\) |
| HCOOCH$_3$ | 24$_{1,24}$–23$_{1,23}$ A $\nu_t$ = 1 | 345 | 258.01075 | 0.63 $\pm$ 0.01 | 3.9 | 2.58 $\pm$ 0.18 | 34.5 | 0.03 | \(2\) |
| HCOOCH$_3$ | 21$_{15,7}$–20$_{15,6}$ E | 285 | 258.02424 | 0.30 $\pm$ 0.02 | 2.2 | 0.69 $\pm$ 0.11 | 35.0 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{9,13}$–20$_{9,12}$ E $\nu_t$ = 1 | 377 | 258.03797 | 0.31 $\pm$ 0.02 | 1.4 | 0.48 $\pm$ 0.06 | 33.7 | 0.03 | ... |
| HCOOCH$_3$ | 24$_{1,24}$–23$_{1,23}$ E $\nu_t$ = 1 | 345 | 258.05504 | 0.69 $\pm$ 0.02 | 4.9 | 3.57 $\pm$ 0.21 | 35.0 | 0.03 | \(1\) |
| HCOOCH$_3$ | 22$_{2,20}$–21$_{2,19}$ E | 152 | 258.08104 | 0.85 $\pm$ 0.02 | 5.4 | 4.93 $\pm$ 0.23 | 34.3 | 0.03 | ... |
| HCOOCH$_3$ | 22$_{2,20}$–21$_{2,19}$ A | 152 | 258.08949 | 0.76 $\pm$ 0.02 | 3.9 | 3.14 $\pm$ 0.18 | 34.6 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{14,7}$–20$_{14,6}$ A | 266 | 258.12119 | 0.69 $\pm$ 0.02 | 4.5 | 3.26 $\pm$ 0.20 | 33.9 | 0.03 | \(2\) |
| HCOOCH$_3$ | 21$_{14,8}$–20$_{14,7}$ E | 266 | 258.14209 | 0.35 $\pm$ 0.02 | 3.8 | 1.41 $\pm$ 0.16 | 34.7 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{13,8}$–20$_{13,7}$ A | 248 | 258.27743 | 0.84 $\pm$ 0.01 | 6.3 | 5.64 $\pm$ 0.36 | 36.0 | 0.03 | \(2\) |
| HCOOCH$_3$ | 21$_{12,9}$–20$_{12,8}$ E | 232 | 258.47645 | 0.47 $\pm$ 0.01 | 5.1 | 2.58 $\pm$ 0.24 | 35.3 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{12,9}$–20$_{12,8}$ A | 232 | 258.48298 | 0.62 $\pm$ 0.02 | 5.8 | 3.84 $\pm$ 0.27 | 34.9 | 0.03 | \(1\) |
| HCOOCH$_3$ | 23$_{2,22}$–22$_{2,21}$ E | 156 | 258.49087 | 0.79 $\pm$ 0.02 | 3.9 | 3.27 $\pm$ 0.17 | 34.7 | 0.03 | ... |
| HCOOCH$_3$ | 23$_{2,22}$–22$_{2,21}$ A | 156 | 258.49624 | 0.83 $\pm$ 0.01 | 5.0 | 4.38 $\pm$ 0.28 | 34.4 | 0.03 | \(1\) |
| HCOOCH$_3$ | 23$_{1,22}$–22$_{1,21}$ E | 156 | 258.50273 | 0.81 $\pm$ 0.01 | 3.5 | 3.00 $\pm$ 0.18 | 34.6 | 0.03 | ... |
| HCOOCH$_3$ | 23$_{1,22}$–22$_{1,21}$ A | 156 | 258.50818 | 0.85 $\pm$ 0.02 | 3.3 | 2.97 $\pm$ 0.14 | 34.5 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{5,17}$–20$_{5,16}$ A $\nu_t$ = 1 | 341 | 258.70105 | 0.33 $\pm$ 0.02 | 2.7 | 0.93 $\pm$ 0.12 | 34.3 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{11,10}$–20$_{11,9}$ E | 217 | 258.74625 | 0.50 $\pm$ 0.02 | 3.5 | 1.84 $\pm$ 0.15 | 35.0 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{11,11}$–20$_{11,10}$ A | 217 | 258.75667 | 0.62 $\pm$ 0.02 | 4.9 | 3.20 $\pm$ 0.21 | 34.9 | 0.03 | \(1\) |
| HCOOCH$_3$ | 21$_{11,11}$–20$_{11,10}$ E | 217 | 258.76997 | 0.59 $\pm$ 0.02 | 4.8 | 3.03 $\pm$ 0.20 | 35.1 | 0.03 | \(1\) |
| HCOOCH$_3$ | 21$_{3,18}$–20$_{3,17}$ A $\nu_t$ = 1 | 333 | 258.77532 | 0.35 $\pm$ 0.02 | 2.9 | 1.07 $\pm$ 0.12 | 35.1 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{7,14}$–20$_{7,13}$ A $\nu_t$ = 1 | 356 | 259.00387 | 0.39 $\pm$ 0.02 | 4.3 | 1.77 $\pm$ 0.32 | 34.2 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{7,14}$–20$_{7,13}$ E $\nu_t$ = 1 | 356 | 259.02583 | 0.29 $\pm$ 0.02 | 2.2 | 0.67 $\pm$ 0.09 | 34.6 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{10,11}$–20$_{10,10}$ E | 203 | 259.11395 | 0.46 $\pm$ 0.02 | 4.3 | 2.09 $\pm$ 0.19 | 34.6 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{10,12}$–20$_{10,11}$ A | 203 | 259.12818 | 0.77 $\pm$ 0.02 | 4.1 | 3.37 $\pm$ 0.17 | 34.7 | 0.03 | \(1\) |
| HCOOCH$_3$ | 21$_{10,12}$–20$_{10,11}$ E | 203 | 259.13793 | 0.45 $\pm$ 0.02 | 3.4 | 1.63 $\pm$ 0.14 | 34.6 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{3,18}$–20$_{3,17}$ E $\nu_t$ = 1 | 333 | 259.26499 | 0.28 $\pm$ 0.02 | 3.3 | 0.99 $\pm$ 0.14 | 34.2 | 0.03 | ... |
| HCOOCH$_3$ | 20$_{4,16}$–19$_{4,15}$ A | 139 | 259.52181 | 0.68 $\pm$ 0.02 | 4.1 | 2.98 $\pm$ 0.17 | 35.0 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{9,12}$–20$_{9,11}$ E | 190 | 259.62930 | 0.46 $\pm$ 0.02 | 3.6 | 1.76 $\pm$ 0.16 | 34.7 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{9,13}$–20$_{9,12}$ A | 190 | 259.64653 | 0.85 $\pm$ 0.02 | 4.8 | 4.37 $\pm$ 0.21 | 33.8 | 0.03 | \(1\) |
| HCOOCH$_3$ | 21$_{9,13}$–20$_{9,12}$ E | 190 | 259.65308 | 0.53 $\pm$ 0.02 | 3.5 | 2.01 $\pm$ 0.15 | 34.4 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{3,18}$–20$_{3,17}$ E | 147 | 260.24450 | 0.66 $\pm$ 0.02 | 4.1 | 2.89 $\pm$ 0.17 | 34.7 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{8,14}$–20$_{8,13}$ A | 179 | 260.39273 | 0.59 $\pm$ 0.02 | 3.5 | 2.22 $\pm$ 0.15 | 34.6 | 0.03 | ... |
| HCOOCH$_3$ | 21$_{8,13}$–20$_{8,12}$ A | 179 | 260.41533 | 0.57 $\pm$ 0.02 | 4.0 | 2.42 $\pm$ 0.17 | 34.6 | 0.03 | ... |
| HCOOCH$_3$ | 27$_{8,20}$–26$_{8,19}$ A | 267 | 337.50352 | 0.39 $\pm$ 0.04 | 2.9 | 1.19 $\pm$ 0.29 | 34.8 | 0.07 | ... |
| HCOOCH$_3$ | 27$_{8,19}$–26$_{8,18}$ A | 267 | 338.35579 | 0.37 $\pm$ 0.04 | 3.4 | 1.33 $\pm$ 0.31 | 34.7 | 0.07 | ... |
| HCOOCH$_3$ | 27$_{7,21}$–26$_{7,20}$ E | 258 | 338.39632 | 0.53 $\pm$ 0.03 | 4.4 | 2.46 $\pm$ 0.39 | 34.9 | 0.07 | \(1\) |
| HCOOCH$_3$ | 13$_{7,7}$–12$_{6,6}$ A | 86 | 339.18591 | 0.19 $\pm$ 0.04 | 1.5 | 0.30 $\pm$ 0.14 | 34.3 | 0.07 | \(3\) |
| HCOOCH$_3$ | 13$_{7,6}$–12$_{6,7}$ A | 86 | 339.19634 | 0.21 $\pm$ 0.03 | 2.7 | 0.63 $\pm$ 0.25 | 34.7 | 0.07 | \(3\) |
| HCOOCH$_3$ | 29$_{3,26}$–28$_{3,25}$ A $\nu_t$ = 1 | 450 | 339.88222 | 0.24 $\pm$ 0.04 | 3.8 | 0.99 $\pm$ 0.34 | 34.6 | 0.07 | ... |
| HCOOCH$_3$ | 28$_{5,24}$–27$_{5,23}$ E | 257 | 340.74199 | 0.58 $\pm$ 0.04 | 4.9 | 3.03 $\pm$ 0.42 | 34.3 | 0.07 | ... |
| HCOOCH$_3$ | 28$_{5,24}$–27$_{5,23}$ A | 257 | 340.75476 | 0.41 $\pm$ 0.03 | 5.3 | 2.33 $\pm$ 0.45 | 34.7 | 0.07 | ... |
| HCOOCH$_3$ | 29$_{5,25}$–28$_{5,24}$ E $\nu_t$ = 1 | 460 | 349.68548 | 0.26 $\pm$ 0.04 | 2.1 | 0.58 $\pm$ 0.21 | 35.1 | 0.08 | ... |
| HCOOCH$_3$ | 30$_{4,27}$–29$_{4,26}$ A $\nu_t$ = 1 | 467 | 350.13257 | 0.71 $\pm$ 0.03 | 2.0 | 1.48 $\pm$ 0.30 | 33.5 | 0.08 | ... |
| HCOOCH$_3$ | 30$_{3,27}$–29$_{3,26}$ A $\nu_t$ = 1 | 467 | 350.30254 | 0.33 $\pm$ 0.04 | 4.2 | 1.48 $\pm$ 0.39 | 34.0 | 0.08 | ... |
| HCOOCH$_3$ | 30$_{4,27}$–29$_{4,26}$ E $\nu_t$ = 1 | 467 | 350.55020 | 0.33 $\pm$ 0.04 | 3.7 | 1.27 $\pm$ 0.37 | 33.9 | 0.08 | ... |
| HCOOCH$_3$ | 27$_{6,21}$–26$_{6,20}$ E | 252 | 350.91952 | 0.49 $\pm$ 0.03 | 4.4 | 2.27 $\pm$ 0.52 | 34.6 | 0.08 | ... |
| HCOOCH$_3$ | 27$_{6,21}$–26$_{6,20}$ A | 252 | 350.94733 | 0.53 $\pm$ 0.04 | 3.9 | 2.21 $\pm$ 0.35 | 34.4 | 0.08 | ... |
| HCOOCH$_3$ | 28$_{7,22}$–27$_{7,21}$ E | 275 | 350.99804 | 0.50 $\pm$ 0.04 | 4.3 | 2.29 $\pm$ 0.37 | 34.8 | 0.08 | ... |
| HCOOCH$_3$ | 28$_{7,22}$–27$_{7,21}$ A | 275 | 351.01591 | 0.49 $\pm$ 0.04 | 4.9 | 2.57 $\pm$ 0.43 | 35.2 | 0.08 | ... |
| HCOOCH$_3$ | 29$_{5,25}$–28$_{5,24}$ E | 274 | 351.51710 | 0.40 $\pm$ 0.04 | 4.7 | 1.99 $\pm$ 0.40 | 35.2 | 0.08 | ... |
| HCOOCH$_3$ | 29$_{5,25}$–28$_{5,24}$ A | 274 | 351.52916 | 0.41 $\pm$ 0.04 | 4.6 | 2.02 $\pm$ 0.39 | 35.0 | 0.08 | ... |
| HCOOCH$_3$ | 28$_{8,20}$–27$_{8,19}$ E | 284 | 351.82345 | 0.39 $\pm$ 0.04 | 4.0 | 1.67 $\pm$ 0.35 | 34.6 | 0.08 | ... |
| HCOOCH$_3$ | 28$_{8,20}$–27$_{8,19}$ A | 284 | 351.84219 | 0.44 $\pm$ 0.04 | 3.4 | 1.59 $\pm$ 0.30 | 35.0 | 0.08 | ... |
| HCOOCH$_3$ | 30$_{4,27}$–29$_{4,26}$ E | 281 | 352.28276 | 0.41 $\pm$ 0.04 | 3.0 | 1.31 $\pm$ 0.28 | 34.6 | 0.08 | ... |
| HCOOCH$_3$ | 30$_{4,27}$–29$_{4,26}$ A | 281 | 352.29258 | 0.40 $\pm$ 0.04 | 4.5 | 1.87 $\pm$ 0.38 | 34.7 | 0.08 | ... |
| HCOOCH$_3$ | 30$_{3,27}$–29$_{3,26}$ E | 281 | 352.40468 | 0.51 $\pm$ 0.04 | 2.0 | 1.09 $\pm$ 0.17 | 34.1 | 0.08 | ... |
| HCOOCH$_3$ | 30$_{3,27}$–29$_{3,26}$ A | 281 | 352.41414 | 0.53 $\pm$ 0.04 | 3.7 | 2.09 $\pm$ 0.32 | 34.4 | 0.08 | ... |
| HCOOCH$_3$ | 33$_{1,33}$–32$_{1,32}$ A $\nu_t$ = 1 | 479 | 352.81684 | 0.32 $\pm$ 0.04 | 3.0 | 1.00 $\pm$ 0.26 | 33.7 | 0.08 | \(1\) |

: Line Parameters for HCOOCH$_3$

Table notes: (1) Blend of two HCOOCH$_3$ lines with similar spectroscopic constants. (2) Blend of three HCOOCH$_3$ lines with similar spectroscopic constants.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | $E_{u}$ | Frequency | $T_{br}$ | $\Delta$$V$ | $\int T_{br} dV$ | $V_{LSR}$ | RMS | Note |
|  |  | \(K\) | (GHz) | \(K\) | (km/s) | (K km/s) | (km/s) | \(K\) |  |
| CH$_3$OCH$_3$ | 5$_{3,2}$–4$_{2,3}$ EE | 26 | 241.52872 | 0.59 $\pm$ 0.02 | 5.0 | 3.12 $\pm$ 0.26 | 33.3 | 0.04 | \(1\) |
| CH$_3$OCH$_3$ | 5$_{3,2}$–4$_{2,3}$ AA | 26 | 241.53103 | 0.58 $\pm$ 0.02 | 5.2 | 3.23 $\pm$ 0.32 | 36.3 | 0.04 | ... |
| CH$_3$OCH$_3$ | 21$_{3,18}$–20$_{4,17}$ EE | 226 | 241.63730 | 0.25 $\pm$ 0.02 | 4.7 | 1.25 $\pm$ 0.29 | 34.8 | 0.04 | \(1\) |
| CH$_3$OCH$_3$ | 13$_{1,13}$–12$_{0,12}$ EE | 81 | 241.94654 | 0.92 $\pm$ 0.02 | 4.2 | 4.12 $\pm$ 0.23 | 34.5 | 0.04 | \(2\) |
| CH$_3$OCH$_3$ | 23$_{2,22}$–23$_{1,23}$ EE | 253 | 244.50830 | 0.16 $\pm$ 0.02 | 4.2 | 0.72 $\pm$ 0.24 | 33.5 | 0.04 | ... |
| CH$_3$OCH$_3$ | 23$_{2,22}$–23$_{1,23}$ AA | 253 | 244.51274 | 0.12 $\pm$ 0.02 | 3.3 | 0.40 $\pm$ 0.17 | 34.5 | 0.04 | ... |
| CH$_3$OCH$_3$ | 18$_{2,16}$–17$_{3,15}$ EE | 164 | 257.04988 | 0.46 $\pm$ 0.02 | 4.4 | 2.16 $\pm$ 0.19 | 34.4 | 0.03 | \(2\) |
| CH$_3$OCH$_3$ | 27$_{3,25}$–27$_{2,26}$ EE | 356 | 257.61453 | 0.09 $\pm$ 0.02 | 8.1 | 0.79 $\pm$ 0.37 | 34.0 | 0.03 | \(2\) (3) |
| CH$_3$OCH$_3$ | 14$_{1,14}$–13$_{0,13}$ EE | 93 | 258.54906 | 1.17 $\pm$ 0.02 | 4.4 | 5.43 $\pm$ 0.19 | 34.2 | 0.03 | \(2\) |
| CH$_3$OCH$_3$ | 17$_{5,12}$–17$_{4,13}$ EE | 175 | 259.31195 | 0.46 $\pm$ 0.07 | 9.0 | 3.34 $\pm$ 0.16 | 35.0 | 0.03 | \(2\) |
| CH$_3$OCH$_3$ | 6$_{3,4}$–5$_{2,3}$ EE | 32 | 259.48973 | 0.47 $\pm$ 0.01 | 3.0 | 1.48 $\pm$ 0.20 | 34.4 | 0.03 | \(1\) |
| CH$_3$OCH$_3$ | 6$_{3,4}$–5$_{2,3}$ AA | 32 | 259.49375 | 0.39 $\pm$ 0.01 | 2.9 | 1.21 $\pm$ 0.19 | 34.4 | 0.03 | ... |
| CH$_3$OCH$_3$ | 23$_{5,19}$–23$_{4,20}$ EE | 287 | 259.69007 | 0.41 $\pm$ 0.02 | 4.3 | 1.87 $\pm$ 0.18 | 34.1 | 0.03 | \(2\) |
| CH$_3$OCH$_3$ | 21$_{5,17}$–21$_{4,18}$ EE | 246 | 259.73215 | 0.47 $\pm$ 0.02 | 5.8 | 2.87 $\pm$ 0.25 | 34.4 | 0.03 | \(2\) |
| CH$_3$OCH$_3$ | 20$_{5,16}$–20$_{4,17}$ EE | 227 | 259.98441 | 0.53 $\pm$ 0.01 | 3.5 | 1.99 $\pm$ 0.20 | 35.6 | 0.03 | \(2\) |
| CH$_3$OCH$_3$ | 24$_{5,20}$–24$_{4,21}$ EE | 309 | 260.00439 | 0.43 $\pm$ 0.02 | 5.0 | 2.33 $\pm$ 0.21 | 34.0 | 0.03 | \(2\) |
| CH$_3$OCH$_3$ | 19$_{5,15}$–19$_{4,16}$ EE | 208 | 260.32922 | 0.46 $\pm$ 0.02 | 4.1 | 2.03 $\pm$ 0.21 | 34.4 | 0.03 | \(2\) |
| CH$_3$OCH$_3$ | 25$_{5,21}$–25$_{4,22}$ EE | 332 | 260.61685 | 0.35 $\pm$ 0.02 | 3.0 | 1.13 $\pm$ 0.15 | 35.0 | 0.03 | \(2\) |
| CH$_3$OCH$_3$ | 21$_{2,19}$–20$_{3,18}$ AA | 220 | 337.42046 | 0.57 $\pm$ 0.04 | 3.2 | 1.95 $\pm$ 0.32 | 34.6 | 0.07 | ... |
| CH$_3$OCH$_3$ | 7$_{4,4}$–6$_{3,3}$ AE | 48 | 337.72300 | 0.55 $\pm$ 0.04 | 2.3 | 1.33 $\pm$ 0.28 | 35.1 | 0.07 | ... |
| CH$_3$OCH$_3$ | 7$_{4,3}$–6$_{3,3}$ EE | 48 | 337.73219 | 0.40 $\pm$ 0.04 | 4.5 | 1.88 $\pm$ 0.38 | 35.4 | 0.07 | ... |
| CH$_3$OCH$_3$ | 7$_{4,4}$–6$_{3,4}$ EE | 48 | 337.77802 | 0.40 $\pm$ 0.03 | 3.8 | 1.59 $\pm$ 0.32 | 33.8 | 0.07 | ... |
| CH$_3$OCH$_3$ | 7$_{4,3}$–6$_{3,4}$ AA | 48 | 337.78721 | 0.71 $\pm$ 0.03 | 5.8 | 4.41 $\pm$ 0.51 | 34.8 | 0.07 | ... |
| CH$_3$OCH$_3$ | 19$_{1,18}$–18$_{2,17}$ EE | 176 | 339.49153 | 0.60 $\pm$ 0.04 | 3.9 | 2.50 $\pm$ 0.33 | 34.5 | 0.07 | ... |
| CH$_3$OCH$_3$ | 10$_{3,7}$–9$_{2,8}$ EE | 63 | 340.61262 | 0.45 $\pm$ 0.03 | 7.0 | 3.35 $\pm$ 0.59 | 35.1 | 0.07 | ... |
| CH$_3$OCH$_3$ | 11$_{2,9}$–10$_{1,10}$ EE | 66 | 349.80618 | 0.31 $\pm$ 0.04 | 4.6 | 1.52 $\pm$ 0.41 | 33.6 | 0.08 | ... |

: Line Parameters for CH$_3$OCH$_3$

Table notes: (1) Blend of three CH$_3$OCH$_3$ lines with similar spectroscopic constants. (2) Blend of four CH$_3$OCH$_3$ lines with similar spectroscopic constants.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | $E_{u}$ | Frequency | $T_{br}$ | $\Delta$$V$ | $\int T_{br} dV$ | $V_{LSR}$ | RMS | Note |
|  |  | \(K\) | (GHz) | \(K\) | (km/s) | (K km/s) | (km/s) | \(K\) |  |
| C$_2$H$_5$CN | 27$_{3,25}$–26$_{3,24}$ | 173 | 241.62587 | 0.13 $\pm$ 0.02 | 4.9 | 0.69 $\pm$ 0.29 | 33.3 | 0.04 | ... |
| C$_2$H$_5$CN | 27$_{9,18}$–26$_{9,17}$ | 253 | 241.93218 | 0.23 $\pm$ 0.03 | 3.6 | 0.86 $\pm$ 0.21 | 33.9 | 0.04 | \(1\) |
| C$_2$H$_5$CN | 27$_{12,15}$–26$_{12,14}$ | 322 | 241.95905 | 0.12 $\pm$ 0.02 | 3.1 | 0.40 $\pm$ 0.16 | 34.2 | 0.04 | \(2\) |
| C$_2$H$_5$CN | 27$_{8,20}$–26$_{8,19}$ | 234 | 241.97045 | 0.30 $\pm$ 0.02 | 1.8 | 0.56 $\pm$ 0.10 | 33.5 | 0.04 | \(2\) |
| C$_2$H$_5$CN | 27$_{13,14}$–26$_{13,13}$ | 350 | 241.99710 | 0.12 $\pm$ 0.02 | 3.2 | 0.40 $\pm$ 0.17 | 33.2 | 0.04 | \(2\) |
| C$_2$H$_5$CN | 27$_{7,21}$–26$_{7,20}$ | 217 | 242.05249 | 0.23 $\pm$ 0.02 | 4.0 | 0.97 $\pm$ 0.22 | 34.2 | 0.04 | \(2\) |
| C$_2$H$_5$CN | 27$_{6,22}$–26$_{6,21}$ | 203 | 242.20698 | 0.30 $\pm$ 0.02 | 6.3 | 2.03 $\pm$ 0.34 | 31.7 | 0.04 | \(2\) |
| C$_2$H$_5$CN | 27$_{4,24}$–26$_{4,23}$ | 181 | 242.66469 | 0.32 $\pm$ 0.03 | 2.4 | 0.83 $\pm$ 0.17 | 33.9 | 0.04 | ... |
| C$_2$H$_5$CN | 14$_{3,11}$–13$_{2,12}$ | 55 | 245.02365 | 0.32 $\pm$ 0.02 | 2.3 | 0.77 $\pm$ 0.14 | 35.1 | 0.04 | ... |
| C$_2$H$_5$CN | 30$_{0,30}$–29$_{0,29}$ | 194 | 257.31064 | 0.11 $\pm$ 0.02 | 3.7 | 0.43 $\pm$ 0.16 | 34.2 | 0.03 | ... |
| C$_2$H$_5$CN | 30$_{1,30}$–29$_{0,29}$ | 194 | 257.58361 | 0.20 $\pm$ 0.02 | 1.5 | 0.32 $\pm$ 0.06 | 33.6 | 0.03 | ... |
| C$_2$H$_5$CN | 29$_{9,21}$–28$_{9,20}$ | 277 | 259.86276 | 0.11 $\pm$ 0.02 | 3.5 | 0.42 $\pm$ 0.15 | 33.9 | 0.03 | \(2\) |
| C$_2$H$_5$CN | 29$_{12,17}$–28$_{12,16}$ | 347 | 259.86989 | 0.35 $\pm$ 0.02 | 1.4 | 0.53 $\pm$ 0.08 | 33.4 | 0.03 | \(2\) |
| C$_2$H$_5$CN | 29$_{13,16}$–28$_{13,15}$ | 374 | 259.90664 | 0.09 $\pm$ 0.02 | 3.2 | 0.31 $\pm$ 0.14 | 33.5 | 0.03 | \(2\) (3) |
| C$_2$H$_5$CN | 29$_{6,24}$–28$_{6,23}$ | 227 | 260.22166 | 0.24 $\pm$ 0.02 | 3.1 | 0.80 $\pm$ 0.15 | 34.8 | 0.03 | ... |
| C$_2$H$_5$CN | 29$_{5,25}$–28$_{5,24}$ | 215 | 260.53569 | 0.27 $\pm$ 0.02 | 3.7 | 1.04 $\pm$ 0.16 | 34.3 | 0.03 | ... |
| NH$_2$CHO | 13$_{0,13}$–12$_{1,12}$ | 91 | 244.85421 | $<$0.08 | ... | $<$0.3 | ... | 0.04 | ... |
| NH$_2$CHO | 13$_{2,12}$–13$_{1,13}$ | 104 | 258.63638 | 0.10 $\pm$ 0.02 | 3.9 | 0.40 $\pm$ 0.17 | 35.6 | 0.03 | \(3\) |
| NH$_2$CHO | 12$_{2,10}$–11$_{2,9}$ | 92 | 260.18909 | 0.36 $\pm$ 0.02 | 4.4 | 1.67 $\pm$ 0.19 | 34.7 | 0.03 | ... |
| NH$_2$CHO | 16$_{9,7}$–15$_{9,6}$ | 380 | 339.68606 | 0.36 $\pm$ 0.03 | 4.3 | 1.63 $\pm$ 0.36 | 33.2 | 0.07 | \(4\) |
| NH$_2$CHO | 16$_{8,8}$–15$_{8,7}$ | 329 | 339.71519 | 0.30 $\pm$ 0.04 | 3.9 | 1.27 $\pm$ 0.34 | 35.2 | 0.07 | \(4\) |
| NH$_2$CHO | 16$_{7,10}$–15$_{7,9}$ | 284 | 339.77954 | 0.36 $\pm$ 0.04 | 3.3 | 1.26 $\pm$ 0.29 | 33.9 | 0.07 | \(5\) |
| NH$_2$CHO | 16$_{6,11}$–15$_{6,10}$ | 246 | 339.90250 | 0.29 $\pm$ 0.04 | 4.9 | 1.49 $\pm$ 0.42 | 34.0 | 0.07 | \(5\) |
| NH$_2$CHO | 16$_{3,14}$–15$_{3,13}$ | 166 | 340.48963 | 0.37 $\pm$ 0.04 | 4.2 | 1.65 $\pm$ 0.36 | 34.0 | 0.07 | ... |
| NH$_2$CHO | 16$_{4,13}$–15$_{4,12}$ | 186 | 340.53439 | 0.36 $\pm$ 0.04 | 5.2 | 1.98 $\pm$ 0.44 | 34.1 | 0.07 | ... |
| NH$_2$CHO | 16$_{4,12}$–15$_{4,11}$ | 186 | 340.69074 | 0.46 $\pm$ 0.03 | 2.5 | 1.19 $\pm$ 0.27 | 33.7 | 0.07 | ... |
| NH$_2$CHO | 16$_{2,14}$–15$_{2,13}$ | 153 | 349.47820 | 0.36 $\pm$ 0.04 | 3.6 | 1.41 $\pm$ 0.33 | 33.9 | 0.08 | ... |
| NH$_2$CHO | 9$_{2,8}$–8$_{1,7}$ | 58 | 349.63403 | $<$0.30 | ... | $<$1.3 | ... | 0.08 | ... |

: Line Parameters for C$_2$H$_5$CN and NH$_2$CHO

Table notes: (1) Blend of four C$_2$H$_5$CN lines with similar spectroscopic constants. (2) Blend of two C$_2$H$_5$CN lines with similar spectroscopic constants. (4) Blend of four NH$_2$CHO lines with similar spectroscopic constants. (5) Blend of two NH$_2$CHO lines with similar spectroscopic constants.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | $E_{u}$ | Frequency | $T_{br}$ | $\Delta$$V$ | $\int T_{br} dV$ | $V_{LSR}$ | RMS | Note |
|  |  | \(K\) | (GHz) | \(K\) | (km/s) | (K km/s) | (km/s) | \(K\) |  |
| *trans*-HCOOH | 12$_{1,12}$–11$_{1,11}$ | 84 | 257.97501 | 0.52 $\pm$ 0.02 | 5.5 | 3.00 $\pm$ 0.23 | 34.5 | 0.03 | ... |
| *trans*-HCOOH | 15$_{4,12}$–14$_{4,11}$ | 181 | 338.14384 | 0.42 $\pm$ 0.03 | 5.0 | 2.26 $\pm$ 0.43 | 34.6 | 0.07 | ... |
| *trans*-HCOOH | 15$_{3,13}$–14$_{3,12}$ | 158 | 338.20186 | 0.36 $\pm$ 0.03 | 4.4 | 1.70 $\pm$ 0.39 | 34.7 | 0.07 | ... |
| *trans*-HCOOH | 15$_{4,11}$–14$_{4,10}$ | 181 | 338.24882 | 0.35 $\pm$ 0.04 | 2.8 | 1.04 $\pm$ 0.26 | 34.7 | 0.07 | ... |
| *trans*-HCOOH | 15$_{3,12}$–14$_{3,11}$ | 159 | 340.22910 | 0.31 $\pm$ 0.04 | 5.8 | 1.92 $\pm$ 0.49 | 35.1 | 0.07 | ... |
| *cis*-HCOOH | 13$_{0,13}$–12$_{1,12}$ | 95 | 244.23510 | 0.33 $\pm$ 0.02 | 1.6 | 0.57 $\pm$ 0.09 | 35.7 | 0.04 | ... |
| *cis*-HCOOH | 9$_{1,9}$–8$_{0,8}$ | 49 | 244.24786 | 0.27 $\pm$ 0.02 | 2.5 | 0.73 $\pm$ 0.16 | 34.2 | 0.04 | \(1\) |
| H$_2$CCO | 12$_{4,9}$–11$_{4,8}$ | 284 | 242.30938 | 0.12 $\pm$ 0.02 | 3.0 | 0.36 $\pm$ 0.16 | 34.3 | 0.04 | \(2\) |
| H$_2$CCO | 12$_{0,12}$–11$_{0,11}$ | 76 | 242.37573 | 0.23 $\pm$ 0.02 | 4.0 | 0.99 $\pm$ 0.27 | 33.8 | 0.04 | ... |
| H$_2$CCO | 12$_{3,10}$–11$_{3,9}$ | 193 | 242.39845 | 0.41 $\pm$ 0.03 | 3.1 | 1.35 $\pm$ 0.19 | 34.4 | 0.04 | \(2\) |
| H$_2$CCO | 12$_{2,11}$–11$_{2,10}$ | 128 | 242.42466 | $<$0.10 | ... | $<$0.4 | ... | 0.04 | ... |
| H$_2$CCO | 12$_{2,10}$–11$_{2,9}$ | 128 | 242.53616 | 0.13 $\pm$ 0.02 | 3.2 | 0.43 $\pm$ 0.19 | 35.5 | 0.04 | ... |
| H$_2$CCO | 12$_{1,11}$–11$_{1,10}$ | 89 | 244.71227 | 0.61 $\pm$ 0.03 | 3.4 | 2.24 $\pm$ 0.20 | 34.4 | 0.04 | ... |
| H$_2$CCO | 13$_{1,13}$–12$_{1,12}$ | 100 | 260.19198 | 0.67 $\pm$ 0.02 | 3.1 | 2.21 $\pm$ 0.18 | 34.6 | 0.03 | ... |
| H$_2$CCO | 17$_{1,17}$–16$_{1,16}$ | 160 | 340.19308 | 0.41 $\pm$ 0.03 | 4.8 | 2.08 $\pm$ 0.61 | 34.6 | 0.07 | \(3\) |
| c-C$_2$H$_4$O | 11$_{2,10}$–10$_{1,9}$ | 104 | 338.77198 | 0.35 $\pm$ 0.03 | 4.2 | 1.57 $\pm$ 0.35 | 34.6 | 0.07 | \(4\) |

: Line Parameters for HCOOH, H$_2$CCO, and c-C$_2$H$_4$O

Table notes: (1) Partial blend with SO$_2$. (2) Blend of two H$_2$CCO lines with similar spectroscopic constants. (3) Partial blend with C$_2$H$_5$OH. (4) Blend of two c-C$_2$H$_4$O lines with similar spectroscopic constants.

# Fitted spectra

Figures [14](#line_others)–[24](#line_otherCOMs_2) show the results of the spectral line fitting (see Section [3.1](#sec_spc) for details).

![](fB1.eps)

![](fB2.eps)

![](fB3.eps)

![](fB4.eps)

![](fB5.eps)

![](fB6.eps)

![](fB7.eps)

![](fB8.eps)

![](fB9.eps)

![](fB10.eps)

![](fB11.eps)

[^1]: https://www.astro.uni-koeln.de/cdms

[^2]: http://spec.jpl.nasa.gov

[^3]: The following lines are used for non-LTE calculation with RADEX; H$^{13}$CO$^+$(3–2), HC$^{18}$O$^+$(4–3), H$_2$CO(5$_{1,5}$–4$_{1,4}$), c-C$_3$H$_2$(3$_{2,1}$–2$_{1,2}$), CN(N = 3–2, J = $\frac{5}{2}$–$\frac{3}{2}$, F = $\frac{5}{2}$–$\frac{5}{2}$), H$^{13}$CN(3–2), HC$^{15}$N(3–2), HC$_3$N(27–26), NO(J = $\frac{7}{2}$–$\frac{5}{2}$, $\Omega$ = $\frac{1}{2}$, F = $\frac{9}{2}$$^+$–$\frac{7}{2}$$^-$), CH$_3$CN(14$_{0}$–13$_{0}$), SiO(6–5), CS(5–4), OCS(20–19), H$_2$CS(7$_{1,6}$–6$_{1,5}$), SO($N_J$ = 6$_{6}$–5$_{5}$), and CH$_3$OH(7$_{5}$ E–6$_{5}$ E).

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Perform LTE rotation diagram analysis for molecules with multiple transitions, single-temperature LTE calculation for other molecules, and non-LTE RADEX calculations for selected molecules",
  "failed_quote": "Column densities of molecular species for which rotation diagram analysis is not applicable are estimated from Equation [Eq_rd1] after solving it for $N$."
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "CH3OH rotation temperature in WB89-789 SMM1 = 245 K",
  "failed_quote": "CH$_3$OH | *245$^{+4}_{-4}$* | *(1.8 $\\pm$ 0.1) $\\times$ 10$^{16}$* | (2.6 $\\pm$ 0.1) $\\times$ 10$^{16}$$^{b}$ | 0.51"
 }
]
```
