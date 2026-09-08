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

`sylius/sylius-ai-dev-tools` pins the AI developer experience for [**Sylius**](https://sylius.com) 2.x projects to a known-compatible set of versions, so you don't have to work out which `sylius-mate-extension` and `symfony/ai-symfony-mate-extension` releases fit together.

The pack is **dev-only**. Install it as a `require-dev` dependency; never ship it to production.

What it pins:

- **Tools**: the [Sylius Mate Extension](https://github.com/Sylius/sylius-mate-extension), exposing the running Sylius kernel (resources, hooks, grids, routes, Twig helpers, mailer, …) to AI coding agents as Mate CLI tools (`vendor/bin/mate tools:call …`).
- **Skills**: `sylius-mate-extension` also ships the `sylius-dev` skill (via Mate's native skill distribution), with guidance for building Sylius features idiomatically (resources, admin CRUD, grids, hooks, emails, fixtures, …).

## Installation

Add the pack as a dev dependency of your Sylius project:

```bash
composer require --dev sylius/sylius-ai-dev-tools
```

Composer will ask whether to trust `symfony/ai-mate-composer-plugin`; answer yes, it is what re-runs extension discovery after every `composer install`/`update`. In non-interactive installs (CI, Docker builds) Composer silently blocks unknown plugins instead of asking, so allow it up front there with `composer config allow-plugins.symfony/ai-mate-composer-plugin true`.

Then bootstrap Mate:

```bash
vendor/bin/mate init
composer dump-autoload
vendor/bin/mate discover
```

`init` creates `mate/` (config, generated agent instructions, `mate/src/` for your own tools) and registers the `Mate\` autoloader in `composer.json`; run `composer dump-autoload` right after it, since anything you put in `mate/src/` is silently invisible to Mate until the autoloader is dumped. Both Mate commands also maintain a managed block in `AGENTS.md` and `CLAUDE.md` telling your coding agent how to call Mate.

`discover` installs the `sylius-dev` skill (and any other Mate-distributed skills) into `.agents/skills/` as `mate-*` copies, with mirror symlinks in `.claude/skills/`. Both folders are generated and rebuilt by Mate (`skills:install`), so add them to your project's `.gitignore`:

```gitignore
.agents/skills/mate-*
.claude/skills/mate-*
```

Restart Claude Code afterwards to load the skill.

## Bug Tracking

Report bugs or suggest ideas via [GitHub issues](https://github.com/Sylius/sylius-ai-dev-tools/issues).

## Community Support

Get Sylius support on [Slack](https://sylius.com/slack), [Forum](https://forum.sylius.com/) or [Stack Overflow](https://stackoverflow.com/questions/tagged/sylius).

## MIT License

Released under the terms of the [MIT License](LICENSE).
