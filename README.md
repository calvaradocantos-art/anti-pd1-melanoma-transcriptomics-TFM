# anti-pd1-melanoma-transcriptomics-TFM

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

Las cohortes fueron analizadas de forma independiente y sus matrices de expresión no se fusionaron directamente debido a las diferencias existentes en el procesamiento de los datos y las unidades de expresión.

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

## Firma transcriptómica candidata

La firma exploratoria está constituida por cinco genes:

- FAM151A
- GP1BA
- SPIB
- NELL2
- FCER2

La composición de la firma y sus parámetros fueron definidos antes de su aplicación en la cohorte externa GSE145996, con el propósito de evitar fuga de información (*data leakage*) y optimización *post hoc*.

Esta firma debe considerarse exploratoria y no debe interpretarse como un biomarcador predictivo clínicamente validado.

## Software

Todos los análisis se realizaron en R utilizando, entre otros, los siguientes paquetes:

- GEOquery
- DESeq2
- apeglm
- tidyverse
- AnnotationDbi
- org.Hs.eg.db
- clusterProfiler
- EnhancedVolcano
- pheatmap
- ggplot2
- readxl
- pROC

La versión exacta de R, las versiones de los paquetes y la información correspondiente al entorno computacional utilizado se encuentran documentadas en:

`environment/sessionInfo.txt`

## Reproducibilidad

El flujo de análisis puede reproducirse mediante el script:

`scripts/TFM_pipeline.R`

El repositorio también contiene metadatos procesados, resultados complementarios y figuras generadas durante los análisis.

Los conjuntos de datos transcriptómicos originales no se redistribuyen en este repositorio, debido a que se encuentran disponibles públicamente en NCBI Gene Expression Omnibus (GEO) mediante los siguientes números de acceso:

- GSE91061
- GSE78220
- GSE145996

## Estructura del repositorio

```text
.
├── README.md
├── LICENSE
├── CITATION.cff
├── scripts/
│   └── TFM_pipeline.R
├── metadata/
├── results/
│   ├── differential_expression/
│   ├── functional_enrichment/
│   ├── reproducibility/
│   └── external_evaluation/
├── figures/
└── environment/
    └── sessionInfo.txt
