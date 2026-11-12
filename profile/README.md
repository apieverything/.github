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
Work in Progress
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

A FAIRE

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

Distributed under the MIT License.

See the [`LICENSE`](LICENSE) file.
