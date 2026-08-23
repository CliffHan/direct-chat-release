---
layout: default
lang: zh-CN
lang_alt: /en/
title: direct-chat · 不依赖服务器的点对点即时通信
description: direct-chat：消息直接在设备之间传递，没有服务器、没有账号，只要两台设备都在线，就能互相联系。
---

<section class="hero">
  <div class="container">
    <p class="eyebrow">点对点即时通信 · 原型阶段</p>
    <h1 class="title">direct-chat</h1>
    <p class="lede">
      消息直接在两台设备之间传递。
      <em>没有服务器，没有账号</em>——只要两台设备都在线，就能互相联系。
    </p>
    <div class="meta">
      <span class="status">
        <span class="dot"></span>
        当前客户端：<code>isle</code> v{{ site.app_version }}
      </span>
      <span class="status">
        <span class="dot dot-dim"></span>
        Windows x64 / Android arm64
      </span>
    </div>
    <div class="cta-row">
      <a class="btn btn-primary" href="{{ '/app/isle_v' | append: site.app_version | append: '_' | append: site.app_git_sha | append: '_windows_x64.exe' | relative_url }}">
        下载 Windows x64
        <span class="btn-note">v{{ site.app_version }} · exe</span>
      </a>
      <a class="btn btn-primary" href="{{ '/app/isle_v' | append: site.app_version | append: '_' | append: site.app_git_sha | append: '_android_arm64.apk' | relative_url }}">
        下载 Android arm64
        <span class="btn-note">v{{ site.app_version }} · apk</span>
      </a>
      <a class="btn btn-ghost" href="#connect">联系与反馈</a>
    </div>
    <p class="dl-hint">
      当前为原型版本，使用前请先阅读<a href="#limits">已知限制</a>。
      源码与历史发布见 <a href="https://github.com/CliffHan/direct-chat-release" target="_blank" rel="noopener">GitHub</a>。
    </p>
  </div>
</section>

<section id="why" class="section">
  <div class="container narrow">
    <h2>为什么做这个</h2>
    <p>
      起因是一件小事：有一次孩子单独在家，我想联系他，却发现没有一个简单直接的办法。
    </p>
    <ul class="plain-list">
      <li>家里有旧手机，但孩子没有 sim 卡——没有号码，就装不了以手机号为账号的聊天软件。</li>
      <li>座机因为骚扰电话，常年不插线。</li>
      <li>自建聊天服务器可行，但公网访问限制多，过程也复杂。</li>
    </ul>
    <p>
      于是问题变成了：<em>有没有一种通信方式，对环境的要求低到“只要有网络”？</em>
    </p>
    <p>
      看到 <a href="https://www.iroh.computer/blog/v1" target="_blank" rel="noopener">iroh 1.0 的这篇文章</a>之后，答案清晰起来：点对点通信。
      只要拿到对方的身份（peer），就能把消息直接送到那台设备，不需要任何中间服务。
      direct-chat 就是围绕这个想法的一系列实验软件。
    </p>
  </div>
</section>

<section id="features" class="section section-alt">
  <div class="container narrow">
    <h2>它有什么不同</h2>
    <div class="feature-grid">
      <div class="feature-card">
        <h3>不依赖服务器</h3>
        <p>消息和通话直接在两台设备之间传递。没有中间人，也就没有随服务消失而失效的风险。</p>
      </div>
      <div class="feature-card">
        <h3>没有账号体系</h3>
        <p>不需要手机号或邮箱注册。你的身份就是你自己持有的密钥，设备标识是设备的身份。</p>
      </div>
      <div class="feature-card">
        <h3>隐私天然成立</h3>
        <p>通信不经过任何第三方服务器，没有能拿到你聊天记录的中间环节。</p>
      </div>
      <div class="feature-card">
        <h3>只要有网络</h3>
        <p>两台设备都在线（同一局域网，或都能连上互联网），就可以互相联系。账号、套餐、sim 卡都不需要。</p>
      </div>
    </div>
  </div>
</section>

<section id="status" class="section">
  <div class="container narrow">
    <h2>isle 目前能做什么</h2>
    <p>
      <code>isle</code> 是 direct-chat 当前的客户端，已实现：
    </p>
    <ul class="feature-list">
      <li>
        <span class="bullet"></span>
        <div><strong>设备与身份管理</strong> — 创建 p2p 网络节点，生成设备唯一标识，可创建或共享身份。</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>地址簿</strong> — 节点之间交换公开信息并保存，方便再次联系。</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>消息</strong> — 节点直连收发 plaintext / markdown 消息。</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>通话</strong> — 节点直连进行 WebRTC 音频 / 视频通话。</div>
      </li>
    </ul>
  </div>
</section>

