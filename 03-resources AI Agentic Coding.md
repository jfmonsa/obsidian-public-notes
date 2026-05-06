i# Browser Integration
To enable an AI agent to verify that a web page is working (rendering correctly, functioning, etc.), you can ==use a **Model Context Protocol (MCP) server** that connects the agent to a browser automation tool like Playwright or Chrome DevTools==. 

Here are the best ways to achieve this:

1. Playwright MCP Server 

This is the most common approach for testing and automation. It allows the agent to navigate to a site, take screenshots, and click elements. 

- **How it works:** The agent uses tools like `navigate`, `screenshot`, or `click` to verify the page.
- **Example use:** "Navigate to `localhost:3000`, check if the login button is present, and take a screenshot". 

2. Chrome DevTools MCP Server 

This is best for deep technical verification (debugging, network checks, performance). 

- **How it works:** Connects directly to a Chromium instance, allowing the agent to inspect console logs, network activity (e.g., finding 404 errors), and page performance.
- **Example use:** "Find any JavaScript errors on this page" or "Measure the LCP for `example.com`".