JavaScript for Automation Notes (WWDC 2014 Video)
===

An Overview of the Script Editor UI is given which is good, because it's unclear what many UI components do. This is something that needs some usability love. Presenter acknowledges that most experienced devs will start here first, then move to their own editor. That's my plan, so he's got that right.

What does the record button do? Why would you explain all the other buttons in the same grouping but leave one out? The completionist in me is furious. If this plot point doesn't get resolved I want my money back.

Anyhow, there's a top pane for some code and then an eventlog which is as close as we're going to get to a debugging tool it seems like. You click the Run button, and your lil' script runs, and if it produces output you'll find it in the event log.

You have to toggle from AppleScript to JavaScript in more than one location (once in the main UI, once in Preferences) in order to actually be working in JavaScript.

The UI says JavaScript 1.0 when you do change one of the configuration thingies, this refers to 'JS for Automation JavaScript'- which is to say the JavaScript that Apple has built for us to use here which is based on modern JavaScript. The presenter explains this, which is good, because I nearly pooped when I saw the 1.0 and thought he meant we were doomed to some antiquated version of JavaScript to work with.

_Phew._

There's a little box you can check to add a 'script icon' to OSX's kitchen sink - you know what I'm talking about - the system bar thingy. I am really a champ with words today. In any case, from this script icon you'll get a menu of scripts you've created so you can run them whenever you feel like it with a few clicks.

There's a place in Preferences to change your syntax highlighting colors.

Now we learn that every scriptable application in OSX contains within it's bundle a Dictionary of all the terms that it understands. Classes, methods, properties etc. File >> Open Dictionary

Or click on Library.

Oh wait, another place to toggle from AppleScript to JavaScript otherwise you're reading the wrong docs. I did that for a few minutes and was genuinely beguiled.

Scripting Dictionaries are grouped into 'Suites' by functionality.

Once a Suite is selected, you'll see the methods and classes for that particular Suite. Selecting a class will reveal it's elements and properties. Bottom part of the window is a detail drilldown for whatever is selected in the top tree/panes.

Okay, now we're done with the Script Editor basics.

Another presenter comes on. I should have maybe caught the names, but hey, content is queen right now so just roll with it.

We are walked through a business case with repetitive tasks we want to automate. We are selling widgets again. What a crowded market space. A script is shown that produces a full slide deck for Keynote from some Numbers data. I can already do this in Node and generate an HTML slide deck, so I think maybe this isn't the example that will sell me. If you do use Keynote a lot though, this is really cool for localizing and customizing your presentations on the fly and generating them from your Numbers documents. There is definitely an audience for this.

Apple Events are the underlying communication mechanism behind all this scripting stuff. There is a diagram that is basically explaining that you talk to the scriptable application using your language of choice with these events via the JavaScript Apple Event bridge.

I should have started counting how many times they say 'THE POWER OF AUTOMATION' because it's definitely been said more than once.

Node gets a shoutout.

Describes 'Javascript for Automation' as a kind of server-side JavaScript. I guess he's saying it's closer to writing in the Node/io style environment as compared to the browser?

Application object is always the topmost entry point, can entry into it via name, process ID, path - variety of ways

Properties: Safari.name
Elements: Safari.documents[0]
Commands: Safari.open(...)
Classes: Safari.Document(...)

An example is given where we access a tab in Safari and get it's URL, set it's URL. Simple get/set example.

Three ways to access array items:

window = Safari.windows[0]
window = Safari.windows['Apple']
window = Safari.windows['#412']

Some caution about knowing which of these to use when is given but not elaborated on. Something abou safety or security? Have to follow up on that.

Demo Time~

A Hello World is console.log'd.

A small script that changes various properties about a TextEdit document, we are instructed to watch the Event Log just to see how this script works.

The presenter explains how to write a function. Since this is WWDC and not 'JavaScript for people moving to ScriptEditor from Automator' I find this redundant; I think what he was probably try

A filtering arrays example is given using the Mail app, filtering which emails we want to match from the inbox.

The following are equivilent:

message.open()
Mail.open(message)

Path object:

path = Path('/Users/path/to/thing.rtf')
TextEdit.open(path)

Use path objects anywhere a file is expected.

If you pass a string where a file is expected, it's Error Town time.

doc = TextEdit.Document()
TextEdit.documents.push(doc) <--- makes it actually visible in application

You can pass in arguments as a JavaScript dictionary for a lot of constructors.

Use the standardAdditions flag for a bunch of generically useful functions, including a lot of user interaction.


Library/Script Libraries/toolbox.scpt

then

toolbox = Library('toolbox')
toolbox.log('hi hi')

Applets!

"This is doubleclickable JavaScript living on my desktop!"

Heh.

A bunch of handlers with a library for interacting with an app.

UI Scripting via Accesibility to interact with your Mac on your behalf, i.e. simulate clicking on UI elements in an app. An example is given for clicking and typing.

Can use system APIs using ObjC and $. $ has nothing to do with jQuery. ObjC can bridge JS into Objective C and vice versa, and importing Frameworks you want to use. ONce you import stuff, you use it from the $.

An example is given using NSString. 

Another example is given using NSTask.

Bridged nil object. nil ! == undefined.

An example is given on subclassing that produces a Cocoa application. That's pretty cool.

"BEAUTIFUL WHIRLWIND TOUR"

A summary of all the ways you can run scripts around OSX are given.

The guy suddenly started calling Applets: Droplets. This isn't DigitalOcean, what is going on?

We're going to go through one more example with batch processing some photos and emailing them.

We get meta scripting the Script Editor.

Can bind 'run in AppleScript editor to a key command' to show you can code in whatever editor you like.

Can use the osascript command line tool to run the code. osascript has an interactive Javascript mode.

We close with a summary of how good Apple thinks this feature is.












