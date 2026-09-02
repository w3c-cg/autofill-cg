# Introduction

Every day on the web, millions of users enter information into forms to complete journeys ranging from e-commerce, 
to account creation and log-in, to government services, and more. Given the onerous nature of re-typing information, 
many user agents and other “Autofill implementors” (e.g., browser extensions) provide “Autofill” services to aid the
user in easily filling in forms.
However, today, Autofill implementors have a wide range of capabilities and behaviours, such that both users and websites
are faced with different experiences depending on the Autofill implementor being used.

# Goals
The mission of this group is to provide a forum for Autofill implementors to develop a common understanding of the interface
between Autofill and the web page. The group will discuss known issues and develop joint proposals to improve the developer
experience, focusing on explicit website signals, client-side data representation, and the mechanics of form filling.
Internal implementation details, such as proprietary heuristics or backend data processing, are out of scope.

# Scope of work

This group will discuss any feature proposal related to autofill and may incubate Specifications on that front. The group will strive to upstream
any mature specifications with traction to relevant WG venues. 

## Out of scope
Specifications related to extension-specific APIs may be discussed in the group, but will be defined and published in other venues
(e.g. The [WebExtensions CG](https://www.w3.org/community/webextensions/)).

# Liaisons
It is anticipated that the group will collaborate with appropriate W3C Working Groups and WHATWG Workstreams in order to transition
spec proposals to the Recommendation or Living Standard track. 

The following groups are the most likely to adopt proposals from this group:

* [HTML workstream at the WHATWG](https://whatwg.org/workstreams#html)
* [WebExtensions CG](https://www.w3.org/community/webextensions/)

# Chair

The CG is chaired by:
* Yoav Weiss, Shopify

The Chair is responsible for the day-to-day running of the group,
including:

  * ensuring the group adheres to its [Process](#process),
  * appointing [Editors](#editors) for [Deliverables](#deliverables),
  * managing the group's GitHub repositories, website, and online
    presence,
  * moderating the group's discussions, whatever the forum (GitHub,
    mailing lists, face to face, etc.),
  * running teleconferences and face-to-face meetings,
  * resolving conflicts between contributors,
  * encouraging participation in the group,
  * and keeping this Charter compliant with the [Community and Business
    Group Process](#community-and-business-group-process), [updating it
    as necessary](#amendments-to-this-charter).

# Process
## Community and Business Group Process

The group operates under the [Community and Business Group
Process](https://www.w3.org/community/about/agreements/). Terms in this
Charter that conflict with those of the Community and Business Group
Process are void.

As with other Community Groups, W3C seeks organizational licensing
commitments under the [W3C Community Contributor License Agreement
(CLA)](http://www.w3.org/community/about/agreements/cla/). When people
request to participate without representing their organization's legal
interests, W3C will in general approve those requests for this group
with the following understanding: W3C will seek and expect an
organizational commitment under the CLA starting with the individual's
first request to make a contribution to a group
[Deliverable](#deliverables). The section on [Contribution
Mechanics](#contribution-mechanics) describes how W3C expects to monitor
these contribution requests.

The [W3C Code of Ethics and Professional
Conduct](https://www.w3.org/Consortium/cepc/) applies to participation
in this group.

## Work Limited to Charter Scope

The group will not publish Specifications on topics other than those
listed under [Specifications](#specifications) above. See below for [how
to modify the charter](#amendments-to-this-charter).

## Contribution Mechanics

Substantive Contributions to Specifications can only be made by
Community Group Participants who have agreed to the [W3C Community
Contributor License Agreement
(CLA)](http://www.w3.org/community/about/agreements/cla/).

Specifications created in the Community Group must use the [W3C Software
and Document
License](http://www.w3.org/Consortium/Legal/2015/copyright-software-and-document).

All other documents produced by the group should use that License where
possible (except for tests; [see above](#test-suites-and-other-software).

Community Group participants agree to make all contributions in the
GitHub repo the group is using for the particular document. This may be
in the form of a pull request (preferred), by raising an issue, or by
adding a comment to an existing issue.

## Transparency

The group will conduct all of its technical work in public. All
technical work will occur in its GitHub repositories (and not in mailing
list discussions). This is to ensure contributions can be tracked
through a software tool.

Meetings may be restricted to Community Group participants, but a public
summary or minutes must be posted to GitHub.

## Decision Process

This group will seek to make decisions where there is consensus.
[Editors](#editors) assess consensus on issues related to their
[Deliverable](#deliverables). Where consensus isn't clear, or where
there is sustained, substantive disagreement with an Editor's decision,
the Editors and [Chairs](#chairs) may issue a Call for Consensus [CfC]
to allow multi-day online feedback for a proposed course of action.
After discussion and due consideration of different opinions, a decision
should be publicly recorded on GitHub.

If substantial disagreement remains (e.g. the group is divided) and the
group needs to decide an Issue in order to continue to make progress,
the Chairs will, in consultation with the Editors and group, choose an
alternative that had substantial support and which drew the weakest
objections.

Any decisions reached at any meeting are tentative and should be
recorded in a GitHub Issue. Any group participant may object to a
decision reached at an online or in-person meeting within 7 days of
publication of the decision provided that they include clear technical
reasons for their objection. The Chairs will facilitate discussion to
try to resolve the objection according to the [decision
process](#decision-process).

It is the Chairs' responsibility to ensure that the decision process is
fair, respects the consensus of the CG, and does not unreasonably favour
or discriminate against any group participant or their employer.

## Chair Selection

Additional [Chairs](#chairs) may be appointed by unanimous consent of
the then-current Chairs.

If 5 participants, no two from the same organisation, call for an
election, the group must use the following process to replace all of the
Chairs with a new Chair, consulting the Community Development Lead on
election operations (e.g., voting infrastructure and using [RFC
2777](https://tools.ietf.org/html/rfc2777)).

  * Participants announce their candidacies. Participants have 14 days
    to announce their candidacies, but this period ends as soon as all
    participants have announced their intentions. If there is only one
    candidate, that person becomes the Chair. If there are two or more
    candidates, there is a vote. Otherwise, nothing changes.

  * Participants vote. Participants have 21 days to vote for a single
    candidate, but this period ends as soon as all participants have
    voted. The individual who receives the most votes, no two from the
    same organisation, is elected chair. In case of a tie, RFC 2777 is
    used to break the tie.

Participants dissatisfied with the outcome of an election may ask the
Community Development Lead to intervene. The Community Development Lead,
after evaluating the election, may take any action including no action.

## Amendments to this Charter

The group can decide to work on a proposed amended charter, editing the
text using the [Decision Process](#decision-process) described above.
The decision on whether to adopt the amended charter is made by
conducting a 30-day vote on the proposed new charter. The new charter,
if approved, takes effect on either the proposed date in the charter
itself, or 7 days after the result of the election is announced,
whichever is later. A new charter must receive 2/3 of the votes cast in
the approval vote to pass. The group may make simple corrections to the
charter such as deliverable dates by the simpler group decision process
rather than this charter amendment process. The group will use the
amendment process for any substantive changes to the [goals](#goals),
[scope](#scope-of-work), [deliverables](#deliverables), [decision
process](#decision-process) or [rules for amending the
charter](#amendments-to-this-charter).
