# Hacker101-CTF Ticketastic Blind SQLi Scanner

This tool is a multi-threaded Blind SQL Injection exploit for the Hacker101 CTF 'Ticketastic' challenge.

## Features
- **Multi-threading**: Accelerates data extraction via concurrent execution. The default is set to 8 threads, but you can adjust this value to optimize performance for your specific environment.
- **HEX-Encoded Extraction**: Retrieves data in **HEX format** to bypass character filtering and prevent data corruption during transit. The tool **decodes HEX in real-time** and streams the result directly to your terminal.
- **Dual Environment Support**: Compatible with both **Demo** and **Live** instances. You can switch environments simply by configuring the session cookie name (`session_level7a` for Demo, `session_level7b` for Live).
- **Interactive UI**: Provides a user-friendly interface to select specific targets for data extraction.
- **Automatic Discovery**: Automatically enumerates database names, tables, and columns.

## Configuration
When starting the tool, you will be prompted to enter your session information:
- **Demo Instance**: Set cookie name to `session_level7a`
- **Live Instance**: Set cookie name to `session_level7b`

## How it Works (Real-time Decoding)
The scanner fetches character values using a binary search algorithm wrapped in a `HEX()` function. This ensures that special characters (like those found in XSS payloads) are retrieved accurately without breaking the SQL query or terminal output.
1. The SQL query wraps the target data with `HEX()`.
2. The scanner retrieves HEX pairs concurrently using binary search.
3. Each HEX pair is instantly converted back to UTF-8 and displayed on the screen for real-time monitoring.

## Disclaimer
For educational and wargame purposes only.