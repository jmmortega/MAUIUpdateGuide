## Messenger Service

MessagingCenter it's included in MAUI, move like always. Anyway, my recommendation here is use a abstraction, if you didn't use yet. There are a lot of reasons to create an abstraction for that:

- We can move to another implementation if we needed. 
- Idk, it's my impression, but if you see actual namespace that use MessagingCenter (Microsoft.Maui.Controls), that things like Lifecycle events doesn't use another implementation Messenger pattern, see below Lifecycle section. Sounds like in any moment, MessagingCenter could be deprecated. That I say, it's my opinion.
- If we use an abstraction, we could add new layers of security. I'm not a fan of use MessagingCenter, it's really easy to lost a subscriber, add more subscriber that needed or another problems that MessagingCenter can't allow protect in a easy way.