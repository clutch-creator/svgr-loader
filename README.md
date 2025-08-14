# @clutch-creator/svgr-loader

A Turbopack-compatible SVG loader that transforms SVG files into React components using SVGR.

## Features

- 🚀 **Turbopack Compatible**: Designed specifically for Next.js with Turbopack
- ⚛️ **React Component Generation**: Transforms SVGs into React components using SVGR
- 🎨 **Icon Support**: Special handling for icon SVGs with color replacement
- 📦 **Dual Export**: Export SVGs as components or base64 data URLs
- 🔧 **Configurable**: Supports query parameters for different behaviors

## Installation

```bash
npm install @clutch-creator/svgr-loader
# or
yarn add @clutch-creator/svgr-loader
# or
bun add @clutch-creator/svgr-loader
```

## Usage

### Basic SVG Import

By default, SVGs are exported as base64 data URLs:

```javascript
import logo from './logo.svg';
// Returns: "data:image/svg+xml;base64,..."
```

### React Component Import

Add the `?icon` query parameter to transform SVGs into React components:

```javascript
import { ReactComponent as Logo } from './logo.svg?icon';

function App() {
  return <Logo />;
}
```

### Color Replacement

Use `?icon&replaceColors` to replace fill and stroke colors with `currentColor`:

```javascript
import { ReactComponent as Icon } from './icon.svg?icon&replaceColors';

function App() {
  return (
    <div style={{ color: 'red' }}>
      <Icon /> {/* Icon will be red */}
    </div>
  );
}
```

## Configuration

This loader is designed to work with Turbopack. Configure it in your Next.js project's `next.config.js`:

```javascript
/** @type {import('next').NextConfig} */
const nextConfig = {
  turbopack: {
    rules: {
      '*.svg': {
        loaders: ['@clutch-creator/svgr-loader'],
        as: '*.js',
      },
    },
  },
};

module.exports = nextConfig;
```

## Query Parameters

| Parameter       | Description                                                      |
| --------------- | ---------------------------------------------------------------- |
| `icon`          | Transform SVG into a React component                             |
| `replaceColors` | Replace fill/stroke colors with `currentColor` (requires `icon`) |

## Examples

```javascript
// As data URL
import svgUrl from './image.svg';

// As React component
import { ReactComponent as MyIcon } from './icon.svg?icon';

// As React component with color replacement
import { ReactComponent as ColorIcon } from './icon.svg?icon&replaceColors';

function MyComponent() {
  return (
    <div>
      <img src={svgUrl} alt='SVG as image' />
      <MyIcon />
      <ColorIcon style={{ color: 'blue' }} />
    </div>
  );
}
```

## Development

```bash
# Install dependencies
bun install

# Build the project
bun run build

# Lint code
bun run lint

# Format code
bun run format
```

## License

MIT

---

Made with ❤️ by the [Clutch team](https://clutch.io)

Clutch is the next-generation visual builder that empowers creative professionals with total design freedom, advanced functionality, and top-tier performance. Learn more at [clutch.io](https://clutch.io).
