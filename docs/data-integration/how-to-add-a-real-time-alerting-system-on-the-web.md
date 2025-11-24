---
icon: post_office
---

# How to add a (near) real-time alerting system for IoT sensors on the Web?

### Description

Data readings form different sensors can be made available using the [OGC Sensor Things API](https://docs.ogc.org/is/18-088/18-088.html) also known as STA.
The API can be separated in a MQTT and a HTTP interface. 
The HTTP interface is typically used for reading observations (data readings provided by the connected sensors) or creating entities like Datastream, Things, etc. that are required for sensors to publish observations. 
The MQTT interface is typically used by low cost sensors to publish their data readings.

When it comes to establishing a real-time (or near real time) alerting system, it is necessary that an interested client can receive alerts at the time they take place. This requires some kind of a subscription mechanism that allows the client to register for events.
The STA MQTT interface can be used to subscribe for events but it requires that the MQTT port(s) can make it through all intermediate firewalls. Alos, it is required that the underlying TCP socket remains connected at all time. Otherwise, the client and server need to implement error handling properly which is very complicated. So, even though the MQTT interace could be used to build an alerting system for IoT devices, there are performance and security arguments that indicate not to use the MQTT build into a STA deployment: Using the same MQTT broker for sensors to publish data and to deliver events to all subscribed clients is difficult to scale as the load heavily depend on the number of subscribers and the events they subscribe to. For scaling an MQTT broker without controlling the subscriptions is difficult as there could be subscribers to very chatty events like `v1.1/Observations`. Establishing re-scaling of the MQTT broker is almost impossible and introducing access control requires a proprietary layer to be implemented. These challenges in summary indicate to leverage the STA MQTT interface for registered sensors to publish their readings. But how to establish the alerting-system to support the scaling notifications of events?

The [W3C WebSub](https://www.w3.org/TR/websub/) defines a protocol to build an alerting system over the Web. In a nutshell, WebSub defines three roles: A subscriber is the entity that is first discovering topics (events) at a publisher that can be used for subscription. Once the subscriber found a topic, a subscription for hte topic is made to the associated hub. In the context of SensorThings API, the discovery of self-defined topics provides the flexibility for any client to shape the event trigger and data structure using a regular STA query.

In order to build an alerting system for sensorts over the Web based on STA, a combination with the W3C WebSub seems to be the approach. The [OGC SensorThings API Extension: WebSub Asynchronous Messaging Standard](https://docs.ogc.org/DRAFTS/24-032.html) (STA-WebSub) is currently a draft standard to be approved for adoption. The STA-WebSub standard defines the required changes to adopt the W3C WebSub protocol with SensorThings API v1.1.

### Why is STA-WebSub relevant?

The use of STA-WebSub enables the building of a (near) real-time alerting system over the Web by combingin the W3C WebSub and the OGCSensorThings API v1.1.
The basic use is that a client can use a regular HTTP URL to fetch data but also to discover whether that URL could be used for subscription. This is a powerful mechanism, as the subscriber (client) can self-define (i) the condition for a notification event and (ii) the data structure being returned when the event occurs. The prevent that large amounts of data is returned with the discovery, HTTP HEAD requests can be used. Once the client has confidence to have found a topic, the client can use the HTTP GET request to fetch the base data and then subscribe with the exact same URL to the associated hub to receive the alerts when the event occurs. Because the data shaping query part of the URL has not changed, the data structure for the alerts remain identical with the base data which eases the processing of the alerts.

As outlined in the W3C WebSub, each subscription has a receiving Webhook URL hosted at the subscriber. The use of Webhooks do not require TCP sockets to remain open. Each time that a subscription event occurs, the hub uses the associated Webhook (callback URL) to deliver the alert data. Dedicated processing at the subscriber's side is straight forward for each Webhook: First, the subscriber should check via the X-Hub-Signature mechanism that the received alert data (i) was sent by the expected hub and (ii) has not been tampered.

There are three major improvements by leveraging STA-WebSub over the STA MQTT. 
The first improvement is concerned with event (alert) distribution: The STA-WebSub does use regular HTTP(S) firewall ports and the requirement to keep a MQTT socket continously open does not exist. The STA MQTT broker delivers the events to the hub which is supposed to be deployed in a network close to the STA service. This means that external subscriptions (other than coming from the hub) can be denied by the broker.
The second improvement is concerned with the security and the performance of the MQTT broker. The topic discovery, done by subscribers via the STA HTTP interface can include access control. The access control policy can control which subscribers can subscribe to which topic and what hub to use. So, for example, a STA service could be associated with three different hubs: (i) The first hub could be optimized for chatty topics with short alert data like `v1.1/Observations`; (ii) the second hub could be optimized for large alert data; and (iii) the third hub could be exclusive for paying subscribers ensuring a "exact-once" delivery of alerts.
The third improvement is concerned with the ease to scale hubs. During the topic discovery, a STA service returns theURL for the hub that the subscriber should use for subscription. Enforcing "short" subscription expiration ensures that scaling up/down can take place without impacting the MQTT broker.

### Useful resources

Based on OGC STA-WebSub, a complete alerting system over the Web for IoT sensors was implemented as open source: 

* [FROST-Server](https://github.com/FraunhoferIOSB/FROST-Server) is the open source reference implementation for OGC SensorThings API v1.1 by Fraunhofer
* [FROST-Server-WebSub](https://github.com/securedimensions/FROST-Server-WebSub) is the open source implementation of a FROST-Server plugin that enables STA-WebSub
* [STA-WebSub-Hub](https://github.com/securedimensions/STA-WebSub-Hub) is an open source implementation of a STA-WebSub Hub that demonstrates the W3C WebSub subscription protocol and the subscription/notification with a STA service (FROST-Server)
* [STA-WebSub-Discovery]([https://github.com/securedimensions/STA-WebSub-Subscriber](https://github.com/securedimensions/STA-WebSub-Discovery)) is an open source implementation to demonstrate the use of STA-Websub for discovering topics (executed by subscribers)
* [STA-WebSub Subscriber](https://github.com/grumets/ganxet) is an example implementation of a STA-WebSub Subscriber
* [TAPIS]() is an example implementation of a Web-Application to visualize alerts received via a STA-WebSub Hub

Online resources demonstrating the use of STA-WebSub:

* [STA-WebSub Discovery client](https://sta-websub-discovery.citiobs.secd.eu/) is a Web-Application that demonstrates the STA-WebSub discovery with a STA service
* [STA service (STA-WebSub enabled)](https://citiobs.demo.secure-dimensions.de/staplustest/v1.1) is a STA service endpoint that is assoviated with a STA-WebSub Hub
* [STA-WebSub Hub](https://sta-websub-hub.citiobs.secd.eu/) is a Web-Application that connects to a STA-WebSub Hub which is connected to the STA service above
* [TAPIS](https://www.tapis.grumets.cat/) is a Web-Application that illustrates the use of the demo alerting system


{% hint style="info" %}


{% endhint %}

### You might be also interested in...

The deployment and use of the CitiObs (near) real-time alerting system for IoT sensors on the Web based on STA-WebSub was illustrated during the OGC Code Sprint in Rotterdam from 20 - 22 October 2025. More details are available from the [Code Sprint Wiki](https://github.com/opengeospatial/developer-events/wiki/October-2025-Open-Standards-Code-Sprint#introduction-to-sta-websub) and [here](https://github.com/opengeospatial/developer-events/wiki/Introduction-to-STA%E2%80%90WebSub).

