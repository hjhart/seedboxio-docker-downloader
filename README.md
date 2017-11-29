# Docker Downloader for seedbox.io

This docker set up allows you to set up a local dockerized Sonarr, Radarr, Jackett, and Resilio Sync, that will automatically hook up to your seedbox.io seedbox instance, straight out of the box. It even has an nginx reverse proxy sitting on port 80 to give you a front page to your media services.

# Installation

Set your seedbox.io name as an environment variable.

```
export SEEDHOST=psb18653.seedbox.io
open https://$SEEDHOST/
```

* Make sure rTorrent has AutoMove set to a directory, CompletedDownloads, and checkbox for adding the label.

Now go add that directory in resilio sync.

```
open https://$SEEDHOST/resilio
```

* Add that directory in Resilio Sync, copy the read-only secret.

```
cp .env.example .env
```

Now edit the .env file to include your newly generated Resilio Sync secret as RSLSYNC_SECRET.

While you're in the .env file, add in correct data for MOVIE_DIR, TV_SHOW_DIR, and STORAGE_DIR. These represent where you want you movies, your tv shows, and where your completed downloads should go.

## Configure Radarr:

* Add indexers that you want to add.
* Add rTorrent as a Download Client to point to your seedbox.io. [See this article](https://panel.seedbox.io/index.php?rp=/knowledgebase/41/How-to-connect-Sonarr-to-your-service.html)
* Toggle "Advanced Settings" in the Download Client tab.
* Add a new Remote Path Mapping like this:

```
   host                               remote path                                        local path
psb18653.seedbox.io       /home/psb18653/files/CompletedDownloads/radarr/              /downloads/radarr/

```

## Configure Sonarr: 

* Add indexers that you want to add.
* Add rTorrent as a Download Client to point to your seedbox.io. [See this article](https://panel.seedbox.io/index.php?rp=/knowledgebase/41/How-to-connect-Sonarr-to-your-service.html)
* Add a new Remote Path Mapping like this:

```
   host                               remote path                                        local path
psb18653.seedbox.io       /home/psb18653/files/CompletedDownloads/sonarr/              /downloads/sonarr/

```

TODO:


* Figure out how to configure Download Clients automatically and check it into version control
* (Essentially figure out how to remove the "Configure Radarr / Sonarr" manual steps)
* Add download clients automatically
