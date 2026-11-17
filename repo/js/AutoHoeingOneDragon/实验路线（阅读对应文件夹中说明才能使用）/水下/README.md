Underwater routes are generally slower in overall efficiency with higher average monster health, and are only selected when common mob weights are high.
Underwater routes require a separate configuration group, utilizing dedicated party compositions and combat strategies.
It is recommended to set combat timeout to 60 seconds or more and disable monster rotation search. Example combat strategy below (using Dehya as an example; can be replaced with other durable characters):

```text
Dehya attack,wait(0.1),keypress(e),attack,wait(0.6),attack,wait(0.7),attack
```

When Furina is not in the party, extended wait times are required:

```text
Dehya attack,wait(0.1),keypress(e),attack,wait(0.8),attack,wait(0.9),attack
```

Once verified and ready to use, copy this part of the routes to any location under the `pathing` folder.
