# 🔨 Wayhaven Enforcer Bot v2.0

A sophisticated Discord bot designed for **enterprise-grade cross-server moderation** and **punishment synchronization** across multiple linked Discord servers. Built with `discord.py` and SQLite for reliable, scalable moderation management that can handle complex server networks.

## 📋 Table of Contents

- [🚀 Features](#-features)
- [🏗️ Architecture Overview](#️-architecture-overview)
- [🛠 Installation & Setup](#-installation--setup)
- [🧙 Step-by-Step Setup Wizards](#-step-by-step-setup-wizards)
- [⚙️ Configuration](#️-configuration)
- [📚 Complete Command Reference](#-complete-command-reference)
- [🔄 How Everything Works](#-how-everything-works)
- [🔧 Advanced Features](#-advanced-features)
- [📊 Monitoring & Performance](#-monitoring--performance)
- [🔄 Migration Guide v1→v2](#-migration-guide-v1→v2)
- [🆘 Troubleshooting & Support](#-troubleshooting--support)
- [🛡️ Backup & Disaster Recovery](#️-backup--disaster-recovery)
- [🔌 API Reference (MCP Integration)](#-api-reference-mcp-integration)

---

## 🍼 First Time Admin Guide

### 👋 Welcome! Let's Set Up Your Bot Together! 🎉

**Hi there!** If you've never set up a Discord bot before, don't worry! This guide will walk you through everything step-by-step, like we're setting up a new game together. We'll go slow and I'll explain everything as we go.

---

### 🤔 What Does This Bot Do?

Imagine you have a big playground (that's your Discord server). Sometimes kids don't follow the rules, right? This bot is like a friendly crossing guard that:

🎯 **Keeps everyone safe** - Stops rule-breakers across ALL your servers
🤝 **Works as a team** - If someone gets in trouble on Server A, they're in trouble on Server B too
📝 **Takes notes** - Remembers everything so you can check who's been naughty
⏰ **Gives time-outs** - Makes loud kids be quiet for a while
✅ **Says sorry later** - Lets good kids come back when they're ready

**In short:** One punishment works everywhere! No more rule-breakers jumping between your servers. 😊

---

### 🚀 Step 1: Get Your Bot Token (The Secret Key) 🔑

Every bot needs a special "key" to join Discord. It's like getting a library card!

1. **Go to [Discord Developer Portal](https://discord.com/developers/applications)**
   - Log in with your Discord account
   - Click the blue "New Application" button

2. **Name Your Bot**
   - Call it "Wayhaven Enforcer" or whatever you like
   - Click "Create"

3. **Get the Bot Ready**
   - Click "Bot" on the left menu
   - Click "Add Bot"
   - Copy the "Token" - **this is super secret, like your password!**

---

### 📥 Step 2: Download & Prepare (Like Unboxing a New Toy) 🎁

1. **Get the Bot Files**
   - Click the green "Code" button on GitHub
   - Download ZIP and unzip it somewhere safe

2. **Install Python** (if you don't have it)
   - Go to [python.org](https://python.org)
   - Download and install Python 3.8 or higher

3. **Set Up the Secret Place**
   ```bash
   # Open a black window (called "Command Prompt" or "Terminal")
   # Go to where you unzipped the bot:
   cd "Wayhaven Punishment sync bot"

   # Get ready:
   pip install -r requirements.txt
   python setup_database.py
   ```

---

### ⚙️ Step 3: Tell the Bot Your Secrets (Configuration) 🤫

Create a file called `.env` in your bot folder. Put these words in it:

```env
BOT_TOKEN=your_secret_token_here
APPLICATION_ID=your_application_number
CLIENT_ID=your_client_id_number
MAIN_GUILD_ID=your_main_server_number
TEST_GUILD_ID=your_test_server_number
DEBUG=false
```

**Where do I find these numbers?**
- `BOT_TOKEN`: The secret key from Step 1
- `APPLICATION_ID`: Big number shown in your Discord Developer Portal
- `CLIENT_ID`: Also from Developer Portal
- `MAIN_GUILD_ID`: Right-click your main server → "Copy ID"
- `TEST_GUILD_ID`: Same for your test server

---

### 👋 Step 4: Invite Your Bot to Party (Discord) 🎊

1. **Make the Invite Link**
   ```
   https://discord.com/oauth2/authorize?client_id=YOUR_CLIENT_ID&permissions=268561488&scope=bot%20applications.commands
   ```

2. **Click the Link**
   - Pick your server from the dropdown
   - Check all the boxes that say "YES"
   - Click "Authorize"

3. **Start the Bot!**
   ```bash
   python bot.py
   ```
   - You should see: "Bot started successfully!"

---

### 🛠️ Step 5: Set Up Like Arranging Your Room (Basic Configuration) 🏠

Now your bot is in your server! Let's teach it the rules:

#### First, Tell It Where the "Quiet Corner" Is
```
/config muterole role:@Muted
```
*(Create a @Muted role first if you don't have one)*

#### Set Up Notification Channel
```
/config notifications channel:#mod-logs enabled:true
```
*(So you know when the bot does something)*

#### Test That Everything Works
```
/warn user:@someone reason:Testing the bot
```
*(You should see a warning message!)*

---

### 🎮 Step 6: Using Your Bot (Like Playing a Game) 🎲

#### Basic Commands (Easy Peasy)

**Stop Someone Being Mean:**
```
/warn user:@badguy reason:Being not nice
```

**Make Someone Take a Break:**
```
/mute user:@loudperson duration:1h reason:Too loud
```

**Remove Someone Completely:**
```
/ban user:@troublemaker reason:Breaking all rules
```

**Say Sorry and Let Them Back:**
```
/unban user:123456789 reason:Good behavior
```

**(The numbers are the person's Discord ID - right-click their name to copy)**

---

### 🌉 Step 7: Connect Multiple Servers (Advanced Magic) ✨

Want the same punishment to work on ALL your servers? Let's connect them!

1. **Pick Your Main Server**
   ```
   /setup main-guild
   ```

2. **Add Other Servers**
   ```
   /setup add-child guild-id:123456789012345678
   ```
   *(Get the guild ID by right-clicking the server name)*

3. **Check Everything Works**
   ```
   /setup dashboard
   ```

**Now:** If you ban someone on Server A, they're banned on Server B automatically! 🎉

---

### 🆘 Help! Something Isn't Working! 😰

#### "The bot isn't responding to commands"
1. Check if the bot is online (green circle)
2. Make sure you invited it with admin permissions
3. Try typing `/` and see if commands show up

#### "I can't use admin commands"
- You need "Administrator" permissions in the server
- Or ask the server owner to give you the right roles

#### "Mute role isn't working"
- Make sure the bot's role is ABOVE the @Muted role
- Check that @Muted role permissions are set correctly

#### "Nothing happens when I type commands"
1. Is the bot online?
2. Did you invite it with slash command permissions?
3. Try running `/setup dashboard` first

#### Still stuck? Ask for help!
- Check the fancy technical sections later in this guide
- Look at the bot's log file (`bot.log`) for error messages
- Ask in our Discord server (link at bottom)

---

### 🎉 Success Checkpoints (Make Sure Everything Works) ✅

- [ ] Bot is online (green dot)
- [ ] You can type `/` and see bot commands
- [ ] `/warn` command works
- [ ] `/setup dashboard` shows your server info
- [ ] You can mute someone successfully
- [ ] Logs appear in your chosen channel

**Congratulations! 🎊** You're now a bot expert! Your Discord servers are safer and your moderators have superpowers.

---

⭐ **Tip:** Come back to the advanced sections when you're ready for fancy features like webhooks, analytics, and complex server networks!

---

## 🚀 Features

### Core Functionality
- **🔗 Cross-Server Punishment Sync**: Real-time synchronization of punishments across linked servers
- **🤖 Auto-Detection**: Monitors ban/unban events and propagates punishments automatically
- **⚡ Slash Commands**: Modern Discord slash command interface with autocomplete
- **📊 Audit Trail**: Complete logging and audit system for all moderation actions
- **⏱️ Time-Based Punishments**: Support for temporary mutes, bans, and timeouts
- **🔍 Reconciliation System**: Automatic detection and resolution of punishment inconsistencies
- **❤️ Health Monitoring**: System health tracking and automated maintenance tasks

### Moderation Actions
- `/ban` - Cross-server ban with automatic sync
- `/unban` - Cross-server unban with automatic sync
- `/kick` - Cross-server kick with logging
- `/mute` - Timed or permanent mute with role management
- `/timeout` - Discord timeout with cross-server sync
- `/warn` - Warning system with warning count tracking

### Server Architecture
- **Dynamic Guild Relationships**: No hardcoded guild IDs - configure anywhere
- **Relationship Types**: Main-child hierarchy with different sync modes
- **Multi-Server Networks**: Support for complex server networks and hierarchies
- **Permission-Based Access**: Role-based command access control

### Administrative Features
- **Setup Wizards**: Interactive setup processes for different scenarios
- **Configuration Dashboard**: Real-time system status and health
- **Audit Commands**: Advanced search and export capabilities
- **Notification System**: Webhook and channel-based notifications
- **CSV Export**: Audit log export functionality

---

## 🏗️ Architecture Overview

### System Components

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Main Guild    │◄──►│   Sync Engine   │◄──►│  Child Guilds   │
│                 │    │                 │    │                 │
│ • Command Hub   │    │ • Queue System  │    │ • Auto-Sync     │
│ • Audit Logs    │    │ • Rate Limiting │    │ • Notifications │
│ • Dashboard     │    │ • Error Handling│    │ • Reconciliation│
└─────────────────┘    └─────────────────┘    └─────────────────┘
                              ▲
                              │
                       ┌─────────────────┐
                       │  SQLite Database│
                       │                 │
                       │ • Punishments   │
                       │ • Guild Config  │
                       │ • Audit Trail   │
                       │ • Relationships │
                       └─────────────────┘
```

### Data Flow

1. **Command Execution**: User issues punishment command in any linked guild
2. **Database Recording**: Punishment details stored with unique event ID
3. **Queue Processing**: Sync engine processes punishments in background queue
4. **Cross-Server Sync**: Punishment applied to all configured linked servers
5. **Audit Logging**: All actions logged to database and notified via channels/webhooks
6. **Reconciliation**: Automatic checks ensure consistency across servers

### Security Model

- **Role-Based Access**: Commands require specific Discord permissions
- **Audit Trail**: All actions are logged with moderator and reason tracking
- **Rate Limiting**: Built-in delays prevent Discord API abuse
- **Permission Validation**: Real-time permission checking before actions

---

## 🛠 Installation & Setup

### Prerequisites

- **Python 3.8+** (recommended: 3.9+)
- **Discord Bot Token** from [Discord Developer Portal](https://discord.com/developers/applications)
- **Administrative Access** in target Discord servers
- **Stable Internet Connection** for real-time sync

### Required Discord Permissions

The bot needs these permissions in ALL servers:

```
✅ Read Messages          ✅ Send Messages
✅ Use Slash Commands     ✅ Ban Members
✅ Kick Members           ✅ Moderate Members (for timeout)
✅ Manage Roles           ✅ View Audit Log
✅ Read Message History   ✅ Embed Links
```

### Step-by-Step Installation

#### 1. Download & Extract

```bash
# Clone or download the bot files
git clone <repository-url>
cd "Wayhaven Punishment sync bot"
```

#### 2. Create Virtual Environment

```bash
# Create isolated Python environment
python -m venv venv

# Activate environment
# Windows:
venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate
```

#### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

#### 4. Create Bot Application

1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
2. Click "New Application" → Name: "Wayhaven Enforcer"
3. Go to "Bot" section → Click "Add Bot"
4. Copy the **Bot Token** (keep this secret!)

#### 5. Configure Environment

```bash
# Copy template (update with your token)
cp .env.example .env
```

Edit `.env` file:
```env
BOT_TOKEN=your_bot_token_here
APPLICATION_ID=your_application_id
CLIENT_ID=your_client_id
CLIENT_SECRET=your_client_secret
MAIN_GUILD_ID=your_main_server_id
TEST_GUILD_ID=your_test_server_id
DEBUG=false
```

#### 6. Initialize Database

```bash
python setup_database.py
```

#### 7. Start the Bot

```bash
python bot.py
```

**Expected Output:**
```
INFO - WayhavenEnforcer - Bot started successfully
INFO - WayhavenEnforcer - Connected to Discord
INFO - WayhavenEnforcer - Loaded 6 cogs
INFO - WayhavenEnforcer - Slash commands synced
```

#### 8. Invite Bot to Servers

Generate invite URL: `https://discord.com/oauth2/authorize?client_id=YOUR_CLIENT_ID&permissions=268561488&scope=bot%20applications.commands`

**Minimum Required Permissions:** `268,561,488`

---

## 🧙 Step-by-Step Setup Wizards

### Wizard 1: Single Server Setup

**For servers that want basic moderation without cross-server sync**

1. **Invite Bot** to your server
2. **Set Basic Configuration**
   ```discord
   /config muterole role:@Muted
   /config logchannel channel:#mod-logs
   /config notifications channel:#mod-alerts enabled:true
   ```
3. **Test Commands**
   ```discord
   /warn user:@baduser reason:Testing warnings
   ```
4. **View Dashboard**
   ```discord
   /setup dashboard
   ```

### Wizard 2: Main Server Setup

**For servers that will be the central moderation hub**

1. **Configure Basic Settings**
   ```discord
   /setup main-guild  # Set as main guild
   /config muterole role:@Muted
   /config logchannel channel:#sync-logs
   /config webhook webhook-url:"https://discord.com/api/webhooks/..."
   ```

2. **Create Backup Channels**
   ```discord
   # Create these channels first
   #mod-commands, #sync-notifications, #reconciliation-alerts
   /config notifications channel:#sync-notifications enabled:true
   /config logchannel channel:#mod-commands
   ```

3. **Set Security Roles**
   ```discord
   # Create and assign staff role with proper permissions
   /config staffrole role:@Server Staff
   ```

4. **Test Configuration**
   ```discord
   /config show  # Verify all settings
   ```

### Wizard 3: Child Server Linking

**For servers that want to join an existing moderation network**

1. **Get Main Guild ID**
   ```
   Right-click main server → Copy ID (Developer Mode must be ON)
   Main Guild ID: 123456789012345678
   ```

2. **Link to Main Guild**
   ```discord
   /guildlink guild-id:123456789012345678 mode:MAIN_ONLY
   ```

3. **Configure Local Settings**
   ```discord
   /config muterole role:@Muted
   /config notifications channel:#moderation enabled:true
   ```

4. **Verify Connection**
   ```discord
   /setup test-connection guild-id:123456789012345678
   ```

### Wizard 4: Multi-Server Network Setup

**For complex networks with multiple main servers**

1. **Server Architecture Planning**
   ```
   Hierarchy: Main A → Child B, Child C
   Hierarchy: Main X → Child Y, Child Z
   Bidirectional: Main A ↔ Main X
   ```

2. **Setup Each Main Server**
   ```discord
   # Server A (Main)
   /setup main-guild
   /setup add-child guild-id:BBBBBBBBBBBBBBBBB relationship-type:sync
   /setup add-child guild-id:CCCCCCCCCCCCCCCCC relationship-type:sync

   # Server X (Main)
   /setup main-guild
   /setup add-child guild-id:YYYYYYYYYYYYYYYYY relationship-type:monitor
   /guildlink guild-id:AAAAAAAAAAAAAAAAAAAA mode:BIDIRECTIONAL
   ```

3. **Configure Sync Actions**
   ```discord
   # Default actions: ban, unban, kick, mute, warn, timeout
   # Customize per relationship in database if needed
   ```

4. **Setup Monitoring**
   ```discord
   # Set up webhook for cross-network alerts
   /config webhook webhook-url:"https://discord.com/api/webhooks/..."
   /setup dashboard  # Check status
   ```

### Wizard 5: Emergency/Backup Server Setup

**For servers that only receive syncs during emergencies**

1. **Configure as Backup**
   ```discord
   /guildlink guild-id:MAINGUILDID mode:MAIN_ONLY
   # Actions will only sync during reconciliation or manual triggers
   ```

2. **Setup Alert System**
   ```discord
   /config webhook webhook-url:"https://discord.com/api/webhooks/..."
   ```

---

## ⚙️ Configuration

### Environment Variables (.env)

```env
# Required Settings
BOT_TOKEN=MTE0MjM0...  # Your Discord bot token
APPLICATION_ID=1423440206492729364  # Bot application ID
CLIENT_ID=1423440206492729364       # Client ID
CLIENT_SECRET=secret_here            # Client secret
MAIN_GUILD_ID=your_main_server_id   # Primary server ID
TEST_GUILD_ID=test_server_id        # Development server ID

# Optional Settings
DATABASE_URL=sqlite+aiosqlite:///wayhaven_enforcer.db
DEBUG=false                          # Enable debug logging
SYNC_DELAY=2                         # Seconds between sync operations
RECONCILIATION_INTERVAL=21600        # 6 hours in seconds
```

### Advanced Configuration Options

#### Sync Settings
```python
# In config.py - adjust these for performance
SYNC_DELAY = 2          # Rate limiting (1-5 seconds)
MAX_RETRY_ATTEMPTS = 3  # API failure retries
```

#### Reconciliation Timing
```python
RECONCILIATION_INTERVAL = 21600  # Check every 6 hours
```

#### Color Scheme
```python
COLORS = {
    'success': 0x00ff00,    # Green
    'error': 0xff0000,      # Red
    'warning': 0xffff00,    # Yellow
    'info': 0x0099ff,       # Blue
    'ban': 0xff0000,        # Red
    'mute': 0xffa500,       # Orange
    'kick': 0xff6b6b,       # Light Red
    'warn': 0xffff00,       # Yellow
}
```

#### Notification Templates

All notifications use embedded messages with:
- **Action Icons**: 🔨 (ban), ✅ (unban), 🔇 (mute), ⚠️ (warn)
- **Color Coding**: Action-specific colors
- **Timestamps**: UTC time with relative formatting
- **Structured Data**: User, moderator, reason, expiration

---

## 📚 Complete Command Reference

### 🔗 Setup Commands (`/setup`)

| Command | Description | Permissions | Example |
|---------|-------------|-------------|---------|
| `/setup main-guild` | Set server as main guild | Administrator | `/setup main-guild` |
| `/setup add-child` | Link child server | Administrator | `/setup add-child guild-id:123456789` |
| `/setup remove-child` | Remove child server | Administrator | `/setup remove-child guild-id:123456789` |
| `/setup test-connection` | Test server connection | Administrator | `/setup test-connection guild-id:123456789` |
| `/setup config-wizard` | Start setup wizard | Administrator | `/setup config-wizard` |
| `/setup dashboard` | View configuration dashboard | Administrator | `/setup dashboard` |

### ⚙️ Configuration Commands (`/config`)

| Command | Description | Permissions | Example |
|---------|-------------|-------------|---------|
| `/config muterole` | Set mute role | Administrator | `/config muterole role:@Muted` |
| `/config logchannel` | Set log channel | Administrator | `/config logchannel channel:#logs` |
| `/config notifications` | Set notification channel | Administrator | `/config notifications channel:#alerts enabled:true` |
| `/config webhook` | Set webhook URL | Administrator | `/config webhook webhook-url:"https://..."` |
| `/config show` | Show current config | Administrator | `/config show` |
| `/guildlink` | Link to another guild | Administrator | `/guildlink guild-id:123456789 mode:MAIN_ONLY` |
| `/config unlink` | Remove guild link | Administrator | `/config unlink guild-id:123456789` |

### 🔨 Moderation Commands

| Command | Description | Permissions | Example |
|---------|-------------|-------------|---------|
| `/ban` | Ban user across servers | Ban Members | `/ban user:@user reason:Spam` |
| `/unban` | Unban user across servers | Ban Members | `/unban user:123456789 reason:Appeal accepted` |
| `/kick` | Kick user across servers | Kick Members | `/kick user:@troublemaker reason:Disruption` |
| `/mute` | Mute user with duration | Manage Roles | `/mute user:@user duration:1d reason:Flooding` |
| `/timeout` | Discord timeout | Moderate Members | `/timeout user:@user duration:2h reason:Trolling` |
| `/warn` | Issue warning | Moderate Members | `/warn user:@user reason:Inappropriate content` |

### 📊 Audit Commands (`/audit`)

| Command | Description | Permissions | Example |
|---------|-------------|-------------|---------|
| `/audit log` | View user's punishment history | Moderate Members | `/audit log user:@user days:30` |
| `/audit stats` | View server statistics | Moderate Members | `/audit stats days:7` |
| `/audit warnings` | View user's warnings | Moderate Members | `/audit warnings user:@user` |
| `/audit search` | Search audit logs | Moderate Members | `/audit search action:ban days:7` |
| `/audit export` | Export logs to CSV | Administrator | `/audit export days:30` |

### 🔍 Reconciliation Commands (`/reconcile`)

| Command | Description | Permissions | Example |
|---------|-------------|-------------|---------|
| `/reconcile check` | Check discrepancies | Administrator | `/reconcile check` |
| `/reconcile fix` | Fix discrepancies | Administrator | `/reconcile fix dry-run:true` |
| `/reconcile status` | Show reconciliation status | Administrator | `/reconcile status` |

### 🔄 Sync Commands (`/sync`)

| Command | Description | Permissions | Example |
|---------|-------------|-------------|---------|
| `/forcesync` | Force sync user's punishments | Administrator | `/forcesync user:@user` |
| `/syncstatus` | Show sync system status | Administrator | `/syncstatus` |

---

## 🔄 How Everything Works

### 1. Command Execution Flow

```
User Command → Permission Check → Database Entry → Event Queue → Sync Processing
       ↓             ↓              ↓              ↓            ↓
    Validate    Check Roles     Create Event    Queue Event  Process Sync
```

### 2. Punishment Synchronization Mechanism

```
Main Guild Action ──┐
                     ├── Event Detection (Automatic)
Punishment Issued ───┤
                     └── Manual Command (Slash Commands)

                        ↓

Database Recording ── Event ID Created ── Audit Log Entry

                        ↓

Queue System ─────── Background Processing ── Rate Limiting Applied

                        ↓

Linked Guilds ────── Permission Checks ─── Action Applied ── Notification Sent
     │                      │                      │                   │
     └─ Child Guild 1      └─ Role Check          └─ Ban/Kick/Mute   └─ Webhook/Channel
       Child Guild 2        API Call               Success/Failure    Audit Update
       Child Guild 3        Error Handling         Database Update    Moderator Alert
       Child Guild N        Retry Logic
```

### 3. Event Detection System

- **Automatic Monitoring**: Listens for `on_member_ban`, `on_member_unban` events
- **Audit Log Parsing**: Extracts moderator and reason from Discord audit logs
- **Queue Processing**: Prevents rate limiting with configurable delays
- **Error Handling**: Retry logic for failed API calls

### 4. Database Architecture

```sql
-- Core Tables
punishments (events, users, actions, reasons, timestamps)
guild_relationships (server links, sync settings)
guild_settings (per-server configuration)
audit_logs (detailed action history)
system_health (monitoring and diagnostics)
```

### 5. Relationship Types

- **Sync**: Full bidirectional synchronization
- **Monitor**: One-way monitoring (child → main only)
- **Backup**: Emergency backup (manual triggers only)

### 6. Action Propagation Logic

Each punishment goes through:

1. **Pre-Check**: Permission validation, role verification
2. **Recording**: Database entry with unique event ID
3. **Queue**: Background processing queue
4. **Execution**: Apply to linked servers with rate limiting
5. **Verification**: Check success/failure
6. **Notification**: Alert via webhooks/channels
7. **Audit**: Log all actions for compliance

### 7. Reconciliation System

- **Periodic Checks**: Runs every 6 hours (configurable)
- **Discrepancy Detection**: Compares ban lists across servers
- **Auto-Resolution**: Fixes missing punishments
- **Reporting**: Alerts in log channels for manual review
- **Health Monitoring**: Tracks system status and performance

---

## 🔧 Advanced Features

### Custom Sync Actions

Control which actions sync per relationship:

```sql
-- Examples
["ban", "unban"]              -- Ban sync only
["mute", "kick", "warn"]      -- Light moderation
["ban", "unban", "timeout"]   -- All heavy moderation
```

### Webhook Notifications

```json
{
  "embeds": [{
    "title": "🔨 User Banned (Synced)",
    "color": 16711680,
    "fields": [
      {"name": "👤 User", "value": "@username (123456789)"},
      {"name": "📝 Reason", "value": "Violation of rules"},
      {"name": "🏠 Source Server", "value": "Main Server"}
    ]
  }]
}
```

### Performance Tuning

```python
# config.py adjustments
SYNC_DELAY = 1                    # Faster sync (higher rate limit risk)
RECONCILIATION_INTERVAL = 3600    # Check hourly
MAX_RETRY_ATTEMPTS = 5            # More resilient
```

### Complex Network Architectures

#### Hierarchical Setup
```
Main Server A
├── Child Server B
├── Child Server C
│   └── Child Server D (B's child)
└── Child Server E
```

#### Group Setup
```
Cluster 1 ── Cluster 2
├── Server A ── Server X
├── Server B ── Server Y
└── Server C ── Server Z
```

#### Hybrid Setup
```
Main Network + Independent Servers
├── Synced Guilds (full sync)
├── Monitored Guilds (alerts only)
└── Backup Guilds (emergency only)
```

---

## 📊 Monitoring & Performance

### Health Monitoring

The bot tracks multiple components:

- **Database**: Connection status, query performance
- **API**: Discord API rate limits, response times
- **Sync Engine**: Queue status, processing delays
- **Reconciliation**: Scan completion, discrepancy counts

### Performance Metrics

```python
# Track these metrics:
sync_success_rate = successful_syncs / total_syncs * 100
average_sync_time = total_time / sync_count
queue_backlog = queue.size()
error_rate = errors / total_operations * 100
```

### System Logs

All actions logged to `bot.log`:

```
2025-01-20 10:30:15 - INFO - Sync completed: 3 successful, 0 failed
2025-01-20 10:30:20 - WARNING - Rate limit approached, slowing sync
2025-01-20 10:35:00 - INFO - Reconciliation found 1 discrepancy, auto-resolved
```

### Dashboard Information

`/setup dashboard` shows:

- Total linked guilds
- Recent activity (7 days)
- System health status
- Sync performance metrics
- Active tasks status

---

## 🔄 Migration Guide v1→v2

### What's New in v2.0

1. **Dynamic Configuration**: No hardcoded guild IDs
2. **Relationship System**: Flexible server linking
3. **Health Monitoring**: System diagnostics
4. **Enhanced Timeouts**: Discord timeout support
5. **Queue System**: Better sync processing
6. **Notification Webhooks**: Advanced alerting

### Migration Steps

#### Step 1: Backup Database

```bash
cp wayhaven_enforcer.db wayhaven_enforcer_v1_backup.db
```

#### Step 2: Update Code

```bash
# Pull latest changes
git pull origin main
```

#### Step 3: Install New Dependencies

```bash
pip install -r requirements.txt  # May include new packages
```

#### Step 4: Run Migration Script

```bash
python migrate_to_v2.py
```

**Expected Output:**
```
🛠️  Wayhaven Enforcer Database Migration v1 → v2
==================================================
INFO - Starting migration from v1 to v2...
INFO - Current database version: 1.0
INFO - Creating new tables...
INFO - Adding indexes...
INFO - Migrating existing guild links...
INFO - Migration v1 -> v2 completed successfully!
✅ Validation passed!
```

#### Step 5: Update Configuration

Remove hardcoded values from `config.py`:

```python
# OLD (v1)
MAIN_GUILD_ID = 123456789
TEST_GUILD_ID = 987654321

# NEW (v2) - Use environment variables
MAIN_GUILD_ID = int(os.getenv('MAIN_GUILD_ID'))
TEST_GUILD_ID = int(os.getenv('TEST_GUILD_ID'))
```

#### Step 6: Update Environment Variables

```env
# Add these new variables
MAIN_GUILD_ID=your_main_server_id
TEST_GUILD_ID=your_test_server_id
DEBUG=false
```

#### Step 7: Reconfigure Server Relationships

```discord
# Recreate your server links using new commands
/setup main-guild
/setup add-child guild-id:987654321

# Instead of old hardcoded configuration
```

#### Step 8: Test New Features

```discord
# Test new timeout command
/timeout user:@testuser duration:5m reason:Testing v2.0

# Check system health
/setup dashboard

# Test reconciliation
/reconcile check
```

#### Step 9: Monitor Migration

```bash
# Check logs for any issues
tail -f bot.log

# Verify all relationships
/config show
```

### Rollback Plan

If migration fails:

1. **Stop Bot**: `Ctrl+C`
2. **Restore Backup**: `cp wayhaven_enforcer_v1_backup.db wayhaven_enforcer.db`
3. **Revert Code**: `git checkout v1.0`
4. **Restart**: `python bot.py`

### Migration Checklist

- [ ] Database backed up
- [ ] Migration script run successfully
- [ ] Configuration updated
- [ ] Environment variables set
- [ ] Server relationships recreated
- [ ] Permission tests passed
- [ ] New commands tested
- [ ] Webhooks configured
- [ ] Dashboard operational
- [ ] Logs monitoring active

---

## 🆘 Troubleshooting & Support

### Common Issues

#### "Bot not responding to commands"
```
✅ Check bot is online
✅ Verify bot permissions in server settings
✅ Confirm slash commands synced: `@bot-name`
✅ Check bot.log for error messages
```

#### "Sync not working"
```
✅ Test connection: /setup test-connection
✅ Verify permissions in target server
✅ Check rate limits in logs
✅ Confirm relationship type allows sync
```

#### "Mute role not working"
```
✅ Set mute role: /config muterole
✅ Ensure bot has "Manage Roles" permission
✅ Check role hierarchy (bot role above mute role)
✅ Test role permissions manually
```

#### "Database errors"
```
✅ Check database file exists
✅ Verify write permissions on folder
✅ Run integrity check: sqlite3 wayhaven_enforcer.db "PRAGMA integrity_check;"
✅ Restore from backup if corrupted
```

#### "Webhook notifications failing"
```
✅ Verify webhook URL is valid
✅ Check webhook permissions in target channel
✅ Test webhook manually with curl
✅ Enable webhook in config
```

### Error Codes

| Error | Meaning | Solution |
|-------|---------|----------|
| `403 Forbidden` | Missing permissions | Grant required roles |
| `429 Rate Limited` | Too many requests | Wait and retry |
| `404 Not Found` | User/guild not found | Verify IDs are correct |
| `500 Internal Server Error` | Discord API issue | Retry later |

### Debug Mode

Enable detailed logging:

```python
# In .env
DEBUG=true

# Restart bot, check bot.log for details
tail -f bot.log
```

### Contact Support

1. **Check Logs**: `tail -f bot.log` for error details
2. **Run Diagnostics**: `/setup dashboard` for system status
3. **Test Components**: `/setup test-connection` for connectivity
4. **Export Data**: `/audit export` for investigation

---

## 🛡️ Backup & Disaster Recovery

### Automated Backups

```bash
# Create daily backup script (backup.sh)
#!/bin/bash
DATE=$(date +%Y%m%d_%H%M%S)
cp bot.log bot_$DATE.log
cp wayhaven_enforcer.db wayhaven_enforcer_$DATE.db
echo "Backup created: $DATE"
```

### Database Maintenance

```sql
-- Regular maintenance commands
VACUUM;                    -- Reclaim space
REINDEX;                   -- Optimize indexes
PRAGMA integrity_check;    -- Verify database health
```

### Recovery Procedures

#### Database Corruption
```bash
# Stop bot
pkill -f "python bot.py"

# Restore from backup
cp wayhaven_enforcer_backup.db wayhaven_enforcer.db

# Reindex if needed
sqlite3 wayhaven_enforcer.db "REINDEX;"

# Restart bot
python bot.py
```

#### Configuration Loss
```bash
# Recreate relationships
/setup main-guild
/setup add-child guild-id:SERVER_ID

# Restore settings
/config muterole role:@Muted
/config webhook webhook-url:"https://..."
```

#### Multiple Server Failure
```bash
# Use reconciliation to sync everything
/reconcile check
/reconcile fix dry-run:false

# Force full resync
/audit log days:1  # Identify recent actions
/forcesync user:@user  # Resync individual users
```

### High Availability Setup

```
┌─────────────────┐    ┌─────────────────┐
│   Primary Bot   │    │  Backup Bot     │
│   (Active)      │    │  (Standby)      │
└─────────────────┘    └─────────────────┘
          │                       │
          └─────── Shared ────────┘
                  Database
                      │
               ┌─────────────────┐
               │   File Backup   │
               │   (Daily)       │
               └─────────────────┘
```

---

## 🔌 API Reference (MCP Integration)

The bot can be integrated with external systems via Model Context Protocol (MCP).

### Server Registration

```json
{
  "mcpServers": {
    "wayhaven-enforcer": {
      "command": "python",
      "args": ["/path/to/bot.py", "--mcp"],
      "env": {
        "BOT_TOKEN": "token",
        "DATABASE_URL": "sqlite:///db"
      }
    }
  }
}
```

### Available MCP Tools

#### `execute_moderation_action`

Execute a moderation action across servers.

**Parameters:**
- `action`: "ban" | "kick" | "mute" | "warn"
- `user_id`: Discord user ID (string)
- `reason`: Reason for action (string)
- `duration`: Duration for temporary actions (optional)
- `guild_id`: Source guild ID (optional - uses main if not specified)

**Returns:**
```json
{
  "success": true,
  "event_id": "12345",
  "synced_guilds": ["guild1", "guild2"],
  "errors": []
}
```

#### `query_audit_logs`

Query audit logs with filtering.

**Parameters:**
- `user_id`: Filter by user ID (optional)
- `action`: Filter by action type (optional)
- `guild_id`: Filter by guild ID (optional)
- `days`: Days to look back (default: 30)
- `limit`: Maximum results (default: 100)

**Returns:**
```json
{
  "logs": [
    {
      "event_id": "12345",
      "timestamp": "2025-01-20T10:30:00Z",
      "user_id": "987654321",
      "action": "ban",
      "reason": "Rule violation",
      "moderator_id": "111222333",
      "guild_id": "123456789"
    }
  ],
  "total": 1,
  "filtered": false
}
```

#### `get_system_health`

Get current system health status.

**Parameters:**
- `component`: Specific component to check (optional)

**Returns:**
```json
{
  "overall_status": "healthy",
  "components": {
    "database": {"status": "healthy", "last_check": "2025-01-20T10:30:00Z"},
    "sync_engine": {"status": "healthy", "queue_size": 0},
    "reconciliation": {"status": "healthy", "last_run": "2025-01-20T10:25:00Z"}
  }
}
```

#### `sync_user_punishments`

Force synchronization of a user's active punishments.

**Parameters:**
- `user_id`: Discord user ID (required)
- `guild_id`: Source guild ID (optional)

**Returns:**
```json
{
  "success": true,
  "user_id": "987654321",
  "actions_synced": 2,
  "target_guilds": ["guild1", "guild2"],
  "errors": []
}
```

---

## ⚠️ Important Notes

### Security Considerations
- Always use HTTPS webhooks for production
- Regularly rotate bot tokens
- Limit `/config` commands to trusted administrators only
- Monitor audit logs for unauthorized access
- Use environment variables for sensitive configuration

### Performance Guidelines
- **Rate Limiting**: Sync delays prevent Discord API abuse
- **Database Optimization**: Regular VACUUM operations recommended
- **Monitoring**: Set up alerts for sync failures
- **Backup Frequency**: Daily backups for critical deployments
- **Resource Allocation**: Monitor memory usage in high-traffic servers

### Compliance & Privacy
- Audit logs contain user data - comply with local privacy laws
- User punishment data is stored permanently unless manually deleted
- Bot actions are attributed to moderators - maintain accountability
- Cross-server data sharing requires user consent in some jurisdictions

### Support Channels
- **Documentation**: This README.md provides comprehensive guidance
- **Logs**: Check `bot.log` for detailed error information
- **Commands**: Use `/setup dashboard` for real-time diagnostics
- **Community**: Join our Discord server for peer support

---

## 📈 Future Roadmap

### Planned Features v2.1+
- **Advanced Analytics**: Punishment trends and user behavior analysis
- **Custom Integration**: REST API for external moderation tools
- **Multi-Platform Support**: Integration with other chat platforms
- **Machine Learning**: Automated spam detection and user risk assessment
- **Advanced Filtering**: Custom rules for automated moderation

### Contributing
We welcome contributions! Please:
1. Fork the repository
2. Create a feature branch
3. Add comprehensive tests
4. Update documentation
5. Submit a pull request

### License
This project is licensed under the MIT License. See LICENSE file for details.

---

**🎉 Thank you for choosing Wayhaven Enforcer Bot v2.0!**

*This README provides comprehensive guidance for setting up and operating your enterprise-grade Discord moderation bot. For additional support, please refer to the troubleshooting section or join our community Discord server.*
