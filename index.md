---
layout: default
lang: zh-CN
lang_alt: /en/
title: direct-chat/isle · 不依赖服务器的点对点即时通信
description: direct-chat：消息直接在设备之间传递，没有服务器、没有账号，只要两台设备都在线，就能互相联系。
---

<section class="hero">
  <div class="container">
    <p class="eyebrow">点对点即时通信</p>
    <h1 class="title">direct-chat<span class="title-app">/isle</span></h1>
    <p class="lede">
      消息直接在两台设备之间传递。
      <em>没有服务器，没有账号</em>——只要两台设备都在线，就能互相联系。
    </p>
    <div class="meta">
      <span class="status">
        <span class="dot"></span>
        当前客户端：<code>isle</code>
      </span>
      <span class="status">
        <span class="dot dot-dim"></span>
        Windows · macOS · Android
      </span>
    </div>
    <ul class="dl-list">
      <li class="dl-item">
        <div class="dl-info">
          <span class="dl-name">Android<span class="dl-tag">原生版</span></span>
          <p class="dl-desc">
            针对 Android 本身开发，后台保活、通知与系统电话界面适配更好，手机与平板界面均已适配。
          </p>
        </div>
        <div class="dl-actions">
          <a class="btn btn-primary" href="{{ site.download_android }}">
            下载 APK
            <span class="btn-note">v{{ site.native_version }} · 免费版</span>
          </a>
          {%- for store in site.app_stores %}
          <a class="btn btn-ghost" href="{{ store.url }}" target="_blank" rel="noopener">
            {{ store.name }}
            {%- if store.note_zh %}
            <span class="btn-note">{{ store.note_zh }}</span>
            {%- endif %}
          </a>
          {%- endfor %}
        </div>
      </li>
      <li class="dl-item">
        <div class="dl-info">
          <span class="dl-name">桌面版<span class="dl-tag">Windows x64 · macOS universal</span></span>
          <p class="dl-desc">
            消息、语音与视频通话都已可用。macOS 版未经 Apple 公证，首次打开需要手动放行；我没有 macOS 设备，这一版尚未经过实际验证。详见<a href="{{ '/faq/' | relative_url }}">常见问题</a>。
          </p>
        </div>
        <div class="dl-actions">
          <a class="btn btn-primary" href="{{ site.download_windows }}">
            下载 Windows 版
            <span class="btn-note">v{{ site.desktop_version }} · x64 · exe</span>
          </a>
          <a class="btn btn-ghost" href="{{ site.download_macos }}">
            下载 macOS 版
            <span class="btn-note">v{{ site.desktop_version }} · universal · zip</span>
          </a>
        </div>
      </li>
    </ul>
    <p class="dl-hint">
      历史发布见 <a href="{{ site.releases_url }}" target="_blank" rel="noopener">GitHub Releases</a>。
    </p>
    <p class="hero-notice">
      <strong>免责声明：</strong>本软件为技术研究与教学示例，不提供平台服务，使用者自行承担全部风险。<a href="#disclaimer">详见免责声明 →</a>
    </p>
  </div>
</section>

