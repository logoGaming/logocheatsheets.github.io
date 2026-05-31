  Logo's Java Plugin Cheat Sheet :root { --bg: #0f1117; --bg2: #1a1d27; --bg3: #22263a; --border: #2e3250; --accent: #7c6aff; --accent2: #00d4a0; --text: #e8e8f0; --muted: #8888aa; --code-bg: #141720; --tag-bg: #2a2060; --tag-text: #a99fff; --sidebar-w: 250px; } \* { box-sizing: border-box; margin: 0; padding: 0; } body { font-family: 'Segoe UI', system-ui, sans-serif; background: var(--bg); color: var(--text); display: flex; min-height: 100vh; } /\* Sidebar \*/ #sidebar { width: var(--sidebar-w); min-width: var(--sidebar-w); background: var(--bg2); border-right: 1px solid var(--border); position: fixed; top: 0; left: 0; height: 100vh; overflow-y: auto; display: flex; flex-direction: column; } #sidebar-header { padding: 20px 16px 12px; border-bottom: 1px solid var(--border); } #sidebar-header h1 { font-size: 14px; font-weight: 700; color: var(--accent); letter-spacing: 0.5px; } #sidebar-header p { font-size: 11px; color: var(--muted); margin-top: 4px; } #sidebar nav { padding: 8px 0; flex: 1; } .nav-item { display: flex; align-items: center; gap: 8px; padding: 7px 16px; font-size: 12.5px; color: var(--muted); cursor: pointer; border-left: 2px solid transparent; transition: all 0.15s; text-decoration: none; } .nav-item:hover { color: var(--text); background: var(--bg3); } .nav-item.active { color: var(--accent); border-left-color: var(--accent); background: #1c1840; } .nav-icon { font-size: 13px; width: 16px; text-align: center; } /\* Main \*/ #main { margin-left: var(--sidebar-w); flex: 1; padding: 40px 48px; max-width: 980px; } /\* Search \*/ #search-wrap { margin-bottom: 32px; position: relative; } #search { width: 100%; background: var(--bg2); border: 1px solid var(--border); color: var(--text); border-radius: 8px; padding: 10px 16px 10px 40px; font-size: 14px; outline: none; } #search:focus { border-color: var(--accent); } #search-wrap::before { content: '⌕'; position: absolute; left: 14px; top: 50%; transform: translateY(-50%); color: var(--muted); font-size: 18px; pointer-events: none; } /\* Sections \*/ .section { margin-bottom: 56px; scroll-margin-top: 24px; } .section-title { font-size: 22px; font-weight: 700; color: var(--text); border-bottom: 1px solid var(--border); padding-bottom: 12px; margin-bottom: 24px; display: flex; align-items: center; gap: 10px; } .section-title .badge { font-size: 11px; background: var(--tag-bg); color: var(--tag-text); border-radius: 4px; padding: 2px 8px; font-weight: 600; letter-spacing: 0.4px; } /\* Cards \*/ .card { background: var(--bg2); border: 1px solid var(--border); border-radius: 10px; margin-bottom: 16px; overflow: hidden; } .card-header { padding: 14px 18px; display: flex; align-items: flex-start; justify-content: space-between; cursor: pointer; gap: 12px; } .card-header:hover { background: var(--bg3); } .card-label { font-size: 14px; font-weight: 600; color: var(--text); } .card-desc { font-size: 13px; color: var(--muted); margin-top: 4px; line-height: 1.5; } .card-toggle { color: var(--muted); font-size: 18px; line-height: 1; flex-shrink: 0; padding-top: 2px; transition: transform 0.2s; } .card.open .card-toggle { transform: rotate(45deg); } .card-body { display: none; border-top: 1px solid var(--border); } .card.open .card-body { display: block; } /\* Code \*/ .code-wrap { position: relative; } pre { background: var(--code-bg); padding: 16px 18px; margin: 0; font-family: 'Cascadia Code','Fira Code','Consolas',monospace; font-size: 12.5px; line-height: 1.7; overflow-x: auto; color: #c9d1d9; border-top: 1px solid var(--border); } .copy-btn { position: absolute; top: 8px; right: 8px; background: var(--bg3); border: 1px solid var(--border); color: var(--muted); border-radius: 5px; padding: 4px 10px; font-size: 11px; cursor: pointer; opacity: 0; transition: opacity 0.15s; } .code-wrap:hover .copy-btn { opacity: 1; } .copy-btn:hover { color: var(--text); } .copy-btn.copied { color: var(--accent2); border-color: var(--accent2); } /\* Syntax \*/ .kw { color: #ff79c6; } .cm { color: #6272a4; font-style: italic; } .st { color: #f1fa8c; } .nm { color: #bd93f9; } .fn { color: #50fa7b; } .cn { color: #8be9fd; } .an { color: #ffb86c; } .op { color: #ff79c6; } /\* Table \*/ .tbl-wrap { padding: 0 0 4px; overflow-x: auto; } table { width: 100%; border-collapse: collapse; font-size: 12.5px; } table td, table th { padding: 7px 12px; border: 1px solid var(--border); vertical-align: top; } table th { background: var(--bg3); color: var(--muted); font-weight: 600; font-size: 11.5px; text-align: left; } table td:first-child { font-family: 'Cascadia Code','Fira Code','Consolas',monospace; color: #8be9fd; white-space: nowrap; } table.plain td:first-child { font-family: inherit; color: var(--text); white-space: normal; } table.plain td:last-child { color: var(--muted); } table.color-chart td { font-family: 'Cascadia Code','Fira Code','Consolas',monospace; font-size: 12px; } /\* Note \*/ .note { background: #1a2040; border-left: 3px solid var(--accent); padding: 10px 14px; font-size: 13px; color: var(--muted); margin: 12px 18px; border-radius: 0 6px 6px 0; line-height: 1.6; } .note strong { color: var(--text); } .warn { background: #261a00; border-left: 3px solid #ffb86c; padding: 10px 14px; font-size: 13px; color: #ccaa60; margin: 12px 18px; border-radius: 0 6px 6px 0; line-height: 1.6; } .warn strong { color: #ffcc66; } /\* Slot grid \*/ .slot-grid { display: grid; grid-template-columns: repeat(9,1fr); gap: 3px; padding: 16px 18px; } .slot { background: var(--bg3); border: 1px solid var(--border); border-radius: 4px; text-align: center; font-size: 11px; font-family: 'Cascadia Code','Fira Code','Consolas',monospace; padding: 5px 2px; color: var(--muted); } .slot.border-slot { background: #1e1a3a; color: var(--accent); border-color: var(--accent); } /\* Color preview swatches \*/ .color-swatch { display: inline-block; width: 12px; height: 12px; border-radius: 2px; margin-right: 4px; vertical-align: middle; } /\* No results \*/ #no-results { display: none; text-align: center; padding: 60px 20px; color: var(--muted); } #no-results h2 { font-size: 20px; margin-bottom: 8px; } @media (max-width: 700px) { #sidebar { display: none; } #main { margin-left: 0; padding: 24px 20px; } }

# ☕ Logo's Cheat Sheet

PaperMC · Java 21 · Paper 1.21+

[📦 Imports](#imports) [⚙️ Core](#core) [🎯 Events](#events) [🗡️ Custom Items](#custom-items) [🗂️ GUI](#gui) [✨ Particles](#particles) [📘 Java Basics](#java-basics) [🌍 PaperMC Basics](#papermc-basics) [⏱️ Timers](#timers) [💬 Commands](#commands) [💾 Configs / Data](#configs) [🏷️ PDC](#pdc) [🗄️ SQLite](#sqlite) [💡 Tips](#tips) [🔊 Sounds](#sounds) [🚀 Advanced Patterns](#advanced) [🏗️ Plugin Structure](#plugin-structure) [📋 Quick Reference](#quickref)

## No results

Try a different search term.

📦 Imports BASICS

Common Imports

Tell Java where to find classes — without these, Java won't know what EventHandler, Player, etc. are.

+

copy

import org.bukkit.event.Listener;
import org.bukkit.event.EventHandler;
import org.bukkit.event.EventPriority;
import org.bukkit.plugin.java.JavaPlugin;
import org.bukkit.Bukkit;
import org.bukkit.entity.Player;
import org.bukkit.Material;
import org.bukkit.Location;
import org.bukkit.World;
import org.bukkit.inventory.Inventory;
import org.bukkit.inventory.ItemStack;
import org.bukkit.inventory.meta.ItemMeta;
import org.bukkit.Sound;
import org.bukkit.Particle;
import org.bukkit.scheduler.BukkitTask;
import org.bukkit.scheduler.BukkitRunnable;
import java.util.\*;

⚙️ Core SETUP

Register Events

Tells the server this class has event listeners. Without this, your @EventHandler methods never fire. Put this in onEnable().

+

copy

getServer().getPluginManager().registerEvents(this, this);

// Or with a separate listener class (recommended):
getServer().getPluginManager().registerEvents(new MyListener(this), this);

Register a Command

Link a command string to its executor class. Put this in onEnable().

+

copy

PluginCommand cmd = getCommand("starsmp");
if (cmd != null) {
    StarSMPCommand executor = new StarSMPCommand(this);
    cmd.setExecutor(executor);
    cmd.setTabCompleter(executor); // same class can handle tab complete
}

Access Plugin From Another Class

Gets a reference to your main plugin instance from anywhere in your code.

+

copy

// Option 1 — cast from Bukkit (works from anywhere)
SMPEssentials plugin = (SMPEssentials) Bukkit.getPluginManager().getPlugin("SMPEssentials");

// Option 2 — singleton pattern (recommended)
public class SMPEssentials extends JavaPlugin {
    private static SMPEssentials instance;
    @Override public void onEnable() { instance = this; }
    public static SMPEssentials getInstance() { return instance; }
}
// Then anywhere:
SMPEssentials.getInstance().someMethod();

Broadcast & Loop All Players

+

copy

// Broadcast to everyone at once
Bukkit.broadcastMessage("§aHello everyone!");

// Loop through all online players
for (Player player : Bukkit.getOnlinePlayers()) {
    if (player.getName().equals("Steve")) {
        player.sendMessage("Found you!");
    }
}

// With Java Streams (cleaner filtering)
Bukkit.getOnlinePlayers().stream()
    .filter(p -> p.hasPermission("admin"))
    .forEach(p -> p.sendMessage("§cAdmin alert!"));

🎯 Events LISTENERS

Listener Class Setup

The full pattern for a listener class. Register it in onEnable().

+

copy

public class MyListener implements Listener {
    private final MyPlugin plugin;
    public MyListener(MyPlugin plugin) { this.plugin = plugin; }

    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event) {
        Player player = event.getPlayer();
        event.setJoinMessage("§a» §f" + player.getName() + " §ajoined!");
        player.sendMessage("§aWelcome to the server!");
    }

    @EventHandler(priority = EventPriority.HIGH, ignoreCancelled = true)
    public void onBlockBreak(BlockBreakEvent event) {
        // ignoreCancelled = skip if another plugin cancelled it first
    }
}

