# RTP Play Kodi video addon

Watch [RTP Play](https://www.rtp.pt/play) in Kodi: live TV and radio, the
on-demand catalogue, and, with an RTP account, your favourites and continue
watching.

Disclaimer: This plugin is not official and is not endorsed by RTP. RTP can
change its website at any time, which may break the add-on.

## Features

- Live TV (RTP1, RTP2, RTP Notícias, RTP Memória, RTP Internacional, ...) and
  live radio (Antena 1, 2, 3, ...)
- Programs by category, with all their episodes
- Search
- Optional RTP account login, for **Os seus favoritos** and **Continuar a ver**,
  kept in sync with the RTP Play website and apps

## Requirements

- Kodi 19 (Matrix) or later. Tested on Kodi 21 (Omega) and 22 (Piers).
- [inputstream.adaptive](https://github.com/xbmc/inputstream.adaptive), for
  RTP2 live and most on-demand TV. These are protected with Widevine DRM.
  Many Kodi builds already include it; on Debian and Ubuntu install the
  `kodi-inputstream-adaptive` package.
- Widevine itself is installed by the add-on the first time you play a
  protected stream (through
  [InputStream Helper](https://github.com/emilsvennesson/script.module.inputstreamhelper)).
  Just accept the prompt.

Content is geo-restricted by RTP, and some programs are only available in
Portugal.

## Installation

### From the Kodi repository

RTP Play is in the official Kodi add-on repository. In Kodi go to
**Add-ons → Install from repository → Kodi Add-on repository → Video add-ons →
RTP Play**, then select **Install**. Dependencies are installed automatically.

New versions reach the repository after they have been reviewed, so the
latest changes may only be available by installing from a zip.

### From a zip file

1. Build the zip from a clone of this repository. The folder inside the zip
   must be called `plugin.video.rtpplay`, so use `git archive` rather than
   GitHub's *Download ZIP*:

   ```sh
   git archive --prefix=plugin.video.rtpplay/ -o plugin.video.rtpplay.zip HEAD
   ```

2. Copy the zip to the device running Kodi, for example over a network share
   or a USB stick.
3. In Kodi, enable **Settings → System → Add-ons → Unknown sources**.
4. Go to **Add-ons → Install from zip file** and choose
   `plugin.video.rtpplay.zip`. Kodi installs the dependencies from its
   official repository.

### For development

Link a clone straight into Kodi's add-on folder, so changes take effect the
next time the add-on runs:

```sh
ln -s "$PWD" ~/.kodi/addons/plugin.video.rtpplay
```

Restart Kodi to pick up a new add-on, or changes to `addon.xml`,
`settings.xml` and the translations. Kodi registers add-ons copied in by hand
as disabled, so enable it under **Add-ons → My add-ons → Video add-ons**. Its
dependencies (`script.module.routing`, `script.module.requests` and
`script.module.inputstreamhelper`) must be installed too, for example by
installing the add-on once from a zip.

## Logging in to your RTP account

Logging in is optional. Without it, everything except favourites and continue
watching works.

1. Open RTP Play and select **Log in to your RTP account**. This is also under
   the add-on's settings, in **Account**.
2. Kodi shows a web address and a code. On your phone or computer, open the
   address, sign in to your RTP account (or create one) and enter the code.
3. Kodi logs in automatically once you approve, and **Os seus favoritos** and
   **Continuar a ver** appear in the main menu.

Your password is only typed on RTP's own login page. Kodi stores just the
login tokens, and renews them so you stay logged in. To log out, use
**Log out** in the add-on's settings.

Once logged in:

- Add or remove a program from your favourites through its context menu.
- Episodes you have partly watched offer to resume where you left off, and
  your progress is saved to your account as you watch.
