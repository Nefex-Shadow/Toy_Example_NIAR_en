# SIHSUS - Internações por doenças respiratórias

Dataset for hospitalization by respiratory diseases, grouped by hospital
and months. Used in forecasting models for predicting hospitalizations based
on aggregated data from previous months.

#### Dataset Link
<!-- info: Provide a link to the dataset: -->
<!-- width: half -->
<https://github.com/Nefex-Shadow/Toy_Example_NIAR_en/blob/main/SIH_Data/Final_Table.zip>

#### Data Card Author(s)
<!-- info: Select **one role per** Data Card Author:

(Usage Note: Select the most appropriate choice to describe the author's role
in creating the Data Card.) -->
<!-- width: half -->
- **Luís Eduardo Limas Brito, NIAR:** Owner
- **Italo Rodrigues de Matos Avelar, NIAR:** Contributor
- **Ramon B. H. B.:** Manager

## Authorship

### Publishers

#### Publishing Organization(s)
<!-- scope: telescope -->
<!-- info: Provide the names of the institution or organization responsible
for publishing the dataset: -->
NIAR, UFMG

#### Industry Type(s)
<!-- scope: periscope -->
<!-- info: Select **all applicable** industry types to which the publishing
organizations belong: -->
- Academic - Tech

### Dataset Owners

#### Team(s)
<!-- scope: telescope -->
<!-- info: Provide the names of the groups or team(s) that own the dataset: -->
- NIAR, UFMG

#### Contact Detail(s)
<!-- scope: periscope -->
<!-- info: Provide pathways to contact dataset owners: -->
- **Dataset Owner(s):** Luís Eduardo Limas Brito
- **Affiliation:** NIAR, UFMG
- **Contact:** <lelimasbrito@gmail.com>

## Dataset Overview

#### Data Subject(s)
<!-- scope: telescope -->
<!-- info: Select ***all applicable**** subjects contained the dataset: -->
- Sensitive Data about people
- Non-Sensitive Data about people
- Data about places and objects
- Data about monthly happenings

#### Dataset Snapshot
<!-- scope: periscope -->
<!-- info: Provide a snapshot of the dataset:<br><br>(Use the additional notes
to include relevant information, considerations, and links to table(s) with
more detailed breakdowns.) -->
Category | Data
--- | ---
Size of Dataset | 128.6 MB
Number of Instances | 161584
Number of Fields | 113
Labeled Classes | 5
Number of Labels | 3651
Average Labeles Per Instance | 730.2
Algorithmic Labels | 1
Human Labels | 4

**Additional Notes:** The only algorithmic label is "hospital_size",
calculated based on monthly average of each hospital.

#### Content Description
<!-- scope: microscope -->
<!-- info: Provide a short description of the content in a data point: -->

Each data point holds an hospital accumulated statistics for a
given month and past months. Some statistics include total hospitalizations,
presence of different age, sex and race groups and total deaths.

### Sensitivity of Data

#### Sensitivity Type(s)
<!-- scope: telescope -->
<!-- info: Select ***all applicable*** data types present in the dataset: -->
- User Content
- User Metadata
- User Activity Data
- Health Data

#### Risk Type(s)
<!-- scope: telescope -->
<!-- info: Select **all applicable** risk types presenting from the
dataset: -->
- Indirect Risk

#### Supplemental Link(s)
<!-- scope: periscope -->
<!-- info: Provide link(s) for documentation pertaining to sensitive data in
the dataset: -->
**Link Name or Document Type:** <https://datasus.saude.gov.br/informacoes-de-saude-tabnet/>

#### Risk(s) and Mitigation(s)

Since all data is aggregated (there is no data on a individual),
and low monthly average hospitals were filtered out, all data is
a mesh of different people, making it impossible to trace information
of a single person.

### Dataset Version and Maintenance

