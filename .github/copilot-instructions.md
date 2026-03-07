# Copilot instructions for this project

This is an existing production-style website. Do not rebuild it from scratch unless explicitly requested.

Priorities:
- Preserve the current frontend design and behavior
- Prefer refactoring over replacement
- Make all major site content editable by a non-technical admin
- Avoid hardcoding content in components when it should be editable
- Favor clear admin UX over developer convenience

Admin UX standards:
- Use plain-English field labels
- Add helper text for non-obvious fields
- Group related fields into sections/tabs
- Support media upload and replacement
- Support repeatable collections where needed
- Add validation with understandable error messages
- Keep field names and content models intuitive
- Minimize required technical knowledge for editing
- Prefer predictable, maintainable content structures

When changing the codebase:
- First audit where content is hardcoded
- Reuse existing architecture where possible
- Keep changes incremental
- Explain which files changed and why
- State what content is editable after each implementation step

## Technical Architecture

This is a **single-page static HTML website** with a built-in admin panel:
- **File structure**: Single `index.html` file contains all HTML, CSS, and JavaScript
- **No backend**: Entirely client-side; can be deployed to any static hosting
- **Data persistence**: Uses browser `localStorage` with key `"comedyWebsiteData"`
- **Authentication**: Session-based admin login (password stored in `ADMIN_PASSWORD` constant)
- **Navigation**: Hash-based routing (`#home`, `#about`, `#shows`, etc.)
- **Framework**: Vanilla JavaScript, no external dependencies except Font Awesome icons

## Current Data Model

Content is stored in `localStorage` as JSON with this structure:
```javascript
{
  name: string,              // Comedian's name
  tagline: string,           // Tagline/subtitle
  landingPhoto: string,      // URL for home page photo
  bio: string,               // About page biography
  aboutPhoto: string,        // URL for about page photo
  shows: [                   // Array of upcoming shows
    {
      date: string,
      venue: string,
      city: string,
      time: string
    }
  ],
  social: {                  // Social media links (platform: url)
    instagram: string,
    twitter: string,
    // ... additional platforms
  },
  instagramUsername: string, // Username for auto-loading posts
  instagramPosts: [string],  // Manual Instagram embed URLs
  email: string,             // Contact email
  footer: string             // Footer text
}
```

## Implemented Features

✅ **Home/Landing Page**: Name, tagline, photo, CTA buttons  
✅ **About Page**: Bio text, photo  
✅ **Shows Page**: List of upcoming shows with date/venue/time  
✅ **Instagram Page**: Auto-load from username or manual embed URLs  
✅ **Contact Page**: Email and social media links  
✅ **Admin Panel**: Full content management interface at `#admin`

## Placeholder Features (Not Implemented)

⚠️ **Featured Artists**: HTML section exists (`#artists`) but no data model or admin interface  
⚠️ **Blog/News**: HTML section exists (`#blog`) but no data model or admin interface

## Admin System

**Access**: Navigate to `#admin` in URL (e.g., `index.html#admin`)  
**Default password**: `"password123"` (defined in `ADMIN_PASSWORD` constant)  
**Authentication**: Session-based (clears on browser close)  
**Storage key**: `"comedyWebsiteData"` in localStorage  

## Adding New Editable Content

To make new content editable, update these 5 areas in `index.html`:

1. **`defaultData` object** (~line 1080): Add new fields with default values
2. **`siteData` initialization**: Ensure new fields merge/migrate properly
3. **`renderContent()` function** (~line 1220): Add logic to display content on page
4. **Admin panel HTML** (~line 930): Add form inputs in appropriate section
5. **`loadAdminForm()` function** (~line 1290): Load existing values into admin form
6. **`saveAllChanges()` function** (~line 1547): Save form values to siteData

## Code Organization in index.html

- **Lines 1-700**: HTML structure and CSS styles
- **Lines 700-900**: Page sections (home, about, shows, artists, blog, instagram, contact)
- **Lines 900-1070**: Admin panel HTML
- **Lines 1070-1650**: JavaScript
  - Config & data model
  - Authentication & admin UI
  - Page navigation
  - Content rendering
  - Admin form management
  - Data persistence

## Development & Deployment

**Local development**: Open `index.html` in any modern browser  
**Testing admin**: Navigate to `file:///path/to/index.html#admin`  
**Deployment**: Upload `index.html` to any static host (GitHub Pages, Netlify, Vercel, S3, etc.)  
**Data backup**: Export from browser console: `localStorage.getItem("comedyWebsiteData")`  
**Password change**: Edit `ADMIN_PASSWORD` constant (line ~1078)

## Common Tasks

**Change password**: Update `ADMIN_PASSWORD` constant  
**Reset content**: Use "Reset to Defaults" button in admin or clear localStorage  
**Add social platform**: New platforms auto-use Font Awesome icon (e.g., `fab fa-{platform}`)  
**Backup data**: `localStorage.getItem("comedyWebsiteData")` from browser console  
**Restore data**: `localStorage.setItem("comedyWebsiteData", jsonString)` from console
