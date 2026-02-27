# Academic Pages
**Academic Pages is a GitHub Pages template for personal and professional portfolio-oriented websites.**

![Academic Pages template example](images/themes/homepage-light.png "Academic Pages template example")

# Getting Started


1. Register a GitHub account if you don't have one and confirm your e-mail (required!)
1. Click the "Use this template" button in the top right.
1. On the "New repository" page, enter your public repository name as "[your GitHub username].github.io", which will also be your website's URL.
1. Set site-wide configuration and add your content.
1. Upload any files (like PDFs, .zip files, etc.) to the `files/` directory. They will appear at https://[your GitHub username].github.io/files/example.pdf.
1. Check status by going to the repository settings, in the "GitHub pages" section
1. (Optional) Use the Jupyter notebooks or python scripts in the `markdown_generator` folder to generate markdown files for publications and talks from a TSV file.

See more info at https://academicpages.github.io/

## Running locally

When you are initially working on your website, it is very useful to be able to preview the changes locally before pushing them to GitHub. To work locally you will need to:

1. Clone the repository and made updates as detailed above.

### Using a different IDE
1. Make sure you have ruby-dev, bundler, and nodejs installed
    
    On most Linux distribution and [Windows Subsystem Linux](https://learn.microsoft.com/en-us/windows/wsl/about) the command is:
    ```bash
    sudo apt install ruby-dev ruby-bundler nodejs
    ```
    If you see error `Unable to locate package ruby-bundler`, `Unable to locate package nodejs `, run the following:
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```
    then try run `sudo apt install ruby-dev ruby-bundler nodejs` again.

    On MacOS the commands are:
    ```bash
    brew install ruby
    brew install node
    gem install bundler
    ```
1. Run `bundle install` to install ruby dependencies. If you get errors, delete Gemfile.lock and try again.

    If you see file permission error like `Fetching bundler-2.6.3.gem ERROR:  While executing gem (Gem::FilePermissionError) You don't have write permissions for the /var/lib/gems/3.2.0 directory.` or `Bundler::PermissionError: There was an error while trying to write to /usr/local/bin.`
    Install Gems Locally (Recommended):
    ```bash
    bundle config set --local path 'vendor/bundle'
    ```
    then try run `bundle install` again. If succeeded, you should see a folder called `vendor` and `.bundle`.

1. Run `jekyll serve -l -H localhost` to generate the HTML and serve it from `localhost:4000` the local server will automatically rebuild and refresh the pages on change to Markdown (*.md) and HTML files, while changes to the core template and configuration (i.e., `_config.yml`) will require stoping and restarting Jekyll.
    You may also try `bundle exec jekyll serve -l -H localhost` to ensure jekyll to use specific dependencies on your own local machine.

If you are running on Linux it may be necessary to install some additional dependencies prior to being able to run locally: `sudo apt install build-essential gcc make`

## Using Docker

Working from a different OS, or just want to avoid installing dependencies? You can use the provided `Dockerfile` to build a container that will run the site for you if you have [Docker](https://www.docker.com/) installed.

You can build and execute the container by running the following command in the repository:

```bash
chmod -R 777 .
docker compose up
```

You should now be able to access the website from `localhost:4000`.

## What this file explains

This README explains, in plain English, how to replace the website content (text, posts, pages), which files to edit, and how to swap or add images so the site will display the updated content when deployed to the web. It intentionally omits local development or build commands.

## Which README to edit

- The canonical place to store guidance for this repository is the root `README.md` (this file). Edit this file if you want to change high-level instructions or repository-specific notes.

## Where to put and replace content

This site uses a Jekyll-style source layout (folders that start with `_` and regular markdown files). To change content, edit or add the files below:

- Posts (blog entries): `_posts/YYYY-MM-DD-title.md` — Edit the markdown files here. Keep the filename date and front matter `date:` consistent.
- Pages: files in the root and `_pages/` (for example, `about.md`, `members.md`, `talks.html`) — edit the markdown or HTML files to change page content.
- Members (team/person pages): `_members/*.md` — edit the individual member files to change bios, photos, and metadata.
- Portfolio items: `_portfolio/` — each item is a markdown/html file.
- Talks / Talks metadata: `_talks/` — edit talk pages or data files used to generate talk listings.
- Publications: `_publications/` — edit each publication markdown file.
- Data used across site: `_data/*.yml` (for example `_data/authors.yml`, `navigation.yml`, `ui-text.yml`) — update author names, navigation labels, or site-controlled text here.
- Site settings and global metadata: `_config.yml` and (if present) `_config_docker.yml` — change site title, URL, description, baseurl, and other global settings.
- Files for direct download (PDFs, zips): `files/` — upload downloadable assets here; they are referenced as `/files/filename.ext` on the site.

Note: Keep front matter at the top of each markdown file (`---` block) correctly populated. Common front matter keys used here include: `title`, `date`, `layout`, `categories`, `tags`, `image` (see image section below), and `excerpt`.

## How to replace images so changes show on the live site

Follow these rules to ensure images are displayed correctly when the site is deployed:

1. Where to place images
    - Preferred locations (choose one and be consistent):
      - `assets/images/` — for general site images (recommended).
      - `images/` — the repository already uses this folder for some theme/example images.
      - `files/` — for large downloadable assets (PDFs, zip archives), not regular inline images.
    - You can also place images alongside a page or post (same folder), but prefer `assets/images` for shared images.

2. Filenames and formats
    - Use lowercase letters, hyphens instead of spaces, and avoid special characters: `team-photo-2025.jpg`.
    - Prefer modern web formats: WebP for best compression, JPEG for photos, PNG for graphics with transparency. Provide a JPG/PNG fallback if necessary.
    - Keep file sizes reasonable: aim for 100–400 KB for standard hero images and smaller for thumbnails.

3. How to reference images
    - In a page or post front matter (recommended for hero/featured images):

      image: /assets/images/your-image.jpg

    - Inline in markdown:

      ![Alternative text](/assets/images/your-inline-image.jpg)

    - In `_data/authors.yml` or other data files, set author image path to `/assets/images/authors/jane-doe.jpg` (or the path you choose).

4. Overwriting vs adding new names
    - To replace an image without changing references: overwrite the existing file with the same filename and path (commit the new file using the same path). This keeps all links intact.
    - To add a new image or rename: upload the new file and update all references to the new path (front matter, markdown image links, data files, and include templates if they reference the old name).

5. Update any data files that reference images
    - If author photos or avatars are referenced in `_data/authors.yml`, update the `avatar` or `image` field to point at the new path.
    - Check `_includes/` and `_layouts/` for hard-coded image paths used by the theme and update if you replace those files.

6. Caching / CDN notes
    - If you replace an image but keep the same filename, browsers and CDNs may cache the old image. To avoid stale images, use a new filename and update references, or add a cache-busting query string (if your deployment supports it). Since this README does not cover deployment commands, prefer a filename change when urgent replacement is required.

## Quick file map — what to edit for common tasks

- Change site title, base URL, and global settings: edit `_config.yml`.
- Change navigation links: edit `_data/navigation.yml` (or `_data/navigation.yml` equivalent in this repo).
- Update author profiles and their images: edit `_data/authors.yml` and the files in `_members/`.
- Update a post or add a new post: add/edit files in `_posts/` (use `YYYY-MM-DD-title.md` filenames).
- Update publications list entries: `_publications/`.
- Replace theme images (for example images shown in headers or examples): replace files under `images/` or `assets/images/` and update references in `_includes/` or `_layouts/` if needed.

## Small editing checklist (to follow before committing changes)

1. Edit the appropriate markdown or data file listed above.
2. If you changed or added images, place them in `assets/images/` (or `images/`) and update paths in front matter and `_data` as needed.
3. If you renamed an image, update every reference that pointed to the old filename.
4. Keep front matter fields (`title`, `date`, `image`, `layout`) accurate and consistent.

## Helpful tips

- Keep backups or branch your changes if you're doing a large site restructure.
- Use consistent naming and folders for images to make future replacements easier.
- For authors/team photos, keep a standard size (e.g., square 400x400px) to avoid layout inconsistencies.

## If you want further edits

If you'd like, I can also:
- generate a short checklist tailored to a specific page you want to update,
- update the `_data` files to point to new image names, or
- create example front matter blocks for new post/page templates.

Files changed in this update

- `README.md` — replaced with this focused guide describing which files to edit and how to replace images for deployment.

Completion summary

I updated the root `README.md` to explain where to edit content and how to handle images so that changes will appear on the live site. If you want, tell me a specific page or image you want replaced and I will update the corresponding files and data entries for you.
