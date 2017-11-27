---
title: Why TDD is difficult
date: 2017-10-28 00:01:00
categories:
- web
---
# Preparation 

Comparing with the the way that develop a software without unit test, there are couple of extra topics on table when doing test driven development.

## Testing harness

Testing harness vary from techniques, because of that most of us will no long write test harness for ourselves in order to save effort and to utilize rich features already made by other people, we have to learn a unit test framework for each technique we touched.

I faced two problems after I stepped in JavaScript world, the first is what I touched is too much as a bundle including many technologies new to me. I spent considerable time on getting me clearer, however, when writing unit test for a software based on those, I have to understand what can I do with those dependencies. Another problem is that there are two sub types of the technologies, TypeScript for frontend and javascript for backend, they require different setup. For frontend, Angular already shipped with its own testing harness out of the box, but javascript does not.

## Dependencies

It is usually hard to manage dependencies will in unit tests, especially for those SUT which is not well designed. It took much time to get me comfortable with the way to have interfaces ready before I could write any implementation. I suppose the same issue will be there in any technology that new to me.

# Mental model

I am not willing to admit the fact that I go to production code without writing any unit test just because the effect of production code give me feedback I wanted for ensuring I am making progress.

Even I could realize that is not correct way, I can easily get in the state. I think the feedback I am expecting will be not that necessary to my brain when I am getting familiar with the technology. So I suppose after playing with Angular couple of months there is a timing that I could turn things on track.


## Fear

TDD forced us as developer to think carefully before we could write a single line of production code. But I have been working in casual way for long time, even I understand that the total effort of production code first approach will be higher that TDD approach, It turns into habitual old approach easily. I think the cause for this pattern should be fear, I was afraid of being working on writing tests even design the SUT for long time. 

I experienced couple of cases while writing unit tests, I found the design needs to be redone after some of unit tests and their production code ready, this was far from refactoring. On contrast, directly writing production code gave me the feeling that I will waste less when I fall into this kind of situation.

# Conclusion

I still believe that TDD is a better approach of software development than direct coding, or later unit tests approach, but TDD is feasible only following criteria met:

- The SUT is well designed, or could be well designed

- Developer needs to be familiar with the technology been used

- Test harness needs to be handy for developers.


