Brian's old Dockerfiles!

**Stop Press**

I've been working with Docker for a couple of years now, but I consider most of this repo "useful history".

Here is my collection of Docker files.

Working for a large organisation that probably won't use Docker Hub, my focus with these Dockerfiles has been to build a collection of applications, as neatly tiered as I can, that will enable me to populate a private registry whose prototype is currently (Happy New 2015, everyone!) running in a KVM virtual machine on my laptop.

I'm very much open to (objective) feedback on how I structure my layers of images through these Dockerfiles - I'm still learning how best to use Docker.

Being a public Git repository, I'm also happy for you to learn from my efforts if you can. I'm a fan of attribution, so where I've learnt significant things or even blatantly copy/pasted code I tend to comment mine with a link back to the original author - if I forget you, let me know and I'll fix it.

My intent is this:

1)  A set of base, out-of-the-box installed Ubuntu Server images.
2)  A layer containing some extra tools that a large number of apps will find useful (primarily in a non-prod environment for now).
3a) A further set of layers containing bases such as a JDK, Python, Nodejs or other application platforms.
3b) A further set of layers with actual applications on top of the application platforms.
4)  A top pair of layers for data containers (with VOLUMEs) and the runtime (with ENTRYPOINTs).

3a and 3b are currently anywhere between one and three layers thick.

To make life easier, I've also included some Dockerfile snippets I've learnt...

Enjoy!

B
