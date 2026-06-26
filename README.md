# pwc — Packet Lister

A browser-based tool for fetching, parsing, and validating binary packets from a local server.

## What it does

- Fetches raw binary data from `http://localhost:3000/packets`
- Parses the data into 6-byte packets: `[0xAA start] [4-byte payload] [1-byte checksum]`
- Validates each packet's checksum and flags if the payload matches the password `"PASS"`
- Logs results to the browser console (F12)
- POSTs valid payloads back to `http://localhost:3000/save-payload`

## Usage

1. Start your packet server on `http://localhost:3000`
2. Open `index.html` in a browser
3. Click **Fetch Packets** and open the console (F12) to see results

## Packet Format

| Byte | Description |
|------|-------------|
| 0    | Start byte (`0xAA`) |
| 1–4  | Payload |
| 5    | Checksum (sum of payload bytes % 256) |
