# Create Mime Type Handler

## Why?
I was having issues with Brave browser, sometimes it would crash when I opened a URL from another app/process. I got tired of waiting for a fix so I decided to just intercept all `http`/`https` and `html` MIME types sent through `xdg-open` and send them to `xlip` so I could paste them myself.

### Create `.desktop` spec
- Create a file with the extension `.desktop` in the directory `$HOME/.local/share/applications` - [Desktop Entry Specification](https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.1.html)

```
[Desktop Entry]
Version=1.0
Name=Clipboarder
Exec=sh -c "echo %u | /usr/bin/xclip -selection clipboard"
Terminal=false
Type=Application
MimeType=x-scheme-handler/https;x-scheme-handler/http;text/html;
```
### Edit `$HOME/.config/mimeapps.list`
- Edit `$HOME/.config/mimeapps.list` - [Association between MIME types and applications](https://specifications.freedesktop.org/mime-apps-spec/mime-apps-spec-1.0.1.html).

```
[Default Applications]
x-scheme-handler/tg=telegramdesktop.desktop
x-scheme-handler/postman=Postman.desktop
x-scheme-handler/chrome=clipboarder.desktop
text/html=clipboarder.desktop
x-scheme-handler/http=clipboarder.desktop
x-scheme-handler/https=clipboarder.desktop

[Added Associations]
text/html=clipboarder.desktop;
image/png=gimp.desktop;eog.desktop;
application/x-ms-dos-executable=q4wine.desktop;
application/octet-stream=gedit.desktop;
application/x-shellscript=code.desktop;

[Removed Associations]
text/html=brave_brave.desktop
text/html=firefox.desktop
x-scheme-handler/chrome=brave_brave.desktop
x-scheme-handler/chrome=firefox.desktop
```

- Add your new Desktop Entry Specification to `[Added Associations]`. Creating an entry using the key of the MIME type you wish to handle, and a value equalling that of the name of your `.desktop` file.
-- If you want it to also handle default MIME types, add it to [Default Applications], creating an entry using the key of the MIME type you wish to handle default action for.
-- Move any unwanted assocations to `[Removed Associations]`.

![](images/handle-mime-types.gif?raw=true)
