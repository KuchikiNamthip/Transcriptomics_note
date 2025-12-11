
# Gene Ontology (GO) Enrichment Analysis

## Reference

    clusterProfiler (version X.X.X)

    R package for functional enrichment analysis
    Reference: Yu et al., 2012, OMICS

## Code

## 🔍 **EXPLANATION OF EACH COLUMN IN THE OUTPUT**

Below is the accurate meaning of each column (based on the *clusterProfiler* manual) together with how researchers typically interpret them.

| Column          | Meaning                                                     | Interpretation                                                          |
| --------------- | ----------------------------------------------------------- | ----------------------------------------------------------------------- |
| **ID**          | GO term ID (e.g., GO:0008150)                               | Reference ontology identifier                                           |
| **Description** | Name of the GO term, e.g., *“apoptotic process”*            | Represents the biological meaning of the term                           |
| **GeneRatio**   | (significant genes ∩ GO term) / total significant genes     | Higher ratio = the term appears more frequently in your significant set |
| **BgRatio**     | (background genes ∩ GO term) / total background genes       | Baseline frequency of the term in the universe                          |
| **pvalue**      | Hypergeometric test p-value                                 | Probability of observing this enrichment by chance                      |
| **p.adjust**    | FDR-adjusted p-value (Benjamini–Hochberg)                   | This is the primary value used to determine significance                |
| **qvalue**      | Alternative FDR estimate (Storey method)                    | Usually p.adjust is preferred for decision-making                       |
| **geneID**      | Genes from the significant set that fall within the GO term | Stored as a string; can be split into a gene list                       |
| **Count**       | Number of genes from the significant set in the GO term     | Indicates how “solid” or well-supported the term is                     |

---

## 🌟 **INTERPRETING THE RESULTS — KEY POINTS**

### **1) High GeneRatio but low Count → weak evidence**

Example:

* GeneRatio = 2/10
* Count = 2

The proportion looks high, but the actual number of genes is small → less reliable.

### **2) Moderate GeneRatio but high Count → stronger evidence**

Example: Count ≥ 10
Indicates better biological support and more confidence.

### **3) p.adjust < 0.05 = significant**

Your cutoffs:

* `pvalueCutoff = 0.01`
* `qvalueCutoff = 0.05`

Therefore, the `ego` object contains **only significantly enriched GO terms** according to these thresholds.

### **4) readable = TRUE converts ENTREZID → SYMBOL**

This is excellent practice because:

* Gene lists are easier to read.
* Downstream annotation is more convenient.