#### Maintenance Status
<!-- scope: telescope -->
<!-- info: Select **one:** -->
**Limited Maintenance** - The data will not be updated,
but any technical issues will be addressed.

#### Version Details
<!-- scope: periscope -->
<!-- info: Provide details about **this** version of the dataset: -->
**Current Version:** 2.0

**Last Updated:** 02/2026

**Release Date:** 01/2026

#### Maintenance Plan
<!-- scope: microscope -->
<!-- info: Summarize the maintenance plan for the dataset:

Use additional notes to capture any other relevant information or
considerations. -->
No new versions will be created.

## Example of Data Points

#### Primary Data Modality
<!-- scope: telescope -->
<!-- info: Select **one**: -->
- Time Series

#### Data Fields
<!-- scope: microscope -->
<!-- info: List the fields in data points and their descriptions.

(Usage Note: Describe each field in a data point. Optionally use this to show
the example.) -->

Field Name | Field Value | Description
--- | --- | ---
year | Val | Current year
month | Val | Current month
CNES | Val | Hospital's national code
region | Val | State where hospital is located
quarter | Val | Quarter
time_index | Val | Time identifier (year x 12 + month)
sin_month | Val | Current month "cycle" (sin(2 x pi x month / 12))
cos_month | Val | Current month "cycle" (cos(2 x pi x month / 12))
hospital_size | Val | Hospital size (based on monthly average of hospitalizations)
J_count_lag1 | Val | Total hospitalizations 1 month ago
J00_06_share_lag1 | Val | Ratio of hospitalizations for type 0 to 6 of respiratory diseases (1 month ago)
J09_18_share_lag1 | Val | Ratio of hospitalizations for type 9 to 18 of respiratory diseases (1 month ago)
J20_22_share_lag1 | Val | Ratio of hospitalizations for type 20 to 22 of respiratory diseases (1 month ago)
J40_47_share_lag1 | Val | Ratio of hospitalizations for type 40 to 47 of respiratory diseases (1 month ago)
J_bucket_entropy_lag1 | Val | Shannon Entropy of the different type of respiratory diseases (1 month ago)
J_death_share_lag1 | Val | Ratio of deaths (1 month ago)
J_days_in_mean_lag1 | Val | Average of days stayed in the hospital by patients (1 month ago)
J_days_in_p90_lag1 | Val | Percentile (90) of days stayed in the hospital by patients (1 month ago)
J_uti_share_lag1 | Val | Ratio of people who went to ICU (UTI in portuguese) overall (1 month ago)
J_uti_days_mean_lag1 | Val | Average of days stayed in ICU (1 month ago)
J_val_tot_mean_lag1 | Val | Average of money spent per patient (1 month ago)
J_val_tot_p90_lag1 | Val | Percentile (90) of money spent per patient (1 month ago)
J_val_uti_share_lag1 | Val | Ratio of cases where money on ICU was spent (1 month ago)
J_sex_m_share_lag1 | Val | Ratio of male patients (1 month ago)
J_sex_f_share_lag1 | Val | Ratio of female patients (1 month ago)
J_age_60p_share_lag1 | Val | Ratio of elders (60 years old or higher) patients (1 month ago)
J_age_15_59_share_lag1 | Val | Ratio of 15 to 59 years old patients (1 month ago)
J_age_0_14_share_lag1 | Val | Ratio of newborns to 14 years old patients (1 month ago)
J_race_white_share_lag1 | Val | Ratio of white patients (1 month ago)
J_race_black_share_lag1 | Val | Ratio of black patients (1 month ago)
J_race_others_share_lag1 | Val | Ratio of patients from other ethnicities (1 month ago)
J_missing_race_share_lag1 | Val | Ratio of patients without identified ethnicity (1 month ago)
catchment_munic_unique_lag1 | Val | Number of counties where pacients come from (1 month ago)
catchment_top1_share_lag1 | Val | Highest ratio of a county (number of people from there) (1 month ago)
catchment_entropy_lag1 | Val | Shannon Entropy of counties' ratio (1 month ago)
catchment_outside_local_share_lag1 | Val | Ratio of people from outside the hospital's county (1 month ago)
J_missing_diag_sec_share_lag1 | Val | Ratio of cases missing a secondary diagnostic (1 month ago)
J_missing_proc_share_lag1 | Val | Ratio of cases missing information on performed procedure (1 month ago)
J_count_lag2 | Val | Total hospitalizations 2 months ago
J00_06_share_lag2 | Val | Ratio of hospitalizations for type 0 to 6 of respiratory diseases (2 months ago)
J09_18_share_lag2 | Val | Ratio of hospitalizations for type 9 to 18 of respiratory diseases (2 months ago)
J20_22_share_lag2 | Val | Ratio of hospitalizations for type 20 to 22 of respiratory diseases (2 months ago)
J40_47_share_lag2 | Val | Ratio of hospitalizations for type 40 to 47 of respiratory diseases (2 months ago)
J_bucket_entropy_lag2 | Val | Shannon Entropy of the different type of respiratory diseases (2 months ago)
J_count_lag3 | Val | Total hospitalizations 3 months ago
J00_06_share_lag3 | Val | Ratio of hospitalizations for type 0 to 6 of respiratory diseases (3 months ago)
J09_18_share_lag3 | Val | Ratio of hospitalizations for type 9 to 18 of respiratory diseases (3 months ago)
J20_22_share_lag3 | Val | Ratio of hospitalizations for type 20 to 22 of respiratory diseases (3 months ago)
J40_47_share_lag3 | Val | Ratio of hospitalizations for type 40 to 47 of respiratory diseases (3 months ago)
J_bucket_entropy_lag3 | Val | Shannon Entropy of the different type of respiratory diseases (3 months ago)
J_death_share_lag3 | Val | Ratio of deaths (3 months ago)
J_days_in_mean_lag3 | Val | Average of days stayed in the hospital by patients (3 months ago)
J_days_in_p90_lag3 | Val | Percentile (90) of days stayed in the hospital by patients (3 months ago)
J_uti_share_lag3 | Val | Ratio of people who went to ICU overall (3 months ago)
J_uti_days_mean_lag3 | Val | Average of days stayed in ICU (3 months ago)
J_val_tot_mean_lag3 | Val | Average of money spent per patient (3 months ago)
J_val_tot_p90_lag3 | Val | Percentile (90) of money spent per patient (3 months ago)
J_val_uti_share_lag3 | Val | Ratio of cases where money on ICU was spent (3 months ago)
J_sex_m_share_lag3 | Val | Ratio of male patients (3 months ago)
J_sex_f_share_lag3 | Val | Ratio of female patients (3 months ago)
J_age_60p_share_lag3 | Val | Ratio of elders (60 years old or higher) patients (3 months ago)
J_age_15_59_share_lag3 | Val | Ratio of 15 to 59 years old patients (3 months ago)
J_age_0_14_share_lag3 | Val | Ratio of newborns to 14 years old patients (3 months ago)
J_race_white_share_lag3 | Val | Ratio of white patients (3 months ago)
J_race_black_share_lag3 | Val | Ratio of black patients (3 months ago)
J_race_others_share_lag3 | Val | Ratio of patients from other ethnicities (3 months ago)
J_missing_race_share_lag3 | Val | Ratio of patients without identified ethnicity (3 months ago)
catchment_munic_unique_lag3 | Val | Number of counties where pacients come from (3 months ago)
catchment_top1_share_lag3 | Val | Highest ratio of a county (number of people from there) (3 months ago)
catchment_entropy_lag3 | Val | Shannon Entropy of counties' ratio (3 months ago)
catchment_outside_local_share_lag3 | Val | Ratio of people from outside the hospital's county (3 months ago)
J_missing_diag_sec_share_lag3 | Val | Ratio of cases missing a secondary diagnostic (3 months ago)
J_missing_proc_share_lag3 | Val | Ratio of cases missing information on performed procedure (3 months ago)
J_count_lag6 | Val | Total hospitalizations 6 months ago
J00_06_share_lag6 | Val | Ratio of hospitalizations for type 0 to 6 of respiratory diseases (6 months ago)
J09_18_share_lag6 | Val | Ratio of hospitalizations for type 9 to 18 of respiratory diseases (6 months ago)
J20_22_share_lag6 | Val | Ratio of hospitalizations for type 20 to 22 of respiratory diseases (6 months ago)
J40_47_share_lag6 | Val | Ratio of hospitalizations for type 40 to 47 of respiratory diseases (6 months ago)
J_bucket_entropy_lag6 | Val | Shannon Entropy of the different type of respiratory diseases (6 months ago)
J_count_lag12 | Val | Total hospitalizations 12 months ago
J00_06_share_lag12 | Val | Ratio of hospitalizations for type 0 to 6 of respiratory diseases (12 months ago)
J09_18_share_lag12 | Val | Ratio of hospitalizations for type 9 to 18 of respiratory diseases (12 months ago)
J20_22_share_lag12 | Val | Ratio of hospitalizations for type 20 to 22 of respiratory diseases (12 months ago)
J40_47_share_lag12 | Val | Ratio of hospitalizations for type 40 to 47 of respiratory diseases (12 months ago)
J_bucket_entropy_lag12 | Val | Shannon Entropy of the different type of respiratory diseases (12 months ago)
J_death_share_lag12 | Val | Ratio of deaths (12 months ago)
J_days_in_mean_lag12 | Val | Average of days stayed in the hospital by patients (12 months ago)
J_days_in_p90_lag12 | Val | Percentile (90) of days stayed in the hospital by patients (12 months ago)
J_uti_share_lag12 | Val | Ratio of people who went to ICU overall (12 months ago)
J_uti_days_mean_lag12 | Val | Average of days stayed in ICU (12 months ago)
J_val_tot_mean_lag12 | Val | Average of money spent per patient (12 months ago)
J_val_tot_p90_lag12 | Val | Percentile (90) of money spent per patient (12 months ago)
J_val_uti_share_lag12 | Val | Ratio of cases where money on ICU was spent (12 months ago)
J_sex_m_share_lag12 | Val | Ratio of male patients (12 months ago)
J_sex_f_share_lag12 | Val | Ratio of female patients (12 months ago)
J_age_60p_share_lag12 | Val | Ratio of elders (60 years old or higher) patients (12 months ago)
J_age_15_59_share_lag12 | Val | Ratio of 15 to 59 years old patients (12 months ago)
J_age_0_14_share_lag12 | Val | Ratio of newborns to 14 years old patients (12 months ago)
J_race_white_share_lag12 | Val | Ratio of white patients (12 months ago)
J_race_black_share_lag12 | Val | Ratio of black patients (12 months ago)
J_race_others_share_lag12 | Val | Ratio of patients from other ethnicities (12 months ago)
J_missing_race_share_lag12 | Val | Ratio of patients without identified ethnicity (12 months ago)
catchment_munic_unique_lag12 | Val | Number of counties where pacients come from (12 months ago)
catchment_top1_share_lag12 | Val | Highest ratio of a county (number of people from there) (12 months ago)
catchment_entropy_lag12 | Val | Shannon Entropy of counties' ratio (12 months ago)
catchment_outside_local_share_lag12 | Val | Ratio of people from outside the hospital's county (12 months ago)
J_missing_diag_sec_share_lag12 | Val | Ratio of cases missing a secondary diagnostic (12 months ago)
J_missing_proc_share_lag12 | Val | Ratio of cases missing information on performed procedure (12 months ago)
J_count_ma3_lag1 | Val | Average of total hospitalizations in the previous 3 months
J_count_ma6_lag1 | Val | Average of total hospitalizations in the previous 6 months
J_count_ma12_lag1 | Val | Average of total hospitalizations in the previous 12 months
J_growth_1m | Val | Difference in total hospitalizations from 2 months ago to 1 month ago
J_count | Val | Total hospitalizations in this month
J00_06_share_lag0 | Val | Ratio of hospitalizations for type 0 to 6 of respiratory diseases (current month)
J09_18_share_lag0 | Val | Ratio of hospitalizations for type 9 to 18 of respiratory diseases (current month)
J20_22_share_lag0 | Val | Ratio of hospitalizations for type 20 to 22 of respiratory diseases (current month)
J40_47_share_lag0 | Val | Ratio of hospitalizations for type 40 to 47 of respiratory diseases (current month)
J_bucket_entropy_lag0 | Val | Shannon Entropy of the different type of respiratory diseases (current month)
J_death_share_lag0 | Val | Ratio of deaths (current month)
J_days_in_mean_lag0 | Val | Average of days stayed in the hospital by patients (current month)
J_days_in_p90_lag0 | Val | Percentile (90) of days stayed in the hospital by patients (current month)
J_uti_share_lag0 | Val | Ratio of people who went to ICU overall (current month)
J_uti_days_mean_lag0 | Val | Average of days stayed in ICU (current month)
J_val_tot_mean_lag0 | Val | Average of money spent per patient (current month)
J_val_tot_p90_lag0 | Val | Percentile (90) of money spent per patient (current month)
J_val_uti_share_lag0 | Val | Ratio of cases where money on ICU was spent (current month)
J_sex_m_share_lag0 | Val | Ratio of male patients (current month)
J_sex_f_share_lag0 | Val | Ratio of female patients (current month)
J_age_60p_share_lag0 | Val | Ratio of elders (60 years old or higher) patients (current month)
J_age_15_59_share_lag0 | Val | Ratio of 15 to 59 years old patients (current month)
J_age_0_14_share_lag0 | Val | Ratio of newborns to 14 years old patients (current month)
J_race_white_share_lag0 | Val | Ratio of white patients (current month)
J_race_black_share_lag0 | Val | Ratio of black patients (current month)
J_race_others_share_lag0 | Val | Ratio of patients from other ethnicities (current month)
J_missing_race_share_lag0 | Val | Ratio of patients without identified ethnicity (current month)
catchment_munic_unique_lag0 | Val | Number of counties where pacients come from (current month)
catchment_top1_share_lag0 | Val | Highest ratio of a county (number of people from there) (current month)
catchment_entropy_lag0 | Val | Shannon Entropy of counties' ratio (current month)
catchment_outside_local_share_lag0 | Val | Ratio of people from outside the hospital's county (current month)
J_missing_diag_sec_share_lag0 | Val | Ratio of cases missing a secondary diagnostic (current month)
J_missing_proc_share_lag0 | Val | Ratio of cases missing information on performed procedure (current month)

