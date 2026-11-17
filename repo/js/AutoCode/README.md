# Genshin Impact Auto Redemption Code Tool Instructions

## Preparation
If you are redeeming exclusive redemption codes obtained through specific promotions (e.g., collaboration bundles), enter them in `BetterGI\User\JsScript\AutoCode\codes.txt` using the format `RedeemCode,ExpirationTime` (follow the existing format and use standard half-width English commas).  
If you are redeeming public redemption codes (such as special program livestreams, anniversary rewards, etc.), congratulations, no preparation is required! Simply click and run!

## Using the BGI-Provided Code List
You can select `Use BGI Provided Code List` in the settings. This fetches the latest livestream codes in real-time via network requests and records your redemption history, allowing long-term use without needing to manually update the script!  
> This feature requires enabling `JS Http Permission` under `Edit General Configuration` by right-clicking the script in the scheduler; otherwise, it will not function.

### Server Selection
You can select your current account server in the settings:
- **No Filter**: Does not filter by server; attempts all codes (matches original behavior).
- **CN Server**: Prioritizes CN server codes, attempting Global codes as fallback (records to cache if invalid to avoid repeated attempts).
- **Global Server (Beta)**: Prioritizes Global server codes, attempting CN codes as fallback.

The server classification logic aligns with BetterGI core: it checks whether the code entry's `title` starts with `[国际服]` (`[Global Server]`).

<details>
<summary>View BetterGI Core Server Distinction Code</summary>

Core implementation in `FeedWindowViewModel.cs`:

```csharp
private const string GlobalServerTitlePrefix = "[国际服]";

public enum RedeemCodeServerType
{
    Cn,
    Global
}

public static RedeemCodeServerType GetServerType(FeedItem feed)
{
    return feed.Title?.StartsWith(GlobalServerTitlePrefix, StringComparison.OrdinalIgnoreCase) == true
        ? RedeemCodeServerType.Global
        : RedeemCodeServerType.Cn;
}

public static (List<FeedItem> CnFeeds, List<FeedItem> GlobalFeeds) SplitByServer(IEnumerable<FeedItem?> items)
{
    var cnFeeds = new List<FeedItem>();
    var globalFeeds = new List<FeedItem>();

    foreach (var feed in items)
    {
        if (feed is null) continue;
        if (GetServerType(feed) == RedeemCodeServerType.Global)
        {
            globalFeeds.Add(feed);
        }
        else
        {
            cnFeeds.Add(feed);
        }
    }

    return (cnFeeds, globalFeeds);
}
```

Corresponding implementation in the script:

```javascript
const codeServer = item.title && item.title.startsWith("[国际服]") ? "global" : "cn";
```

</details>

### Trust Code Validity Period
When enabled, expired redemption codes are skipped immediately without attempting redemption.
> Code expiration dates are provided by the data source. If you prefer to verify directly, keep this disabled; expired codes will still be submitted and reported as "Expired" by the game.

### Redemption Cache Mechanism
After a code is attempted, the following outcomes are cached and will be skipped on subsequent runs:
- Redemption successful
- Already redeemed / used
- Expired
- Invalid code for a non-targeted server

The following outcomes are **NOT** cached and will be retried next time:
- Invalid code for the targeted server
- Event has not started yet

## Username Settings (Multi-Account Setup)
After adding the script to the scheduler, right-click the JS script and select `Edit JS Script Custom Settings` to set your Username.  

### Username Rules:

```text
Supports English, Chinese, and numbers
Length: 1-20 characters
If not set or formatted incorrectly, the default username "default" is used
```
