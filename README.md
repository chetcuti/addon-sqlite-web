# Community Hass.io Add-ons: SQLite Web

[![GitHub Release][releases-shield]][releases]
![Project Stage][project-stage-shield]
[![License][license-shield]](LICENSE.md)

[![GitLab CI][gitlabci-shield]][gitlabci]
![Project Maintenance][maintenance-shield]
[![GitHub Activity][commits-shield]][commits]

[![Bountysource][bountysource-shield]][bountysource]
[![Discord][discord-shield]][discord]
[![Community Forum][forum-shield]][forum]

[![Buy me a coffee][buymeacoffee-shield]][buymeacoffee]

Explore your Home-Assistant database from your web browser!

## About

This enables you to easily explore all tables and content that is saved in your database.

![sample view](/images/sample-view.png)

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Hass.io add-on.

1. [Add our Hass.io add-ons repository][repository] to your Hass.io instance.
1. Install the "SQLite Web" add-on.
1. Start the "SQLite Web" add-on
1. Check the logs of the "SQLite Web" add-on to see if everything went well.
1. Click "OPEN WEB UI" to open the SQLite Web interface.

**NOTE**: Starting the add-on might take a couple of minutes (especially the
first time starting the add-on).

**NOTE**: Do not add this repository to Hass.io, please use:
`https://github.com/hassio-addons/repository`.

## Docker status

![Supports armhf Architecture][armhf-shield]
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports i386 Architecture][i386-shield]

[![Docker Layers][layers-shield]][microbadger]
[![Docker Pulls][pulls-shield]][dockerhub]

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```json
{
  "log_level": "info",
  "database_path": "home-assistant_v2.db",
  "read_only": true,
  "datasette": false,
  "username": "MarryPoppins",
  "password": "Supercalifragilisticexpialidocious",
  "ssl": true,
  "certfile": "fullchain.pem",
  "keyfile": "privkey.pem",
  "ipv6": false
}
```

**Note**: _This is just an example, don't copy and past it! Create your own!_

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`:  Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

### Option: `database_path`

The path for the database file relative to `/config/`

### Option: `read_only`

Open the database in read only mode if `true`.
**It is not recommended setting this to `false`,
this will enable you to corrupt the database!**

### Option: `datasette`

This option enables the optional service [Datasette]
that can serve as an API to your DB.
This endpoint will be exposed to port `6220`

### Option: `username`

Username for authenticating with the SQLite Web interface. Leaving the username
field empty, will disable the authentication mechanism entirely.

Setting a username/password can be added as an extra line of defense,
to prevent users of using your installation for themselves.

This option is HIGHLY recommended in case you expose this add-on to the outside
world.

**Note**: _This option support secrets, e.g., `!secret sqlite-web_username`._

### Option: `password`

Password for authenticating with SQLite Web interface.

**Note**: _This option support secrets, e.g., `!secret sqlite-web_password`._

### Option: `ssl`

Enables/Disables SSL (HTTPS) on the web interface of SQLite Web. Set it `true`
to enable it, `false` otherwise.

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default for Hass.io_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default for Hass.io_

### Option: `ipv6`

Set this option too `false` to disable IPv6 support.

### Option: `i_like_to_be_pwned`

Adding this option to the add-on configuration allows to you bypass the
HaveIBeenPwned password requirement by setting it to `true`.

**Note**: _We STRONGLY suggest picking a stronger/safer password instead of
using this option! USE AT YOUR OWN RISK!_

### Option: `leave_front_door_open`

Adding this option to the add-on configuration allows you to disable
authentication on the add-on by setting it to `true` and leaving the
username and password empty.

**Note**: _We STRONGLY suggest, not to use this, even if this add-on is
only exposed to your internal network. USE AT YOUR OWN RISK!_

## Embedding into Home Assistant

It is possible to embed SQLite Web directly into Home Assistant, allowing you to
access your SQLite Web through the Home Assistant frontend.

Home Assistant provides the `panel_iframe` component, for these purposes.

Example configuration:

```yaml
panel_iframe:
  sqlite-web:
    title: SQLite Web
    icon: mdi:database
    url: https://address.to.your.hass.io:6210
