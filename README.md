Real-Time Market Intelligence System
🚀 Indian Stock Market Tweet Scraping | NLP Signal Generation | Streaming ETL Pipeline

This project implements a complete end-to-end real-time market intelligence system to collect, process, and analyze social sentiment around the Indian stock market using Twitter/X — without paid APIs.
The system scrapes live discussions, cleans and processes text, generates quantitative sentiment signals using TF-IDF + feature engineering, and stores results in optimized Parquet format.

✨ Key Features
| Domain                   | Functionality                                                      |
| ------------------------ | ------------------------------------------------------------------ |
|   Data Collection        | Selenium-based scraper, deduplication, dynamic wait, anti-bot safe |
|   Market Scope           | #nifty50, #sensex, #intraday, #banknifty, #stocks                  |
|   Processing             | Cleaning, normalization, Unicode handling, rate limiting           |
|   Storage Format         | Date-partitioned Parquet + incremental streaming writes            |
|   NLP & ML               | TF-IDF Vectorization → composite sentiment signal                  |
|   Performance            | Lightweight processing, memory-optimized visualization             |
|   Logging & Monitoring   | Error recovery, debug logs, modular pipeline structure             |
|   Visualization          | Sample-based plotting for faster analytics                         |


Project Structure
real_time_market_intel/
├── README.md
├── requirements.txt
├── run_pipeline.py
├── setup.sh
├── scripts/
│   ├── scraper_selenium.py
│   ├── processor.py
│   ├── storage.py
│   ├── analyzer.py
│   └── visualize.py
├── utils/
│   ├── logging_config.py
│   └── helpers.py
├── samples/
│   ├── sample_tweets.parquet
│   └── sample_signals.parquet
└── docs/
    ├── technical_design.md
    ├── ARCHITECTURE.md
    └── architecture_diagram.png

    
🏗 Architecture Diagram

Pipeline Flow

  1. Scrape tweets in real time using Selenium
  2. Clean & normalize text
  3. Store to Parquet (date + batch partitioning)
  4. Convert text to TF-IDF vectors
  5.  Generate bullish/bearish market signal
  6.  Visualize aggregated sentiment

Installation & Setup

  Clone the Repository
  git clone https://github.com/USERNAME/real-time-market-intelligence.git
  cd real-time-market-intelligence
  
  Install Dependencies
  bash setup.sh
  source venv/bin/activate

  Run in Sample Mode
  python run_pipeline.py --mode sample

  Run Live Streaming Mode
  python run_pipeline.py --mode live --max-tweets 100 --hashtags nifty50 sensex intraday banknifty


Sample Output Structure
| timestamp        | username    | content                | likes | retweets | sentiment_score | signal  |
| ---------------- | ----------- | ---------------------- | ----- | -------- | --------------- | ------- |
| 2025-01-10 10:21 | @financeguy | Nifty breakout coming! | 54    | 12       | 0.82            | Bullish |

Files available:
| File                             | Description                         |
| -------------------------------- | ----------------------------------- |
| `samples/sample_tweets.parquet`  | Cleaned tweets dataset              |
| `samples/sample_signals.parquet` | Signal scores for trading sentiment |

Signal Generation Formula
The final market signal is computed using weighted NLP + engagement scoring:
Signal = (TF-IDF score * Keyword intensity * Engagement weight)
Signal strength ranges from:
  +1.0 → Strong Bullish
  0.0 → Neutral
  -1.0 → Strong Bearish
    
  
Limitations & Future Scope
| Area                  | Proposed Improvement                               |
| --------------------- | -------------------------------------------------- |
| Anti-bot rate limits  | Add rotating proxies + Tor                         |
| Basic TF-IDF modeling | Switch to embeddings (BERT, FinBERT)               |
| Local streaming       | Kafka + Spark Streaming                            |
| Visualization         | Real-time dashboards (Streamlit, PowerBI, Grafana) |
| Market application    | Backtesting with actual stock price data           |



