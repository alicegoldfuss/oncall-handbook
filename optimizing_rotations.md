# Optimizing Your On-Call Rotations

If you're in a position to suggest changes to your on-call rotation, here are some things to consider:

1. If the person on-call does not have a secondary, provide them a secondary.
2. If the rotation is too small, employees on-call will always feel stressed about being on-call. If the rotation is too large, employees on-call may not have frequent enough interactions with certain systems.
3. If pages are coming in too frequently and your staff is wiped out, rotate more frequently (daily?) or alternate between primary/secondary on a regular cadence (Foo is the primary on Mon/Wed/Fri/Sun and secondary on Tue/Thu/Sat; Bar is the opposite).
4. If you are changing the number of people in the on-call rotation, make sure that everybody on the team is aware of their new schedule. They may need to move things around in their schedule or swap (if it overlaps with PTO).
5. Make sure there is a clear way to manage shift swapping if you allow it. Remember that PagerDuty supports overriding primary/secondary.
6. Find your team's best way to rotate primary and secondary. Some teams prefer a team member to escalate from off-call to secondary to primary to get a feel for the current set of issues in production. Other teams prefer to go from primary down to secondary.
7. If you have a number of new team members (say, a reorg occurs), build your rotation so that any given primary and secondary pair has an experienced team member and a newer team member so that the experienced team member can provide support.

There are some other things you can do as a team to make your on-call rotation successful:

1. Make sure there is time budgeted to resolve issues that arise during on-call rotations. This can be done in a number of ways: carving off a block of time each week; dedicating one person to fix problems when they arise; etc. Remember that a) your on-call person will be randomized and is not ideal for fixing permanent problems and b) if your team does not pick up this work, it will be forgotten when the next person is on-call. This can also include a review of the severity of the alerting; is an after-hours page necessary, or could it be solved during the next business day?
2. Have PagerDuty send an email to the entire team whenever a page fires so that everybody is aware of the frequency. Have on-call employees send emails with more detail once the issue is resolved. This will give everybody an idea of how often specific incidents are occurring and how long they take to resolve. If something fails frequently, its stability should be examined.
3. If you have a daily standup, review your availability metrics every time. This should take no more than 5 minutes and provide the entire team with regular data about what is up and what is not. Discuss in-depth anything that is lower than expected. Assign team members to proactively investigate if you have spare cycles. If you're lucky, you will catch issues before they become incidents. If you're unlucky, this at least provides visibility into incidents.
4. Provide support for your team members who are on-call, especially from the management level.


