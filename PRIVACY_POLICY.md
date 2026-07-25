# Privacy Policy for PodPlay

**Last Updated:** July 25, 2026

PodPlay ("we", "our", "us") is a podcast player for Android and iOS. This policy explains
exactly what the app stores, what it sends over the network, and to whom. It is written to
match the app's actual behaviour — if you find a discrepancy, treat it as a bug and tell us.

There are no user accounts. You never register, log in, or give us your name or email to
use PodPlay.

---

## 1. Summary

| What | Where it goes |
|---|---|
| Subscriptions, queue, playback positions, history, settings, downloads | Stay on your device |
| Podcast feeds, artwork, episode audio | Fetched directly from the publisher's servers |
| **Ad-skip lookups (podcast name, episode title, episode audio URL, episode description, country, install ID)** | **Sent to our ad-analysis service, `api.dawncast.uk`** |
| Crash reports | Written to your device only; sent nowhere unless you explicitly share one |
| Casting / DLNA discovery | Stays on your local Wi-Fi network |

The ad-skip lookup in bold is the only feature that sends information about your listening
off your device. Section 3 covers it in full, and you can turn it off.

---

## 2. Data Stored on Your Device

The following is written to your device's private app storage and is not transmitted to us:

* **Subscriptions and playlists** — the podcasts you follow and any lists you create.
* **Playback state** — positions, play queue, listening history, completed episodes.
* **Downloaded audio** — episode files you have saved for offline listening.
* **Preferences** — playback speed, skip intervals, sleep timer, download rules, theme.
* **Listening statistics** — total time listened, ads skipped, episodes finished.
* **Crash reports** — see Section 5.

You can erase all of it at any time via your device settings (Android: **Settings > Apps >
PodPlay > Storage > Clear Data**; iOS: delete the app). Uninstalling removes everything.

---

## 3. The Ad-Skip Service

PodPlay can automatically skip advertising inside episodes. Doing this requires analysis
that cannot run on your phone, so the app asks our ad-analysis service about the episode
you are about to play.

### What is sent

When ad-skip is enabled and you play or download an episode, the app sends the following to
`https://api.dawncast.uk/ads`:

* the **podcast name** and **episode title**
* the **episode's audio URL** (the public link from the podcast's RSS feed)
* the **episode description** as published in the feed
* a **country code** (used to select the right regional ad data)
* an **install ID** — see below
* an **entitlement level** — currently always `early_access`

The service replies with the positions of ads in that episode, chapter markers, and, where
one exists, the matching YouTube video ID for the episode.

**What this means in practice:** the service can infer which episodes you play. It does not
receive your name, email, phone number, contacts, location, IP-based profile, advertising
ID, or any device identifier.

### The install ID

The install ID is a random number generated on your device the first time ad-skip runs. It
is **not** derived from your hardware, your Google/Apple account, or any advertising
identifier. It exists so the service can distinguish one installation from another for
abuse prevention and rate limiting, and — when ad-skip becomes a paid feature — to
recognise a valid subscription.

You can view it and generate a fresh one at any time under **Settings > Ad Skip > Install
ID**. Resetting it severs the link between your earlier and later lookups. Clearing app
data or reinstalling also produces a new one.

### Turning it off

**Settings > Ad Skip > Skip ads** disables the feature. When it is off, PodPlay makes no
requests to the ad-analysis service at all. Everything else in the app continues to work.

### Retention

Ad analysis is cached per episode, not per listener, so that the next person to play the
same episode gets an instant answer. Request logs containing install IDs are retained for
no more than 30 days for abuse prevention and are then deleted.

### Pricing

Ad-skip is currently **free for all users during early access**. We intend to make it a
paid subscription feature in future. That change will not alter what is described above; if
it ever does, this policy will be updated first.

---

## 4. Connections to Third Parties

