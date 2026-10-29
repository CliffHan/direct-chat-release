---
layout: default
permalink: /en/faq/
lang: en
lang_alt: /faq/
title: FAQ · direct-chat/isle
description: Frequently asked questions about direct-chat and isle — devices and identities, staying online, encryption and privacy, and how it compares to other tools.
---

<section class="section">
<div class="container narrow" markdown="1">

## FAQ

Common questions about direct-chat and isle. Didn't find yours? Write to <cliff@clifftop.win>.

<h3 class="faq-group">Concepts</h3>

<h3 class="faq-q">What's the relationship between devices and identities?</h3>

Each device can bind to at most one identity; one identity can be shared by several devices.

The relationship is established like this:

1. A device may be initialized without an identity and run as an “anonymous device”.
2. Creating an identity after initialization binds the device to that identity.
3. To organize several devices under one identity, share it: an identity-less device sends a sharing request to your own device that already holds the identity, and once approved, those devices present the same identity to others.

Once bound, the association cannot simply be removed — the only way out is resetting the device's data, which turns it back into a “new device” that starts over.

What a reset does to your data depends on the build:

- **Desktop (Windows / macOS)**: export an encrypted backup and import it during initialization — or simply leave the config file and database (default `isle.toml` and `isle.db`) in place, or back them up and put them back. Both files live in the system's app data directory: `%APPDATA%\com.cliff.isle` on Windows, `~/Library/Application Support/com.cliff.isle` on macOS, and the app has a shortcut that opens that directory for you.
- **Android, native build**: export an encrypted backup, then import it during initialization, and your address book, chat history, and identity all come back.

How a backup works: when you **export**, you set a password, the backup is encrypted with it, and it is saved to the device's Downloads folder by default. When you **import**, you pick the file through the system file picker and enter the same password to decrypt it. The password is never uploaded anywhere and the developer has no means of decrypting the file. That cuts both ways: no one else ends up holding a readable copy, but there is no way to recover a forgotten password either — lose it and that backup cannot be opened.

<h3 class="faq-q">What does “node” mean?</h3>

Every device running isle is a p2p network node with its own unique device ID. All communication happens between nodes; an identity is more than the “name card” a node presents — it also carries the signing and encryption keys that confirm the sender and the recipient of a message are who you intend them to be.

<h3 class="faq-q">Desktop or native Android version — which is which?</h3>

Both are builds of the same client, <code>isle</code>: same core, same feature set, differing in interface and in how deeply each fits into its system.

- **Desktop** — shipped as Windows x64 and macOS (universal), with an interface designed for desktop windows. The macOS build is not notarized, so the first launch needs a manual override — see the question below.
- **Native Android version** — written against Android itself, so the parts that lean on the system (background survival, notifications, a call UI that integrates with the system dialler and comes up on the lock screen) behave far better, with layouts adapted for both phones and tablets.

Both are downloadable from the [homepage]({{ '/en/' | relative_url }}); older builds live on [GitHub Releases]({{ site.releases_url }}).

Unless a question says otherwise, everything else in this FAQ that mentions Android refers to the native Android build.

<h3 class="faq-group">Using it</h3>

<h3 class="faq-q">Do the two devices have to be on the same LAN?</h3>

No. Across networks, connections are established through the iroh network — at this stage you need to enable “free relay network” in the app's network settings.

It currently uses the infrastructure provided by n0. With IPv6 availability much better than it used to be, most everyday cases connect directly peer-to-peer and rarely need a relay at all. Self-hosted relays / DNS can be added later if needed.

<h3 class="faq-q">Messages arrive, but voice or video calls won't connect — why?</h3>

Known issue: on some networks messages go through fine, but a call never connects.

The app uses two different ways to connect peers: messages travel over iroh, while for a call **only the signalling** goes over iroh — the media connection is established by WebRTC itself. An iroh connection succeeds on most networks, so messages almost always get through; whether WebRTC can connect depends on both sides' networks allowing a direct path (NAT, firewalls and carrier policies can all block it), and there's currently no TURN server to fall back on.

