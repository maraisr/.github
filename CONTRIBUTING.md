# Contribution Guide

Hi there 👋 glad you could make it, super stoked you decided to contribute to one of my projects~! ❤️

This is a very general guide, and anything specific will be noted in the project itself.

## 🧪 Getting ready

I program on a Mac, so most of this guide will be geared towards nix based machines and setup through my
[`dotfile`](https://github.com/maraisr/dotfiles).

> **Note**: [`.editorconfig`](#editorconfig)'s are at play, make sure your IDE supports it.

### 🟨 JavaScript based projects

You'll find most of my projects use now use [`pnpm`](https://pnpm.io), there may still be a scattering of npm and yarn
around. See them, squash it and help [raise a pull request 🚀](#raising-a-pull-request) migrating to pnpm.

1. install [Node](https://nodejs.org)
1. install [`pnpm`](https://pnpm.io/installation) (stable)
1. install dependencies — `pnpm i`

> **Note**: my projects include a `volta` property in the `package.json` file that indicates the node version for the project. I do suggest you
> install [`volta`](https://docs.volta.sh/guide/) to make sure we are both on the same toolchain.

### 🟧 Rust based projects

My projects typically run on the `nightly` channel, but for the most part the MSRV if not specified in the project
readme will be `1.64.0`, managed through [rustup](https://rust-lang.github.io/rustup/installation/index.html).

In these projects you'll find a `.rust-toolchain.toml` that describes the targets and channel/version to run against, so
just a matter of the `cargo build` and `cargo test` we know and love.

> **Note**: `cargo fmt` **MUST** be used before raising PR's

## 🫶 Raising a Pull Request

### Lets have a cin-wag[^2] first

[^2]: cin-wag: the motion created when one speaks.

Sometimes the direction your pull request might go in might not quite align with the design goals of the project. So
let's save both our times here, and have a cin-wag.

If you're raising any typo fixes, or bumping versions, or you're a maintainer of another dependency please go straight
to a pull request.

### Commit Convention

Marais uses a personally adapted [Conventional Commit](https://www.conventionalcommits.org/en/v1.0.0/) but very similar,
please have a read of that first to gain the context.

Format:

```
<type>: <summary>

[long winded description]

[fixes: <issue number>]
```

- **type**: `chore` | `feat` | `fix` | `docs` | `ci`. But I use `chore` for all the business-as-usual commits.

<details><summary>Example</summary>

```
feat: `charCode`'s over doing a `toString` in tail check

Typically charCode comparison is faster than doing a to toString, then slicing to check a certain character

fixes: #56
```

</details>

I use these commits to
[automatically generate release notes](https://docs.github.com/en/repositories/releasing-projects-on-github/automatically-generated-release-notes)
where only `feat` and `fix`'s will be noted.

Please keep these commits short-n-sweet, although no enforced but generally keep the first line of the commit under 50
characters.

### Pull Request

Now that you're ready to raise the PR (pull request), you can follow
[this guide](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)
on creating your very PR on GitHub.

| Step                | Example                                                                                                                                                                                                                                |
| :------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.&nbsp;set a title | Your PR title should also follow the [commit convention](#commit-convention). <br /> eg `feat: polish message output format`                                                                                                           |
| 2.&nbsp;description | Your PR description should autofill with the commit description, please do describe the change in more depth. Typically I like using the **why** _then_ **how**. Firstly describe why your change is the way it is, then how it works. |
| 3.&nbsp;comment     | Firstly, don't over comment the points of interest. But please annotate at least the main moment of the PR. Sometimes there is lots of boilerplate around a change, and easily missing the point. So please do call it out.            |

Should your PR be resolving an issue, add a `fixes: #123` at the tail end of your PR description. Merging this PR will
then automatically close that issue. Learn more
[here](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword).

All my projects are setup with "Squash and Merge" so feel free to have as many commits as you like, no need to rebase.
But if possible, let your commits tell a story, than a series of `wip` and `f*** you` commits.

## 📓 References

### Volta

A node version manager for node and toolchains.

```sh
curl https://get.volta.sh | bash
volta install node
```

when using any of the scripts `pnpm run` or `node index.js` or whatever, Volta will ensure the correct version is running.

### `.editorconfig`

My projects all use this as the base `.editorconfig`.

```
root = true

[*]
charset = utf-8
end_of_line = lf
indent_style = tab
indent_size = 4
insert_final_newline = true
trim_trailing_whitespace = true
```

### Prettier

My projects all should have a root `.prettierrc` file denoting the configuration. But if not this should be the bare
minium configuration:

```yml
useTabs: true
tabWidth: 4
singleQuote: true
```

## 🫡 Resources

- [`maraisr/dotfiles`](https://github.com/maraisr/dotfiles) — my fish configurations and setup
- [`maraisr/tsconfig`](https://github.com/maraisr/tsconfig) — tsconfig file used extended by my projects
- [`fnm`](https://github.com/Schniz/fnm) — the node version manager I use
- [`git config`](https://github.com/maraisr/dotfiles/blob/main/.gitconfig) — the git config/aliases I use
