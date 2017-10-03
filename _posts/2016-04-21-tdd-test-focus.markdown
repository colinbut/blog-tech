---
layout: post
title:  "TDD or Not - Test Focus (Test as you develop)"
date:   2016-04-21 10:00:08
categories: Lorem
comments: true
---
I want to share my opinion, thoughts, and experiences on TDD practices against not doing TDD at all. In addition, also explore what i see are other alternatives.

## A little background of TDD

TDD which stands for Test Driven Development is a well known software design philosophy within Agile methodologies whereby developers write tests before they write any code. For me, tests can be any kind of tests like Unit tests or Integration tests. The idea of this whole philosophy is to use these 'tests' to derive your design of the solution to the problem you are trying to solve.

You start of with writing a unit test with the appropriate test process (assertions etc...). The unit test code obviously doesn't compile because the code you are trying to test doesn't exist yet. This is normal and expected. So the tests fails. You then write your code (method under test) bit by bit to first make the unit test code compile. It compiles but the tests still fails. This is also expected. Now you gradually write more code or tweak your existing code to make the unit test pass. As part of this process you will probably find that the method under test is not what you initially intended to do and so you begin to refactor and make the necessary improvements according to good object-oriented design principles i.e. you refactor methods, add more classes, compose or deconstruct certain code. You gradually evolve your unit test too to make your tests pass. At the end of this exercise, you will hopefully have a piece of well written code along with a good set of tests to backup your code or to prove your code works as expected.

## My experiences with TDD

To date, i have worked in a number of companies and have participated in a variety of different software projects. 
To me there are many ways to do TDD. Some of the ways i have done in the past are considered by the TDD purists to be not really TDD. In my opinion, TDD is very broad, there is what i deemed to be traditional TDD and other what i see as more modern TDD practices to be other flavours or variation of TDD.

I have worked in software teams where we practice traditional TDD where we are really strict and serious about the way we develop our code, the way we write our tests. 

I have also worked in teams where we don't practice TDD at all, where we write a lot of application code, get it working, and then write our unit tests or integration tests afterward. Personally, my opinion is that this is an anti-agile approach of doing things where it is more traditional waterfall style approach. It is also an inefficient approach to software development and could yet develop into a dangerous precedence. Most of the times, due to time constraints imposed on delivering business functionality the writing of tests are timeboxed and thus sometimes none are written at all. Because we have made the code work we say "it works" and sometimes we say "tests are not important" and so we move on to finish stuff as quickly as possible. This is not just anti-agile approach, it is not professional software development. It is amateur.

I have also worked in teams where we do something in between what i've described in above two examples. 

## Test Focus

I really believe in TDD. But what i really believe in is "Test Focus". You could argue it is same as being test driven. But that's not all.
At the end of the day, i feel you should have tests. No matter what way you get there, there should be tests. It doesn't matter if you write tests before hand or after you've written all the code, or while you write your code. There must be tests. I prefer to have the best compromise of writing the tests are you develop your code because that is what i believe in - "Test as you develop". 
That is my bottom line. I personally cannot stand writing code without any tests at all. 

## Conclusion

Ultimately i feel, it all boils down to how well you believe in the philosophy. Let me give an analogy. For the frantic football fans out there, they would understand where i'm coming from. In football, there are more than one way to ‘play’ whether its long ball or tika-taka the ultimate goal is the same, you want to get the ball into opposition goal to win the match.

