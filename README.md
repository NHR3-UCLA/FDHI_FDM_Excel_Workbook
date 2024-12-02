# Workbook Explanation
This Workbook implements four new Fault Displacement Models (FDMs) developed through the Fault Displacement Hazard Initiative (FDHI) research program at UCLA [(link)](https://www.risksciences.ucla.edu/nhr3/fdhi/home) using Deterministic and pseudo-Probabilistic methods in an Excel spreadsheet. 

The following FDMs are implemented herein:
- [Lavrentiadis & Abrahamson, 2023](#references)
- [Moss et al., 2024](#references)
- [Kuehn et al., 2024](#references)
- [Chiou et al., 2025](#references)


All users of this Workbook should review the Usage & Limitations below.

## Purpose & Intended Audience
The Workbook was created to accompany a presentation entitled *Probabilistic Fault Displacement Hazard Analysis Using New Predictive Displacement Models from the Fault Displacement Hazard Initiative Project* at the *International Workshop on Recent Advances in Seismic and Fault Displacement Hazard Assessment for Nuclear Installations*, hosted by the International Atomic Energy Agency (IAEA) June 18-21, 2024. 

The Workbook was recently updated to also compute deterministic displacements.

## Pseudo-Probabilistic Analysis
> [!IMPORTANT]  
> This Workbook provides a **simplified** probabilistic fault displacement hazard analysis (PFDHA) implementation to *demonstrate the key concept* of the PFDHA framework. 

The following simplifications are used herein to minimize the complexity of this Workbook and are a significant departure from the commonly accepted PFDHA state-of-practice:

- Only one earthquake magnitude is considered.
- The rate of earthquakes is based on balancing the seismic moment accumulation (e.g., based on slip rate) with the moment released in a single earthquake (Equation 2).
- The Probability of Surface Rupture (PSR) for the earthquake is based on the global [Wells & Coppersmith, 1993](#references) magnitude-dependent logistic regression model. This model may not be applicable to fault sources or seismogenic zones that are dissimilar to the empirical data used to develop the model.
- The surface rupture location is assumed to be exactly known and pass through the site of interest.

The simplified framework can be expressed as follows:

$$
\lambda(D > D_0) = \lambda_M \cdot P(SR \ne 0 \mid \mathbf{M}) \cdot P(D > D_0 \mid \mathbf{M}, \frac{x}{L}, \text{SOF})
$$

where:

- **$\lambda(D > D_0)$**: Annual frequency of earthquakes that produce displacement amplitude $D$ greater than a specified level of displacement $D_0$.
- **$\lambda_M$**: Annual rate of scenario earthquake.
- **$P(SR \ne 0 \mid \mathbf{M})$**: Probability that surface rupture $SR$ occurs anywhere in the scenario earthquake.
- **$P(D > D_0 \mid \mathbf{M}, \frac{x}{L}, \text{SOF})$**: Probability that displacement $D_0$ is exceeded for $\mathbf{M}$, $\frac{x}{L}$ scenario; based on the fault displacement model.
- **$\mathbf{M}$**: Earthquake moment magnitude.
- **$\frac{x}{L}$**: Normalized position along the rupture length.
- **SOF**: Style of faulting (mechanism).

The rate of earthquakes $\lambda_M$ is determined by:

$$
\lambda_M = \frac{\mu AS}{M_0(\mathbf{M})}
$$

where:

- **$\mu$**: Crustal shear modulus (3+E11 dyne/cm²).
- **$A$**: Rupture area estimated based on magnitude and mechanism using [Wells & Coppersmith, 1994](#references) relations, in cm².
- **$S$**: Fault slip rate in cm/yr.
- **$M_0(\mathbf{M})$**: Seismic moment of the earthquake in dyne-cm.

## Deterministic Analysis
Deterministic results are provided in two formats in the Workbook:
1. Probability of exceedance curves; i.e., $P(D > D_0 \mid \mathbf{M}, \frac{x}{L}, \text{SOF})$
2. Deterministic displacements for specific aleatory quantiles; i.e., $D$ such that $P(D \le z \mid \mathbf{M}, \frac{x}{L}, \text{SOF}) = q$

The deterministic results are generally consistent with the state-of-practice.

## Usage & Limitations
> [!CAUTION]  
> The **PFDHA results** (i.e., annual frequency of exceedance hazard curves) presented in this Workbook **should not be used** in professional applications. The assumptions and simplifications in this Workbook are not consistent with the current state-of-practice in PFDHA. For example, the current state-of-practice in PFDHA involves the following, at minimum:
> 
> - Evaluating multiple faults (if applicable).
> - Evaluating multiple magnitudes (i.e., an appropriate magnitude-frequency distribution).
> - "Floating" earthquakes along the fault system to account for the range of earthquake scenarios the fault system can produce (e.g., different magnitudes, rupture dimensions, and rupture locations).
> - Source-appropriate event probability of surface rupture models (e.g., based on rupture width and seismogenic thickness).
> - Inclusion of site probability of surface rupture model(s).

> [!NOTE] 
> The **PFDHA results** in this Workbook may be used to demonstrate the *general trends* of how hazard varies with earthquake magnitude, position along the rupture, slip rate, and inclusion/exclusion of a global conditional probability of surface rupture based on simple logistic regression.

> [!TIP]
> The **Deterministic results** in this Workbook **may be used** when scenario-specific rupture and site configurations (e.g., a specific magnitude $\mathbf{M}$ and location $\frac{x}{L}$) are of interest and appropriate for the application.

If you use this Workbook, please cite it using the following DOI: [![DOI](https://zenodo.org/badge/895202514.svg)](https://doi.org/10.5281/zenodo.14231829)

## Errors
The model calculations have been verified to the extent feasible. While the model developers assisted in the verification and implementation of the models, any errors are the sole responsibility of the Workbook author. Please contact the author if errors are found.

## License!
This project is licensed under the MIT License. See the [LICENSE](https://github.com/NHR3-UCLA/FDHI_FDM_Excel_Workbook/blob/main/LICENSE) file for details.

## Acknowledgments
Helpful discussions with the model developers, including support with calculations and implementation, is greatly appreciated. The UCLA Natural Hazards Risk and Resiliency Research Center at The B. John Garrick Institute for the Risk Sciences supported the development of this Workbook.

Financial support for the Fault Displacement Hazard Initiative (FDHI) research program from multiple sponsors, including the Pacific Gas \& Electric Company, California High-Speed Rail Authority, and California Energy Commission is greatly appreciated.

## References
- Chiou, B., Chen, R., Thomas, K., Milliner, C., Dawson, T., & Petersen, M. D. (2025). *Surface principal displacement model for strike-slip faults*. Earthquake Spectra, in review.
- Kuehn, N. M., Kottke, A. R., Sarmiento, A. C., Madugo, C., & Bozorgnia, Y. (2024). *A fault displacement model based on the FDHI Database*. Earthquake Spectra, in press, DOI: [10.1177/87552930241291077](https://doi.org/10.1177/87552930241291077).
- Lavrentiadis, G., & Abrahamson, N. (2023). *Fault-displacement models for aggregate and principal displacements*. Earthquake Spectra, Epub ahead of print, DOI: [10.1177/87552930231201531](https://doi.org/10.1177/87552930231201531).
- Moss, R. E. S., Thompson, S. C., Kuo, C.-H., Younesi, K., & Baumont, D. (2024). *New probabilistic fault displacement hazard models for reverse faulting*. Earthquake Spectra, Epub ahead of print, DOI: [10.1177/87552930241288560](https://doi.org/10.1177/87552930241288560).
- Wells, D. L., & Coppersmith, K. J. (1993). *Likelihood of surface rupture as a function of magnitude*. Seismological Research Letters, 64(1), 54.
- Wells, D. L., & Coppersmith, K. J. (1994). *New empirical relationships among magnitude, rupture length, rupture width, rupture area, and surface displacement*. Bulletin of the Seismological Society of America, 84(4), 974-1002.
