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

Each connector is a standalone HTTP service. See [`connectors/socials/instagram`](../../connectors/socials/instagram/README.md) for setup. Public data needs **no account and no session cookie**.

```bash
cd connectors/socials/instagram
cp .env.example .env          # optional for public data
docker compose up -d
```

```bash
curl "http://localhost:3000/v1/instagram/kametolol"
curl "http://localhost:3000/v1/instagram/kametolol/posts?limit=12"
```

```json
{
  "username": "kametolol",
  "profile": { "followers": 401268, "following": 368, "posts": 35, "fullName": "Kameto" },
  "count": 1,
  "posts": [
    {
      "url": "https://www.instagram.com/p/Cxxxxxxx/",
      "userPosted": "kametolol",
      "description": "Great night #Kameto",
      "hashtags": ["#Kameto"],
      "numComments": 142,
      "datePosted": "2026-11-12T15:07:23.000Z",
      "likes": 28411,
      "photos": ["https://scontent-xxx.cdninstagram.com/...jpg"],
      "type": "reel"
    }
  ],
  "source": "anon_grid",
  "strategy": "anon_grid"
}
```

There is no hosted instance: you run it on your own machine, with your own IP. Optional rotating residential proxies can be configured per instance. That is what makes it free, unlimited, and independent of any intermediary.

The [`core`](https://github.com/apieverything/core) gateway optionally fronts every connector with one account and rotatable API keys: a 16-digit unlock code opens the account, `ae_…` API keys (created, reset and revoked inside it) are the only credentials accepted for API calls, and weighted credits follow the account. It is optional — connectors keep full functionality without it.

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

- [`infra`](https://github.com/apieverything/infra) — One-command local deployment (`./deploy.sh`)
- [`core`](https://github.com/apieverything/core) — Unified gateway: 16-digit unlock code, rotatable API keys, weighted credits, zero data retention
- [`connectors`](https://github.com/apieverything/connectors) — Official service connectors (Instagram, LinkedIn, TikTok)
- [`web`](https://github.com/apieverything/web) — Public website and dashboard
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
