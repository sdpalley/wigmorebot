###Wigmore:  Because Lawyers Should Have Robots Too.

---

####1.  What is this?

This is a version of GitHub's Campfire bot, hubot, and inspired by [compleatang's](https://github.com/compleatang) Billings (of which this is a loose fork).  (Thanks,  Casey, for introducing me to Billings).  **You're welcome to copy/fork Wigmore, of course, but you're better off  building your own from Github's original hubot code, which is [at https://github.com/github/hubot](https://github.com/github/hubot).**  

####2. Why should lawyers care?

For lawyers out there who are wondering what the point of bot is, here are a couple of useful things that a Wigmore or Billings can do, with the right scripts added:

 **A.  Wigmore can help us 'remember ' things. **  

If I write    `wigmore remember negligence is a tort` this is saved as a `key: value` pair ` negligence: tort `.  When I later ask `wigmore what is negligence?` the bot will remind me that `negligence is a tort`.

This doesn't mean that Wigmore **knows** what a tort **is**.   (It's not artificial intelligence).  And if doesn't distinguish (yet) between correct information ('negligence is a tort') and incorrect information ('negligence is a type of cheese').  

AI or (in this case) not, it's a simple way to create collections of structured data using plain English sytax.  What's done with the data is a different question.

 **B. Wigmore can  help perform research. **  

If you write `wigmore abstract negligence` it will return a definition culled from on-line searches.  Now, the result is of course only as good as the search engine references that Wigmore is provided in the `abstract` script (which could certainly be augmented). But it's a start.

**C.  Wigmore can help keep your calendar for you.**

**D.  Wigmore can check the news for you.**  

I don't have this features added, actually, but it could be by adding  `news.coffee` to `package.json` and then typing `wigmore news me on topic` in your interface.  Not a bad thing to try if you're just getting started.

**E.  Wigmore helps with automation of many repetitive tasks, using plain English.**

In short, Wigmore can automate the performance of many tasks** -- either with existing scripts or ones that are created.  It will interact with you using plain English, on the command line or in a graphical user interface.  And it is pretty  darn cool.  

And there's no reason why lawyers can't have robots too.

**3. Caveat/Advice if You're Just Getting Started**

While you don't have to be a skilled programmer to build your own bot, it does take some technical knowledge in order to meld together many (pre-built) moving parts.  (To my programmer friends, most of the world isn't as familiar with things like git, node, heroku etc -- there is a learning curve for most of us -- thank you for your continued patience with neophytes).  And patience, particularly  if you're just starting. Full instructions are below.  

The developer/programmer community is incredibly generous with help/advice, though it's usually a good idea to try first and show your work -- if you go to Stack Exchange, for example, this is expected.  

For what it is worth, here are a couple of rookie mistakes I made:

- You need 'redis' to run your bot locally and  have it remember stuff (this is known as 'persistence' and is discussed below).  Here's the rookie mistake -- you have start redis for the bot's brain to work .  I know, duh.  (What's redis?  It's a kind of server that the bot uses to save your `key:value` pairs and remember them later.   Here's a link to [redis.io](http://redis.io), for a real explanation.  Think of it as the place where your bot's memory lives.)

- The scripts contain  'dependencies' -- if you look at a script you'll see a reference to `dependencies` at the top of the document.  Some scripts have 'em; some don't.  If you're a lawyer, think of it as a form of "incorporation by reference."  The script won't work if you don't include a reference to required dependencies in the `package.json` file.  It seems obvious but, well, it took me a little time with Professors Google and Stack Exchange to figure out what I was missing.

- If something isn't workig right, look at your `{ }`s and `;`'s  -- half of my problems seem to be 'punctuation' formatting errors.

###Conclusion

Github's original readme follows, below.  The instructions work way too well for me to mess with them.   By the same token, your

--

###Original Readme###

-----

This version is designed to be deployed on [Heroku][heroku]. This README was generated for you by hubot to help get you started. Definitely update and improve to talk about your own instance, how to use and deploy, what functionality he has, etc!

[heroku]: http://www.heroku.com

### Testing Hubot Locally

You can test your hubot by running the following.

    % bin/hubot

You'll see some start up output about where your scripts come from and a
prompt.

    [Sun, 04 Dec 2011 18:41:11 GMT] INFO Loading adapter shell
    [Sun, 04 Dec 2011 18:41:11 GMT] INFO Loading scripts from /home/tomb/Development/hubot/scripts
    [Sun, 04 Dec 2011 18:41:11 GMT] INFO Loading scripts from /home/tomb/Development/hubot/src/scripts
    Hubot>