Item Right-Click Detection

Always null-check getItem() — empty hand returns null and will crash without it.

+

copy

@EventHandler
public void onRightClick(PlayerInteractEvent event) {
    if (event.getAction() == Action.RIGHT\_CLICK\_BLOCK ||
        event.getAction() == Action.RIGHT\_CLICK\_AIR) {
        if (event.getItem() != null &&
            event.getItem().getType() == Material.DIAMOND\_SWORD) {
            event.getPlayer().sendMessage("You right-clicked with a Diamond Sword!");
        }
    }
}

Block Right-Click Detection

Check getClickedBlock() instead of item. Null check required — clicking in air has no clicked block.

+

copy

@EventHandler
public void onRightClick(PlayerInteractEvent event) {
    if (event.getAction() == Action.RIGHT\_CLICK\_BLOCK) {
        if (event.getClickedBlock() != null) {
            event.getPlayer().sendMessage("Block: " +
                event.getClickedBlock().getType().toString());
        }
    }
}

Events Quick Reference — 25+ Common Events

All the events you'll use most often, with their most useful methods.

+

| Event Class | When it fires | Key Methods |
| --- | --- | --- |
| PlayerJoinEvent | Player connects | getPlayer(), setJoinMessage() |
| PlayerQuitEvent | Player disconnects | getPlayer(), setQuitMessage() |
| PlayerMoveEvent | Player moves (every tick!) | getFrom(), getTo(), setTo(loc) |
| PlayerTeleportEvent | Player teleports | getFrom(), getTo(), getCause() |
| PlayerInteractEvent | Click / interact | getAction(), getItem(), getClickedBlock() |
| PlayerInteractEntityEvent | Right-click on entity | getPlayer(), getRightClicked() |
| PlayerDeathEvent | Player dies | getEntity(), setDeathMessage(), getDrops() |
| PlayerRespawnEvent | Player respawns | getPlayer(), setRespawnLocation() |
| EntityDeathEvent | Any entity dies | getEntity(), getEntity().getKiller(), getDrops() |
| EntityDamageEvent | Entity takes damage | getDamage(), setDamage(), getCause() |
| EntityDamageByEntityEvent | Damaged by an entity | getDamager(), getEntity(), getFinalDamage() |
| EntitySpawnEvent | Entity spawns | getEntity(), getLocation(), setCancelled() |
| AsyncPlayerChatEvent | Chat message (async!) | getPlayer(), getMessage(), setMessage() |
| PlayerCommandPreprocessEvent | Types a command | getPlayer(), getMessage(), setMessage() |
| InventoryClickEvent | Click in any inventory | getClickedInventory(), getCurrentItem(), getSlot(), getClick() |
| InventoryDragEvent | Drag items across slots | getNewItems(), getInventory(), setCancelled() |
| InventoryCloseEvent | Inventory closed | getPlayer(), getInventory() |
| BlockBreakEvent | Block broken by player | getPlayer(), getBlock(), setDropItems() |
| BlockPlaceEvent | Block placed by player | getPlayer(), getBlock(), getItemInHand() |
| ProjectileLaunchEvent | Projectile fired | getEntity(), setCancelled() |
| ProjectileHitEvent | Projectile lands | getEntity(), getHitEntity(), getHitBlock() |
| PlayerDropItemEvent | Player drops item (Q) | getPlayer(), getItemDrop() |
| PlayerPickupItemEvent | Player picks up item | getPlayer(), getItem(), setCancelled() |
| CreatureSpawnEvent | Mob spawns naturally | getEntity(), getSpawnReason(), setCancelled() |
| FoodLevelChangeEvent | Hunger changes | getEntity(), getFoodLevel(), setFoodLevel() |
| PlayerFishEvent | Fishing action | getPlayer(), getCaught(), getState() |

Event Priority & Cancellation

Controls the order your handler runs relative to other plugins. MONITOR is for observation only — never modify the event there.

+

copy

// Priority order — LOWEST runs first, MONITOR runs last
@EventHandler(priority = EventPriority.LOWEST)   // first — great for setup
@EventHandler(priority = EventPriority.LOW)
@EventHandler(priority = EventPriority.NORMAL)   // default
@EventHandler(priority = EventPriority.HIGH)
@EventHandler(priority = EventPriority.HIGHEST)
@EventHandler(priority = EventPriority.MONITOR)  // last, observation ONLY

// ignoreCancelled — skip if another plugin already cancelled it
@EventHandler(priority = EventPriority.NORMAL, ignoreCancelled = true)
public void onBreak(BlockBreakEvent event) { }

// Cancelling an event — stops the action from happening
event.setCancelled(true);
if (event.isCancelled()) return;

Critical Null Checks by Event

The most common crash causes in plugin dev. Always add these guards at the top of your handlers.

+

| Situation | Guard Code |
| --- | --- |
| GUI border click | if (event.getClickedInventory() == null) return; |
| Empty slot clicked | if (event.getCurrentItem() == null) return; |
| Item has no meta | ItemMeta m = item.getItemMeta(); if (m == null) return; |
| No player killer (env death) | Player k = event.getEntity().getKiller(); if (k == null) return; |
| Clicked air, not a block | if (event.getClickedBlock() == null) return; |
| Empty hand | if (event.getItem() == null) return; |
| Pressure plate step | if (event.getAction() == Action.PHYSICAL) return; |
| Projectile not from player | if (!(event.getEntity().getShooter() instanceof Player)) return; |
| World not found | World w = Bukkit.getWorld("name"); if (w == null) return; |
| Wrong inventory holder | if (!(inv.getHolder() instanceof MyHolder)) return; |

🗡️ Custom Items ITEMS

Creating an Item

ItemStack = the item. ItemMeta = extra info (name, lore, enchants etc.). Always call setItemMeta() at the end or your changes won't save.

+

copy

ItemStack starMenu = new ItemStack(Material.NETHER\_STAR);
ItemMeta meta = starMenu.getItemMeta();
meta.setDisplayName("§f§lStar Chooser");
meta.setLore(Arrays.asList(
    "§7A legendary relic",
    "§eRight-click to open menu",
    "",
    "§8Bound to Steve"
));
meta.addEnchant(Enchantment.DAMAGE\_ALL, 5, true); // true = ignore level cap
meta.setUnbreakable(true);
meta.addItemFlags(ItemFlag.HIDE\_ENCHANTS);        // hide enchant lines
meta.addItemFlags(ItemFlag.HIDE\_UNBREAKABLE);     // hide unbreakable tag
meta.addItemFlags(ItemFlag.HIDE\_ATTRIBUTES);      // hide attack speed/damage
meta.setCustomModelData(1001);                    // custom resource pack model
starMenu.setItemMeta(meta);                        // ✦ MUST apply back or all changes lost!

Giving an Item + Checking Items

+

copy

// Give to player (drops on ground if inventory is full)
player.getInventory().addItem(starMenu);

// Set a specific slot
player.getInventory().setItem(9, starMenu);

// Check item type
if (item.getType() == Material.DIAMOND\_SWORD) { }

// Check display name (always null-check meta first!)
if (item.hasItemMeta() && item.getItemMeta().hasDisplayName()) {
    String name = item.getItemMeta().getDisplayName();
}

// Stack size
item.getAmount();     // how many in the stack
item.setAmount(32);  // change stack size
item.isSimilar(other); // compare ignoring amount

Specialized Meta Types

Cast to the right meta type for skulls, leather armor, potions, and maps.

+

copy

// Skull — set player head owner
SkullMeta sm = (SkullMeta) skull.getItemMeta();
sm.setOwningPlayer(Bukkit.getOfflinePlayer("Username"));

// Leather armor — custom color
LeatherArmorMeta lam = (LeatherArmorMeta) chestplate.getItemMeta();
lam.setColor(Color.fromRGB(255, 0, 128));  // hot pink

// Potion — custom effects
PotionMeta pm = (PotionMeta) potion.getItemMeta();
pm.setBasePotionData(new PotionData(PotionType.SPEED, false, true));
pm.addCustomEffect(new PotionEffect(PotionEffectType.JUMP, 400, 2), true);

// Always apply the meta back!
skull.setItemMeta(sm);
chestplate.setItemMeta(lam);
potion.setItemMeta(pm);

🗂️ GUI INVENTORY UI

Creating a GUI

Sizes must be multiples of 9 (9, 18, 27, 36, 45, 54). Slots go left to right, top to bottom from 0.

+

copy

private final String GUI\_TITLE = "§6§lMy Shop";
private Inventory gui;

