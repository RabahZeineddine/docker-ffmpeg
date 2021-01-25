# About

## What is this for?

This is a clone from [adilinden-oss/docker-ffmpeg](https://github.com/adilinden-oss/docker-ffmpeg).

## Building

Build it from Github

    git clone https://github.com/adilinden-oss/docker-ffmpeg.git
    cd docker-rpi-ffmpeg
    docker build -t adilinden/ffmpeg .

Or, get it from Docker Hub

    docker pull adilinden/ffmpeg

## Usage

To use simply execute `ffmpeg`.

    docker run -it --rm --privileged adilinden/ffmpeg ffmpeg \
        -re -f mjpeg -framerate 5 -i http://<IP of OctoPi>:8080/?action=stream \
        -ar 44100 -ac 2 -acodec pcm_s16le -f s16le -ac 2 -i /dev/zero -acodec aac -ab 128k \
        -strict experimental -vcodec h264 -pix_fmt yuv420p -g 10 -vb 700k -framerate 5 \
        -f flv rtmp://a.rtmp.youtube.com/live2/<YouTube Stream ID>
