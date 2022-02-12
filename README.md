# Revival

Main repository for the HTS revival planning. Actual code will likely live in many different repositories.

# Vague immediate goals

 - lower admin maintenance
 - lower moderator maintenance
 - modernize/revive the website

---

## Lower admin maintenance

Administrators must do the following (in order?):
 - keep user data safe
 - keep HTS alive
 - keep hacker spirit alive
 - pay all the bills
 - try not to die themselves

### problem

Since keeping user data safe is often at odds of using invasive ads, admins end up paying the majority of bills using their own money.  
So admins tend to have demanding 'real life' jobs to pay for it.

Keeping user data safe makes delegating hard, we cannot allow a helpful staff member to steal and publish all user data on the pirate bay.

We are currently failing to achieve our other goals so some change is required.

### solution

Modernizing our infrastructure, from a traditional self hosted approach, to the 'cloud' can help reduce admin overhead.

Ideally moving to an [infrastructure as code](https://en.wikipedia.org/wiki/Infrastructure_as_code) approach would make maintenance and documentation a lot easier.  Furthermore it would allow community members to improve infrastructure via a pull request to further decrease load on administrators.

Using the public cloud is not cheaper than doing it yourself, but will be sufficient for the short term and to prove out the concept. Long term we would probably move to a private or hybrid cloud approach.

---

## lower moderator maintenance

The current website has a lot of things that require moderation, and frankly isn't being done.

- discord
- irc
- user comments on articles, news, user profiles
- article submissions
- forums

We can solve this by focussing on the areas volunteers actually enjoy moderating.

### community

Users can interact in a lot of places and ways on the modern web,  
removing all functionality except irc and discord will not be a big loss to anyone.

Focussing mainly on [discord](https://discord.gg/hts) as the central hub for the HTS community,  
and keeping irc as a nice place for oldies to hang without bothering the kids.

### user generated content

A lot of our articles aren't that high quality, people these days can publish on a blog or medium for free so there is no more point in us offering this service.

In the medium term, articles could be converted from bbcode to markdown and posted in a git repository.  
Stripping out low quality content, allowing people to improve on the same articles, and moving moderation to github pull requests.

From an infrastructure point of view, it reduces required resources and lowers the attack surface to host these as static content instead of using some custom CMS and database.

Forums were integrated in the site login system which just makes it a nightmare to maintain, they are only a source of spam now.  
In the long term we could put up a read only archive for historical reasons.

---

## modernize/revive the website

### problems

The website is old, the code is old, its ugly. Take my word for it when I say that reading its source may in fact lead to severe mental issues.


Past attempts at revival have all failed for numerous reasons. The most technically relevant **problems**:
 - reading old code will make your brain deteriorate
 - there is no upgrade path for the old code at all
 - the amount of work required to keep all functionality is so large and daunting, no one in their right mind wants to attempt it
 - the amount of work required to keep it compatible with the longterm hopes and dreams of the HTS project is also so large and daunting, no one in their right mind wants to attempt it
 - we are 100% volunteer based

### solution

I propose we avoid those technical problems by **severely limiting** the scope and focussing on what we're good at:
- missions: literally the name of the website
- strong community
- anti capitalist propaganda: no one else will let you hack nazi's

We can expand on it after everything is up and running, this project is **only** about what is needed **now**.

By ditching all user generated content on the website in the short term, and moving it to git repos in the long term, we don't need to code anything for the community part.

Our news and info pages are also static, if we can use a static site generator to build from a specific repo it will be really easy to maintain and take almost no resources to host.  

We only need to create the following capabilities:
- create/edit/recover/delete users
- missions: keep old missions functional, display completed missions on profiles, update completed missions when an old mission is completed

For the frontend, my own experience is mostly with angular, but that isn't very suitable for large amounts of static content.
There are however several frameworks available for generating static websites intermixed with react.


## Decisions needed

### Frontend
We should use some sort of static site generator and inject the very few dynamic pieces of information using javascript.

- What framework to use
- Who is going to work on it

### Backend
We'll need some sort of API so we can create/edit/view/delete users. We can have the frontend fetch all that and avoid needing to pre-render any pages at all.

Likely we'll host the missions in a separate container, and they will need some sort of private API to mark missions as completed.

- What language
- What framework
- Who is going to work on what

### Infrastructure

Where are we going to put all this stuff? Right now digital ocean or scaleway's hosted kubernetes stuff is looking most promising.

- which hosting
- which tools to use for 'infrastructure as code' (terraform?)
- Who is going to work on it
