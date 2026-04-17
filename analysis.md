\# Analysis — RTT vs. Speed-of-Light



\*\*Source location:\*\* Waltham, MA (42.3765, -71.2356)



\---



\## Q1: Which city has the highest inefficiency ratio?



From the results, \*\*London\*\* has the highest inefficiency ratio at \*\*3.70\*\*, followed by Frankfurt at \*\*3.38\*\*. Both exceed the threshold of 3.0, so they’re flagged as highly inefficient.



At first glance, this might suggest poor network performance, but that’s a bit misleading. London is relatively close (about 5,275 km), which means its theoretical minimum RTT is very small—around 52.7 ms. In practice, though, the measured RTT is much higher (195.1 ms) because it includes fixed delays like TCP connection setup, TLS handshake, and server processing time. These delays don’t depend much on distance, so they end up dominating when the actual propagation delay is small.



Because of that, the inefficiency ratio for nearby cities gets artificially inflated. So while London appears to be the “worst,” it’s really more of a measurement effect than a true infrastructure problem.



A more meaningful case is \*\*Lagos, Nigeria\*\*, which has a ratio of \*\*2.44\*\*. Here, distance plays a larger role, so the ratio reflects real routing inefficiencies rather than just fixed overhead.



Looking at submarine cable routes, West Africa is mainly served by cables like \*\*ACE (Africa Coast to Europe)\*\*, \*\*WACS (West Africa Cable System)\*\*, and \*\*SAT-3/WASC\*\*. These all run along the west coast of Africa and connect northward into Europe. There isn’t a direct cable from the US East Coast to West Africa, so traffic has to detour through Europe. That extra distance explains why Lagos’s RTT is much higher than the theoretical minimum.



\---



\## Q2: Which city is closest to the theoretical minimum?



\*\*Sydney, Australia\*\* has the lowest inefficiency ratio at \*\*1.38\*\*, making it the closest to the theoretical minimum. Its measured RTT is 223.6 ms, compared to a theoretical value of 162.3 ms.



This actually makes sense. Sydney is the farthest city in the dataset (over 16,000 km away), so most of the RTT is just propagation delay. The fixed overhead from things like TCP and TLS becomes relatively small compared to the total time.



Also, the network path between the US and Australia is well-optimized. There are modern submarine cables, such as \*\*Southern Cross\*\* and \*\*PIPE Pacific Cable\*\*, that provide fairly direct, high-capacity routes between the US and Sydney. That helps keep the RTT close to the theoretical limit.



Other far-away cities like Singapore (1.42) and Mumbai (1.87) show a similar pattern. Since they’re also far from the source and are major network hubs, their performance is relatively efficient.



Overall, this shows that inefficiency ratio isn’t just about network quality—it’s also heavily influenced by distance. Short-distance routes tend to look worse because fixed delays dominate, while long-distance routes look better because propagation delay is the main factor.



\---



\## Q3: Why does traffic to Lagos route through Europe?



For Lagos, the measured RTT is 201.7 ms, while the theoretical minimum is only 82.6 ms. That’s a big gap, which tells us the packets are traveling much farther than the straight-line distance suggests.



In reality, traffic from Waltham to Lagos doesn’t go directly across the Atlantic. Instead, it typically follows a path like: Waltham → New York → across the Atlantic to Europe (e.g., London or Lisbon) → then down the west coast of Africa to Lagos. This detour through Europe adds a significant amount of extra distance, which shows up as higher RTT.



There are a few reasons for this routing pattern:



1\. \*\*Historical development\*\*: Much of Africa’s network infrastructure was originally built to connect to Europe, not directly to the US or even between African countries.



2\. \*\*Cable layout\*\*: There are no major direct submarine cables between the US East Coast and West Africa. Most transatlantic cables land in Europe or North Africa, so traffic naturally flows that way.



3\. \*\*Limited IXPs\*\*: Africa has relatively few Internet Exchange Points. As a result, even traffic within Africa can sometimes leave the continent, go through Europe, and then come back—this is known as “tromboning.”



To improve this situation, a few things would help:



\* Building direct submarine cables between the US and West Africa

\* Expanding Internet Exchange Points within Africa

\* Improving terrestrial fiber networks across the continent



Some newer projects, like \*\*2Africa Pearls\*\*, are starting to address these issues, but the overall infrastructure is still evolving.



\---



