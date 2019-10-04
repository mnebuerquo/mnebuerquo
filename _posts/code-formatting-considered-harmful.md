# Code Formatting Considered Harmful

Are you getting angry yet?

You might not have read my title carefully. What it means is that those red squiggly lines in your favorite editor make you a worse programmer.

Are you angry now?

I just said you're a worse programmer because of something you think is making your coding better. You're definitely not going to like the fact that I'm correct about that.

# What's Code Formatting All About Anyway?

Code formatting is the practice of changing your code to apply a consistent set of conventions about the use of whitespace. This means spaces between tokens, newlines, indents, and line length. The changes made are only to the whitespace, and do not change the meaning of the code or the behavior of the program.

People often ask for code formatting conventions because as code is modified by multiple contributors it starts to get messy. Some people indent with different patterns than others. Some people put a space before the paren and some people put a space after. There has been research done which concluded that having consistent use of whitespace in a project reduces the mental effort required to read and modify the code.

People have worked very hard to establish tools to aid in code formatting. There are linters with whitespace rules. There are editors which draw red squiggly lines under your code where it doesn't match the rules. Most editors automatically indent when you insert a newline. Many editors reformat when you save a file. There are tools which will reformat your entire project.

This sounds like a good thing. Why would you not want your code to be consistently formatted?

There are a few reasons, and none of them have anything to do with the readability of the code. Sure, code which is consistently formatted is more readable and easier to work with. But that's only part of the story.

# Cognitive Load

Chances are that your code isn't already well formatted. And new code you write might not be well formatted. And new code written by someone on your team is almost certainly not well formatted. This is because you're humans, and your team is composed of other humans, and humans are not good at consistency.

When you're writing code, you're solving a problem. This problem requires you to hold many variables in your short-term memory, and manage the relationships between their possible states. It's a problem of combinatorial complexity, so as the number of variables increases, you multiply the complexity by the cardinality of their states. Basically, the more things you have to think about, the harder it is to keep track of it all.

Reading complicated code is harder when the spacing between tokens is inconsistent. Instead of just loading those symbols into your short-term memory and starting the mapping of relationships, you first have to parse the symbols to accurately identify what they are in their context. This is why people want the code to be formatted consistently. They want to be able to read it faster so they can start to build their mental model more quickly.

Writing new code or changing code is a little different. When writing, you have an idea in your head which you are trying to translate into symbols which form the instructions the computer will then follow to solve the problem. This requires you to still hold all the variables and state and relationships you mapped from other parts of the code, and now you're making new relationships while transforming them back into the symbols the machine understands.

Now those little squiggly lines in your editor are there to help you write better code. Someone added a little hint which underlines things as you type if they don't match the rules for your project. What's more helpful when you're trying to think through complex sequences of steps than someone interrupting every second or two to tell you you're doing it wrong? What they're actually doing is adding to the number of things you're juggling in your very finite brain. Sure, it's easy to fix all your spaces anywhere they don't match the rules, and each of those fixes is trivial. But when you have your tool telling you to change stuff as you type, those trivial little choices add up to a big distraction.

# Multi-Dimensional Beings

Remember that episode of your favorite sci-fi show when the crew met some creatures which perceived and interacted with more dimensions than humans do? What about the multi-verse episode where they could jump between different universes where someone in the past had made different choices? Well, those multi-dimensional beings are programmers.

Writing code isn't a two-dimensional excercise. You could think of it as existing in the lines of code, and the number of tokens in each line, and that's two dimensions. But when you think about code, you're thinking of how the machine executes it. It's chains of cause and effect. That adds a dimension for the passage of time. Then every variable you've ever referenced in that code could have different values. Each of those is a dimension.

Those dimensions just represent the code as it is now. The code is a changing landscape. Yesterday it was different from today, and tomorrow it will be different again. Every change a developer has made gives you a new universe of code to explore. In this multiverse, reading code may require jumping to a different branch to understand the consequences of a different set of decisions. It might also be important to trace back through the decisions which created your current universe out of a parent state.

The multiverse analogy is a way to look at your git branches. You want the differences between universes to be meaningful, and there is a chain of events in the formation of your current branch which you sometimes need to trace. Suppose you're adding a feature which touches several modules. You want to know why a particular line of code is what it is. Git has tools for searching history to find where changes happened. This is easier if there are fewer changes, or if you only see the meaningful changes. Code formatting changes are just layers of history where nothing happened. It makes it harder to find when something changed, who changed it, and the important part which is why it changed.

# Who is in charge here?

