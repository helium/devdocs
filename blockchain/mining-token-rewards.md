# Mining and Token Rewards

![](../.gitbook/assets/efee.jpg)

Hotspot Hosts and other Helium Network participants have many questions about expected mining rewards. This is for good reason. Earning `HNT` is one of the most exciting pieces of the Helium Network.

While at this point we can't give a precise formula for calculating how much `HNT` you'll earn over a given period, there are some higher level concepts, design elements, and rules to keep in mind that will help better explain what you might earn and why. This section covers these, as well as some mining and token reward basics.

## How Do Hotspots Earn Helium Tokens?

The Helium blockchain rewards Hotspots for providing wireless coverage and verifying the Helium Network. Hotspots are rewarded in Helium Token \(`HNT`\).

Every [epoch](mining-token-rewards.md), the current consensus group mines some amount of `HNT` which then gets divided among all Hotspots that have earned it. Hotspots and other network participants are rewarded across the following reward types:

| Reward Type | Description |
| :--- | :--- |
| PoC Challenger | Paid to any Hotspot that creates a valid PoC challenge and submits the corresponding receipt to the blockchain. |
| PoC Challengees | Awarded toa any Hotspot that completes a stage of a PoC challenge. |
| Witnesses | Distributed to all Hotspots that witness a packet as part of a PoC Challenge. |
| Consensus Group | Divided equally among the Hotspots that are part of outgoing Concesus Group, responsible for mining blocks. |
| Security | Awarded to Helium, Inc and other Network investors who hold Security Tokens. |
| Network Data Transfer | Distributed each epoch to Hotspots that route LongFi sensor data for sensors on the Network during that epoch. _Not yet activated._ |

{% hint style="info" %}
**Do I Have To Actively Participate to Earn Rewards Once My Hotspot is Deployed?**

No. Once your Hotspot is completely deployed and fully synced with the Helium blockchain, you as the owner are not required to do anything else in order to earn HNT. Your Hotspot will perform all of the above activities on its own while it runs. That said, there are some optimizations you can make to ensure your Hotspot is operating at full capacity.
{% endhint %}

## Target HNT Production Per Epoch

The target production rate for new `HNT` minted per month is `5,000,000`. This means that, if the blockchain performs as designed, it will produce `5,000,000` HNT per month. This target rate is based on the following two targets, as defined in their specific chain variables:

* Target **block time** is `60` seconds;
* Target **epoch size** is `30` blocks;

Recall that, in the Helium blockchain, [blocks](mining-token-rewards.md) contain some number of individual transactions and [epochs](mining-token-rewards.md) are comprised of all the blocks mined by a the current Consensus Group since the last epoch.

So, if we acheive our target block time of `60` seconds, and target epoch of `30` blocks, the blockchain will produce `5MM` HNT per month. Per epoch, this equals roughly `3424.66` HNT. The math for this is as follows:

* `43800` minutes in the average month;
* `30` minutes per epoch; 
* `1460` epochs per month;
* This results in `3424.66` HNT per epoch \(`3424.65753424658` HNT to be precise\);

{% hint style="info" %}
#### What Are The Current Block and Epoch Times?

