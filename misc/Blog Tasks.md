
## 1. Discovery & Distribution

- ~~**RSS Feed Navigation (`/index.xml`)**:~~
    
    - ~~_Why_: Independent readers and feed aggregators (Feedly, NetNewsWire, Miniflux) depend on RSS.~~
        
    - ~~_How_: Hugo generates `/index.xml` automatically. Add a visible `RSS` link or icon in your main navigation or footer so visitors can easily copy and subscribe.~~
        
- ~~**Search Engine Verification & Sitemaps**:~~
    
    - ~~_Why_: Ensures search crawlers index new posts instantly.~~
        
    - ~~_How_: Keep `sitemap.xml` enabled in `hugo.toml` and submit it to Google Search Console and Bing Webmaster Tools.~~
        
- ~~**Taxonomy Index Pages (Tags & Categories)**:~~
    
    - ~~_Why_: Allows readers to browse related writing by topic (e.g., tech, essays, off-grid living).~~
        
    - ~~_How_: Define tags in your TOML front matter (`tags = ['linux', 'writing']`) and ensure your theme displays category/tag archive links.~~
        

## 2. Reading Experience & UI

- ~~**Dark / Light Mode Toggle**:~~
    
    - ~~_Why_: Improves accessibility and readability across different devices and lighting environments.~~
        
    - ~~_How_: Most modern Hugo themes (like PaperMod) include a native CSS/JS toggle out of the box.~~
        
- ~~**Estimated Reading Time & Publication Dates**:~~
    
    - ~~_Why_: Gives readers context on post length and currency before diving in.~~
        
    - ~~_How_: Enable `showReadingTime = true` in your theme parameters (`params`).~~
        
- ~~**Syntax Highlighting for Code Blocks**:~~
    
    - ~~_Why_: Makes code snippets clean and readable.~~
        
    - ~~_How_: Hugo includes native Chroma syntax highlighting. You can configure color palettes (e.g., `monokai`, `dracula`, `nord`) directly inside `hugo.toml`:~~
        
        ~~Ini, TOML~~
        
        ```
        [markup.highlight]
          style = 'dracula'
          lineNos = true
        ```
        

## 3. Privacy-Friendly Analytics & Interaction

- ~~**Lightweight, Privacy-Focused Analytics**:~~
    
    - ~~_Why_: Track visitor counts and popular posts without tracking cookies, popups, or invasive user tracking.~~
        
    - ~~_How_:~~
        
        - ~~**Cloudflare Web Analytics** (Free, built into your Cloudflare dashboard, zero setup scripts needed).~~
            
        - ~~**Plausible** or **Umami** (Minimal JS snippet, privacy-compliant, open-source).~~
            
- ~~**Static Commenting or Webmentions** (Optional):~~
    
    - ~~_Why_: Receive feedback without bloated comment plugins like Disqus.~~
        
    - ~~_How_: Use **Giscus** (uses GitHub Discussions for comment storage), **Remark42**, or standard **Webmentions** (`indieweb.org`).~~
        

## 4. Performance & Reliability

- **Custom 404 Page (`content/404.md`)**:
    
    - _Why_: Guides visitors back to your home page if they land on broken links or outdated URLs.
        
    - _How_: Create a `content/404.md` file with a friendly message and a link back home.
        
- **Asset Optimization (Page Bundles)**:
    
    - _Why_: Keeps image file sizes small and load times instant.
        
    - _How_: Store images inside post page bundles so Hugo's built-in image processing can automatically compress and resize them on build.

### How to Browse and Switch Themes

You can view live previews of hundreds of options on the official [Hugo Themes Directory](https://themes.gohugo.io/).

  

Switching themes is straightforward: if you ever want to swap out the one you are using, you just remove the old theme folder, add a new one as a Git submodule, and update the `theme = "new-theme-name"` line in your `hugo.toml` configuration file.