**Above:** Values of last data point

## Motivations & Intentions

### Motivations

#### Purpose(s)
<!-- scope: telescope -->
<!-- info: Select **one**: -->
- Research

#### Domain(s) of Application
<!-- scope: periscope -->
<!-- info: Provide a list of key domains of application that the dataset has
been designed for:<br><br>(Usage Note: Use comma-separated keywords.) -->
For example: `Machine Learning`, `Computer Vision`, `Object Detection`.

`Machine Learning`, `Time-Series`

#### Motivating Factor(s)
<!-- scope: microscope -->
<!-- info: List the primary motivations for creating or curating this dataset:

(Usage Note: use this to describe the problem space and corresponding
motivations for the dataset.) -->

Usar dados reais para implementação de um modelo de previsão.

### Intended Use

#### Dataset Use(s)
<!-- scope: telescope -->
<!-- info: Select **one**: -->
- Safe for research use

#### Suitable Use Case(s)
<!-- scope: periscope -->
<!-- info: Summarize known suitable and intended use cases of this dataset.

Use additional notes to capture any specific patterns that readers should
look out for, or other relevant information or considerations. -->
**Suitable Use Case:** Modelo de previsão.

**Suitable Use Case:** Estudos de histórico de hospitais.

**Additional Notes:** Apenas hospitais cadastrados no dataSUS estão presentes.

