# Overview

AterBot is a Minecraft bot application designed to keep Aternos servers alive 24/7 by maintaining an active player connection. The bot automatically performs random movements (forward, back, left, right, jump) to simulate player activity and prevent server shutdown due to inactivity.

## Current Configuration

- **Server Host:** szostacsmp.falixsrv.me
- **Server Port:** 25565
- **Bot Username:** online_bot

## Recent Changes (November 15, 2025)

1. Fixed PORT environment variable bug in `src/web.ts` (changed from `process.PORT` to `process.env.PORT`)
2. Updated JSON import syntax from `assert` to `with` in `src/bot.ts` for Node.js 22 compatibility
3. Configured server connection details in `config.json`
4. Fixed bot username to comply with Minecraft naming rules (changed from "online bot" to "online_bot")
5. Web server now runs on port 5000 for Replit webview compatibility

## System Architecture

**Technology Stack:**
- Runtime: Node.js 20 with TypeScript
- Build Tool: tsx (TypeScript execution without compilation)
- Module System: ES Modules
- Minecraft Client Library: Mineflayer v4.33.0

**Components:**
1. Minecraft bot client (`src/bot.ts`) - Connects to server and performs periodic movements
2. HTTP health check server (`src/web.ts`) - Responds to UptimeRobot pings on port 5000
3. Main orchestrator (`src/index.ts`) - Initializes both subsystems

**Bot Features:**
- Automatic reconnection on disconnect (15 second retry delay)
- Random movement simulation every 5 seconds
- 50% chance of sprinting during movements
- Automatic view direction changes

## Setup Instructions

1. Make sure your Minecraft server has `online-mode` set to `false`
2. The bot needs OP permissions and Creative mode to prevent death
3. Build a bedrock room (recommended: 5x3x5) to contain the bot
4. Configure UptimeRobot to ping your Replit URL to keep the bot alive 24/7

## External Dependencies

- **Mineflayer:** Minecraft protocol implementation
- **tsx:** TypeScript runtime execution
- **Replit:** Hosting platform
- **UptimeRobot:** Monitoring service to prevent auto-shutdown