private void createGUI() {
    gui = Bukkit.createInventory(null, 27, GUI\_TITLE); // 27 = 3 rows

    // Helper: make a button item
    ItemStack btn = makeButton(Material.DIAMOND\_SWORD, "§b§lBuy Sword",
        "§7A powerful weapon", "§ePrice: §a$500", "§8Click to purchase");
    gui.setItem(13, btn); // center slot of row 2

    // Fill border with glass pane
    ItemStack filler = makeButton(Material.GRAY\_STAINED\_GLASS\_PANE, "§8");
    int\[\] border = {0,1,2,3,4,5,6,7,8,18,19,20,21,22,23,24,25,26};
    for (int slot : border) gui.setItem(slot, filler);
}

private ItemStack makeButton(Material mat, String name, String... lore) {
    ItemStack item = new ItemStack(mat);
    ItemMeta meta = item.getItemMeta();
    meta.setDisplayName(name);
    meta.setLore(Arrays.asList(lore));
    meta.addItemFlags(ItemFlag.HIDE\_ATTRIBUTES);
    item.setItemMeta(meta);
    return item;
}

// Open for a player
public void openGUI(Player player) { player.openInventory(gui); }

InventoryHolder Pattern (Recommended)

A custom holder ties data to your GUI so you can identify it without comparing title strings.

+

copy

// Step 1 — Custom holder class
public class ShopHolder implements InventoryHolder {
    private final String shopId;
    private Inventory inventory;
    public ShopHolder(String shopId) { this.shopId = shopId; }
    public String getShopId() { return shopId; }
    @Override public Inventory getInventory() { return inventory; }
    public void setInventory(Inventory inv) { this.inventory = inv; }
}

// Step 2 — Create GUI with holder
ShopHolder holder = new ShopHolder("weapons");
Inventory gui = Bukkit.createInventory(holder, 27, "§6Weapon Shop");
holder.setInventory(gui);

// Step 3 — Detect in click handler (type-safe, no title comparison!)
if (!(event.getInventory().getHolder() instanceof ShopHolder shopHolder)) return;
String shopId = shopHolder.getShopId(); // access custom data

Click Event Handler

Always add both null checks at the top and always cancel the event to prevent item theft.

+

copy

@EventHandler
public void onInventoryClick(InventoryClickEvent event) {
    if (event.getClickedInventory() == null) return; // border click = null
    if (event.getCurrentItem() == null) return;      // empty slot
    if (event.getCurrentItem().getType() == Material.AIR) return;

    if (!(event.getInventory().getHolder() instanceof ShopHolder holder)) return;

    event.setCancelled(true); // ✦ ALWAYS cancel or players can steal items

    Player player = (Player) event.getWhoClicked();
    int slot = event.getSlot();
    ClickType type = event.getClick();

    if (slot == 13 && type == ClickType.LEFT) {
        player.getInventory().addItem(new ItemStack(Material.DIAMOND\_SWORD));
        player.sendMessage("§aPurchased Sword!");
        player.playSound(player.getLocation(), Sound.ENTITY\_PLAYER\_LEVELUP, 1f, 1f);
    }
}

// Also block shift-click from player inventory into GUI
@EventHandler
public void onInventoryDrag(InventoryDragEvent event) {
    if (event.getInventory().getHolder() instanceof ShopHolder) {
        event.setCancelled(true);
    }
}

Click Types & Slot Chart

Reference for ClickType values and GUI slot numbering.

+

| ClickType | Triggered By | ClickType | Triggered By |
| --- | --- | --- | --- |
| LEFT | Left click | SHIFT\_LEFT | Shift + left click |
| RIGHT | Right click | SHIFT\_RIGHT | Shift + right click |
| MIDDLE | Middle mouse | NUMBER\_KEY | 1–9 hotbar keys |
| DROP | Q key | DOUBLE\_CLICK | Double click |

6-row chest = 54 slots (Row 1: 0–8, Row 2: 9–17, … Row 6: 45–53)

0

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

33

34

35

36

37

38

39

40

41

42

43

44

45

46

47

48

49

50

51

52

53

Center of 3-row: 13 | Center of 6-row: 22 & 31 | Blue = common border slots

✨ Particles VFX

Basic Particle Spawning

+

copy

// Simple burst at location
world.spawnParticle(Particle.FLAME, location, 30);

// With spread: (particle, location, count, spreadX, spreadY, spreadZ, speed)
world.spawnParticle(Particle.CRIT, location, 20, 0.5, 0.5, 0.5, 0.05);

// Directional (count=0, spread=direction, speed=force)
world.spawnParticle(Particle.END\_ROD, location, 0, 0, 0.1, 0, 0.05);

// Player-only (only that player sees it)
player.spawnParticle(Particle.HEART, location, 5);

Colored Dust Particles

Custom RGB color and size. The DustTransition version transitions between two colors (1.17+).

+

copy

// Colored dust: (Color, size: 0.1=tiny to 4.0=huge)
Particle.DustOptions red    = new Particle.DustOptions(Color.RED, 1.5f);
Particle.DustOptions orange = new Particle.DustOptions(Color.fromRGB(255,140,0), 1.0f);
world.spawnParticle(Particle.REDSTONE, location, 1, red);

// Transitioning dust (1.17+) — fades from one color to another
Particle.DustTransition trans = new Particle.DustTransition(Color.RED, Color.BLUE, 1.5f);
world.spawnParticle(Particle.DUST\_COLOR\_TRANSITION, location, 1, trans);

// Block / item particles
world.spawnParticle(Particle.BLOCK\_CRACK, location, 30,
    Material.DIAMOND\_BLOCK.createBlockData());
world.spawnParticle(Particle.ITEM\_CRACK, location, 20,
    new ItemStack(Material.DIAMOND\_SWORD));

Common Particle Types

+

| Particle | Looks Like | Particle | Looks Like |
| --- | --- | --- | --- |
| FLAME | Orange fire | SMOKE\_NORMAL | Grey smoke puff |
| CRIT | Star critical hit | END\_ROD | White sparkle |
| HEART | Pink hearts | ENCHANTMENT\_TABLE | Rune letters |
| REDSTONE | Colored dust\* | SPELL\_WITCH | Purple magic |
| DUST\_COLOR\_TRANSITION | Gradient dust\* | VILLAGER\_HAPPY | Green sparkle |
| TOTEM | Totem swirl | DRAGON\_BREATH | Purple mist |
| EXPLOSION\_LARGE | Big puff | PORTAL | Nether purple |
| SOUL\_FIRE\_FLAME | Blue soul fire | CHERRY\_LEAVES | Pink petals |
| CAMPFIRE\_SIGNAL | Rising smoke | FALLING\_DUST | Falling block\* |

\* = requires data parameter (DustOptions, BlockData, or ItemStack)

Particle Line (A → B)

+

copy

public void drawLine(Location a, Location b, Particle p, double gap) {
    Vector dir = b.toVector().subtract(a.toVector());
    double len = dir.length();
    dir.normalize();
    for (double d = 0; d <= len; d += gap) {
        a.getWorld().spawnParticle(p, a.clone().add(dir.clone().multiply(d)), 1, 0, 0, 0, 0);
    }
}
// drawLine(player.getLocation(), target.getLocation(), Particle.END\_ROD, 0.3);

Circle, Sphere & Burst

+

copy

// Horizontal circle
public void drawCircle(Location center, double r, Particle p, int pts) {
    for (int i = 0; i < pts; i++) {
        double a = (2 \* Math.PI / pts) \* i;
        center.getWorld().spawnParticle(p,
            center.clone().add(Math.cos(a)\*r, 0, Math.sin(a)\*r), 1, 0, 0, 0, 0);
    }
}
// drawCircle(player.getLocation(), 3.0, Particle.FLAME, 36);

// Sphere (Fibonacci lattice — even distribution)
public void drawSphere(Location center, double r, Particle p, int pts) {
    for (int i = 0; i < pts; i++) {
        double phi = Math.acos(1 - 2.0\*i/pts);
        double theta = Math.PI\*(1+Math.sqrt(5))\*i;
        double x = r\*Math.sin(phi)\*Math.cos(theta);
        double y = r\*Math.cos(phi);
        double z = r\*Math.sin(phi)\*Math.sin(theta);
        center.getWorld().spawnParticle(p, center.clone().add(x,y,z), 1, 0, 0, 0, 0);
    }
}
// drawSphere(player.getLocation().add(0,1,0), 2.0, Particle.END\_ROD, 150);

// Random burst (explosion-style)
public void burst(Location c, Particle p, int count, double speed) {
    Random rand = new Random();
    for (int i = 0; i < count; i++) {
        double phi = Math.acos(2\*rand.nextDouble()-1);
        double theta = 2\*Math.PI\*rand.nextDouble();
        c.getWorld().spawnParticle(p, c, 0,
            Math.sin(phi)\*Math.cos(theta),
            Math.cos(phi),
            Math.sin(phi)\*Math.sin(theta), speed);
    }
}
// burst(player.getLocation().add(0,1,0), Particle.CRIT, 50, 0.3);

Animated Helix / Spiral

An animated double helix that rises over time — looks like a rising vortex. Auto-cancels.

+

copy

public BukkitTask spawnHelix(Location center, Particle particle) {
    final double\[\] t = {0};
    return new BukkitRunnable() {
        @Override public void run() {
            for (int arm = 0; arm < 2; arm++) {
                double angle = t\[0\] + (Math.PI \* arm);
                double x = Math.cos(angle) \* 1.5;
                double z = Math.sin(angle) \* 1.5;
                double y = (t\[0\] / (2\*Math.PI)) \* 2 % 4;
                center.getWorld().spawnParticle(particle,
                    center.clone().add(x,y,z), 1, 0, 0, 0, 0);
            }
            t\[0\] += 0.15;
            if (t\[0\] > 20\*Math.PI) this.cancel();
        }
    }.runTaskTimer(plugin, 0L, 1L);
}

📘 Java Basics LANGUAGE

Data Types & Conversions

