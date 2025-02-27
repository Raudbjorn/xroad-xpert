# Hosting Your X-Road X-pert Website on GitHub Pages

This guide will walk you through hosting your `xro.ad` website on GitHub Pages, which provides free hosting directly from your GitHub repository.

## Prerequisites
- A GitHub account
- Git installed on your computer
- Your website files (HTML, CSS, JS, images, etc.)

## Step 1: Create a New GitHub Repository

1. Log in to your GitHub account
2. Click the "+" in the top-right corner and select "New repository"
3. Name your repository `xroad-xpert` (or any name you prefer)
4. Make sure the repository is set to "Public"
5. Click "Create repository"

## Step 2: Prepare Your Website Files

1. Save the HTML file I provided as `index.html` in a folder on your computer
2. Create any other files you want to include (images, additional pages, etc.)

## Step 3: Initialize and Push Your Repository

Open your terminal or command prompt and run the following commands:

```bash
# Navigate to your website folder
cd path/to/your/website/folder

# Initialize a new Git repository
git init

# Add all files to the repository
git add .

# Commit your changes
git commit -m "Initial commit of X-Road X-pert website"

# Add your GitHub repository as a remote
git remote add origin https://github.com/YOUR-USERNAME/xroad-xpert.git

# Push your files to GitHub
git push -u origin main
```

Note: If you're using an older version of Git, you might need to use `master` instead of `main`.

## Step 4: Configure GitHub Pages

1. Go to your repository on GitHub
2. Click "Settings" (tab near the top)
3. Scroll down to the "GitHub Pages" section
4. Under "Source", select "main" (or "master") branch
5. Click "Save"

GitHub will show you the URL where your site is published (usually `https://YOUR-USERNAME.github.io/xroad-xpert/`).

## Step 5: Set Up Your Custom Domain (xro.ad)

### 5.1 Add Your Custom Domain in GitHub

1. In your repository settings, under the "GitHub Pages" section
2. Enter `xro.ad` in the "Custom domain" field
3. Click "Save"
4. Check the "Enforce HTTPS" option if available (recommended)

### 5.2 Configure Your Domain DNS Settings

You'll need to configure your domain registrar's DNS settings. Here's what to add:

#### Option 1: Apex Domain Configuration
If you want to use `xro.ad` directly (without www):

Add these A records pointing to GitHub Pages servers:
```
A  @  185.199.108.153
A  @  185.199.109.153
A  @  185.199.110.153
A  @  185.199.111.153
```

#### Option 2: Subdomain Configuration
If you want to use `www.xro.ad`:

Add a CNAME record:
```
CNAME  www  YOUR-USERNAME.github.io.
```

#### Option 3: Both Apex and Subdomain (recommended)
For the most flexibility, set up both:
- Configure the A records as in Option 1
- Add this CNAME record:
  ```
  CNAME  www  YOUR-USERNAME.github.io.
  ```

## Step 6: Verify Your Domain

1. GitHub will automatically add a file called `CNAME` to your repository
2. It may take several hours for DNS changes to propagate
3. Once complete, your website will be accessible at your custom domain

## Updating Your Website

When you want to make changes to your website:

1. Make the changes to your local files
2. Commit and push the changes to GitHub:
   ```bash
   git add .
   git commit -m "Describe your changes"
   git push
   ```
3. GitHub Pages will automatically update your site

## Additional Tips

1. **Custom 404 Page**: Create a file named `404.html` to customize the error page visitors see if they go to a nonexistent URL on your site.

2. **Jekyll Support**: GitHub Pages supports Jekyll, a static site generator. If you want to use Jekyll, you can structure your repository accordingly.

3. **Enforce HTTPS**: Always keep the "Enforce HTTPS" option enabled for security.

4. **Repository vs. User/Organization Site**: If you want your site to appear at `YOUR-USERNAME.github.io` (without a repository name in the URL), name your repository `YOUR-USERNAME.github.io`.

5. **GitHub Actions**: For more advanced deployment workflows, consider using GitHub Actions.

## Troubleshooting

- If your custom domain isn't working, make sure DNS settings have propagated (can take up to 48 hours)
- Verify that your CNAME file contains only your domain name and no other text
- Check GitHub status page if you experience any unexpected issues

## Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [Troubleshooting custom domains](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/troubleshooting-custom-domains-and-github-pages)
