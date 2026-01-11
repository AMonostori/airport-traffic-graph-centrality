# Global Airport Network Analysis

A graph-based analysis of airport connectivity that models the global air transportation network to identify major hubs and traffic patterns using centrality measures.

## Motivation

Traditional airport rankings rely on passenger counts or flight volumes. This project takes a structural approach by modeling airports as nodes in a graph network and their flight routes as edges, applying graph theory to understand which airports function as critical hubs in the global transportation infrastructure.

## Challenge: Working Within Constraints

With API query limits capping the dataset at 250 airports, the goal shifted from comprehensive global coverage to developing a robust analytical framework. The key challenge was selecting representative airports without geographic bias.

**Selection Strategy:**
- Divided the world into 6 geographic regions (Europe, North America, South America, Asia, Africa & Middle East, Australia & Oceania)
- Selected 40 major airports per region (240 total)
- Scraped curated lists from aviation websites rather than relying on incomplete "top 100" rankings or unstable Wikipedia tables

This approach balanced regional representation while staying within API constraints.

## Methodology

1. **Data Collection** - Scraped airport lists and stored in CSV
2. **Airport Details** - Retrieved ICAO codes, coordinates, and metadata via Aviation Reference Data API
3. **Route Mapping** - Collected daily flight statistics between airport pairs using AeroDataBox API
4. **Graph Construction** - Built directed graph with NetworkX (nodes = airports, edges = routes, weights = daily flights)
5. **Centrality Analysis** - Calculated three key metrics:
   - **Degree Centrality** - Number of direct connections
   - **In-Degree Centrality** - Number of incoming routes (popularity as destination)
   - **Betweenness Centrality** - Role as connector between other airports (hub importance)
6. **Visualization** - Plotted global network on Robinson projection map using Basemap

## Tech Stack

- **Python 3.x**
- **Pandas** - Data manipulation
- **NetworkX** - Graph construction and centrality analysis
- **Requests** - API data retrieval
- **Matplotlib & Basemap** - Geographic visualization
- **flatten_json** - JSON normalization

## Key Findings

Top airports by centrality varied depending on the metric:

- **Most Connected (Degree):** Istanbul (LTFM), Miami (KMIA), Frankfurt (EDDF)
- **Critical Hubs (Betweenness):** Dubai (OMDB), Istanbul (LTFM), Sydney (YSSY)

These results demonstrate that "busiest" depends on perspective—some airports handle high volumes, while others serve as indispensable bridges in the network.

## Visualization

The project includes a global map visualization showing:
- Airport nodes scaled by connectivity
- Edge density representing route frequency
- Geographic distribution of major hubs

## Limitations & Future Work

- Dataset limited to 240 airports due to API constraints
- Framework prioritized over absolute accuracy
- Future expansion could include temporal analysis (seasonal variations) or weighted centrality by passenger volume

