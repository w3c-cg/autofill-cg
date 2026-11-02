Attendees:
Stephen McGruer (Google)
Yoav Weiss (Shopify)
Darwin Yang (Google)
Cathy Li (Meta)
Rick Byers (Google)
Johnny Stenback (Google)

Notes:
Yoav: Hey folks; no slides, but:
A year ago, we did a breakout at TPAC 2025 related to autofill
It turned into a nice therapy session for us all
We concluded that we should start a CG
In the year since, we've had roughly monthly calls (somewhat inconsistent)
We've pushed a few proposals in the CG, mainly autofill-event
Ran a Chrome OT with Shopify
Saw success in reduction in edits-after-autofill in non-US regions
Also discussed some other proposals around extensions (didPerformAutofill API proposal), had general conversations about expanding the semantics of autocomplete to try to minimize cases where developers and autofill providers clash
Find cases where we could provide semantics, e.g. "someone elses address"
In terms of participants
Mostly Shopify, Chrome, lot of other Autofill providers (mostly extension based)
Unfortunately not other browsers yet :(
Would love more developers as well outside of just Shopify
Goal of todays session:
Provide this update
Hear from y'all - what should we push further in the Autofill CG?
Rick: Can you give us an update on the autofill-event, I'm just out of the loop
Yoav: Outside of the OT, next steps are more testing infrastructure work, also dovetails into better WebDriver for autofill in general
The event itself can also help testing
Yoav: Spec currently includes WebDriver BiDi, need to fully land it, make sure it enables full testing, etc.
Yoav: Then we'll send an I2S
Yoav: Shopify think that this is sufficient value to justify a double implementation (autofill-event for browsers that support it, honey trap where they don't)
Yoav: Have also talked to other large consumers of forms, not seen a lot of follow up there unfortunately.
Rick: I know at Shopify a lot of front-end dev is agentic these days. Do you know if anyone is asking your agents to profile/quantify the types of bugs that tend to get introduced, and what the root source of bugs tends to be?
In my own experience, its things that aren't testable, and Autofill feels like a classic example of that.
Yoav: Good question, I don't have a good answer, but I think making it testable across engines and Autofill providers matters a lot. Not just for agentic but also for humans.
Cathy: We've had to do some work in making sure that our IAB (WebView based) more standalone in order to let agents test the WebView.
Also had to split out form detection from filling more, and then we hook up an LLM, go to the most popular sites that people visit, and ask LLM "did autofill look like it did something correct" and analyze the failures
As we move to agentic use-cases, autofill becomes more important as it really helps agents.
Stephen: does that change the priority of custom select elements?
Cathy: We're currently looking at radio boxes and checkboxes that Chrome removed in August
(Stephen ducks ;))
Cathy: We plan to now rebuild it and upstream 
Cathy: Custom select is still a problem
Stephen: Yeah, I dont know if selectmenu got much adoption :(
Johnny: On the testability front, is it just work, or any roadblocks there?
Yoav: Mostly work; we have a spec-local WebDriver BiDi extensions (tried to upstream and main WebDriver group wasn't interested). For Chromium thats not an issue, but maybe will be for other browsers/etc.
Stephen: I think the elephant in the room there is still that browser vendors (and TAG?) are not aligned on whether autofill is something that can be even slightly spec'd beyond autocomplete attributes
Yoav: I think TAG was mixed
Yoav: I think parts of Autofill are browser features and parts of Autofill is very web exposed
Stephen: 100%, and I want the web-exposed parts to be spec'd. Autofill has a HUGE impact on the web and web developers, and the fact that it's not spec'd is weird.
Yoav: One interesting thing; imagine we do get WebDriver coverage on all engines, we're still missing other autofill providers
Yoav: Knowing what happens there requires some sort of user data from the wild, but those extensions are not identifying themselves in order for us to know that some specific extension is broken in the latest version.
Stephen: Will the WebDriver testing API support extension based providers?
Benjamin (1Password): We definitely do use WebDriver for testing this, it generally works, but there are some limitations (triggering the pop-up in a trustable way)
[Editor; I think I have this wrong, seems to be about in real user cases not WebDriver? Not sure]
We can open the extension page, but from a user perpsective it would be wonderful to be able to click that button
???: Is there not now an API for open popup, at least in Chromium?
Benjamin: Yes, but thats very recent.
Benjamin: The Web Platform Test group now also includes extensions, and that now is across engines.
Yoav: Going back to measuring in the field, we now know that if we don't get an autofill-event in Chromium but something autofill-like happens, we can conclude that an autofill provider exists
Benjamin: Yeah there's a problem there where we don't want to expose information.
Yoav: I agree, but an aggregate data ability might be very useful here…
Christian (1Password): I'm curious, what is useful from credential provider extensions here?
Yoav: Just to be able to split my users on what autofill provider, so that I could know that for example users with a particular provider have a worse conversion rate and so there's a bug to fix.
Totally get that from the privacy perspective
Christian: We do offer publicly documented 1Password specific attributes that make us ignore it.
Yoav: They could put your attribute on one input field, the bitwarden one on another, etc
Christian: In general we've not seen people use them outside of e.g. banks
Christian: wrt fingerprinting this stuff; for extensions that inject content scripts can websites not already detect that there is code from extension origin?
Rick: Yes if its in the same world
Christian: Ours have to be, to touch the form. So isn't this data there already? So maybe we should just provide it in a more structured way.
Rick: +1, real fingerprints are absolutely already using that. They're looking at extension IDs to fingerprint users.
Rick: This is the same tension as the user agent string; there is value to providing who you specifically are
Maybe a user agent client hints ability for extensions to just declare it?
???: In talking about fingerprinting you're talking about user session data, would aggregate reporting still be helpful?
Yoav: Yes, but the browser needs to be aware of what we consider success.
Christian: For the apple folks; Safari randomizes extension IDs frequently, I assume this fingerprinting part doesn't work there?
Ricky: I am not sure
???: I believe this is the case
Ricky: So in Chromium the origins of the injected scripts aren't randomized?
Rick: Correct
Ricky: That is unfortunate, it's definitely possible. I assume that there's a compat cliff, but that would be very good to do.
Rick: If an extension is injecting some script, code in the origin of that script can get the contents, hash it, etc. I don't think they can hide.
So the determined fingerprinters still have the information, but the good folks don't invest that much and so they don't get that information.
Yoav: +1, plus I actually have privacy people who won't approve just fingerprinting it
Rick: Maybe the autofill event should come with an optional ID string, extensions can exclude or lie about it
Yoav: No extension autofill provider supports the event right now unfortunately.
Ben: We looked at it, not outside the realm of possibility but low priority for us.
Ben: Standardization is close to our hearts; the range of expressions of even just [editor; missed this], we get that the autofill-event is a way to combat it, but why don't we all use the same value
Ben: Like to know that they want 2-letter country code vs Canada etc
Yoav: Yeah so previously we realised that its boiling the ocean to do the entire thing, but maybe you're just suggesting new autocomplete attributes?
(we all share pain with mistakes web developers make :( )
Yoav: So yeah if web developers are not doing it right then adding a new standard doesn't help (https://xkcd.com/927/), but maybe we could combine it with developer tooling/reporting?
Johnny: On the metrics question, we could collect this at the browser level, and we could slice it internally and maybe share some sort of autofill quality metric sliced on provider.
Stephen: probably technically possible, need to do heuristics to detect if an extension did the fill, then we can use our own metrics and then turn it into CRUX or similar?
Yoav: Solves the 'you broke autofill last week/month', not as good as "something just broke"
???: Can you define is broke? is it just did-edit-after-fill?
Yoav: That's the metric we saw change, we could do other metrics.
Ben: One thing thats complicated is that this is user-entered, and sometimes they provide data that doesn't fit.
??? (Samsung browser): You mentioned at the top that some parts of this can be standardized and some parts can never be standardized
Would be good to know which parts can/cannot be standardized
I'm not an expert to be clear
Stephen: we believe that we should be able to spec autofill permission policy. It’s our security model that if a user initiated a fill, we can’t fill a cross origin iframe. That breaks cards where the name is main frame and card numbers are on a cross-origin frame. Users were broken.
Didn’t move forward due to opposition on “should we standardize autofill at all”?
Rick: believe that autofill needs to have a partnership between the developer and the browser, the site should opt-in 
Alex (Apple)S: You said we don't want to boil the ocean, but maybe we should? Maybe its time to do something as complicated as unicode, to let websites really declare the kinds of things they expect? Isn't that what standards are for?
Cathy: leaning onto that, WebMCP for autofill?
Ben: or some other kind of brokering, agent says I'd love to fill this, website says I want this, provider says I can provide this, agent joins their hand
Agent never sees the password, for example
Cathy: Isn't autofill kind of an agent?
Johnny: I think there's something to do this, haven't we shown clearly that autofill cannot deal with all things?
Ricky: I'm still scarred by autocomplete=off
Yoav: We did some work to actually understand this. The best we came up with was:
1. Misguided security policies
2. Real need for alternative semantics (e.g., "not my address" cases)
Rick: Maybe we should acknowledge - standadizing something doesn't change the order of constituents. Users still come above Developers.
autocomplete=off is standardized, but we ignore it, and thats because the User wants to ignore it.
Yoav: Yep, there's valid use cases however.
Dan: Is there a risk of the autofill event being used to make it easier to get in the way
Yoav: That's the crux of WebKit's position on the event (and opposition)
Yoav: I think that autofill is already observable, if banks really want to do shenanigans
Yoav: If they do that, seems very user hostile, what can we do about that?
Yoav: The event makes it more explicit.
I am happy to carve out cases where the event isn't as useful
Or vendors can do origin blocking if they want
Stephen: By not doing this we’re putting barriers in the way of good actors, and bad actors simply say “claude write me an autofill detector” and it just works. We’re always going to have an autofill that’s detectable (if you made it look like human typing, it would be terrible). We’re punishing the good actors without any harm to the bad actors.
Ryosuke: we emulate what the user types
Stephen: but you emulate that quickly
Stephen: same problem as agent detection - if agent behaves like a human, its not useful
