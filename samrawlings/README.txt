SAMRAWLINGS.NET — YOUR WEBSITE GUIDE
======================================

This site is built with Eleventy, a "static site generator." That sounds
technical but here's all you need to know: you write your content in simple
text files, and the site builds itself.

The big difference from before: you NEVER edit the HTML pages. You only
edit content files (posts, shelf data, photo data, bio). The site assembles
itself when you push your changes to GitHub.


═══════════════════════════════════════════════════════════════
ONE-TIME SETUP (do this first)
═══════════════════════════════════════════════════════════════

1. Create a free GitHub account at github.com if you don't have one.

2. Make a new repository (call it "samrawlings"). Don't tick any of the
   "add a README" or ".gitignore" boxes — leave it empty.

3. Drag every file and folder from THIS folder into GitHub's
   "uploading an existing file" page. Commit the upload.

4. Go to netlify.com and log in. Click "Add new site" → "Import an
   existing project" → choose GitHub → choose your samrawlings repo.

5. Netlify will detect the settings automatically (build command:
   `npm run build`, publish directory: `_site`). Click deploy.

6. Done. Your site is now live, and every time you change a file on
   GitHub, Netlify rebuilds your site automatically. No more dragging
   folders.


═══════════════════════════════════════════════════════════════
DAY-TO-DAY: HOW TO DO EVERYTHING
═══════════════════════════════════════════════════════════════

Everything below is done by editing one file on GitHub.com:
  1. Open your repo on GitHub
  2. Click the file you want to edit
  3. Click the pencil icon (top right) to edit
  4. Make your change
  5. Click "Commit changes" at the bottom
  6. Wait ~30 seconds for Netlify to rebuild
  7. Your change is live

You can also create new files this way: "Add file" → "Create new file".


-----------------------------------------------------------------
ADD A NEW POST
-----------------------------------------------------------------

1. In your GitHub repo, open the `posts` folder.
2. Click "Add file" → "Create new file".
3. Name it like this:   2026-05-19-on-tutoring.md
   (Format: YYYY-MM-DD-short-title.md, all lowercase, dashes for spaces.)
4. Type this at the top of the file:

       ---
       title: On tutoring
       date: 2026-05-19
       ---

       Your first paragraph goes here.

       Your second paragraph goes here. Just leave a blank line between
       paragraphs. No HTML needed.

5. Commit the file. Your post is live in 30 seconds.

That's it. The post will appear automatically on your writing page AND
on the home page's "recent writing" section. No other files to edit.


-----------------------------------------------------------------
ADD A SHELF ENTRY (book, film, album)
-----------------------------------------------------------------

1. Open `_data/shelf.json` on GitHub.
2. Click the pencil to edit.
3. At the very TOP of the list (just under the opening `[`), paste:

       {
         "title": "The Beginning of Infinity",
         "author": "David Deutsch",
         "type": "book",
         "rating": 5,
         "link": "https://www.goodreads.com/...",
         "note": "Optional one-line thought."
       },

4. Change the values. Notes:
   - "type" must be exactly one of: book, film, album
   - "rating" is a number 1 to 5 (no stars, just the number)
   - "link" and "note" are optional — delete the line if you don't want them
   - Every entry except the last needs a comma at the end of the `}`
5. Commit. Live in 30 seconds.


-----------------------------------------------------------------
REMOVE A SHELF ENTRY
-----------------------------------------------------------------

1. Open `_data/shelf.json`.
2. Find the entry's `{ ... },` block (from the `{` to the `},`).
3. Delete the whole block including the trailing comma.
4. Commit.


-----------------------------------------------------------------
ADD A PHOTO
-----------------------------------------------------------------

Step A — Upload the image:
  1. Compress your photo at squoosh.app (quality 80%).
  2. Rename it to something simple: nepal-stupa.jpg (no spaces).
  3. In GitHub, open the `photos` folder.
  4. Click "Add file" → "Upload files" → drop your image in. Commit.

Step B — Add it to the photo list:
  1. Open `_data/photos.json`.
  2. At the top, paste:

       {
         "caption": "Boudhanath Stupa, Nepal",
         "category": "travel",
         "file": "nepal-stupa.jpg"
       },

  3. "category" must be "travel" or "film".
  4. Commit.


-----------------------------------------------------------------
CHANGE YOUR BIO
-----------------------------------------------------------------

Open `_data/site.json`, change the text inside the quotes, commit.


-----------------------------------------------------------------
EDIT AN EXISTING POST
-----------------------------------------------------------------

Open the post file in the `posts/` folder, edit, commit. That's all.


═══════════════════════════════════════════════════════════════
HOW THE FOLDERS WORK
═══════════════════════════════════════════════════════════════

You'll touch these:
  posts/              your writing, one .md file per post
  _data/site.json     your bio
  _data/shelf.json    your books, films, albums
  _data/photos.json   your photo list
  photos/             actual photo image files

You should NOT need to touch these:
  index.njk           home page template
  writing.njk         writing list template
  shelf.njk           shelf template
  photos.njk          photos template
  _includes/          shared layouts
  css/style.css       site styling
  .eleventy.js        build settings
  netlify.toml        deploy settings
  package.json        Eleventy dependency
  _redirects          old URL redirects
  favicon.svg         tab icon

You can ignore these (auto-generated):
  _site/              the built site (Netlify makes this for you)
  node_modules/       only if you build locally


═══════════════════════════════════════════════════════════════
SOMETHING WENT WRONG?
═══════════════════════════════════════════════════════════════

Two options:

Option 1 — Roll back on GitHub:
  Every commit is saved. Go to your repo → "Commits" → find the last
  good one → click "..." → "Revert".

Option 2 — Ask Claude:
  Open claude.ai, paste in the file you changed, and say:
  "I'm editing my Eleventy site and something broke. Can you fix it?"

If a post doesn't appear:
  - Check the filename starts with a date: YYYY-MM-DD-title.md
  - Check the front matter (the `---` block at top) has both title and date
  - Check Netlify's "Deploys" tab — a failed build will show the error

If the shelf is broken:
  - Almost always a missing comma or extra comma in shelf.json
  - Paste the file into claude.ai and ask it to fix the JSON