* **Podcast publishers and hosts.** Searching, refreshing feeds, streaming and downloading
  connect your device directly to the publisher's servers. Those servers see your IP
  address and request headers, as they would with any podcast app. Their privacy policies
  govern that data; we are not involved in the connection.
* **Apple Podcasts search directory.** Podcast search queries are sent to Apple's public
  podcast search API to return results.
* **YouTube.** Video podcast playback uses YouTube's official embedded player. Your
  interaction with it is governed by [YouTube's Terms of Service](https://www.youtube.com/t/terms)
  and the [Google Privacy Policy](https://policies.google.com/privacy).
* **Google Cast, DLNA and AirPlay.** Discovering and controlling speakers or TVs happens
  entirely over your local Wi-Fi network. Nothing about it reaches us.

We do not include any third-party advertising SDK, analytics SDK, attribution SDK, or
tracking library in PodPlay.

---

## 5. Crash Reports

If PodPlay crashes, a technical report (the error, the app version, your Android/iOS
version, and your device model) is written to the app's private storage on your device.

**These are never transmitted automatically.** No crash-reporting service is built into the
app. If you want to help us fix a crash, **Settings > About > Send crash report** hands the
file to your device's share sheet so you can choose to email it to us. Only the ten most
recent reports are kept.

---

## 6. Permissions

Android permissions PodPlay requests, and why:

| Permission | Purpose |
|---|---|
| `INTERNET` | Fetch feeds, stream and download episodes, ad-skip lookups |
| `ACCESS_NETWORK_STATE`, `ACCESS_WIFI_STATE` | Detect Wi-Fi vs mobile data for the "download on Wi-Fi only" rule |
| `CHANGE_WIFI_MULTICAST_STATE` | Discover Cast and DLNA devices on your local network (SSDP multicast) |
| `FOREGROUND_SERVICE`, `FOREGROUND_SERVICE_MEDIA_PLAYBACK` | Keep audio playing when the app is in the background |
| `POST_NOTIFICATIONS` | Show the playback notification and its controls (Android 13+) |
| `WAKE_LOCK` | Prevent the device sleeping mid-episode |
| `RECEIVE_BOOT_COMPLETED` | Re-register the background feed refresh after a restart |

PodPlay requests no access to contacts, location, camera, microphone, or your files.

---

## 7. Children's Privacy

PodPlay is not directed at children under 13, and we do not knowingly collect personal
information from them.

---

## 8. Your Rights

Because the app holds no account and stores nothing about you on our servers beyond
short-lived request logs keyed to a resettable random ID, there is no account to access,
export, or delete. To remove everything: reset your install ID (severs past lookups), then
clear the app's data or uninstall it.

If you are in the UK/EU and want to exercise a right regarding the ad-skip request logs,
contact us with your install ID within the 30-day retention window and we will delete the
matching entries.

---

## 9. Changes

We may update this policy. Material changes — particularly any change to what leaves your
device — will be reflected here with a new "Last Updated" date before the behaviour ships.

---

## 10. Contact

* **Email:** cassian.d123@gmail.com

<!--
  MAINTAINER NOTE — remove this comment before publishing.

  1. The contact address above is a personal Gmail. Play requires a working address on the
     listing; a dedicated one (support@ your domain) is worth setting up before launch,
     and if you do, change it here and in the Play Console together.

  2. Section 3's retention claims ("cached per episode", "logs no more than 30 days") are
     commitments about the SERVER, not the app. Confirm the DawnCast backend actually does
     this before publishing, and change the text if it does not. Publishing a retention
     period you do not honour is worse than publishing none.

  3. Play Data Safety form must match Section 3. Declare: "App activity — other actions"
     as COLLECTED, transmitted off-device, NOT linked to identity, NOT used for tracking,
     user can request deletion. Do not declare "no data collected" — the /ads call makes
     that false and is the fastest route to a policy suspension.

  4. Keep this file, the published copy at
     github.com/cassiand123-dev/podplay-privacy, and the in-app link in sync.
-->
