---
layout: default
permalink: /en/faq/
lang: en
lang_alt: /faq/
title: FAQ · direct-chat
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

1. A device may be initialized without an identity and run as a “blank device”.
2. Creating an identity after initialization binds the device to that identity.
3. To organize several devices under one identity, share it: an identity-less device sends a sharing request to your own device that already holds the identity, and once approved, those devices present the same identity to others.

Once bound, the association cannot simply be removed — the only way out is resetting the device's data, which turns it back into a “new device” that starts over.

What a reset does to your data depends on the platform:

- **Android**: reset wipes everything — the address book and chat history go with it.
- **Windows**: the address book and chat history live in a SQLite database file, while your identity and other personal info live in a TOML file with the same name. Keep those two files in place (or back them up and restore them), and the data survives the reset.

<h3 class="faq-q">What does “node” mean?</h3>

Every device running isle is a p2p network node with its own unique device ID. All communication happens between nodes; an identity is more than the “name card” a node presents — it also carries the signing and encryption keys that confirm the sender and the recipient of a message are who you intend them to be.

<h3 class="faq-group">Using it</h3>

<h3 class="faq-q">Do the two devices have to be on the same LAN?</h3>

No. Across networks, connections are established through the iroh network — at this stage you need to enable “free relay network” in the app's network settings.

It currently uses the infrastructure provided by n0. With IPv6 availability much better than it used to be, most everyday cases connect directly peer-to-peer and rarely need a relay at all. It works in mainland China. Self-hosted relays / DNS can be added later if needed.

<h3 class="faq-q">How do I keep the Android app alive?</h3>

There is no server holding messages, so the receiving end must keep isle online. What works differs per system:

- **General**: keep it plugged in; set screen timeout to the maximum (or always-on) in system settings; keep isle in the foreground.
- **MIUI / Xiaomi**: open the recent-apps switcher, long-press the isle card, and choose “Lock” so it survives one-tap cleanup.
- **Other Chinese ROMs**: most have similar mechanisms — disable battery optimization for isle and allow autostart / background running.

Behavior varies a lot between ROMs. If you find something that works on your device, write in and I'll add it here.

<h3 class="faq-q">Can I move my data to a new phone?</h3>

Not in the short term. The protocol isn't settled yet — the database / config file formats are still changing, and import / export isn't implemented (see [known limitations]({{ '/en/' | relative_url }}#limits) on the homepage). A new phone means starting over as a “new device”.

<h3 class="faq-q">Will old data survive an upgrade?</h3>

Not guaranteed. The protocol is still maturing and the database / config formats keep changing:

- A change in the **first two** version-number segments almost certainly means an incompatible data format — old data can no longer be used.
- A change in the **third** segment generally doesn't touch the database format, so old data should work.

<h3 class="faq-group">Privacy &amp; security</h3>

<h3 class="faq-q">Who can see my messages?</h3>

Only the sender and the recipient.

Messages travel over iroh's peer-to-peer connections using a custom protocol, and are end-to-end encrypted via QUIC by default. Even when traffic occasionally goes through a relay, the relay only ever sees encrypted data.

If server nodes are added in the future to hold messages: point-to-point messages will be encrypted with the recipient's identity key, so only the recipient can decrypt them — the server is a “storage box that can't read what's inside”.

<h3 class="faq-q">Where are my keys stored? What if I lose them?</h3>

isle has no account system and no login — the config is bound to the device, so there is no “password” in the first place, and nothing to “recover”. Keys stay on the device and are never uploaded:

- **Android**: in the app's private directory.
- **Windows**: in the same directory as the app itself.

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

<h3 class="faq-q">What about iOS / macOS / Linux?</h3>

The prototype can technically be compiled for these platforms, but I don't have the bandwidth to verify and fix platform-specific issues right now, so they're on hold.

<h3 class="faq-q">I found a bug — how do I report it?</h3>

Include your OS version, app version (e.g. v{{ site.app_version }}) and steps to reproduce, then email <cliff@clifftop.win> or open an issue on the [GitHub repo](https://github.com/CliffHan/direct-chat-release).

</div>
</section>
