# CrewAI basic financial news sentiment analyzer

This project uses the CrewAI framework to create a team of AI agents that attempt to analyze the recent news sentiment surrounding a specific publicly traded stock. The crew finds recent news articles, assesses the sentiment of each regarding the company, aggregates the findings, identifies key themes, and compiles a summary brief.

**🚨🚨 CRITICAL WARNING & DISCLAIMER 🚨🚨**

**This tool is highly experimental and provides automated analysis for INFORMATIONAL PURPOSES ONLY.**

*   **IT IS ABSOLUTELY NOT FINANCIAL OR INVESTMENT ADVICE.**
*   The sentiment analysis is based on AI interpretation of news text and can be **highly inaccurate, incomplete, biased, or misinterpreted.** Financial news is complex and nuanced.
*   Market sentiment is volatile and can change instantly. This analysis is only a snapshot based on limited, recent articles found by the tool.
*   **DO NOT** make any investment decisions based on the output of this tool.
*   You **MUST** conduct your own thorough research and consult with a **qualified, independent financial advisor** before making any investment decisions.
*   Use of this tool is entirely at your own risk. The creators assume **NO LIABILITY** whatsoever for any actions taken or decisions made based on its output.

## Features

*   **News aggregation:** Finds recent news articles related to a specified stock ticker using web search.
*   **Sentiment analysis:** Attempts to classify the sentiment (positive, negative, neutral) of each news item specifically concerning the company.
*   **Sentiment aggregation:** Calculates the overall distribution of sentiment across the analyzed articles.
*   **Theme extraction:** Tries to identify key topics driving the observed sentiment.
*   **Summary reporting:** Compiles the findings into a brief report, including **mandatory disclaimers**.

## Requirements

*   Python 3.9+
*   Google Colab environment (recommended) or a local Python setup.
*   **API Keys:**
    *   **OpenAI API key:** Required for the language model (GPT-4 Turbo strongly recommended for better analysis nuance). Needs a **funded account** or active credits from [platform.openai.com](https://platform.openai.com/).
    *   **Serper API key:** Required for the `NewsFinder` agent's web search via `SerperDevTool`. Get one from [serper.dev](https://serper.dev/) (free tier available).

## Setup (Google Colab)

1.  **Get the notebook:** Clone the repository or download the `.ipynb` file.
2.  **Open in Colab:** Upload and open the notebook in Google Colab ([colab.research.google.com](https://colab.research.google.com/)).
3.  **Install libraries:** Run the first cell (`# @title 1. Install...`) to install dependencies.
4.  **Configure API keys in Colab secrets:**
    *   Open Colab secrets (Key icon `<>` left sidebar).
    *   Enable "Notebook access".
    *   Add two secrets:
        *   Name: `OPENAI_API_KEY` | Value: Your OpenAI key (`sk-...`)
        *   Name: `SERPER_API_KEY` | Value: Your Serper key
    *   Ensure the toggle switch is **ON** for both secrets.
5.  **Run Cell 2:** Execute the second cell (`# @title 2. Import Modules...`). Check the output carefully to ensure both API keys were found. Fix errors before proceeding.

## How to use

1.  **Define stock ticker (Cell 3):**
    *   Go to Cell 3 (`# @title 3. Define stock ticker...`).
    *   **Modify the `stock_ticker` variable** to the symbol you want to analyze (e.g., "MSFT", "TSLA").
    *   **Read and understand the CRITICAL DISCLAIMER** printed by this cell.
2.  **Select LLM (Optional - Cell 4):**
    *   Ensure GPT-4 Turbo is selected in Cell 4 for best (but still imperfect) results.
3.  **Run cells sequentially:** Execute the remaining cells (4 through 8) in order.
    *   Cell 5 defines the agents.
    *   Cell 6 defines the tasks.
    *   **Cell 7** creates the `Crew` and runs `kickoff()`. This is the main execution step, involving web searches and multiple LLM calls. It will take time and use API credits.
    *   **Cell 8** displays the final generated sentiment brief. **Pay close attention to the final disclaimer displayed.**

## Workflow overview

1.  **News finder (Task 1):** Searches for recent news about the ticker.
2.  **Article sentiment assessor (Task 2):** Classifies sentiment for each news item found.
3.  **Sentiment aggregator (Task 3):** Counts positive/negative/neutral results.
4.  **Key themes extractor (Task 4):** Identifies potential reasons for the sentiment.
5.  **Sentiment brief writer (Task 5):** Compiles the results into a report including strong disclaimers.

## Customization

*   **Ticker symbol:** Change the `stock_ticker` in Cell 3.
*   **Number of articles:** Modify the goal/description for `news_finder` (Agent 1) and `task_find_news` (Task 1) to fetch more/fewer articles.
*   **Sentiment criteria:** Adjust the prompts for `article_sentiment_assessor` (Agent 2 / Task 2) if you have more specific sentiment definitions (though this is difficult for LLMs).
*   **News sources:** Modify the search query implicitly or explicitly in the `news_finder` prompt if you want to target specific financial news sites (results depend on the search tool).

## Limitations & critical disclaimer (reiteration)

*   **NOT FINANCIAL ADVICE:** This tool is purely informational and experimental.
*   **Accuracy is limited:** Sentiment analysis by AI is imperfect, especially for complex financial topics. Results may be wrong.
*   **Bias:** News sources and the LLM itself can have biases influencing results.
*   **Oversimplification:** Reduces complex situations to simple positive/negative/neutral labels.
*   **Timeliness:** Based on *recent* news found at runtime; sentiment can change rapidly.
*   **Context is missing:** The tool doesn't understand the broader market, economic conditions, company fundamentals, or your personal financial situation.
*   **API costs:** Uses OpenAI API credits.
*   **Requires human expertise:** **Always consult a qualified financial advisor before making investment decisions.**