<section id="screens" class="section section-alt">
  <div class="container">
    <h2>应用截图</h2>
    <p class="section-sub">以下截图取自 <code>isle</code> 当前版本。</p>

    <div class="shot-grid">
      <figure class="shot">
        <img src="{{ '/screenshots/wizard_1_zh.png' | relative_url }}" alt="初始化向导" loading="lazy" />
        <figcaption>初始化向导 — 配置网络发现方式</figcaption>
      </figure>
      <figure class="shot">
        <img src="{{ '/screenshots/main_device_wo_identity_zh.png' | relative_url }}" alt="设备主页" loading="lazy" />
        <figcaption>设备主页 — 尚未设置身份时</figcaption>
      </figure>
      <figure class="shot">
        <img src="{{ '/screenshots/main_addrbook_with_identity_zh.png' | relative_url }}" alt="地址簿" loading="lazy" />
        <figcaption>地址簿 — 已设置身份 “Alice”</figcaption>
      </figure>
      <figure class="shot">
        <img src="{{ '/screenshots/find_other_local_device_zh.png' | relative_url }}" alt="局域网查找" loading="lazy" />
        <figcaption>局域网查找 — 自动发现同网下的其他节点</figcaption>
      </figure>
      <figure class="shot">
        <img src="{{ '/screenshots/list_other_contacts_zh.png' | relative_url }}" alt="联系人列表" loading="lazy" />
        <figcaption>联系人列表 — 聊天、语音、视频入口</figcaption>
      </figure>
      <figure class="shot">
        <img src="{{ '/screenshots/chat_with_text_zh.png' | relative_url }}" alt="文本聊天" loading="lazy" />
        <figcaption>文本聊天 — 支持 plaintext / markdown</figcaption>
      </figure>
    </div>

    <figure class="shot shot-wide">
      <img src="{{ '/screenshots/call_from_left_to_write.png' | relative_url }}" alt="呼叫界面" loading="lazy" />
      <figcaption>呼叫界面 — 双方分别显示正在呼叫 / 来电</figcaption>
    </figure>

    <figure class="shot shot-wide">
      <img src="{{ '/screenshots/videocall_from_right_to_left.png' | relative_url }}" alt="视频通话" loading="lazy" />
      <figcaption>视频通话 — WebRTC 直连</figcaption>
    </figure>
  </div>
</section>

<section id="how" class="section">
  <div class="container narrow">
    <h2>快速上手</h2>
    <ol class="steps">
      <li>
        <span class="step-num">1</span>
        <div>
          <h4>下载并安装</h4>
          <p>Windows x64 或 Android arm64，跟随向导完成初始化：设置网络、设备信息，身份可选。</p>
        </div>
      </li>
      <li>
        <span class="step-num">2</span>
        <div>
          <h4>添加联系人</h4>
          <p>局域网内自动查找对方设备，或输入对方的设备唯一标识（带外交换，例如当面或用其他渠道告知）。</p>
        </div>
      </li>
      <li>
        <span class="step-num">3</span>
        <div>
          <h4>开始通信</h4>
          <p>保持双方同时在线，直接聊天，或发起语音 / 视频通话。</p>
        </div>
      </li>
    </ol>
  </div>
</section>

<section id="limits" class="section section-alt">
  <div class="container narrow">
    <h2>已知限制</h2>
    <p class="callout">
      <code>isle</code> 的当前实现是原型，目的是验证点对点通信这条路线。
      以下限制客观存在，部分可能不会解决。
    </p>

    <h3>数据兼容性</h3>
    <p>
      版本升级后，无法保证旧数据必定可用。版本号前两位的变化基本意味着数据格式不兼容；仅第三位变化一般不影响数据。
    </p>

    <h3>平台与界面</h3>
    <p>
      应用基于 tauri，理论上可覆盖全平台，目前只编译 Windows 和 Android aarch64 版本。
      UI 按手机小屏设计，桌面端只有简单自适应。Android 不同版本的 webview 差异较大，界面问题基本难以避免。
    </p>

    <h3>功能缺口</h3>
    <ul>
      <li>尚不支持文件传输。</li>
      <li>尚不支持数据（密钥、地址簿、聊天记录）导入导出。</li>
      <li>通知铃声、通话记录、断线处理等细节未完成。</li>
    </ul>

    <h3>双方须同时在线</h3>
    <p>
      没有服务器暂存消息：一方离线（尤其 Android 应用切到后台断网时），另一方就无法送达。
      如果打算用旧手机做受话端，现阶段只能<em>插电、亮屏、保持应用在前台</em>——更多做法见 <a href="{{ '/faq/' | relative_url }}">FAQ</a>。
    </p>
  </div>
</section>

<section id="roadmap" class="section">
  <div class="container narrow">
    <h2>接下来做什么</h2>
    <ol class="roadmap">
      <li>
        <span class="prio">P1</span>
        <div>
          <h4>新增各类辅助节点</h4>
          <p>提供中继、查找与消息暂存能力，缓解“双方必须同时在线”的限制。</p>
        </div>
      </li>
      <li>
        <span class="prio">P2</span>
        <div>
          <h4>完善 isle</h4>
          <p>增加点对点文件传输，逐步补齐通知、记录、连接管理等细节。</p>
        </div>
      </li>
      <li>
        <span class="prio">P3</span>
        <div>
          <h4>重新设计 isle</h4>
          <p>吸收原型阶段的经验，可能按不同平台分别重新实现。</p>
        </div>
      </li>
    </ol>
  </div>
</section>

<section id="connect" class="section section-connect">
  <div class="container narrow">
    <h2>聊聊？</h2>
    <p>
      这是个验证想法的原型项目，我很想知道你的看法：
      用起来感受如何、碰到了什么问题、或者你觉得“只要有网络就能通信”这件事应该是什么样。
    </p>
    <div class="connect-grid">
      <a class="connect-card" href="mailto:cliff@clifftop.win">
        <span class="connect-label">邮箱</span>
        <span class="connect-value">cliff@clifftop.win</span>
        <span class="connect-desc">任何问题和建议，直接写信。</span>
      </a>
      <a class="connect-card" href="https://github.com/CliffHan/direct-chat-release" target="_blank" rel="noopener">
        <span class="connect-label">GitHub</span>
        <span class="connect-value">CliffHan/direct-chat-release</span>
        <span class="connect-desc">源码、发布历史与问题反馈。</span>
      </a>
    </div>
    <p class="connect-note">
      项目暂时没有开源计划，但这不妨碍交流——欢迎一切意见和建议。
      更多常见问题见 <a href="{{ '/faq/' | relative_url }}">FAQ</a>。
    </p>
  </div>
</section>
