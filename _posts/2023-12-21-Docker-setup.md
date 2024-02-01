---
title: Run Jekyll Site Using Docker Container
tags: [ Docker, Technology]
style: fill 
color: light
description: Using docker to run jekyll theme
---
You might ask if we already got our website running locally why do even bother using Docker? The reasons contain many diffrent aspects, including consistent environments, easy portability, and dependency isolation. Docker encapsulates the Jekyll runtime, ensuring consistent behavior across different systems and environments. Portability enables sharing and deployment across diverse platforms, while isolation prevents conflicts with other dependencies. Docker simplifies deployment, allows version control of the environment, enhances security, and supports easy scaling. 
{% include elements/figure.html image="assets/jd.png" caption="Jekyll & Docker logo" %}

## 1.Install Docker
If you haven't installed Docker yet, download and install it from the official Docker website: https://docs.docker.com/engine/install/. Docker provides straightforward installation packages for Windows, macOS, and Linux.

## 2. Create a Dockerfile
In the root of your Jekyll site, create a file named Dockerfile (without any file extension) with the following content:
```Dockerfile
FROM jekyll/builder:latest

WORKDIR /srv/jekyll

COPY . .

RUN bundle install

EXPOSE 4000

CMD ["jekyll", "serve", "--host", "0.0.0.0"]

```
## 3. Build the Docker Image
In the root of your Jekyll site, create a file named Dockerfile (without any file extension) with the following content:
```Bash
docker build -t my-jekyll-image .
```

## 4. Run your Jekyll Site
After building the image, run a container using the following command:
```Bash
docker run -p 4000:4000 --name my-jekyll-container my-jekyll-image
```

## Congratulations 
Now, you have successfully set up and run your Jekyll site using Docker. Adjust the configuration according to your specific needs, and feel free to customize the Dockerfile or docker-compose.yml based on your project requirements.