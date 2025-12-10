# Tillerstead Site

## Ruby environment (Windows via RubyInstaller)
- Install [RubyInstaller 3.1+ with MSYS2](https://rubyinstaller.org/downloads/) and select option 3 to run `ridk install` when prompted so the DevKit and build tooling are configured.
- From a PowerShell terminal in the project root, run `powershell -ExecutionPolicy Bypass -File scripts/activate-ruby.ps1`. The helper locates your RubyInstaller installation, sources `ridk`/`setrbvars`, and installs Bundler `2.4.19` if it is missing.
- `scripts/activate-ruby.ps1` now auto-detects RubyInstaller 3.x installs (including 3.4) in common locations even if `ruby.exe` is not yet on your `PATH`.
- Re-run `scripts/activate-ruby.ps1` any time you open a fresh shell so the Ruby toolchain is on your `PATH` before invoking Bundler or Jekyll.
- If Ruby is installed in a non-standard directory, provide the path manually: `powershell -ExecutionPolicy Bypass -File scripts/activate-ruby.ps1 -RubyRoot 'D:\Tools\Ruby32-x64'`.

### Typical workflow
```powershell
# Activate Ruby (installs Bundler on first run)
powershell -ExecutionPolicy Bypass -File scripts/activate-ruby.ps1

# Install Ruby gems / Node dependencies once
bundle install
npm install

# Build the site
npm run build:site   # runs Sass build + bundle exec jekyll build
```

If `scripts/activate-ruby.ps1` cannot find RubyInstaller it will stop with a helpful message that includes the download URL. Once activated, the terminal echoes the Ruby version so you know the environment is ready.

## VS Code workflow
1. Install the recommended extensions when VS Code prompts (including the Ruby LSP). Once accepted, every new integrated terminal defaults to **Ruby Dev Shell**, which cd's to the workspace and runs `scripts/activate-ruby.ps1` automatically so Bundler/Jekyll are always on the `PATH`.
2. Use the pre-wired tasks (Terminal > Run Task...) for repeatable commands:
   - `Setup > install everything` runs `bundle install` and `npm install`.
   - `Build > full site` mirrors `npm run build:site` with the Ruby env preloaded.
   - `Serve > jekyll --livereload` starts `bundle exec jekyll serve --incremental --livereload` and stays attached so you can stop it with Ctrl+C.
3. If a shell is still "looking for Ruby", open the command palette > `Terminal: Select Default Profile` > choose **Ruby Dev Shell**, then create a fresh terminal. Existing panes can be fixed by running `powershell -ExecutionPolicy Bypass -File scripts/activate-ruby.ps1`.
4. Having trouble getting the Ruby LSP extension to activate? Follow the checklist in [`RUBY_LSP_TROUBLESHOOTING.md`](./RUBY_LSP_TROUBLESHOOTING.md) to confirm Ruby is available to VS Code, the correct version manager is configured, and macOS/Windows permissions are granted.

# Tillerstead.com

A fast, client-safe static site for Tillerstead LLC, built with Jekyll and a handcrafted design system. The repo is tuned for long-term maintainability, SEO, and straightforward authoring by developers or content editors.

## At a Glance
- **Platform:** Jekyll static site with custom layouts and includes—no third-party themes.
- **Styling:** SCSS sources in [`_sass`](./_sass) compiled to [`assets/css`](assets/css).
- **Content:** Markdown posts and pages in [`_posts`](./_posts) and [`pages`](./pages) with data-driven sections in [`_data`](./_data).
- **Templates:** Layouts and shared fragments live in [`_layouts`](./_layouts) and [`_includes`](./_includes).
- **Performance & SEO:** Minified CSS, sitemap, robots directives, and tightly written meta data in [`_config.yml`](./_config.yml) and [`manifest.webmanifest`](./manifest.webmanifest).
- **Deployment:** Suitable for static hosting (Netlify/GitHub Pages); build artifacts live in `_site/` when generated.

## Prerequisites
- **Ruby & Bundler** for Jekyll (`bundle install`).
- **Node.js & npm** for tooling (`npm install`).
- **Sass** and **Sharp** are installed via `npm install`; no global installs required.

## Getting Started
1. Install dependencies:
   - `bundle install`
   - `npm install`
2. Build CSS once:
   - `npm run build:css`
3. Start a local site:
   - `bundle exec jekyll serve`
4. Visit `http://127.0.0.1:4000` to preview.

## Development Workflow
- **Style changes:** Edit `_sass/theme.scss` (and partials) then run `npm run watch:css` during development or `npm run build:css` for a one-off build.
- **Content updates:** Add or edit Markdown files in `_posts/` for dated content or `pages/` for evergreen pages. Use `_data/` YAML/JSON for repeatable content blocks.
- **Templates:** Modify `_layouts/` for page-level wrappers and `_includes/` for reusable fragments (headers, footers, CTAs).
- **Images:** Use `npm run images:webp` to generate WebP variants in-place under `assets/`.

## Quality & Linting
- Run `npm run lint` before committing to check JavaScript, HTML, and front-end conventions.
- Use `npm run format` to apply Prettier formatting across the project.
- The `build` script keeps compiled CSS compressed for fast page loads.

## SEO & Accessibility Practices
- Page metadata defaults live in `_config.yml`; keep titles, descriptions, and keyword lists relevant to South Jersey property services.
- Prefer semantic HTML in `_layouts/` and `_includes/` for accessibility; linting flags common ARIA issues.
- Keep image alt text descriptive and leverage WebP output for performance.

## Production Build
- Generate a full site (including CSS compilation) with:
  ```sh
  npm run build:site
  ```
- The built site appears in `_site/` and is ready to deploy to any static host (Netlify config is available in `netlify.toml`).

## Project Structure
```
assets/           # Compiled and static assets (CSS, images, fonts)
_sass/            # Source SCSS for the design system
_includes/        # Reusable HTML partials (navigation, footer, CTAs)
_layouts/         # Page and post layout templates
_posts/           # Blog or update entries (Markdown)
pages/            # Standalone pages (Markdown/HTML)
_data/            # YAML/JSON data powering dynamic sections
scripts/          # Utility scripts (e.g., image conversion)
test/             # Automated tests or fixtures
```

## Contributing
1. Create a feature branch.
2. Keep commits focused and linted (`npm run lint`).
3. Open a pull request with a clear summary and testing notes.

## License
This project is licensed under the MIT License; see [`LICENSE`](LICENSE) for details.
