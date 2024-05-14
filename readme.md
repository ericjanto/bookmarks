# Bookmarks
This was a 15min project to solve my frustration with modern browser's start
pages. I wanted a simple, fast, and keyboard-friendly way to access my
bookmarks.

![Screenshot showing an overview of my bookmarks displayed in Safari](image.png)

The website is a single HTML file. Bookmarks are kept in a jsonl file (can be
kept as csv file as well). Everything can easily be hosted locally. No
external dependencies.

## Local setup
It's best to host this locally, that's the easiest way of keeping your
bookmarks private, and the load time is instant.

Create a `plist` file, e.g. `com.yourname.yourserver.plist`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.yourname.yourserver</string>
    <key>ProgramArguments</key>
    <array>
        <string>/usr/local/bin/python3</string>
        <string>-m</string>
        <string>http.server</string>
        <string>8000</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>KeepAlive</key>
    <true/>
    <key>WorkingDirectory</key>
    <string>/path/to/your/project</string>
    <key>StandardErrorPath</key>
    <string>/tmp/com.yourname.yourserver.err</string>
    <key>StandardOutPath</key>
    <string>/tmp/com.yourname.yourserver.out</string>
</dict>
</plist>
```

Then load the service and verify it's running.

```zsh
launchctl load ~/Library/LaunchAgents/com.yourname.yourserver.plist
launchctl list | grep com.yourname.yourserver
```
