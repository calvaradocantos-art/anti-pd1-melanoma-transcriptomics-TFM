# Biomarcadores transcriptómicos asociados a la respuesta anti-PD-1 en melanoma

Este repositorio contiene el flujo de trabajo bioinformático reproducible desarrollado para el Trabajo Fin de Máster (TFM):

**Identificación de biomarcadores transcriptómicos asociados a respuesta a inmunoterapia anti-PD-1 en melanoma**

## Objetivo

El objetivo de este estudio fue identificar biomarcadores transcriptómicos candidatos asociados con la respuesta a la inmunoterapia anti-PD-1 en melanoma mediante el análisis de conjuntos de datos públicos de expresión génica.

## Conjuntos de datos

Se analizaron tres cohortes transcriptómicas independientes disponibles en Gene Expression Omnibus (GEO):

- **GSE91061:** cohorte de descubrimiento.
- **GSE78220:** cohorte para la evaluación de reproducibilidad y priorización de candidatos.
- **GSE145996:** cohorte para la evaluación externa retrospectiva *in silico*.

Las cohortes fueron procesadas y analizadas de forma independiente. Sus matrices de expresión no se fusionaron directamente debido a las diferencias existentes en el procesamiento de los datos y las unidades de expresión.

Los datos transcriptómicos originales no se redistribuyen en este repositorio, debido a que se encuentran disponibles públicamente en NCBI Gene Expression Omnibus (GEO).

## Flujo de análisis

El flujo de trabajo bioinformático comprende las siguientes etapas:

1. Obtención, limpieza y armonización de los metadatos.
2. Selección de muestras y control de calidad.
3. Filtrado de genes con baja expresión.
4. Análisis de expresión diferencial mediante DESeq2.
5. Análisis de componentes principales (PCA) y visualización exploratoria.
6. Análisis de enriquecimiento funcional mediante GO-BP, KEGG y GSEA.
7. Evaluación de la reproducibilidad de los genes candidatos entre cohortes.
8. Priorización de genes candidatos.
9. Construcción y congelación de una firma transcriptómica exploratoria de cinco genes.
10. Evaluación externa retrospectiva mediante la prueba de Wilcoxon-Mann-Whitney y análisis ROC/AUC.
11. Análisis de sensibilidad de la evaluación externa.

## Firma transcriptómica candidata

La firma transcriptómica exploratoria quedó constituida por cinco genes:

- FAM151A
- GP1BA
- SPIB
- NELL2
- FCER2

La composición de la firma fue definida antes de su aplicación en la cohorte externa GSE145996, con el propósito de evitar fuga de información (*data leakage*) y optimización *post hoc*.

La firma debe considerarse exploratoria y no debe interpretarse como un biomarcador predictivo clínicamente validado.

## Estructura del repositorio

```text
anti-pd1-melanoma-transcriptomics-TFM/
│
├── README.md
│
├── scripts/
│   └── Script TFM
│
├── metadata/
│   ├── META_CLEAN_GSE91061.csv
│   ├── META_EVAL_PATIENT_GSE78220.csv
│   ├── META_EXT_FINAL_GSE45996.csv
│   └── META_FINAL_GSE91061.csv
│
├── results/
│   ├── README.md
│   │
│   ├── differential_expression/
│   │   ├── GSE91061_DEGs_significativos.csv
│   │   └── GSE91061_DESeq2_resultados_completos.csv
│   │
│   ├── functional_enrichment/
│   │   ├── README.md
│   │   ├── GSEA_GO_BP_GSE91061.csv
│   │   ├── GSEA_GO_BP_significativos_GSE91061.csv
│   │   ├── GSEA_KEGG_GSE91061.csv
│   │   └── GSEA_KEGG_significativos_GSE91061.csv
│   │
│   ├── reproducibility/
│   │   ├── README.md
│   │   ├── candidate_reproducibility_GSE78220.csv
│   │   └── prioritized_genes_GSE78220.csv
│   │
│   └── external_evaluation/
│       ├── README.md
│       ├── GSE145996_evaluacion_principal_CRPR_vs_PD.csv
│       ├── GSE145996_scores_todos_pacientes.csv
│       ├── GSE145996_sensibilidad_CRPR_vs_SDPD.csv
│       └── firma_genica_congelada.csv
│
├── figures/
│   ├── README.md
│   ├── GSEA_GO_BP_GSE91061.png
│   ├── GSEA_KEGG_GSE91061.png
│   ├── PCA_GSE78220.png
│   ├── PCA_GSE91061.png
│   ├── ROC_GSE145996.png
│   ├── heatmap_DEGs_GSE91061.png
│   └── volcano_GSE91061.png
│
└── environment/
    ├── README.md
    └── sessionInfo_TFM.txt