Java is strict — you must declare the type. Primitives are lowercase. Wrapper objects are capitalized and can be null.

+

copy

// Primitives — stored by value, NOT nullable
int     kills     = 5;           // whole numbers -2B to 2B
long    bigNum    = 9999999999L; // bigger integer — add L suffix
double  health    = 20.0;        // decimal 64-bit (prefer over float)
float   speed     = 1.5f;        // decimal 32-bit — add f suffix
boolean pvpOn     = true;
char    grade     = 'A';         // single character, single quotes

// Wrapper objects — capitalized, CAN be null, have helper methods
Integer i    = 42;   // auto-boxed from int
Boolean flag = null; // can hold null unlike primitive boolean

// Conversions
int    from\_d = (int) 3.9;              // 3 (truncates, NOT rounds)
double from\_i = (double) 5 / 2;          // 2.5 — cast BEFORE dividing
String str    = String.valueOf(42);       // "42"
int    parsed = Integer.parseInt("42");   // 42 (throws NumberFormatException!)
double parsedD = Double.parseDouble("3.14");

Variables & Math Operators

+

copy

int score = 0;
score = 10;
score += 5;   // shorthand for score = score + 5 → 15
final int MAX = 20;  // constant — cannot reassign
var list = new ArrayList<String\>(); // Java 10+ — type inferred

int a = 10 + 5;  // 15   addition
int b = 10 - 3;  // 7    subtraction
int c = 4  \* 3;  // 12   multiplication
int d = 10 / 2;  // 5    division
int e = 10 % 3;  // 1    modulo (remainder)
x++;  x--;        // increment / decrement

// Ternary (inline if/else)
String label = (kills >= 10) ? "§cKiller" : "§7Newbie";

Strings (Text)

Always use .equals() to compare strings — never ==. That compares memory address, not content.

+

copy

String name = "Logo";
name.length();                                  // 4
name.equals("Logo");                           // ✓ ALWAYS use .equals()
name.equalsIgnoreCase("logo");
name.contains("og");
name.startsWith("Lo"); name.endsWith("go");
name.toUpperCase(); name.toLowerCase();
name.trim(); name.strip();                      // strip = Java 11+ unicode-aware
name.isEmpty();  name.isBlank();                // isBlank = only whitespace?
name.replace("Logo", "Steve");
name.substring(6); name.substring(0, 5);
name.split(",");
name.indexOf("og"); name.charAt(0);

// String.format — cleaner than concatenation
String.format("§aPlayer §f%s §ahas §f%d §akills!", name, kills);
// %s=String  %d=int/long  %f=float/double  %b=boolean

// Join
String.join(", ", "a", "b", "c"); // "a, b, c"

// StringBuilder — efficient when doing many appends
StringBuilder sb = new StringBuilder();
for (Player p : online) sb.append(p.getName()).append(", ");
String result = sb.toString();

If / Else / Switch

+

copy

if (health <= 0) {
    // dead
} else if (health < 5.0) {
    // critical
} else {
    // healthy
}
// ==  !=  >  <  >=  <=  |  &&=AND  ||=OR  !=NOT

// Classic switch
switch (args\[0\].toLowerCase()) {
    case "heal": handleHeal(); break;
    default: sender.sendMessage("Unknown!"); break;
}

// Switch expression (Java 14+) — much cleaner
int result = switch (gameMode) {
    case "survival"  -> 0;
    case "creative"  -> 1;
    case "adventure" -> 2;
    default         -> -1;
};

Loops

+

copy

// Classic for (known count)
for (int i = 0; i < 10; i++) { }

// For-each (collections)
for (Player p : Bukkit.getOnlinePlayers()) {
    p.sendMessage("§aHello!");
}

// While loop
int count = 0;
while (count < 5) { count++; }

// Do-while — always runs at least once
do { count++; } while (count < 5);

// Break / continue
for (int i = 0; i < 10; i++) {
    if (i == 3) continue; // skip 3
    if (i == 7) break;    // stop at 7
}

// Java Streams (functional style)
List<String\> names = Bukkit.getOnlinePlayers().stream()
    .map(Player::getName)
    .filter(n -> n.startsWith("A"))
    .collect(Collectors.toList());

long admins = Bukkit.getOnlinePlayers().stream()
    .filter(p -> p.hasPermission("admin")).count();

Collections — List, Map, Set

+

copy

// List — ordered, allows duplicates
List<String\> players = new ArrayList<>();
players.add("Logo");
players.add(0, "First");     // insert at index
players.set(0, "Updated");   // replace at index
players.remove("Logo");      // by value
players.remove(0);           // by index
players.get(0);  players.size();  players.contains("Logo");  players.clear();
Collections.sort(players);  Collections.shuffle(players);

// Map — key → value, keys must be unique
Map<UUID, Integer\> killMap = new HashMap<>();
killMap.put(uuid, 5);
killMap.get(uuid);                     // null if missing
killMap.getOrDefault(uuid, 0);        // safe fallback
killMap.putIfAbsent(uuid, 0);          // only puts if not present
killMap.merge(uuid, 1, Integer::sum); // increment kill counter!
killMap.containsKey(uuid);  killMap.remove(uuid);
for (Map.Entry<UUID,Integer\> e : killMap.entrySet()) {
    e.getKey(); e.getValue();
}

// Set — unique values, O(1) lookup
Set<UUID\> seen = new HashSet<>();
seen.add(player.getUniqueId());
seen.contains(uuid);  seen.remove(uuid);

// Thread-safe map for async use
Map<UUID,Long\> cdMap = new ConcurrentHashMap<>();

Methods, Null Safety & Casting

+

copy

// Methods
public void greetPlayer(Player p) { p.sendMessage("Hello, " + p.getName() + "!"); }
public boolean isAlive(Player p) { return p.getHealth() > 0; }
public static int clamp(int value, int min, int max) {
    return Math.max(min, Math.min(max, value));
}
// Varargs — accepts any number of args
public void log(String... messages) { for (String m : messages) plugin.getLogger().info(m); }

// Null safety — calling a method on null = NullPointerException crash!
Player killer = event.getEntity().getKiller(); // may be null
if (killer == null) return;                    // ✓ early return pattern
String display = (name != null) ? name : "Unknown"; // ternary

// Casting — always check before downcasting
if (sender instanceof Player) {
    Player player = (Player) sender;
}
// Java 16+ pattern matching (cleaner)
if (sender instanceof Player player) { player.sendMessage("Hi!"); }
if (entity instanceof Zombie zombie) { zombie.setVillager(true); }

🌍 PaperMC Basics API

Player — Everything You Need

+

copy

// Getting a player
Player p = Bukkit.getPlayer("Logo");  // by name, null if offline
Player p = Bukkit.getPlayer(uuid);     // by UUID — preferred!

// Identity
p.getName(); p.getUniqueId(); p.getDisplayName(); p.getPlayerListName();
p.isOp(); p.setOp(true);
p.hasPermission("myplugin.use");
p.getGameMode(); p.setGameMode(GameMode.SURVIVAL);
p.isSneaking(); p.isSprinting(); p.isFlying(); p.isDead();

// Health / Food
p.getHealth(); p.setHealth(20.0);   // 0.0 – 20.0
p.getFoodLevel(); p.setFoodLevel(20);
p.getSaturation(); p.setSaturation(5.0f);

// Messaging
p.sendMessage("§aHello!");
p.sendTitle("§6Title", "§7Subtitle", 10, 70, 20); // fadeIn/stay/fadeOut ticks
p.sendActionBar("§eAbove hotbar");
p.resetTitle(); // clear title

// Movement
p.getLocation(); p.teleport(location);
p.setVelocity(new Vector(0, 1.5, 0)); // launch upward
p.setAllowFlight(true); p.setFlying(true);
p.setWalkSpeed(0.2f);  // default 0.2, max 1.0

// Inventory
p.getInventory().addItem(itemStack);
p.getInventory().setItem(9, itemStack);
p.getInventory().getItemInMainHand();
p.getInventory().getArmorContents(); // \[boots, legs, chest, helm\]
p.getInventory().clear();
p.updateInventory(); // refresh client after changes

// Effects / Sounds
p.addPotionEffect(new PotionEffect(PotionEffectType.SPEED, 200, 1));
// (type, durationTicks, amplifier) — amplifier 0=level I, 1=level II
p.removePotionEffect(PotionEffectType.SPEED);
p.playSound(p.getLocation(), Sound.ENTITY\_PLAYER\_LEVELUP, 1f, 1f);

// Misc
p.kickPlayer("§cYou have been kicked.");
p.setExp(0.5f); p.setLevel(10); p.giveExp(100);
p.setFireTicks(80);   // set on fire for 4 seconds
p.hidePlayer(plugin, other); p.showPlayer(plugin, other);
p.getBedSpawnLocation(); p.setBedSpawnLocation(loc, true);

Location

Represents a position in a world. Always clone before modifying to preserve the original!

+

copy

Location loc = new Location(world, x, y, z);
Location loc = new Location(world, x, y, z, yaw, pitch);
// yaw: -180 to 180 (horizontal) | pitch: -90 to 90 (-90=up)

loc.getX(); loc.getY(); loc.getZ();
loc.getBlockX(); loc.getBlockY(); loc.getBlockZ(); // floored to int
loc.getYaw(); loc.getPitch(); loc.getWorld(); loc.getBlock();

// ✦ ALWAYS clone before modifying!
Location above  = loc.clone().add(0, 2, 0);
Location front  = loc.clone().add(loc.getDirection().multiply(3));
Location behind = loc.clone().subtract(loc.getDirection().multiply(3));

// Distance
double exact = loc1.distance(loc2);           // actual distance (slower)
double sq    = loc1.distanceSquared(loc2);    // faster — use for range checks
if (loc1.distanceSquared(loc2) <= 25) { }   // within 5 blocks (5²=25)

