# Weather MCP Server

A Model Context Protocol (MCP) server that provides weather data and alerts using the National Weather Service (NWS) API. This server enables AI assistants to fetch real-time weather forecasts and alerts for locations within the United States.

## Features

- **Weather Forecasts**: Get detailed weather forecasts for any US location using latitude and longitude coordinates
- **Weather Alerts**: Retrieve active weather alerts for any US state using two-letter state codes
- **Real-time Data**: All data is fetched directly from the National Weather Service API
- **MCP Compatible**: Works seamlessly with Claude Desktop and other MCP-compatible clients

## Installation

1. Clone this repository:

```bash
git clone <repository-url>
cd weather
```

2. Install dependencies:

```bash
npm install
```

3. Build the project:

```bash
npm run build
```

## Usage

### As an MCP Server

Add this server to your Claude Desktop configuration file (`claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "weather": {
      "command": "node",
      "args": ["/absolute/path/to/weather/build/index.js"]
    }
  }
}
```

Replace `/absolute/path/to/weather` with the actual path to your weather project directory.

### Available Tools

#### `get-forecast`

Get weather forecast for a specific location.

**Parameters:**

- `latitude` (number): Latitude of the location (-90 to 90)
- `longitude` (number): Longitude of the location (-180 to 180)

**Example:**

```
Get forecast for latitude 40.7128, longitude -74.0060 (New York City)
```

#### `get-alerts`

Get active weather alerts for a US state.

**Parameters:**

- `state` (string): Two-letter state code (e.g., "CA", "NY", "TX")

**Example:**

```
Get alerts for California (CA)
```

## Development

### Project Structure

```
weather/
├── src/
│   └── index.ts          # Main server implementation
├── build/
│   └── index.js          # Compiled JavaScript
├── package.json
├── tsconfig.json
└── README.md
```

### Building

```bash
npm run build
```

This compiles the TypeScript source code and makes the executable file at `build/index.js` executable.

### Testing

You can test the server by running it directly:

```bash
node build/index.js
```

The server will start and listen for MCP protocol messages on stdin/stdout.

## API Information

This server uses the National Weather Service API:

- **Base URL**: https://api.weather.gov
- **Coverage**: United States only
- **Data Source**: Official NWS weather data
- **Rate Limits**: Follow NWS API guidelines

## Dependencies

- `@modelcontextprotocol/sdk`: MCP protocol implementation
- `zod`: Schema validation and type safety
- `typescript`: TypeScript compiler
- `@types/node`: Node.js type definitions

## License

ISC

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## Support

For issues related to:

- **MCP Protocol**: Visit [Model Context Protocol documentation](https://modelcontextprotocol.io/)
- **Weather Data**: Check the [National Weather Service API documentation](https://www.weather.gov/documentation/services-web-api)
- **This Server**: Open an issue in this repository
