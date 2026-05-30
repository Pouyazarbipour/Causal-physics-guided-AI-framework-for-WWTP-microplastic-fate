# Causal-Physics-Guided Environmental AI for WWTP Microplastics

This is a publication-oriented redesign of the original overtopping PINN-UQ script into a WWTP microplastic framework. It deliberately does not implement a PDE-residual PINN. The model combines causal discovery, physics-guided neural representation learning, counterfactual interventions, uncertainty quantification, and explainable AI.

## Required Dataset Columns

Continuous columns:

`PI1_HRR`, `PI2_TFAN`, `PI3_HLN`, `PI4_PFP`, `PI5_SIN`, `PI6_RTDN`, `PI7_CSSN`, `PI8_RHDN`, `PI9_PSN`, `PI10_MFN`, `PI11_NECN`, `PI12_PCMA`, `PI13_SCN`, `pH`

Categorical columns:

`Treatment_Process`, `Sampling_Point`, `Microplastic_Type`, `Particle_Color`, `Polymer_Type`

Targets and grouping:

`polymer_occurrence`, `polymer_fate_class`, `WWTP_ID`

## Run

```powershell
python run_wwtp_causal_pgnn.py --data path\to\microplastic_particles.csv --output wwtp_causal_pgnn_outputs --epochs 300 --folds 7
```

## Outputs

The run creates:

- `causal/weighted_adjacency.npy`
- `causal/causal_graph.json`
- `causal/learned_dag.png`
- `counterfactuals/intervention_ate_cate.csv`
- `uncertainty/fold_*_particle_predictions.csv`
- `explainability/permutation_importance.csv`
- `explainability/integrated_gradients.csv`
- `explainability/causal_vs_correlation_importance.csv`
- `tables/groupkfold_metrics.csv`
- `tables/summary_metrics.json`

## Scientific Framing

The framework is designed to answer:

What causal mechanisms govern polymer-specific transport in WWTPs?

What would happen if WWTP operational conditions were altered?

