---
layout: default
lang: en
lang_alt: /
title: direct-chat/isle · serverless peer-to-peer messaging
description: direct-chat — messages travel directly between two devices. No server, no accounts — if both devices are online, you can reach each other.
---

<section class="hero">
  <div class="container">
    <p class="eyebrow">Peer-to-peer messaging · prototype stage</p>
    <h1 class="title">direct-chat<span class="title-app">/isle</span></h1>
    <p class="lede">
      Messages travel directly between two devices.
      <em>No server, no accounts</em> — as long as both devices are online, you can reach each other.
    </p>
    <div class="meta">
      <span class="status">
        <span class="dot"></span>
        Current client: <code>isle</code>
      </span>
      <span class="status">
        <span class="dot dot-dim"></span>
        Windows x64 · Android
      </span>
    </div>
    <ul class="dl-list">
      <li class="dl-item">
        <div class="dl-info">
          <span class="dl-name">Android<span class="dl-tag">native</span></span>
          <p class="dl-desc">
            Written for Android itself — better background survival, notifications, and system dialler integration. Its current build does not yet implement messaging.
          </p>
        </div>
        <div class="dl-actions">
          <a class="btn btn-primary" href="{{ site.download_android }}">
            Download APK
            <span class="btn-note">v{{ site.native_version }} · free</span>
          </a>
          {%- for store in site.app_stores %}
          <a class="btn btn-ghost" href="{{ store.url }}" target="_blank" rel="noopener">
            {{ store.name }}
            {%- if store.note_en %}
            <span class="btn-note">{{ store.note_en }}</span>
            {%- endif %}
          </a>
          {%- endfor %}
        </div>
      </li>
      <li class="dl-item">
        <div class="dl-info">
          <span class="dl-name">Windows<span class="dl-tag">x64 · prototype</span></span>
          <p class="dl-desc">
            The desktop build of the cross-platform prototype — messaging, voice and video calls all work. Please read the <a href="#limits">known limitations</a> first.
          </p>
        </div>
        <div class="dl-actions">
          <a class="btn btn-primary" href="{{ site.download_windows }}">
            Download exe
            <span class="btn-note">v{{ site.proto_version }}</span>
          </a>
        </div>
      </li>
    </ul>
    <p class="dl-hint">
      Previous releases live on <a href="{{ site.releases_url }}" target="_blank" rel="noopener">GitHub Releases</a>.
    </p>
    <p class="hero-notice">
      <strong>Disclaimer:</strong> This software is a technical research and teaching example. No platform service is provided. Users bear all risks. <a href="#disclaimer">Read full disclaimer →</a>
    </p>
  </div>
</section>

<section id="disclaimer" class="section section-alt">
  <div class="container narrow">
    <h2>Disclaimer</h2>
    <p class="callout">
      Please read the following terms carefully before using the direct-chat software (including the <code>isle</code> client). Downloading, installing, or using this software constitutes acceptance of this disclaimer in full.
    </p>

    <h3>Nature of the software</h3>
    <p>
      direct-chat is a personal <strong>technical research and teaching example</strong> project, not a commercially released product. The software is in the prototype stage; its functionality and stability have not been validated at scale and may contain known or unknown defects.
    </p>

    <h3>No platform, no data control</h3>
    <p>
      This project does not provide or operate any central platform service. All communication data is generated, transmitted, and stored solely on the users' own devices. The project maintainer does not hold, store, or control any user data. This means:
    </p>
    <ul>
      <li>The maintainer cannot access, view, or manage your communication content;</li>
      <li>The maintainer cannot assist in recovering lost data or resetting identities;</li>
      <li>The maintainer cannot guarantee the reachability or reliability of communications.</li>
    </ul>

    <h3>Prohibited uses</h3>
    <p>
      Users must not use this software for any purpose that violates applicable laws or regulations, including but not limited to infringing on others' privacy, distributing illegal content, compromising network security, engaging in fraud, or other criminal activities. Users must ensure their use is lawful and compliant with the laws of their jurisdiction.
    </p>

    <h3>Use at your own risk</h3>
    <p>
      This software is provided "as is," without any express or implied warranty, including but not limited to warranties of merchantability, fitness for a particular purpose, and non-infringement. Users bear all risks and consequences of using this software. The project maintainer shall not be liable for any direct or indirect damages arising from the use of or inability to use this software.
    </p>

    <h3>Other</h3>
    <ul>
      <li>The maintainer reserves the right to modify, suspend, or terminate the software, or update any part of its functionality, at any time without prior notice.</li>
      <li>This disclaimer may be updated from time to time; the version displayed on the website at the time of access shall prevail.</li>
      <li>If you have any questions, please contact the maintainer via the <a href="#connect">contact information</a>.</li>
    </ul>
  </div>
