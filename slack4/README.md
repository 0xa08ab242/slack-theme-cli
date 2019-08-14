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

So, since this looks like it going to happen daily, I made a simple script to use a backup copy of local-settings.json and overwrite the one that keeps changing.  Such a item feels too trivial to add to the repo at this time; the main reason for making the script was laziness as I attempt to trigger the processes that revert the file.

I tested my suspicion that local-settings.json is reverting as part of the 'update check and notification' processes.  Going to the Updates tab of the App Store, where an available update exists for Slack causes the file to revert.  Between the hassle of the last slack update and the uselessly vague changelog for the available update, I have no appetite for more from them right now, so I will defer testing what happens when there is no availale Slack update to a later date - assuming that the next update does not cause more breakage.

## Credits

Special thanks to:

- [Slack Dark Mode for macOS Mojave](https://github.com/LanikSJ/slack-dark-mode)
- [Reddit User Cruftbrew](https://www.reddit.com/user/cruftbrew/)
