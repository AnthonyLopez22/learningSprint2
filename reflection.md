# Reflection
 
## What I knew going in
 
I already knew what integer overflow was, but I was pretty rusty on the topic.
I understood the basic idea (that a number can get too big for its type) but I
couldn't really picture what was happening in my head. It was more of a
definition I'd memorized than something I actually visualized.
 
## What the app helped with
 
Building and using the visualization app really helped with that. Being able to see
the bits and watch the values change made the concept click in a way that just
reading about it never did. Seeing the signed and unsigned readouts disagree
once the top bit turns on, and watching a result wrap around when it didn't fit,
turned integer overflow from an abstract definition into something I could
actually see happening. I understand it better now than I did before.
 
## 
 
Being completly honest the AI carried me through most of the actual building of the app.
I described what the assignment needed and it generated the code. What I got the
most out of was how well it explained things along the way, instead of just
handing me a finished file, it walked through what integer overflow is, why the
bits behave the way they do, and what each part of the app was demonstrating.
So even though I didn't write most of the code myself, the acitivty helped better my understanding of integer overflow
 
## Connection to the rest of the class
 
Integer overflow and buffer overflow are basically the same kind of problem: data
going past the limits it's supposed to stay inside. The allocation example in
the app shows this when a size calculation overflows, the program
reserves a buffer that's way too small and then writes past the end of it, which
is a buffer overflow. So the integer overflow work connects straight into the
buffer overflow part of the assignment, and 