loc.toVector();           // Vector representation
loc.getDirection();       // unit vector player is facing
loc.setDirection(vector); // set yaw/pitch from a Vector

// Configs save/load locations automatically!
config.set("home", loc);
Location home = (Location) config.get("home");

World

+

copy

World w = Bukkit.getWorld("world");
List<World\> all = Bukkit.getWorlds();

w.spawnEntity(loc, EntityType.ZOMBIE);
w.spawnParticle(Particle.FLAME, loc, 30, 0.5, 0.5, 0.5, 0.05);
w.playSound(loc, Sound.ENTITY\_ENDER\_DRAGON\_GROWL, 1f, 1f);
w.strikeLightning(loc);              // real — causes damage/fire
w.strikeLightningEffect(loc);        // visual only, no damage
w.createExplosion(loc, 4f);          // 4=TNT power, 0=visual only
w.createExplosion(loc, 4f, false, false); // (fire, blockDamage)
w.setTime(6000);  // 0=dawn 6000=noon 12000=dusk 18000=midnight
w.setStorm(true); w.setThundering(true);
w.getPlayers(); w.getEntities(); w.getLivingEntities();
w.getHighestBlockYAt(x, z); // top solid block Y
w.dropItem(loc, item);         // spawn item entity
w.dropItemNaturally(loc, item); // with random velocity

Block, Entity & Vector

+

copy

// Block
Block block = world.getBlockAt(x, y, z);
block.getType(); block.setType(Material.GOLD\_BLOCK);
block.setType(Material.AIR); // remove block
block.getRelative(BlockFace.UP);
block.getRelative(BlockFace.DOWN);
block.getRelative(0, 1, 0); // same as BlockFace.UP
// BlockData — for state like waterlogged, slab type, facing
if (block.getBlockData() instanceof Slab slab) { slab.getType(); }
if (block.getBlockData() instanceof Waterlogged wl) { wl.isWaterlogged(); }

// Entity
entity.getType(); entity.getUniqueId(); entity.getLocation();
entity.getVelocity(); entity.setVelocity(vec);
entity.remove();        entity.isDead();
entity.setGravity(false); entity.setGlowing(true);
entity.setCustomName("§cBoss"); entity.setCustomNameVisible(true);
entity.setInvulnerable(true);
// LivingEntity extras
LivingEntity le = (LivingEntity) entity;
le.setAI(false); le.setSilent(true);
le.getTarget(); le.setTarget(player);
le.addPotionEffect(new PotionEffect(PotionEffectType.POISON, 200, 0));

// BoundingBox — hitbox
BoundingBox bb = entity.getBoundingBox();
bb.contains(loc.toVector()); bb.overlaps(other);

// Vector — direction or velocity, NOT a position
player.setVelocity(new Vector(0, 0.8, 0)); // launch upward
Vector dir = player.getLocation().getDirection(); // unit vector facing
Location front = player.getLocation().clone().add(dir.multiply(5));
v.multiply(2.0); v.normalize(); v.length();
v.clone(); // ✦ always clone before mutating!

⏱️ Timers SCHEDULER

**20 ticks = 1 second.** NEVER use Thread.sleep() — it freezes the entire server main thread.

One-Shot Delay & Repeating Tasks

+

copy

// Run once after delay (60 ticks = 3 seconds)
Bukkit.getScheduler().runTaskLater(plugin, () -> {
    player.sendMessage("§a3 seconds have passed!");
}, 60L);

// Run on next server tick
Bukkit.getScheduler().runTask(plugin, () -> { /\* safe to use Bukkit API \*/ });

// Run repeatedly (0L=start now, 40L=every 2 seconds)
BukkitTask task = Bukkit.getScheduler().runTaskTimer(plugin, () -> {
    Bukkit.broadcastMessage("§ePing!");
}, 0L, 40L);

task.cancel(); // stop it

// Self-cancelling task (runs 5 times then stops)
final int\[\] count = {0};
final BukkitTask\[\] ref = {null};
ref\[0\] = Bukkit.getScheduler().runTaskTimer(plugin, () -> {
    player.sendMessage("Count: " + (++count\[0\]));
    if (count\[0\] >= 5) ref\[0\].cancel();
}, 0L, 20L);

BukkitRunnable — Cleaner Self-Contained Tasks

+

copy

new BukkitRunnable() {
    int ticks = 0;
    @Override
    public void run() {
        ticks++;
        if (player.isOnline()) {
            player.sendActionBar("§eTask tick: " + ticks);
        }
        if (ticks >= 100 || !player.isOnline()) {
            this.cancel(); // cancel self
        }
    }
}.runTaskTimer(plugin, 0L, 1L); // start now, every tick

// Or with a delay
new BukkitRunnable() {
    @Override public void run() { player.sendMessage("§aDelayed!"); }
}.runTaskLater(plugin, 100L);

// Cancel all plugin tasks on disable
Bukkit.getScheduler().cancelTasks(this);

Async Tasks — For Heavy Work (DB, Files, HTTP)

NEVER call Bukkit API inside async tasks! Always switch back to the main thread first.

+

**⚠ NEVER** call player.sendMessage(), teleport(), or any world modification inside async — it will crash or corrupt the world. Switch back to main thread first.

copy

// Async → heavy work → sync → update game
Bukkit.getScheduler().runTaskAsynchronously(plugin, () -> {
    // ✓ safe: file I/O, database queries, HTTP requests
    String data = database.loadPlayerData(player.getUniqueId());

    // Switch back to main thread for any Bukkit API
    Bukkit.getScheduler().runTask(plugin, () -> {
        player.sendMessage("§aLoaded: " + data); // ✓ safe now
        player.teleport(spawnLocation);           // ✓ safe now
    });
});

// Async repeating (e.g. auto-save every 5 minutes)
Bukkit.getScheduler().runTaskTimerAsynchronously(plugin, () -> {
    saveAllData();
}, 6000L, 6000L); // delay 5min, repeat every 5min

Ticks / Time Reference

+

| Ticks | Real Time | Ticks | Real Time |
| --- | --- | --- | --- |
| 1   | 0.05s | 200 | 10 seconds |
| 20  | 1 second | 1200 | 1 minute |
| 40  | 2 seconds | 6000 | 5 minutes |
| 60  | 3 seconds | 24000 | 20 min (full MC day) |
| 100 | 5 seconds | 72000 | 1 hour |

💬 Commands CMD

plugin.yml — Registering Commands

Every command MUST be declared in plugin.yml or the server won't recognize it at all.

+

copy

\# src/main/resources/plugin.yml
commands:
  heal:
    description: "Heal a player to full health"
    usage: "/ \[player\]"
    permission: myplugin.heal
    permission-message: "§cNo permission!"
    aliases: \[h, healme\]

permissions:
  myplugin.\*:
    description: "All MyPlugin permissions"
    children:
      myplugin.heal: true
  myplugin.heal:
    description: "Allow /heal"
    default: op  \# true | false | op | not op

Full Command Class

Return true = command handled. Return false = shows the usage message from plugin.yml.

+

copy

public class HealCommand implements CommandExecutor, TabCompleter {
    private final MyPlugin plugin;
    public HealCommand(MyPlugin plugin) { this.plugin = plugin; }

    @Override
    public boolean onCommand(CommandSender sender, Command cmd,
                              String label, String\[\] args) {
        if (!(sender instanceof Player player)) {
            sender.sendMessage("§cPlayers only!"); return true;
        }
        if (!player.hasPermission("myplugin.heal")) {
            player.sendMessage("§cNo permission!"); return true;
        }
        if (args.length == 0) {
            // /heal — heal self
            player.setHealth(20.0); player.setFoodLevel(20);
            player.sendMessage("§aYou have been fully healed!");
            return true;
        }
        // /heal 
        Player target = Bukkit.getPlayer(args\[0\]);
        if (target == null) {
            player.sendMessage("§cPlayer §f" + args\[0\] + " §cis not online!");
            return true;
        }
        target.setHealth(20.0); target.setFoodLevel(20);
        player.sendMessage("§aHealed §f" + target.getName());
        target.sendMessage("§f" + player.getName() + " §ahealed you!");
        target.playSound(target.getLocation(), Sound.ENTITY\_PLAYER\_LEVELUP, 1f, 2f);
        return true;
    }

    @Override
    public List<String\> onTabComplete(CommandSender sender, Command cmd,
                                        String alias, String\[\] args) {
        if (args.length == 1) {
            String input = args\[0\].toLowerCase();
            return Bukkit.getOnlinePlayers().stream()
                .map(Player::getName)
                .filter(n -> n.toLowerCase().startsWith(input))
                .collect(Collectors.toList());
        }
        return Collections.emptyList();
    }
}

Argument Patterns

+

| Pattern | Code |
| --- | --- |
| Check no args | if (args.length == 0) |
| Check minimum args | if (args.length < 2) { player.sendMessage("Usage: ..."); return true; } |
| Parse int safely | try { int n = Integer.parseInt(args\[1\]); } catch (NumberFormatException e) { } |
| Parse double safely | try { double d = Double.parseDouble(args\[1\]); } catch (NumberFormatException e) { } |
| Get online player | Player t = Bukkit.getPlayer(args\[0\]); if (t == null) { ... } |
| Join all args | String.join(" ", args) |
| Join from index 1 | String.join(" ", Arrays.copyOfRange(args, 1, args.length)) |
| Case-insensitive | args\[0\].equalsIgnoreCase("heal") |
| Run as console | Bukkit.dispatchCommand(Bukkit.getConsoleSender(), "ban " + name) |

Subcommand System + Tab Complete

+

copy

// Switch expression for clean routing (Java 14+)
switch (args\[0\].toLowerCase()) {
    case "give"  -> handleGive(player, args);
    case "take"  -> handleTake(player, args);
    case "reset" -> handleReset(player, args);
    default      -> player.sendMessage("§cUnknown: §f/myplugin ");
}

