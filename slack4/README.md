# Workaround for Slack-4.0.0
Install slack-theme as normal
Try using it and get file not found error
copy the files in this folder to wherever slack-them installed...

- kill slack
- run the before script - requires sudo :(
- run the slack4-theme using the new file names and file paths, pick your theme
- run the after script - requires sudo :(
- start slack

those steps worked for me, but I only tried it on macOS Mojave

# And then it stopped working, suddenly...
Then, I saw this thread: https://www.reddit.com/r/Slack/comments/cdv1w7/were_not_getting_that_dark_mode_are_we/eu1mkvv/ where Cruftbrew posted the fix:
Edit '~/Library/Containers/com.tinyspeck.slackmacgap/Data/Library/Application\ Support/Slack/local-settings.json'
changing the value for "bootSonic": from "once" to "bootSonic": "never"
then restart Slack.

This resolved it, but two weeks later, the theming reverted because the setting had 'magically' changed from "never" to "always."  Changing it back fixed it, but I am left wondering what changed this setting?

Then, about a week later, it reverted again, this time the theming reverted because the setting had 'magically' changed from "never" to "once."  As before, changing it back fixed it, and I still don't know what changed the setting.

Then, the next day, it reverted again, this time the theming reverted because the setting had 'magically' changed from "never" to "once."  As before, changing it back fixed it, and I still don't know what changed the setting. 

## Credits

Special thanks to:

- [Slack Dark Mode for macOS Mojave](https://github.com/LanikSJ/slack-dark-mode)
- [Reddit User Cruftbrew](https://www.reddit.com/user/cruftbrew/)
