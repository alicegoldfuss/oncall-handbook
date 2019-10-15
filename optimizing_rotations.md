# Optimizing Your On-Call Rotations
Optimizing on-call rotations for health and life-balance is a group effort. Managers
have a large impact on how successful a rotation is allowed to be. Peers have a
large impact on how draining a rotation is, and in the mental well-being of everyone
involved.

## If you're in a position to suggest changes to your on-call rotation, here are some things to consider:

1. If the person on-call does not have a secondary, another team-member to escalate to, provide them a secondary.
2. If the rotation is too small, employees on-call will always feel stressed about being on-call. If the rotation is too large, employees on-call may not have frequent enough interactions with certain systems.
3. If pages are coming in too frequently and your staff is wiped out, rotate more frequently (daily?) or alternate between primary/secondary on a regular cadence (Foo is the primary on Mon/Wed/Fri/Sun and secondary on Tue/Thu/Sat; Bar is the opposite).
4. If you are changing the number of people in the on-call rotation, make sure that everybody on the team is aware of their new schedule. They may need to move things around in their schedule or swap (if it overlaps with PTO).
5. Make sure there is a clear way to manage shift swapping if you allow it. Remember that PagerDuty supports overriding primary/secondary.
6. Find your team's best way to rotate primary and secondary. Some teams prefer a team member to escalate from off-call to secondary to primary to get a feel for the current set of issues in production. Other teams prefer to go from primary down to secondary.
7. If you have a number of new team members (say, a reorg occurs), build your rotation so that any given primary and secondary pair has an experienced team member and a newer team member so that the experienced team member can provide support.
8. If your rotation has a defined *maximum time-to-response*, that alone has impacts on the ability of people to have a life. Consider shorter shifts if your rotation has such.
9. Posting on-call shifts to the calendars of the people on-call will help people plan around on-call times better.

## There are some other things you can do as a team to make your on-call rotation successful:

1. Make sure there is time budgeted to resolve issues that arise during on-call rotations. This can be done in a number of ways: carving off a block of time each week; dedicating one person to fix problems when they arise; etc. Remember that a) your on-call person will be randomized and is not ideal for fixing permanent problems and b) if your team does not pick up this work, it will be forgotten when the next person is on-call. This can also include a review of the severity of the alerting; is an after-hours page necessary, or could it be solved during the next business day?
2. Have PagerDuty send an email to the entire team whenever a page fires so that everybody is aware of the frequency. Have on-call employees send emails with more detail once the issue is resolved. This will give everybody an idea of how often specific incidents are occurring and how long they take to resolve. If something fails frequently, its stability should be examined.
3. If you have a daily standup, review your availability metrics every time. This should take no more than 5 minutes and provide the entire team with regular data about what is up and what is not. Discuss in-depth anything that is lower than expected. Assign team members to proactively investigate if you have spare cycles. If you're lucky, you will catch issues before they become incidents. If you're unlucky, this at least provides visibility into incidents.
4. Provide support for your team members who are on-call, especially from the management level.

## Right-sizing your shift durations
How long an on-call shift should be has many variables, so there is no one-size-fits-all rule of
thumb to go by. *Week* may be a nice round number, but that doesn't always make for a healthy
duration. Here are the variables, with guidance around whether they suggest longer or shorter
shifts.

### Page frequency:
How often the pager fires.
  * **Impact to watch-stander**: Very high. When it goes off, it's a drop-everything emergency no matter where you are.
  * **Rule of thumb**: The more often it goes off, the shorter the shift.
  * **More details**:
    * A frequency of between one per month and one per two weeks is low impact. A week long shift may not have any call-outs. At this frequency, the **[maximum response time][MRT]** will be a stronger impact to the watch-stander.
    * A frequency of between one per week and one per five days guarantees at least one call-out per week-long shift. Impacts are balanced with the **[maximum response time][MRT]**.
    * A frequency of between one per five days and one per two days guarantees multiple call-outs per week-long shift, which will make it stressful. Consider shorter shifts.
    * A frequency of between one per day and one per twelve hours allows the possibility of uninterrupted sleep. One to three day shifts may be acceptable, with longer shifts being more guaranteed to involve lost sleep.
    * A frequency of more than one per eight hours means guaranteed lost sleep. A one day shift may be acceptable, but will be hardship duty. 12 hour shifts, more survivable.
    * Any more often than 1 per 8 hours, and you have a distributed [NOC][NOC], not an on-call rotation.

