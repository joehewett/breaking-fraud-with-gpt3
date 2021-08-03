# Solutions to problems that need to be solved 

This project can't run in production using GPT-3 without solving these [#0186274](https://mantis.netcraft.com/view.php?id=15448#c186274) problems.

There are two solutions to this:
- A special agreement with Microsoft (commercial) or OpenAI (research) that would allow us to privileged access to GPT-3 
- Use the next best thing, and open source model [GPT-J](https://mantis.netcraft.com/view.php?id=15448#c186282)

## OpenAI/Microsoft Agreement
We'd contact OpenAI to collaborate in helping them extend their usage guidelines, or contact Microsoft who have exclusive commercial rights.  
 
### pros
- we'd get access to GPT-3, the current state of the art LM
- we would have a newsworthy story that might be good for publicity ("Cybersecurity company partners with $company to tackle cybercrime with cutting-edge AI" etc)

### cons
- without special treatment, application even for access to the beta could get ignored or take 3 months
- even once getting access, there is no saying whether OpenAI or Microsoft would be open to talk
- GPT-3 is relatively expensive, at $0.02 per email. This scales to > $10,000 per year to reply to all confirmed AFF once each (based on 1500 per day in https://emailblacklist.netcraft.com).
- we'd be at the mercy of OpenAI and could be cut off at any moment 

## GPT-J 
We'd use GPT-J, mentioned in notes above, as a substitute for GPT-3

### pros 
- we can easily plug-and-play different LM's into our architecture, and only need to change 1 line of code. If we eventually get access to GPT-3 it would only take a matter of minutes to unplug GPT-3J and switch over to the GPT-3 API.
- it's open source, we could send 1 or 300 emails per scammer and not be rate limited by the API
- it's free, no campaign would be cost-prohibitive as with GPT-3

### cons
- it performs at roughly 90% of GPT-3's performance on benchmarks. 

Responses are still strong: 

```
 Hi,

 Thanks for your mail.
 I am glad that you have taken interest in my claims.
 I would like to know how can you be sure that this is me.
 I don't understand what you are doing.
 Can you please give me more details on how I can be sure that this is me.
 Also, how do I have the money without getting my card.
 I don't understand anything about this.
 I am so confused about everything.
 I would really appreciate if you would please help me on this matter.

 Thanks and God bless.
```


# Suggestion 
Because we could be rate-limited, cut off, or cost-prohibited by GPT-3 at any moment, my suggestion would be that regardless of whether we have access to GPT-3, we have GPT-J as a failover that can be switched in if needed.

Further, the process of negotiating use of GPT-3 is going to be fairly arduous. We're going to need to find the right people to talk to, and make a strong case that what we're doing is worthy of breaking their terms of service. 

As such, my suggestion would be to architect the actual system itself with GPT-J plugged in, building an MVP that will allow us to get substantial, indisputable test data (say, n>10,000). Simultaneously we can negotiate with OpenAI about usage of GPT-3, using our test data as a reliable source to argue our case. Then, if we get access to GPT-3 we can simply switch the API we're calling to generate our responses in a matter of minutes.