<section id="disclaimer" class="section section-alt">
  <div class="container narrow">
    <h2>免责声明</h2>
    <p class="callout">
      使用 direct-chat 系列软件（含 <code>isle</code> 客户端）前，请仔细阅读以下条款。下载、安装或使用本软件即视为你已阅读并接受本声明全部内容。
    </p>

    <h3>产品性质</h3>
    <p>
      direct-chat 是个人开发的<strong>技术研究与教学示例</strong>项目，并非正式发布的商业产品。软件仍处于早期开发阶段，功能与稳定性未经大规模验证，可能存在已知或未知的缺陷。
    </p>

    <h3>无平台、无数据控制力</h3>
    <p>
      本项目不提供、不运营任何中央平台服务。所有通信数据仅在用户自己的设备上产生、传输和存储，项目方不持有、不存储、不控制任何用户数据。这意味着：
    </p>
    <ul>
      <li>项目方无法访问、查看或管理你的通信内容；</li>
      <li>项目方无法协助恢复丢失的数据或重置身份；</li>
      <li>项目方无法对通信的可达性和可靠性做出保证。</li>
    </ul>

    <h3>禁止非法用途</h3>
    <p>
      用户不得将本软件用于任何违反适用法律法规的用途，包括但不限于侵犯他人隐私、传播违法信息、危害网络安全、从事欺诈或其他违法犯罪活动。用户应确保自身使用行为合法合规，并遵守所在地区的相关法律。
    </p>

    <h3>用户自担风险</h3>
    <p>
      本软件按"现状"提供，不提供任何明示或暗示的担保，包括但不限于对适销性、特定用途适用性和不侵权的担保。用户需自行承担使用本软件的全部风险及后果，项目方不对因使用或无法使用本软件而导致的任何直接或间接损失承担责任。
    </p>

    <h3>其他</h3>
    <ul>
      <li>项目方保留随时修改、暂停或终止软件提供或更新部分或全部功能的权利，且不另行通知。</li>
      <li>本声明可能不时更新，以发布时网站展示的版本为准。</li>
      <li>如有任何疑问，请通过<a href="#connect">联系方式</a>与项目方沟通。</li>
    </ul>
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
    <h2>direct-chat/isle 目前能做什么</h2>
    <p>
      <strong>direct-chat</strong> 是项目名称，<strong>isle</strong> 是它的客户端——你下载安装的就是它，各个版本都以这个名字发布。
      以下是 isle 当前已实现的能力（桌面版与 Android 原生版的能力一致，区别见<a href="{{ '/faq/' | relative_url }}">FAQ</a>）：
    </p>
    <ul class="feature-list">
      <li>
        <span class="bullet"></span>
        <div><strong>设备与身份管理</strong> — 创建 p2p 网络节点，生成设备唯一标识，可创建或共享身份。</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>地址簿</strong> — 局域网内自动发现、扫二维码或手动输入设备标识来添加联系人，公开信息交换后保存在本地。</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>消息</strong> — 节点直连收发 plaintext / markdown 消息。</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>通话</strong> — 节点直连进行 WebRTC 音频 / 视频通话。</div>
      </li>
      <li>
        <span class="bullet"></span>
        <div><strong>备份与迁移</strong> — 导出加密备份，重装或换机时导入即可恢复。</div>
      </li>
    </ul>
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
          <p>Windows x64、macOS 或 Android，跟随向导完成初始化：设置网络、设备信息，身份可选。</p>
        </div>
      </li>
      <li>
        <span class="step-num">2</span>
        <div>
          <h4>添加联系人</h4>
          <p>局域网内自动查找对方设备，或扫对方的二维码添加，也可以手动输入设备唯一标识（带外交换，例如当面或用其他渠道告知）。</p>
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

    <figure class="demo">
      <iframe src="https://www.youtube-nocookie.com/embed/2QF7xbiXzbg"
              title="isle 桌面版与 Android 版演示"
              loading="lazy"
              allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
              referrerpolicy="strict-origin-when-cross-origin"
              allowfullscreen></iframe>
      <figcaption>
        桌面版 ↔ Android 互通 · 约 2 分钟：初始化并建立身份、交换设备标识添加联系人，以及桌面端与手机之间的语音 / 视频通话。
        如无法观看，可<a href="{{ '/assets/Isle_Demo_v0.2.2_desktop-android.mp4' | relative_url }}" download>直接下载视频</a>（约 15 MB）。
      </figcaption>
    </figure>

    <figure class="demo">
      <iframe src="https://www.youtube-nocookie.com/embed/fVOADGt6zVE"
              title="isle Android 版互通演示"
              loading="lazy"
              allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
              referrerpolicy="strict-origin-when-cross-origin"
              allowfullscreen></iframe>
      <figcaption>
        Android ↔ Android 互通 · 约 3 分钟：网络与权限设置、局域网内互相发现设备、发起通话，以及支持 markdown / mermaid 渲染的聊天会话。
        如无法观看，可<a href="{{ '/assets/Isle_Demo_v0.2.1_android-android.mp4' | relative_url }}" download>直接下载视频</a>（约 11 MB）。
      </figcaption>
    </figure>
  </div>
