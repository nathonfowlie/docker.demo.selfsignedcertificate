# Overview
Demonstration dockerfile that shows how self-signed certificates can be securely generated at build time (or run time, with a little bit of tweaking). Deploying the image will give you a simple website running on NGINX, using the certificates that were generated during the build.

# Building the image
In its most basic form, you can build the image via -
`docker build --tag foo/bar .`

You can also modify the contents of the generated certificate by providing one or more of the following arguments, for example:
`docker build --build-arg SAN="DNS:foo.com,DNS:*.foo.com,IP:111.111.111.111" --build-arg SUBJECT="/C=US/ST=AK/L=Ketchikan/O=Evil Corp/CN=Overlord" --tag foo/bar`

|Argument|Description|Default|
|--------|-----------|-------|
|SAN|Subject Alternative Name(s) to be added to the certificate.|DNS:localhost,IP:127.0.0.1|
|SUBJECT|Subject field to be added to the certificate.|/C=AU/ST=NSW/L=Sydney/O=Localhost/CN=localhost|
|CN|Common Name to be added to the certificate.|localhost|

# How to Use
1. Start a container -
`docker run -p 443:443 -d nathonfowlie/demo.createselfsignedcertificate`
2. Navigate to https://docker and gaze in wonder at my incredible web development skills.

If all goes well, you'll see an animated gif, and your browser will be complaining about trust issues :)
