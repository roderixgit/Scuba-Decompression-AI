# Scuba Decompression AI

Final project for the Building AI course

## Summary

This project uses artificial intelligence to improve scuba diving safety by optimizing decompression 
model parameters. It analyzes dive data and outcomes, including cases of Decompression sickness, to 
better understand how the body handles inert gases. The goal is to create more accurate and personalized 
ascent plans that reduce the risk of decompression related injuries.


## Background

Scuba diving relies on a variety of decompression models, many inspired by the work of Albert A. Bühlmann, 
each with different parameters, levels of conservatism, and complexity. This diversity makes it difficult 
for divers to understand which configuration best fits their physiology and dive conditions. 

Moreover, even advanced models cannot fully prevent cases of Decompression sickness, particularly mild 
incidents that can occur despite staying within recommended limits. These challenges highlight the need 
for a more adaptive, data driven approach to decompression planning.


## How is it used?

Modern dive computers rely on several types of decompression models. The most common are dissolved gas 
models based on the work of Albert A. Bühlmann (ZHL family), which simulate inert gas uptake and release 
across multiple tissue compartments and are often adjusted using gradient factors to control conservatism. 
Others use bubble models such as VPM or RGBM, which aim to limit the formation and growth of microbubbles 
during ascent, while some systems combine both approaches to balance realism and safety.

The AI tool could treat these model parameters, like tissue half times, gradient factors, and bubble related 
coefficients, as variables to be optimized. By analyzing large datasets of dive profiles and outcomes, it 
could learn how to tune these parameters for safer decompression. Importantly, it could also incorporate 
cases of Decompression sickness that occurred even when dives stayed within recommended limits, using this 
data to refine and enhance the models beyond their current assumptions and improve real world reliability.


## Data sources and AI methods

To train such an AI system, information about decompression models can be gathered from a mix of scientific 
literature, manufacturer documentation, and open source implementations. Foundational models, such as those 
derived from Albert A. Bühlmann, are well documented in academic papers and diving research, while variants 
like RGBM or VPM are described in technical reports and vendor materials. Although some implementations are 
proprietary, enough detail is publicly available to reconstruct their structure and identify key parameters 
(e.g., tissue compartments, gradient factors, bubble constraints).

Dive profile data can be obtained directly from dive computers, most of which allow log downloads via USB, 
Bluetooth, or mobile apps. These logs typically include depth over time, gas mixes, ascent rates, and 
temperature, and can be exported in standard or semi-standard formats (e.g., CSV or manufacturer specific 
formats). Aggregating such logs, either from individual divers, clubs, or shared repositories, provides the 
time series data needed to train and validate models.

In addition, diving organizations and research bodies are valuable partners. Training agencies and groups 
like Divers Alert Network (DAN) collect incident reports, conduct studies on diver health, and maintain 
large datasets on dive exposures and outcomes, including cases of Decompression sickness. These sources 
not only provide high quality data but also domain expertise to interpret results, validate assumptions, 
and ensure that any AI driven optimization remains grounded in established safety practices.

A good approach here isn’t a single model, but a hybrid AI strategy that combines physics based modeling 
with data driven learning.

Start with a model based foundation: treat existing decompression models (e.g., those derived from Albert 
A. Bühlmann or bubble models like VPM/RGBM) as the baseline. Instead of replacing them, use AI to learn 
optimal parameter adjustments, such as gradient factors, tissue half times, or bubble suppression terms. 
based on real dive data.

On top of that, use supervised learning to estimate risk. Train models (e.g., gradient boosting or neural 
networks) on dive profiles and outcomes to predict the probability of Decompression sickness. This gives 
you a data driven “risk layer” that can evaluate how safe a given ascent profile is.

Then, apply optimization or reinforcement learning:
- Use Bayesian optimization or evolutionary algorithms to tune model parameters globally.
- Use reinforcement learning to simulate dives and learn ascent strategies that minimize predicted risk 
while respecting constraints (e.g., time, gas usage).

A key strength of this setup is that it can learn from edge cases, especially dives that resulted in DCI 
despite staying within model limits, and adjust parameters to better reflect real world physiology.


## Challenges

A major challenge is data quality and completeness. Dive profiles from computers can be noisy, inconsistent 
between manufacturers, and missing important context such as exact gas switch timing or diver behavior. Even 
if large datasets are available, they may not be representative of all diving conditions, environments, or 
diver populations. This makes it difficult for any model to generalize reliably.

Another limitation is that the system still depends on underlying decompression theory. These models are 
simplifications of human physiology and cannot fully capture the complexity of gas exchange, microbubble 
formation, and individual variability. As a result, even an optimized model cannot guarantee the prevention 
of Decompression sickness, especially in edge cases.

A key constraint is that the model cannot account well for human physiological and behavioral factors, 
which are often critical in real world outcomes. 
Factors such as:
- fatigue or poor sleep
- dehydration or nutrition status
- stress or anxiety
- alcohol consumption
- illness or infection
- medication use

are typically not recorded in dive logs and are extremely difficult to quantify reliably. These variables 
can significantly influence decompression risk, but they are partially or entirely invisible to the model, 
making predictions inherently uncertain.


## What next?

The project will require contributions from machine learning engineers, decompression theory experts, and 
access to real world dive logs, potentially supported by organizations like Divers Alert Network (DAN). 

An open-source approach would be especially valuable, enabling shared datasets, transparent validation of 
models, and collaborative improvement of safety-critical algorithms.

The next steps in this project is to build a working dataset of dive profiles and implement a baseline 
decompression model that can be used as a reference for comparison. On top of this, an AI layer can be 
developed to learn from historical dive data and cases of Decompression sickness in order to optimize 
model parameters and improve risk prediction.


## Acknowledgments

Divers Alert Network (DAN) - One of the most important global sources of diving safety research. 
Collects diving accident and incident reports, runs physiological and decompression studies, publishes 
medical and safety research for the diving community.
Some data and reports are publicly available.

Diving Science and Technology Corporation (DSAT / PADI research arm legacy) - Conducts decompression and 
recreational diving safety studies, contributes to recreational dive table development, research informed 
modern dive computer algorithms. Some materials are publicly referenced through training agencies.

Gesellschaft für Tauch- und Überdruckmedizin (GTÜM) - GTÜM is the central scientific and medical society in 
Germany for diving medicine (Tauchsportmedizin), hyperbaric oxygen therapy (HBO / Überdruckmedizin), research 
on decompression physiology and safety, training and certification of diving physicians.


## Notes

Images generated using AI tools and included for illustrative purposes.
