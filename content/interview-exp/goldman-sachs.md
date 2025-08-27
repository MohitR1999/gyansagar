---
title: Goldman Sachs
---
So for Goldman Sachs, a recruiter reached out to me for an Associate Role in their AWM (Asset and Wealth Management) team. Essentially it was similar to an SDE II role primarily focused on backend development with Java. The process was fairly straightforward, I applied for the role using the link provided by them, and it initiated the following chain of events:
### Online assessment I
I received an invite for a Hackerrank test, which consisted of 2 easy/medium level DSA problems. It got cleared fairly well.
### Online assessment II
Strangely, I received another invite for a Hackerrank test again, which consisted of 2 easy level DSA questions again, which I cleared as well.
### Interview round I
Now the first interview consisted of two DSA questions, which I'm linking here:
- [Longest substring with repeating characters](https://www.geeksforgeeks.org/dsa/largest-substring-with-same-characters/): This had a slight variation, in addition to the length I was also asked to find the starting index of the desired substring.
- [Median of two sorted arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/description/): Although this is a hard level problem on leetcode, I solved it with some basic techniques without much optimisation and it was accepted :)

After this round, I had 'bulk interviews', as the upcoming rounds were held on a single day, starting from 10:00 AM onwards. I had 3 rounds, each lasting for an hour, with breaks of approx 30 minutes between each of them.  
### Bulk interview round I (Data Structures)
This round consisted of coding as well as theoretical concepts. For this round I was asked two questions:
- [[file-diff|File diff]]: I had to implement a diffing system that generates differences between the contents of two files, pretty similar to how `git diff` works. Follow the link to read in detail
- Network connections: Given a number of computers and the connections between them, find out how many connections need to be modified in order to connect all the computers in a single network. I was able to solve this orally as I explained a simple approach: If we have `n` computers then we need atleast `n - 1` network connections. If that's satisfied, then just get the number of computers having degree less than `1`. For this approach, the interviewer was happy with my answer :)
After I solved these questions, I was asked some questions related to microservices and the differences between monolith and microservices based architecture
### Bulk interview round II (Software Engineering Practices)
This round revolved mostly around the projects that I had developed personally and professionally. I explained the projects that I had taken up during my career, the strategies of version control I used to follow at my workplace, and a few questions were asked related to microservices and scaling, both horizontal and vertical.
### Bulk interview round III (Software Design and Architecture)
This round also started off with explanations related to my projects and the workflows at my workplace, but finally ended up with the high level and low level design of a revenue ticketing system for a badminton tournament. I was able to draft a high level design of the system but wasn't able to properly explain the low level design, and hence the journey ended here :(
### Key takeaways
The data structures and algorithms part was pretty easy, but I needed to focus more on the HLD and LLD concepts. Thanks for reading :)
