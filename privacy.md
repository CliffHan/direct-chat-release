---
layout: default
permalink: /privacy/
lang: en
title: Privacy Policy · direct-chat
description: How the direct-chat applications, currently isle, handle your information — no accounts, no servers, no analytics; messages stay on your devices; advertising is served by third-party SDKs.
---

<section class="section">
<div class="container narrow" markdown="1">

<h1 class="page-title">Privacy Policy</h1>

<p class="legal-meta">Effective {{ site.legal_effective_date }} · Last updated {{ site.legal_last_updated }} · Applies to the {{ site.legal_project }} applications, currently <code>{{ site.legal_app }}</code>, and to this website</p>

<p class="callout"><strong>The short version:</strong> direct-chat has no accounts, no servers, and no analytics or crash reporting of my own. Your contacts and messages are stored only on your own device and on the devices of the people you talk to; as the developer I operate no backend service, so I have no way to read, store, or produce your messages. When a direct device-to-device connection cannot be established, traffic is relayed through the public iroh relay network, and relayed data stays encrypted end to end. Setting up a call also involves queries to public STUN/ICE servers, which see only the network addresses involved and never your content. The Apps are ad-supported: advertisements are served by third-party SDKs through {{ site.legal_ads_platform }}, and those SDKs collect device identifiers and ad-interaction data for their own advertising purposes, as explained in section 6.</p>

<nav class="toc" aria-label="On this page">
  <p class="toc-title">On this page</p>
  <ol>
    <li><a href="#who">Who this policy is from</a></li>
    <li><a href="#scope">Scope</a></li>
    <li><a href="#not-collected">Information that is never collected</a></li>
    <li><a href="#on-device">Information stored on your device</a></li>
    <li><a href="#transmitted">Information transmitted over the network</a></li>
    <li><a href="#advertising">Advertising and third-party SDKs</a></li>
    <li><a href="#permissions">Device permissions</a></li>
    <li><a href="#retention">How long information is kept</a></li>
    <li><a href="#sharing">Sharing, selling and legal requests</a></li>
    <li><a href="#security">Security</a></li>
    <li><a href="#children">Children's privacy</a></li>
    <li><a href="#rights">Your rights and choices</a></li>
    <li><a href="#transfers">International data transfers</a></li>
    <li><a href="#website">This website</a></li>
    <li><a href="#store">Summary for app store data safety declarations</a></li>
    <li><a href="#changes">Changes to this policy</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</nav>

