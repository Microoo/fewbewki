# Comfy
Comfy to develop for and easy to get into discord bot using discord.js

## How to start & requirements
Create yourself a discord dev application at https://discord.com/developers/applications. Once created open the application and create a new bot under 'Bot'. Click 'Click to Reveal Token' and copy it to your credentials.json file token field. (token_dev is to be used with another bot which you can switch to by setting devToggle = true in index.js)

### NPM Packages
- discord.js
#### Optional
- forever

## Command template/example
Dropping this .js file in ./commands will fully work
```javascript
// ./commands/example.js
module.exports = {
    help: 'I will be shown when called with !help example',
    help_detailed: [
        'I am optional',
        'supports and will output more lines'
    ],
    alias: [
        'you can also call this whole command by this string',
        'supports multiple aliases',
        'testexample'
        // !testexample
        // ^ will return same results as !example
    ],
    func: (Client, msg, args) => { // Parameters passed in index.js at Comfy.startListen()
        // This will execute when you call the function directly
        // Examples of parameter handling...

        // Show help command result for command if not enough parameters
        if (args.length == 1) {
            args[1] = args[0];
            return Client.commands.help.func(Client, msg, args);
        }

        // Easy checking of arguments
        if (args[2] == 'profile') {
            Client.errorReply(msg, 'You did bad stuff');
        }

        if (args.length >= 2) {
            return msg.channel.send('Hello world');
        }
    }
}
```
