# Write Free Science Books to Get Famous Website

Dream: live in a world where you can learn mathematics, physics, chemistry, biology and engineering for free whenever they want from perfect open source books made for free by people who want to get famous to get better paying jobs.

Desired society impact: crush the current grossly inneficient educational system, replace today's students + teachers + researchers with unified "online content creators / consumers". Gamify them, and pay the best creators so they can work it full time, until some company hires for more them since they are so provenly good.

This is just a wacky project idea right now.

Method: a crash between:

- Stack Overflow gamification
- GitHub-like pull requests. Not anyone can edit anything like Wikipedia madness, but you *can* make your own copy (fork), and a precise a suggestion.
- Wikipedia. Imagine if you could link up-votable application examples to the useless page of a Mathematics theorem, and add you own completely different versions of articles explaining them in your own perfect manner.
- page rank-like algorithm for user reputation, including a per-tag reputation (which user knows more about mathematics?) and content recommendation (what are the best articles about a given subject?)

Very early stage prototype(s):

- <https://github.com/cirosantilli/free-books-django-raw>

Why you can't make money with this website right now:

- society has huge inertia
- Stack Overflow is good enough (?), even though it could be so much better

## Intro

Consider a [Stack-Overflow]()-like Q&A website:

- there are questions and answers
- questions have tags, e.g. programming languages like `C`, `C++`, `Java`
- users have a reputation measure. If you upvote someone's question or answer, his reputation increases. You need 15 reputation to upvote someone.

But Stack Overflow's reputation system sucks because:

- if the living ultimate god of `C++` upvotes you, you get `10` reputation
- if the first-day newb of `Java` upvotes you, you also get `10` reputation

We want to improve Stack Overflow's simplistic linear reputation system to determine who is the user who knows the most about a given tag.

Fundamental requirement: a Google PageRank-like algorithm (Eigenvalue based) such that:

-   everyone has one reputation per tag
-   if someone with high rep on a given tag upvotes you, you get a lot of reputation on that tag. More than you would get from someone with low reputation on that tag.

Optional but very desirable requirements:

-   users can upvote tags on a given question to say: "I agree that this question deserves this tag".

    The vote of users with higher rep on the tag should count more.

-   each time you upvote the same given person, it has less positive impact on his reputation for that tag.

    This would counter voting fraud, e.g. of close groups of friends which upvote each other a lot.

-   people can post articles, not just questions. A question is just a topic definition for an article. 

Another problem this would solve: multiple site split silliness: <http://meta.stackoverflow.com/questions/271989/does-it-pay-to-spin-off-sites> Since there is no human moderation, only algorithms, splitting websites makes no sense.

## Extra problems

### Tag duplicates

How to mark tags `java` and `Java` as being duplicates without moderators?

Possible solution: everyone can mark tags as duplicate.

Once you mark tags as duplicate, if you search for one, you will see both.

Then we need some algorithms that fuzilly joins all subjects that many people said are the same.

This is one of Quora's focus: <https://data.quora.com/First-Quora-Dataset-Release-Question-Pairs>

### Original research vs explanations

How to determine if something is "original research" or not?

E.g.: a genius discovers something and publishes it really badly explained.

Someone less intelligent comes, explains it better, and gets widely read.

Or someone who just posts a bunch of links to good sources.

### Post age

Post metrics on Stack Overflow also suck: the post with most upvotes goes up and that is it.

It would be cool to give a boost to recent posts that got lots of upvotes.

They can't beat the older ones in total upvotes, but the upvote rate is a strong indicator of quality.

Even better, would be to consider how many times users view EACH post in a single page, with some JS black magic. With that, we can just use the Wilso score interval https://en.wikipedia.org/wiki/Binomial_proportion_confidence_interval#Wilson_score_interval as mentioned at: https://www.evanmiller.org/how-not-to-sort-by-average-rating.html

SO threads:

- http://meta.stackexchange.com/questions/125455/sorting-new-answers-to-old-questions?rq=1
- http://meta.stackexchange.com/questions/6662/how-to-give-some-boost-to-some-really-good-answers-that-arrive-late?rq=1
- http://meta.stackexchange.com/questions/15805/how-can-we-make-good-answers-to-old-questions-float-to-the-top
- http://meta.stackoverflow.com/questions/272570/how-to-deal-with-hugely-upvoted-bad-and-outdated-answers

