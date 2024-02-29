
> Visit [suna.garden](https://www.suna.garden/) to see it live

As of Feb 29, 2024, this project was a lab for a lot of experimentation for everything canvas related. I even explored topics like [[📝 CRDTs]] and [[📝 Data Persistence]] in general.

But after working on the [[🔬 HTML as the static canvas format]] experiment, I feel the need to change and maybe even commit to a final intent for this project or product:

"suna.garden" is a tool for creating web rooms or canvas web docs.

Specifically, it allows users to:
- Use are.na blocks as content cards
- Customize the room's wallpaper, metadata, etc.
- Upload directly to are.na channels as html file or living garden*.
- Export html files to do whatev the fuck you want.
- Importing html files with compatible modules (see [[🧰 oceloti-js]])

Something important to note is the two main formats: living gardens and oceloti html.

Living gardens are dynamic are.na blocks with changing content that maintain the same block reference/id.

Compared to an oceloti html file, this allows a user to read a living garden and export it or create a living copy.

In any case, it's important to know that living gardens or simply gardens are stored locally first, and uploaded as blocks second. The source of truth is whatever the user decides — the block or the local garden stored in an indexeddb table.

---

I want to make `suna.garden/logs` a blog/feed page that shows my activity:
- Relevant updates on obscurity.wiki
- Blocks added on relevant are.na channels
- Communication about its progress and development such as announcements or just thoughts.