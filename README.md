# BlockChain-Backend  
Back End Files for Blockchain Project at ITU Computer Engineering Computer Project Class  
Solution inspired by the medium article:  
https://medium.com/p/117428612f46

## Installation

1. Install Visual Studio IDE:  
https://www.visualstudio.com/vs/

2. Open the solution file (BlockChain.sln).  

3. From within the "Solution Explorer", right click the BlockChain.Console project and select the "Set As Startup Project" option.  

4. Click the "Start" button, or hit F5 to run. The program executes in a console window, and is controlled via HTTP.

## Usage with Client API

**1. [POST] /transactions/new**  
Create a new transaction to a block  

Example request body:  
```  
{  
 "sender": "my address",  
 "recipient": "someone else's address",  
 "amount": 5  
}
```  

**2. [GET] /mine**  
Tell our server to mine a new block. If success, miner server will forge a new block. And gain the reward with 1 Coin  

Return Example:  

```
{
  "hash": "8bbcb347e0634905b0cac7955bae152cb347e0634b5b0cac79534b5b0",
  "index": 4,  
  "message": "New Block Forged",  
  "proof": 26096,  
  "transactions": [
    {  
      "amount": 1,  
      "recipient": "8bbcb347e0634905b0cac7955bae152b",  
      "sender": "0"  
    }  
  ]
}
```  


**3. [GET] /chain**     
Returns the full Blockchain  .

Return Example:  

```
{  
  "chain": [  
    {  
      "index": 1,  
      "previous_hash": 1,  
      "proof": 100,  
      "timestamp": 1506280650.770839,  
      "transactions": []  
    },  
    {  
      "index": 2,  
      "previous_hash": "c099bc...bfb7",  
      "proof": 35293,  
      "timestamp": 1506280664.717925,  
      "transactions": [  
        {  
          "amount": 1,  
          "recipient": "8bbcb347e0634905b0cac7955bae152b",  
          "sender": "0"  
        }  
      ]  
    },  
    ... SO on  
  ],  
  "length": n (number)  
}
```
  
4. [POST] /nodes/register  

Registers nodes with urls. This should change to Node ID for further usage.  

Example return value: 
```
1 new nodes have been added: http://localhost:5001
```
  
5. [GET] /nodes/resolve
  
Resolves conflicts by looking up to other chains. If there is a longer valid chain replace our chain with it.  

```
{
    "Message": "Our chain is authoritive",
    "Chain": [
        {
            "Index": 0,
            "Timestamp": "2020-12-20T15:10:02.6924724Z",
            "Transactions": [],
            "Proof": 100,
            "PreviousHash": "1"
        }
    ]
}
```
