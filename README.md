# Supply_Chain_Root_Cause_Analysis
Finding Bottlenecks at Supply chain level
I stopped blaming the driver for my late deliveries.

We’ve all had that frustration: checking an app for a package that was supposed to arrive yesterday and imagining the truck stuck in a massive traffic jam.

While analyzing 10k orders from a logistics dataset, I wanted to see if that "traffic jam" was actually the problem. Or was it something else?

Context: The "Late Delivery" tag is a heavy one that usually hurts the logistics team's reputation. I conducted a Root Cause Analysis to see exactly where the clock stops. Is it the Driver (Transit) or the Merchant (Processing)?

I didn't just look at the final delivery date. I used SQL to "split the clock" into two phases:

The Warehouse Phase: Time from order approval to hand-off to the carrier.

The Road Phase: Time from the truck leaving to hitting the customer's doorstep.

To keep the analysis fair, I used Python to isolate "local" orders where the distance was under 15km. If a 10km trip takes 3 days, one can’t blame the highway. For these 194 local orders:

The average processing (warehouse) time was approximately 2.37 days. The average delivery (road) time was approximately 1.05 days. The "Aha!" Moment:

The Bottleneck: Our initial SQL query on late orders (distance < 50km) showed that for the first few examples, the root_cause was consistently a 'Merchant Bottleneck', indicating the package spent significantly more time in the warehouse.

Even for local trips, data shows that the warehouse processing time is, on average, more than double the road delivery time. This points to the warehouse as the primary area for improvement.

My Recommendation: At this point, my recommendation wouldn't be "buy faster trucks." That’s expensive and ignores the root cause. The high-value fix is Merchant Incentives and process optimization at the warehouse level. By rewarding sellers who dispatch quickly and streamlining warehouse operations, the delay is solved before the driver even arrives.
