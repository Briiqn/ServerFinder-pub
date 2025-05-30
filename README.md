# ServerFinder
A Minecraft server scanner that's indexed over 240,000 servers in the last 3 months.

## What it does
ServerFinder scans the internet for Minecraft servers by targeting IP blocks owned by popular hosting providers. It uses a custom-patched version of MCProtocolLib with ViaVersion injected directly into the Netty pipeline, allowing it to connect to servers running different Minecraft versions without rewriting protocol handlers for each version.

## Technical details
- Built on [MCProtocolLib](https://github.com/GeyserMC/MCProtocolLib) with [ViaVersion](https://github.com/ViaVersion/ViaVersion) integration
- Connects to servers across all versions (1.8.x through 1.21.x) (Currently Native 1.21.5 (770) )
- Supports full online mode authentication (premium accounts)
- Netty pipeline modifications specifically for ViaVersion support 
- Multi threaded scanning (zoom performance)

## Server discovery
The scanner finds servers by:
- Pulling IP blocks from ASN databases (OVH, Hetzner, AWS, etc.)
- Port scanning common Minecraft ports (to bypass honeypots we just start the handshake with an absurd client version and see what the server responds with)
- Picking ranges at random so its less likely to come across duplicates (we already check every ip it scans against db)
- Filtering results based on connection patterns

Currently indexed 240,000+ unique servers since February 2025.

## Data collection capabilities
- Server version and mods detection (from ping)
- Player count and MOTD parsing (from ping and in game)
- Entity position tracking
- Player placed block detection (e.g diamond blocks, wood planks etc etc)
- Web map discovery (Dynmap, BlueMap, etc.)
- Misconfigured Bungeecord detection (UUID spoofing)

## Database Statistics
- **Total Servers**: 240,978

### Server Distribution by Country (As of May 30, 2025)
| Country | Servers | Percentage |
|---------|---------|------------|
| United States | 110,159 | 45.7% |
| Germany | 31,551 | 13.1% |
| Japan | 18,060 | 7.5% |
| Canada | 10,809 | 4.5% |
| United Kingdom | 8,424 | 3.5% |
| France | 7,927 | 3.3% |
| China | 7,622 | 3.2% |
| Netherlands | 5,179 | 2.1% |
| Australia | 4,912 | 2.0% |
| Sweden | 2,991 | 1.2% |

### Geographic Coverage
- **Total Countries**: 138
- **Countries with 100+ servers**: 52

### System Status
- Status: **Operational**
- Last update: Friday, 30 May 2025 19:36

## Requirements (If I ever release it)
- Java 11+
- Premium Minecraft account(s)
- Fast network connection

## Notes
This tool is a personal project for Minecraft server research and analysis, not for malicious purposes.
