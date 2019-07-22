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

The Base Transciever Station (BTS) replaces the wired connection to the subscriber with a wireless connection,  which is also referred to as the air interface.

The GSM Air Interface - the transmission path between the BTS and the mobile device is referred to, in the  GSM specifications, as the air interface or the Um interface.

The Base Station Controller (BSC) is responsible for the establishment, release and maintenance of  all connections for cells that are connected to it.

The Transcoding and Rate Adaptation Unit (TRAU), which is located between the MSC and a BSC and controlled by the BSC, performs the compression and decompression of the voice data stream.

**4. How is BTS able to communicate with several subscribers at the same time?**

To allow the base station to communicate with several subscribers simultaneously, two methods are used. The first  method is frequency division multiple access (FDMA), which means that users communicate with the base station on different frequencies. The second method used is time division multiple access (TDMA). GSM uses carrier frequencies with a bandwidth of 200kHz over which up to eight subscribers can communicate with the base station simultaneously.

**5. Which steps are neccesery to digitize a speech signal in mobile device before it can be send over the GSM air interface?**

**6. What is a handover and which network components are involved?**

As subscribers can roam freely through  the network while a call is ongoing, it can happen that the subscriber roams out of the  coverage area of the cell in which the call was initially established. In this case, the BSC  has to redirect the call to the appropriate cell. This procedure is called handover.  

**7. How is the current location of a subscriber determined for a mobile-terminated call and how is the call forwarded through the network?**

From the fixed-line network, the Gateway‐Mobile Switching Center (G-MSC) receives the telephone number (MSISDN) of the called  party via an ISUP IAM message. the fixed-line network does not have to be aware that the called  party is a mobile subscriber. The G‐MSC in this example is simply a normal MSC with  additional connections to other networks. When the G-MSC receives the IAM message, it sends a Send Routing Information (SRI) message to the HLR to locate the subscriber in the network. The MSC currently responsible for the subscriber is also called  the subscriber’s Visited Mobile Switching Center (V-MSC).
The HLR then determines the subscriber’s IMSI by using the MSISDN to search  through its database and thus is able to locate the subscriber’s current V‐MSC. The  HLR then sends a Provide Roaming Number (PRN) message to the V-MSC/VLR to  inform the switching center of the incoming call. In the V-MSC/VLR, the IMSI of the  subscriber, which is part of the PRN message, is associated with a temporary Mobile  Station Roaming Number (MSRN), which is returned to the HLR. The HLR then transparently returns the MSRN to the G-MSC.

The G-MSC uses the MSRN to forward the call to the V-MSC. This is possible as the MSRN not only temporarily identifies the subscriber in the V-MSC/VLR but also  uniquely identifies the V-MSC to external switches. To forward the call from the  G-MSC to the V-MSC, an IAM message is used again, which, instead of the MSISDN, contains the MSRN to identify the subscriber. This has been done as it is possible, and  even likely, that there are transit switching centers between the G-MSC and V-MSC,  which are thus able to forward the call without querying the HLR themselves.


