I couldn't find an OSSEC-HIDS Docker image that actually worked, so I made my own. 

This is a very quick and dirty build, but it pulls from the official ossec-hids Github repo so it should be fairly simple to keep up to date. 

The server is configured with pretty much all the defaults, except e-mail notifications, which I don't need / want to deal with. Everything else is pretty much bone, stock, but that should work for most folk. 

I am an OSSEC newbie, and this Docker Image has been tested *lightly*, so expect updates. If you know better (like I'm missing a persistent volume or something important) please give me a shout. I'm also open to any critique of my Dockerfile, since this is my first build with Docker and I suspect there are some less-than-best-practice moments here and there.

All the details can be found in my [Github repo](https://github.com/luciusbono/Docker-ossec-hids). 

An example container launch: 

`docker run -d -p 1514:1514/udp -p 514:514/udp --name ossec luciusbono/ossec-hids:latest`

Add agents with:

`docker exec -it ossec /var/ossec/bin/manage_agents`

Don't forget to do a `docker exec -it ossec /var/ossec/bin/ossec-control restart` after you'd added your first agent. 