# Why problem sovling

Problem solving is a core skill for software engineers. Whether you are debugging something in a code base, or working through an interview challenge, you will need to have a plan in place for how to approach the problem. Without one, you may find yourself quickly getting stuck or distracted by unrelated issues. Worse - during an in-person interview, you might find it difficult to stay on track, focused and able to scope the problem. Having a well rehearsed process will help you come accross as confident and professional.  

The problem solving process is based on mathematician George Pólya's technique [read more](https://en.wikipedia.org/wiki/How_to_Solve_It)

*Most the details will be specific to whiteboarding problems, but the general technique can be used for any problem solving scenario*

> If this technique fails, Pólya advises "If you can't solve a problem, then there is an easier problem you can solve: find it." Or: "If you cannot solve the proposed problem, try to solve first some related problem. Could you imagine a more accessible related problem?" [src](https://en.wikipedia.org/wiki/How_to_Solve_It)

[Example whiteboard interview](https://www.youtube.com/watch?v=XKu_SEDAykw)

## Objectives

- Explain the four stages of the problem solving process
  - Ask one or more "What if" questions about edge cases
  - Propose 2 or more solutions
  - "Stake your claim" - choose one solution to recommend, along with why
  - Verbalize your solution before starting to write
    - Maybe mention 2 ways to solve the problem if and only if:
        - you can think of more than one solution
        - you can deliver on both
  - *Implementing:*
        - Identify sensible defaults for each primitive type
        - Identify which parts of a function are boilerplate and which require thought
        - Write the boilerplate code from memory
  - Use problem solving process during whiteboard interview

# Problem Solving Overview (memorize these steps!)

1. Understand the Problem
    * Identify Inputs and Outputs
    * Ask "What if" Questions
2. Devise a Plan
    * Come up with more than one possible solution
    * Choose a solution based on Performance, Maintainability and your Capability
3. Carry Out the Plan
    * Quickly dispense with boilerplate code
    * Write code 'outside in'
4. Look Back
    * Check for correctness - Test it out on the whiteboard
    * Look for opportunities to refactor
        * DRY [read more](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
        * SOLID [read more](https://en.wikipedia.org/wiki/SOLID)


# Step 1: Understand the problem

## Identify Inputs and Outputs

The first question / assumption you should verify when thinking about an algorithm problem is to figure out what the inputs and outputs are. Pay careful attention to the _type_ of the input and output (string, number, boolean etc...) - this will help determine what boilerplate code to write. Also pay attention to which inputs are _required_ and which are _optional_, and for optional ones, what their default values might be.

## Ask 'what-if' Questions

By the end of this article, you should be able to:

- Ask one or more "What if" questions about edge cases
- Propose 2 or more solutions
- "Stake your claim" - choose one solution to recommend, along with why

### Rationale

In the real world, problems often have ill-defined or complex inputs (data from a web form, data from files in the file system etc...), and knowing what to do with those inputs is key to being able to write high quality, robust software.

A _good_ whiteboard interviewer is looking for your problem solving skills.  

### How it works

In real life product managers / project managers may not give you all of the edge cases.  They'll rely on you to figure them out.  They'll give you a story like "users can sign in" and a wireframe and it's your job to say:

- "What happens when the email has a space in the beginning or end?  Do we trim that or just let it fail?"
- "What happens when the email has uppercase / lowercase letters?  Do we look for an exact match?"
- "Do we need to handle the case where someone is trying to gain access to the system and keeps trying different passwords for a user?  So.... should we lock people out after 3 attempts?"
- etc...

In an interview, often times interviewers will test this skill by not giving you the full story.  For example they might say: "build a chess board with such-and-such characteristics..." and you might ask "Will the chess board always be 8x8 or is that a parameter my function should take?"

## Ask a few "what if" questions

Here are a few things to look out for:

- Things being out of bounds of an array / input
- Missing parameters
- Things being out of order
- Things having mis-matched lengths
- Divide by zero errors

Generally speaking there won't be a minefield of edge cases, so don't take the whole interview worrying about this.  But _assume_ there is a hidden requirement until you've confirmed you are good.

### Propose a few solutions

Every time you ask "what happens when..." be prepared to follow up immediately with a few options, and then be able to choose one option and explain why.

For example:

**Interviewer**

> Write a function that takes a CSV string, parses it and returns an array of arrays.

**You**

_after confirming some sample inputs..._

>  What happens when I get a CSV row that's a different length?

**Interviewer**

> What do you think would be good?

**You**

> I suppose I could throw an error saying it's malformed.  I could also adjust the all rows to be the length of the longest, and fill the cells with null/empty values.  I could also just return an array of arrays of empty lengths.  I'd probably throw an error for the sake of time today, but do you have a strong preference?

**Interviewer**

> For now don't even worry about it.  Just assume you get well-formed input.

### Stake a claim

The example above demonstrates:

- showing multiple possibilities
- staking a claim with a reason
- doing nothing is always an option

### (sometimes) ask if there's anything you've missed

It's not a bad idea to quickly confirm if there's anything you've missed before writing code.

# Step Two: Devise a plan

## Come up with more than one possible solution

- Talk through broadly what you think the possible solutions
- Compare the time and space complexity of the solutions
- Make sure the interview OK's your verbal solution before you proceed to write on the whiteboard

*Resources for coming up with strategies:*

[Data Structure Approach](https://books.google.com/books?id=7tY5BAAAQBAJ&pg=PT222&lpg=PT222&dq=data+structure+brainstorm&source=bl&ots=ys1eMPMQps&sig=Jh2SPe_kzOtFF2Pnq5JBGmDE53s&hl=en&sa=X&ved=0ahUKEwj09ZWNst_OAhVO12MKHbObAkMQ6AEIPTAF#v=onepage&q=data%20structure%20brainstorm&f=false)

[Algorithms & Sample Problems](https://www.geeksforgeeks.org/fundamentals-of-algorithms/)

### Stuck?

 - Compute the problem by hand (forget about computers):
    - With the given input, did you arrive to the correct output? 
        - **Yes**: Look back at the steps you took...
            - Think about what things the computer/you have to keep track of
            - What are your instructions for the computer?
                - Keeping in mind that computers are really good at
                    - looping through things, keeping track of lists, item pairings, counting
                    - storing things in memory
                - How would you model the data you are working with in computer memory? [see](https://books.google.com/books?id=7tY5BAAAQBAJ&pg=PT222&lpg=PT222&dq=data+structure+brainstorm&source=bl&ots=ys1eMPMQps&sig=Jh2SPe_kzOtFF2Pnq5JBGmDE53s&hl=en&sa=X&ved=0ahUKEwj09ZWNst_OAhVO12MKHbObAkMQ6AEIPTAF#v=onepage&q=data%20structure%20brainstorm&f=false)
        - **No**: You should probably go back and review **Step 1: Understand the problem**
 - Try to solve a subset of the problem
 - Look for a simpler problem in the more complex problem, perhaps ignore certain edge cases
    - Sometimes interviewers will intentionally ask a hard question that has a much simpler version, if you can figure out the simpler version is solved, it might help you work on the harder version.


### Verbalizing your strategy

![](https://cft.vanderbilt.edu/wp-content/uploads/sites/59/Bloomtaxonomy.jpg)

A lot of people can memorize solutions to things like `sum` or memorize a solution to solving `isPalindrome` - that falls on the lower end of Bloom's Taxonomy.  Fewer people can analyze problems and propose multiple options, evaluate those options and then create novel solutions, and employers want to find and hire _those_ people.  

By being here you are honing those skills every day, choosing which technologies to use in projects, choosing which NPM packages to install, figuring out ways to get disparate elements like sockets and charts to work in the frameworks you are using, like Angular and React.  Employers unfortunately can't just pair with you or work with you on projects though, so they need to have some kind of a proxy, and that proxy is typically a whiteboard interview.

We train on this step so that they can see, in 20 minutes, what we see in you every day.

**How it works**

In real life, when you sit down to solve a problem you have a myriad of choices to make.  PostgreSQL or MySQL or Mongo?  Express or Koa?  Angular or React?  Each one has its merits and tradeoffs, and you have to both make a call, and also know why you are making that call in case situations change and you need to adapt to new requirements.  You'll often want to talk about these solutions before writing code, get feedback from the team, or at least have some sense of

In whiteboard interviews, there's a microcosm of this where you have to choose which approach you are going to take, and what data structures you are going to use. Is an accumulator? `for` loops or `while` loops?  `if` statements or `switch` statements?  Should you store data in Objects or Arrays?

**The technique**

Before you put the marker to the board, take a minute to describe what you are doing in one or two sentences.  That might look something like this:

*Interviewer*

> Write a function that takes a base number and an exponent and returns the base to that power.

*You* (_after checking inputs, asking what if questions etc..._)

> OK, so I could JavaScript's built-in Math.pow, or I could use a `for` loop or it could be solved using `reduce`.

*Interviewer*

Ah - Here at troll inc we don't use any methods on the Math object, so Math.pow is off limits.

*You*

OK - in that case I think I'll use a `for` loop with a basic accumulator pattern since I'm not confident I could get reduce correctly without being able to run it.  So I'll start with....

### Options

Often times there are some options available to you, such as:

- Storing data in arrays or objects
- Using builtin methods or not
- Using forEach, map, filter, reduce etc... or using for loops
- Using recursion or using loops
- Writing brute-force solutions with poor performance or writing more optimized solutions
- Writing one big function / object or splitting it into multiple

If you mention something you can't do make sure not to say "I could..." but instead say "it would be possible to...."

### Complete example so far

Here's an example script that covers everything you've learned up to this point:

*Interviewer*

> Write a function that takes in a paragraph of text and returns the number of words that are palindromes.

*You* (_show some inputs / outputs_)

>  Cool - OK.  So if I get "hello bob" I'd return 1, because there's just one palindrome.  But if I got "bob racecar" I'd return 2.

*You* (_ask some what if questions_)

> What should happen if I get "Hi Madam I'M Adam Smith", where "Madam I'M Adam" is a palindrome if you remove the spaces, punctuation etc...?

*Interviewer*

> What do you think?

*You* (_proposing some solutions, then staking a claim_)

> Well I could try to write an algorithm that removes all spaces and punctuation, then gets all substrings and sees if they are palindromes.  Or I could just split on spaces and see if a given word is a palindrome.  Hmmm... I think given the time constraints I'd go with just splitting on words - is that OK?

*Interviewer*

> That sounds great.  Go for it.

*You* (_stepping back, verbalizing your solution_)

> So I see two different parts to this problem.  One is figuring out if a word is a palindrome.  The other is splitting / looping / counting.  I could solve in this in one big function, or I could split it up into two functions.  I think I'll do that so I can focus separately on each problem.  So I'll start by just assuming that isPalindrome exists, and I'll write the outer function first, then I'll go and implement isPalindrome.

*You* (_writing some boilerplate sandwich code_)

> Alright, so I think I'll name this outer function palindromeCount and it takes a string, which I'll call `words`.  And it returns a count so I'll just initialize a count variable at the top here, and return it at the bottom.

------

After writing both functions you check both answers, and they hire you on the spot! Just kidding, lots of places have multiple levels of whiteboard interviews :)


# Step Three: Carry out the plan

**Rationale**

Whether you are writing on your own, pairing or at a whiteboard interview you can categorize the new lines of code you write into two categories:  **boilerplate code**, and **interesting code**.  The boilerplate code includes things like function/method/class definitions, opening and closing brackets, indentation etc...  Learning to separate boilerplate code from interesting code has two important benefits:

First, it helps you decrease your syntax errors.  If you make sure that you write the boilerplate code outside-in then you decrease the chances that you'll have syntax errors because you'll have already matched up brackets, indented things correctly.

Second, if you can fill in the boilerplate parts of your code _automatically_ then you free your brain up to focus on the upcoming _interesting_ code that you're about to write.

Whenever you are faced with a problem one of the first steps is likely to identify the [inputs and outputs](./Inputs and Outputs.md).  Next you'll probably figure out a decent name for your classes/methods/functions.  With this information, you have enough to write the following boilerplate code:

- The class/method/function definition with inputs
- Initializing the return value
- Returning the return value

Let's say you are tasked with writing a function that "takes an array of strings and returns a single string with the items separated by a space".

You already know a few things:

- Your function will have one parameter
- You have enough info to give your function a name

So right off the bat, without thinking about it, you can just write:

**Step 1: Function Definition Sandwich**

```js
function join(input) {
}
```

You also know that

- It will return something (as opposed to mutating something)
- The thing it returns will be of the type String

So you can add the following code:

**Step 2: Result Sandwich**

```js
function join(input) {
  let result = "";
  // your code goes here
  return result;
}
```

Notice how this makes a "sandwich" - you are writing the code from the outside-in.  First the function definition, then the `result` initialization and `return`.  This might not work 100% of the time, but it's a great start.

You also know you'll need to do something with input, so you'll probably have another "sandwich" (a `for` loop) that looks like this:

**Step 3: Input Iteration Sandwich**

```js
function join(input) {
  let result = "";
  for (var i = 0; i < input.length; i++) {
    // here you'll likely do something with input[i] AND result
  }
  return result;
}
```

**Review The Formula**

Without much thinking, you can follow this pattern for many kinds of accumulator problems:

1. Add a "sandwich" of the function definition
  - Identify inputs / outputs
  - Use problem description to come up with a name for the function
  - Use inputs to determine which parameters to add
  - Be sure to close the curly braces / parens correctly
1. Add a "sandwich" for a result variable
  - Declare / initialize a result
  - Use the _type_ of the output to determine the default value
  - Return the result
1. Add a "sandwich" for working with the input
  - Iterate over the input somehow (be sure to close the quotes / parens before adding stuff in the middle)
  - Note that you're likely to do something with each value in the iteration, as well as `result`

**Sensible Defaults**

A common pattern is to declare and accumulate into your `result` variable.  When you do this, it's often helpful to have a default value.  As you are thinking about boilerplate code, keep in mind the following default values for some of the builtin types in JavaScript:

| Output Type | Default Value     |
| :---------- | :-------------    |
| string      | `""`              |
| number      | `0`               |
| array       | `[]`              |
| object      | `{}`              |
| boolean     | `true` or `false` |

**Caveats**

Will this approach always work?  No.

Here are some places where your solution won't look identical to this:

- Not all inputs need to be iterated over
- Sometimes you don't actually need a `result` _variable_ (especially when you are programming in a functional style and just return a chained `map`, `filter`, `reduce` etc...)

# Step Four: Look Back

**Check for correctness - Test it out on the whiteboard**

**Look for opportunities to refactor**

- Improving the algorithm:
    - Can you make the time / space complexity better?
    - Have you dealt with enough edge cases?
    - What would happen if the input size increased beyond memory capacity?
- Improving readability and modification (may not be appropriate for whiteboarding specifically):
    - (DRY) [read more](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
    - (SOLID) [read more](https://en.wikipedia.org/wiki/SOLID)