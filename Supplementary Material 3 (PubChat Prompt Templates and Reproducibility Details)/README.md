# Supplementary Material 3 - PubChat Prompt Templates and Reproducibility Details

This folder contains the direct prompt templates sent to LLMs during the PubChat workflow. Each prompt template is stored as a separate Markdown file. Runtime placeholders such as `{user_query}`, `{abstract}`, `{scoring_criteria}`, `{attempt_number}`, `{target_language_instruction}`, and `{language_name}` are filled by PubChat during execution.

## Runtime Placeholder Definitions

The prompt files use braces to mark values that are populated automatically during execution. These placeholders are not additional instructions; they indicate where PubChat inserts the user query, article abstract, retrieval state, language setting, or scoring information before sending the prompt to the LLM.

| Placeholder | Runtime value |
|---|---|
| `{user_query}` | The original natural-language research question entered by the user. |
| `{abstract}` | The title/abstract text of the PubMed record being screened or extracted. |
| `{scoring_criteria}` | The query-specific five-level relevance criteria generated before screening. |
| `{attempt_number}` | The current retrieval or refinement round number. |
| `{failed_query}` | The previous PubMed Boolean query that requires refinement. |
| `{failed_query_length}` | Character length of the previous PubMed Boolean query. |
| `{previous_count}` | Number of articles retrieved in the previous search round. |
| `{current_results_count}` | Number of articles retrieved or screened at the current workflow step. |
| `{stage1_end}`, `{stage2_start}`, `{stage2_end}`, `{stage3_start}`, `{stage3_end}`, `{stage4_start}`, `{stage4_end}`, `{stage5_start}`, `{max_attempts}` | Round boundaries for the adaptive query-refinement stages. |
| `{very_low_threshold}`, `{low_threshold}`, `{mid_threshold1}`, `{mid_threshold2}`, `{high_threshold}` | Article-count thresholds used to select the next refinement strategy. |
| `{target_language_instruction}` | The language-control instruction inserted according to the selected output language. |
| `{language_name}` | The selected output language name. |
| `{field_key}` | Internal English key of the structured field to be completed. |
| `{field_display_name}` | Localized display name of the structured field. |
| `{localized_score_field_name}`, `{localized_study_type_field_name}`, `{localized_study_population_field_name}` | Localized field labels shown inside the extraction prompt. |
| `{first_display}`, `{second_display}` | The two candidate scores used in third-pass arbitration. |

## Runtime Language Instructions

For language-controlled prompts, `{target_language_instruction}` is populated from the selected output language before the prompt is sent to the LLM. The available language instructions are:

| Language | Runtime instruction |
|---|---|
| Chinese | Respond and output strictly in Chinese. |
| English | Please respond strictly in English for all outputs |
| Spanish | Respond and output strictly in Spanish. |
| French | Respond and output strictly in French. |
| Portuguese | Respond and output strictly in Portuguese. |
| Italian | Respond and output strictly in Italian. |
| German | Respond and output strictly in German. |
| Russian | Respond and output strictly in Russian. |

## File Inventory

