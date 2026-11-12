<p align="center">
  <img src="../assets/banner.jpg" alt="API Everything banner">
</p>

<h1 align="center">API Everything</h1>

<p align="center">
  An open-source, self-hostable layer for accessing multiple services through a unified API.
</p>


## About

API Everything is an open-source organization providing self-hostable connectors for services such as:

```
Instagram — profile stats and posts (URL, description, hashtags, comments, date, likes, photos)
```

The goal is to reduce reliance on paid API providers while keeping control over your infrastructure and data.

## How It Works

```text
Your application
       ↓
API Everything
       ↓
Service connector
       ↓
External service
```

Each service is integrated through an independent connector, developed as its own project within the organization.

## Planned Features

- Unified REST API
- Independent connectors
- Self-hosting support
- OpenAPI documentation
- API key and session management
- Local caching
- Logging and error handling
- Data normalization

## Example

Each connector is a standalone HTTP service. See [`connectors/socials/instagram`](../../connectors/socials/instagram/README.md) for setup and the cookie-based session configuration.

```bash
cd connectors/socials/instagram
cp .env.example .env          # add your own IG_SESSIONID
docker compose up -d
```

```bash
curl "http://localhost:3000/v1/instagram/kametolol"
curl "http://localhost:3000/v1/instagram/kametolol/posts?limit=12"
```

```json
{
  "url": "https://www.instagram.com/p/Cxxxxxxx/",
  "userPosted": "kametolol",
  "description": "Great night #Kameto",
  "hashtags": ["#Kameto"],
  "numComments": 142,
  "datePosted": "2025-09-14T18:32:07.000Z",
  "likes": 28411,
  "photos": ["https://scontent-xxx.cdninstagram.com/...jpg"]
}
```

There is no hosted instance: you run it on your own machine, with your own IP and your own session. Optional rotating residential proxies can be configured per instance. That is what makes it free, unlimited, and independent of any intermediary.

## Status

> Project under development.

Connectors may have different stability levels depending on the integrated service.

## Principles

- Open source
- Self-hostable
- Transparent
- Respectful of user data
- No mandatory intermediary service

## Repositories

- [`core`](https://github.com/apieverything/core) — Main API gateway
- [`connectors`](https://github.com/apieverything/connectors) — Official service connectors
- [`docs`](https://github.com/apieverything/docs) — Documentation

## Installation

```bash
git clone https://github.com/apieverything/core.git
cd core
```

> Installation instructions will be added with the first functional release.

## Contributing

Contributions are welcome.

1. Fork the relevant repository
2. Clone your fork:

```bash
git clone git@github.com:YOUR_USERNAME/REPOSITORY.git
cd REPOSITORY
```

3. Add the official repository as an upstream remote:

```bash
git remote add upstream git@github.com:apieverything/REPOSITORY.git
```

4. Create a branch:

```bash
git checkout -b feat/my-change
```

5. Add or improve a connector and add the necessary tests
6. Push your branch:

```bash
git push origin feat/my-change
```

7. Open a pull request

## License

Distributed under the MIT License with an attribution notice.

See [`LICENSE.md`](../LICENSE.md). Use, modification and redistribution are
permitted; any project built on this work elsewhere must visibly credit
**API Everything**.
