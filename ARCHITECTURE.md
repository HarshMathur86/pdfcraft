# PDFCraft - Architecture & Tech Stack Documentation ( ✨ AI Generrated)

## 📋 Project Overview

**PDFCraft** is a comprehensive, browser-based PDF processing toolkit that prioritizes privacy and performance. It's a full-stack web application that processes PDF files entirely on the client side using WebAssembly technology, ensuring no files are uploaded to external servers. The project features 90+ PDF tools, a visual workflow editor for chaining operations, multi-language support, and a modern, responsive UI.

**Core Principle**: 100% client-side processing - your documents never leave your device.

---

## 🏗️ Project Architecture

### Directory Structure

```
pdfcraft/
├── src/
│   ├── __tests__/              # Unit and integration tests
│   ├── app/                    # Next.js app directory (routes)
│   ├── components/             # React components
│   │   ├── common/             # Reusable common components
│   │   ├── layout/             # Layout components (navigation, sidebars)
│   │   ├── seo/                # SEO-related components
│   │   ├── tools/              # Individual PDF tool components (90+)
│   │   ├── ui/                 # UI library components
│   │   └── workflow/           # Workflow editor components
│   ├── config/                 # Configuration files
│   ├── hooks/                  # Custom React hooks
│   ├── i18n/                   # Internationalization setup
│   ├── lib/                    # Library code and utilities
│   │   ├── contexts/           # React contexts for global state
│   │   ├── pdf/                # PDF processing logic
│   │   ├── storage/            # Local storage management
│   │   ├── utils/              # Helper utilities
│   │   └── workflow/           # Workflow engine logic
│   └── types/                  # TypeScript type definitions
├── public/                     # Static assets
│   ├── images/                 # Logo and UI images
│   ├── pdfjs-viewer/           # PDF.js viewer distribution
│   ├── pdfjs-annotation-viewer/# PDF annotation extensions
│   ├── pymupdf-wasm/           # Python/PyMuPDF WebAssembly
│   └── workers/                # Web Workers (90+ processing tasks)
├── messages/                   # i18n translation files (9 languages)
├── extension/                  # Browser extension files
└── Configuration files         # next.config.js, tsconfig.json, etc.
```

### Component Architecture

#### **Workflow Editor Components** (`src/components/workflow/`)

```
WorkflowEditor/
├── WorkflowEditor.tsx          # Main canvas and orchestration
├── ToolNode.tsx                # Visual node representation
├── ToolSidebar.tsx             # Available tools palette
├── WorkflowLibrary.tsx         # Pre-built templates (23+)
├── NodeSettingsPanel.tsx       # Node configuration UI
├── FileListPanel.tsx           # Input file management
├── WorkflowControls.tsx        # Undo/redo/save controls
└── WorkflowPreview.tsx         # Batch processing preview
```

#### **Core Libraries & Utilities** (`src/lib/`)

```
lib/
├── pdf/                        # PDF manipulation
│   ├── merge.ts               # PDF merging logic
│   ├── split.ts               # PDF splitting logic
│   ├── compress.ts            # Compression algorithms
│   └── ...                    # 90+ tool implementations
├── storage/                   # IndexedDB/localStorage
├── utils/                     # Common utilities
├── contexts/                  # Global state management
└── workflow/                  # Workflow engine & execution
```

#### **Custom Hooks** (`src/hooks/`)

```
hooks/
├── useFavorites.ts            # Save/load favorite tools
└── useUndoRedo.ts             # State history management
```

---

## 🛠️ Detailed Tech Stack

### 1. **Frontend Framework & Core**

| Technology | Version | Purpose |
|-----------|---------|---------|
| **Next.js** | ^15.1.8 | React framework with SSR/SSG capabilities, static export support |
| **React** | ^19.0.0 | UI library and component architecture |
| **TypeScript** | ^5.6.3 | Type-safe JavaScript development |
| **Tailwind CSS** | ^4.0.0 | Utility-first CSS framework |
| **PostCSS** | ^8.4.47 | CSS transformations |
| **Turbopack** | Latest | Next.js bundler for fast compilation (dev mode) |

### 2. **State Management & Data**

| Library | Version | Purpose |
|---------|---------|---------|
| **Zustand** | ^5.0.0 | Lightweight global state management |
| **React Context** | Built-in | Component-level state management |
| **Custom Hooks** | Local | Undo/redo and favorites management |

### 3. **PDF Processing Libraries** (Core Engines)

| Library | Version | Purpose |
|---------|---------|---------|
| **pdf-lib** | ^1.17.1 | Core PDF manipulation (create, modify, extract, annotations) |
| **@pdf-lib/fontkit** | ^1.1.1 | Font support in PDF-lib |
| **pdfjs-dist** | ^4.8.69 | PDF rendering, viewing, and text extraction |
| **tesseract.js** | ^6.0.1 | OCR (optical character recognition) for scanned PDFs |
| **qpdf.js** | Browser WASM | Advanced PDF compression and security operations |
| **coherentpdf.browser.min.js** | Browser WASM | High-performance PDF operations |

