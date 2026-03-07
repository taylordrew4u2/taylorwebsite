Analyze this existing website workspace and refactor it so the admin side is usable by a non-coder.

Workspace grounding:
- Site file: `index.html`
- Project notes: `README.md`

Goal:
I need to be able to edit the site without knowing how to code. Do not rebuild the public site from scratch. Work with the current codebase and preserve the current design, routes, and frontend behavior unless a change is required to make editing easier.

Your tasks:
1. Audit the current codebase and find every place where content is hardcoded.
2. Identify what already exists for admin/editing, if anything.
3. Refactor the project so all important content is editable through an admin interface instead of code edits.
4. Create or improve an /admin experience that is simple for a non-technical person.

Admin UX requirements:
- Clear labels for every field
- Helper text under fields
- Group fields into logical sections
- Media upload/replacement for images
- Repeatable sections for things like shows, blog posts, featured artists, links, FAQs, testimonials, etc.
- Slug controls only where necessary
- Draft/publish status if applicable
- Preview support if possible
- Validation and error messages in plain English
- No developer terminology in the UI unless unavoidable
- Sensible defaults and placeholders
- Reordering controls for lists/sections
- Global site settings area for nav, footer, SEO defaults, social links, ticket links, contact info

Content that must become editable:
- Homepage
- About page
- Show/event listings
- Blog/news posts
- Featured artist sections
- Venue details
- Buttons and links
- Navigation and footer
- SEO title, meta description, OG image
- Announcement bars/banners
- Any reusable homepage sections
- Any images, files, or media used across the site

Implementation rules:
- Reuse the existing stack and patterns already in the repo where possible
- Keep the public frontend intact
- Do not hardcode new content
- Centralize editable content structure cleanly
- Make the admin side as low-maintenance as possible
- If a CMS, database schema, config model, or admin library is needed, choose the option that best fits the existing project and explain why
- Make incremental changes and show me which files you changed and why
- After each step, tell me exactly what is now editable through the admin

Start by auditing the workspace and listing:
A. what is currently hardcoded
B. what is already editable
C. the fastest path to making everything editable for a non-coder
Then begin implementing that plan.
