## Chapter 1: GSM

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

The Home Location Register (HLR) is the subscriber database of a GSM network. It contains a record for each  subscriber, with information about the individually available services.

The Short Messaging Service Center (SMSC) is used to store and forward short messages.

**3. Name the most important components of the GSM radio network (BSS) and their tasks.**

The Base Transciever Station (BTS) replace the wired connection to the subscriber with a wireless connection,  which is also referred to as the air interface.

The GSM Air Interface - the transmission path between the BTS and the mobile device is referred to, in the  GSM specifications, as the air interface or the Um interface.

The Base Station Controller (BSC) is responsible for the establishment, release and maintenance of  all connections for cells that are connected to it.

The Transcoding and Rate Adaptation Unit (TRAU), which is located between the MSC and a BSC and controlled by the BSC, performs the compression and decompression of the voice data stream.


