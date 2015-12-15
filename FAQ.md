# FAQ

Q: Why would you use this?
A: I don't know, you're the one looking into it.

Q: No, really, why?
A: You can bootstrap project management of something you're working on 
   without any dependencies on external software. You can work offline. 
   You can use whatever tools you want (SublimeText, notepad, ed, cat,
   vim..) to manage issues and not be locked into any vendor-specific
   tracking software. You can keep track of things you need to do on 
   as granular a level as you want locally without management complaining 
   about the number of tickets. You can follow this convention and keep your
   issues alongside your code in the same repo. You can trivially define 
   your own extensions/conventions to add to this since arbitrary files 
   are permited.
   
   I don't know you're the one looking into it.

Q: How do I close an issue?
A: `git rm -r`

Q: How do I reopen an issue?
A: `git revert`

Q: How do I rename an issue?
A: `git mv`

Q: What if issue names conflict?
A: Why are your issue titles generic? If you're using a shared git repo
   to manage issues with other people, make sure you pull (and push) often 
   enough to avoid conflicts and other users are using descriptive issue
   titles.

Q: How do I check the issue creation time?
A: Check the file ctime, or use `git log`

Q: How do I check the issue last update?
A: Check the maximum file mtime of anything in the issue directory. 
   (or `git log`)

Q: How do I see the issue author?
A: `git log` (if it's not tracked, the author is you.)

Q: How does a team comment on issues?
A: Adopt a convention to use as an extension of this standard and track it
   in a git repo. In the unlikely event that this standard becomes popular,
   whatever convention is most widely adopted/considered best practice will 
   probably be incorporated into a future version.

   (Whatever the convention is, `git log` will almost certainly be how 
    you find the time/author of a comment.)


Q: How do I enforce [policy x] for a team
A: Write a git hook.

Q: This can never work because [...]
A: Okay, so use something that works better for you.
