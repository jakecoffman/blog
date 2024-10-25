<h1>Breaking up a PR</h1>

<p>
	When you're working on a feature, it's tempting to make a bunch of changes in a single pull request.
	But it's better to break it up into smaller, more focused PRs.
</p>

<p>
	If you've ever wondered why no one is reviewing your PR, it might be because it's too big.
	Or you might have had your teammates just ask directly, "Can you break this up into smaller PRs?"
</p>

<p>
	The reason for this is simple: large PRs are hard to review. You understand what you wrote,
	because you loaded all the context for it into your brain. But your coworkers don't have that context,
	and they might not want to spend the time to load it all in.
</p>

<p>
	When breaking up a PR, it's important to do so in a way that makes sense and is easy to review.
</p>

<p>
	One anti-pattern for breaking up a PR is doing it by file or class. This will create smaller PRs,
	but the full context is still required. Plus, you're effectively adding dead code to the project
	that you'll only use later. This means the PR is still hard to review, your reviewers will
	be less effective at reviewing.
</p>

<p>
	When I think about how to effectively break up a PR, or make smaller PRs in the first place, I
	consider the MVP model:
</p>

<div style="text-align: center;">
	<img src="../mvp.jpg" alt="MVP model: Make small, focused PRs.">
</div>

<p>
	Having a PR that just updates a class, which is otherwise unused is like starting with a useless tire.
	Instead, focus on getting something functional first. Then you can iterate on it.
</p>

<p>
	That might mean you need to touch several files to get a feature working. That's fine!
	But it should be minimal and only what is required to get that bit working.
</p>

<p>
	Then in subsequent PRs, you iterate on the feature, clean up the code, and do refactors
	when needed. Focus on keeping the changes in the PR related, so that additional context isn't required.
</p>

<p>
	This will make it much easier for reviewers to approve, and get reviews done much faster!
</p>

<p>
	An additional benefit is if you get pulled off that feature for a higher priority task,
	the PRs you've already merged are still valid and working. Instead of coming back to a half-finished
	set of changes that are unused in the codebase, you have a solid foundation to build on or hand off
	to someone else.
</p>
