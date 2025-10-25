# Wayhaven Enforcer Bot

## Overview

Wayhaven Enforcer is a comprehensive Discord moderation bot designed to provide cross-server punishment synchronization with integrated ZERO-LEAK security measures.

## Features

### Core Functionality
- **Cross-Server Moderation**: Synchronize punishments across multiple Discord servers automatically
- **ZERO-LEAK Security**: Advanced security model preventing unauthorized cross-server actions
- **Comprehensive Audit Logging**: Complete transparency and compliance tracking
- **Professional Moderation Tools**: Ban, mute, kick, timeout, and warning commands
- **GDPR Compliance**: Built-in data protection and privacy management

### Architecture
The bot operates on a hierarchical security model:
- **Main Server (Authority Hub)**: Designated server capable of broadcasting punishments network-wide
- **Child Servers (Execution Nodes)**: Connected servers that receive and apply punishments
- **Immutable Relationships**: Once-way data flow prevents bidirectional command execution

---

## Prerequisites

### System Requirements
- **Python**: Version 3.8.0 or higher
- **Operating System**: Windows 10/11, macOS 11+, or Linux distributions (Ubuntu 18.04+)
- **Memory**: Minimum 2GB RAM recommended
- **Storage**: 1GB free space for application and database
- **Network**: Stable internet connection for Discord API communication

### Discord Requirements
- **Administrator Permissions**: Full control over target Discord servers
- **Bot Account Creation**: Dedicated Discord application for bot hosting
- **Server Management**: Ability to create roles, channels, and manage permissions

---

## Installation and Setup

### Step 1: Obtain Source Code

Download the Wayhaven Enforcer source code from the repository and extract it to your desired installation directory:

```bash
# Navigate to installation directory
cd /path/to/installation/directory/Wayhaven\ Punishment\ sync\ bot/
```

### Step 2: Install Python Dependencies

Install required Python libraries using pip:

```bash
# Install all required dependencies
pip install -r requirements.txt
```

**Core Dependencies:**
- `discord.py`: Discord API integration and bot functionality
- `aiosqlite`: Asynchronous SQLite database operations
- `python-dotenv`: Environment variable management
- `sqlalchemy`: Database ORM and query operations

### Step 3: Initialize Database

Execute the database setup script to create required tables and security constraints:

```bash
# Initialize database schema and security settings
python setup_database.py
```

**Expected Output:**
```
Wayhaven Enforcer Database Setup
Creating database tables...
✅ Created punishments table
✅ Created guild_relationships table (ZERO-LEAK enabled)
✅ Created command_audit table (100% compliance)
✅ Created security_alerts table
✅ Database initialization complete!
⚠️ IMMUTABLE SECURITY: Database locked for ZERO-LEAK protection
🔒 Ready for bot startup
```

---

## Discord Bot Configuration

### Step 1: Create Discord Application

