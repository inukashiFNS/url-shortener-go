# URL Shortener

This is an URL Shortener made using Go and Redis. The Go web framework Fiber has been used to make this.

It has a Rate Limiting feature, which allows a particular IP to only shorten 10 URLs in a span of 30 mins. Also the API allows users, to create custom short URLs and users can set the expiry of the short URLs too.

## Installation

To build/install this app you will need [Docker](https://docs.docker.com/get-docker/). If Docker is installed, then the following commands need to be performed.

```bash
git clone https://github.com/inukashiFNS/url-shortener-go.git
```
```bash
cd url-shortener-go/
```
```bash
docker-compose up -d
```

## API

```bash
curl --header "Content-Type: application/json" \
     --request POST \
     --data '{"url":"https://example.com/"}' \
     http://localhost:3000/api/v1
```

The response for above should be something like this:

```JSON
{
  "url": "https://example.com/",
  "short": "localhost:3000/52152e",
  "expiry": 24,
  "rate_limit": 9,
  "rate_limit_reset": 30
}
```

For custom URL and setting expiry of the URL, you can pass these in the data flag of the request too.
```JSON
    {"short":"abcd","expiry":24} 
```