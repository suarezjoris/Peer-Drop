# Peer-Drop

Local network file sharing via WebRTC. No app installation, no accounts, no cloud — just open a browser.

## How it works

1. Run `peer-drop` on any computer on your network
2. Open `http://localhost:8080` in a browser (desktop or mobile)
3. Other devices on the same network appear automatically
4. Click a device to send files directly, peer-to-peer

The server acts only as a WebSocket signaling relay — file data travels directly between browsers via WebRTC and never touches the server.

## Install

**From source:**

```bash
git clone https://github.com/suarezjoris/Peer-Drop
cd Peer-Drop
go build -o peer-drop .
./peer-drop
```

## Usage

```
peer-drop [flags]

Flags:
  -port int     Server port (default 8080)
  -verbose      Enable verbose logging
  -version      Print version
  -help         Show help
```

## Public rooms

To share files with someone outside your local network, create a **public room** from the UI. You get a 5-character code (e.g. `XK9TQ`) that the other person enters to join the same room.

## Configuration

Config is stored at:

- Linux/macOS: `~/.config/peerdrop/config.json`
- Windows: `%APPDATA%\peerdrop\config.json`

```json
{
  "device_name": "My Laptop",
  "port": 8080,
  "download_dir": "~/Downloads/PeerDrop"
}
```

## Tech stack

- **Backend:** Go, gorilla/websocket
- **Frontend:** Vanilla JS, WebRTC
- **Peer discovery:** IP subnet grouping (/24 IPv4, /64 IPv6)

## License

MIT
