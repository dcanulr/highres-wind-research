# Conclusions {#sec-conclusions}
This thesis aimed to address critical gaps in understanding the multi-scale complexity of integrating wind energy in Mexico. It outlined specific objectives around three main contributions, each focused on different temporal and spatial scales. Different regions of Mexico were studied including those with higher wind resources as the Yucatan Peninsula and the Gulf of Tehuantepec, also those regions with complex orography as La Rumorosa and Puebla among others.

The first contribution analyzed the interaction between wind and solar renewable resources and the electrical demand of the Yucatan Peninsula. To capture the variability associated with both human activities and natural phenomena, data spanning several years were required. The analysis focused on demand patterns at daily, weekly, and monthly timescales, which are the most relevant for understanding the temporal dynamics of energy consumption. This approach provides a robust framework for optimizing renewable energy integration, addressing both the variability of resources and the temporal dynamics of demand. However, the proposed framework has some limitations. First, using a specific point to analyze wind and solar resources assumes homogeneity across the region, which may not fully reflect local variations in resource availability. A strategy to optimize the selection of sites, or a set of sites, could be implemented by incorporating technical constraints specific to the technologies. Additionally, the optimization method regarding the minimum distance between generated energy and electrical demand should be expanded to account for other electrical regions, allowing for broader generalization and applicability.

The second contribution bridges two temporal scales and sources of information. The proposed methodology leverages available experimental data to characterize turbulent fluctuations at high resolution, enhancing a lower-resolution reanalysis dataset. By identifying areas of effectiveness, the methodology demonstrates the homogeneity of wind resources in relation to terrain complexity. The enhancement of the meteorological model, incorporating variability from experimental observations, reduces uncertainty in wind energy assessments, resulting in more accurate resource evaluations. Nevertheless, the method relies on both the ERA5 reanalysis dataset and observational data. ERA5 has inherent biases that vary by region, and developing more accurate, corrected, and validated models would improve the results, especially when validated with reliable data from additional meteorological stations across Mexico. The restricted availability of high-quality measured data limits the methodology's application, not only to regions where observation towers are located but also to the temporal range of measurements. Expanding the geographical and temporal scope of the data could lead to more robust assessments, especially in underrepresented regions where complex terrain presents a significant challenge.

The final contribution evaluated the feasibility of floating wind turbine technology under the specific meteorological and oceanic conditions of the Gulf of Tehuantepec. First, these conditions were characterized using long-term regional reanalysis data. Then, high-frequency simulations were conducted to capture real-world variability, allowing for a detailed analysis of mechanical loads caused by wind and wave interactions with the turbine. The theoretical assessment of emerging technologies involves several assumptions, including the use of long-term reanalysis data to represent short-term variability, which may not capture rapid fluctuations or localized atmospheric phenomena that can significantly affect turbine behavior. Additionally, some physical forces acting on the floating platform and the turbine, such as nonlinear hydrodynamic effects, mooring line dynamics, or coupling between wave and current forces, may be simplified or neglected. Therefore, the results presented in this study should be considered preliminary recommendations to inform the design and deployment of new technologies. To validate the identified strengths and weaknesses, experimental testing of prototype devices in potential deployment zones should be considered a critical first step toward future integration.

The frameworks developed in this thesis address key challenges in diverse applications: integrating renewable sources into regional grids, improving meteorological models with region-specific physical characteristics, and assessing emerging technologies such as floating wind turbines to identify technical challenges for future deployment. These contributions not only advance academic understanding but also provide practical tools for policymakers and industry stakeholders, enabling more informed decision-making and sustainable energy planning.

## Future Research {#future-research .unnumbered}

This research opens new questions and opportunities for further
investigation. The continuous evolution of meteorological datasets, such
as the upcoming ECMWF reanalysis ERA6 with higher resolution, along with
advancements in simulation tools like the new version of OpenFAST with
improved solvers, presents an opportunity to refine and extend the
methodologies developed in this study, potentially leading to more
accurate results.

Long-term datasets provide an opportunity to analyze the impact of
climate change on wind resources, which is essential for understanding
the interaction between large-scale natural phenomena, such as
hurricanes and tropical storms, and wind energy technology. Analyzing
resource variability can help guide the development of strategies for
future wind energy planning and deployment.

To enhance the integration of renewable energy sources into the energy
mix, future studies could explore the complementarity between different
energy sources based on regional resource availability and electricity
demand. Additionally, incorporating solutions such as energy storage
could improve grid stability and reliability. Such analyses could also
be extended beyond Mexico to other regions, such as Latin America, where
diverse renewable energy potentials exist.

Offshore wind energy remains an emerging technology in Mexico, with no
concrete deployment plans despite its identified potential. Further
research is needed to refine technical assessments and conduct
specialized studies that evaluate not only turbine performance but also
broader implications, including environmental impact, grid integration,
and interactions with economic activities.

Finally, the automation of the presented frameworks could optimize
analysis by incorporating additional data sources and leveraging
advanced techniques such as machine learning and artificial
intelligence. However, it remains crucial to validate existing
meteorological models to ensure the availability of high-quality data
for training and analysis.
