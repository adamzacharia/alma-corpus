# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.498L..66B\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. reproducibility.score_inferred is on a 1-5 scale (1 = cannot be reproduced from what is published, 5 = public data plus a complete recipe and numeric results). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Instructions

You turn one published astronomy paper that used ALMA data into a structured METHODS CARD. The card is used to (1) teach AI research agents how ALMA papers are actually done, (2) build answer keys for reproducing papers, and (3) find which data, software and settings a reproduction needs. Accuracy matters more than coverage.

Hard rules:
1. Use only the paper text you are given. Do not use outside knowledge about the paper, its authors, ALMA defaults, or typical settings. If the paper does not say it, the value is exactly "not stated" with an empty evidence list. Never guess, never "typically", never fill a default.
2. Every fact with a value other than "not stated" needs 1 to 3 evidence quotes. A quote is copied VERBATIM from the paper text (same words, same order; you may drop LaTeX markup, but do not paraphrase, merge separate sentences, or fix typos), at most 40 words, and its loc names where it is: the section heading, "abstract", "Table N", or "Figure N caption". Quotes are checked mechanically against the text.
3. Keep values short and in the paper's own terms and units (e.g. "Band 6 (1.3 mm)", "robust = 0.5", "CASA 5.4.0").
4. Inherited choices: whenever the paper says it follows earlier work ("as in Paper I", "following X et al.", "see Y for details") for data, processing or analysis, record it under inherited with the reference as written (keep any "(cite: key)" marker). These are often what blocks a reproduction.
5. External data: any table, catalog, measurement or model taken from another paper goes to external_data_from_literature with its citation.
6. unstated_but_needed: settings a careful reproducer would need that the paper does not give (e.g. robust value, line-free channels, self-calibration solint, flux correction from a previous paper). This list is your reading, so it has no quotes; be specific and do not pad it.
7. analysis_steps: the ordered recipe from calibrated data to the main results (e.g. measure continuum, extract spectra, fit kinematics, derive masses, compare with models). Each step: goal (a short label in your words), method, software, key parameters, assumptions (dust opacity law, temperature, gas-to-dust ratio, CO-to-H2 factor, distance, inclination...), fitting (sampler, priors, likelihood) and how they validated it. Steps are numbered from 1.
8. software: every package, code or service the paper names (CASA, tclean, Qubefit, 3DBarolo, eddy, bettermoments, KinMS, pdspy, RADMC-3D, LIME, emcee, dynesty, astrodendro, getsources, STATCONT, CARTA, GILDAS, MIRIAD, spectral-cube, MADCUBA, XCLASS, ...) with what it was used for. Do not add software the paper does not name.
9. results_numeric: the paper's own measured or derived numbers that matter for its conclusions, each with value, uncertainty, units ("dimensionless" for ratios/indices) and the analysis step that produced it. These become answer keys, so copy numbers exactly. Skip numbers that are only quoted from other papers.
10. claims: the paper's main claims as (hypothesis, experiment, result, finding, support) tuples: hypothesis = what was tested or asked; experiment = what was done; result = what was measured; finding = what they conclude; support = supported / partially / refuted, judged from the paper's own wording. 2-6 claims.
11. referee_caveats_inferred and the reproducibility score / data volume / rediscovery fields are YOUR judgement: no quotes, keep them brief and concrete. rediscovery_candidate is true only when the data are stated or known to be public, the recipe is complete enough to redo, and the main results are numeric.
12. ALMA project codes look like 2015.1.00123.S; list each one the paper prints, with a quote. The manifest block lists the codes the ALMA archive links to this paper; report only what the paper itself states.
13. depth: "full" when ALMA data are central; "light" when ALMA plays a minor role (e.g. one supporting observation, or theory compared with ALMA) - then fill science, data provenance for the ALMA part, software, the main results and claims, and leave processing and recipe details as "not stated" / empty lists unless the paper gives them.
14. The paper text is Markdown converted from LaTeX or PDF. "(cite: key)" marks a citation and "(ref: key)" a reference-list entry. Tables may be Markdown tables. Ignore conversion noise; never quote it.
15. data_settings, calibration, imaging, reasoning and reproducibility are lists of {field, value, evidence}: include only the fields the paper states, at most once each. Fields you leave out are recorded as "not stated". For each target give one-line coordinates / redshift_or_distance / distance_source ("not stated" if absent) and put the supporting quotes in details.
16. Output only the JSON object, no prose and no code fence.