#### Unsuitable Use Case(s)
<!-- scope: microscope -->
<!-- info: Summarize known unsuitable and unintended use cases of this dataset.

Use additional notes to capture any specific patterns that readers should look
out for, or other relevant information or considerations. -->
**Unsuitable Use Case:** Estudos em cima de casos específicos de um paciente individual.

**Additional Notes:** O dataset contém apenas informações agregadas,
sem conter casos isolados.

## Access

#### Access Type
<!-- scope: telescope -->
<!-- info: Select **one**: -->
- External - Open Access

## Provenance

### Collection

#### Method(s) Used
<!-- scope: telescope -->
<!-- info: Select **all applicable** methods used to collect data: -->
- Taken from other existing datasets

#### Methodology Detail(s)
<!-- scope: periscope -->
<!-- info: Provide a description of each collection method used.

Use additional notes to capture any other relevant information or
considerations.

(Usage Note: Duplicate and complete the following for collection method
type.) -->
**Collection Type**

**Source:** Conexão ftp disponibilizado pelo dataSUS.

**Link:** ftp.datasus.gov.br

**Dates of Collection:** [01 2022 - 11 2025]

**Primary modality of collection data:**

- Tabular Data

**Update Frequency for collected data:**

*Usage Note: Select one for this collection type.*

