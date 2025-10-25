# Wayhaven Enforcer Bot

[![Version](https://img.shields.io/badge/version-2.1.0-blue.svg)](https://github.com)
[![Security](https://img.shields.io/badge/security-ZERO--LEAK-critical.svg)](https://github.com)

Professional Discord moderation with cross-server punishment synchronization and ZERO-LEAK security.

---

## 🎓 What It Does

Wayhaven Enforcer creates a unified moderation system across multiple Discord servers:

**School Network Analogy:**
- **Principal's Office** (Main Server): Can issue punishments that automatically apply everywhere
- **Classrooms** (Child Servers): Receive punishment notifications and maintain consistent rules
- **ZERO-LEAK Security**: Prevents classrooms from issuing school-wide punishments

---

## 🚀 Quick Start

### 1. System Requirements
- Python 3.8+
- Discord Bot Account (with proper permissions)
- Administrator access to your Discord servers

### 2. Installation

```bash
# Download and extract the bot files
# Navigate to the bot directory
cd "Wayhaven Punishment sync bot"

# Install dependencies
pip install -r requirements.txt

# Run database setup
python setup_database.py
```

### 3. Discord Bot Setup

1. **Create Discord Application:**
   - Go to https://discord.com/developers/applications
   - Create "New Application" named "Wayhaven Enforcer"
   - Go to "Bot" section and create bot user

2. **Get Bot Token & IDs:**
   - Copy the bot token (keep secret!)
   - Note the Application ID and Client ID

3. **Set Permissions:**
   - Enable: Ban Members, Kick Members, Manage Roles, Moderate Members, View Audit Log, Send Messages, Use Slash Commands

4. **Invite Bot:**
   - Use OAuth2 URL Generator with "bot" and "applications.commands" scopes
   - Invite to ALL servers you want to moderate

### 4. Configuration

Create `.env` file:

```env
# Required Settings
BOT_TOKEN=your_bot_token_here
APPLICATION_ID=your_application_id
MAIN_GUILD_ID=your_main_server_id

# Optional but recommended
TEST_GUILD_ID=your_test_server_id
DEBUG=false
```

### 5. First Run

```bash
python bot.py
```

**Success indicators:**
- ✅ "ZERO-LEAK Database tables created"
- ✅ "Bot is in X guilds"
- ✅ "Wayhaven Enforcer is ready!"

---

## ⚙️ Server Setup

### Step 1: Configure Roles
Create a "Muted" role in your Discord server settings:
- **Color:** Orange/Red
- **Permissions:** Deny "Send Messages", "Speak", Allow "View Channels"
- **Position:** Below staff roles

### Step 2: Configure Bot Channels
Create these channels:
- **#moderation-logs** (Staff only)
- **#security-alerts** (Admin only)

Assign to bot:
```
/config muterole role:@Muted
/config notifications channel:#moderation-logs enabled:true
/config logchannel channel:#security-alerts
```

### Step 3: Setup Server Network

**Make Main Server (Principal's Office):**
```
/setup main-guild
```
This server can now issue punishments that spread to connected servers.

**Connect Child Servers (Classrooms):**
```
/setup add-child guild-id:123456789012345678
```
Replace `guild-id` with actual server ID. These servers will receive punishments but cannot issue network-wide discipline.

**Check Network Status:**
```
/setup dashboard
```

---

## 📋 Commands Guide

### Moderation Commands

| Command | Description | Example | Permissions |
|---------|-------------|---------|-------------|
| `/ban @user` | Network-wide ban | `/ban @troublemaker reason:Spamming` | Administrators |
| `/unban user_id` | Network-wide unban | `/unban 987654321 reason:Appeal approved` | Administrators |
| `/kick @user` | Local kick | `/kick @talker reason:Disruptive` | Moderators |
| `/mute @user` | Network-wide mute | `/mute @shouter duration:30m` | Moderators |
| `/timeout @user` | Local timeout | `/timeout @arguer duration:1h` | Moderators |
| `/warn @user` | Local warning | `/warn @newbie reason:Please read rules` | Staff |

### Network Management

| Command | Purpose |
|---------|---------|
| `/setup main-guild` | Become principal server |
| `/setup add-child guild:123` | Connect classroom server |
| `/setup remove-child guild:123` | Disconnect classroom |
| `/setup test-connection guild:123` | Test server link |
| `/setup dashboard` | View network overview |

### Configuration

| Command | Purpose |
|---------|---------|
| `/config muterole role:@Muted` | Set mute role |
| `/config notifications channel:#logs` | Set punishment log channel |
| `/config logchannel channel:#alerts` | Set security alerts |
| `/config audit enabled:true` | Enable activity logging |

### Audit & Monitoring

| Command | Purpose |
|---------|---------|
| `/audit log user:@student days:30` | View user punishment history |
| `/audit stats days:7` | Weekly moderation statistics |
| `/audit warnings user:@student` | User warning records |

---

## 🔐 Security Architecture

### ZERO-LEAK Protection
- **Main servers ONLY** can trigger cross-server punishments
- **Child servers** receive punishments but cannot issue them
- **Immutable constraints** prevent bidirectional relationships
- **Audit trail** logs every network action

### Authority Levels

#### Principal Server (Main Network Hub)
- ✅ Issue network-wide punishments
- ✅ Connect/disconnect child servers
- ✅ Full administrative control
- ✅ Network management

#### Classroom Servers (Child Nodes)
- ❌ Cannot trigger network punishments
- ✅ Local moderation (warns, kicks)
- ✅ Receive punishment notifications
- ✅ Automatic compliance

---

## 🔧 Troubleshooting

### Bot Won't Start

**Check these first:**
```bash
python --version  # Should be 3.8+
python bot.py     # Look for error messages
```

#### "Module not found"
```
pip install -r requirements.txt --upgrade
```

#### "Improper token"
1. Go to Discord Developer Portal
2. Regenerate token
3. Update `.env` file
4. Restart bot

### Permission Problems

#### "Missing permissions" error
- Bot needs Administrator or proper permissions in Discord
- Check bot role position in server settings
- Re-invite bot with correct permissions

#### Commands not appearing
- Type `/` to refresh command list
- Check bot has "Use Slash Commands" permission
- Restart bot and try again

### Network Sync Problems

#### Punishments not spreading
**Common reasons:**
- Child server not connected (`/setup add-child`)
- Bot not invited to target server
- Missing mute role in target server
- ZERO-LEAK protection (intentional)

#### Sync shows "No mute role configured"
- Set up muted role in target server
- Use `/config muterole` to assign it to the bot

#### Bot offline in some servers
- Invite bot to ALL connected servers
- Check bot permissions in each server
- Verify bot is online in server member list

### Database Issues

#### "Database locked" or corruption
```bash
# Backup current database first
cp wayhaven_enforcer.db backup.db

# Reset database
rm wayhaven_enforcer.db
python setup_database.py
```

**Prevention:** Don't edit database files while bot is running

---

## 🏢 Compliance Features

### GDPR Compliance
- **Data Minimization:** Only stores necessary moderation data
- **Right to Access:** `/audit log user:@user` for compliance records
- **Data Retention:** Automatic cleanup per configured policies
- **Audit Trail:** Complete transparency for all moderation actions

### Educational Environment Ready
- **Student Privacy Protection:** Pseudonymized Discord user IDs
- **Incident Documentation:** Timestamped discipline records
- **Parent Communication:** DM notifications for serious incidents
- **School Policy Integration:** Customizable discipline rules

---

## 📞 Support

For issues and questions:
1. **Check this troubleshooting guide first**
2. **Search for similar issues in documentation**
3. **Join our Discord server for community support**
4. **Create GitHub issue for bug reports**

### Quick Debug
```bash
# Check if bot can start
python -c "import discord; print('Discord library OK')"

# Test database connection
python -c "import aiosqlite; print('Database library OK')"

# Validate .env configuration
python -c "import os; print('TOKEN:', '****' if os.getenv('BOT_TOKEN') else 'MISSING')"
```

---

## ⚠️ Important Notes

### Security First
- ZERO-LEAK protection prevents abuse by untrusted servers
- Only designated Main servers can broadcast punishments
- All actions are logged for accountability

### Performance Considerations
- Bot handles multiple servers efficiently
- SQLite database is fine for most use cases
- Automatic cleanup prevents database bloat

### Backup Recommendations
- Regularly backup `wayhaven_enforcer.db`
- Export important configuration settings
- Keep bot tokens secure and rotated periodically

---

## 📄 License

**MIT License** - See full license for details.

**Built with ❤️ for secure Discord moderation**

*Visit us at [wayhaven.dev](https://wayhaven.dev) for more security tools*
