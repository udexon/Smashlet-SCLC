 123 3 + /sdcard l: sp: c: _ c: swap: c: t:

123 5 + rl: /sdcard l: /sdcard/f2019 w:

Use t: to show result for each word.



Can an Android project or Java program be simplified like a Turtle Logo program?

We introduce Smashlet, a term that combines stack machine and shell, mimicking the architecture of a Forth program, as a simplified interface to an Android Java http Servlet and other high level programming languages. 

While the Logo Programming Language has been popularized as an educational tool to introduce programming to children, Forth, which we consider to be one of its close relatives, has maintained an image of niche programming language for geeks. 

We shall demonstrate that Smashlet, employing a similar syntax to Forth i.e. the reverse Polish notation, is powerful enough, or has sufficiently flexible syntactic structures, to represent and simplify a Java program or Android project, and in general, theoretically all known programming languages.

We call the process of mapping reverse Polish notation to a high level programming language the inverse shunting yard algorithm (ISYA), as it is a generalized inverse operation of Dijkstra's now legendary Shunting Yard Algorithm (DSYA). 



The complexity of software development tools has grown exponentially over the last few decades, as with the number of new programming languages. There does not seem to be an end to this ever growing trend. Perhaps there is still plenty of room for growth as programmers from third world countries continue to churn out profits for the silver gilded companies in the silicon valley, which in turn fuel such novel projects.

At present,  it is no longer humanly possible to manually maintain the files for a simple Hello World program for the Android environment or equivalent by a single programmer alone. The default practice would be to install the multi gigabyte Android SDK, download an Android project repository from GitHub or equivalent, fire up Android Studio, and hope the Gradle build does not break, which fortunately has stabilized tremendously over time. 

While GNU Forth for Android consumes a mere 70mb and makes assembly to GUI software development on the Android device itself possible, it suffers greatly from a lack of function libraries and awareness, which unfortunately is a chicken and egg dilemma.

Smashlet aims to break this deadlock, by utilizing the full suit of libraries in Java and other Programming Languages, while popularizing Forth via a less steep learning curve.

In this project, we introduce the following SMASH words ….

We use the term "SMASH words" as analogous to Forth words, which means function names in conventional Programming Languages. 

As SMASH is derived from stack machine and shell, Smashlet is an instance of SMASH, similar to Servlet in Java.  We will also introduce other terms such as SmashCloud, a cloud computing system to be constructed using SMASH.

Over the years, many programmers have ported Forth to various host programming languages, including Java. However, these projects remain the interests of a small audience as they were not aimed at integrating the function libraries of the host programming language, and the full implementation of Forth makes the port difficult to understand, and therefore extend.  These two concerns have been addressed in Smashlet. We aim to integrate Smashlet seamlessly with the host function libraries and provide a barebone skeletal framework of a Forth like architecture which can be understood and extended by novice programmers.

While the motivation of developing Smashlet may intrigue most readers, as it combines several extreme factors into one platform, we believe it is critical to introduce the reverse Polish notation, and the stack machine and graph theory concepts to a wider audience, much like how the spreadsheet software revolutionize computation skills of the masses. We believe Smashlet will lead towards a revolution in the education of programming and mathematics, as it can provide a bridge between computer algebra system and metaprogramming.

Leading towards a Revolution in the education of programming and mathematics, like spreadsheet changed computation skills of the masses? 


AndServer is a http Servlet written in Java for the Android environment. We created a stack machine shell (Smashlet) within its TestController.java. Its login.html sends user's inputs by Ajax to the function login() as parameters account and password. Smashlet splits the string account into space delimited tokens, pushes non-function words onto a stack, and calls a function on function words. 

Our first example is the following string:

123 3 + t:

Readers familiar with Forth will recognize that 123 and 3 are pushed onto the stack, and added up, and the result 126 is placed on the stack. t: is a Smashlet command that pops the top of stack (TOS) i.e. 126 and assigns it to the response string so that it will be displayed as output, as shown below:

{"data":" MR 126 S.size 0 tl 4 123 3 + t: Login successful.","errorCode":200,"isSuccess":true}

