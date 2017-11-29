# Installation

Set your seedbox.io name as an environment variable.

```
export SEEDHOST=psb18653.seedbox.io
open https://$SEEDHOST/resilio
```

```
cp .env.example .env
```

Now edit the .env file to include your newly generated Resilio Sync number.

* Make sure rTorrent has AutoMove set to a directory, CompletedDownloads, and add the label.
* Add that directory in Resilio Sync, copy the read-only secret.
* Put that secret inside the .env file as RSLSYNC_SECRET
* Add in correct data for MOVIE_DIR, TV_SHOW_DIR, and STORAGE_DIR.

Configure Radarr:

* Add trackers
* Add rTorrent as a Download Client
* Add a remote to local mapping in your
