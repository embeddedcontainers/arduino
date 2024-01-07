# Arduino Container Images

Develop Arduino sketches using OCI-compatible Docker images.

Currently there are two types of images - a "base" image that contains the main dependencies to build a Arduino sketches and ones for a specific Cores. Most users will generally interact with the Core-specific images.

# Getting container images

## Build images locally

Building images locally ensures you can trust the source of the image, as well as allow you to modify the container image configuration.

### Building with Docker CLI

_Build the base image_

```
docker build -f "./arduino-base/Dockerfile" -t arduino:base "./arduino-base/"
```

_Build an image for the Arduino AVR Core:_


```
docker build --build-arg BASE_IMAGE="arduino:base" --build-arg CORE="arduino:avr" --build-arg VERSION="latest" -f "./arduino/Dockerfile" -t arduino:arduino-avr-latest "./arduino"
```

_Build an image for the Adafruit SAMD Core:_

```
docker build --build-arg BASE_IMAGE="arduino:base" --build-arg CORE="adafruit:samd" --build-arg VERSION="latest" --build-arg URL="https://adafruit.github.io/arduino-board-index/package_adafruit_index.json" -f "./arduino/Dockerfile" -t arduino:adafruit-samd-latest "./arduino"
```
