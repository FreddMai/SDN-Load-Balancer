# SDN-Load-Balancer
This is the second assignment for our SDN course. We built a load balancer application which uses an OpenFlow switch to balance load stemming from a set of clients towards a set of servers.
Our network includes 8 hosts and a switch with an OpenFlow controller (POX). The first 4 hosts (h1 to h4) act as clients for a service offered by the hosts h5 to h8, which act as servers. The switch acts as a load balancer, and balances the flows from the clients towards the servers. The clients are addressing the public IP of the service, and the switch acts as a transparent proxy between the clients and the actual server.

# How to run:
Take your SimpleLoadBalancer.py file and put it in pox/ext.
Open the terminal inside and run:
./pox.py SimpleLoadBalancer --ip=10.1.2.3 --servers=10.0.0.5,10.0.0.6,10.0.0.7,10.0.0.8
Now, open another terminal, it doesn't matter where, and write: 
sudo mn --topo single,8 --controller remote --mac --switch ovsk

After the two terminals are up and running, type in the mininet:
h1 ping -c 10000 10.1.2.3

It should take a while, so you can go and relax a bit.
After it stopped sending all the packets, you can close the mininet and you should get a graph open up with the statistics of the requests per ip sent.
Also, you should get a graph built in your directory under the name: 'graph.png'.

