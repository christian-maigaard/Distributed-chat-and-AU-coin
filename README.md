# Distributed-chat-and-currency-2018
A distributed chat, where clients relay messages to eachother, aswell as transfering the cryptocurrency 'AU Coin' to eachother without any centralized entity. Project made in 2018 for the course Distributed Systems and Security. 

# System Test

The system can obtain agreement between three peers. The code was tested by running the peers asdescribed above. After a peers completes a transaction, it is distributed in total order by the winnerof the lottery. The lottery winner is agreed upon by all the peers in the system. If a peer decides tobe malicious and try to transfer to himself this will be rejected by the system. A transaction thata given peer will do is signed and verified by other peers on the network. If any alterations is doneby and adversary to the signature or the transaction the transaction will be ignored. When thelottery winner adds a block to the network the block is only added to the blockchain if the messageis verified by the receiver.

# System design 

The system begins by assigning the sequencer. This is simply done if the initial peer doesn’t findany peer, if there are not any peers, he must therefore be the sequencer. After this is done the RSAkey pair is generated and stored for later use. The network knows who the sequencer is by checkingthe peerList that they will receive upon entering the network. Due to the design of our system theinitial peer is always on the top of this peerList. This makes it easy for all peers to determine whothe sequencer is. This solution will however fail, if the peerList is not ordered in the same way.The sequencer broadcasts all the transactions that it has received every 10 second. This is doneby storing every received transaction in a list, and running through that list every 10 second andbroadcasting every transaction in the order that they were received. After a transaction is broadcastto the network, it is deleted from the list. When a peer receives a block from the sequencer, theycheck the signature and blocknumber, and do a transaction, and relay the transaction to the 10peers after them on the peerList. This ensures that transactions are processed in the order that thesequencer sends them, as well as ensuring that the transaction is valid, and not a transaction froma malicious peer.

# How to Run 
Run client.go. enter some random input at the first peer. Thenext peer should connect to the initial peer. The IP is hardcoded to be localhost and the port isprinted from peer 1. Peer 2 should now be connected to p1. Do the same with p3. The system innow done initiating, and transactions can now be entered in the terminal. Enter the receiver(pk),followed by the amount. Unfortunately, due to random crashes, the system currently only workswith 3 peers.
