## Plex Media Server with Docker Compose
This repository provides a ready-to-use Docker Compose configuration for deploying Plex Media Server. Plex allows you to organize, stream, and enjoy your media (movies, TV shows, music) on various devices.

## Environment Variables:
PUID and PGID: Use your system's user ID and group ID

## Volumes:
/config: Stores Plex configuration files (persistent across container restarts).
/movies: Points to the directory where your media files are stored.
/transcode: Temporary directory used during video transcoding.

## Commands to Deploy Plex
Start the Container : 
docker-compose -f /media/your_user/DOCKER-STORAGE/dock_serv_plex/docker-compose.yml up -d

## Access Plex Server:
http://<SERVER_IP>:32400/web
Log in with your Plex account or create a new account.
Go to Settings → Libraries → Add Library.
Choose the type (Movies, TV Shows, etc.) and point to /movies (configured in Docker Compose as /media/your_user/DOCKER-STORAGE/SHARE/ANIME).

Note : Plex will index your media files. Depending on your library size, this may take some time.

## Boosting Server Cache for Stability
If you experience frequent buffering or interruptions due to weak Wi-Fi, you can improve the server's performance by increasing the cache size.
1) Locate Plex’s Preferences.xml file in the /config directory:
config\Library\Application Support\Plex Media Server
2) Edit the file and add the following line (or update if it exists): 
<Setting id="TranscoderBufferSize" value="120"/>
"This increases the transcoder's buffer size to 120 seconds."
3) Restart the Plex container:
docker restart plex

## Additional Tips
Optimizing Media: Use Plex's built-in optimization to create lower-resolution versions of your videos for smoother playback.

Made with the help of ChatGPT