### 1. Who this policy is from
{: #who}

**{{ site.legal_project }}** is the name of the project. **{{ site.legal_app }}** is the name of the client application published under it, currently for Android and Windows. In this policy, the "**Apps**" means {{ site.legal_app }} together with any other application I publish under the {{ site.legal_project }} name, and the "**Software**" means those Apps. Where a section applies to one App only, it says so.

The project is developed and maintained by {{ site.legal_developer }} ("I", "me", "the developer"). I am the controller for the personal information described in this policy, which in practice means: I control an app and a website, not a copy of your data.

Two notes on scope, since the project may grow:

- This policy covers every App published under the {{ site.legal_project }} name. If a future App handles information in a materially different way, this policy will be updated before that App is published, or that App will be given its own policy.
- The version published at this URL is the one that applies to the App you are using.

### 2. Scope
{: #scope}

This policy explains what happens to information when you use the Apps and when you visit this website. It does not cover third-party apps, services, or advertising partners that you may encounter through the Apps or the website; those are governed by their own policies.

Direct-chat is peer-to-peer software that you install and run yourself. It is not a communications service that I operate for you, and there is no contractual relationship between us beyond the licence granted in the [Terms of Service]({{ '/terms/' | relative_url }}).

### 3. Information that is never collected
{: #not-collected}

Direct-chat is built so that **I**, as the developer, never receive your data. I do not collect, receive, or store:

- **Account information** — there is no sign-up: no email address, phone number, user name, or password is requested or verified.
- **Your contacts** — your address book is never uploaded to me and never synced with any service I operate. It leaves your device only in ways you control: the details you publish are exchanged with the peers you add, and in builds that support it they are included in a backup you export yourself (section 4). I receive nothing in either case.
- **Message and call content** — messages, files, and call audio or video are exchanged directly between devices and are not copied to, recorded by, or stored on any server operated by me.
- **Analytics or crash reports** — the app contains no analytics and no crash-reporting SDK, and sends no usage statistics, logs, or diagnostics back to me.
- **Location** — the app does not currently request location permissions and does not collect GPS or precise location data.
- **Payment data** — the Software is currently distributed free of charge and no payment is processed. If paid options are introduced later, payment would be handled by the distribution platform or another external payment provider; card details and similar payment credentials would go to that provider, not to me.

Advertising SDKs described in section 6 are the one exception to this section: they do collect information for their own purposes, and that information goes to those providers rather than to me.

**A note on what comes next.** What is written above describes the Software as it exists today. Features that have been considered but are not built — sharing location between contacts, or paid options handled through an external platform — are therefore deliberately not described here. Anything that changes what is collected or how it moves will appear in an updated version of this policy before it reaches your device, together with whatever system permission prompt or consent applies. This policy will not quietly start being untrue.

### 4. Information stored on your device
{: #on-device}

Everything the app needs to work is created and kept on your own device:

- **Device identity** — a device ID and its key pair, generated locally the first time the app runs.
- **Identity (optional)** — the name, avatar, and key pair of an identity you create, if you choose to create one.
- **Address book** — the names and public keys of the peers you have added.
- **Messages and files** — the conversations you send and receive, including any attachments.
- **Settings and local logs** — application preferences and diagnostic logs kept on the device for troubleshooting.

The two platforms do not protect this data equally. On Android it lives in the app's private storage, inside the sandbox the operating system enforces — other apps and other users cannot read it on a device that has not been compromised. On Windows there is no equivalent protection: the data is a SQLite database (address book and chat history) and a TOML file (identity and settings) sitting alongside the application, readable by your own account, by any other account that can reach those files, and by anyone who can read the disk. If you run the Windows build on a shared, portable, or easily accessed machine, protect those files the way you would protect any sensitive document — or use full-disk encryption.

Some builds of the app let you export an encrypted backup of this data and import it again when the app is initialized.

- **Export.** A backup is created only when you ask for one. You set a password, and the backup is encrypted with that password before it is written. By default it is saved to your device's standard Downloads folder; on Windows you can pick a different location. Because Downloads is a shared folder, an exported backup is no longer inside the app's private storage — other apps that can read that folder, or anyone who can browse the device's files, may be able to copy the file. What they would get is an encrypted file, not readable conversations.
- **Import.** You choose the backup file through the system file picker and enter the same password. The app decrypts it on your device and restores the data. Nothing is uploaded in either direction.

A backup is a copy of the data listed above, so it contains your identity keys and your chat history. Two things follow from the password design: your password is never transmitted to me and is not stored anywhere I can reach, so I hold no copy of the backup and have no way to decrypt one; and that means I cannot help you recover it either. If the file is lost, or the password is forgotten, the data in that backup is unrecoverable.

Audio and video from calls are streamed to the other participant; they are not recorded or stored by me, and they are not retained on my side after the call ends.

### 5. Information transmitted over the network
{: #transmitted}

- **To the recipient's device.** Messages, files, and call media are encrypted on your device and decrypted on the recipient's device. In the normal case they travel directly between the two devices.
- **Over the local network.** When both devices are on the same network, the Apps can discover the peer and connect directly, without traffic leaving that network.
- **When a call is set up (STUN/ICE).** Calls run over WebRTC, and for two devices to connect directly each side has to learn how its own address appears from the outside. The Apps do this by sending small queries to public STUN/ICE servers: publicly available endpoints run by unrelated third parties, a mix of cloud, network and other internet providers, including servers operated by Google and Cloudflare. Such a server sees only the IP address and port the query came from. No message content and no call media passes through it, and in the current implementation these endpoints are used only to discover addresses, never to carry traffic. Which endpoints are used is not a fixed list: they may be added, replaced or dropped between releases, and the app does not depend on any single provider. Messages, files and call signalling do not go through these servers — signalling is exchanged over the same encrypted iroh connection as the messages themselves.
- **Through relay servers, when a direct connection is not possible.** Across NATs or restrictive networks, traffic is relayed through the iroh network. The default relay servers are operated by number0, Inc. (n0), a third party. A relay forwards already-encrypted packets; it can observe metadata such as IP addresses, node identifiers, connection times, and data volumes, but it cannot decrypt content and does not store messages. Support for running your own relay is planned but is not available yet; until then, the default relays operated by number0 are the ones in use. You can switch off the "free relay network" option in the app's network settings, in which case the app connects only when it can find a direct path.
- **For peer discovery.** Depending on your network settings, a peer is found through local network discovery, through a distributed hash table (DHT), or through a discovery service operated by number0, Inc. With DHT discovery, the lookup is served by other nodes participating in that DHT, which learn which node ID you are looking for; with number0's discovery service, that provider learns it instead. A discovery lookup reveals only the node ID being sought — never message content.

No other party receives your message content. Because the network is peer-to-peer, the people you communicate with necessarily receive the messages, files, and call media you send them.

### 6. Advertising and third-party SDKs
{: #advertising}

The app is free and ad-supported. Advertisements are delivered through {{ site.legal_ads_platform }}, a third-party advertising platform that works with a number of advertising networks and demand partners. The platform in use is not fixed: it may be changed in a future release, in which case this policy is updated to match.

Advertising SDKs run inside the app and communicate directly with those providers. They may collect and use:

- **Device identifiers**, such as the Android advertising ID;
- **Device and connection information**, such as device model, OS version, language, carrier, and IP address (from which an approximate location may be inferred);
- **Advertising data**, such as which ads were shown, viewed, or tapped, and interactions with them.

This data is used for advertising purposes: selecting and delivering ads, measuring ad performance, frequency capping, fraud prevention, and — where permitted — personalising ads. Some of these activities are treated as "sale" or "sharing" of personal information under certain privacy laws; see section 12 for your choices. Advertising providers act as independent controllers for the data they collect, and their handling of it is governed by their own privacy policies, not by this one. The platform's own privacy policy describes it and the partner networks it works with — see [{{ site.legal_ads_platform }}]({{ site.legal_ads_privacy_url }}) — and the partners active at any time can change without notice to me.

To be clear about what advertising does **not** mean here: I receive no analytics, usage statistics, or crash reports from the app, ads are served independently of your conversations, and the content of your messages and calls is never used for advertising.

### 7. Device permissions
{: #permissions}

The app requests the permissions it needs to work as a peer-to-peer messenger and calling client. Each permission is used only for the purpose below:

- **Connectivity** — <code>INTERNET</code>, <code>ACCESS_NETWORK_STATE</code>, <code>ACCESS_WIFI_STATE</code>, <code>CHANGE_WIFI_MULTICAST_STATE</code>: to open direct peer-to-peer connections, to discover peers on the local network, and (for advertising SDKs) to load ads.
- **Staying reachable** — <code>FOREGROUND_SERVICE</code> and <code>FOREGROUND_SERVICE_SPECIAL_USE</code>, <code>WAKE_LOCK</code>: to keep a foreground service running so the app can listen for incoming connections, messages, and calls while it is in the background.
- **Notifications** — <code>POST_NOTIFICATIONS</code>: to alert you to incoming messages. You can turn notifications off in system settings.
- **Incoming calls** — <code>USE_FULL_SCREEN_INTENT</code> and <code>SYSTEM_ALERT_WINDOW</code>: to bring up the incoming-call screen when the device is locked or when another app is in the foreground.
- **Telecom integration** — <code>MANAGE_OWN_CALLS</code>, <code>MODIFY_AUDIO_SETTINGS</code>, <code>READ_PHONE_STATE</code>: to register a connection service with the Android telecom framework (<code>TelecomManager</code>) so that calls made in the app are managed by the system alongside regular cellular calls and do not conflict with them, and to route call audio correctly. <code>READ_PHONE_STATE</code> is used only for that telecom integration — the app does not read your phone number, your IMEI or any other device identifier, or your call history.
- **Camera and microphone** — <code>CAMERA</code>, <code>RECORD_AUDIO</code>, <code>FOREGROUND_SERVICE_CAMERA</code>, <code>FOREGROUND_SERVICE_MICROPHONE</code>: used only while you are making a call or capturing a photo or video to send. They are never activated in the background or without you starting that action.
- **Battery optimisation (optional)** — <code>REQUEST_IGNORE_BATTERY_OPTIMIZATIONS</code>: so the app can stay online when you are away from it. You can decline; messages may then arrive late or not at all while the app is not in the foreground.

The app does **not** request access to your contacts, your precise or approximate location, your SMS messages, or your call history, and it does not request general access to your files. When it needs to read a file you have chosen — attaching one to a message, or importing a backup — it does so through the system file picker. When it exports a backup, it writes to the shared Downloads folder through the system's media store. Neither path requires a general storage permission, and neither gives the app access to the rest of your files.

One note on how calls are wired in: the app registers a connection service with the system telecom framework so its calls behave like ordinary phone calls (they appear in the call UI, and audio focus is handled by the system). This is a system integration rather than a permission — it gives the app no additional access to your data, and only the Android system itself can bind to that service.

### 8. How long information is kept
{: #retention}

There is no server-side retention period, because there is no server. Messages and files remain on your device and on your recipient's device until someone deletes them.

You can remove local data at any time by deleting individual conversations, by using the in-app reset (on Android this erases the address book and chat history; on Windows you can delete the SQLite and TOML files or keep them as a backup), or by uninstalling the app. An exported backup is a separate copy that none of those actions touch — delete the backup file itself to get rid of it.

Advertising providers keep the data they collect for their own retention periods, which I do not control; see their privacy policies.

Please note a consequence of peer-to-peer design: I cannot delete copies of your messages that remain on other people's devices, and neither can you. If that matters for a conversation, do not send the message.

### 9. Sharing, selling and legal requests
{: #sharing}

As the developer, I do not sell, rent, or trade personal information for money, and I do not disclose it to third parties for their own analytics or marketing.

Two kinds of transmission do occur, and are described elsewhere in this policy:

- **Network infrastructure** (section 5) — relays and discovery services act purely as carriers of encrypted traffic, and the public STUN/ICE servers queried when a call is set up see only network addresses. None of them receive your message content or call media.
- **Advertising SDKs** (section 6) — advertising providers receive device identifiers, IP-derived approximate location, and ad-interaction data for their own advertising and measurement purposes. Some privacy laws describe this as "sharing" or "selling"; where that is the case, you can exercise the choices in section 12.

If I were ever served with a legal request for user data, I would have nothing to hand over: I hold no accounts, no message content, and no communication records. I would respond accordingly and, unless legally prohibited, notify the person affected.

### 10. Security
{: #security}

Messages, files, and call media are encrypted end to end between devices, using keys that are generated on and never leave your device. Relay servers and any other network hop only ever see encrypted payloads.

You are responsible for the security of your own device and keys:

- Keep your device locked and updated.
- Keep backups of your Windows data files in a safe place; anyone who can read those files can read your history.
- An exported backup is only as strong as the password you protect it with. Choose a long one you will not forget, keep the file where only you can reach it, and delete copies you no longer need. There is no password reset: a forgotten password means that backup cannot be opened, by you or by anyone else.
- Without a backup, a lost or reset device key is gone for good, and an identity can only be recovered from another device that still holds it. Where a build supports encrypted backup, that backup is your safety net — and the password protecting it is its only key.
- The Windows build’s data files have no sandbox around them: unlike the Android build, they can be read by any account that can reach them. Use full-disk encryption (BitLocker) or store them where only your own account can reach.
- Verify a contact's identity out of band before trusting it; no server vouches for anyone.

If you believe you have found a security vulnerability, please contact me at <{{ site.legal_email }}> before disclosing it publicly, and I will respond as quickly as I can.

### 11. Children's privacy
{: #children}

Direct-chat is a general-audience communication tool — comparable to a phone or SMS app in that it can be used by anyone, including older children, but it is not designed, marketed, or intended to appeal specifically to children. It is not directed to children under 13, and I do not knowingly collect personal information from children. Because the app has no sign-up and no server, no age information is requested or recorded, and advertising shown in it is not knowingly targeted at children.

If a child uses the app, a parent or guardian should manage the device and the contact list, since the app provides no parental controls or content filtering. If you believe a child has provided personal information to me, contact <{{ site.legal_email }}>; as I hold no data, the practical remedy is to delete the conversation or reset the app on the child's device, which a parent or guardian can do at any time.

### 12. Your rights and choices
{: #rights}

**Your data.** Depending on where you live, you may have rights to access, correct, delete, or export your personal information, and to object to or restrict certain processing. Because I hold no personal information, there is nothing for me to access, correct, export, or delete — you already have direct and complete control over your data on your own device, through the app itself (delete conversations, reset data, uninstall). Where a build supports backup and import, exporting a backup is your export right, and deleting the backup file deletes that copy. If you nonetheless believe I hold information about you, write to <{{ site.legal_email }}> and I will confirm my position and, if there is anything to delete, delete it. I will not treat you differently for exercising a privacy right.

**Advertising choices.** Device-level advertising controls work independently of the app, whether or not the release you are running shows ads:

- On Android you can reset or delete your advertising ID, and turn on "Opt out of Ads Personalization", in the device's settings — usually Settings → Privacy → Ads, though the exact wording and location vary by manufacturer and Android version. Opting out makes ads less relevant rather than removing them; it does not stop advertising SDKs from loading.
- Where the law requires it (for example in the EEA, the UK, or certain US states), the app will ask for your consent before personalised advertising is shown, and you can change or withdraw that choice in the app's privacy settings.
- Installing an ad-blocking DNS or another device-level content blocker is up to you; doing so may affect how the app behaves.

I do not sell your personal information for money. Where a jurisdiction treats interest-based advertising as "sale" or "sharing", the controls above are how you opt out.

### 13. International data transfers
{: #transfers}

The peers you connect to, the relay and discovery servers used to reach them, the public STUN/ICE servers queried when a call is set up, and the advertising providers that serve ads may be located in a country other than your own. Message content is encrypted before it leaves your device, so it is not readable in transit. Advertising data is handled by those providers under their own transfer safeguards. Cross-border transmission is inherent to how a peer-to-peer network and third-party advertising work, and is not something I can route or restrict.

### 14. This website
{: #website}

The direct-chat website is a set of static pages. It does not use accounts, login, or contact forms, and it does not set advertising cookies on its own.

The website does load Google AdSense, a third-party advertising service. Google and its partners may use cookies or similar technologies to serve and measure ads, and may collect information such as your IP address and interactions with ads, subject to Google's own privacy policy. You can control ad personalisation through Google's ad settings and through your browser's cookie controls. Blocking or removing cookies does not affect the Apps, which are independent of the website's advertising.

### 15. Summary for app store data safety declarations
{: #store}

This section is provided to help keep the data safety declarations I file with app stores consistent with this policy. It is a summary, not a substitute for the declaration itself:

- **Data collected by the developer:** none. No data is transmitted off the device to me, and there is no analytics or crash-reporting SDK.
- **Data collected by third parties (advertising):** device or other identifiers (advertising ID), approximate location derived from IP address, and app activity / ad interactions — collected by advertising SDKs through {{ site.legal_ads_platform }} for advertising, measurement, and fraud prevention, and shared with advertising partners.
- **Message and call content:** never collected by me or by advertising providers; transmitted in encrypted form between devices.
- **Encrypted in transit:** yes, all user data transmitted by the app is encrypted in transit.
- **Deletion:** there is no server-side data of mine to delete; users delete local data in the app or by uninstalling. Advertising providers retain data under their own policies.
- **Independent security review:** none has been performed. This is a personally developed project, not a certified product.

If a given release ships without advertising, no advertising-related data is collected in that release, and the declaration is adjusted accordingly. If a store's declaration options and this policy ever appear to conflict, this policy describes what the software actually does.

### 16. Changes to this policy
{: #changes}

I may update this policy as the software changes — for example when advertising is introduced or when self-hosted relays become available. When I do, I will revise the "Last updated" date at the top of this page and, for material changes, note it on the website or in the release notes. The version published here is the one that applies. Continuing to use the software after a change means you accept the updated policy.

### 17. Contact
{: #contact}

Questions, requests, or complaints about privacy:

- Email: <{{ site.legal_email }}>
- Issues: [GitHub repository](https://github.com/CliffHan/direct-chat-release)
- Postal address: {{ site.legal_address }}

I read everything that arrives at that address, though as a one-person project I may take a little while to reply.

<p class="legal-updated">See also: <a href="{{ '/terms/' | relative_url }}">Terms of Service</a> · <a href="{{ '/en/' | relative_url }}#disclaimer">Disclaimer</a></p>

</div>
</section>
