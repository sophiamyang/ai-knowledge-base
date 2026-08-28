---
id: "aea0432a4a7f6a47"
title: "🔬“We have foundation models for language, not for physics” — Anima Anandkumar, Bren Professor of Computing"
aliases:
  - "🔬“We have foundation models for language, not for physics” — Anima Anandkumar, Bren Professor of Computing"
type: "resource"
source: "podcast"
source_name: "Latent Space"
content_type: "podcast"
speakers:
  - "Anima Anandkumar, Bren Professor of Computing"
url: "https://www.latent.space/p/anima"
origin: "https://api.substack.com/feed/podcast/1084089.rss"
published: "2026-08-26"
transcript_method: "mistral_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-28-podcast-we-have-foundation-models-for-language-not-for-physics-anima-anandkumar-bren-pro-aea0432a4a7f6a47.md"
created: "2026-08-28"
tags:
  - "topic/ai-for-science"
  - "topic/foundation-models"
  - "topic/model-training"
  - "topic/open-source-ai"
---

Raw transcript: [[raw_transcripts/2026-08-28-podcast-we-have-foundation-models-for-language-not-for-physics-anima-anandkumar-bren-pro-aea0432a4a7f6a47|🔬“We have foundation models for language, not for physics” — Anima Anandkumar, Bren Professor of Computing raw transcript]]

# 🔬“We have foundation models for language, not for physics” — Anima Anandkumar, Bren Professor of Computing

Source: podcast
Original link: https://www.latent.space/p/anima

## One-Sentence Takeaway
Foundation models for physics require embedding domain structure (e.g., geometry, conservation laws) rather than relying on scale alone, enabling accurate, efficient, and generalizable modeling of chaotic, multi-scale systems like weather and fusion.

## Short Summary
Anima Anandkumar argues that AI for physical systems (weather, fusion, fluid dynamics) cannot follow the scaling laws of language models due to data scarcity, resolution demands, and computational limits. Instead, her work on **Neural Operators**—particularly **Fourier Neural Operators**—combines data-driven learning with physics-informed constraints (e.g., spherical geometry, conservation laws) to achieve competitive accuracy at a fraction of the cost. FourCastNet, her open-source weather model, demonstrated this by matching traditional physics-based simulations while running on consumer GPUs, and ForecastNet 3 extended this to long-term climate modeling by incorporating Earth’s spherical geometry.

Her broader thesis is that the physical world’s inherent structure (e.g., non-local dependencies, multi-scale phenomena) allows AI to generalize from limited data, but only if architectures encode domain knowledge. She also explores **TorchLean**, a framework to formally verify neural networks (e.g., for robustness in control systems), bridging AI with mathematical proof systems like Lean.

## Featured Speakers
- Anima Anandkumar: Bren Professor of Computing at Caltech, Director of Machine Learning Research at NVIDIA, and co-founder of Accelerated Understanding

## Main Ideas
- **Physics-informed AI resists pure scaling**: Unlike language models, physical systems (e.g., weather, fusion) lack sufficient data (often <100K samples) and require resolutions (e.g., 1K³ grid points) that make transformers infeasible due to context length (hundreds of billions to trillions). Progress depends on embedding inductive biases (e.g., geometry, conservation laws) into architectures.
- **Neural Operators enable multi-scale, resolution-agnostic modeling**: Unlike standard neural networks (fixed input/output resolutions), Neural Operators model mappings between *function spaces*, allowing zoom-in/out to arbitrary resolutions. Fourier Neural Operators (FNOs) strike a balance between efficiency (quasi-linear complexity via Fourier transforms) and expressivity (non-linear layers) to capture non-local phenomena (e.g., atmospheric rivers, plasma disruptions).
- **Domain structure compensates for limited data**: The physical world’s latent structure (e.g., spherical harmonics for Earth, MHD equations for plasma) allows models to generalize from sparse data. For example, FourCastNet achieved near-parity with physics-based weather models using 50K samples, and fusion disruption prediction worked with only thousands of samples—both at speeds 10K–1M× faster than traditional simulations.
- **Foundation models for physics require unified architectures**: Traditional systems use separate models for short-term weather and long-term climate. ForecastNet 3 demonstrated that a single architecture (with spherical geometry) could handle both, suggesting a path to "foundation models for physics" that span phenomena and tasks (simulation, design, control).
- **Formal verification bridges AI and safety-critical systems**: TorchLean integrates neural networks with the Lean proof assistant, enabling formal verification of properties like certified robustness (e.g., bounds on output perturbations given input noise). This is critical for deploying AI in control loops (e.g., fusion reactors, drones) where safety and stability are paramount.

