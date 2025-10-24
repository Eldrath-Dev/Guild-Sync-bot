# Wayhaven Enforcer Bot

<p align="center">
  <img src="https://img.shields.io/badge/version-2.0-blue.svg" alt="Version">
  <img src="https://img.shields.io/badge/python-3.8+-blue.svg" alt="Python Version">
  <img src="https://img.shields.io/badge/discord.py-2.3.0+-blue.svg" alt="Discord.py">
  <img src="https://img.shields.io/badge/status-stable-green.svg" alt="Status">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License">
</p>

<p align="center">
  <strong>Enterprise-grade Discord moderation bot with cross-server punishment synchronization</strong>
</p>

---

## Table of Contents

- [About](#-about)
- [Features](#-features)
- [Getting Started](#-getting-started)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Commands](#-commands)
- [Architecture](#-architecture)
- [Setup Wizards](#-setup-wizards)
- [Advanced Features](#-advanced-features)
- [Monitoring](#-monitoring)
- [Migration Guide](#-migration-guide)
- [Troubleshooting](#-troubleshooting)
- [API Reference](#-api-reference)
- [Contributing](#-contributing)
- [License](#-license)

---

## About

Wayhaven Enforcer is a powerful Discord bot designed for managing moderation across multiple servers. It provides seamless punishment synchronization, ensuring consistent enforcement regardless of which server a user joins. The bot is built with scalability and reliability in mind, making it suitable for both small communities and large server networks.

## Key Benefits

- **Consistent Moderation**: Punishments applied on one server automatically sync to linked servers
- **Comprehensive Audit Trail**: Full logging and reporting of all moderation actions
- **Automatic Reconciliation**: Detects and resolves inconsistencies across server networks
- **Flexible Configuration**: Adapts to various server architectures and moderation needs
- **Enterprise Features**: System health monitoring, backup procedures, and disaster recovery

---

## Features

### Core Functionality

- Cross-server punishment synchronization
- Automatic event detection and propagation
- Time-based punishments (timeouts, temporary mutes)
- Audit logging and reporting
- System health monitoring
- Automatic reconciliation

### Moderation Actions

- `/ban` - Ban users across linked servers
- `/unban` - Remove bans across linked servers
- `/kick` - Kick users from multiple servers
- `/mute` - Apply timed or permanent mutes
- `/timeout` - Discord timeout with synchronization
- `/warn` - Issue warnings with tracking

### Administrative Features

- Dynamic server relationship management
- Multiple relationship types (sync, monitor, backup)
- Webhook notifications
- CSV audit export
- Command-line interface
- Database maintenance tools

---

## Getting Started

If you've never set up a Discord bot before, this section will guide you through the complete setup process. We'll cover everything from creating your bot account to performing your first moderation action.

### What the Bot Does

Wayhaven Enforcer automatically synchronizes moderation actions across multiple Discord servers. When you ban someone on one server, they're banned on all connected servers simultaneously. The bot handles:

- **Cross-server punishments**: Bans, mutes, kicks, timeouts, and warnings
- **Automatic synchronization**: No manual action needed on linked servers
- **Audit trail**: Complete logging of all moderation actions
- **Time-based punishments**: Automatic expiration for temporary penalties
- **Reconciliation**: Detects and fixes inconsistencies between servers

In short, one moderator action applies everywhere in your server network.

---

### Step 1: Get Your Bot Token

Every bot needs a token to join Discord. Create your bot at the [Discord Developer Portal](https://discord.com/developers/applications):

1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
2. Click "New Application"
3. Name your application (e.g., "Wayhaven Enforcer")
4. Go to the "Bot" section and click "Add Bot"
5. Copy the token - keep this secret!

### Step 2: Download and Install

1. Download the bot files from GitHub
2. Extract them to a folder on your computer
3. Install Python 3.8+ if you don't have it
4. Open a terminal/command prompt in the bot folder

### Step 3: Setup the Bot

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Create the database:
   ```bash
   python setup_database.py
   ```

3. Create a `.env` file in the bot folder:
   ```env
   BOT_TOKEN=your_bot_token_here
   APPLICATION_ID=your_application_id_beginning_number
   CLIENT_ID=your_client_id_number
   MAIN_GUILD_ID=your_main_server_id
   TEST_GUILD_ID=your_test_server_id
   DEBUG=false
   ```

   To find your server IDs: Right-click your server icon → "Copy ID" (Developer Mode must be enabled).

### Step 4: Invite Bot to Discord

1. Generate the invite URL:
   ```
   https://discord.com/oauth2/authorize?client_id=YOUR_CLIENT_ID&permissions=268561488&scope=bot%20applications.commands
   ```

2. Click the URL and invite the bot to your server

3. Start the bot:
   ```bash
   python bot.py
   ```

   You should see confirmation messages that the bot connected successfully.

---

### Step 5: Configure Basic Settings

Configure the bot's basic moderation settings:

1. **Set Mute Role**
   ```
   /config muterole role:@Muted
   ```
   (Create the @Muted role first if it doesn't exist)

2. **Configure Log Channel**
   ```
   /config notifications channel:#mod-logs enabled:true
   ```
   (This channel will show moderation notifications)

3. **Test Basic Functionality**
   ```
   /warn user:@testuser reason:Testing the bot
   ```
   (You should see a warning message appear)

---

### Step 6: Learn Basic Commands

The bot supports several key moderation commands:

**Issue a Warning**
```
/warn user:@username reason:Breaking server rules
```

**Apply a Timed Mute**
```
/mute user:@username duration:1h reason:Disruptive behavior
```

**Ban a User Across Servers**
```
/ban user:@username reason:Violation of community guidelines
```

**Unban a User**
```
/unban user:123456789 reason:Appeal accepted
```

*Note: Use Discord's "Copy ID" feature to get user IDs (enable Developer Mode first)*

---

### Step 7: Connect Multiple Servers (Optional)

For network-wide moderation, connect your servers:

1. **Set Main Server**
   ```
   /setup main-guild
   ```

2. **Add Child Servers**
   ```
   /setup add-child guild-id:123456789012345678
   ```
   (Get server ID by right-clicking server icon → Copy ID)

3. **Verify Setup**
   ```
   /setup dashboard
   ```

Once connected, punishments applied on one server automatically sync to linked servers.

---

### Troubleshooting Common Issues

**Bot not responding to commands:**
- Check if bot is online with a green status
- Verify admin permissions were granted
- Try typing `/` to see if commands appear
- Check `bot.log` for error messages

**Permission denied for admin commands:**
- You need Administrator role or equivalent permissions
- Contact server owner for proper role assignment

**Mute functionality not working:**
- Bot role must be higher than @Muted role
- Check @Muted role permissions
- Test with `/warn` first to ensure basic functionality

**Commands not executing:**
- Confirm bot has "Use Slash Commands" permission
- Try `/setup dashboard` for diagnostics
- Restart bot if needed

---

### Verification Checklist

- [ ] Bot appears online with green status
- [ ] Slash commands appear when typing `/`
- [ ] `/warn` command functions correctly
- [ ] `/setup dashboard` displays server information
- [ ] Mute functionality works (if configured)
- [ ] Notifications appear in configured channel

---

## Features

### Core Functionality

- **Cross-server punishment synchronization**: Real-time propagation of moderation actions across linked servers
- **Automatic event detection**: Monitors Discord events and triggers synchronization
- **Modern slash commands**: Full Discord slash command support with autocomplete
- **Comprehensive audit logging**: Complete track of all moderation actions and changes
- **Time-based punishments**: Support for temporary actions with automatic expiration
- **Reconciliation system**: Automatic detection and resolution of inconsistencies
- **Health monitoring**: System diagnostics and performance tracking

### Moderation Actions

- `/ban` - Ban users across linked servers
- `/unban` - Remove bans across linked servers
- `/kick` - Kick users from linked servers
- `/mute` - Apply timed or permanent mutes
- `/timeout` - Discord timeout synchronization
- `/warn` - Issue warnings with tracking

### Server Management

- **Dynamic server relationships**: Flexible configuration without hardcoded IDs
- **Relationship types**: Support for different sync modes (sync, monitor, backup)
- **Multi-server networks**: Complex hierarchical server architectures
- **Permission-based access**: Role-based command authorization

### Administration Tools

- **Setup wizards**: Guided configuration for different scenarios
- **Configuration dashboard**: Real-time system monitoring
- **Advanced audit commands**: Search, filter, and export moderation logs
- **Notification system**: Webhook and channel notifications
- **Data export**: CSV export capabilities for audit data

---

## Architecture Overview

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