| No. | File | Main role |
|---|---|---|
| 3.1 | [3.1 Five-Level Relevance Scoring Criteria Generation Prompt](3.1%20Five-Level%20Relevance%20Scoring%20Criteria%20Generation%20Prompt.md) | Generates query-specific five-level relevance criteria before screening begins. |
| 3.2 | [3.2 Embedding Query Core Prompt Template](3.2%20Embedding%20Query%20Core%20Prompt%20Template.md) | Converts the user query into an English semantic query for embedding-based pre-filtering. |
| 3.3 | [3.3 Initial PubMed Boolean Query Generation Prompt](3.3%20Initial%20PubMed%20Boolean%20Query%20Generation%20Prompt.md) | Generates the initial PubMed Boolean search expression. |
| 3.4.01 | [3.4.01 Adaptive PubMed Query Refinement Prompt - Synonym Expansion](3.4.01%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Synonym%20Expansion.md) | Adds synonyms and MeSH terms for core concepts during the first refinement stage. |
| 3.4.02 | [3.4.02 Adaptive PubMed Query Refinement Prompt - Instance Supplementation and Related Terms](3.4.02%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Instance%20Supplementation%20and%20Related%20Terms.md) | Adds concrete examples and related terms during the second refinement stage. |
| 3.4.03 | [3.4.03 Adaptive PubMed Query Refinement Prompt - Diagnosis and Adjustment](3.4.03%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Diagnosis%20and%20Adjustment.md) | Diagnoses Boolean logic, missing examples, and conceptual scope before adjustment. |
| 3.4.04 | [3.4.04 Adaptive PubMed Query Refinement Prompt - Related Term Deepening](3.4.04%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Related%20Term%20Deepening.md) | Adds additional related terms when retrieval volume is moderate. |
| 3.4.05 | [3.4.05 Adaptive PubMed Query Refinement Prompt - Conservative Synonym Expansion](3.4.05%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Conservative%20Synonym%20Expansion.md) | Conservatively adds missing core synonyms when retrieval volume is already high. |
| 3.4.06 | [3.4.06 Adaptive PubMed Query Refinement Prompt - Continued Diagnosis and Deep Upward Expansion](3.4.06%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Continued%20Diagnosis%20and%20Deep%20Upward%20Expansion.md) | Continues diagnostic correction and performs deeper upward expansion when retrieval remains low. |
| 3.4.07 | [3.4.07 Adaptive PubMed Query Refinement Prompt - Deep Related Term Expansion](3.4.07%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Deep%20Related%20Term%20Expansion.md) | Broadens the query through deeper related methods, applications, populations, and outcomes. |
| 3.4.08 | [3.4.08 Adaptive PubMed Query Refinement Prompt - Strategic Narrowing and Conservative Refinement](3.4.08%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Strategic%20Narrowing%20and%20Conservative%20Refinement.md) | Applies strategic narrowing and conservative refinement when Stage 4 retrieval volume is already high. |
| 3.4.09 | [3.4.09 Adaptive PubMed Query Refinement Prompt - Forced Maximum Upward Expansion](3.4.09%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Forced%20Maximum%20Upward%20Expansion.md) | Forces maximum upward expansion when the retrieved article count is critically low. |
| 3.4.10 | [3.4.10 Adaptive PubMed Query Refinement Prompt - Conservative Synonym Expansion](3.4.10%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Conservative%20Synonym%20Expansion.md) | Conservatively adds missing core synonyms during the final refinement stage. |
| 3.4.11 | [3.4.11 Adaptive PubMed Query Refinement Prompt - Syntax and Structure Optimization](3.4.11%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Syntax%20and%20Structure%20Optimization.md) | Optimizes Boolean syntax, field tags, nesting, and query structure. |
| 3.4.12 | [3.4.12 Adaptive PubMed Query Refinement Prompt - Forced Query Simplification](3.4.12%20Adaptive%20PubMed%20Query%20Refinement%20Prompt%20-%20Forced%20Query%20Simplification.md) | Simplifies overly long PubMed Boolean queries when the query length exceeds 1,500 characters. |
| 3.5 | [3.5 Article Information Extraction and First-Pass Relevance Scoring Prompt](3.5%20Article%20Information%20Extraction%20and%20First-Pass%20Relevance%20Scoring%20Prompt.md) | Extracts structured article fields and assigns the first relevance score. |
| 3.6 | [3.6 Single-Field Completion Prompt](3.6%20Single-Field%20Completion%20Prompt.md) | Completes missing structured fields from an abstract. |
| 3.7 | [3.7 Second Independent Relevance Scoring Prompt](3.7%20Second%20Independent%20Relevance%20Scoring%20Prompt.md) | Performs the second independent blind relevance score. |
| 3.8 | [3.8 Third-Pass Score Arbitration Prompt](3.8%20Third-Pass%20Score%20Arbitration%20Prompt.md) | Resolves disagreement between first and second scores. |
