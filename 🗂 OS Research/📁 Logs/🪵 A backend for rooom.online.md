
This post is a type of continuation for [[🪵 Git for web rooms & migrating obscurity.wiki]] where I explore in further detail how the backend could look like and a snapshot of my notes.

I would append the notes rooom but it has some information that I want to keep private for now.

### File-oriented Architecture 

```bash
DIR STRUCTURE

subdomain root # /
-   room manager # /index.html
-   modules dir # /mod
-       modules manager # /mod/index.html
-   assets dir # /media
-       media manager # /media/index.html
-   rooms dir # /rooms
-       rooms # /rooms/[room-slug]/index.html
-       snaps # /rooms/[room-slug]/snap-[ts].html
-       room meta # /rooms/[room-slug]/meta/*
-           ... sqlite files or other room storage form
-       room tmp # /rooms/[room-slug]/tmp/*
```

Instead of providing users with a folder to host whatever they want, I'll provide a very specific system for them that works around rooms.

The idea is that each user can CRUD their rooms under their user subdomain (username.rooom.online).

They'll be able to setup an entrance page that shows up when their subdomain is hit, and from there they can create public or private rooms.

Private rooms are encrypted and authentication is needed to access them.

The core thing about the backend is that it needs to support module, assets, and room management.

Developing or installing modules should be easy and secure, so this should be enabled by the backend.

For assets it should be straight forward to keep track of them serve as a media library, these should be stored externally using S3 buckets.

The room manager will basically be your home or any room that you specify for that task. This is because this is probably a more personal choice compared to how a module or media manager would require.

I like this file-oriented approach to dealing with data and configurations.

I'm not experienced enough to know what's needed to setup in order to have public vs private files served through a CDN or directly served from the server.

There are a lot of details I'm not aware of but this is why I'm looking at the first version of the backend as a prototype that I can show a backend engineer and say: something like this but fast and secure.

### Prototype 1

I want user and basic user functionality:

- Register
- Sign in / sign out
- Forgot password
- Change password
- Update user data
- Delete account

Register runs a setup process that creates the corresponding directories and files.

I wont be using a CDN for prototype 1.

In terms of the API I want pretty much what's mentioned in [[🪵 Git for web rooms & migrating obscurity.wiki]]:

- APIs for CRUDing modules, assets, and rooms.
- I want to experiment and prototype with Git too. I want to know how feasible it is to use a local git on each user account.

I eventually want to move away from developing rooom modules locally to doing it fully on a rooom itself.

This is my goal.