Non SO literature:

- https://www.quora.com/When-Google-indexes-a-page-does-it-consider-that-pages-creation-date-when-it-comes-to-PR-computation

### User trusts user

It would be cool for a user to say: I trust this other user on given tags / all tags.

Maybe this is required. E.g., given a real network, a bot network could make an exact copy of it, and that should have the same reputation as the real one.

Such relations make per-user score of other users / posts even more important.

### Per user score of all other users

Rate how much one user likes other users based on his actions.

E.g.: someone who only upvotes C questions will give score 0 for someone with only Java questions.

### Pull request disagreements

What happens if:

- the writter of an answer dies, and someone makes a great pull request to his answer with 1M upvotes?
- 50% of users agree with a pull request, 50% don't?

Possible solution:

- next to each answer, have a list of forks
- everyone can mark an answer as the "best version" or just upvote the pull requests

## Testing: a difficulty

While it is possible to download all public data from Stack overflow in dumps, this algorithms would need private information like who upvoted what.

So generating meaningful test data would be a problem in itself.

## Research

- http://meta.stackexchange.com/questions/98141/ranking-users-similar-to-page-rank
- http://meta.stackexchange.com/questions/64938/doesnt-science-have-a-better-reputation-system-than-stack-overflow
- http://meta.stackexchange.com/questions/103735/modified-h-index-for-questions-and-answers

Software:

-   http://www.bibsonomy.org/
    - https://bitbucket.org/bibsonomy/bibsonomy
    - http://www2007.org/workshops/paper_25.pdf
-   https://github.com/networkx/networkx Python, does a lot of other graph things

StackApps:

- http://stackapps.com/questions/6520/skillrep-experiment-in-computing-a-skill-focused-reputation
- http://stackapps.com/questions/6298/stackrating-tracks-skill-of-stack-overflow-users

General reputation systems:

- https://en.wikipedia.org/wiki/Reputation_system
- https://en.wikipedia.org/wiki/Bibliometrics
- https://en.wikipedia.org/wiki/Network_theory#Link_analysis

Concept maps:

- http://conceptnet5.media.mit.edu/

Social network:

-   <https://en.wikipedia.org/wiki/Tsū_(social_network)>
    - <http://www.tsu.co/>
    - shares 90% ad revenue with content creators
-   <http://www.synereo.com/whitepapers/synereo.pdf#subsection.2.2.2> distributed social network, seems to use quality metrics to determine how much content will be hosted from each person?
    - paper <http://www.synereo.com/whitepapers/synereo.pdf#subsection.2.2.2>
    - TODO open source? <https://github.com/synereo> Where is the source?
    - Where does their money come from? When will it launch?
- SocialSwarm
- Diaspora
- https://github.com/debiki/ed-server no tags? Best go up focus.

### PageRank

Implementations:

-   https://github.com/louridas/pagerank C++
-   https://github.com/dcadenas/rankable_graph Ruby
-   https://github.com/dcadenas/pagerank/ Go, port of rankable_graph
-   https://github.com/frankmcsherry/pagerank
-   https://en.wikipedia.org/wiki/EigenTrust

Mathematical problem: make a stochastic matrix graph where each entry equals:

- `(1 / n_links)` if there is a link going out
- `0` otherwise

Now calculate the steady state of the Markov process: <https://en.wikipedia.org/wiki/Markov_chain#Steady-state_analysis_and_limiting_distributions> which is the same as calculating the eigenvector.

Convergence of simple interactive algorithm: stochastic link matrix M iff M is both: (TODO proof):

