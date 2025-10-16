# react-pdf-viewer (Maintenance Fork)

> **Note**: This is a maintained fork of the original [react-pdf-viewer](https://github.com/react-pdf-viewer/react-pdf-viewer) project, which appears to be no longer actively maintained. This fork includes critical bug fixes and improvements for production use.

## Why This Fork?

The original `react-pdf-viewer` library (last updated with v3.12.0) is an excellent PDF viewer for React applications, but has not seen active maintenance. This fork addresses specific issues we encountered in production:

### Fixes Included

1. **Multi-keyword Search Sorting** - Search results are now properly sorted by page index and position when using multiple keywords
2. **Smart Scroll Behavior** - Highlights only trigger scrolling when they are outside the viewport, preventing unnecessary jumps
3. **Dependency Updates** - Fixed internal package dependencies and build artifacts

## Installation

Published under the `@illassad` scope on npm:

```bash
npm install @illassad/react-pdf-viewer-core @illassad/react-pdf-viewer-search @illassad/react-pdf-viewer-default-layout
```

## Usage

The API is identical to the original `@react-pdf-viewer` packages:

```tsx
import { Provider, Viewer } from '@illassad/react-pdf-viewer-core';
import { searchPlugin } from '@illassad/react-pdf-viewer-search';
import { defaultLayoutPlugin } from '@illassad/react-pdf-viewer-default-layout';
import * as pdfjs from 'pdfjs-dist';

import '@illassad/react-pdf-viewer-core/lib/styles/index.css';
import '@illassad/react-pdf-viewer-search/lib/styles/index.css';
import '@illassad/react-pdf-viewer-default-layout/lib/styles/index.css';

function PDFViewer({ pdfUrl }) {
    const searchPluginInstance = searchPlugin();
    const defaultLayoutPluginInstance = defaultLayoutPlugin();

    return (
        <Provider
            pdfApiProvider={pdfjs}
            workerUrl="https://unpkg.com/pdfjs-dist@3.4.120/build/pdf.worker.min.js"
        >
            <Viewer
                fileUrl={pdfUrl}
                plugins={[searchPluginInstance, defaultLayoutPluginInstance]}
            />
        </Provider>
    );
}
```

## Version

Current version: `3.12.1-illassad.3`

Based on: `@react-pdf-viewer` v3.12.0

## Original Project

All credit goes to the original author [Nguyen Huu Phuoc](https://twitter.com/nghuuphuoc) for creating this excellent PDF viewer library.

- Original repository: https://github.com/react-pdf-viewer/react-pdf-viewer
- Original documentation: https://react-pdf-viewer.dev

## Changes from Original

- Fixed search result sorting for multi-keyword searches
- Fixed viewport visibility checking before scrolling to highlights
- Updated package build process to work with scoped package names
- Removed abandoned canvas dependency

## Contributing

This is a maintenance fork focused on keeping the library usable for production. If the original project resumes active development, we encourage using that instead.

## Repository Structure

This repository maintains the original structure:

- `/packages` - Individual npm packages for different PDF viewer features
- `/demo` - Demo applications
- `/docs` - Documentation

## Building

The original build system is preserved. However, note that some packages may have build issues - the published npm packages include pre-built artifacts.