// Tab complete for subcommands — StringUtil filters by partial match
if (args.length == 1) {
    return StringUtil.copyPartialMatches(args\[0\],
        Arrays.asList("give", "take", "reset"),
        new ArrayList<>());
}
// Tab complete player names for arg 2
if (args.length == 2 && args\[0\].equalsIgnoreCase("give")) {
    return Bukkit.getOnlinePlayers().stream()
        .map(Player::getName)
        .filter(n -> n.toLowerCase().startsWith(args\[1\].toLowerCase()))
        .collect(Collectors.toList());
}

💾 Configs / Data Saving PERSISTENCE

config.yml (Built-in)

+

copy

\# src/main/resources/config.yml
welcome-message: "§aWelcome to the server!"
settings:
  pvp-enabled: true
  max-kills: 100
  spawn-radius: 50.5
rewards: \[DIAMOND, GOLD\_INGOT, IRON\_INGOT\]
kits:
  warrior:
    price: 500
    cooldown: 3600

copy

// In onEnable()
saveDefaultConfig(); // creates config.yml from resources if it doesn't exist
reloadConfig();      // read from disk into memory

// Reading
String  msg    = getConfig().getString("welcome-message", "Default!"); // with fallback
boolean pvp    = getConfig().getBoolean("settings.pvp-enabled");
int     max    = getConfig().getInt("settings.max-kills", 100);
double  radius = getConfig().getDouble("settings.spawn-radius");
List<String\> items = getConfig().getStringList("rewards");
int     price  = getConfig().getInt("kits.warrior.price", 0);

// Writing
getConfig().set("settings.pvp-enabled", false);
getConfig().set("players.Logo.kills", 42);
saveConfig(); // ✦ MUST call this or changes only exist in memory!

// Check / delete
getConfig().contains("settings.pvp-enabled");
getConfig().set("key", null); // set to null = delete that key

Custom Player Data Files

For saving player-specific data like kills, homes, stats, etc.

+

copy

private File dataFile;
private FileConfiguration data;

private void loadData() {
    dataFile = new File(getDataFolder(), "playerdata.yml");
    if (!dataFile.exists()) { dataFile.getParentFile().mkdirs(); }
    data = YamlConfiguration.loadConfiguration(dataFile);
}

private void saveData() {
    try { data.save(dataFile); }
    catch (IOException e) { getLogger().severe("Could not save data!"); }
}

// Write player data
String path = "players." + player.getUniqueId();
data.set(path + ".kills", kills);
data.set(path + ".home", player.getLocation()); // Location saves perfectly!
data.set(path + ".name", player.getName());      // cache name for display
saveData();

// Read player data
String base = "players." + uuid;
int      kills = data.getInt(base + ".kills", 0);
Location home  = (Location) data.get(base + ".home"); // may be null

// List all players
ConfigurationSection sec = data.getConfigurationSection("players");
if (sec != null) {
    for (String uuidStr : sec.getKeys(false)) {
        int k = data.getInt("players." + uuidStr + ".kills");
    }
}

🏷️ PersistentDataContainer (PDC) ITEM / ENTITY DATA

**PDC data survives restarts and server reloads.** Ideal for custom item tags, custom mob IDs, or any data that needs to live on an item or entity.

Writing & Reading PDC Data

+

copy

// Step 1 — Create NamespacedKeys (once per tag, store them)
NamespacedKey SWORD\_KEY  = new NamespacedKey(plugin, "legendary\_sword");
NamespacedKey DAMAGE\_KEY = new NamespacedKey(plugin, "bonus\_damage");
NamespacedKey BOSS\_KEY   = new NamespacedKey(plugin, "boss\_id");

// Step 2 — Write to ItemMeta
ItemMeta meta = item.getItemMeta();
PersistentDataContainer pdc = meta.getPersistentDataContainer();
pdc.set(SWORD\_KEY,  PersistentDataType.STRING,  "fire"); // string tag
pdc.set(DAMAGE\_KEY, PersistentDataType.INTEGER, 50);      // int
item.setItemMeta(meta); // ✦ must apply back!

// Step 3 — Read
String  type = pdc.get(SWORD\_KEY,  PersistentDataType.STRING);  // null if absent
Integer dmg  = pdc.get(DAMAGE\_KEY, PersistentDataType.INTEGER);

// Check / Remove
pdc.has(SWORD\_KEY, PersistentDataType.STRING);
pdc.remove(SWORD\_KEY);

// On entities (same API)
entity.getPersistentDataContainer().set(BOSS\_KEY, PersistentDataType.STRING, "king");

Available PDC Types & Nested Containers

+

copy

// Available types
PersistentDataType.STRING
PersistentDataType.INTEGER
PersistentDataType.DOUBLE
PersistentDataType.FLOAT
PersistentDataType.LONG
PersistentDataType.SHORT
PersistentDataType.BYTE
PersistentDataType.BYTE\_ARRAY
PersistentDataType.INTEGER\_ARRAY
PersistentDataType.LONG\_ARRAY
PersistentDataType.TAG\_CONTAINER    // nested PDC — for complex structures

// Nested containers
PersistentDataContainer nested = pdc.getAdapterContext().newPersistentDataContainer();
nested.set(new NamespacedKey(plugin, "level"), PersistentDataType.INTEGER, 5);
pdc.set(new NamespacedKey(plugin, "stats"), PersistentDataType.TAG\_CONTAINER, nested);

🗄️ SQLite DATABASE

**⚠ Always run database operations async!** SQLite is built into the JVM — no extra dependency needed. Blocking the main thread with DB queries will lag the server.

Connection Setup & Table Creation

+

copy

private Connection conn;

private void setupDatabase() throws Exception {
    File dbFile = new File(getDataFolder(), "data.db");
    dbFile.getParentFile().mkdirs();
    conn = DriverManager.getConnection("jdbc:sqlite:" + dbFile.getAbsolutePath());
    conn.createStatement().execute(
        "CREATE TABLE IF NOT EXISTS players (" +
        "  uuid TEXT PRIMARY KEY," +
        "  name TEXT NOT NULL," +
        "  kills INTEGER DEFAULT 0," +
        "  deaths INTEGER DEFAULT 0," +
        "  coins REAL DEFAULT 0.0," +
        "  last\_seen INTEGER)");
    getLogger().info("Database connected.");
}

// Close on disable
if (conn != null && !conn.isClosed()) conn.close();

Insert, Update & Query

+

copy

// Insert or overwrite (duplicate primary key)
PreparedStatement ps = conn.prepareStatement(
    "INSERT OR REPLACE INTO players (uuid, name, kills, coins) VALUES (?,?,?,?)");
ps.setString(1, player.getUniqueId().toString());
ps.setString(2, player.getName());
ps.setInt(3, kills);
ps.setDouble(4, coins);
ps.executeUpdate();

// Update only
PreparedStatement up = conn.prepareStatement(
    "UPDATE players SET kills=?, coins=? WHERE uuid=?");
up.setInt(1, kills); up.setDouble(2, coins);
up.setString(3, player.getUniqueId().toString());
up.executeUpdate();

// Query a single player
PreparedStatement qs = conn.prepareStatement(
    "SELECT kills, coins FROM players WHERE uuid=?");
qs.setString(1, player.getUniqueId().toString());
ResultSet rs = qs.executeQuery();
if (rs.next()) {
    int    kills = rs.getInt("kills");
    double coins = rs.getDouble("coins");
}

// Leaderboard (top 10 by kills)
ResultSet top = conn.createStatement().executeQuery(
    "SELECT name, kills FROM players ORDER BY kills DESC LIMIT 10");
while (top.next()) {
    String name = top.getString("name");
    int    k    = top.getInt("kills");
}

// Always run DB code async!
Bukkit.getScheduler().runTaskAsynchronously(plugin, () -> {
    savePlayerData(player);
});

💡 Tips BEST PRACTICES

UUID vs Player Name

Always use UUID for storing player data — names can change, UUIDs never do.

+

copy

UUID uuid    = player.getUniqueId();
String uuidStr = uuid.toString();   // "550e8400-e29b-41d4-..."
UUID back     = UUID.fromString(uuidStr);

// Offline player (can access even if not online)
OfflinePlayer op = Bukkit.getOfflinePlayer(uuid);
op.getName(); op.hasPlayedBefore(); op.getLastPlayed();
// ✦ NEVER use Bukkit.getOfflinePlayer(String name) in production!
// It makes a slow Mojang web request. Always use UUID.

Cooldown System Using a Map

Track cooldowns with a UUID → timestamp map. Uses ConcurrentHashMap for thread safety.

+

copy

private final Map<UUID, Long\> cooldowns = new ConcurrentHashMap<>();
private final long COOLDOWN\_MS = 5000L; // 5 seconds

public boolean isOnCooldown(Player p) {
    Long last = cooldowns.get(p.getUniqueId());
    return last != null && System.currentTimeMillis() - last < COOLDOWN\_MS;
}

public long getRemainingMs(Player p) {
    Long last = cooldowns.get(p.getUniqueId());
    if (last == null) return 0;
    return Math.max(0, COOLDOWN\_MS - (System.currentTimeMillis() - last));
}

public void setCooldown(Player p) { cooldowns.put(p.getUniqueId(), System.currentTimeMillis()); }
public void clearCooldown(Player p) { cooldowns.remove(p.getUniqueId()); }

// Usage
if (isOnCooldown(player)) {
    long rem = getRemainingMs(player);
    player.sendMessage("§cCooldown: §f" + String.format("%.1f", rem/1000.0) + "s");
    return;
}
setCooldown(player);
// ... do the action

🔊 Sounds AUDIO

Playing & Stopping Sounds

Volume: 0.0 (silent) to 1.0 (full). Pitch: 0.5 (deep/slow) to 1.0 (normal) to 2.0 (high/fast).

+

copy