-   irreducible: definition: no strongly connected components smaller than the entire matrix. You can get from any place to any place.

    Or in other words, there are no sets of pages from which the surfer cannot escape. One example of this is a page without any outgoing links.

    http://drops.dagstuhl.de/volltexte/2007/1072/pdf/07071.VignaSebastiano.Paper.1072.pdf the damping factor can be interpreted as a probability that the random surfer will jump to a random page. It solves in particular the problem if the page has no outgoing links.

    If is the same as adding a `dumping_factor / total_n_pages` to every element of he matrix, and multiplying the actual matrix by `1 - damping_factor`.

    1 is always the largest eigenvalue http://math.stackexchange.com/questions/40320/proof-that-the-largest-eigenvalue-of-a-stochastic-matrix-is-1 wit Looks like 1 is the only eigenvalue: <http://math.stackexchange.com/questions/351142/why-markov-matrices-always-have-1-as-an-eigenvalue>

    Existence of a single largest real eigenvalue is guaranteed by https://en.wikipedia.org/wiki/Perron–Frobenius_theorem

-   aperiodic <http://math.stackexchange.com/questions/112151/what-values-makes-this-markov-chain-aperiodic>

    Aperiodicity is likely for the huge graph of the web, so we forget about it.

Proposal to use it on Stack Overflow:

- http://meta.stackexchange.com/questions/28874/applying-pagerank-like-algorithm-to-stack-overflow-votes

PageRank tutorials and papers:

- http://www.cs.princeton.edu/~chazelle/courses/BIB/pagerank.htm

PageRank alternatives:

- https://en.wikipedia.org/wiki/TrustRank Starts from a set of trusted pages. Interesting, as that could be pages / users which were upvoted.
- https://en.wikipedia.org/wiki/HITS_algorithm separates author from referrer, which could be interesting to give more reputation to those who actually write material.
- https://www.nayuki.io/page/computing-wikipedias-internal-pageranks Wikipedia internal PageRanks, using a simple proprietary open-source Java PageRank implementation.

PageRank variants:

-   topic sensitive TODO understand better. Seems to modify the damping biasing to favour some pre-determined pages, on the paper based on DMOZ human consensus classification (no upvotes, just politics)
    - we could use something like that but based on votes of a given user, but it could be too expensive
    - http://www-cs-students.stanford.edu/~taherh/papers/topic-sensitive-pagerank.pdf Contains a great explanation of PageRank.
    - http://drops.dagstuhl.de/volltexte/2007/1072/pdf/07071.VignaSebastiano.Paper.1072.pdf
    - Seems to use an arbitrary previously fixed number of topics?

## Algorithm possibilities

The most obvious possibility is to reduce the problem to pagerank.

If we forget tags to simplify, we could do a bipartite authors / posts graph:

- each post and user is node in one side of the bipartite graph
- if userN upvotes postN, add a link from userN to postN
- link postN to it's author userN

To consider tags without weight, in addition:

- each user is represented by one node per tag userN-tagM
- if userN upvotes postN, add a link from userN-tagM to postN if postN is tagged with tagM
- link from postN to each userN-tagM where userN is the autor and tagM a tag of the post

## Tag hierarchy extraction

We could be able to deduce that `animal` includes `dog`, is a lot of articles tagged as 

- Tibeli 2013 http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0084133

## Websites with tag votes by any user

- Flickr 2016 only photo author can add tags
- Delicious TODO down?

## Datasets

- https://en.wikipedia.org/wiki/DMOZ http://www.dmoz.org/ http://c2.com/cgi/wiki?OpenDirectoryProject

## Business model

### Consulting

Start with consulting for universities to get some cash flowing.

Help teachers create perfect courses.

At the same time, develop the website, and use the generated content to bootstrap it.

Choose a domain of knowledge, generate perfect courses for it, and find all teachers of the domain in the world who are teaching that and help them out.

Then expand out to other domains.

TODO: which domain of knowledge should we go for? The more precise the better.

- maths is perfect because it "never" changes. But does not make money.
- computer science might be good, e.g. machine learning.

### Knowledge market

If enough people use it, we can let people sell courses through us, to become the YouTube of courses.

Teachers have the incentive of making open source to get more students.

Students pay when they want help to learn something.

### Who to propose this to

<https://catalogue.polytechnique.fr/cours.php?id=2913>

<http://psc.polytechnique.fr/>

### Ads

Possibly shared with top content producers, like Tsu.

Plus a paid option to opt out of ads.

But this is what YouTube does with videos, and it only pays for a ton of views...
