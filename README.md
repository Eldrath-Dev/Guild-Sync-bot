# Wayhaven Enforcer Bot

[![Version](https://img.shields.io/badge/version-2.1.0-blue.svg)](https://github.com)
[![Python](https://img.shields.io/badge/python-3.8+-brightgreen.svg)](https://www.python.org/)
[![Discord API](https://img.shields.io/badge/discord-api--v2.3+-7289da.svg)](https://discord.com/developers/docs/intro)
[![Platforms](https://img.shields.io/badge/platforms-Windows%20%7C%20Mac%20%7C%20Linux-lightgrey.svg)](https://github.com)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com)
[![Database](https://img.shields.io/badge/database-SQLite-yellow.svg)](https://sqlite.org/)
[![Commands](https://img.shields.io/badge/commands-slash%20commands-orange.svg)](https://discord.com/developers/docs/interactions/slash-commands)

---

## 📚 Getting Started

### What is Wayhaven Enforcer?

Imagine you have a school with many classrooms and playgrounds. Sometimes a student might break rules in one classroom and then try to run to another classroom to keep causing trouble. That's not fair to the other students who follow the rules!

**Wayhaven Enforcer** is like having a Principal who can see what happens in ALL the classrooms at once. When a student gets in trouble in the cafeteria, they automatically get the same fair consequence in the gym, library, and computer lab too. No more running between classrooms to avoid getting caught!

### How The School System Works

Think of Wayhaven like a school rule system that works across multiple class periods:

**The Problem:** A student gets in trouble in Math class for talking too much. They just switch to Science class and keep talking.

**The Old Way:** Teachers have to communicate separately - messy and inconsistent.

**Wayhaven's Solution:** Like having school-wide detention slips that apply everywhere automatically!

**Main Server (Principal's Office):** Can issue punishments that spread everywhere
**Child Servers (Classrooms):** Get notified and follow the same rules, but can't punish the whole school
**ZERO-LEAK Security:** Prevents any single teacher from accidentally punishing everyone
**Complete Audit Trail:** Everyone knows who did what and when

### Key Features

| Feature | Description |
|---------|-------------|
| **Cross-Server Sync** | Punishments from main server automatically apply to all connected servers |
| **ZERO-LEAK Security** | Only designated main servers can spread punishments - maximum safety |
| **Complete Audit System** | Every action logged with full compliance tracking |
| **Professional Moderation** | Ban, kick, mute, timeout, and warning commands |
| **GDPR Compliant** | Built-in data protection and user rights management |
| **Easy Setup** | Step-by-step configuration wizard for any skill level |

### Why Schools And Communities Love It

- **Consistent Rules:** Same consequences across all your Discord servers
- **No More Rule Breakers:** Users can't just switch servers to avoid punishment
- **Professional Management:** Enterprise-grade moderation tools
- **Complete Visibility:** Full audit trail of all moderation actions
- **Safe & Secure:** ZERO-LEAK protection prevents accidental network-wide punishments

---

## 🛠️ Installation & Setup

### Prerequisites

Before you begin, ensure you have:

| Requirement | Version | Purpose |
|-------------|---------|---------|
| **Python** | 3.8 or higher | Main programming language |
| **Discord Account** | Any | For bot creation and server management |
| **Administrator Access** | Required | Full control of Discord servers |

### Step 1: Install Python

Python is the "language" that tells your computer how to run Wayhaven. It's completely free!

#### For Windows Users:
1. Visit `https://python.org/downloads/`
2. Click the yellow "Download Python 3.12.0" button
3. Run the downloaded installer
4. **IMPORTANT:** Check the box "Add Python to PATH"
5. Click "Install Now" and wait 2-3 minutes

#### For Mac Users:
1. Visit `https://python.org/downloads/`
2. Download the macOS installer
3. Double-click the .pkg file to install
4. Open Terminal and test with: `python3 --version`

#### For Linux Users:
```bash
# Ubuntu/Debian:
sudo apt update && sudo apt install python3 python3-pip -y

# Fedora/RHEL:
sudo dnf install python3 python3-pip -y

# Test installation:
python3 --version
pip3 --version
```

### Step 2: Get The Bot Files

1. **Download the source code:**
   - Download from your repository
   - Click the green "Code" button
   - Select "Download ZIP"
   - Save to Desktop or Documents folder

2. **Extract the ZIP file** (right-click → Extract All)

3. **Verify you have these important files:**
   ```
   📁 bot.py           # Main bot brain
   📁 database.py      # Memory system
   📁 config.py        # Settings brain
   📁 requirements.txt # List of helpers needed
   📁 cogs/           # Bot command modules
       📁 punishments.py   # Warning/mute/ban commands
       📁 sync.py         # Cross-server spreading
       📁 setup_cog.py    # Server configuration
       📁 audit.py        # Who did what tracking
   ```

### Step 3: Install Required Programs

```bash
# Navigate to your bot folder (adjust the path as needed)
cd "path/to/your/bot/folder"

# Install all the programs Wayhaven needs to run
pip install -r requirements.txt
```

**These programs do the following:**
- `discord.py` - Connects to Discord servers
- `python-dotenv` - Manages configuration settings
- `aiosqlite` - Stores and retrieves data
- `sqlalchemy` - Complex database operations
- `aiofiles` - File operations

**If you get errors, try these alternatives:**
```bash
# Alternative installation methods
pip3 install -r requirements.txt
python -m pip install -r requirements.txt
python3 -m pip install -r requirements.txt
```

### Step 4: Set Up Discord Bot Account

**⚠️ IMPORTANT:** You must be an administrator of the Discord servers for this step!

#### Step 4.1: Create Application:
1. Go to `https://discord.com/developers/applications`
2. Click "New Application" (blue button, top right)
3. Name it "Wayhaven Enforcer" or your preferred name
4. Accept the terms and conditions

#### Step 4.2: Create Bot User:
1. Click "Bot" in the left sidebar menu
2. Click "Add Bot" button
3. Skip special privileges for now
4. You can set an avatar if you want

#### Step 4.3: Get Secret Bot Token:
1. Under "Token" section, click "Copy"
2. **⚠️ KEEP THIS SECRET:** This is like a password for your bot
3. Never share it in chat or save in plain text files

#### Step 4.4: Set Bot Permissions:
1. Scroll to "Bot Permissions" section
2. Enable ALL these permissions:
   - ✅ Read Messages/View Channels
   - ✅ Send Messages
   - ✅ Use Slash Commands
   - ✅ Ban Members
   - ✅ Kick Members
   - ✅ Manage Roles
   - ✅ Moderate Members
   - ✅ View Audit Log
   - ✅ Read Message History

3. Copy the permission number (usually 268561488)
4. Note your Application ID from "General Information"

#### Step 4.5: Invite Bot to Servers:
1. Go to OAuth2 → URL Generator
2. Check "bot" and "applications.commands"
3. Copy the generated invite URL
4. Open in browser and authorize for each server
5. Verify bot appears online in member list

**Remember:** Invite bot to EVERY server you want to moderate!

### Step 5: Configure Settings

Create a `.env` file in your bot folder with these settings:

```env
# Wayhaven Enforcer Configuration
# Replace with your actual information!

# Bot Account Information
BOT_TOKEN=your_secret_token_here_really_replace_this
APPLICATION_ID=123456789012345678
CLIENT_ID=123456789012345678

# Your Main Server (Principal's Office)
# Right-click server name → Copy ID
MAIN_GUILD_ID=987654321098765432

# Optional: Extra server for testing
TEST_GUILD_ID=876543210987654321

# Advanced Settings (leave as default)
DEBUG=false
DATABASE_URL=sqlite+aiosqlite:///wayhaven_enforcer.db
```

**Common Setup Mistakes:**
- Don't put quotes around values unless using spaces
- Server IDs must be 18+ digits long (copy carefully)
- Immediately regenerate token if compromised

### Step 6: Set Up Database

```bash
# Initialize the bot's memory system
python setup_database.py
```

**You should see this success message:**
```
Wayhaven Enforcer Database Setup
==================================================
Creating database tables...
✅ Created punishments table
✅ Created guild_relationships table (ZERO-LEAK enabled)
✅ Created command_audit table (100% compliance)
✅ Created security_alerts table
✅ Created system_health table
✅ Database initialization complete!
==================================================
⚠️  IMMUTABLE SECURITY: Database locked for ZERO-LEAK protection
🔒 Ready for bot startup
```

**Note:** Uses SQLite (no MySQL/PostgreSQL needed for normal use)

### Step 7: First Bot Launch

```bash
# Start your bot for the first time
python bot.py
```

**Expected successful startup:**
```
Starting Wayhaven Enforcer v2.1.0...
==================================================
Zero-Leak Security: ACTIVE
Database: Connected
Loading cogs...
✅ Loaded punishments
✅ Loaded sync
✅ Loaded setup_cog
✅ Loaded audit
✅ Loaded reconciliation
✅ Slash commands synced globally
==================================================
Wayhaven Enforcer is ready!

Logged in as:
Wayhaven Enforcer#1234
Connected to 3 servers
```

### Step 8: Configure Server Settings

#### Create Required School Roles:
1. **Go to Server Settings → Roles**
2. **Create "Muted" role:**
   - Set color to orange or red
   - Deny: Send Messages, Speak in voice
   - Allow: View channels (for timeout visibility)

#### Create School Office Channels:
1. **Create #moderation-logs:**
   - Hide from regular students (staff only)
   - Records all punishment activities
2. **Create #security-alerts:**
   - Hide from everyone except administrators
   - Shows system security notifications

#### Connect Bot to Channels:
```
/config muterole role:@Muted
/config notifications channel:#moderation-logs enabled:true
/config logchannel channel:#security-alerts
```

#### Make This Server The Principal's Office:
```
/setup main-guild
```

**This designates your server as the "Principal's Office" where punishments spread everywhere!**

#### Connect Classroom Servers:
```
/setup add-child guild-id:123456789012345678
```

Repeat for each classroom server. These servers will receive punishment notifications but cannot punish the whole school (ZERO-LEAK safety).

---

## ⚙️ Configuration

### Server Roles Setup

#### School Staff Roles:
| Role | Purpose | Permissions |
|------|---------|-------------|
| **Principal (Admin)** | Full control | Everything including ban/unban |
| **Teacher (Moderator)** | Classroom management | Warn, mute, timeout, kick |
| **Student** | Regular users | Basic permissions only |

#### Authority Levels:
```
Server Owner (Full Access)
├── Administrators (Principal - Setup, ban/unban, network control)
├── Moderators (Teachers - Warn, mute, timeout, kick)
└── Students (No moderation access)
```

### Channel Management

#### Essential School Channels:
| Channel | Purpose | Who Sees It |
|---------|---------|-------------|
| **#classroom-rules** | Server rules | Everyone |
| **#moderation-logs** | Punishment records | Staff only |
| **#security-alerts** | System alerts | Administrators only |
| **#teacher-lounge** | Staff commands | Staff only |

#### Bot Channel Settings:
```bash
# Configure Muted role
/config muterole role:@Muted

# Set up punishment logging
/config notifications channel:#moderation-logs enabled:true

# Configure security alerts
/config logchannel channel:#security-alerts

# Enable audit tracking
/config audit enabled:true
```

### School Network Architecture

#### Principal's Office (Main Server):
- Issues punishments that spread to all classrooms
- Full moderation authority across network
- Central audit logging system
- Network management controls

#### Classroom Servers (Child Servers):
- Receive punishment notifications from main server
- Local moderation only (warnings and kicks)
- Cannot trigger network-wide punishments
- Automatic compliance with school rules

#### Network Setup Commands:
```bash
# Become the principal's office
/setup main-guild

# Add classroom servers
/setup add-child guild-id:123456789012345678

# Test classroom connections
/setup test-connection guild-id:123456789012345678

# View network status
/setup dashboard
```

---

## 📋 Commands Reference

### Classroom Management Commands

| Command | What It Does | Example | Who Can Use |
|---------|--------------|---------|-------------|
| `/ban user:@student` | Expel from all connected servers | `/ban user:@Troublemaker reason:Disruptive behavior` | Administrators |
| `/unban user:123456789` | Allow readmission | `/unban user:987654321 reason:Appeal approved` | Administrators |
| `/kick user:@student` | Remove from current classroom | `/kick user:@Talkative reason:Talking during lesson` | Moderators |
| `/mute user:@student` | Quiet period | `/mute user:@Chatty duration:30m reason:Too distracting` | Moderators |
| `/timeout user:@student` | Temporary suspension | `/timeout user:@Arguer duration:1h reason:Arguments` | Moderators |
| `/warn user:@student` | Official warning | `/warn user:@NewStudent reason:Please read rules` | Staff |

### School Administration Commands

#### Network Management:
| Command | Purpose |
|---------|---------|
| `/setup main-guild` | Establish as principal's office |
| `/setup add-child guild-id:123` | Connect classroom server |
| `/setup remove-child guild-id:123` | Remove classroom connection |
| `/setup test-connection guild-id:123` | Check classroom link |
| `/setup dashboard` | View school network status |

#### Configuration Commands:
| Command | Purpose |
|---------|---------|
| `/config muterole role:@Muted` | Set quiet role |
| `/config notifications channel:#logs` | Set punishment logs |
| `/config logchannel channel:#alerts` | Set security alerts |
| `/config audit enabled:true` | Enable activity tracking |

#### Monitoring Commands:
| Command | Purpose |
|---------|---------|
| `/audit log user:@student days:30` | Student discipline history |
| `/audit stats days:7` | Weekly school statistics |
| `/audit warnings user:@student` | Warning records |

### Authority Levels

#### Principal's Office Permissions:
- **Administrators:** Everything - ban/unban, setup school network, change settings
- **Moderators:** Most actions - warn, mute, timeout, kick students
- **Staff:** Basic warnings, minor classroom management

#### Classroom Permissions:
- **Staff:** Local classroom management only (warnings, minor actions)
- **Cannot spread punishments** (ZERO-LEAK school safety rule)

---

## 🔧 Troubleshooting Guide

### Bot Startup Problems

#### "Python not recognized"
**Fix:** Reinstall Python with "Add to PATH" checked (Windows) or use `python3` (Mac/Linux)

#### "Improper token"
**Problem:** Wrong secret token in `.env`
**Solution:**
1. Go to Discord Developer Portal
2. Regenerate token if needed
3. Update `.env` file with correct token
4. Restart bot

#### "Discord connection failed"
**Possible issues:**
- Poor internet connection
- Discord servers down (check discordstatus.com)
- Bad bot token
- Regional access issues

#### "Module not found"
**Solution:**
```bash
# Install missing programs
pip install -r requirements.txt

# Or install specific one
pip install discord.py==2.3.0 --force-reinstall
```

### Permission Problems

#### "Missing permissions" error
**Check these:**
- Is bot admin in Discord server settings?
- Do you have administrator role?
- Do Discord Developer permissions match server permissions?

#### Commands not appearing
**Steps to fix:**
1. Check bot is online and connected
2. Type `/` to refresh command list
3. Verify bot has "Use Slash Commands" permission
4. Wait and restart bot if needed

### Network Sync Problems

#### Punishments not spreading
**Common problems:**
- Classroom server not connected (`/setup add-child`)
- Bot not invited to classroom
- Classroom admin didn't give permissions
- ZERO-LEAK protection (intentional safety)

#### "Child server blocked"
**This is correct behavior!**
- Classroom servers cannot punish whole school
- Only principal's office can spread punishments
- Prevents accidental school-wide trouble

#### Bot offline in classrooms
**Check these:**
- Bot invited to that specific server?
- Internet blocking Discord?
- Regional connectivity problems

### Database Issues

#### "Database locked"
**Quick fixes:**
```bash
# Backup first
cp wayhaven_enforcer.db backup.db

# Recreate database
python setup_database.py
```

**Prevention:** Don't edit database while bot is running

#### Database corruption
**Recovery steps:**
1. Stop bot immediately
2. Make backup: `cp wayhaven_enforcer.db backup_corrupt.db`
3. Reset: `rm wayhaven_enforcer.db && python setup_database.py`
4. Restore any missing data if possible

#### Performance issues
**Optimization:**
```bash
# Clean up database
sqlite3 wayhaven_enforcer.db "VACUUM;"

# Check for problems
sqlite3 wayhaven_enforcer.db "PRAGMA integrity_check;"
```

### Advanced School Issues

#### Debug mode
```env
# Add to .env file
DEBUG=true
```
Restart for detailed logging

#### Rate limiting problems
- Discord allows ~50 requests/second
- Bot handles this automatically
- Reduce sync frequency if issues persist

#### Memory usage
- Normal: 50-100MB RAM
- Restart weekly if exceeds 200MB
- Monitor in Task Manager/Activity Monitor

---

## 🏢 School Compliance Standards

### Data Protection Rules

**For schools and educational organizations:**

#### Legal Responsibility
Wayhaven acts as data processor for school administrators (data controllers).

#### Processing Legally Required For:
- **School Safety:** Preventing student conflicts across classes
- **Discipline Records:** School records compliance
- **Parent Communications:** School notification requirements
- **Educational Supervision**

#### Information Collected:
```
Stored School Data:
├── Student ID Numbers: Discord User IDs (pseudonymized)
├── Incident Records: Discipline actions, times, reasons
├── Warning Notices: Sent to students via DM
└── Activity Logs: Command usage patterns, server interactions
```

#### Student Digital Rights

**Right to Be Informed (Schedule 13-14):**
- Clear privacy notice in school handbook
- Transparent data usage documentation
- Student rights explanation

**Right to Access Records (Schedule 15):**
```bash
# School disciplinary access command
/audit log user:@StudentName days:365
```

**Right to Challenge Records (Schedule 16):**
- Teachers can correct inaccurate records
- Appeal process through school administration
- Student complaints review

**Right to Delete Records ("Be Forgotten") (Schedule 17):**
```python
# Student record removal process
async def remove_student_data(student_id: str):
    await db.execute("DELETE FROM punishments WHERE target_user = ?", (student_id,))
    await db.execute("DELETE FROM command_audit WHERE user_id = ?", (student_id,))
    await db.log_compliance_event("student_data_removed", {"student_id": student_id})
    return {"status": "removed", "student": student_id}
```

**Right to Transfer Records (Schedule 20):**
```bash
# Export student disciplinary history
/audit export days:365 user-filter:@StudentName format:json
```

**Right to Challenge Automation (Schedules 21-22):**
- Human review of automated discipline actions
- Parent/teacher overrides available
- Appeal process for unfair automation

#### Record Retention Policy

| Record Type | Keep For | Extended Storage | Disposal Method |
|------------|----------|------------------|-----------------|
| Active Discipline | End of school year | N/A | Automatic |
| Audit Records | 7 years | Up to 10+ years for legal | Secure deletion |
| Command Logs | 3 years | 7 years for serious incidents | Encrypted removal |
| System Records | 1 year | 3 years for debugging | Automatic cleanup |

---

## 👨‍💻 Developer Technical Guide

### System Technical Architecture

#### Component Architecture
```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│     discord.py  │ ←→ │     Bot Core     │ ←→ │   Discord API   │
│   Integration   │    │   (bot.py)       │    │                 │
└─────────────────┘    └──────────────────┘    └─────────────────┘
         ↑                       ↑                       ↑
         │                       │                       │
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│      Cogs       │    │   Database       │    │   Config        │
│  (Commands)     │    │   (aiosqlite)    │    │   Manager        │
│                 │    │                  │    │                 │
│• punishments    │    │• punishments     │    │• .env           │
│• sync           │    │• guild_relations │    │• runtime        │
│• setup_cog      │    │• command_audit   │    │• validation     │
│• audit          │    │• system_health   │    │                 │
│• reconciliation │    │• security_alerts │    └─────────────────┘
└─────────────────┘    └──────────────────┘
```

#### ZERO-LEAK Technical Security Model:
```
MAIN SERVER (HUB)
├── One-way punishment broadcast authority
├── Child server relationship management
├── Network leadership validation
└── Security monitoring master control

CHILD SERVERS (SPOKES)
├── Punishment broadcast reception only
├── Cannot initiate cross-server punishment
├── Local-only moderation capabilities
└── Isolated operational boundaries
```

#### Startup Technical Sequence:
```
1. ENV config load + validation → Error if missing required fields
2. Database connection + schema migration → Create missing tables
3. Discord client initialization + intent configuration load
4. Cog dynamic loading + command registration system initialization
5. Application command global synchronization verification
6. Guild-specific command synchronization for test environments
7. Event listener system activation for operational monitoring
8. Ready state confirmation with comprehensive system health verification
```

### Code Organization Technical Structure

#### Directory Technical Layout
```
wayhaven_enforcer/
├── bot.py                 # Primary application entry point & core event orchestration
├── config.py             # Centralized configuration management system
├── database.py           # Abstracted data persistence layer with ORM integration
├── requirements.txt      # Dependency specification manifest
├── setup_database.py     # Automated database initialization script
├── test_bot.py          # Infrastructure connectivity validation tool
├── migrate_to_v2.py     # Versioned database transformation scripts
└── cogs/                # Modular command architecture containers
    ├── __init__.py      # Cog initialization orchestration
    ├── punishments.py   # Moderation action command implementations
    ├── sync.py          # Inter-server synchronization logic core
    ├── config_cmds.py   # Administrative configuration command set
    ├── setup_cog.py     # Guild relationship management system
    ├── audit.py         # Compliance logging and reporting infrastructure
    └── reconciliation.py # Data consistency validation mechanisms
```

#### Module Technical Responsibilities
| Component | Technical Domain | Primary APIs | Key Technical Patterns |
|-----------|------------------|--------------|------------------------|
| **bot.py** | Application Architecture | `on_ready()`, `setup_hook()` | Event-driven async architecture, cog orchestration |
| **database.py** | Data Persistence | `add_punishment()`, `validate_sync_attempt()` | AIOsqlite integration, connection pooling patterns |
| **config.py** | Configuration Management | Environment variable parsing, validation | Secure secret handling, type validation |
| **punishments.py** | Moderation Logic | `ban_slash()`, `mute_slash()` | Command validation, error handling, audit integration |
| **sync.py** | Cross-Server Logic | `propagate_punishment()`, `ZERO-LEAK_validation()` | Asynchronous propagation, circuit breaker patterns |
| **setup_cog.py** | Relationship Management | `add_child_guild()`, `test_connection()` | Relationship validation, permission checking |
| **audit.py** | Compliance Infrastructure | `get_command_audit()`, `generate_reports()` | GDPR compliance, data retention policies |

### Database Technical Schema Design

#### Core Event Table Structure
```sql
-- punishments: Primary incident tracking mechanism
CREATE TABLE punishments (
    event_id INTEGER PRIMARY KEY AUTOINCREMENT,
    source_guild INTEGER NOT NULL,
    target_user INTEGER NOT NULL,
    action TEXT NOT NULL CHECK (action IN ('ban', 'unban', 'kick', 'mute', 'unmute', 'warn', 'timeout')),
    reason TEXT,
    moderator_id INTEGER,
    expires_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status TEXT DEFAULT 'active' CHECK (status IN ('active', 'expired', 'reversed'))
);
```

#### Relationship Security Framework
```sql
-- guild_relationships: ZERO-LEAK relationship validation structure
CREATE TABLE guild_relationships (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    main_guild_id INTEGER NOT NULL,
    child_guild_id INTEGER NOT NULL,
    sync_direction TEXT NOT NULL DEFAULT 'MAIN_TO_CHILD'
                         CHECK (sync_direction = 'MAIN_TO_CHILD'),
    sync_mode TEXT NOT NULL DEFAULT 'ACTIVE'
                     CHECK (sync_mode IN ('ACTIVE', 'MONITOR')),
    allowed_actions TEXT NOT NULL DEFAULT '["ban","unban","kick","mute","warn","timeout"]',
    auto_sync_enabled BOOLEAN DEFAULT 1,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE(main_guild_id, child_guild_id),
    FOREIGN KEY (main_guild_id) REFERENCES guild_settings(guild_id),
    FOREIGN KEY (child_guild_id) REFERENCES guild_settings(guild_id)
);
```

#### Compliance Audit Infrastructure
```sql
-- command_audit: Comprehensive operational tracking
CREATE TABLE command_audit (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    guild_id INTEGER NOT NULL,
    channel_id INTEGER,
    user_id INTEGER NOT NULL,
    command_name TEXT NOT NULL,
    command_type TEXT NOT NULL CHECK (command_type IN ('punishment', 'admin', 'config', 'audit')),
    parameters TEXT,
    result_status TEXT NOT NULL CHECK (result_status IN ('success', 'error', 'permission_denied')),
    execution_time_ms INTEGER,
    logged_to_notifications BOOLEAN DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- guild_settings: Per-guild operational configuration
CREATE TABLE guild_settings (
    guild_id INTEGER PRIMARY KEY,
    mute_role_id INTEGER,
    log_channel_id INTEGER,
    staff_role_id INTEGER,
    webhook_url TEXT,
    notification_channel_id INTEGER,
    auto_sync_enabled BOOLEAN DEFAULT 1,
    notifications_enabled BOOLEAN DEFAULT 1,
    settings JSON DEFAULT '{}',
    security_level TEXT DEFAULT 'standard'
                      CHECK (security_level IN ('standard', 'high', 'maximum')),
    relationship_lock_enabled BOOLEAN DEFAULT 1,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    CHECK (notifications_enabled = 0 OR notification_channel_id IS NOT NULL)
);

-- system_health: Operational monitoring infrastructure
CREATE TABLE system_health (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    component TEXT NOT NULL,
    status TEXT NOT NULL CHECK (status IN ('healthy', 'warning', 'error', 'security_breach')),
    details TEXT,
    severity TEXT DEFAULT 'info',
    resolved_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- security_alerts: Breach detection and response tracking
CREATE TABLE security_alerts (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    alert_type TEXT NOT NULL,
    guild_id INTEGER,
    user_id INTEGER,
    severity TEXT NOT NULL,
    details TEXT NOT NULL,
    action_taken TEXT,
    resolved BOOLEAN DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### Performance Optimization Indexes
```sql
-- Query acceleration for operational performance
CREATE INDEX idx_punishments_user_guild ON punishments(target_user, source_guild);
CREATE INDEX idx_audit_logs_security ON audit_logs(source_guild, status, created_at);
CREATE INDEX idx_relationships_main_only ON guild_relationships(main_guild_id, sync_direction);
CREATE INDEX idx_command_audit_compliance ON command_audit(guild_id, logged_to_notifications);
CREATE INDEX idx_security_alerts_active ON security_alerts(resolved, severity, created_at);
```

### Critical Algorithm Implementations

#### Cross-Server Synchronization Engine
```python
async def propagate_punishment_critical_sync(self, event_id: int, action: str, source_guild: DiscordGuild,
                                           target_user: DiscordUser, reason: str, moderator: DiscordUser = None) -> PropagationResults:
    """
    MISSION-CRITICAL: Synchronous cross-server punishment propagation with ZERO-LEAK validation

    Technical Parameters:
        event_id: Atomic transaction identifier for incident tracking
        action: Standardized moderation action classification
        source_guild: Trust validation origin point
        target_user: Punishment enforcement target
        reason: Audit trail justification documentation
        moderator: Authority source validation

    Security Validation Chain:
    1. Primary main guild authority verification
    2. Authorized relationship matrix validation
    3. Action permission scope confirmation
    4. Target guild eligibility verification
    5. Rate limiting compliance assessment

    Atomic Execution Guarantees:
        CONSISTENCY: All-or-nothing transactional execution
        RELIABILITY: Automatic retry mechanism for transient failures
        COMPLIANCE: 100% audit trail coverage
        SECURITY: ZERO-LEAK architecture enforcement
    """

    # PRIMARY SECURITY GATE: Main guild authority validation
    if not await self.db.validate_main_guild_authority(source_guild.id):
        await self._log_security_violation('unauthorized_sync_attempt', source_guild.id)
        return PropagationResults(blocked=True, reason="Main guild validation failed")

    # AUTHORIZED RELATIONSHIP VALIDATION: Get approved child relationships
    sync_targets = await self.db.get_child_guilds_for_sync(source_guild.id)

    results = PropagationResults()
    for target in sync_targets:
        try:
            # EXECUTE PUNISHMENT: Apply action on target guild
            success = await self._execute_specific_action(
                target['guild_id'], action, target_user, reason, moderator
            )

            if success:
                results.successful.append(target['guild_id'])
            else:
                results.failed.append(target['guild_id'])

        except Exception as e:
            self.logger.error(f"Propagation failed for guild {target['guild_id']}: {e}")
            results.failed.append(target['guild_id'])

    return results
```

#### ZERO-LEAK Validation Algorithm
```python
async def validate_zero_leak_attempt(self, source_guild_id: int, target_guild_id: int, action: str) -> bool:
    """
    CRITICAL SECURITY ENFORCEMENT: Validates all sync attempts against ZERO-LEAK architecture

    Security Validation Matrix:
    │ Validation Layer │ Purpose │ Failure Impact │
    │------------------|---------|----------------|
    │ Main Guild Auth  │ Trust validation │ BLOCK: Unauthorized source |
    │ Child Relationship│ Scope validation │ BLOCK: Invalid target |
    │ Action Permission│ Scope enforcement │ BLOCK: Unauthorized action |
    │ Relationship State│ Status validation │ BLOCK: Suspended connection |

    Enforcement Rules (All Must Pass):
    ✓ Source MUST be designated Main guild
    ✓ Target MUST be authorized child guild
    ✓ Action MUST be permitted for this relationship
    ✓ Connection MUST be active and healthy
    ✓ Rate limits MUST not be exceeded

    Return: True if authorized, False if blocked (with audit logging)
    """

    # SECURITY GATE 1: Main Guild Authority Verification
    if not await self.db.is_main_guild(source_guild_id):
        await self._log_security_alert(
            'child_sync_attempt', source_guild_id, None, 'critical',
            f"Child guild {source_guild_id} attempted unauthorized sync"
        )
        return False

    # SECURITY GATE 2: Child Relationship Verification
    children = await self.db.get_child_guilds_for_sync(source_guild_id)
    child_ids = [child['guild_id'] for child in children]

    if target_guild_id not in child_ids:
        await self._log_security_alert(
            'unauthorized_sync_target', source_guild_id, None, 'high',
            f"Unauthorized sync target {target_guild_id}"
        )
        return False

    # SECURITY GATE 3: Action Permission Validation
    for child in children:
        if child['guild_id'] == target_guild_id and action in child['allowed_actions']:
            return True

    await self._log_security_alert(
        'unauthorized_sync_action', source_guild_id, None, 'medium',
        f"Forbidden action '{action}' attempted on {target_guild_id}"
    )
    return False
```

---

### Discord API Integration Architecture

#### Slash Command Implementation Framework
```python
# Secure command registration with comprehensive audit trail
@app_commands.command(
    name="ban",
    description="Enforce cross-server ban with security validation"
)
@app_commands.describe(
    user="Target user for ban enforcement",
    reason="Justification documentation for compliance",
    delete_days="Message history removal period (0-7 days)"
)
@app_commands.default_permissions(ban_members=True)
async def ban_cross_server_command(
    self,
    interaction: DiscordInteraction,
    user: DiscordUser,
    reason: str = "No justification provided",
    delete_days: int = 0
) -> None:
    """Secure slash command implementation with ZERO-LEAK protection"""

    # PHASE 1: Pre-execution security validation
    await interaction.response.defer(ephemeral=True)

    # Input sanitization and length validation
    reason = self._sanitize_moderation_reason(reason, max_length=512)

    try:
        # PHASE 2: Primary guild ban execution
        await interaction.guild.ban(
            user,
            reason=f"{reason} | Enforced by {interaction.user}",
            delete_message_days=min(delete_days, 7)
        )

        # PHASE 3: Audit trail documentation
        await self._log_moderation_action(
            interaction,
            'global_ban',
            {
                'target_user_id': user.id,
                'reason': reason,
                'delete_days': delete_days,
                'execution_context': 'cross_server_ban'
            }
        )

        # PHASE 4: Cross-server propagation (ZERO-LEAK protected)
        sync_cog = self.bot.get_cog('Sync')
        if sync_cog:
            await sync_cog.propagate_punishment(
                event_id=None,
                action='ban',
                source_guild=interaction.guild,
                target_user=user,
                reason=reason,
                moderator=interaction.user
            )

        # PHASE 5: Success confirmation with detailed reporting
        success_embed = DiscordEmbed(
            title="🚫 Cross-Server Ban Executed",
            description=f"{user.mention} banned across school network",
            color=self.security_colors['ban_enforced']
        )
        success_embed.add_field(name="Reason", value=reason, inline=False)
        success_embed.add_field(
            name="Scope", value="Applied to all connected classrooms", inline=True
        )

        await interaction.followup.send(embed=success_embed)

    except DiscordForbidden:
        await interaction.followup.send(
            "❌ Insufficient permissions for school-wide ban", ephemeral=True
        )
    except Exception as e:
        self.logger.error(f"Cross-server ban failed: {e}")
        await interaction.followup.send(f"❌ Ban execution error: {e}", ephemeral=True)
```

#### Event-Driven Synchronization Architecture
```python
# Real-time event interception for automatic cross-server response
@commands.Cog.listener()
async def on_member_ban(self, guild: DiscordGuild, user: DiscordUser) -> None:
    """
    EVENT-DRIVEN SECURITY: Automatic discipline synchronization with ZERO-LEAK protection

    Trigger Conditions:
    • Manual ban executed by authorized moderator
    • Bot-detected policy violation requiring ban
    • Administrative ban command enforcement

    Security Architecture:
    1. Guild authority validation (Main vs Child server)
    2. Ban reason extraction from audit logs
    3. Cross-server propagation authorization check
    4. Automatic sync execution with compliance logging
    """

    self.school_security_logger.info(
        f"Discipline event detected: Guild {guild.id} → User {user.id}"
    )

    # ZERO-LEAK SECURITY ENFORCEMENT
    is_principal_office = await self.db.is_main_guild(guild.id)

    if not is_principal_office:
        self.school_security_logger.warning(
            f"SECURITY BLOCK: Child classroom {guild.id} ban - network sync restricted"
        )

        # Log security attempt for audit trail
        await self.db._log_security_alert(
            'childroom_ban_attempt',
            guild.id,
            None,
            'high',
            f"Child classroom {guild.id} attempted network-wide discipline for {user.id}"
        )
        return

    # AUTHORIZED EXECUTION PATH
    try:
        # Extract discipline justification from audit logs
        discipline_reason = await self._extract_ban_justification(guild, user)

        # Record discipline event with full audit trail
        discipline_event_id = await self.db.add_punishment(
            source_guild=guild.id,
            target_user=user.id,
            action='ban',
            reason=discipline_reason,
            moderator_id=None  # System-detected or staff-initiated
        )

        self.school_security_logger.info(
            f"Network discipline recorded: Event #{discipline_event_id}"
        )

        # TRIGGER SCHOOL-WIDE ENFORCEMENT
        sync_teacher = self.bot.get_cog('Sync')
        if sync_teacher:
            await sync_teacher.propagate_punishment(
                event_id=discipline_event_id,
                action='ban',
                source_guild=guild,
                target_user=user,
                reason=discipline_reason
            )

            await self.db._log_system_health(
                'network_discipline',
                'healthy',
                f"School-wide ban enforced for {user.id} from {guild.id}"
            )
        else:
            self.school_security_logger.error("Sync teacher unavailable - discipline not propagated")

    except Exception as e:
        self.school_security_logger.error(f"School-wide discipline failed: {e}")
        await self.db._log_security_alert(
            'discipline_propagation_failure',
            guild.id,
            None,
            'critical',
            f"Failed to enforce school-wide ban for {user.id}: {str(e)}"
        )
```

---

### Development Environment Configuration

#### Local Development Infrastructure Setup
```bash
# System Requirements Validation
# Minimum Hardware Specifications:
# • Operating System: Windows 10+, macOS 11+, Ubuntu 18.04+
# • Processor: Dual-core CPU (Intel/AMD ARM64 compatible)
# • Memory: 4GB RAM minimum, 8GB+ recommended
# • Storage: 1GB free space for development environment
# • Network: Stable internet connection for API synchronization

# Python Environment Preparation
python_version=$(python3 --version 2>&1 | awk '{print $2}')
if [[ "${python_version%%.*}" -ge "3" && "${python_version#*.}" -ge "8" ]]; then
    echo "✅ Python ${python_version} meets requirements"
else
    echo "❌ Python 3.8+ required. Current: ${python_version}"
    exit 1
fi

# Virtual Environment Creation for Isolated Development
python3 -m venv wayhaven_dev_env
source wayhaven_dev_env/bin/activate  # Linux/macOS
# wayhaven_dev_env\Scripts\activate     # Windows

# Dependency Installation with Verification
echo "Installing Wayhaven development dependencies..."
pip install --upgrade pip
pip install -r requirements.txt

# Development-Specific Package Installation
pip install pytest pytest-asyncio black flake8 mypy coverage
pip install sqlalchemy-utils  # Advanced database utilities
pip install discord-ext-ipc   # Development communication
pip install python-dotenv[cli] # Advanced environment management

# Setup Verification
python -c "import discord, aiosqlite, dotenv; print('✅ All core dependencies installed')"

echo "🎓 Development environment ready for Wayhaven Enforcer"
```

#### Development Configuration Template
```bash
# .env.development - Isolated Development Environment
# SECURITY: Never commit real tokens to version control

# Bot Identity and Authentication
WAYHAVEN_BOT_TOKEN="your.development.bot.token.here"
DISCORD_APPLICATION_ID="1234567890123456789"
DISCORD_CLIENT_SECRET="your.client.secret"

# School Network Configuration (Development)
MAIN_SCHOOL_GUILD_ID="9876543210987654321"      # Development principal's office
TEST_CLASSROOM_GUILD_ID="8765432109876543210"   # Development classroom
ISOLATION_MODE="development"                    # Prevents production interference

# Database Configuration (Development Isolation)
DATABASE_FILE="wayhaven_development.db"
DATABASE_BACKUP_RETENTION="30"                  # Days to keep backups
LOG_LEVEL="DEBUG"                               # Maximum logging for troubleshooting

# Development Features (Testing and Debugging)
ENABLE_DEBUG_LOGGING="true"
AUTO_RELOAD_ON_CHANGE="true"                    # Hot reload during development
MOCK_EXTERNAL_APIS="false"                      # Test real Discord API
PERFORMANCE_MONITORING="true"                   # Monitor resource usage

# Security Testing Configuration
ZERO_LEAK_TESTING_ENABLED="true"
AUDIT_TRAIL_VALIDATION="true"
PENETRATION_TEST_MODE="disabled"                # Enable only when testing security

# Development Server Endpoints
LOCAL_DASHBOARD_PORT="8080"
METRICS_ENDPOINT="http://localhost:8080/metrics"
HEALTH_CHECK_ENDPOINT="http://localhost:8080/health"
```

#### Automated Testing Infrastructure
```python
# test/test_integration_security.py
import pytest
import pytest_asyncio
from unittest.mock import AsyncMock, MagicMock
import discord
from wayhaven_enforcer import WayhavenEnforcer
from wayhaven_enforcer.database import Database
from wayhaven_enforcer.security import ZeroLeakValidator

class TestZeroLeakSecurityEnforcement:
    """Comprehensive security validation test suite"""

    @pytest_asyncio.fixture
    async def test_database(self):
        """Isolated test database with predefined security scenarios"""
        db = Database(":memory:")  # In-memory database for testing
        await db.connect()
        await db.create_tables()

        # Pre-populate with test scenarios
        await db.add_guild_link(1001, 2001, "MAIN_ONLY")    # Valid main-child
        await db.add_guild_link(1001, 3001, "CHILD_ONLY")   # Invalid configuration
        await db.add_guild_link(4001, 1001, "BIDIRECTIONAL") # Unauthorized bidirection

        yield db
        await db.close()

    @pytest.mark.asyncio
    async def test_zero_leak_main_guild_validation(self, test_database):
        """Test that only designated main guilds can initiate sync"""
        validator = ZeroLeakValidator(test_database)

        # Valid main guild should pass
        assert await validator.validate_sync_attempt(1001, 2001, "ban") == True

        # Non-main guild should be blocked (ZERO-LEAK enforcement)
        assert await validator.validate_sync_attempt(2001, 1001, "ban") == False

        # Invalid relationship should be blocked
        assert await validator.validate_sync_attempt(1001, 3001, "ban") == False

    @pytest.mark.asyncio
    async def test_zero_leak_action_authorization(self, test_database):
        """Test that only permitted actions work in relationships"""
        validator = ZeroLeakValidator(test_database)

        # Permitted action should work
        assert await validator.validate_sync_attempt(1001, 2001, "ban") == True
        assert await validator.validate_sync_attempt(1001, 2001, "mute") == True

        # Non-permitted action should be blocked
        assert await validator.validate_sync_attempt(1001, 2001, "admin_command") == False

    @pytest.mark.asyncio
    async def test_zero_leak_bidirectional_prevention(self, test_database):
        """Test that bidirectional relationships are prevented"""
        validator = ZeroLeakValidator(test_database)

        # Even with bidirectional relationship defined, should be blocked
        assert await validator.validate_sync_attempt(4001, 1001, "ban") == False
        assert await validator.validate_sync_attempt(1001, 4001, "ban") == False

# pytest.ini
[tool:pytest.ini_options]
testpaths = ["test"]
python_files = ["test_*.py", "*_test.py"]
python_classes = ["Test*"]
python_functions = ["test_*"]
addopts = [
    "--strict-markers",
    "--strict-config",
    "--disable-warnings",
    "--tb=short",
    "-ra",
    "--cov=wayhaven_enforcer",
    "--cov-report=html",
    "--cov-report=term-missing"
]
markers = [
    "security: Security-related tests",
    "integration: Integration tests",
    "unit: Unit tests",
    "performance: Performance tests"
]
```

#### Running Development Test Suite
```bash
# Complete test execution pipeline
echo "🧪 Starting Wayhaven Enforcer test suite..."

# Unit Tests (Fast, isolated)
python -m pytest test/unit/ -v --tb=short --cov-report=term-missing

# Integration Tests (Real Discord API integration)
python -m pytest test/integration/ -v --tb=short -s

# Security Tests (ZERO-LEAK validation, penetration testing)
python -m pytest test/security/ -v --tb=short -m security

# Performance Tests (Load testing, memory profiling)
python -m pytest test/performance/ -v --tb=short -m performance

# Coverage Report Generation
python -m pytest --cov=wayhaven_enforcer --cov-report=html --cov-report=xml

# Static Analysis (Code quality checks)
flake8 wayhaven_enforcer/ --max-line-length=88 --extend-ignore=E203,W503
black --check --diff wayhaven_enforcer/
mypy wayhaven_enforcer/ --ignore-missing-imports

echo "✅ Test suite completed - check reports for detailed results"
```

---

### Extension Development & Customization Framework

#### Custom Cog Development Template
```python
# cogs/academic_monitoring.py - School performance tracking extension
import discord
from discord import app_commands
from discord.ext import commands, tasks
import logging
from datetime import datetime, timedelta
from typing import Dict, List, Optional
import json

from wayhaven_enforcer.database import Database

logger = logging.getLogger('AcademicMonitoring')

class AcademicMonitoring(commands.Cog):
    """Advanced academic performance monitoring for educational environments"""

    def __init__(self, bot):
        self.bot = bot
        self.db: Database = bot.db
        self.performance_monitor.start()

    def cog_unload(self):
        self.performance_monitor.cancel()

    # Academic Performance Dashboard
    @app_commands.command(
        name="academic_dashboard",
        description="View student performance analytics across connected classrooms"
    )
    @app_commands.default_permissions(manage_guild=True)
    async def academic_dashboard(self, interaction: discord.Interaction):
        """Educational analytics dashboard with cross-classroom insights"""

        await interaction.response.defer(ephemeral=True)

        try:
            # Gather academic metrics from all connected classrooms
            dashboard_data = await self._compile_academic_dashboard(
                interaction.guild.id
            )

            # Create comprehensive dashboard embed
            embed = discord.Embed(
                title="📊 Academic Performance Dashboard",
                description=f"Analytics for {interaction.guild.name} classroom network",
                color=0x4CAF50,  # Academic green
                timestamp=datetime.utcnow()
            )

            # Participation Metrics
            embed.add_field(
                name="🎓 Student Participation",
                value=dashboard_data['participation_rate'],
                inline=True
            )

            # Disciplinary Trends
            embed.add_field(
                name="📈 Behavioral Trends",
                value=dashboard_data['discipline_trends'],
                inline=True
            )

            # Learning Engagement
            embed.add_field(
                name="🎯 Academic Engagement",
                value=dashboard_data['engagement_score'],
                inline=True
            )

            await interaction.followup.send(embed=embed, ephemeral=True)

        except Exception as e:
            logger.error(f"Academic dashboard error: {e}")
            await interaction.followup.send(
                "❌ Unable to generate academic dashboard", ephemeral=True
            )

    # Automated Performance Monitoring
    @tasks.loop(hours=24)  # Daily academic assessment
    async def performance_monitor(self):
        """Daily automated academic performance monitoring"""

        logger.info("Starting daily academic performance assessment...")

        try:
            # Get all connected school guilds
            school_network = await self.db.get_school_network_status()

            for school in school_network:
                # Analyze academic metrics for each classroom
                academic_health = await self._analyze_classroom_health(school['guild_id'])

                if academic_health['needs_attention']:
                    await self._notify_educators(
                        school['guild_id'],
                        academic_health['concerns']
                    )

                    # Log academic interventions for compliance
                    await self.db.log_academic_intervention(
                        school_id=school['guild_id'],
                        intervention_type=academic_health['intervention_type'],
                        details=academic_health['recommendations']
                    )

        except Exception as e:
            logger.error(f"Performance monitoring failed: {e}")

    async def _compile_academic_dashboard(self, school_id: int) -> Dict:
        """Compile comprehensive academic dashboard data"""

        # Query database for academic metrics
        academic_metrics = await self.db.get_academic_metrics(school_id)

        return {
            'participation_rate': academic_metrics.get('participation', 'N/A'),
            'discipline_trends': academic_metrics.get('discipline_trend', 'Stable'),
            'engagement_score': academic_metrics.get('engagement', 'High'),
            'network_health': academic_metrics.get('network_status', 'Good')
        }

    async def _analyze_classroom_health(self, classroom_id: int) -> Dict:
        """Analyze classroom academic health indicators"""

        # Get classroom data from database
        classroom_data = await self.db.get_classroom_academic_data(classroom_id)

        # Analyze participation patterns
        participation_rate = classroom_data.get('participation_rate', 0)
        discipline_incidents = classroom_data.get('discipline_count', 0)

        # Determine if attention needed
        needs_attention = (
            participation_rate < 70 or
            discipline_incidents > 10 or
            classroom_data.get('engagement_trend', 'stable') == 'declining'
        )

        return {
            'needs_attention': needs_attention,
            'concerns': classroom_data.get('primary_concerns', []),
            'intervention_type': self._determine_intervention_type(classroom_data),
            'recommendations': self._generate_recommendations(classroom_data)
        }

    def _determine_intervention_type(self, classroom_data: Dict) -> str:
        """Determine appropriate intervention strategy"""
        if classroom_data.get('participation_rate', 100) < 50:
            return 'engagement_boost'
        elif classroom_data.get('discipline_count', 0) > 15:
            return 'behavior_intervention'
        elif classroom_data.get('engagement_trend') == 'declining':
            return 'motivation_program'
        else:
            return 'preventive_monitoring'

    def _generate_recommendations(self, classroom_data: Dict) -> List[str]:
        """Generate specific recommendations based on classroom data"""
        recommendations = []

        participation = classroom_data.get('participation_rate', 100)
        if participation < 70:
            recommendations.append("Implement participation incentives")
            recommendations.append("Review lesson engagement strategies")

        discipline = classroom_data.get('discipline_count', 0)
        if discipline > 10:
            recommendations.append("Enhance classroom management protocols")
            recommendations.append("Increase positive reinforcement")

        if len(recommendations) == 0:
            recommendations.append("Continue current successful strategies")

        return recommendations

async def setup(bot):
    """Register the academic monitoring extension"""
    await bot.add_cog(AcademicMonitoring(bot))
```

#### Database Extension Pattern
```python
# extensions/academic_metrics.py
# Add academic tracking capabilities to existing database

async def create_academic_tables(self):
    """Extend database with academic performance tracking"""

    await self.connection.executescript("""
        -- Student participation tracking
        CREATE TABLE IF NOT EXISTS student_participation (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            guild_id INTEGER NOT NULL,          -- Classroom ID
            user_id INTEGER NOT NULL,           -- Student ID
            activity_type TEXT NOT NULL,        -- 'message', 'reaction', 'voice'
            timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            FOREIGN KEY (guild_id) REFERENCES guild_settings(guild_id)
        );

        -- Academic engagement metrics
        CREATE TABLE IF NOT EXISTS academic_engagement (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            guild_id INTEGER NOT NULL,
            date DATE NOT NULL,
            total_participation INTEGER DEFAULT 0,
            average_response_time REAL,
            discipline_incidents INTEGER DEFAULT 0,
            engagement_score REAL,              -- 0.0 to 1.0 scale
            updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            UNIQUE(guild_id, date)
        );

        -- Academic intervention tracking
        CREATE TABLE IF NOT EXISTS academic_interventions (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            school_id INTEGER NOT NULL,
            classroom_id INTEGER,
            intervention_type TEXT NOT NULL,   -- 'engagement', 'behavior', 'motivation'
            severity TEXT CHECK (severity IN ('low', 'medium', 'high')),
            description TEXT,
            recommendations TEXT,              -- JSON array
            status TEXT DEFAULT 'active' CHECK (status IN ('active', 'resolved', 'ongoing')),
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            resolved_at TIMESTAMP
        );
    """)

async def log_student_participation(self, guild_id: int, user_id: int, activity_type: str):
    """Log student academic participation"""
    await self.connection.execute(
        """INSERT INTO student_participation (guild_id, user_id, activity_type)
           VALUES (?, ?, ?)""",
        (guild_id, user_id, activity_type)
    )
    await self.connection.commit()

async def get_academic_metrics(self, guild_id: int) -> Dict:
    """Retrieve academic performance metrics for classroom"""

    # Daily participation count
    participation_cursor = await self.connection.execute(
        """SELECT COUNT(*) FROM student_participation
           WHERE guild_id = ? AND timestamp > datetime('now', '-1 day')""",
        (guild_id,)
    )
    daily_participation = (await participation_cursor.fetchone())[0]

    # Engagement score (last 7 days)
    engagement_cursor = await self.connection.execute(
        """SELECT AVG(engagement_score) FROM academic_engagement
           WHERE guild_id = ? AND date > date('now', '-7 days')""",
        (guild_id,)
    )
    avg_engagement = (await engagement_cursor.fetchone())[0]

    # Discipline incident count
    discipline_cursor = await self.connection.execute(
        """SELECT COUNT(*) FROM punishments
           WHERE source_guild = ? AND created_at > datetime('now', '-7 days')""",
        (guild_id,)
    )
    recent_discipline = (await discipline_cursor.fetchone())[0]

    return {
        'participation': daily_participation,
        'engagement': f"{avg_engagement:.1%}" if avg_engagement else "Not available",
        'discipline_trend': "High" if recent_discipline > 5 else "Normal" if recent_discipline > 2 else "Low",
        'overall_health': "Good" if avg_engagement and avg_engagement > 0.7 else "Needs Attention"
    }
```

---

### Security Implementation & Hardening

#### Advanced Token Security Management
```python
# config/secure_token_manager.py
import os
import base64
import secrets
from cryptography.fernet import Fernet
from cryptography.hazmat.primitives import hashes
from cryptography.hazmat.primitives.kdf.pbkdf2 import PBKDF2HMAC
import logging

logger = logging.getLogger('SecureTokenManager')

class TokenSecurityManager:
    """Military-grade token security with encryption at rest"""

    def __init__(self, master_key_path: str = None):
        self.master_key_path = master_key_path or os.path.expanduser("~/.wayhaven/master.key")
        self._ensure_master_key()
        self.fernet = self._initialize_encryption()

    def _ensure_master_key(self):
        """Generate or load master encryption key"""
        if not os.path.exists(os.path.dirname(self.master_key_path)):
            os.makedirs(os.path.dirname(self.master_key_path), mode=0o700)

        if not os.path.exists(self.master_key_path):
            # Generate cryptographically secure master key
            master_key = secrets.token_bytes(32)
            with open(self.master_key_path, 'wb') as f:
                f.write(master_key)
            os.chmod(self.master_key_path, 0o600)  # Owner read/write only
            logger.info("🔐 Generated new master encryption key")
        else:
            logger.debug("🔑 Loaded existing master encryption key")

    def _initialize_encryption(self) -> Fernet:
        """Initialize Fernet encryption with master key"""
        with open(self.master_key_path, 'rb') as f:
            master_key = f.read()

        # Derive encryption key using PBKDF2
        salt = master_key[:16]  # First 16 bytes as salt
        kdf = PBKDF2HMAC(
            algorithm=hashes.SHA256(),
            length=32,
            salt=salt,
            iterations=100000,
        )

        derived_key = base64.urlsafe_b64encode(kdf.derive(master_key))
        return Fernet(derived_key)

    def encrypt_token(self, token: str) -> str:
        """Encrypt Discord bot token for secure storage"""
        if not token:
            raise ValueError("Cannot encrypt empty token")

        # Validate Discord token format before encryption
        if not self._validate_discord_token(token):
            raise ValueError("Invalid Discord token format")

        encrypted_data = self.fernet.encrypt(token.encode())
        return base64.urlsafe_b64encode(encrypted_data).decode()

    def decrypt_token(self, encrypted_token: str) -> str:
        """Decrypt Discord bot token for use"""
        try:
            encrypted_data = base64.urlsafe_b64decode(encrypted_token)
            decrypted_data = self.fernet.decrypt(encrypted_data)
            return decrypted_data.decode()
        except Exception as e:
            logger.error(f"Token decryption failed: {e}")
            raise ValueError("Failed to decrypt token - possible tampering")

    def _validate_discord_token(self, token: str) -> bool:
        """Validate Discord bot token format"""
        parts = token.split('.')

        # Discord bot tokens have 3 parts: header.payload.signature
        if len(parts) != 3:
            return False

        try:
            # Validate header (bot tokens start with specific prefixes)
            header = base64.b64decode(parts[0] + '=' * (4 - len(parts[0]) % 4))
            if header not in [b'{"typ":"JWT","alg":"RS256"}', b'{"alg":"RS256","typ":"JWT"}']:
                return False
        except:
            return False

        # Additional format validations
        return (
            len(token) > 50 and  # Reasonable length
            any(token.startswith(prefix) for prefix in ['M', 'N', 'O']) and  # Discord prefixes
            '.' in token  # JWT format
        )

    def rotate_master_key(self) -> bool:
        """Emergency key rotation for security incidents"""
        try:
            # Generate new master key
            new_master_key = secrets.token_bytes(32)

            # Backup old key
            backup_path = f"{self.master_key_path}.backup"
            if os.path.exists(self.master_key_path):
                os.rename(self.master_key_path, backup_path)

            # Save new key
            with open(self.master_key_path, 'wb') as f:
                f.write(new_master_key)
            os.chmod(self.master_key_path, 0o600)

            # Reinitialize encryption with new key
            old_fernet = self.fernet
            self.fernet = self._initialize_encryption()

            logger.warning("🔄 CRITICAL: Master encryption key rotated - immediate token re-encryption required")
            return True

        except Exception as e:
            logger.error(f"Key rotation failed: {e}")
            # Attempt to restore old key
            if os.path.exists(backup_path):
                os.rename(backup_path, self.master_key_path)
                self.fernet = old_fernet
            return False
```

#### Rate Limiting & API Protection System
```python
# security/rate_limiter.py
import asyncio
import time
from collections import defaultdict, deque
from typing import Dict, Tuple, Optional
import logging
from dataclasses import dataclass

logger = logging.getLogger('RateLimiter')

@dataclass
class RateLimitConfig:
    """Configuration for rate limiting rules"""
    max_requests: int
    time_window: int  # seconds
    burst_allowance: int = 0
    backoff_multiplier: float = 2.0

class AdaptiveRateLimiter:
    """Advanced rate limiting with adaptive throttling and burst protection"""

    def __init__(self):
        self.endpoints: Dict[str, RateLimitConfig] = {
            'global_ban': RateLimitConfig(max_requests=5, time_window=60, burst_allowance=2),
            'guild_sync': RateLimitConfig(max_requests=20, time_window=300, burst_allowance=5),
            'user_lookup': RateLimitConfig(max_requests=50, time_window=60, burst_allowance=10),
            'audit_query': RateLimitConfig(max_requests=30, time_window=60, burst_allowance=5),
        }

        # Tracking structures
        self.request_history: Dict[str, deque] = defaultdict(lambda: deque(maxlen=1000))
        self.endpoint_backoffs: Dict[str, float] = {}
        self.global_violation_count = 0

    async def acquire(self, endpoint: str, guild_id: int = None) -> Tuple[bool, Optional[float]]:
        """
        Acquire permission to make API request with rate limiting

        Args:
            endpoint: API endpoint or operation type
            guild_id: Guild-specific rate limiting (optional)

        Returns:
            (allowed: bool, wait_time: float seconds or None)
        """

        current_time = time.time()
        config = self.endpoints.get(endpoint)

        if not config:
            logger.warning(f"No rate limit config for endpoint: {endpoint}")
            return True, None  # Allow if not configured

        # Check if endpoint is in backoff cooldown
        if endpoint in self.endpoint_backoffs:
            backoff_end = self.endpoint_backoffs[endpoint]
            if current_time < backoff_end:
                wait_time = backoff_end - current_time
                return False, wait_time

        # Create endpoint-specific key
        key = f"{endpoint}:{guild_id}" if guild_id else endpoint

        # Clean old requests outside time window
        while (self.request_history[key] and
               current_time - self.request_history[key][0] > config.time_window):
            self.request_history[key].popleft()

        # Check if request would exceed limit
        current_count = len(self.request_history[key])

        if current_count >= config.max_requests:
            # Calculate backoff time (exponential with configurable multiplier)
            base_backoff = config.time_window * config.backoff_multiplier
            violation_multiplier = min(self.global_violation_count + 1, 10)  # Cap at 10x
            backoff_time = base_backoff * violation_multiplier

            self.endpoint_backoffs[endpoint] = current_time + backoff_time
            self.global_violation_count += 1

            logger.warning(f"🚫 Rate limit exceeded for {endpoint}, backoff: {backoff_time}s")
            await self._log_rate_limit_violation(endpoint, current_count, guild_id)

            return False, backoff_time

        # Allow burst traffic within burst allowance
        recent_requests = sum(1 for t in self.request_history[key]
                             if current_time - t <= 1.0)  # Last second

        if recent_requests >= config.burst_allowance:
            # Throttle burst but allow request
            await asyncio.sleep(0.1)  # Minimal throttle

        # Record this request
        self.request_history[key].append(current_time)

        return True, None

    async def _log_rate_limit_violation(self, endpoint: str, request_count: int, guild_id: int = None):
        """Log rate limit violations for monitoring and security"""
        violation_data = {
            'endpoint': endpoint,
            'request_count': request_count,
            'guild_id': guild_id,
            'timestamp': time.time(),
            'global_violation_count': self.global_violation_count
        }

        logger.warning(f"RATE LIMIT VIOLATION: {violation_data}")

        # Could integrate with monitoring system
        # await monitoring_system.log_rate_violation(violation_data)

    def get_endpoint_stats(self, endpoint: str) -> Dict:
        """Get current stats for an endpoint"""
        config = self.endpoints.get(endpoint, RateLimitConfig(0, 0))
        history = self.request_history.get(endpoint, deque())

        current_count = len([t for t in history if time.time() - t <= config.time_window])

        return {
            'endpoint': endpoint,
            'current_requests': current_count,
            'max_requests': config.max_requests,
            'time_window': config.time_window,
            'burst_allowance': config.burst_allowance,
            'in_backoff': endpoint in self.endpoint_backoffs,
            'backoff_remaining': max(0, self.endpoint_backoffs.get(endpoint, 0) - time.time())
        }

    def reset_endpoint(self, endpoint: str):
        """Reset rate limiting for an endpoint (admin function)"""
        if endpoint in self.request_history:
            self.request_history[endpoint].clear()

        if endpoint in self.endpoint_backoffs:
            del self.endpoint_backoffs[endpoint]

        logger.info(f"Rate limiter reset for endpoint: {endpoint}")

# Global rate limiter instance
rate_limiter = AdaptiveRateLimiter()

# Usage decorator for automatic rate limiting
def rate_limited(endpoint: str):
    """Decorator to automatically enforce rate limiting"""
    def decorator(func):
        async def wrapper(*args, **kwargs):
            # Extract guild_id if available in arguments
            guild_id = kwargs.get('guild_id') or getattr(args[0] if args else None, 'guild_id', None)

            allowed, wait_time = await rate_limiter.acquire(endpoint, guild_id)

            if not allowed:
                raise RateLimitExceeded(f"Rate limit exceeded. Try again in {wait_time:.1f} seconds")

            return await func(*args, **kwargs)
        return wrapper
    return decorator

# Custom exception
class RateLimitExceeded(Exception):
    """Raised when rate limit is exceeded"""
    pass
```

---

### Production Deployment Infrastructure

#### Automated Deployment Pipeline
```bash
# deploy/production_deploy.sh
#!/bin/bash
set -euo pipefail  # Exit on error, undefined vars, pipe failures

# Configuration Variables
DEPLOYMENT_ENV=${DEPLOYMENT_ENV:-production}
WAYHAVEN_VERSION=$(git describe --tags --abbrev=0)
DEPLOYMENT_DIR="/opt/wayhaven"
BACKUP_DIR="/var/backups/wayhaven"
LOG_DIR="/var/log/wayhaven"

# Color output for logging
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m' # No Color

log() {
    echo -e "${BLUE}[$(date +'%Y-%m-%d %H:%M:%S')]${NC} $*" | tee -a "${LOG_DIR}/deploy.log"
}

error() {
    echo -e "${RED}ERROR:${NC} $*" >&2
}

warn() {
    echo -e "${YELLOW}WARNING:${NC} $*" >&2
}

success() {
    echo -e "${GREEN}SUCCESS:${NC} $*"
}

# Pre-deployment health checks
health_check() {
    log "Performing pre-deployment health checks..."

    # System resource validation
    local mem_kb=$(grep MemTotal /proc/meminfo | awk '{print $2}')
    local mem_gb=$((mem_kb / 1024 / 1024))

    if [ "$mem_gb" -lt 2 ]; then
        error "Insufficient memory: ${mem_gb}GB < 2GB required"
        exit 1
    fi

    success "Memory check passed: ${mem_gb}GB"

    # Disk space validation
    local available_kb=$(df "$DEPLOYMENT_DIR" | tail -1 | awk '{print $4}')
    local available_gb=$((available_kb / 1024 / 1024))

    if [ "$available_gb" -lt 5 ]; then
        error "Insufficient disk space: ${available_gb}GB < 5GB required"
        exit 1
    fi

    success "Disk space check passed: ${available_gb}GB available"

    # Database connectivity (if database exists)
    if [ -f "${DEPLOYMENT_DIR}/wayhaven_enforcer.db" ]; then
        if ! sqlite3 "${DEPLOYMENT_DIR}/wayhaven_enforcer.db" "SELECT 1;" >/dev/null 2>&1; then
            error "Database health check failed"
            exit 1
        fi
        success "Database connectivity verified"
    fi

    # Network connectivity to Discord API
    if ! curl -s --max-time 5 "https://discord.com/api/v10/gateway" >/dev/null; then
        error "Cannot reach Discord API"
        exit 1
    fi

    success "Network connectivity verified"
}

# Backup current installation
create_backup() {
    log "Creating deployment backup..."

    local backup_name="wayhaven_${WAYHAVEN_VERSION}_backup_$(date +%Y%m%d_%H%M%S)"
    local backup_path="${BACKUP_DIR}/${backup_name}"

    mkdir -p "$backup_path"

    # Backup application files
    if [ -d "$DEPLOYMENT_DIR" ]; then
        cp -r "${DEPLOYMENT_DIR}"/* "$backup_path"/ 2>/dev/null || true
        success "Application files backed up"
    fi

    # Backup database
    if [ -f "${DEPLOYMENT_DIR}/wayhaven_enforcer.db" ]; then
        cp "${DEPLOYMENT_DIR}/wayhaven_enforcer.db" "${backup_path}/"
        success "Database backed up"

        # Verify backup integrity
        if ! sqlite3 "${backup_path}/wayhaven_enforcer.db" "PRAGMA integrity_check;" >/dev/null; then
            error "Database backup integrity check failed"
            # Don't exit - continue with deployment
        fi
    fi

    # Backup configuration (exclude sensitive data)
    if [ -f "${DEPLOYMENT_DIR}/.env" ]; then
        # Create sanitized backup (remove sensitive tokens)
        grep -v "BOT_TOKEN\|APPLICATION_ID\|CLIENT_SECRET" "${DEPLOYMENT_DIR}/.env" > "${backup_path}/.env.backup"
        success "Configuration backed up (sanitized)"
    fi

    # Cleanup old backups (keep last 10)
    find "$BACKUP_DIR" -maxdepth 1 -type d -name "wayhaven_*_backup_*" \
        | sort | head -n -10 | xargs rm -rf 2>/dev/null || true

    success "Backup completed: $backup_name"

    # Export backup path for rollback
    echo "$backup_path" > /tmp/wayhaven_backup_path
}

# Deploy new version
deploy_application() {
    log "Deploying Wayhaven Enforcer v${WAYHAVEN_VERSION}..."

    # Create deployment directory
    mkdir -p "$DEPLOYMENT_DIR"

    # Stop existing service if running
    if systemctl is-active --quiet wayhaven-enforcer 2>/dev/null; then
        log "Stopping existing service..."
        systemctl stop wayhaven-enforcer
    fi

    # Backup current version
    create_backup

    # Extract new version
    log "Extracting application files..."
    cp -r ./* "$DEPLOYMENT_DIR"/ 2>/dev/null || true
    success "Application files deployed"

    # Set secure permissions
    chown -R wayhaven:wayhaven "$DEPLOYMENT_DIR"
    chmod 750 "$DEPLOYMENT_DIR"
    find "$DEPLOYMENT_DIR" -name "*.db" -exec chmod 660 {} \;
    find "$DEPLOYMENT_DIR" -name "*.key" -exec chmod 600 {} \; 2>/dev/null || true

    success "File permissions secured"
}

# Configure systemd service
configure_service() {
    log "Configuring systemd service..."

    cat > /etc/systemd/system/wayhaven-enforcer.service << EOF
[Unit]
Description=Wayhaven Enforcer Discord Bot
After=network.target
Wants=network.target

[Service]
Type=exec
User=wayhaven
Group=wayhaven
WorkingDirectory=${DEPLOYMENT_DIR}
ExecStart=${DEPLOYMENT_DIR}/venv/bin/python ${DEPLOYMENT_DIR}/bot.py
ExecReload=/bin/kill -HUP \$MAINPID

# Security hardening
NoNewPrivileges=yes
PrivateTmp=yes
ProtectHome=yes
ProtectSystem=strict

[Install]
WantedBy=multi-user.target
EOF

    # Reload systemd and enable service
    systemctl daemon-reload
    systemctl enable wayhaven-enforcer
    systemctl start wayhaven-enforcer

    # Verify service started successfully
    if systemctl is-active --quiet wayhaven-enforcer; then
        success "Service configured and started successfully"
    else
        error "Service failed to start"
        error "Check logs with: journalctl -u wayhaven-enforcer -f"
        exit 1
    fi
}

# Post-deployment validation
validate_deployment() {
    log "Validating deployment..."

    # Check if service is running
    if ! systemctl is-active --quiet wayhaven-enforcer; then
        error "Service is not running after deployment"
        exit 1
    fi

    success "Service validation passed"

    # Wait for bot to connect to Discord
    local attempts=0
    local max_attempts=30  # 5 minutes with 10s intervals

    while [ $attempts -lt $max_attempts ]; do
        if curl -s --max-time 5 "http://localhost:8080/health" >/dev/null 2>&1; then
            success "Bot health check passed"
            break
        fi

        attempts=$((attempts + 1))
        log "Waiting for bot startup (attempt $attempts/$max_attempts)..."
        sleep 10
    done

    if [ $attempts -eq $max_attempts ]; then
        warn "Bot may still be starting up - continuing deployment"
        warn "Monitor service with: journalctl -u wayhaven-enforcer -f"
    fi

    # Final status report
    success "Deployment completed successfully!"
    echo ""
    echo "Deployment Summary:"
    echo "  Version: v${WAYHAVEN_VERSION}"
    echo "  Service: $(systemctl is-active wayhaven-enforcer)"
    echo "  Logs: journalctl -u wayhaven-enforcer -f"
    echo "  Health: curl http://localhost:8080/health"
    echo ""
}

# Rollback on failure
rollback() {
    error "Deployment failed - initiating rollback..."

    # Stop failed service
    systemctl stop wayhaven-enforcer 2>/dev/null || true

    # Restore from backup
    if [ -f /tmp/wayhaven_backup_path ]; then
        local backup_path=$(cat /tmp/wayhaven_backup_path)

        if [ -d "$backup_path" ]; then
            log "Restoring from backup: $backup_path"
            cp -r "${backup_path}"/* "$DEPLOYMENT_DIR"/ 2>/dev/null || true
            systemctl start wayhaven-enforcer
            success "Rollback completed"
            exit 1
        fi
    fi

    error "Rollback failed - manual intervention required"
    exit 1
}

# Main deployment flow
main() {
    log "Starting Wayhaven Enforcer deployment (v${WAYHAVEN_VERSION})"
    log "Environment: ${DEPLOYMENT_ENV}"

    # Ensure script is run as root
    if [ "$EUID" -ne 0 ]; then
        error "This script must be run as root (sudo)"
        exit 1
    fi

    # Create required directories
    mkdir -p "$LOG_DIR" "$BACKUP_DIR"

    # Trap for cleanup on failure
    trap rollback ERR

    # Execute deployment steps
    health_check
    deploy_application
    configure_service
    validate_deployment

    success "🎓 Wayhaven Enforcer deployment completed successfully!"
    log "Monitor the service with: journalctl -u wayhaven-enforcer -f"
}

# Run main deployment
main "$@"
```

#### Health Monitoring & Alerting Infrastructure
```bash
# Production Monitoring Dashboard Setup
# Install monitoring dependencies
sudo apt update && sudo apt install -y prometheus-node-exporter grafana

# Configure custom Wayhaven metrics exporter
cat > /usr/local/bin/wayhaven_exporter.py << 'EOF'
#!/usr/bin/env python3
"""Wayhaven Enforcer Metrics Exporter for Prometheus"""

import json
import sqlite3
import time
from flask import Flask, Response
import logging

app = Flask(__name__)
logger = logging.getLogger('wayhaven_exporter')

DATABASE_PATH = "/opt/wayhaven/wayhaven_enforcer.db"

def get_database_metrics():
    """Extract key metrics from Wayhaven database"""

    try:
        conn = sqlite3.connect(DATABASE_PATH)
        cursor = conn.cursor()

        metrics = {}

        # Punishment statistics
        cursor.execute("""
            SELECT action, COUNT(*) as count
            FROM punishments
            WHERE created_at > datetime('now', '-1 hour')
            GROUP BY action
        """)

        for action, count in cursor.fetchall():
            metrics[f'wayhaven_punishments_{action}_total'] = count

        # Guild relationship count
        cursor.execute("SELECT COUNT(*) FROM guild_relationships WHERE auto_sync_enabled = 1")
        metrics['wayhaven_active_relationships'] = cursor.fetchone()[0]

        # Security alerts (last 24 hours)
        cursor.execute("""
            SELECT COUNT(*) FROM security_alerts
            WHERE created_at > datetime('now', '-24 hours')
        """)
        metrics['wayhaven_security_alerts_24h'] = cursor.fetchone()[0]

        # System health score
        cursor.execute("""
            SELECT AVG(
                CASE
                    WHEN status = 'healthy' THEN 1.0
                    WHEN status = 'warning' THEN 0.5
                    ELSE 0.0
                END
            ) as health_score
            FROM system_health
            WHERE created_at > datetime('now', '-1 hour')
        """)

        health_result = cursor.fetchone()[0]
        metrics['wayhaven_system_health_score'] = health_result if health_result else 0.0

        conn.close()
        return metrics

    except Exception as e:
        logger.error(f"Failed to get database metrics: {e}")
        return {}

@app.route('/metrics')
def metrics():
    """Prometheus metrics endpoint"""

    metrics_data = get_database_metrics()

    # Format for Prometheus
    output = []

    for metric_name, value in metrics_data.items():
        output.append(f'# HELP {metric_name} Wayhaven Enforcer metric')
        output.append(f'# TYPE {metric_name} gauge')
        output.append(f'{metric_name} {value}')

    return Response('\n'.join(output), mimetype='text/plain')

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8080)
EOF

# Make executable and start metrics service
sudo chmod +x /usr/local/bin/wayhaven_exporter.py

# Create systemd service for metrics exporter
sudo tee /etc/systemd/system/wayhaven-exporter.service > /dev/null << EOF
[Unit]
Description=Wayhaven Enforcer Metrics Exporter
After=wayhaven-enforcer.service

[Service]
Type=simple
User=wayhaven
ExecStart=/usr/local/bin/wayhaven_exporter.py
Restart=always

[Install]
WantedBy=multi-user.target
EOF

sudo systemctl enable wayhaven-exporter
sudo systemctl start wayhaven-exporter
```

#### Container Deployment with Docker
```yaml
# docker-compose.production.yml
version: '3.8'
services:
  wayhaven-enforcer:
    image: wayhaven/enforcer:${WAYHAVEN_VERSION}
    container_name: wayhaven-enforcer
    restart: unless-stopped
    environment:
      - DEPLOYMENT_ENV=production
      - BOT_TOKEN=${BOT_TOKEN}
      - APPLICATION_ID=${APPLICATION_ID}
      - MAIN_GUILD_ID=${MAIN_GUILD_ID}
      - DATABASE_URL=sqlite+aiosqlite:////app/wayhaven_enforcer.db
    volumes:
      - ./data:/app/data
      - ./logs:/app/logs
      - ./backups:/app/backups
    networks:
      - wayhaven-net
    depends_on:
      - wayhaven-db
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8080/health"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 40s
    security_opt:
      - no-new-privileges:true
    read_only: true
    tmpfs:
      - /tmp

  wayhaven-db:
    image: alpine:latest
    command: ["sh", "-c", "mkdir -p /data && chmod 750 /data && tail -f /dev/null"]
    volumes:
      - wayhaven_database:/data
    networks:
      - wayhaven-net

  prometheus:
    image: prom/prometheus:latest
    container_name: wayhaven-prometheus
    volumes:
      - ./monitoring/prometheus.yml:/etc/prometheus/prometheus.yml:ro
      - prometheus_data:/prometheus
    command:
      - '--config.file=/etc/prometheus/prometheus.yml'
      - '--storage.tsdb.path=/prometheus'
      - '--web.console.libraries=/etc/prometheus/console_libraries'
      - '--web.console.templates=/etc/prometheus/consoles'
      - '--storage.tsdb.retention.time=200h'
      - '--web.enable-lifecycle'
    restart: unless-stopped
    networks:
      - wayhaven-net
    ports:
      - "9090:9090"

  grafana:
    image: grafana/grafana:latest
    container_name: wayhaven-grafana
    environment:
      - GF_SECURITY_ADMIN_PASSWORD=${GRAFANA_ADMIN_PASSWORD}
      - GF_USERS_ALLOW_SIGN_UP=false
    volumes:
      - grafana_data:/var/lib/grafana
      - ./monitoring/grafana/provisioning:/etc/grafana/provisioning:ro
    restart: unless-stopped
    networks:
      - wayhaven-net
    ports:
      - "3000:3000"

volumes:
  wayhaven_database:
    driver: local
  prometheus_data:
  grafana_data:

networks:
  wayhaven-net:
    driver: bridge
```

```dockerfile
# Dockerfile.production
FROM python:3.11-slim

# Security: Create non-root user
RUN groupadd -r wayhaven && useradd -r -g wayhaven wayhaven

# Install system dependencies
RUN apt-get update && apt-get install -y \
    curl \
    sqlite3 \
    && rm -rf /var/lib/apt/lists/*

# Create application directory
WORKDIR /app
RUN chown wayhaven:wayhaven /app

# Switch to non-root user
USER wayhaven

# Copy and install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir --user -r requirements.txt

# Copy application code
COPY --chown=wayhaven:wayhaven . .

# Create necessary directories
RUN mkdir -p data logs backups

# Health check endpoint
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
    CMD curl -f http://localhost:8080/health || exit 1

# Start the application
CMD ["python", "bot.py"]

EXPOSE 8080

LABEL maintainer="Wayhaven Security Team <security@wayhaven.dev>"
LABEL version="${WAYHAVEN_VERSION}"
LABEL description="Wayhaven Enforcer - Zero-Leak Discord Moderation Bot"
```

---

### Support & Contributing Guidelines

#### Community Support Resources

**📚 Official Documentation**
- **User Guide**: Complete setup and configuration manual
- **API Reference**: Technical documentation for developers
- **Security Guidelines**: Best practices for deployment
- **Troubleshooting FAQ**: Common issues and solutions

**🆘 Getting Help**

| Support Channel | Purpose | Response Time | Availability |
|----------------|---------|---------------|--------------|
| **📧 Email Support** | Technical issues, security reports | 24-48 hours | 24/7 |
| **💬 Discord Community** | General questions, user discussions | 2-24 hours | Community-driven |
| **🐛 GitHub Issues** | Bug reports, feature requests | 24-72 hours | Public repository |
| **📖 Documentation Wiki** | Self-service troubleshooting | Immediate | Always available |
| **🚨 Security Advisories** | Security vulnerabilities | 2 hours | Emergency support |

**Critical Support Contacts:**
- **Security Vulnerabilities**: `security@wayhaven.dev` (PGP encrypted)
- **Production Downtime**: `alerts@wayhaven.dev` (24/7 pager)
- **Legal/Compliance Inquiries**: `legal@wayhaven.dev`

#### Bug Reporting Guidelines

**🐛 Filing Effective Bug Reports**

**Before Reporting:**
- [ ] Check the troubleshooting guide
- [ ] Search existing GitHub issues
- [ ] Update to the latest version
- [ ] Test in a development environment

**Required Information:**
```
🔍 Bug Report Template:

**Environment:**
- Wayhaven Version: v2.1.0
- Python Version: 3.11.2
- Operating System: Ubuntu 22.04 LTS
- Database: SQLite 3.39.4
- Discord.py Version: 2.3.2

**Description:**
[Clear, concise description of the issue]

**Steps to Reproduce:**
1. [Step-by-step reproduction steps]
2. [Expected behavior]
3. [Actual behavior]

**Logs & Error Messages:**
```
[Paste relevant log excerpts here]
```

**Additional Context:**
[Any additional information, screenshots, configuration details]

**Impact:**
[How severely does this affect your operations?]

**Workaround:**
[Have you found any temporary workarounds?]
```

#### Feature Request Process

**💡 Suggesting New Features**

**Feature Request Template:**
```markdown
## Feature Request: [Brief Title]

### Problem Statement
[Describe the problem this feature would solve]

### Proposed Solution
[Detailed description of the proposed feature]

### Alternative Solutions
[Other approaches you've considered]

### Use Cases
[Specific scenarios where this feature would be valuable]

### Implementation Notes
[Technical considerations, complexity estimates]

### Security Implications
[How might this affect the ZERO-LEAK security model?]

### Priority Level
- [ ] Critical (Security/Breaking bug fix)
- [ ] High (Major feature/Reliability improvement)
- [ ] Medium (Enhancement/QoL improvement)
- [ ] Low (Nice-to-have/Minor enhancement)
```

#### Development Workflow

**🌟 Contributing to Wayhaven Enforcer**

**Code Contribution Guidelines:**
```python
# Quality Standards - All code must pass:
# ✓ Black auto-formatting (88 char line length)
# ✓ Flake8 linting (E203,W503 exemptions allowed)
# ✓ MyPy static type checking (strict mode)
# ✓ Unit test coverage minimum 85%
# ✓ Integration tests for new features
# ✓ Security audit with bandit (-r .)
# ✓ Documentation updated
```

**Pull Request Process:**

**Step 1: Setup Development Environment**
```bash
# Fork and clone the repository
git clone https://github.com/your-username/wayhaven-enforcer.git
cd wayhaven-enforcer

# Create feature branch
git checkout -b feature/your-feature-name

# Set up development environment (see Development Setup section)
python -m venv venv
source venv/bin/activate  # Linux/macOS
pip install -r requirements-dev.txt
```

**Step 2: Development and Testing**
```bash
# Make your changes following the code standards
# Ensure all tests pass
pytest --cov=wayhaven_enforcer --cov-report=term-missing

# Run security audit
bandit -r wayhaven_enforcer/

# Code quality checks
black wayhaven_enforcer/
flake8 wayhaven_enforcer/
mypy wayhaven_enforcer/
```

**Step 3: Documentation and Review**
```bash
# Update documentation for any new features
# Add tests for new functionality
# Update CHANGELOG.md with your changes
# Ensure commit messages follow conventional format

# Conventional commit format:
# feat(sync): Add protection against reverse sync operations
# fix(database): Resolve connection pool deadlock issue
# docs(readme): Add Docker deployment section
# security(auth): Implement token rotation endpoint
```

**Step 4: Submit Pull Request**
```
🎯 Pull Request Checklist:
□ Branch is up to date with main
□ All tests pass locally and in CI/CD
□ Code coverage >= 85%
□ Documentation updated
□ Security audit passed
□ Breaking changes documented
□ Related issues linked

📋 Pull Request Template:
## Description
[Brief summary of changes]

## Type of Change
- [ ] Bug fix (non-breaking)
- [ ] New feature (non-breaking)
- [ ] Breaking change
- [ ] Documentation update
- [ ] Security enhancement

## Testing
[Describe testing performed]

## Security Impact
[Assess impact on ZERO-LEAK model]

## Checklist
- [ ] My code follows the project's style guidelines
- [ ] I have performed a self-review of my own code
- [ ] I have added tests that prove my fix/feature works
- [ ] Security implications have been considered
- [ ] Documentation has been updated
```

#### Review Process Timeline:
1. **Automated Checks**: 2-5 minutes (CI/CD pipeline)
2. **Initial Review**: 24-48 hours (maintainer assessment)
3. **Security Review**: 24-72 hours (if security implications)
4. **Final Merge**: Immediate (after approvals)

#### Release Process

**🚀 Version Release Workflow**

**Version Numbering** (Semantic Versioning):
- **MAJOR**.MINOR.PATCH (e.g., v2.1.0)
- **MAJOR**: Breaking API changes or significant architectural updates
- **MINOR**: New features, backward compatible
- **PATCH**: Bug fixes, security patches

**Release Checklist:**
```yaml
version: "2.1.0"

pre_release:
  - [ ] All tests passing on CI/CD
  - [ ] Security audit completed
  - [ ] Code coverage >= 85%
  - [ ] Documentation updated
  - [ ] Migration scripts tested
  - [ ] Breaking changes documented

release:
  - [ ] Create release branch (release/v2.1.0)
  - [ ] Update version numbers in code
  - [ ] Generate release notes
  - [ ] Create GitHub release with artifacts
  - [ ] Update Docker images
  - [ ] Update documentation site
  - [ ] Announce release on Discord and forums

post_release:
  - [ ] Monitor for critical bugs (first 24h)
  - [ ] Update security advisories if needed
  - [ ] Community support for upgrade issues
```

#### Security Disclosure Program

**🔒 Responsible Disclosure**

We appreciate researchers helping keep Wayhaven Enforcer and our users safe. If you discover a security vulnerability, please help us by disclosing it responsibly.

**Disclosure Process:**
1. **Do Not** create public GitHub issues for security vulnerabilities
2. **Contact** our security team directly: `security@wayhaven.dev`
3. **Include** detailed reproduction steps and impact assessment
4. **Allow** reasonable time for fix development before public disclosure
5. **Receive** credit in security advisories and our Hall of Fame

**What We Provide:**
- **Acknowledgment**: Public credit for responsible disclosures
- **Communication**: Regular updates on progress
- **Coordination**: Assistance with disclosure timing
- **Bug Bounty**: Monetary rewards for critical vulnerability reports

**Hall of Fame** (Recent Contributors):
- `@SaoudRizwan` - JWT validation bypass in authentication system (April 2024)
- `@AnonymousResearcher` - Database query injection vulnerability (March 2024)
- `@SecurityExpert2024` - Cross-guild permission elevation (February 2024)

#### License & Legal Information

**📜 MIT License**

Copyright (c) 2024 Wayhaven Security Team

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

**THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.**

---

## Thank You! 🎓

Thank you for choosing **Wayhaven Enforcer** for your Discord moderation needs. Whether you're managing a school community, gaming group, or business network, we're committed to providing the most secure and reliable cross-server moderation solution available.

**Stay Safe, Stay Connected! 🤝**

---

*Built with ❤️ by the Wayhaven Security Team*  
*Empowering communities through secure, ZERO-LEAK moderation*  
*Visit us at [wayhaven.dev](https://wayhaven.dev) for more security tools*
