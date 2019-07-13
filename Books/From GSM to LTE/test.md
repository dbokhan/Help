**1. Which algorithm is used to digitize a voice signal for transmission in a digital circuit-switched network and at which datarate is the voice signal transmitted?**

The PCM algorithm is used to digitize the voice signal, which makes full use of the available 64 kbit/s bandwidth of an E‐1 timeslot to encode the voice signal 

**2. Name the most important components of the GSM NSS and their tasks.**

The Mobile Switching Center (MSC) - The management activities to establish and maintain a connection are part of the Call  Control (CC) protocol, which is generally responsible for the following tasks:

- Registration of mobile subscribers: When the mobile device, also referred to as MS, is  switched on, it registers to the network and is then reachable by all other subscribers  of the network.

- Call establishment and call routing between two subscribers.

- Forwarding of SMS messages.

As subscribers can roam freely in the network, the MSC is also responsible for the  Mobility Management (MM) of subscribers. This activity comprises the following tasks:

- Authentication of subscribers at connection establishment is necessary because a  subscriber cannot be identified as in the fixed network by the pair of copper cables  over which the signal arrives.

- If no active connection exists between the network and the mobile device, the MS has to report a change of location to the network to be reachable for incoming calls and SMS messages. This procedure is called location update.

- If the subscriber changes their location while a connection is established with the  network, the MSC is part of the process that ensures that the connection is not interrupted and is rerouted to the next cell. This procedure is called handover.

The Visitor Location Register (VLR) - which holds the record of each subscriber that is currently served by the MSC. These records are only copies of the original records, which are stored in the HLR. While the standards allow implementation of the VLR as an independent  hardware component, all vendors have implemented the VLR simply as a software comoponent in the MSC.



