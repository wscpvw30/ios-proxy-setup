# 9proxy ios: How to Set Up Residential Proxies on iPhone and iPad, and Which Plan Is Worth Paying For

Most people typing "9proxy ios" want one of two things: to find out whether there's an iPhone app, or to work out why the proxies they just paid for won't route any traffic on their phone. Both questions have concrete answers, and neither one is "download it from the App Store."

9Proxy is a residential proxy provider — 20M+ IPs across 90+ countries, HTTP/HTTPS/SOCKS5, targeting down to country, state, city and ISP level. It's sold as a balance-based one-off purchase rather than a monthly subscription, and the desktop tooling is Windows-first. iOS is the platform where the setup stops being automatic. The official docs cover three separate routes to get a proxy running on an iPhone or iPad, and picking the wrong one is the usual reason people think the service is broken.

Here's what each route actually is, what iOS refuses to do no matter which one you pick, and what the plans cost after the June 2026 price adjustment.

## Why iOS gets awkward

Two limits sit underneath every setup guide.

The first: iOS only handles HTTP proxies natively, and only over Wi-Fi. HTTPS and SOCKS5 aren't supported through Settings, and proxies cannot be used on cellular networks at all. That's Apple's restriction, not 9Proxy's — the same thing is true for every proxy vendor.

The second: 9Proxy's proxy credentials are session-based. The username you enter isn't just a login, it carries your targeting instructions. The docs use this format:


<subaccount>-country-<country_code>-st-<state_code>-city-<city_code>-isp-<isp_code>-ssid-<session_id>-sst-<session_time>


A working example from their documentation: `useruser123-country-US-ssid-rhdN1907ma`. Change the country code and you're exiting from a different country. Change the session ID and you get a different IP. People who paste only the sub-account name and wonder why geotargeting does nothing have missed this part.

## Route 1: Proxy2Web credentials in iOS Wi-Fi settings

This is the fastest path and needs nothing installed on the phone.

1. Generate an active proxy session in your 9Proxy dashboard (Proxy2Web lives under IP-based Residential Proxies, or you can activate a share code first).
2. On the iPhone, open **Settings → Wi-Fi**.
3. Tap the blue ℹ️ info icon next to the network you're connected to.
4. Scroll to **Configure Proxy** and choose **Manual**.
5. Enter the server IP and port, then the structured username and your sub-account password.
6. Tap **Save**.

Saving is the whole activation step. That Wi-Fi connection now routes through the proxy.

The catch is scope: the setting belongs to one Wi-Fi network. Switch to another network, or turn Wi-Fi off, and the proxy is gone. For a laptop-replacement workflow where you're mostly on one network, that's fine. For someone hopping between cafés and a phone hotspot, it's a constant re-entry job.