### Maximum response time:
Sometimes called 'time to first work', this is the maximum allowed time for someone receiving a page to
start work on that page. If you're carrying your laptop with you, this is often how far you're allowed
to be from a network connection.
  * **Impact to watch-stander**: High. Unlike page-frequency, this impacts throughout the shift regardless of how busy it is.
  * **Rule of thumb**: Anything less than an hour will be very hard on parents of kids. Anything less than 15 minutes means the watch-stander is effectively house-bound.
  * **More details**:
    * The duration determines the length of errands a watch-stander can perform while on-call.
    * Impact can be lessened if escalating to secondary is destigmatized.
    * Holding both primary and secondary, if used, to the same response time doubles the life disruption for the team.
    * Not all rotations formally define this. Many informally define it as the "unackowledged [escalation][escalation]" time when an alarm automatically bumps up to the secondary person.

### Average time-to-resolve:
How long, on average, it takes to resolve a page.
  * **Impact to watch-stander**: Medium
  * **Rule of thumb**: This acts as a multiplier for how impactful the **[page frequency][PF]** is.
  * **More details**:
    * If most call-outs are for small things such as approving change-requests (reading a little and clicking a button), the impact is slight.
    * If the average call-out takes over 30 minutes or so to resolve, each page weighs more than the frequency would otherwise suggest.

### Rotation size:
The number of people involved in the rotation.
  * **Impact to watch-stander**: Medium
  * **Rule of thumb**: The more people in the rotation, the lower the percentage of your non-work life is eaten by on-call.
  * **More details**:
    * For a group of three, expect to be on-call a third of the time.
    * Due to how life works, expect more [shift-swapping][shift-swapping] or small term [overrides][overrides] for smaller teams than larger.
    * For larger teams, announcing the call schedule at least 6 weeks in advance helps minimize shift-swaps.
    * Long-term leaves, such as extended summer vacations, and medical or parental leaves, can be hard on small teams. Pay more attention to burnout during these times.

### On-call compensation:
Extra payment for being on-call.
  * **Impact to watch-stander**: Medium
  * **Rule of thumb**: Paying people extra explicitly for on-call can made harder on-call shifts easier to accept for employees.
  * **More details**:
    * US labor law may call almost everyone salaried-exempt and on-call can be a job duty without extra compensation.
    * Extra money for a hard task makes that task easier to accept with grace.

### Number of schedule tiers:
How deep the schedule is. Primary + Secondary would be 2 deep. Primary + Secondary + Management + CIO would be 4 deep.
  * **Impact to watch-stander**: Low
  * **Rule of thumb**: The higher the tier an escalation goes, the longer a problem goes unworked.
  * **More details**:
    * Secondary tiers on small teams may be too disruptive to be viable.
    * If a secondary tier is used, definitely have a framework for how the primary and secondary tiers are supposed to work together.
    * Policies governing how escalations work need to be in place.
    * Tying on-call performance to general job performance may require **[on-call compensation][OCC]** in some jurisdictions.
    * The terminal tier often expects to never get paged, and getting paged may initiate a [post-mortem process][post-mortem] to figure out why.

### Company paid cellular coverage:
The company pays for or subsidizes the cell service for people on-call.
  * **Impact to watch-stander**: Low
  * **Rule of thumb**: If you're paying for cell service, response-time improves as watch-standers are more willing to tether to deal with call-outs.
  * **More details**:
    * For companies that do not have company phones, some compensation may be required for must-carry-phone employees. This varies by location.
      * [US California rules require such compensation.][byod-ca]
    * This can be a single on-call phone that gets passed around or employer stipends for cell coverage.
    * Having a hotspot in their pocket reduces the impact a short **[maximum response time][MRT]** has on a watch-stander's life.

[MRT]: #maximum-response-time
[PF]: #page-frequency
[OCC]: #on-call-compensation
[NOC]: glossary.md#network-operations-center
[escalation]: glossary.md#escalation
[overrides]: glossary.md#overrides
[post-mortem]: glossary.md#post-mortem
[shift-swapping]: gloccary.md#shift-swapping
[byod-ca]: http://www.computerworld.com/article/2599121/byod/california-cell-phone-ruling-poses-big-byod-challenge.html

