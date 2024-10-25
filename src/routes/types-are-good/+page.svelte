<h1>Types are Good</h1>

<p>
	For one reason or another, I was asked if I would like to read
	"Practical Object-Oriented Design in Ruby: An Agile Primer" by Sandi Metz.
</p>

<p>
	Well I'll be honest, I don't really read books. My brain just can't focus on prose and I forget
	what I read immediately.
</p>

<p>
	But I skimmed some parts and the section "Subverting Duck Types with Static Types" caught my eye.
	The author writes:
</p>

<blockquote>
	<p>The two remaining qualities are static typing’s compile time type checking and
	dynamic typing’s lack of a compile/make cycle. Static typing advocates assert that
	preventing unexpected type errors at runtime is so necessary and so valuable that its
	benefit trumps the greater programming efficiency that is gained by removing the
	compiler.
	<p>This argument rests on static typing’s premise that:
	<ul>
	<li> The compiler truly can save you from accidental type errors.
	<li> Without the compiler’s help, these type errors will occur.
	</ul>
	<p>If you have spent years programming in a statically typed language you may accept
	these assertions as gospel. However, dynamic typing is here to shake the foundations
	of your belief. To these arguments dynamic typing says “It can’t” and “They won’t.”
</blockquote>

<p>
	I've spent years in both static and dynamic languages. And in my experience, static typing
	<i>does</i> save you from accidental type errors. And without the compiler's help, these type
	errors <i>do</i> occur with some frequency!
</p>

<p>
	Just like in dynamic languages, you can do silly things like cast an object to something it's not.
	Or use a subvert the type system in other ways. But overall the compiler is a tool that helps you.
</p>

<p>
	The funny thing is, this being a classic book, I can see it was written in 2012. I would have
	agreed to a lot of this around that time! It was when I was going through a phase of thinking
	that C++ was bad and Python was amazing.
</p>

<p>
	This is because C++ is very much out to ruin your productivity:
</p>

<ul>
	<li>
		Separate headers and implementation files (.h and .cpp) is just a silly separation that makes it
		harder to keep things in your head, and in sync.
	</li>
	<li>
		Needing to remember rules about secret constructors (rule of 3, rule of 5, rule of 0).
	</li>
	<li>
		About 10 different ways to write constructors.
	</li>
	<li>
		Fiddling with libraries and build systems.
	</li>
	<li>
		I could go on...
	</li>
</ul>

<p>
	But in recent years, having used more modern statically typed languages, I've found that they
	are not out to ruin your productivity. They are out to help you write better code!
</p>

<p>
	One of the biggest things I miss when writing Ruby, it just having my IDE know everything about
	the types in my code. It's so nice to find all usages of a method, or jump to the definition of a class.
	I often feel in a large Ruby codebase, that you simply need to know everything about the code to be
	effective. And that's just not possible.
</p>

<p>
	With a Go project, I can drop into it and be effective immediately. I don't need to remember
	how things work, because the editor will know all the types, and I can lean on the compiler.
</p>

<p>
	And having worked in Ruby for a while, I've seen experienced developers commit typos which go on
	to cause production issues. This should never happen in 2024! To prevent this, a classic response
	is it should have been caught by a test. But that means we need 100% test coverage, which is
	difficult to achieve an maintain!
</p>

<p>
	A language with a good type system, and a codebase that uses types well, actually reduces the need
	for tests. The types are the tests! And they are always up to date, because the compiler will
	ensure that they are.
</p>

<p>
	If you imagine some contrived code like this:
</p>

<code>
func makeSprocket(metal Metal, chip Chip) Sprocket &#123;
	casing := processMetal(metal)
	programmedChip := programChip(chip)
	sprocket := assemble(casing, programmedChip)
	qualityCheck(sprocket)
	return sprocket
}
</code>

<p>
	With types there is no need to test this at the unit level. It's "glue code" which is held
	together by the types. If there's a higher level logic error, that's one thing. But the compiler
	ensures that the types are correct and there's no typos.
</p>

<p>
	In Ruby, a simple typo could ruin your day so you've got to make sure this type of code is
	tested too.
</p>

<p>
	In conclusion, while everyone is entitled to their own opinion and their own way of working,
	I think that types are objectively good. They help you write better code, and avoid simple typos,
	without 100% code coverage.
</p>

<style>
	blockquote {
		border-left: 2px solid #818080;
		padding-left: 1em;
		font-style: italic;
	}
	code {
		background: none;
		padding: 0.5em;
		border-radius: 0.5em;
		white-space: pre;
		width: 100%;
	}
</style>
