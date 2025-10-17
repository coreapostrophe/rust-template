# Rust Template

A production-ready Rust workspace template with best practices, CI/CD, and development container support.

## ✨ Features

- **Cargo Workspace**: Organized multi-crate workspace structure with resolver v2
- **CI/CD Pipeline**: Automated testing, linting, formatting, and security audits via GitHub Actions
- **Development Container**: Pre-configured VS Code devcontainer with Rust tools
- **Code Quality**: Pre-configured Clippy, Rustfmt, and cargo-audit
- **Multi-Version Testing**: Tests against multiple Rust versions (MSRV and stable)

## 🚀 Quick Start

### Using This Template

1. Click the "Use this template" button on GitHub
2. Clone your new repository:
   ```bash
   git clone https://github.com/yourusername/your-repo-name.git
   cd your-repo-name
   ```

3. Build and test:
   ```bash
   cargo build
   cargo test
   ```

### Prerequisites

- Rust 1.75.0 or later
- Cargo (comes with Rust)

## 📁 Project Structure

```
rust-template/
├── .devcontainer/          # VS Code development container configuration
├── .github/
│   └── workflows/
│       └── ci.yml          # GitHub Actions CI/CD pipeline
├── crates/
│   └── foundations/        # Example workspace crate
│       ├── Cargo.toml
│       └── src/
│           └── lib.rs
├── Cargo.toml              # Workspace root configuration
├── Cargo.lock
├── .gitignore
└── README.md
```

## 🛠️ Development

### Building

```bash
# Build all crates
cargo build

# Build in release mode
cargo build --release
```

### Testing

```bash
# Run all tests
cargo test

# Run tests with output
cargo test -- --nocapture
```

### Code Quality

```bash
# Format code
cargo fmt

# Check formatting (CI mode)
cargo fmt --all -- --check

# Run Clippy lints
cargo clippy --all-targets --all-features -- -D warnings

# Security audit
cargo install cargo-audit
cargo audit
```

### Adding New Crates

Add new crates to the workspace:

```bash
cargo new --lib crates/your-crate-name
```

The workspace is configured to automatically include all crates in the `crates/` directory.

## 🐳 Development Container

This template includes a VS Code devcontainer configuration for a consistent development environment.

### Using the Dev Container

1. Install [Docker](https://www.docker.com/products/docker-desktop) and [VS Code](https://code.visualstudio.com/)
2. Install the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
3. Open the project in VS Code
4. Click "Reopen in Container" when prompted

The container includes:
- Rust toolchain
- rust-analyzer
- Clippy and Rustfmt
- Git and GitHub CLI
- VS Code extensions for Rust development

## 🔄 CI/CD

The GitHub Actions workflow automatically runs on push and pull requests to `main` and `develop` branches.

### CI Pipeline Includes

- **Testing**: Runs tests against multiple Rust versions (1.75.0, 1.76.0, stable)
- **Formatting**: Ensures code follows Rust style guidelines
- **Linting**: Runs Clippy with warnings treated as errors
- **Security**: Runs cargo-audit to check for security vulnerabilities
- **Build Verification**: Validates both debug and release builds
- **Caching**: Optimizes build times with cargo registry caching

## 📝 Customization

### Update Project Name

1. Update `Cargo.toml` workspace configuration
2. Rename crates in `crates/` directory
3. Update crate names in `crates/*/Cargo.toml`
4. Update references in this README

### Adjust MSRV (Minimum Supported Rust Version)

Edit `.github/workflows/ci.yml` and modify the Rust versions in the matrix:

```yaml
strategy:
  matrix:
    rust: [1.75.0, 1.76.0, stable]  # Adjust versions as needed
```

## 📄 License

This template is provided as-is for you to use in your own projects. Add your own license as appropriate.

## 🤝 Contributing

Contributions are welcome! Feel free to:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 💡 Tips

- Use `cargo watch` for automatic rebuilding during development: `cargo install cargo-watch && cargo watch -x check`
- Run `cargo doc --open` to generate and view documentation
- Keep dependencies updated with `cargo update`
- Use workspace dependencies in `Cargo.toml` for shared dependencies across crates

---

Happy coding! 🦀