</section>

<section id="limits" class="section section-alt">
  <div class="container narrow">
    <h2>已知限制</h2>
    <p class="callout">
      以下限制客观存在，部分可能不会解决。
    </p>

    <h3>数据兼容性</h3>
    <p>
      版本升级后，无法保证旧数据必定可用。版本号前两位的变化基本意味着数据格式不兼容；仅第三位变化一般不影响数据。
    </p>

    <h3>平台与界面</h3>
    <p>
      桌面版提供 Windows x64 与 macOS（universal，Intel 与 Apple Silicon 通用）两个构建，界面按桌面窗口设计；
      Android 由单独的原生版提供，手机与平板界面均已适配。Linux 暂不提供。
      macOS 版未经 Apple 公证，首次打开需要手动放行，且尚未经过实际验证，详见 <a href="{{ '/faq/' | relative_url }}">FAQ</a>。
    </p>

    <h3>功能缺口</h3>
    <ul>
      <li>文件、图片、语音等多媒体传输暂不提供——这部分要等 iroh-blobs 完善之后再做。</li>
      <li>意外断线后的自动重连尚未实现。</li>
    </ul>

    <h3>双方须同时在线</h3>
    <p>
      没有服务器暂存消息：一方离线，另一方就无法送达。
      桌面版把窗口收进托盘就会继续在线，彻底退出应用则不再接收。
      Android 原生版以后台服务保持在线，应用内会提醒你开启所需权限；权限给全后，正常情况下切到后台也不影响接收。
      但个别厂商 ROM（如 MIUI）在特定情况下仍会杀掉应用，这一点无法保证。更多说明见 <a href="{{ '/faq/' | relative_url }}">FAQ</a>。
    </p>
  </div>
</section>

<section id="roadmap" class="section">
  <div class="container narrow">
    <h2>接下来做什么</h2>
    <p class="section-sub">
      接下来主要做这几件事。
    </p>
    <ol class="roadmap">
      <li>
        <span class="prio">P1</span>
        <div>
          <h4>辅助节点开发与整合</h4>
          <p>开发中继、查找与消息暂存等辅助节点，并整合进现有客户端，缓解“双方必须同时在线”的限制。</p>
        </div>
      </li>
      <li>
        <span class="prio">P2</span>
        <div>
          <h4>文件传输与稳定性</h4>
          <p>增加点对点文件传输（要等 iroh-blobs 完善），并补上意外断线后的自动重连等稳定性细节。</p>
        </div>
      </li>
      <li>
        <span class="prio">P3</span>
        <div>
          <h4>移植到更多平台</h4>
          <p>
            让 isle 跑在更多形态的设备上。可能的方向包括 Android TV（更大的屏幕与遥控器交互），
            以及命令行版本（思路尚未确定）。排在上面两项之后，具体时间未定。
          </p>
        </div>
      </li>
    </ol>
  </div>
</section>

<section id="connect" class="section section-connect">
  <div class="container narrow">
    <h2>聊聊？</h2>
    <p>
      这是个验证想法的个人项目，我很想知道你的看法：
      用起来感受如何、碰到了什么问题、或者你觉得“只要有网络就能通信”这件事应该是什么样。
    </p>
    <p>
      另外想找同路人：isle 并不局限于桌面和手机。只要设备能提供 WebRTC 与网络连接，理论上都可以移植过去——
      各种 Linux 开发板、电视盒子、车机都在这个范围内。这类移植会针对具体设备单独做界面，不受现有桌面界面的限制。
      如果你手上正好有这样的设备或场景，或者想一起把它跑通，欢迎来信，合作方式可以聊。
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
        <span class="connect-desc">发布历史、更新说明与问题反馈。</span>
      </a>
    </div>
    <p class="connect-note">
      项目暂时没有开源计划，但这不妨碍交流——欢迎一切意见和建议。
      更多常见问题见 <a href="{{ '/faq/' | relative_url }}">FAQ</a>。
    </p>
  </div>
</section>