Then you can interact with hubot by typing `hubot help`.

    Hubot> hubot help

    Hubot> animate me <query> - The same thing as `image me`, except adds a few
    convert me <expression> to <units> - Convert expression to given units.
    help - Displays all of the help commands that Hubot knows about.
    ...


### Scripting

Take a look at the scripts in the `./scripts` folder for examples.
Delete any scripts you think are useless or boring.  Add whatever functionality you
want hubot to have. Read up on what you can do with hubot in the [Scripting Guide](https://github.com/github/hubot/blob/master/docs/scripting.md).

### Redis Persistence

If you are going to use the `redis-brain.coffee` script from `hubot-scripts`
(strongly suggested), you will need to add the Redis to Go addon on Heroku which requires a verified
account or you can create an account at [Redis to Go][redistogo] and manually
set the `REDISTOGO_URL` variable.

    % heroku config:set REDISTOGO_URL="..."

If you don't require any persistence feel free to remove the
`redis-brain.coffee` from `hubot-scripts.json` and you don't need to worry
about redis at all.

[redistogo]: https://redistogo.com/

## Adapters

Adapters are the interface to the service you want your hubot to run on. This
can be something like Campfire or IRC. There are a number of third party
adapters that the community have contributed. Check
[Hubot Adapters][hubot-adapters] for the available ones.

If you would like to run a non-Campfire or shell adapter you will need to add
the adapter package as a dependency to the `package.json` file in the
`dependencies` section.

Once you've added the dependency and run `npm install` to install it you can
then run hubot with the adapter.

    % bin/hubot -a <adapter>

Where `<adapter>` is the name of your adapter without the `hubot-` prefix.

[hubot-adapters]: https://github.com/github/hubot/blob/master/docs/adapters.md

## hubot-scripts

There will inevitably be functionality that everyone will want. Instead
of adding it to hubot itself, you can submit pull requests to
[hubot-scripts][hubot-scripts].

To enable scripts from the hubot-scripts package, add the script name with
extension as a double quoted string to the `hubot-scripts.json` file in this
repo.

[hubot-scripts]: https://github.com/github/hubot-scripts

## external-scripts

Tired of waiting for your script to be merged into `hubot-scripts`? Want to
maintain the repository and package yourself? Then this added functionality
maybe for you!

Hubot is now able to load scripts from third-party `npm` packages! To enable
this functionality you can follow the following steps.

1. Add the packages as dependencies into your `package.json`
2. `npm install` to make sure those packages are installed

To enable third-party scripts that you've added you will need to add the package
name as a double quoted string to the `external-scripts.json` file in this repo.

## Deployment

    % heroku create --stack cedar
    % git push heroku master
    % heroku ps:scale app=1

If your Heroku account has been verified you can run the following to enable
and add the Redis to Go addon to your app.

    % heroku addons:add redistogo:nano

If you run into any problems, checkout Heroku's [docs][heroku-node-docs].

You'll need to edit the `Procfile` to set the name of your hubot.

More detailed documentation can be found on the
[deploying hubot onto Heroku][deploy-heroku] wiki page.

### Deploying to UNIX or Windows

If you would like to deploy to either a UNIX operating system or Windows.
Please check out the [deploying hubot onto UNIX][deploy-unix] and
[deploying hubot onto Windows][deploy-windows] wiki pages.

[heroku-node-docs]: http://devcenter.heroku.com/articles/node-js
[deploy-heroku]: https://github.com/github/hubot/blob/master/docs/deploying/heroku.md
[deploy-unix]: https://github.com/github/hubot/blob/master/docs/deploying/unix.md
[deploy-windows]: https://github.com/github/hubot/blob/master/docs/deploying/unix.md

## Campfire Variables

If you are using the Campfire adapter you will need to set some environment
variables. Refer to the documentation for other adapters and the configuraiton
of those, links to the adapters can be found on [Hubot Adapters][hubot-adapters].

Create a separate Campfire user for your bot and get their token from the web
UI.

    % heroku config:set HUBOT_CAMPFIRE_TOKEN="..."

Get the numeric IDs of the rooms you want the bot to join, comma delimited. If
you want the bot to connect to `https://mysubdomain.campfirenow.com/room/42`
and `https://mysubdomain.campfirenow.com/room/1024` then you'd add it like this:

    % heroku config:set HUBOT_CAMPFIRE_ROOMS="42,1024"

Add the subdomain hubot should connect to. If you web URL looks like
`http://mysubdomain.campfirenow.com` then you'd add it like this:

    % heroku config:set HUBOT_CAMPFIRE_ACCOUNT="mysubdomain"

[hubot-adapters]: https://github.com/github/hubot/blob/master/docs/adapters.md

## Restart the bot

You may want to get comfortable with `heroku logs` and `heroku restart`
if you're having issues.
