# Smooth Cursor

A highly customizable, physics-based smooth cursor animation component for React applications. Features spring animations, velocity tracking, and rotation effects for creating engaging cursor experiences.

🎯 **[Live Preview](https://figbruary.apexia.club)** - See the smooth cursor in action!

![NPM Version](https://img.shields.io/npm/v/smooth-cursor)
![License](https://img.shields.io/npm/l/smooth-cursor)

## Features

- 🎯 Smooth physics-based cursor animations
- 🔄 Rotation effects based on movement direction
- ⚡ Performance optimized with RAF
- 🎨 Fully customizable cursor design
- 📦 Lightweight and easy to implement
- 💪 Written in TypeScript
- 🔌 Powered by Framer Motion

## Installation

```bash
npm install smooth-cursor
# or
yarn add smooth-cursor
# or
pnpm add smooth-cursor
```

## Usage

### Next.js Integration

#### App Router (Next.js 13+)

```tsx
// app/layout.tsx
'use client';

import { SmoothCursor } from 'smooth-cursor';

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>
        <SmoothCursor />
        {children}
      </body>
    </html>
  );
}
```

#### Pages Router

```tsx
// pages/_app.tsx
import type { AppProps } from 'next/app';
import { SmoothCursor } from 'smooth-cursor';

export default function App({ Component, pageProps }: AppProps) {
  return (
    <>
      <SmoothCursor />
      <Component {...pageProps} />
    </>
  );
}
```

### Basic Usage

```jsx
import { SmoothCursor } from 'smooth-cursor';

function App() {
  return (
    <div>
      <SmoothCursor />
      {/* Your app content */}
    </div>
  );
}
```

### Custom Cursor

```jsx
import { SmoothCursor } from 'smooth-cursor';

const CustomCursor = () => (
  <div className="w-8 h-8 bg-blue-500 rounded-full" />
);

function App() {
  return (
    <div>
      <SmoothCursor cursor={<CustomCursor />} />
      {/* Your app content */}
    </div>
  );
}
```

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| cursor | JSX.Element | `<DefaultCursorSVG />` | Custom cursor component to replace the default cursor |
| springConfig | SpringConfig | See below | Configuration object for the spring animation behavior |

### SpringConfig Type

```typescript
interface SpringConfig {
    damping: number;    // Controls how quickly the animation settles
    stiffness: number;  // Controls the spring stiffness
    mass: number;       // Controls the virtual mass of the animated object
    restDelta: number;  // Controls the threshold at which animation is considered complete
}
```

### Default Spring Configuration

```typescript
const defaultSpringConfig = {
    damping: 45,      // Default damping value
    stiffness: 400,   // Default stiffness value
    mass: 1,          // Default mass value
    restDelta: 0.001  // Default rest delta value
}
```

### Usage with Custom Spring Configuration

```tsx
function App() {
  const customSpringConfig = {
    damping: 60,      // Higher damping for less oscillation
    stiffness: 500,   // Higher stiffness for faster movement
    mass: 1.2,        // Slightly more mass for momentum
    restDelta: 0.0005 // Smaller rest delta for more precise settling
  };

  return (
    <div>
      <SmoothCursor springConfig={customSpringConfig} />
      {/* Your app content */}
    </div>
  );
}
```

## Animation Configuration

The cursor uses Framer Motion's spring animation with the following default configuration:

```typescript
const springConfig = {
  damping: 45,
  stiffness: 400,
  mass: 1,
  restDelta: 0.001
};
```

## Browser Support

The component is compatible with all modern browsers that support:
- `requestAnimationFrame`
- CSS transforms
- Pointer events

## Performance Considerations

The component is optimized for performance by:
- Using `requestAnimationFrame` for smooth animations
- Implementing throttling for mouse movement events
- Using hardware-accelerated transforms
- Optimizing re-renders with React's lifecycle methods

## Development

To run the development environment:

```bash
# Install dependencies
npm install

# Build the package
npm run rollup
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Credits

Created by [Code-Parth](https://github.com/Code-Parth)

## Support

If you have any questions or need help integrating the component, please [open an issue](https://github.com/Code-Parth/smooth-cursor/issues).
