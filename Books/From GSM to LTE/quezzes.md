## Chapter 1: GSM

**1. Which algorithm is used to digitize a voice signal for transmission in a digital circuit-switched network and at which datarate is the voice signal transmitted?**

The PCM algorithm is used to digitize the voice signal, which makes full use of the available 64 kbit/s bandwidth of an E-1 timeslot to encode the voice signal


> Answer 1:
In a circuit switched digital telecommunication network a speech channel usually uses a 64 kbit/s timeslot. The pulse code modulation (PCM) algorithm is used to convert an analog voice signal for digital transmission.


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

**8. How is a subscriber authenticated in the GSM network? Why is an authentication neccesery?**

In the first step of the process, the MSC requests an  authentication triplet from the HLR/AuC. The AuC retrieves the Ki of the subscriber  and the authentication algorithm (A3 algorithm) based on the IMSI of the subscriber  that is part of the message from the MSC. The Ki is then used together with the A3  algorithm and a random number to generate the authentication triplet, which contains  the following values:

RAND: A 128‐bit random number.

SRES: The signed response (SRES) is generated by using Ki, RAND and the A3  authentication algorithm, and has a length of 32 bits.

Kc: The ciphering key, Kc, is also generated by using Ki and RAND. It is used for the ciphering of the connection once the authentication has been performed successfully.

RAND, SRES and Kc are then returned to the MSC, which then performs authentication  of the subscriber. It is important to note that the secret Ki key never leaves the AuC.

In the next step, the MSC sends the RAND inside an Authentication Request message to  the mobile device. The mobile device forwards the RAND to the SIM card, which then uses  the Ki and the authentication A3 algorithm to generate a signed response (SRES* ). The  SRES*  is returned to the mobile device and then sent back to the MSC inside an Authentication  Response message. The MSC then compares SRES and SRES* , and if they are equal, the  subscriber is authenticated and allowed to proceed with the communication.

**9. How is an SMS message exchanged between two subscribers?**

The sender of an SMS prepares the text for the message and then sends the SMS via a  signaling channel to the MSC as shown in Figure 1.17. As a signaling channel is used, an  SMS is just an ordinary DTAP SS‐7 message and thus, apart from the content, very  similar to other DTAP messages, such as a Location Update message or a Setup message  to establish a voice call. Apart from the text, the SMS message also contains the MSISDN  of the destination party and the address of the SMSC, which the mobile device has  retrieved from the SIM card. When the MSC receives an SMS from a subscriber, it  transparently forwards the SMS to the SMSC. As the message from the mobile device  contains the address of the subscriber’s SMSC, international roaming is possible and  the foreign MSC can forward the SMS to the home SMSC without the need for an  international SMSC database.
To deliver a message, the SMSC analyzes the MSISDN of the recipient and retrieves  its current location (the MSC concerned) from the HLR. The SMS is then forwarded to  the MSC concerned. If the subscriber is currently attached, the MSC tries to contact the  mobile device, and if an answer is received, the SMS is forwarded. Once the mobile  device has confirmed the proper reception of the SMS, the MSC notifies the SMSC as  well and the SMS is deleted from the SMSC’s data storage.

If the subscriber is not reachable because the battery of the mobile device is empty,  network coverage has been lost temporarily or the device is simply switched off, it is not  possible to deliver the SMS. In this case, the message waiting flag is set in the VLR and  the SMS is stored in the SMSC. Once the subscriber communicates with the MSC, the  MSC notifies the SMSC to reattempt delivery.

As the message waiting flag is also set in the HLR, the SMS also reaches a subscriber  who has switched off the mobile device in London, for example, and switches it on again  after a flight to Los Angeles. When the mobile device is switched on in Los Angeles, the  visited MSC reports the location to the subscriber’s home HLR (location update). The  HLR then sends a copy of the user’s subscription information to the MSC/VLR in Los  Angeles including the message waiting flag and thus the SMSC can also be notified that  the user is reachable again.

**10. Which tasks are performed by the RISC processor and which tasks are performed by the DSP in a mobile device?**

The RISC processor is responsible for the following tasks:

- handling of information that is received via the different signaling channels (BCCH,  PCH, AGCH, PCH and so on)

- call establishment (DTAP)

- GPRS management and GPRS data flow

- parts of the transmission chain, like channel coder, interleaver and cipherer (dedicated  hardware component in some designs)

- mobility management (network search, cell reselection, location update, handover,  timing advance, etc.)

- connections via external interfaces like Bluetooth, infrared and Universal Serial  Bus (USB)

- user interface (keypad, display, graphical user interface)

The DSP is another important component of a GSM chipset. Its main task is the  decoding of the incoming signal and FR, EFR, HR or AMR speech compression. In  GSM, signal decoding starts with the analysis of the training sequence of a burst. As the DSP is aware of the composition of the training sequence of a frame, the DSP can calculate a filter that is then used to decode the data part of the  burst. This increases the probability that the data can be correctly reconstructed.

**11. How is data stored on the SIM card?**

From a logical point of view, data are stored on a GSM SIM card in directories and  files, in a manner similar to the storage on a PC’s hard drive. The file and folder structures are specified in 3GPP TS 31.102. In the specification, the root directory is  called the main file (MF), which is somewhat confusing at first. Subsequent directories  are called dedicated files (DF), and normal files are called elementary files (EF). As there  is only a very limited amount of memory on the SIM card, files are not identified via file  and directory names. Instead, hexadecimal numbers with a length of four digits are  used, which require only 2 B memory.


**12. What is CAMEL and for which service is it typically used?**

Customized Applications for Mobile‐Enhanced Logic, or CAMEL for short. the CAMEL specification defines the protocol for  communication between different network elements such as the MSC and the SCP, as  well as a state model for call control
