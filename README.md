# HTTPS on Local Stack
With Django + Gunicorn + PostgreSQL + Caddy

## Instructions
1. Try to build the `Dockerfile` within the app directory, to see if everything's working fine.
2. If the app works, build a new compose stack using `docker compose up --build`.
3. Try accessing in your browser to, `https://django.app.localhost/`
    * Didn't work? That's great, it means your computer is still safe and is up to standards.
    * You actually need to install a root certificate on to your computer's trust store just for this activity, and be sure to remove it later.
4. From your browser settings, find a way to open a Trust Store manager.
5. Import a new certificate which is at `caddy/data/caddy/pki/authorities/local/root.crt`.
6. Try accessing the site again, it should get you there but might stuck on Not Found page.
    * Navigating to admin page should work as usual.

## What does this benefit you?
Not much, but you get to test how your application runs on production and with HTTPS, so you are steps toward to more real-world production-like environment.

Doing this also enforces you to try the application with `DEBUG=False`, since you cannot really use development version of site to handle HTTPS requests.

Some OAuth2 providers also require HTTPS callbacks, so this way could be a good workaround to test something like so.

Additionally, here's [why](https://aws.amazon.com/compare/the-difference-between-https-and-http/#:~:text=HTTP%20messages%20are%20plaintext%2C%20which,the%20data%20over%20the%20network.) you'd always use HTTPS on production.

## Getting practical
How about using this on your project development during this week before deployment?