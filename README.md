# blockchaindemo
A very basic python-based decentralized blockchain system including blockmining and adding transactions. 


Testing Procedure: 

1. On Spyder platform, start three consoles to run bitcoin_node_5001.py, bitcoin_node_5002.py, and bitcoin_node_5003.py. 
* select all content in each python file and run to start the console. By now the decentralized blockchain is running.

2. On postman, start three nodes to run bitcoin_node_5001.py, bitcoin_node_5002.py, and bitcoin_node_5003.py. 
2.1 On the 1st node: [Get] http://127.0.0.1:5001/get_chain
2.2 On the 2nd node: [Get] http://127.0.0.1:5002/get_chain
2.3 On the 3rd node: [Get] http://127.0.0.1:5003/get_chain
2.4 On the 1rd node: [Post] http://127.0.0.1:5001/connect_node
select Body section, choose raw - Json, and fill in: 
{
  "nodes": ["http://127.0.0.1:5002",
            "http://127.0.0.1:5003"]
}
2.5 On the 2rd node: [Post] http://127.0.0.1:5002/connect_node
select Body section, choose raw - Json, and fill in: 
{
  "nodes": ["http://127.0.0.1:5001",
            "http://127.0.0.1:5003"]
}
2.6 On the 3rd node: [Post] http://127.0.0.1:5003/connect_node
select Body section, choose raw - Json, and fill in: 
{
  "nodes": ["http://127.0.0.1:5001",
            "http://127.0.0.1:5002"]
}
2.7 On the 1st node: [Get] http://127.0.0.1:5001/mine_block
2.8 On the 1nd node: [Get] http://127.0.0.1:5001/get_chain *two blocks
2.9 On the 2rd node: [Get] http://127.0.0.1:5002/get_chain *only one block
2.10 On the 2rd node: [Get] http://127.0.0.1:5002/replace_chain *get the longer chain
2.11 On the 3rd node: [Get] http://127.0.0.1:5003/replace_chain *get the longer chain
2.12 On the 1st node: [Post] http://127.0.0.1:5001/add_transaction
select Body section, choose raw - Json, and fill in: *transaction.json file content
{
  "sender": "Xin",
  "receiver": "Stephen", *use public key
  "amount": "10888"
}
2.13 On the 1st node: [Get] http://127.0.0.1:5001/mine_block * this will add the transaction to the block frommempool
2.14 On the 1st node: [Get] http://127.0.0.1:5001/get_chain * this will show three blocks and the third block contains the new transaction
2.15 On the 2rd node: [Get] http://127.0.0.1:5002/replace_chain *apply consensus to get the longest chain
2.16 On the 3rd node: [Get] http://127.0.0.1:5003/replace_chain *apply consensus to get the longest chain
2.17 On the 1st node: [Post] http://127.0.0.1:5001/add_transaction
select Body section, choose raw - Json, and fill in: *transaction.json file content
{
  "sender": "Xin",
  "receiver": "Alice", *use public key
  "amount": "1088888"
}
2.18 On the 1st node: [Get] http://127.0.0.1:5001/mine_block
* this will add the new transaction to the fourth block
2.19 On the 1st node: [Get] http://127.0.0.1:5001/get_chain * this will show four blocks and the third block contains the new transaction
2.20 On the 2rd node: [Get] http://127.0.0.1:5002/replace_chain *apply consensus to get the longest chain
2.21 On the 3rd node: [Get] http://127.0.0.1:5003/replace_chain *apply consensus to get the longest chain



