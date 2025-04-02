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
- Port scanning common Minecraft ports (to bypass honeypots we just start the handshake with an absurd client version and see what the server responds with)
- Picking ranges at random so its less likely to come across duplicates (we already check every ip it scans against db)
- Filtering results based on connection patterns

Currently indexed 200,000+ unique servers since February 2025.

## Data collection capabilities
- Server version and mods detection (from ping)
- Player count and MOTD parsing (from ping and in game)
- Entity position tracking
- Player placed block detection (e.g diamond blocks, wood planks etc etc)
- Web map discovery (Dynmap, BlueMap, etc.)
- Misconfigured Bungeecord detection (UUID spoofing)

## Statistics
### Top Server Locations (As of April 2 2025)
| Country | Servers | Percentage |
|---------|---------|------------|
| United States | 64,586 | 34.1% |
| Germany | 29,465 | 15.6% |
| Japan | 19,421 | 10.3% |
| Canada | 8,704 | 4.6% |
| United Kingdom | 7,540 | 4.0% |
| China | 7,206 | 3.8% |
| France | 6,085 | 3.2% |
| Australia | 4,566 | 2.4% |
| Netherlands | 4,443 | 2.3% |
| South Korea | 3,048 | 1.6% |

### Other Shit
- Total Countries: 151
- Countries with 100+ servers: 55

## Requirements (If I ever release it)
- Java 11+
- Premium Minecraft account(s)
- Fast network connection

## Notes
This tool is a personal project for Minecraft server research and analysis, not for malicous purposes.
