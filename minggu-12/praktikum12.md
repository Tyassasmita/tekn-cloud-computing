
## Section 2: Configure Swarm Mode

```docker run -dt ubuntu sleep infinity```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/1.jpg)

```docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/2.jpg)

### Step 2.1 - Create a Manager node

#### Run docker swarm init on node1.

```docker swarm init --advertise-addr $(hostname -i)```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/3.jpg)

```docker info```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/4.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/5.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/6.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/7.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/8.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/9.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/10.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/11.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/12.jpg)

### Step 2.2 - Join Worker nodes to the Swarm

``` docker swarm join --token SWMTKN-1-5t91j5u3prqbydwtq641swgfk8q02spg2v84b23bvocuipua5m-b8ajw7det44uvje95dbapfuc7 192.168.0.8:2377```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/13.jpg)

```docker node ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/14.jpg)

## Section 3: Deploy applications across multiple hosts
### Step 3.1 - Deploy the application components as Docker services
#### You will perform this procedure from node1.

``` docker service create --name sleep-app ubuntu sleep infinity``` 

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/15.jpg)

``` docker service ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/16.jpg)

## Section 4: Scale the application

```docker service update --replicas 7 sleep-app```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/17.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/18.jpg)

```docker service ps sleep-app```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/19.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/20.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/21.jpg)

```docker service update --replicas 4 sleep-app```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/22.jpg)

```docker service ps sleep-app```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/23.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/24.jpg)

## Section 5: Drain a node and reschedule the containers

```docker node ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/25.jpg)

#### Let’s see the containers that you have running on node2.

```docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/26.jpg)

####  back to node1

```docker node ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/27.jpg)

```docker node update --availability drain 690hkbdiu8fp5kt2v75pwo4xr ```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/28.jpg)

```docker node ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/29.jpg)

#### Switch back to node2 and see what is running there by running ```docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/30.jpg)

```docker service ps sleep-app```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/31.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/32.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/33.jpg)

## Cleaning Up

```docker service rm sleep-app```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/34.jpg)

```docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/35.jpg)

#### Lets run docker swarm leave --force on node1, node2 and node3.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/36.jpg)