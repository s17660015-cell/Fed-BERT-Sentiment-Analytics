# Fed-BERT: Quantifying Central Bank Sentiment via NLP

### Project Overview
Global macro trading strategies rely heavily on interpreting the "tone" of Federal Reserve policy. This project implements a **Natural Language Processing (NLP)** pipeline using the **BERT Transformer architecture** (specifically `FinBERT`) to quantify the sentiment of FOMC statements from 2022 to 2024.

By mapping soft-max probability outputs to a custom "Hawk-Dove Index," this engine visualizes the shift in monetary policy regimes without human bias.

### Key Output
**The Hawk-Dove Sentiment Index (2022–2024)**
![Sentiment Chart](Fed_Sentiment_Analysis.png)
*(Figure 1: Visualizing the Fed's pivot. Red bars indicate "Hawkish" (restrictive) language during the hiking cycle; Green bars indicate the shift to "Dovish" (neutral/easing) language in late 2023.)*

### Methodology
1.  **Model Selection:** Utilized `ProsusAI/finbert`, a pre-trained Large Language Model (LLM) fine-tuned on financial 10-k filings to understand nuances in economic syntax (e.g., understanding that "lowering inflation" is positive).
2.  **Tokenization:** Applied BertTokenizer to parse unstructured FOMC text data.
3.  **Scoring Logic:** 
    *   Extracted raw logits from the model's final layer.
    *   Mapped `Negative` labels to **-1 (Hawkish/Rate Hike)**.
    *   Mapped `Positive` labels to **+1 (Dovish/Rate Cut)**.
    *   Mapped `Neutral` labels to **0**.

### Tech Stack
*   **Python 3.10**
*   **Hugging Face Transformers** (NLP Architecture)
*   **PyTorch** (Tensor computation)
*   **Seaborn/Matplotlib** (Data Visualization)
