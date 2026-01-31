# AgentLens

**Visualize and analyze AI agent tool usage patterns, performance metrics, and execution flows.**

AgentLens is a React-based analytics dashboard for understanding how AI agents use tools during execution. It provides interactive visualizations and insights to help identify performance bottlenecks, error patterns, and optimization opportunities.

![AgentLens Dashboard](https://img.shields.io/badge/React-18.2.0-blue) ![Vite](https://img.shields.io/badge/Vite-4.4.9-brightgreen) ![License](https://img.shields.io/badge/license-MIT-green)

## Features

### 📊 **Tools Overview**
- Visual cards for each tool with key metrics
- Usage count, average duration, and error rates
- Token usage breakdown (prompt vs completion)
- Mini visualizations for quick insights
- Search and sort capabilities

### 📈 **Metrics Dashboard**
- High-level KPIs (total calls, average duration, error rate, token usage)
- Multiple chart types: line, scatter, bar, pie, area, boxplot, and heatmap
- Tool-specific filtering and comparison
- Error analysis by execution step
- Token distribution analysis

### 🔄 **Tool Flow Visualization**
- Sankey diagrams showing tool transitions across execution steps
- Normal and error flow views
- Interactive flow exploration
- Error statistics panel

### 🔍 **Individual Tool Analysis**
- **Overview Tab**: Token distribution, runtime distribution, historical performance
- **Step Analysis Tab**: Performance metrics organized by execution step
- **Execution Timeline Tab**: Timeline visualization of tool calls

## Tech Stack

- **Framework**: React 18.2.0 with React Router 6.14.2
- **Build Tool**: Vite 4.4.9
- **UI Libraries**: Bootstrap 5.3.0, React Bootstrap 2.8.0
- **Visualizations**: 
  - Recharts 2.7.2 (bar, line, scatter, pie, area charts)
  - Plotly.js 2.26.0 (Sankey diagrams, boxplots, heatmaps)
- **Data Processing**: PapaParse 5.4.1, Lodash 4.17.21

## Getting Started

### Prerequisites

- Node.js (v16 or higher recommended)
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd agentlens
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

### Building for Production

```bash
npm run build
```

The build output will be in the `dist` directory.

### Preview Production Build

```bash
npm run preview
```

## Data Format

AgentLens expects a CSV file located at `/public/agent_metrics.csv` with the following structure:

| Column | Description |
|--------|-------------|
| `subdir` | Use case or category identifier |
| `step` | Execution step number |
| `tool_name` | Name of the tool called |
| `duration` | Execution duration in milliseconds |
| `token_count` | Total tokens used |
| `prompt_tokens` | Tokens in the prompt |
| `completion_tokens` | Tokens in the completion |
| `cached_tokens_pct` | Percentage of cached tokens |
| `has_error` | Boolean indicating error occurrence |
| `error_type` | Type of error (if applicable) |
| `model_name` | AI model used |
| `finish_reason` | Reason for completion |

### Example CSV

```csv
subdir,step,tool_name,duration,token_count,prompt_tokens,completion_tokens,cached_tokens_pct,has_error,error_type,model_name,finish_reason
use_case_1,1,Read,234,1500,1000,500,0,false,,gpt-4,stop
use_case_1,2,Grep,156,800,600,200,0,false,,gpt-4,stop
use_case_1,3,Write,345,2000,1200,800,0,false,,gpt-4,stop
```

## Project Structure

```
agentlens/
├── public/
│   └── agent_metrics.csv      # Your agent metrics data
├── src/
│   ├── components/
│   │   ├── Layout.jsx         # Navigation wrapper
│   │   ├── SparklineBar.jsx   # Mini bar chart component
│   │   ├── ToolDetail.jsx     # Individual tool analysis page
│   │   └── Tabs/
│   │       ├── ToolsTab.jsx   # Tools overview
│   │       ├── MetricsTab.jsx # Metrics dashboard
│   │       └── ToolFlowTab.jsx # Flow visualization
│   ├── utils/
│   │   ├── dataProcessing.js  # CSV parsing & data transformations
│   │   └── plotlyHelpers.js   # Plotly-specific helpers
│   ├── App.jsx                # Main app with routing
│   └── main.jsx               # Entry point
├── package.json
├── vite.config.js
└── README.md
```

## Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server with hot reload |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build locally |
| `npm run lint` | Run ESLint for code quality checks |
| `npm run clean` | Remove build artifacts and cached files |

## Key Features Explained

### Consistent Color Mapping
Tools maintain consistent colors across all visualizations for easy visual tracking.

### Multi-Level Analysis
Navigate from high-level overview → tool list → individual tool details for deeper insights.

### Step-Based Analysis
Understand how tools perform across different execution steps to identify bottlenecks.

### Error Flow Visualization
Sankey diagrams show both normal execution flows and error-specific patterns.

### Token Analytics
Deep dive into token usage with breakdowns of prompt, completion, and cached tokens.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License.

## Acknowledgments

Built with React, Vite, Recharts, and Plotly.js for powerful data visualization capabilities.
