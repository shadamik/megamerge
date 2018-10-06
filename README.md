# GitHub Mega Merger

## Deployment Guide
The application will be packed into a Container including all sources as well as the ruby runtime.
* To generate the Container do `docker build . -t megamerge`.
* If you added files to the `Gemfile` you will need to repopulate your `Gemfile.lock`. This is done by outing the current folder into the Container ans calling the `bundler install`. Complete call: `docker run -it --rm -v ${PWD}:/srv -w /srv/ megamerge bundle install`

## Development Guide
The container will open a port on http://localhost:3000 service the application. Also this will be linked to the GITHub test application ID.
* You will need to provide a [/src/credentials.yml](src/credentials.yml) that contains the application configuration:

```yaml
---
server: https://www.github.com
api: https://api.github.com
homepage: https://www.megamerge.com
app_id: 0
client: xxxxxxxxxxxxxxxxxxxx
secret: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
private_key: |
  -----BEGIN RSA PRIVATE KEY-----
  xxx
  -----END RSA PRIVATE KEY-----
```
* To run the Container with the packed sources: `docker run -it --rm -p 3000:3000 megamerge`
* check the "http://localhost:3000" to start the megamerge

## License
* MegaMerge is released under the [Apache License](LICENSE)
* MegaMerge is making use of files generated by Ruby on Rails, released under the [MIT License](MIT-LICENSE)
