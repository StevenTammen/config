## Purpose of this repo

Over the last couple of weeks (early Januaray '18) I've introduced myself to the wonderful and slightly terrifying world of config files and customization. This is my second real semester as a computer science major, and I'm starting to take sides in the Holy Wars. I've always had problems with perfectionism, and I was somewhat horrified to realize how big a time-sink this area has the potential to be.

My general procedure for optimizing things in life is surfing on the absolute edge of marginal cost and marginal benefit: doing the minimum amount of work to achieve the payoff that matches my use case and individual time-distributions. A good shorthand way of describing the system is "research, implement, forget about it."

This area will, of necessity, be a bit more of a continual process. You can't really "set and forget" tools that don't yet exist, and new workflows are being introduced all the time. However, a good bit of the initial legwork can be accomplished at the outset. Below I've tried to summarize more or less what I've gathered in my "initial sweep" of the playing field.

## Shared stuff

Before we get to text editors, terminal clients, and the like, let's get some shared stuff out of the way.

### Theming: colors

[Solarized](http://ethanschoonover.com/solarized) has a design based on lightness relationships and color wheel relationships, and enables consistent use across light and dark themes for easy adjustability to external lighting conditions. Well designed to main the same perceived contrast and lightness across situations/combinations.

I'm a big fan of the thought that went into this. Another good thing to read on the subject: [meet the man behind Solarized](http://observer.com/2015/02/meet-the-man-behind-solarized-the-most-important-color-scheme-in-computer-history/). According to this piece, some amount quantitative A/B testing went into the design as well. (At least with respect to the color red... but probably elsewhere as well).

### Powerline

[A Powerline zsh theme configuration](https://gist.github.com/kevin-smets/8568070).

The [main Repo](https://github.com/powerline/powerline) for the original powerline is separate from some of the themes that implement the concept. The base implementation is written in Python, lightweight, can be run in daemon mode for performance, and has settings through JSON.

There is no reason not to use some implementation of this in everything that could benefit. It makes prompts more useful and displays information at a glance.

## Font

Fonts needs to be patched to work with Powerline and the themes associated with the idea. [List of patched fonts](https://github.com/powerline/fonts).

I like slashed zeroes since they are the easiest to distinguish (even though some people find them a bit jarring: see [Inconsolata-g](http://leonardo-m.livejournal.com/77079.html)). It's important to check characters that affect legibility: `O0, l1, 17, lI, Z2, S5, G6, B8, vy`. I prefer uniform heights across (\[{ for visual consistency, unlike Inconsolata (cf. bracket heights to those of curly brackets and parentheses). It's also important to have a relatively large x-height, a good width, a good default weight, and optimal line-spacing. (Among other things).

[Input](http://input.fontbureau.com/info/) appears to have a lot of thought behind it. I really like that you can customize the choices for characters, line height, width, weight, and so forth. (See the [preview page](http://input.fontbureau.com/preview/)).

I'm a fan of proportional fonts for coding, outsourcing the semantic vertical alignment of comments and the like to the development environment (see [Elastic Tabstops](http://nickgravgaard.com/elastic-tabstops/)). Proportional fonts help you catch typos in strings of text that start the same way, and let characters take up the space that they need, rather than stretching or truncating them in a procrustean manner. They are also much better for using different typefaces to aid in syntax highlighting, which is something that is so obviously superior I can't figure out why it isn't done more. (A bold weight that takes up the same width as the font's regular weight is less distiguishable, e.g.).

## Text Editor

### Editing Style

Modal editing is superior to chorded editing since we do tend to edit in bursts, and it is more ergonomic/faster to type long sequences of commands without having to chord. However, leader keys and escape keys do add overhead to command sequences.

There are two ways that I've come across to solve this problem. Unlike other layers that can be accessed by holding down a thumb key, Vim uses almost all the key bindings, meaning you need thumbs free as well. According to [Tristan Hume's excellent text editor comparison](http://thume.ca/2017/03/04/my-text-editor-journey-vim-spacemacs-atom-and-sublime-text/), you can achieve fast, temporarily modal access with palm keys:

> The fanciest thing I did was create my own [set of keybindings](https://github.com/trishume/SublimeTect) that work like Vim except with the palm keys of [my custom keyboard as the mode](http://thume.ca/2014/09/08/creating-a-keyboard-1-hardware/). That way it is faster to quickly do movement and editing actions in the middle of writing. It also synergizes way better with the mouse because I never am in an unexpected mode when I use it and then move back to the keyboard since they physical state of my hands is the state of the editor. I still drop into Vintageous mode for fancier editing though.

However, I see couple problems with this approach. First off, while I've never had the luxury of palm keys myself, all the "mock-ups" I've tried have impacted the freedom of my hands when typing, particularly far away keys that require any sort of extension. My hands naturally shift when my index and pinky are reaching for laterally displaced keys, for example, and this is made more difficult by anchoring the palm/wrist. Secondly, palm keys add significantly to the size of a keyboard due to how they need to be spaced away from the rest of the hand. This makes the keyboards more expensive, less portable, and harder to leg-mount, which is definitely the best location ergonomically and practically. (Even though there is stigma because it looks goofy).

A foot pedal (e.g., [here](https://www.kinesis-ergo.com/shop/advantage-single-pedal/)) seems like the most logical solution to the "editing spurts" problem. Our feet do not have anywhere near the dexterity of our hands (making a foot pedal suboptimal for regularly actuating keys), but the broad movements are sufficient for actuating a layer system that is held down for at least a couple seconds to jump in and out of normal mode. I have not tested this yet personally, but it has none of the philosophical problems that palm keys do. A foot pedal should not interfere with proper chair ergonomics if you configure your workstation correctly. Same deal with standing-desk configurations, if you take the time to construct a logical standing platform. I'll report back once I verify this workflow.

These solutions basically negate the advantage that chorded bindings have over modal bindings: being available all the time.

As to which modal system to choose, I've chosen to stick with Vim (with a couple modifications to make [my custom character layout](https://github.com/StevenTammen/hieam) work with it) due to the mnemonics. [Xah Fly Keys](http://ergoemacs.org/misc/ergoemacs_vi_mode.html) is a worthy project to check out for people who spend enough time in their text-editor to get commands strictly into muscle memory, since it prioritizes key placement over memorability. Eventually it would be good to line up command frequency and mnemonic considerations to create a layout that was both optimally layed out and memorable (e.g., coming up for mnemonics for the placement of optimal keys to make them easier to remember), but that is a project for someone else.

Leader key sequences a la [Spacemacs](https://github.com/syl20bnr/spacemacs), [SpaceVim](https://spacevim.org/), or [Xah Fly Keys](http://ergoemacs.org/misc/ergoemacs_vi_mode.html) should also definitely be implemented. Remember, sequences are better/faster than chords in most situations, and certainly faster than typing out the full name of commands, even with autocompletion.

### Some Initial Commentary

Read [Tristan Hume's page on text editors](http://thume.ca/2017/03/04/my-text-editor-journey-vim-spacemacs-atom-and-sublime-text/) all the way through. Shoutout to him for posting this thorough comparison. This piece really jump started my thought process, and I've referred to it a lot as I've started thinking.

It's worth pointing out that NeoVim is not part of this comparison. More on that below.

My main takeaways from this post:

- Mouse hostility in text editors is dumb. Sometimes (rarely, but sometimes) using the mouse *is* fastest. Disabling its use, or complicating it, makes no sense.
  - I think it's worth pointing out that relative line numbers make keybindings that much more efficient (since you don't have to mentally calculate anything). 
- Multiple text editing cursors looks awesome (and gives my inner poweruser warm fuzzies). It also makes a lot of sense in certain contexts (looking at you, HTML). Emacs and Vim should get on board and make their implementations as good as Sublime's.
- His criticisms of Spacemacs (bugs, problems in layer integration, having to contribute a lot to get desired functionality) seem valid, but will all be less applicable the more stable the platform gets. It's grown since the time this was written, and presumably bug-squashing, layer interoperability, etc. were part of that growth.
  - The complaint about hit-or-miss support for less common languages like Rust is valid, but wont apply to most devs. Probably also improving with time. See also below for a discussion of Microsoft's [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) that would help in this respect.
- The example of his non-regex search-and-replace workflow needs to be qualified. It sounds like it may be easier in Sublime. But there are going to be examples going the other way too: things easier to do in Spacemacs than Sublime (and I'm sure things Spacemacs can do that Sublime just straight-up can't). Need lots more data points before I am comfortable generalizing about how much they "just work."
  - I am comfortable with the idea that Sublime is better out of the box for most people, however. Emacs is fiddly. Full stop. It's one of the things that makes it powerful: you can craft it to do *exactly* what you want. But it may take you a while to get there. Spacemacs and other package aggregators help in this regard.
- Good points made with respect to windows/tabs/buffers etc. I'm still looking into the best way to do window management with GUI Emacs. The playing field may have changed since this was written. [Tmux](https://github.com/tmux/tmux/wiki) etc. might integrate, you can use packages like [Eyebrowse](https://github.com/wasamasa/eyebrowse), there is [daemon mode](https://emacs-fu.blogspot.com/2009/02/emacs-daemon.html) (i.e., Emacs as server), etc. There is also an [Emacs X Window Manager](https://github.com/ch11ng/exwm).
  - All this to say, the problems appear to be soluble.
- Performance: this is one of the areas that I'm most concerned with Spacemacs. Emacs, especially Emacs with hacked-on elisp packages not written with each other in mind, is going to be slower than an application that can fully optimize. It's a question of how much slower, and if it's enough to merit switching to a different editor. Of course, Vim plugins and Sublime Text plugins are also not part of the editor cores, so they can have the same the same sorts of problems. But it appears to be more of a roadblock in Emacs, probably in part because you can change more (so one plugin can change an editor variable than another plugin depends on, etc.).
- APIs: this stuff is important. Async is mandatory. The more plugins/packages you have in Vim/Emacs, generally speaking, the slower you get. Things don't play nice. Having core plugin behavior actually coded into the editor means everything will work seamlessly
  - Not having to be backwards compatible with a bunch of different 3rd-party-plugins is important for being able to keep increasing speed and code efficiency. [Relevant xkcd](https://xkcd.com/1172/).

### NeoVim

The basic gist of NeoVim, from what I've gathered:

- Much better development community than straight Vim. More contributors, less of a "one-man-running-the-show" deal. More in the spirit of OSS.
- Async plugins. Vim 8 has this too now, but NeoVim did it first. Sublime has them too, of coure.
- Flexible plugin writing with support for multiple languages. Most notably Python and Lua.
  - Not everything about Vim script is terrible, but I'd rather have Python and Lua, thanks much. I haven't pegged how well elisp fares against Python or Lua, but having the flexibility to write plugins in *any* language is definitely a plus.
  - I read some stuff from Paul Graham that really makes me want to grok Lisp. For example, [this post about his startup](http://paulgraham.com/avg.html) and [this one about Lisp in web applications](http://ep.yimg.com/ty/cdn/paulgraham/bbnexcerpts.txt). This isn't talking about Elisp per say, but, well, Elisp is in the family.
- [Fzf](https://github.com/junegunn/fzf). Fuzzy search with Go. Not necessarily exclusive to NeoVim, but often comes up in conversations about it.

### Editor Choice

As long as you are using a hackable editor with extended support for changing keybindings, remapping functions/commands, and emulating Vim/modal editing to a fairly high degree, you can do most things that you would want to do. For example, you can set up "Spacemacs-like" key sequences in both [Sublime Text](https://github.com/dvcrn/sublimious) and [Vim/NeoVim](https://github.com/SpaceVim/SpaceVim). More or less work may be required to get that sort of "set and forget" config, but it seems to be possible with all of them.

This being said, all appear to have their pros and cons. Vim/NeoVim is definitely the best if you need to quickly edit a file somewhere over SSH. NeoVim also allows for plugins in theoretically any language (though emphasizing Python and Lua), as opposed to Sublime's Python plugins and Emacs' elisp plugins. Sublime text has better multiple cursor support (some say *a lot* better than the Vim/Emacs plugins that emulate it, but I don't know enough to judge), much better fuzzy search, and reportedly better project management. Emacs is definitely the most customizable of the three (you can basically change anything and everything), and has many large, stable packages that the other two may not be able to match. Packages like [Magit](https://github.com/magit/magit), [Helm](https://github.com/emacs-helm/helm), [Projectile](https://github.com/bbatsov/projectile), [Dired](https://www.gnu.org/software/emacs/manual/html_node/emacs/Dired.html), [VLF](https://github.com/m00natic/vlfi), and, perhaps most importantly, [Org Mode](https://orgmode.org/), which has no analogue that even comes close in the other editors. Emacs also has [Tramp](https://www.emacswiki.org/emacs/TrampMode) which makes dealing with remote files a breeze (another thing for which the others don't really have a comparable answer) and [Eshell](https://www.gnu.org/software/emacs/manual/html_mono/eshell.html), with support for running other shells (zsh fish, etc.) inside Emacs. Eshell is sort of an unloved bastard child (with awful documentation), but it is very different. More on this below. It's worth poiting out that Evil-mode in Emacs is basically to the point now where Emacs is just as much Vim as Vim is (in terms of text-editig power, that is).

I am optimistic that Microsoft's [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) will gain traction, and that the people pushing for it, as in [the people at Langserver](https://langserver.org/), will be able to make all the editors powerful with respect to IDE stuff. This would serve to narrow the gaps between the editors even more, particularly for less common languages.

The one thing I am most interested in this point (since NeoVim/Spacemacs/Sublime all support async plugins and extensibility with "real" languages -- meaning all features are, to one degree or another, transferable) is quantitative performance analysis. How do they run on large codebases with many dependencies? What is fuzzy search like when your file is 70MB? What is autocomplete like when your directory has 10,000 files? How snappy is the editor when you have the full complement of necessary packages installed and operational? What about when you have multple SSH sessions open, and many (15+) windows with code and documetation?

It would also be good to make a full study of which "framework" had the best overall system for continuing plugin development and quality. Maintainable APIs that allow plugins to asynchronously share information, low-level optimization to make plugins blazing fast, strictly enforced rules to make sure that plugins can't break each other, etc. In the long term it might be best to pick the platform that would allow for the fastest, most feature-filled editor, aside from current implementations.

Spacemacs and its clones are very much a step in the right direction towards getting things to work together seamlessly, without things breaking and slowing each other down. But a real push to do this *systematically* could be huge in the spead department, particularly for Vim and Emacs where there is less top-down enforcement of what a plugin can and cannot do.

It's worth pointing out that things like [Atom](https://atom.io/) and [VSCode](https://code.visualstudio.com/) also exist, as well as full-blown IDEs like [IntelliJ](https://www.jetbrains.com/idea/). I just don't think they really compare to any of these three when examined overall (for Atom, being built on [Electron](https://electronjs.org/) for cross-system compatibility does not do good things for speed). I'll do more research on these other options later.

### Other Considerations

Something to consider independent of editor is whether to run the editor in GUI mode or in terminal mode. [Here](https://blog.aaronbieber.com/2016/12/29/don-t-use-terminal-emacs.html) is a good introduction to some of the considerations. 

In my opinion, what matters is consistency from editing remote files in your own environment. Speed is born of regularity -- using "your system" (whatever it may be) will be superior to using whatever distribution happens to be present on the server you SSH into. So whether or not you run terminal Vim/Emacs/whatever on your box is not the most relevant thing... what is important is that you are on *your* box. [Tramp mode](https://www.emacswiki.org/emacs/TrampMode) for Emacs allows this seamlessly. I don't know enough about how you might implement similar file access protocols for Vim and Sublime, but I'm guessing there is a way, even if it less elegant.

Window management comes into play here. The hipster combo seems to be pairing vim with [tmux](https://github.com/tmux/tmux) and [iTerm2](https://iterm2.com/) on Mac OS X. Tmux obviously focuses on terminals, but from what I gather it is the "session" aspect that sets Tmux apart from the likes of [i3](https://i3wm.org/). Since having window management for things like Chrome, spreadsheets, etc. is also useful, I don't see a reason to complicate things with two sets of bindings (one for a window manager, and one for tmux). Perhaps using [abduco](https://github.com/martanne/abduco) with a proper window manager would work just as well? On the other hand, other people seem to argue that the scriptability of tmux and the ability to SSH into it are the main benefits (see [here](https://www.reddit.com/r/vim/comments/6krkji/i3_or_tmux_for_managing_terminals/) and [here](https://www.reddit.com/r/vim/comments/73y8o6/people_of_unix_and_vim_do_you_use_tmux_or_a_tiled/)). I don't know enough to make judgements about these things. Anyway, the point is, your editor needs to integrate seamlessly with the larger window/session manager you use.

## Terminal Emulator

While there are popular options like iTerm2 and XTerm, my research has basically led to the unavoidable conclusion that [Alacritty](https://jwilm.io/blog/announcing-alacritty/) is the grail terminal emulator. Heavy use of the GPU for things that aren't video games is something that I've always thought would be a good idea (given that [CPUs and GPUs do different things optimally](https://people.duke.edu/~ccc14/sta-663/CUDAPython.html)), and here we are.

Speed is king here. Sessions, splits, history, etc. can all be handled by the likes of tmux without bloating the terminal itself. Simplicity is beauty.

[Terminals are sexy](https://github.com/k4m4/terminals-are-sexy) is an excellent collection of links to terminal stuff (and shell stuff: see below).

## Shell Choice

Even before I knew what a shell *really* was, I was convinced that I would be using something other than bash. I kept seeing all these blog posts (like [this one](http://www.drbunsen.org/the-text-triumvirate/) -- one of my favorites) praise [zsh](https://www.zsh.org/) for its extended tab-completion, and [oh-my-zsh](http://ohmyz.sh/) for customizability, etc. So I thought I would use zsh.

Then I started doing research, and learned that there is this other thing called [fish](https://fishshell.com/). Apparently fish has a lot of functionality out of the box (syntax highlighting, completion, etc.) that you have to implement in zsh with plugins that can be hard to keep up with. It is also billed as being more "interactive," which in shell parlance, apparently means it is more visual. On the other hand, it's not fully POSIX compliant (whatever that really means), and its Python-ish scripting is not very similar to bash's, for better or for worse. (Better, presumably).

Then there is [xonsh](https://xonsh.org/), which is unabashedly Python-centric (no pun intended), and has some really cool stuff with history and JSON files. It looks like it might do away with some of the shell inefficiencies masked in tradition, replacing glommed-on bash syntax with the elegance of Python. Eshell (baked into Emacs) is somewhat similar, replacing bash syntax with elisp. Running Eshell (or even a normal shell through [M-x shell](https://www.gnu.org/software/emacs/manual/html_node/emacs/Shell.html)) lets you harness the full power of Emacs bindings and buffers -- which is absolutely fantastic since you can use proper search, pagination, etc., instead of black magic with `awk`, `sed`, and `grep`. Eshell in particular is great since it can call elisp functions like file-find and whatnot without any modification whatsoever ([among other things](https://www.masteringemacs.org/article/complete-guide-mastering-eshell)). (You can do something similar with M-x shell and bash/zsh/etc. with aliases and a shell mode hook).

Several people have switched over to Eshell/using shells in Emacs almost exclusively. For example:
- [This dude on reddit](https://www.reddit.com/r/emacs/comments/6y3q4k/yes_eshell_is_my_main_shell/)
- [Howard Abrams](http://www.howardism.org/Technical/Emacs/eshell-fun.html)
- The guy (quoted below) on [this reddit page](https://www.reddit.com/r/emacs/comments/5qh2sd/using_emacs_27_shell_and_eshell/) who provides a good example of why Emacs' "kitchen sink approach" can be excellent:

> I live in three types of shells: eshell is my home, shell-mode on any of a dozen or so remote GNU/Linux machines, and sql-interactive-mode (based on comint-mode) for database use.
>
>One of my favorite features of eshell is being able to treat remote files as if they were local. So files can be copied, moved, deleted, and listed by using Tramp file names without having to adjust much due to which machine the files located.
>
>My init.el sets up dozens of aliases in eshell for each GNU/Linux host and each database user that I use. The shell aliases set the 'default-directory' to the remote machine in Tramp format, and then invokes 'shell'; Tramp does the rest of the magic. I get a new buffer with a shell running on the specified remote host. I also have a chunk of code similar to the magit 'with-editor' package, that allows me to create bash aliases that print a special string that a shell-mode hook recognizes and runs an emacs command as if I had invoked the function from M-x. This allows me to use normal shells much like I do eshell. The database related eshell aliases invoke 'sql-connect' with predefined database connections.
>
>I chuckle at my co-workers who flip between IntelliJ, dbVis, Chrome, Outlook, and Putty applications that have little or no integration beyond cut-n-paste. With Emacs, I have two fullscreen frames open (one on each monitor) with email, IM, web, code editing, and numerous shells. I've added lots of small elisp functions that allow me to move regions quickly between windows, so that I can take SQL query results and add then directly to email messages or wiki pages, or restart a web server on a remote host and bringing it up in a w3m buffer to verify.
>
>As an old-timer, the keyboard with a shell is a very familiar environment, so Emacs' ability to integrate all these pieces saves me time and effort every day.

However, more interactive programs (`top`, `htop`, ncurses programs) don't work well in Eshell, there is no input redirection, and getting good completion set up may require some tinkering around. In other words, for all the cool things it does and tight integration with Emacs, Eshell is not always the best tool for the job. From the [GNU page on Eshell](https://www.gnu.org/software/emacs/manual/html_mono/eshell.html):

> Eshell is not a replacement for system shells such as bash or zsh. Use Eshell when you want to move text between Emacs and external processes; if you only want to pipe output from one external process to another (and then another, and so on), use a system shell, because Emacs's IO system is buffer oriented, not stream oriented, and is very inefficient at such tasks. If you want to write shell scripts in Eshell, don't; either write an elisp library or use a system shell.

I am unsure whether the IO considerations apply to shell mode in general (which would make Eshell no worse than any other shell being run in Emacs), or just to Eshell. I asked [a question about it](https://emacs.stackexchange.com/questions/38230/shell-io-behavior-for-emacs-shells) on the StackExchange.

Finally, a page that has enough information about shells to make you dizzy: [unix shells](http://hyperpolyglot.org/unix-shells).