## Questions And Answers
- **Why can’t we use transformers for high-resolution physical systems?**
  A 1K×1K×1K×1K (3D space + time) grid would require a context length of ~10¹²–10¹⁸ tokens—far beyond feasible compute. Neural Operators avoid this by operating in function space (not discretized grids) and using efficient bases (e.g., Fourier, spherical harmonics).

- **How does FourCastNet achieve stability for long-term climate modeling?**
  By incorporating Earth’s spherical geometry (via spherical harmonics) and physics-informed constraints, the model avoids the blow-up seen in rectangular-grid architectures when rolled out for months/years. Each ensemble member respects physical laws, even if the ensemble average does not.

- **What’s the role of TorchLean in AI for science?**
  It allows writing neural networks in Lean (a proof assistant) and formally verifying properties like robustness bounds or finite-precision effects. For example, it can prove that a neural network in a fusion reactor’s control loop won’t exceed safety thresholds under input perturbations.

## Notable Details
- FourCastNet matched the accuracy of traditional weather models (e.g., ECMWF’s physics-based systems) while running **tens of thousands of times faster** on a single consumer GPU.
- ForecastNet 3 uses **spherical Fourier Neural Operators** to model Earth’s geometry, enabling stable rollouts for climate-scale predictions (months to years) from a model trained only on 6-hour steps.
- In fusion, Neural Operators predicted plasma disruptions with **~1M× speedup** over traditional MHD simulations, using only thousands of samples.
- Current weather/climate data resolution is ~0.25° (≈700×1000 grid points), but higher-resolution synthetic data could further improve models.
- **Ensemble prediction** for extreme events (e.g., hurricanes) requires probabilistic calibration. FourCastNet 3 explicitly trains for this, enabling risk assessment (e.g., landfall probabilities).
- **Open challenge**: Long-term rollouts still require guardrails (e.g., projecting to physically valid states) to prevent drift, even with spherical geometry.

## Actionable Takeaways
- For physical systems, prioritize architectures that encode domain knowledge (e.g., geometry, conservation laws) over brute-force scaling.
- Explore Neural Operators (or similar function-space models) for multi-scale, resolution-agnostic tasks where data is limited but structure is rich.
- Use spherical harmonics or other natural bases (e.g., Fourier for non-local phenomena) to stabilize long-horizon predictions.
- For safety-critical applications, integrate formal verification (e.g., TorchLean) to bound uncertainties and ensure robustness.
- Watch for advances in **physics-informed ensemble methods** to improve long-term stability in climate and other chaotic systems.

## People, Companies, Tools, And Links Mentioned
- Anima Anandkumar
- Caltech
- NVIDIA
- Amazon Web Services (AWS)
- FourCastNet
- ForecastNet 3
- Fourier Neural Operator (FNO)
- TorchLean
- Lean (proof assistant)
- ECMWF (European Centre for Medium-Range Weather Forecasts)
- ERA5 (ECMWF’s reanalysis dataset)
- Spherical Harmonics
- Crown (certified robustness algorithm)
- Allen Institute for AI
- [Latent Space podcast](https://www.latent.space/p/anima)

## Reading Priority

High – This conversation presents a rare, concrete blueprint for AI in physical sciences, combining novel architectures (Neural Operators), real-world deployments (weather/climate), and rigorous verification (TorchLean), with implications for fields from fusion to robotics.

## Connections

- Source: [[sources/Latent Space|Latent Space]]
- Topics: [[topics/AI For Science|AI For Science]], [[topics/Foundation Models|Foundation Models]], [[topics/Model Training|Model Training]], [[topics/Open Source AI|Open Source AI]]
- Speaker: [[people/anima-anandkumar|Anima Anandkumar]]