```

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality. The format of the log is based on
[Keep a Changelog][keepchangelog].

Releases are based on [Semantic Versioning][semver], and use the format
of ``MAJOR.MINOR.PATCH``. In a nutshell, the version will be incremented
based on the following:

- ``MAJOR``: Incompatible or major changes.
- ``MINOR``: Backwards-compatible new features and enhancements.
- ``PATCH``: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The [Community Hass.io Add-ons Discord chat server][discord] for add-on
  support and feature requests.
- The [Home Assistant Discord chat server][discord-ha] for general Home
  Assistant discussions and questions.
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

You could also [open an issue here][issue] GitHub.

## Contributing

This is an active open-source project. We are always open to people who want to
use the code or contribute to it.

We have set up a separate document containing our
[contribution guidelines](CONTRIBUTING.md).

Thank you for being involved! :heart_eyes:

## Authors & contributors

The original setup of this repository is by [Joakim Sørensen][ludeeus].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## We have got some Hass.io add-ons for you

Want some more functionality to your Hass.io Home Assistant instance?

We have created multiple add-ons for Hass.io. For a full list, check out
our [GitHub Repository][repository].

## License

MIT License

Copyright (c) 2018 Joakim Sørensen

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[anchore-shield]: https://anchore.io/service/badges/image/67d1185473090e99d5ac5e1bb4d1aa2295117a9bd3d7abbf8cd8a71e331c8388
[anchore]: https://anchore.io/image/dockerhub/hassioaddons%2Funifi%3Alatest
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[bountysource-shield]: https://img.shields.io/bountysource/team/hassio-addons/activity.svg
[bountysource]: https://www.bountysource.com/teams/hassio-addons/issues
[buymeacoffee-shield]: https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg
[buymeacoffee]: https://www.buymeacoffee.com/ludeeus
[commits-shield]: https://img.shields.io/github/commit-activity/y/hassio-addons/addon-sqlite-web.svg
[commits]: https://github.com/hassio-addons/addon-sqlite-web/commits/master
[contributors]: https://github.com/hassio-addons/addon-sqlite-web/graphs/contributors
[Datasette]: https://github.com/simonw/datasette
[discord-ha]: https://discord.gg/c5DvZ4e
[discord-shield]: https://img.shields.io/discord/478094546522079232.svg
[discord]: https://discord.me/hassioaddons
[dockerhub]: https://hub.docker.com/r/hassioaddons/sqlite-web
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg
[forum]: https://community.home-assistant.io/t/community-hass-io-add-on-sqlite-web/68912
[ludeeus]: https://github.com/ludeeus
[gitlabci-shield]: https://gitlab.com/hassio-addons/addon-sqlite-web/badges/master/pipeline.svg
[gitlabci]: https://gitlab.com/hassio-addons/addon-sqlite-web/pipelines
[home-assistant]: https://home-assistant.io
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg
[issue]: https://github.com/hassio-addons/addon-sqlite-web/issues
[keepchangelog]: http://keepachangelog.com/en/1.0.0/
[layers-shield]: https://images.microbadger.com/badges/image/hassioaddons/sqlite-web.svg
[license-shield]: https://img.shields.io/github/license/hassio-addons/addon-sqlite-web.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2019.svg
[microbadger]: https://microbadger.com/images/hassioaddons/sqlite-web
[project-stage-shield]: https://img.shields.io/badge/project%20stage-experimental-yellow.svg
[pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/sqlite-web.svg
[reddit]: https://reddit.com/r/homeassistant
[releases-shield]: https://img.shields.io/github/release/hassio-addons/addon-sqlite-web.svg
[releases]: https://github.com/hassio-addons/addon-sqlite-web/releases
[repository]: https://github.com/hassio-addons/repository
[semver]: http://semver.org/spec/v2.0.0.htm