So “signalling works” does not mean “media works”. What you see: the call UI shows the connection state moving along, then it fails at the point where the media connection should be established.

Fixing this properly needs a TURN relay server, so calls that can't connect directly can have their media relayed — that's part of the auxiliary server work and isn't possible in the near term. For now, try a different network (a phone hotspot, another Wi-Fi): a different NAT situation may let the direct path succeed, though there's no guarantee.

<h3 class="faq-q">The macOS build says the developer cannot be verified — what now?</h3>

The macOS build is ad-hoc signed and not notarized by Apple, so Gatekeeper blocks the first launch. How you allow it depends on your macOS version:

- **macOS 15 (Sequoia) and later**: double-click once, dismiss the warning, then open System Settings → Privacy &amp; Security, scroll to the Security section and click “Open Anyway”, confirming when asked. **Right-click → Open no longer works on these versions.**
- **macOS 14 and earlier**: right-click the app icon → “Open”, then click “Open” again in the dialog.

You can also strip the quarantine flag from Terminal with `xattr -dr com.apple.quarantine /Applications/isle-desktop.app` (assuming the app is in your Applications folder) and then just double-click it.

Note also that ad-hoc signing has no stable developer identity, so after installing a new build macOS may ask for camera and microphone permission again.

<h3 class="faq-q">How do I keep the Android app alive?</h3>

There is no server holding messages, so the receiving end must keep isle online.

The native Android build keeps itself online with a background service: on first use the app prompts you to grant the permissions it needs. Grant those and going to the background no longer stops it staying online and taking incoming calls.

Granted permissions are not a guarantee, though — some vendor ROMs, MIUI in particular, will still kill the app in certain situations, and there is nothing the app can do about that. These help, depending on your device:

- **MIUI / Xiaomi**: open the recent-apps switcher, long-press the isle card, and choose “Lock” so it survives one-tap cleanup.
- **Other Chinese ROMs**: most have similar mechanisms — disable battery optimization for isle and allow autostart / background running.
- **If it still misses things**: keep it plugged in, set screen timeout to the maximum (or always-on), and keep isle in the foreground as a last resort.

Behavior varies a lot between ROMs. If you find something that works on your device, write in and I'll add it here.

<h3 class="faq-q">Can I move my data to a new machine?</h3>

Yes.

**Native Android version** — export an encrypted backup on the old phone, then import it during setup on the new one, and your address book, chat history, and identity all come back.

**Desktop** (Windows / macOS) — export a backup on the old machine and import it during setup on the new one.

The backup route requires remembering the password — there is no way to recover it. And since the protocol isn't settled and the database format keeps changing (see [known limitations]({{ '/en/' | relative_url }}#limits) on the homepage), moving across major versions isn't guaranteed to work.

> On desktop there's a simpler route: copy `isle.toml` and `isle.db` from the app data directory straight across — no password involved, with the same caveat about major versions.

<h3 class="faq-q">Will old data survive an upgrade?</h3>

Not guaranteed. The protocol is still maturing and the database / config formats keep changing:

- A change in the **first two** version-number segments almost certainly means an incompatible data format — old data can no longer be used.
- A change in the **third** segment generally doesn't touch the database format, so old data should work.

<h3 class="faq-q">Do messages support markdown?</h3>

Yes. Both the desktop and the native Android build render markdown, but they don't share the same implementation — the exact syntax they support differs, and both are still incomplete. If a message doesn't render the way you expect, that's usually why.

mermaid diagrams work on both. They're rendered by the WebView, so if it's too old a diagram may fail to appear or come out wrong — update WebView to the latest version your system supports.

<h3 class="faq-group">Privacy &amp; security</h3>

<h3 class="faq-q">Who can see my messages?</h3>

Only the sender and the recipient.

Messages travel over iroh's peer-to-peer connections using a custom protocol, and are end-to-end encrypted via QUIC by default. Even when traffic occasionally goes through a relay, the relay only ever sees encrypted data.

If server nodes are added in the future to hold messages: point-to-point messages will be encrypted with the recipient's identity key, so only the recipient can decrypt them — the server is a “storage box that can't read what's inside”.