If you don't have a sub-account or session yet, that's where the signup comes first — 👉 [create a 9Proxy account and set up your first proxy session](https://bit.ly/9-Proxy).

## Route 2: Desktop app plus LAN port forwarding

9Proxy's separate guide for IP-based residential proxies takes a different approach: the phone borrows a proxy that the desktop application is already running.

Prerequisites are strict — the computer and the iPhone or iPad must be on the same local network, and your firewall has to allow traffic between them. If either condition fails, you'll see a saved proxy configuration that simply doesn't connect.

The steps:

1. Find your computer's LAN IP address.
2. Open the 9Proxy app on the computer and go to the Proxy List.
3. In the Port section, select that LAN IP.
4. Forward the chosen proxy to whichever port you want.
5. Open the Forwarding List and copy the IP and port pair.
6. On the iPhone, go back to **Settings → Wi-Fi → ℹ️ → Configure Proxy → Manual** and enter the forwarded address.

This works well for testing mobile layouts, checking how a session behaves on a phone-sized fingerprint, or running a small number of iOS devices from one machine. It falls apart the moment you leave the house, because the phone has to stay on the same LAN as the desktop app. It also means leaving a computer running.

## Route 3: Shadowrocket for SOCKS5, and ProxyHub for device management

If you need SOCKS5 or HTTPS on iOS, Settings won't help. The documented workaround is a third-party client — 9Proxy's guides use [Shadowrocket](https://bit.ly/9-Proxy), available from the App Store as a paid app.

Inside Shadowrocket: tap **Add Server**, set **Type** to HTTP or SOCKS5, then fill in the address, port, the structured 9Proxy username, and your sub-account password. Save, toggle the connection on, and allow the VPN configuration when iOS asks. The docs suggest checking `ipinfo.io/what-is-my-ip` to confirm the exit IP.

Two things worth knowing before you go down this road. Shadowrocket needs a real proxy session and sub-user created in the dashboard first — it is not a substitute for having credentials. And the VPN profile prompt is normal: that's how iOS lets a third-party app route system traffic.

The other iOS-specific tool is ProxyHub. **ProxyHub Lite** runs on a single mobile device; the iOS build is currently distributed as a Developer Preview, which means sideloading an IPA file with AltStore or Sideloadly from a computer rather than installing from the App Store. **ProxyHub Pro** runs on your desktop and manages multiple mobile devices from one screen — assign proxies, rotate IPs, watch device status — so the phone side stays simple while the admin work happens on the computer. Lite for one device, Pro for a fleet. If your plan involves real iOS device volume, this is the pair that matters.

## What iOS still won't do, no matter how you set it up

Running through this list before you buy saves a support ticket:

- **Cellular is out.** Mobile-data traffic can't be routed through a proxy on iOS. The docs state it plainly.
- **SOCKS5 and HTTPS aren't native.** They require a client app like Shadowrocket. Plain HTTP over Wi-Fi is the only built-in option.
- **Per-network configuration.** Every Wi-Fi network needs entering separately.
- **Older UI references.** The screenshots in 9Proxy's own guides were captured on iOS 16.1. The menu path is unchanged in later versions, but tap labels may differ slightly from what you see.
- **No invisible OS-level routing.** The desktop Windows client routes at the OS layer with zero application config. iOS doesn't allow that level of access to a normal app.

## Every 9Proxy plan currently on the price list

Pricing changed on June 1, 2026 — the first adjustment the company says it has made. IP-based packages and bundle packages moved; GB-based packages stayed where they were. Purchases are one-off top-ups against a balance, not subscriptions, and IPs don't expire.

**IP-based residential packages** — unlimited bandwidth per IP, best for sessions that need to hold the same IP across many requests:

| Package | Core config | Price | Billing | Buy |
| --- | --- | --- | --- | --- |
| 100 IPs | 20M+ pool, 90+ countries, unlimited bandwidth per IP | $24 ($0.24/IP) | One-off, IPs don't expire | [Get the 100 IP plan](https://bit.ly/9-Proxy) |
| 500 IPs | Same pool, volume rate | $72 ($0.144/IP) | One-off | [Get the 500 IP plan](https://bit.ly/9-Proxy) |
| 1,000 + 500 bonus IPs | Most popular tier per the site's own labelling | $126 ($0.084/IP) | One-off | [Get the 1,500 IP plan](https://bit.ly/9-Proxy) |
| 2,500 IPs | Same pool, deeper discount | $210 ($0.084/IP) | One-off | [Get the 2,500 IP plan](https://bit.ly/9-Proxy) |
| 5,000 IPs | Same pool | $360 ($0.072/IP) | One-off | [Get the 5,000 IP plan](https://bit.ly/9-Proxy) |
| 15,000 IPs | Same pool | $720 ($0.048/IP) | One-off | [Get the 15,000 IP plan](https://bit.ly/9-Proxy) |
| 25,000 IPs | Same pool | $863 ($0.035/IP) | One-off | [Get the 25,000 IP plan](https://bit.ly/9-Proxy) |
| 50,000 IPs | Same pool | $1,438 ($0.029/IP) | One-off | [Get the 50,000 IP plan](https://bit.ly/9-Proxy) |
| 100,000 IPs (Business) | Industrial-volume tier | $2,300 ($0.023/IP) | One-off | [Get the 100,000 IP business plan](https://bit.ly/9-Proxy) |
| 200,000 IPs (Business) | Industrial-volume tier | $4,140 ($0.021/IP) | One-off | [Get the 200,000 IP business plan](https://bit.ly/9-Proxy) |
| 500,000 IPs (Business) | Lowest advertised per-IP rate | $8,625 ($0.018/IP) | One-off | [Get the 500,000 IP business plan](https://bit.ly/9-Proxy) |

**GB-based residential packages** — you pay per gigabyte consumed and rotate freely across the full pool:

| Package | Price | Rate | Validity | Buy |
| --- | --- | --- | --- | --- |
| 5 GB | $15 | $3.00/GB | 180 days | [Get the 5 GB plan](https://bit.ly/9-Proxy) |
| 50 + 5 bonus GB | $105 | $2.10/GB | 180 days | [Get the 55 GB plan](https://bit.ly/9-Proxy) |
| 100 GB | $150 | $1.50/GB | 180 days | [Get the 100 GB plan](https://bit.ly/9-Proxy) |
| 200 GB | $200 | $1.00/GB | 180 days | [Get the 200 GB plan](https://bit.ly/9-Proxy) |
| 1,000 GB | $800 | $0.80/GB | 180 days | [Get the 1,000 GB plan](https://bit.ly/9-Proxy) |
| 2,000 GB | $1,500 | $0.75/GB | 180 days | [Get the 2,000 GB plan](https://bit.ly/9-Proxy) |

**Enterprise GB packages** — same model, no expiry on the balance:

| Package | Price | Rate | Validity | Buy |
| --- | --- | --- | --- | --- |
| 3,000 GB | $2,160 | $0.72/GB | Unlimited | [Get the 3,000 GB enterprise plan](https://bit.ly/9-Proxy) |
| 6,000 GB | $4,200 | $0.70/GB | Unlimited | [Get the 6,000 GB enterprise plan](https://bit.ly/9-Proxy) |
| 10,000 GB | $6,800 | $0.68/GB | Unlimited | [Get the 10,000 GB enterprise plan](https://bit.ly/9-Proxy) |

**Bundle packages** — IPs and bandwidth together, also repriced on June 1:

| Bundle | Config | Price | Billing | Buy |
| --- | --- | --- | --- | --- |
| Starter | 100 IPs + 5 GB | $30 | One-off, 180-day traffic validity | [Get the Starter bundle](https://bit.ly/9-Proxy) |
| Popular | 1,500 IPs + 50 GB | $180 | One-off, 180-day traffic validity | [Get the Popular bundle](https://bit.ly/9-Proxy) |
| Pro | 5,000 IPs + 500 GB | $720 | One-off, 180-day traffic validity | [Get the Pro bundle](https://bit.ly/9-Proxy) |

## Which one makes sense if your main device is an iPhone

Here's the practical split.

If your iPhone is the only device you have, the **GB-based plans** are the better fit. Proxy2Web runs in the dashboard, so you can generate a session from the phone's browser, paste the credentials into Wi-Fi settings, and you're done — no desktop app, no port forwarding, no second machine on the same network. The 5 GB tier at $15 is the cheapest way to find out whether the exit IPs behave on the sites you care about.

If you have a desktop in the loop anyway, **IP-based** is where the value is. Unlimited bandwidth per IP means long sessions and heavy page loads cost nothing extra, and the 1,000 + 500 bonus tier at $126 is the point where per-IP pricing drops sharply without committing to five-figure IP counts. The headline rate of $0.018/IP only appears at 500,000 IPs — unless you're reselling, that number is irrelevant to you.

Two warnings about scale. GB credits expire after 180 days on the standard tiers; enterprise tiers don't. Buy bandwidth for the work you'll actually run in six months, not for a number that looks impressive. And buying a large IP package to "use on your phone" is a category error — a single iOS device consumes one proxy session at a time.

## Discounts, trials, and the fine print worth reading first

**The discount.** 9Proxy runs a referral program, and the referred user gets 5% off purchases made with that code. Signing up through a referral link attaches the code automatically — 👉 [grab the 5% referral discount at signup](https://bit.ly/9-Proxy). That's a permanent 5% off future purchases for as long as the referral is linked to your account, not a one-time coupon.

**The free trial question.** Directory sites don't agree on this one. SaaSworthy lists a free trial with no credit card required; a Caproxy review states the service doesn't currently offer one. Don't plan around a trial you haven't confirmed — the 24/7 live chat is the place to ask before you pay.

**The refund mechanics.** 9Proxy's stated safety nets are a 60-second replacement window (a proxy that fails right after activation gets credited back) and the "Today List," which lets you reuse proxies accessed in the previous 24 hours at no extra cost. Reviewers describe both as better than the industry norm. They're also narrow: the refund policy is presented and agreed at checkout, and Trustpilot complaints about 9Proxy cluster around exactly that — refund expectations versus what the policy actually covers. If automated replacements aren't going to be enough for your use case, clarify the terms with support first.

## What reviewers say, including the uncomfortable parts

The positive coverage is consistent. Geekflare's 2026 review treats it as a competent budget residential option with targeting down to city and state. Caproxy rates it well on price and pool quality while noting it isn't aimed at absolute beginners. SourceForge and Slashdot carry positive user blurbs about clean IPs and quick support, and Product Hunt commenters mention stability with anti-detect browsers.

The negative side is real too, and you'll hit it within a few minutes of searching. Trustpilot's page for the domain shows an average around 2 out of 5, with complaints about non-working IPs, refund refusals, and fake-review accusations that the company disputes in its replies. One automated site scanner flagged the domain as elevated risk. A proxy reseller, Proxy Universe, published a report claiming 9Proxy went down for roughly two weeks in June 2026 and went dark again in August 2026 — worth weighing alongside the fact that the same publisher sells competing networks.

The honest summary: when the service is working, it issues real residential IPs at aggressive prices, and the documented iOS routes above do function. The risk that reviewers keep pointing at isn't quality, it's availability and refunds. Which leads to one straightforward rule if you're buying for phone workflows: start with the smallest package that covers a week of real work, verify your targets through the iOS setup before scaling, and don't park a year of budget in the balance until you've seen it perform on your own traffic.

## FAQ

**Does 9Proxy have an iOS app?**
Not in the usual App Store sense. ProxyHub Lite has an iOS build, but it ships as a Developer Preview that you sideload via AltStore or Sideloadly with a computer. For everything else — Wi-Fi proxy settings, Proxy2Web, or Shadowrocket — you're using the iPhone's own capabilities rather than a 9Proxy app.

**Why does my iPhone show "Configure Proxy" but nothing loads?**
Check the username first. It has to be the full structured string including country, session ID and session time parameters, plus the sub-account password. Then confirm you're on Wi-Fi, since cellular traffic can't be proxied at all, and that the proxy session is still active in your dashboard.

**Can I use SOCKS5 on an iPhone?**
Only through a third-party client. Shadowrocket is the one 9Proxy documents; it supports both HTTP and SOCKS5 and asks to install a VPN profile, which you'll need to approve with your passcode.

**Do I need the desktop app at all for iOS?**
No. It's required for the LAN port-forwarding route, and ProxyHub Pro needs a computer to manage multiple devices, but a single iPhone running Proxy2Web credentials never touches the desktop app.

**Which plan should an iPhone-only user buy first?**
The 5 GB package at $15. It's the lowest entry point, it works entirely through the browser dashboard, and it tells you whether the exit nodes hold up on your targets before you spend anything on IP volume.

Ready to test it on your own network? 👉 [Open a 9Proxy account, activate your referral discount, and generate your first proxy session](https://bit.ly/9-Proxy) — then follow Route 1 above and you'll know within ten minutes whether iOS routing works for what you're doing.