Your tools are supposed to serve you. They are supposed to either enable you to do things you couldn't before, or make previously slow things faster.

Suppose you add a bunch of lint rules about whitespace, and you enable the editor hints so you see red lines under your code. This adds a distraction as you write code. The effort is tiny each time, but the tool is interrupting you when you're working. So you decide to turn that off and work without interruption. This allows you to just write what you're thinking, and not worry about how it's spaced. You can always fix that stuff later. Your flow improves as you stop thinking about stuff that's not related to the problem.

Then you've got a code change which works and is ready to commit. You try to commit and now you get lint messages from your pre-commit hook. The thing you are working on is still only partly complete, and you just want to commit often. Maybe it's even a not-yet-working commit and you just need to push a branch before you go to a meeting or lunch. Now your lint is blocking your commit because of whitespace. Each of these lint messages will take 30 seconds or so to address, and there are a dozen messages blocking you. So you take the lint warnings out of the pre-commit hook, and now you can commit often without having to address all those little whitespace things first.

So now your linter starts complaining in your CI pipeline. In addition to the 30 seconds to find and fix each little thing, you now have the cost of another commit and re-running the pipeline up to the linter step. This might be slower or faster depending on your project, but it's always annoying.

Your tools are telling you what to do the whole time. Aren't you the one who is supposed to be calling the shots?

# It's a Tax

So you pay this continuous cost while you work. Maybe it's while you're coding, where it's constantly interrupting and maybe doesn't feel like a heavy burden because the effort is so small with each one. Maybe it's whenever you try to commit, which feels like a cost because you're needing to go to a meeting or catch the bus home. Or it's in the pipeline which leads to frustration because you maybe forgot about the linter and thought your changes were complete. Regardless of how it feels, there's a cost to keeping your code formatted and looking pretty.

Now it's still true that there's a cost to leaving it messy. Messy code costs when you read it. This cost is variable. Some code is still pretty quick to read even if it's not consistently formatted, and some code is hard to read, no matter how well formatted. Unless your whitespace chaos is extreme, this is going to be a lot less important than other kinds of readability issues, such as how things are named.

It is your choice where you pay this price. It's often more expensive to let the code get messier and pay every time you read. Some files you look at rarely and it probably doesn't matter. Other modules like library code you might be reading often but seldom changing. It might make sense to do some formatting on them so future reads are cheaper. Other files you might modify often, so it might be more practical to clean them up as you go, or maybe not. In a legacy codebase where git history is important, it might be cheaper to avoid changing whitespace at all.

# Developers are Insane

Developers look at the world in a different way than regular people. People don't like to be told what to do, and developers tend to take that to a new level. Especially when there isn't a good reason, developers want you to mind your own business and get out of their way so they can do what they love to do.

I've seen multiple heated arguments about code formatting. People have almost religious beliefs around it, and most just automatically say that code must be formatted and readable without really examining that idea. Someone told them its a best practice, and now they Believe. If you tell someone that this thing they Believe is wrong, they get angry. "Tabs vs. Spaces" is just as dogmatic as beliefs about politics or religion. Developers have been trained to view this topic in absolutes, as black or white.

The reality that many people can't see is that there isn't an answer to "How should I format my code?" The answers are all entirely subjective and biased. There is some evidence that consistency helps readability, but no one tells you about the cost of maintaining that consistency.

Combine the "you can't tell me how to write my code" independence with a dogmatic "tabs are better than spaces" belief, and you get a holy war whenever a team starts debating whitespace rules. Just starting the conversation is bad team smell. It says that the people on the team don't trust each other to write readable code.

# Give me Liberty

Your tools are supposed to work for you, not the other way around. Why not make the formatting of code completely automatic? There are tools that do that for a variety of languages. Don't make the linter fuss at people about spacing when they commit or in the pipeline. Just add a hook which quietly formats all commits according to the rules whenever the author commits the code. Then it's impossible to add unformatted code to your repo, and no one is distracted with red lines about it while coding, and no commits are blocked by it. If something still isn't right, it can fail tests in the pipeline.

Always use the default rules or a set from some big open-source project because then no one in the team is making the decision. Use a standard set for your language if it exists. The rules came from outside people who aren't available to argue with. It doesn't matter what the rules themselves are. The value is in consistency, and that no one in the team needs to think about it again.

# Life is too short to ever think about whitespace again

The important thing is to not have to argue about it anymore. Just do it the way the tool does it and focus on something much more important.

And don't let me hear you talking about it. Just do that somewhere else.