<h3 class="faq-q">Where are my keys stored? What if I lose them?</h3>

isle has no account system and no login — the config is bound to the device, so there is no “password” in the first place, and nothing to “recover”. Keys stay on the device and are never uploaded:

- **Android**: in the app's private directory.
- **Desktop**: in the system's app data directory (Windows `%APPDATA%\com.cliff.isle`, macOS `~/Library/Application Support/com.cliff.isle`).

There are two kinds of keys, and losing them has different consequences:

- **Device key**: generated when the device is initialized; it's the device's identity on the network. If lost, it cannot be recovered — the only option is resetting the data and starting over as a new device.
- **Identity key**: generated when the identity is created. If lost, it can be brought back through the sharing flow described above, as long as another device still holds the same identity; if every device sharing it has lost it, a new identity is the only option.

One thing to keep in mind: the old identity's public key stays in your contacts' address books, so after creating a new identity you'll need to notify contacts out-of-band (in person, by phone, …) to update theirs. In other words, the responsibility for keeping your identity and devices trustworthy rests with you — no server vouches for you, which is one of the fundamental differences from traditional instant messaging.

<h3 class="faq-group">Plans &amp; other</h3>

<h3 class="faq-q">What are “auxiliary nodes”? Isn't that just servers again?</h3>

In a sense, yes — a server is essentially just a computer that stays on 24/7. Its value: when a server exists, messages have somewhere to wait even if the target device is offline, which removes the “both sides online at once” constraint.

The current thinking is to **let users self-host their servers**: the infrastructure stays in the user's hands, and so does the storage of their messages.

Server nodes could also support group chats, but in that case the server holds the group key, so the server administrator would be able to read group messages. That's a trade-off in the future design, not a current feature.

<h3 class="faq-q">How is this different from Signal / Tox / Briar?</h3>

- **Signal**: mature and pleasant to use, but requires registering with a phone number and depends on officially operated servers.
- **Tox**: technically the closest. Tox relies on DHT for node discovery; direct-chat builds on the iroh network, where DHT is just one possible way to find devices — more flexible, more self-directed, and iroh's base infrastructure can be self-hosted and replaced too.
- **Briar**: emphasizes passing messages between devices through many channels (Tor, LAN, Bluetooth) for harsher environments. direct-chat is simpler and more direct.
- The core of direct-chat is **returning data ownership to the user**: use and self-host your own private communication network without having to understand complex concepts.

<h3 class="faq-q">Why not open source?</h3>

Technical feasibility still needs to be proven, and my bandwidth is limited — open-sourcing too early would bring noise and distraction. Questions and suggestions are always welcome regardless.

<h3 class="faq-q">Which operating systems are supported?</h3>

- **Windows / Android** — what I use day to day; messaging, voice and video calls and the other main features have all been verified in practice.
- **macOS** — same codebase as the Windows build, compiled from the same tauri project; it has been tested and works on macOS, but I don't use it day to day, so the testing isn't thorough. Reports are welcome.
- **iOS** — not supported. The system doesn't let ordinary apps listen in the background indefinitely, and isle has to stay online to receive messages: once iOS suspends the app, messages for it simply don't arrive. In theory a machine that's always on (or an auxiliary node) could hold them, but that needs a whole extra mechanism — not something I can do in the near term.
- **Linux** — building the desktop version for Linux is technically possible, but the WebView that ships with each distribution varies in how well it supports WebRTC (what voice and video calls are built on), so shipping one wouldn't guarantee calls actually work. Once Tauri 3 lands and apps can bundle their own browser engine (CEF), that dependency on the system WebView goes away — I'll revisit it then.

So only Windows and Android have been verified through regular use; nothing else has been properly verified — macOS has had basic functional testing only.

<h3 class="faq-q">I found a bug — how do I report it?</h3>

Include your OS version, app version (e.g. v{{ site.native_version }}) and steps to reproduce, then email <cliff@clifftop.win> or open an issue on the [GitHub repo](https://github.com/CliffHan/direct-chat-release).

</div>
</section>
