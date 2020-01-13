# DiscortBotAvatarChanger
Changes discord bot avatar dynamically based on date and time from a configurable json file.  
  
  
  
This is usable with any javascript discord library, as it makes calls directly to Discord.
  
  

## Usage  
Put the `avatarChanger.min.js` file into the root folder of your bot.  
Create a folder, called `avatars`.  
This is where you will put the `avatars.json` file. (if it doesn't exist it will be created)  

In this file you should set up the `main.image` property to the default image,  
if no dates in the file apply, it will apply this image.

**Example:**
```json
"main": {
  "image": "main.png"
}
```

Now you can start adding dates  

You need 4 values:  
Key - Title this will tell you what picture it set to, make sure it's unique  
`image` - The image file name to set on this date.  
`time` - The date it activates (Format: `dd-mm`).  
`duration` - The duration of how long this avatar will stay active, in days.  
  
**Example:**   
```json
"christmas": {
  "image": "christmas.png",
  "time": "20-12",
  "duration": 7
}
```

This will activate on the 20th of December and will stay active for 7 days.




Now require it in your bot file, and call the constructor.
```js
const avatarChanger = require('./avatarchanger')
avatarChanger("./avatars/", token);
```  
Now, we need to start the timer in javascript:  
```js
avatarChanger.timer.Start()
```  
(I recommend doing this on `bot.ready`)  
  
  
Now This will run every 4 hours, and update the avatar if necessary.
The `token` is your bot token, this is required to update the avatar.


Avoid using this during development of the bot, to avoid rate limiting yourself.
  
  
## Methods  
Some other methods that you can use:  
`.timer.Stop()` - Stops the timer loop that updates the avatar.  
`.timer.setTimeout(int)` - Changes the duration of the loop, in seconds, if you feel the need to change this, *not recommended* (Default: 4 hours)  

There's some others, but I wouldn't recommend using those. If you use it like the example everything will work fine.  
I might improve those functions later or document them.  
