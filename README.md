# ServerFinder

A Minecraft server scanner that's indexed over 200,000 servers in the last 2 months.

## What it does

ServerFinder scans the internet for Minecraft servers by targeting IP blocks owned by popular hosting providers. It uses a custom-patched version of MCProtocolLib with ViaVersion injected directly into the Netty pipeline, allowing it to connect to servers running different Minecraft versions without rewriting protocol handlers for each version.

## Technical details

- Built on [MCProtocolLib](https://github.com/GeyserMC/MCProtocolLib) with [ViaVersion](https://github.com/ViaVersion/ViaVersion) integration
- Connects to servers across all versions (1.8.x through 1.21.x) (Currently Native 1.21.4 (769) )
- Supports full online mode authentication (premium accounts)
- Netty pipeline modifications specifically for ViaVersion support 
- Multi threaded scanning (zoom perofmrnac)

## Server discovery

The scanner finds servers by:
- Pulling IP blocks from ASN databases (OVH, Hetzner, AWS, etc.)
- Port scanning common Minecraft ports
- Picking ranges at random so its less likely to come across duplicates (we already check every ip it scans against db)
- Filtering results based on connection patterns

Currently indexed 200,000+ unique servers since February 2025.

## Data collection capabilities

- Server version and mods detection (from ping)
- Player count and MOTD parsing (from ping and in game)
- Entity position tracking
- Player placed block detection (e.g diamond blocks, wood planks etc etc)
- Web map discovery (Dynmap, BlueMap, etc.)

## Requirements (If I ever release it)

- Java 11+
- Premium Minecraft account(s)
- Fast network connection

## Notes

This tool is a personal project for Minecraft server research and analysis, not for malicous purposes.

