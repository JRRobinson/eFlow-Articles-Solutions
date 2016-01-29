# **eFLOW can work with Proxy Server? ** #

## **Question / Description** ##

Anyone know if eFLOW can work with proxy server (specific question from customer: bluecoat / Wtam proxy servers)?
 
e.g. 

eFLOW Web Client -> Proxy Server -> eFLOW Web Server -> eFLOW App Server (TisAppPool)
eFLOW Thick Client -> Proxy Server -> eFLOW App Server (TisAppPool)
 
What if there is NLB?

Can proxy be used?

e.g. 

eFLOW Web Client -> Proxy Server ->  NLB (e.g. MS NLB, F5, Net Scaler) -> eFLOW Web Server -> NLB (e.g. MS NLB, F5, Net Scaler) ->  eFLOW App Server (TisAppPool)
eFLOW Thick Client -> Proxy Server -> NLB (e.g. MS NLB, F5, Net Scaler) -> eFLOW App Server (TisAppPool)




## **Answer / Solution** ##

eFlow uses plain http (or https by default since 5.2).
A (transparent) proxy should be transparent to the client or it is a broken proxy. In other words: If these products break http(s), eFlow will fail. If they are somewhat decent, eFlow should work. That's the whole point of these things.

Things to watch out for:

- HTTPS
- NTLM authentication

The former, because corporate proxies basically do a man-in-the-middle attack on users, relying on a company certificate that is rolled out via the domain. When you really want to go to https://www.facebook.com to complain about your day at work, the proxy will impersonate that site (Facebook's cert is backed by DigiCert. The proxy will now claim to be facebook.com according to YourCorporateOverlordsInIT). This _might_ break things in our WCF scenarios - I wouldn't know.

The latter, because .. that's what we usually use for authentication ofc. If the proxy 'breaks' that, your users will be sad. That said, I assume these customers have other internal sites ('intranet?'), so if that works, eFlow should work just as well.

In general, a proxy should be able to filter requests based on the target hostname/address. Your customer should be able to (and arguably that's the Right Way™) exclude connections to eFlow completely, because that's internal and not 'the internet'. Which would solve the problem completely.

NLB or not shouldn't matter again. The NLB is supposed to be transparent to the clients as well, i.e. the clients should never notice if they're talking to eFlow directly or via some NLB. Just like transparent proxies.

I expect that to work.



























