Recommended Method: Hugo + Git (100% Free & Open Source)

Setting up a blog with **Hugo** and **Git** gives you a lightning-fast, completely independent site that you fully control. Here is a step-by-step guide to getting your local site running and connected to Git.

  

### Step 1: Install Prerequisites

Before you begin, ensure you have **Git** and **Hugo** installed on your computer.

  

- **macOS (via Homebrew):** `brew install hugo git`
    
      
    
- **Windows (via Winget):** `winget install Hugo.Hugo.Extended` and `winget install Git.Git`
    
      
    
- **Linux (Ubuntu/Debian):** `sudo apt install hugo git`
    
      
    

### Step 2: Create Your Hugo Site

Open your terminal (or command prompt) and run the following command to generate a new Hugo site folder:

  

Bash

```
hugo new site my-blog
cd my-blog
```

Initialize a local Git repository inside your new site folder:

  

Bash

```
git init
```

### Step 3: Add a Theme

Hugo requires a theme to style your site. You can add one as a Git submodule so it stays linked. For example, let's add the popular _PaperMod_ theme:

  

Bash

```
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/papermod
```

Next, tell Hugo to use this theme by opening your `hugo.toml` (or `config.toml`) file in a text editor and adding this line at the bottom:

  

Ini, TOML

```
theme = "papermod"
```

### Step 4: Create Your First Post

Hugo makes it easy to generate content templates from the command line:

  

Bash

```
hugo new content content/posts/my-first-post.md
```

Open the newly created file (`content/posts/my-first-post.md`) in your text editor. Change `draft = true` to `draft = false`, and add some Markdown text below the front matter header:

  

Markdown

```
---
title: "My First Post"
date: 2026-10-09T14:00:00-06:00
draft: false
---

Hello world! This is my independent blog powered by Hugo and Git.
```

### Step 5: Test Locally

To preview your blog live in your browser, run:

  

Bash

```
hugo server
```

Open your browser and navigate to `http://localhost:1313`. Any changes you make to your Markdown files will instantly update on the page.

  

### Step 6: Commit Your Code to Git

Once you are happy with your setup, stage and commit your files to Git:

  

Bash

```
git add .
git commit -m "Initial commit with first blog post"
```


---


To host your Hugo blog online for free without relying on corporate platforms, the most robust approach is using **GitHub** for your code repository and **Cloudflare Pages** for free global hosting.

  

**1.Create a GitHub Repository:**Cloudflare needs to pull your code from somewhere.