### 4. **Format Conversion Libraries**

| Library | Version | Purpose |
|---------|---------|---------|
| **jspdf** | ^4.0.0 | Generate PDFs from HTML/Canvas content |
| **html2canvas** | ^1.4.1 | Convert HTML/DOM to canvas images |
| **html2pdf.js** | ^0.14.0 | High-level HTML to PDF conversion |
| **marked** | ^17.0.1 | Markdown parsing and rendering |
| **ag-psd** | ^29.0.0 | Adobe Photoshop (PSD) file handling |
| **jszip** | ^3.10.1 | ZIP archive creation/extraction (for CBZ, EPUB) |

### 5. **Image & Annotation Tools**

| Library | Version | Purpose |
|---------|---------|---------|
| **cropperjs** | ^1.6.2 | Image cropping and manipulation |
| **react-cropper** | ^2.3.3 | React wrapper for cropper.js |
| **highlight.js** | ^11.11.1 | Code syntax highlighting (JSON tool) |

### 6. **Visual Components & UI**

| Library | Version | Purpose |
|---------|---------|---------|
| **lucide-react** | ^0.454.0 | Modern icon library |
| **clsx** | ^2.1.1 | Conditional className utility |
| **tailwind-merge** | ^2.5.4 | Merge and deduplicate Tailwind CSS classes |
| **reactflow** | ^11.11.4 | Node-based workflow editor (visual workflows) |

### 7. **Internationalization**

| Library | Version | Purpose |
|---------|---------|---------|
| **next-intl** | ^4.1.0 | Multi-language support for 9 languages |

**Supported Languages**:
- English (en)
- Spanish (es)
- French (fr)
- German (de)
- Portuguese (pt)
- Japanese (ja)
- Korean (ko)
- Chinese Simplified (zh)
- Chinese Traditional (zh-TW)

### 8. **WebAssembly & High-Performance Computing**

#### Pyodide Environment
Loaded from `public/pymupdf-wasm/`, includes:

**Core Libraries**:
- **pyodide.js** - Python runtime in browser
- **pymupdf-lite.js** - Fast PDF processing
- **pymupdf.js** - Full PyMuPDF functionality

**Python Packages**:
- **pandas** - Data processing and manipulation
- **numpy** - Numerical operations
- **opencv_python** - Computer vision and image processing
- **pillow** - Image processing (PIL)
- **pymupdf4llm** - LLM-ready PDF extraction
- **python-docx** - Microsoft Word document handling
- **python-pptx** - Microsoft PowerPoint handling
- **pdf2docx** - PDF to DOCX conversion
- **openpyxl** - Excel spreadsheet handling
- **lxml** - XML processing

### 9. **Testing & Quality Assurance**

| Library | Version | Purpose |
|---------|---------|---------|
| **Vitest** | ^2.1.3 | Fast unit testing framework |
| **@testing-library/react** | ^16.0.1 | React component testing utilities |
| **@testing-library/dom** | ^10.4.0 | DOM testing utilities |
| **@testing-library/jest-dom** | ^6.9.1 | Jest matchers for DOM |
| **@testing-library/user-event** | ^14.6.1 | User interaction simulation |
| **jsdom** | ^25.0.1 | JavaScript DOM implementation |
| **fake-indexeddb** | ^6.2.5 | Mock IndexedDB for testing |
| **fast-check** | ^3.22.0 | Property-based testing |
| **ESLint** | ^9.17.0 | Code linting and quality |
| **eslint-config-next** | ^15.1.8 | Next.js ESLint configuration |

### 10. **Build & Deployment**

| Technology | Configuration | Purpose |
|-----------|---------------|---------|
| **Static Export** | `output: 'export'` in next.config.js | Deploy as static site (CDN-friendly) |
| **Webpack WASM** | Custom webpack config | Enable WebAssembly module loading |
| **Docker** | docker-compose.yml | Containerization |
| **Nginx** | nginx.conf | Reverse proxy and static file serving |
| **Vercel** | vercel.json | Deployment and edge functions |

---

## 📦 Development Setup

### Environment Configuration

**Node.js Version**: Latest LTS (18+)

**Package Manager**: npm (or yarn/pnpm)

### Build & Development Scripts

```json
{
  "dev": "next dev --turbopack",        // Development with Turbopack
  "build": "next build",                // Production build
  "start": "next start",                // Start production server
  "lint": "eslint . --ext .ts,.tsx",    // Lint TypeScript files
  "test": "vitest run",                 // Run tests once
  "test:watch": "vitest",               // Watch mode testing
  "test:coverage": "vitest run --coverage"  // Coverage report
}
```

