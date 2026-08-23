---
layout: default
lang: en
lang_alt: /
title: direct-chat · serverless peer-to-peer messaging
description: direct-chat — messages travel directly between two devices. No server, no accounts — if both devices are online, you can reach each other.
---

<section class="hero">
  <div class="container">
    <p class="eyebrow">Peer-to-peer messaging · prototype stage</p>
    <h1 class="title">direct-chat</h1>
    <p class="lede">
      Messages travel directly between two devices.
      <em>No server, no accounts</em> — as long as both devices are online, you can reach each other.
    </p>
    <div class="meta">
      <span class="status">
        <span class="dot"></span>
        Current client: <code>isle</code> v{{ site.app_version }}
      </span>
      <span class="status">
        <span class="dot dot-dim"></span>
        Windows x64 / Android arm64
      </span>
    </div>
    <div class="cta-row">
      <a class="btn btn-primary" href="{{ '/app/isle_v' | append: site.app_version | append: '_' | append: site.app_git_sha | append: '_windows_x64.exe' | relative_url }}">
        Download Windows x64
        <span class="btn-note">v{{ site.app_version }} · exe</span>
      </a>
      <a class="btn btn-primary" href="{{ '/app/isle_v' | append: site.app_version | append: '_' | append: site.app_git_sha | append: '_android_arm64.apk' | relative_url }}">
        Download Android arm64
        <span class="btn-note">v{{ site.app_version }} · apk</span>
      </a>
      <a class="btn btn-ghost" href="#connect">Contact &amp; feedback</a>
    </div>
    <p class="dl-hint">
      This is a prototype — please read the <a href="#limits">known limitations</a> before using it.
      Source and previous releases live on <a href="https://github.com/CliffHan/direct-chat-release" target="_blank" rel="noopener">GitHub</a>.
    </p>
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
    <h2>What isle does today</h2>
    <p>
      <code>isle</code> is the current direct-chat client. It already supports:
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
    <h2>Screenshots</h2>
    <p class="section-sub">Taken from the current build of <code>isle</code>. The app UI itself is bilingual.</p>

    <div class="shot-grid">
      <figure class="shot">
        <img src="{{ '/screenshots/wizard_1_en.png' | relative_url }}" alt="Setup wizard" loading="lazy" />
        <figcaption>Setup wizard — configuring discovery methods</figcaption>
      </figure>
      <figure class="shot">
        <img src="{{ '/screenshots/main_device_wo_identity_en.png' | relative_url }}" alt="Device home" loading="lazy" />
        <figcaption>Device home — before an identity is set</figcaption>
      </figure>
      <figure class="shot">
        <img src="{{ '/screenshots/main_addrbook_with_identity_en.png' | relative_url }}" alt="Address book" loading="lazy" />
        <figcaption>Address book — identity “Alice” in use</figcaption>
      </figure>
      <figure class="shot">
        <img src="{{ '/screenshots/find_other_local_device_en.png' | relative_url }}" alt="LAN discovery" loading="lazy" />
        <figcaption>LAN discovery — other nodes on the same network</figcaption>
      </figure>
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
          <p>Windows x64 or Android arm64. Follow the setup wizard: configure networking, name the device, optionally set an identity.</p>
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
  </div>
</section>

<section id="limits" class="section section-alt">
  <div class="container narrow">
    <h2>Known limitations</h2>
    <p class="callout">
      <code>isle</code> is a prototype built to validate the peer-to-peer approach.
      The limitations below are real, and some may never be fixed.
    </p>

    <h3>Data compatibility</h3>
    <p>
      After an upgrade, old data is not guaranteed to work. A change in the first two version-number segments almost always means an incompatible data format; a change in the third alone generally doesn't affect your data.
    </p>

    <h3>Platforms &amp; UI</h3>
    <p>
      The app is built with tauri, so full-platform coverage is possible in principle, but only Windows and Android aarch64 builds exist today.
      The UI targets phone-sized screens; desktop only gets basic adaptation. Android webview differences across versions make UI glitches hard to avoid.
    </p>

    <h3>Missing features</h3>
    <ul>
      <li>No file transfer yet.</li>
      <li>No import / export of data (keys, address book, chat history).</li>
      <li>Notification sounds, call history, disconnect handling and many other details are unfinished.</li>
    </ul>

    <h3>Both sides must be online</h3>
    <p>
      There is no server holding messages for you: if one side goes offline (especially when the Android app is backgrounded and loses network), delivery fails.
      If you plan to use an old phone as the receiving end, for now it has to stay <em>plugged in, screen on, app in the foreground</em> — more tips in the <a href="{{ '/en/faq/' | relative_url }}">FAQ</a>.
    </p>
  </div>
</section>

<section id="roadmap" class="section">
  <div class="container narrow">
    <h2>What's next</h2>
    <ol class="roadmap">
      <li>
        <span class="prio">P1</span>
        <div>
          <h4>Auxiliary nodes</h4>
          <p>Relay, discovery, and message-holding nodes to ease the “both sides online at once” constraint.</p>
        </div>
      </li>
      <li>
        <span class="prio">P2</span>
        <div>
          <h4>Polish isle</h4>
          <p>Peer-to-peer file transfer, plus notifications, history, connection handling and other details.</p>
        </div>
      </li>
      <li>
        <span class="prio">P3</span>
        <div>
          <h4>Redesign isle</h4>
          <p>Take what the prototype taught us and reimplement — possibly separately per platform.</p>
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
        <span class="connect-desc">Source, releases, and issue tracking.</span>
      </a>
    </div>
    <p class="connect-note">
      There's no open-source plan for now — but that's never stopped a good conversation. All feedback is welcome.
      More questions in the <a href="{{ '/en/faq/' | relative_url }}">FAQ</a>.
    </p>
  </div>
</section>