</section>

<section id="why" class="section">
  <div class="container narrow">
    <h2>Why this exists</h2>
    <p>
      It started with a small frustration: one day my kid was home alone, and I realized I had no simple, direct way to reach him.
    </p>
    <ul class="plain-list">
      <li>We had an old phone, but no spare SIM card for it — and without a phone number, messaging apps that use numbers for accounts simply won't install.</li>
      <li>The landline stays unplugged, thanks to spam calls.</li>
      <li>Self-hosting a chat server is doable, but public network access is restrictive and the setup is a lot of work.</li>
    </ul>
    <p>
      That turned into a question: <em>is there a way to communicate whose only requirement is “both ends have a network connection”?</em>
    </p>
    <p>
      Then I came across <a href="https://www.iroh.computer/blog/v1" target="_blank" rel="noopener">the iroh 1.0 announcement</a>, and the answer became clear: peer-to-peer.
      If you know the other side's identity (their peer), you can deliver a message straight to their device — no intermediary service required.
      direct-chat is a series of experiments built around that idea.
    </p>
  </div>
</section>

<section id="features" class="section section-alt">
  <div class="container narrow">
    <h2>What makes it different</h2>
    <div class="feature-grid">
      <div class="feature-card">
        <h3>No servers involved</h3>
        <p>Messages and calls travel directly between the two devices. No middleman — and nothing that disappears when someone else's service does.</p>
      </div>
      <div class="feature-card">
        <h3>No account system</h3>
        <p>No phone number or email signup. Your identity is a key you hold; your device is identified by its own unique ID.</p>
      </div>
      <div class="feature-card">
        <h3>Privacy by construction</h3>
        <p>Nothing passes through a third-party server, so there is no middle layer that could hold your conversations.</p>
      </div>
      <div class="feature-card">
        <h3>Just needs a network</h3>
        <p>Both devices online — same LAN, or both on the internet — is all it takes. No account, no plan, no SIM card.</p>
      </div>
    </div>
  </div>
</section>

<section id="status" class="section">
  <div class="container narrow">
    <h2>What direct-chat/isle does today</h2>
    <p>
      <strong>direct-chat</strong> is the name of the project; <strong>isle</strong> is the client you install and run — every build is published under that name.
      What it already does (this describes the prototype you can download above; see the <a href="{{ '/en/faq/' | relative_url }}">FAQ</a> for how the native Android version differs):
    </p>
    <ul class="feature-list">
      <li>
        <span class="bullet"></span>
        <div><strong>Device &amp; identity management</strong> — create p2p nodes, generate device IDs, create or share identities.</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>Address book</strong> — exchange public information between nodes and keep it for later.</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>Messaging</strong> — direct plaintext / markdown messaging between isle nodes.</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>Calls</strong> — direct WebRTC audio / video calls between isle nodes.</div>
      </li>
    </ul>
  </div>
</section>

<section id="screens" class="section section-alt">
  <div class="container">
    <h2>Windows prototype UI</h2>
    <p class="section-sub">These are from the <code>isle</code> prototype downloadable above (Windows x64). For the native Android build, see the demo in <a href="#how">quick start</a>.</p>

    <div class="shot-grid">
      <figure class="shot">
        <img src="{{ '/screenshots/list_other_contacts_en.png' | relative_url }}" alt="Contacts list" loading="lazy" />
        <figcaption>Contacts list — chat, voice, and video entry points</figcaption>
      </figure>
      <figure class="shot">
        <img src="{{ '/screenshots/chat_with_text_en.png' | relative_url }}" alt="Text chat" loading="lazy" />
        <figcaption>Text chat — plaintext / markdown</figcaption>
      </figure>
    </div>

    <figure class="shot shot-wide">
      <img src="{{ '/screenshots/call_from_left_to_write.png' | relative_url }}" alt="Outgoing call" loading="lazy" />
      <figcaption>Calling — both sides see calling / incoming states</figcaption>
    </figure>

    <figure class="shot shot-wide">
      <img src="{{ '/screenshots/videocall_from_right_to_left.png' | relative_url }}" alt="Video call" loading="lazy" />
      <figcaption>Video call — direct WebRTC</figcaption>
    </figure>
  </div>
</section>

