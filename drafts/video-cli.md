While professionals use advanced tools such as Adobe Premiere, Sony Vegas, iMovie for video editing, as a programmer, command line tools are often more handy.
Below is a quick list of useful command line tools and examples for the future self and others who are in search for these oneliners.

## ffmpeg

### crop

Crop a video from some start time (1 second) with a duration of 3 seconds

```shell
$ ffmpeg -ss 1 -i from.avi -t 3 -c copy to.avi
```

- `-ss` start position, this may be approximate because it's not possible to be precise in some video formats.
- `-i` input file, can be a url
- `-t` duration; alternatively you can use `-to`.
- `-c copy` don't do transcoding and will simply copy from the source
