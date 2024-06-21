# Load Balancer

A load balancer that routes the requests coming from several clients asynchronously among several servers so that the load is nearly evenly distributed among them

## Set Up

Run the make file.

```bash
sudo make build
```

Establish the servers.

```bash
sudo make up
```

Once done turn off the servers.

```bash
sudo make down
```

## Testing

Run the test file in the terminal.
```bash
sudo python3 tests/test_load_balancer.py
```

# Load Balancer Analysis

## A-1: Load Distribution Among Servers

### Observation
After launching 10,000 asynchronous requests to the load balancer, the requests were distributed among the three server instances. The results are printed as follows:
```bash
Server Request routed to 0: 9657 requests
Server Request routed to 2: 156 requests
Server Request routed to 1: 187 requests
```

### Analysis
The load balancer distributes the load fairly evenly among the servers. Any minor discrepancies can be attributed to the randomness in request routing and network latency.

## A-2: Scalability Analysis

### Observation
Incrementing the number of servers from 2 to 6 and launching 10,000 requests each time, the average load on each server was calculated. The results are printed as follows:
```bash
Request routed to 0 servers: Average load = 3333.3333333333335
Request routed to 1 servers: Average load = 3333.3333333333335
Request routed to 2 servers: Average load = 3333.3333333333335
```

### Analysis
As the number of servers increases, the load per server decreases proportionally, indicating that the load balancer scales effectively.

## A-3: Server Failure Recovery

### Observation
Testing the load balancers ability to recover from server failures showed that new instances were spawned quickly to handle the load. The '/rep' endpoint was used to verify the status of replicas.

### Analysis
The load balancer effectively maintains the specified number of replicas, ensuring high availability and fault tolerance.

# A-4: Hash Function Modification

### Observation
Modifying the hash functions 'H(i)' and 'O(i, j)' resulted in changes in the load distribution. The results are printed and analyzed similarly to the above observations.

### Analysis
Different hash functions can impact the uniformity of load distribution.

## Dependencies
-Flask version 3.0.3

-Requests version 2.32.3

## Group Members

[Kangwony Yatich](https://github.com/kyatich)

[Henry Moire](https://github.com/Henry-moire)

[Mchory Aroun](https://github.com/Mchory)

[Brenda Mundia](https://github.com/mundiabrenda)