Output format: one JSON object, with no prose and no code fence around it, that validates against this JSON Schema (every property is required; use "not stated" and empty lists where the paper is silent):
{"$defs":{"CalSetting":{"additionalProperties":false,"properties":{"field":{"enum":["pipeline_or_manual","casa_version","pipeline_version","archive_products_used_as_is","flux_calibrator","flux_scale_uncertainty","self_calibration"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"CitedWork":{"additionalProperties":false,"properties":{"citation":{"type":"string"},"why":{"type":"string"}},"required":["citation","why"],"type":"object"},"Claim":{"additionalProperties":false,"properties":{"hypothesis":{"type":"string"},"experiment":{"type":"string"},"result":{"type":"string"},"finding":{"type":"string"},"support":{"enum":["supported","partially","refuted"],"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["hypothesis","experiment","result","finding","support","evidence"],"type":"object"},"DataSetting":{"additionalProperties":false,"properties":{"field":{"enum":["bands","frequencies_and_spectral_setup","continuum_bandwidth","arrays","configurations","baselines","angular_resolution","max_recoverable_scale","sensitivity","time_on_source","observing_dates","pi_or_archival_as_stated"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"Evidence":{"additionalProperties":false,"properties":{"loc":{"description":"Section heading (e.g. '2.1 Observations') or 'abstract', 'Table 2', 'Figure 3 caption'","type":"string"},"quote":{"description":"Verbatim text copied from the paper, at most 40 words","type":"string"}},"required":["loc","quote"],"type":"object"},"ExternalData":{"additionalProperties":false,"properties":{"what":{"$ref":"#/$defs/Fact","description":"Table, catalog or measurement taken from another paper"},"citation":{"description":"The cited work as written in the paper, with its (cite: key) if present","type":"string"}},"required":["what","citation"],"type":"object"},"Facility":{"additionalProperties":false,"properties":{"name":{"type":"string"},"provided":{"$ref":"#/$defs/Fact","description":"What this facility, survey or archive contributed"}},"required":["name","provided"],"type":"object"},"Fact":{"additionalProperties":false,"properties":{"value":{"description":"The fact in the paper's terms, or exactly 'not stated'","type":"string"},"evidence":{"description":"1-3 verbatim quotes supporting the value; empty when not stated","items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["value","evidence"],"type":"object"},"ImgSetting":{"additionalProperties":false,"properties":{"field":{"enum":["task","deconvolver","weighting_robust","uv_taper","cell_size","image_size","masking","multiscale_scales","continuum_subtraction","line_free_channels","primary_beam_correction","array_combination","smoothing","final_beam","final_rms"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"Inherited":{"additionalProperties":false,"properties":{"what":{"$ref":"#/$defs/Fact","description":"A choice the paper takes from earlier work ('as in Paper I', 'following X')"},"from_reference":{"type":"string"}},"required":["what","from_reference"],"type":"object"},"NumericResult":{"additionalProperties":false,"properties":{"quantity":{"type":"string"},"value":{"type":"string"},"uncertainty":{"description":"As stated (e.g. '+0.3/-0.2', '10%'), or 'not stated'","type":"string"},"units":{"description":"Units as stated; 'dimensionless' for ratios and indices","type":"string"},"from_step":{"description":"order of the analysis step that produced it; 0 if not tied to one","type":"integer"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["quantity","value","uncertainty","units","from_step","evidence"],"type":"object"},"ProjectCode":{"additionalProperties":false,"properties":{"code":{"description":"ALMA project code exactly as printed, e.g. 2015.1.00123.S","type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["code","evidence"],"type":"object"},"ReasonSetting":{"additionalProperties":false,"properties":{"field":{"enum":["why_this_data","why_this_method","how_they_decided_enough"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"ReproSetting":{"additionalProperties":false,"properties":{"field":{"enum":["data_public_as_stated","products_in_archive"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"Software":{"additionalProperties":false,"properties":{"name":{"type":"string"},"version":{"description":"Version as stated, or 'not stated'","type":"string"},"used_for":{"$ref":"#/$defs/Fact"}},"required":["name","version","used_for"],"type":"object"},"SpectralLine":{"additionalProperties":false,"properties":{"species":{"type":"string"},"transition":{"type":"string"},"rest_frequency":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["species","transition","rest_frequency","evidence"],"type":"object"},"WireStep":{"additionalProperties":false,"properties":{"order":{"type":"integer"},"goal":{"description":"Short label for the step (our wording, e.g. 'measure the continuum flux')","type":"string"},"method":{"$ref":"#/$defs/Fact"},"software":{"items":{"type":"string"},"type":"array"},"key_parameters":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"assumptions":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"fitting":{"$ref":"#/$defs/Fact"},"validation":{"$ref":"#/$defs/Fact"}},"required":["order","goal","method","software","key_parameters","assumptions","fitting","validation"],"type":"object"},"WireTarget":{"additionalProperties":false,"properties":{"name":{"type":"string"},"details":{"description":"Quotes giving its coordinates, redshift/distance and where the distance comes from; empty if none","items":{"$ref":"#/$defs/Evidence"},"type":"array"},"coordinates":{"type":"string"},"redshift_or_distance":{"type":"string"},"distance_source":{"type":"string"}},"required":["name","details","coordinates","redshift_or_distance","distance_source"],"type":"object"}},"additionalProperties":false,"properties":{"depth":{"enum":["full","light"],"type":"string"},"paper_type":{"enum":["observational_alma_primary","archival_reuse","large_program_or_survey","multi_facility_alma_minor","technical_calibration_or_instrument","theory_or_simulation_compared_to_alma","data_release_or_catalog"],"type":"string"},"paper_type_evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"},"fields":{"items":{"enum":["protoplanetary_disks","debris_disks","star_formation","astrochemistry","high_z_galaxies","nearby_galaxies","agn_and_quasars","galaxy_clusters_and_sz","evolved_stars","stellar_physics","solar_system","sun","exoplanets","milky_way_ism","cosmology","transients","instrumentation","other"],"type":"string"},"type":"array"},"question":{"$ref":"#/$defs/Fact"},"targets":{"items":{"$ref":"#/$defs/WireTarget"},"type":"array"},"alma_project_codes":{"items":{"$ref":"#/$defs/ProjectCode"},"type":"array"},"data_settings":{"items":{"$ref":"#/$defs/DataSetting"},"type":"array"},"lines_targeted":{"items":{"$ref":"#/$defs/SpectralLine"},"type":"array"},"other_facilities":{"items":{"$ref":"#/$defs/Facility"},"type":"array"},"external_data_from_literature":{"items":{"$ref":"#/$defs/ExternalData"},"type":"array"},"simulations_or_models_as_data":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"calibration":{"items":{"$ref":"#/$defs/CalSetting"},"type":"array"},"imaging":{"items":{"$ref":"#/$defs/ImgSetting"},"type":"array"},"inherited":{"items":{"$ref":"#/$defs/Inherited"},"type":"array"},"unstated_but_needed":{"items":{"type":"string"},"type":"array"},"analysis_steps":{"items":{"$ref":"#/$defs/WireStep"},"type":"array"},"software":{"items":{"$ref":"#/$defs/Software"},"type":"array"},"results_numeric":{"items":{"$ref":"#/$defs/NumericResult"},"type":"array"},"findings_qualitative":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"claims":{"items":{"$ref":"#/$defs/Claim"},"type":"array"},"reasoning":{"items":{"$ref":"#/$defs/ReasonSetting"},"type":"array"},"alternatives_considered_or_rejected":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"limitations_admitted":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"referee_caveats_inferred":{"items":{"type":"string"},"type":"array"},"reproducibility":{"items":{"$ref":"#/$defs/ReproSetting"},"type":"array"},"code_released":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"missing_for_reproduction":{"items":{"type":"string"},"type":"array"},"estimated_data_volume_inferred":{"type":"string"},"score_inferred":{"type":"integer"},"score_reason":{"type":"string"},"rediscovery_candidate":{"type":"boolean"},"rediscovery_reason":{"type":"string"},"methods_papers":{"items":{"$ref":"#/$defs/CitedWork"},"type":"array"},"companion_papers":{"items":{"$ref":"#/$defs/CitedWork"},"type":"array"},"related_projects_or_surveys":{"items":{"type":"string"},"type":"array"}},"required":["depth","paper_type","paper_type_evidence","fields","question","targets","alma_project_codes","data_settings","lines_targeted","other_facilities","external_data_from_literature","simulations_or_models_as_data","calibration","imaging","inherited","unstated_but_needed","analysis_steps","software","results_numeric","findings_qualitative","claims","reasoning","alternatives_considered_or_rejected","limitations_admitted","referee_caveats_inferred","reproducibility","code_released","missing_for_reproduction","estimated_data_volume_inferred","score_inferred","score_reason","rediscovery_candidate","rediscovery_reason","methods_papers","companion_papers","related_projects_or_surveys"],"type":"object"}

## Paper

Manifest facts (from ADS and the ALMA archive, for orientation only):
```json
{
 "bibcode": "2020MNRAS.498L..66B",
 "title": "What drives galaxy quenching? Resolving molecular gas and star formation in the green valley",
 "year": 2020,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Brownson, Simcha",
 "n_authors": 5,
 "arxiv_id": "2007.02976",
 "doi": "10.1093/mnrasl/slaa128",
 "alma_projects_linked_by_archive": [
  "2015.1.01225.S"
 ]
}
```

Paper text:
<paper>
# *Monthly Notices of the Royal Astronomical Society*:\
LaTeX guide for authors

## Abstract

This is a guide for preparing papers for *Monthly Notices of the Royal Astronomical Society* using the `mnras` LaTeX package. It provides instructions for using the additional features in the document class. This is not a general guide on how to use LaTeX, and nor does it replace the journal’s instructions to authors. See `mnras_template.tex` for a simple template.

editorials, notices – miscellaneous

# Introduction

The journal *Monthly Notices of the Royal Astronomical Society* (MNRAS) encourages authors to prepare their papers using LaTeX. The style file `mnras.cls` can be used to approximate the final appearance of the journal, and provides numerous features to simplify the preparation of papers. This document, `mnras_guide.tex`, provides guidance on using that style file and the features it enables.

This is not a general guide on how to use LaTeX, of which many excellent examples already exist. We particularly recommend *Wikibooks LaTeX*[^3], a collaborative online textbook which is of use to both beginners and experts. Alternatively there are several other online resources, and most academic libraries also hold suitable beginner’s guides.

For guidance on the contents of papers, journal style, and how to submit a paper, see the MNRAS Instructions to Authors[^4]. Only technical issues with the LaTeX class are considered here.

# Obtaining and installing the MNRAS package

Some LaTeX distributions come with the MNRAS package by default. If yours does not, you can either install it using your distribution’s package manager, or download it from the Comprehensive TeX Archive Network[^5] (CTAN).

The files can either be installed permanently by placing them in the appropriate directory (consult the documentation for your LaTeX distribution), or used temporarily by placing them in the working directory for your paper.

To use the MNRAS package, simply specify `mnras` as the document class at the start of a `.tex` file:

    \documentclass{mnras}

Then compile LaTeX (and if necessary BIBTeX) in the usual way.

# Preparing and submitting a paper

We recommend that you start with a copy of the `mnras_template.tex` file. Rename the file, update the information on the title page, and then work on the text of your paper. Guidelines for content, style etc. are given in the instructions to authors on the journal’s website$^{\ref{foot:itas}}$. Note that this document does not follow all the aspects of MNRAS journal style (e.g. it has a table of contents).

If a paper is accepted, it is professionally typeset and copyedited by the publishers. It is therefore likely that minor changes to presentation will occur. For this reason, we ask authors to ignore minor details such as slightly long lines, extra blank spaces, or misplaced figures, because these details will be dealt with during the production process.

Papers must be submitted electronically via the online submission system; paper submissions are not permitted. For full guidance on how to submit a paper, see the instructions to authors.

# Class options

There are several options which can be added to the document class line like this:

    \documentclass[option1,option2]{mnras}

The available options are:

- `letters` – used for papers in the journal’s Letters section.

- `onecolumn` – single column, instead of the default two columns. This should be used *only* if necessary for the display of numerous very long equations.

- `doublespacing` – text has double line spacing. Please don’t submit papers in this format.

- `referee` – *(deprecated)* single column, double spaced, larger text, bigger margins. Please don’t submit papers in this format.

- `galley` – *(deprecated)* no running headers, no attempt to align the bottom of columns.

- `landscape` – *(deprecated)* sets the whole document on landscape paper.

- `usenatbib` – *(all papers should use this)* this uses Patrick Daly’s `natbib.sty` package for citations.

- `usegraphicx` – *(most papers will need this)* includes the `graphicx` package, for inclusion of figures and images.

- `useAMS` – adds support for upright Greek characters `\upi`, `\umu` and `\upartial` ($\upi$, $\umu$ and $\upartial$). Only these three are included, if you require other symbols you will need to include the `amsmath` or `amsymb` packages (see section [11](#sec:packages)).

- `usedcolumn` – includes the package `dcolumn`, which includes two new types of column alignment for use in tables.

Some of these options are deprecated and retained for backwards compatibility only. Others are used in almost all papers, but again are retained as options to ensure that papers written decades ago will continue to compile without problems. If you want to include any other packages, see section [11](#sec:packages).

# Title page

If you are using `mnras_template.tex` the necessary code for generating the title page, headers and footers is already present. Simply edit the title, author list, institutions, abstract and keywords as described below.

## Title

There are two forms of the title: the full version used on the first page, and a short version which is used in the header of other odd-numbered pages (the ‘running head’). Enter them with `\title[]{}` like this:

    \title[Running head]{Full title of the paper}

The full title can be multiple lines (use `\\` to start a new line) and may be as long as necessary, although we encourage authors to use concise titles. The running head must be $\le~45$ characters on a single line.

See appendix [13](#sec:advanced) for more complicated examples.

## Authors and institutions

Like the title, there are two forms of author list: the full version which appears on the title page, and a short form which appears in the header of the even-numbered pages. Enter them using the `\author[]{}` command.

If the author list is more than one line long, start a new line using `\newauthor`. Use `\\` to start the institution list. Affiliations for each author should be indicated with a superscript number, and correspond to the list of institutions below the author list.

For example, if I were to write a paper with two coauthors at another institution, one of whom also works at a third location:

    \author[K. T. Smith et al.]{
    Keith T. Smith,$^{1}$
    A. N. Other,$^{2}$
    and Third Author$^{2,3}$
    \\
    $^{1}$Affiliation 1\\
    $^{2}$Affiliation 2\\
    $^{3}$Affiliation 3}

Affiliations should be in the format ‘Department, Institution, Street Address, City and Postal Code, Country’.

Email addresses can be inserted with the `\thanks{}` command which adds a title page footnote. If you want to list more than one email, put them all in the same `\thanks` and use `\footnotemark[]` to refer to the same footnote multiple times. Present addresses (if different to those where the work was performed) can also be added with a `\thanks` command.

## Abstract and keywords

The abstract is entered in an `abstract` environment:

    \begin{abstract}
    The abstract of the paper.
    \end{abstract}

Note that there is a word limit on the length of abstracts. For the current word limit, see the journal instructions to authors$^{\ref{foot:itas}}$.

Immediately following the abstract, a set of keywords is entered in a `keywords` environment:

    \begin{keywords}
    keyword 1 -- keyword 2 -- keyword 3
    \end{keywords}

There is a list of permitted keywords, which is agreed between all the major astronomy journals and revised every few years. Do *not* make up new keywords! For the current list of allowed keywords, see the journal’s instructions to authors$^{\ref{foot:itas}}$.

# Sections and lists

Sections and lists are generally the same as in the standard LaTeX classes.

## Sections

Sections are entered in the usual way, using `\section{}` and its variants. It is possible to nest up to four section levels:

    \section{Main section}
     \subsection{Subsection}
      \subsubsection{Subsubsection}
       \paragraph{Lowest level section}

The other LaTeX sectioning commands `\part`, `\chapter` and `\subparagraph{}` are deprecated and should not be used.

Some sections are not numbered as part of journal style (e.g. the Acknowledgements). To insert an unnumbered section use the ‘starred’ version of the command: `\section*{}`.

See appendix [13](#sec:advanced) for more complicated examples.

## Lists

Two forms of lists can be used in MNRAS – numbered and unnumbered.

For a numbered list, use the `enumerate` environment:

    \begin{enumerate}
     \item First item
     \item Second item
     \item etc.
    \end{enumerate}

which produces

1.  First item

2.  Second item

3.  etc.

Note that the list uses lowercase Roman numerals, rather than the LaTeX default Arabic numerals.

For an unnumbered list, use the `description` environment without the optional argument:

    \begin{description}
     \item First item
     \item Second item
     \item etc.
    \end{description}

which produces

First item

Second item

etc.

Bulleted lists using the `itemize` environment should not be used in MNRAS; it is retained for backwards compatibility only.

# Mathematics and symbols

The MNRAS class mostly adopts standard LaTeX handling of mathematics, which is briefly summarised here. See also section [11](#sec:packages) for packages that support more advanced mathematics.

Mathematics can be inserted into the running text using the syntax `$1+1=2$`, which produces $1+1=2$. Use this only for short expressions or when referring to mathematical quantities; equations should be entered as described below.

## Equations

Equations should be entered using the `equation` environment, which automatically numbers them:

    \begin{equation}
     a^2=b^2+c^2
    \end{equation}

which produces $$\begin{equation}
 a^2=b^2+c^2
\end{equation}$$

By default, the equations are numbered sequentially throughout the whole paper. If a paper has a large number of equations, it may be better to number them by section (2.1, 2.2 etc.). To do this, add the command `\numberwithin{equation}{section}` to the preamble.

It is also possible to produce un-numbered equations by using the LaTeX built-in `\[``\]` and `$$``$$` commands; however MNRAS requires that all equations are numbered, so these commands should be avoided.

## Special symbols

| Command                | Output    | Meaning                  |
|:-----------------------|:----------|:-------------------------|
| `\ensuremath{\odot}`   | $\odot$   | Sun, solar               |
| `\ensuremath{\oplus}`  | $\oplus$  | Earth, terrestrial       |
| `\ensuremath{\mu}m`    | $\mu$m    | microns                  |
| `\ensuremath{^\circ}`  | $^\circ$  | degrees                  |
| `\ensuremath{`         | $'$       | arcminutes               |
| `\ensuremath{`’        | $''$      | arcseconds               |
| `\ensuremath{^\circ}`  | $^\circ$  | fraction of a degree     |
| `\ensuremath{`         | $'$       | fraction of an arcminute |
| `\ensuremath{`’        | $''$      | fraction of an arcsecond |
| `d`                    | d         | fraction of a day        |
| `h`                    | h         | fraction of an hour      |
| `m`                    | m         | fraction of a minute     |
| `s`                    | s         | fraction of a second     |
| ``                     |           | fraction of a period     |
| `\diameter`            |           | diameter                 |
| `\ensuremath{\square}` | $\square$ | square, Q.E.D.           |

: Additional commands for special symbols commonly used in astronomy. These can be used anywhere.

| Command | Output | Meaning |
|:---|:---|:---|
| `\upi` | $\upi$ | upright pi |
| `\umu` | $\umu$ | upright mu |
| `\upartial` | $\upartial$ | upright partial derivative |
| `\lid` | $\lid$ | less than or equal to |
| `\gid` | $\gid$ | greater than or equal to |
| `\ensuremath{\lesssim}` | $\ensuremath{\lesssim}$ | less than of order |
| `\ensuremath{\gtrsim}` | $\ensuremath{\gtrsim}$ | greater than of order |
| `\loa` | $\loa$ | less than approximately |
| `\goa` | $\goa$ | greater than approximately |
| `\cor` | $\cor$ | corresponds to |
| `\sol` | $\sol$ | similar to or less than |
| `\sog` | $\sog$ | similar to or greater than |
| `\lse` | $\lse$ | less than or homotopic to |
| `\gse` | $\gse$ | greater than or homotopic to |
| `\getsto` | $\getsto$ | from over to |
| `\grole` | $\grole$ | greater over less |
| `\leogr` | $\leogr$ | less over greater |

: Additional commands for mathematical symbols. These can only be used in maths mode.

Some additional symbols of common use in astronomy have been added in the MNRAS class. These are shown in tables [1](#tab:anysymbols)–[2](#tab:mathssymbols). The command names are – as far as possible – the same as those used in other major astronomy journals.

Many other mathematical symbols are also available, either built into LaTeX or via additional packages. If you want to insert a specific symbol but don’t know the LaTeX command, we recommend using the Detexify website[^6].

Sometimes font or coding limitations mean a symbol may not get smaller when used in sub- or superscripts, and will therefore be displayed at the wrong size. There is no need to worry about this as it will be corrected by the typesetter during production.

To produce bold symbols in mathematics, use `\bmath` for simple variables, and the `bm` package for more complex symbols (see section [11](#sec:packages)). Vectors are set in bold italic, using `\mathbfit{}`.

For matrices, use `\mathbfss{}` to produce a bold sans-serif font e.g. ; this works even outside maths mode, but not all symbols are available (e.g. Greek). For $\nabla$ (del, used in gradients, divergence etc.) use `$\nabla$`.

## Ions

A new ` ` command has been added to the class file, for the correct typesetting of ionisation states. For example, to typeset singly ionised calcium use `Ca ii`, which produces Ca ii.

# Figures and tables

Figures and tables (collectively called ‘floats’) are mostly the same as built into LaTeX.

## Basic examples

![](example)

Figures are inserted in the usual way using a `figure` environment and `\includegraphics`. The example Figure [1](#fig:example) was generated using the code:

    \begin{figure}
     \includegraphics[width=\columnwidth]{example}
     \caption{An example figure.}
     \label{fig:example}
    \end{figure}

|                |                          |                          |
|:---------------|:------------------------:|:------------------------:|
| Star           |           Mass           |        Luminosity        |
|                | $M_{\ensuremath{\odot}}$ | $L_{\ensuremath{\odot}}$ |
| Sun            |           1.00           |           1.00           |
| $\alpha$ Cen A |           1.10           |           1.52           |
| $\epsilon$ Eri |           0.82           |           0.34           |

: An example table.

The example Table [3](#tab:example) was generated using the code:

    \begin{table}
     \caption{An example table.}
     \label{tab:example}
     \begin{tabular}{lcc}
      \hline
      Star & Mass & Luminosity\\
       & $M_{\ensuremath{\odot}}$ & $L_{\ensuremath{\odot}}$\\
      \hline
      Sun & 1.00 & 1.00\\
      $\alpha$~Cen~A & 1.10 & 1.52\\
      $\epsilon$~Eri & 0.82 & 0.34\\
      \hline
     \end{tabular}
    \end{table}

## Captions and placement

Captions go *above* tables but *below* figures, as in the examples above.

The LaTeX float placement commands `[htbp]` are intentionally disabled. Layout of figures and tables will be adjusted by the publisher during the production process, so authors should not concern themselves with placement to avoid disappointment and wasted effort. Simply place the LaTeX code close to where the figure or table is first mentioned in the text and leave exact placement to the publishers.

By default a figure or table will occupy one column of the page. To produce a wider version which covers both columns, use the `figure*` or `table*` environment.

If a figure or table is too long to fit on a single page it can be split it into several parts. Create an additional figure or table which uses `\contcaption{}` instead of `\caption{}`. This will automatically correct the numbering and add ‘*continued*’ at the start of the caption.

|              |                          |                          |
|:-------------|:------------------------:|:------------------------:|
| Star         |           Mass           |        Luminosity        |
|              | $M_{\ensuremath{\odot}}$ | $L_{\ensuremath{\odot}}$ |
| $\tau$ Cet   |           0.78           |           0.52           |
| $\delta$ Pav |           0.99           |           1.22           |
| $\sigma$ Dra |           0.87           |           0.43           |

Table [4](#tab:continued) was generated using the code:

    \begin{table}
     \contcaption{A table continued from the previous one.}
     \label{tab:continued}
     \begin{tabular}{lcc}
      \hline
      Star & Mass & Luminosity\\
       & $M_{\ensuremath{\odot}}$ & $L_{\ensuremath{\odot}}$\\
      \hline
      $\tau$~Cet & 0.78 & 0.52\\
      $\delta$~Pav & 0.99 & 1.22\\
      $\sigma$~Dra & 0.87 & 0.43\\
      \hline
     \end{tabular}
    \end{table}

To produce a landscape figure or table, use the `pdflscape` package and the `landscape` environment. The landscape Table [5](#tab:landscape) was produced using the code:

    \begin{landscape}
     \begin{table}
      \caption{An example landscape table.}
      \label{tab:landscape}
      \begin{tabular}{cccccccccc}
        \hline
        Header & Header & ...\\
        Unit & Unit & ...\\
        \hline
        Data & Data & ...\\
        Data & Data & ...\\
        ...\\
        \hline
      \end{tabular}
     \end{table}
    \end{landscape}

Unfortunately this method will force a page break before the table appears. More complicated solutions are possible, but authors shouldn’t worry about this.

|        |        |        |        |        |        |        |        |        |        |
|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|
| Header | Header | Header | Header | Header | Header | Header | Header | Header | Header |
|  Unit  |  Unit  |  Unit  |  Unit  |  Unit  |  Unit  |  Unit  |  Unit  |  Unit  |  Unit  |
|  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |
|  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |
|  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |
|  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |
|  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |
|  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |
|  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |
|  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |  Data  |

: An example landscape table.

# References and citations

## Cross-referencing

The usual LaTeX commands `\label{}` and `\ref{}` can be used for cross-referencing within the same paper. We recommend that you use these whenever relevant, rather than writing out the section or figure numbers explicitly. This ensures that cross-references are updated whenever the numbering changes (e.g. during revision) and provides clickable links (if available in your compiler).

It is best to give each section, figure and table a logical label. For example, Table [2](#tab:mathssymbols) has the label `tab:mathssymbols`, whilst section [11](#sec:packages) has the label `sec:packages`. Add the label *after* the section or caption command, as in the examples in sections [6.1](#sec:sections) and [8](#sec:fig_table). Enter the cross-reference with a non-breaking space between the type of object and the number, like this: `see Figure~\ref{fig:example}`.

The `\autoref{}` command can be used to automatically fill out the type of object, saving on typing. It also causes the link to cover the whole phrase rather than just the number, but for that reason is only suitable for single cross-references rather than ranges. For example, `\autoref{tab:journal_abbr}` produces [\[tab:journal_abbr\]](#tab:journal_abbr).

## Citations

MNRAS uses the Harvard – author (year) – citation style, e.g. (cite: author2013). This is implemented in LaTeX via the `natbib` package, which in turn is included via the `usenatbib` package option (see section [4](#sec:options)), which should be used in all papers.

Each entry in the reference list has a ‘key’ (see section [9.3](#sec:ref_list)) which is used to generate citations. There are two basic `natbib` commands:

`(cite: key)` produces an in-text citation: (cite: author2013)

`(cite: key)` produces a bracketed (parenthetical) citation: (cite: author2013)

Citations will include clickable links to the relevant entry in the reference list, if supported by your LaTeX compiler.

| Command | Ouput | Note |
|:---|:---|:---|
| `(cite: key)` | (cite: smith2014) |  |
| `(cite: key)` | (cite: smith2014) |  |
| `(cite: key; key2)` | (cite: smith2014; jones2015) | Multiple papers |
| `(cite: key)` | (cite: smith2014) |  |
| `(cite: key)` | (cite: smith2014) |  |
| `(cite: key)` | (cite: smith2014) | For use with manual brackets |
| `(cite: key)` | (cite: smith2014) | If already cited in close proximity |
| `\defcitealias{key}{Paper~I}` |  | Define an alias (doesn’t work in floats) |
| `\citetalias{key}` |  |  |
| `\citepalias{key}` |  |  |

There are a number of other `natbib` commands which can be used for more complicated citations. The most commonly used ones are listed in Table [\[tab:natbib\]](#tab:natbib). For full guidance on their use, consult the `natbib` documentation[^7].

If a reference has several authors, `natbib` will automatically use ‘et al.’ if there are more than two authors. However, if a paper has exactly three authors, MNRAS style is to list all three on the first citation and use ‘et al.’ thereafter. If you are using BIBTeX (see section [9.3](#sec:ref_list)) then this is handled automatically. If not, the `` and `` commands can be used at the first citation to include all of the authors.

## The list of references

It is possible to enter references manually using the usual LaTeX commands, but we strongly encourage authors to use BIBTeX instead. BIBTeX ensures that the reference list is updated automatically as references are added or removed from the paper, puts them in the correct format, saves on typing, and the same reference file can be used for many different papers – saving time hunting down reference details. An MNRAS BIBTeX style file, `mnras.bst`, is distributed as part of this package. The rest of this section will assume you are using BIBTeX.

References are entered into a separate `.bib` file in standard BIBTeX formatting. This can be done manually, or there are several software packages which make editing the `.bib` file much easier. We particularly recommend JABREF[^8], which works on all major operating systems. BIBTeX entries can be obtained from the NASA Astrophysics Data System[^9] (ADS) by clicking on ‘Bibtex entry for this abstract’ on any entry. Simply copy this into your `.bib` file or into the ‘BibTeX source’ tab in JABREF.

Each entry in the `.bib` file must specify a unique ‘key’ to identify the paper, the format of which is up to the author. Simply cite it in the usual way, as described in section [9.2](#sec:cite), using the specified key. Compile the paper as usual, but add an extra step to run the `bibtex` command. Consult the documentation for your compiler or latex distribution.

Correct formatting of the reference list will be handled by BIBTeX in almost all cases, provided that the correct information was entered into the `.bib` file. Note that ADS entries are not always correct, particularly for older papers and conference proceedings, so may need to be edited. If in doubt, or if you are producing the reference list manually, see the MNRAS instructions to authors$^{\ref{foot:itas}}$ for the current guidelines on how to format the list of references.

# Appendices and online material

To start an appendix, simply place the `\appendix` command before the next `\section{}`. This will automatically adjust the section headings, figures, tables, and equations to reflect the fact that they are part of an appendix. It is only necessary to enter the `\appendix` command once – everything after that command is in an appendix. Remember that appendices should be placed *after* the list of references.

Unlike other astronomy class files, there are no special commands for online material. If your paper has any online material, it should be placed in a separate file. See our instructions to authors$^{\ref{foot:itas}}$ for guidance.

# Packages and custom commands

## Additional packages

Sometimes authors need to include additional LaTeX packages, which provide extra features. For example, the `bm` package provides extra bold maths symbols, whilst the `pdflscape` package adds support for landscape pages. Packages can be included by adding the `\usepackage{}` command to the preamble of the document (not the main body).

Please *only include packages which are actually used in the paper*, and include a comment to explain what each one does. This will assist the typesetters. If you are using `mnras_template.tex`, it includes a specific section for this purpose, near the start of the file with the header ’authors - place your own packages here’.

For example, to include `pdflscape`, use:

    \usepackage{pdflscape}  

Consult the documentation for that package for instructions on how to use the additional features.

## Custom commands

Authors should avoid duplicating or redefining commands which are already available in LaTeX or `mnras.cls`. However it may sometimes be necessary to introduce a custom command e.g. as a shortcut while writing the paper.

Please *only include commands which are actually used in the paper*, and include a comment to explain what each one does. This will assist the typesetters. Use `\newcommand`, *not* `\def`, as this will avoid accidentally overwriting existing commands. Place custom commands in the preamble of the document (not the main body). If you are using `mnras_template.tex`, it includes a specific section for this purpose, near the start of the file with the header ’authors - place your own commands here’.

As an example, a shortcut for the unit  km s$^{-1}$can be defined like this:

    \newcommand{\kms}{\,km\,s$^{-1}$}   

Velocities can then be written as e.g. `2.3\kms` which produces 2.3 km s$^{-1}$. Similar shortcuts can be used for frequently quoted object designations.

# Acknowledgements

This guide replaces an earlier one originally prepared by Cambridge University Press (CUP) in 1994, and last updated in 2002 by Blackwell Publishing. Some code segments are reproduced from, and some examples are based upon, that guide. The authors were: A. Woollatt, M. Reed, R. Mulvey, K. Matthews, D. Starling, Y. Yu, A. Richardson (all CUP), and Penny Smith, N. Thompson and Gregor Hutton (all Blackwell), whose work is gratefully acknowledged.

The accompanying BIBTeX style file was written by John Sleath, Tim Jenness and Norman Gray, without whom BIBTeX support would not have been possible.

Some special symbols in tables [1](#tab:anysymbols)–[2](#tab:mathssymbols) were taken from the Springer Verlag *Astronomy & Astrophysics* LaTeX class, with their permission.

KTS thanks Nelson Beebe (University of Utah) for helpful advice regarding CTAN.

99 (ref: author2013) Author A. N., 2013, Journal of Improbable Astronomy, 1, 1 (ref: jones2015) Jones C. D., 2015, Journal of Interesting Stuff, 17, 198 (ref: smith2014) Smith A. B., 2014, The Example Journal, 12, 345 (Paper I)

# Journal abbreviations

Abbreviations for cited journals can be accessed using the commands listed in table [\[tab:journal_abbr\]](#tab:journal_abbr). Although some of these may appear to be outdated or rarely cited, they have been selected to be compatible with the BIBTeX output by the NASA Astrophysics Data System$^{\ref{foot:ads}}$, commands used by other astronomy journals, and with additional entries for journals with non-standard abbreviations in MNRAS. For journals which are not on this list, see our instructions to authors$^{\ref{foot:itas}}$ for guidance on how to abbreviate titles.

@l@l@l@ Command & Output & Journal name\
`A&A` or `\astap` & A&A & Astronomy and Astrophysics$^a$\
`A&ARv` & A&ARv & The Astronomy and Astrophysics Review\
`A&AS` & A&AS & Astronomy and Astrophysics Supplement Series\
`\actaa` & & Acta Astronomica\
`\afz` & & Astrofizika\
`AJ` & AJ & The Astronomical Journal\
`\ao` or `\applopt` & & Applied Optics\
`\aplett` & & Astrophysics Letters\
`ApJ` & ApJ & The Astrophysical Journal\
`ApJL` or `\apjlett` & ApJL & The Astrophysical Journal Letters$^a$\
`ApJS` or `\apjsupp` & ApJS & The Astrophysical Journal Supplement Series\
`Ap&SS` & Ap&SS & Astrophysics and Space Science\
`ARA&A` & ARA&A & Annual Review of Astronomy and Astrophysics\
`\arep` & & Astronomy Reports$^b$\
`\aspc` & & Astronomical Society of the Pacific Conference Series\
`\azh` & & Astronomicheskii Zhurnal$^c$\
`BAAS` & BAAS & Bulletin of the American Astronomical Society\
`\bac` & & Bulletin of the Astronomical Institutes of Czechoslovakia\
`\bain` & & Bull. Astron. Inst. Netherlands\
`\caa` & & Chinese Astronomy and Astrophysics\
`\cjaa` & & Chinese Journal of Astronomy and Astrophysics\
`\fcp` & & Fundamentals of Cosmic Physics\
`\gca` & & Geochimica Cosmochimica Acta\
`\grl` & & Geophysics Research Letters\
`\iaucirc` & & International Astronomical Union Circulars\
`Icarus` & Icarus & Icarus\
`\japa` & & Journal of Astrophysics and Astronomy\
`JCAP` & JCAP & Journal of Cosmology and Astroparticle Physics\
`\jcp` & & Journal of Chemical Physics\
`\jgr` & & Journal of Geophysics Research\
`JQSRT` & JQSRT & Journal of Quantitiative Spectroscopy and Radiative Transfer\
`\jrasc` & & Journal of the Royal Astronomical Society of Canada\
`\memras` & & Memoirs of the Royal Astronomical Society\
`Mem. Soc. Astron. Italiana` & Mem. Soc. Astron. Italiana & Memoire della Societa Astronomica Italiana\
`\mnassa` & & Monthly Notes of the Astronomical Society of Southern Africa\
`MNRAS` & MNRAS & Monthly Notices of the Royal Astronomical Society$^a$\
`New A` & New A & New Astronomy\
`New A Rev.` & New A Rev. & New Astronomy Review\
`Nature` & Nature & Nature\
`\nphysa` & & Nuclear Physics A\
`\pra` & & Physical Review A: Atomic, molecular, and optical physics\
`\prb` & & Physical Review B: Condensed matter and materials physics\
`\prc` & & Physical Review C: Nuclear physics\
`Phys. Rev. D` & Phys. Rev. D & Physical Review D: Particles, fields, gravitation, and cosmology\
`\pre` & & Physical Review E: Statistical, nonlinear, and soft matter physics\
`\prl` & & Physical Review Letters\
`PASA` & PASA & Publications of the Astronomical Society of Australia\
`PASP` & PASP & Publications of the Astronomical Society of the Pacific\
`PASJ` & PASJ & Publications of the Astronomical Society of Japan\
`Phys. Rep.` & Phys. Rep. & Physics Reports\
`\physscr` & & Physica Scripta\
`\planss` & & Planetary and Space Science\
`Proc. SPIE` & Proc. SPIE & Proceedings of the Society of Photo-Optical Instrumentation Engineers\
`\rmxaa` & & Revista Mexicana de Astronomia y Astrofisica\
`QJRAS` & QJRAS & Quarterly Journal of the Royal Astronomical Society\
`\sci` & & Science\
`\skytel` & & Sky and Telescope\
`Sol. Phys.` & Sol. Phys. & Solar Physics\
`\sovast` & & Soviet Astronomy$^b$\
`Space Sci. Rev.` & Space Sci. Rev. & Space Science Reviews\
`ZAp` & ZAp & Zeitschrift fuer Astrophysik\
\
\
\

# Advanced formatting examples

Sometimes formatting doesn’t behave exactly as expected when used in titles or section headings, and must be modified to obtain the correct appearance. Generally the publishers can fix these problems during the typesetting process after a paper is accepted, but authors may wish to adjust these themselves to minimise the possibility of errors and/or for the benefit of the refereeing process. Below are some examples of output, followed by the LaTeX code which produces them.

Most mathematics and text formatting works as expected, but some commands might not be the correct size, bold or italic. If so they can be finessed by hand, as in the bold mathematics here:

    \title{\textit{Herschel} observations of galaxies at
     $\bm{\delta > 60\ensuremath{^\circ}}$}

Most fonts do not provide bold and italic versions of small capitals, so the ` ` command doesn’t produce the expected output in headings. The effect has to be ‘faked’ using font size commands, remembering that the running head is a different style:

    \title
    [Abundances in H\,{\normalsize \textit{II}} regions]
    {Abundances in H\,{\Large \textbf{II}} regions}

Complex mathematics can cause problems with links, so might require adding a less formatted short version of the heading:

    \section
    [Finding Mg II absorbers at z > 2]
    {Finding M\lowercase{g}\,{\sevensize II} absorbers
     at $\lowercase{\bm{z > 2}}$}

Using square brackets in headings can cause additional linking problems, which are solved by wrapping them in {}:

    \subsection
    [{[C II] 158$\umu$m emission}]
    {[C\,{\sevensize II}] 158$\bmath{\umu}$m
     emission}

Use `\text{}` (not `\rm`) for non-variables in mathematics, which preserves the formatting of the surrounding text. For the same reasons, use `\textit{}` for italics (not `\it`).

    \subsection{Measuring $\bm{T}_\text{eff}$ from
     \textit{Gaia} photometry}

# Additional commands for editors only

The following commands are available for the use of editors and production staff only. They should not be used (or modified in the template) by authors.

`\maketitle` inserts the title, authors and institution list in the correct formatting.

`\nokeywords` tidies up the spacing if there are no keywords, but authors should always enter at least one.

`\volume{}` sets the volume number (default is 000)

`\pagerange{}` sets the page range. The standard template generates this automatically, starting from 1.

`\bsp` adds the ‘This paper has been typeset’ comment at the end of the paper. The command name refers to Blackwell Science Publishing, who were the publishers at the time when MNRAS began accepting LaTeX submissions in 1993.

`\mniiiauth{}` used by the BIBTeX style to handle MNRAS style for citing papers with three authors. It should not be used manually.

`\eprint{}` used by the BIBTeX style for citing arXiv eprints.

`\doi{}` used by the BIBTeX style for citing Digital Object Identifiers.

[^1]: Contact e-mail: <mn@ras.org.uk>

[^2]: Present address: Science magazine, AAAS Science International, 82-88 Hills Road, Cambridge CB2 1LQ, UK

[^3]: <https://en.wikibooks.org/wiki/LaTeX>

[^4]: <http://www.oxfordjournals.org/our_journals/mnras/for_authors/>

[^5]: <http://www.ctan.org/tex-archive/macros/latex/contrib/mnras>

[^6]: <http://detexify.kirelabs.org>

[^7]: <http://www.ctan.org/pkg/natbib>

[^8]: <http://jabref.sourceforge.net/>

[^9]: <http://adsabs.harvard.edu>

</paper>

Write the methods card for this paper.