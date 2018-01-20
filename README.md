## Purpose of this repo

Over the last couple of weeks (early Januaray '18) I've introduced myself to the wonderful and slightly terrifying world of config files and customization. This is my second real semester as a computer science major, and I'm starting to take sides in the Holy Wars. I've always had problems with perfectionism, and I was somewhat horrified to realize how big a time-sink this area has the potential to be.

My general procedure for optimizing things in life is surfing on the absolute edge of marginal cost and marginal benefit: doing the minimum amount of work to achieve the payoff that matches my use case and individual time-distributions. A good shorthand way of describing the system is "research, implement, forget about it."

This area will, of necessity, be a bit more of a continual process. You can't really "set and forget" tools that don't yet exist, and new workflows are being introduced all the time. However, a good bit of the initial legwork can be accomplished at the outset. Below I've tried to summarize more or less what I've gathered in my "initial sweep" of the playing field.

## Shared stuff

Before we get to text editors, terminal clients, and the like, let's get some shared stuff out of the way.

### Theming: colors

[Solarized](http://ethanschoonover.com/solarized). Has design based on lightness relationships and color wheel relationships, and consistent use across light and dark themes for easy adjustability to external lighting conditions. Well designed to main same perceived contrast and lightness across situations/combinations.

I'm a big fan of the thought that went into this. Another good thing to read on the subject: [here](http://observer.com/2015/02/meet-the-man-behind-solarized-the-most-important-color-scheme-in-computer-history/). According to this piece, some amount quantitative A/B testing went into the design as well. (At least with respect to the color red... but probably elsewhere as well).

### Powerline

[Look at this](https://gist.github.com/kevin-smets/8568070). Example of a Powerline zsh theme. 

[Main Repo](https://github.com/powerline/powerline) for the original powerline. Written in Python, lightweight, can be run in daemon mode for performance, and has settings through JSON.

No reason not to use this (in whatever form) in everything that could benefit.

## Font

Fonts needs to be patched to work with Powerline. [List](https://github.com/powerline/fonts).

I like slashed zeroes since they are the easiest to distinguish (even though some people find them a bit jarring: see [Inconsolata-g](http://leonardo-m.livejournal.com/77079.html)). It's important to check characters that affect legibility: `O0, l1, 17, lI, Z2, S5, G6, B8, vy`. I prefer uniform heights across (\[{ for visual consistency, unlike Inconsolata (cf. bracket heights to those of curly brackets and parentheses). It's also important to have a relatively large x-height, a good width, a good default weight, and optimal line-spacing. (Among other things).

[Input](http://input.fontbureau.com/info/) appears to have a lot of thought behind it. I really like that you can customize the choices for characters, line height, width, weight, and so forth. (See the [preview page](http://input.fontbureau.com/preview/)).

I'm a fan of proportional fonts for coding, outsourcing the semantic vertical alignment of comments and the like to the development environment (see [Elastic Tabstops](http://nickgravgaard.com/elastic-tabstops/)). Proportional fonts help you catch typos in strings of text that start the same way, and let characters take up the space that they need, rather than stretching or truncating them in a procrustean manner. They are also much better for using different typefaces to aid in syntax highlighting, which is something that is so obviously superior I can't figure out why it isn't done more. (A bold weight that takes up the same width as the font's regular weight is less distiguishable, e.g.).

## Text Editor

### Editing Style

Modal editing is superior to chorded editing since we do tend to edit in bursts, and it is more ergonomic/faster to type long sequences of commands without having to chord. However, leader keys and escape keys do add overhead to command sequences.

There are two ways that I've come across to solve this problem. Unlike other layers that can be accessed by holding down a thumb key, Vim uses almost all the key bindings, meaning you need thumbs free as well. According to [Tristan Hume's excellent text editor comparison](http://thume.ca/2017/03/04/my-text-editor-journey-vim-spacemacs-atom-and-sublime-text/), you can achieve fast, temporarily modal access with palm keys:

> The fanciest thing I did was create my own [set of keybindings](https://github.com/trishume/SublimeTect) that work like Vim except with the palm keys of [my custom keyboard as the mode](http://thume.ca/2014/09/08/creating-a-keyboard-1-hardware/). That way it is faster to quickly do movement and editing actions in the middle of writing. It also synergizes way better with the mouse because I never am in an unexpected mode when I use it and then move back to the keyboard since they physical state of my hands is the state of the editor. I still drop into Vintageous mode for fancier editing though.

However, I see couple problems with this approach. First off, while I've never had the luxury of thumb keys myself, all the "mock-ups" I've tried have impacted the freedom of my hands when typing, particularly far away keys that require any sort of extension. My hands naturally shift when my index and pinky are reaching for laterally shifted keys, for example, and this is made more difficult by anchoring the palm/wrist. Secondly, palm keys add significantly to the size of a keyboard due to how they need to be spaced away from the rest of the hand. This makes the keyboards more expensive, less portable, and harder to leg-mount, which is definitely the best location ergonomically and practically. (Even though there is stigma because it looks goofy).

A foot pedal (e.g., [here](https://www.kinesis-ergo.com/shop/advantage-single-pedal/)) seems like the most logical solution to the "editing spurts" problem. Our feet do not have anywhere near the dexterity of our hands (making a foot pedal suboptimal for regularly actuating keys), but the broad movements are sufficient for actuating a layer system that is held down for at least a couple seconds to jump in and out of normal mode. I have not tested this yet personally, but it has none of the philosophical problems that palm keys do. A foot pedal should not interfere with proper chair ergonomics if you configure your workstation correctly. Same deal with standing-desk configurations, if you take the time to construct a logical standing platform. I'll report back once I verify this workflow.

These solutions basically negate the advantage that chorded bindings have over modal bindings: being available all the time.

As to which modal system to choose, I've chosen to stick with Vim (with a couple modifications to make [my custom character layout](https://github.com/StevenTammen/hieam) work with it) due to the mnemonics. [Xah Fly Keys](http://ergoemacs.org/misc/ergoemacs_vi_mode.html) is a worthy project to check out for people who spend enough time in their text-editor to get commands strictly into muscle memory, since it prioritizes key placement over memorability. Eventually it would be good to line up command frequency and mnemonic considerations to create a layout that was both optimally layed out and memorable (e.g., coming up for mnemonics for the placement of optimal keys to make them easier to remember), but that is a project for someone else.

Leader key sequences a la [Spacemacs](https://github.com/syl20bnr/spacemacs), [SpaceVim](https://spacevim.org/), or [Xah Fly Keys](http://ergoemacs.org/misc/ergoemacs_vi_mode.html) should also definitely be implemented. Remember, sequences are better/faster than chords in most situations, and certainly faster than typing out the full name of commands, even with autocompletion.

### Some Initial Commentary

Read [this page](http://thume.ca/2017/03/04/my-text-editor-journey-vim-spacemacs-atom-and-sublime-text/) -- the one linked above -- all the way through. Shoutout to [Tristan Hume](http://thume.ca/) for posting this thorough comparison. This piece really jump started my thought process, and I've referred to it a lot as I've started thinking.

It's worth pointing out that NeoVim is not part of this comparison. More on that below.

My main takeaways from this post:

- Mouse hostility in text editors is dumb. Sometimes (rarely, but sometimes) using the mouse *is* fastest. Disabling its use, or complicating it, makes no sense.
- Multiple text editing cursors looks awesome (and gives my inner poweruser warm fuzzies). It also makes a lot of sense in certain contexts. Emacs and Vim should get on board and make their implementations as good as Sublime's.
- Criticisms of Spacemacs (bugs, problems in layer integration, having to contribute a lot to get desired functionality) seem valid, but will all be less applicable the more stable the platform gets. It's grown since the time this was written, and presumably bug-squashing, layer interoperability, etc. were part of that growth.
  - The complaint about hit-or-miss support for less common languages like Rust is valid, but wont apply to most devs. Probably also improving with time.
- Example of fuzzy (non-regex) search-and-replace workflow needs to be qualified. It sounds like it may be easier in Sublime. But there are going to be examples going the other way too: things easier to do in Spacemacs than Sublime (and I'm sure things Spacemacs can do that Sublime just straight-up can't). Need lots more data points before I am comfortable generalizing about how much they "just work."
  - I am comfortable with the idea that Sublime is better out of the box for most people, however. Emacs is fiddly. Full stop.
- Good points made with respect to windows/tabs/buffers etc. I'm still looking into the best way to do window management with GUI Emacs. The playing field may have changed since this was written. Tmux etc. might integrate, you can use packages like eyebrowse, there is daemon mode, etc.
- Performance: this is one of the areas that I'm most concerned with Spacemacs. Emacs, especially Emacs with hacked-on elisp packages not written with each other in mind, is going to be slower. It's a question of how much slower, and if it's enough to merit switching to a different editor.
- APIs and limits on plugin development: this stuff is important. Async is mandatory. The more plugins/packages you have in Vim/Emacs, generally speaking, the slower you get. Things don't play nice. Having core plugin behavior actually coded into the editor means everything will work seamlessly
  - Not having to be backwards compatible with a bunch of different 3rd-party-plugins is important for being able to keep increasing speed and code efficiency. [Relevant xkcd](https://xkcd.com/1172/).

### NeoVim

The basic gist of NeoVim, from what I've gathered:

- Much better development community than straight Vim. More contributors, less of a "one-man-running-the-show" deal.
- Async plugins. Vim 8 has this too now, bit NeoVim did it first. Sublime has them too, of coure.
- Flexible plugin writing with support for multiple languages. Most notably Python and Lua.
  - Not everything about elisp and Vim script is terrible, but I'd rather have Python and Lua, thanks much.
- [Fzf](https://github.com/junegunn/fzf). Fuzzy search with Go. Not necessarily exclusive to NeoVim, but often comes up in conversations about it.

### Editor Choice

As long as you are using a hackable editor with extended support for changing keybindings, remapping functions/commands, and emulating Vim/modal editing to a fairly high degree, I honestly don't think it matters all that much. (So much for Holy Wars). For example, you can set up "Spacemacs-like" key sequences in both [Sublime Text](https://github.com/dvcrn/sublimious) and [Vim/NeoVim](https://github.com/SpaceVim/SpaceVim). More or less work may be required to get that sort of "set and forget" config, but it seems to be possible with all of them.

I am optimistic that Microsoft's [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) will gain traction and people pushing for it, as in [here](https://langserver.org/), will be able to make all the editors powerful with respect to IDE stuff. This would serve to narrow the gaps between the editors even more.

The one thing I am most interested in this point (since NeoVim/Spacemacs/Sublime all support Async plugins and extensibility with "real" languages) is quantitative performance analysis. How do they run on large codebases with many dependencies? What is fuzzy search like when your file is 70MB? What is autocomplete like when your directory has 10,000 files? How snappy is the editor when you have the full complement of necessary packages installed and operational?

I am particularly interested in how efforts over time to standardize plugin APIs (not to mention more IDE like features, see the LSP above) could improve speed. Spacemacs and its clones are very much a step in the right direction towards getting things to work together seamlessly, without things breaking and slowing each other down.

It's worth poiting out that things like Atom and VSCode also exist, as well as full-blown IDEs like IntelliJ. I just don't think they really compare to any of these three when examined overall. I'll do more research on other options later.

### Other Considerations

Something to consider independent of editor is whether to run the editor in GUI mode or in terminal mode. [Here](https://blog.aaronbieber.com/2016/12/29/don-t-use-terminal-emacs.html) is a good introduction to some of the considerations. 

What really seems to matter, it seems to me, is consistency from editing remote files in your own environment. Speed is born of regularity -- using "your system" (whatever it may be) will be superior to using whatever distribution happens to be present on the server you SSH into. So whether or not you run terminal Vim/Emacs/whatever on your box is not the most relevant thing... what is important is that you are on *your* box. [Tramp mode](https://www.emacswiki.org/emacs/TrampMode) for Emacs allows this seamlessly. I don't know enough about how you might implement similar file access protocols for Vim and Sublime, but I'm guessing there is a way. Maybe mounting SSHFS directories?

Window management comes into play here. The hipster combo seems to be pairing Vim with Tmux and iTerm2 on Mac OS X. Tmux obviously focuses on terminals, but from what I gather it is the "session" aspect that sets Tmux apart from the likes of [i3](https://i3wm.org/). Since having window management for things like Chrome, Spreadsheets, etc. is also useful, I don't see a reason to complicate things with two sets of bindings (one for a window manager, and one for Tmux). Perhaps using [Abduco](https://github.com/martanne/abduco) with a proper window manager would work just as well? On the other hand, other people seem to argue that the scriptability of Tmux and the ability to SSH into it are the main benefits (see [here](https://www.reddit.com/r/vim/comments/6krkji/i3_or_tmux_for_managing_terminals/) and [here](https://www.reddit.com/r/vim/comments/73y8o6/people_of_unix_and_vim_do_you_use_tmux_or_a_tiled/)). I don't know enough to make judgements about these things. Anyway, the point is, your editor needs to integrate seamlessly with the larger window/session manager you use.
