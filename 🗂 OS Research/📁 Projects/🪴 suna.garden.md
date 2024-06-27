
> Visit [suna.garden](https://www.suna.garden/) to see it live

As of Feb 29, 2024, this project was a lab for a lot of experimentation for everything canvas related. I even explored topics like [[📝 CRDTs]] and [[📝 Data Persistence]] in general.

But after working on the [[🔬 HTML as the static canvas format]] experiment, I changed the way that this site is used.

Now (Wed 26 Jun 2024) it's used as a way to browse html room files. The suna.garden points to a cloudflare worker that takes the url slug to fetch an are.na channel. It takes the channel's most recent block, if the block is an html it will render it. For private channels the client html can send a cookie with the auth token.

It even has a [404 page](https://www.suna.garden/this-room-doesnt-exist).

Setting the domain this way has been a great tool for my own needs. I'm able to organize notes in different rooms while keeping a history of all uploaded versions of each room. It also informs what I'll need for rooom.online in terms of the backend.

Overall it allows me and others to see the progress and evolution of [[💡 Web Rooms]].