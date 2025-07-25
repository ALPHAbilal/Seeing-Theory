# AI Code Generation Platforms: Comprehensive Research & Implementation Details

## Table of Contents
1. [Lovable.dev Implementation](#lovabledev-implementation)
2. [v0.dev by Vercel Implementation](#v0dev-by-vercel-implementation)
3. [Bolt.new with WebContainers](#boltnew-with-webcontainers)
4. [Cursor AI Architecture](#cursor-ai-architecture)
5. [Building Your Educational Platform](#building-your-educational-platform)

---

## Lovable.dev Implementation

### Core Architecture
- **AI Model**: Anthropic's Claude (primary), with GPT-4 and Google Gemini support
- **Frontend Stack**: React/TypeScript with Tailwind CSS, Vite, and shadcn/ui
- **Backend**: Supabase (database, auth, real-time features)
- **Infrastructure**: Fly.io containers using Firecracker MicroVMs

### System Prompts (Leaked)
- Available on GitHub: `x1xhlol/system-prompts-and-models-of-ai-tools`
- 8,500+ lines of system prompts
- XML-like tag structure: `<tool_calling>`, `<making_code_changes>`, `<web_development>`
- Strict JSON schema adherence
- Console log access for debugging

### Key Features
1. **Agent Mode (Beta)**: Autonomous codebase search and file reading
2. **Context Management**: Maintains understanding across 50+ prompts
3. **Error Handling**:
   - React error boundaries
   - Exponential backoff for retries
   - Circuit breakers
   - Graceful fallback mechanisms

### Technical Insights
- Simplified from multi-agent to single-agent architecture
- $17M ARR in 90 days
- 1,000+ projects built daily
- Separate micro VMs per user for isolation

### API Integration Pattern
```javascript
// Natural language to code
"Set up Stripe for payments" → Complete Stripe integration code
// OpenAPI Support
Automatic integration with ChatGPT, Airtable, Stripe APIs
```

---

## v0.dev by Vercel Implementation

### Composite Model Architecture
- **Base Models**: 
  - Anthropic Sonnet 3.7 (v0-1.0-md)
  - Anthropic Sonnet 4 (v0-1.5-md)
- **Custom Models**:
  - `vercel-autofixer-01`: Trained with Fireworks AI using RFT
  - Real-time error checking and linting

### System Prompts (Leaked)
Found on multiple GitHub repositories:
- `github.com/2-fly-4-ai/V0-system-prompt`
- `github.com/sharkqwy/v0prompt`
- `github.com/jujumilk3/leaked-system-prompts`

Key components:
```markdown
- Identifies as "advanced AI coding assistant created by Vercel"
- Uses MDX format for responses
- Access to custom components: CodeProject, QuickEdit, MoveFile
- Always uses shadcn/ui and Tailwind CSS
- Implements <Thinking /> component before responses
```

### Code Generation System
```tsx
// Generation format
```tsx project="Project Name" file="file_path" type="react"
// Complete React component
export default function Component() {
  // Always complete, copy-pastable code
}
```

### Training & Fine-Tuning
- Mix of custom code, open-source, and synthetic datasets
- Reinforcement Fine-Tuning (RFT) with Fireworks AI
- AutoFix model: 10-40x faster than GPT-4o-mini
- Compilation-based evaluation

### Technical Implementation
- **SDK**: `@ai-sdk/vercel` and `v0-sdk` npm packages
- **API**: OpenAI-compatible at `https://api.v0.dev/v1`
- **Models Available**:
  - v0-1.0-md (Sonnet 3.7)
  - v0-1.5-md (Sonnet 4)
  - v0-1.5-lg (larger variant)

---

## Bolt.new with WebContainers

### Core Architecture
- **Frontend**: Remix Run framework
- **Deployment**: CloudFlare Pages and Workers
- **AI Integration**: Vercel AI SDK
- **Runtime**: WebContainers API (browser-based Node.js)

### WebContainers Integration
```javascript
import { WebContainer } from '@webcontainer/api';

// Initialize WebContainer
const webcontainerInstance = await WebContainer.boot();

// Mount filesystem
await webcontainerInstance.mount({
  'package.json': {
    file: {
      contents: JSON.stringify(packageJson, null, 2)
    }
  },
  'src/index.js': {
    file: {
      contents: 'console.log("Hello World");'
    }
  }
});

// Spawn processes
const process = await webcontainerInstance.spawn('npm', ['install']);
process.output.pipeTo(new WritableStream({
  write(data) {
    terminal.write(data);
  }
}));
```

### AI Agent Control
The AI has complete control over:
- Filesystem operations
- Node.js server execution
- Package management (npm, yarn, pnpm)
- Terminal command execution
- Browser console access

### Open-Source bolt.diy
Repository: `stackblitz-labs/bolt.diy`

Key directories:
- `app/lib/webcontainer/`: WebContainer integration
- `app/lib/common/prompts/`: AI system prompts
- `app/components/workbench/`: IDE interface
- `app/components/chat/`: AI chat interface

Multi-LLM Support:
- OpenAI, Anthropic, Ollama
- Gemini, Mistral, Groq
- HuggingFace, DeepSeek

### Security & Performance
- Browser sandbox isolation
- WebAssembly-based execution
- 20% faster builds than local
- 5x faster package installations
- Zero infrastructure risk

---

## Cursor AI Architecture

### Anyrun Orchestrator (Rust)
- Written entirely in Rust for performance
- Amazon EC2 + AWS Firecracker for virtualization
- Bridges TypeScript business logic with Rust
- Turbopuffer database for encrypted file storage
- Merkle Tree-based sync engine

### RAG Implementation
```python
# Core components
- Vector embeddings in Qdrant database
- Syntax-level chunking with tree-sitter
- GPU-accelerated embedding generation
- <1 minute indexing for mid-sized codebases

# Search architecture
- Semantic search + BM25 keyword search
- HyDE (Hypothetical Document Embeddings)
- Natural language annotations on code chunks
```

### Custom Models
1. **Llama-3-70b-ft**: Matches Claude-3 Opus performance
2. **Tab Model**: Multi-file suggestions
3. **Fast-apply Model**: 1000 tokens/second for editing

Infrastructure:
- Tens of thousands of NVIDIA H100 GPUs
- Azure GPUs for inference only
- Knowledge distillation for smaller models

### Context Management
- Models handle up to 200k tokens
- Merkle tree-based codebase sync
- High-latency sync: every 3 minutes
- Low-latency sync: <1 second for suggestions

### Tree-Sitter Integration
```javascript
// AST-based code splitting
- Depth-first traversal
- Sibling node merging
- Incremental parsing
- Path obfuscation for security
```

### Performance Metrics
- $500M+ annual revenue
- 1000 tokens/second editing
- Sub-second tab completions
- Efficient large codebase handling

---

## Building Your Educational Platform

### Recommended Architecture

```yaml
Frontend Platform:
  - Next.js 14 (main platform)
  - D3.js (generated visualizations)
  - Tailwind CSS (styling)

AI Layer:
  - Claude 3.5 Sonnet API
  - Custom educational prompts
  - Subject-specific templates

Execution Environment:
  - WebContainers API (like Bolt)
  - Or Sandpack (CodeSandbox alternative)

Backend:
  - Supabase (auth + database)
  - Vercel (hosting)
  - GitHub (version control)
```

### Implementation Strategy

#### Phase 1: MVP (3 months)
1. Fork bolt.diy open-source starter
2. Integrate Claude API
3. Build 10 physics/math templates
4. Create prompt → visualization flow

#### Phase 2: Scale (6 months)
1. Add more subjects
2. Build teacher dashboard
3. Add customization options
4. Implement error correction

#### Phase 3: Monetize (9 months)
1. School licenses
2. Premium templates
3. LMS integration
4. White-label options

### Key Differentiators
1. **Education-First**: Subject-specific visualizations
2. **Simple Output**: Clean HTML/JS/CSS like Seeing-Theory
3. **Teacher Tools**: Progress tracking, customization
4. **Pre-built Components**: Common educational patterns

### Technical Implementation Example

```javascript
// Educational Playground Architecture
const EducationalPlayground = {
  // Subject Templates
  templates: {
    physics: ['pendulum', 'waves', 'circuits'],
    chemistry: ['molecules', 'reactions', 'periodic-table'],
    math: ['graphs', 'geometry', 'calculus']
  },
  
  // AI Configuration
  ai: {
    model: 'Claude 3.5 Sonnet',
    customPrompts: loadEducationalPrompts(),
    context: 'Generate D3.js educational visualizations'
  },
  
  // Execution Environment
  runtime: {
    environment: 'WebContainers',
    libraries: ['D3.js', 'jStat', 'MathJax'],
    sandbox: true
  }
};
```

### Cost-Effective Approach
1. Use bolt.diy as foundation (open-source)
2. Add educational template layer
3. Focus on prompt engineering
4. Start with single subject proof-of-concept

---

## Additional Resources

### Open-Source Repositories
- `stackblitz-labs/bolt.diy` - Bolt alternative
- `x1xhlol/system-prompts-and-models-of-ai-tools` - Leaked prompts
- WebContainers starter kits

### Key Technologies to Study
1. WebContainers API
2. Vercel AI SDK
3. Tree-sitter for code parsing
4. Qdrant vector database
5. D3.js for visualizations

### Learning Path
1. Study bolt.diy implementation
2. Understand WebContainers API
3. Learn prompt engineering
4. Build simple MVP
5. Iterate based on user feedback

---

*Last Updated: July 2025*