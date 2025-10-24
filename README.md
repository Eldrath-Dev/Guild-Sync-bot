
# Wayhaven Enforcer Bot

[![Version](https://img.shields.io/badge/version-2.1.0-blue.svg)](https://github.com)
[![Python](https://img.shields.io/badge/python-3.8+-brightgreen.svg)](https://www.python.org/)
[![Discord API](https://img.shields.io/badge/discord-api--v2.3+-7289da.svg)](https://discord.com/developers/docs/intro)
[![Security](https://img.shields.io/badge/security-ZERO--LEAK-critical.svg)](https://github.com)
[![Status](https://img.shields.io/badge/status-production--ready-green.svg)](https://github.com)
[![Platforms](https://img.shields.io/badge/platforms-Windows%20%7C%20Mac%20%7C%20Linux-lightgrey.svg)](https://github.com)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com)
[![Database](https://img.shields.io/badge/database-SQLite-yellow.svg)](https://sqlite.org/)
[![Commands](https://img.shields.io/badge/commands-slash%20commands-orange.svg)](https://discord.com/developers/docs/interactions/slash-commands)

---

## 📚 Getting Started

### What is Wayhaven Enforcer?

Imagine you have a school with many classrooms and playgrounds. Sometimes a student might break rules in one classroom and then try to run to another classroom to keep causing trouble. That's not fair to the other students who follow the rules!

**Wayhaven Enforcer** is like having a Principal who can see what happens in ALL the classrooms at once. When a student gets in trouble in the cafeteria, they automatically get the same fair consequence in the gym, library, and computer lab too. No more running between classrooms to avoid getting caught!

### How It Works (School Analogy)

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

### Quick Benefits

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

#### Windows Installation:
1. Visit `https://python.org/downloads/`
2. Click the yellow "Download Python 3.12.0" button
3. Run the downloaded installer
4. **IMPORTANT:** Check the box "Add Python to PATH"
5. Click "Install Now" and wait 2-3 minutes

#### Mac Installation:
1. Visit `https://python.org/downloads/`
2. Download the macOS installer
3. Double-click the .pkg file to install
4. Open Terminal and test with: `python3 --version`

#### Linux Installation:
```bash
# Ubuntu/Debian:
sudo apt update && sudo apt install python3 python3-pip -y

# Fedora/RHEL:
sudo dnf install python3 python3-pip -y

# Test installation:
python3 --version
pip3 --version
```

### Step 2: Download Bot Files

1. **Get the source code:**
   - Download from your repository
   - Click the green "Code" button
   - Select "Download ZIP"
   - Save to Desktop or Documents folder

2. **Extract the ZIP file** (right-click → Extract All)

3. **Verify file structure:**
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

### Step 3: Install Dependencies

```bash
# Navigate to bot folder (adjust path as needed)
cd "path/to/your/bot/folder"

# Install all required packages
pip install -r requirements.txt
```

**What gets installed:**
- `discord.py` - Discord API integration
- `python-dotenv` - Environment variable management
- `aiosqlite` - Database operations
- `sqlalchemy` - Database toolkit
- `aiofiles` - File operations

**If you encounter errors, try:**
```bash
# Alternative installation methods
pip3 install -r requirements.txt
python -m pip install -r requirements.txt
python3 -m pip install -r requirements.txt
```

### Step 4: Create Discord Bot Account

**⚠️ IMPORTANT:** You must be a server administrator to complete this step!

#### Create Application:
1. Go to `https://discord.com/developers/applications`
2. Click "New Application" (blue button, top right)
3. Name it "Wayhaven Enforcer" or your preferred name
4. Accept terms and conditions

#### Create Bot User:
1. Click "Bot" in the left sidebar
2. Click "Add Bot" button
3. Skip special privileges for now
4. Set an avatar if desired

#### Get Bot Token:
1. Under "Token" section, click "Copy"
2. **⚠️ SECURITY:** Keep this token secret like a password
3. Never share in chat or save in plain text files

#### Configure Permissions:
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

3. Copy the permission number (typically 268561488)
4. Note the Application ID from "General Information"

#### Invite Bot to Servers:
1. Go to OAuth2 → URL Generator
2. Check "bot" and "applications.commands"
3. Copy the generated invite URL
4. Paste in browser and authorize for each server
5. Verify bot appears online in member list

**Note:** Invite the bot to EVERY server you want to moderate!

### Step 5: Configuration Setup

Create a `.env` file in your bot folder:

```env
# Wayhaven Enforcer Configuration
# Replace with your actual values!

# Bot Account Information
BOT_TOKEN=your_secret_token_here_really_replace_this
APPLICATION_ID=123456789012345678
CLIENT_ID=123456789012345678

# Main Server (Principal's Office)
# Right-click server name → Copy ID
MAIN_GUILD_ID=987654321098765432

# Optional: Test server for practice
TEST_GUILD_ID=876543210987654321

# Advanced Settings (leave default for now)
DEBUG=false
DATABASE_URL=sqlite+aiosqlite:///wayhaven_enforcer.db
```

**Common Configuration Mistakes:**
- Don't add quotes around values unless they contain spaces
- Ensure server IDs are 18+ digits long (copy carefully)
- Regenerate token immediately if compromised

### Step 6: Database Initialization

```bash
# Initialize the bot's memory system
python setup_database.py
```

**Expected Success Output:**
```
Wayhaven Enforcer Database Setup
Creating database tables...
✅ Created punishments table
✅ Created guild_relationships table (ZERO-LEAK enabled)
✅ Created command_audit table (100% compliance)
✅ Created security_alerts table
✅ Created system_health table
✅ Database initialization complete!
⚠️  IMMUTABLE SECURITY: Database locked for ZERO-LEAK protection
🔒 Ready for bot startup
```

**Database:** Uses SQLite (no MySQL/PostgreSQL required for standard deployments)

### Step 7: First Launch

```bash
# Start the bot for the first time
python bot.py
```

**Expected Startup Output:**
```
Starting Wayhaven Enforcer v2.1.0...
Zero-Leak Security: ACTIVE
Database: Connected
Loading cogs...
✅ Loaded punishments
✅ Loaded sync
✅ Loaded setup_cog
✅ Loaded audit
✅ Loaded reconciliation
✅ Slash commands synced globally
Wayhaven Enforcer is ready!

Logged in as:
Wayhaven Enforcer#1234
Connected to 3 servers
```

### Step 8: Server Configuration

#### Create Required Roles:
1. **Go to Server Settings → Roles**
2. **Create "Muted" role:**
   - Color: Orange or red
   - Deny: Send Messages, Send Messages in Threads, Speak in voice
   - Allow: View channels (for timeout visibility)

#### Create Moderation Channels:
1. **Create #moderation-logs:**
   - Hide from regular members
   - Used for punishment logging
2. **Create #security-alerts:**
   - Hide from everyone except admins
   - Used for system security notifications

#### Configure Bot Settings:
```
/config muterole role:@Muted
/config notifications channel:#moderation-logs enabled:true
/config logchannel channel:#security-alerts
```

#### Set Up Main Server:
```
/setup main-guild
```

**This designates your server as the "Principal's Office" - punishments here spread everywhere!**

#### Connect Child Servers:
```
/setup add-child guild-id:123456789012345678
```

Repeat for each server you want to connect. Child servers receive punishments from main server but cannot spread punishments themselves (ZERO-LEAK safety).

---

## ⚙️ Configuration

### Server Roles Setup

#### Required Roles:
| Role | Purpose | Permissions |
|------|---------|-------------|
| **Muted** | Timeout users | Deny: Send Messages, Speak |
| **Moderator** | Basic moderation | Use warn, timeout commands |
| **Admin** | Full moderation | All commands including ban/unban |

#### Role Hierarchy:
```
Server Owner (Full Access)
├── Administrators (Setup, Ban/Unban, Network Management)
├── Moderators (Warn, Mute, Timeout, Kick)
└── Child Server Staff (Local warnings/kicks only)
```

### Channel Configuration

#### Essential Channels:
| Channel | Purpose | Privacy |
|---------|---------|---------|
| **#moderation-logs** | Punishment records | Staff only |
| **#security-alerts** | System notifications | Admins only |
| **#bot-commands** | Command usage | Public (optional) |

#### Bot Configuration Commands:
```bash
# Set mute role
/config muterole role:@Muted

# Configure notification channel
/config notifications channel:#moderation-logs enabled:true

# Set security alerts channel
/config logchannel channel:#security-alerts

# Enable audit logging
/config audit enabled:true
```

### Main/Child Server Architecture

#### Main Server (Principal's Office):
- Can issue punishments that spread to all child servers
- Full moderation capabilities
- Central audit logging
- Network management controls

#### Child Servers (Classrooms):
- Receive punishments from main server
- Cannot spread punishments (ZERO-LEAK security)
- Local moderation only (warnings, kicks)
- Automatic sync compliance

#### Setting Up Relationships:
```bash
# Designate main server
/setup main-guild

# Link child servers
/setup add-child guild-id:123456789012345678

# Test connection
/setup test-connection guild-id:123456789012345678

# View network status
/setup dashboard
```

---

## 📋 Commands Reference

### Moderation Commands

| Command | Description | Example | Permissions |
|---------|-------------|---------|-------------|
| `/ban user:@username reason:Spam` | Ban user across all linked servers | `/ban user:@Spammer reason:Excessive spam` | Administrator |
| `/unban user:123456789 reason:Appeal` | Unban user from all servers | `/unban user:987654321 reason:Appeal approved` | Administrator |
| `/kick user:@username reason:Disruption` | Remove user from current server | `/kick user:@Loud reason:Disrupting chat` | Moderator |
| `/mute user:@username duration:30m reason:Spam` | Mute user temporarily | `/mute user:@Chatter duration:1h reason:Excessive talking` | Moderator |
| `/timeout user:@username duration:2h reason:Argument` | Discord native timeout | `/timeout user:@Arguer duration:1d reason:Heated argument` | Moderator |
| `/warn user:@username reason:First warning` | Send warning via DM | `/warn user:@Newbie reason:Please read rules` | Staff |

### Setup & Administration Commands

#### Server Linking:
| Command | Purpose |
|---------|---------|
| `/setup main-guild` | Designate server as main hub |
| `/setup add-child guild-id:123456789` | Link child server to main |
| `/setup remove-child guild-id:123456789` | Remove server relationship |
| `/setup test-connection guild-id:123456789` | Test server connectivity |

#### Configuration:
| Command | Purpose |
|---------|---------|
| `/config muterole role:@Muted` | Set mute role |
| `/config notifications channel:#logs enabled:true` | Configure logging |
| `/config audit enabled:true` | Enable audit system |

#### Monitoring:
| Command | Purpose |
|---------|---------|
| `/setup dashboard` | View network status |
| `/audit log user:@user days:30` | User punishment history |
| `/audit stats days:7` | Weekly statistics |

### Permission Structure

#### Main Server Permissions:
- **Administrators:** Full control - ban, unban, setup network, configure settings
- **Moderators:** Can warn, mute, timeout, kick users
- **Staff:** Can issue warnings only

#### Child Server Permissions:
- **Staff:** Can only punish locally (warnings/kicks only)
- **Cannot spread punishments** (ZERO-LEAK security feature)

---

## 🔧 Troubleshooting Guide

### Bot Startup Issues

#### "Python not recognized"
**Solution:** Reinstall Python with "Add to PATH" checked (Windows) or use `python3` (Mac/Linux)

#### "Improper token passed"
**Cause:** Invalid BOT_TOKEN in `.env` file
**Solution:**
1. Go to Discord Developer Portal
2. Regenerate token if needed
3. Update `.env` file with correct token
4. Restart bot

#### "Discord login failure"
**Possible Causes:**
- Internet connectivity issues
- Discord API service disruption (check discordstatus.com)
- Expired bot token
- Regional restrictions

#### "Module 'discord' not found"
**Solution:**
```bash
pip install -r requirements.txt
# Or specifically:
pip install discord.py==2.3.0 --force-reinstall
```

### Permission Issues

#### "Missing Permissions" Error
**Checklist:**
- Bot has correct permissions in server settings?
- User running command has administrator privileges?
- Discord Developer Portal permissions match server permissions?

#### Commands Not Appearing
**Troubleshooting Steps:**
1. Verify bot is online and responsive
2. Try typing `/` to refresh command list
3. Confirm "Use Slash Commands" permission is enabled
4. Restart bot (commands sync on startup)

### Cross-Server Sync Problems

#### Punishments Not Spreading
**Common Causes:**
- Target server not configured as child server (`/setup add-child`)
- Bot not invited to child server
- Child server administrator didn't grant bot permissions
- ZERO-LEAK protection preventing unauthorized sync (this is intentional)

#### "Child server blocked by security"
**This is NORMAL behavior!**
- Child servers cannot spread punishments (safety feature)
- Only main server can spread to children
- Prevents accidental network-wide punishments

#### Bot Offline in Child Servers
**Possible Issues:**
- Bot not invited to that specific server
- Server region blocking Discord services
- Network connectivity problems

### Database Issues

#### "Database locked" Error
**Immediate Solutions:**
```bash
# Stop bot first, then:
cp wayhaven_enforcer.db backup.db  # Create backup
python setup_database.py           # Recreate database
```

**Prevention:** Avoid opening database file in other programs while bot is running

#### Database Corruption
**Recovery Process:**
1. Stop bot immediately
2. Create backup: `cp wayhaven_enforcer.db backup_corrupt.db`
3. Reset database: `rm wayhaven_enforcer.db && python setup_database.py`
4. Restore missing data if possible

#### Performance Optimization
```bash
# Database maintenance
sqlite3 wayhaven_enforcer.db "VACUUM;"        # Optimize database
sqlite3 wayhaven_enforcer.db "PRAGMA integrity_check;"  # Verify integrity
```

### Advanced Troubleshooting

#### Enable Debug Logging:
```env
# Add to .env file
DEBUG=true
```
Restart bot for detailed console logging.

#### Rate Limiting Issues:
- Discord API limits: ~50 requests/second
- Wayhaven handles this automatically
- If issues persist, reduce sync frequency

#### Memory Management:
- Normal usage: 50-100MB RAM
- Restart weekly if usage exceeds 200MB
- Monitor with Task Manager (Windows) or Activity Monitor (Mac)

---

## 🏢 Enterprise Compliance & Legal Framework

### GDPR Compliance Implementation

**For organizations in Europe or handling European data:**

#### Data Controller Responsibilities
Wayhaven acts as a data processor on behalf of Discord server administrators (the data controllers).

#### Lawful Processing Basis
- **Legitimate Interest:** Operating moderation systems for community safety
- **Legal Obligation:** Compliance with Discord's Terms of Service
- **Consent:** Users consent by joining moderated servers

#### Data Categories Processed
```
Stored Data:
├── Personal Identifiers: Discord User IDs (pseudonymized)
├── Event Data: Moderation actions, timestamps, reasons
├── Communication: Warning messages (when sent)
└── Metadata: Command usage patterns, server interaction logs
```

#### User Rights Implementation

**Right to Information (Articles 13-14):**
- Provide privacy notice explaining data processing
- Transparently document data retention policies
- Explain user rights for data subjects

**Right to Access (Article 15):**
```bash
/audit log user:@username days:365
```

**Right to Rectification (Article 16):**
- Server administrators can correct inaccurate data
- Users can request corrections through appeal processes

**Right to Erasure ("Right to be Forgotten") (Article 17):**
```python
async def delete_user_data(user_id: str):
    await db.execute("DELETE FROM punishments WHERE target_user = ?", (user_id,))
    await db.execute("DELETE FROM command_audit WHERE user_id = ?", (user_id,))
    await db.log_compliance_event("user_data_erased", {"user_id": user_id})
    return {"status": "erased", "user_id": user_id}
```

**Right to Data Portability (Article 20):**
```bash
/audit export days:365 user-filter:@username format:json
```

#### Data Retention Schedule

| Data Type | Primary Retention | Extended Retention | Disposal Method |
|-----------|-------------------|-------------------|-----------------|
| Active Punishments | Until expired + 90 days | N/A | Automatic |
| Audit Logs | 3 years | Up to 7 years if legal requirement | Secure deletion |
| Command Logs | 6 months | 24 months for security investigations | Encrypted destruction |
| System Logs | 3 months | 12 months for debugging | Compression then deletion |

#### Data Protection Impact Assessment (DPIA)
- Controllers must conduct DPIA before deployment
- Technology assessment completed
- Risk mitigation strategies documented
- Data protection measures implemented

---

## 📞 Support & Contributing

### Getting Help
- Check the troubleshooting guide above
- Review Discord Developer documentation
- Verify bot permissions in Discord server settings

### Reporting Issues
- Include bot version and Python version
- Provide error messages and console output
- Describe steps to reproduce the issue
- Note any recent configuration changes

### Contributing
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

---

**Wayhaven Enforcer Bot v2.1.0** - Professional Discord Moderation with ZERO-LEAK Security
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

**Resource:** SQLite is used (no MySQL/PostgreSQL needed for small deployments)

### Step 7: First Boot 🚀

```bash
# Start your bot for the first time:
python bot.py
```

**What you should see:**
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

#### If It Doesn't Start:

**Token Invalid:**
```
discord.errors.LoginFailure: Improper token passed
```
- Check your `.env` file has the correct BOT_TOKEN
- Make sure you copied the token correctly (including all characters)

**Permission Issues:**
```
discord.errors.Forbidden: Missing Permissions
```
- Bot doesn't have the right permissions in some servers
- Go back and reinvite with correct permissions

**Database Issues:**
```
sqlite3.OperationalError: database is locked
```
- Close any other programs using the database
- Run `python setup_database.py` again

**Module Not Found:**
```
ModuleNotFoundError: No module named 'discord'
```
- Run `pip install -r requirements.txt` again

#### Test Basic Functionality:
1. In Discord, type `/` and look for Wayhaven commands
2. Test a warning: `/warn user:@Yourself reason:Testing Wayhaven setup`
3. Check if you received the warning message and if it logged

### Step 8: Essential Server Configuration 🏫

#### Create Required Roles:
1. **Go to Server Settings → Roles**
2. **Create "Muted" role:**
   - Color: Orange/red
   - Deny: Send Messages, Send Messages in Threads, Speak in voice
   - Allow voice and text channel viewing

#### Create Moderation Channels:
1. **Create #moderation-logs:**
   - Hide from regular members
   - Used for punishment logging
2. **Create #security-alerts:**
   - Hide from everyone except admins
   - Used for system security issues

#### Link Wayhaven to Your Channels:
```
/config muterole role:@Muted
/config notifications channel:#moderation-logs enabled:true
/config logchannel channel:#security-alerts
```

#### Make Your Server a "Main Server":
```
/setup main-guild
```

**This designates your server as the "Principal's Office" - punishments here spread everywhere!**

#### Connect Child Servers:
```
/setup add-child guild-id:123456789012345678
```

Repeat this for each server you want to connect. The child servers will receive punishments from the main server but cannot spread punishments themselves (ZERO-LEAK safety).

---

## Complete Command Reference 📋

### Moderation Commands (The Main Tools):

| Command | What It Does | Example | Who Can Use |
|---------|--------------|---------|-------------|
| `/ban user:@username reason:Kicked too many times` | Permanently removes user from all linked servers | `/ban user:@Spammer reason:Spam` | Admins, Moderators |
| `/unban user:123456789 reason:Appeal approved` | Allows banned user back into all servers | `/unban user:987654321 reason:Mistake` | Admins only |
| `/kick user:@username reason:Temporary removal` | Removes user from current server only | `/kick user:@Loud reason:Disruption` | Admins, Moderators |
| `/mute user:@username duration:30m reason:Talking too much` | Prevents typing/speaking temporarily | `/mute user:@Chatter duration:1h` | Admins, Moderators |
| `/timeout user:@username duration:2h reason:Argument` | Discord's built-in timeout system | `/timeout user:@Arguer duration:1d` | All moderators with permission |
| `/warn user:@username reason:Reminder of rules` | Official warning to user (via DM) | `/warn user:@Newbie reason:Rule 1` | All staff |

### Setup & Administration Commands:

| Category | Commands | Purpose |
|----------|----------|---------|
| **Server Linking** | `/setup main-guild`<br>`/setup add-child guild-id:123`<br>`/setup remove-child guild-id:123` | Designate main server, connect/remove child servers |
| **Server Status** | `/setup dashboard`<br>`/setup test-connection guild-id:123` | Check overall network health, test specific connections |
| **Configuration** | `/config muterole role:@Muted`<br>`/config notifications channel:#logs enabled:true` | Set mute role, configure logging channels |
| **Audit System** | `/audit log user:@user days:30`<br>`/audit stats days:7`<br>`/audit warnings user:@user` | Review user history, get statistics |

### Permission Structure:

**Main Server Admins**: Full control - can ban, unban, setup network
**Main Server Moderators**: Can warn, mute, timeout, kick  
**Child Server Staff**: Can only punish locally (warnings/kicks only)

**ZERO-LEAK RULE**: Child servers CANNOT spread punishments to other servers - keeps things safe!

---

## Complete Troubleshooting Guide 🔧

### "Bot Won't Start" Problems:

#### Problem: "Python not recognized"
**Fix:** Reinstall Python with "Add to PATH" checked (Windows) or use `python3` on Mac/Linux

#### Problem: "Improper token passed"
**Cause:** Invalid BOT_TOKEN in `.env` file
**Fix:**
1. Go to Discord Developer Portal
2. Regenerate Token (click "Regenerate" if needed)
3. Update `.env` file with new token
4. Restart bot

#### Problem: "Discord login failure"
**Causes:**
- Internet connection issues
- Discord API down (check discordstatus.com)
- Outdated bot token
- Regional blocks (rare)

#### Problem: "Module 'discord' not found"
**Fix:**
```bash
pip install -r requirements.txt
# Or reinstall discord.py specifically:
pip install discord.py==2.3.0 --force-reinstall
```

### Permission Issues:

#### Problem: "Missing Permissions" error
**Checks:**
- Bot has correct permissions in server settings?
- Are you an admin of the server?
- Discord Developer Portal permissions match what we set up earlier?

#### Problem: Commands don't appear in Discord
**Fixes:**
1. Bot online and responsive?
2. Try `/` to trigger command list
3. Bot has "Use Slash Commands" permission?
4. Restart bot (some commands sync on startup)

### Cross-Server Sync Problems:

#### Problem: Punishments don't spread
**Common Causes:**
- Target server not set up as child server (`/setup add-child`)
- Bot not invited to child server
- Child server admin didn't give bot permissions
- ZERO-LEAK protection preventing parent from spreading (this is intentional)

#### Problem: "Child server blocked by security"
**This is NORMAL ZERO-LEAK behavior!**
- Child servers cannot spread punishments (safety feature)
- Only main server can spread to children
- This prevents accidental network-wide punishments

#### Problem: Bot appears offline in child servers
- Bot not invited to that specific server?
- Server region blocking Discord?
- Internet connectivity issues?

### Database Issues:

#### Problem: "Database locked" error
**Immediate fixes:**
```bash
# Stop the bot first
# Make a backup if worried:
cp wayhaven_enforcer.db backup.db

# Recreate empty database:
python setup_database.py

# Restart bot
```
**Prevention:** Don't open database file in other programs while bot is running

#### Problem: Database corruption
**Recovery:**
1. Stop bot immediately
2. Backup current file: `cp wayhaven_enforcer.db backup_corrupt.db`
3. Reset: `rm wayhaven_enforcer.db && python setup_database.py`
4. Restore any missing data if possible

#### Problem: Slow performance over time
**Maintenance:**
```bash
# Vacuum database for better performance:
sqlite3 wayhaven_enforcer.db "VACUUM;"

# Check for corruption:
sqlite3 wayhaven_enforcer.db "PRAGMA integrity_check;"
```

### Advanced Issues:

#### Enable Debug Logging:
```env
# Add to .env file
DEBUG=true
```

Restart bot for detailed logging in console.

#### Rate Limiting Issues:
- Discord limits to ~50 requests/second
- Wayhaven automatically handles this
- If still hitting limits, reduce sync frequency or contact support

#### Memory Leaks:
- Bot uses ~50-100MB normally
- Restart weekly if it climbs to 200MB+
- Monitor with Task Manager/Activity Monitor

---

## Enterprise Compliance & Legal Framework 🏢

### GDPR Compliance Implementation

**For organizations in Europe or handling European data:**

#### Data Controller Responsibilities
Wayhaven acts as a data processor on behalf of Discord server administrators (the data controllers).

#### Lawful Processing Basis
- **Legitimate Interest:** Operating moderation systems for community safety
- **Legal Obligation:** Compliance with Discord's Terms of Service
- **Consent:** Users consent by joining moderated servers

#### Data Categories Processed
```
Stored Data:
├── Personal Identifiers: Discord User IDs (pseudonymized)
├── Event Data: Moderation actions, timestamps, reasons
├── Communication: Warning messages (when sent)
└── Metadata: Command usage patterns, server interaction logs
```

#### User Rights Implementation

**Right to Information (Articles 13-14):**
- Provide privacy notice explaining data processing
- Transparently document data retention policies
- Explain user rights for data subjects

**Right to Access (Article 15):**
```bash
# Built-in data access command:
/audit log user:@username days:365
```

**Right to Rectification (Article 16):**
- Server administrators can correct inaccurate data
- Users can request corrections through appeal processes

**Right to Erasure ("Right to be Forgotten") (Article 17):**
```python
# Automated deletion procedure:
async def delete_user_data(user_id: str):
    # Remove from all punishment tables
    await db.execute("DELETE FROM punishments WHERE target_user = ?", (user_id,))

    # Remove audit history (after legal retention period)
    await db.execute("DELETE FROM command_audit WHERE user_id = ?", (user_id,))

    # Log deletion for compliance
    await db.log_compliance_event("user_data_erased", {"user_id": user_id})

    # Confirm deletion
    return {"status": "erased", "user_id": user_id}
```

**Right to Data Portability (Article 20):**
```bash
# Export user data in standard format:
/audit export days:365 user-filter:@username format:json
```

**Right to Restriction (Article 18):**
- Data processing can be restricted during complaint investigations
- Automatic restraints during legal holds

**Right to Object/Automated Decision Making (Articles 21-22):**
- Users can opt out of automated decision-making processes
- Clear appeals processes for algorithmic decisions

#### Data Retention Schedule

| Data Type | Primary Retention | Extended Retention | Disposal Method |
|-----------|-------------------|-------------------|-----------------|
| Active Punishments | Until expired + 90 days | N/A | Automatic |
| Audit Logs | 3 years | Up to 7 years if legal requirement | Secure deletion |
| Command Logs | 6 months | 24 months for security investigations | Encrypted destruction |
| System Logs | 3 months | 12 months for debugging | Compression then deletion |

#### Data Protection Impact Assessment (DPIA)

**Required for high-risk processing:**
- Controllers must conduct DPIA before deployment
- Technologies assessment completed
- Risk mitigation strategies documented
- Data
