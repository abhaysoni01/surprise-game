# Surprise Game

## Discord notifications through Cloudflare

The game sends the winner's name, gift, and timestamp to the Cloudflare Worker
configured as `CLOUDFLARE_WORKER_URL` in `index.html`. The Discord webhook must
be stored as a Worker secret in Cloudflare; it must never be added to this
page. The project `.env` file is not read by the game.

Serve this page over HTTPS (or localhost during development), not as a `file://`
URL. Configure the Worker to accept `POST` requests with JSON and to return the
appropriate CORS headers for this game's origin, including an `OPTIONS`
preflight response. The win screen reports whether the Worker accepted the
notification. A successful response means the Worker accepted it; check the
Worker logs if Discord delivery itself fails.

## Gift coupon

After the game, choose **Download your gift coupon** to save the coupon as a
PNG image.
