# Finance AI Agent using GROQ and Phidata

## Overview
This project leverages an AI agent powered by [GROQ](https://groq.com/) and [Phidata](https://phidata.com/) to fetch and analyze financial data for stocks. The agent retrieves stock prices, analyst recommendations, company information, and news using the `YFinanceTools` module.

## Features
- Fetch real-time stock prices
- Summarize analyst recommendations
- Retrieve company financial information
- Get the latest company news
- Display data in a structured tabular format

## Technologies Used
- **Python**: Core programming language
- **GROQ**: AI model for processing queries
- **Phidata**: AI agent framework
- **yFinanceTools**: Fetch financial data from Yahoo Finance
- **dotenv**: Load environment variables

## Installation

1. **Clone the Repository**
   ```sh
   git clone <repository-url>
   cd <repository-folder>
   ```

2. **Create a Virtual Environment (Optional but Recommended)**
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**
   ```sh
   pip install -r requirements.txt
   ```

4. **Set Up Environment Variables**
   Create a `.env` file in the project directory and add necessary API keys if required.

## Usage

Run the following script to fetch financial data using the AI agent:

```python
from phi.agent import Agent
from phi.model.groq import Groq
from phi.tools.yfinance import YFinanceTools
from dotenv import load_dotenv

load_dotenv()

finance_agent = Agent(
    name="Finance Agent",
    description="Your task is to find the financial information",
    model=Groq(id="llama-3.3-70b-versatile"),
    tools=[YFinanceTools(stock_price=True, analyst_recommendations=True, company_info=True, company_news=True)],
    instructions=["Use tables for displaying the data"],
    show_tool_calls=True,
    markdown=True,
    debug_mode=True
)

finance_agent.print_response("Summarize analyst recommendation for IRFC", stream=True)
```

## Example Output
```
| Date       | Analyst Recommendation |
|------------|------------------------|
| 2024-03-01 | Buy                     |
| 2024-02-28 | Hold                    |
| 2024-02-25 | Strong Buy              |
```

## Future Improvements
- Enhance AI responses with additional financial indicators
- Support multiple stock ticker queries
- Add visualization support for stock trends

## License
This project is licensed under the MIT License.

## Contact
For any queries or contributions, feel free to reach out!

