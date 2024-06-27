
### Migrating obscurity.wiki to web rooms

I really need to migrate obscurity.wiki to be made of [[💡 Web Rooms]].

I'm getting multiple ideas:

- It's not necessarily following the rooom.online design direction and complexity.
- It leverages the rooom.online architecture
- Remove folders and use rooms instead? Not sure on this yet. I also like the idea of having like obscurity.wiki notebook that I can use as a room thing. Like reference pages and things like that. But, that works only if I still use obsidian and if I setup some sort of API, etc.

More and more I'm needing a solution for the hosting problem. By "hosting problem" I mean I need a way to host rooms locally or remotely and keep track of snapshots. Like what I'm doing with are.na channels.

### Hosting Rooms

- Folder with snapshots where title is timestamp
- API endpoint that gets latest or specific snapshot
- API endpoint that pushes a new snapshot (auth required)
- API endpoint that deletes a snapshot (auth required)


Comparing this to Git I'm A LOT of features but this is ok. I haven't had a need for more.

Now, I'd like to have a similar solution for assets and modules.

### Hosting Assets

- A simple static file server
- API endpoint to get file metadata like media dimensions, etc.
- API endpoint to upload, update or remove files (auth required)

### Hosting Modules

- Folder per module with JS and CSS files.
- Branches as sub-folders.
- API endpoint to push new snapshot (auth required)
- API endpoint that deletes a snapshot (auth required)
- API endpoints to manage branches, etc.

Folder structure:

```bash
# module-name -> branch -> snapshot -> files
module-name/main/timestamp/script.js # required
module-name/main/timestamp/styles.css # required
module-name/main/timestamp/assets/...
```

What if I do use git but locally on that server?


