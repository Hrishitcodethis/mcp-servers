# MCP Demo Project

This project serves as a demonstration and exploration of various Model Context Protocol (MCP) servers and their respective use cases. It aims to provide a clear understanding of how different MCP services can be integrated and utilized within a single application, showcasing their functionalities and potential workflows.

## Project Overview

This project uses a combination of MCP servers to demonstrate diverse functionalities, including:

*   **Web Browsing Automation (Playwright MCP):** For interacting with web pages, navigating, and extracting information.
*   **Travel Booking Search (Airbnb MCP):** For searching available listings on Airbnb.
*   **Deep Research and Analysis (Octagon Deep Research MCP):** For comprehensive multi-source data aggregation, web scraping, and analysis.

## Workflow

The general workflow of this project involves:

1.  **User Input:** The user provides a query or request.
2.  **Tool Selection:** The system identifies the most appropriate MCP tool based on the user's request.
3.  **Tool Execution:** The selected MCP tool is invoked with the necessary parameters.
4.  **Result Processing:** The results from the MCP tool are processed and presented back to the user.

For example:

*   When the user asks to "open google.com and then open makemytrip.com", the Playwright MCP is used to navigate to the specified URLs.
*   When the user asks for "available hotels for 15th june in bangalore", the Airbnb MCP is used to search for listings. Note that the `ignoreRobotsText` flag is used in this case to bypass `robots.txt` restrictions for demonstration purposes.
*   When the user asks for "latest AI news", a web search is performed to gather information.
*   When the user asks to "explain me about his error", the system provides details about the rate limit error encountered with the `duckduckgo-mcp-server`.

## MCP Server Configuration

The `browser_mcp.json` file configures the MCP servers used in this project:

```json
{
    "mcpServers": {
      "playwright": {
        "command": "npx",
        "args": [
          "@playwright/mcp@latest"
        ]
      },
       "airbnb": {
            "command": "npx",
            "args": [
                "-y",
                "@openbnb/mcp-server-airbnb",
                "--ignore-robots-txt"
            ]
      },
    "octagon-deep-research-mcp": {
      "command": "npx",
      "args": ["-y", "octagon-deep-research-mcp@latest"],
      "env": {
        "OCTAGON_API_KEY": "{{OCTAGON_API_KEY}}"
      }
    }
  }
}
```

### API Key Management

For the `octagon-deep-research-mcp`, the `OCTAGON_API_KEY` is loaded from an environment variable for security purposes. You should create a `.env` file in the root of your project with your actual API key:

```
OCTAGON_API_KEY="your_octagon_api_key_here"
```

## Getting Started

To run this project, ensure you have Node.js and npm/npx installed. Then, set up your environment variables as described above.

Further instructions on how to run the specific components of this project would depend on the main application's entry point (e.g., Python script, web server).

## How to Run in Terminal

To run this project, follow these steps:

1.  **Install Dependencies:** Ensure you have `uv` installed. If not, you can install it using pip: `pip install uv`. Then, install the project dependencies:

    ```bash
    uv pip install -r requirements.txt
    ```
    (Note: If you don't have a `requirements.txt` file, you might need to create one or install dependencies based on `pyproject.toml` or `uv.lock`.)

2.  **Set up Environment Variables:** Create a `.env` file in the project root and add your `OCTAGON_API_KEY` as described in the "API Key Management" section.

3.  **Run the Application:** Execute the main application script (assuming `app.py` is your main entry point):

    ```bash
    uv run app.py
    ```

## Terminal Interaction Snapshots
<img width="1161" alt="Screenshot 2025-06-13 at 1 25 00 PM" src="https://github.com/user-attachments/assets/0c069fa9-bb99-49ea-a2d4-9033ff5f0e3b" />

## Cursor Interaction Snapshots

The Cursor IDE can also function as an MCP client, allowing for direct interaction and execution of MCP commands within the IDE environment.