These operations are accomplished by iterating through the list of tokens in a while() loop, checking the tokens via a series of if … else if … statements, pushing the non function tokens onto the stack by default (the last operation).

In fact, this seemingly trivial loop is the most important workhorse in computer programming, being the heart of all stack machine based programming languages. Ruby, Python, Java, JavaScript, PHP, … Even non sm Languages can be translated to sm easily, plus major microprocessors have stack engine. 

We have demonstrated how a new function word t: can be created and mapped to http response. This example shows how Smashlet can be integrated seamlessly into existing function libraries of the host programming language, a critical feature that past Forth porting projects failed to emphasize. 

/sdcard l: t:

l: is mapped to listFiles() which returns a list files in a given directory. The file names listed are pushed onto the stack. t: pops the last file name and output it as http response. 

{"data":" MR John_Denver_-_Take_Me_Home_Country_Roads_Official_Audio-1vrEljMfXYo.mp4 S.size 19 tl 3 /sdcard l: t: Login successful.","errorCode":200,"isSuccess":true}

/sdcard/d_1 File: rl: t:

File: opens a file for reading. rl: reads one line from the opened file.

{"data":" MR {\"s\":\"190601060445522798\",\"sn\":0,\"a\":\"setting_begin\",\"p\":\"zyeid=3dcf7a115e8e4ec48a625670842a2a02&usr=r020784677&rgt=7&p1=XPGk%2B7eB1bQDAFxRdN1B7pfr&pc=10&p2=120152&p3=302044&p4=501644&p5=19&p6=&p7=CJAIfEcDJHBBfDaF&p9=50212&p12=&p16=CPH1803&p21=31303&p22=8.1.0\",\"d\":1559340284356} S.size 0 tl 4 /sdcard/d_1 File: rl: t: Login successful.","errorCode":200,"isSuccess":true}


/sdcard/d_1 File: rl: /sdcard/f2019 w:

w: pops the top of stack, opens the file for writing, then pops and writes the subsequent top of stack to the opened file. In this case, the contents written was the line read by rl:


We have chosen several fundamental input output functions in Java as examples to demonstrate the utility of Smashlet. Most importantly, we demonstrate how effortless it is to add Smashlet function words to call existing functions supported by the host programming language, a critical feature overlooked by previous Forth projects.

The colon suffix in function words was a convention we adopted in the implementation of Smashlet on PHP and JavaScript, initially to allow us to distinguish function words from non-function words, and map them to host functions via eval(). The colon suffix also serves to distinguish Smashlet words from Forth words.

Veteran Java programmers should immediately notice that by adding reflection and annotation functions to Smashlet, we will be able to access the complete repertoire of Java functions.

This opens up some interesting and significant questions concerning program compilation, interpreter and execution. 

Question: Is a Forth program running in a C ...

Python interpreter is a compiled program. Python programs run within a Python interpreter.

Compiled or interpreter programs, modified during run time? 
 
Metaprograms? A program that is changed during execution? 

Interactive execution?

Change a program?

All program development from Java to Forth are interactive, only difference is frequency of change, size of code, number of people participating in development? 

Free software, open source enables creation of large number of APIs. Cloud based, social networks apps.  

Smashlet reduces footprint of software development tools. Very important in mobile era. Old tools were pre mobile era. 

Software development is a continuous process of improvement involving feedback from users as well as programmers. By enabling large number of users to be involved in software development, some users may acquire the necessary technical skills to complement existing programmers, and this number could be significant. Smashlet is a breakthrough in footprint, immediacy, live test, learn by examples, compared to conventional software development model. 

Call this inverse shunting yard algorithm? 

Simplifying programming languages. Use this as main selling point for Smashlet.

Patience of modern readers is only long enough for an interesting introduction.




Android or equivalent modern Programming environment have become too complicated. How to simplify them? Systematically? 

Show RPN simplifies Java, then other configuration files in Android. 

To simplify an Android project or Java program, many readers would know what it means, but not how to do it. As simplify here involves metaprogramming. 


Can an Android project or Java program be simplified like a Turtle Logo program?

Perhaps most readers understand the question but would be amazed by its answer.

