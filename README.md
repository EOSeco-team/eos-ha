# How to keep BP node secure and high available

As we all know, bootstrapping of EOS mainnet is a very important event in blockchain field. We EOSeco as a BP candidate will try our best to make our node secure and available.

![](/img/architecture.png)

This is our architecture. There are several roles, include
- BP server
- API server cluster
- Load balance server
- Monitor server

## API server cluster

API server cluster is composed of many API servers. We can adjust number of API server as needed. API servers are none producing full node. They Sync block data with ohter EOS full node and serve EOS users with http api call. We will set "max-clients" parameter a larger value to 


## BP server

Block producer server will have our key-pair and will produce block if we are voted to do this. And there is a backup server,  in normal situation, backup server work as a none producing full node, when master BP server is down, backup server will change to be producing node. BP server work in intranet, **so attack can not reach BP server**. BP server sync data and push block with our API servers with high speed intranet. These API servers will push blocks that we produce to other EOS nodes.

## Load balance server

Load balance server accepting users api call and distribute these api call to different API server. So that, we can offer continuous service when some API servers are down.

## Monitor server

Monitor server will check the health of BP server and API servers. When server run in high pressure or fail down. We can fix problems in shortest time.


