# PROJECT NAME: Perplexity.ai RAG demo
## DESCRIPTION: Demo of a RAG (Retrieval-Augmented Generation) system based on Perplexity.ai's llms-full.txt file

This is a simple demo ("toy") Q&A system about Perplexity.ai. Using [Evidently AI's cloud platform](https://app.evidently.cloud), I derived 10 reference (ground truth) answers from Perplexity.ai's published [llms-full.txt](https://docs.perplexity.ai/llms-full.txt) file. Then I evaluated the system's generated answers by 2 criteria:
1. Whether they were faithful to the corresponding contexts from the source data (llms-full.txt)
2. Whether they contradicted the reference answers

The system and evaluations are adapted from the [6.2. Tutorial: Building and evaluating a RAG system](https://www.youtube.com/watch?v=jckp5R09Afg) ([GitHub](https://github.com/evidentlyai/community-examples/blob/main/learn/LLMCourse_RAG_Evals.ipynb)) tutorial (by course instructor Emeli Dral) from Evidently AI's free, hands-on [Applied course: LLM evaluation for builders](https://www.evidentlyai.com/llm-evaluation-course-practice) course.

![Evaluating a RAG QA System](.images/Evaluating%20a%20RAG%20QA%20System.gif)

## Here are the steps I used:

1. Download Perplexity.ai's [llms-full.txt](https://docs.perplexity.ai/llms-full.txt) file via the [llms.text directory](https://llmstxt.site/) ([GitHub](https://github.com/krish-adi/llmstxt-site)).

| Product | Website | llms-txt | llms-txt-tokens | llms-full.txt | llms-full.txt-tokens |
| :-- | :-- | :-- | :-- | :-- | :-- |
| Perplexity | perplexity.ai/ | docs.perplexity.ai/llms.txt | 510 | docs.perplexity.ai/llms-full.txt | 16583 |

2. From the downloaded copy of Perplexity.ai's [llms-full.txt](https://docs.perplexity.ai/llms-full.txt) file, generate a ground truth RAG dataset of 10 questions and answers, using [Evidently AI's platform](https://app.evidently.cloud).
Instructions for doing so are on the [Synthetic data: Generation: RAG evaluation dataset](https://docs.evidentlyai.com/synthetic-data/rag_data) page of [Evidently AI's documentation site](https://docs.evidentlyai.com).

[I created a dataset with context (for my reference), but then used a copy of that with the context removed as input to the next steps.]

3. Export a copy of the ground truth dataset for reference and safekeeping

4. Create a Python virtual environment
```
python -m venv .venv
```
and activate it.

5. Install 'ipykernel' into the Python environment, so that VS Code can run the code within the Jupyter notebook:
```
pip install ipykernel
```

6. Open the included Jupyter notebook, and set it to use your Python virtual environment<br>
[If you're using Microsoft VS Code, click the "kernel picker" in the notebook's upper right corner.]

7. Create a ".PRIVATE\\.env" file which defines the following environment variables:
- OPENAI_API_KEY="your_openai_api_key"            # From Open AI
- EVIDENTLY_API_KEY="your_evidently_ai_api_key"  # From the Evidently AI platform
- PROJECT_ID="your_project_id"                    # From the Evidently AI platform
- DATASET_ID="your_dataset_id"                    # From the Evidently AI platform

8. Within the Jupyter notebook, do the following:
- Restart Kernel
- Clear All Outputs
- Run All

9. Examine the results both in the Jupyter notebook and on the Evidently AI platform

10. Export a copy of the final dataset (containing ground truth, context, and evaluations) for reference and safekeeping