// Player-only (only that player hears it)
player.playSound(player.getLocation(), Sound.ENTITY\_PLAYER\_LEVELUP, 1f, 1f);
//              location               sound                          vol  pitch

// Everyone in earshot hears it
world.playSound(location, Sound.ENTITY\_LIGHTNING\_BOLT\_THUNDER, 1f, 1f);

// With SoundCategory
player.playSound(loc, Sound.UI\_BUTTON\_CLICK, SoundCategory.MASTER, 1f, 1f);

// Custom resource pack sound
player.playSound(loc, "myplugin:custom.ability", 1f, 1f);

// Stop sounds
player.stopSound(Sound.MUSIC\_DISC\_CAT);
player.stopAllSounds();

Pitch Values Guide

+

| Pitch | Sound Effect | Pitch | Sound Effect |
| --- | --- | --- | --- |
| 0.5 | Very deep / slow | 1.25 | Slightly high |
| 0.75 | Low / dark | 1.5 | High / fast |
| 1.0 | Normal (default) | 1.75 | Very high |
| 1.1 | Slightly higher | 2.0 | Maximum — fastest / highest |

Common Sounds Reference

+

| Sound | Best Used For |
| --- | --- |
| UI\_BUTTON\_CLICK | GUI button clicks — perfect for menus |
| BLOCK\_NOTE\_BLOCK\_PLING | Successful action, ping sound |
| ENTITY\_PLAYER\_LEVELUP | Achievement, reward, win |
| BLOCK\_ANVIL\_USE | Heavy / metallic confirmation |
| ENTITY\_VILLAGER\_TRADE | Purchase confirmation |
| ENTITY\_EXPERIENCE\_ORB\_PICKUP | XP gain, small reward |
| BLOCK\_CHEST\_OPEN / CLOSE | Menu open / close |
| ENTITY\_ARROW\_HIT\_PLAYER | Hit confirmation |
| ENTITY\_ENDER\_DRAGON\_GROWL | Boss roar, dramatic event |
| ENTITY\_FIREWORK\_ROCKET\_LAUNCH | Celebration |
| ENTITY\_LIGHTNING\_BOLT\_THUNDER | Power, electric ability |
| BLOCK\_BEACON\_ACTIVATE | Shield / power-up activate |
| ENTITY\_WITHER\_SPAWN | Dark / ominous warning |
| BLOCK\_ENCHANTMENT\_TABLE\_USE | Magic ability, enchanting |
| ENTITY\_ENDERMAN\_TELEPORT | Teleport effect |
| ENTITY\_ELDER\_GUARDIAN\_CURSE | Debuff applied |

🚀 Advanced Patterns POWER FEATURES

BossBar

A progress bar at the top of the screen with a title. Great for events, timers, and raids.

+

copy

BossBar bar = Bukkit.createBossBar(
    "§6§lEvent Name",
    BarColor.YELLOW,
    BarStyle.SEGMENTED\_10
);
// Colors: PINK BLUE RED GREEN YELLOW PURPLE WHITE
// Styles: SOLID SEGMENTED\_6 SEGMENTED\_10 SEGMENTED\_12 SEGMENTED\_20

bar.setProgress(0.75);         // 0.0 to 1.0
bar.setTitle("§a75% Complete");
bar.setColor(BarColor.GREEN);
bar.addPlayer(player);          // show to player
bar.removePlayer(player);
bar.setVisible(true);
bar.removeAll();                // clear all players

// Countdown timer with BossBar
final int\[\] t = {200}; // 10 seconds \* 20 ticks
BossBar cBar = Bukkit.createBossBar("§eStarting...", BarColor.YELLOW, BarStyle.SOLID);
for (Player p : players) cBar.addPlayer(p);
new BukkitRunnable() {
    @Override public void run() {
        t\[0\]--;
        cBar.setProgress(t\[0\] / 200.0);
        cBar.setTitle("§eStarting in: §f" + (t\[0\]/20) + "s");
        if (t\[0\] <= 0) { cBar.removeAll(); this.cancel(); }
    }
}.runTaskTimer(plugin, 0L, 1L);

ActionBar & Title

ActionBar = text above the hotbar. Title = full-screen overlay text.

+

copy

// ActionBar — one-shot
player.sendActionBar("§ePvP Zone!");

// Persistent ActionBar — re-send every 2 seconds or it fades
new BukkitRunnable() {
    @Override public void run() {
        if (!player.isOnline()) { this.cancel(); return; }
        player.sendActionBar(
            "§c❤ " + (int) player.getHealth() +
            "  §a■ " + player.getFoodLevel()
        );
    }
}.runTaskTimer(plugin, 0L, 20L);

// Title — full-screen text
player.sendTitle("§6§lYOU WIN!", "§eKills: " + kills, 10, 60, 20);
// (title, subtitle, fadeIn ticks, stay ticks, fadeOut ticks)
player.resetTitle(); // clear title

Scoreboard / Sidebar

The sidebar list on the right side of the screen. Higher score = higher position.

+

copy

Scoreboard board = Bukkit.getScoreboardManager().getNewScoreboard();
Objective obj = board.registerNewObjective("sidebar", "dummy", "§6§lMy Server");
obj.setDisplaySlot(DisplaySlot.SIDEBAR);

// Lines — higher score = higher position on sidebar
// Use unique spacing strings for blank lines (duplicates collapse)
obj.getScore("§7" + player.getWorld().getName()).setScore(8);
obj.getScore("§8——————————————").setScore(7);
obj.getScore("§eKills: §f" + kills).setScore(6);
obj.getScore("§cDeaths: §f" + deaths).setScore(5);
obj.getScore("§b§8——————————————").setScore(4);
obj.getScore("§aCoins: §f" + coins).setScore(3);
obj.getScore("§7§8——————————————").setScore(2);
obj.getScore("§7play.myserver.com").setScore(1);

player.setScoreboard(board);

// Update a line (must remove old then re-add)
board.resetScores("§eKills: §f" + oldKills);
obj.getScore("§eKills: §f" + newKills).setScore(6);

Teams

Group players into named teams with prefixes, colors, and friendly fire settings.

+

copy

Scoreboard board = player.getScoreboard();
Team red  = board.registerNewTeam("red\_team");
Team blue = board.registerNewTeam("blue\_team");

red.setDisplayName("§cRed Team");
red.setPrefix("§c\[RED\] §f");
red.setSuffix(" §c✦");
red.setColor(ChatColor.RED);
red.setAllowFriendlyFire(false);
red.setCanSeeFriendlyInvisibles(true);

red.addEntry(player.getName());    // add to team
red.removeEntry(player.getName()); // remove
red.unregister();                  // remove the whole team

// Check which team a player is on
Team team = board.getEntryTeam(player.getName()); // null if no team

Math Utilities

+

copy

Math.abs(-5)        // 5    — absolute value
Math.max(3, 7)       // 7    — larger of two
Math.min(3, 7)       // 3    — smaller of two
Math.pow(2, 8)       // 256.0 — exponent
Math.sqrt(16)        // 4.0  — square root
Math.floor(4.9)      // 4.0  — round down
Math.ceil(4.1)       // 5.0  — round up
Math.round(4.5)      // 5    — round to nearest

// Clamp (keep value within range)
double clamped = Math.max(0.0, Math.min(value, 20.0));

// Lerp (linear interpolation — smooth movement)
double lerp(double a, double b, double t) { return a + (b - a) \* t; }
// lerp(0, 100, 0.5) = 50.0

// Random
Random rand = new Random();
rand.nextInt(6);          // 0–5
rand.nextInt(6) + 1;      // 1–6 (dice roll)
rand.nextDouble();          // 0.0–1.0
rand.nextBoolean();

// ThreadLocalRandom — better for concurrent/async use
ThreadLocalRandom.current().nextInt(1, 101); // 1–100

🏗️ Plugin Structure PROJECT SETUP

Main Plugin Class

The entry point for every plugin. Extends JavaPlugin and has onEnable() / onDisable() lifecycle methods.

+

copy

public class MyPlugin extends JavaPlugin {
    private static MyPlugin instance; // singleton for access anywhere

    @Override
    public void onEnable() {
        instance = this;

        // 1. Create data folder / save default config
        saveDefaultConfig();

        // 2. Register listeners
        getServer().getPluginManager().registerEvents(new PlayerListener(this), this);
        getServer().getPluginManager().registerEvents(new GUIListener(this), this);

        // 3. Register commands
        Objects.requireNonNull(getCommand("mycmd")).setExecutor(new MyCommand(this));

        // 4. Start scheduled tasks (e.g. auto-save every 5 min)
        Bukkit.getScheduler().runTaskTimerAsynchronously(this, () -> {
            saveAllData();
        }, 6000L, 6000L);

        getLogger().info("§aMyPlugin enabled! v" + getDescription().getVersion());
    }

    @Override
    public void onDisable() {
        saveAllData();  // save before shutdown
        Bukkit.getScheduler().cancelTasks(this); // cancel all tasks
        getLogger().info("§cMyPlugin disabled.");
    }

    public static MyPlugin getInstance() { return instance; }
}

plugin.yml — Full Example

+

copy

name: MyPlugin
version: "${project.version}"       \# Maven auto-fills from pom.xml
main: com.example.myplugin.MyPlugin
api-version: "1.21"               \# minimum Paper API version
description: "My awesome plugin"
author: YourName
authors: \[YourName, Contributor\]
website: "https://example.com"

depend: \[Vault\]         \# hard dependency — plugin fails without it
softdepend: \[PlaceholderAPI\]  \# soft — loads after if present
loadbefore: \[OtherPlugin\]     \# this plugin loads before OtherPlugin

commands:
  mycmd:
    description: "My main command"
    usage: "/ "
    permission: myplugin.use

permissions:
  myplugin.\*:
    description: "All permissions"
    children:
      myplugin.use: true
      myplugin.admin: true
  myplugin.use:
    description: "Use the plugin"
    default: true
  myplugin.admin:
    description: "Admin features"
    default: op

