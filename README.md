# blogs-read
<details>
  <summary>How Discord stores trillions of messages</summary>

  https://discord.com/blog/how-discord-stores-trillions-of-messages 

  Discord migrated their entire DB from Cassandra to ScyllaDB. Cassandra had latency issues, garbage collector (GC) pauses and other issues. They also faced a problem which they termed as Hot Partition. ScyllaDB was compatible with Cassandra and was written in Cpp. So it didn't have issues with GC. I thought GCs were an advantage of Java, but turns out they aren't that great when it comes to large scale realtime systems. Discord also wrote a data service in between the API and the DB. It was written with Rust because of its speed, safety and concurrency performance. This service avoids multiple concurrent calls (for example, when a message with @everyone is sent) to the same DB by creating a worker task only for the first request. The subsequent reqeuests subscribe to the response of the worker task and so the DB is actually fetched only once. 

</details>

<details>
  <summary>Circuit Breaker Pattern (Design Patterns for Microservices)</summary>

  https://medium.com/geekculture/design-patterns-for-microservices-circuit-breaker-pattern-276249ffab33

</details>

<details>
  <summary>Understanding IAM roles for service accounts, IRSA, on AWS EKS.</summary>

  https://medium.com/@ankit.wal/the-how-of-iam-roles-for-service-accounts-irsa-on-aws-eks-3d76badb8942

</details>

<details>
  <summary>The What, Why, and How of Mastering App Size</summary>

https://engineering.atspotify.com/2023/11/the-what-why-and-how-of-mastering-app-size/

This was a blog on why app size matters on Spotify’s tech page. They briefed how each PR goes through a CI that checks for the change in the app size. It was really useful and I hope I read more such blogs on a daily basis.

</details>


<details>
  <summary>How Instagram scaled to 14 million users with only 3 engineers</summary>

https://read.engineerscodex.com/p/how-instagram-scaled-to-14-million#:~:text=Instagram%20scaled%20from%200%20to,having%20a%20reliable%20tech%20stack

It was a great read. They stuck with 3 principles – keep things simple, don’t re-invent the wheel, use proven technologies.

</details>


<details>
  <summary>Twitter's Recommendation Algorithm</summary>

  https://blog.twitter.com/engineering/en_us/topics/open-source/2023/twitter-recommendation-algorithm

  The recommendation pipeline consists of 3 stages:
1. Candidate sourcing: Helps in retrieving relevant tweets for a user. Each request filters 1.5k tweets from 100s of millions. In network tweets are those from people you follow and out of network tweets are from those who you don't follow. Candidates are found from these with ~50% from each. In-network tweets are ranked using Real Graph which is a model to predict the engagement between 2 users. Out of network tweets are ranked using social graphs and embedding spaces. Social graphs, as the name suggests, ranks tweets based on people with similar interests. Embedding spaces calculate the similarity between users and user-tweet pairs.
2. Ranking: From the ~1500 candidate sources filtered, ranking is done using a 48M parameter neural network. A tweet score is generated that gives the probability of engagement to that tweet.
3. Heuristics and filters: At this stage, a balanced and diverse feed is made. eg: Tweets from people you blocked are discarded. And finally the results are served along with ads and follow recommendations.

From the blog, I Was able to comprehend how recommendation algorithms work at scale. I've mostly worked with personal projects and now looking at how things work in real world software projects helped me gain a lot of insights and understand the various complexities present.

</details>