Go to [GitHub](https://github.com), log in, and create a **new empty repository** (do not add a README, .gitignore, or license). Name it whatever you like (e.g., `my-blog`).

  

**2.Push Your Local Code to GitHub:**Link your terminal project to the remote repository.

Run the following commands in your terminal inside your local `my-blog` folder (replace `YOUR_USERNAME` and `my-blog` with your actual details):

  

Bash

```
git remote add origin https://github.com/YOUR_USERNAME/my-blog.git
git branch -M main
git push -u origin main
```

_Verification:_ Refresh your GitHub repository page in your browser; you should see your project files and the `themes` submodule folder listed.

  

**3.Connect to Cloudflare Pages:**Set up free automated hosting.

1. Log into your [Cloudflare Dashboard](https://dash.cloudflare.com) (sign up for a free account if you do not have one).
    
      
    
2. In the left sidebar or home panel, select **Workers & Pages**.
    
      
    
3. Click **Create application** $\rightarrow$ choose the **Pages** tab $\rightarrow$ click **Connect to Git**.
    
      
    
4. Link your GitHub account and select your newly created `my-blog` repository.
    
      
    

**4.Configure Build Settings:**Tell Cloudflare how to compile Hugo.

In the **Set up builds and deployments** section, use these exact settings:

  

- **Production branch:** `main`
    
      
    
- **Build command:** `hugo`
    
      
    
- **Build output directory:** `public`
    
      
    

Expand **Environment variables**, add a new variable:

  

- **Variable name:** `HUGO_VERSION`
    
      
    
- **Value:** `0.140.0` (or whichever recent version of Hugo you installed locally; run `hugo version` in your terminal to check).
    
      
    

Click **Save and Deploy**.

  

Cloudflare will compile your Markdown into static HTML files and publish your site live on a free `*.pages.dev` subdomain. Whenever you write a new post locally, just commit it and push it to GitHub (`git add .`, `git commit -m "New post"`, `git push`), and Cloudflare will automatically rebuild and update your live site within seconds.

---

To attach a custom domain to your Cloudflare Pages deployment, you will need to update your Hugo configuration and add the domain inside Cloudflare.

  

### Step 1: Update Your Hugo Configuration

Open your `hugo.toml` (or `config.toml`) file and update the `baseURL` to match your custom domain:

  

Ini, TOML

```
baseURL = "https://your-custom-domain.com/"
```

_(Save the file, then commit and push the change to GitHub: `git add .`, `git commit -m "Update base URL"`, `git push`)_.

  

### Step 2: Add the Custom Domain in Cloudflare

1. Log into your [Cloudflare Dashboard](https://dash.cloudflare.com) and go to **Workers & Pages**.
    
      
    
2. Click on your Hugo project, then select the **Custom domains** tab.
    
      
    
3. Click **Set up a domain** (or **Add custom domain**) and enter your domain name.
    
      
    
4. Follow the on-screen prompts:
    
      
    - **If your domain's DNS is already on Cloudflare:** Cloudflare will automatically configure the required DNS records for you.
        
          
        
    - **If your domain is registered elsewhere (e.g., Namecheap, GoDaddy):** Cloudflare will give you specific CNAME records to copy and paste into your domain registrar's DNS settings.
        
          
        

Once verified, Cloudflare will automatically provision an SSL certificate, and your independent blog will be live on your own custom domain with global HTTPS.

---

Hugo has a massive, active directory containing hundreds of open-source themes. Because Hugo builds static sites, themes range from ultra-minimalist text diaries to feature-rich documentation hubs and magazine layouts.

  

The primary styles available include:

  

### 1. Minimalist & Text-Focused (Best for Personal Blogs)

- **PaperMod:** The most popular Hugo theme. It is blazing fast, clean, features a built-in light/dark mode switch, supports tag navigation, and has zero heavy JavaScript bloat.
    
      
    
- **Paper:** A stripped-down, ultra-minimalist alternative designed purely for writers who want zero visual distraction and maximum readability.
    
      
    
- **Terminal:** Gives your blog a retro command-line aesthetic with a blinking cursor and monospaced typography.
    
      
    

### 2. Modern & Feature-Rich (Best for Portfolios & Tech)

- **Blowfish:** A modern, highly customizable theme built on Tailwind CSS. It supports advanced features like built-in image galleries, timeline layouts, reading time estimators, and support for interactive charts or math equations.
    
      
    
- **Stack:** Features a card-based layout inspired by modern dashboard and social media designs, making it look distinct from a standard chronological blog.
    
      
    
- **Hugo Blox (formerly Wowchemy):** A modular framework that lets you build landing pages, academic portfolios, and resume sites alongside a blog section using drag-and-drop structural blocks.
    
      
    

### 3. Documentation & Knowledge Bases (Best for Technical Writing)

- **Book:** Styled after GitBook, this creates a clean, sidebar-driven navigation layout that is ideal if your blog involves structured guides, tutorials, or documentation.
    
      
    
- **Docsy / Doks:** Professional, heavily structured themes used by open-source projects requiring multi-page hierarchies, fast search bars, and code syntax highlighting.
    
      
    

### How to Browse and Switch Themes

You can view live previews of hundreds of options on the official [Hugo Themes Directory](https://themes.gohugo.io/).

  

Switching themes is straightforward: if you ever want to swap out the one you are using, you just remove the old theme folder, add a new one as a Git submodule, and update the `theme = "new-theme-name"` line in your `hugo.toml` configuration file.