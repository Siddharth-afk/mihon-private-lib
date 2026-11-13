<div align="center">

# Tijori

### Mihon, with a private shelf
A manga, webtoon and comic reader for Android, built on [Mihon](https://github.com/mihonapp/mihon), with a hidden,
PIN-protected folder inside the library.

[![CI](https://img.shields.io/github/actions/workflow/status/Siddharth-afk/mihon-private-lib/build.yml?labelColor=27303D)](https://github.com/Siddharth-afk/mihon-private-lib/actions/workflows/build.yml)
[![License: Apache-2.0](https://img.shields.io/github/license/Siddharth-afk/mihon-private-lib?labelColor=27303D&color=0877d2)](/LICENSE)

*Tijori (तिजोरी) is Hindi for a safe or strongbox.*

*Requires Android 8.0 or higher.*

</div>

> [!NOTE]
> Tijori is an unofficial fork. It is not affiliated with or supported by the Mihon project, so please don't
> report Tijori issues to them. It installs as its own app (`app.tijori`) and can sit next to Mihon on the same
> phone.

## What Tijori adds

### Protected folder

Move entries into a folder that only opens with a 4-digit PIN. While it is locked, nothing in the app shows that
those entries exist.

- **Hidden everywhere while locked:** the Library tabs and counts, Updates, History and its resume button, Stats,
  Upcoming, the home-screen widget, the download queue, and library update notifications. In browse and global
  search they show as not in your library.
- **No visible entry point:** there is no tab, button or menu item for it. Long-press the **Library** title to
  open the PIN pad.
- **Locks itself:** when the app goes to the background, when you leave the folder, and after a period without
  interaction (1 minute by default, changeable). Reading a chapter from the folder doesn't count as idle.
- **Brute-force protection:** five wrong PINs in a row lock entry for 30 seconds, and every further wrong PIN
  doubles the wait.
- **Secure screen:** the folder is blank in the recent-apps view and can't be screenshotted.
- **Biometric unlock (optional):** fingerprint or face unlock, falling back to the PIN. The phone's own PIN or
  pattern is not accepted.
- **Stays up to date:** protected entries are still checked for new chapters and auto-downloaded, silently.
- **Forgot PIN:** the PIN pad offers a reset that permanently deletes everything in the folder, including
  downloads and reading history, then lets you set a new PIN. You have to type `DELETE` to confirm.

### Backups

- Protected entries are left out of backups unless you turn on **Include in manual backups** inside the folder.
- When included, they restore back into the folder, not the visible library.
- Automatic backups never include them, and the PIN is never backed up.

### Everything else from Mihon

- Local reading of content.
- A configurable reader with multiple viewers, reading directions and other settings.
- Tracker support: [MangaBaka](https://mangabaka.org), [MyAnimeList](https://myanimelist.net/),
  [AniList](https://anilist.co/), [Kitsu](https://kitsu.app/), [MangaUpdates](https://mangaupdates.com),
  [Shikimori](https://shikimori.one), [Bangumi](https://bgm.tv/) and [Hikka](https://hikka.io/).
- Categories to organize your library.
- Light and dark themes.
- Scheduled library updates for new chapters.
- Local backups, to read offline or keep in your cloud service.

## Using the protected folder

1. Long-press the **Library** title and set a 4-digit PIN.
2. In the Library, long-press an entry to select it, open the **⋮** menu in the bottom bar and choose
   **Move to protected folder**.
3. To see protected entries, long-press the Library title again and enter the PIN.
4. To return an entry to the library, select it inside the folder and choose **Remove from protected folder**.
5. Change or remove the PIN under **Settings → Security and privacy → Protected folder**. Removing the PIN returns
   every entry to the library.

## What the protected folder does not protect against

- **It is for casual snooping on an unlocked phone.** It doesn't stop someone with root access or access to the
  app's private storage: the database isn't encrypted, and a 4-digit PIN can be guessed offline in minutes.
- **Anyone who can open the PIN pad can wipe the folder** through "Forgot PIN?". That is the intended way back in
  for someone who forgot their PIN.
- **Downloaded chapters** of protected entries stay in the normal download folder, where a file manager can see
  them.
- **Opening an entry from its source** shows its real state (in library, chapters read). Only the "in library"
  marker in browse and search results is hidden.
- **Once a PIN is set**, the "Move to protected folder" action and the settings section are visible, which tells
  an observer the feature is in use.
- **Trackers** still receive reading progress for protected entries.

The full design, the list of every hidden view and the backup rules are in
[docs/protected-library-folder.md](docs/protected-library-folder.md).

## Download

There are no prebuilt releases yet; build the app yourself:

1. Install JDK 21 and the Android SDK (Android Studio includes both).
2. Clone this repository and run `./gradlew assembleDebug`.
3. Install `app/build/outputs/apk/debug/app-arm64-v8a-debug.apk` on your phone, or
   `app-universal-debug.apk` if your phone isn't 64-bit ARM.

## Credits

Tijori is built on the work of the [Mihon](https://github.com/mihonapp/mihon) contributors and, before them,
the Tachiyomi project. All credit for the reader itself goes to them.

<a href="https://github.com/mihonapp/mihon/graphs/contributors">
    <img src="https://contrib.rocks/image?repo=mihonapp/mihon" alt="Mihon app contributors" title="Mihon app contributors" width="800"/>
</a>

### Disclaimer

The developer(s) of this application do not have any affiliation with the content providers available, and this
application hosts zero content.

### License

<pre>
Copyright © 2015 Javier Tomás
Copyright © 2024 Mihon Open Source Project

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
</pre>