### TypeScript Configuration

```typescript
{
  "compilerOptions": {
    "target": "ES2017",
    "lib": ["dom", "dom.iterable", "esnext"],
    "strict": true,
    "jsx": "preserve",
    "moduleResolution": "bundler",
    "paths": {
      "@/*": ["./src/*"],
      "@/components/*": ["./src/components/*"],
      "@/lib/*": ["./src/lib/*"],
      "@/types/*": ["./src/types/*"],
      "@/config/*": ["./src/config/*"]
    }
  }
}
```

---

## ✨ Key Features Implementation

### 1. **90+ PDF Tools**
Organized in categories:
- **27 Organize & Manage Tools** - Merge, split, rotate, reorder, etc.
- **19 Edit & Annotate Tools** - Add text, signatures, watermarks, etc.
- **22 Convert to PDF Tools** - Image, document, ebook conversions
- **22+ Other Tools** - Compress, secure, extract, view, etc.

### 2. **Workflow Editor (Beta)**
- Visual node-based interface using ReactFlow
- 23+ pre-built templates
- Drag-and-drop tool palette
- Real-time validation
- Batch processing support
- Save/load custom workflows

### 3. **Client-Side Processing**
- All processing happens in the browser
- WebAssembly for performance
- No server-side file uploads
- Pyodide for advanced Python operations
- Web Workers for non-blocking operations

### 4. **Multi-Language Support**
- Translation files in `messages/` directory
- Language detection via next-intl middleware
- URL-based language routing

### 5. **Persistent Storage**
- IndexedDB for large file storage
- localStorage for settings/preferences
- Service Worker for offline capabilities

### 6. **Favorites & History**
- `useFavorites` hook - Save frequently used tools
- `useUndoRedo` hook - Full undo/redo stack management

---

## 🔄 Data Flow

1. **User Input** → File upload or text input in browser
2. **Tool Selection** → User selects PDF tool from UI
3. **Processing** → 
   - JavaScript-based tools use pdf-lib, jspdf, etc.
   - Complex operations use Web Workers
   - Advanced tasks use Pyodide/WebAssembly
4. **Output** → Download processed file or preview in browser
5. **State Management** → Zustand stores tool state, undo/redo tracked

---

## 🚀 Performance Optimizations

- **Turbopack** - Fast bundling in development
- **Web Workers** - Non-blocking processing operations
- **WebAssembly** - Near-native performance for heavy operations
- **Static Export** - Minimal server requirements
- **Lazy Loading** - Code splitting for tools
- **IndexedDB** - Efficient file caching

---

## 🔒 Security Features

- **100% Client-Side** - No files leave your device
- **No Backend Storage** - Stateless architecture
- **HTTPS Only** - Encrypted data transmission
- **Input Validation** - Safe file processing
- **Content Security Policy** - Nginx-enforced CSP headers

---

## 📝 Testing Strategy

- **Unit Tests** - Vitest for JavaScript/TypeScript code
- **Component Tests** - Testing Library for React components
- **Property-Based Testing** - Fast-check for edge cases
- **Coverage** - V8 provider for code coverage reporting

---

## 🔧 Configuration Files

| File | Purpose |
|------|---------|
| `next.config.js` | Next.js configuration with webpack WASM support |
| `tsconfig.json` | TypeScript compiler options |
| `vitest.config.ts` | Vitest testing framework config |
| `postcss.config.js` | PostCSS plugins (Tailwind CSS) |
| `middleware.ts` | next-intl internationalization middleware |
| `docker-compose.yml` | Docker service orchestration |
| `nginx.conf` | Nginx reverse proxy configuration |
| `vercel.json` | Vercel deployment configuration |

---

## 📚 Extension System

Browser extension in `extension/` directory:
- **manifest.json** - Extension metadata
- **background.js** - Background service worker
- **popup.js** - Extension UI
- **popup.html/popup.css** - Extension interface

---

## 🎯 Development Workflow

1. **Local Development**: `npm run dev` (Turbopack-powered)
2. **Testing**: `npm run test` or `npm run test:watch`
3. **Linting**: `npm run lint`
4. **Build**: `npm run build`
5. **Production**: `npm start` (static export)
6. **Docker**: `docker-compose up` for containerized deployment

---

## 📖 Additional Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [React Documentation](https://react.dev)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [pdf-lib Documentation](https://pdf-lib.js.org/)
- [PDF.js Documentation](https://mozilla.github.io/pdf.js/)
- [ReactFlow Documentation](https://reactflow.dev/)
- [next-intl Documentation](https://next-intl-docs.vercel.app/)
- [Zustand Documentation](https://github.com/pmndrs/zustand)

---

**Last Updated**: January 22, 2026  
**Status**: Actively Maintained
