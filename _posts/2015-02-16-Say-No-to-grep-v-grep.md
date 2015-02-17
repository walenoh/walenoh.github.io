---
layout: post
title: "Say No to grep -v grep"
category: articles
tags: [grep, OS X]
---



Sometimes, I need to search for process ids, so I pipe that search to grep and search the processes. Depending on how I run that search, ps may return the grep search too. One way to remove grep from the list would be to use grep -v grep. There has to be a better way right? Randal L. Schwartz explains a better way. [Original Post](http://www.perlmonks.org/bare/?node_id=203760)  

"```ps -ef | grep -v grep | grep inetd```


Please, let us not cargo-cult this crazy "grep -v grep" some more. I cringe each time I see that. It's a poor solution to a common problem.
The way to avoid picking out the grep process itself is to ask ps for the proper things:


```ps axc | grep inetd```

If your ps doesn't have a "command-name only" solution, then simply muddy the argument so that the grep cannot match it:

```ps ax | grep '[i]netd'```

Let's not be wasting processes needlessly. Think before you type, people.
-- Randal L. Schwartz, Perl hacker"

