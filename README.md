# Tensor Lang

**Tensor Lang** is a new domain-specific programming language designed for high-performance linear algebra and tensor-based computation. Its primary goal is to be an **explicit**, **efficient**, and **extensible** language that makes no compromises on transparency, expressiveness, or performance.

---

## Vision

Tensor Lang aims to:

- Be **explicit** by default. Nothing is hidden from the user. There's no implicit `self`, no magical inheritance, no compiler tricks you can't trace. If you write `A + B`, it maps to a well-defined function call (e.g. `Add.add(A, B)`), and the language provides tools to *see* that.
- Feel **approachable and expressive** like Python, but with curly-brace scoping, static typing, and true performance control.
- Make **tensors first-class citizens**. Every array, matrix, and vector is a tensor. Shapes and types are part of the type system, making it easier to catch bugs and optimize early.
- Be **extensible by design**. From user-defined types and traits to C/C++ or GPU-backed native modules and MLIR-based plugins, you can drop down to low-level performance layers when needed.

Tensor Lang is especially suited for users working in:
- Machine learning & scientific computing
- Compiler research
- High-performance computing
- Systems programming for numerical applications

---

## Language Highlights

- **Statically typed**, with support for gradual typing and shape annotations.
- **No hidden behavior**: methods and operators are explicit, and users can inspect desugared forms.
- **MLIR and LLVM-backed**, enabling high-performance backend optimizations and GPU integration.
- **Custom operators and traits** are fully supported.
- **User-extensible via native modules**, runtime plugins, or dialect-based IR extensions.

---

## Example

```ts
// Define a simple tensor type

type LinearLayer {
    weights: float[output x input],
    bias: float[output]
}

// Forward pass function

def forward(layer: LinearLayer, x: float[input]) -> float[output] {
    wx: float[output] = matmul(layer.weights, x);
    return wx + layer.bias;
}

// Desugared version of `wx + layer.bias`
// -> Add.add(wx, layer.bias)
```

---

## Development Roadmap / TODOs

This project is in early stages. Here are the planned phases of development:

### Language Design
- [ ] Formalize grammar (tokens, syntax, operators, types)
- [ ] Define core type system: tensors, shapes, traits, modules
- [ ] Design standard library primitives (math, tensor ops, I/O)

### Frontend
- [ ] Implement lexer & parser
- [ ] Build an AST structure
- [ ] Add semantic analysis & type checking
- [ ] Implement desugaring and sugar-inspection tools

### Intermediate Representation
- [ ] Lower AST to MLIR
- [ ] Define trait/operator rewriting and inlining passes
- [ ] Integrate shape/type inference into IR passes

### Backend
- [ ] Lower MLIR to LLVM (CPU)
- [ ] Add GPU support via MLIR's GPU dialect / NVVM / ROCDL
- [ ] JIT execution engine (MLIR + LLVM)
- [ ] AOT compilation support (shared libraries, binaries)

### Extensibility
- [ ] Define module system for native extensions
- [ ] Allow user-defined dialects to be imported as modules
- [ ] Support `extern` functions backed by C/C++ or CUDA
- [ ] Build runtime hooks for custom memory allocators, devices

### Tooling
- [ ] REPL with desugared-form hints
- [ ] LSP for IDEs (hover tooltips, diagnostics, autocomplete)

---

## License
MIT

---

## Get Involved
Interested in contributing ideas or code? Open an issue, start a discussion, or reach out directly. Tensor Lang is built for clarity, performance, and long-term experimentation. Let's make something powerful together.