At any point you can go to the [Helium blockchain Dashboard](http://dashboard.helium.com/) to view recent block and epoch statistics, past HNT production numbers, and much more. Your Helium Mobile Wallet will also give you the average block and epoch times for the trailing 24 hour period.
{% endhint %}

## HNT Distributions Per Epoch

As calculated above, the target `HNT` per epoch is approximately `3424.66`. The next logical question is "Where does all this HNT go?" Let's take a look.

Below are the current mining rewards per epoch. For every complete epoch \(marked by the election of a new Consensus Group\), all the `HNT` produced get distributed over the following reward types:

| Reward Type | Percentage | HNT Earned by Reward Type |
| :--- | :--- | :--- |
| PoC Challenger | 15% | 513.69 |
| PoC Challengees | 35% | 1198.63 |
| Witnesses | 5% | 171.24 |
| Consensus Group | 10% | 342.47 |
| Security | 35% | 1198.63 |
| Network Data Transfer | 0% | 0 |
| **Total** | **100%** | **3424.66** |

{% hint style="info" %}
#### Why is 0% Allocated for Network Data Transfer?

With the Network being very new, the reward distrubution is currently designed to incentivize the building of coverage. When the Data Credit infrastructure goes live, roughly Q2-2020, `30%` of HNT per epoch will be allocated to Network Data Transfer to ensure that Hotspots routing sensor data are compensated accordingly.
{% endhint %}

## HNT Earnings Per Hotspot By Reward Type

The last thing to examine is the amout of `HNT` earned per Hotspot in a given epoch, taking into acount the total number of Hotspots live on the Network eligible for each category of `HNT` reward. The following table shows the precise `HNT` payouts for a recently concluded epoch. These specific rewards were paid out in block `113718` and precise amount of `HNT` mined in this epoch was `3472.22222152`.

| Reward Type | Hotspots Earning Reward | HNT Earned Per Hotspot | Total Earned by Reward Type |
| :--- | :--- | :--- | :--- |
| PoC Challenger | 160 | 3.25520833 | 520.833333228 |
| PoC Challengee | 128 \(unique instances\) | 9.49435764 | 1215.277777532 |
| Witnesses | 409 \(unique instances\) | 0.42447704 | 173.611111076 |
| Consensus Group | 16 | 21.70138889 | 347.222222152 |
| Security | N/A | N/A | 1215.277777532 |
| Network Data Transfer | 0% | 0 | 0 |
| **Total** | N/A | N/A | **3472.22222152** |

**Notes on Reward Types and Payouts:**

* All Hotspots that have earned a specific reward type will split it equally. 
* Hotposts can earn one or more reward types during any given epoch. 
* Hotspots are only eligible to submit one Proof of Coverage Challenge - which results in them earning the `POC Challenger` reward type - once per epoch.
* `PoC Challenger`, `PoC Challengee`, and `Witness` reward types get distributed in the epoch that includes the corresponding PoC receipt. 
* A Hotspot can earn more than one `PoC Challengee` and `Witness` rewards per epoch. 

## HNT Proration and Slow Block Times

Target block and epoch times can be difficult to attain consistently. The Helium Network is still very new and growing quite quickly, so there are many bugs to be squashed and optimizations to be made. To account for this, the Helium blockchain uses something called `proration` to ensure that the target of `5,000,000` is achieved even if block and epoch times aren't on target.

{% hint style="info" %}
#### Target HNT Depends on Blocks, Not Clocks

It's easiest to think of target HNT production over the span of one month. Meaning, if the blockchain performs on target - resulting in roughly 1460 epochs per month - then 5MM new HNT will be produced. "One month" is a period of time measured by a clock. However, under the hood, we use block time, and the resulting epochs, to mark HNT production against our target. So when blocks are slow, HNT production is reduced proportionally.
{% endhint %}

### What Happens to HNT When Block Times are Slow?

As the network scales up and we fix bugs, there have been some less-than-optimal block times. This results in slower epochs. When this happens the Network will produce **less** HNT over the same period of time. This may seem counterintituve. _Shouldn't the blockchain produce more HNT when block times are slower to ensure the 5MM per month target is hit?_ No. Again, think blocks, not clocks. Here's a step-by-step example to hopefully make it more transparent:

* Let's assume for a given `60` minute period, the average block time was `120` seconds \(instead of the target `60` seconds\). 
* This would mark `30` blocks over the `60` minute period, conclude an epoch, and result in an HNT distribution. 
* As with any epoch, we would distribute the target of \(approximately\) `3424.66` HNT. 
* However, since this epoch took twice as long as normal \(`60` minutes versus `30` minutes\) the blockchain essentially distributes HNT at **half the normal rate**.

### When Block Times Slow Down, Everyone Earns Less

The most important take away here is that, when block times slow and HNT production is reduced, everyone participating in the Network - Witnesses, Challengers, Helium, Investors, etc. - **is impacted equally** \(with the exception of Consensus Group members; more on this below\). So, although it's annoying that the effective rate of HNT may have dropped over a given period of time, know that you're not the only one earning less. And this is by design.

### Consensus Groups and Slow Block Times

The only group that doesn't see its HNT reduced per epoch when blocks are slow is the Consensus Group. Currently there are 16 members of each Consensus Group, sharing 10% of the HNT produced per epoch - or approximately `21.70` HNT.

This amount stays fixed while every other category of HNT payout is prorated so that members of the Consensus Group are incentived to keep elections fast. Otherwise, a malicious Consensus Group member might be inclined to prolong elections. This could be done, for example, to prevent a subsequent election, thus ensuring current membership in the Consensus Group stays intact. By distributing a fixed amount of HNT per `30` block epoch \(as opposed to prorating payouts\), we remove the incentive to disrupt elections.

## Optimizing Your HNT Earnings

In order to optimize your HNT earnings, there are a few things we recommend:

* **Ensuring you aren't the only Hotspot in your area** is the method most likely to increase your earnings. If you are in an area with three or more Hotspots you are likely to participate as a `PoC Challengee` and `Witness` more PoC challenges that are happening around you. These are the two highest `HNT` distributions per epoch so optimizing around them has the highest impact.
* **Updgrading to a larger antenna** will help in situations where you have other Hotspots nearby but either fail challenges that you participate in or do not witness challenges that they are participating in. Note, upgrading to a larger antenna will not help in situations when you are the only Hotspot in the area, as your only HNT earnings will come from issuing challenges which only uses your internet connection. Figuring out which antenna to upgrade to is a complex question, and we recommend joining our [Community Slack](http://chat.helium.com) where plenty of antenna discussion occurs.
* **Opening internet network ports** helps in delivering `PoC Challengee` and `Witness` receipts to the `PoC Challenger`. These receipts are delivered via the internet through a peer-to-peer network, and can be affected by NAT, firewalls, and other networking issues. The most optimal configuration is adding the Hotspot to your network \[DMZ\]\([https://en.wikipedia.org/wiki/DMZ\_\(computing\)](https://en.wikipedia.org/wiki/DMZ_(computing))\) which allows unfettered access to and from the internet, but not to your local network. Alternatively manually opening port `44158` to the Hotspot will help, and enabling `uPNP` on your network router is a good fallback.

