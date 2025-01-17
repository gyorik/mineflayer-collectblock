<h1 align="center">mineflayer-collectblock</h1>
<p align="center"><i>A small utility plugin for allowing users to collect blocks using a higher level API.</i></p>

<p align="center">
  <img src="https://github.com/TheDudeFromCI/mineflayer-collectblock/workflows/Build/badge.svg" />
  <a href="https://www.npmjs.com/package/mineflayer-collectblock"><img src="https://img.shields.io/npm/v/mineflayer-collectblock" /></a>
  <img src="https://img.shields.io/github/repo-size/TheDudeFromCI/mineflayer-collectblock" />
  <img src="https://img.shields.io/npm/dm/mineflayer-collectblock" />
  <img src="https://img.shields.io/github/contributors/TheDudeFromCI/mineflayer-collectblock" />
  <img src="https://img.shields.io/github/license/TheDudeFromCI/mineflayer-collectblock" />
</p>

---

## Showcase

You can see a video of the plugin in action, [here.](https://youtu.be/5T_rcCnNnf4)
The source code of the bot in the video can be seen in the examples folder, [here.](https://github.com/TheDudeFromCI/mineflayer-collectblock/blob/master/examples/collector.js)

### Getting Started

This plugin is built using Node and can be installed using:
```bash
npm install --save mineflayer-collectblock
```

### Simple Bot

The brief description goes here.

```js
// Create your bot
const mineflayer = require("mineflayer")
const bot = mineflayer.createBot({
  host: 'localhost',
  username: 'Player',
})
let mcData

// Load collect block
bot.loadPlugin(require('mineflayer-collectblock').plugin)

async function collectGrass() {
  // Find a nearby grass block
  const grass = bot.findBlock({
    matching: mcData.blocksByName.grass_block.id,
    maxDistance: 64
  })

  if (grass) {
    // If we found one, collect it.
    try {
      await bot.collectBlock.collect(grass)
      collectGrass() // Collect another grass block
    } catch (err) {
      console.log(err) // Handle errors, if any
    }
  }
}

// On spawn, start collecting all nearby grass
bot.once('spawn', () => {
  mcData = require('minecraft-data')(bot.version)
  collectGrass()
})
```

### Documentation

[API](https://github.com/TheDudeFromCI/mineflayer-collectblock/blob/master/docs/api.md)

[Examples](https://github.com/TheDudeFromCI/mineflayer-collectblock/tree/master/examples)

### License

This project uses the [MIT](https://github.com/TheDudeFromCI/mineflayer-collectblock/blob/master/LICENSE) license.

### Contributions

This project is accepting PRs and Issues. See something you think can be improved? Go for it! Any and all help is highly appreciated!

For larger changes, it is recommended to discuss these changes in the issues tab before writing any code. It's also preferred to make many smaller PRs than one large one, where applicable.
