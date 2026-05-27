<p align="center">
    <a href="https://sylius.com" target="_blank">
        <picture>
          <source media="(prefers-color-scheme: dark)" srcset="https://media.sylius.com/sylius-logo-800-dark.png">
          <source media="(prefers-color-scheme: light)" srcset="https://media.sylius.com/sylius-logo-800.png">
          <img alt="Sylius Logo." src="https://media.sylius.com/sylius-logo-800.png">
        </picture>
    </a>
</p>

<h1 align="center">Sylius AI Dev Tools</h1>

<p align="center">Dev-only bootstrap pack for your AI experience in Sylius.</p>

## About

`sylius/sylius-ai-dev-tools` bootstraps the AI developer experience for [**Sylius**](https://sylius.com) 2.x projects. One install wires up the MCP server and Claude Code skills you need to work on Sylius features with an AI assistant, in both new and existing Sylius projects.

The pack is **dev-only**. Install it as a `require-dev` dependency; never ship it to production.

What it installs:

- **MCP**: the [Sylius Mate Extension](https://github.com/Sylius/sylius-mate-extension), exposing the running Sylius kernel (resources, hooks, grids, routes, Twig helpers, mailer, …) to AI assistants over the Model Context Protocol.
- **Skills**: the [`Sylius/sylius-ai-dev-skills`](https://github.com/Sylius/sylius-ai-dev-skills) Claude Code marketplace, with skills for building Sylius features idiomatically (resources, admin CRUD, grids, hooks, emails, fixtures, …).

## Installation

Add the pack as a dev dependency of your Sylius project:

```bash
composer require --dev sylius/sylius-ai-dev-tools
```

Then bootstrap everything with a single command:

```bash
vendor/bin/sylius-ai init
```

`sylius-ai init` runs Mate init + discover, then prompts to register the Sylius skills marketplace and install the skills via `claude plugin`. Restart Claude Code afterwards.

## Bug Tracking

Report bugs or suggest ideas via [GitHub issues](https://github.com/Sylius/sylius-ai-dev-tools/issues).

## Community Support

Get Sylius support on [Slack](https://sylius.com/slack), [Forum](https://forum.sylius.com/) or [Stack Overflow](https://stackoverflow.com/questions/tagged/sylius).

## MIT License

Released under the terms of the [MIT License](LICENSE).
