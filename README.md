# A simple [Battlesnake](http://play.battlesnake.com) written in Mule and DataWeave

This is a basic implementation of the [Battlesnake API](https://docs.battlesnake.com/snake-api). It's a great starting point for anyone wanting to program their first Battlesnake using Mule and DataWeave.

## Quickstart

The [Quick Start Coding Guide](https://docs.battlesnake.com/guides/getting-started) provides the full set of instructions to customize, register, and create your first games with your Battlesnake! 


### Prerequisites

* A free [Battlesnake Account](https://play.battlesnake.com/?utm_source=github&utm_medium=readme&utm_campaign=mule_battlesnake&utm_content=homepage)
* [Anypoint Studio](https://www.mulesoft.com/lp/dl/studio) for local development
* Mule Runtime
* [Anypoint Platform account](https://anypoint.mulesoft.com/) for deploying to Cloudhub


## Running Your Battlesnake in local Anypoint Studio

1. Fork and clone this repo
2. Import this project in Anypoint Studio
3. Run mule-battlesnake mule application. This will expose API at http://localhost:8081/api that you can use for creating battlesnakes.
4. Expose local http to internet with [ngrok](https://ngrok.com/) or similar tools.
5. Follow Battlesnake [quickstart quide](https://docs.battlesnake.com/guides/getting-started#step-4-create-your-battlesnake) to create your battlesnake and play

## Deploying to Cloudhub

Project's POM is configured for deploying to Cloudhub using [Mule Maven Plugin](https://docs.mulesoft.com/mule-runtime/4.4/deploy-to-cloudhub#configure-the-cloudhub-deployment-strategy). See the mule-maven-plugin configuration in pom.xml. Set appropriate values for properties and run `mvn deploy -DmuleDeploy`.

Once deployed to Cloudhub, use application's URL `https://{ch-app-name}.{region}.cloudhub.io/api` to create your battlesnake.
 
## Customizing Your Battlesnake

Accessing http://localhost:8081/api will return response like below. You can change these parameter values from `src/main/resources/application.yaml`. 

```json
{
  "apiversion": "1",
  "author": "mmsonline",
  "color": "#888888",
  "head": "default",
  "tail": "default",
  "version": "0.0.1-beta"
}
```
This resource is called by the game engine periodically to make sure your Battlesnake is healthy, responding correctly, and to determine how your Battlesnake will appear on the game board. See [Battlesnake Personalization](https://docs.battlesnake.com/references/personalization) for how to customize your Battlesnake's appearance using these values.

Whenever you update these values, go to the page for your Battlesnake and select 'Refresh Metadata' from the option menu. This will update your Battlesnake to use your latest configuration and those changes should be reflected in the UI as well as any new games created.

## Changing Behavior

On every turn of each game your Battlesnake receives information about the game board and must decide its next move. Possible moves are "up", "down", "left", or "right" and initially your Battlesnake will choose a move randomly. Your goal as a developer is to read information sent to you about the game (available in the `payload`) and decide where your Battlesnake should move next. All your Battlesnake logic lives in [/src/main/resources/dw/move-snake.dwl](./src/main/resources/dw/move-snake.dwl), and this is the code you will want to edit.

See the [Battlesnake Game Rules](https://docs.battlesnake.com/references/rules) for more information on playing the game, moving around the board, and improving your algorithm.


## Playing Battlesnake

### Completing Challenges

If you're looking for the Single Player Mode of Battlesnake, or something to practice with between events, check out [Challenges.](https://docs.battlesnake.com/guides/quick-start-challenges-guide)

### Joining a Battlesnake Arena

Once you've made your Battlesnake behave and survive on its own, you can enter it into the [Global Battlesnake Arena](https://play.battlesnake.com/arena/global) to see how it performs against other Battlesnakes worldwide.

Arenas will regularly create new games and rank Battlesnakes based on their results. They're a good way to get regular feedback on how well your Battlesnake is performing, and a fun way to track your progress as you develop your algorithm.

### Joining a Battlesnake League

Want to get out there to compete and win prizes? Check out the [Quick Start League Guide](https://docs.battlesnake.com/guides/quick-start-league-guide) for information on the how and when of our competitive seasons.

---

## Resources

All documentation is available at [docs.battlesnake.com](https://docs.battlesnake.com), including detailed Guides, API References, and Tips.

You can also join the Battlesnake Developer Community on [Discord](https://play.battlesnake.com/discord?utm_source=github&utm_medium=readme&utm_campaign=python_starter&utm_content=discord). We have a growing community of Battlesnake developers of all skill levels wanting to help everyone succeed and have fun with Battlesnake :)

Check out live Battlesnake events on [Twitch](https://www.twitch.tv/battlesnakeofficial) and see what is happening when on the [Calendar.](https://play.battlesnake.com/calendar?utm_source=github&utm_medium=readme&utm_campaign=python_starter&utm_content=calendar)

Want to contribute to Battlesnake? We have a number of open-source codebases and would love for you to get involved! Check out our page on [Contributing.](https://docs.battlesnake.com/guides/contributing)