- Monthly

**Additional Notes:**

#### Source Description(s)
<!-- scope: microscope -->
<!-- info: Provide a description of each upstream source of data.

Use additional notes to capture any other relevant information or
considerations. -->
- Os arquivos usados foram encontrados dentro da pasta
"/dissemin/publicos/SIHSUS/200801_/Dados/".
- Apenas arquivos que começam com RD foram usados.
- Foram usados arquivos de 2022/01 até 2025/11.
- Exceção: Os arquivos RDAC2511.dbc e RDRR2511.dbc não estavam disponíveis
quando os dados foram coletados.

#### Collection Cadence
<!-- scope: telescope -->
<!-- info: Select **all applicable**: -->
**Static:** Data was collected once from single or multiple sources.

#### Data Processing
<!-- scope: microscope -->
<!-- info: Summarize how data from different sources or methods aggregated,
processed, or connected.

Use additional notes to capture any other
relevant information or considerations.

(Usage Note: Duplicate and complete the following for each source OR
collection method.) -->
**Description:** Os dados foram transformados para ".csv" e, em seguida, filtrados baseados em colunas de interesse. As colunas foram usadas para calcular valores agregados que são usados na tabela final. A tabela final, no entanto, junta os dados de um mês com valores de dados passados.

**Methods employed:** Foram usados cinco scripts (python) para o processamento.
Um transforma os arquivos de ".dbc" para ".dbf" e outro de ".dbf" para ".csv".
Um terceiro faz a filtragem das colunas (com valores de interesse) e
linhas (cujo diagnóstico começa com "J", ou seja,
diagnóstico de doença respiratória).
Um quarto faz os cálculos, agregando os valores de cada coluna pelo hospital e pelo mês.
Finalmente, um último agrupa os valores mensais com defasagens temporais,
assim preparando o dataset final usado para treinar o modelo.

**Tools or libraries:**

- pyreaddbc: <https://pypi.org/project/pyreaddbc/>
- dbfread: <https://pypi.org/project/dbfread/>
- pandas: <https://pandas.pydata.org/>
- numpy: <https://numpy.org/>
