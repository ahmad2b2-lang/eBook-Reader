# eBook Reader

A mobile-friendly web app for reading scanned (image-only) PDF books.

- Sign in with username + passcode
- Upload PDF books; files are stored privately in Supabase Storage (bucket `ebook-reader`)
- Every page you view for 3 seconds (or move past) is saved as **read**
- Opening the app takes you straight back to the book and page where you stopped
- Swipe / tap the page edges to turn pages, pinch or use the buttons to zoom
- Right-to-left page turning for Arabic books (per book, in the ⋮ menu)
- Books are cached on the device after the first download

## Supabase layout ("First Project")

Everything belongs to this app only:

| Item | Purpose |
| --- | --- |
| `ebook_members` | Users allowed into the app |
| `ebook_books` | Book title, file path, page count, last page, direction |
| `ebook_pages_read` | One row per page marked as read |
| `ebook_state` | The last opened book (for resuming) |
| Storage bucket `ebook-reader` | The PDF files, in a folder per user |

All tables and the bucket use row-level security: only signed-in members can reach their own rows and files.

Plain HTML + JavaScript; no build step. Hosted on GitHub Pages.
