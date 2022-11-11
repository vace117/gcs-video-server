This is a very simple way of serving files to authenticated Google users from GCS buckets.

# Create bucket 
`gs://dumb-video-storage`

# Set Web Config
```
gsutil web set -m redirect.html -e redirect.html gs://dumb-video-storage
```

# Upload
```
gsutil -m cp redirect.html gs://dumb-video-storage/redirect.html
gsutil -m cp video_directory.html gs://dumb-video-storage/video_directory.html
```

# Expose Public Entrypoint
```
gsutil acl ch -u AllUsers:R gs://dumb-video-storage/redirect.html
```

# Access the videos
https://storage.googleapis.com/dumb-video-storage/redirect.html

or directly w/o a redirect:

https://storage.cloud.google.com/dumb-video-storage/video_directory.html?authuser=1