<section id="how" class="section">
  <div class="container narrow">
    <h2>Quick start</h2>
    <ol class="steps">
      <li>
        <span class="step-num">1</span>
        <div>
          <h4>Download and install</h4>
          <p>Windows x64 or Android. Follow the setup wizard: configure networking, name the device, optionally set an identity.</p>
        </div>
      </li>
      <li>
        <span class="step-num">2</span>
        <div>
          <h4>Add a contact</h4>
          <p>Find the other device automatically on the LAN, or enter its device ID directly (exchanged out of band — in person, or via any other channel).</p>
        </div>
      </li>
      <li>
        <span class="step-num">3</span>
        <div>
          <h4>Talk</h4>
          <p>With both sides online, chat or start a voice / video call.</p>
        </div>
      </li>
    </ol>

    <figure class="demo">
      <video controls preload="metadata" playsinline
             src="{{ '/assets/isle-demo-v1.mp4' | relative_url }}"></video>
      <figcaption>Native Android demo · ~50 seconds: setup, adding a contact (LAN discovery), starting a call.</figcaption>
    </figure>
  </div>
</section>

<section id="limits" class="section section-alt">
  <div class="container narrow">
    <h2>Known limitations</h2>
    <p class="callout">
      The limitations below are real, and some may never be fixed.
    </p>

    <h3>Data compatibility</h3>
    <p>
      After an upgrade, old data is not guaranteed to work. A change in the first two version-number segments almost always means an incompatible data format; a change in the third alone generally doesn't affect your data.
    </p>

    <h3>Platforms &amp; UI</h3>
    <p>
      The prototype is built with tauri, so full-platform coverage is possible in principle, but only the Windows build exists today; Android is served by the separate native version.
      The UI targets phone-sized screens; desktop only gets basic adaptation.
    </p>

    <h3>Missing features</h3>
    <ul>
      <li>No file transfer yet.</li>
      <li>No import / export of data (keys, address book, chat history).</li>
      <li>Notification sounds, call history, disconnect handling and many other details are unfinished.</li>
    </ul>

    <h3>Both sides must be online</h3>
    <p>
      There is no server holding messages for you: if one side goes offline, delivery fails.
      The native Android build keeps itself online with a background service and prompts you to grant the permissions it needs — with those granted, going to the background no longer stops it receiving.
      Some vendor ROMs (MIUI, for instance) will still kill the app in certain situations, though, and there is no guarantee against that. More details in the <a href="{{ '/en/faq/' | relative_url }}">FAQ</a>.
    </p>
  </div>
</section>

<section id="roadmap" class="section">
  <div class="container narrow">
    <h2>What's next</h2>
    <p class="section-sub">
      There are two builds now: the prototype and the native Android version. They share the same core and differ in interface and how deeply each fits into its system — both continue in parallel.
    </p>
    <ol class="roadmap">
      <li>
        <span class="prio">P1</span>
        <div>
          <h4>Auxiliary nodes — build &amp; integrate</h4>
          <p>Develop relay, discovery, and message-holding nodes and integrate them into the existing clients, easing the “both sides online at once” constraint.</p>
        </div>
      </li>
      <li>
        <span class="prio">P2</span>
        <div>
          <h4>Rework the prototype UI</h4>
          <p>Rebuild the prototype interface around the design the native Android version establishes — same core underneath, one shared experience on top.</p>
        </div>
      </li>
      <li>
        <span class="prio">P3</span>
        <div>
          <h4>Android native: Android TV</h4>
          <p>Adapt the native Android version for Android TV — bigger screens and remote-control interaction.</p>
        </div>
      </li>
      <li>
        <span class="prio">P4</span>
        <div>
          <h4>Messaging polish &amp; file transfer</h4>
          <p>Round out messaging and add peer-to-peer file transfer.</p>
        </div>
      </li>
    </ol>
  </div>
</section>

<section id="connect" class="section section-connect">
  <div class="container narrow">
    <h2>Let's talk</h2>
    <p>
      This is a prototype built to test an idea, and I'd love to hear your take:
      how it feels to use, what broke, or what you think “communicate with nothing but a network connection” should look like.
    </p>
    <div class="connect-grid">
      <a class="connect-card" href="mailto:cliff@clifftop.win">
        <span class="connect-label">Email</span>
        <span class="connect-value">cliff@clifftop.win</span>
        <span class="connect-desc">Questions and suggestions — just write.</span>
      </a>
      <a class="connect-card" href="https://github.com/CliffHan/direct-chat-release" target="_blank" rel="noopener">
        <span class="connect-label">GitHub</span>
        <span class="connect-value">CliffHan/direct-chat-release</span>
        <span class="connect-desc">Releases, updates, and issue tracking.</span>
      </a>
    </div>
    <p class="connect-note">
      There's no open-source plan for now — but that's never stopped a good conversation. All feedback is welcome.
      More questions in the <a href="{{ '/en/faq/' | relative_url }}">FAQ</a>.
    </p>
  </div>
</section>
