# External connections — guide

> What this is: for every external service a project has already had to talk to, the right method already decided — and why. Consult it before writing a new integration (an API script, scraping, browser automation): if the service is already mapped, use that, don't invent a new one.
> This is not the inventory of connectors available in the session — the environment declares those at every start and they change over time. Only decisions taken live here, and they stay true even when the roster changes.
> **It is updated the moment a chat learns the right method for a new service, or finds a better one than what is written here — especially after a mistake that cost money.** Same discipline as Rule 14, applied to this domain.

## Order of search, when the service is not in the table yet

1. **Who actually holds the data or the action you need?** Not every source covers the same thing: a generic connector and a script on the official API are often not substitutes, they return different data. Before choosing the means, establish who owns the thing.
2. **Among the sources that have it, which one is already connected *and alive*?** Connected does not mean working: an account can authenticate and still answer "subscription expired" on the calls that matter. Verify with a real call before building on top.
3. **If no dedicated source exists:** a connector aggregator (broad but not exhaustive coverage — check it covers the real case) before a pay-per-use scraping service (must be budgeted) before a direct script on the official API (when you need full control, or the data is private and an intermediary is a pointless risk).
4. **Browser automation, last resort.** Only when no practicable API exists or the action genuinely requires an interface (interactive login, captcha, panels with no API). It is the slowest and most fragile method. **Exception worth recognising:** for some actions no API exists upstream at all — there the browser is not a fallback, it is the only road, and it goes in the table as the primary method.
5. **Every pay-per-use run is announced first**, with an explicit spending cap, and starts only after confirmation. Where the service allows it, the cap is enforced with a parameter that stops the work by itself, rather than relying on a limit held by hand.

## Decided cases

One row per service, added when the method has actually been tried — not when it has been assumed.

| Service / need | Method | Why | Where it was tested |
|---|---|---|---|
| | | | |

## Careful: connected does not mean working

A connector showing up in the list of available tools is no guarantee. Before designing work around a source, verify it with a real call on the data you need: it happens that authentication works while the data comes back with an expired-plan or missing-permission error. When that happens, the row goes in this section — not deleted from the table, because the fact that it *cannot* be used is information the next round needs.