1. Visit the [Discord Developer Portal](https://discord.com/developers/applications)
2. Click **"New Application"**
3. Enter **"Wayhaven Enforcer"** as the application name
4. Accept the terms of service

### Step 2: Create Bot User

1. Navigate to the **"Bot"** section in the left sidebar
2. Click **"Add Bot"**
3. Agree to create the bot
4. Optionally set an avatar and username for the bot

### Step 3: Obtain Bot Credentials

1. In the **"Bot"** section, locate **"Token"**
2. Click **"Copy"** to obtain the bot token
3. **Important**: Store this token securely - never share it publicly
4. In **"General Information"**, note the **"Application ID"**

### Step 4: Configure Bot Permissions

In the **"Bot Permissions"** section, enable the following permissions:
- Read Messages/View Channels
- Send Messages
- Use Slash Commands
- Ban Members
- Kick Members
- Manage Roles
- Moderate Members (timeout functionality)
- View Audit Log
- Read Message History

**Generated Permission Integer**: `268561488`

### Step 5: Generate Bot Invite Link

1. Navigate to **"OAuth2" -> "URL Generator"**
2. Select scopes: **"bot"** and **"applications.commands"**
3. Select the previously configured bot permissions
4. Copy the generated URL and use it to invite the bot to your servers

---

## Configuration File Setup

Create a `.env` file in the bot's root directory with the following content:

```env
# Discord Bot Authentication
BOT_TOKEN=your_secret_bot_token_here
APPLICATION_ID=123456789012345678
CLIENT_ID=123456789012345678

# Server Configuration
MAIN_GUILD_ID=987654321098765432
TEST_GUILD_ID=876543210987654321

# Debugging and Logging
DEBUG=false
DATABASE_URL=sqlite+aiosqlite:///wayhaven_enforcer.db

# Advanced Security Settings
ZERO_LEAK_SECURITY_ENABLED=true
AUDIT_LOG_RETENTION_DAYS=365
AUTO_BACKUP_ENABLED=true
```

### Configuration Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `BOT_TOKEN` | Yes | Discord bot authentication token |
| `APPLICATION_ID` | Yes | Discord application identifier |
| `MAIN_GUILD_ID` | Yes | Server ID designated for main authority |
| `TEST_GUILD_ID` | No | Server ID for testing features |
| `DEBUG` | No | Enable detailed logging (default: false) |
| `DATABASE_URL` | No | Custom database connection URL |
| `ZERO_LEAK_SECURITY_ENABLED` | No | Enable advanced security (default: true) |

---

## Server Configuration

### Step 1: Role Configuration

Create a designated "Muted" role with the following properties:

**Role Settings:**
- **Name**: Muted
- **Color**: Orange (#FF6B35) or Red (#DC143C)
- **Display Separately**: Enabled
- **Permissions**:
  - ✗ Send Messages
  - ✗ Send Messages in Threads
  - ✗ Create Public Threads
  - ✗ Create Private Threads
  - ✗ Speak in Voice Channels
  - ✓ View Channels
  - ✓ Read Message History

### Step 2: Channel Configuration

Create the following channels for operational functionality:

**#moderation-logs**
- **Purpose**: Display punishment actions and audit information
- **Permissions**: Staff/Moderators only (deny @everyone)
- **Recommended Settings**: Slow mode disabled, webhooks enabled

**#security-alerts**
- **Purpose**: System security notifications and alerts
- **Permissions**: Administrators only
- **Recommended Settings**: Read-only for non-admins, notifications enabled

### Step 3: Bot Configuration Commands

Execute the following commands to configure bot settings:

```
/config muterole role:@Muted
/config notifications channel:#moderation-logs enabled:true
/config logchannel channel:#security-alerts
/config audit enabled:true
```

---

## Network Architecture Setup

### Establishing Main Server Authority

Designate the primary server as the authority hub:

```
/setup main-guild
```

**Functionality Granted:**
- Cross-server punishment broadcasting capabilities
- Network relationship management
- Central audit logging authority
- Child server connection management

### Connecting Child Servers

Connect additional servers to receive punishment synchronization:

```
/setup add-child guild-id:123456789012345678
```

**Parameters:**
- `guild-id`: Discord server ID to connect (18-digit number)

**Resulting Functionality:**
- Automatic punishment reception
- Local moderation capabilities preserved
- Centralized rule compliance

### Network Management

Monitor and manage the interconnected server network:

```
/setup dashboard
```

Displays current network status including:
- Connected server count
- Active relationship status
- Synchronization health
- Security compliance status

---

---

## Command Reference

### Moderation Commands

Wayhaven Enforcer provides comprehensive moderation functionality through intuitive slash commands:

| Command | Description | Parameters | Required Permissions |
|---------|-------------|-------------|----------------------|
| `/ban @user` | Issues a network-wide permanent ban | `user:` Target user<br>`reason:` Justification text | Administrator |
| `/unban user_id` | Removes network-wide ban restrictions | `user_id:` Discord user ID<br>`reason:` Removal justification | Administrator |
| `/kick @user` | Removes user from current server only | `user:` Target user<br>`reason:` Kick justification | Moderator |
| `/mute @user` | Applies timed mute across connected servers | `user:` Target user<br>`duration:` Time period (e.g., "30m", "2h")<br>`reason:` Mute justification | Moderator |
| `/timeout @user` | Applies temporary timeout to current server | `user:` Target user<br>`duration:` Time period<br>`reason:` Timeout reason | Moderator |
| `/warn @user` | Issues formal warning in current server | `user:` Target user<br>`reason:` Warning description | Staff |

### Network Management Commands

These commands control the interconnected server relationships and network topology:

| Command | Description | Parameters | Function |
|---------|-------------|-------------|----------|
| `/setup main-guild` | Designates server as network authority hub | None | Grants broadcast capabilities |
| `/setup add-child guild-id:X` | Connects child server to network | `guild-id:` 18-digit server ID | Enables punishment reception |
| `/setup remove-child guild-id:X` | Disconnects child server from network | `guild-id:` 18-digit server ID | Stops punishment synchronization |
| `/setup test-connection guild-id:X` | Verifies server connection health | `guild-id:` 18-digit server ID | Tests network connectivity |
| `/setup dashboard` | Displays comprehensive network overview | None | Shows status and relationships |

### Configuration Commands

System configuration and maintenance commands:

| Command | Description | Usage | Effect |
|---------|-------------|--------|--------|
| `/config muterole role:@Role` | Defines mute role for punishment enforcement | Specify role mention | Sets standardized mute application |
| `/config notifications channel:#X enable:Y` | Configures punishment logging channel | Channel mention, boolean toggle | Enables/disables audit logging |
| `/config logchannel channel:#X` | Sets security alert destination | Channel mention | Routes system security events |
| `/config audit enabled:X` | Controls audit trail functionality | Boolean value | Activates compliance logging |

### Audit and Monitoring Commands

Comprehensive compliance and monitoring functions:

| Command | Description | Parameters | Purpose |
|---------|-------------|-------------|----------|
| `/audit log user:@user days:X` | Retrieves complete user punishment history | User mention, day count | GDPR compliance and investigation |
| `/audit stats days:X` | Generates moderation statistics report | Day count for analysis window | Performance analysis and trends |
| `/audit warnings user:@user` | Displays user warning history | Target user mention | Warning record management |

---

## Security Implementation Details

### ZERO-LEAK Security Model

The ZERO-LEAK security framework employs several architectural safeguards:

#### Authorization Layers
1. **Guild Authority Verification**: Every cross-server operation validates the source server's authority level
2. **Relationship Authentication**: Commands verify established trust relationships between servers
3. **Action Scope Enforcement**: Only permitted actions execute based on configured server roles
4. **Audit Trail Integration**: All security decisions are logged with full context

#### Immutable Security Constraints
- **One-Way Propagation**: Punishments flow only from main servers to authorized child servers
- **Relationship Immutability**: Trust relationships cannot be modified during active operations
- **Role-Based Access Control**: Commands require specific permission levels for execution
- **Transaction Atomicity**: Security operations either complete entirely or fail completely

#### Threat Mitigation
- **Injection Prevention**: All inputs sanitized to prevent SQL injection attacks
- **Rate Limiting**: API calls throttled to prevent abuse and system overload
- **Data Encryption**: Sensitive configuration data encrypted at rest using industry standards
- **Anomaly Detection**: Unusual patterns flagged for administrative review

### Authority Hierarchy Implementation

#### Main Server (Authority Hub) Capabilities
- **Broadcast Authority**: Can initiate network-wide punishment operations
- **Network Governance**: Manages child server connections and trust relationships
- **Audit Oversight**: Maintains centralized logging of all network activities
- **Security Coordination**: Implements and enforces network security policies

#### Child Server (Execution Node) Capabilities
- **Local Autonomy**: Retains full control over internal server moderation
- **Punishment Reception**: Automatically applies punishments from authorized main servers
- **Notification Forwarding**: Receives and displays punishment notifications
- **Compliance Integration**: Aligns with network-wide moderation policies

---

## Operational Procedures

### First-Time Bot Startup

Execute the bot initialization sequence:

```bash
# Launch the Discord bot application
python bot.py
```

**Successful Initialization Indicators:**
- Database connection establishes successfully
- Bot authentication with Discord API completes
- Command synchronization with Discord servers finishes
- Background services (reconciliation, sync processor) start
- Network connection to all configured servers verified

**Initialization Sequence:**
1. Environment configuration loading and validation
2. Database connectivity test and security constraint verification
3. Discord API authentication and client initialization
4. Command registry synchronization with Discord services
5. Event listener system activation and background task startup

### Network Synchronization Process

#### Punishment Propagation Workflow

1. **Event Detection**: Bot identifies punishment command execution in main server
2. **Authority Validation**: Verifies source server possesses broadcast permission
3. **Relationship Verification**: Confirms target servers have established trust relationships
4. **Permission Assessment**: Validates specific action against configured allowances
5. **Execution Queue**: Adds approved punishment to synchronized processing queue
6. **Parallel Distribution**: Simultaneously applies punishment across authorized servers
7. **Notification Generation**: Sends audit notifications to designated channels
8. **Result Aggregation**: Compiles execution results and reports status

#### Synchronization States

- **Authorized**: Punishment propagates successfully to all permitted servers
- **Partial Success**: Punishment applies to some servers, fails on others (detailed in audit logs)
- **Blocked**: Security validation fails, operation cancelled with full audit trail
- **Queued**: Operation postponed due to rate limiting or system load

---

## Problem Resolution Guide

### Startup Failure Analysis

#### Common Initialization Errors

**Configuration File Issues:**
- **Missing `.env` file**: Create file with required authentication parameters
- **Invalid token format**: Regenerate bot token from Discord Developer Portal
- **Permission insufficient**: Verify bot has required Discord permissions
- **Server ID incorrect**: Confirm server IDs are 18-digit numeric values

**Dependency Problems:**
- **Missing Python modules**: Execute `pip install -r requirements.txt`
- **Version incompatibility**: Ensure Python 3.8+ and compatible library versions
- **Import path errors**: Verify file locations and PYTHONPATH settings

**Database Connectivity:**
- **File permissions**: Ensure write access to database directory
- **Corrupted schema**: Reinitialize with `python setup_database.py`
- **Version mismatch**: Clear database and perform fresh initialization

#### Diagnostic Commands

```bash
# Validate Python environment
python --version
python -c "import sys; print('Python path:', sys.executable)"

# Test core dependencies
python -c "import discord, aiosqlite, dotenv; print('Libraries loaded successfully')"

# Check Discord connectivity
python -c "
import discord
intents = discord.Intents.default()
client = discord.Client(intents=intents)
@client.event
async def on_ready():
    print(f'Connected as {client.user}')
    await client.close()
client.run('YOUR_BOT_TOKEN', log_level=None)
"

# Validate database integrity
python -c "
import aiosqlite
import asyncio
async def check_db():
    async with aiosqlite.connect('wayhaven_enforcer.db') as db:
        cursor = await db.cursor()
        await cursor.execute('PRAGMA integrity_check')
        result = await cursor.fetchone()
        print(f'Database integrity: {result[0]}')
asyncio.run(check_db())
"
```

### Network Synchronization Issues

#### Punishment Propagation Problems

**Connection Validation:**
- Verify bot presence in target server member lists
- Confirm bot roles include required permissions for punishment execution
- Check server region settings for potential connectivity limitations

**Configuration Verification:**
- Ensure mute role exists and is properly configured in target servers
- Validate notification channels are accessible and configured
- Confirm audit settings are enabled and functioning

**Security Constraint Analysis:**
- Review ZERO-LEAK settings for appropriate trust levels
- Verify server relationship configurations are current and authorized
- Check for any active security alerts impacting operations

#### Synchronization Monitoring

Identify potential issues through systematic verification:

```bash
# Check recent synchronization activities
python -c "
import aiosqlite
import asyncio
async def monitor_sync():
    async with aiosqlite.connect('wayhaven_enforcer.db') as db:
        cursor = await db.cursor()
        await cursor.execute('''
            SELECT COUNT(*) as total_punishments,
                   COUNT(CASE WHEN status = 'success' THEN 1 END) as successful,
                   COUNT(CASE WHEN status = 'failed' THEN 1 END) as failed
            FROM command_audit
            WHERE created_at > datetime('now', '-1 hour')
        ''')
        results = await cursor.fetchone()
        print(f'Sync Statistics (last hour): Total: {results[0]}, Successful: {results[1]}, Failed: {results[2]}')
asyncio.run(monitor_sync())
"
```

### Performance Optimization

#### System Resource Management

**Memory Usage Monitoring:**
- Track heap allocation during peak usage periods
- Monitor background task memory consumption
- Implement garbage collection optimizations

**Database Performance:**
- Regular vacuum operations to reclaim storage space
- Query optimization for frequently accessed data
- Index maintenance to ensure efficient lookups

**Network Efficiency:**
- Connection pooling for Discord API interactions
- Rate limit adherence to prevent throttling
- Compression for webhook notification payloads

---

## Compliance and Regulatory Framework

### GDPR Implementation Details

#### Data Protection Principles
- **Lawfulness and Fairness**: All data processing occurs with explicit user consent mechanisms
- **Purpose Limitation**: Data collected solely for moderation and security purposes
- **Data Minimization**: Only essential information retained for operational requirements
- **Accuracy**: Automatic validation and update mechanisms maintain data correctness
- **Storage Limitation**: Configurable retention policies with automatic data purging
- **Integrity and Confidentiality**: Encryption at rest and secure transmission protocols
- **Accountability**: Comprehensive audit trails document all data processing activities

#### User Rights Implementation

**Right to Access:**
- Users can request their personal data via audit commands
- Administrators can access user-specific punishment histories
- Data export functionality supports privacy requests

**Right to Rectification:**
- Correction mechanisms available through administrative interfaces
- Automated validation prevents incorrect data storage
- Change tracking maintains record of modifications

**Right to Erasure:**
- Automated data retention policies govern information lifecycle
- Secure deletion procedures ensure complete data removal
- Anonymization techniques preserve statistical integrity

**Right to Data Portability:**
- Structured data formats enable seamless information transfer
- Export functions facilitate compliance with portability requirements
- Standardized interfaces support integration with external systems

### Educational Environment Compliance

#### Student Privacy Protection
- **Identifier Pseudonymization**: Discord user IDs masked in logs and interfaces
- **Age-Appropriate Controls**: Moderation actions respect educational age restrictions
- **Parental Communication Channels**: Integrated notification systems for guardians
- **Incident Documentation Standards**: Structured reporting for educational records

#### FERPA Compliance Considerations
- **Institutional Control**: Schools maintain authority over educational data
- **Student Record Protection**: Specific safeguards for academic performance data
- **Directory Information Management**: Controlled disclosure of student information
- **Incident Response Coordination**: Procedures for educational data breaches

---

## Maintenance and Administration

### Regular Maintenance Tasks

#### Database Maintenance Procedures

**Daily Operations:**
- Execute transaction log maintenance
- Verify database integrity checks
- Monitor disk space utilization
- Review performance metrics

**Weekly Operations:**
- Execute comprehensive database vacuum procedures
- Archive audit logs based on retention policies
- Update security configurations as needed
- Verify backup integrity and accessibility

**Monthly Operations:**
- Complete system health assessment
- Review and update access permissions
- Analyze usage patterns and performance trends
- Coordinate with network administrators

#### Security Assessment Schedule

**Continuous Monitoring:**
- Real-time security alert processing
- Automated threat detection and response
- Log analysis for anomalous activities
- Performance baseline comparisons

**Quarterly Reviews:**
- Comprehensive security configuration audits
- Access permission validations
- Software dependency updates and vulnerability assessments
- Incident response procedure testing

**Annual Assessments:**
- Full security architecture review
- Regulatory compliance verification
- Disaster recovery scenario testing
- Business continuity plan updates

---

## Associated Documentation

### Related Resources
- **API Documentation**: Technical specifications for custom integrations
- **Deployment Guide**: Advanced installation procedures for enterprise environments
- **Migration Procedures**: Instructions for system upgrades and version transitions
- **Integration Examples**: Code samples for external system connections

---

## License and Attribution

### MIT License Summary

This software is licensed under the MIT License. Key provisions include:

- **Permissive Usage**: Software may be used, modified, and distributed freely
- **Commercial Deployment**: No restrictions on commercial application
- **Attribution Requirements**: Original copyright notice must be maintained
- **Warranty Disclaimer**: Software provided "as-is" without express warranties
- **Liability Limitations**: Authors not liable for software-related damages

### Attribution
Developed by the Wayhaven Security Team for professional Discord moderation solutions.
