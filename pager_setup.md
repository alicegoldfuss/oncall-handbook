# Pager Setup

That thing you have to carry around now. This section assumes you are using a cell phone and PagerDuty. Other setups welcome.

## iPhone

1. Add Pagerduty's number (have it do a test call) to your Contacts list and add it as a Favorite. PagerDuty provides [all their numbers and an updated vCard](https://support.pagerduty.com/hc/en-us/articles/202828870-Phone-numbers-notifications-are-sent-from) that you can add to your Contacts.
2. Open the Contacts app and find the Contact that the PagerDuty app added, it will be called something like "PagerDuty Outgoing Numbers". Edit > Ringtone > Emergency Bypass. This way a paging call will never be accidentally silenced by Do Not Disturb or Silent Mode.
3. In your iPhone's Settings, enable Do Not Disturb at night and Allow Calls From > Favorites. This way you can sleep soundly, knowing that if you get a phone call, it's either someone important (from your Favorites) or servers dying.

## Android

1. Starting with Android Marshmallow, you can enable Do Not Disturb in "Priority Only" mode to only allow notifications from contacts you specify.
2. In addition to DND mode (or as an alternative, for pre-Marshmallow phones), you can also use [Tasker](http://tasker.dinglisch.net/index.html) to customize notifications: for example, when certain numbers call or text, use Tasker to raise the volume to max (good for heavy sleepers!). There are many ways to do this, but [here is one example](http://www.androidauthority.com/tasker-emergency-calls-399762/)

## All

1. Setup your PagerDuty notifications to call you (repeatedly) and give Pagerduty its own unique ringtone. If you only rely on SMS or push notifications, you will constantly worry about missing them (or actually miss them) and your heart will race every time your phone pings. PagerDuty is highly customizable, and a combination of SMS, push, and phone calls is recommended.
2. Set your PagerDuty push alert sounds and ringtone to be something highly distinct from your regular ringtone, and avoid commonly used or OS-native sounds: this well help avoid confusing a stranger's SMS tone in public with your own on-call notifications.
3. Make sure your phone is not silenced.

### A Sample Notification Escalation policy

#### Notify on Assignment

This is a sample notification policy to alert me when an incident is assigned to me.  It's intention is to be "helpfully persistent".  This is catered to my order-of-notification preference, as well as my "dexterity issues" during the wee hours.  Feel free to tweak as desired.

| Timeframe   | Method |
| ----------- | ------ |
| Immediately | Email  |
| Immediately | Push   |
| 1 Minute    | Push   |
| 2 Minutes   | SMS    |
| 3 Minutes   | Call   |

One common mistake is to have all notification types trigger at the same time.  Unfortunately, what ends up happening is that in the time that it takes you to start responding to the one notification, another will trigger on top of the first.  You can't acknowledge the Push Notification before the SMS comes in, and while you're trying to type the number to ACK the SMS, the call will come in.

It's for this reason that it's better for me to stagger notifications.  Emails don't provide any special notification to me (no beeps or vibrations, tyvm), but some alerts messages may get mangled on a mobile device, and knowing that I can reference the original message elsewhere is helpful to me.

#### Notify on Resolution

Next, I like being notified immediately if an incident is resolved.  Perhaps an alert was being tested and accidentally went Live, or someone is already working the issue and doesn't need help, but I want to know immediately that action on my part is no longer needed.  If your alerting product of choice supports it, you may consider setting up notification that an incident has been resolved, like so:

| Timeframe   | Method |
| ----------- | ------ |
| Immediately | Email  |
| Immediately | Push   |

#### Notify before going on-call

As much as I like to think that I have my life together, and that everyone else does, too, things happen.  Whether I forget that a rotation is coming up, or that I promised to cover someone's shift, or a colleague is suddenly ill and I'm needed to cover for them, I like being reminded that I'm going on-call.

| Timeframe   | Method |
| ----------- | ------ |
| Immediately | Email  |
| Immediately | Push   |
| 1 Day       | Email  |
| 7 Days      | Email  |

#### (Optional) Group address for email notifications

You might find useful to send email notifications to your regular email address *and* to a group address that you will filter in its own folder. This can serve multiple purposes.

1. When you get paged, especially in the beginning of a shift, this can give you a clue if the problem might be the tail end of a previous problem. This is also helpful if you don't have awesome observability.
2. As a manager or mindful coworker, it will let you know at a glance who got paged, when, and for what – if your email notifications contain more information than just "SOMETHING BROKE, FIX IT PLS." Of course, you can get that information from e.g. PagerDuty directly; but having it conveniently accessible and searchable in an email folder can be very useful.

If you are on-call, it is crucial that your manager is aware of the burden that it represents (especially if that manager is not part of the rotation). Email notifications can create a good trail that will be usable by your manager, even if they don't even have a PagerDuty account, for instance.