pom.xml — Maven Setup

+

copy

<!-- Repository -->
<repository>
  <id>papermc</id>
  <url>https://repo.papermc.io/repository/maven-public/</url>
</repository>

<!-- Paper API dependency — provided at runtime by server -->
<dependency>
  <groupId>io.papermc.paper</groupId>
  <artifactId>paper-api</artifactId>
  <version>1.21.4-R0.1-SNAPSHOT</version>
  <scope>provided</scope>
</dependency>

<!-- Compiler — set to Java 21 -->
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-compiler-plugin</artifactId>
  <configuration>
    <source>21</source>
    <target>21</target>
  </configuration>
</plugin>

📋 Quick Reference REFERENCE

Minecraft Color & Format Codes

Use § prefix in chat/display names. For Paper 1.16+, use the Adventure API with Component.text() for more control.

+

| Code | Color | Code | Color | Code | Format |
| --- | --- | --- | --- | --- | --- |
| §0  | ■ Black | §8  | ■ Dark Gray | §l  | **Bold** |
| §1  | ■ Dark Blue | §9  | ■ Blue | §o  | _Italic_ |
| §2  | ■ Dark Green | §a  | ■ Green | §n  | Underline |
| §3  | ■ Dark Aqua | §b  | ■ Aqua | §m  | Strike |
| §4  | ■ Dark Red | §c  | ■ Red | §k  | §k Obfuscated |
| §5  | ■ Dark Purple | §d  | ■ Pink | §r  | Reset all |
| §6  | ■ Gold | §e  | ■ Yellow |     |     |
| §7  | ■ Gray | §f  | ■ White |     |     |

Common Mistakes & Fixes

+

| Mistake | Root Cause | Fix |
| --- | --- | --- |
| NullPointerException crash | Called method on null value | Always null-check: if (x != null) |
| String comparison fails | Used == instead of .equals() | Always use .equals() or .equalsIgnoreCase() |
| Command not working | Not registered in plugin.yml | Add block under "commands:" in plugin.yml |
| NumberFormatException | parseInt on non-number string | Wrap in try { } catch (NumberFormatException e) { } |
| Items stolen from GUI | Did not cancel InventoryClickEvent | Always call event.setCancelled(true) in GUI handler |
| ItemMeta changes lost | Edited meta but never applied it | Always call item.setItemMeta(meta) after changes |
| Server freezes on heavy task | Blocking code on main thread | Use runTaskAsynchronously() for blocking work |
| Bukkit API crash in async | Called Bukkit API off main thread | Wrap Bukkit calls in runTask() inside the async block |
| Data tied to wrong player | Stored by player name | Always use getUniqueId().toString() as key |
| Config changes not saved | Called set() but not saveConfig() | Call saveConfig() after every set() |
| Listener not firing | Forgot to register it | Call registerEvents(new MyListener(this), this) in onEnable() |
| getKiller() crash | Null when entity dies from environment | Player k = getKiller(); if (k == null) return; |
| SkullMeta ClassCastException | Cast wrong meta type | Check: if (item.getType() == Material.PLAYER\_HEAD) |
| return false in onCommand() | Shows plugin.yml usage message | Return false ONLY for wrong usage, true otherwise |

Common Materials

+

| Category | Materials |
| --- | --- |
| Swords | WOODEN\_SWORD, STONE\_SWORD, IRON\_SWORD, GOLDEN\_SWORD, DIAMOND\_SWORD, NETHERITE\_SWORD |
| Pickaxes | WOODEN\_PICKAXE, IRON\_PICKAXE, DIAMOND\_PICKAXE, NETHERITE\_PICKAXE |
| Axes | WOODEN\_AXE, IRON\_AXE, DIAMOND\_AXE, NETHERITE\_AXE |
| Helmets | LEATHER\_HELMET, CHAINMAIL\_HELMET, IRON\_HELMET, DIAMOND\_HELMET, NETHERITE\_HELMET |
| Chestplates | LEATHER\_CHESTPLATE, IRON\_CHESTPLATE, DIAMOND\_CHESTPLATE, NETHERITE\_CHESTPLATE |
| Food | APPLE, BREAD, COOKED\_BEEF, GOLDEN\_APPLE, ENCHANTED\_GOLDEN\_APPLE, COOKED\_CHICKEN |
| Blocks | STONE, GRASS\_BLOCK, DIRT, SAND, OAK\_LOG, DIAMOND\_BLOCK, GOLD\_BLOCK, IRON\_BLOCK |
| Ores | DIAMOND\_ORE, IRON\_ORE, GOLD\_ORE, COAL\_ORE, EMERALD\_ORE, DEEPSLATE\_DIAMOND\_ORE |
| Glass Panes | WHITE\_STAINED\_GLASS\_PANE, GRAY\_STAINED\_GLASS\_PANE, RED\_STAINED\_GLASS\_PANE, LIME\_STAINED\_GLASS\_PANE |
| Heads | PLAYER\_HEAD, ZOMBIE\_HEAD, SKELETON\_SKULL, WITHER\_SKELETON\_SKULL, CREEPER\_HEAD |
| GUI Misc | COMPASS, CLOCK, PAPER, BOOK, NAME\_TAG, MAP, FILLED\_MAP, KNOWLEDGE\_BOOK |
| Special | BARRIER, BEDROCK, COMMAND\_BLOCK, STRUCTURE\_VOID, LIGHT, SPAWNER, END\_PORTAL\_FRAME |
| Air / Empty | AIR — used for empty slots. Check: item.getType() == Material.AIR |

Common Enchantments

+

| Enchantment | Applies To | Max | Enchantment | Applies To | Max |
| --- | --- | --- | --- | --- | --- |
| DAMAGE\_ALL | Sword | V   | PROTECTION\_ENVIRONMENTAL | Armor | IV  |
| SHARPNESS | Sword/Axe | V   | PROTECTION\_FIRE | Armor | IV  |
| FIRE\_ASPECT | Sword | II  | FEATHER\_FALLING | Boots | IV  |
| KNOCKBACK | Sword | II  | DEPTH\_STRIDER | Boots | III |
| LOOTING | Sword | III | THORNS | Armor | III |
| POWER | Bow | V   | EFFICIENCY | Tools | V   |
| FLAME | Bow | I   | FORTUNE | Tools | III |
| INFINITY | Bow | I   | SILK\_TOUCH | Tools | I   |
| MENDING | Any | I   | UNBREAKING | Any | III |

Potion Effects Reference

+

| PotionEffectType | Effect | PotionEffectType | Effect |
| --- | --- | --- | --- |
| SPEED | Movement speed+ | SLOW | Movement speed- |
| FAST\_DIGGING | Haste (mining+) | SLOW\_DIGGING | Mining fatigue |
| INCREASE\_DAMAGE | Strength | WEAKNESS | Attack damage- |
| JUMP | Jump boost | LEVITATION | Float upward |
| REGENERATION | Health regen | POISON | Periodic damage |
| DAMAGE\_RESISTANCE | Resistance | WITHER | Wither damage |
| FIRE\_RESISTANCE | Fire immunity | HUNGER | Hunger drain |
| WATER\_BREATHING | Breathe water | SATURATION | Food restore |
| INVISIBILITY | Invisible | BLINDNESS | Screen darken |
| NIGHT\_VISION | See in dark | ABSORPTION | Yellow hearts |
| HEALTH\_BOOST | Extra hearts | GLOWING | Outline glow |

EntityType Quick Reference

+

| Passive | Neutral | Hostile | Boss / Special |
| --- | --- | --- | --- |
| COW | WOLF | ZOMBIE | ENDER\_DRAGON |
| PIG | SPIDER | SKELETON | WITHER |
| SHEEP | CAVE\_SPIDER | CREEPER | ELDER\_GUARDIAN |
| CHICKEN | ENDERMAN | WITCH | WARDEN |
| HORSE | POLAR\_BEAR | BLAZE | IRON\_GOLEM |
| VILLAGER | BEE | GHAST | SNOW\_GOLEM |
| RABBIT | PANDA | PHANTOM | ARMOR\_STAND |
| TURTLE | GOAT | PILLAGER | FALLING\_BLOCK |
| AXOLOTL | DOLPHIN | GUARDIAN | AREA\_EFFECT\_CLOUD |
| ALLAY | LLAMA | RAVAGER | ITEM\_DISPLAY |

function toggleCard(header) { const card = header.closest('.card'); card.classList.toggle('open'); } function copyCode(btn) { const pre = btn.nextElementSibling; navigator.clipboard.writeText(pre.innerText).then(() => { btn.textContent = 'copied!'; btn.classList.add('copied'); setTimeout(() => { btn.textContent = 'copy'; btn.classList.remove('copied'); }, 1800); }); } // Search const search = document.getElementById('search'); const noResults = document.getElementById('no-results'); search.addEventListener('input', () => { const q = search.value.toLowerCase().trim(); const sections = document.querySelectorAll('.section'); let any = false; sections.forEach(sec => { if (!q) { sec.style.display = ''; any = true; return; } const show = sec.innerText.toLowerCase().includes(q); sec.style.display = show ? '' : 'none'; if (show) any = true; }); noResults.style.display = any ? 'none' : 'block'; }); // Active nav on scroll const navLinks = document.querySelectorAll('.nav-item'); const observer = new IntersectionObserver(entries => { entries.forEach(entry => { if (entry.isIntersecting) { navLinks.forEach(l => l.classList.remove('active')); const link = document.querySelector(\`.nav-item\[href="#${entry.target.id}"\]\`); if (link) link.classList.add('active'); } }); }, { threshold: 0.15 }); document.querySelectorAll('.section').forEach(s => observer.observe(s)); HTMLEOF echo "Done! File size: $(wc -c < /mnt/user-data/outputs/logos-java-cheatsheet.html) bytes"
