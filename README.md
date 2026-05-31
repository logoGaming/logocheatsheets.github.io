<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Logo's Java Plugin Cheat Sheet</title>
<style>
  :root {
    --bg: #0f1117; --bg2: #1a1d27; --bg3: #22263a;
    --border: #2e3250; --accent: #7c6aff; --accent2: #00d4a0;
    --text: #e8e8f0; --muted: #8888aa;
    --code-bg: #141720; --tag-bg: #2a2060; --tag-text: #a99fff;
    --sidebar-w: 250px;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: 'Segoe UI', system-ui, sans-serif; background: var(--bg); color: var(--text); display: flex; min-height: 100vh; }

  /* Sidebar */
  #sidebar { width: var(--sidebar-w); min-width: var(--sidebar-w); background: var(--bg2); border-right: 1px solid var(--border); position: fixed; top: 0; left: 0; height: 100vh; overflow-y: auto; display: flex; flex-direction: column; }
  #sidebar-header { padding: 20px 16px 12px; border-bottom: 1px solid var(--border); }
  #sidebar-header h1 { font-size: 14px; font-weight: 700; color: var(--accent); letter-spacing: 0.5px; }
  #sidebar-header p { font-size: 11px; color: var(--muted); margin-top: 4px; }
  #sidebar nav { padding: 8px 0; flex: 1; }
  .nav-item { display: flex; align-items: center; gap: 8px; padding: 7px 16px; font-size: 12.5px; color: var(--muted); cursor: pointer; border-left: 2px solid transparent; transition: all 0.15s; text-decoration: none; }
  .nav-item:hover { color: var(--text); background: var(--bg3); }
  .nav-item.active { color: var(--accent); border-left-color: var(--accent); background: #1c1840; }
  .nav-icon { font-size: 13px; width: 16px; text-align: center; }

  /* Main */
  #main { margin-left: var(--sidebar-w); flex: 1; padding: 40px 48px; max-width: 980px; }

  /* Search */
  #search-wrap { margin-bottom: 32px; position: relative; }
  #search { width: 100%; background: var(--bg2); border: 1px solid var(--border); color: var(--text); border-radius: 8px; padding: 10px 16px 10px 40px; font-size: 14px; outline: none; }
  #search:focus { border-color: var(--accent); }
  #search-wrap::before { content: '⌕'; position: absolute; left: 14px; top: 50%; transform: translateY(-50%); color: var(--muted); font-size: 18px; pointer-events: none; }

  /* Sections */
  .section { margin-bottom: 56px; scroll-margin-top: 24px; }
  .section-title { font-size: 22px; font-weight: 700; color: var(--text); border-bottom: 1px solid var(--border); padding-bottom: 12px; margin-bottom: 24px; display: flex; align-items: center; gap: 10px; }
  .section-title .badge { font-size: 11px; background: var(--tag-bg); color: var(--tag-text); border-radius: 4px; padding: 2px 8px; font-weight: 600; letter-spacing: 0.4px; }

  /* Cards */
  .card { background: var(--bg2); border: 1px solid var(--border); border-radius: 10px; margin-bottom: 16px; overflow: hidden; }
  .card-header { padding: 14px 18px; display: flex; align-items: flex-start; justify-content: space-between; cursor: pointer; gap: 12px; }
  .card-header:hover { background: var(--bg3); }
  .card-label { font-size: 14px; font-weight: 600; color: var(--text); }
  .card-desc { font-size: 13px; color: var(--muted); margin-top: 4px; line-height: 1.5; }
  .card-toggle { color: var(--muted); font-size: 18px; line-height: 1; flex-shrink: 0; padding-top: 2px; transition: transform 0.2s; }
  .card.open .card-toggle { transform: rotate(45deg); }
  .card-body { display: none; border-top: 1px solid var(--border); }
  .card.open .card-body { display: block; }

  /* Code */
  .code-wrap { position: relative; }
  pre { background: var(--code-bg); padding: 16px 18px; margin: 0; font-family: 'Cascadia Code','Fira Code','Consolas',monospace; font-size: 12.5px; line-height: 1.7; overflow-x: auto; color: #c9d1d9; border-top: 1px solid var(--border); }
  .copy-btn { position: absolute; top: 8px; right: 8px; background: var(--bg3); border: 1px solid var(--border); color: var(--muted); border-radius: 5px; padding: 4px 10px; font-size: 11px; cursor: pointer; opacity: 0; transition: opacity 0.15s; }
  .code-wrap:hover .copy-btn { opacity: 1; }
  .copy-btn:hover { color: var(--text); }
  .copy-btn.copied { color: var(--accent2); border-color: var(--accent2); }

  /* Syntax */
  .kw { color: #ff79c6; } .cm { color: #6272a4; font-style: italic; }
  .st { color: #f1fa8c; } .nm { color: #bd93f9; }
  .fn { color: #50fa7b; } .cn { color: #8be9fd; }
  .an { color: #ffb86c; } .op { color: #ff79c6; }

  /* Table */
  .tbl-wrap { padding: 0 0 4px; overflow-x: auto; }
  table { width: 100%; border-collapse: collapse; font-size: 12.5px; }
  table td, table th { padding: 7px 12px; border: 1px solid var(--border); vertical-align: top; }
  table th { background: var(--bg3); color: var(--muted); font-weight: 600; font-size: 11.5px; text-align: left; }
  table td:first-child { font-family: 'Cascadia Code','Fira Code','Consolas',monospace; color: #8be9fd; white-space: nowrap; }
  table.plain td:first-child { font-family: inherit; color: var(--text); white-space: normal; }
  table.plain td:last-child { color: var(--muted); }
  table.color-chart td { font-family: 'Cascadia Code','Fira Code','Consolas',monospace; font-size: 12px; }

  /* Note */
  .note { background: #1a2040; border-left: 3px solid var(--accent); padding: 10px 14px; font-size: 13px; color: var(--muted); margin: 12px 18px; border-radius: 0 6px 6px 0; line-height: 1.6; }
  .note strong { color: var(--text); }
  .warn { background: #261a00; border-left: 3px solid #ffb86c; padding: 10px 14px; font-size: 13px; color: #ccaa60; margin: 12px 18px; border-radius: 0 6px 6px 0; line-height: 1.6; }
  .warn strong { color: #ffcc66; }

  /* Slot grid */
  .slot-grid { display: grid; grid-template-columns: repeat(9,1fr); gap: 3px; padding: 16px 18px; }
  .slot { background: var(--bg3); border: 1px solid var(--border); border-radius: 4px; text-align: center; font-size: 11px; font-family: 'Cascadia Code','Fira Code','Consolas',monospace; padding: 5px 2px; color: var(--muted); }
  .slot.border-slot { background: #1e1a3a; color: var(--accent); border-color: var(--accent); }

  /* Color preview swatches */
  .color-swatch { display: inline-block; width: 12px; height: 12px; border-radius: 2px; margin-right: 4px; vertical-align: middle; }

  /* No results */
  #no-results { display: none; text-align: center; padding: 60px 20px; color: var(--muted); }
  #no-results h2 { font-size: 20px; margin-bottom: 8px; }

  @media (max-width: 700px) { #sidebar { display: none; } #main { margin-left: 0; padding: 24px 20px; } }
</style>
</head>
<body>

<aside id="sidebar">
  <div id="sidebar-header">
    <h1>☕ Logo's Cheat Sheet</h1>
    <p>PaperMC · Java 21 · Paper 1.21+</p>
  </div>
  <nav id="sidenav">
    <a class="nav-item" href="#imports"><span class="nav-icon">📦</span> Imports</a>
    <a class="nav-item" href="#core"><span class="nav-icon">⚙️</span> Core</a>
    <a class="nav-item" href="#events"><span class="nav-icon">🎯</span> Events</a>
    <a class="nav-item" href="#custom-items"><span class="nav-icon">🗡️</span> Custom Items</a>
    <a class="nav-item" href="#gui"><span class="nav-icon">🗂️</span> GUI</a>
    <a class="nav-item" href="#particles"><span class="nav-icon">✨</span> Particles</a>
    <a class="nav-item" href="#java-basics"><span class="nav-icon">📘</span> Java Basics</a>
    <a class="nav-item" href="#papermc-basics"><span class="nav-icon">🌍</span> PaperMC Basics</a>
    <a class="nav-item" href="#timers"><span class="nav-icon">⏱️</span> Timers</a>
    <a class="nav-item" href="#commands"><span class="nav-icon">💬</span> Commands</a>
    <a class="nav-item" href="#configs"><span class="nav-icon">💾</span> Configs / Data</a>
    <a class="nav-item" href="#pdc"><span class="nav-icon">🏷️</span> PDC</a>
    <a class="nav-item" href="#sqlite"><span class="nav-icon">🗄️</span> SQLite</a>
    <a class="nav-item" href="#tips"><span class="nav-icon">💡</span> Tips</a>
    <a class="nav-item" href="#sounds"><span class="nav-icon">🔊</span> Sounds</a>
    <a class="nav-item" href="#advanced"><span class="nav-icon">🚀</span> Advanced Patterns</a>
    <a class="nav-item" href="#plugin-structure"><span class="nav-icon">🏗️</span> Plugin Structure</a>
    <a class="nav-item" href="#quickref"><span class="nav-icon">📋</span> Quick Reference</a>
  </nav>
</aside>

<main id="main">
  <div id="search-wrap">
    <input id="search" type="text" placeholder="Search the cheat sheet…" autocomplete="off">
  </div>
  <div id="no-results"><h2>No results</h2><p>Try a different search term.</p></div>
  <div id="content">

<!-- ═══ IMPORTS ═══ -->
<section class="section" id="imports">
  <div class="section-title">📦 Imports <span class="badge">BASICS</span></div>
  <div class="card open">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Common Imports</div><div class="card-desc">Tell Java where to find classes — without these, Java won't know what EventHandler, Player, etc. are.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">import</span> org.bukkit.event.Listener;
<span class="kw">import</span> org.bukkit.event.EventHandler;
<span class="kw">import</span> org.bukkit.event.EventPriority;
<span class="kw">import</span> org.bukkit.plugin.java.JavaPlugin;
<span class="kw">import</span> org.bukkit.Bukkit;
<span class="kw">import</span> org.bukkit.entity.Player;
<span class="kw">import</span> org.bukkit.Material;
<span class="kw">import</span> org.bukkit.Location;
<span class="kw">import</span> org.bukkit.World;
<span class="kw">import</span> org.bukkit.inventory.Inventory;
<span class="kw">import</span> org.bukkit.inventory.ItemStack;
<span class="kw">import</span> org.bukkit.inventory.meta.ItemMeta;
<span class="kw">import</span> org.bukkit.Sound;
<span class="kw">import</span> org.bukkit.Particle;
<span class="kw">import</span> org.bukkit.scheduler.BukkitTask;
<span class="kw">import</span> org.bukkit.scheduler.BukkitRunnable;
<span class="kw">import</span> java.util.*;</pre></div></div>
  </div>
</section>

<!-- ═══ CORE ═══ -->
<section class="section" id="core">
  <div class="section-title">⚙️ Core <span class="badge">SETUP</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Register Events</div><div class="card-desc">Tells the server this class has event listeners. Without this, your @EventHandler methods never fire. Put this in onEnable().</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre>getServer().getPluginManager().registerEvents(<span class="kw">this</span>, <span class="kw">this</span>);

<span class="cm">// Or with a separate listener class (recommended):</span>
getServer().getPluginManager().registerEvents(<span class="kw">new</span> <span class="cn">MyListener</span>(<span class="kw">this</span>), <span class="kw">this</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Register a Command</div><div class="card-desc">Link a command string to its executor class. Put this in onEnable().</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">PluginCommand</span> cmd = getCommand(<span class="st">"starsmp"</span>);
<span class="kw">if</span> (cmd != <span class="kw">null</span>) {
    <span class="cn">StarSMPCommand</span> executor = <span class="kw">new</span> <span class="cn">StarSMPCommand</span>(<span class="kw">this</span>);
    cmd.setExecutor(executor);
    cmd.setTabCompleter(executor); <span class="cm">// same class can handle tab complete</span>
}</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Access Plugin From Another Class</div><div class="card-desc">Gets a reference to your main plugin instance from anywhere in your code.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Option 1 — cast from Bukkit (works from anywhere)</span>
<span class="cn">SMPEssentials</span> plugin = (<span class="cn">SMPEssentials</span>) <span class="cn">Bukkit</span>.getPluginManager().getPlugin(<span class="st">"SMPEssentials"</span>);

<span class="cm">// Option 2 — singleton pattern (recommended)</span>
<span class="kw">public class</span> <span class="cn">SMPEssentials</span> <span class="kw">extends</span> <span class="cn">JavaPlugin</span> {
    <span class="kw">private static</span> <span class="cn">SMPEssentials</span> instance;
    <span class="an">@Override</span> <span class="kw">public void</span> <span class="fn">onEnable</span>() { instance = <span class="kw">this</span>; }
    <span class="kw">public static</span> <span class="cn">SMPEssentials</span> <span class="fn">getInstance</span>() { <span class="kw">return</span> instance; }
}
<span class="cm">// Then anywhere:</span>
<span class="cn">SMPEssentials</span>.getInstance().someMethod();</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Broadcast & Loop All Players</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Broadcast to everyone at once</span>
<span class="cn">Bukkit</span>.broadcastMessage(<span class="st">"§aHello everyone!"</span>);

<span class="cm">// Loop through all online players</span>
<span class="kw">for</span> (<span class="cn">Player</span> player : <span class="cn">Bukkit</span>.getOnlinePlayers()) {
    <span class="kw">if</span> (player.getName().equals(<span class="st">"Steve"</span>)) {
        player.sendMessage(<span class="st">"Found you!"</span>);
    }
}

<span class="cm">// With Java Streams (cleaner filtering)</span>
<span class="cn">Bukkit</span>.getOnlinePlayers().stream()
    .filter(p -> p.hasPermission(<span class="st">"admin"</span>))
    .forEach(p -> p.sendMessage(<span class="st">"§cAdmin alert!"</span>));</pre></div></div>
  </div>
</section>

<!-- ═══ EVENTS ═══ -->
<section class="section" id="events">
  <div class="section-title">🎯 Events <span class="badge">LISTENERS</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Listener Class Setup</div><div class="card-desc">The full pattern for a listener class. Register it in onEnable().</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">public class</span> <span class="cn">MyListener</span> <span class="kw">implements</span> <span class="cn">Listener</span> {
    <span class="kw">private final</span> <span class="cn">MyPlugin</span> plugin;
    <span class="kw">public</span> <span class="fn">MyListener</span>(<span class="cn">MyPlugin</span> plugin) { <span class="kw">this</span>.plugin = plugin; }

    <span class="an">@EventHandler</span>
    <span class="kw">public void</span> <span class="fn">onPlayerJoin</span>(<span class="cn">PlayerJoinEvent</span> event) {
        <span class="cn">Player</span> player = event.getPlayer();
        event.setJoinMessage(<span class="st">"§a» §f"</span> + player.getName() + <span class="st">" §ajoined!"</span>);
        player.sendMessage(<span class="st">"§aWelcome to the server!"</span>);
    }

    <span class="an">@EventHandler</span>(priority = <span class="cn">EventPriority</span>.HIGH, ignoreCancelled = <span class="kw">true</span>)
    <span class="kw">public void</span> <span class="fn">onBlockBreak</span>(<span class="cn">BlockBreakEvent</span> event) {
        <span class="cm">// ignoreCancelled = skip if another plugin cancelled it first</span>
    }
}</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Item Right-Click Detection</div><div class="card-desc">Always null-check getItem() — empty hand returns null and will crash without it.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="an">@EventHandler</span>
<span class="kw">public void</span> <span class="fn">onRightClick</span>(<span class="cn">PlayerInteractEvent</span> event) {
    <span class="kw">if</span> (event.getAction() == <span class="cn">Action</span>.RIGHT_CLICK_BLOCK ||
        event.getAction() == <span class="cn">Action</span>.RIGHT_CLICK_AIR) {
        <span class="kw">if</span> (event.getItem() != <span class="kw">null</span> &&
            event.getItem().getType() == <span class="cn">Material</span>.DIAMOND_SWORD) {
            event.getPlayer().sendMessage(<span class="st">"You right-clicked with a Diamond Sword!"</span>);
        }
    }
}</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Block Right-Click Detection</div><div class="card-desc">Check getClickedBlock() instead of item. Null check required — clicking in air has no clicked block.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="an">@EventHandler</span>
<span class="kw">public void</span> <span class="fn">onRightClick</span>(<span class="cn">PlayerInteractEvent</span> event) {
    <span class="kw">if</span> (event.getAction() == <span class="cn">Action</span>.RIGHT_CLICK_BLOCK) {
        <span class="kw">if</span> (event.getClickedBlock() != <span class="kw">null</span>) {
            event.getPlayer().sendMessage(<span class="st">"Block: "</span> +
                event.getClickedBlock().getType().toString());
        }
    }
}</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Events Quick Reference — 25+ Common Events</div><div class="card-desc">All the events you'll use most often, with their most useful methods.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table class="plain" style="font-size:12px;">
          <tr><th>Event Class</th><th>When it fires</th><th>Key Methods</th></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerJoinEvent</td><td>Player connects</td><td>getPlayer(), setJoinMessage()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerQuitEvent</td><td>Player disconnects</td><td>getPlayer(), setQuitMessage()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerMoveEvent</td><td>Player moves (every tick!)</td><td>getFrom(), getTo(), setTo(loc)</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerTeleportEvent</td><td>Player teleports</td><td>getFrom(), getTo(), getCause()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerInteractEvent</td><td>Click / interact</td><td>getAction(), getItem(), getClickedBlock()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerInteractEntityEvent</td><td>Right-click on entity</td><td>getPlayer(), getRightClicked()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerDeathEvent</td><td>Player dies</td><td>getEntity(), setDeathMessage(), getDrops()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerRespawnEvent</td><td>Player respawns</td><td>getPlayer(), setRespawnLocation()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">EntityDeathEvent</td><td>Any entity dies</td><td>getEntity(), getEntity().getKiller(), getDrops()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">EntityDamageEvent</td><td>Entity takes damage</td><td>getDamage(), setDamage(), getCause()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">EntityDamageByEntityEvent</td><td>Damaged by an entity</td><td>getDamager(), getEntity(), getFinalDamage()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">EntitySpawnEvent</td><td>Entity spawns</td><td>getEntity(), getLocation(), setCancelled()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">AsyncPlayerChatEvent</td><td>Chat message (async!)</td><td>getPlayer(), getMessage(), setMessage()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerCommandPreprocessEvent</td><td>Types a command</td><td>getPlayer(), getMessage(), setMessage()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">InventoryClickEvent</td><td>Click in any inventory</td><td>getClickedInventory(), getCurrentItem(), getSlot(), getClick()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">InventoryDragEvent</td><td>Drag items across slots</td><td>getNewItems(), getInventory(), setCancelled()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">InventoryCloseEvent</td><td>Inventory closed</td><td>getPlayer(), getInventory()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">BlockBreakEvent</td><td>Block broken by player</td><td>getPlayer(), getBlock(), setDropItems()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">BlockPlaceEvent</td><td>Block placed by player</td><td>getPlayer(), getBlock(), getItemInHand()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">ProjectileLaunchEvent</td><td>Projectile fired</td><td>getEntity(), setCancelled()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">ProjectileHitEvent</td><td>Projectile lands</td><td>getEntity(), getHitEntity(), getHitBlock()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerDropItemEvent</td><td>Player drops item (Q)</td><td>getPlayer(), getItemDrop()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerPickupItemEvent</td><td>Player picks up item</td><td>getPlayer(), getItem(), setCancelled()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">CreatureSpawnEvent</td><td>Mob spawns naturally</td><td>getEntity(), getSpawnReason(), setCancelled()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">FoodLevelChangeEvent</td><td>Hunger changes</td><td>getEntity(), getFoodLevel(), setFoodLevel()</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;">PlayerFishEvent</td><td>Fishing action</td><td>getPlayer(), getCaught(), getState()</td></tr>
        </table>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Event Priority & Cancellation</div><div class="card-desc">Controls the order your handler runs relative to other plugins. MONITOR is for observation only — never modify the event there.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Priority order — LOWEST runs first, MONITOR runs last</span>
<span class="an">@EventHandler</span>(priority = <span class="cn">EventPriority</span>.LOWEST)   <span class="cm">// first — great for setup</span>
<span class="an">@EventHandler</span>(priority = <span class="cn">EventPriority</span>.LOW)
<span class="an">@EventHandler</span>(priority = <span class="cn">EventPriority</span>.NORMAL)   <span class="cm">// default</span>
<span class="an">@EventHandler</span>(priority = <span class="cn">EventPriority</span>.HIGH)
<span class="an">@EventHandler</span>(priority = <span class="cn">EventPriority</span>.HIGHEST)
<span class="an">@EventHandler</span>(priority = <span class="cn">EventPriority</span>.MONITOR)  <span class="cm">// last, observation ONLY</span>

<span class="cm">// ignoreCancelled — skip if another plugin already cancelled it</span>
<span class="an">@EventHandler</span>(priority = <span class="cn">EventPriority</span>.NORMAL, ignoreCancelled = <span class="kw">true</span>)
<span class="kw">public void</span> <span class="fn">onBreak</span>(<span class="cn">BlockBreakEvent</span> event) { }

<span class="cm">// Cancelling an event — stops the action from happening</span>
event.setCancelled(<span class="kw">true</span>);
<span class="kw">if</span> (event.isCancelled()) <span class="kw">return</span>;</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Critical Null Checks by Event</div><div class="card-desc">The most common crash causes in plugin dev. Always add these guards at the top of your handlers.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table class="plain" style="font-size:12px;">
          <tr><th>Situation</th><th>Guard Code</th></tr>
          <tr><td>GUI border click</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">if (event.getClickedInventory() == null) return;</td></tr>
          <tr><td>Empty slot clicked</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">if (event.getCurrentItem() == null) return;</td></tr>
          <tr><td>Item has no meta</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">ItemMeta m = item.getItemMeta(); if (m == null) return;</td></tr>
          <tr><td>No player killer (env death)</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">Player k = event.getEntity().getKiller(); if (k == null) return;</td></tr>
          <tr><td>Clicked air, not a block</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">if (event.getClickedBlock() == null) return;</td></tr>
          <tr><td>Empty hand</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">if (event.getItem() == null) return;</td></tr>
          <tr><td>Pressure plate step</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">if (event.getAction() == Action.PHYSICAL) return;</td></tr>
          <tr><td>Projectile not from player</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">if (!(event.getEntity().getShooter() instanceof Player)) return;</td></tr>
          <tr><td>World not found</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">World w = Bukkit.getWorld("name"); if (w == null) return;</td></tr>
          <tr><td>Wrong inventory holder</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">if (!(inv.getHolder() instanceof MyHolder)) return;</td></tr>
        </table>
      </div>
    </div>
  </div>
</section>

<!-- ═══ CUSTOM ITEMS ═══ -->
<section class="section" id="custom-items">
  <div class="section-title">🗡️ Custom Items <span class="badge">ITEMS</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Creating an Item</div><div class="card-desc">ItemStack = the item. ItemMeta = extra info (name, lore, enchants etc.). Always call setItemMeta() at the end or your changes won't save.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">ItemStack</span> starMenu = <span class="kw">new</span> <span class="cn">ItemStack</span>(<span class="cn">Material</span>.NETHER_STAR);
<span class="cn">ItemMeta</span> meta = starMenu.getItemMeta();
meta.setDisplayName(<span class="st">"§f§lStar Chooser"</span>);
meta.setLore(<span class="cn">Arrays</span>.asList(
    <span class="st">"§7A legendary relic"</span>,
    <span class="st">"§eRight-click to open menu"</span>,
    <span class="st">""</span>,
    <span class="st">"§8Bound to Steve"</span>
));
meta.addEnchant(<span class="cn">Enchantment</span>.DAMAGE_ALL, <span class="nm">5</span>, <span class="kw">true</span>); <span class="cm">// true = ignore level cap</span>
meta.setUnbreakable(<span class="kw">true</span>);
meta.addItemFlags(<span class="cn">ItemFlag</span>.HIDE_ENCHANTS);        <span class="cm">// hide enchant lines</span>
meta.addItemFlags(<span class="cn">ItemFlag</span>.HIDE_UNBREAKABLE);     <span class="cm">// hide unbreakable tag</span>
meta.addItemFlags(<span class="cn">ItemFlag</span>.HIDE_ATTRIBUTES);      <span class="cm">// hide attack speed/damage</span>
meta.setCustomModelData(<span class="nm">1001</span>);                    <span class="cm">// custom resource pack model</span>
starMenu.setItemMeta(meta);                        <span class="cm">// ✦ MUST apply back or all changes lost!</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Giving an Item + Checking Items</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Give to player (drops on ground if inventory is full)</span>
player.getInventory().addItem(starMenu);

<span class="cm">// Set a specific slot</span>
player.getInventory().setItem(<span class="nm">9</span>, starMenu);

<span class="cm">// Check item type</span>
<span class="kw">if</span> (item.getType() == <span class="cn">Material</span>.DIAMOND_SWORD) { }

<span class="cm">// Check display name (always null-check meta first!)</span>
<span class="kw">if</span> (item.hasItemMeta() && item.getItemMeta().hasDisplayName()) {
    <span class="cn">String</span> name = item.getItemMeta().getDisplayName();
}

<span class="cm">// Stack size</span>
item.getAmount();     <span class="cm">// how many in the stack</span>
item.setAmount(<span class="nm">32</span>);  <span class="cm">// change stack size</span>
item.isSimilar(other); <span class="cm">// compare ignoring amount</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Specialized Meta Types</div><div class="card-desc">Cast to the right meta type for skulls, leather armor, potions, and maps.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Skull — set player head owner</span>
<span class="cn">SkullMeta</span> sm = (<span class="cn">SkullMeta</span>) skull.getItemMeta();
sm.setOwningPlayer(<span class="cn">Bukkit</span>.getOfflinePlayer(<span class="st">"Username"</span>));

<span class="cm">// Leather armor — custom color</span>
<span class="cn">LeatherArmorMeta</span> lam = (<span class="cn">LeatherArmorMeta</span>) chestplate.getItemMeta();
lam.setColor(<span class="cn">Color</span>.fromRGB(<span class="nm">255</span>, <span class="nm">0</span>, <span class="nm">128</span>));  <span class="cm">// hot pink</span>

<span class="cm">// Potion — custom effects</span>
<span class="cn">PotionMeta</span> pm = (<span class="cn">PotionMeta</span>) potion.getItemMeta();
pm.setBasePotionData(<span class="kw">new</span> <span class="cn">PotionData</span>(<span class="cn">PotionType</span>.SPEED, <span class="kw">false</span>, <span class="kw">true</span>));
pm.addCustomEffect(<span class="kw">new</span> <span class="cn">PotionEffect</span>(<span class="cn">PotionEffectType</span>.JUMP, <span class="nm">400</span>, <span class="nm">2</span>), <span class="kw">true</span>);

<span class="cm">// Always apply the meta back!</span>
skull.setItemMeta(sm);
chestplate.setItemMeta(lam);
potion.setItemMeta(pm);</pre></div></div>
  </div>
</section>

<!-- ═══ GUI ═══ -->
<section class="section" id="gui">
  <div class="section-title">🗂️ GUI <span class="badge">INVENTORY UI</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Creating a GUI</div><div class="card-desc">Sizes must be multiples of 9 (9, 18, 27, 36, 45, 54). Slots go left to right, top to bottom from 0.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">private final</span> <span class="cn">String</span> GUI_TITLE = <span class="st">"§6§lMy Shop"</span>;
<span class="kw">private</span> <span class="cn">Inventory</span> gui;

<span class="kw">private void</span> <span class="fn">createGUI</span>() {
    gui = <span class="cn">Bukkit</span>.createInventory(<span class="kw">null</span>, <span class="nm">27</span>, GUI_TITLE); <span class="cm">// 27 = 3 rows</span>

    <span class="cm">// Helper: make a button item</span>
    <span class="cn">ItemStack</span> btn = makeButton(<span class="cn">Material</span>.DIAMOND_SWORD, <span class="st">"§b§lBuy Sword"</span>,
        <span class="st">"§7A powerful weapon"</span>, <span class="st">"§ePrice: §a$500"</span>, <span class="st">"§8Click to purchase"</span>);
    gui.setItem(<span class="nm">13</span>, btn); <span class="cm">// center slot of row 2</span>

    <span class="cm">// Fill border with glass pane</span>
    <span class="cn">ItemStack</span> filler = makeButton(<span class="cn">Material</span>.GRAY_STAINED_GLASS_PANE, <span class="st">"§8"</span>);
    <span class="kw">int</span>[] border = {<span class="nm">0</span>,<span class="nm">1</span>,<span class="nm">2</span>,<span class="nm">3</span>,<span class="nm">4</span>,<span class="nm">5</span>,<span class="nm">6</span>,<span class="nm">7</span>,<span class="nm">8</span>,<span class="nm">18</span>,<span class="nm">19</span>,<span class="nm">20</span>,<span class="nm">21</span>,<span class="nm">22</span>,<span class="nm">23</span>,<span class="nm">24</span>,<span class="nm">25</span>,<span class="nm">26</span>};
    <span class="kw">for</span> (<span class="kw">int</span> slot : border) gui.setItem(slot, filler);
}

<span class="kw">private</span> <span class="cn">ItemStack</span> <span class="fn">makeButton</span>(<span class="cn">Material</span> mat, <span class="cn">String</span> name, <span class="cn">String</span>... lore) {
    <span class="cn">ItemStack</span> item = <span class="kw">new</span> <span class="cn">ItemStack</span>(mat);
    <span class="cn">ItemMeta</span> meta = item.getItemMeta();
    meta.setDisplayName(name);
    meta.setLore(<span class="cn">Arrays</span>.asList(lore));
    meta.addItemFlags(<span class="cn">ItemFlag</span>.HIDE_ATTRIBUTES);
    item.setItemMeta(meta);
    <span class="kw">return</span> item;
}

<span class="cm">// Open for a player</span>
<span class="kw">public void</span> <span class="fn">openGUI</span>(<span class="cn">Player</span> player) { player.openInventory(gui); }</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">InventoryHolder Pattern (Recommended)</div><div class="card-desc">A custom holder ties data to your GUI so you can identify it without comparing title strings.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Step 1 — Custom holder class</span>
<span class="kw">public class</span> <span class="cn">ShopHolder</span> <span class="kw">implements</span> <span class="cn">InventoryHolder</span> {
    <span class="kw">private final</span> <span class="cn">String</span> shopId;
    <span class="kw">private</span> <span class="cn">Inventory</span> inventory;
    <span class="kw">public</span> <span class="fn">ShopHolder</span>(<span class="cn">String</span> shopId) { <span class="kw">this</span>.shopId = shopId; }
    <span class="kw">public</span> <span class="cn">String</span> <span class="fn">getShopId</span>() { <span class="kw">return</span> shopId; }
    <span class="an">@Override</span> <span class="kw">public</span> <span class="cn">Inventory</span> <span class="fn">getInventory</span>() { <span class="kw">return</span> inventory; }
    <span class="kw">public void</span> <span class="fn">setInventory</span>(<span class="cn">Inventory</span> inv) { <span class="kw">this</span>.inventory = inv; }
}

<span class="cm">// Step 2 — Create GUI with holder</span>
<span class="cn">ShopHolder</span> holder = <span class="kw">new</span> <span class="cn">ShopHolder</span>(<span class="st">"weapons"</span>);
<span class="cn">Inventory</span> gui = <span class="cn">Bukkit</span>.createInventory(holder, <span class="nm">27</span>, <span class="st">"§6Weapon Shop"</span>);
holder.setInventory(gui);

<span class="cm">// Step 3 — Detect in click handler (type-safe, no title comparison!)</span>
<span class="kw">if</span> (!(event.getInventory().getHolder() <span class="kw">instanceof</span> <span class="cn">ShopHolder</span> shopHolder)) <span class="kw">return</span>;
<span class="cn">String</span> shopId = shopHolder.getShopId(); <span class="cm">// access custom data</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Click Event Handler</div><div class="card-desc">Always add both null checks at the top and always cancel the event to prevent item theft.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="an">@EventHandler</span>
<span class="kw">public void</span> <span class="fn">onInventoryClick</span>(<span class="cn">InventoryClickEvent</span> event) {
    <span class="kw">if</span> (event.getClickedInventory() == <span class="kw">null</span>) <span class="kw">return</span>; <span class="cm">// border click = null</span>
    <span class="kw">if</span> (event.getCurrentItem() == <span class="kw">null</span>) <span class="kw">return</span>;      <span class="cm">// empty slot</span>
    <span class="kw">if</span> (event.getCurrentItem().getType() == <span class="cn">Material</span>.AIR) <span class="kw">return</span>;

    <span class="kw">if</span> (!(event.getInventory().getHolder() <span class="kw">instanceof</span> <span class="cn">ShopHolder</span> holder)) <span class="kw">return</span>;

    event.setCancelled(<span class="kw">true</span>); <span class="cm">// ✦ ALWAYS cancel or players can steal items</span>

    <span class="cn">Player</span> player = (<span class="cn">Player</span>) event.getWhoClicked();
    <span class="kw">int</span> slot = event.getSlot();
    <span class="cn">ClickType</span> type = event.getClick();

    <span class="kw">if</span> (slot == <span class="nm">13</span> && type == <span class="cn">ClickType</span>.LEFT) {
        player.getInventory().addItem(<span class="kw">new</span> <span class="cn">ItemStack</span>(<span class="cn">Material</span>.DIAMOND_SWORD));
        player.sendMessage(<span class="st">"§aPurchased Sword!"</span>);
        player.playSound(player.getLocation(), <span class="cn">Sound</span>.ENTITY_PLAYER_LEVELUP, <span class="nm">1f</span>, <span class="nm">1f</span>);
    }
}

<span class="cm">// Also block shift-click from player inventory into GUI</span>
<span class="an">@EventHandler</span>
<span class="kw">public void</span> <span class="fn">onInventoryDrag</span>(<span class="cn">InventoryDragEvent</span> event) {
    <span class="kw">if</span> (event.getInventory().getHolder() <span class="kw">instanceof</span> <span class="cn">ShopHolder</span>) {
        event.setCancelled(<span class="kw">true</span>);
    }
}</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Click Types & Slot Chart</div><div class="card-desc">Reference for ClickType values and GUI slot numbering.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table style="font-size:12px;">
          <tr><th>ClickType</th><th>Triggered By</th><th>ClickType</th><th>Triggered By</th></tr>
          <tr><td>LEFT</td><td style="color:var(--muted)">Left click</td><td>SHIFT_LEFT</td><td style="color:var(--muted)">Shift + left click</td></tr>
          <tr><td>RIGHT</td><td style="color:var(--muted)">Right click</td><td>SHIFT_RIGHT</td><td style="color:var(--muted)">Shift + right click</td></tr>
          <tr><td>MIDDLE</td><td style="color:var(--muted)">Middle mouse</td><td>NUMBER_KEY</td><td style="color:var(--muted)">1–9 hotbar keys</td></tr>
          <tr><td>DROP</td><td style="color:var(--muted)">Q key</td><td>DOUBLE_CLICK</td><td style="color:var(--muted)">Double click</td></tr>
        </table>
      </div>
      <div style="padding:12px 18px 4px;"><div style="font-size:12px;color:var(--muted);margin-bottom:8px;">6-row chest = 54 slots (Row 1: 0–8, Row 2: 9–17, … Row 6: 45–53)</div></div>
      <div class="slot-grid">
        <div class="slot border-slot">0</div><div class="slot border-slot">1</div><div class="slot border-slot">2</div><div class="slot border-slot">3</div><div class="slot border-slot">4</div><div class="slot border-slot">5</div><div class="slot border-slot">6</div><div class="slot border-slot">7</div><div class="slot border-slot">8</div>
        <div class="slot">9</div><div class="slot">10</div><div class="slot">11</div><div class="slot">12</div><div class="slot" style="background:#1e2a1e;color:#50fa7b;border-color:#50fa7b;">13</div><div class="slot">14</div><div class="slot">15</div><div class="slot">16</div><div class="slot">17</div>
        <div class="slot">18</div><div class="slot">19</div><div class="slot">20</div><div class="slot">21</div><div class="slot">22</div><div class="slot">23</div><div class="slot">24</div><div class="slot">25</div><div class="slot">26</div>
        <div class="slot">27</div><div class="slot">28</div><div class="slot">29</div><div class="slot">30</div><div class="slot">31</div><div class="slot">32</div><div class="slot">33</div><div class="slot">34</div><div class="slot">35</div>
        <div class="slot">36</div><div class="slot">37</div><div class="slot">38</div><div class="slot">39</div><div class="slot">40</div><div class="slot">41</div><div class="slot">42</div><div class="slot">43</div><div class="slot">44</div>
        <div class="slot border-slot">45</div><div class="slot border-slot">46</div><div class="slot border-slot">47</div><div class="slot border-slot">48</div><div class="slot border-slot">49</div><div class="slot border-slot">50</div><div class="slot border-slot">51</div><div class="slot border-slot">52</div><div class="slot border-slot">53</div>
      </div>
      <div style="padding:4px 18px 14px;font-size:11px;color:var(--muted);">Center of 3-row: 13 | Center of 6-row: 22 & 31 | Blue = common border slots</div>
    </div>
  </div>
</section>

<!-- ═══ PARTICLES ═══ -->
<section class="section" id="particles">
  <div class="section-title">✨ Particles <span class="badge">VFX</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Basic Particle Spawning</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Simple burst at location</span>
world.spawnParticle(<span class="cn">Particle</span>.FLAME, location, <span class="nm">30</span>);

<span class="cm">// With spread: (particle, location, count, spreadX, spreadY, spreadZ, speed)</span>
world.spawnParticle(<span class="cn">Particle</span>.CRIT, location, <span class="nm">20</span>, <span class="nm">0.5</span>, <span class="nm">0.5</span>, <span class="nm">0.5</span>, <span class="nm">0.05</span>);

<span class="cm">// Directional (count=0, spread=direction, speed=force)</span>
world.spawnParticle(<span class="cn">Particle</span>.END_ROD, location, <span class="nm">0</span>, <span class="nm">0</span>, <span class="nm">0.1</span>, <span class="nm">0</span>, <span class="nm">0.05</span>);

<span class="cm">// Player-only (only that player sees it)</span>
player.spawnParticle(<span class="cn">Particle</span>.HEART, location, <span class="nm">5</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Colored Dust Particles</div><div class="card-desc">Custom RGB color and size. The DustTransition version transitions between two colors (1.17+).</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Colored dust: (Color, size: 0.1=tiny to 4.0=huge)</span>
<span class="cn">Particle</span>.DustOptions red    = <span class="kw">new</span> <span class="cn">Particle</span>.DustOptions(<span class="cn">Color</span>.RED, <span class="nm">1.5f</span>);
<span class="cn">Particle</span>.DustOptions orange = <span class="kw">new</span> <span class="cn">Particle</span>.DustOptions(<span class="cn">Color</span>.fromRGB(<span class="nm">255</span>,<span class="nm">140</span>,<span class="nm">0</span>), <span class="nm">1.0f</span>);
world.spawnParticle(<span class="cn">Particle</span>.REDSTONE, location, <span class="nm">1</span>, red);

<span class="cm">// Transitioning dust (1.17+) — fades from one color to another</span>
<span class="cn">Particle</span>.DustTransition trans = <span class="kw">new</span> <span class="cn">Particle</span>.DustTransition(<span class="cn">Color</span>.RED, <span class="cn">Color</span>.BLUE, <span class="nm">1.5f</span>);
world.spawnParticle(<span class="cn">Particle</span>.DUST_COLOR_TRANSITION, location, <span class="nm">1</span>, trans);

<span class="cm">// Block / item particles</span>
world.spawnParticle(<span class="cn">Particle</span>.BLOCK_CRACK, location, <span class="nm">30</span>,
    <span class="cn">Material</span>.DIAMOND_BLOCK.createBlockData());
world.spawnParticle(<span class="cn">Particle</span>.ITEM_CRACK, location, <span class="nm">20</span>,
    <span class="kw">new</span> <span class="cn">ItemStack</span>(<span class="cn">Material</span>.DIAMOND_SWORD));</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Common Particle Types</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table style="font-size:12px;">
          <tr><th>Particle</th><th>Looks Like</th><th>Particle</th><th>Looks Like</th></tr>
          <tr><td>FLAME</td><td style="color:var(--muted)">Orange fire</td><td>SMOKE_NORMAL</td><td style="color:var(--muted)">Grey smoke puff</td></tr>
          <tr><td>CRIT</td><td style="color:var(--muted)">Star critical hit</td><td>END_ROD</td><td style="color:var(--muted)">White sparkle</td></tr>
          <tr><td>HEART</td><td style="color:var(--muted)">Pink hearts</td><td>ENCHANTMENT_TABLE</td><td style="color:var(--muted)">Rune letters</td></tr>
          <tr><td>REDSTONE</td><td style="color:var(--muted)">Colored dust*</td><td>SPELL_WITCH</td><td style="color:var(--muted)">Purple magic</td></tr>
          <tr><td>DUST_COLOR_TRANSITION</td><td style="color:var(--muted)">Gradient dust*</td><td>VILLAGER_HAPPY</td><td style="color:var(--muted)">Green sparkle</td></tr>
          <tr><td>TOTEM</td><td style="color:var(--muted)">Totem swirl</td><td>DRAGON_BREATH</td><td style="color:var(--muted)">Purple mist</td></tr>
          <tr><td>EXPLOSION_LARGE</td><td style="color:var(--muted)">Big puff</td><td>PORTAL</td><td style="color:var(--muted)">Nether purple</td></tr>
          <tr><td>SOUL_FIRE_FLAME</td><td style="color:var(--muted)">Blue soul fire</td><td>CHERRY_LEAVES</td><td style="color:var(--muted)">Pink petals</td></tr>
          <tr><td>CAMPFIRE_SIGNAL</td><td style="color:var(--muted)">Rising smoke</td><td>FALLING_DUST</td><td style="color:var(--muted)">Falling block*</td></tr>
        </table>
      </div>
      <div style="padding:8px 18px 14px;font-size:11.5px;color:var(--muted);">* = requires data parameter (DustOptions, BlockData, or ItemStack)</div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Particle Line (A → B)</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">public void</span> <span class="fn">drawLine</span>(<span class="cn">Location</span> a, <span class="cn">Location</span> b, <span class="cn">Particle</span> p, <span class="kw">double</span> gap) {
    <span class="cn">Vector</span> dir = b.toVector().subtract(a.toVector());
    <span class="kw">double</span> len = dir.length();
    dir.normalize();
    <span class="kw">for</span> (<span class="kw">double</span> d = <span class="nm">0</span>; d <= len; d += gap) {
        a.getWorld().spawnParticle(p, a.clone().add(dir.clone().multiply(d)), <span class="nm">1</span>, <span class="nm">0</span>, <span class="nm">0</span>, <span class="nm">0</span>, <span class="nm">0</span>);
    }
}
<span class="cm">// drawLine(player.getLocation(), target.getLocation(), Particle.END_ROD, 0.3);</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Circle, Sphere & Burst</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Horizontal circle</span>
<span class="kw">public void</span> <span class="fn">drawCircle</span>(<span class="cn">Location</span> center, <span class="kw">double</span> r, <span class="cn">Particle</span> p, <span class="kw">int</span> pts) {
    <span class="kw">for</span> (<span class="kw">int</span> i = <span class="nm">0</span>; i < pts; i++) {
        <span class="kw">double</span> a = (<span class="nm">2</span> * <span class="cn">Math</span>.PI / pts) * i;
        center.getWorld().spawnParticle(p,
            center.clone().add(<span class="cn">Math</span>.cos(a)*r, <span class="nm">0</span>, <span class="cn">Math</span>.sin(a)*r), <span class="nm">1</span>, <span class="nm">0</span>, <span class="nm">0</span>, <span class="nm">0</span>, <span class="nm">0</span>);
    }
}
<span class="cm">// drawCircle(player.getLocation(), 3.0, Particle.FLAME, 36);</span>

<span class="cm">// Sphere (Fibonacci lattice — even distribution)</span>
<span class="kw">public void</span> <span class="fn">drawSphere</span>(<span class="cn">Location</span> center, <span class="kw">double</span> r, <span class="cn">Particle</span> p, <span class="kw">int</span> pts) {
    <span class="kw">for</span> (<span class="kw">int</span> i = <span class="nm">0</span>; i < pts; i++) {
        <span class="kw">double</span> phi = <span class="cn">Math</span>.acos(<span class="nm">1</span> - <span class="nm">2.0</span>*i/pts);
        <span class="kw">double</span> theta = <span class="cn">Math</span>.PI*(<span class="nm">1</span>+<span class="cn">Math</span>.sqrt(<span class="nm">5</span>))*i;
        <span class="kw">double</span> x = r*<span class="cn">Math</span>.sin(phi)*<span class="cn">Math</span>.cos(theta);
        <span class="kw">double</span> y = r*<span class="cn">Math</span>.cos(phi);
        <span class="kw">double</span> z = r*<span class="cn">Math</span>.sin(phi)*<span class="cn">Math</span>.sin(theta);
        center.getWorld().spawnParticle(p, center.clone().add(x,y,z), <span class="nm">1</span>, <span class="nm">0</span>, <span class="nm">0</span>, <span class="nm">0</span>, <span class="nm">0</span>);
    }
}
<span class="cm">// drawSphere(player.getLocation().add(0,1,0), 2.0, Particle.END_ROD, 150);</span>

<span class="cm">// Random burst (explosion-style)</span>
<span class="kw">public void</span> <span class="fn">burst</span>(<span class="cn">Location</span> c, <span class="cn">Particle</span> p, <span class="kw">int</span> count, <span class="kw">double</span> speed) {
    <span class="cn">Random</span> rand = <span class="kw">new</span> <span class="cn">Random</span>();
    <span class="kw">for</span> (<span class="kw">int</span> i = <span class="nm">0</span>; i < count; i++) {
        <span class="kw">double</span> phi = <span class="cn">Math</span>.acos(<span class="nm">2</span>*rand.nextDouble()-<span class="nm">1</span>);
        <span class="kw">double</span> theta = <span class="nm">2</span>*<span class="cn">Math</span>.PI*rand.nextDouble();
        c.getWorld().spawnParticle(p, c, <span class="nm">0</span>,
            <span class="cn">Math</span>.sin(phi)*<span class="cn">Math</span>.cos(theta),
            <span class="cn">Math</span>.cos(phi),
            <span class="cn">Math</span>.sin(phi)*<span class="cn">Math</span>.sin(theta), speed);
    }
}
<span class="cm">// burst(player.getLocation().add(0,1,0), Particle.CRIT, 50, 0.3);</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Animated Helix / Spiral</div><div class="card-desc">An animated double helix that rises over time — looks like a rising vortex. Auto-cancels.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">public</span> <span class="cn">BukkitTask</span> <span class="fn">spawnHelix</span>(<span class="cn">Location</span> center, <span class="cn">Particle</span> particle) {
    <span class="kw">final double</span>[] t = {<span class="nm">0</span>};
    <span class="kw">return new</span> <span class="cn">BukkitRunnable</span>() {
        <span class="an">@Override</span> <span class="kw">public void</span> <span class="fn">run</span>() {
            <span class="kw">for</span> (<span class="kw">int</span> arm = <span class="nm">0</span>; arm < <span class="nm">2</span>; arm++) {
                <span class="kw">double</span> angle = t[<span class="nm">0</span>] + (<span class="cn">Math</span>.PI * arm);
                <span class="kw">double</span> x = <span class="cn">Math</span>.cos(angle) * <span class="nm">1.5</span>;
                <span class="kw">double</span> z = <span class="cn">Math</span>.sin(angle) * <span class="nm">1.5</span>;
                <span class="kw">double</span> y = (t[<span class="nm">0</span>] / (<span class="nm">2</span>*<span class="cn">Math</span>.PI)) * <span class="nm">2</span> % <span class="nm">4</span>;
                center.getWorld().spawnParticle(particle,
                    center.clone().add(x,y,z), <span class="nm">1</span>, <span class="nm">0</span>, <span class="nm">0</span>, <span class="nm">0</span>, <span class="nm">0</span>);
            }
            t[<span class="nm">0</span>] += <span class="nm">0.15</span>;
            <span class="kw">if</span> (t[<span class="nm">0</span>] > <span class="nm">20</span>*<span class="cn">Math</span>.PI) <span class="kw">this</span>.cancel();
        }
    }.runTaskTimer(plugin, <span class="nm">0L</span>, <span class="nm">1L</span>);
}</pre></div></div>
  </div>
</section>

<!-- ═══ JAVA BASICS ═══ -->
<section class="section" id="java-basics">
  <div class="section-title">📘 Java Basics <span class="badge">LANGUAGE</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Data Types & Conversions</div><div class="card-desc">Java is strict — you must declare the type. Primitives are lowercase. Wrapper objects are capitalized and can be null.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Primitives — stored by value, NOT nullable</span>
<span class="kw">int</span>     kills     = <span class="nm">5</span>;           <span class="cm">// whole numbers -2B to 2B</span>
<span class="kw">long</span>    bigNum    = <span class="nm">9999999999L</span>; <span class="cm">// bigger integer — add L suffix</span>
<span class="kw">double</span>  health    = <span class="nm">20.0</span>;        <span class="cm">// decimal 64-bit (prefer over float)</span>
<span class="kw">float</span>   speed     = <span class="nm">1.5f</span>;        <span class="cm">// decimal 32-bit — add f suffix</span>
<span class="kw">boolean</span> pvpOn     = <span class="kw">true</span>;
<span class="kw">char</span>    grade     = <span class="st">'A'</span>;         <span class="cm">// single character, single quotes</span>

<span class="cm">// Wrapper objects — capitalized, CAN be null, have helper methods</span>
<span class="cn">Integer</span> i    = <span class="nm">42</span>;   <span class="cm">// auto-boxed from int</span>
<span class="cn">Boolean</span> flag = <span class="kw">null</span>; <span class="cm">// can hold null unlike primitive boolean</span>

<span class="cm">// Conversions</span>
<span class="kw">int</span>    from_d = (<span class="kw">int</span>) <span class="nm">3.9</span>;              <span class="cm">// 3 (truncates, NOT rounds)</span>
<span class="kw">double</span> from_i = (<span class="kw">double</span>) <span class="nm">5</span> / <span class="nm">2</span>;          <span class="cm">// 2.5 — cast BEFORE dividing</span>
<span class="cn">String</span> str    = <span class="cn">String</span>.valueOf(<span class="nm">42</span>);       <span class="cm">// "42"</span>
<span class="kw">int</span>    parsed = <span class="cn">Integer</span>.parseInt(<span class="st">"42"</span>);   <span class="cm">// 42 (throws NumberFormatException!)</span>
<span class="kw">double</span> parsedD = <span class="cn">Double</span>.parseDouble(<span class="st">"3.14"</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Variables & Math Operators</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">int</span> score = <span class="nm">0</span>;
score = <span class="nm">10</span>;
score += <span class="nm">5</span>;   <span class="cm">// shorthand for score = score + 5 → 15</span>
<span class="kw">final int</span> MAX = <span class="nm">20</span>;  <span class="cm">// constant — cannot reassign</span>
<span class="kw">var</span> list = <span class="kw">new</span> <span class="cn">ArrayList</span>&lt;<span class="cn">String</span>&gt;(); <span class="cm">// Java 10+ — type inferred</span>

<span class="kw">int</span> a = <span class="nm">10</span> + <span class="nm">5</span>;  <span class="cm">// 15   addition</span>
<span class="kw">int</span> b = <span class="nm">10</span> - <span class="nm">3</span>;  <span class="cm">// 7    subtraction</span>
<span class="kw">int</span> c = <span class="nm">4</span>  * <span class="nm">3</span>;  <span class="cm">// 12   multiplication</span>
<span class="kw">int</span> d = <span class="nm">10</span> / <span class="nm">2</span>;  <span class="cm">// 5    division</span>
<span class="kw">int</span> e = <span class="nm">10</span> % <span class="nm">3</span>;  <span class="cm">// 1    modulo (remainder)</span>
x++;  x--;        <span class="cm">// increment / decrement</span>

<span class="cm">// Ternary (inline if/else)</span>
<span class="cn">String</span> label = (kills >= <span class="nm">10</span>) ? <span class="st">"§cKiller"</span> : <span class="st">"§7Newbie"</span>;</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Strings (Text)</div><div class="card-desc">Always use .equals() to compare strings — never ==. That compares memory address, not content.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">String</span> name = <span class="st">"Logo"</span>;
name.length();                                  <span class="cm">// 4</span>
name.equals(<span class="st">"Logo"</span>);                           <span class="cm">// ✓ ALWAYS use .equals()</span>
name.equalsIgnoreCase(<span class="st">"logo"</span>);
name.contains(<span class="st">"og"</span>);
name.startsWith(<span class="st">"Lo"</span>); name.endsWith(<span class="st">"go"</span>);
name.toUpperCase(); name.toLowerCase();
name.trim(); name.strip();                      <span class="cm">// strip = Java 11+ unicode-aware</span>
name.isEmpty();  name.isBlank();                <span class="cm">// isBlank = only whitespace?</span>
name.replace(<span class="st">"Logo"</span>, <span class="st">"Steve"</span>);
name.substring(<span class="nm">6</span>); name.substring(<span class="nm">0</span>, <span class="nm">5</span>);
name.split(<span class="st">","</span>);
name.indexOf(<span class="st">"og"</span>); name.charAt(<span class="nm">0</span>);

<span class="cm">// String.format — cleaner than concatenation</span>
<span class="cn">String</span>.format(<span class="st">"§aPlayer §f%s §ahas §f%d §akills!"</span>, name, kills);
<span class="cm">// %s=String  %d=int/long  %f=float/double  %b=boolean</span>

<span class="cm">// Join</span>
<span class="cn">String</span>.join(<span class="st">", "</span>, <span class="st">"a"</span>, <span class="st">"b"</span>, <span class="st">"c"</span>); <span class="cm">// "a, b, c"</span>

<span class="cm">// StringBuilder — efficient when doing many appends</span>
<span class="cn">StringBuilder</span> sb = <span class="kw">new</span> <span class="cn">StringBuilder</span>();
<span class="kw">for</span> (<span class="cn">Player</span> p : online) sb.append(p.getName()).append(<span class="st">", "</span>);
<span class="cn">String</span> result = sb.toString();</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">If / Else / Switch</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">if</span> (health <= <span class="nm">0</span>) {
    <span class="cm">// dead</span>
} <span class="kw">else if</span> (health < <span class="nm">5.0</span>) {
    <span class="cm">// critical</span>
} <span class="kw">else</span> {
    <span class="cm">// healthy</span>
}
<span class="cm">// ==  !=  &gt;  &lt;  &gt;=  &lt;=  |  &&=AND  ||=OR  !=NOT</span>

<span class="cm">// Classic switch</span>
<span class="kw">switch</span> (args[<span class="nm">0</span>].toLowerCase()) {
    <span class="kw">case</span> <span class="st">"heal"</span>: <span class="fn">handleHeal</span>(); <span class="kw">break</span>;
    <span class="kw">default</span>: sender.sendMessage(<span class="st">"Unknown!"</span>); <span class="kw">break</span>;
}

<span class="cm">// Switch expression (Java 14+) — much cleaner</span>
<span class="kw">int</span> result = <span class="kw">switch</span> (gameMode) {
    <span class="kw">case</span> <span class="st">"survival"</span>  -> <span class="nm">0</span>;
    <span class="kw">case</span> <span class="st">"creative"</span>  -> <span class="nm">1</span>;
    <span class="kw">case</span> <span class="st">"adventure"</span> -> <span class="nm">2</span>;
    <span class="kw">default</span>         -> -<span class="nm">1</span>;
};</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Loops</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Classic for (known count)</span>
<span class="kw">for</span> (<span class="kw">int</span> i = <span class="nm">0</span>; i < <span class="nm">10</span>; i++) { }

<span class="cm">// For-each (collections)</span>
<span class="kw">for</span> (<span class="cn">Player</span> p : <span class="cn">Bukkit</span>.getOnlinePlayers()) {
    p.sendMessage(<span class="st">"§aHello!"</span>);
}

<span class="cm">// While loop</span>
<span class="kw">int</span> count = <span class="nm">0</span>;
<span class="kw">while</span> (count < <span class="nm">5</span>) { count++; }

<span class="cm">// Do-while — always runs at least once</span>
<span class="kw">do</span> { count++; } <span class="kw">while</span> (count < <span class="nm">5</span>);

<span class="cm">// Break / continue</span>
<span class="kw">for</span> (<span class="kw">int</span> i = <span class="nm">0</span>; i < <span class="nm">10</span>; i++) {
    <span class="kw">if</span> (i == <span class="nm">3</span>) <span class="kw">continue</span>; <span class="cm">// skip 3</span>
    <span class="kw">if</span> (i == <span class="nm">7</span>) <span class="kw">break</span>;    <span class="cm">// stop at 7</span>
}

<span class="cm">// Java Streams (functional style)</span>
<span class="cn">List</span>&lt;<span class="cn">String</span>&gt; names = <span class="cn">Bukkit</span>.getOnlinePlayers().stream()
    .map(<span class="cn">Player</span>::getName)
    .filter(n -> n.startsWith(<span class="st">"A"</span>))
    .collect(<span class="cn">Collectors</span>.toList());

<span class="kw">long</span> admins = <span class="cn">Bukkit</span>.getOnlinePlayers().stream()
    .filter(p -> p.hasPermission(<span class="st">"admin"</span>)).count();</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Collections — List, Map, Set</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// List — ordered, allows duplicates</span>
<span class="cn">List</span>&lt;<span class="cn">String</span>&gt; players = <span class="kw">new</span> <span class="cn">ArrayList</span>&lt;&gt;();
players.add(<span class="st">"Logo"</span>);
players.add(<span class="nm">0</span>, <span class="st">"First"</span>);     <span class="cm">// insert at index</span>
players.set(<span class="nm">0</span>, <span class="st">"Updated"</span>);   <span class="cm">// replace at index</span>
players.remove(<span class="st">"Logo"</span>);      <span class="cm">// by value</span>
players.remove(<span class="nm">0</span>);           <span class="cm">// by index</span>
players.get(<span class="nm">0</span>);  players.size();  players.contains(<span class="st">"Logo"</span>);  players.clear();
<span class="cn">Collections</span>.sort(players);  <span class="cn">Collections</span>.shuffle(players);

<span class="cm">// Map — key → value, keys must be unique</span>
<span class="cn">Map</span>&lt;<span class="cn">UUID</span>, <span class="cn">Integer</span>&gt; killMap = <span class="kw">new</span> <span class="cn">HashMap</span>&lt;&gt;();
killMap.put(uuid, <span class="nm">5</span>);
killMap.get(uuid);                     <span class="cm">// null if missing</span>
killMap.getOrDefault(uuid, <span class="nm">0</span>);        <span class="cm">// safe fallback</span>
killMap.putIfAbsent(uuid, <span class="nm">0</span>);          <span class="cm">// only puts if not present</span>
killMap.merge(uuid, <span class="nm">1</span>, <span class="cn">Integer</span>::sum); <span class="cm">// increment kill counter!</span>
killMap.containsKey(uuid);  killMap.remove(uuid);
<span class="kw">for</span> (<span class="cn">Map</span>.Entry&lt;<span class="cn">UUID</span>,<span class="cn">Integer</span>&gt; e : killMap.entrySet()) {
    e.getKey(); e.getValue();
}

<span class="cm">// Set — unique values, O(1) lookup</span>
<span class="cn">Set</span>&lt;<span class="cn">UUID</span>&gt; seen = <span class="kw">new</span> <span class="cn">HashSet</span>&lt;&gt;();
seen.add(player.getUniqueId());
seen.contains(uuid);  seen.remove(uuid);

<span class="cm">// Thread-safe map for async use</span>
<span class="cn">Map</span>&lt;<span class="cn">UUID</span>,<span class="cn">Long</span>&gt; cdMap = <span class="kw">new</span> <span class="cn">ConcurrentHashMap</span>&lt;&gt;();</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Methods, Null Safety & Casting</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Methods</span>
<span class="kw">public void</span> <span class="fn">greetPlayer</span>(<span class="cn">Player</span> p) { p.sendMessage(<span class="st">"Hello, "</span> + p.getName() + <span class="st">"!"</span>); }
<span class="kw">public boolean</span> <span class="fn">isAlive</span>(<span class="cn">Player</span> p) { <span class="kw">return</span> p.getHealth() > <span class="nm">0</span>; }
<span class="kw">public static int</span> <span class="fn">clamp</span>(<span class="kw">int</span> value, <span class="kw">int</span> min, <span class="kw">int</span> max) {
    <span class="kw">return</span> <span class="cn">Math</span>.max(min, <span class="cn">Math</span>.min(max, value));
}
<span class="cm">// Varargs — accepts any number of args</span>
<span class="kw">public void</span> <span class="fn">log</span>(<span class="cn">String</span>... messages) { <span class="kw">for</span> (<span class="cn">String</span> m : messages) plugin.getLogger().info(m); }

<span class="cm">// Null safety — calling a method on null = NullPointerException crash!</span>
<span class="cn">Player</span> killer = event.getEntity().getKiller(); <span class="cm">// may be null</span>
<span class="kw">if</span> (killer == <span class="kw">null</span>) <span class="kw">return</span>;                    <span class="cm">// ✓ early return pattern</span>
<span class="cn">String</span> display = (name != <span class="kw">null</span>) ? name : <span class="st">"Unknown"</span>; <span class="cm">// ternary</span>

<span class="cm">// Casting — always check before downcasting</span>
<span class="kw">if</span> (sender <span class="kw">instanceof</span> <span class="cn">Player</span>) {
    <span class="cn">Player</span> player = (<span class="cn">Player</span>) sender;
}
<span class="cm">// Java 16+ pattern matching (cleaner)</span>
<span class="kw">if</span> (sender <span class="kw">instanceof</span> <span class="cn">Player</span> player) { player.sendMessage(<span class="st">"Hi!"</span>); }
<span class="kw">if</span> (entity <span class="kw">instanceof</span> <span class="cn">Zombie</span> zombie) { zombie.setVillager(<span class="kw">true</span>); }</pre></div></div>
  </div>
</section>

<!-- ═══ PAPERMC BASICS ═══ -->
<section class="section" id="papermc-basics">
  <div class="section-title">🌍 PaperMC Basics <span class="badge">API</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Player — Everything You Need</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Getting a player</span>
<span class="cn">Player</span> p = <span class="cn">Bukkit</span>.getPlayer(<span class="st">"Logo"</span>);  <span class="cm">// by name, null if offline</span>
<span class="cn">Player</span> p = <span class="cn">Bukkit</span>.getPlayer(uuid);     <span class="cm">// by UUID — preferred!</span>

<span class="cm">// Identity</span>
p.getName(); p.getUniqueId(); p.getDisplayName(); p.getPlayerListName();
p.isOp(); p.setOp(<span class="kw">true</span>);
p.hasPermission(<span class="st">"myplugin.use"</span>);
p.getGameMode(); p.setGameMode(<span class="cn">GameMode</span>.SURVIVAL);
p.isSneaking(); p.isSprinting(); p.isFlying(); p.isDead();

<span class="cm">// Health / Food</span>
p.getHealth(); p.setHealth(<span class="nm">20.0</span>);   <span class="cm">// 0.0 – 20.0</span>
p.getFoodLevel(); p.setFoodLevel(<span class="nm">20</span>);
p.getSaturation(); p.setSaturation(<span class="nm">5.0f</span>);

<span class="cm">// Messaging</span>
p.sendMessage(<span class="st">"§aHello!"</span>);
p.sendTitle(<span class="st">"§6Title"</span>, <span class="st">"§7Subtitle"</span>, <span class="nm">10</span>, <span class="nm">70</span>, <span class="nm">20</span>); <span class="cm">// fadeIn/stay/fadeOut ticks</span>
p.sendActionBar(<span class="st">"§eAbove hotbar"</span>);
p.resetTitle(); <span class="cm">// clear title</span>

<span class="cm">// Movement</span>
p.getLocation(); p.teleport(location);
p.setVelocity(<span class="kw">new</span> <span class="cn">Vector</span>(<span class="nm">0</span>, <span class="nm">1.5</span>, <span class="nm">0</span>)); <span class="cm">// launch upward</span>
p.setAllowFlight(<span class="kw">true</span>); p.setFlying(<span class="kw">true</span>);
p.setWalkSpeed(<span class="nm">0.2f</span>);  <span class="cm">// default 0.2, max 1.0</span>

<span class="cm">// Inventory</span>
p.getInventory().addItem(itemStack);
p.getInventory().setItem(<span class="nm">9</span>, itemStack);
p.getInventory().getItemInMainHand();
p.getInventory().getArmorContents(); <span class="cm">// [boots, legs, chest, helm]</span>
p.getInventory().clear();
p.updateInventory(); <span class="cm">// refresh client after changes</span>

<span class="cm">// Effects / Sounds</span>
p.addPotionEffect(<span class="kw">new</span> <span class="cn">PotionEffect</span>(<span class="cn">PotionEffectType</span>.SPEED, <span class="nm">200</span>, <span class="nm">1</span>));
<span class="cm">// (type, durationTicks, amplifier) — amplifier 0=level I, 1=level II</span>
p.removePotionEffect(<span class="cn">PotionEffectType</span>.SPEED);
p.playSound(p.getLocation(), <span class="cn">Sound</span>.ENTITY_PLAYER_LEVELUP, <span class="nm">1f</span>, <span class="nm">1f</span>);

<span class="cm">// Misc</span>
p.kickPlayer(<span class="st">"§cYou have been kicked."</span>);
p.setExp(<span class="nm">0.5f</span>); p.setLevel(<span class="nm">10</span>); p.giveExp(<span class="nm">100</span>);
p.setFireTicks(<span class="nm">80</span>);   <span class="cm">// set on fire for 4 seconds</span>
p.hidePlayer(plugin, other); p.showPlayer(plugin, other);
p.getBedSpawnLocation(); p.setBedSpawnLocation(loc, <span class="kw">true</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Location</div><div class="card-desc">Represents a position in a world. Always clone before modifying to preserve the original!</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">Location</span> loc = <span class="kw">new</span> <span class="cn">Location</span>(world, x, y, z);
<span class="cn">Location</span> loc = <span class="kw">new</span> <span class="cn">Location</span>(world, x, y, z, yaw, pitch);
<span class="cm">// yaw: -180 to 180 (horizontal) | pitch: -90 to 90 (-90=up)</span>

loc.getX(); loc.getY(); loc.getZ();
loc.getBlockX(); loc.getBlockY(); loc.getBlockZ(); <span class="cm">// floored to int</span>
loc.getYaw(); loc.getPitch(); loc.getWorld(); loc.getBlock();

<span class="cm">// ✦ ALWAYS clone before modifying!</span>
<span class="cn">Location</span> above  = loc.clone().add(<span class="nm">0</span>, <span class="nm">2</span>, <span class="nm">0</span>);
<span class="cn">Location</span> front  = loc.clone().add(loc.getDirection().multiply(<span class="nm">3</span>));
<span class="cn">Location</span> behind = loc.clone().subtract(loc.getDirection().multiply(<span class="nm">3</span>));

<span class="cm">// Distance</span>
<span class="kw">double</span> exact = loc1.distance(loc2);           <span class="cm">// actual distance (slower)</span>
<span class="kw">double</span> sq    = loc1.distanceSquared(loc2);    <span class="cm">// faster — use for range checks</span>
<span class="kw">if</span> (loc1.distanceSquared(loc2) <= <span class="nm">25</span>) { }   <span class="cm">// within 5 blocks (5²=25)</span>

loc.toVector();           <span class="cm">// Vector representation</span>
loc.getDirection();       <span class="cm">// unit vector player is facing</span>
loc.setDirection(vector); <span class="cm">// set yaw/pitch from a Vector</span>

<span class="cm">// Configs save/load locations automatically!</span>
config.set(<span class="st">"home"</span>, loc);
<span class="cn">Location</span> home = (<span class="cn">Location</span>) config.get(<span class="st">"home"</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">World</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">World</span> w = <span class="cn">Bukkit</span>.getWorld(<span class="st">"world"</span>);
<span class="cn">List</span>&lt;<span class="cn">World</span>&gt; all = <span class="cn">Bukkit</span>.getWorlds();

w.spawnEntity(loc, <span class="cn">EntityType</span>.ZOMBIE);
w.spawnParticle(<span class="cn">Particle</span>.FLAME, loc, <span class="nm">30</span>, <span class="nm">0.5</span>, <span class="nm">0.5</span>, <span class="nm">0.5</span>, <span class="nm">0.05</span>);
w.playSound(loc, <span class="cn">Sound</span>.ENTITY_ENDER_DRAGON_GROWL, <span class="nm">1f</span>, <span class="nm">1f</span>);
w.strikeLightning(loc);              <span class="cm">// real — causes damage/fire</span>
w.strikeLightningEffect(loc);        <span class="cm">// visual only, no damage</span>
w.createExplosion(loc, <span class="nm">4f</span>);          <span class="cm">// 4=TNT power, 0=visual only</span>
w.createExplosion(loc, <span class="nm">4f</span>, <span class="kw">false</span>, <span class="kw">false</span>); <span class="cm">// (fire, blockDamage)</span>
w.setTime(<span class="nm">6000</span>);  <span class="cm">// 0=dawn 6000=noon 12000=dusk 18000=midnight</span>
w.setStorm(<span class="kw">true</span>); w.setThundering(<span class="kw">true</span>);
w.getPlayers(); w.getEntities(); w.getLivingEntities();
w.getHighestBlockYAt(x, z); <span class="cm">// top solid block Y</span>
w.dropItem(loc, item);         <span class="cm">// spawn item entity</span>
w.dropItemNaturally(loc, item); <span class="cm">// with random velocity</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Block, Entity & Vector</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Block</span>
<span class="cn">Block</span> block = world.getBlockAt(x, y, z);
block.getType(); block.setType(<span class="cn">Material</span>.GOLD_BLOCK);
block.setType(<span class="cn">Material</span>.AIR); <span class="cm">// remove block</span>
block.getRelative(<span class="cn">BlockFace</span>.UP);
block.getRelative(<span class="cn">BlockFace</span>.DOWN);
block.getRelative(<span class="nm">0</span>, <span class="nm">1</span>, <span class="nm">0</span>); <span class="cm">// same as BlockFace.UP</span>
<span class="cm">// BlockData — for state like waterlogged, slab type, facing</span>
<span class="kw">if</span> (block.getBlockData() <span class="kw">instanceof</span> <span class="cn">Slab</span> slab) { slab.getType(); }
<span class="kw">if</span> (block.getBlockData() <span class="kw">instanceof</span> <span class="cn">Waterlogged</span> wl) { wl.isWaterlogged(); }

<span class="cm">// Entity</span>
entity.getType(); entity.getUniqueId(); entity.getLocation();
entity.getVelocity(); entity.setVelocity(vec);
entity.remove();        entity.isDead();
entity.setGravity(<span class="kw">false</span>); entity.setGlowing(<span class="kw">true</span>);
entity.setCustomName(<span class="st">"§cBoss"</span>); entity.setCustomNameVisible(<span class="kw">true</span>);
entity.setInvulnerable(<span class="kw">true</span>);
<span class="cm">// LivingEntity extras</span>
<span class="cn">LivingEntity</span> le = (<span class="cn">LivingEntity</span>) entity;
le.setAI(<span class="kw">false</span>); le.setSilent(<span class="kw">true</span>);
le.getTarget(); le.setTarget(player);
le.addPotionEffect(<span class="kw">new</span> <span class="cn">PotionEffect</span>(<span class="cn">PotionEffectType</span>.POISON, <span class="nm">200</span>, <span class="nm">0</span>));

<span class="cm">// BoundingBox — hitbox</span>
<span class="cn">BoundingBox</span> bb = entity.getBoundingBox();
bb.contains(loc.toVector()); bb.overlaps(other);

<span class="cm">// Vector — direction or velocity, NOT a position</span>
player.setVelocity(<span class="kw">new</span> <span class="cn">Vector</span>(<span class="nm">0</span>, <span class="nm">0.8</span>, <span class="nm">0</span>)); <span class="cm">// launch upward</span>
<span class="cn">Vector</span> dir = player.getLocation().getDirection(); <span class="cm">// unit vector facing</span>
<span class="cn">Location</span> front = player.getLocation().clone().add(dir.multiply(<span class="nm">5</span>));
v.multiply(<span class="nm">2.0</span>); v.normalize(); v.length();
v.clone(); <span class="cm">// ✦ always clone before mutating!</span></pre></div></div>
  </div>
</section>

<!-- ═══ TIMERS ═══ -->
<section class="section" id="timers">
  <div class="section-title">⏱️ Timers <span class="badge">SCHEDULER</span></div>
  <div class="note"><strong>20 ticks = 1 second.</strong> NEVER use Thread.sleep() — it freezes the entire server main thread.</div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">One-Shot Delay & Repeating Tasks</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Run once after delay (60 ticks = 3 seconds)</span>
<span class="cn">Bukkit</span>.getScheduler().runTaskLater(plugin, () -> {
    player.sendMessage(<span class="st">"§a3 seconds have passed!"</span>);
}, <span class="nm">60L</span>);

<span class="cm">// Run on next server tick</span>
<span class="cn">Bukkit</span>.getScheduler().runTask(plugin, () -> { <span class="cm">/* safe to use Bukkit API */</span> });

<span class="cm">// Run repeatedly (0L=start now, 40L=every 2 seconds)</span>
<span class="cn">BukkitTask</span> task = <span class="cn">Bukkit</span>.getScheduler().runTaskTimer(plugin, () -> {
    <span class="cn">Bukkit</span>.broadcastMessage(<span class="st">"§ePing!"</span>);
}, <span class="nm">0L</span>, <span class="nm">40L</span>);

task.cancel(); <span class="cm">// stop it</span>

<span class="cm">// Self-cancelling task (runs 5 times then stops)</span>
<span class="kw">final int</span>[] count = {<span class="nm">0</span>};
<span class="kw">final</span> <span class="cn">BukkitTask</span>[] ref = {<span class="kw">null</span>};
ref[<span class="nm">0</span>] = <span class="cn">Bukkit</span>.getScheduler().runTaskTimer(plugin, () -> {
    player.sendMessage(<span class="st">"Count: "</span> + (++count[<span class="nm">0</span>]));
    <span class="kw">if</span> (count[<span class="nm">0</span>] >= <span class="nm">5</span>) ref[<span class="nm">0</span>].cancel();
}, <span class="nm">0L</span>, <span class="nm">20L</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">BukkitRunnable — Cleaner Self-Contained Tasks</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">new</span> <span class="cn">BukkitRunnable</span>() {
    <span class="kw">int</span> ticks = <span class="nm">0</span>;
    <span class="an">@Override</span>
    <span class="kw">public void</span> <span class="fn">run</span>() {
        ticks++;
        <span class="kw">if</span> (player.isOnline()) {
            player.sendActionBar(<span class="st">"§eTask tick: "</span> + ticks);
        }
        <span class="kw">if</span> (ticks >= <span class="nm">100</span> || !player.isOnline()) {
            <span class="kw">this</span>.cancel(); <span class="cm">// cancel self</span>
        }
    }
}.runTaskTimer(plugin, <span class="nm">0L</span>, <span class="nm">1L</span>); <span class="cm">// start now, every tick</span>

<span class="cm">// Or with a delay</span>
<span class="kw">new</span> <span class="cn">BukkitRunnable</span>() {
    <span class="an">@Override</span> <span class="kw">public void</span> <span class="fn">run</span>() { player.sendMessage(<span class="st">"§aDelayed!"</span>); }
}.runTaskLater(plugin, <span class="nm">100L</span>);

<span class="cm">// Cancel all plugin tasks on disable</span>
<span class="cn">Bukkit</span>.getScheduler().cancelTasks(<span class="kw">this</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Async Tasks — For Heavy Work (DB, Files, HTTP)</div><div class="card-desc">NEVER call Bukkit API inside async tasks! Always switch back to the main thread first.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="warn"><strong>⚠ NEVER</strong> call player.sendMessage(), teleport(), or any world modification inside async — it will crash or corrupt the world. Switch back to main thread first.</div>
      <div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Async → heavy work → sync → update game</span>
<span class="cn">Bukkit</span>.getScheduler().runTaskAsynchronously(plugin, () -> {
    <span class="cm">// ✓ safe: file I/O, database queries, HTTP requests</span>
    <span class="cn">String</span> data = database.loadPlayerData(player.getUniqueId());

    <span class="cm">// Switch back to main thread for any Bukkit API</span>
    <span class="cn">Bukkit</span>.getScheduler().runTask(plugin, () -> {
        player.sendMessage(<span class="st">"§aLoaded: "</span> + data); <span class="cm">// ✓ safe now</span>
        player.teleport(spawnLocation);           <span class="cm">// ✓ safe now</span>
    });
});

<span class="cm">// Async repeating (e.g. auto-save every 5 minutes)</span>
<span class="cn">Bukkit</span>.getScheduler().runTaskTimerAsynchronously(plugin, () -> {
    saveAllData();
}, <span class="nm">6000L</span>, <span class="nm">6000L</span>); <span class="cm">// delay 5min, repeat every 5min</span></pre></div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Ticks / Time Reference</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table style="font-size:12px;">
          <tr><th>Ticks</th><th>Real Time</th><th>Ticks</th><th>Real Time</th></tr>
          <tr><td>1</td><td style="color:var(--muted)">0.05s</td><td>200</td><td style="color:var(--muted)">10 seconds</td></tr>
          <tr><td>20</td><td style="color:var(--muted)">1 second</td><td>1200</td><td style="color:var(--muted)">1 minute</td></tr>
          <tr><td>40</td><td style="color:var(--muted)">2 seconds</td><td>6000</td><td style="color:var(--muted)">5 minutes</td></tr>
          <tr><td>60</td><td style="color:var(--muted)">3 seconds</td><td>24000</td><td style="color:var(--muted)">20 min (full MC day)</td></tr>
          <tr><td>100</td><td style="color:var(--muted)">5 seconds</td><td>72000</td><td style="color:var(--muted)">1 hour</td></tr>
        </table>
      </div>
    </div>
  </div>
</section>

<!-- ═══ COMMANDS ═══ -->
<section class="section" id="commands">
  <div class="section-title">💬 Commands <span class="badge">CMD</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">plugin.yml — Registering Commands</div><div class="card-desc">Every command MUST be declared in plugin.yml or the server won't recognize it at all.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm"># src/main/resources/plugin.yml</span>
commands:
  heal:
    description: <span class="st">"Heal a player to full health"</span>
    usage: <span class="st">"/<command> [player]"</span>
    permission: myplugin.heal
    permission-message: <span class="st">"§cNo permission!"</span>
    aliases: [h, healme]

permissions:
  myplugin.*:
    description: <span class="st">"All MyPlugin permissions"</span>
    children:
      myplugin.heal: <span class="kw">true</span>
  myplugin.heal:
    description: <span class="st">"Allow /heal"</span>
    default: op  <span class="cm"># true | false | op | not op</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Full Command Class</div><div class="card-desc">Return true = command handled. Return false = shows the usage message from plugin.yml.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">public class</span> <span class="cn">HealCommand</span> <span class="kw">implements</span> <span class="cn">CommandExecutor</span>, <span class="cn">TabCompleter</span> {
    <span class="kw">private final</span> <span class="cn">MyPlugin</span> plugin;
    <span class="kw">public</span> <span class="fn">HealCommand</span>(<span class="cn">MyPlugin</span> plugin) { <span class="kw">this</span>.plugin = plugin; }

    <span class="an">@Override</span>
    <span class="kw">public boolean</span> <span class="fn">onCommand</span>(<span class="cn">CommandSender</span> sender, <span class="cn">Command</span> cmd,
                              <span class="cn">String</span> label, <span class="cn">String</span>[] args) {
        <span class="kw">if</span> (!(sender <span class="kw">instanceof</span> <span class="cn">Player</span> player)) {
            sender.sendMessage(<span class="st">"§cPlayers only!"</span>); <span class="kw">return true</span>;
        }
        <span class="kw">if</span> (!player.hasPermission(<span class="st">"myplugin.heal"</span>)) {
            player.sendMessage(<span class="st">"§cNo permission!"</span>); <span class="kw">return true</span>;
        }
        <span class="kw">if</span> (args.length == <span class="nm">0</span>) {
            <span class="cm">// /heal — heal self</span>
            player.setHealth(<span class="nm">20.0</span>); player.setFoodLevel(<span class="nm">20</span>);
            player.sendMessage(<span class="st">"§aYou have been fully healed!"</span>);
            <span class="kw">return true</span>;
        }
        <span class="cm">// /heal <player></span>
        <span class="cn">Player</span> target = <span class="cn">Bukkit</span>.getPlayer(args[<span class="nm">0</span>]);
        <span class="kw">if</span> (target == <span class="kw">null</span>) {
            player.sendMessage(<span class="st">"§cPlayer §f"</span> + args[<span class="nm">0</span>] + <span class="st">" §cis not online!"</span>);
            <span class="kw">return true</span>;
        }
        target.setHealth(<span class="nm">20.0</span>); target.setFoodLevel(<span class="nm">20</span>);
        player.sendMessage(<span class="st">"§aHealed §f"</span> + target.getName());
        target.sendMessage(<span class="st">"§f"</span> + player.getName() + <span class="st">" §ahealed you!"</span>);
        target.playSound(target.getLocation(), <span class="cn">Sound</span>.ENTITY_PLAYER_LEVELUP, <span class="nm">1f</span>, <span class="nm">2f</span>);
        <span class="kw">return true</span>;
    }

    <span class="an">@Override</span>
    <span class="kw">public</span> <span class="cn">List</span>&lt;<span class="cn">String</span>&gt; <span class="fn">onTabComplete</span>(<span class="cn">CommandSender</span> sender, <span class="cn">Command</span> cmd,
                                        <span class="cn">String</span> alias, <span class="cn">String</span>[] args) {
        <span class="kw">if</span> (args.length == <span class="nm">1</span>) {
            <span class="cn">String</span> input = args[<span class="nm">0</span>].toLowerCase();
            <span class="kw">return</span> <span class="cn">Bukkit</span>.getOnlinePlayers().stream()
                .map(<span class="cn">Player</span>::getName)
                .filter(n -> n.toLowerCase().startsWith(input))
                .collect(<span class="cn">Collectors</span>.toList());
        }
        <span class="kw">return</span> <span class="cn">Collections</span>.emptyList();
    }
}</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Argument Patterns</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table class="plain" style="font-size:12px;">
          <tr><th>Pattern</th><th>Code</th></tr>
          <tr><td>Check no args</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">if (args.length == 0)</td></tr>
          <tr><td>Check minimum args</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">if (args.length &lt; 2) { player.sendMessage("Usage: ..."); return true; }</td></tr>
          <tr><td>Parse int safely</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">try { int n = Integer.parseInt(args[1]); } catch (NumberFormatException e) { }</td></tr>
          <tr><td>Parse double safely</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">try { double d = Double.parseDouble(args[1]); } catch (NumberFormatException e) { }</td></tr>
          <tr><td>Get online player</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">Player t = Bukkit.getPlayer(args[0]); if (t == null) { ... }</td></tr>
          <tr><td>Join all args</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">String.join(" ", args)</td></tr>
          <tr><td>Join from index 1</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">String.join(" ", Arrays.copyOfRange(args, 1, args.length))</td></tr>
          <tr><td>Case-insensitive</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">args[0].equalsIgnoreCase("heal")</td></tr>
          <tr><td>Run as console</td><td style="font-family:monospace;color:#8be9fd;font-size:11.5px;">Bukkit.dispatchCommand(Bukkit.getConsoleSender(), "ban " + name)</td></tr>
        </table>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Subcommand System + Tab Complete</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Switch expression for clean routing (Java 14+)</span>
<span class="kw">switch</span> (args[<span class="nm">0</span>].toLowerCase()) {
    <span class="kw">case</span> <span class="st">"give"</span>  -> <span class="fn">handleGive</span>(player, args);
    <span class="kw">case</span> <span class="st">"take"</span>  -> <span class="fn">handleTake</span>(player, args);
    <span class="kw">case</span> <span class="st">"reset"</span> -> <span class="fn">handleReset</span>(player, args);
    <span class="kw">default</span>      -> player.sendMessage(<span class="st">"§cUnknown: §f/myplugin <give|take|reset>"</span>);
}

<span class="cm">// Tab complete for subcommands — StringUtil filters by partial match</span>
<span class="kw">if</span> (args.length == <span class="nm">1</span>) {
    <span class="kw">return</span> <span class="cn">StringUtil</span>.copyPartialMatches(args[<span class="nm">0</span>],
        <span class="cn">Arrays</span>.asList(<span class="st">"give"</span>, <span class="st">"take"</span>, <span class="st">"reset"</span>),
        <span class="kw">new</span> <span class="cn">ArrayList</span>&lt;&gt;());
}
<span class="cm">// Tab complete player names for arg 2</span>
<span class="kw">if</span> (args.length == <span class="nm">2</span> && args[<span class="nm">0</span>].equalsIgnoreCase(<span class="st">"give"</span>)) {
    <span class="kw">return</span> <span class="cn">Bukkit</span>.getOnlinePlayers().stream()
        .map(<span class="cn">Player</span>::getName)
        .filter(n -> n.toLowerCase().startsWith(args[<span class="nm">1</span>].toLowerCase()))
        .collect(<span class="cn">Collectors</span>.toList());
}</pre></div></div>
  </div>
</section>

<!-- ═══ CONFIGS ═══ -->
<section class="section" id="configs">
  <div class="section-title">💾 Configs / Data Saving <span class="badge">PERSISTENCE</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">config.yml (Built-in)</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm"># src/main/resources/config.yml</span>
welcome-message: <span class="st">"§aWelcome to the server!"</span>
settings:
  pvp-enabled: <span class="kw">true</span>
  max-kills: <span class="nm">100</span>
  spawn-radius: <span class="nm">50.5</span>
rewards: [DIAMOND, GOLD_INGOT, IRON_INGOT]
kits:
  warrior:
    price: <span class="nm">500</span>
    cooldown: <span class="nm">3600</span></pre></div>
      <div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// In onEnable()</span>
saveDefaultConfig(); <span class="cm">// creates config.yml from resources if it doesn't exist</span>
reloadConfig();      <span class="cm">// read from disk into memory</span>

<span class="cm">// Reading</span>
<span class="cn">String</span>  msg    = getConfig().getString(<span class="st">"welcome-message"</span>, <span class="st">"Default!"</span>); <span class="cm">// with fallback</span>
<span class="kw">boolean</span> pvp    = getConfig().getBoolean(<span class="st">"settings.pvp-enabled"</span>);
<span class="kw">int</span>     max    = getConfig().getInt(<span class="st">"settings.max-kills"</span>, <span class="nm">100</span>);
<span class="kw">double</span>  radius = getConfig().getDouble(<span class="st">"settings.spawn-radius"</span>);
<span class="cn">List</span>&lt;<span class="cn">String</span>&gt; items = getConfig().getStringList(<span class="st">"rewards"</span>);
<span class="kw">int</span>     price  = getConfig().getInt(<span class="st">"kits.warrior.price"</span>, <span class="nm">0</span>);

<span class="cm">// Writing</span>
getConfig().set(<span class="st">"settings.pvp-enabled"</span>, <span class="kw">false</span>);
getConfig().set(<span class="st">"players.Logo.kills"</span>, <span class="nm">42</span>);
saveConfig(); <span class="cm">// ✦ MUST call this or changes only exist in memory!</span>

<span class="cm">// Check / delete</span>
getConfig().contains(<span class="st">"settings.pvp-enabled"</span>);
getConfig().set(<span class="st">"key"</span>, <span class="kw">null</span>); <span class="cm">// set to null = delete that key</span></pre></div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Custom Player Data Files</div><div class="card-desc">For saving player-specific data like kills, homes, stats, etc.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">private</span> <span class="cn">File</span> dataFile;
<span class="kw">private</span> <span class="cn">FileConfiguration</span> data;

<span class="kw">private void</span> <span class="fn">loadData</span>() {
    dataFile = <span class="kw">new</span> <span class="cn">File</span>(getDataFolder(), <span class="st">"playerdata.yml"</span>);
    <span class="kw">if</span> (!dataFile.exists()) { dataFile.getParentFile().mkdirs(); }
    data = <span class="cn">YamlConfiguration</span>.loadConfiguration(dataFile);
}

<span class="kw">private void</span> <span class="fn">saveData</span>() {
    <span class="kw">try</span> { data.save(dataFile); }
    <span class="kw">catch</span> (<span class="cn">IOException</span> e) { getLogger().severe(<span class="st">"Could not save data!"</span>); }
}

<span class="cm">// Write player data</span>
<span class="cn">String</span> path = <span class="st">"players."</span> + player.getUniqueId();
data.set(path + <span class="st">".kills"</span>, kills);
data.set(path + <span class="st">".home"</span>, player.getLocation()); <span class="cm">// Location saves perfectly!</span>
data.set(path + <span class="st">".name"</span>, player.getName());      <span class="cm">// cache name for display</span>
saveData();

<span class="cm">// Read player data</span>
<span class="cn">String</span> base = <span class="st">"players."</span> + uuid;
<span class="kw">int</span>      kills = data.getInt(base + <span class="st">".kills"</span>, <span class="nm">0</span>);
<span class="cn">Location</span> home  = (<span class="cn">Location</span>) data.get(base + <span class="st">".home"</span>); <span class="cm">// may be null</span>

<span class="cm">// List all players</span>
<span class="cn">ConfigurationSection</span> sec = data.getConfigurationSection(<span class="st">"players"</span>);
<span class="kw">if</span> (sec != <span class="kw">null</span>) {
    <span class="kw">for</span> (<span class="cn">String</span> uuidStr : sec.getKeys(<span class="kw">false</span>)) {
        <span class="kw">int</span> k = data.getInt(<span class="st">"players."</span> + uuidStr + <span class="st">".kills"</span>);
    }
}</pre></div></div>
  </div>
</section>

<!-- ═══ PDC ═══ -->
<section class="section" id="pdc">
  <div class="section-title">🏷️ PersistentDataContainer (PDC) <span class="badge">ITEM / ENTITY DATA</span></div>
  <div class="note"><strong>PDC data survives restarts and server reloads.</strong> Ideal for custom item tags, custom mob IDs, or any data that needs to live on an item or entity.</div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Writing & Reading PDC Data</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Step 1 — Create NamespacedKeys (once per tag, store them)</span>
<span class="cn">NamespacedKey</span> SWORD_KEY  = <span class="kw">new</span> <span class="cn">NamespacedKey</span>(plugin, <span class="st">"legendary_sword"</span>);
<span class="cn">NamespacedKey</span> DAMAGE_KEY = <span class="kw">new</span> <span class="cn">NamespacedKey</span>(plugin, <span class="st">"bonus_damage"</span>);
<span class="cn">NamespacedKey</span> BOSS_KEY   = <span class="kw">new</span> <span class="cn">NamespacedKey</span>(plugin, <span class="st">"boss_id"</span>);

<span class="cm">// Step 2 — Write to ItemMeta</span>
<span class="cn">ItemMeta</span> meta = item.getItemMeta();
<span class="cn">PersistentDataContainer</span> pdc = meta.getPersistentDataContainer();
pdc.set(SWORD_KEY,  <span class="cn">PersistentDataType</span>.STRING,  <span class="st">"fire"</span>); <span class="cm">// string tag</span>
pdc.set(DAMAGE_KEY, <span class="cn">PersistentDataType</span>.INTEGER, <span class="nm">50</span>);      <span class="cm">// int</span>
item.setItemMeta(meta); <span class="cm">// ✦ must apply back!</span>

<span class="cm">// Step 3 — Read</span>
<span class="cn">String</span>  type = pdc.get(SWORD_KEY,  <span class="cn">PersistentDataType</span>.STRING);  <span class="cm">// null if absent</span>
<span class="cn">Integer</span> dmg  = pdc.get(DAMAGE_KEY, <span class="cn">PersistentDataType</span>.INTEGER);

<span class="cm">// Check / Remove</span>
pdc.has(SWORD_KEY, <span class="cn">PersistentDataType</span>.STRING);
pdc.remove(SWORD_KEY);

<span class="cm">// On entities (same API)</span>
entity.getPersistentDataContainer().set(BOSS_KEY, <span class="cn">PersistentDataType</span>.STRING, <span class="st">"king"</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Available PDC Types & Nested Containers</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Available types</span>
<span class="cn">PersistentDataType</span>.STRING
<span class="cn">PersistentDataType</span>.INTEGER
<span class="cn">PersistentDataType</span>.DOUBLE
<span class="cn">PersistentDataType</span>.FLOAT
<span class="cn">PersistentDataType</span>.LONG
<span class="cn">PersistentDataType</span>.SHORT
<span class="cn">PersistentDataType</span>.BYTE
<span class="cn">PersistentDataType</span>.BYTE_ARRAY
<span class="cn">PersistentDataType</span>.INTEGER_ARRAY
<span class="cn">PersistentDataType</span>.LONG_ARRAY
<span class="cn">PersistentDataType</span>.TAG_CONTAINER    <span class="cm">// nested PDC — for complex structures</span>

<span class="cm">// Nested containers</span>
<span class="cn">PersistentDataContainer</span> nested = pdc.getAdapterContext().newPersistentDataContainer();
nested.set(<span class="kw">new</span> <span class="cn">NamespacedKey</span>(plugin, <span class="st">"level"</span>), <span class="cn">PersistentDataType</span>.INTEGER, <span class="nm">5</span>);
pdc.set(<span class="kw">new</span> <span class="cn">NamespacedKey</span>(plugin, <span class="st">"stats"</span>), <span class="cn">PersistentDataType</span>.TAG_CONTAINER, nested);</pre></div></div>
  </div>
</section>

<!-- ═══ SQLITE ═══ -->
<section class="section" id="sqlite">
  <div class="section-title">🗄️ SQLite <span class="badge">DATABASE</span></div>
  <div class="warn"><strong>⚠ Always run database operations async!</strong> SQLite is built into the JVM — no extra dependency needed. Blocking the main thread with DB queries will lag the server.</div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Connection Setup & Table Creation</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">private</span> <span class="cn">Connection</span> conn;

<span class="kw">private void</span> <span class="fn">setupDatabase</span>() <span class="kw">throws</span> <span class="cn">Exception</span> {
    <span class="cn">File</span> dbFile = <span class="kw">new</span> <span class="cn">File</span>(getDataFolder(), <span class="st">"data.db"</span>);
    dbFile.getParentFile().mkdirs();
    conn = <span class="cn">DriverManager</span>.getConnection(<span class="st">"jdbc:sqlite:"</span> + dbFile.getAbsolutePath());
    conn.createStatement().execute(
        <span class="st">"CREATE TABLE IF NOT EXISTS players ("</span> +
        <span class="st">"  uuid TEXT PRIMARY KEY,"</span> +
        <span class="st">"  name TEXT NOT NULL,"</span> +
        <span class="st">"  kills INTEGER DEFAULT 0,"</span> +
        <span class="st">"  deaths INTEGER DEFAULT 0,"</span> +
        <span class="st">"  coins REAL DEFAULT 0.0,"</span> +
        <span class="st">"  last_seen INTEGER)"</span>);
    getLogger().info(<span class="st">"Database connected."</span>);
}

<span class="cm">// Close on disable</span>
<span class="kw">if</span> (conn != <span class="kw">null</span> && !conn.isClosed()) conn.close();</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Insert, Update & Query</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Insert or overwrite (duplicate primary key)</span>
<span class="cn">PreparedStatement</span> ps = conn.prepareStatement(
    <span class="st">"INSERT OR REPLACE INTO players (uuid, name, kills, coins) VALUES (?,?,?,?)"</span>);
ps.setString(<span class="nm">1</span>, player.getUniqueId().toString());
ps.setString(<span class="nm">2</span>, player.getName());
ps.setInt(<span class="nm">3</span>, kills);
ps.setDouble(<span class="nm">4</span>, coins);
ps.executeUpdate();

<span class="cm">// Update only</span>
<span class="cn">PreparedStatement</span> up = conn.prepareStatement(
    <span class="st">"UPDATE players SET kills=?, coins=? WHERE uuid=?"</span>);
up.setInt(<span class="nm">1</span>, kills); up.setDouble(<span class="nm">2</span>, coins);
up.setString(<span class="nm">3</span>, player.getUniqueId().toString());
up.executeUpdate();

<span class="cm">// Query a single player</span>
<span class="cn">PreparedStatement</span> qs = conn.prepareStatement(
    <span class="st">"SELECT kills, coins FROM players WHERE uuid=?"</span>);
qs.setString(<span class="nm">1</span>, player.getUniqueId().toString());
<span class="cn">ResultSet</span> rs = qs.executeQuery();
<span class="kw">if</span> (rs.next()) {
    <span class="kw">int</span>    kills = rs.getInt(<span class="st">"kills"</span>);
    <span class="kw">double</span> coins = rs.getDouble(<span class="st">"coins"</span>);
}

<span class="cm">// Leaderboard (top 10 by kills)</span>
<span class="cn">ResultSet</span> top = conn.createStatement().executeQuery(
    <span class="st">"SELECT name, kills FROM players ORDER BY kills DESC LIMIT 10"</span>);
<span class="kw">while</span> (top.next()) {
    <span class="cn">String</span> name = top.getString(<span class="st">"name"</span>);
    <span class="kw">int</span>    k    = top.getInt(<span class="st">"kills"</span>);
}

<span class="cm">// Always run DB code async!</span>
<span class="cn">Bukkit</span>.getScheduler().runTaskAsynchronously(plugin, () -> {
    savePlayerData(player);
});</pre></div></div>
  </div>
</section>

<!-- ═══ TIPS ═══ -->
<section class="section" id="tips">
  <div class="section-title">💡 Tips <span class="badge">BEST PRACTICES</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">UUID vs Player Name</div><div class="card-desc">Always use UUID for storing player data — names can change, UUIDs never do.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">UUID</span> uuid    = player.getUniqueId();
<span class="cn">String</span> uuidStr = uuid.toString();   <span class="cm">// "550e8400-e29b-41d4-..."</span>
<span class="cn">UUID</span> back     = <span class="cn">UUID</span>.fromString(uuidStr);

<span class="cm">// Offline player (can access even if not online)</span>
<span class="cn">OfflinePlayer</span> op = <span class="cn">Bukkit</span>.getOfflinePlayer(uuid);
op.getName(); op.hasPlayedBefore(); op.getLastPlayed();
<span class="cm">// ✦ NEVER use Bukkit.getOfflinePlayer(String name) in production!</span>
<span class="cm">// It makes a slow Mojang web request. Always use UUID.</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Cooldown System Using a Map</div><div class="card-desc">Track cooldowns with a UUID → timestamp map. Uses ConcurrentHashMap for thread safety.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">private final</span> <span class="cn">Map</span>&lt;<span class="cn">UUID</span>, <span class="cn">Long</span>&gt; cooldowns = <span class="kw">new</span> <span class="cn">ConcurrentHashMap</span>&lt;&gt;();
<span class="kw">private final long</span> COOLDOWN_MS = <span class="nm">5000L</span>; <span class="cm">// 5 seconds</span>

<span class="kw">public boolean</span> <span class="fn">isOnCooldown</span>(<span class="cn">Player</span> p) {
    <span class="cn">Long</span> last = cooldowns.get(p.getUniqueId());
    <span class="kw">return</span> last != <span class="kw">null</span> && <span class="cn">System</span>.currentTimeMillis() - last < COOLDOWN_MS;
}

<span class="kw">public long</span> <span class="fn">getRemainingMs</span>(<span class="cn">Player</span> p) {
    <span class="cn">Long</span> last = cooldowns.get(p.getUniqueId());
    <span class="kw">if</span> (last == <span class="kw">null</span>) <span class="kw">return</span> <span class="nm">0</span>;
    <span class="kw">return</span> <span class="cn">Math</span>.max(<span class="nm">0</span>, COOLDOWN_MS - (<span class="cn">System</span>.currentTimeMillis() - last));
}

<span class="kw">public void</span> <span class="fn">setCooldown</span>(<span class="cn">Player</span> p) { cooldowns.put(p.getUniqueId(), <span class="cn">System</span>.currentTimeMillis()); }
<span class="kw">public void</span> <span class="fn">clearCooldown</span>(<span class="cn">Player</span> p) { cooldowns.remove(p.getUniqueId()); }

<span class="cm">// Usage</span>
<span class="kw">if</span> (isOnCooldown(player)) {
    <span class="kw">long</span> rem = getRemainingMs(player);
    player.sendMessage(<span class="st">"§cCooldown: §f"</span> + <span class="cn">String</span>.format(<span class="st">"%.1f"</span>, rem/<span class="nm">1000.0</span>) + <span class="st">"s"</span>);
    <span class="kw">return</span>;
}
setCooldown(player);
<span class="cm">// ... do the action</span></pre></div></div>
  </div>
</section>

<!-- ═══ SOUNDS ═══ -->
<section class="section" id="sounds">
  <div class="section-title">🔊 Sounds <span class="badge">AUDIO</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Playing & Stopping Sounds</div><div class="card-desc">Volume: 0.0 (silent) to 1.0 (full). Pitch: 0.5 (deep/slow) to 1.0 (normal) to 2.0 (high/fast).</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// Player-only (only that player hears it)</span>
player.playSound(player.getLocation(), <span class="cn">Sound</span>.ENTITY_PLAYER_LEVELUP, <span class="nm">1f</span>, <span class="nm">1f</span>);
<span class="cm">//              location               sound                          vol  pitch</span>

<span class="cm">// Everyone in earshot hears it</span>
world.playSound(location, <span class="cn">Sound</span>.ENTITY_LIGHTNING_BOLT_THUNDER, <span class="nm">1f</span>, <span class="nm">1f</span>);

<span class="cm">// With SoundCategory</span>
player.playSound(loc, <span class="cn">Sound</span>.UI_BUTTON_CLICK, <span class="cn">SoundCategory</span>.MASTER, <span class="nm">1f</span>, <span class="nm">1f</span>);

<span class="cm">// Custom resource pack sound</span>
player.playSound(loc, <span class="st">"myplugin:custom.ability"</span>, <span class="nm">1f</span>, <span class="nm">1f</span>);

<span class="cm">// Stop sounds</span>
player.stopSound(<span class="cn">Sound</span>.MUSIC_DISC_CAT);
player.stopAllSounds();</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Pitch Values Guide</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table style="font-size:12px;">
          <tr><th>Pitch</th><th>Sound Effect</th><th>Pitch</th><th>Sound Effect</th></tr>
          <tr><td>0.5</td><td style="color:var(--muted)">Very deep / slow</td><td>1.25</td><td style="color:var(--muted)">Slightly high</td></tr>
          <tr><td>0.75</td><td style="color:var(--muted)">Low / dark</td><td>1.5</td><td style="color:var(--muted)">High / fast</td></tr>
          <tr><td>1.0</td><td style="color:var(--muted)">Normal (default)</td><td>1.75</td><td style="color:var(--muted)">Very high</td></tr>
          <tr><td>1.1</td><td style="color:var(--muted)">Slightly higher</td><td>2.0</td><td style="color:var(--muted)">Maximum — fastest / highest</td></tr>
        </table>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Common Sounds Reference</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table class="plain" style="font-size:12px;">
          <tr><th>Sound</th><th>Best Used For</th></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">UI_BUTTON_CLICK</td><td>GUI button clicks — perfect for menus</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">BLOCK_NOTE_BLOCK_PLING</td><td>Successful action, ping sound</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_PLAYER_LEVELUP</td><td>Achievement, reward, win</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">BLOCK_ANVIL_USE</td><td>Heavy / metallic confirmation</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_VILLAGER_TRADE</td><td>Purchase confirmation</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_EXPERIENCE_ORB_PICKUP</td><td>XP gain, small reward</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">BLOCK_CHEST_OPEN / CLOSE</td><td>Menu open / close</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_ARROW_HIT_PLAYER</td><td>Hit confirmation</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_ENDER_DRAGON_GROWL</td><td>Boss roar, dramatic event</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_FIREWORK_ROCKET_LAUNCH</td><td>Celebration</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_LIGHTNING_BOLT_THUNDER</td><td>Power, electric ability</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">BLOCK_BEACON_ACTIVATE</td><td>Shield / power-up activate</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_WITHER_SPAWN</td><td>Dark / ominous warning</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">BLOCK_ENCHANTMENT_TABLE_USE</td><td>Magic ability, enchanting</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_ENDERMAN_TELEPORT</td><td>Teleport effect</td></tr>
          <tr><td style="font-family:monospace;color:#8be9fd;font-size:11px;">ENTITY_ELDER_GUARDIAN_CURSE</td><td>Debuff applied</td></tr>
        </table>
      </div>
    </div>
  </div>
</section>

<!-- ═══ ADVANCED ═══ -->
<section class="section" id="advanced">
  <div class="section-title">🚀 Advanced Patterns <span class="badge">POWER FEATURES</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">BossBar</div><div class="card-desc">A progress bar at the top of the screen with a title. Great for events, timers, and raids.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">BossBar</span> bar = <span class="cn">Bukkit</span>.createBossBar(
    <span class="st">"§6§lEvent Name"</span>,
    <span class="cn">BarColor</span>.YELLOW,
    <span class="cn">BarStyle</span>.SEGMENTED_10
);
<span class="cm">// Colors: PINK BLUE RED GREEN YELLOW PURPLE WHITE</span>
<span class="cm">// Styles: SOLID SEGMENTED_6 SEGMENTED_10 SEGMENTED_12 SEGMENTED_20</span>

bar.setProgress(<span class="nm">0.75</span>);         <span class="cm">// 0.0 to 1.0</span>
bar.setTitle(<span class="st">"§a75% Complete"</span>);
bar.setColor(<span class="cn">BarColor</span>.GREEN);
bar.addPlayer(player);          <span class="cm">// show to player</span>
bar.removePlayer(player);
bar.setVisible(<span class="kw">true</span>);
bar.removeAll();                <span class="cm">// clear all players</span>

<span class="cm">// Countdown timer with BossBar</span>
<span class="kw">final int</span>[] t = {<span class="nm">200</span>}; <span class="cm">// 10 seconds * 20 ticks</span>
<span class="cn">BossBar</span> cBar = <span class="cn">Bukkit</span>.createBossBar(<span class="st">"§eStarting..."</span>, <span class="cn">BarColor</span>.YELLOW, <span class="cn">BarStyle</span>.SOLID);
<span class="kw">for</span> (<span class="cn">Player</span> p : players) cBar.addPlayer(p);
<span class="kw">new</span> <span class="cn">BukkitRunnable</span>() {
    <span class="an">@Override</span> <span class="kw">public void</span> <span class="fn">run</span>() {
        t[<span class="nm">0</span>]--;
        cBar.setProgress(t[<span class="nm">0</span>] / <span class="nm">200.0</span>);
        cBar.setTitle(<span class="st">"§eStarting in: §f"</span> + (t[<span class="nm">0</span>]/<span class="nm">20</span>) + <span class="st">"s"</span>);
        <span class="kw">if</span> (t[<span class="nm">0</span>] <= <span class="nm">0</span>) { cBar.removeAll(); <span class="kw">this</span>.cancel(); }
    }
}.runTaskTimer(plugin, <span class="nm">0L</span>, <span class="nm">1L</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">ActionBar & Title</div><div class="card-desc">ActionBar = text above the hotbar. Title = full-screen overlay text.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">// ActionBar — one-shot</span>
player.sendActionBar(<span class="st">"§ePvP Zone!"</span>);

<span class="cm">// Persistent ActionBar — re-send every 2 seconds or it fades</span>
<span class="kw">new</span> <span class="cn">BukkitRunnable</span>() {
    <span class="an">@Override</span> <span class="kw">public void</span> <span class="fn">run</span>() {
        <span class="kw">if</span> (!player.isOnline()) { <span class="kw">this</span>.cancel(); <span class="kw">return</span>; }
        player.sendActionBar(
            <span class="st">"§c❤ "</span> + (<span class="kw">int</span>) player.getHealth() +
            <span class="st">"  §a■ "</span> + player.getFoodLevel()
        );
    }
}.runTaskTimer(plugin, <span class="nm">0L</span>, <span class="nm">20L</span>);

<span class="cm">// Title — full-screen text</span>
player.sendTitle(<span class="st">"§6§lYOU WIN!"</span>, <span class="st">"§eKills: "</span> + kills, <span class="nm">10</span>, <span class="nm">60</span>, <span class="nm">20</span>);
<span class="cm">// (title, subtitle, fadeIn ticks, stay ticks, fadeOut ticks)</span>
player.resetTitle(); <span class="cm">// clear title</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Scoreboard / Sidebar</div><div class="card-desc">The sidebar list on the right side of the screen. Higher score = higher position.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">Scoreboard</span> board = <span class="cn">Bukkit</span>.getScoreboardManager().getNewScoreboard();
<span class="cn">Objective</span> obj = board.registerNewObjective(<span class="st">"sidebar"</span>, <span class="st">"dummy"</span>, <span class="st">"§6§lMy Server"</span>);
obj.setDisplaySlot(<span class="cn">DisplaySlot</span>.SIDEBAR);

<span class="cm">// Lines — higher score = higher position on sidebar</span>
<span class="cm">// Use unique spacing strings for blank lines (duplicates collapse)</span>
obj.getScore(<span class="st">"§7"</span> + player.getWorld().getName()).setScore(<span class="nm">8</span>);
obj.getScore(<span class="st">"§8——————————————"</span>).setScore(<span class="nm">7</span>);
obj.getScore(<span class="st">"§eKills: §f"</span> + kills).setScore(<span class="nm">6</span>);
obj.getScore(<span class="st">"§cDeaths: §f"</span> + deaths).setScore(<span class="nm">5</span>);
obj.getScore(<span class="st">"§b§8——————————————"</span>).setScore(<span class="nm">4</span>);
obj.getScore(<span class="st">"§aCoins: §f"</span> + coins).setScore(<span class="nm">3</span>);
obj.getScore(<span class="st">"§7§8——————————————"</span>).setScore(<span class="nm">2</span>);
obj.getScore(<span class="st">"§7play.myserver.com"</span>).setScore(<span class="nm">1</span>);

player.setScoreboard(board);

<span class="cm">// Update a line (must remove old then re-add)</span>
board.resetScores(<span class="st">"§eKills: §f"</span> + oldKills);
obj.getScore(<span class="st">"§eKills: §f"</span> + newKills).setScore(<span class="nm">6</span>);</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Teams</div><div class="card-desc">Group players into named teams with prefixes, colors, and friendly fire settings.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">Scoreboard</span> board = player.getScoreboard();
<span class="cn">Team</span> red  = board.registerNewTeam(<span class="st">"red_team"</span>);
<span class="cn">Team</span> blue = board.registerNewTeam(<span class="st">"blue_team"</span>);

red.setDisplayName(<span class="st">"§cRed Team"</span>);
red.setPrefix(<span class="st">"§c[RED] §f"</span>);
red.setSuffix(<span class="st">" §c✦"</span>);
red.setColor(<span class="cn">ChatColor</span>.RED);
red.setAllowFriendlyFire(<span class="kw">false</span>);
red.setCanSeeFriendlyInvisibles(<span class="kw">true</span>);

red.addEntry(player.getName());    <span class="cm">// add to team</span>
red.removeEntry(player.getName()); <span class="cm">// remove</span>
red.unregister();                  <span class="cm">// remove the whole team</span>

<span class="cm">// Check which team a player is on</span>
<span class="cn">Team</span> team = board.getEntryTeam(player.getName()); <span class="cm">// null if no team</span></pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Math Utilities</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cn">Math</span>.abs(-<span class="nm">5</span>)        <span class="cm">// 5    — absolute value</span>
<span class="cn">Math</span>.max(<span class="nm">3</span>, <span class="nm">7</span>)       <span class="cm">// 7    — larger of two</span>
<span class="cn">Math</span>.min(<span class="nm">3</span>, <span class="nm">7</span>)       <span class="cm">// 3    — smaller of two</span>
<span class="cn">Math</span>.pow(<span class="nm">2</span>, <span class="nm">8</span>)       <span class="cm">// 256.0 — exponent</span>
<span class="cn">Math</span>.sqrt(<span class="nm">16</span>)        <span class="cm">// 4.0  — square root</span>
<span class="cn">Math</span>.floor(<span class="nm">4.9</span>)      <span class="cm">// 4.0  — round down</span>
<span class="cn">Math</span>.ceil(<span class="nm">4.1</span>)       <span class="cm">// 5.0  — round up</span>
<span class="cn">Math</span>.round(<span class="nm">4.5</span>)      <span class="cm">// 5    — round to nearest</span>

<span class="cm">// Clamp (keep value within range)</span>
<span class="kw">double</span> clamped = <span class="cn">Math</span>.max(<span class="nm">0.0</span>, <span class="cn">Math</span>.min(value, <span class="nm">20.0</span>));

<span class="cm">// Lerp (linear interpolation — smooth movement)</span>
<span class="kw">double</span> <span class="fn">lerp</span>(<span class="kw">double</span> a, <span class="kw">double</span> b, <span class="kw">double</span> t) { <span class="kw">return</span> a + (b - a) * t; }
<span class="cm">// lerp(0, 100, 0.5) = 50.0</span>

<span class="cm">// Random</span>
<span class="cn">Random</span> rand = <span class="kw">new</span> <span class="cn">Random</span>();
rand.nextInt(<span class="nm">6</span>);          <span class="cm">// 0–5</span>
rand.nextInt(<span class="nm">6</span>) + <span class="nm">1</span>;      <span class="cm">// 1–6 (dice roll)</span>
rand.nextDouble();          <span class="cm">// 0.0–1.0</span>
rand.nextBoolean();

<span class="cm">// ThreadLocalRandom — better for concurrent/async use</span>
<span class="cn">ThreadLocalRandom</span>.current().nextInt(<span class="nm">1</span>, <span class="nm">101</span>); <span class="cm">// 1–100</span></pre></div></div>
  </div>
</section>

<!-- ═══ PLUGIN STRUCTURE ═══ -->
<section class="section" id="plugin-structure">
  <div class="section-title">🏗️ Plugin Structure <span class="badge">PROJECT SETUP</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Main Plugin Class</div><div class="card-desc">The entry point for every plugin. Extends JavaPlugin and has onEnable() / onDisable() lifecycle methods.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="kw">public class</span> <span class="cn">MyPlugin</span> <span class="kw">extends</span> <span class="cn">JavaPlugin</span> {
    <span class="kw">private static</span> <span class="cn">MyPlugin</span> instance; <span class="cm">// singleton for access anywhere</span>

    <span class="an">@Override</span>
    <span class="kw">public void</span> <span class="fn">onEnable</span>() {
        instance = <span class="kw">this</span>;

        <span class="cm">// 1. Create data folder / save default config</span>
        saveDefaultConfig();

        <span class="cm">// 2. Register listeners</span>
        getServer().getPluginManager().registerEvents(<span class="kw">new</span> <span class="cn">PlayerListener</span>(<span class="kw">this</span>), <span class="kw">this</span>);
        getServer().getPluginManager().registerEvents(<span class="kw">new</span> <span class="cn">GUIListener</span>(<span class="kw">this</span>), <span class="kw">this</span>);

        <span class="cm">// 3. Register commands</span>
        <span class="cn">Objects</span>.requireNonNull(getCommand(<span class="st">"mycmd"</span>)).setExecutor(<span class="kw">new</span> <span class="cn">MyCommand</span>(<span class="kw">this</span>));

        <span class="cm">// 4. Start scheduled tasks (e.g. auto-save every 5 min)</span>
        <span class="cn">Bukkit</span>.getScheduler().runTaskTimerAsynchronously(<span class="kw">this</span>, () -> {
            saveAllData();
        }, <span class="nm">6000L</span>, <span class="nm">6000L</span>);

        getLogger().info(<span class="st">"§aMyPlugin enabled! v"</span> + getDescription().getVersion());
    }

    <span class="an">@Override</span>
    <span class="kw">public void</span> <span class="fn">onDisable</span>() {
        saveAllData();  <span class="cm">// save before shutdown</span>
        <span class="cn">Bukkit</span>.getScheduler().cancelTasks(<span class="kw">this</span>); <span class="cm">// cancel all tasks</span>
        getLogger().info(<span class="st">"§cMyPlugin disabled."</span>);
    }

    <span class="kw">public static</span> <span class="cn">MyPlugin</span> <span class="fn">getInstance</span>() { <span class="kw">return</span> instance; }
}</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">plugin.yml — Full Example</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre>name: MyPlugin
version: <span class="st">"${project.version}"</span>       <span class="cm"># Maven auto-fills from pom.xml</span>
main: com.example.myplugin.MyPlugin
api-version: <span class="st">"1.21"</span>               <span class="cm"># minimum Paper API version</span>
description: <span class="st">"My awesome plugin"</span>
author: YourName
authors: [YourName, Contributor]
website: <span class="st">"https://example.com"</span>

depend: [Vault]         <span class="cm"># hard dependency — plugin fails without it</span>
softdepend: [PlaceholderAPI]  <span class="cm"># soft — loads after if present</span>
loadbefore: [OtherPlugin]     <span class="cm"># this plugin loads before OtherPlugin</span>

commands:
  mycmd:
    description: <span class="st">"My main command"</span>
    usage: <span class="st">"/<command> <subcommand>"</span>
    permission: myplugin.use

permissions:
  myplugin.*:
    description: <span class="st">"All permissions"</span>
    children:
      myplugin.use: <span class="kw">true</span>
      myplugin.admin: <span class="kw">true</span>
  myplugin.use:
    description: <span class="st">"Use the plugin"</span>
    default: <span class="kw">true</span>
  myplugin.admin:
    description: <span class="st">"Admin features"</span>
    default: op</pre></div></div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">pom.xml — Maven Setup</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body"><div class="code-wrap"><button class="copy-btn" onclick="copyCode(this)">copy</button><pre><span class="cm">&lt;!-- Repository --&gt;</span>
&lt;repository&gt;
  &lt;id&gt;papermc&lt;/id&gt;
  &lt;url&gt;https://repo.papermc.io/repository/maven-public/&lt;/url&gt;
&lt;/repository&gt;

<span class="cm">&lt;!-- Paper API dependency — provided at runtime by server --&gt;</span>
&lt;dependency&gt;
  &lt;groupId&gt;io.papermc.paper&lt;/groupId&gt;
  &lt;artifactId&gt;paper-api&lt;/artifactId&gt;
  &lt;version&gt;1.21.4-R0.1-SNAPSHOT&lt;/version&gt;
  &lt;scope&gt;provided&lt;/scope&gt;
&lt;/dependency&gt;

<span class="cm">&lt;!-- Compiler — set to Java 21 --&gt;</span>
&lt;plugin&gt;
  &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;
  &lt;artifactId&gt;maven-compiler-plugin&lt;/artifactId&gt;
  &lt;configuration&gt;
    &lt;source&gt;21&lt;/source&gt;
    &lt;target&gt;21&lt;/target&gt;
  &lt;/configuration&gt;
&lt;/plugin&gt;</pre></div></div>
  </div>
</section>

<!-- ═══ QUICK REFERENCE ═══ -->
<section class="section" id="quickref">
  <div class="section-title">📋 Quick Reference <span class="badge">REFERENCE</span></div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Minecraft Color & Format Codes</div><div class="card-desc">Use § prefix in chat/display names. For Paper 1.16+, use the Adventure API with Component.text() for more control.</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table style="font-size:12px;">
          <tr><th>Code</th><th>Color</th><th>Code</th><th>Color</th><th>Code</th><th>Format</th></tr>
          <tr><td>§0</td><td style="color:#000;background:#555;padding:2px 6px;">■ Black</td><td>§8</td><td style="color:#555;">■ Dark Gray</td><td>§l</td><td style="color:var(--muted)"><b>Bold</b></td></tr>
          <tr><td>§1</td><td style="color:#00a;">■ Dark Blue</td><td>§9</td><td style="color:#55f;">■ Blue</td><td>§o</td><td style="color:var(--muted)"><i>Italic</i></td></tr>
          <tr><td>§2</td><td style="color:#0a0;">■ Dark Green</td><td>§a</td><td style="color:#5f5;">■ Green</td><td>§n</td><td style="color:var(--muted);text-decoration:underline;">Underline</td></tr>
          <tr><td>§3</td><td style="color:#0aa;">■ Dark Aqua</td><td>§b</td><td style="color:#5ff;">■ Aqua</td><td>§m</td><td style="color:var(--muted);text-decoration:line-through;">Strike</td></tr>
          <tr><td>§4</td><td style="color:#a00;">■ Dark Red</td><td>§c</td><td style="color:#f55;">■ Red</td><td>§k</td><td style="color:var(--muted)">§k Obfuscated</td></tr>
          <tr><td>§5</td><td style="color:#a0a;">■ Dark Purple</td><td>§d</td><td style="color:#f5f;">■ Pink</td><td>§r</td><td style="color:var(--muted)">Reset all</td></tr>
          <tr><td>§6</td><td style="color:#fa0;">■ Gold</td><td>§e</td><td style="color:#ff5;">■ Yellow</td><td></td><td></td></tr>
          <tr><td>§7</td><td style="color:#aaa;">■ Gray</td><td>§f</td><td style="color:#fff;">■ White</td><td></td><td></td></tr>
        </table>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Common Mistakes & Fixes</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table class="plain" style="font-size:12px;">
          <tr><th>Mistake</th><th>Root Cause</th><th>Fix</th></tr>
          <tr><td>NullPointerException crash</td><td>Called method on null value</td><td>Always null-check: if (x != null)</td></tr>
          <tr><td>String comparison fails</td><td>Used == instead of .equals()</td><td>Always use .equals() or .equalsIgnoreCase()</td></tr>
          <tr><td>Command not working</td><td>Not registered in plugin.yml</td><td>Add block under "commands:" in plugin.yml</td></tr>
          <tr><td>NumberFormatException</td><td>parseInt on non-number string</td><td>Wrap in try { } catch (NumberFormatException e) { }</td></tr>
          <tr><td>Items stolen from GUI</td><td>Did not cancel InventoryClickEvent</td><td>Always call event.setCancelled(true) in GUI handler</td></tr>
          <tr><td>ItemMeta changes lost</td><td>Edited meta but never applied it</td><td>Always call item.setItemMeta(meta) after changes</td></tr>
          <tr><td>Server freezes on heavy task</td><td>Blocking code on main thread</td><td>Use runTaskAsynchronously() for blocking work</td></tr>
          <tr><td>Bukkit API crash in async</td><td>Called Bukkit API off main thread</td><td>Wrap Bukkit calls in runTask() inside the async block</td></tr>
          <tr><td>Data tied to wrong player</td><td>Stored by player name</td><td>Always use getUniqueId().toString() as key</td></tr>
          <tr><td>Config changes not saved</td><td>Called set() but not saveConfig()</td><td>Call saveConfig() after every set()</td></tr>
          <tr><td>Listener not firing</td><td>Forgot to register it</td><td>Call registerEvents(new MyListener(this), this) in onEnable()</td></tr>
          <tr><td>getKiller() crash</td><td>Null when entity dies from environment</td><td>Player k = getKiller(); if (k == null) return;</td></tr>
          <tr><td>SkullMeta ClassCastException</td><td>Cast wrong meta type</td><td>Check: if (item.getType() == Material.PLAYER_HEAD)</td></tr>
          <tr><td>return false in onCommand()</td><td>Shows plugin.yml usage message</td><td>Return false ONLY for wrong usage, true otherwise</td></tr>
        </table>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Common Materials</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table class="plain" style="font-size:12px;">
          <tr><th>Category</th><th>Materials</th></tr>
          <tr><td>Swords</td><td>WOODEN_SWORD, STONE_SWORD, IRON_SWORD, GOLDEN_SWORD, DIAMOND_SWORD, NETHERITE_SWORD</td></tr>
          <tr><td>Pickaxes</td><td>WOODEN_PICKAXE, IRON_PICKAXE, DIAMOND_PICKAXE, NETHERITE_PICKAXE</td></tr>
          <tr><td>Axes</td><td>WOODEN_AXE, IRON_AXE, DIAMOND_AXE, NETHERITE_AXE</td></tr>
          <tr><td>Helmets</td><td>LEATHER_HELMET, CHAINMAIL_HELMET, IRON_HELMET, DIAMOND_HELMET, NETHERITE_HELMET</td></tr>
          <tr><td>Chestplates</td><td>LEATHER_CHESTPLATE, IRON_CHESTPLATE, DIAMOND_CHESTPLATE, NETHERITE_CHESTPLATE</td></tr>
          <tr><td>Food</td><td>APPLE, BREAD, COOKED_BEEF, GOLDEN_APPLE, ENCHANTED_GOLDEN_APPLE, COOKED_CHICKEN</td></tr>
          <tr><td>Blocks</td><td>STONE, GRASS_BLOCK, DIRT, SAND, OAK_LOG, DIAMOND_BLOCK, GOLD_BLOCK, IRON_BLOCK</td></tr>
          <tr><td>Ores</td><td>DIAMOND_ORE, IRON_ORE, GOLD_ORE, COAL_ORE, EMERALD_ORE, DEEPSLATE_DIAMOND_ORE</td></tr>
          <tr><td>Glass Panes</td><td>WHITE_STAINED_GLASS_PANE, GRAY_STAINED_GLASS_PANE, RED_STAINED_GLASS_PANE, LIME_STAINED_GLASS_PANE</td></tr>
          <tr><td>Heads</td><td>PLAYER_HEAD, ZOMBIE_HEAD, SKELETON_SKULL, WITHER_SKELETON_SKULL, CREEPER_HEAD</td></tr>
          <tr><td>GUI Misc</td><td>COMPASS, CLOCK, PAPER, BOOK, NAME_TAG, MAP, FILLED_MAP, KNOWLEDGE_BOOK</td></tr>
          <tr><td>Special</td><td>BARRIER, BEDROCK, COMMAND_BLOCK, STRUCTURE_VOID, LIGHT, SPAWNER, END_PORTAL_FRAME</td></tr>
          <tr><td>Air / Empty</td><td>AIR — used for empty slots. Check: item.getType() == Material.AIR</td></tr>
        </table>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Common Enchantments</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table style="font-size:12px;">
          <tr><th>Enchantment</th><th>Applies To</th><th>Max</th><th>Enchantment</th><th>Applies To</th><th>Max</th></tr>
          <tr><td>DAMAGE_ALL</td><td style="color:var(--muted)">Sword</td><td style="color:var(--muted)">V</td><td>PROTECTION_ENVIRONMENTAL</td><td style="color:var(--muted)">Armor</td><td style="color:var(--muted)">IV</td></tr>
          <tr><td>SHARPNESS</td><td style="color:var(--muted)">Sword/Axe</td><td style="color:var(--muted)">V</td><td>PROTECTION_FIRE</td><td style="color:var(--muted)">Armor</td><td style="color:var(--muted)">IV</td></tr>
          <tr><td>FIRE_ASPECT</td><td style="color:var(--muted)">Sword</td><td style="color:var(--muted)">II</td><td>FEATHER_FALLING</td><td style="color:var(--muted)">Boots</td><td style="color:var(--muted)">IV</td></tr>
          <tr><td>KNOCKBACK</td><td style="color:var(--muted)">Sword</td><td style="color:var(--muted)">II</td><td>DEPTH_STRIDER</td><td style="color:var(--muted)">Boots</td><td style="color:var(--muted)">III</td></tr>
          <tr><td>LOOTING</td><td style="color:var(--muted)">Sword</td><td style="color:var(--muted)">III</td><td>THORNS</td><td style="color:var(--muted)">Armor</td><td style="color:var(--muted)">III</td></tr>
          <tr><td>POWER</td><td style="color:var(--muted)">Bow</td><td style="color:var(--muted)">V</td><td>EFFICIENCY</td><td style="color:var(--muted)">Tools</td><td style="color:var(--muted)">V</td></tr>
          <tr><td>FLAME</td><td style="color:var(--muted)">Bow</td><td style="color:var(--muted)">I</td><td>FORTUNE</td><td style="color:var(--muted)">Tools</td><td style="color:var(--muted)">III</td></tr>
          <tr><td>INFINITY</td><td style="color:var(--muted)">Bow</td><td style="color:var(--muted)">I</td><td>SILK_TOUCH</td><td style="color:var(--muted)">Tools</td><td style="color:var(--muted)">I</td></tr>
          <tr><td>MENDING</td><td style="color:var(--muted)">Any</td><td style="color:var(--muted)">I</td><td>UNBREAKING</td><td style="color:var(--muted)">Any</td><td style="color:var(--muted)">III</td></tr>
        </table>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">Potion Effects Reference</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table style="font-size:12px;">
          <tr><th>PotionEffectType</th><th>Effect</th><th>PotionEffectType</th><th>Effect</th></tr>
          <tr><td>SPEED</td><td style="color:var(--muted)">Movement speed+</td><td>SLOW</td><td style="color:var(--muted)">Movement speed-</td></tr>
          <tr><td>FAST_DIGGING</td><td style="color:var(--muted)">Haste (mining+)</td><td>SLOW_DIGGING</td><td style="color:var(--muted)">Mining fatigue</td></tr>
          <tr><td>INCREASE_DAMAGE</td><td style="color:var(--muted)">Strength</td><td>WEAKNESS</td><td style="color:var(--muted)">Attack damage-</td></tr>
          <tr><td>JUMP</td><td style="color:var(--muted)">Jump boost</td><td>LEVITATION</td><td style="color:var(--muted)">Float upward</td></tr>
          <tr><td>REGENERATION</td><td style="color:var(--muted)">Health regen</td><td>POISON</td><td style="color:var(--muted)">Periodic damage</td></tr>
          <tr><td>DAMAGE_RESISTANCE</td><td style="color:var(--muted)">Resistance</td><td>WITHER</td><td style="color:var(--muted)">Wither damage</td></tr>
          <tr><td>FIRE_RESISTANCE</td><td style="color:var(--muted)">Fire immunity</td><td>HUNGER</td><td style="color:var(--muted)">Hunger drain</td></tr>
          <tr><td>WATER_BREATHING</td><td style="color:var(--muted)">Breathe water</td><td>SATURATION</td><td style="color:var(--muted)">Food restore</td></tr>
          <tr><td>INVISIBILITY</td><td style="color:var(--muted)">Invisible</td><td>BLINDNESS</td><td style="color:var(--muted)">Screen darken</td></tr>
          <tr><td>NIGHT_VISION</td><td style="color:var(--muted)">See in dark</td><td>ABSORPTION</td><td style="color:var(--muted)">Yellow hearts</td></tr>
          <tr><td>HEALTH_BOOST</td><td style="color:var(--muted)">Extra hearts</td><td>GLOWING</td><td style="color:var(--muted)">Outline glow</td></tr>
        </table>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header" onclick="toggleCard(this)">
      <div><div class="card-label">EntityType Quick Reference</div></div>
      <span class="card-toggle">+</span>
    </div>
    <div class="card-body">
      <div class="tbl-wrap" style="padding:16px 18px 4px;">
        <table style="font-size:12px;">
          <tr><th>Passive</th><th>Neutral</th><th>Hostile</th><th>Boss / Special</th></tr>
          <tr><td>COW</td><td>WOLF</td><td>ZOMBIE</td><td>ENDER_DRAGON</td></tr>
          <tr><td>PIG</td><td>SPIDER</td><td>SKELETON</td><td>WITHER</td></tr>
          <tr><td>SHEEP</td><td>CAVE_SPIDER</td><td>CREEPER</td><td>ELDER_GUARDIAN</td></tr>
          <tr><td>CHICKEN</td><td>ENDERMAN</td><td>WITCH</td><td>WARDEN</td></tr>
          <tr><td>HORSE</td><td>POLAR_BEAR</td><td>BLAZE</td><td>IRON_GOLEM</td></tr>
          <tr><td>VILLAGER</td><td>BEE</td><td>GHAST</td><td>SNOW_GOLEM</td></tr>
          <tr><td>RABBIT</td><td>PANDA</td><td>PHANTOM</td><td>ARMOR_STAND</td></tr>
          <tr><td>TURTLE</td><td>GOAT</td><td>PILLAGER</td><td>FALLING_BLOCK</td></tr>
          <tr><td>AXOLOTL</td><td>DOLPHIN</td><td>GUARDIAN</td><td>AREA_EFFECT_CLOUD</td></tr>
          <tr><td>ALLAY</td><td>LLAMA</td><td>RAVAGER</td><td>ITEM_DISPLAY</td></tr>
        </table>
      </div>
    </div>
  </div>
</section>

  </div><!-- /content -->
</main>

<script>
function toggleCard(header) {
  const card = header.closest('.card');
  card.classList.toggle('open');
}

function copyCode(btn) {
  const pre = btn.nextElementSibling;
  navigator.clipboard.writeText(pre.innerText).then(() => {
    btn.textContent = 'copied!';
    btn.classList.add('copied');
    setTimeout(() => { btn.textContent = 'copy'; btn.classList.remove('copied'); }, 1800);
  });
}

// Search
const search = document.getElementById('search');
const noResults = document.getElementById('no-results');
search.addEventListener('input', () => {
  const q = search.value.toLowerCase().trim();
  const sections = document.querySelectorAll('.section');
  let any = false;
  sections.forEach(sec => {
    if (!q) { sec.style.display = ''; any = true; return; }
    const show = sec.innerText.toLowerCase().includes(q);
    sec.style.display = show ? '' : 'none';
    if (show) any = true;
  });
  noResults.style.display = any ? 'none' : 'block';
});

// Active nav on scroll
const navLinks = document.querySelectorAll('.nav-item');
const observer = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      navLinks.forEach(l => l.classList.remove('active'));
      const link = document.querySelector(`.nav-item[href="#${entry.target.id}"]`);
      if (link) link.classList.add('active');
    }
  });
}, { threshold: 0.15 });
document.querySelectorAll('.section').forEach(s => observer.observe(s));
</script>
</body>
</html>
HTMLEOF
echo "Done! File size: $(wc -c < /mnt/user-data/outputs/logos-java-cheatsheet.html) bytes"
